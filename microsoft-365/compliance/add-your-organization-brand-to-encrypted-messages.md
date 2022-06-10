---
title: Dodawanie marki do zaszyfrowanych komunikatów
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 5/12/2022
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
description: Dowiedz się, jak Office 365 administratorzy globalni mogą stosować znakowanie organizacji do zaszyfrowanych wiadomości e-mail & zawartości portalu szyfrowania.
ms.openlocfilehash: fb0525b112137bf57007b4188bc461abbb0c3f27
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016861"
---
# <a name="add-your-organizations-brand-to-your-microsoft-365-for-business-message-encryption-encrypted-messages"></a>Dodawanie marki organizacji do Microsoft 365 zaszyfrowanych wiadomości szyfrowania komunikatów biznesowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Możesz zastosować znakowanie firmowe, aby dostosować wygląd wiadomości e-mail organizacji i portalu szyfrowania. Aby rozpocząć pracę, musisz zastosować uprawnienia administratora globalnego do konta służbowego. Po uzyskaniu tych uprawnień użyj poleceń cmdlet Get-OMEConfiguration i Set-OMEConfiguration w programie Exchange Online PowerShell, aby dostosować te części zaszyfrowanych wiadomości e-mail:

- Tekst wprowadzający
- Tekst zastrzeżenia
- Adres URL oświadczenia o ochronie prywatności twojej organizacji
- Tekst w portalu OME
- Logo, które pojawia się w wiadomości e-mail i portalu OME lub czy w ogóle ma być używane logo
- Kolor tła w wiadomości e-mail i portalu OME

Możesz również przywrócić domyślny wygląd i działanie w dowolnym momencie.

Jeśli chcesz uzyskać większą kontrolę, użyj zaawansowanego szyfrowania komunikatów usługi Microsoft Purview, aby utworzyć wiele szablonów dla zaszyfrowanych wiadomości e-mail pochodzących z organizacji. Te szablony umożliwiają kontrolowanie części środowiska użytkownika końcowego. Na przykład określ, czy adresaci mogą logować się do portalu szyfrowania przy użyciu kont Google, Yahoo i Microsoft. Użyj szablonów, aby spełnić kilka przypadków użycia, takich jak:

- Poszczególne działy, takie jak Finanse, Sprzedaż itd.
- Różne produkty
- Różne regiony geograficzne lub kraje
- Czy chcesz zezwolić na odwoływanie wiadomości e-mail
- Czy chcesz, aby wiadomości e-mail wysyłane do adresatów zewnętrznych wygasały po określonej liczbie dni.

Po utworzeniu szablonów można je zastosować do zaszyfrowanych wiadomości e-mail przy użyciu Exchange reguł przepływu poczty. Jeśli masz zaawansowane szyfrowanie komunikatów usługi Microsoft Purview, możesz odwołać wszystkie wiadomości e-mail oznaczone marką przy użyciu tych szablonów.

## <a name="work-with-ome-branding-templates"></a>Praca z szablonami znakowania OME

W szablonie znakowania można zmodyfikować kilka funkcji. Szablon domyślny można modyfikować, ale nie usuwać. Jeśli masz zaawansowane szyfrowanie komunikatów, możesz również tworzyć, modyfikować i usuwać szablony niestandardowe. Użyj Exchange Online programu PowerShell, aby pracować z jednym szablonem znakowania jednocześnie.

- [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) — zmodyfikuj domyślny szablon znakowania lub utworzony niestandardowy szablon znakowania.
- [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) — utwórz nowy szablon znakowania, tylko zaawansowane szyfrowanie komunikatów.
- [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration) — usuń niestandardowy szablon znakowania, tylko zaawansowane szyfrowanie komunikatów. Nie można usunąć domyślnego szablonu znakowania.

## <a name="modify-an-ome-branding-template"></a>Modyfikowanie szablonu znakowania OME

Użyj Exchange Online programu PowerShell, aby modyfikować jeden szablon znakowania jednocześnie. Jeśli masz zaawansowane szyfrowanie komunikatów, możesz również tworzyć, modyfikować i usuwać szablony niestandardowe.

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj polecenia cmdlet Set-OMEConfiguration zgodnie z opisem w temacie [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration) lub skorzystaj z poniższej grafiki i tabeli, aby uzyskać wskazówki.

![Dostosowywalne części wiadomości e-mail.](../media/ome-template-breakout.png)

