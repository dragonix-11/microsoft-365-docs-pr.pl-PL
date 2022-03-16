---
title: Zarządzanie Szyfrowanie wiadomości usługi Office 365
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
description: Po zakończeniu konfigurowania programu Szyfrowanie wiadomości usługi Office 365 (OME) dowiedz się, jak dostosować wdrożenie na kilka sposobów.
ms.openlocfilehash: 49a3957eb4bc2cf1123f04ab0dea77d2adb638b0
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512174"
---
# <a name="manage-office-365-message-encryption"></a>Zarządzanie Szyfrowanie wiadomości usługi Office 365

Po zakończeniu konfigurowania Szyfrowanie wiadomości usługi Office 365 (OME) możesz dostosować konfigurację swojego wdrożenia na kilka sposobów. Możesz na przykład skonfigurować, czy włączyć kody dostępu raz, czy wyświetlić przycisk Szyfruj w Outlook w sieci Web i nie tylko. W tym artykule opisano, jak to zrobić.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>Zarządzaj tym, czy adresaci kont Google, Yahoo i Microsoft mogą używać tych kont do logowania się Szyfrowanie wiadomości usługi Office 365 portalu

Po skonfigurowaniu nowych funkcji Szyfrowanie wiadomości usługi Office 365 użytkownicy w organizacji mogą wysyłać wiadomości do adresatów spoza organizacji. Jeśli adresat używa identyfikatora *społecznościowego* , takiego jak konto Google, konto Yahoo lub konto Microsoft, może zalogować się do portalu OME za pomocą identyfikatora społecznościowego. Jeśli chcesz, możesz nie zezwalać adresatom na używanie identyfikatorów społecznościowych do logowania się do portalu OME.
  
### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>Aby zarządzać tym, czy adresaci mogą logować się do portalu OME za pomocą identyfikatorów społecznościowych
  
