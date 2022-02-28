---
title: Zarządzanie Microsoft 365 tożsamością
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
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Dowiedz się, jak korzystać z Microsoft 365 zarządzania tożsamościami.
ms.openlocfilehash: 35b2092412ddbeacd5d6962e110de1931b2d0f4b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977610"
---
# <a name="manage-microsoft-365-identity-governance"></a>Zarządzanie Microsoft 365 tożsamością

Zarządzanie tożsamością to przede wszystkim ochrona, monitorowanie i inspekcja dostępu do krytycznych zasobów przy jednoczesnym zapewnieniu produktywności pracowników. Na przykład za pomocą zarządzania tożsamością można zapewnić odpowiednim użytkownikom odpowiedni dostęp do odpowiednich zasobów i określić, czy dostęp do nich zmieni się z czasem.

Aby uzyskać więcej informacji, zobacz omówienie zarządzania [tożsamością w Azure Active Directory (Azure AD).](/azure/active-directory/governance/identity-governance-overview)

## <a name="set-up-azure-ad-access-reviews"></a>Konfigurowanie recenzji dostępu do usługi Azure AD

Recenzje dostępu do usługi Azure AD umożliwiają sprawdzenie dostępu użytkownika, aby upewnić się, że tylko odpowiednie osoby nadal mają dostęp. Przykład:

- Gdy nowy pracownik dołącza do Twojej organizacji, musisz mieć pewność, że ma odpowiedni dostęp do produktywnej pracy.
- Gdy pracownik przechodzi do innych zespołów, lokalizacji lub działów, musisz upewnić się, że dostęp tego pracownika do poprzednich zespołów, lokalizacji lub działów zostanie w razie potrzeby usunięty.
- Gdy ten pracownik lub gość odchodzi z organizacji, musisz upewnić się, że jego dostęp został usunięty.

Jest to szczególnie ważne, jeśli organizacja podlega inspekcji zabezpieczeń w celu określenia, czy konta użytkowników mają zbyt duży dostęp, co może skutkować naruszeń przepisów branżowych lub regionalnych.

Aby uzyskać więcej informacji, zobacz [omówienie recenzji dostępu](/azure/active-directory/governance/access-reviews-overview).

Zobacz te artykuły, aby skonfigurować różne typy recenzji dostępu:

- [Grupy i aplikacje](/azure/active-directory/governance/create-access-review)
- [Role w usłudze Azure AD](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Role zasobów platformy Azure](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>Konfigurowanie zarządzania uprawnieniami do usługi Azure AD

Zarządzanie uprawnieniami do usługi Azure AD umożliwia zarządzanie cyklem życia tożsamości i dostępu w skali przez automatyzację przepływów pracy żądań dostępu, uzyskiwania dostępu do zadań, recenzowania i wygasania.

Aby wykonać swoją pracę, pracownicy muszą mieć dostęp do różnych grup, aplikacji i witryn. Zarządzanie tym dostępem może być trudne, ponieważ zmieniają się wymagania, dodawane są nowe aplikacje lub użytkownicy muszą mieć dodatkowe prawa dostępu. Jeśli współpracujesz z innymi organizacjami, możesz nie wiedzieć, kto w tej organizacji potrzebuje dostępu do zasobów Organizacji, a użytkownicy zewnętrzni nie będą wiedzieć, jakich aplikacji, grup lub witryn używa Twoja organizacja.

Zarządzanie uprawnieniami do usługi Azure AD może ułatwić wydajniejsze zarządzanie dostępem do grup, aplikacji i witryn SharePoint użytkowników wewnętrznych i zewnętrznych.
 
Aby uzyskać więcej informacji, zobacz [omówienie zarządzania uprawnieniami do usługi Azure AD](/azure/active-directory/governance/entitlement-management-overview).