---
title: Analizowanie danych w zestawie recenzji w programie Advanced eDiscovery
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
description: Informacje na temat narzędzi dostępnych do organizowania zestawów dokumentów podczas analizowania Advanced eDiscovery przypadku.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 829e6e6441403cf5a934e81a1a437f65d2de3db3
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62973989"
---
# <a name="analyze-data-in-a-review-set-in-advanced-ediscovery"></a>Analizowanie danych w zestawie recenzji w programie Advanced eDiscovery

Gdy liczba zebranych dokumentów jest duża, przeglądanie ich wszystkich może być trudne. Advanced eDiscovery udostępnia wiele narzędzi do analizowania dokumentów w celu zmniejszenia ilości dokumentów do przejrzenia bez utraty informacji oraz w celu spójnego organizowania dokumentów. Aby dowiedzieć się więcej o tych możliwościach, zobacz:

- [Wykrywanie niemal duplikatów](near-duplicate-detection-in-advanced-ediscovery.md)

- [Wątkowanie wiadomości e-mail](email-threading-in-advanced-ediscovery.md)

- [Motywy](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Uruchamianie analizy dla zestawu recenzji

Aby przeanalizować dane w zestawie recenzji:

1. Skonfiguruj ustawienia analizy dla Twojej sprawy. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Otwórz zestaw recenzji, który chcesz przeanalizować.

3. Kliknij **pozycję AnalyticsRun** >  **document & e-mail analytics**.

   ![Wybierz pozycję Uruchom dokument & e-mail z listy rozwijanej Analiza.](..\media\RunAnalytics1.png)

Możesz sprawdzić postęp analizy na karcie **Zadania** sprawy.

 Po zakończeniu analizy możesz wyświetlić raport z analiz, uruchomić w ramach zestawu wyników analizy zapytania (zobacz Zapytanie w ramach zestawu recenzji i zobacz Powiązane dokumenty danego dokumentu) (zobacz Przeglądanie danych w zestawie recenzji[).](reviewing-data-in-review-set.md)[](review-set-search.md)

## <a name="using-the-for-review-filter-query"></a>Używanie zapytania filtru Do przeglądu

Po uruchomieniu analizy dla zestawu recenzji możesz użyć automatycznie wygenerowanego zapytania filtru (nazywanego do *przeglądu), które* umożliwia filtrowanie recenzji w celu wykluczenia elementów nieistotnych, zduplikowanych lub nie uwzględniających elementów. Dzięki temu w zestawie recenzji będą dostępne tylko te elementy, które są reprezentacyjne, unikatowe i inkluzywne.

Aby zastosować zapytanie **filtru Do przeglądu** do zestawu recenzji, wybierz  listę rozwijaną Zapisane zapytania filtru, a następnie wybierz pozycję **\[Autogen] do recenzji**.

![Wybierz pozycję Do przeglądu z listy rozwijanej Zapisane zapytania filtru](..\media\ForReviewFilterQuery1.png)

Oto składnia zapytania filtru **Do** przeglądu:

`(((FileClass="Email") AND (InclusiveType="InclusiveMinus" OR InclusiveType="Inclusive")) OR ((FileClass="Attachment") AND (UniqueInEmailSet="true")) OR ((FileClass="Document") AND (MarkAsRepresentative="Unique")) OR (FileClass="Conversations"))`

Na poniższej liście opisano wynik zapytania filtru w kontekście zawartości wyświetlanej po zastosowaniu jej do zestawu recenzji.

- **E-mail**. Wyświetla elementy oznaczone jako **Inclusive lub** **InclusiveMinus**. Element inkluzywny to końcowa wiadomość w wątku wiadomości e-mail. Zawiera on całą poprzednią zawartość w wątku wiadomości e-mail. Zawiera ona jeden lub więcej załączników skojarzonych z określoną wiadomością w wątku wiadomości e-mail. Recenzent może używać wartości minus włącznie do określenia, które określone wiadomości w wątku wiadomości e-mail mają skojarzone załączniki.

- **Załączniki**. Odfiltrowuje zduplikowane załączniki w tym samym zestawie wiadomości e-mail. Wyświetlane są tylko unikatowe załączniki w wątku wiadomości e-mail.

- **Dokumenty i inne.** Odfiltrowuje zduplikowane dokumenty. Wyświetlane są tylko unikatowe dokumenty w zestawie recenzji.

- **Teams konwersacji**. Zostaną Teams wszystkie Yammer (i konwersacje Yammer) w zestawie recenzji.

Aby uzyskać więcej informacji na temat typów inkluzywnych i unikatowości dokumentów, zobacz Wątki [wiadomości e-mail w programie Advanced eDiscovery](email-threading-in-advanced-ediscovery.md).

> [!NOTE]
> Podczas publicznego podglądu nowego [](advanced-ediscovery-new-case-format.md) formatu sprawy w programie Advanced eDiscovery Yammer Teams zapytanie filtru  Do przeglądu nie zwracało konwersacji z użyciem zestawów recenzji (w przypadkach, w których jest używany format dużych liter) utworzonych przed 4 listopada 2021 r. Ten problem został rozwiązany. Oznacza to, że jeśli ponownie użyjemy zapytania do przeglądu w przypadku przypadku, gdy jest używany format dużych liter, może zostać wyświetlonych więcej elementów, które pasują do zapytania filtru, ponieważ wszystkie konwersacje z programu Teams lub Yammer są uwzględniane.

## <a name="analytics-report"></a>Raport analizy

Aby wyświetlić raport z analiz dla zestawu recenzji:

1. Otwórz zestaw recenzji.

2. Kliknij **pozycję AnalyticsShow** >  **reports (Raporty funkcji AnalyticsShow**).

Raport **Analizy** zawiera siedem składników z analizy:

- **Populacja docelowa:** Liczba wiadomości e-mail, załączników i luźnych dokumentów znalezionych w zestawie recenzji.

- **Dokumenty (bez załączników):** Liczba luźnych dokumentów przestawnych, unikatowe niemal duplikaty tabeli przestawnej lub dokładna duplikat innego dokumentu.

- **Wiadomości e-mail:** Liczba wiadomości e-mail oznaczonych jako takie, które są włącznie, włącznie z znakami minus lub żadną z powyższych.

- **Załączniki:** Liczba załączników wiadomości e-mail, które są unikatowe lub duplikaty innych załączników wiadomości e-mail w zestawie recenzji.

- **Numer dokumentów według typu pliku:** Liczba plików oznaczonych rozszerzeniem pliku.

- **Dokumenty według źródła:** Podsumowanie zawartości według jego pierwotnego źródła danych.

- **Dokumenty zagregowane według procesów:** Podsumowanie zawartości według procesów zestawu recenzji. 
