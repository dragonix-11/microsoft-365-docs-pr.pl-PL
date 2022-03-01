---
title: Konfigurowanie nowych funkcji szyfrowania wiadomości
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/30/2019
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
description: Poznaj nowe funkcje obsługi Szyfrowanie wiadomości usługi Office 365 wiadomości e-mail umożliwiające chronioną komunikację z osobami w organizacji i poza nią.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: 006bef8a78a50e3cc47bfcfe7910621a3fa9ef85
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017777"
---
# <a name="set-up-new-message-encryption-capabilities"></a>Konfigurowanie nowych funkcji szyfrowania wiadomości

Nowe funkcje Szyfrowanie wiadomości usługi Office 365 (OME) umożliwiają organizacjom udostępnianie chronionych wiadomości e-mail dowolnym osobom na dowolnym urządzeniu. Użytkownicy mogą wymieniać się chronionymi wiadomościami z Microsoft 365 firmami, a także innymi użytkownikami, którzy nie są klientami, za pomocą Outlook.com, Gmail i innych usług poczty e-mail.

Wykonaj poniższe czynności, aby upewnić się, że w Twojej organizacji są dostępne nowe funkcje OME.

## <a name="verify-that-azure-rights-management-is-active"></a>Sprawdzanie, czy usługa Azure Rights Management jest aktywna

Nowe funkcje OME wykorzystują funkcje ochrony w usługach [Azure Rights Management Services (Azure RMS) ,](/azure/information-protection/what-is-information-protection) technologii używanej przez usługę [Azure Information Protection](/azure/information-protection/what-is-azure-rms) do ochrony wiadomości e-mail i dokumentów za pomocą kontrolek szyfrowania i dostępu.

Jedynym wymaganiem wstępnym do korzystania z nowych funkcji OME jest aktywowanie usługi [Azure Rights Management](/azure/information-protection/what-is-azure-rms) w dzierżawie organizacji. Jeśli tak, Microsoft 365 automatycznie aktywuje nowe funkcje OME i nie musisz nic robić.

Usługa Azure RMS jest również aktywowana automatycznie dla większości uprawnionych planów, więc prawdopodobnie nie musisz też nic robić w tym zakresie. Aby [uzyskać więcej informacji, zobacz Aktywowanie usługi Azure Rights Management](/azure/information-protection/activate-service) .

> [!IMPORTANT]
> Jeśli korzystasz z usługi zarządzania prawami dostępu w usłudze Active Directory (AD RMS) z usługą Exchange Online, musisz przeprowadzić migrację do usługi [Azure Information Protection](/azure/information-protection/migrate-from-ad-rms-to-azure-rms), aby można było korzystać z nowych funkcji usługi OME. Program OME nie jest zgodny z usługami AD RMS.

Więcej informacji można znaleźć w następujących artykułach:

