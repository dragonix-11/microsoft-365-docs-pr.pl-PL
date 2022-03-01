---
title: Konfigurowanie tagów inteligentnych w aplikacji Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Tagi inteligentne umożliwiają stosowanie funkcji uczenia maszynowego podczas przeglądania zawartości w Advanced eDiscovery przypadku. Za pomocą grup tagów inteligentnych można wyświetlać wyniki modeli wykrywania maszynowego uczenia, takich jak model prawniowo-klienta.
ms.openlocfilehash: 80c946da943e4880dbd82ea6b34d238b80030b4c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014684"
---
# <a name="set-up-smart-tags-in-advanced-ediscovery"></a>Konfigurowanie tagów inteligentnych w aplikacji Advanced eDiscovery

Funkcje uczenia maszynowego (ML) w programie Advanced eDiscovery ułatwiają wydajniejsze podejmowanie decyzji podczas przeglądania dokumentów spraw w zestawie recenzji. Tagi inteligentne to sposób na zapewnianie możliwości ML miejsca, w którym są rejestrowane decyzje: podczas tagowania dokumentów podczas przeglądu. Po utworzeniu grupy tagów inteligentnych decyzje wynikające z modelu ML skojarzonego z grupą tagów inteligentnych są wyświetlane razem z tagami w grupie tagów. Dzięki temu podczas rerecenzowania określonych ML zostaną one podane w wierszach.

## <a name="how-to-set-up-a-smart-tag-group"></a>Jak skonfigurować grupę tagów inteligentnych

1. W zestawie recenzji kliknij pozycję **Zarządzaj zestawem recenzji** , a następnie kliknij pozycję **Zarządzaj tagami**.

2. Kliknij **pozycję Dodaj grupę tagów** , a następnie wybierz **pozycję Dodaj grupę tagów inteligentnych**.

3. Wybierz ML, który chcesz skojarzyć z grupą tagów.
    
   Powoduje to utworzenie grupy tagów i *N* tagów podrzędnych, gdzie *N* oznacza liczbę możliwych wyników modelu. Na przykład model [wykrywania uprawnień klienta obsługi klienta ma](attorney-privilege-detection.md) dwa możliwe wyniki: 

   - **Dodatni** — oznacza dokumenty zawierające treści o uprawnieniach klienta.
   
   - **Ujemne** — oznacza dokumenty, które nie zawierają treści o uprawnieniach klienta.
    
    W przypadku wybrania tego modelu zostanie utworzona grupa tagów z dwoma tagami podrzędnmi (jeden tag podrzędny o nazwie **Dodatni, a** drugi o nazwie Ujemny **) dla** zestawu recenzji. W tym przykładzie każdy tag podrzędny odpowiada jednemu z możliwych wyników modelu wykrywania uprawnień obsługi klienta i obsługi klienta.

4. Opcjonalnie możesz zmienić nazwę grupy tagów i tagów podrzędnych. Można na przykład zmienić nazwę tagu **Dodatni** na **"Privileged" (** Uprawnienie), a tag **negatywowy** na **Nieumiejętny**.

## <a name="how-to-use-smart-tags"></a>Jak używać tagów inteligentnych

Podczas przeglądania dokumentu wyniki modelu są wyświetlane obok odpowiedniego tagu podrzędnego. Na przykład jeśli masz grupę tagów inteligentnych do wykrywania uprawnień klienta-obsługi klienta i przeglądasz dokument, który ma potencjalnie uprzywilejowany, przyczyna takiego wnioski jest wyświetlana obok odpowiedniego znacznika. Należy pamiętać, że tag nie jest automatycznie stosowany do dokumentu. Recenzent podejmuje decyzję o oknie o oknie otagowanie dokumentu.
