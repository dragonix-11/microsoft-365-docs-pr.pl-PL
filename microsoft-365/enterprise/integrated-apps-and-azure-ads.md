---
title: Zintegrowane aplikacje i usługa Azure AD dla administratorów Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: landing-page
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
description: Dowiedz się, jak rejestrować i administrować Office 365 zintegrowanymi aplikacjami w usłudze Azure AD, umożliwiając autoryzację aplikacji na poziomie **administratora kontrolera domeny usługi Azure AD** lub **administratora globalnego**.
ms.openlocfilehash: 63d88d5b39dd88fafa9bb874d7d0a9df11f89462
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091198"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Zintegrowane aplikacje i usługa Azure AD dla administratorów Microsoft 365

Zarządzanie zintegrowanymi aplikacjami to coś więcej niż tylko [zarządzanie zgodą użytkownika na aplikacje](../admin/misc/user-consent.md). Wraz z pojawieniem się interfejsów API REST Microsoft 365 użytkownicy mogą przyznawać aplikacjom dostęp do swoich danych Microsoft 365, takich jak poczta, kalendarze, kontakty, użytkownicy, grupy, pliki i foldery. Domyślnie użytkownicy muszą indywidualnie udzielać uprawnień każdej aplikacji. 

Nie jest to jednak dobrze skalowane, jeśli chcesz autoryzować aplikację raz na poziomie **administratora kontrolera domeny usługi Azure AD** lub **administratora globalnego** i wdrożyć ją w całej organizacji za pośrednictwem narzędzia do uruchamiania aplikacji. W tym celu należy zarejestrować aplikację w Azure Active Directory (Azure AD). Przed zarejestrowaniem aplikacji w usłudze Azure AD należy wykonać kilka czynności, które należy wykonać, oraz informacje podstawowe, które powinny ułatwić zarządzanie aplikacjami w organizacji Microsoft 365.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Zasoby usługi Azure AD dla administratorów Microsoft 365

Przed rozpoczęciem zarządzania aplikacjami Microsoft 365 w usłudze Azure AD musisz wykonać te dwa zadania.
  
|Wymagania wstępne|Komentarze|
|:-----|:-----|
|[Korzystanie z bezpłatnej subskrypcji usługi Azure AD](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) <br/> |Każda płatna subskrypcja Microsoft 365 jest dostarczana z bezpłatną subskrypcją usługi Azure AD. Usługa Azure AD umożliwia zarządzanie aplikacjami oraz tworzenie kont użytkowników i grup oraz zarządzanie nimi. Aby korzystać z usługi Azure AD, wystarczy przejść do Azure Portal i [https://portal.azure.com](https://portal.azure.com) zalogować się przy użyciu konta Microsoft 365.  <br/> |
|[Zarządzanie zgodą użytkownika na aplikacje](../admin/misc/user-consent.md) <br/> |Musisz zarządzać zgodą użytkownika na aplikacje, aby zezwolić aplikacjom innych firm na dostęp do informacji Microsoft 365 użytkownika i zarejestrować aplikacje w usłudze Azure AD. Na przykład gdy ktoś korzysta z aplikacji innej firmy, ta aplikacja może poprosić o zezwolenie na dostęp do kalendarza i edytowanie plików, które znajdują się w folderze usługi OneDrive.  <br/> |
   
Zarządzanie aplikacjami Microsoft 365 wymaga znajomości aplikacji w usłudze Azure AD. Skorzystaj z tych artykułów, aby uzyskać potrzebne tło.
  
|Artykułu|Komentarze|
|:-----|:-----|
|[Poznaj narzędzie do uruchamiania aplikacji Microsoft 365](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Jeśli dopiero zaczynasz korzystać z uruchamiania aplikacji, możesz się zastanawiać, co to jest i jak z niego korzystać. Narzędzie do uruchamiania aplikacji zostało zaprojektowane tak, aby ułatwić dostęp do aplikacji z dowolnego miejsca w Microsoft 365.  <br/> |
|[Omówienie interfejsów API zarządzania Office 365](/office/office-365-management-api/office-365-management-apis-overview) <br/> |Interfejsy API zarządzania Microsoft 365 umożliwiają zapewnienie dostępu do danych Microsoft 365, w tym do najważniejszych elementów— poczty, kalendarzy, kontaktów, użytkowników i grup, plików i folderów. <br/> |
|[Integrowanie aplikacji w usłudze Azure AD](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Dowiedz się więcej na temat aplikacji zintegrowanych z usługą Azure AD oraz sposobu rejestrowania aplikacji, poznawania pojęć związanych z zarejestrowaną aplikacją i poznawania wytycznych dotyczących znakowania aplikacji wielodostępnych.  <br/> |
|[Dodawanie kafelków niestandardowych do uruchamiania aplikacji](/office365/admin/manage/customize-the-app-launcher)  <br/> |Uruchamianie aplikacji w Microsoft 365 ułatwia użytkownikom znajdowanie aplikacji i uzyskiwanie do nich dostępu. W tym artykule opisano sposoby wyświetlania aplikacji przez deweloperów w programach uruchamiających aplikacje użytkowników, a także zapewnianie im logowania jednokrotnego przy użyciu poświadczeń Microsoft 365.  <br/> |
|[Samouczki integracji usługi Azure AD](/azure/active-directory/saas-apps/tutorial-list) <br/> |Celem tych samouczków jest pokazanie, jak skonfigurować logowania jednokrotnego usługi Azure AD dla aplikacji SaaS innych firm.  <br/> |
|[Scenariusze uwierzytelniania dla usługi Azure AD](/azure/active-directory/develop/authentication-vs-authorization) <br/> |Usługa Azure AD upraszcza uwierzytelnianie dla deweloperów, zapewniając tożsamość jako usługę dzięki obsłudze standardowych protokołów branżowych, takich jak OAuth 2.0 i OpenID Połączenie, a także open source bibliotek dla różnych platform, które ułatwiają szybkie rozpoczęcie kodowania. Ten dokument ułatwia zrozumienie różnych scenariuszy obsługiwanych przez usługę Azure AD i pokazuje, jak rozpocząć pracę.  <br/> |
|[Dostęp do aplikacji](/azure/active-directory/manage-apps/what-is-access-management) <br/> |Usługa Azure AD umożliwia łatwą integrację z wieloma popularnymi aplikacjami oprogramowania jako usługi (SaaS). Zapewnia zarządzanie tożsamościami i dostępem, a także zapewnia Panel dostępu dla użytkowników, w którym mogą dowiedzieć się, jaki mają dostęp do aplikacji i gdzie mogą korzystać z logowania jednokrotnego w celu uzyskania dostępu do swoich aplikacji. Ten artykuł zawiera linki do powiązanych zasobów, które pozwalają dowiedzieć się więcej na temat ulepszeń dostępu do aplikacji dla usługi Azure AD i sposobu ich współtworzenia.  <br/> |
|[Personalizowanie środowiska Office 365](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Możesz uzyskać szybki dostęp do aplikacji, których używasz na co dzień, dodając lub usuwając aplikacje w programie uruchamiania aplikacji Microsoft 365.  <br/> |
