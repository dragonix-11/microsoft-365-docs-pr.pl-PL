---
title: Microsoft 365 integracji ze środowiskami lokalnymi
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule dowiesz się, jak zintegrować Microsoft 365 z istniejącymi usługami katalogowymi i środowiskami lokalnymi.
ms.openlocfilehash: ca407e6cb77f829b4c6e8de680772817659aeeec
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015952"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Microsoft 365 integracji ze środowiskami lokalnymi

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Możesz zintegrować Microsoft 365 z istniejącym lokalnym serwerem Usługi domenowe w usłudze Active Directory (AD DS) i lokalnymi instalacjami programu Exchange Server, Skype dla firm Server 2015 lub SharePoint Server.
  
 - Integracja tych AD DS umożliwia synchronizowanie kont użytkowników i zarządzanie nimi w obu środowiskach. Możesz również dodać funkcję synchronizacji skrótów haseł (PHS) lub logowania jednokrotnego (SSO), aby użytkownicy mogą logować się do obu środowisk za pomocą swoich poświadczeń lokalnych.
 - Integracja z lokalnymi produktami serwerowym tworzy środowisko hybrydowe. Środowisko hybrydowe może ułatwić migrowanie użytkowników lub informacji do usługi Microsoft 365. Możesz też nadal mieć niektórych użytkowników lub niektóre informacje lokalnie, a inne w chmurze. Aby uzyskać więcej informacji na temat środowisk hybrydowych, zobacz [Hybrydowa chmura](../solutions/cloud-architecture-models.md#hybrid).

Możesz również skorzystać z doradców usługi Azure Active Directory (Azure AD) w celu spersonalizowanych wskazówek dotyczących konfiguracji w centrum administracyjne platformy Microsoft 365 (musisz zalogować się w usłudze Microsoft 365):

- [Przewodnik konfiguracji usługi Azure AD](https://aka.ms/aadpguidance)
- [Synchronizowanie użytkowników z katalogu organizacji](https://aka.ms/aadconnectpwsync)
- [Doradca w zakresie wdrażania usług federatorów Active Directory (AD FS)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed zintegrowaniem Microsoft 365 środowiskiem lokalnym należy również wykonać planowanie [sieci i dostosowywanie wydajności](network-planning-and-performance.md). Warto również poznać dostępne modele [tożsamości](deploy-identity-solution-identity-model.md). 

Aby [uzyskać Microsoft 365,](manage-microsoft-365-accounts.md) zobacz Zarządzanie kontami użytkowników, aby uzyskać listę narzędzi, za pomocą których można zarządzać kontami Microsoft 365 użytkowników. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>Integracja Microsoft 365 z AD DS

Jeśli masz już konta użytkowników w programie AD DS, nie chcesz ponownie tworzyć ich wszystkich w programie Microsoft 365, co może wprowadzać różnice lub błędy między środowiskami. Synchronizacja katalogów ułatwia dublowanie tych kont między środowiskiem lokalnym i online. Dzięki synchronizacji katalogów użytkownicy nie muszą zapamiętywować nowych informacji dla każdego środowiska i nie trzeba dwukrotnie tworzyć ani aktualizować kont. Konieczne będzie przygotowanie katalogu [lokalnego do](prepare-for-directory-synchronization.md) synchronizacji katalogów.
  
![Synchronizacja katalogów umożliwia synchronizowanie informacji o kontach użytkowników w trybie lokalnym i online.](../media/microsoft-365-integration/directory-synchronization.png)
  
Jeśli chcesz, aby użytkownicy mogli logować się do usługi Microsoft 365 ich poświadczeniami lokalnymi, możesz również skonfigurować logowanie jednokrotne. Za pomocą logowania jednokrotnego Microsoft 365 w celu zaufania środowiska lokalnego do uwierzytelniania użytkowników.
  
![W przypadku logowania pojedynczego to samo konto jest dostępne zarówno w środowisku lokalnym, jak i w środowisku online.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>Synchronizacja katalogów z synchronizacją skrótów haseł lub bez tego uwierzytelniania (PTA)

Użytkownik loguje się do swojego środowiska lokalnego przy użyciu swojego konta użytkownika (domena #D0 aunauytkownika). Gdy przejdą do Microsoft 365, muszą zalogować się ponownie przy użyciu swojego konta służbowego (user@domain.com). Nazwa użytkownika jest taka sama w obu środowiskach. Po dodaniu phs lub PTA użytkownik ma to samo hasło w obu środowiskach, ale będzie musiał ponownie podać te poświadczenia podczas logowania się do Microsoft 365. Synchronizacja katalogów z phS to najczęściej używana synchronizacja katalogów.

Aby skonfigurować synchronizację katalogów, użyj narzędzia Azure AD Połączenie. Aby uzyskać instrukcje, [zobacz Konfigurowanie synchronizacji katalogów Microsoft 365](set-up-directory-synchronization.md) usługi [Azure AD Połączenie ustawieniami ekspresowym](/azure/active-directory/hybrid/how-to-connect-install-express).

Dowiedz się więcej [o przygotowywaniu synchronizacji katalogów do Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>Synchronizacja katalogów z logowaniem jednokrotnym

Użytkownik loguje się do swojego środowiska lokalnego przy użyciu swojego konta użytkownika. Gdy użytkownik przejść do usługi Microsoft 365, jest logowany do usługi automatycznie lub loguje się przy użyciu tych samych poświadczeń, co dla środowiska lokalnego (domena #D0 a nazwa_użytkownika).

Aby skonfigurować logowanie jednokrotne, możesz również użyć usługi Azure AD Połączenie. Aby uzyskać instrukcje, [zobacz Niestandardowa instalacja usługi Azure AD Połączenie](/azure/active-directory/hybrid/how-to-connect-install-custom).

Aby uzyskać więcej informacji, zobacz [Logowanie pojedyncze](/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="azure-ad-connect"></a>Azure AD Connect

Narzędzie Azure AD Połączenie zastępuje starsze wersje narzędzi integracji tożsamości, takie jak narzędzie DirSync i Azure AD Sync. Jeśli chcesz zaktualizować dane z synchronizacji usługi Azure Active Directory do usługi Azure AD Połączenie, zobacz [instrukcje dotyczące uaktualniania](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started). 

## <a name="see-also"></a>Zobacz też

[Microsoft 365 Enterprise omówienie](microsoft-365-overview.md)