---
title: Starsze informacje dla Szyfrowanie wiadomości usługi Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 05/22/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.assetid: 5986b9e1-c824-4f8f-9b7d-a2b0ae2a7fe9
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Dowiedz się, jak przejść starsze pliki do Szyfrowanie wiadomości usługi Office 365 (OME) dla organizacji.
ms.openlocfilehash: 6213aec3edd8d55c21ba4137a2052b08147aedc3
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009697"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Starsze informacje dla Szyfrowanie wiadomości usługi Office 365

Jeśli jeszcze nie przeniesiono organizacji do nowych funkcji usługi OME, ale już wdrożono usługę OME, informacje zawarte w tym artykule dotyczą Twojej organizacji. Firma Microsoft zaleca zaplanowanie przeniesienia się do nowych funkcji OME, gdy tylko będzie to uzasadnione dla Twojej organizacji. Aby uzyskać instrukcje, [zobacz Konfigurowanie nowych funkcji Szyfrowanie wiadomości usługi Office 365 wbudowanych w usługę Azure Information Protection](set-up-new-message-encryption-capabilities.md). Jeśli chcesz dowiedzieć się więcej o tym, jak nowe funkcje działają najpierw[, zobacz Szyfrowanie wiadomości usługi Office 365](ome.md). Pozostała część tego artykułu dotyczy zachowania funkcji OME przed wydaniem nowych funkcji OME.

Dzięki Szyfrowanie wiadomości usługi Office 365 Twoja organizacja może wysyłać i odbierać zaszyfrowane wiadomości e-mail między osobami w organizacji i poza nią. Szyfrowanie wiadomości usługi Office 365 z usługami Outlook.com, Yahoo i Gmail oraz z innymi usługami poczty e-mail. Szyfrowanie wiadomości e-mail pozwala zagwarantować, że tylko zamierzony adresaci mogą wyświetlać zawartość wiadomości.

Oto kilka przykładów:

- Pracownik banku wysyła wyciągi z kart kredytowych klientom
- Przedstawiciel firmy ubezpieczeniowych podaje klientom szczegóły zasad
- Doradca kredytów hipotecznych żąda od klienta informacji finansowych dotyczących wniosku o pożyczkę
- Dostawca usług opieki zdrowotnej wysyła informacje o opieki zdrowotnej do pacjentów
- Prawni prawnicy wysyła informacje poufne do klienta lub innego pełnomocnika

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>Jak Szyfrowanie wiadomości usługi Office 365 działa bez nowych możliwości

Szyfrowanie wiadomości usługi Office 365 to usługa online wbudowana w usługę Microsoft Azure rights Management (Azure RMS). Za pomocą usługi Azure RMS administratorzy mogą definiować reguły przepływu poczty e-mail w celu określenia warunków szyfrowania. Na przykład reguła może wymagać szyfrowania wszystkich wiadomości zaadresowanych do określonego adresata.

Gdy ktoś wysyła wiadomość e-mail w Exchange Online, która jest inna niż reguła szyfrowania, jest ona wysyłana z załącznikiem HTML. Adresat otworzy załącznik HTML i rozpocznie przeglądanie zaszyfrowanej wiadomości w Szyfrowanie wiadomości usługi Office 365 html. Adresat może wybrać opcję wyświetlenia wiadomości, logując się za pomocą konta Microsoft lub konta służbowego skojarzonego z programem Office 365, albo przy użyciu kodu zdatowego. Obie opcje zapewniają, że tylko zamierzony adresat będzie miał możliwość wyświetlenia zaszyfrowanej wiadomości. Ten proces jest bardzo inny w przypadku nowych funkcji OME.

Na poniższym diagramie podsumowano fragment wiadomości e-mail w procesie szyfrowania i odszyfrowywania.

![Diagram przedstawiający ścieżkę zaszyfrowanej wiadomości e-mail.](../media/O365-Office365MessageEncryption-Concept.png)

