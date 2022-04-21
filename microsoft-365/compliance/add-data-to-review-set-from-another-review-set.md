---
title: Dodawanie danych z jednego zestawu przeglądów do innego
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Dowiedz się, jak wybierać dokumenty z jednego zestawu przeglądów i pracować z nimi indywidualnie w innym zestawie w przypadku zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium).
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: b87c9278b5009f6873414f8fc53d434c458c62ad
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995849"
---
# <a name="add-data-to-a-review-set-from-another-review-set"></a>Dodawanie danych do zestawu przeglądów z innego zestawu przeglądów

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W niektórych przypadkach może być konieczne wybranie dokumentów z jednego zestawu przeglądów i praca z nimi indywidualnie w innym zestawie przeglądów. Jest to szczególnie przydatne, jeśli zawartość została ubita w zestawie przeglądów i chcesz uruchomić analizę na podzbiorze danych.

Postępuj zgodnie z przepływem pracy w tym artykule, aby dodać zawartość z jednego zestawu przeglądów do innego.

## <a name="create-a-review-set"></a>Tworzenie zestawu przeglądów

Przed rozpoczęciem należy utworzyć zestaw przeglądów, do którego będą dodawane dane.  Nowy zestaw przeglądów można dodać na karcie **Zestawy przeglądów** sprawy. Aby uzyskać więcej informacji, zobacz [Tworzenie zestawu przeglądów](managing-review-sets.md#create-a-review-set).

## <a name="step-1-identify-content-to-add-to-another-review-set"></a>Krok 1. Identyfikowanie zawartości do dodania do innego zestawu przeglądów

Możesz dodać zawartość z jednego zestawu przeglądów do innego, wybierając określone dokumenty w zestawie przeglądu źródłowego lub wybierając wszystkie elementy zwrócone przez zapytanie zestawu przeglądów. Jeśli dodajesz wybrane elementy, wybierz elementy, wybierz pozycję **Akcja**, a następnie wybierz pozycję **Dodaj do innego zestawu przeglądów**.

![Dodaj do innego zestawu przeglądów w menu Akcja.](../media/64f2a4d4-eba3-4ab3-a3ba-d519feea3142.png)

## <a name="step-2-specify-options-for-adding-to-another-review-set"></a>Krok 2. Określanie opcji dodawania do innego zestawu przeglądów

Na stronie wysuwanej **Dodaj do innego zestawu przeglądów** wybierz zestaw przeglądów, do którym chcesz dodać elementy. Określ, czy chcesz dodać **wszystkie wyniki wyszukiwania** , czy **wybrane elementy**.  **Dodatkowe informacje** zawierają opcje dołączania wszystkich metadanych z elementów oraz tego, czy mają zostać uwzględnione tagi (zaznaczając pole wyboru **Etykiety** ) z zestawu przeglądu źródłowego, gdy dokumenty zostaną dodane do nowego zestawu przeglądów.  

![Opcje dodawania danych do innego zestawu przeglądów.](../media/6440ee44-68fd-44d7-b43a-3a477345525c.png)

Po kliknięciu przycisku **OK** zostanie utworzone nowe zadanie (o nazwie **Dodawanie danych do innego zestawu przeglądów**) w celu dodania zawartości do innego zestawu przeglądów. Możesz przejść do karty **Zadania** i monitorować postęp tego zadania. Aby uzyskać więcej informacji, zobacz [Zarządzanie zadaniami](managing-jobs-ediscovery20.md).
