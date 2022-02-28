---
title: Zarządzanie Microsoft 365 kontami użytkowników
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak zarządzać Microsoft 365 kontami użytkowników.
ms.openlocfilehash: 7f75c74984ce58a8b403f01948075b185047f260
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977612"
---
# <a name="manage-microsoft-365-user-accounts"></a>Zarządzanie Microsoft 365 kontami użytkowników

Kontami użytkowników Microsoft 365 zarządza się na kilka różnych sposobów, w zależności od konfiguracji. Kontami użytkowników można zarządzać w programie [centrum administracyjne platformy Microsoft 365](/admin), [PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md), w programie Usługi domenowe w usłudze Active Directory (AD DS) lub w portalu administracyjnym usługi Azure Active Directory (Azure AD). 

Zaraz po zakupie konta Microsoft 365 do zarządzania kontami mogą zostać <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">użyte</a> centrum administracyjne platformy Microsoft 365 i program PowerShell. Podczas zarządzania tożsamościami w chmurze każda osoba w organizacji ma oddzielną nazwę konta użytkownika i hasło. Jeśli chcesz zintegrować z infrastrukturą lokalną i zsynchronizować konta użytkowników z usługą Microsoft 365, możesz za pomocą usługi Azure AD Połączenie udostępnić synchronizację tożsamości i haseł na podstawie funkcji logowania jednokrotnego (SSO).
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planowanie miejsca i sposobu zarządzania kontami użytkowników

Miejsce i sposób zarządzania kontami użytkowników zależy od modelu tożsamości, którego chcesz używać na Microsoft 365. Dwa ogólne modele są oparte na chmurze i hybrydowe.
  
### <a name="cloud-only"></a>Tylko w chmurze

Tworzysz użytkowników i zarządzasz nimi w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a>. Możesz również użyć programu PowerShell lub centrum administracyjnego usługi Azure AD. 
    
### <a name="hybrid"></a>Hybrydowe

Konta użytkowników są synchronizowane Microsoft 365 z programu AD DS, więc do zarządzania kontami użytkowników należy używać lokalnych narzędzi AD DS użytkowników. 
    
## <a name="managing-accounts"></a>Zarządzanie kontami

Wybierając sposób tworzenia kont i zarządzania nimi w organizacji, należy rozważyć następujące wymagania:
  
- Aby połączyć tożsamości między usługą Microsoft 365 a twoją usługą, należy zainstalować oprogramowanie do synchronizacji katalogów na serwerach w środowisku AD DS.
    
- Dowolna opcja synchronizacji katalogów, łącznie z opcjami logowania jednokrotnego, wymaga, aby atrybuty AD DS spełniały standardy. Szczegółowe informacje o atrybutach używanych w katalogu i o tym, jakie oczyszczanie jest konieczne (jeśli jest potrzebne), opisano w tesłudze Przygotowywanie do synchronizacji katalogów z usługą [Microsoft 365](prepare-for-directory-synchronization.md). 
    
- Zaplanuj sposób tworzenia kont Microsoft 365 konta.
    
W poniższej tabeli wymieniono różne narzędzia do zarządzania kontami.
    
|Narzędzie|Uwagi|
|:-----|:-----|
|Centrum administracyjne platformy Microsoft 365  <br/> |[Dodawanie użytkowników pojedynczo lub zbiorczo](../admin/add-users/add-users.md) <br/>  Zapewnia prosty interfejs sieci Web do dodawania i zmieniania kont użytkowników.  <br/>  Nie można ich zmienić, jeśli jest włączona synchronizacja katalogów (można ustawić lokalizację i przypisanie licencji).  <br/>  Nie można używać z opcjami logowania jednokrotnego.  <br/> |
|Windows PowerShell  <br/> |[Zarządzanie Microsoft 365 za pomocą Windows PowerShell](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  Umożliwia zbiorcze dodawanie użytkowników za pomocą skryptu Windows PowerShell sieci.  <br/>  Może być używany do przypisywania lokalizacji i licencji do kont, niezależnie od sposobu ich tworzenia.  <br/> |
|Importowanie zbiorcze  <br/> |[Dodawanie kilku użytkowników jednocześnie](add-several-users-at-the-same-time.md) <br/>  Umożliwia zaimportowanie pliku CSV w celu dodania grupy użytkowników do Microsoft 365.  <br/>  Nie można używać z opcjami logowania jednokrotnego.  <br/> |
|Azure AD  <br/> |Wraz z subskrypcją usługi Azure AD otrzymasz bezpłatną Microsoft 365 usługi Azure AD. Bezpłatna wersja umożliwia wykonywanie funkcji, takich jak samodzielne resetowanie hasła dla użytkowników w chmurze oraz dostosowywanie stron logowania i panelu dostępu. Aby uzyskać rozszerzone funkcje, możesz uaktualnić program do wersji podstawowej, Azure AD — wersja Premium P1 lub Azure AD — wersja Premium P2. Zobacz [Wersje usługi Azure AD,](/azure/active-directory/fundamentals/active-directory-whatis) aby uzyskać listę obsługiwanych funkcji.  <br/> |
|Synchronizacja katalogów  <br/> |[Integrowanie tożsamości lokalnych z usługą Azure AD](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  W przypadku synchronizacji katalogów z synchronizacją haseł lub bez nich użyj usługi [Azure AD Połączenie z ustawieniami ekspresowymi](/azure/active-directory/hybrid/how-to-connect-install-express).  <br/>  W przypadku korzystania z wielu lasów i opcji logowania jednokrotnego użyj [opcji Niestandardowa instalacja usługi Azure AD Połączenie](/azure/active-directory/hybrid/how-to-connect-install-custom).  <br/>  Zapewnia infrastrukturę potrzebną do włączenia logowania jednokrotnego.  <br/>  Wymagane w wielu scenariuszach hybrydowych, takich jak migracja etapowa i migracja hybrydowa Exchange  <br/>  Synchronizuje grupy zabezpieczeń i grupy z obsługą poczty z AD DS.  <br/> |
|||
   
- Niezależnie od tego, jak zamierzasz dodać konta użytkowników do usługi Microsoft 365, musisz zarządzać kilkoma funkcjami kont, takimi jak przypisywanie licencji, określanie lokalizacji itp. Tymi funkcjami można zarządzać przez dłuższy czas z programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a> można też tworzyć konta użytkowników za [pomocą programu PowerShell](./create-user-accounts-with-microsoft-365-powershell.md).
    
    Jeśli zdecydujesz się dodawać wszystkich użytkowników i zarządzać nimi za pośrednictwem centrum administracyjnego, określisz lokalizację i przypiszesz licencje jednocześnie z utworzeniem Microsoft 365 konta. W związku z tym nie jest wymagane zbyt wiele planowania.
    
    > [!IMPORTANT]
    > Utworzenie kont w programie Microsoft 365 bez przypisania licencji (na przykład do usługi SharePoint Online) oznacza, że właściciel konta może wyświetlać centrum Microsoft 365, ale nie może uzyskać dostępu do żadnych usług w ramach subskrypcji firmowej. Po przypisaniu lokalizacji i licencji konto zostanie powielane do przypisanych usług. Użytkownik może zalogować się do swojego konta i korzystać z przypisanych mu usług. 
  
## <a name="see-also"></a>Zobacz też

[Centrum administracyjne platformy Microsoft 365](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)