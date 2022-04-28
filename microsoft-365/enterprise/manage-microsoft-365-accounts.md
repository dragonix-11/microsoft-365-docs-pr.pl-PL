---
title: Zarządzanie kontami użytkowników Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Dowiedz się, jak zarządzać kontami użytkowników Microsoft 365.
ms.openlocfilehash: dbd1c0a3c1c6fdb10d157299552e83a77f495e3c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098345"
---
# <a name="manage-microsoft-365-user-accounts"></a>Zarządzanie kontami użytkowników Microsoft 365

W zależności od konfiguracji można zarządzać kontami użytkowników Microsoft 365 na kilka różnych sposobów. Kontami użytkowników można zarządzać w [Centrum administracyjne platformy Microsoft 365](/admin), [programie PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md) w Active Directory Domain Services (AD DS) lub w portalu administracyjnym Azure Active Directory (Azure AD). 

Po zakupie Microsoft 365 można zarządzać kontami za pomocą <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> i programu PowerShell. Podczas zarządzania tożsamościami w chmurze każda osoba w organizacji ma oddzielną nazwę konta użytkownika i hasło. Jeśli chcesz zintegrować się z infrastrukturą lokalną i mieć konta użytkowników zsynchronizowane z Microsoft 365, możesz użyć usługi Azure AD Połączenie, aby zapewnić synchronizację tożsamości i haseł dla funkcji logowania jednokrotnego.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planowanie miejsca i sposobu zarządzania kontami użytkowników

Miejsce i sposób zarządzania kontami użytkowników zależy od modelu tożsamości, którego chcesz użyć dla Microsoft 365. Dwa ogólne modele są tylko w chmurze i hybrydowe.
  
### <a name="cloud-only"></a>Tylko w chmurze

Użytkowników można tworzyć i zarządzać nimi w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Możesz również użyć programu PowerShell lub centrum administracyjnego usługi Azure AD. 
    
### <a name="hybrid"></a>Hybrydowa

Konta użytkowników są synchronizowane z Microsoft 365 z usług AD DS, dlatego do zarządzania kontami użytkowników należy użyć lokalnych narzędzi usług AD DS. 
    
## <a name="managing-accounts"></a>Zarządzanie kontami

Podczas podejmowania decyzji, w jaki sposób organizacja będzie tworzyć konta i zarządzać nimi, należy wziąć pod uwagę następujące wymagania:
  
- Oprogramowanie do synchronizacji katalogów musi być zainstalowane na serwerach w środowisku lokalnym, aby połączyć tożsamości między Microsoft 365 a usługami AD DS.
    
- Każda opcja synchronizacji katalogów, w tym opcje logowania jednokrotnego, wymaga, aby atrybuty usług AD DS spełniały standardy. Szczegóły atrybutów używanych w katalogu i tego, jakie oczyszczanie (jeśli istnieje) jest wymagane, opisano w temacie [Przygotowanie do synchronizacji katalogów w celu Microsoft 365](prepare-for-directory-synchronization.md). 
    
- Zaplanuj sposób tworzenia kont Microsoft 365.
    
W poniższej tabeli wymieniono różne narzędzia do zarządzania kontami.
    
|Narzędzie|Uwagi|
|:-----|:-----|
|Centrum administracyjne platformy Microsoft 365  <br/> |[Dodawanie użytkowników pojedynczo lub zbiorczo](../admin/add-users/add-users.md) <br/>  Udostępnia prosty interfejs internetowy do dodawania i zmieniania kont użytkowników.  <br/>  Nie można użyć do zmiany użytkowników, jeśli synchronizacja katalogów jest włączona (można ustawić lokalizację i przypisanie licencji).  <br/>  Nie można używać z opcjami logowania jednokrotnego.  <br/> |
|Windows PowerShell  <br/> |[Zarządzanie Microsoft 365 przy użyciu Windows PowerShell](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  Umożliwia dodawanie użytkowników zbiorczo przy użyciu skryptu Windows PowerShell.  <br/>  Może służyć do przypisywania lokalizacji i licencji do kont, niezależnie od sposobu tworzenia kont.  <br/> |
|Import zbiorczy  <br/> |[Dodawanie kilku użytkowników jednocześnie](add-several-users-at-the-same-time.md) <br/>  Umożliwia zaimportowanie pliku CSV w celu dodania grupy użytkowników do Microsoft 365.  <br/>  Nie można używać z opcjami logowania jednokrotnego.  <br/> |
|Azure AD  <br/> |Otrzymasz bezpłatną wersję usługi Azure AD z subskrypcją Microsoft 365. Możesz wykonywać funkcje, takie jak samoobsługowe resetowanie haseł dla użytkowników w chmurze oraz dostosowywanie stron logowania i Panel dostępu przy użyciu bezpłatnej wersji. Aby uzyskać rozszerzoną funkcjonalność, możesz przeprowadzić uaktualnienie do wersji podstawowej, Azure AD — wersja Premium P1 lub Azure AD — wersja Premium P2. Aby uzyskać listę obsługiwanych funkcji, zobacz [wersje usługi Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) .  <br/> |
|Synchronizacja katalogów  <br/> |[Integrowanie tożsamości lokalnych z usługą Azure AD](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  W przypadku synchronizacji katalogów z synchronizacją haseł lub bez niej użyj usługi [Azure AD Połączenie z ustawieniami ekspresowymi](/azure/active-directory/hybrid/how-to-connect-install-express).  <br/>  W przypadku wielu lasów i opcji logowania jednokrotnego użyj instalacji [niestandardowej usługi Azure AD Połączenie](/azure/active-directory/hybrid/how-to-connect-install-custom).  <br/>  Udostępnia infrastrukturę, która jest niezbędna do włączenia logowania jednokrotnego.  <br/>  Wymagane w wielu scenariuszach hybrydowych, takich jak migracja etapowa i hybrydowe Exchange  <br/>  Synchronizuje grupy z obsługą zabezpieczeń i poczty z usług AD DS.  <br/> |
|||
   
- Niezależnie od tego, jak zamierzasz dodać konta użytkowników do Microsoft 365, musisz zarządzać kilkoma funkcjami konta, takimi jak przypisywanie licencji, określanie lokalizacji itd. Tymi funkcjami można zarządzać długoterminowo z <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">poziomu Centrum administracyjne platformy Microsoft 365</a> lub za [pomocą programu PowerShell można również tworzyć konta użytkowników](./create-user-accounts-with-microsoft-365-powershell.md).
    
    Jeśli zdecydujesz się dodać wszystkich użytkowników i zarządzać nimi za pośrednictwem centrum administracyjnego, określisz lokalizację i przypiszesz licencje w tym samym czasie, co utworzenie konta Microsoft 365. W związku z tym nie jest wymagane zbyt wiele planowania.
    
    > [!IMPORTANT]
    > Tworzenie kont w Microsoft 365 bez przypisywania licencji (na przykład do SharePoint Online) oznacza, że właściciel konta może wyświetlić centrum Microsoft 365, ale nie może uzyskać dostępu do żadnej z usług w ramach subskrypcji twojej firmy. Po przypisaniu lokalizacji i licencji konto zostanie zreplikowane do przypisanej usługi lub usług. Użytkownik może zalogować się do swojego konta i korzystać z przypisanych do niego usług. 
  
## <a name="see-also"></a>Zobacz też

[Centrum administracyjne platformy Microsoft 365](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)