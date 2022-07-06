---
title: Zarządzaj szyfrowaniem wiadomości usługi Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
search.appverid:
- MET150
ms.assetid: 09f6737e-f03f-4bc8-8281-e46d24ee2a74
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Po zakończeniu konfigurowania Office 365 szyfrowania komunikatów dowiedz się, jak dostosować wdrożenie na kilka sposobów.
ms.openlocfilehash: b3d7ffe5db987b9fb3bd29682c8e101ffd99946a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635288"
---
# <a name="manage-office-365-message-encryption"></a>Zarządzaj szyfrowaniem wiadomości usługi Office 365

Po zakończeniu konfigurowania Office 365 szyfrowania komunikatów można dostosować konfigurację wdrożenia na kilka sposobów. Możesz na przykład skonfigurować, czy włączyć jednorazowe kody dostępu, wyświetlić przycisk **Szyfruj** w Outlook w sieci Web i nie tylko. Zadania opisane w tym artykule opisują, jak to zrobić.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>Zarządzanie tym, czy adresaci google, yahoo i konta Microsoft mogą używać tych kont do logowania się do portalu szyfrowania wiadomości Office 365

Po skonfigurowaniu nowych funkcji szyfrowania komunikatów Office 365 użytkownicy w organizacji mogą wysyłać wiadomości do adresatów spoza organizacji. Jeśli odbiorca używa identyfikatora *społecznościowego* , takiego jak konto Google, konto Yahoo lub konto Microsoft, adresat może zalogować się do portalu OME przy użyciu identyfikatora społecznościowego. Jeśli chcesz, możesz nie zezwalać adresatom na logowanie się do portalu OME przy użyciu identyfikatorów społecznościowych.

### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>Aby określić, czy adresaci mogą używać identyfikatorów społecznościowych do logowania się do portalu OME

