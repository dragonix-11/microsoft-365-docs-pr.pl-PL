---
title: Integracja platformy Azure z Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Zintegruj Microsoft 365 z usługą Azure AD, jeśli chcesz mieć synchronizację haseł lub logowanie jednokrotne ze środowiskiem lokalnym.
ms.openlocfilehash: bebbad10d0fb7a61437dcb24398ebb88d90db739
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096837"
---
# <a name="azure-integration-with-microsoft-365"></a>Integracja platformy Azure z Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 używa Azure Active Directory (Azure AD) do zarządzania tożsamościami użytkowników w tle. Subskrypcja Microsoft 365 obejmuje bezpłatną subskrypcję usługi Azure AD, dzięki czemu można zintegrować usługi lokalna usługa Active Directory Domain Services (AD DS) w celu synchronizowania kont użytkowników i haseł lub konfigurowania logowania jednokrotnego. Możesz również kupić zaawansowane funkcje, aby lepiej zarządzać kontami.
  
Usługa Azure AD oferuje również inne funkcje, takie jak zarządzanie zintegrowanymi aplikacjami, których można użyć do rozszerzania i dostosowywania subskrypcji Microsoft 365.
  
Doradcy wdrażania usługi Azure AD mogą korzystać z ustawień z przewodnikiem i konfiguracji w Centrum administracyjne platformy Microsoft 365 (musisz zalogować się, aby Microsoft 365):

 - [Doradca Połączenie usługi Azure AD](https://aka.ms/aadconnectpwsync)
 - [Doradca wdrażania usług AD FS](https://aka.ms/adfsguidance)
 - [Przewodnik konfiguracji usługi Azure AD](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>Wersje usługi Azure AD i zarządzanie tożsamościami Microsoft 365

Jeśli masz płatną subskrypcję do Microsoft 365, masz również bezpłatną subskrypcję usługi Azure AD. Za pomocą usługi Azure AD można tworzyć konta użytkowników i grup oraz zarządzać nimi. Aby aktywować tę subskrypcję, musisz ukończyć rejestrację jednorazową. Następnie możesz uzyskać dostęp do usługi Azure AD z poziomu Centrum administracyjne platformy Microsoft 365. 

Aby uzyskać instrukcje dotyczące rejestrowania bezpłatnej subskrypcji usługi Azure AD, zobacz [korzystanie z bezpłatnej subskrypcji usługi Azure AD](../compliance/use-your-free-azure-ad-subscription-in-office-365.md). Nie należy przechodzić bezpośrednio do azure.microsoft.com, aby się zarejestrować lub otrzymasz subskrypcję próbną lub płatną, aby Microsoft Azure, która jest oddzielona od bezpłatnej subskrypcji usługi Azure AD z Microsoft 365. 
  
Dzięki bezpłatnej subskrypcji można synchronizować z katalogami lokalnymi, konfigurować logowanie jednokrotne i synchronizować je z wieloma aplikacjami oprogramowania jako usługami, takimi jak Salesforce, DropBox i wiele innych.
  
Jeśli chcesz zwiększyć funkcjonalność usług AD DS, synchronizację dwukierunkową i inne możliwości zarządzania, możesz uaktualnić bezpłatną subskrypcję do płatnej subskrypcji Premium. Aby uzyskać szczegółowe informacje, zobacz [Azure Active Directory wersje](https://azure.microsoft.com/pricing/details/active-directory/).
  
Aby uzyskać więcej informacji na temat Microsoft 365 i usługi Azure AD, zobacz [Microsoft 365 modele tożsamości](deploy-identity-solution-identity-model.md).
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>Rozszerzanie możliwości dzierżawy Microsoft 365

|**Funkcja**|**Opis**|
|:-----|:-----|
|Zintegrowane aplikacje  <br/> |Możesz przyznać poszczególnym aplikacjom dostęp do danych Microsoft 365, takich jak poczta, kalendarze, kontakty, użytkownicy, grupy, pliki i foldery. Możesz również autoryzować te aplikacje na poziomie **administratora kontrolera domeny usługi Azure AD** lub **administratora globalnego** i udostępnić je całej firmie, rejestrując aplikacje w usłudze Azure AD. Aby uzyskać więcej informacji, zobacz [Integrated Apps and Azure AD for Microsoft 365 administrators (Zintegrowane aplikacje i usługa Azure AD dla administratorów Microsoft 365](integrated-apps-and-azure-ads.md)).<br/> Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](/microsoft-365/admin/add-users/about-admin-roles?). <br/> Zobacz również [logowanie jednokrotne](/azure/active-directory/manage-apps/what-is-single-sign-on).  <br/> |
|Power Apps  <br/> | Power Apps to aplikacje przeznaczone dla urządzeń przenośnych, które mogą łączyć się z istniejącymi źródłami danych, takimi jak listy SharePoint i inne aplikacje danych. Aby uzyskać szczegółowe informacje[, zobacz Tworzenie aplikacji Power App, aby uzyskać listę w usłudze SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) i [na stronie Power Apps](https://powerapps.microsoft.com/).  <br/> |
   
## <a name="see-also"></a>Zobacz też

[omówienie Microsoft 365 Enterprise](microsoft-365-overview.md)
