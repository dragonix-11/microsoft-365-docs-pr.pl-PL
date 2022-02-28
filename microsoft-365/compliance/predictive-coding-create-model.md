---
title: Tworzenie modelu predykcyjnego kodowania w programie Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Dowiedz się, jak utworzyć model predykcyjnego kodowania w programie Advanced eDiscovery. Jest to pierwszy krok w zakresie korzystania z funkcji uczenia maszynowego w programie Advanced eDiscovery w celu zidentyfikowania istotnej i nieistnieowej zawartości w zestawie recenzji.
ms.openlocfilehash: 4366c5779aaca6973f5a2c0cc526086d0742d069
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985637"
---
# <a name="create-a-predictive-coding-model-preview"></a>Tworzenie modelu predykcyjnego kodowania (podgląd)

Pierwszym krokiem w zakresie korzystania z funkcji uczenia maszynowego w zakresie predykcyjnego Advanced eDiscovery jest utworzenie modelu predykcyjnego kodowania. Po utworzeniu modelu można go przeszkolić w celu zidentyfikowania istotnej i nieistnieowej zawartości w zestawie recenzji.

Aby zapoznać się z przepływem pracy predykcyjnego kodowania, zobacz [Informacje na temat predykcyjnego kodowania w programie Advanced eDiscovery](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-create-a-model"></a>Przed utworzeniem modelu

- Aby utworzyć model predykcyjnego kodowania, w zestawie recenzji musi być co najmniej 2000 elementów.

- Pamiętaj o zatwierdzeniu wszystkich kolekcji do zestawu recenzji przed utworzeniem modelu. Elementy dodane do zestawu recenzji po utworzeniu modelu nie będą przetwarzane i nie przypisywany jest wynik prognozy wygenerowany przez model.

- Żaden element w zestawie recenzji, który nie zawiera tekstu, nie zostanie przetworzony przez model ani nie zostanie przypisany wynik prognozowania. Elementy z tekstem będą zawarte w zestawie kontrolek lub zestawie szkoleniowym.

## <a name="create-a-model"></a>Tworzenie modelu

1. W Centrum zgodności platformy Microsoft 365 otwórz sprawę Advanced eDiscovery, a następnie wybierz **kartę Zestawy** recenzji.

2. Otwórz zestaw recenzji, a następnie kliknij pozycję **AnalizaSzybki kodowanie predykcyjne (wersja zapoznawcza)**. > 

   ![Kliknij menu rozwijane Analiza w recenzji, aby przejść do strony Predykcyjne kodowanie.](..\media\ManagePredictiveCoding.png)

3. Na stronie **Predykcyjne modele kodowania (podgląd)** kliknij pozycję **Nowy model**.

4. Na stronie wysuwu wpisz nazwę modelu i opcjonalny opis.

5. Opcjonalnie możesz skonfigurować ustawienia zaawansowane (klikając pozycję Opcje zaawansowane  na wysuwanych stronie) powiązane z poziomem ufności i marginesem błędu. Te ustawienia wpływają na liczbę elementów zawartych w zestawie kontrolek. Zestaw *kontrolek* jest używany w trakcie procesu szkoleniowego do oceny wyników prognozy przypisywanych przez model elementom z etykietami, które wykonuje się podczas zaokrągleń szkolenia. Jeśli organizacja ma wskazówki dotyczące poziomu ufności i marginesu błędu podczas przeglądania dokumentu, określ je w odpowiednich polach. W przeciwnym razie użyj ustawień domyślnych.

6. Kliknij **przycisk Zapisz** , aby utworzyć model.

   Przygotowanie modelu przez system zajmie kilka minut. Gdy wszystko będzie gotowe, możesz przeprowadzić pierwszą rundę szkolenia.

## <a name="what-happens-after-you-create-a-model"></a>Co się dzieje po utworzeniu modelu

Podczas tworzenia i przygotowywania modelu w tle występują następujące zdarzenia:

- System oblicza liczbę elementów dla zestawu kontrolek. Ten rozmiar zależy od liczby elementów w zestawie recenzji oraz ustawień poziomu ufności i marginesu błędu. Elementy zestawu kontrolek są losowo wybierane i wyznaczane jako elementy zestawu kontrolek. System zawiera 10 elementów z zestawu kontrolek w pierwszej turze szkolenia.

- System losowo wybiera 40 elementów z zestawu recenzji do dołączona do zestawu szkoleniowego dla pierwszej rundy szkolenia. Dlatego pierwsza runda szkolenia obejmuje 50 elementów do oznaczania etykietami: 40 elementów z zestawu szkoleniowego i 10 elementów z zestawu kontrolek.

## <a name="next-steps"></a>Następne kroki

Po utworzeniu modelu do zestawu recenzji następnym krokiem jest wykonanie szkoleń, aby "nauczyć" model w celu zidentyfikowania zawartości istotnej dla Twojego badania. Aby uzyskać więcej informacji, zobacz [Szkolenie modelu predykcyjnego kodowania](predictive-coding-train-model.md).
