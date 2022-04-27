---
title: Zarządzanie Microsoft 365 zarządzaniem tożsamościami
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak używać funkcji zarządzania tożsamościami Microsoft 365.
ms.openlocfilehash: f4fcfed9fcb978e40c3bf7c0e7a35eb717fee343
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091176"
---
# <a name="manage-microsoft-365-identity-governance"></a>Zarządzanie Microsoft 365 zarządzaniem tożsamościami

Zarządzanie tożsamościami polega na ochronie, monitorowaniu i inspekcji dostępu do krytycznych zasobów przy jednoczesnym zapewnieniu produktywności pracowników. Na przykład w przypadku zarządzania tożsamościami można upewnić się, że odpowiedni użytkownicy mają odpowiedni dostęp do odpowiednich zasobów i określić, czy ten dostęp zmienia się wraz z upływem czasu.

Aby uzyskać więcej informacji, zobacz [omówienie zarządzania tożsamościami dla Azure Active Directory (Azure AD)](/azure/active-directory/governance/identity-governance-overview).

## <a name="set-up-azure-ad-access-reviews"></a>Konfigurowanie przeglądów dostępu do usługi Azure AD

Przeglądy dostępu usługi Azure AD umożliwiają przeglądanie dostępu użytkownika w celu zapewnienia ciągłego dostępu tylko odpowiednim osobom. Przykład:

- Gdy nowy pracownik dołączy do Twojej organizacji, musisz mieć pewność, że ma on odpowiedni dostęp, aby zapewnić produktywność.
- Gdy pracownik przechodzi do innych zespołów, lokalizacji lub działów, musisz upewnić się, że ich dostęp do poprzednich zespołów, lokalizacji lub działów zostanie usunięty w razie potrzeby.
- Gdy ten pracownik lub gość opuści organizację, musisz upewnić się, że jego dostęp zostanie usunięty.

Jest to szczególnie ważne, jeśli organizacja podlega audytom zabezpieczeń w celu ustalenia, czy konta użytkowników mają zbyt duży dostęp, co może skutkować karami, jeśli naruszają przepisy branżowe lub regionalne.

Aby uzyskać więcej informacji, zobacz [przegląd przeglądów dostępu](/azure/active-directory/governance/access-reviews-overview).

Zobacz następujące artykuły, aby skonfigurować różne typy przeglądów dostępu:

- [Grupy i aplikacje](/azure/active-directory/governance/create-access-review)
- [Role usługi Azure AD](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Role zasobów platformy Azure](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>Konfigurowanie zarządzania uprawnieniami usługi Azure AD

Zarządzanie uprawnieniami usługi Azure AD w usłudze Wiht umożliwia zarządzanie cyklem życia tożsamości i dostępu na dużą skalę przez automatyzację przepływów pracy żądań dostępu, przypisań dostępu, przeglądów i wygasania.

Pracownicy potrzebują dostępu do różnych grup, aplikacji i witryn, aby wykonywać swoje zadania. Zarządzanie tym dostępem może być trudne, ponieważ zmieniają się wymagania, dodawane są nowe aplikacje lub użytkownicy potrzebują dodatkowych praw dostępu. Podczas współpracy z innymi organizacjami możesz nie wiedzieć, kto w innej organizacji potrzebuje dostępu do zasobów organizacji, a użytkownicy zewnętrzni nie będą wiedzieć, z jakich aplikacji, grup lub witryn korzysta twoja organizacja.

Zarządzanie uprawnieniami usługi Azure AD może pomóc w wydajniejszym zarządzaniu dostępem do grup, aplikacji i witryn SharePoint dla użytkowników wewnętrznych i zewnętrznych.
 
Aby uzyskać więcej informacji, zobacz [omówienie zarządzania uprawnieniami usługi Azure AD](/azure/active-directory/governance/entitlement-management-overview).