---
title: Decyzja oparta na wynikach z zbierania elektronicznych materiałów dowodowych (Premium)
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
description: Dowiedz się, jak karta Zdecyduj w usłudze eDiscovery (Premium) udostępnia dane, które mogą pomóc w określeniu prawidłowego rozmiaru zestawu przeglądów plików sprawy.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6c8759db2445b8d98c47cc1103deda058d2f3508
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64932425"
---
# <a name="decisions-based-on-relevance-results-in-ediscovery-premium"></a>Decyzje oparte na istotności skutkują zbierania elektronicznych materiałów dowodowych (Premium)
  
W module Istotność w usłudze eDiscovery (Premium) karta Zdecyduj zawiera dodatkowe informacje dotyczące wyświetlania i używania statystyk dotyczących podejmowania decyzji w celu określenia rozmiaru zestawu przeglądów plików sprawy.
  
## <a name="using-the-decide-tab"></a>Korzystanie z karty Zdecyduj

![Decyzja o istotności.](../media/f32fed89-f3b5-404a-90c7-ea25d2eb58a9.png)
  
Ta karta zawiera następujące składniki:
  
- **Problem**: W tym miejscu możesz wybrać interesujący cię problem z listy.

- **Współczynnik recenzowania i wycofywania**: porównanie przeglądu zbierania elektronicznych materiałów dowodowych (Premium) zgodnie z wynikami istotności. Punkt odcięcia na wykresie reprezentuje procent plików do przejrzenia, zamapowany na wynik istotności. Jest to używane w fazie testu istotności i jako próg eksportu na potrzeby uboju. Domyślnym punktem odcięcia dla liczby plików do przejrzenia jest punkt, w którym równowaga między odwołaniem a dokładnością jest optymalna. Rzeczywisty punkt odcięcia powinien być określany przez użytkownika w zależności od celów, kompromisu kosztowego (%review) i ryzyka (%recall). Za pomocą suwaka można dostosować punkt odcięcia i zobaczyć wpływ na wykres i parametry, podczas dostosowywania procentu odpowiednich plików do pobrania i przed zweryfikowaniem decyzji.

- **Parametry**: Przejrzyj, Przywołuj, Następne odpowiednie i Łączne parametry kosztu to skumulowane statystyki obliczeniowe dotyczące zestawu przeglądów w odniesieniu do kolekcji dla całego przypadku. Definicje tych parametrów są następujące:

  - **Przegląd**: Procent plików do przejrzenia na podstawie tego odcięcia.

  - **Przypomnij sobie**: Procent odpowiednich plików w zestawie przeglądów.

  - **Następne istotne**: Koszt przeglądania i identyfikowania innego odpowiedniego pliku, który nie znajduje się obecnie w zestawie przeglądów.

  - **Całkowity koszt**: koszt przeglądania tego procentu plików sprawy. Ustawienia parametrów kosztu mogą być ustawiane przez menedżera spraw.

  - **Rozkład według wskaźnika istotności**: Pliki na ciemnoszarym ekranie po lewej stronie znajdują się poniżej wyniku odcięcia. Porada narzędzia wyświetla wynik istotności i powiązany procent plików w pliku przeglądu ustawionym w odniesieniu do łącznej liczby plików.

Rozwinięte okienko **Szczegóły** zawiera więcej szczegółów. Pliki na rysunkach kolekcji nie zawierają pustych ani mglistych plików. Dane dotyczące plików rodzinnych reprezentują pliki, które nie są ładowane w obszarze Istotność, ale nadal są liczone jako część rodziny.
