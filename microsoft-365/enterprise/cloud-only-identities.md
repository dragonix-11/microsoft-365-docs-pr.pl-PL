---
title: Microsoft 365 tożsamości tylko w chmurze
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
description: W tym artykule opisano, jak tworzyć użytkowników i grupy, Microsoft 365 subskrypcji usługi korzysta z tożsamości tylko w chmurze.
ms.openlocfilehash: 81c13a6b7e32883d4cb846ef5956102f08fecd6e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015935"
---
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 tożsamości tylko w chmurze

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli wybrano model tożsamości tylko w chmurze, masz już dzierżawę usługi Azure Active Directory (Azure AD) dla subskrypcji usługi Microsoft 365 do przechowywania wszystkich użytkowników, grup i kontaktów. Po skonfigurowaniu ochrony kont administratora w kroku [2](protect-your-global-administrator-accounts.md) i kontach użytkowników w kroku [3](microsoft-365-secure-sign-in.md) tego rozwiązania możesz rozpocząć tworzenie nowych kont i grup, których potrzebuje Twoja organizacja.

Oto podstawowe składniki tożsamości tylko w chmurze.
 
![Podstawowe składniki tożsamości tylko w chmurze.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Użytkownicy i ich konta użytkowników w organizacjach można kategoryzować na wiele sposobów. Na przykład niektórzy są pracownikami i mają stały status. Niektórzy są dostawcami, kontrahentami lub partnerami, którzy mają tymczasowy stan. Niektórzy to użytkownicy zewnętrzni, którzy nie mają kont użytkowników, ale nadal muszą mieć przyznany dostęp do określonych usług i zasobów, aby obsługiwać interakcje i współpracę. Przykład:

- Konta dzierżawy reprezentują użytkowników w organizacji, do których masz licencję na usługi w chmurze

- Konta B2B (Business to Business) reprezentują użytkowników spoza organizacji, których zaprosisz do współpracy

Umożliwia sporządzanie danych różnych typów użytkowników w organizacji. Co to są grupy? Na przykład możesz pogrupować użytkowników według funkcji wysokiego poziomu lub przeznaczenia w organizacji.

Ponadto niektóre usługi w chmurze można udostępniać użytkownikom spoza organizacji bez jakichkolwiek kont. Musisz także zidentyfikować te grupy użytkowników.

Grup w usłudze Azure AD można używać do wielu celów, które upraszczają zarządzanie środowiskiem w chmurze. Na przykład dzięki grupom usługi Azure AD możesz:

- Przy użyciu licencjonowania grupowego możesz automatycznie przypisywać licencje Microsoft 365 do kont użytkowników zaraz po ich dodaniu jako członków.
- Dynamiczne dodawanie kont użytkowników do określonych grup na podstawie atrybutów konta użytkownika, takich jak nazwa działu.
- Automatyczne inicjowanie obsługi użytkowników dla aplikacji SaaS (Software as a Service) oraz ochronę dostępu do tych aplikacji za pomocą uwierzytelniania wieloskładnikowego (MFA) i innych zasad dostępu warunkowego.
- Zapewnianie uprawnień i poziomów dostępu do zespołów i witryn SharePoint zespołów w trybie online.

## <a name="next-steps-for-cloud-only-identity"></a>Następne kroki dotyczące tożsamości tylko w chmurze

- [Zarządzanie kontami użytkowników](manage-microsoft-365-accounts.md)
- [Przypisywanie licencji do kont użytkowników](assign-licenses-to-user-accounts.md)
- [Zarządzanie grupami i członkostwem w grupach](manage-microsoft-365-groups.md)
- [Zarządzanie hasłami do kont użytkowników](manage-microsoft-365-passwords.md)
