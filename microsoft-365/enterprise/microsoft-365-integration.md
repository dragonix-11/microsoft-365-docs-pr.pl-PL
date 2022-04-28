---
title: Microsoft 365 integracji ze środowiskami lokalnymi
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Z tego artykułu dowiesz się, jak zintegrować Microsoft 365 z istniejącymi usługami katalogowymi i środowiskami lokalnymi.
ms.openlocfilehash: a3ba75fd2f2b69e71d5b14b14e17827ed96e4dd4
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093904"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Microsoft 365 integracji ze środowiskami lokalnymi

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Możesz zintegrować Microsoft 365 z istniejącymi usługami lokalna usługa Active Directory Domain Services (AD DS) oraz z lokalnymi instalacjami Exchange Server, Skype dla firm Server 2015 lub SharePoint Serwera.
  
 - Podczas integracji usług AD DS można synchronizować konta użytkowników i zarządzać nimi w obu środowiskach. Możesz również dodać synchronizację skrótów haseł (PHS) lub logowanie jednokrotne,aby użytkownicy mogli logować się do obu środowisk przy użyciu poświadczeń lokalnych.
 - Podczas integracji z lokalnymi produktami serwera tworzysz środowisko hybrydowe. Środowisko hybrydowe może pomóc podczas migrowania użytkowników lub informacji do Microsoft 365 lub nadal mieć niektórych użytkowników lub niektóre informacje w środowisku lokalnym, a niektóre w chmurze. Aby uzyskać więcej informacji na temat środowisk hybrydowych, zobacz [chmura hybrydowa](../solutions/cloud-architecture-models.md#hybrid).

Możesz również użyć doradców Azure Active Directory (Azure AD) w celu uzyskania dostosowanych wskazówek dotyczących konfiguracji w Centrum administracyjne platformy Microsoft 365 (musisz zalogować się do Microsoft 365):

- [Przewodnik konfiguracji usługi Azure AD](https://aka.ms/aadpguidance)
- [Synchronizowanie użytkowników z katalogu organizacji](https://aka.ms/aadconnectpwsync)
- [doradca wdrażania Active Directory Federation Services (AD FS)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed zintegrowaniem Microsoft 365 i środowiskiem lokalnym należy również przeprowadzić [dostrajanie wydajności i planowania sieci](network-planning-and-performance.md). Warto również zapoznać się z dostępnymi [modelami tożsamości](deploy-identity-solution-identity-model.md). 

Zobacz [Zarządzanie kontami Microsoft 365](manage-microsoft-365-accounts.md), aby uzyskać listę narzędzi, których można użyć do zarządzania kontami użytkowników Microsoft 365. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>Integrowanie Microsoft 365 z usługami AD DS

Jeśli masz istniejące konta użytkowników w usługach AD DS, nie chcesz ponownie tworzyć wszystkich tych kont w Microsoft 365 i ryzyko wprowadzenia różnic lub błędów między środowiskami. Synchronizacja katalogów ułatwia dublowanie tych kont między środowiskami lokalnymi i online. W przypadku synchronizacji katalogów użytkownicy nie muszą zapamiętywać nowych informacji dla każdego środowiska i nie trzeba tworzyć ani aktualizować kont dwa razy. Należy [przygotować katalog lokalny](prepare-for-directory-synchronization.md) do synchronizacji katalogów.
  
![Synchronizacja katalogów umożliwia synchronizowanie informacji o kontach użytkowników lokalnych i online.](../media/microsoft-365-integration/directory-synchronization.png)
  
Jeśli chcesz, aby użytkownicy mogli logować się do Microsoft 365 przy użyciu poświadczeń lokalnych, możesz również skonfigurować logowanie jednokrotne. W przypadku logowania jednokrotnego Microsoft 365 jest skonfigurowana tak, aby ufała środowisku lokalnemu na potrzeby uwierzytelniania użytkowników.
  
![W przypadku logowania jednokrotnego to samo konto jest dostępne zarówno w środowisku lokalnym, jak i online.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>Synchronizacja katalogów z synchronizacją skrótów haseł lub bez jej synchronizacji lub uwierzytelniania przekazywanego (PTA)

Użytkownik loguje się do środowiska lokalnego przy użyciu konta użytkownika (domena\nazwa użytkownika). Gdy udają się do Microsoft 365, muszą zalogować się ponownie przy użyciu konta służbowego (user@domain.com). Nazwa użytkownika jest taka sama w obu środowiskach. Po dodaniu phs lub PTA użytkownik ma to samo hasło dla obu środowisk, ale będzie musiał podać te poświadczenia ponownie podczas logowania się do Microsoft 365. Synchronizacja katalogów z językiem PHS jest najczęściej używaną synchronizacją katalogów.

Aby skonfigurować synchronizację katalogów, użyj usługi Azure AD Połączenie. Aby uzyskać instrukcje, zobacz [Konfigurowanie synchronizacji katalogów dla Microsoft 365](set-up-directory-synchronization.md) i [usługi Azure AD Połączenie z ustawieniami ekspresowymi](/azure/active-directory/hybrid/how-to-connect-install-express).

Dowiedz się więcej na temat [przygotowywania do synchronizacji katalogów w celu Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>Synchronizacja katalogów za pomocą logowania jednokrotnego

Użytkownik loguje się do środowiska lokalnego przy użyciu konta użytkownika. Po przejściu do Microsoft 365 użytkownicy są zalogowani automatycznie lub logują się przy użyciu tych samych poświadczeń, których używają w środowisku lokalnym (domena\nazwa użytkownika).

Aby skonfigurować logowania jednokrotnego, należy również użyć usługi Azure AD Połączenie. Aby uzyskać instrukcje, zobacz [Instalacja niestandardowa usługi Azure AD Połączenie](/azure/active-directory/hybrid/how-to-connect-install-custom).

Aby uzyskać więcej informacji, zobacz [logowanie jednokrotne](/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="azure-ad-connect"></a>Azure AD Connect

Usługa Azure AD Połączenie zastępuje starsze wersje narzędzi do integracji tożsamości, takich jak DirSync i Azure AD Sync. Jeśli chcesz zaktualizować usługę Azure Active Directory Sync do usługi Azure AD Połączenie, zapoznaj [się z instrukcjami dotyczącymi uaktualniania](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started). 

## <a name="see-also"></a>Zobacz też

[omówienie Microsoft 365 Enterprise](microsoft-365-overview.md)