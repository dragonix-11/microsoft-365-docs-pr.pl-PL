---
title: Konfigurowanie szyfrowania wiadomości w usłudze Microsoft Purview
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/16/2022
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 7ff0c040-b25c-4378-9904-b1b50210d00e
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Dowiedz się więcej o Szyfrowanie wiadomości w Microsoft Purview, które umożliwiają chronioną komunikację poczty e-mail z osobami w organizacji i poza nią.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: 828588491c3efbc696994f6073ca4ce849a64be5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622134"
---
# <a name="set-up-message-encryption"></a>Konfigurowanie szyfrowania komunikatów

Szyfrowanie wiadomości w Microsoft Purview umożliwia organizacjom udostępnianie chronionej poczty e-mail wszystkim osobom na dowolnym urządzeniu. Użytkownicy mogą wymieniać chronione wiadomości z innymi organizacjami platformy Microsoft 365, a także z innymi firmami przy użyciu Outlook.com, Gmaila i innych usług poczty e-mail.

Wykonaj poniższe kroki, aby upewnić się, że Szyfrowanie wiadomości w Microsoft Purview jest dostępna w Twojej organizacji.

## <a name="verify-that-azure-rights-management-is-active"></a>Sprawdź, czy usługa Azure Rights Management jest aktywna

Szyfrowanie wiadomości w Microsoft Purview korzysta z funkcji ochrony w usługach [Azure Rights Management Services (Azure RMS),](/azure/information-protection/what-is-information-protection) technologii używanej przez usługę [Azure Information Protection](/azure/information-protection/what-is-azure-rms) do ochrony wiadomości e-mail i dokumentów za pośrednictwem szyfrowania i kontroli dostępu.

Jedynym warunkiem wstępnym korzystania z Szyfrowanie wiadomości w Microsoft Purview jest aktywowanie [usługi Azure Rights Management](/azure/information-protection/what-is-azure-rms) w dzierżawie organizacji. Jeśli tak jest, platforma Microsoft 365 automatycznie aktywuje szyfrowanie komunikatów i nie musisz nic robić.

Usługa Azure RMS jest również aktywowana automatycznie w przypadku większości kwalifikujących się planów, więc prawdopodobnie nie musisz nic robić w tym zakresie. Aby uzyskać więcej informacji [, zobacz Aktywowanie usługi Azure Rights Management](/azure/information-protection/activate-service) .

> [!IMPORTANT]
> Jeśli używasz usługi Active Directory Rights Management (AD RMS) z Exchange Online, musisz [przeprowadzić migrację do usługi Azure Information Protection](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) przed użyciem szyfrowania komunikatów. Szyfrowanie wiadomości w Microsoft Purview jest niezgodna z usługą AD RMS.

Więcej informacji można znaleźć w następujących artykułach:

