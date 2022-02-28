---
title: Decyzja oparta na wynikach w programie Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: aed65bcd-0a4f-43e9-b5e5-b98cc376bdf8
description: Dowiedz się, jak karta Advanced eDiscovery udostępnia dane, które mogą pomóc w ustaleniu poprawnego rozmiaru zestawu reenzentów plików sprawy.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 32682690c6febac247d67e3b78f56d1f71b9a2fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988362"
---
# <a name="decisions-based-on-relevance-results-in-advanced-ediscovery"></a>Decyzje oparte na wynikach z istotności w Advanced eDiscovery
  
W module Istotność w programie Advanced eDiscovery na karcie Podejmowanie decyzji przedstawiono dodatkowe informacje dotyczące wyświetlania i używania statystyk dotyczących decyzji w celu określenia rozmiaru zestawu przeglądanych plików sprawy.
  
## <a name="using-the-decide-tab"></a>Korzystanie z karty Zdecyduj

![Decyzja o istotności.](../media/f32fed89-f3b5-404a-90c7-ea25d2eb58a9.png)
  
Ta karta zawiera następujące składniki:
  
- **Problem**: W tym miejscu możesz wybrać z listy problem, który cię interesuje.

- **Współczynnik odwołania recenzji**: Porównanie wyników Advanced eDiscovery na podstawie wyników istotności. Punkt odcięty na wykresie reprezentuje procent plików do przejrzenia zamapowany na wynik Istotności. Jest on stosowany w fazie Test istotności i jako próg eksportu dla wyników. Domyślnym punktem odciętym dla liczby plików do przejrzenia jest punkt, w którym jest optymalna równowaga między odwołaniami i dokładnością. Rzeczywisty punkt odcięty powinien zostać określony przez użytkownika w zależności od celów oraz kompromisu kosztowego (%review) i ryzyka (%odwołania). Za pomocą suwaka możesz dostosować punkt odcięty i zobaczyć wpływ tej zmiany na wykres i parametry, dostosować procent pobierania odpowiednich plików i przed podjęciem decyzji.

- **Parametry**: Przeglądanie, Odwoływanie, Następne parametry dotyczące kosztów całkowitych i Następne są skumulowaną statystyką obliczoną dla zbioru recenzji dla całej sprawy. Definicje tych parametrów są następujące:

  - **Recenzja**: Procent plików do przejrzenia na podstawie tego odciętych plików.

  - **Odwołaj**: Procent odpowiednich plików w zestawie recenzji.

  - **Kolejne istotne**: Koszt przeglądania i identyfikowania innego odpowiedniego pliku, który nie znajduje się obecnie w zestawie recenzji.

  - **Łączny koszt**: koszt przeglądania tej wartości procentowej plików sprawy. Ustawienia parametru koszt mogą zostać określone przez menedżera sprawy.

  - **Rozkład według istotności**: Pliki na ciemnoszarym ekranie po lewej stronie znajdują się poniżej wyniku odciętych. Etykietka narzędzia wyświetla wynik istotności i powiązaną wartość procentową plików w zestawie recenzji względem łącznych plików.

W rozwiniętym **okienku** Szczegóły są wyświetlane więcej szczegółów. Pliki w rysunkach kolekcji nie zawierają pustych ani niepustych plików. Ilustracje dotyczące plików rodzinnych reprezentują pliki, które nie zostały załadowane w celu oceny istotności, ale nadal są liczone jako część rodziny.
