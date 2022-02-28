---
title: Przypisywanie Microsoft 365 do kont użytkowników
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: W tym artykule opisano, Microsoft 365 do kont użytkowników pojedynczo lub na podstawie członkostwa w grupach.
ms.openlocfilehash: dd941be0d257aa356cf6e69bfdd59a8d1743ed93
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983572"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Przypisywanie Microsoft 365 do kont użytkowników

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W przypadku modelu tożsamości tylko w chmurze możesz przypisywać licencje Microsoft 365 do kont użytkowników podczas ich tworzenia, w zależności od sposobu ich utworzenia.

W przypadku modelu tożsamości hybrydowej podczas Usługi domenowe w usłudze Active Directory (AD DS) użytkowników po raz pierwszy nie są one automatycznie przypisywane do nich lokalizacji ani licencji Microsoft 365 licencji. **Każde konto użytkownika należy skonfigurować z lokalizacją użytkownika przed przypisaniem licencji lub wraz z nim.**

W obu przypadkach należy przypisać licencje do kont użytkowników, aby użytkownicy Microsoft 365 usług, takich jak poczta e-mail Microsoft Teams.

Możesz przypisywać licencje do kont użytkowników pojedynczo lub automatycznie za pośrednictwem członkostwa w grupie.

Aby przypisać Microsoft 365 do kont poszczególnych użytkowników, możesz użyć:

- [The centrum administracyjne platformy Microsoft 365](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- Centrum administracyjne usługi Azure AD

## <a name="group-based-licensing"></a>Licencjonowanie oparte na grupach

Możesz skonfigurować grupy zabezpieczeń w usłudze Azure AD, aby automatycznie przypisywać licencje z zestawu subskrypcji do wszystkich członków grupy. Jest to nazywane *licencjonowaniem grup.* Jeśli konto użytkownika zostanie dodane do grupy lub usunięte z tej grupy, licencje dla subskrypcji grupy zostaną automatycznie przypisane do konta użytkownika lub usunięte z tego konta.

Upewnij się, że masz wystarczającą ilość licencji dla wszystkich członków grupy. Jeśli zabraknie licencji, nowym użytkownikom nie zostaną przypisane licencje, dopóki licencje nie staną się dostępne.

>[!Note]
>Nie należy konfigurować licencjonowania grupowego dla grup, które zawierają konta B2B (Dla firm) platformy Azure.
>

Aby uzyskać więcej informacji, zobacz [Licencjonowanie oparte na grupach w usłudze Azure AD](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Następne kroki

W przypadku odpowiedniego zestawu kont użytkowników, do których przypisano licencje, możesz:

- [Implementowanie zabezpieczeń](../security/office-365-security/security-roadmap.md)
- [Wdrażanie oprogramowania klienckiego, takiego jak Aplikacje Microsoft 365](/DeployOffice/deployment-guide-microsoft-365-apps)
- [Konfigurowanie zarządzania urządzeniami](device-management-roadmap-microsoft-365.md)
- [Konfigurowanie usług i aplikacji](configure-services-and-applications.md)