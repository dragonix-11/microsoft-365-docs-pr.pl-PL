---
title: Dodawanie marki organizacji do zaszyfrowanych wiadomości
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 4/1/2020
search.appverid:
- MET150
- MOE150
ms.assetid: 7a29260d-2959-42aa-8916-feceff6ee51d
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Dowiedz się Office 365, jak administratorzy globalni mogą zastosować znakowanie Twojej organizacji do zaszyfrowanych & e-mail w portalu szyfrowania.
ms.openlocfilehash: b96f87886b6f1dc5ca78de068b86dbbcfb9e460d
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009684"
---
# <a name="add-your-organizations-brand-to-your-microsoft-365-for-business-message-encryption-encrypted-messages"></a>Dodawanie marki organizacji do wiadomości szyfrowanych Microsoft 365 wiadomości szyfrowanie wiadomości dla firm

Możesz zastosować znakowanie firmowe, aby dostosować wygląd wiadomości e-mail organizacji i portalu szyfrowania. Aby rozpocząć, musisz zastosować uprawnienia administratora globalnego do swojego konta służbowego. Gdy masz te uprawnienia, dostosuj te części zaszyfrowanych wiadomości e-Get-OMEConfiguration i Set-OMEConfiguration Windows PowerShell cmdlet:

- Tekst wprowadzający
- Tekst zastrzeżenia
- Adres URL zasad zachowania poufności informacji twojej organizacji
- Tekst w portalu OME
- Logo wyświetlane w wiadomości e-mail i w portalu OME oraz informacje o tym, czy w ogóle używać logo
- Kolor tła wiadomości e-mail i portalu OME

W dowolnym momencie możesz także przywrócić domyślny wygląd i sposób pracy.

Jeśli chcesz mieć większą kontrolę, użyj szablonów Zaawansowane szyfrowanie wiadomości usługi Office 365 tworzenia wielu szablonów zaszyfrowanych wiadomości e-mail pochodzących z Twojej organizacji. Szablony te są dostępne do sterowania częściami interfejsu użytkownika końcowego. Możesz na przykład określić, czy adresaci mogą logować się do portalu szyfrowania za pomocą kont Google, Yahoo i Microsoft. Użyj szablonów, aby zrealizować kilka przypadków użycia, takich jak:

- Poszczególne działy, na przykład Finanse, Sprzedaż i tak dalej.
- Różne produkty
- Różne regiony lub kraje
- Czy chcesz zezwolić na odwołanie wiadomości e-mail
- Czy wiadomości e-mail wysyłane do adresatów zewnętrznych mają wygasać po określonej liczbie dni.

Po utworzeniu szablonów możesz zastosować je do zaszyfrowanych wiadomości e-mail, używając Exchange przepływu poczty e-mail. Jeśli masz Zaawansowane szyfrowanie wiadomości usługi Office 365, możesz odwołać wszelkie wiadomości e-mail znakowane za pomocą tych szablonów.

## <a name="work-with-ome-branding-templates"></a>Praca z szablonami  marki OME

W szablonie marki można modyfikować kilka funkcji. Szablon domyślny można modyfikować, ale nie można go usuwać. Jeśli masz zaawansowane szyfrowanie wiadomości, możesz również tworzyć, modyfikować i usuwać szablony niestandardowe. Używaj Windows PowerShell, aby pracować z jednym szablonem  marki na raz.

- [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) — modyfikowanie domyślnego szablonu brandingu lub utworzonego szablonu niestandardowych brandingów.
- [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) — utwórz nowy szablon marki, tylko zaawansowane szyfrowanie wiadomości.
- [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration) — usuwanie niestandardowego szablonu brandingu (dotyczy tylko zaawansowanego szyfrowania wiadomości). Nie można usunąć domyślnego szablonu  brandingu.

## <a name="modify-an-ome-branding-template"></a>Modyfikowanie szablonu  brandingu OME

