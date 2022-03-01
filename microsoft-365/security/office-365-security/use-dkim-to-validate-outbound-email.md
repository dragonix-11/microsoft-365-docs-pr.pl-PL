---
title: Jak używać funkcji DKIM do poczty e-mail w domenie niestandardowej
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
description: Dowiedz się, jak używać DKIM (DomainKeys Identified Mail) z usługą Microsoft 365 w celu zapewnienia, że wiadomości wysyłane z Twojej domeny niestandardowej są zaufane przez docelowe systemy poczty e-mail.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1740d910f95a0076da34b7a08e66853fb7cca598
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032138"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>Używanie funkcji DKIM do sprawdzania poprawności wychodzących wiadomości e-mail wysłanych z domeny niestandardowej

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 Ten artykuł zawiera listę czynności, które należy wykonać w celu używania dKIM (DomainKeys Identified Mail) z usługą Microsoft 365, aby zapewnić, że docelowe systemy poczty e-mail będą ufać wiadomościom wychodzącym wysyłanym z domeny niestandardowej.

W tym artykule:

- [Jak działa DKIM lepiej niż tylko SPF w celu zapobiegania złośliwym fałszerszem](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [Procedura tworzenia, włączania i wyłączania funkcji DKIM Microsoft 365 Defender portalu](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [Procedura ręcznego uaktualniania kluczy 1024-bitowych do 2048-bitowych kluczy szyfrowania DKIM](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [Czynności wykonywane w celu ręcznego skonfigurowania DKIM](#steps-to-manually-set-up-dkim)
- [Procedura konfigurowania usługi DKIM dla więcej niż jednej domeny niestandardowej](#to-configure-dkim-for-more-than-one-custom-domain)
- [Wyłączanie zasad podpisywania DKIM dla domeny niestandardowej](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [Domyślne zachowanie dla danych DKIM i Microsoft 365](#default-behavior-for-dkim-and-microsoft-365)
- [Konfigurowanie usługi DKIM w celu wysyłania lub fałszowania wiadomości e-mail w imieniu domeny niestandardowej przez usługę innej firmy](#set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain)
- [Następne kroki: Po skonfigurowaniu DKIM dla Microsoft 365](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365 automatycznie konfiguruje DKIM dla swoich początkowych domen onmicrosoft.com domen. Oznacza to, że nie musisz nic robić, aby skonfigurować narzędzie DKIM dla jakichkolwiek początkowych nazw domen (na przykład dla litware.onmicrosoft.com). Aby uzyskać więcej informacji o domenach, zobacz [Często zadawane pytania dotyczące domen](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM jest jedną z metod uwierzytelniania (SPF, DKIM i DMARC), która zapobiega wysyłaniu przez atakujących wiadomości wyglądacych tak, jakby pochodziły z Twojej domeny.

Funkcja DKIM umożliwia dodanie podpisu cyfrowego do wychodzących wiadomości e-mail w nagłówku wiadomości. Podczas konfigurowania funkcji DKIM autoryzuje domenę do skojarzenia lub podpisania jej nazwy z wiadomością e-mail przy użyciu uwierzytelniania kryptograficznego. Systemy poczty e-mail, które odbierają pocztę e-mail z Twojej domeny, mogą używać tego podpisu cyfrowego w celu sprawdzenia, czy przychodzące wiadomości e-mail są prawdziwe.

W podstawowym przypadku klucz prywatny szyfruje nagłówek wychodzącej wiadomości e-mail domeny. Klucz publiczny jest publikowany w rekordach DNS domeny, a serwery odbierające mogą użyć tego klucza do odkodowania podpisu. Weryfikacja DKIM pomaga serwerom odbierający potwierdzić, że poczta pochodzi naprawdę z Twojej domeny, a nie przez osobę *podszywając się pod* Twoją domenę.

> [!TIP]
>Nie możesz też nic robić w przypadku DKIM dla swojej domeny niestandardowej. Jeśli nie skonfigurujesz DKIM dla domeny niestandardowej, program Microsoft 365 utworzy parę klucza prywatnego i publicznego, umożliwi podpisywanie DKIM, a następnie skonfiguruje domyślne zasady Microsoft 365 domeny niestandardowej.

 Wbudowana konfiguracja DKIM platformy Microsoft-365 jest wystarczającym zasięgiem dla większości klientów. Jednak należy ręcznie skonfigurować DKIM dla domeny niestandardowej w następujących okolicznościach:

- Masz więcej niż jedną domenę niestandardową w Microsoft 365
- Zamierzasz również skonfigurować DMARC (**zalecane**)
- Chcesz mieć kontrolę nad kluczem prywatnym
- Chcesz dostosować rekordy CNAME
- Chcesz skonfigurować klucze DKIM dla poczty e-mail pochodzącej z domeny innej firmy, na przykład w przypadku korzystania z usługi poczty masowej innej firmy.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>Jak działa DKIM lepiej niż tylko SPF w celu zapobiegania złośliwym fałszerszem
<a name="HowDKIMWorks"> </a>

Spf dodaje informacje do koperty wiadomości, ale DKIM *szyfruje* podpis w nagłówku wiadomości. Gdy przesyłasz wiadomość dalej, część koperty tej wiadomości może zostać zdjęona przez serwer przesyłania dalej. Ponieważ podpis cyfrowy pozostaje z wiadomością e-mail, ponieważ stanowi on część nagłówka wiadomości e-mail, DKIM działa nawet wtedy, gdy wiadomość została przesyłana dalej, jak pokazano w poniższym przykładzie.

![Diagram przedstawiający wiadomość przesyłaną dalej, która przekazuje uwierzytelnianie DKIM w przypadku niepowodzenia sprawdzania rekordu SPF.](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

W tym przykładzie, jeśli opublikowano tylko rekord TXT SPF dla domeny, serwer poczty adresata mógł oznaczać Twoją pocztę e-mail jako spam i wygenerować wynik fałszywie dodatni. **Dodanie dKIM w tym scenariuszu ogranicza raportowanie spamu wyników *fałszywie dodatnich* .** Ponieważ technologia DKIM uwierzytelnia się na podstawie kryptografii klucza publicznego, a nie tylko adresy IP, jest ona uznawana za znacznie silniejszą formę uwierzytelniania niż mechanizm SPF. Zalecamy używanie zarówno funkcji SPF, jak i DKIM, a także DMARC w swoim wdrożeniu.

> [!TIP]
> Aby wstawić zaszyfrowany podpis do nagłówków wiadomości, aplikacja DKIM używa klucza prywatnego. Domena podpisywania (domena ruchu wychodzącego) jest wstawiana jako wartość pola **d=** w nagłówku. Weryfikowana domena lub domena adresata używa następnie pola **d=** do wyszukiwania klucza publicznego w systemie DNS i uwierzytelniania wiadomości. Jeśli wiadomość zostanie zweryfikowana, zostanie pomyślnie zweryfikowana kontrola DKIM.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>Procedura tworzenia, włączania i wyłączania funkcji DKIM Microsoft 365 Defender portalu

Wszystkie zaakceptowane domeny dzierżawy będą widoczne w portalu Microsoft 365 Defender pod stroną DKIM. Jeśli nie widzisz tej nazwy, dodaj zaakceptowaną domenę ze [strony domen](/microsoft-365/admin/setup/add-domain#add-a-domain).
Po dodaniu domeny wykonaj czynności przedstawione poniżej, aby skonfigurować usługę DKIM.

Krok 1. Kliknij domenę, którą chcesz skonfigurować na stronie DKIM (https://security.microsoft.com/dkimv2 lub https://protection.office.com/dkimv2)).

![Strona DKIM w portalu Microsoft 365 Defender z wybraną domeną.](../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png)

Krok 2. Kliknij pozycję Utwórz klucze DKIM.

![Wysuw szczegółów domeny z przyciskiem Utwórz klucze DKIM.](../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png)

Krok 3. Kopiowanie nazw CNAMES wyświetlanych w oknie podręcznym

![Okno podręczne Publikowanie rekordów CNAME zawierające dwa rekordy CNAME do skopiowania.](../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png)

Krok 4. Publikowanie skopiowanych rekordów CNAME na serwerze DNS usługodawca.

W witrynie internetowej dostawcy DNS dodaj rekordy CNAME dla funkcji DKIM, które chcesz włączyć. Upewnij się, że w polach są ustawione następujące wartości dla każdego z nich:

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

Krok 5. Powrót do strony DKIM, aby włączyć funkcję DKIM.

![Przesuń przełącznik do opcji Włączone, aby włączyć funkcję DKIM.](../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png)

Jeśli zobaczysz komunikat o błędzie CNAME, może to być spowodowane tym, że:

1. Synchronizacja z serwerem DNS, co może potrwać kilka sekund do godzin, jeśli problem nadal występuje, ponownie powtarzaj kroki
2. Sprawdź, czy nie ma żadnych błędów wklejania, takich jak dodatkowe spacje lub karty itp.

Jeśli chcesz wyłączyć funkcję DKIM, przełącz się z powrotem do trybu wyłączenia

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>Procedura ręcznego uaktualniania kluczy 1024-bitowych do 2048-bitowych kluczy szyfrowania DKIM
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 automatycznie konfiguruje DKIM dla *onmicrosoft.com* domen. Aby używać funkcji DKIM w przypadku jakichkolwiek początkowych nazw domen (takich jak przykład litware), nie są wymagane żadne kroki.*onmicrosoft.com*). Aby uzyskać więcej informacji o domenach, zobacz [Często zadawane pytania dotyczące domen](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Ponieważ klucze DKIM są obsługiwane zarówno w wersji 1024, jak i 2048, w tych wskazówkach powiesz, jak uaktualnić klucz 1024-bitowy do wersji 2048 w programie [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Poniższe kroki mają zastosowanie w przypadku dwóch przypadków użycia. Wybierz ten, który najlepiej odpowiada Twojej konfiguracji.

- Po **skonfigurowaniu DKIM** można obracać bity, uruchamiając następujące polecenie:

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **lub**

- Aby uruchomić **nową implementację DKIM**, uruchom następujące polecenie:

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

Pozostań w kontakcie Exchange Online programem PowerShell *,* aby zweryfikować konfigurację, uruchamiając następujące polecenie:

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> Ten nowy klucz 2048-bitowy ma wpływ na działanie narzędzia RotateOnDate i będzie wysyłać wiadomości e-mail z pośrednim kluczem 1024-bitowym. Po czterech dniach możesz ponownie przetestować za pomocą klawisza 2048-bitowego (to oznacza, że gdy obrót zostanie wprowadzone do drugiego selektora).

Jeśli chcesz obrócić do drugiego selektora, po upływie czterech dni i potwierdzeniu, że jest w użyciu 2048-bitowa kompletność, ręcznie obróć drugi klawisz selektora przy użyciu odpowiedniego polecenia cmdlet wymienionego powyżej.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz następujące artykuły: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig), [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig) i [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>Czynności wykonywane w celu ręcznego skonfigurowania DKIM
<a name="SetUpDKIMO365"> </a>

Aby skonfigurować aplikację DKIM, wykonaj następujące czynności:

- [Publikowanie dwóch rekordów CNAME dla domeny niestandardowej w systemie DNS](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [Włączanie podpisywania DKIM dla domeny niestandardowej](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>Publikowanie dwóch rekordów CNAME dla domeny niestandardowej w systemie DNS
<a name="Publish2CNAME"> </a>

Dla każdej domeny, dla której chcesz dodać podpis DKIM w systemie DNS, musisz opublikować dwa rekordy CNAME.

> [!NOTE]
> Jeśli nie został przeczytany cały artykuł, być może nie zostały pominięte informacje o połączeniu programu PowerShell oszczędzające czas: Połączenie do Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Uruchom następujące polecenia w programie Exchange Online PowerShell, aby utworzyć rekordy selektora:

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

Jeśli zainicjowano domeny niestandardowe poza domeną początkową w Microsoft 365, musisz opublikować dwa rekordy CNAME dla każdej dodatkowej domeny. Dlatego, jeśli masz dwie domeny, musisz opublikować dwa dodatkowe rekordy CNAME i tak dalej.

Użyj następującego formatu dla rekordów CNAME.

> [!IMPORTANT]
> Jeśli jesteś jednym z naszych GCC High, inaczej obliczamy wartość _customDomainIdentifier_! Zamiast szukać rekordu MX dla twojej _początkowejDomeny_ w celu obliczenia _wartości customDomainIdentifier_, zamiast tego obliczamy go bezpośrednio z domeny niestandardowej. Jeśli na przykład domeną niestandardową jest "contoso.com" Twoja _domena_ _niestandardowaIdentifier_ staje się "contoso-com", wszystkie kropki są zamieniane na kreskę. Niezależnie od rekordu MX, na który  wskazuje Twoja początkowadomena, zawsze użyjesz powyższej metody do obliczenia wartości _customDomainIdentifier_ do użycia w rekordach CNAME.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600
```

Gdzie:

- Dla Microsoft 365 selektorami zawsze będą "selektor1" lub "selektor2".
- _CustomDomainIdentifier_ jest tym samym co _customDomainIdentifier_ w niestandardowym rekordzie MX domeny niestandardowej, który pojawia się przed mail.protection.outlook.com. Na przykład w następującym rekordzie MX domeny contoso.com adres __niestandardowyDomainIdentifier_ to contoso-com:

  > contoso.com.  3600 IN MX 5 contoso-com.mail.protection.outlook.com

- _initialDomain_ to domena, która była używana podczas rejestracji w u Microsoft 365. Domeny początkowe zawsze kończą się na onmicrosoft.com. Aby uzyskać informacje dotyczące określania domeny początkowej, zobacz Często [zadawane pytania dotyczące domen](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Jeśli na przykład masz początkową domenę cohovineyardandwinery.onmicrosoft.com oraz dwie domeny niestandardowe cohovineyard.com i cohowinery.com, musisz skonfigurować dwa rekordy CNAME dla każdej dodatkowej domeny w sumie cztery rekordy CNAME.

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
> Ważne jest utworzenie drugiego rekordu, ale w momencie tworzenia może być dostępny tylko jeden selektor. Drugi selektor może w zasadzie oznaczać adres, który jeszcze nie został utworzony. Nadal zalecamy utworzenie drugiego rekordu CNAME, ponieważ obrót klawisza będzie bezproblemowy.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>Procedura włączania podpisywania DKIM dla domeny niestandardowej
<a name="EnableDKIMinO365"> </a>

Po opublikowaniu rekordów CNAME w systemie DNS możesz włączyć podpisywanie DKIM za pośrednictwem Microsoft 365. Możesz to zrobić za pośrednictwem centrum administracyjne platformy Microsoft 365 lub przy użyciu programu PowerShell.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>Aby włączyć podpisywanie DKIM dla domeny niestandardowej w Microsoft 365 Defender sieci Microsoft 365 Defender sieci

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź do sekcji **&-mail** \> i  zasad & **zasad** \>  \> zagrożeń **DKIM**. Aby przejść bezpośrednio do strony DKIM, użyj funkcji <https://security.microsoft.com/dkimv2>.

2. Na **stronie DKIM** wybierz domenę, klikając jej nazwę.

3. W wyświetlonym wysuwanym czacie szczegółów zmień ustawienie Podpisz wiadomości dla tej domeny z podpisami **DKIM** na **Włączone (**![włącz).](../../media/scc-toggle-on.png)

   Po zakończeniu kliknij pozycję Obróć **klawisze DKIM**.

4. Powtórz te czynności dla każdej domeny niestandardowej.

5. Jeśli konfigurujesz funkcję DKIM po raz pierwszy i jest wyświetlany komunikat o błędzie "Nie zapisano kluczy DKIM dla tej domeny", musisz użyć usługi Windows PowerShell do włączenia podpisywania DKIM zgodnie z objaśnidaniem w następnym kroku.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>Aby włączyć podpisywanie DKIM dla domeny niestandardowej przy użyciu programu PowerShell

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="Błąd &quot;Nie zapisano kluczy DKIM dla tej domeny&quot;.":::
> Jeśli konfigurujesz usługę DKIM po raz pierwszy i zostanie wyświetlony komunikat o błędzie "Brak kluczy DKIM zapisanych dla tej domeny" wykonaj poniższe polecenie w kroku 2 ( `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`na przykład ), aby zobaczyć klucz.

1. [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Należy stosować następującą składnię:

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> to nazwa domeny niestandardowej, dla której chcesz włączyć podpisywanie DKIM.

   W tym przykładzie funkcja podpisywania DKIM dla domeny contoso.com:

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>Aby potwierdzić, że podpisywanie DKIM jest poprawnie skonfigurowane dla Microsoft 365

Przed rozpoczęciem tej procedury odczekaj kilka minut, aby potwierdzić, że DKIM został poprawnie skonfigurowany. Dzięki temu informacje DKIM dotyczące domeny mogą być rozłożone w całej sieci.

- Wyślij wiadomość z konta w Twojej domenie Microsoft 365 domenie z obsługą funkcji DKIM na inne konto e-mail, takie jak outlook.com lub Hotmail.com.
- Nie używaj konta aol.com do celów testowych. Jeśli sprawdzanie SPF przejdzie, w uście AOL może zostać pominięte sprawdzanie DKIM. Spowoduje to zerową wartość testu.
- Otwórz wiadomość i spójrz na nagłówek. Instrukcje dotyczące wyświetlania nagłówka wiadomości będą się różnić w zależności od klienta wiadomości. Aby uzyskać instrukcje dotyczące wyświetlania nagłówków wiadomości w programie Outlook, [zobacz Wyświetlanie nagłówków wiadomości internetowych w programie Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

  Wiadomość podpisana przez DKIM będzie zawierać nazwę hosta i domenę zdefiniowaną podczas opublikowania wpisów CNAME. Wiadomość będzie wyglądać podobnie do tego przykładu:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- Odszukaj Authentication-Results nagłówka. Mimo że każda usługa odbieraca stempluje pocztę przychodzącą w innym formacie, wyniki powinny przypominać **DKIM=pass** lub **DKIM=OK**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>Aby skonfigurować DKIM dla więcej niż jednej domeny niestandardowej
<a name="DKIMMultiDomain"> </a>

Jeśli w przyszłości zdecydujesz się dodać kolejną domenę niestandardową i chcesz włączyć funkcję DKIM dla nowej domeny, musisz wykonać czynności opisane w tym artykule dla każdej domeny. W szczególności wykonaj wszystkie czynności opisane w [tece Co należy zrobić, aby ręcznie skonfigurować DKIM](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>Wyłączanie zasad podpisywania DKIM dla domeny niestandardowej
<a name="DisableDKIMSigningPolicy"> </a>

Wyłączenie zasad podpisywania nie powoduje całkowitego wyłączenia funkcji DKIM. Po upływie tego czasu Microsoft 365 będą automatycznie stosowane zasady domyślne dla Twojej domeny, jeśli zasady domyślne nadal są w stanie włączone. Jeśli chcesz całkowicie wyłączyć funkcję DKIM, musisz wyłączyć funkcję DKIM zarówno w domenach niestandardowych, jak i w domenach domyślnych. Aby uzyskać więcej informacji, [zobacz Zachowanie domyślne dla aplikacji DKIM i Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

### <a name="to-disable-the-dkim-signing-policy-by-using-windows-powershell"></a>Aby wyłączyć zasady podpisywania DKIM przy użyciu Windows PowerShell

1. [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

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

## <a name="default-behavior-for-dkim-and-microsoft-365"></a>Domyślne zachowanie dla danych DKIM i Microsoft 365
<a name="DefaultDKIMbehavior"> </a>

Jeśli nie włączysz funkcji DKIM, program Microsoft 365 automatycznie utworzy 2048-bitowy klucz publiczny DKIM dla adresu routingu poczty e-mail w witrynie Microsoft Online Routing Address (MOERA)/domeny początkowej i skojarzonego klucza prywatnego, który przechowujemy wewnętrznie w naszym centrum danych. Domyślnie program Microsoft 365 używa domyślnej konfiguracji podpisywania dla domen, które nie mają zasad. Oznacza to, że jeśli nie skonfigurujesz funkcji DKIM samodzielnie, Microsoft 365 będzie używać domyślnych zasad i kluczy, które tworzy, aby włączyć funkcję DKIM dla Twojej domeny.

Ponadto, jeśli wyłączysz podpisywanie DKIM w domenie niestandardowej po jej włączeniu, po upływie okresu czasu Microsoft 365 automatycznie zastosuje zasady MOERA/początkowej domeny dla Twojej domeny niestandardowej.

W poniższym przykładzie załóżmy, że funkcja DKIM dla programu fabrikam.com została włączona przez Microsoft 365, a nie przez administratora domeny. Oznacza to, że wymagane nazwy CNAM nie istnieją w systemie DNS. Podpisy DKIM dla wiadomości e-mail z tej domeny będą wyglądać podobnie do tych:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

W tym przykładzie nazwa hosta i domena zawierają wartości, do których nazwa CNAME wskazuje, jeśli podpisywanie DKIM dla fabrikam.com zostało włączone przez administratora domeny. Po pewnym czasie każda wiadomość wysłana z Microsoft 365 będzie podpisana przez DKIM. Jeśli włączysz funkcję DKIM samodzielnie, w tym przypadku domena będzie taka sama jak domena w adresie Od, w tym fabrikam.com. Jeśli nie, nie będzie on wyrównany i będzie używać domeny początkowej organizacji. Aby uzyskać informacje dotyczące określania domeny początkowej, zobacz Często [zadawane pytania dotyczące domen](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>Konfigurowanie usługi DKIM w celu wysyłania lub fałszowania wiadomości e-mail w imieniu domeny niestandardowej przez usługę innej firmy
<a name="SetUp3rdPartyspoof"> </a>

Niektórzy dostawcy zbiorczych usług poczty e-mail lub dostawcy oprogramowania jako usługi umożliwiają skonfigurowanie kluczy DKIM dla wiadomości e-mail pochodzących z ich usług. W celu skonfigurowania wymaganych rekordów DNS wymaga to koordynacji działań ze strony firmy i innej firmy. Niektóre serwery innych firm mogą mieć własne rekordy CNAME z różnymi selektorami. Dwie organizacje nie robią tego dokładnie tak samo. Ten proces zależy w pełni od organizacji.

Przykładowy komunikat przedstawiający poprawnie skonfigurowaną aplikację DKIM dla contoso.com i bulkemailprovider.com może wyglądać tak:

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

W tym przykładzie w celu osiągnięcia tego wyniku:

1. Zbiorczy dostawca poczty e-mail nadał firmie Contoso publiczny klucz DKIM.

2. Firma Contoso opublikowała klucz DKIM w swoim rekordzie DNS.

3. Podczas wysyłania wiadomości e-mail zbiorczy dostawca poczty e-mail podpisuje klucz z odpowiadającym mu kluczem prywatnym. W ten sposób zbiorczy dostawca poczty e-mail dodał podpis DKIM do nagłówka wiadomości.

4. Odbieranie systemów poczty e-mail wykonuje sprawdzanie DKIM, uwierzytelniając wartość DKIM-Signature d=\<domain\> dla domeny w adresie From (5322.From) wiadomości. W tym przykładzie wartości są zgodne:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>Identyfikowanie domen, które nie wysyłają wiadomości e-mail

Organizacje powinny jawnie określać, czy domena nie wysyła wiadomości e-mail, `v=DKIM1; p=` określając w rekordzie DKIM dla tych domen. Zaleca się, aby serwery poczty e-mail nie były prawidłowe klucze publiczne dla tej domeny, a wszystkie wiadomości e-mail, które podszywają się pod tę domenę, powinny zostać odrzucone. Należy to zrobić dla każdej domeny i poddomeny przy użyciu symbolu wieloznacznego DKIM.

Na przykład rekord DKIM będzie wyglądał tak:

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>Następne kroki: Po skonfigurowaniu DKIM dla Microsoft 365
<a name="DKIMNextSteps"> </a>

**Chociaż zadaniem DKIM jest zapobieganie fałszersce, DKIM działa lepiej z SPF i DMARC.**

Po skonfigurowaniu DKIM, jeśli spf nie został jeszcze ustawiony, zrób to. Aby uzyskać krótkie wprowadzenie do SPF i skonfigurować go szybko, zobacz Konfigurowanie spf w programie [**Microsoft 365 zapobiegania fałszersprowadzeniu**](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Aby uzyskać bardziej szczegółowe informacje na temat sposobu, w jaki program Microsoft 365 korzysta z SPF, lub na potrzeby rozwiązywania problemów lub wdrożeń niestandardowych, takich jak wdrożenia hybrydowe, zacznij od tematu Jak program Microsoft 365 używa struktury zasad dotyczących nadawców [(SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) w celu zapobiegania fałszowania.

Następnie zobacz Używanie funkcji [**DMARC do sprawdzania poprawności wiadomości e-mail**](use-dmarc-to-validate-email.md). [Nagłówki wiadomości spamu](anti-spam-message-headers.md) zawierają składnię i pola nagłówków używane przez program Microsoft 365 do sprawdzania DKIM.

**Ten test sprawdzi,** czy konfiguracja podpisywania DKIM została prawidłowo skonfigurowana i czy zostały opublikowane odpowiednie wpisy DNS.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">Uruchom testy: DKIM</a></p>
</div>

## <a name="more-information"></a>Więcej informacji

Obrót klawiszy za pośrednictwem programu PowerShell: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail](use-dmarc-to-validate-email.md)
