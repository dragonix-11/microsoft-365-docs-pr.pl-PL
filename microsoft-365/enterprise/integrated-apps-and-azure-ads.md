---
title: Zintegrowane aplikacje i usługa Azure AD dla administratorów Microsoft 365 administratorów
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Dowiedz się, jak rejestrować i administrować Office 365 zintegrowanymi aplikacjami w usłudze Azure AD, zezwalając na autoryzacje aplikacji na poziomie administratora centrum administracyjnego usługi **Azure AD** lub administratora **globalnego**.
ms.openlocfilehash: 78092ae817708f0af19eaa85648c35a9c413d3fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977613"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Zintegrowane aplikacje i usługa Azure AD dla administratorów Microsoft 365 administratorów

Zarządzanie zintegrowanymi aplikacjami to nie wszystko niż tylko zarządzanie [zgodą użytkowników na aplikacje](../admin/misc/user-consent.md). Wraz z nadejściem interfejsów API usługi Microsoft 365 REST użytkownicy mogą udzielać aplikacjom dostępu do swoich danych Microsoft 365, takich jak poczta, kalendarze, kontakty, użytkownicy, grupy, pliki i foldery. Domyślnie użytkownicy muszą udzielać uprawnień poszczególnym aplikacjom. 

Jednak nie można tego zrobić dobrze, jeśli chcesz autoryzować aplikację raz na poziomie administratora dc usługi **Azure AD** lub administratora  globalnego i wdaj ją w całą organizację za pośrednictwem ikony Uruchamianie aplikacji. W tym celu należy zarejestrować aplikację w usłudze Azure Active Directory (Azure AD). Przed zarejestrowaniem aplikacji w usłudze Azure AD należy wykonać pewne czynności, a także niektóre podstawowe informacje, które warto znać, aby ułatwić zarządzanie aplikacjami w Microsoft 365 organizacji.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Zasoby usługi Azure AD dla Microsoft 365 administratorów

Musisz wykonać te dwa zadania, zanim będzie można zarządzać swoimi Microsoft 365 w usłudze Azure AD.
  
|Wymagania wstępne|Komentarze|
|:-----|:-----|
|[Korzystanie z bezpłatnej subskrypcji usługi Azure AD](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) <br/> |Każda płatna subskrypcja usługi Microsoft 365 jest wyposażona w bezpłatną subskrypcję usługi Azure AD. Za pomocą usługi Azure AD możesz zarządzać swoimi aplikacjami, a także tworzyć konta użytkowników i grup oraz zarządzać nimi. Aby korzystać z usługi Azure AD, po prostu przejdź do portalu Azure Portal [https://portal.azure.com](https://portal.azure.com) i zaloguj się przy użyciu konta Microsoft 365 konta.  <br/> |
|[Zarządzanie zgodą użytkowników na aplikacje](../admin/misc/user-consent.md) <br/> |Musisz zarządzać zgodą użytkownika na aplikacje, aby zezwolić aplikacjom innych firm na uzyskiwanie dostępu do informacji Microsoft 365 użytkownika i rejestrowanie aplikacji w usłudze Azure AD. Na przykład gdy ktoś korzysta z aplikacji innej firmy, ta aplikacja może poprosić o zezwolenie na dostęp do kalendarza i edytowanie plików, które znajdują się w folderze usługi OneDrive.  <br/> |
   
Zarządzanie Microsoft 365 wymaga znajomości aplikacji w usłudze Azure AD. W tych artykułach znajdziesz potrzebne informacje.
  
|Artykuł|Komentarze|
|:-----|:-----|
|[Poznaj Microsoft 365 Uruchamianie aplikacji](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Jeśli jesteś nowym użytkownikm funkcji Uruchamiania aplikacji, być może zastanawiasz się, czym to jest i jak z niego korzystać. Uruchamianie aplikacji ma na celu pomoc w dostępie do Twoich aplikacji z dowolnego miejsca w Microsoft 365.  <br/> |
|[Omówienie Office 365 interfejsów API zarządzania](/office/office-365-management-api/office-365-management-apis-overview) <br/> |Interfejsy API zarządzania Microsoft 365 umożliwiają zapewnienie dostępu do danych usługi Microsoft 365, w tym do najważniejszych z nich, takich jak poczta, kalendarze, kontakty, użytkownicy i grupy, pliki i foldery. <br/> |
|[Integrowanie aplikacji z usługą Azure AD](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Dowiedz się więcej na temat aplikacji zintegrowanych z usługą Azure AD, sposobu rejestrowania aplikacji, zrozumienia pojęć związanych z zarejestrowaną aplikacją oraz wskazówek dotyczących  oznaczania aplikacji wielodostępnych.  <br/> |
|[Dodawanie kafelków niestandardowych do ikony Uruchamianie aplikacji](/office365/admin/manage/customize-the-app-launcher)  <br/> |Uruchamianie aplikacji w aplikacji Microsoft 365 ułatwia użytkownikom znajdowanie ich aplikacji i uzyskiwanie do nich dostępu. W tym artykule opisano, jak deweloper może ustawić aplikacje jako deweloper do pojawiania się w uruchamianie aplikacji użytkowników, a także zapewnić im środowisko logowania jednokrotnego (SSO) przy użyciu poświadczeń użytkowników Microsoft 365 logowania.  <br/> |
|[Samouczki dotyczące integracji z usługą Azure AD](/azure/active-directory/saas-apps/tutorial-list) <br/> |Celem tych samouczków jest pokazanie, jak skonfigurować logowanie jednokrotne usługi Azure AD dla aplikacji SaaS innych firm.  <br/> |
|[Scenariusze uwierzytelniania dla usługi Azure AD](/azure/active-directory/develop/authentication-vs-authorization) <br/> |Usługa Azure AD upraszcza uwierzytelnianie dla deweloperów, udostępniając tożsamość jako usługę wraz z obsługą standardowych protokołów branżowych, takich jak OAuth 2.0 i OpenID Połączenie, a także biblioteki open source dla różnych platform, które ułatwiają szybkie rozpoczęcie kodowania. Ten dokument ułatwia zrozumienie różnych scenariuszy, które obsługuje usługa Azure AD, i pokazuje, jak rozpocząć pracę.  <br/> |
|[Dostęp do aplikacji](/azure/active-directory/manage-apps/what-is-access-management) <br/> |Usługa Azure AD umożliwia łatwą integrację z wieloma popularnymi obecnie aplikacjami Oprogramowanie jako usługa (SaaS). Zapewnia zarządzanie tożsamościami i dostępem oraz udostępnia użytkownikom panel dostępu, w którym mogą oni dowiedzieć się, do jakich aplikacji mają dostęp i gdzie mogą używać logowania jednokrotnego. Ten artykuł zawiera linki do powiązanych zasobów, które pozwalają dowiedzieć się więcej o ulepszeniach dostępu do aplikacji w usłudze Azure AD oraz o tym, jak można je włączyć.  <br/> |
|[Personalizowanie Office 365 użytkownika](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Możesz uzyskać szybki dostęp do aplikacji, których codziennie używasz, dodając lub usuwając aplikacje w Microsoft 365 Uruchamianie aplikacji.  <br/> |
