---
title: Konfigurowanie tagów inteligentnych w usłudze eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ROBOTS: NOINDEX, NOFOLLOW
description: Tagi inteligentne umożliwiają stosowanie możliwości uczenia maszynowego podczas przeglądania zawartości w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Użyj grup tagów inteligentnych, aby wyświetlić wyniki modeli wykrywania uczenia maszynowego, takich jak model uprawnień adwokackiego klienta.
ms.openlocfilehash: 30d2d6f30f09fe8fb6772a4fb46c6895b174991f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629084"
---
# <a name="set-up-smart-tags-in-ediscovery-premium"></a>Konfigurowanie tagów inteligentnych w usłudze eDiscovery (Premium)

Możliwości uczenia maszynowego (ML) w Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) mogą pomóc w usprawnieniu procesu podejmowania decyzji podczas przeglądania dokumentów przypadków w zestawie przeglądów. Tagi inteligentne to sposób na zapewnienie możliwości uczenia maszynowego do miejsca, w którym są rejestrowane decyzje: podczas tagowania dokumentów podczas przeglądu. Podczas tworzenia grupy tagów inteligentnych decyzje będące wynikiem modelu uczenia maszynowego skojarzonego z grupą tagów inteligentnych są wyświetlane w wierszu z tagami w grupie tagów. Pomaga to wyświetlić informacje o wynikach uczenia maszynowego w wierszu podczas przeglądania określonych dokumentów.

## <a name="how-to-set-up-a-smart-tag-group"></a>Jak skonfigurować grupę tagów inteligentnych

1. W zestawie przeglądów kliknij pozycję **Zarządzaj zestawem przeglądów** , a następnie kliknij pozycję **Zarządzaj tagami**.

2. Kliknij **pozycję Dodaj grupę tagów** , a następnie wybierz pozycję **Dodaj grupę tagów inteligentnych**.

3. Wybierz model uczenia maszynowego, który chcesz skojarzyć z grupą tagów.
    
   Spowoduje to utworzenie grupy tagów i *tagów* podrzędnych N, gdzie *N* jest liczbą możliwych danych wyjściowych modelu. Na przykład [model wykrywania uprawnień adwokackiego klienta](attorney-privilege-detection.md) ma dwa możliwe dane wyjściowe: 

   - **Pozytywne** — służy do tagowania dokumentów zawierających uprzywilejowaną zawartość adwokacka klienta.
   
   - **Negatywna** — służy do tagowania dokumentów, które nie zawierają uprzywilejowanej zawartości adwokackiej klienta.
    
    Jeśli wybierzesz ten model, zostanie utworzona grupa tagów z dwoma tagami podrzędnymi (jeden tag podrzędny o nazwie **Positive** , a drugi o nazwie **Negative**) dla zestawu przeglądów. W tym przykładzie każdy tag podrzędny odpowiada jednemu z możliwych danych wyjściowych z modelu wykrywania uprawnień adwokackiego klienta.

4. Opcjonalnie możesz zmienić nazwę grupy tagów i tagów podrzędnych. Można na przykład zmienić nazwę tagu **Pozytywna** na **Uprzywilejowana** , a wartość **Tag ujemny** na **Nieusłuszona**.

## <a name="how-to-use-smart-tags"></a>Jak używać tagów inteligentnych

Podczas przeglądania dokumentu wyniki modelu są wyświetlane obok odpowiedniego tagu podrzędnego. Jeśli na przykład masz grupę tagów inteligentnych do wykrywania uprawnień adwokata klienta i przejrzysz dokument, który jest potencjalnie uprzywilejowany, przyczyna tego wniosku jest wyświetlana obok odpowiedniego tagu. Należy pamiętać, że tag nie jest automatycznie stosowany do dokumentu. Recenzent podejmuje decyzję o tym, jak otagować dokument.
