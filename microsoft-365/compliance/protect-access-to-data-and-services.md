---
title: Ochroń dostęp użytkowników i urządzeń
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 4/17/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: Dowiedz się, jak chronić dostęp użytkowników i urządzeń do danych i usług platformy Microsoft 365 oraz bronić się przed utratą danych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f8b6b266d037e8bbc185643e530bf7a2f6919038
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623716"
---
# <a name="protect-user-and-device-access"></a>Ochroń dostęp użytkowników i urządzeń

Ochrona dostępu do danych i usług platformy Microsoft 365 ma kluczowe znaczenie dla obrony przed cyberatakami i ochrony przed utratą danych. Te same zabezpieczenia mogą być stosowane do innych aplikacji SaaS w środowisku, a nawet do aplikacji lokalnych opublikowanych za pomocą usługi Azure Active Directory serwer proxy aplikacji.
  
## <a name="step-1-review-recommendations"></a>Krok 1. Przegląd zaleceń

Zalecane możliwości ochrony tożsamości i urządzeń uzyskujących dostęp do Office 365, innych usług SaaS i aplikacji lokalnych opublikowanych za pomocą Azure AD serwer proxy aplikacji.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) |  [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657) |  [Więcej języków](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>Krok 2. Ochrona kont administratorów i dostępu

Konta administracyjne używane do administrowania środowiskiem platformy Microsoft 365 obejmują podwyższone uprawnienia. Są to cenne cele dla hakerów i cyberataków.

Rozpocznij od używania kont administratora tylko do administrowania. Administratorzy powinni mieć oddzielne konto użytkownika do regularnego, nieadministracyjnyego użytku i używać konta administracyjnego tylko wtedy, gdy jest to konieczne do wykonania zadania skojarzonego z funkcją zadania.

Chroń konta administratorów za pomocą uwierzytelniania wieloskładnikowego i dostępu warunkowego. Aby uzyskać więcej informacji, zobacz [Ochrona kont administratorów](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

Następnie skonfiguruj usługę Microsoft Purview Privileged Access Management. Zarządzanie dostępem uprzywilejowanym umożliwia szczegółową kontrolę dostępu nad uprzywilejowanymi zadaniami administratora w Office 365. Może pomóc chronić organizację przed naruszeniami, które mogą korzystać z istniejących kont administratorów uprzywilejowanych z dostępem do poufnych danych lub dostępem do krytycznych ustawień konfiguracji.

- [Omówienie zarządzania dostępem uprzywilejowanym](privileged-access-management.md)
- [Konfigurowanie zarządzania dostępem uprzywilejowanym](privileged-access-management-configuration.md)

Innym najlepszym zaleceniem jest użycie stacji roboczych specjalnie skonfigurowanych do pracy administracyjnej. Są to dedykowane urządzenia, które są używane tylko do zadań administracyjnych. Zobacz [Zabezpieczanie dostępu uprzywilejowanego](/windows-server/identity/securing-privileged-access/securing-privileged-access).

Na koniec możesz ograniczyć wpływ niezamierzonego braku dostępu administracyjnego, tworząc co najmniej dwa konta dostępu awaryjnego w dzierżawie. Zobacz [Zarządzanie kontami dostępu awaryjnego w Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>Krok 3. Konfigurowanie zalecanych zasad dostępu do tożsamości i urządzeń

Zasady uwierzytelniania wieloskładnikowego (MFA) i dostępu warunkowego to zaawansowane narzędzia do ograniczania naruszonych kont i nieautoryzowanego dostępu. Zalecamy zaimplementowanie zestawu zasad, które zostały przetestowane razem. Aby uzyskać więcej informacji, w tym kroki wdrażania, zobacz [Konfiguracje tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md).

 Te zasady implementują następujące możliwości:

- Uwierzytelnianie wieloskładnikowe
- Dostęp warunkowy
- Intune ochrony aplikacji (ochrona aplikacji i danych dla urządzeń)
- zgodność Intune urządzeniami
- Ochrona tożsamości w usłudze Azure AD

Implementowanie zgodności urządzeń Intune wymaga rejestracji urządzenia. Zarządzanie urządzeniami pozwala upewnić się, że są one w dobrej kondycji i zgodne przed zezwoleniem im na dostęp do zasobów w środowisku. Zobacz [Rejestrowanie urządzeń do zarządzania w Intune](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>Krok 4. Konfigurowanie zasad dostępu urządzeń programu SharePoint

Firma Microsoft zaleca ochronę zawartości w witrynach programu SharePoint za pomocą poufnych i wysoce regulowanych treści za pomocą kontroli dostępu do urządzeń. Aby uzyskać więcej informacji, zobacz [Zalecenia dotyczące zasad dotyczące zabezpieczania witryn i plików programu SharePoint](../security/office-365-security/sharepoint-file-access-policies.md).