|Aby dostosować tę funkcję środowiska szyfrowania|Użyj tych poleceń|
|---|---|
|Kolor tła|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <p> Aby uzyskać więcej informacji na temat kolorów tła, zobacz sekcję [Kolory tła](#background-color-reference) w dalszej części tego artykułu.|
|Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Obsługiwane formaty plików: .png, .jpg, .bmp lub .tiff <p> Optymalny rozmiar pliku logo: mniej niż 40 KB <p> Optymalny rozmiar obrazu logo: 170x70 pikseli. Jeśli obraz przekroczy te wymiary, usługa zmienia rozmiar logo do wyświetlenia w portalu. Usługa nie modyfikuje samego pliku graficznego. Aby uzyskać najlepsze wyniki, użyj optymalnego rozmiaru.|
|Tekst obok nazwy nadawcy i adresu e-mail|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|Tekst wyświetlany na przycisku "Odczyt wiadomości"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|Tekst wyświetlany poniżej przycisku "Odczyt wiadomości"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|Adres URL linku zasady zachowania poufności informacji|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Instrukcja zastrzeżenia w wiadomości e-mail zawierającej zaszyfrowaną wiadomość|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Tekst wyświetlany w górnej części zaszyfrowanego portalu wyświetlania poczty|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|Aby włączyć lub wyłączyć uwierzytelnianie przy użyciu jednorazowego kodu dostępu dla tego szablonu niestandardowego|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <p> **Przykłady:** <br/>Aby włączyć jednorazowe kody dostępu dla tego szablonu niestandardowego <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <p> Aby wyłączyć jednorazowe kody dostępu dla tego szablonu niestandardowego <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Aby włączyć lub wyłączyć uwierzytelnianie przy użyciu tożsamości firmy Microsoft, Google lub Yahoo dla tego szablonu niestandardowego|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <p> **Przykłady:** <br/>Aby włączyć identyfikatory społecznościowe dla tego szablonu niestandardowego <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <p> Aby wyłączyć identyfikatory społecznościowe dla tego szablonu niestandardowego <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>Tworzenie szablonu znakowania OME (zaawansowane szyfrowanie komunikatów)

Jeśli masz zaawansowane szyfrowanie komunikatów usługi Microsoft Purview, możesz tworzyć niestandardowe szablony znakowania dla swojej organizacji przy użyciu polecenia cmdlet [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) . Po utworzeniu szablonu można zmodyfikować szablon przy użyciu polecenia cmdlet Set-OMEConfiguration zgodnie z opisem w artykule [Modyfikowanie szablonu znakowania OME](#modify-an-ome-branding-template). Możesz utworzyć wiele szablonów.

Aby utworzyć nowy szablon znakowania niestandardowego:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj polecenia cmdlet [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) , aby utworzyć nowy szablon.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   Na przykład:

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Zwracanie domyślnego szablonu znakowania do jego oryginalnych wartości

Aby usunąć wszystkie modyfikacje z szablonu domyślnego, w tym dostosowania marki itd., wykonaj następujące kroki:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj polecenia cmdlet **Set-OMEConfiguration** zgodnie z opisem w temacie [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration). Aby usunąć dostosowania markowe organizacji z wartości DisclaimerText, EmailText i PortalText, ustaw wartość na pusty ciąg . `""` Dla wszystkich wartości obrazu, takich jak Logo, ustaw wartość na `"$null"`.

   W poniższej tabeli opisano wartości domyślne opcji dostosowywania szyfrowania.

   |Aby przywrócić tę funkcję środowiska szyfrowania z powrotem do domyślnego tekstu i obrazu|Użyj tych poleceń|
   |:-----|:-----|
   |Domyślny tekst dostarczany z zaszyfrowanymi wiadomościami e-mail. Tekst domyślny jest wyświetlany powyżej instrukcji wyświetlania zaszyfrowanych komunikatów|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Instrukcja zastrzeżenia w wiadomości e-mail zawierającej zaszyfrowaną wiadomość|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <p> **Przykład:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Tekst wyświetlany w górnej części zaszyfrowanego portalu wyświetlania poczty|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <p> **Przykład powrót do wartości domyślnej:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <p> **Przykład powrót do wartości domyślnej:** <p> `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |Kolor tła|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <p> **Przykład powrót do wartości domyślnej:** <p> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Usuwanie niestandardowego szablonu znakowania (zaawansowane szyfrowanie komunikatów)

Możesz usuwać lub usuwać tylko utworzone szablony znakowania. Nie można usunąć domyślnego szablonu znakowania.

Aby usunąć niestandardowy szablon znakowania:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj polecenia cmdlet **Remove-OMEConfiguration** w następujący sposób:

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   Na przykład:

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Aby uzyskać więcej informacji, zobacz [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>Tworzenie reguły przepływu poczty Exchange, która stosuje niestandardowe znakowanie do zaszyfrowanych wiadomości e-mail

> [!IMPORTANT]
> Aplikacje innych firm, które skanują i modyfikują pocztę, mogą uniemożliwić poprawne stosowanie znakowania OME.

Po zmodyfikowaniu szablonu domyślnego lub utworzeniu nowych szablonów znakowania można utworzyć Exchange reguł przepływu poczty, aby zastosować znakowanie niestandardowe na podstawie określonych warunków. Co najważniejsze, wiadomość e-mail musi być szyfrowana. Taka reguła będzie stosować znakowanie niestandardowe w następujących scenariuszach:

- Jeśli wiadomość e-mail została ręcznie zaszyfrowana przez użytkownika końcowego przy użyciu Outlook lub Outlook w sieci Web, wcześniej Outlook Web App
- Jeśli wiadomość e-mail została automatycznie zaszyfrowana za pomocą reguły przepływu poczty Exchange lub zasad ochrony przed utratą danych w usłudze Microsoft Purview

Aby upewnić się, że usługa Microsoft Purview Message Encryption stosuje niestandardowe znakowanie, skonfiguruj regułę przepływu poczty w celu szyfrowania wiadomości e-mail. Priorytet reguły szyfrowania powinien być wyższy niż reguła znakowania, aby reguła szyfrowania była przetwarzana jako pierwsza. Domyślnie jeśli utworzysz regułę szyfrowania przed regułą znakowania, reguła szyfrowania będzie miała wyższy priorytet. Aby uzyskać informacje na temat tworzenia reguły przepływu poczty Exchange, która stosuje szyfrowanie, zobacz [Definiowanie reguł przepływu poczty w celu szyfrowania wiadomości e-mail w Office 365](define-mail-flow-rules-to-encrypt-email.md). Aby uzyskać informacje na temat ustawiania priorytetu reguły przepływu poczty, zobacz [Zarządzanie regułami przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#set-the-priority-of-a-mail-flow-rule).

1. W przeglądarce internetowej przy użyciu konta służbowego, któremu przyznano uprawnienia administratora globalnego, [zaloguj się do Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Wybierz kafelek **Administrator** .

3. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> wybierz pozycję **Centra** \> administracyjne <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. W usłudze EAC przejdź do pozycji **Reguły** **przepływu poczty** \> i wybierz pozycję **Nowa** ![ikona.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Utwórz nową regułę**. Aby uzyskać więcej informacji na temat korzystania z usługi EAC, zobacz [centrum administracyjne Exchange w Exchange Online](/exchange/exchange-admin-center).

5. W **polu Nazwa** wpisz nazwę reguły, taką jak Branding dla działu sprzedaży.

6. W **obszarze Zastosuj tę regułę, jeśli** wybierz warunek **Nadawca znajduje się w organizacji** i inne warunki, które chcesz, z listy dostępnych warunków. Możesz na przykład zastosować określony szablon znakowania do następujących elementów:

   - Wszystkie zaszyfrowane wiadomości e-mail wysyłane od członków działu finansowego
   - Zaszyfrowane wiadomości e-mail wysyłane przy użyciu określonego słowa kluczowego, takiego jak "Zewnętrzne" lub "Partner"
   - Zaszyfrowane wiadomości e-mail wysyłane do określonej domeny

7. Jeśli zdefiniowano już regułę przepływu poczty w celu zastosowania szyfrowania, pomiń ten krok. W przeciwnym razie, aby skonfigurować regułę przepływu poczty w celu zastosowania szyfrowania **, wybierz** pozycję **Modyfikuj zabezpieczenia komunikatów**, a następnie wybierz pozycję **Zastosuj Office 365 szyfrowanie wiadomości i ochronę praw**. Wybierz szablon usługi RMS z listy, a następnie wybierz pozycję **Dodaj akcję**.

   Lista szablonów zawiera szablony domyślne i opcje oraz wszelkie utworzone szablony niestandardowe. Jeśli lista jest pusta, upewnij się, że skonfigurowano szyfrowanie komunikatów usługi Microsoft Purview. Aby uzyskać instrukcje, zobacz [Konfigurowanie szyfrowania komunikatów usługi Microsoft Purview](set-up-new-message-encryption-capabilities.md). Aby uzyskać informacje o szablonach domyślnych, zobacz [Konfigurowanie szablonów platformy Azure Information Protection i zarządzanie nimi](/information-protection/deploy-use/configure-policy-templates). Aby uzyskać informacje o opcji **Nie przesyłaj dalej** , zobacz [Nie przesyłaj dalej dla wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Aby uzyskać informacje o opcji **tylko do szyfrowania** , zobacz [Opcja Tylko szyfrowanie dla wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

8. W **obszarze Wykonaj następujące** czynności wybierz pozycję **Modyfikuj zabezpieczenia komunikatów** \> **Zastosuj znakowanie niestandardowe do komunikatów OME**. Następnie z listy rozwijanej wybierz szablon znakowania.

   Wybierz **pozycję Dodaj akcję** , jeśli chcesz określić inną akcję, lub wybierz pozycję **Zapisz**, a następnie wybierz przycisk **OK**.

## <a name="background-color-reference"></a>Dokumentacja koloru tła

Nazwy kolorów, których można użyć dla koloru tła, są ograniczone. Zamiast nazwy koloru można użyć wartości kodu szesnastkowego (`#RRGGBB`). Możesz użyć wartości kodu szesnastkowego, która odpowiada nazwie koloru, lub użyć niestandardowej wartości kodu szesnastkowego. Pamiętaj, aby ująć wartość kodu szesnastkowego w cudzysłów (na przykład `"#f0f8ff"`).

Dostępne nazwy kolorów tła i odpowiadające im wartości kodu szesnastkowego są opisane w poniższej tabeli.

|Nazwa koloru|Kod koloru|
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