1. [Połącz się z usługą Exchange Online w programie PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-OMEConfiguration przy użyciu parametru SocialIdSignIn w następujący sposób:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -SocialIdSignIn <$true|$false>
   ```

   Aby na przykład wyłączyć identyfikatory społecznościowe:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $false
   ```

   Aby włączyć identyfikatory społecznościowe:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $true
   ```

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>Zarządzanie użyciem jednorazowych kodów dostępu dla portalu szyfrowania komunikatów Office 365

Jeśli odbiorca wiadomości zaszyfrowanej przez OME nie korzysta z programu Outlook, niezależnie od konta używanego przez adresata, odbiorca otrzyma ograniczony link do widoku internetowego, który umożliwia odczytywanie wiadomości. Ten link zawiera jednorazowy kod dostępu. Jako administrator możesz zdecydować, czy adresaci mogą używać jednorazowych kodów dostępu do logowania się do portalu OME.

### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>Aby zarządzać tym, czy OME generuje jednorazowe kody dostępu

1. Użyj konta służbowego z uprawnieniami administratora globalnego w organizacji i połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)).

2. Uruchom polecenie cmdlet Set-OMEConfiguration przy użyciu parametru OTPEnabled:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   Aby na przykład wyłączyć jednorazowe kody dostępu:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   Aby włączyć jednorazowe kody dostępu:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>Zarządzanie wyświetlaniem przycisku Szyfruj w Outlook w sieci Web

Jako administrator możesz zarządzać tym, czy ten przycisk ma być wyświetlany użytkownikom końcowym.

### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>Aby określić, czy przycisk Szyfruj jest wyświetlany w Outlook w sieci Web

1. Użyj konta służbowego z uprawnieniami administratora globalnego w organizacji i połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)).

2. Uruchom polecenie cmdlet Set-IRMConfiguration z parametrem -SimplifiedClientAccessEnabled:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   Aby na przykład wyłączyć przycisk **Szyfruj** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   Aby włączyć przycisk **Szyfruj** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>Włączanie odszyfrowywania wiadomości e-mail po stronie usługi dla użytkowników aplikacji poczty systemu iOS

Aplikacja poczty systemu iOS nie może odszyfrować wiadomości chronionych za pomocą szyfrowania wiadomości Office 365. Jako administrator platformy Microsoft 365 możesz zastosować odszyfrowywanie po stronie usługi dla wiadomości dostarczonych do aplikacji poczty systemu iOS. W przypadku wybrania opcji odszyfrowywania po stronie usługi usługa wysyła odszyfrowana kopię komunikatu do urządzenia z systemem iOS. Urządzenie klienckie przechowuje odszyfrowanej kopii komunikatu. Komunikat zachowuje również informacje o prawach użytkowania, mimo że aplikacja poczty systemu iOS nie stosuje praw użytkowania po stronie klienta do użytkownika. Użytkownik może skopiować lub wydrukować komunikat, nawet jeśli pierwotnie nie miał do tego uprawnień. Jeśli jednak użytkownik podejmie próbę wykonania akcji wymagającej serwera poczty microsoft 365, takiego jak przekazanie wiadomości dalej, serwer nie zezwoli na akcję, jeśli użytkownik pierwotnie nie miał do tego prawa użytkowania. Jednak użytkownicy końcowi mogą obejść ograniczenie użycia "Nie przesyłaj dalej", przekazując wiadomość z innego konta w aplikacji poczty systemu iOS. Niezależnie od tego, czy skonfigurowano odszyfrowywanie poczty po stronie usługi, załączniki do zaszyfrowanej i chronionej przez prawa poczty nie mogą być wyświetlane w aplikacji poczty systemu iOS.

Jeśli zdecydujesz się nie zezwalać na wysyłanie odszyfrowanych wiadomości do użytkowników aplikacji poczty systemu iOS, użytkownicy otrzymają wiadomość z informacją, że nie mają uprawnień do wyświetlania wiadomości. Domyślnie odszyfrowywanie wiadomości e-mail po stronie usługi nie jest włączone.

Aby uzyskać więcej informacji i wyświetlić środowisko klienta, zobacz [Wyświetlanie zaszyfrowanych wiadomości na telefonie iPhone lub urządzeniu iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).

### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>Aby określić, czy użytkownicy aplikacji poczty systemu iOS mogą wyświetlać wiadomości chronione przez szyfrowanie wiadomości Office 365

1. Użyj konta służbowego z uprawnieniami administratora globalnego w organizacji i połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)).

2. Uruchom polecenie cmdlet Set-ActiveSyncOrganizations przy użyciu parametru AllowRMSSupportForUnenlightenedApps:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   Aby na przykład skonfigurować usługę do odszyfrowywania wiadomości przed wysłaniem ich do nieoświetlonych aplikacji, takich jak aplikacja poczty systemu iOS:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   Możesz też skonfigurować usługę, aby nie wysyłała odszyfrowanych komunikatów do nieoświetlonych aplikacji:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> Zasady poszczególnych skrzynek pocztowych (OWA/ActiveSync) zastępują te ustawienia (tj. jeśli wartość -IRMEnabled jest ustawiona na wartość False w ramach odpowiednich zasad skrzynki pocztowej OWA lub zasad skrzynki pocztowej ActiveSync, te konfiguracje nie będą stosowane).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>Włączanie odszyfrowywania załączników wiadomości e-mail po stronie usługi dla klientów poczty w przeglądarce internetowej

Zwykle w przypadku korzystania z szyfrowania Office 365 komunikatów załączniki są automatycznie szyfrowane. Jako administrator możesz zastosować odszyfrowywanie po stronie usługi dla załączników wiadomości e-mail pobieranych przez użytkowników z przeglądarki internetowej.

W przypadku korzystania z odszyfrowywania po stronie usługi usługa wysyła odszyfrowanej kopii pliku do urządzenia. Komunikat jest nadal zaszyfrowany. Załącznik wiadomości e-mail przechowuje również informacje o prawach użytkowania, mimo że przeglądarka nie stosuje praw użytkowania po stronie klienta do użytkownika. Użytkownik może skopiować lub wydrukować załącznik wiadomości e-mail, nawet jeśli pierwotnie nie miał do tego uprawnień. Jeśli jednak użytkownik spróbuje wykonać akcję, która wymaga serwera poczty platformy Microsoft 365, takiego jak przekazywanie załącznika, serwer nie zezwoli na akcję, jeśli użytkownik pierwotnie nie miał do tego prawa użytkowania.

Niezależnie od tego, czy skonfigurowano odszyfrowywanie załączników po stronie usługi, użytkownicy nie mogą wyświetlać żadnych załączników do zaszyfrowanej i chronionej prawami poczty w aplikacji poczty systemu iOS.

Jeśli zdecydujesz się nie zezwalać na odszyfrowane załączniki wiadomości e-mail, co jest domyślne, użytkownicy otrzymają komunikat informujący, że nie mają uprawnień do wyświetlania załącznika.

Aby uzyskać więcej informacji o tym, jak platforma Microsoft 365 implementuje szyfrowanie wiadomości e-mail i załączników wiadomości e-mail za pomocą opcji Encrypt-Only, zobacz [Opcja Tylko szyfrowanie dla wiadomości e-mail.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>Aby określić, czy załączniki wiadomości e-mail są odszyfrowywane podczas pobierania z przeglądarki internetowej

1. Użyj konta służbowego z uprawnieniami administratora globalnego w organizacji i połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)).

2. Uruchom polecenie cmdlet Set-IRMConfiguration przy użyciu parametru DecryptAttachmentForEncryptOnly:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   Aby na przykład skonfigurować usługę do odszyfrowywania załączników wiadomości e-mail, gdy użytkownik pobierze je z przeglądarki internetowej:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   Aby skonfigurować usługę tak, aby pozostawiała zaszyfrowane załączniki wiadomości e-mail w miarę ich pobierania:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>Upewnij się, że wszyscy adresaci zewnętrzni używają portalu OME do odczytywania zaszyfrowanej poczty

Niestandardowych szablonów znakowania można użyć, aby wymusić na adresatach otrzymywanie wiadomości e-mail z otoką, która kieruje ich do odczytu zaszyfrowanej wiadomości e-mail w portalu OME zamiast korzystania z programu Outlook lub Outlook w sieci Web. Możesz to zrobić, jeśli chcesz mieć większą kontrolę nad sposobem, w jaki adresaci korzystają z otrzymywanych wiadomości e-mail. Jeśli na przykład adresaci zewnętrzni wyświetlają wiadomość e-mail w portalu internetowym, możesz ustawić datę wygaśnięcia wiadomości e-mail i odwołać wiadomość e-mail. Te funkcje są obsługiwane tylko za pośrednictwem portalu OME. Podczas tworzenia reguł przepływu poczty możesz użyć opcji Szyfruj i Nie przesyłaj dalej.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>Użyj szablonu niestandardowego, aby wymusić, aby wszyscy zewnętrzni adresaci korzystali z portalu OME i szyfrowanej poczty e-mail

1. Użyj konta służbowego z uprawnieniami administratora globalnego w organizacji i połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)).

2. Uruchom polecenie cmdlet New-TransportRule:

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    Gdzie:

   - `mail flow rule name` to nazwa, która ma być używana dla nowej reguły przepływu poczty.

   - `option name` jest albo `Encrypt` lub `Do Not Forward`.

   - `template name` to nazwa nadana niestandardowemu szablonowi znakowania, na przykład `OME Configuration`.

   Aby zaszyfrować wszystkie zewnętrzne wiadomości e-mail za pomocą szablonu "Konfiguracja OME" i zastosować opcję Encrypt-Only:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   Aby zaszyfrować wszystkie zewnętrzne wiadomości e-mail za pomocą szablonu "Konfiguracja OME" i zastosować opcję Nie przesyłaj dalej:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>Dostosowywanie wyglądu wiadomości e-mail i portalu OME

Aby uzyskać szczegółowe informacje o sposobie dostosowywania Szyfrowanie wiadomości w Microsoft Purview dla organizacji, zobacz [Dodawanie marki organizacji do zaszyfrowanych komunikatów](add-your-organization-brand-to-encrypted-messages.md). Aby umożliwić śledzenie i odwoływanie zaszyfrowanych komunikatów, należy dodać niestandardowe znakowanie do portalu OME.

## <a name="disable-microsoft-purview-message-encryption"></a>Wyłącz Szyfrowanie wiadomości w Microsoft Purview

Mamy nadzieję, że do tego nie dojdzie, ale jeśli trzeba, wyłączenie Szyfrowanie wiadomości w Microsoft Purview jest bardzo proste. Najpierw musisz usunąć wszystkie utworzone reguły przepływu poczty, które używają Szyfrowanie wiadomości w Microsoft Purview. Aby uzyskać informacje na temat usuwania reguł przepływu poczty, zobacz [Zarządzanie regułami przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). Następnie wykonaj te kroki w Exchange Online programu PowerShell.

### <a name="to-disable-microsoft-purview-message-encryption"></a>Aby wyłączyć Szyfrowanie wiadomości w Microsoft Purview

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, połącz się z programem Exchange Online programu PowerShell. Aby uzyskać instrukcje, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)).

2. Jeśli w Outlook w sieci Web włączono przycisk **Szyfruj**, wyłącz go, uruchamiając polecenie cmdlet Set-IRMConfiguration z parametrem SimplifiedClientAccessEnabled. W przeciwnym razie pomiń ten krok.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. Wyłącz Szyfrowanie wiadomości w Microsoft Purview, uruchamiając polecenie cmdlet Set-IRMConfiguration z parametrem AzureRMSLicensingEnabled ustawionym na wartość false:

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
