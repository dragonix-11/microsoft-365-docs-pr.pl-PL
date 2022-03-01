---
title: Integracja platformy Azure z usługą Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Zintegruj Microsoft 365 z usługą Azure AD, jeśli chcesz mieć synchronizację haseł lub logowanie pojedyncze ze środowiskiem lokalnym.
ms.openlocfilehash: 2d560c2d94552b91c4325a74f99d2f34aa1af399
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015941"
---
# <a name="azure-integration-with-microsoft-365"></a>Integracja platformy Azure z usługą Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Microsoft 365 zarządza tożsamościami użytkowników Azure Active Directory (Azure AD) w tle. Subskrypcja usługi Microsoft 365 obejmuje bezpłatną subskrypcję usługi Azure AD, dzięki czemu możesz zintegrować lokalną usługę Usługi domenowe w usłudze Active Directory (AD DS), aby synchronizować konta użytkowników i hasła lub skonfigurować logowanie pojedyncze. Możesz również zakupić funkcje zaawansowane, aby lepiej zarządzać kontami.
  
Usługa Azure AD oferuje również inne funkcje, takie jak zarządzanie zintegrowanymi aplikacjami, za pomocą których można rozszerzać i dostosowywać Microsoft 365 subskrypcji.
  
Doradców w zakresie wdrażania usługi Azure AD możesz używać do konfiguracji i konfiguracji ze przewodnikiem w centrum administracyjne platformy Microsoft 365 (musisz zalogować się w usłudze Microsoft 365):

 - [Doradca Połączenie usługi Azure AD](https://aka.ms/aadconnectpwsync)
 - [Doradca w zakresie wdrażania usług AD FS](https://aka.ms/adfsguidance)
 - [Przewodnik konfiguracji usługi Azure AD](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>Wersje usługi Azure AD i Microsoft 365 zarządzanie tożsamościami

Jeśli masz płatną subskrypcję usługi Microsoft 365, masz również bezpłatną subskrypcję usługi Azure AD. Za pomocą usługi Azure AD możesz tworzyć konta użytkowników i grup oraz zarządzać nimi. Aby aktywować tę subskrypcję, należy zakończyć rejestrację w trybie online. Później możesz uzyskać dostęp do usługi Azure AD z centrum administracyjne platformy Microsoft 365. 

Aby uzyskać instrukcje dotyczące rejestrowania bezpłatnej subskrypcji usługi Azure AD, [zobacz Korzystanie z bezpłatnej subskrypcji usługi Azure AD](../compliance/use-your-free-azure-ad-subscription-in-office-365.md). Nie przechoduj bezpośrednio do usługi azure.microsoft.com, aby się zarejestrować. W końcu otrzymasz wersję próbną lub płatną subskrypcję usługi Microsoft Azure odrębną od bezpłatnej subskrypcji usługi Azure AD z usługą Microsoft 365. 
  
Dzięki bezpłatnej subskrypcji możesz synchronizować katalogi lokalne, synchronizować je z logowaniem pojedynczym i synchronizować z wieloma aplikacjami typu oprogramowanie jako usługa, takimi jak Salesforce, DropBox i wiele innych.
  
Jeśli potrzebujesz rozszerzonych AD DS, synchronizacji dwukierunkowej i innych możliwości zarządzania, możesz uaktualnić bezpłatną subskrypcję do płatnej subskrypcji premium. Aby uzyskać szczegółowe informacje, [zobacz Azure Active Directory wersje](https://azure.microsoft.com/pricing/details/active-directory/).
  
Aby uzyskać więcej informacji na Microsoft 365 usługi Azure AD, zobacz Microsoft 365 [tożsamości](deploy-identity-solution-identity-model.md).
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>Rozszerzanie możliwości dzierżawy Microsoft 365 dzierżawy

|**Funkcja**|**Opis**|
|:-----|:-----|
|Zintegrowane aplikacje  <br/> |Możesz udzielić poszczególnym aplikacjom dostępu do Twoich Microsoft 365, takich jak poczta, kalendarze, kontakty, użytkownicy, grupy, pliki i foldery. Możesz także autoryzować te aplikacje na poziomie administratora usługi **Azure AD DC** lub administratora globalnego i udostępnić je całej firmie, rejestrując je w usłudze Azure AD. Aby uzyskać więcej informacji, zobacz [Zintegrowane aplikacje i usługa Azure AD Microsoft 365 administratorów](integrated-apps-and-azure-ads.md).<br/> Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](/microsoft-365/admin/add-users/about-admin-roles?). <br/> Zobacz też [Logowanie pojedyncze](/azure/active-directory/manage-apps/what-is-single-sign-on).  <br/> |
|Power Apps  <br/> | Power Apps to aplikacje dla urządzeń przenośnych, które mogą łączyć się z istniejącymi źródłami danych, SharePoint listami danych i innymi aplikacjami danych. Zobacz [Tworzenie aplikacji Power App, aby uzyskać listę w aplikacji SharePoint Online, a](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) Power Apps [stronie aplikacji](https://powerapps.microsoft.com/) Power App, aby uzyskać szczegółowe informacje.  <br/> |
   
## <a name="see-also"></a>Zobacz też

[Microsoft 365 Enterprise omówienie](microsoft-365-overview.md)
