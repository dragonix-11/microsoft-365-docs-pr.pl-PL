---
title: Analiza regresji procesora
description: Opis wyników regresji i metryk użycia procesora
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 935781e929c159918f8a0aec3b4a551ab974480f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985285"
---
# <a name="intelligent-cpu-regression-analysis"></a>Inteligentna analiza regresji procesora

Użycie procesora może wskazywać, czy na aplikację wpływa aktualizacja systemu operacyjnego. 

Baza testowa dla oprogramowania Microsoft 365 udostępnia deweloperom oprogramowania szczegółowe informacje o regresji wydajności procesora, która występuje, gdy ich aplikacja działa na różnych wersjach nadchodzącej aktualizacji systemu Windows (OS). 

Te regresje procesora umożliwiają deweloperom wykrywanie i rozwiązywanie problemów z aplikacją (i potencjalnych błędów) przed publicznie wdrożoną aktualizacją systemu operacyjnego, przez co użytkownik końcowy nie będzie już mieć problemów.


### <a name="how-cpu-regression-analysis-works"></a>Jak działa analiza regresji procesora ###

Jako użytkownik bazy testowej możesz przekazać pliki binarne aplikacji (w jednym pliku .zip) wraz ze skojarzonymi skryptami testowym i wybrać wersję systemu operacyjnego Windows, dla której chcesz przetestować aplikację w portalu Test Base na platformie Azure. 

Usługa Test Base następnie uruchamia skrypty testowe i wykonuje analizę **regresji procesora**. 

Usługa sprawdza, czy użycie procesora w aplikacji w wersji wstępnej aktualizacji dla docelowego systemu operacyjnego jest zgodne z wykorzystaniem procesora dla wydanej wersji systemu operacyjnego. 

Użycie procesora nie jest porównaniem 100% podobnym do tego, ponieważ procesy uruchomione w dwóch wersjach systemu operacyjnego mogą, ale nie muszą być dokładnym dopasowaniem ze względu na inne wersje systemu operacyjnego. Jednak analiza wykonana przez bazę testową może pokazać, czy na wykorzystanie procesora w Twojej aplikacji ma wpływ nadchodzące aktualizacje systemu operacyjnego, a dokładnie na to, które procesy wystąpiły w porównaniu z poprzednimi testami.

W poniższej migawki istnieją dwa wersje systemu operacyjnego, w stosunku do których są porównywane użycia procesora w tej samej aplikacji. 
-   Na karcie Wykorzystanie procesora jest pokazana górna i dolna granica użycia dla obu wersji odpowiednio dla 90- i 10-ego percentylu. 
-   Na wykresach są wyświetlane serie czasowe użycia procesora wraz ze średnim wykorzystaniem. 

Klienci mogą teraz używać tej funkcji do określania, czy aktualizacje systemu operacyjnego mają wpływ na wykorzystanie procesora w ich aplikacjach, a dokładnie na które procesy zostały pominięte w poprzednich wykonaniach.


![Analiza regresji procesora.](Media/cpu-regression-analysis.jpg)

### <a name="relevant-process-identification"></a>Identyfikacja odpowiedniego procesu ###

W tym miejscu omówiono sposób identyfikowania procesów wyekskutowanych w aplikacji. 

Analizowanie regresji wydajności wymaga śledzenia różnych rodzajów liczników wydajności dla każdego procesu uruchomionego na maszynie wirtualnej podczas uruchamiania testowego. 

Taka analiza rejestruje wiele zmiennych dla wielu procesów dla danej aplikacji. Nie wszystkie procesy są skojarzone z uruchamianiem lub aplikacją. Aby zmierzyć się z tym wyzwaniem, stosuje się algorytm klasyfikacji wspólnych informacji przy użyciu prawdopodobieństwa i teorii informacji, aby ustalić, które procesy są najbardziej istotne dla danej aplikacji. 

Aplikację można traktować jako jeden z typów osobnej zmiennej losowej, podczas gdy proces jest traktowany jako inny rodzaj osobnej zmiennej losowej. Skojarzenie dwóch zmiennych losowych jest mierzone przy użyciu prawdopodobieństwa warunkowego do oceny istotności. 

Procesy są następnie wyświetlane w kolejności ich istotności dla poszczególnych aplikacji. Można również dodać do ulubionych podzbiór procesów, które mogą być domyślnie monitorowane, wraz z odpowiednimi procesami analizy regresji procesora. Po wykryciu regresji możesz pobrać zestaw narzędzi analizatora Windows oraz przeanalizować przyczyny regresji wydajności procesora. 

Analizator Windows wydajności pobiera dane wejściowe dziennika śledzenia zdarzeń (ETL), a te pliki etl są dostępne do pobrania w plikach dziennika do pobrania w celu testowania w portalu. Jeśli chcesz dowiedzieć się więcej o debugowaniu wydajności procesora, zobacz dokumentację Windows Analizatora wydajności.

