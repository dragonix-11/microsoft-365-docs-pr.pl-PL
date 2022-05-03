---
title: Omówienie kolejności zasad w Microsoft Defender dla Firm
description: Dowiedz się więcej o kolejności priorytetów dzięki zasadom cyberbezpieczeństwa, aby chronić urządzenia firmowe za pomocą usługi Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 4003585c82c835c21218fd1200b3468140c8370b
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174091"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>Omówienie kolejności zasad w Microsoft Defender dla Firm

## <a name="policy-order-in-microsoft-defender-for-business"></a>Kolejność zasad w Microsoft Defender dla Firm

Microsoft Defender dla Firm zawiera wstępnie zdefiniowane zasady, aby zapewnić ochronę urządzeń używanych przez pracowników. Twój zespół ds. zabezpieczeń może również dodawać nowe zasady. Załóżmy na przykład, że chcesz zastosować określone ustawienia do niektórych urządzeń i inne ustawienia do innych urządzeń. Można to zrobić, dodając zasady, takie jak zasady ochrony następnej generacji lub zasady zapory.

Po dodaniu zasad zauważysz, że przypisano kolejność priorytetów. Możesz edytować kolejność priorytetów zdefiniowanych zasad, ale nie możesz zmienić kolejności priorytetów dla zasad domyślnych. Załóżmy na przykład, że w przypadku urządzeń klienckich Windows masz trzy zasady ochrony nowej generacji. W takim przypadku domyślne zasady mają priorytet numer 3. Możesz zmienić kolejność zasad o numerach 1 i 2, ale domyślne zasady pozostaną na liście numerem 3. 

**Ważne jest, aby pamiętać o wielu zasadach, ponieważ urządzenia otrzymają tylko pierwsze zastosowane zasady.** Odwołując się do naszego wcześniejszego przykładu trzech zasad nowej generacji, załóżmy, że masz urządzenia objęte wszystkimi trzema zasadami. W takim przypadku te urządzenia otrzymają numer zasad 1, ale nie otrzymają zasad o numerach 2 i 3. 

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="key-points-to-remember-about-policy-order"></a>Najważniejsze kwestie, które należy pamiętać o kolejności zasad

- Zasady mają przypisaną kolejność priorytetów.
- Urządzenia otrzymują tylko pierwsze zastosowane zasady.
- Możesz zmienić kolejność priorytetów zasad.
- Zasady domyślne mają najniższy porządek priorytetu.

## <a name="next-steps"></a>Następne kroki

- [Wprowadzenie przy użyciu usługi Defender dla Firm](mdb-get-started.md)
- [Zarządzanie urządzeniami](mdb-manage-devices.md)
- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)