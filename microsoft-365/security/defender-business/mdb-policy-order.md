---
title: Opis kolejności zasad w programie Microsoft Defender dla firm
description: Dowiedz się więcej o kolejności priorytetów przy użyciu zasad w programie Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 18e4675f3c9448a8ee24fbb8f623599baaf79b4f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329337"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>Opis kolejności zasad w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>Kolejność zasad w programie Microsoft Defender dla firm

Usługa Microsoft Defender dla firm zawiera wstępnie zdefiniowane zasady zapewniające ochronę urządzeń, z których korzystają Twoi pracownicy. Zespół zabezpieczeń może również dodawać nowe zasady. Załóżmy na przykład, że chcesz zastosować pewne ustawienia do niektórych urządzeń, a inne dla innych urządzeń. Możesz to zrobić, dodając zasady, takie jak zasady ochrony następnej generacji lub zasady zapory.

Po dodaniu zasad zauważysz, że przypisano kolejność priorytetów. Możesz edytować kolejność priorytetów definiowania zasad, ale nie możesz zmienić kolejności priorytetów zasad domyślnych. Załóżmy na przykład, że dla Windows klienckich są trzy zasady ochrony następnej generacji. W tym przypadku zasady domyślne mają priorytet numer 3. Możesz zmienić kolejność zasad o numerach 1 i 2, ale domyślne zasady pozostaną na liście wartością 3. 

**Ważne, aby pamiętać o wielu zasadach, to to, że urządzenia będą otrzymywać tylko pierwsze zastosowane zasady.** Odwołując się do naszego wcześniejszego przykładu trzech zasad następnej generacji, załóżmy, że masz urządzenia, do których odnoszą się wszystkie trzy zasady. W takim przypadku te urządzenia otrzymają zasady numer 1, ale nie będą otrzymywać zasad o numerach 2 i 3. 

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="key-points-to-remember-about-policy-order"></a>Najważniejsze kwestie do zapamiętania o kolejności zasad

- Zasady mają przypisywany priorytet.

- Urządzenia otrzymują tylko pierwsze zastosowane zasady.

- Kolejność priorytetów zasad można zmienić.

- Zasady domyślne mają najniższy priorytet.

## <a name="next-steps"></a>Następne kroki

- [Wprowadzenie do korzystania z usługi Defender dla firm](mdb-get-started.md)

- [Zarządzanie urządzeniami](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)