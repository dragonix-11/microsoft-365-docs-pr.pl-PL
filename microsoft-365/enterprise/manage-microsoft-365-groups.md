---
title: Zarządzaj grupami platformy Microsoft 365
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
description: Dowiedz się, jak zarządzać grupami Microsoft 365.
ms.openlocfilehash: 0e7cef7d1b55f695af9a33f22393172f6eee6485
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100506"
---
# <a name="manage-microsoft-365-groups"></a>Zarządzaj grupami platformy Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Grupy Microsoft 365 można zarządzać na kilka różnych sposobów, w zależności od konfiguracji. Kontami użytkowników można zarządzać w [Centrum administracyjne platformy Microsoft 365](/admin), programie PowerShell w Active Directory Domain Services (AD DS) lub w [centrum administracyjnym Azure Active Directory (Azure AD).](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>Planowanie miejsca i sposobu zarządzania grupami

Miejsce i sposób zarządzania kontami użytkowników zależy od modelu tożsamości, którego chcesz użyć dla Microsoft 365. Dwa ogólne modele są tylko w chmurze i hybrydowe.
  
### <a name="cloud-only"></a>Tylko w chmurze

Grupy można tworzyć i zarządzać nimi za pomocą:

- [Centrum administracyjne platformy Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Centrum administracyjne usługi Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>Hybrydowa

Grupy usług AD DS są synchronizowane z Microsoft 365 z usług AD DS, więc do zarządzania tymi grupami należy użyć lokalnych narzędzi usług AD DS.

Można również tworzyć grupy usługi Azure AD i zarządzać nimi, które są oddzielone od grup usług AD DS, ale mogą zawierać użytkowników i grupy z usług AD DS. W tym przypadku można użyć następujących elementów:

- [Centrum administracyjne platformy Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Centrum administracyjne usługi Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Zezwalaj użytkownikom na tworzenie własnych grup i zarządzanie nimi

Usługa Azure AD zezwala na grupy, które mogą być zarządzane przez właścicieli grup zamiast administratorów IT. Ta funkcja, znana jako *samoobsługowe zarządzanie grupami*, umożliwia właścicielom grup, którzy nie mają przypisanej roli administracyjnej, tworzenie grup zabezpieczeń i zarządzanie nimi. 

Użytkownicy mogą żądać członkostwa w grupie zabezpieczeń i to żądanie jest wysyłane do właściciela grupy, a nie do administratora IT. Dzięki temu codzienna kontrola członkostwa w grupie może być delegowana do zespołu, projektu lub właścicieli firm, którzy rozumieją użycie biznesowe grupy i mogą zarządzać jej członkostwem.

>[!Note]
>Samoobsługowe zarządzanie grupami jest dostępne tylko dla grup zabezpieczeń i Microsoft 365 usługi Azure AD. Nie jest ona dostępna dla grup obsługujących pocztę, list dystrybucyjnych ani żadnej grupy, która została zsynchronizowana z usług AD DS.
>

Aby uzyskać więcej informacji, zobacz [instrukcje dotyczące konfigurowania grupy usługi Azure AD na potrzeby samoobsługowego zarządzania](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>Konfigurowanie dynamicznego członkostwa w grupie

Usługa Azure AD obsługuje konfigurowanie serii reguł, które automatycznie dodają lub usuwają konta użytkowników jako członków grupy usługi Azure AD. Jest to *nazywane dynamicznym członkostwem w grupach*. Reguły są oparte na atrybutach konta użytkownika, takich jak Dział lub Kraj.

Oto jak są stosowane reguły:

- Jeśli nowe konto użytkownika jest zgodne ze wszystkimi regułami grupy, staje się członkiem.
- Jeśli konto użytkownika nie jest członkiem grupy, ale jego atrybuty zmieniają się tak, aby pasowały do wszystkich reguł grupy, staje się członkiem tej grupy.
- Jeśli konto użytkownika nie jest zgodne ze wszystkimi regułami grupy, nie zostanie dodane do grupy.
- Jeśli konto użytkownika jest członkiem grupy, ale jego atrybuty zmieniają się tak, aby nie odpowiadało już wszystkim regułom grupy, zostanie usunięte jako członek grupy.

Aby korzystać z członkostwa dynamicznego, należy najpierw określić zestawy grup, które mają wspólny zestaw atrybutów konta użytkownika. Na przykład wszyscy członkowie działu sprzedaży powinni znajdować się w grupie Sales Azure AD na podstawie atrybutu konta użytkownika Działu ustawionego na "Sales".

Zapoznaj [się z instrukcjami dotyczącymi tworzenia i konfigurowania reguł dla dynamicznej grupy usługi Azure AD](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>Konfigurowanie automatycznego licencjonowania

Grupy zabezpieczeń w usłudze Azure AD można skonfigurować tak, aby automatycznie przypisywać licencje z zestawu subskrypcji do wszystkich członków grupy. Jest to *nazywane licencjonowaniem opartym na grupach*. Jeśli konto użytkownika zostanie dodane do grupy lub usunięte z grupy, licencje dla subskrypcji grupy zostaną automatycznie przypisane lub nie zostaną przypisane z konta użytkownika.

W przypadku Microsoft 365 Enterprise skonfigurujesz grupy zabezpieczeń usługi Azure AD w celu przypisania odpowiedniej licencji Microsoft 365 Enterprise.

Upewnij się, że masz wystarczającą liczbę licencji dla wszystkich członków grupy. Jeśli zabraknie Ci licencji, nowi użytkownicy nie będą przypisywani licencji, dopóki licencje nie staną się dostępne.

>[!Note]
>Nie należy konfigurować licencjonowania opartego na grupach dla grup zawierających konta biznesowe platformy Azure (B2B).
>

Aby uzyskać więcej informacji, zobacz [Podstawowe informacje dotyczące licencjonowania opartego na grupach w usłudze Azure AD](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

Zapoznaj [się z instrukcjami konfigurowania licencjonowania opartego na grupach dla grupy zabezpieczeń platformy Azure](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).