Użyj Windows PowerShell, aby modyfikować jeden szablon  marki na raz. Jeśli masz zaawansowane szyfrowanie wiadomości, możesz również tworzyć, modyfikować i usuwać szablony niestandardowe.

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj polecenia cmdlet Set-OMEConfiguration zgodnie z opisem w tece [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration) lub skorzystaj z poniższej grafiki i tabeli, aby uzyskać wskazówki.

![Możliwe do dostosowania części wiadomości e-mail.](../media/ome-template-breakout.png)

<br>

****

|**Aby dostosować tę funkcję obsługi szyfrowania**|**Używanie tych poleceń**|
|---|---|
|Kolor tła|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <p> Aby uzyskać więcej informacji na temat kolorów tła, zobacz sekcję Kolory [tła](#background-color-reference) w dalszej części tego artykułu.|
|Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Obsługiwane formaty plików: .png, .jpg, .bmp lub tiff <p> Optymalny rozmiar pliku logo: mniej niż 40 KB <p> Optymalny rozmiar obrazu logo: 170x70 pikseli. Jeśli obraz przekracza te wymiary, usługa zmienia rozmiar logo w celu wyświetlenia go w portalu. Usługa nie modyfikuje samego pliku graficznego. Aby uzyskać najlepsze wyniki, korzystaj z optymalnego rozmiaru.|
|Tekst obok nazwy i adresu e-mail nadawcy|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|Tekst wyświetlany na przycisku "Czytaj wiadomość"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|Tekst wyświetlany poniżej przycisku "Czytaj wiadomość"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|Adres URL linku do zasad zachowania poufności informacji|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Oświadczenie o zrzeczeniu odpowiedzialności w wiadomości e-mail zawierającej zaszyfrowaną wiadomość|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Tekst wyświetlany w górnej części zaszyfrowanego portalu wyświetlania poczty|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|Aby włączyć lub wyłączyć uwierzytelnianie za pomocą kodu dostępu w czasie rzeczywistym dla tego szablonu niestandardowego|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <p> **Przykłady:** <br/>Aby włączyć hasło dostępu w czasie rzeczywistym dla tego szablonu niestandardowego <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <p> Aby wyłączyć kod dostępu do tego szablonu niestandardowego <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Aby włączyć lub wyłączyć uwierzytelnianie za pomocą tożsamości firmy Microsoft, Google lub Yahoo dla tego szablonu niestandardowego|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <p> **Przykłady:** <br/>Aby włączyć identyfikatory społecznościowe dla tego szablonu niestandardowego <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <p> Aby wyłączyć identyfikatory społecznościowe dla tego szablonu niestandardowego <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|
|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>Tworzenie szablonu  marki OME (zaawansowane szyfrowanie wiadomości)

Jeśli masz Zaawansowane szyfrowanie wiadomości usługi Office 365, możesz utworzyć niestandardowe szablony brandingu dla swojej organizacji, korzystając z polecenia cmdlet [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration). Po utworzeniu szablonu można go zmodyfikować za pomocą polecenia cmdlet Set-OMEConfiguration zgodnie z opisem w tece Modyfikowanie szablonu marki [OME](#modify-an-ome-branding-template). Możesz utworzyć wiele szablonów.

Aby utworzyć nowy szablon niestandardowych  brandingów:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utwórz nowy szablon za pomocą polecenia cmdlet [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) .

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   Na przykład:

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Zwracanie oryginalnych wartości domyślnego szablonu  brandingu

Aby usunąć wszystkie modyfikacje z szablonu domyślnego, w tym dostosowania marki i tak dalej, wykonaj następujące czynności:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj **polecenia cmdlet Set-OMEConfiguration** zgodnie z opisem w [tece Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration). Aby usunąć znakowane dostosowania organizacji z wartości DisclaimerText, EmailText i PortalText, ustaw dla tej wartości pusty ciąg. `""` Dla wszystkich wartości obrazów, takich jak Logo, ustaw wartość .`"$null"`

   W poniższej tabeli opisano domyślne opcje dostosowywania szyfrowania.

   <br>

   ****

   |Aby przywrócić domyślną funkcję szyfrowania do domyślnego tekstu i obrazu|Używanie tych poleceń|
   |:-----|:-----|
   |Domyślny tekst, który jest dostarczany z zaszyfrowanymi wiadomościami e-mail. Tekst domyślny jest wyświetlany powyżej instrukcji dotyczących wyświetlania zaszyfrowanych wiadomości|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Oświadczenie o zrzeczeniu odpowiedzialności w wiadomości e-mail zawierającej zaszyfrowaną wiadomość|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Tekst wyświetlany w górnej części zaszyfrowanego portalu wyświetlania poczty|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <p> **Przykład przywracania domyślnego ustawienia:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <p> **Przykład przywracania domyślnego ustawienia:** <p> `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |Kolor tła|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <p> **Przykład przywracania domyślnego ustawienia:** <p> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|
   |

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Usuwanie niestandardowego szablonu  marki (zaawansowane szyfrowanie wiadomości)

Możesz usuwać tylko te szablony, które zostały wprowadzone. Nie można usunąć domyślnego szablonu  brandingu.

Aby usunąć szablon niestandardowych  brandingów:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj polecenia cmdlet **Remove-OMEConfiguration** w następujący sposób:

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   Na przykład:

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Aby uzyskać więcej informacji, [zobacz Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>Tworzenie reguły Exchange przepływu poczty e-mail, która stosuje znakowanie niestandardowe do zaszyfrowanych wiadomości e-mail

> [!IMPORTANT]
> Aplikacje innych firm, które skanują i modyfikują pocztę, mogą uniemożliwić poprawne zastosowanie  brandingu OME.

Po zmodyfikowaniu szablonu domyślnego lub utworzeniu nowych szablonów  marki możesz utworzyć reguły Exchange przepływu poczty e-mail, aby zastosować znakowanie niestandardowe na podstawie określonych warunków. Taka reguła będzie stosować znakowanie niestandardowe w następujących scenariuszach:

- Jeśli wiadomość e-mail została ręcznie zaszyfrowana przez użytkownika końcowego przy Outlook lub Outlook w sieci Web, wcześniej Outlook Web App
- Jeśli wiadomość e-mail została automatycznie zaszyfrowana przez regułę przepływu Exchange lub zasady ochrony przed utratą danych

Aby uzyskać informacje na temat tworzenia reguły przepływu Exchange poczty e-mail stosowanej do szyfrowania, zobacz Definiowanie reguł przepływu poczty w celu szyfrowania wiadomości e-mail [w Office 365](define-mail-flow-rules-to-encrypt-email.md).

1. W przeglądarce internetowej, używając konta służbowego, które otrzymało uprawnienia administratora globalnego[, zaloguj](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) się w celu Office 365.

2. Wybierz **kafelek Administrator** .

3. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365 wybierz</a> pozycję **Centra administracyjne** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. W selektorze wiadomości e-mail przejdź do **menu Reguły przepływu** \> **poczty e-mail** i wybierz **ikonę Nowy** ![nowy.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Utwórz nową regułę**. Aby uzyskać więcej informacji na temat korzystania z Centrum administracyjnego programu Exchange [centrum administracyjnego w programie Exchange Online](/exchange/exchange-admin-center).

5. **W imieniu** firmy Wpisz nazwę reguły, na przykład Znakowanie dla działu sprzedaży.

6. W **części Zastosuj tę regułę**, jeśli wybierz  warunek Nadawca znajduje się wewnątrz organizacji i inne odpowiednie warunki z listy dostępnych warunków. Na przykład możesz zastosować określony szablon  marki do:

   - Wszystkie zaszyfrowane wiadomości e-mail wysłane przez członków działu finansowego
   - Zaszyfrowane wiadomości e-mail wysłane za pomocą określonego słowa kluczowego, takiego jak "Zewnętrzne" lub "Partner"
   - Zaszyfrowane wiadomości e-mail wysyłane do określonej domeny

7. W **poniższej czynności wybierz** **pozycję Modyfikuj zabezpieczenia wiadomości** \> **Zastosuj znakowanie niestandardowe do wiadomości OME**. Następnie z listy rozwijanej wybierz szablon  marki.

8. (Opcjonalnie) Możesz skonfigurować regułę przepływu poczty e-mail tak, aby stosować szyfrowanie i znakowanie niestandardowe. Na **stronie Wykonaj następujące czynności** wybierz **pozycję Modyfikuj zabezpieczenia wiadomości**, a następnie wybierz pozycję **Zastosuj Szyfrowanie wiadomości usługi Office 365 i ochronę praw**. Wybierz szablon RMS z listy, wybierz pozycję **Zapisz**, a następnie wybierz przycisk **OK**.

   Lista szablonów zawiera domyślne szablony i opcje oraz wszelkie szablony niestandardowe, które tworzysz. Jeśli lista jest pusta, upewnij się, że masz już Szyfrowanie wiadomości usługi Office 365 nowych możliwości. Aby uzyskać instrukcje, [zobacz Konfigurowanie nowych Szyfrowanie wiadomości usługi Office 365 funkcji](set-up-new-message-encryption-capabilities.md). Aby uzyskać informacje na temat szablonów domyślnych, zobacz [Konfigurowanie szablonów usługi Azure Information Protection i zarządzanie nimi](/information-protection/deploy-use/configure-policy-templates). Aby uzyskać informacje na temat **opcji Nie przesyłaj dalej** , zobacz Opcja [Nie przesyłaj dalej w wiadomościach e-mail](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Aby uzyskać informacje o opcji **tylko szyfrowania** , zobacz [Opcja Tylko szyfrowanie w przypadku wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Wybierz **pozycję dodaj** akcję, jeśli chcesz określić inną akcję.

## <a name="background-color-reference"></a>Odwołanie do koloru tła

Nazwy kolorów, których można użyć dla koloru tła, są ograniczone. Zamiast nazwy koloru można użyć wartości kodu hex (`#RRGGBB`). Można użyć heksowej wartości kodu odpowiadającej nazwie koloru lub niestandardowej wartości kodu hex. Pamiętaj, aby ująć hex wartość kodu w cudzysłów (na przykład `"#f0f8ff"`).

Dostępne nazwy kolorów tła i odpowiadające im wartości kodów hex są opisane w poniższej tabeli.

|**Nazwa koloru**|**Kod koloru**|
|---|---|
|`aliceblue`|#f0f8ff|
|`antiquewhite`|#faebd7|
|`aqua`|#00ffff|
|`aquamarine`|#7fffd4|
|`azure`|#f0ffff|
|`beige`|#f5f5dc|
|`bisque`|#ffe4c4|
|`black`|#000000|
|`blanchedalmond`|#ffebcd|
|`blue`|#0000ff|
|`blueviolet`|#8a2be2|
|`brown`|#a52a2a|
|`burlywood`|#deb887|
|`cadetblue`|#5f9ea0|
|`chartreuse`|#7fff00|
|`chocolate`|#d2691e|
|`coral`|#ff7f50|
|`cornflowerblue`|#6495ed|
|`cornsilk`|#fff8dc|
|`crimson`|#dc143c|
|`cyan`|#00ffff|
|`darkblue`|#00008b|
|`darkcyan`|#008b8b|
|`darkgoldenrod`|#b8860b|
|`darkgray`|#a9a9a9|
|`darkgreen`|#006400|
|`darkkhaki`|#bdb76b|
|`darkmagenta`|#8b008b|
|`darkolivegreen`|#556b2f|
|`darkorange`|#ff8c00|
|`darkorchid`|#9932cc|
|`darkred`|#8b0000|
|`darksalmon`|#e9967a|
|`darkseagreen`|#8fbc8f|
|`darkslateblue`|#483d8b|
|`darkslategray`|#2f4f4f|
|`darkturquoise`|#00ced1|
|`darkviolet`|#9400d3|
|`deeppink`|#ff1493|
|`deepskyblue`|#00bfff|
|`dimgray`|#696969|
|`dodgerblue`|#1e90ff|
|`firebrick`|#b22222|
|`floralwhite`|#fffaf0|
|`forestgreen`|#228b22|
|`fuchsia`|#ff00ff|
|`gainsboro`|#dcdcdc|
|`ghostwhite`|#f8f8ff|
|`gold`|#ffd700|
|`goldenrod`|#daa520|
|`gray`|#808080|
|`green`|#008000|
|`greenyellow`|#adff2f|
|`honeydew`|#f0fff0|
|`hotpink`|#ff69b4|
|`indianred`|#cd5c5c|
|`indigo`|#4b0082|
|`ivory`|#fffff0|
|`khaki`|#f0e68c|
|`lavender`|#e6e6fa|
|`lavenderblush`|#fff0f5|
|`lawngreen`|#7cfc00|
|`lemonchiffon`|#fffacd|
|`lightblue`|#add8e6|
|`lightcoral`|#f08080|
|`lightcyan`|#e0ffff|
|`lightgoldenrodyellow`|#fafad2|
|`lightgray`|#d3d3d3|
|`lightgrey`|#d3d3d3|
|`lightgreen`|#90ee90|
|`lightpink`|#ffb6c1|
|`lightsalmon`|#ffa07a|
|`lightseagreen`|#20b2aa|
|`lightskyblue`|#87cefa|
|`lightslategray`|#778899|
|`lightsteelblue`|#b0c4de|
|`lightyellow`|#ffffe0|
|`lime`|#00ff00|
|`limegreen`|#32cd32|
|`linen`|#faf0e6|
|`magenta`|#ff00ff|
|`maroon`|#800000|
|`mediumaquamarine`|#66cdaa|
|`mediumblue`|#0000cd|
|`mediumorchid`|#ba55d3|
|`mediumpurple`|#9370db|
|`mediumseagreen`|#3cb371|
|`mediumslateblue`|#7b68ee|
|`mediumspringgreen`|#00fa9a|
|`mediumturquoise`|#48d1cc|
|`mediumvioletred`|#c71585|
|`midnightblue`|#191970|
|`mintcream`|#f5fffa|
|`mistyrose`|#ffe4e1|
|`moccasin`|#ffe4b5|
|`navajowhite`|#ffdead|
|`navy`|#000080|
|`oldlace`|#fdf5e6|
|`olive`|#808000|
|`olivedrab`|#6b8e23|
|`orange`|#ffa500|
|`orangered`|#ff4500|
|`orchid`|#da70d6|
|`palegoldenrod`|#eee8aa|
|`palegreen`|#98fb98|
|`paleturquoise`|#afeeee|
|`palevioletred`|#db7093|
|`papayawhip`|#ffefd5|
|`peachpuff`|#ffdab9|
|`peru`|#cd853f|
|`pink`|#ffc0cb|
|`plum`|#dda0dd|
|`powderblue`|#b0e0e6|
|`purple`|#800080|
|`red`|#ff0000|
|`rosybrown`|#bc8f8f|
|`royalblue`|#4169e1|
|`saddlebrown`|#8b4513|
|`salmon`|#fa8072|
|`sandybrown`|#f4a460|
|`seagreen`|#00ff00|
|`seashell`|#fff5ee|
|`sienna`|#a0522d|
|`silver`|#c0c0c0|
|`skyblue`|#87ceeb|
|`slateblue`|#6a5acd|
|`slategray`|#708090|
|`snow`|#fffafa|
|`springgreen`|#00ff7f|
|`steelblue`|#4682b4|
|`tan`|#d2b48c|
|`teal`|#008080|
|`thistle`|#d8bfd8|
|`tomato`|#ff6347|
|`turquoise`|#40e0d0|
|`violet`|#ee82ee|
|`wheat`|#f5deb3|
|`white`|#ffffff|
|`whitesmoke`|#f5f5f5|
|`yellow`|#ffff00|
|`yellowgreen`|#9acd32|