1. [Połączenie do Exchange Online przy użyciu zdalnej pracy z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-OMEConfiguration z parametrem SocialIdSignIn w następujący sposób:

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

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>Zarządzanie korzystaniem z kodów dostępu czasowego dla portalu Szyfrowanie wiadomości usługi Office 365 klienta

Jeśli adresat wiadomości zaszyfrowanej przez OME nie używa programu Outlook, niezależnie od konta używanego przez adresata, adresat otrzymuje ograniczony czas link do wyświetlania w sieci Web, który umożliwia odczytanie wiadomości. Ten link zawiera kod w czasie jednego dostępu. Jako administrator możesz zdecydować, czy adresaci mogą logować się do portalu OME przy użyciu kodów zdatymi w czasie rzeczywistym.
  
### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>Aby określić, czy OME generuje kody dostępu w czasie rzeczywistym
  
1. Użyj konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji i rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-OMEConfiguration z parametrem OTPEnabled:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   Aby na przykład wyłączyć kody zdań w czasie rzeczywistym:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   Aby włączyć kody dostępu czasowego:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>Zarządzanie wyświetlaniem przycisku Szyfruj w Outlook w sieci Web

Jako administrator możesz zarządzać tym, czy ten przycisk ma być wyświetlany użytkownikom końcowych.
  
### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>Aby określić, czy przycisk Szyfruj pojawia się w Outlook w sieci Web
  
1. Użyj konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji i rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-IRMConfiguration z parametrem -SimplifiedClientAccessEnabled:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   Aby na przykład wyłączyć przycisk **Szyfruj** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   Aby włączyć **przycisk Zaszyfruj** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>Włączanie odszyfrowywania wiadomości e-mail dla użytkowników aplikacji poczty systemu iOS po stronie usługi

Aplikacja poczty systemu iOS nie może odszyfrowywać wiadomości chronionych za pomocą Szyfrowanie wiadomości usługi Office 365. Jako administrator Microsoft 365, możesz zastosować odszyfrowywanie po stronie usługi dla wiadomości dostarczonych do aplikacji poczty systemu iOS. Gdy zdecydujesz się użyć odszyfrowywania po stronie usługi, usługa wysyła odszyfrowany kopię wiadomości na urządzenie z systemem iOS. Urządzenie klienckie przechowuje odszyfrowane kopie wiadomości. Wiadomość zawiera również informacje o prawach użytkowania, nawet jeśli aplikacja poczty systemu iOS nie stosuje praw użytkowania po stronie klienta do użytkownika. Użytkownik może skopiować lub wydrukować wiadomość, nawet jeśli pierwotnie nie miał do tego uprawnień. Jeśli jednak użytkownik spróbuje wykonać akcję wymaganą od serwera poczty Microsoft 365, na przykład przesłanie wiadomości dalej, nie zezwoli na to, jeśli użytkownik pierwotnie nie miał prawa użytkowania. Jednak użytkownicy końcowi mogą ominą ograniczenie dotyczące użycia funkcji "Nie przesyłaj dalej", przesyłając dalej wiadomość z innego konta w aplikacji poczty systemu iOS. Niezależnie od tego, czy została przez Ciebie skonfigurowanie odszyfrowywania poczty po stronie usługi, załączniki do zaszyfrowanej i chronionej prawami poczty nie mogą być przeglądane w aplikacji poczty systemu iOS.
  
Jeśli zdecydujesz, aby nie zezwalać na odszyfrowane wiadomości do użytkowników aplikacji poczty systemu iOS, użytkownicy otrzymają komunikat z powiadomieniem o tym, że nie mają uprawnień do wyświetlania wiadomości. Domyślnie funkcja odszyfrowywania wiadomości e-mail po stronie usługi nie jest włączona.
  
Aby uzyskać więcej informacji oraz wyświetlić informacje o stanie obsługi klienta, zobacz Wyświetlanie zaszyfrowanych wiadomości na komputerze iPhone [lub iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).
  
### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>Aby określić, czy użytkownicy aplikacji poczty systemu iOS mogą wyświetlać wiadomości chronione przez Szyfrowanie wiadomości usługi Office 365
  
1. Użyj konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji i rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-ActiveSyncOrganizations z parametrem AllowRMSSupportForUnenlightenedApps:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   Aby na przykład skonfigurować usługę do odszyfrowywania wiadomości przed ich wysłaniem do niezaświetlanych aplikacji, takich jak aplikacja poczty systemu iOS:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   Aby usługa nie wysyłała odszyfrowanych wiadomości do niezaświetlanych aplikacji:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> Poszczególne zasady skrzynek pocztowych (OWA/ActiveSync) zastępują te ustawienia (na przykład jeśli wartość -IRMEnabled jest ustawiona na Fałsz w ramach odpowiednich zasad skrzynek pocztowych aplikacji OWA lub zasad skrzynki pocztowej programu ActiveSync, te konfiguracje nie mają zastosowania).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>Włączanie odszyfrowywania załączników wiadomości e-mail po stronie usługi dla klientów poczty przeglądarki sieci Web

Zazwyczaj, gdy używasz szyfrowania Office 365 wiadomości, załączniki są automatycznie szyfrowane. Jako administrator możesz zastosować odszyfrowywanie po stronie usługi dla załączników wiadomości e-mail, które użytkownicy pobierają z przeglądarki sieci Web.
  
Podczas korzystania z odszyfrowywania po stronie usługi usługa wysyła odszyfrowany kopię pliku na urządzenie. Wiadomość jest nadal zaszyfrowana. Załącznik wiadomości e-mail przechowuje również informacje o prawach użytkowania, nawet jeśli przeglądarka nie stosuje praw użytkowania po stronie klienta do użytkownika. Użytkownik może skopiować lub wydrukować załącznik wiadomości e-mail, nawet jeśli pierwotnie nie miał do tego uprawnień. Jeśli jednak użytkownik spróbuje wykonać akcję wymaganą od serwera poczty programu Microsoft 365, na przykład przesyłanie dalej załącznika, nie zezwoli na to, jeśli użytkownik pierwotnie nie miał prawa do wykonania tej czynności.
  
Niezależnie od tego, czy ustawiono odszyfrowywanie załączników po stronie usługi, użytkownicy nie mogą wyświetlać żadnych załączników do zaszyfrowanej i chronionej prawami poczty w aplikacji poczty systemu iOS.
  
Jeśli nie zezwolisz na odszyfrowane załączniki wiadomości e-mail (ustawienie domyślne), użytkownicy otrzymają komunikat informujący o tym, że nie mają uprawnień do wyświetlania załącznika.
  
Aby uzyskać więcej informacji na temat Microsoft 365 szyfrowania wiadomości e-mail i załączników wiadomości e-mail za pomocą Encrypt-Only wiadomości e-mail, zobacz Opcję tylko szyfrowania [dla wiadomości e-mail.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)
  
### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>Aby określić, czy załączniki wiadomości e-mail są odszyfrowywać podczas pobierania z przeglądarki sieci Web
  
1. Użyj konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji i rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-IRMConfiguration z parametrem DecryptAttachmentForEncryptOnly:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   Aby na przykład skonfigurować usługę do odszyfrowywania załączników wiadomości e-mail, gdy użytkownik pobierze je z przeglądarki sieci Web:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   Aby skonfigurować usługę tak, aby pozostawiała zaszyfrowane załączniki wiadomości e-mail w momencie ich pobrania:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>Zapewnianie, że wszyscy adresaci zewnętrzni używają portalu OME do odczytu zaszyfrowanej poczty

Możesz użyć niestandardowych szablonów  brandingu, aby wymusić adresatom odbieranie wiadomości zawijających, która kieruje ich do odczytywania zaszyfrowanych wiadomości e-mail w portalu OME zamiast używania oprogramowania Outlook lub Outlook w sieci Web. Możesz to zrobić, jeśli chcesz mieć większą kontrolę nad tym, jak adresaci używają obierania przez nich wiadomości. Jeśli na przykład adresaci zewnętrzni przeglądają pocztę e-mail w portalu sieci Web, możesz ustawić datę wygaśnięcia wiadomości e-mail i odwołać wiadomość e-mail. Te funkcje są obsługiwane tylko za pośrednictwem portalu OME. Podczas tworzenia reguł przepływu poczty możesz użyć opcji Szyfruj i Nie przesyłaj dalej.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>Użyj szablonu niestandardowego, aby wymusić, aby wszyscy adresaci zewnętrzni korzystali z portalu OME i szyfrowanych wiadomości e-mail

1. Użyj konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji i rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom New-TransportRule cmdlet:

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    gdzie:

   - `mail flow rule name` to nazwa, której chcesz użyć dla nowej reguły przepływu poczty e-mail.

   - `option name`jest albo `Encrypt` .`Do Not Forward`

   - `template name` to na przykład nazwa nadana szablonowi niestandardowego marki `OME Configuration`.

   Aby zaszyfrować wszystkie zewnętrzne wiadomości e-mail przy użyciu szablonu "Konfiguracja OME" i zastosować Encrypt-Only wiadomości:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   Aby zaszyfrować wszystkie zewnętrzne wiadomości e-mail przy użyciu szablonu "Konfiguracja OME" i zastosować opcję Nie przesyłaj dalej:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>Dostosowywanie wyglądu wiadomości e-mail i portalu OME

Aby uzyskać szczegółowe informacje na temat dostosowywania OME dla organizacji, zobacz Dodawanie marki organizacji [do zaszyfrowanych wiadomości](add-your-organization-brand-to-encrypted-messages.md). Aby umożliwić śledzenie i odwoływanie zaszyfrowanych wiadomości, musisz dodać znakowanie niestandardowe do portalu OME.
  
## <a name="disable-the-new-capabilities-for-ome"></a>Wyłączanie nowych możliwości usługi OME

Mamy nadzieję, że tak się nie stanie, ale w razie potrzeby wyłączenie nowych funkcji OME jest bardzo proste. Najpierw musisz usunąć wszystkie utworzone reguły przepływu poczty e-mail, które korzystają z nowych funkcji OME. Aby uzyskać informacje na temat usuwania reguł przepływu poczty e-mail, zobacz [Zarządzanie regułami przepływu poczty e-mail](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). Następnie wykonaj te czynności w Exchange Online PowerShell.
  
### <a name="to-disable-the-new-capabilities-for-ome"></a>Aby wyłączyć nowe funkcje usługi OME
  
1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Jeśli w **programie** Outlook w sieci Web włączono przycisk Encrypt (Zaszyfruj), wyłącz go, uruchamiając Set-IRMConfiguration cmdlet z parametrem SimplifiedClientAccessEnabled. W przeciwnym razie pomiń ten krok.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. Wyłącz nowe funkcje usługi OME, uruchamiając polecenie cmdlet Set-IRMConfiguration z parametrem AzureRMSLicensingEnabled ustawionym na wartość false:

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
