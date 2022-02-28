---
title: Konfigurowanie usługi Azure Rights Management podszytą wersją szyfrowania wiadomości
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
description: Poprzednia wersja programu Szyfrowanie wiadomości usługi Office 365 jest zależna od Microsoft Azure (wcześniej znanego jako Windows Azure Active Directory zarządzania prawami dostępu).
ms.openlocfilehash: c94497069d929dd3819e3ced915c8e778e983c10
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983657"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>Konfigurowanie usługi Azure Rights Management podszytą wersją szyfrowania wiadomości

W tym temacie opisano czynności, które należy wykonać, aby aktywować i skonfigurować usługę Azure Rights Management (RMS), część usługi Azure Information Protection, do używania z poprzednią wersją programu Szyfrowanie wiadomości usługi Office 365 (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>Ten artykuł dotyczy tylko poprzedniej wersji OME

Jeśli jeszcze nie przeniesiono organizacji do nowych funkcji usługi OME, ale już wdrożono usługę OME, informacje zawarte w tym artykule dotyczą Twojej organizacji. Firma Microsoft zaleca zaplanowanie przeniesienia się do nowych funkcji OME, gdy tylko będzie to uzasadnione dla Twojej organizacji. Aby uzyskać instrukcje, [zobacz Konfigurowanie nowych Szyfrowanie wiadomości usługi Office 365 funkcji](set-up-new-message-encryption-capabilities.md). Jeśli chcesz dowiedzieć się więcej o tym, jak nowe funkcje działają najpierw[, zobacz Szyfrowanie wiadomości usługi Office 365](ome.md). Pozostała część tego artykułu dotyczy zachowania funkcji OME przed wydaniem nowych funkcji OME.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>Wymagania wstępne dotyczące korzystania z poprzedniej wersji Szyfrowanie wiadomości usługi Office 365
<a name="warmprereqs"> </a>

Szyfrowanie wiadomości usługi Office 365 (OME), w tym IRM, zależy od usługi Azure Rights Management (Azure RMS). Usługa Azure RMS to technologia ochrony używana przez usługę Azure Information Protection. Aby używać narzędzia OME, Twoja organizacja musi obejmować subskrypcję usługi Exchange Online lub Exchange Online Protection, która z kolei obejmuje subskrypcję usługi Azure Rights Management.
  
- Jeśli nie masz pewności, co obejmuje Twoja subskrypcja, zobacz opisy usługi Exchange Online dotyczące zasad wiadomości, odzyskiwania i [zgodności](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- Jeśli masz usługę Azure Rights Management, ale nie ustawiono jej dla usługi Exchange Online ani Exchange Online Protection, w tym artykule wyjaśniono, jak aktywować usługę Azure Rights Management, a następnie opisano najlepszy sposób skonfigurowania usługi OME do współpracy z usługą Azure Rights Management.

- Jeśli już skonfigurujemy usługę OME do współpracy z usługą Azure Rights Management dla usługi Exchange Online lub Exchange Online Protection, w zależności od sposobu jej skonfigurowania możesz od razu zacząć korzystać z usługi OME i jej nowych funkcji. W tym artykule wyjaśniono, jak ustalić, czy obiekt OME został poprawnie skonfigurowany, co należy zrobić w razie potrzeby zmiany konfiguracji i co się stanie, jeśli zrobisz to, jeśli nie zmienisz konfiguracji. Aby na przykład korzystać z nowych możliwości, musisz używać usługi Azure RMS z usługą OME. Nowych funkcji nie można używać z lokalnym usługą RMS usługi Active Directory.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>Aktywowanie usługi Azure Rights Management dla poprzedniej wersji narzędzia OME w usłudze Office 365

Należy aktywować usługę Azure Rights Management, aby użytkownicy w Twojej organizacji mieli możliwość stosowania ochrony informacji do wysyłanych wiadomości oraz otwierania wiadomości i plików chronionych przez usługę Azure Rights Management. Aby uzyskać instrukcje, [zobacz Aktywowanie usługi Azure Rights Management](/azure/information-protection/activate-service). Po ukończeniu aktywacji wróć tutaj i kontynuuj zadania z tego artykułu.
  
## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>Konfigurowanie poprzedniej wersji usługi OME do używania usługi Azure RMS przez zaimportowanie zaufanych domen publikowania (TPDS)

TPD to plik XML, który zawiera informacje o ustawieniach zarządzania prawami w organizacji. Na przykład TPD zawiera informacje o certyfikacie licencjodawcy serwera (SLC) używanym do podpisywania i szyfrowania certyfikatów i licencji, adresach URL używanych do licencjonowania i publikowania itp. Do organizacji można zaimportować dane TPD za pomocą narzędzia Windows PowerShell.
  
> [!IMPORTANT]
> Wcześniej można było wybrać importowanie identyfikatorów TPD z usługi zarządzania prawami dostępu w usłudze Active Directory (AD RMS) do organizacji. Uniemożliwi to jednak korzystanie z nowych funkcji usługi OME i nie jest zalecane. Jeśli w Twojej organizacji skonfigurowano obecnie tę konfigurację, firma Microsoft zaleca utworzenie planu migracji z lokalnej usługi Active Directory RMS do opartej na chmurze usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). Nie będziesz w stanie korzystać z nowych funkcji OME, dopóki nie zakończysz migracji do usługi Azure Information Protection.
  
 **Aby zaimportować identyfikatory TPD z usługi Azure RMS**
  
1. [Połączenie do Exchange Online przy użyciu zdalnej pracy z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Wybierz adres URL udostępniania kluczy, który odpowiada lokalizacji geograficznej Twojej organizacji:

|**Lokalizacja**|**Adres URL lokalizacji udostępniania klucza**|
|:-----|:-----|
|Ameryka Północna  <br/> |https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Unia Europejska  <br/> |https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Azja  <br/> |https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Ameryka Południowa  <br/> |https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Office 365 dla instytucji rządowych (Government Community Cloud)  <br/> Ta lokalizacja udostępniania kluczy usługi RMS jest zarezerwowana dla klientów, którzy zakupili usługę Office 365 dla instytucji rządowych.  <br/> |https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
  
3. Skonfiguruj lokalizację udostępniania kluczy, uruchamiając polecenie cmdlet [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) w następujący sposób: 

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```
  
   Na przykład w celu skonfigurowania lokalizacji udostępniania kluczy, jeśli organizacja znajduje się w Ameryce Północnej:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. Uruchom [polecenie cmdlet Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) za pomocą przełącznika -RMSOnline, aby zaimportować dane TPD z usługi Azure Rights Management: 

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   Gdzie  *TPDName*  to nazwa, której chcesz użyć dla funkcji TPD. Na przykład "Contoso North American TPD". 

5. Aby sprawdzić, czy organizacja pomyślnie skonfigurowała korzystanie z usługi Azure Rights Management, uruchom polecenie cmdlet [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) z przełącznikiem -RMSOnline w następujący sposób:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   To polecenie cmdlet sprawdza między innymi łączność z usługą Azure Rights Management, pobiera plik TPD i sprawdza jego poprawność.

6. Uruchom polecenie [cmdlet Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) w następujący sposób, aby wyłączyć możliwość dostępu szablonów usługi Azure Rights Management w Outlook w sieci Web i Outlook: 

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. Uruchom polecenie [cmdlet Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) w następujący sposób, aby włączyć usługę Azure Rights Management dla opartej na chmurze organizacji poczty e-mail i skonfigurować ją do korzystania z usługi Azure Rights Management dla usługi Szyfrowanie wiadomości usługi Office 365:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. Aby sprawdzić, czy pomyślnie zaimportowano usługę TPD i włączono usługę Azure Rights Management, użyj Test-IRMConfiguration cmdlet w celu przetestowania funkcji usługi Azure Rights Management. Aby uzyskać szczegółowe informacje, zobacz "Przykład 1" w [teście -IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>Co mam zrobić, jeśli w usłudze Zarządzanie prawami dostępu w usłudze Active Directory jest skonfigurować poprzednią wersję narzędzia OME, a nie usługę Azure Information Protection?
<a name="importTPDs"> </a>

Z istniejących reguł przepływu poczty e Szyfrowanie wiadomości usługi Office 365 można nadal korzystać z usługi Zarządzanie prawami dostępu w usłudze Active Directory, ale nie można konfigurować nowych funkcji usługi OME ani ich używać. Zamiast tego należy przeprowadzić migrację do usługi Azure Information Protection. Aby uzyskać informacje na temat migracji i tego, co to oznacza dla Twojej organizacji, zobacz Migrowanie z usług [AD RMS do usługi Azure Information Protection](/information-protection/deploy-use/prepare-environment-adrms).
  
## <a name="next-steps"></a>Następne kroki
<a name="importTPDs"> </a>

Po ukończeniu konfigurowania usługi Azure Rights Management, jeśli chcesz włączyć nowe funkcje OME, zobacz Konfigurowanie nowych funkcji usługi [Szyfrowanie wiadomości usługi Office 365 wbudowanych w usługę Azure Information Protection.](./set-up-new-message-encryption-capabilities.md)
  
Po skonfigurowaniu organizacji do korzystania z nowych funkcji OME możesz rozpocząć definiowanie reguł przepływu poczty e-mail w celu ochrony wiadomości e-mail za pomocą nowych funkcji [OME](define-mail-flow-rules-to-encrypt-email.md).
  
## <a name="related-topics"></a>Tematy pokrewne
<a name="importTPDs"> </a>

[Szyfrowanie w Office 365](encryption.md)
  
[Informacje techniczne dotyczące szyfrowania w Office 365](technical-reference-details-about-encryption.md)
  
[Co to jest usługa Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)