---
title: Microsoft 365 tożsamości tylko w chmurze
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
description: W tym artykule opisano sposób tworzenia użytkowników i grup, gdy subskrypcja Microsoft 365 korzysta z tożsamości tylko w chmurze.
ms.openlocfilehash: 7b2ad2cee32f075302ea591806214b697fa9b206
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091374"
---
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 tożsamości tylko w chmurze

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli wybrano model tożsamości tylko w chmurze, masz już dzierżawę Azure Active Directory (Azure AD) dla subskrypcji Microsoft 365 do przechowywania wszystkich użytkowników, grup i kontaktów. Po skonfigurowaniu ochrony kont administratorów w [kroku 2](protect-your-global-administrator-accounts.md) i kont użytkowników w [kroku 3](microsoft-365-secure-sign-in.md) tego rozwiązania możesz teraz rozpocząć tworzenie nowych kont i grup, których potrzebuje twoja organizacja.

Poniżej przedstawiono podstawowe składniki tożsamości tylko w chmurze.
 
![Podstawowe składniki tożsamości tylko w chmurze.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Użytkowników i ich konta użytkowników w organizacjach można podzielić na wiele sposobów. Na przykład niektórzy z nich to pracownicy i mają stały stan. Niektórzy z nich to dostawcy, wykonawcy lub partnerzy, którzy mają tymczasowy status. Niektóre z nich to użytkownicy zewnętrzni, którzy nie mają kont użytkowników, ale nadal muszą mieć dostęp do określonych usług i zasobów w celu obsługi interakcji i współpracy. Przykład:

- Konta dzierżawy reprezentują użytkowników w organizacji, na których licencjobiorca ma licencję na usługi w chmurze

- Konta między firmami (B2B) reprezentują użytkowników spoza organizacji, których zapraszasz do udziału we współpracy

Zaserwuj typy użytkowników w organizacji. Jakie są grupy? Można na przykład grupować użytkowników według funkcji wysokiego poziomu lub celu w organizacji.

Ponadto niektóre usługi w chmurze mogą być udostępniane użytkownikom spoza organizacji bez żadnych kont użytkowników. Należy również zidentyfikować te grupy użytkowników.

Grupy w usłudze Azure AD można używać do kilku celów, które upraszczają zarządzanie środowiskiem chmury. Na przykład w przypadku grup usługi Azure AD możesz:

- Licencje oparte na grupach umożliwiają automatyczne przypisywanie licencji Microsoft 365 do kont użytkowników po ich dodaniu jako członków.
- Dynamiczne dodawanie kont użytkowników do określonych grup na podstawie atrybutów konta użytkownika, takich jak nazwa działu.
- Automatycznie aprowizuj użytkowników aplikacji SaaS (Software as a Service) i aby chronić dostęp do tych aplikacji za pomocą uwierzytelniania wieloskładnikowego (MFA) i innych zasad dostępu warunkowego.
- Aprowizowanie uprawnień i poziomów dostępu dla zespołów i witryn zespołów SharePoint Online.

## <a name="next-steps-for-cloud-only-identity"></a>Następne kroki dotyczące tożsamości tylko w chmurze

- [Zarządzanie kontami użytkowników](manage-microsoft-365-accounts.md)
- [Przypisywanie licencji do kont użytkowników](assign-licenses-to-user-accounts.md)
- [Zarządzanie grupami i członkostwem w grupach](manage-microsoft-365-groups.md)
- [Zarządzanie hasłami konta użytkownika](manage-microsoft-365-passwords.md)
