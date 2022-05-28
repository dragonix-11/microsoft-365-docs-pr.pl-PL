---
title: Jak używać programu DKIM do obsługi poczty e-mail w domenie niestandardowej
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak używać funkcji DomainKeys Identified Mail (DKIM) z Microsoft 365, aby upewnić się, że wiadomości wysyłane z domeny niestandardowej są zaufane przez docelowe systemy poczty e-mail.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 87f565d5058edff9ebde5af6e2cf84ca3e8262b4
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772155"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>Sprawdzanie poprawności wychodzących wiadomości e-mail wysyłanych z domeny niestandardowej za pomocą funkcji DKIM

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 W tym artykule wymieniono kroki korzystania z funkcji DomainKeys Identified Mail (DKIM) z Microsoft 365 w celu zapewnienia, że docelowe systemy poczty e-mail ufają komunikatom wysyłanym wychodzącym z domeny niestandardowej.

W tym artykule:

- [Jak DKIM działa lepiej niż sam SPF, aby zapobiec złośliwemu fałszowaniu](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [Kroki tworzenia, włączania i wyłączania modułu DKIM w portalu Microsoft 365 Defender](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [Kroki ręcznego uaktualniania kluczy 1024-bitowych do 2048-bitowych kluczy szyfrowania DKIM](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [Kroki ręcznego konfigurowania infrastruktury DKIM](#steps-to-manually-set-up-dkim)
- [Kroki konfigurowania usługi DKIM dla więcej niż jednej domeny niestandardowej](#to-configure-dkim-for-more-than-one-custom-domain)
- [Wyłączanie zasad podpisywania DKIM dla domeny niestandardowej](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [Zachowanie domyślne dla infrastruktury DKIM i Microsoft 365](#default-behavior-for-dkim-and-microsoft-365)
- [Skonfiguruj usługę DKIM tak, aby usługa innej firmy mogła wysyłać lub podszywać się pod adres e-mail w imieniu domeny niestandardowej](#set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain)
- [Następne kroki: Po skonfigurowaniu programu DKIM dla Microsoft 365](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365 automatycznie konfiguruje program DKIM dla początkowych domen "onmicrosoft.com". Oznacza to, że nie musisz nic robić, aby skonfigurować infrastrukturę DKIM dla żadnych początkowych nazw domen (na przykład litware.onmicrosoft.com). Aby uzyskać więcej informacji na temat domen, zobacz [Często zadawane pytania dotyczące domen](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM to jedna z trzech metod uwierzytelniania (SPF, DKIM i DMARC), które uniemożliwiają osobom atakującym wysyłanie komunikatów, które wyglądają tak, jakby pochodziły z Twojej domeny.

Program DKIM umożliwia dodanie podpisu cyfrowego do wychodzących wiadomości e-mail w nagłówku wiadomości. Podczas konfigurowania infrastruktury DKIM autoryzujesz domenę do kojarzenia lub podpisywania jej nazwy z wiadomością e-mail przy użyciu uwierzytelniania kryptograficznego. Systemy poczty e-mail, które pobierają wiadomości e-mail z twojej domeny, mogą używać tego podpisu cyfrowego, aby sprawdzić, czy przychodząca wiadomość e-mail jest legalna.

W warstwie podstawowej klucz prywatny szyfruje nagłówek w wychodzącej wiadomości e-mail domeny. Klucz publiczny jest publikowany w rekordach DNS domeny, a serwery odbierające mogą użyć tego klucza do dekodowania podpisu. Weryfikacja DKIM pomaga serwerom odbierającym potwierdzić, że poczta rzeczywiście pochodzi z Twojej domeny, a nie ktoś *podszywający się pod* Twoją domenę.

> [!TIP]
>Możesz też nie wykonywać żadnych czynności dotyczących usługi DKIM dla domeny niestandardowej. Jeśli nie skonfigurujesz modułu DKIM dla domeny niestandardowej, Microsoft 365 tworzy parę kluczy prywatnych i publicznych, włącza podpisywanie DKIM, a następnie konfiguruje zasady domyślne Microsoft 365 dla domeny niestandardowej.

 Wbudowana konfiguracja DKIM firmy Microsoft-365 jest wystarczająca dla większości klientów. Należy jednak ręcznie skonfigurować infrastrukturę DKIM dla domeny niestandardowej w następujących okolicznościach:

- Masz więcej niż jedną domenę niestandardową w Microsoft 365
- Skonfigurujesz również usługę DMARC (**zalecane**)
- Chcesz mieć kontrolę nad kluczem prywatnym
- Chcesz dostosować rekordy CNAME
- Chcesz skonfigurować klucze DKIM dla poczty e-mail pochodzącej z domeny innej firmy, na przykład w przypadku korzystania z poczty zbiorczej innej firmy.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>Jak DKIM działa lepiej niż sam SPF, aby zapobiec złośliwemu fałszowaniu
<a name="HowDKIMWorks"> </a>

SPF dodaje informacje do koperty komunikatów, ale program DKIM *szyfruje* podpis w nagłówku wiadomości. Po przesłaniu dalej wiadomości fragmenty koperty tej wiadomości mogą zostać usunięte przez serwer przekazywania. Ponieważ podpis cyfrowy pozostaje z wiadomością e-mail, ponieważ jest częścią nagłówka wiadomości e-mail, program DKIM działa nawet wtedy, gdy wiadomość została przesłana dalej, jak pokazano w poniższym przykładzie.

![Diagram przedstawiający przekazywany komunikat przekazujący uwierzytelnianie DKIM, w którym sprawdzanie SPF kończy się niepowodzeniem.](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

W tym przykładzie, jeśli opublikowano tylko rekord SPF TXT dla domeny, serwer poczty adresata mógł oznaczyć wiadomość e-mail jako spam i wygenerować wynik fałszywie dodatni. **Dodanie modułu DKIM w tym scenariuszu zmniejsza *liczbę fałszywie dodatnich* raportów o spamie.** Ponieważ program DKIM korzysta z kryptografii klucza publicznego do uwierzytelniania, a nie tylko adresów IP, moduł DKIM jest uważany za znacznie silniejszą formę uwierzytelniania niż SPF. Zalecamy używanie zarówno SPF, jak i DKIM, a także DMARC we wdrożeniu.

> [!TIP]
> Program DKIM używa klucza prywatnego do wstawiania zaszyfrowanego podpisu do nagłówków wiadomości. Domena podpisywania lub domena wychodząca jest wstawiona jako wartość pola **d=** w nagłówku. Domena weryfikacji lub domena adresata używa pola **d=** do wyszukania klucza publicznego z usługi DNS i uwierzytelnienia komunikatu. Jeśli komunikat zostanie zweryfikowany, sprawdzanie DKIM przejdzie pomyślnie.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>Kroki tworzenia, włączania i wyłączania modułu DKIM w portalu Microsoft 365 Defender

Wszystkie akceptowane domeny dzierżawy będą wyświetlane w portalu Microsoft 365 Defender na stronie DKIM. Jeśli jej nie widzisz, dodaj zaakceptowaną domenę ze [strony domen](/microsoft-365/admin/setup/add-domain#add-a-domain).
Po dodaniu domeny wykonaj kroki przedstawione poniżej, aby skonfigurować infrastrukturę DKIM.

Krok 1. Kliknij domenę, którą chcesz skonfigurować na stronie DKIM (https://security.microsoft.com/dkimv2 lub https://protection.office.com/dkimv2)).

:::image type="content" source="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png" alt-text="Strona DKIM w portalu Microsoft 365 Defender z wybraną domeną" lightbox="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png":::

Krok 2. Przesuń przełącznik do **pozycji Włącz**. Zostanie wyświetlone okno podręczne z informacją o konieczności dodania rekordów CNAME.

:::image type="content" source="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png" alt-text="Wysuwane szczegóły domeny z przyciskiem Utwórz klucze DKIM" lightbox="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png":::

Krok 3. Skopiuj rekord CNAMES wyświetlany w oknie podręcznym

:::image type="content" source="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png" alt-text="Okno podręczne Publikuj rekordy CNAME zawierające dwa rekordy CNAME do skopiowania" lightbox="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png":::

Krok 4. Publikowanie skopiowanych rekordów CNAME u dostawcy usług DNS.

W witrynie internetowej dostawcy DNS dodaj rekordy CNAME dla maszyny DKIM, którą chcesz włączyć. Upewnij się, że pola są ustawione następujące wartości dla każdego z nich:

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

Krok 5. Wróć do strony DKIM, aby włączyć funkcję DKIM.

:::image type="content" source="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png" alt-text="Przełącznik umożliwiający włączenie usługi DKIM" lightbox="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png":::

Jeśli zobaczysz, że rekord CNAME nie istnieje, może to być spowodowane następującymi przyczynami:

1. Synchronizacja z serwerem DNS, która może potrwać od kilku sekund do godzin, jeśli problem będzie powtarzać kroki ponownie
2. Sprawdź, czy nie występują błędy wklejania kopii, takie jak dodatkowe miejsce lub karty itp.

Jeśli chcesz wyłączyć moduł DKIM, przełącz z powrotem, aby wyłączyć tryb

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>Kroki ręcznego uaktualniania kluczy 1024-bitowych do 2048-bitowych kluczy szyfrowania DKIM
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 automatycznie konfiguruje program DKIM dla *domen onmicrosoft.com*. Nie są wymagane żadne kroki, aby użyć programu DKIM dla żadnych początkowych nazw domen (takich jak oprogramowanie litware.*onmicrosoft.com*). Aby uzyskać więcej informacji na temat domen, zobacz [Często zadawane pytania dotyczące domen](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Ponieważ zarówno bitowość 1024, jak i 2048 jest obsługiwana w przypadku kluczy DKIM, w tych kierunkach dowiesz się, jak uaktualnić klucz 1024-bitowy do wersji 2048 w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Poniższe kroki dotyczą dwóch przypadków użycia. Wybierz ten, który najlepiej pasuje do Twojej konfiguracji.

- Jeśli **masz już skonfigurowaną infrastrukturę DKIM**, możesz obrócić bitness, uruchamiając następujące polecenie:

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **Lub**

- Aby uzyskać **nową implementację DKIM**, uruchom następujące polecenie:

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

Pozostań w kontakcie z programem Exchange Online programu PowerShell, aby *zweryfikować* konfigurację, uruchamiając następujące polecenie:

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> Ten nowy klucz 2048-bitowy wchodzi w życie z parametrem RotateOnDate i w międzyczasie wysyła wiadomości e-mail z kluczem 1024-bitowym. Po czterech dniach możesz ponownie przetestować przy użyciu klucza 2048-bitowego (oznacza to, że gdy rotacja wejdzie w życie do drugiego selektora).

Jeśli chcesz obrócić do drugiego selektora po czterech dniach i potwierdzić, że 2048-bitness jest w użyciu, ręcznie obróć drugi klucz selektora przy użyciu odpowiedniego polecenia cmdlet wymienionego powyżej.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz następujące artykuły: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig), [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig) i [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>Kroki ręcznego konfigurowania infrastruktury DKIM
<a name="SetUpDKIMO365"> </a>

Aby skonfigurować infrastrukturę DKIM, wykonaj następujące kroki:

- [Publikowanie dwóch rekordów CNAME dla domeny niestandardowej w systemie DNS](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [Włączanie podpisywania DKIM dla domeny niestandardowej](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>Publikowanie dwóch rekordów CNAME dla domeny niestandardowej w systemie DNS
<a name="Publish2CNAME"> </a>

Dla każdej domeny, dla której chcesz dodać podpis DKIM w systemie DNS, musisz opublikować dwa rekordy CNAME.

> [!NOTE]
> Jeśli nie przeczytano pełnego artykułu, być może pominięto informacje o połączeniu programu PowerShell, które oszczędzają czas: [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Uruchom następujące polecenia w programie Exchange Online programu PowerShell, aby utworzyć rekordy selektora:

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

Jeśli oprócz domeny początkowej w Microsoft 365 aprowizowano domeny niestandardowe, musisz opublikować dwa rekordy CNAME dla każdej dodatkowej domeny. Jeśli masz dwie domeny, musisz opublikować dwa dodatkowe rekordy CNAME itd.

Użyj następującego formatu dla rekordów CNAME.

> [!IMPORTANT]
> Jeśli jesteś jednym z naszych klientów GCC High, obliczamy _customDomainIdentifier_ inaczej! Zamiast szukać rekordu MX dla _domeny initialDomain_ do _obliczania customDomainIdentifier_, zamiast tego obliczamy go bezpośrednio z dostosowanej domeny. Jeśli na przykład dostosowana domena to "contoso.com" _niestandardowadomainIdentifier_ staje się "contoso-com", wszystkie kropki są zastępowane kreską. Dlatego niezależnie od tego, na co wskazuje rekord MX, na który wskazuje _twoja nazwa początkowa_ , zawsze użyjesz powyższej metody, aby obliczyć _wartość customDomainIdentifier_ do użycia w rekordach CNAME.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600
```

Gdzie:

- W przypadku Microsoft 365 selektory zawsze będą mieć wartość "selector1" lub "selector2".
- _customDomainIdentifier_ jest taki sam jak _customDomainIdentifier_ w dostosowanym rekordzie MX dla domeny niestandardowej, który pojawia się przed mail.protection.outlook.com. Na przykład w następującym rekordzie MX dla contoso.com domeny _, customDomainIdentifier_ jest contoso-com:

  > contoso.com.  3600 IN MX 5 contoso-com.mail.protection.outlook.com

- _initialDomain to domena używana podczas rejestrowania_ się w celu Microsoft 365. Początkowe domeny zawsze kończą się onmicrosoft.com. Aby uzyskać informacje na temat określania domeny początkowej, zobacz [Często zadawane pytania dotyczące domen](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Jeśli na przykład masz domenę początkową cohovineyardandwinery.onmicrosoft.com i dwie domeny niestandardowe cohovineyard.com i cohowinery.com, musisz skonfigurować dwa rekordy CNAME dla każdej dodatkowej domeny dla łącznie czterech rekordów CNAME.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector1._domainkey
Points to address or value:    selector1-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600
```

> [!NOTE]
> Ważne jest utworzenie drugiego rekordu, ale w momencie tworzenia może być dostępny tylko jeden z selektorów. W istocie drugi selektor może wskazywać adres, który nie został jeszcze utworzony. Nadal zalecamy utworzenie drugiego rekordu CNAME, ponieważ rotacja kluczy będzie bezproblemowa.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>Kroki włączania podpisywania DKIM dla domeny niestandardowej
<a name="EnableDKIMinO365"> </a>

Po opublikowaniu rekordów CNAME w systemie DNS możesz włączyć podpisywanie DKIM za pośrednictwem Microsoft 365. Można to zrobić za pośrednictwem Centrum administracyjne platformy Microsoft 365 lub za pomocą programu PowerShell.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>Aby włączyć podpisywanie DKIM dla domeny niestandardowej w portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Zasady współpracy** \> & poczty e-mail **& Zasady dotyczące** \> **zagrożeń** \> **DKIM** w sekcji **Reguły**. Aby przejść bezpośrednio do strony DKIM, użyj polecenia <https://security.microsoft.com/dkimv2>.

2. Na stronie **DKIM** wybierz domenę, klikając nazwę.

3. W wyświetlonym oknie wysuwowym szczegółów zmień ustawienie **Podpisz komunikaty dla tej domeny przy użyciu sygnatur DKIM** na **Włączone** (![Przełącz włączone).](../../media/scc-toggle-on.png)

   Po zakończeniu kliknij pozycję **Obróć klucze DKIM**.

4. Powtórz ten krok dla każdej domeny niestandardowej.

5. Jeśli konfigurujesz moduł DKIM po raz pierwszy i widzisz błąd "Brak kluczy DKIM zapisanych dla tej domeny", musisz użyć Windows PowerShell, aby włączyć podpisywanie DKIM, jak wyjaśniono w następnym kroku.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>Aby włączyć podpisywanie DKIM dla domeny niestandardowej przy użyciu programu PowerShell

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="Błąd Brak zapisanych kluczy DKIM dla tej domeny" lightbox="../../media/dkim.png":::
> Jeśli konfigurujesz moduł DKIM po raz pierwszy i widzisz błąd "Brak kluczy DKIM zapisanych dla tej domeny", wykonaj polecenie w kroku 2 poniżej (na przykład `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`), aby wyświetlić klucz.

1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Należy stosować następującą składnię:

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> to nazwa domeny niestandardowej, dla którego chcesz włączyć podpisywanie DKIM.

   Ten przykład umożliwia podpisywanie DKIM dla contoso.com domeny:

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>Aby potwierdzić, że podpisywanie DKIM jest poprawnie skonfigurowane dla Microsoft 365

Poczekaj kilka minut, zanim wykonaj te kroki, aby potwierdzić, że poprawnie skonfigurowano moduł DKIM. Pozwala to na rozłożenie informacji DKIM o domenie w całej sieci.

- Wyślij wiadomość z konta w domenie z obsługą Microsoft 365 DKIM do innego konta e-mail, takiego jak outlook.com lub Hotmail.com.
- Nie używaj konta aol.com do celów testowych. Funkcja AOL może pominąć sprawdzanie DKIM, czy sprawdzanie SPF przebiega pomyślnie. Spowoduje to unieważnienie testu.
- Otwórz komunikat i przyjrzyj się nagłówkowi. Instrukcje dotyczące wyświetlania nagłówka wiadomości będą się różnić w zależności od klienta obsługi komunikatów. Aby uzyskać instrukcje dotyczące wyświetlania nagłówków komunikatów w Outlook, zobacz [Wyświetlanie nagłówków wiadomości internetowych w Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

  Komunikat z podpisem DKIM będzie zawierać nazwę hosta i domenę zdefiniowaną podczas publikowania wpisów CNAME. Komunikat będzie wyglądać mniej więcej tak:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- Poszukaj nagłówka Authentication-Results. Podczas gdy każda usługa odbierania używa nieco innego formatu do sygnatury poczty przychodzącej, wynik powinien zawierać coś takiego jak **DKIM=pass** lub **DKIM=OK**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>Aby skonfigurować program DKIM dla więcej niż jednej domeny niestandardowej
<a name="DKIMMultiDomain"> </a>

Jeśli w przyszłości zdecydujesz się dodać kolejną domenę niestandardową i chcesz włączyć usługę DKIM dla nowej domeny, musisz wykonać kroki opisane w tym artykule dla każdej domeny. W szczególności wykonaj wszystkie kroki opisane w [temacie Co należy zrobić, aby ręcznie skonfigurować infrastrukturę DKIM](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>Wyłączanie zasad podpisywania DKIM dla domeny niestandardowej
<a name="DisableDKIMSigningPolicy"> </a>

Wyłączenie zasad podpisywania nie powoduje całkowitego wyłączenia modułu DKIM. Po upływie określonego czasu Microsoft 365 automatycznie zastosuje zasady domyślne dla twojej domeny, jeśli zasady domyślne są nadal włączone. Jeśli chcesz całkowicie wyłączyć moduł DKIM, musisz wyłączyć moduł DKIM w domenach niestandardowych i domyślnych. Aby uzyskać więcej informacji, zobacz [Zachowanie domyślne dla infrastruktury DKIM i Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

### <a name="to-disable-the-dkim-signing-policy-by-using-windows-powershell"></a>Aby wyłączyć zasady podpisywania DKIM przy użyciu Windows PowerShell

1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom jedno z następujących poleceń dla każdej domeny, dla której chcesz wyłączyć podpisywanie DKIM.

   ```powershell
   $p = Get-DkimSigningConfig -Identity <Domain>
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   Przykład:

   ```powershell
   $p = Get-DkimSigningConfig -Identity contoso.com
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   Lub

   ```powershell
   Set-DkimSigningConfig -Identity $p[<number>].Identity -Enabled $false
   ```

   Gdzie _liczba_ jest indeksem zasad. Przykład:

   ```powershell
   Set-DkimSigningConfig -Identity $p[0].Identity -Enabled $false
   ```

## <a name="default-behavior-for-dkim-and-microsoft-365"></a>Zachowanie domyślne dla infrastruktury DKIM i Microsoft 365
<a name="DefaultDKIMbehavior"> </a>

Jeśli nie włączysz modułu DKIM, Microsoft 365 automatycznie tworzy 2048-bitowy klucz publiczny DKIM dla twojego adresu e-mail usługi Microsoft Online Routing Address (MOERA)/domeny początkowej i skojarzonego klucza prywatnego, który przechowujemy wewnętrznie w naszym centrum danych. Domyślnie Microsoft 365 używa domyślnej konfiguracji podpisywania dla domen, które nie mają zasad. Oznacza to, że jeśli nie skonfigurujesz programu DKIM samodzielnie, Microsoft 365 użyje domyślnych zasad i kluczy tworzonych w celu włączenia modułu DKIM dla domeny.

Ponadto jeśli po włączeniu tej domeny wyłączysz podpisywanie DKIM w domenie niestandardowej, Microsoft 365 automatycznie zastosuje zasady domeny MOERA/początkowej dla domeny niestandardowej.

W poniższym przykładzie załóżmy, że usługa DKIM dla fabrikam.com została włączona przez Microsoft 365, a nie przez administratora domeny. Oznacza to, że wymagane rekordy CNAM Nie istnieją w systemie DNS. Podpisy DKIM dla poczty e-mail z tej domeny będą wyglądać mniej więcej tak:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

W tym przykładzie nazwa hosta i domena zawierają wartości, do których CNAME wskazuje, czy podpisywanie DKIM dla fabrikam.com zostało włączone przez administratora domeny. Ostatecznie każda wiadomość wysłana z Microsoft 365 będzie podpisana przez moduł DKIM. Jeśli włączysz usługę DKIM samodzielnie, domena będzie taka sama jak domena w adresie Od: w tym przypadku fabrikam.com. Jeśli tego nie zrobisz, nie będzie on wyrównany i zamiast tego użyje początkowej domeny organizacji. Aby uzyskać informacje na temat określania domeny początkowej, zobacz [Często zadawane pytania dotyczące domen](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>Skonfiguruj usługę DKIM tak, aby usługa innej firmy mogła wysyłać lub podszywać się pod adres e-mail w imieniu domeny niestandardowej
<a name="SetUp3rdPartyspoof"> </a>

Niektórzy dostawcy usług poczty e-mail zbiorczej lub dostawcy oprogramowania jako usługi umożliwiają skonfigurowanie kluczy DKIM dla poczty e-mail pochodzącej z ich usługi. Wymaga to koordynacji między użytkownikiem a inną firmą w celu skonfigurowania niezbędnych rekordów DNS. Niektóre serwery innych firm mogą mieć własne rekordy CNAME z różnymi selektorami. Żadna z dwóch organizacji nie robi tego dokładnie w ten sam sposób. Zamiast tego proces zależy całkowicie od organizacji.

Przykładowy komunikat przedstawiający prawidłowo skonfigurowaną infrastrukturę DKIM dla contoso.com i bulkemailprovider.com może wyglądać następująco:

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

W tym przykładzie, aby osiągnąć ten wynik:

1. Dostawca poczty e-mail zbiorczej dał firmie Contoso publiczny klucz DKIM.

2. Firma Contoso opublikowała klucz DKIM w swoim rekordzie DNS.

3. Podczas wysyłania wiadomości e-mail dostawca poczty e-mail zbiorczej podpisuje klucz przy użyciu odpowiedniego klucza prywatnego. W ten sposób dostawca poczty e-mail zbiorczej dołączył podpis DKIM do nagłówka wiadomości.

4. Odbieranie systemów poczty e-mail wykonuje sprawdzanie DKIM, uwierzytelniając wartość DKIM-Signature d=\<domain\> względem domeny w adresie Od: (5322.From) komunikatu. W tym przykładzie wartości są zgodne:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>Identyfikowanie domen, które nie wysyłają wiadomości e-mail

Organizacje powinny jawnie określić, czy domena nie wysyła wiadomości e-mail, określając `v=DKIM1; p=` w rekordzie DKIM dla tych domen. Zaleca to odbieranie serwerów poczty e-mail, że nie ma prawidłowych kluczy publicznych dla domeny, a wszelkie wiadomości e-mail podające się za pochodzące z tej domeny powinny zostać odrzucone. Należy to zrobić dla każdej domeny i poddomeny przy użyciu wieloznacznego modułu DKIM.

Na przykład rekord DKIM będzie wyglądać następująco:

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>Następne kroki: Po skonfigurowaniu programu DKIM dla Microsoft 365
<a name="DKIMNextSteps"> </a>

**Mimo że rozwiązanie DKIM ma na celu zapobieganie fałszowaniu, rozwiązanie DKIM działa lepiej z platformami SPF i DMARC.**

Po skonfigurowaniu infrastruktury DKIM, jeśli jeszcze nie skonfigurowano SPF, należy to zrobić. Aby uzyskać krótkie wprowadzenie do SPF i szybko skonfigurować go, zobacz [**Konfigurowanie SPF w Microsoft 365, aby zapobiec fałszowaniu**](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Aby uzyskać bardziej szczegółowe informacje na temat sposobu, w jaki Microsoft 365 używa protokołu SPF, rozwiązywania problemów lub wdrożeń niestandardowych, takich jak wdrożenia hybrydowe, zacznij od tego, [jak Microsoft 365 używa struktury zasad nadawcy (SPF), aby zapobiec fałszowaniu](how-office-365-uses-spf-to-prevent-spoofing.md).

Następnie zobacz [**Używanie usługi DMARC do weryfikowania poczty e-mail**](use-dmarc-to-validate-email.md). [Nagłówki wiadomości antyspamowych](anti-spam-message-headers.md) zawierają pola składni i nagłówków używane przez Microsoft 365 do sprawdzania DKIM.

**Ten test sprawdzi, czy** konfiguracja podpisywania DKIM została prawidłowo skonfigurowana i czy zostały opublikowane odpowiednie wpisy DNS.

> [!NOTE]
> Ta funkcja wymaga konta administratora usługi Microsoft 365. Ta funkcja nie jest dostępna w usługach Microsoft 365 dla instytucji, Microsoft 365 obsługiwany przez 21Vianet lub Microsoft 365 Germany.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">Uruchamianie testów: DKIM</a></p>
</div>

## <a name="more-information"></a>Więcej informacji

Rotacja kluczy za pośrednictwem programu PowerShell: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[Sprawdzanie poprawności poczty e-mail przy użyciu usługi DMARC](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email?view=o365-worldwide&preserve-view=true)

[Używanie zaufanych nadawców usługi ARC na potrzeby legalnych przepływów poczty](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&branch=tracyp_emailauth)