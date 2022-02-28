---
title: Zarządzanie Microsoft 365 grupami
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
description: Dowiedz się, jak zarządzać Microsoft 365 grupami.
ms.openlocfilehash: 28d8bae8aaed6d02fe082824c07afe03bdc0ce5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977611"
---
# <a name="manage-microsoft-365-groups"></a>Zarządzanie Microsoft 365 grupami

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Możesz zarządzać Microsoft 365 na kilka różnych sposobów, w zależności od konfiguracji. Kontami użytkowników można zarządzać w programie [centrum administracyjne platformy Microsoft 365](/admin), PowerShell, w programie Usługi domenowe w usłudze Active Directory (AD DS) lub w centrum administracyjnym usługi [Azure Active Directory (Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)). 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>Planowanie miejsca i sposobu zarządzania grupami

Miejsce i sposób zarządzania kontami użytkowników zależy od modelu tożsamości, którego chcesz używać na Microsoft 365. Dwa ogólne modele są oparte na chmurze i hybrydowe.
  
### <a name="cloud-only"></a>Tylko w chmurze

Do tworzenia grup i zarządzania nimi używasz:

- [The centrum administracyjne platformy Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Centrum administracyjne usługi Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>Hybrydowe

AD DS grupy są synchronizowane Microsoft 365 z programu AD DS, więc do zarządzania tymi grupami należy używać lokalnych narzędzi AD DS.

Możesz również tworzyć grupy usługi Azure AD, które są niezależne od grup usługi AD DS i zarządzać nimi, ale mogą zawierać użytkowników i grupy z usługi AD DS. W takim przypadku możesz użyć:

- [The centrum administracyjne platformy Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Centrum administracyjne usługi Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Zezwalanie użytkownikom na tworzenie własnych grup i zarządzanie nimi

Usługa Azure AD umożliwia grupom, które mogą być zarządzane przez właścicieli grup zamiast administratorów IT. Ta funkcja *, znana jako samoobsługowe* zarządzanie grupami, umożliwia właścicielom grup, którym nie przypisano roli administracyjnej, tworzenie grup zabezpieczeń i zarządzanie nimi. 

Użytkownicy mogą zażądać członkostwa w grupie zabezpieczeń, a to żądanie trafia do właściciela grupy, a nie do administratora IT. Umożliwia to delegowanie dziennej kontroli członkostwa w grupie do zespołu, projektu lub właścicieli firm, którzy rozumieją zastosowanie biznesowe grupy i mogą zarządzać jej członkostwem.

>[!Note]
>Samoobsługowe zarządzanie grupami jest dostępne tylko dla zabezpieczeń i grup usługi Azure AD Microsoft 365 grupy. Nie jest dostępna dla grup z obsługą poczty, list dystrybucyjnych ani żadnej grupy zsynchronizowanej z usługą AD DS.
>

Aby uzyskać więcej informacji, zobacz [instrukcje dotyczące konfigurowania grupy usługi Azure AD do samoobsługowego zarządzania](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>Konfigurowanie dynamicznego członkostwa w grupach

Usługa Azure AD obsługuje konfigurowanie serii reguł, które automatycznie dodają lub usuwają konta użytkowników jako członków grupy usługi Azure AD. Jest to nazywane *dynamicznym członkostwem w grupach*. Reguły są oparte na atrybutach konta użytkownika, takich jak Department (Dział) lub Country (Kraj).

Oto jak są stosowane te reguły:

- Jeśli nowe konto użytkownika będzie odpowiadać wszystkim regułom grupy, staje się ono członkiem.
- Jeśli konto użytkownika nie jest członkiem grupy, ale jego atrybuty zmieniają się tak, że są takie, jak wszystkie reguły grupy, staje się ono członkiem tej grupy.
- Jeśli konto użytkownika nie jest zgodne ze wszystkimi regułami grupy, nie jest dodawane do grupy.
- Jeśli konto użytkownika jest członkiem grupy, ale jego atrybuty zmieniają się, tak że nie są już takie samo jak wszystkie reguły grupy, są usuwane jako członek grupy.

Aby korzystać z członkostwa dynamicznego, należy najpierw określić zestawy grup o wspólnym zestawie atrybutów konta użytkownika. Na przykład wszyscy członkowie działu sprzedaży powinni być w grupie Sales Azure AD na podstawie atrybutu konta użytkownika ustawionego na wartość "Sprzedaż".

Zobacz [instrukcje tworzenia i konfigurowania reguł dla dynamicznej grupy usługi Azure AD](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>Konfigurowanie licencjonowania automatycznego

Możesz skonfigurować grupy zabezpieczeń w usłudze Azure AD, aby automatycznie przypisywać licencje z zestawu subskrypcji do wszystkich członków grupy. Jest to nazywane *licencjonowaniem grup.* Jeśli konto użytkownika zostanie dodane do grupy lub usunięte z tej grupy, licencje dla subskrypcji grupy zostaną automatycznie przypisane do konta użytkownika lub usunięte z tego konta.

Na Microsoft 365 Enterprise skonfigurujesz grupy zabezpieczeń usługi Azure AD w celu przypisania odpowiedniej Microsoft 365 Enterprise zabezpieczeń.

Upewnij się, że masz wystarczającą ilość licencji dla wszystkich członków grupy. Jeśli zabraknie licencji, nowym użytkownikom nie zostaną przypisane licencje, dopóki licencje nie staną się dostępne.

>[!Note]
>Nie należy konfigurować licencjonowania grupowego dla grup, które zawierają konta B2B (Dla firm) platformy Azure.
>

Aby uzyskać więcej informacji, zobacz [Podstawowe informacje o licencjonowaniu opartym na grupach w usłudze Azure AD](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

Zapoznaj się [z instrukcjami dotyczącymi konfigurowania licencjonowania grupowego dla grupy zabezpieczeń platformy Azure](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).