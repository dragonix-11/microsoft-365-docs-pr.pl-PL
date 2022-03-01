---
title: Planowanie zarządzania organizacją i cyklem życia Microsoft 365 grup i Microsoft Teams
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Informacje o opcjach zarządzania cyklem życia narzędzi do współpracy w programie Microsoft 365
ms.openlocfilehash: a0f4622afd1a22b8cd6574865012b7f636fc06c5
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63004955"
---
# <a name="plan-organization-and-lifecycle-governance-for-microsoft-365-groups-and-microsoft-teams"></a>Planowanie zarządzania organizacją i cyklem życia Microsoft 365 grup i Microsoft Teams

Microsoft 365 grupy mają bogaty zestaw narzędzi do wdrażania funkcji zarządzania wymaganych przez organizację. 

W poniższej sekcji opisano te funkcje, po polecane są najlepsze rozwiązania i podajemy wskazówki dotyczące zadawania odpowiednich pytań w celu określenia wymagań w zakresie zarządzania i sposobu ich spełnienia.

## <a name="control-who-can-create-microsoft-365-groups"></a>Kontrolowanie, kto może tworzyć Microsoft 365 grupy

Grupy mogą być tworzone przez użytkowników końcowych w wielu punktach końcowych, takich Outlook, SharePoint, Teams i innych środowisk.

![image desc.](../media/04.png)

Zdecydowanie zalecamy korzystanie z samoobsługi w celu wzmocnienia pozycji właścicieli grup i ułatwić użytkownikom korzystanie z nich. Ograniczenie możliwości tworzenia grup i  zespołu może spowalniać pracę użytkowników, ponieważ wiele Microsoft 365 wymaga tworzenia grup, aby usługa działała.

Rozważ następujące opcje zarządzania tworzeniem grup:

- Aby ograniczyć sprawną grupę, użyj [](microsoft-365-groups-expiration-policy.md) zasad wygasania grup, aby automatycznie usuwać grupy, które nie są używane.
- Ograniczanie tworzenia grup do członków grup [zabezpieczeń z dynamicznym](/azure/active-directory/users-groups-roles/groups-create-rule) członkostwem, na przykład ze wszystkimi pracownikami zatrudnieni na pełny etat.
- Ogranicz tworzenie grup do grupy zabezpieczeń i wymagaj od użytkowników ukończenia szkolenia w zakresie zasad używania grup w Organizacji, aby zostać członkami grupy zabezpieczeń.

Jeśli chcesz ograniczyć liczbę osób, które mogą tworzyć grupy, zobacz Zarządzanie tym, kto może tworzyć Microsoft 365 [grupy](manage-creation-of-groups.md), aby uzyskać informacje o tym, jak to skonfigurować.

## <a name="group-delete-restore-and-archiving"></a>Grupowanie usuwania, przywracania i archiwizowania

Po usunięciu Microsoft 365 grupa jest domyślnie zachowywana przez 30 dni. Ten 30-dniowy okres jest nazywany „miękkim usunięciem", ponieważ nadal można przywrócić grupę. Po 30 dniach grupa i skojarzona zawartość zostaną trwale usunięte i nie będzie można ich przywrócić.

Jeśli w miejscu są przechowywane zasady przechowywania, które zachowują czat, pliki lub pocztę, te elementy zostaną zachowane po usunięciu grupy. Aby [uzyskać szczegółowe informacje, zobacz Informacje o zasadach](../compliance/retention.md) przechowywania.

Jeśli chcesz usunąć grupę, ale zachować zawartość jednej lub kilku usług połączonych z grupą, zobacz Archiwizowanie grup[,](end-life-cycle-groups-teams-sites-yammer.md) zespołów i Yammer, aby uzyskać informacje.

## <a name="group-naming-policy"></a>Zasady nazewnictwa grup

Zasady nazewnictwa grup mogą ułatwić nadawanie nazwy grupom na dwa sposoby:

- Zasady nazewnictwa prefiksów i sufiksów mogą być używane do wymuszania stałych ciągów lub atrybutów usługi Azure AD na początku lub końcu nazwy grupy i skojarzonego z nią adresu e-mail. W ten sposób możesz zapewnić uwzględnianie na przykład nazw działów lub regionów w nazwach grup.
- Zasady dotyczące zablokowanych wyrazów mogą zapewnić, że w nazwach grup nie będą używane określone wyrazy, na przykład nazwiska kadry kierowniczej.

Zasady nazewnictwa są stosowane, gdy grupy są tworzone z dowolnej usługi połączonej z grupą.

Jeśli zdecydujesz się na stosowanie zasad nazewnictwa dla grup, zobacz Zasady [nazewnictwa Microsoft 365 grup](groups-naming-policy.md).

## <a name="group-expiration-policy"></a>Zasady wygasania grupy

Możesz określić okres wygaśnięcia, a każda grupa, która osiągnie koniec tego okresu i nie zostanie odnowiona, zostanie usunięta. Okres wygasania grupy rozpoczyna się od daty jej utworzenia lub od daty jej ostatniego odnowienia.

Po skonfigurowaniu grup do wygaśnięcia:
- Właściciele grupy są powiadomieni o zbliżaniu się wygaśnięcia grupy.
- Aktywne grupy są odnawiane automatycznie.
- Wszystkie grupy, które nie zostaną odnowione, zostaną usunięte.
- Każda usunięta grupa może zostać przywrócona przez właścicieli grupy lub administratora w ciągu 30 dni.

Zasady wygasania to dobry sposób na ograniczenie rozrastania grupy przez upewnienie się, że usunięte są już nieuzyskane grupy. Jeśli chcesz utworzyć zasady wygasania grup, zobacz Microsoft 365 [wygasania grup](microsoft-365-groups-expiration-policy.md).

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Usuwanie byłego pracownika i zabezpieczanie danych](/microsoft-365/admin/add-users/remove-former-employee)
