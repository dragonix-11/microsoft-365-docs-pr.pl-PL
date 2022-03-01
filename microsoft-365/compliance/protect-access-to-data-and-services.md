---
title: Ochrona dostępu użytkownika i urządzenia
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 4/17/2018
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: Dowiedz się, jak chronić dostęp użytkowników i urządzeń do Microsoft 365 i usług oraz chronić się przed utratą danych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 121c5b8f1168e9986693fea128aa66626b3e31fe
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014746"
---
# <a name="protect-user-and-device-access"></a>Ochrona dostępu użytkownika i urządzenia

Ochrona dostępu do Twoich Microsoft 365 danych i usług jest kluczowa podczas obrony przed cyberatakami i ochrony przed utratą danych. Te same zabezpieczenia można stosować do innych aplikacji SaaS w Twoim środowisku, a nawet do aplikacji lokalnych opublikowanych za Azure Active Directory proxy aplikacji.
  
## <a name="step-1-review-recommendations"></a>Krok 1. Przejrzyj zalecenia

Zalecane funkcje ochrony tożsamości i urządzeń, które mają Office 365 dostępu do usług SaaS, innych usług SaaS oraz aplikacji lokalnych opublikowanych za pomocą serwera proxy aplikacji Azure AD.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) |  [](https://go.microsoft.com/fwlink/p/?linkid=841657) |  Visio [Więcej języków](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>Krok 2. Ochrona kont administratora i dostępu
Konta administracyjne służące do administrowania środowiskiem Microsoft 365 mają podwyższony poziom uprawnień. Są to wartościowe cele dla hakerów i cyberprzestępczych. 

Zacznij od używania kont administratora tylko do administrowania. Administratorzy powinni mieć oddzielne konto użytkownika do regularnego, nieadministracyjnym i używać swojego konta administracyjnego tylko wtedy, gdy jest to konieczne do wykonania zadania skojarzonego z ich funkcją.

Konta administratora można chronić za pomocą uwierzytelniania wieloskładnikowego i dostępu warunkowego. Aby uzyskać więcej informacji, zobacz [Chronienie kont administratora](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

Następnie skonfiguruj zarządzanie dostępem uprzywilejowanym w programie Office 365. Zarządzanie dostępem z uprawnieniami umożliwia szczegółową kontrolę dostępu nad zadaniami administratora z uprawnieniami w Office 365. Pomaga chronić organizację przed naruszeniem zabezpieczeń, które mogą korzystać z istniejących uprzywilejowanych kont administratora z dostępem do poufnych danych lub dostępem do krytycznych ustawień konfiguracji.

- [Omówienie zarządzania dostępem z uprawnieniami](privileged-access-management-overview.md)
- [Konfigurowanie zarządzania dostępem z uprawnieniami](privileged-access-management-configuration.md)

Innym górnym zaleceniem jest korzystanie ze stacji roboczych specjalnie skonfigurowanych do pracy administracyjnej. Są to urządzenia dedykowane, które są używane tylko do zadań administracyjnych. Zobacz [Zabezpieczanie dostępu z uprawnieniami](/windows-server/identity/securing-privileged-access/securing-privileged-access).

Na koniec można zminimalizować wpływ niezamierzonego braku dostępu administracyjnego, tworząc co najmniej dwa konta dostępu dla służb ratunkowych w dzierżawie. Zobacz [Zarządzanie kontami dostępu alarmowego w usłudze Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>Krok 3. Konfigurowanie zalecanych zasad dostępu do urządzenia i tożsamości
Uwierzytelnianie wieloskładnikowe (MFA) i zasady dostępu warunkowego to zaawansowane narzędzia do ograniczania przed naruszonymi kontami i nieautoryzowanym dostępem. Zalecamy zaimplementowanie zestawu testowanych razem zasad. Aby uzyskać więcej informacji, w tym kroki wdrażania, zobacz [Konfiguracje tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md).

 Te zasady wdrażają następujące funkcje:
- Uwierzytelnianie wieloskładnikowe
- Dostęp warunkowy
- Ochrona aplikacji Intune (aplikacja i ochrona danych dla urządzeń)
- Zgodność urządzenia w usłudze Intune
- Azure AD Identity Protection

Wdrażanie zgodności urządzenia Intune wymaga rejestracji urządzenia. Zarządzanie urządzeniami umożliwia zagwarantowanie, że są one w dobrej kondycji i zgodne, zanim umożliwią im dostęp do zasobów w Twoim środowisku. Zobacz [Rejestrowanie urządzeń do zarządzania w usłudze Intune.](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>Krok 4. Konfigurowanie SharePoint dostępu do urządzenia

Firma Microsoft zaleca ochronę zawartości w witrynach SharePoint za pomocą poufnych i ściśle uregulowanych treści za pomocą kontroli dostępu do urządzeń. Aby uzyskać więcej informacji, zobacz [Zalecenia dotyczące zasad dotyczące SharePoint witryn i plików](../security/office-365-security/sharepoint-file-access-policies.md).



