---
title: Konfigurowanie usługi Azure Rights Management dla poprzedniej wersji szyfrowania komunikatów
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/30/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 2cba47b3-f09e-4911-9207-ac056fcb9db7
description: Poprzednia wersja Office 365 Szyfrowanie komunikatów zależy od usługi Microsoft Azure Rights Management (wcześniej znanej jako Windows Azure Active Directory Rights Management).
ms.openlocfilehash: 386056c282ea5f4ad996cc7ae7c50926436fe720
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641367"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>Konfigurowanie usługi Azure Rights Management dla poprzedniej wersji szyfrowania komunikatów

W tym temacie opisano kroki, które należy wykonać w celu aktywowania, a następnie skonfigurowania usługi Azure Rights Management (RMS), części usługi Azure Information Protection, do użycia z poprzednią wersją szyfrowania komunikatów Office 365 (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>Ten artykuł dotyczy tylko poprzedniej wersji OME

Jeśli organizacja nie została jeszcze przeniesiona do Szyfrowanie wiadomości w Microsoft Purview, ale już wdrożono protokół OME, informacje zawarte w tym artykule dotyczą Twojej organizacji. Firma Microsoft zaleca, aby zaplanować przejście do Szyfrowanie wiadomości w Microsoft Purview, gdy tylko będzie to uzasadnione dla Twojej organizacji. Aby uzyskać instrukcje, zobacz [Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](set-up-new-message-encryption-capabilities.md). Jeśli chcesz dowiedzieć się więcej o tym, jak nowe możliwości działają w pierwszej kolejności, zobacz [Szyfrowanie komunikatów](ome.md). W pozostałej części tego artykułu opisano zachowanie OME przed wydaniem Szyfrowanie wiadomości w Microsoft Purview.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>Wymagania wstępne dotyczące korzystania z poprzedniej wersji szyfrowania komunikatów Office 365
<a name="warmprereqs"> </a>

Office 365 szyfrowanie komunikatów (OME), w tym IRM, zależy od usługi Azure Rights Management (Azure RMS). Azure RMS to technologia ochrony używana przez usługę Azure Information Protection. Aby korzystać z protokołu OME, organizacja musi zawierać subskrypcję Exchange Online lub Exchange Online Protection, która z kolei obejmuje subskrypcję usługi Azure Rights Management.

- Jeśli nie masz pewności co do subskrypcji, zobacz opisy usługi Exchange Online dotyczące [zasad komunikatów, odzyskiwania i zgodności](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- Jeśli masz usługę Azure Rights Management, ale nie jest ona skonfigurowana do Exchange Online lub Exchange Online Protection, w tym artykule wyjaśniono, jak aktywować usługę Azure Rights Management, a następnie opisano najlepszy sposób konfigurowania protokołu OME do pracy z usługą Azure Rights Management.

- Jeśli masz już skonfigurowaną usługę OME do pracy z usługą Azure Rights Management dla Exchange Online lub Exchange Online Protection, w zależności od sposobu jej konfigurowania możesz od razu rozpocząć korzystanie z protokołu OME i jego nowych możliwości. W tym artykule wyjaśniono, jak określić, czy skonfigurowano poprawnie protokół OME, co zrobić, jeśli trzeba zmienić konfigurację i co się stanie, jeśli nie chcesz zmieniać konfiguracji. Aby na przykład korzystać z nowych możliwości, należy użyć usługi Azure RMS z rozwiązaniem OME. Nie można używać nowych możliwości z usługą RMS lokalna usługa Active Directory.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>Aktywowanie usługi Azure Rights Management dla poprzedniej wersji protokołu OME w Office 365

Musisz aktywować usługę Azure Rights Management, aby użytkownicy w organizacji mogli stosować ochronę informacji do wysyłanego komunikatu oraz otwierać wiadomości i pliki chronione przez usługę Azure Rights Management. Aby uzyskać instrukcje, zobacz [Aktywowanie usługi Azure Rights Management](/azure/information-protection/activate-service). Po zakończeniu aktywacji wróć tutaj i kontynuuj wykonywanie zadań w tym artykule.

## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>Konfigurowanie poprzedniej wersji protokołu OME do korzystania z usługi Azure RMS przez importowanie zaufanych domen publikowania (TPD)

TPD to plik XML zawierający informacje o ustawieniach zarządzania prawami organizacji. Na przykład TPD zawiera informacje o certyfikacie licencjodawcy serwera (SLC) używanym do podpisywania i szyfrowania certyfikatów i licencji, adresów URL używanych do licencjonowania i publikowania itd. TPD należy zaimportować do organizacji przy użyciu programu PowerShell.

> [!IMPORTANT]
> Wcześniej można było zaimportować dyski TPD z usługi Active Directory Rights Management (AD RMS) do organizacji. Jednak uniemożliwi to korzystanie z Szyfrowanie wiadomości w Microsoft Purview i nie jest zalecane. Jeśli twoja organizacja jest obecnie skonfigurowana w ten sposób, firma Microsoft zaleca utworzenie planu migracji z usługi RMS lokalna usługa Active Directory do opartej na chmurze usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). Nie będzie można używać Szyfrowanie wiadomości w Microsoft Purview do momentu ukończenia migracji do usługi Azure Information Protection.

**Aby zaimportować dyski TPD z usługi Azure RMS**:

1. [Połącz się z usługą Exchange Online w programie PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Wybierz adres URL udostępniania kluczy odpowiadający lokalizacji geograficznej organizacji:

   |Lokalizacja|Adres URL lokalizacji udostępniania kluczy|
   |---|---|
   |Ameryka Północna|<https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Unia Europejska|<https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Azji|<https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Ameryka Południowa|<https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Office 365 for Government (Government Community Cloud)  <br/> Ta lokalizacja udostępniania kluczy usługi RMS jest zarezerwowana dla klientów, którzy kupili Office 365 dla jednostek SKU instytucji rządowych.|<https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc>|

3. Skonfiguruj lokalizację udostępniania kluczy, uruchamiając polecenie cmdlet [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) w następujący sposób:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```

   Aby na przykład skonfigurować lokalizację udostępniania kluczy, jeśli organizacja znajduje się w Ameryka Północna:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. Uruchom polecenie cmdlet [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) z przełącznikiem -RMSOnline, aby zaimportować identyfikator TPD z usługi Azure Rights Management:

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   Gdzie  *TPDName*  jest nazwą, której chcesz użyć dla TPD. Na przykład "Contoso North American TPD".

5. Aby sprawdzić, czy organizacja została pomyślnie skonfigurowana do korzystania z usługi Azure Rights Management, uruchom polecenie cmdlet [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) z przełącznikiem -RMSOnline w następujący sposób:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   To polecenie cmdlet sprawdza między innymi łączność z usługą Azure Rights Management, pobiera identyfikator TPD i sprawdza jego ważność.

6. Uruchom polecenie cmdlet [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) w następujący sposób, aby wyłączyć dostępność szablonów usługi Azure Rights Management w programach Outlook w sieci Web i Outlook:

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. Uruchom polecenie cmdlet [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) w następujący sposób, aby włączyć usługę Azure Rights Management dla organizacji poczty e-mail opartej na chmurze i skonfigurować ją tak, aby używała usługi Azure Rights Management do Office 365 szyfrowania komunikatów:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. Aby sprawdzić, czy pomyślnie zaimportowano usługę TPD i włączono usługę Azure Rights Management, użyj polecenia cmdlet Test-IRMConfiguration, aby przetestować funkcjonalność usługi Azure Rights Management. Aby uzyskać szczegółowe informacje, zobacz "Przykład 1" w [temacie Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>Mam poprzednią wersję protokołu OME skonfigurowaną z usługą Active Directory Rights Management, a nie usługą Azure Information Protection, co mam zrobić?
<a name="importTPDs"> </a>

Istniejące reguły przepływu poczty szyfrowania wiadomości Office 365 można nadal używać z usługą Active Directory Rights Management, ale nie można konfigurować ani używać Szyfrowanie wiadomości w Microsoft Purview. Zamiast tego należy przeprowadzić migrację do usługi Azure Information Protection. Aby uzyskać informacje o migracji i o tym, co to oznacza dla Twojej organizacji, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection](/information-protection/deploy-use/prepare-environment-adrms).

## <a name="next-steps"></a>Następne kroki
<a name="importTPDs"> </a>

Po zakończeniu konfigurowania usługi Azure Rights Management, jeśli chcesz włączyć Szyfrowanie wiadomości w Microsoft Purview, zobacz [Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](./set-up-new-message-encryption-capabilities.md).

Po skonfigurowaniu organizacji do korzystania z Szyfrowanie wiadomości w Microsoft Purview możesz przystąpić do [definiowania reguł przepływu poczty](define-mail-flow-rules-to-encrypt-email.md).

## <a name="related-topics"></a>Tematy pokrewne
<a name="importTPDs"> </a>

[Szyfrowanie w Office 365](encryption.md)

[Informacje techniczne dotyczące szyfrowania w Office 365](technical-reference-details-about-encryption.md)

[Co to jest usługa Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)
