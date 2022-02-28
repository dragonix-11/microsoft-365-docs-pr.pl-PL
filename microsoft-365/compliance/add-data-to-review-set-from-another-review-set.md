---
title: Dodawanie danych z jednego zestawu recenzji do innego zestawu recenzji
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
description: Dowiedz się, jak wybierać dokumenty z jednego zestawu recenzji i pracować z nimi indywidualnie w innym zestawie w Advanced eDiscovery przypadku.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 4f230c5a9a4a202fc417ad4e16ca5bee5f7e433b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985648"
---
# <a name="add-data-to-a-review-set-from-another-review-set"></a>Dodawanie danych do zestawu recenzji z innego zestawu recenzji

W niektórych przypadkach może być konieczne wybranie dokumentów z jednego zestawu recenzji i praca z nimi indywidualnie w innym zestawie recenzji. Jest to szczególnie przydatne, jeśli zawartość zestawu recenzji była już analizowana i podzbiór danych ma zostać uruchomiony.

Postępuj zgodnie z przepływem pracy w tym artykule, aby dodać zawartość z jednego zestawu recenzji do innego.

## <a name="create-a-review-set"></a>Tworzenie zestawu recenzji

Przed rozpoczęciem musisz utworzyć zestaw recenzji, aby dodać dane.  Na karcie Zestawy recenzji sprawy można dodać  nowy zestaw recenzji. Aby uzyskać więcej informacji, [zobacz Tworzenie zestawu recenzji](managing-review-sets.md#create-a-review-set).

## <a name="step-1-identify-content-to-add-to-another-review-set"></a>Krok 1. Identyfikowanie zawartości do dodania do innego zestawu recenzji

Zawartość jednego zestawu recenzji można dodać do innego, wybierając określone dokumenty w źródłowym zestawie recenzji lub wybierając wszystkie elementy zwrócone przez zapytanie zestawu recenzji. Jeśli dodajesz zaznaczone elementy, zaznacz je, wybierz **pozycję** Akcja, a następnie wybierz pozycję **Dodaj do innego zestawu recenzji**.

![Dodaj do innego zestawu recenzji w menu Akcja.](../media/64f2a4d4-eba3-4ab3-a3ba-d519feea3142.png)

## <a name="step-2-specify-options-for-adding-to-another-review-set"></a>Krok 2. Określanie opcji dodawania do innego zestawu recenzji

Na stronie **wysuwanych opcji Dodaj do innego zestawu recenzji** wybierz zestaw recenzji, do którego chcesz dodać elementy. Wybierz, czy chcesz dodać **Wszystkie wyniki wyszukiwania,** czy **Zaznaczone elementy**.  **Dodatkowe informacje** zawierają opcje dołączania wszystkich metadanych z elementów oraz tego, czy mają być dołączane tagi (przez  zaznaczenie pola wyboru Etykiety) w zestawie recenzji źródłowej podczas dodawana dokumentów do nowego zestawu recenzji.  

![Opcje dodawania danych do innego zestawu recenzji.](../media/6440ee44-68fd-44d7-b43a-3a477345525c.png)

Po kliknięciu **przycisku OK** zostanie utworzone nowe zadanie (o nazwie Dodawanie danych do innego zestawu recenzji **) w** celu dodania zawartości do innego zestawu recenzji. Możesz przejść do karty **Zadania** i monitorować postęp tego zadania. Aby uzyskać więcej informacji, zobacz [Zarządzanie zadaniami](managing-jobs-ediscovery20.md).