- [Często zadawane pytania dotyczące szyfrowania komunikatów](ome-faq.yml), aby sprawdzić, czy plan subskrypcji obejmuje usługę Azure Information Protection (która obejmuje funkcje usługi Azure RMS).
- [Usługa Azure Information Protection](https://azure.microsoft.com/services/information-protection/), aby uzyskać informacje o zakupie kwalifikującej się subskrypcji.

### <a name="manually-activating-azure-rights-management"></a>Ręczne aktywowanie usługi Azure Rights Management

Jeśli usługa Azure RMS została wyłączona lub nie została ona automatycznie aktywowana z jakiegokolwiek powodu, możesz aktywować ją ręcznie w następujących elementach:

- **Centrum administracyjne platformy Microsoft 365**: aby uzyskać instrukcje [, zobacz Jak aktywować usługę Azure Rights Management z poziomu centrum administracyjnego](/azure/information-protection/activate-office365).
- **Azure Portal**: aby uzyskać instrukcje, zobacz [Jak aktywować usługę Azure Rights Management z Azure Portal](/azure/information-protection/activate-azure).

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>Konfigurowanie zarządzania kluczem dzierżawy usługi Azure Information Protection

Jest to krok opcjonalny. Umożliwienie firmie Microsoft zarządzania kluczem głównym platformy Azure Information Protection jest ustawieniem domyślnym i zalecanym najlepszym rozwiązaniem dla większości organizacji. Jeśli tak jest, nie musisz nic robić.

Istnieje wiele powodów, na przykład wymagania dotyczące zgodności, które mogą wymagać wygenerowania własnego klucza głównego i zarządzania nim (znanego również jako bring your own key (BYOK)). W takim przypadku zalecamy wykonanie wymaganych kroków przed skonfigurowaniem Szyfrowanie wiadomości w Microsoft Purview. Aby uzyskać więcej informacji, zobacz [Planowanie i implementowanie klucza dzierżawy usługi Azure Information Protection](/information-protection/plan-design/plan-implement-tenant-key).

## <a name="verify-microsoft-purview-message-encryption-configuration-in-exchange-online-powershell"></a>Weryfikowanie konfiguracji Szyfrowanie wiadomości w Microsoft Purview w programie Exchange Online PowerShell

Możesz sprawdzić, czy dzierżawa usługi Microsoft 365 jest prawidłowo skonfigurowana do używania Szyfrowanie wiadomości w Microsoft Purview w [programie Exchange Online programu PowerShell](/powershell/exchange/exchange-online-powershell).

1. [Połącz się z Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) przy użyciu konta z uprawnieniami administratora globalnego w dzierżawie usługi Microsoft 365.

2. Uruchom polecenie cmdlet Get-IRMConfiguration.

     Powinna zostać wyświetlona wartość $True dla parametru AzureRMSLicensingEnabled, co oznacza, że Szyfrowanie wiadomości w Microsoft Purview jest skonfigurowana w dzierżawie. Jeśli tak nie jest, użyj Set-IRMConfiguration, aby ustawić wartość elementu AzureRMSLicensingEnabled na $True w celu włączenia Szyfrowanie wiadomości w Microsoft Purview.

3. Uruchom polecenie cmdlet Test-IRMConfiguration przy użyciu następującej składni:

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **Przykład**:

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - W przypadku nadawcy i odbiorcy użyj adresu e-mail dowolnego użytkownika w dzierżawie usługi Microsoft 365.

     Wyniki powinny być podobne do następujących:

     ```console
     Results : Acquiring RMS Templates ...
                - PASS: RMS Templates acquired.  Templates available: Contoso  - Confidential View Only, Contoso  - Confidential, Do Not
            Forward.
            Verifying encryption ...
                - PASS: Encryption verified successfully.
            Verifying decryption ...
                - PASS: Decryption verified successfully.
            Verifying IRM is enabled ...
                - PASS: IRM verified successfully.

            OVERALL RESULT: PASS
     ```

   - Nazwa organizacji zastąpi nazwę *Contoso*.

   - Domyślne nazwy szablonów mogą różnić się od tych wyświetlanych powyżej. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów platformy Azure Information Protection i zarządzanie nimi](/azure/information-protection/configure-policy-templates).

4. Jeśli test zakończy się niepowodzeniem z komunikatem o błędzie **Nie można uzyskać szablonów usługi RMS**, wykonaj następujące polecenia i uruchom polecenie cmdlet Test-IRMConfiguration, aby sprawdzić, czy jest ono wykonywane.

   ```powershell
   $RMSConfig = Get-AadrmConfiguration
   $LicenseUri = $RMSConfig.LicensingIntranetDistributionPointUrl
   Set-IRMConfiguration -LicensingLocation $LicenseUri
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```
5. Uruchom polecenie cmdlet Remove-PSSession, aby odłączyć się od usługi Rights Management.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-microsoft-purview-message-encryption"></a>Następne kroki: Definiowanie reguł przepływu poczty w celu używania Szyfrowanie wiadomości w Microsoft Purview

Jeśli istnieją wcześniej skonfigurowane reguły przepływu poczty do szyfrowania poczty e-mail w organizacji, musisz zaktualizować istniejące reguły, aby używać Szyfrowanie wiadomości w Microsoft Purview. W przypadku nowych wdrożeń należy utworzyć nowe reguły przepływu poczty.

> [!IMPORTANT]
> Jeśli nie zaktualizujesz istniejących reguł przepływu poczty, użytkownicy będą nadal otrzymywać zaszyfrowaną pocztę, która korzysta z poprzedniego formatu załącznika HTML, zamiast nowego bezproblemowego środowiska.

Reguły przepływu poczty określają, w jakich warunkach wiadomości e-mail powinny być szyfrowane, a także warunki usuwania tego szyfrowania. Po ustawieniu akcji dla reguły wszystkie komunikaty zgodne z warunkami reguły są szyfrowane po ich wysłaniu.

Aby uzyskać instrukcje dotyczące tworzenia szyfrowania komunikatów reguł przepływu poczty, zobacz [Definiowanie reguł przepływu poczty w celu szyfrowania wiadomości e-mail w Office 365](define-mail-flow-rules-to-encrypt-email.md).

Aby zaktualizować istniejące reguły do użycia Szyfrowanie wiadomości w Microsoft Purview:

1. W Centrum administracyjne platformy Microsoft 365 przejdź do **obszaru Administracja centers** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.
2. W centrum administracyjnym programu Exchange przejdź do pozycji **Przepływ poczty > Reguły**.
3. Dla każdej reguły w **obszarze Wykonaj następujące czynności**:
    - Wybierz **pozycję Modyfikuj zabezpieczenia komunikatów**.
    - Wybierz pozycję **Zastosuj Office 365 szyfrowanie komunikatów i ochronę praw**.
    - Wybierz szablon usługi RMS z listy.
    - Wybierz **Zapisz**.
    - Wybierz przycisk **OK**.