Aby uzyskać więcej informacji, zobacz Informacje o usłudze dla starszych Szyfrowanie wiadomości usługi Office 365 wersji przed wydaniem [nowych funkcji OME](legacy-information-for-message-encryption.md#LegacyServiceInfo).

## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities"></a>Definiowanie reguł przepływu poczty e Szyfrowanie wiadomości usługi Office 365 które nie korzystają z nowych funkcji OME

Aby umożliwić Szyfrowanie wiadomości usługi Office 365 bez nowych możliwości, administratorzy Exchange Online i administratorzy Exchange Online Protection definiować Exchange przepływu poczty e-mail. Te reguły określają, na jakich warunkach wiadomości e-mail powinny być szyfrowane, a także warunki usuwania szyfrowania wiadomości. Gdy dla reguły jest ustawiona akcja szyfrowania, usługa wykonuje akcję na wszystkich wiadomościach, które są zgodne z regułą, przed wysłaniem wiadomości.

Elastyczne reguły przepływu poczty e-mail pozwalającą łączyć warunki, dzięki czemu można spełnić określone wymagania dotyczące zabezpieczeń w ramach jednej reguły. Można na przykład utworzyć regułę szyfrowania wszystkich wiadomości zawierających określone słowa kluczowe i zaadresowanych do adresatów zewnętrznych. Szyfrowanie wiadomości usługi Office 365 także szyfruje odpowiedzi od adresatów zaszyfrowanych wiadomości e-mail i możesz utworzyć regułę odszyfrowywania tych odpowiedzi dla użytkowników poczty e-mail. Dzięki temu użytkownicy w Twojej organizacji nie będą muszą logować się do portalu szyfrowania, aby wyświetlać odpowiedzi.

Aby uzyskać więcej informacji na temat tworzenia reguł przepływu Exchange, zobacz [Definiowanie reguł dla Szyfrowanie wiadomości usługi Office 365](define-mail-flow-rules-to-encrypt-email.md).

### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Tworzenie reguły przepływu poczty e-mail w celu szyfrowania wiadomości e-mail bez nowych funkcji usługi OME za pomocą Usługi EAC

1. W przeglądarce internetowej, używając konta służbowego, które otrzymało uprawnienia administratora globalnego[, zaloguj](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) się w celu Office 365.

2. Wybierz **kafelek Administrator** .

3. W centrum administracyjne platformy Microsoft 365 wybierz pozycję **Centra administracyjne Exchange**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>

4. W selektorze wiadomości e-mail przejdź do **menu Reguły przepływu** \> **poczty e-mail** i wybierz **ikonę Nowy** ![nowy.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Utwórz nową regułę**. Aby uzyskać więcej informacji na temat korzystania z Centrum administracyjnego programu Exchange [centrum administracyjnego w programie Exchange Online](/exchange/exchange-admin-center).

5. W **imieniu** i nazwisku wpisz nazwę reguły, na przykład Szyfruj pocztę dla DrToniRamos@hotmail.com.

6. W **polecej Zastosuj tę** regułę, jeśli wybierz warunek, a następnie w razie potrzeby wprowadź wartość. Aby na przykład zaszyfrować wiadomości do DrToniRamos@hotmail.com:

   1. W **polecej Zastosuj tę regułę**, jeśli wybierz **adresatem jest**.

   2. Wybierz istniejącą nazwę z listy kontaktów lub wpisz nowy adres e-mail w **polu nazw pól wyboru** .

      - Aby wybrać istniejącą nazwę, wybierz ją z listy, a następnie kliknij przycisk **OK**.

      - Aby wprowadzić nową nazwę, wpisz adres e-mail w  polu nazwy, a następnie wybierz pozycję **Sprawdź nazwy OK**\>.

7. Aby dodać więcej warunków, wybierz pozycję **Więcej opcji** , a następnie wybierz **pozycję Dodaj warunek** i wybierz pozycję z listy.

   Aby na przykład zastosować regułę tylko wtedy, gdy adresat znajduje się poza organizacją, wybierz  pozycję dodaj warunek, a następnie wybierz pozycję Adresat jest zewnętrzny **/** \> wewnętrzny Poza **organizacją** \> **OK**.

8. Aby włączyć szyfrowanie bez używania nowych funkcji OME,  \> w poniższej czynności wybierz pozycję Modyfikuj zabezpieczenia wiadomości Zastosuj poprzednią wersję **OME**, a następnie wybierz pozycję **Zapisz**.

   Jeśli zostanie wyświetlony komunikat o błędzie, że nie włączono licencjonowania usługi IRM, oznacza to, że nie używasz starszej wersji usługi OME.

9. (Opcjonalnie) Wybierz **pozycję dodaj akcję** , aby określić inną akcję.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Użyj Exchange Online PowerShell, aby utworzyć regułę przepływu poczty e-mail na potrzeby szyfrowania wiadomości e-mail bez nowych funkcji OME

1. Połącz się z usługą Exchange Online w programie PowerShell. Aby uzyskać więcej informacji, zobacz [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utwórz regułę przy użyciu polecenia cmdlet **New-TransportRule** i ustaw dla _parametru ApplyOME_ wartość `$true`.

   W tym przykładzie wymagane jest zaszyfrowanie DrToniRamos@hotmail.com e-mail wysyłanych na adresy e-mail.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   Gdzie,

   - Unikatowa nazwa nowej reguły to "Szyfruj regułę dla Dr Toni Ramos".
   - Parametr _SentTo_ określa adresatów wiadomości (identyfikowanych za pomocą nazwy, adresu e-mail, nazwy odróżniaowej itp.). W tym przykładzie adresat jest identyfikowany za pomocą adresu e-mail "adres e-DrToniRamos@hotmail.com".
   - Parametr _SentToScope_ określa lokalizację adresatów wiadomości. W tym przykładzie skrzynka pocztowa adresata znajduje się w usłudze hotmail i nie należy do organizacji, więc jest `NotInOrganization` używana ta wartość.

   Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Polecenie New-TransportRule](/powershell/module/exchange/New-TransportRule).

### <a name="remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Usuwanie szyfrowania z odpowiedzi e-mail zaszyfrowanych bez nowych funkcji OME

Gdy użytkownicy poczty e-mail wysyłają zaszyfrowane wiadomości, adresaci tych wiadomości mogą odpowiadać za pomocą zaszyfrowanych odpowiedzi. Możesz utworzyć reguły przepływu poczty e-mail, aby automatycznie usuwać szyfrowanie z odpowiedzi, dzięki czemu użytkownicy poczty e-mail w Twojej organizacji nie muszą logować się do portalu szyfrowania, aby je wyświetlać. Aby zdefiniować te reguły, możesz użyć Windows PowerShell EAC lub polecenia cmdlet. Możesz odszyfrować wiadomości wysłane z Twojej organizacji lub wiadomości, które są odpowiedziami na wiadomości wysłane z twojej organizacji. Nie można odszyfrowywać zaszyfrowanych wiadomości pochodzących spoza organizacji.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Tworzenie reguły w celu usuwania szyfrowania odpowiedzi e-mail zaszyfrowanych bez nowych funkcji OME za pomocą SAC

1. W przeglądarce internetowej, używając konta służbowego, które otrzymało uprawnienia administratora, [zaloguj](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) się w celu Office 365.

2. Wybierz **kafelek Administrator** .

3. W >centrum administracyjne platformy Microsoft 365 wybierz pozycję **Centra administracyjne Exchange**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>

4. W selektorze wiadomości e-mail przejdź do **menu Reguły przepływu** \> **poczty e-mail** i wybierz **ikonę Nowy** ![nowy.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Utwórz nową regułę**. Aby uzyskać więcej informacji na temat korzystania z Centrum administracyjnego programu Exchange [centrum administracyjnego w programie Exchange Online](/exchange/exchange-admin-center).

5. W **nazwie** wpisz nazwę reguły, na przykład Usuń szyfrowanie z poczty przychodzącej.

6. W **tece Zastosuj tę regułę, jeśli** wybierz warunki, do których wiadomości ma zostać usunięte  szyfrowanie, \> na przykład Adresat znajduje się **w organizacji**.

7. W **aplikacji Wykonaj następujące czynności** wybierz **pozycję Modyfikuj zabezpieczenia wiadomości** \> **Usuń poprzednią wersję usługi OME**.

8. Wybierz **Zapisz**.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Tworzenie Exchange Online PowerShell w celu usunięcia szyfrowania odpowiedzi e-mail zaszyfrowanych bez nowych funkcji OME

1. Połącz się z usługą Exchange Online w programie PowerShell. Aby uzyskać więcej informacji, zobacz [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utwórz regułę przy użyciu polecenia cmdlet **New-TransportRule** i ustaw dla _parametru RemoveOME_ wartość `$true`.

   W tym przykładzie usuwane jest szyfrowanie wszystkich wiadomości wysyłanych do adresatów w organizacji.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   Gdzie,

   - Unikatowa nazwa nowej reguły to "Usuwanie szyfrowania z poczty przychodzącej".
   - Parametr _SentToScope_ określa lokalizację adresatów wiadomości. W tym przykładzie jest używana `InOrganization` wartość, która wskazuje jedną z następujących wartości:
     - Adresat jest skrzynką pocztową, użytkownikiem poczty, grupą lub folderem publicznym z obsługą poczty w organizacji.
     - Adres e-mail adresata znajduje się w zaakceptowanych domenach skonfigurowanych jako domena autorytatywna lub domena przekazywania wewnętrznego w _organizacji, a_ wiadomość została wysłana lub odebrana za pośrednictwem uwierzytelnionego połączenia.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Polecenie New-TransportRule](/powershell/module/exchange/New-TransportRule).

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>Wysyłanie, wyświetlanie i odpowiadanie na wiadomości zaszyfrowane bez nowych możliwości

W Szyfrowanie wiadomości usługi Office 365 wiadomości e-mail są szyfrowane automatycznie na podstawie reguł zdefiniowanych przez administratora. Wiadomość e-mail z zaszyfrowaną wiadomością jest dołączona do Skrzynki odbiorczej adresata wraz z dołączonym plikiem HTML.

Adresaci postępują zgodnie z instrukcjami w wiadomości, aby otworzyć załącznik i uwierzytelnić się przy użyciu konta Microsoft lub konta służbowego skojarzonego z programem Office 365. Adresaci, którzy nie mają obu kont, zostaną skierowani do utworzenia konta Microsoft, które pozwoli im zalogować się w celu wyświetlenia zaszyfrowanej wiadomości. Adresaci mogą również uzyskać kod dostępu w celu wyświetlenia wiadomości. Po zalogowaniu się lub użyciu kodu w postaci hasła czasowego adresaci mogą wyświetlić odszyfrowaną wiadomość i wysłać zaszyfrowaną odpowiedź.

## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>Dostosowywanie zaszyfrowanych wiadomości za pomocą Szyfrowanie wiadomości usługi Office 365

Jako administrator Exchange Online i administrator Exchange Online Protection, możesz dostosowywać zaszyfrowane wiadomości. Możesz na przykład dodać markę i logo firmy, określić wprowadzenie i dodać tekst zastrzeżenia w zaszyfrowanych wiadomościach oraz w portalu, w którym odbiorcy mogą wyświetlać zaszyfrowane wiadomości. Używając Windows PowerShell cmdlet, możesz dostosować następujące aspekty wyświetlania dla adresatów zaszyfrowanych wiadomości e-mail:

- Tekst wprowadzający wiadomości e-mail zawierającej zaszyfrowaną wiadomość
- Tekst zastrzeżenia w wiadomości e-mail zawierającej zaszyfrowaną wiadomość
- Tekst portalu wyświetlany w portalu wyświetlania wiadomości
- Logo, które będzie wyświetlane w wiadomości e-mail i wyświetlaniu portalu

W dowolnym momencie możesz także przywrócić domyślny wygląd i sposób pracy.

W poniższym przykładzie pokazano niestandardowe logo dla domeny ContosoPharma w załączniku wiadomości e-mail:

> [!div class="mx-imgBorder"]
> ![Przykład zaszyfrowanej strony wiadomości widoku.](../media/TA-OME-3attachment2.jpg)

### <a name="to-customize-encryption-email-messages-and-the-encryption-portal-with-your-organizations-brand"></a>Aby dostosować wiadomości e-mail szyfrowania i portal szyfrowania przy użyciu marki organizacji

1. Połączenie użyć Exchange Online PowerShell w sposób opisany Połączenie, Exchange Online [zdalny program PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj polecenia cmdlet Set-OMEConfiguration zgodnie z poniższym opisem: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) lub skorzystaj z poniższej tabeli, aby uzyskać wskazówki.

   **Opcje dostosowywania szyfrowania**

   |Aby dostosować tę funkcję obsługi szyfrowania|Użyj tych Windows PowerShell poleceń|
   |---|---|
   |Tekst domyślny towarzyszący zaszyfrowanym wiadomościom e-mail <p> Tekst domyślny jest wyświetlany powyżej instrukcji dotyczących wyświetlania zaszyfrowanych wiadomości|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <p> **Przykład:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"`|
   |Oświadczenie o zrzeczeniu odpowiedzialności w wiadomości e-mail zawierającej zaszyfrowaną wiadomość|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <p> **Przykład:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"`|
   |Tekst wyświetlany w górnej części zaszyfrowanego portalu wyświetlania poczty|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <p> **Przykład:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <p> **Przykład:** `Set-OMEConfiguration -Identity "OME configuration" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Obsługiwane formaty plików: .png, .jpg, .bmp lub tiff <p> Optymalny rozmiar pliku logo: mniej niż 40 KB <p> Optymalny rozmiar obrazu logo: 170x70 pikseli|

### <a name="to-remove-brand-customizations-from-encryption-email-messages-and-the-encryption-portal"></a>Aby usunąć dostosowania marki z wiadomości e-mail szyfrowania i portalu szyfrowania

1. Połączenie użyć Exchange Online PowerShell w sposób opisany Połączenie, Exchange Online [zdalny program PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj polecenia cmdlet Set-OMEConfiguration w sposób opisany tutaj: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration). Aby usunąć znakowane dostosowania organizacji z wartości DisclaimerText, EmailText i PortalText, ustaw dla tej wartości pusty ciąg. `""` Dla wszystkich wartości obrazów, takich jak Logo, ustaw wartość .`"$null"`

   **Opcje dostosowywania szyfrowania**

   |Aby przywrócić domyślną funkcję szyfrowania do domyślnego tekstu i obrazu|Użyj tych Windows PowerShell poleceń|
   |---|---|
   |Tekst domyślny towarzyszący zaszyfrowanym wiadomościom e-mail <p> Tekst domyślny jest wyświetlany powyżej instrukcji dotyczących wyświetlania zaszyfrowanych wiadomości|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <p> **Przykład:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Oświadczenie o zrzeczeniu odpowiedzialności w wiadomości e-mail zawierającej zaszyfrowaną wiadomość <p> |`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <p> **Przykład:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Tekst wyświetlany w górnej części zaszyfrowanego portalu wyświetlania poczty|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <p> **Przykład przywracania domyślnego ustawienia:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <p> **Przykład przywracania domyślnego ustawienia:** `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>Informacje o usłudze dla starszych Szyfrowanie wiadomości usługi Office 365 wersji przed wydaniem nowych funkcji OME
<a name="LegacyServiceInfo"> </a>

W poniższej tabeli przedstawiono szczegóły techniczne Szyfrowanie wiadomości usługi Office 365 usługi przed wydaniem nowych funkcji usługi OME.

|Szczegóły usługi|Opis|
|---|---|
|Wymagania dotyczące urządzeń klienckich|Zaszyfrowane wiadomości można wyświetlać na dowolnym urządzeniu klienckim, o ile załącznik HTML można otworzyć w nowoczesnej przeglądarce obsługującej wpis formularza.|
|Algorytm szyfrowania i zgodność z normami federalną przetwarzania informacji (FIPS, Federal Information Processing Standards)|Szyfrowanie wiadomości usługi Office 365 korzysta z tych samych kluczy szyfrowania co usługa Windows Azure Information Rights Management (IRM) i obsługuje tryb kryptograficzny 2 (klucz 2K dla RSA i klucz 256 bitów dla systemów SHA-1). Aby uzyskać więcej informacji na temat podstawowych trybów szyfrowania usługi IRM, zobacz Tryby [kryptograficzne usługi AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
|Obsługiwane typy wiadomości|Szyfrowanie wiadomości usługi Office 365 jest obsługiwane tylko w przypadku elementów, które mają identyfikator klasy wiadomości usługi **IPM. Uwaga**. Aby uzyskać więcej informacji, zobacz [Typy elementów i klasy wiadomości](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Limity rozmiaru wiadomości|Szyfrowanie wiadomości usługi Office 365 szyfrować wiadomości o wysokości do 25 megabajtów. Aby uzyskać więcej szczegółowych informacji na temat limitów rozmiaru wiadomości, [zobacz Exchange Online Limity](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).|
|Exchange Online przechowywania poczty e-mail|Exchange Online wiadomości nie są przechowywane.|
|Obsługa języków dla Szyfrowanie wiadomości usługi Office 365|Office 365 szyfrowanie wiadomości obsługuje Microsoft 365, w następujący sposób: <p> Przychodzące wiadomości e-mail i dołączone pliki HTML są zlokalizowane w zależności od ustawień językowych nadawcy. <p> Portal wyświetlania jest zlokalizowany na podstawie ustawień przeglądarki adresata. <p> Treść (zawartości) zaszyfrowanej wiadomości nie jest zlokalizowany.|
|Informacje dotyczące prywatności dla portalu OME i aplikacji przeglądarka OME|Zasady [zachowania Office 365 dotyczące](https://privacy.microsoft.com/privacystatement) portalu szyfrowania wiadomości zawierają szczegółowe informacje o tym, co firma Microsoft robi z Twoimi informacjami prywatnymi, a czego nie.|

## <a name="frequently-asked-questions-about-legacy-ome"></a>Często zadawane pytania dotyczące starszego OME
<a name="LegacyServiceInfo"> </a>

Masz pytania dotyczące Szyfrowanie wiadomości usługi Office 365? Oto kilka odpowiedzi. Jeśli nie możesz znaleźć tego, czego potrzebujesz, sprawdź, czy na forach Community Microsoft [Tech Office 365](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365).

 **Q. Moi użytkownicy wysyłają zaszyfrowane wiadomości e-mail do adresatów spoza naszej organizacji. Czy istnieją jakkolwiek działania, które muszą wykonać adresaci zewnętrzni, aby móc odczytywać wiadomości e-mail zaszyfrowane przy użyciu Szyfrowanie wiadomości usługi Office 365?**

Adresaci spoza organizacji, którzy Microsoft 365 zaszyfrowanych wiadomości, mogą je wyświetlać na jeden z dwóch sposobów:

- Logując się za pomocą konta Microsoft lub konta służbowego skojarzonego z usługą Office 365.

- Przy użyciu kodu zdajętego jeden raz.

 **Q. Czy Microsoft 365 przechowywane w chmurze czy na serwerach firmy Microsoft?**

Nie, zaszyfrowane wiadomości są przechowywane w systemie poczty e-mail adresata, a gdy adresat otworzy wiadomość, jest ona tymczasowo publikowana w celu wyświetlania na serwerach firmy Microsoft. Wiadomości nie są tam przechowywane.

 **Q. Czy mogę dostosowywać zaszyfrowane wiadomości e-mail marką?**

Tak. Za pomocą Windows PowerShell cmdlet możesz dostosować domyślny tekst wyświetlany u góry zaszyfrowanych wiadomości e-mail, tekstu zastrzeżenia i logo, którego chcesz używać w wiadomości e-mail i portalu szyfrowania. Ta funkcja jest teraz dostępna w omEv2. Aby uzyskać szczegółowe informacje, [zobacz Dodawanie marki do zaszyfrowanych wiadomości](add-your-organization-brand-to-encrypted-messages.md).

 **Q. Czy usługa wymaga licencji dla każdego użytkownika w mojej organizacji?**

Wymagana jest licencja dla każdego użytkownika w organizacji, który wysyła zaszyfrowaną wiadomość e-mail.

 **Q. Czy adresaci zewnętrzni wymagają subskrypcji?**

Nie, adresaci zewnętrzni nie wymagają subskrypcji, aby odczytywać zaszyfrowane wiadomości lub odpowiadać na nie.

 **Q. Czym różni Szyfrowanie wiadomości usługi Office 365 od usług zarządzania prawami (RMS)?**

Usługi RMS zapewniają funkcje ochrony praw do informacji w wewnętrznych wiadomościach e-mail organizacji, udostępniając wbudowane szablony, takie jak: Nie przesyłaj dalej i Poufne dane firmowe. Szyfrowanie wiadomości usługi Office 365 obsługuje szyfrowanie wiadomości e-mail w przypadku wiadomości wysyłanych zarówno do adresatów zewnętrznych, jak i wewnętrznych.

 **Q. Czym różni Szyfrowanie wiadomości usługi Office 365 od S/MIME?**

S/MIME to zasadniczo technologia szyfrowania po stronie klienta, która wymaga skomplikowanej infrastruktury zarządzania certyfikatami i publikowania. Szyfrowanie wiadomości usługi Office 365 są używane reguły przepływu poczty e-mail (nazywane także regułami transportu) i nie zależą od publikowania certyfikatów.

 **Q. Czy mogę odczytywać zaszyfrowane wiadomości na urządzeniach przenośnych?**

Tak, możesz wyświetlać wiadomości w systemach Android i iOS, pobierając aplikacje Przeglądarki OME ze sklepu Google Play i Apple App Store. Otwórz załącznik HTML w aplikacji Przeglądarka OME, a następnie postępuj zgodnie z instrukcjami, aby otworzyć zaszyfrowaną wiadomość. W przypadku innych urządzeń przenośnych możesz otworzyć załącznik HTML, o ile klient poczty obsługuje wpis formularza.

 **Q. Czy odpowiedzi i wiadomości przekazane są szyfrowane?**

Tak. Odpowiedzi będą nadal szyfrowane przez cały czas trwania wątku.

 **Q. Czy Szyfrowanie wiadomości usługi Office 365 lokalizacji?**

Przychodząca wiadomość e-mail i zawartość HTML są zlokalizowane na podstawie ustawień poczty e-mail nadawcy. Portal wyświetlania jest zlokalizowany na podstawie ustawień przeglądarki adresata. Jednak rzeczywista treść (zawartość) zaszyfrowanej wiadomości nie jest zlokalizowane.

 **Q. Jaka metoda szyfrowania jest używana w Szyfrowanie wiadomości usługi Office 365?**

Szyfrowanie wiadomości usługi Office 365 korzysta z usług zarządzania prawami dostępu (RMS) jako swojej infrastruktury szyfrowania. Używana metoda szyfrowania zależy od tego, gdzie uzyskasz klucze rms używane do szyfrowania i odszyfrowywania wiadomości.

- Jeśli za pomocą Microsoft Azure RMS uzyskujesz klucze, używany jest tryb kryptograficzny 2. Tryb kryptograficzny 2 to zaktualizowana i rozszerzona implementacja kryptograficzna usług AD RMS. Obsługuje on podpis i szyfrowanie RSA 2048, a także obsługuje podpis SHA-256.

- W przypadku używania usługi Active Directory (AD) RMS do uzyskania kluczy jest używany tryb kryptograficzny 1 lub tryb kryptograficzny 2. Używana metoda zależy od lokalnego wdrożenia usług AD RMS. Tryb kryptograficzny 1 to pierwotna implementacja kryptograficzna usług AD RMS. Obsługuje on RSA 1024 do podpisów i szyfrowania, a także obsługuje podpis SHA-1. Ten tryb będzie nadal obsługiwany przez wszystkie bieżące wersje usługi RMS.

Aby uzyskać więcej informacji, zobacz [Tryby kryptograficzne usług AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).

**Q. Dlaczego niektóre zaszyfrowane wiadomości wiedzą, że pochodzą z** Office365@messaging.microsoft.com?

Gdy zaszyfrowana odpowiedź jest wysyłana z portalu szyfrowania lub za pośrednictwem aplikacji Przeglądarka OME, wysyłający adres e-mail jest ustawiony na Office365@messaging.microsoft.com, ponieważ zaszyfrowana wiadomość jest wysyłana za pośrednictwem punktu końcowego firmy Microsoft. Pozwala to zapobiec oznaczaniu zaszyfrowanych wiadomości jako spamu. Nazwa wyświetlana w wiadomości e-mail i adres w portalu szyfrowania nie są zmieniane z powodu tej etykiety. Ponadto to etykiety mają zastosowanie tylko do wiadomości wysyłanych za pośrednictwem portalu, a nie za pośrednictwem żadnego innego klienta poczty e-mail.

 **Q. Mam subskrypcję usługi Exchange szyfrowanie hostowane (EHE). Gdzie mogę uzyskać więcej informacji na temat uaktualnienia do programu Szyfrowanie wiadomości usługi Office 365?**

Uaktualniono wszystkich klientów EHE do Szyfrowanie wiadomości usługi Office 365. Aby uzyskać więcej informacji, odwiedź [Exchange Hostowane Centrum uaktualniania szyfrowania](../security/office-365-security/exchange-online-protection-overview.md).

 **Q. Czy muszę otwierać adresy URL, adresy IP lub porty w zaporze mojej organizacji w celu obsługi Szyfrowanie wiadomości usługi Office 365?**

Tak. Aby włączyć uwierzytelnianie wiadomości zaszyfrowanych za pomocą Szyfrowanie wiadomości usługi Office 365, należy dodać adresy URL Exchange Online listy Szyfrowanie wiadomości usługi Office 365. Aby uzyskać listę adresów URL Exchange Online, zobacz Adresy [URL Microsoft 365 i zakresy adresów IP](../enterprise/urls-and-ip-address-ranges.md).

 **Q. Do ilu adresatów mogę wysłać Microsoft 365 zaszyfrowaną wiadomość?**

Limit adresatów wynosi 500 adresatów na wiadomość lub , w przypadku kombinacji po rozwinięciu listy dystrybucyjnej, 11 980 znaków w polu Do wiadomości, w zależności  od tego, co nastąpi najpierw.

 **Q. Czy można odwołać wiadomość wysłaną do określonego adresata?**

L.p. Nie można odwołać wiadomości do określonej osoby po jej wysłaniu.

 **Q. Czy można wyświetlić raport zaszyfrowanych wiadomości, które zostały odebrane i przeczytane?**

Nie ma raportu, który pokazuje, czy zaszyfrowana wiadomość została wyświetlona, ale są dostępne raporty programu Microsoft 365, które możesz wykorzystać do ustalenia liczby wiadomości, które pasują do określonej reguły przepływu poczty (nazywanej na przykład regułą transportu).

 **Q. Do czego firma Microsoft dostarcza informacje podane za pośrednictwem portalu OME i aplikacji przeglądarka OME?**

Zasady [zachowania Office 365 dotyczące](https://privacy.microsoft.com/privacystatement) portalu szyfrowania wiadomości zawierają szczegółowe informacje o tym, co firma Microsoft robi z Twoimi informacjami prywatnymi, a czego nie.

**Q. Co zrobić, jeśli po żądaniu kodu nie otrzymam kodu w terminie?**

Najpierw sprawdź folder wiadomości-śmieci lub spam w kliencie poczty e-mail. Ustawienia DKIM i DMARC w Twojej organizacji mogą powodować, że te wiadomości e-mail będą filtrowane jako spam.

Następnie sprawdź kwarantannę w Centrum & zgodności. Często wiadomości zawierające kod wytyczysz w miejscu kwarantanny, zwłaszcza te, które są odbierane przez Twoją organizację jako pierwsze.