- [Jakich subskrypcji potrzebuję, aby korzystać z nowych funkcji OME?](ome-faq.yml#what-subscriptions-do-i-need-to-use-the-new-ome-capabilities-) aby sprawdzić, czy Twój plan subskrypcji obejmuje usługę Azure Information Protection (która zawiera funkcję usługi Azure RMS).
- [Azure Information Protection](https://azure.microsoft.com/services/information-protection/) , aby uzyskać informacje na temat kupowania uprawniających subskrypcji.

### <a name="manually-activating-azure-rights-management"></a>Ręczne aktywowanie usługi Azure Rights Management

Jeśli usługa Azure RMS została wyłączona lub z jakiegoś powodu nie została aktywowana automatycznie, możesz aktywować ją ręcznie w:

- **centrum administracyjne platformy Microsoft 365**: Aby uzyskać instrukcje [, zobacz Jak aktywować usługę Azure Rights Management z centrum](/azure/information-protection/activate-office365) administracyjnego.
- **Azure Portal**: Aby uzyskać [instrukcje, zobacz Jak aktywować usługę Azure Rights Management z portalu Azure Portal](/azure/information-protection/activate-azure) .

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>Konfigurowanie zarządzania kluczem dzierżawy usługi Azure Information Protection

Jest to krok opcjonalny. Zezwolenie firmie Microsoft na zarządzanie kluczem głównym usługi Azure Information Protection to domyślne ustawienie i zalecane najlepsze rozwiązanie dla większości organizacji. W takim przypadku nie trzeba nic robić.

Istnieje wiele powodów, na przykład wymagań dotyczących zgodności, które mogą doprowadzić do konieczności generowania i zarządzania własnym kluczem głównym (nazywanym też "bring your own key" (BYOK)). W takim przypadku zalecamy, aby wykonać wymagane czynności przed skonfigurowaniem nowych funkcji OME. Aby [uzyskać więcej informacji, zobacz Planowanie i implementowanie klucza dzierżawy usługi Azure Information Protection](/information-protection/plan-design/plan-implement-tenant-key) .

## <a name="verify-new-ome-configuration-in-exchange-online-powershell"></a>Weryfikowanie nowej konfiguracji OME w programie Exchange Online PowerShell

Możesz sprawdzić, czy dzierżawa usługi Microsoft 365 jest prawidłowo skonfigurowana do korzystania z nowych funkcji OME w [programie Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell).

1. [Połączenie użyć Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) przy użyciu konta z uprawnieniami administratora globalnego w Twojej Microsoft 365 dzierżawie.

2. Uruchom Get-IRMConfiguration cmdlet.

     Dla parametru AzureRMSLicensingEnabled powinna być $True wartość parametru OME, która wskazuje, że w dzierżawie skonfigurowano usługę OME. Jeśli tak nie jest, użyj programu Set-IRMConfiguration, aby ustawić wartość właściwości AzureRMSLicensingEnabled tak, $True włączyć funkcję OME.

3. Uruchom Test-IRMConfiguration cmdlet programu Test-IRMConfiguration przy użyciu następującej składni:

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **Przykład**:

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - W przypadku nadawcy i adresata użyj adresu e-mail dowolnego użytkownika w twojej Microsoft 365 dzierżawie.

     Wyniki powinny przypominać:

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

   - Nazwa Twojej organizacji zastąpi *contoso.*

   - Domyślne nazwy szablonów mogą być inne niż te wyświetlane powyżej. Aby [uzyskać więcej informacji, zobacz Konfigurowanie szablonów usługi Azure Information Protection](/azure/information-protection/configure-policy-templates) i zarządzanie nimi.

4. Uruchom Remove-PSSession cmdlet, aby odłączyć się od usługi zarządzania prawami.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-new-ome-capabilities"></a>Następne kroki: Definiowanie reguł przepływu poczty e-mail w celu używania nowych funkcji OME

Jeśli w organizacji skonfigurowano wcześniej reguły przepływu poczty e-mail do szyfrowania wiadomości e-mail, musisz zaktualizować istniejące reguły, aby używać nowych funkcji OME. W przypadku nowych wdrożeń musisz utworzyć nowe reguły przepływu poczty e-mail.

> [!IMPORTANT]
> Jeśli nie zaktualizujemy istniejących reguł przepływu poczty e-mail, użytkownicy nadal będą otrzymywać zaszyfrowaną pocztę z poprzednim formatem załącznika HTML, zamiast nowego bezproblemowego obsługi edytora OME.

Reguły przepływu poczty e-mail określają, jakie warunki powinny być szyfrowane wiadomości e-mail, a także warunki usuwania tego szyfrowania. Po skonfigurowaniu akcji reguły wszystkie wiadomości zgodne z warunkami reguły są szyfrowane podczas ich wysłania.

Aby uzyskać instrukcje dotyczące tworzenia reguł przepływu poczty e-mail dla usługi OME, zobacz Definiowanie reguł przepływu poczty e-mail [w celu szyfrowania wiadomości e-mail w Office 365](define-mail-flow-rules-to-encrypt-email.md).

Aby zaktualizować istniejące reguły w celu używania nowych funkcji OME:

1. W centrum centrum administracyjne platformy Microsoft 365 przejdź do pozycji **Centra administracyjne** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.
2. W centrum Exchange przejdź do pozycji Przepływ poczty **e-mail > Reguły**.
3. Dla każdej reguły w **te czynnościach wykonaj następujące czynności**:
    - Wybierz **pozycję Modyfikuj zabezpieczenia wiadomości**.
    - Wybierz **pozycję Zastosuj Szyfrowanie wiadomości usługi Office 365 i ochronę praw**.
    - Wybierz szablon RMS z listy.
    - Wybierz **Zapisz**.
    - Wybierz przycisk **OK**.
