---
title: Przypisywanie licencji Microsoft 365 do kont użytkowników
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Opis sposobu przypisywania licencji Microsoft 365 do kont użytkowników indywidualnie lub na podstawie członkostwa w grupie.
ms.openlocfilehash: ab9769aa4dee6a9f7982f72f377b0c7e0d3f444e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091418"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Przypisywanie licencji Microsoft 365 do kont użytkowników

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W przypadku modelu tożsamości tylko w chmurze można przypisać licencje Microsoft 365 do kont użytkowników podczas ich tworzenia, w zależności od sposobu ich tworzenia.

W przypadku modelu tożsamości hybrydowej, gdy konta użytkowników Active Directory Domain Services (AD DS) są synchronizowane po raz pierwszy, nie są automatycznie przypisywane do lokalizacji ani licencji Microsoft 365. **Przed przypisaniem licencji lub wraz z przypisaniem licencji należy skonfigurować każde konto użytkownika z lokalizacją użytkownika.**

W obu przypadkach musisz przypisać licencję do kont użytkowników, aby użytkownicy mogli uzyskiwać dostęp do usług Microsoft 365, takich jak poczta e-mail i Microsoft Teams.

Licencje można przypisywać do kont użytkowników indywidualnie lub automatycznie za pośrednictwem członkostwa w grupie.

Aby przypisać licencje Microsoft 365 do poszczególnych kont użytkowników, możesz użyć:

- [Centrum administracyjne platformy Microsoft 365](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- Centrum administracyjne usługi Azure AD

## <a name="group-based-licensing"></a>Licencjonowanie oparte na grupach

Grupy zabezpieczeń w usłudze Azure AD można skonfigurować tak, aby automatycznie przypisywać licencje z zestawu subskrypcji do wszystkich członków grupy. Jest to *nazywane licencjonowaniem opartym na grupach*. Jeśli konto użytkownika zostanie dodane do grupy lub usunięte z grupy, licencje dla subskrypcji grupy zostaną automatycznie przypisane lub nie zostaną przypisane z konta użytkownika.

Upewnij się, że masz wystarczającą liczbę licencji dla wszystkich członków grupy. Jeśli zabraknie Ci licencji, nowi użytkownicy nie będą przypisywani licencji, dopóki licencje nie staną się dostępne.

>[!Note]
>Nie należy konfigurować licencjonowania opartego na grupach dla grup zawierających konta biznesowe platformy Azure (B2B).
>

Aby uzyskać więcej informacji, zobacz [licencjonowanie oparte na grupach w usłudze Azure AD](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Następne kroki

Dzięki odpowiedniemu zestawowi kont użytkowników, do których przypisano licencje, możesz teraz przystąpić do następujących czynności:

- [Implementowanie zabezpieczeń](../security/office-365-security/security-roadmap.md)
- [Wdrażanie oprogramowania klienckiego, takiego jak Aplikacje Microsoft 365](/DeployOffice/deployment-guide-microsoft-365-apps)
- [Konfigurowanie zarządzania urządzeniami](device-management-roadmap-microsoft-365.md)
- [Konfigurowanie usług i aplikacji](configure-services-and-applications.md)