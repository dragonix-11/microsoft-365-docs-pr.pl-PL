---
title: Opis kolejności zasad w programie Microsoft Defender dla firm (wersja Preview)
description: Dowiedz się więcej o kolejności priorytetów dzięki zasadom w programie Microsoft Defender dla firm (wersja Preview)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 01d6b5cc77068bc8f86d4a32777663ae251acd8d
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027065"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business-preview"></a>Opis kolejności zasad w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>Kolejność zasad w programie Microsoft Defender dla firm

Usługa Microsoft Defender dla firm (wersja Preview) zawiera wstępnie zdefiniowane zasady, które zapewniają ochronę urządzeń, z których korzystają Twoi pracownicy. Zespół zabezpieczeń może również dodawać nowe zasady. Załóżmy na przykład, że chcesz zastosować pewne ustawienia do niektórych urządzeń, a inne dla innych urządzeń. Możesz to zrobić, dodając zasady, takie jak zasady ochrony następnej generacji lub zasady zapory.

Po dodaniu zasad zauważysz, że przypisano kolejność priorytetów. Możesz edytować kolejność priorytetów definiowania zasad, ale nie możesz zmienić kolejności priorytetów zasad domyślnych. Załóżmy na przykład, że dla Windows klienckich są trzy zasady ochrony następnej generacji. W tym przypadku zasady domyślne mają priorytet numer 3. Możesz zmienić kolejność zasad o numerach 1 i 2, ale domyślne zasady pozostaną na liście wartością 3. 

**Ważne, aby pamiętać o wielu zasadach, to to, że urządzenia będą otrzymywać tylko pierwsze zastosowane zasady.** Odwołując się do naszego wcześniejszego przykładu trzech zasad następnej generacji, załóżmy, że masz urządzenia, do których odnoszą się wszystkie trzy zasady. W takim przypadku te urządzenia otrzymają zasady numer 1, ale nie będą otrzymywać zasad o numerach 2 i 3. 

## <a name="key-points-to-remember-about-policy-order"></a>Najważniejsze kwestie do zapamiętania o kolejności zasad

- Zasady mają przypisaną kolejność priorytetów

- Urządzenia otrzymują tylko pierwsze zastosowane zasady

- Kolejność priorytetów zasad można zmienić

- Zasady domyślne mają najniższy priorytet

## <a name="next-steps"></a>Następne kroki

- [Wprowadzenie do korzystania z usługi Defender dla firm (wersja Preview)](mdb-get-started.md)

- [Zarządzanie urządzeniami](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm (wersja Preview)](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)