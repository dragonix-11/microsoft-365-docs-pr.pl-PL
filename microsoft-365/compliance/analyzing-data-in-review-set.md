---
title: Analizowanie danych w zestawie przeglądów w usłudze eDiscovery (Premium)
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
description: Dowiedz się więcej o narzędziach dostępnych do organizowania zestawów dokumentów podczas analizowania przypadku zbierania elektronicznych materiałów dowodowych (Premium) w usłudze Microsoft Purview.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: c12b71d4bc2ddbf39df4e9414689cafeb4f4f785
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935703"
---
# <a name="analyze-data-in-a-review-set-in-ediscovery-premium"></a>Analizowanie danych w zestawie przeglądów w usłudze eDiscovery (Premium)

Gdy liczba zebranych dokumentów jest duża, przeglądanie ich wszystkich może być trudne. Usługa Microsoft Purview eDiscovery (Premium) udostępnia szereg narzędzi do analizowania dokumentów w celu zmniejszenia ilości dokumentów, które mają być przeglądane bez utraty informacji, oraz ułatwia organizowanie dokumentów w spójny sposób. Aby dowiedzieć się więcej o tych możliwościach, zobacz:

- [Wykrywanie niepełnych duplikatów](near-duplicate-detection-in-advanced-ediscovery.md)

- [Wątki wiadomości e-mail](email-threading-in-advanced-ediscovery.md)

- [Motywy](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Uruchamianie analizy dla zestawu przeglądów

Aby analizować dane w zestawie przeglądów:

1. Skonfiguruj ustawienia analizy dla danego przypadku. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Otwórz zestaw przeglądów, który chcesz przeanalizować.

3. Kliknij pozycję **AnalizaNieuchomienie dokumentu & analizy poczty e-mail**. > 

   ![Wybierz pozycję Uruchom dokument & analizy poczty e-mail z listy rozwijanej Analiza](..\media\RunAnalytics1.png)

Postęp analizy można sprawdzić na karcie **Zadania** sprawy.

 Po zakończeniu analizy możesz wyświetlić raport analizy, uruchomić zapytania w ramach zestawu przeglądów na danych wyjściowych analizy (zobacz [Zapytanie w zestawie przeglądów](review-set-search.md) i wyświetlić powiązane dokumenty danego dokumentu (zobacz [Przeglądanie danych w zestawie przeglądów](reviewing-data-in-review-set.md).

## <a name="using-the-for-review-filter-query"></a>Korzystanie z zapytania filtru For Review

Po uruchomieniu analizy dla zestawu przeglądów można użyć automatycznie wygenerowanego zapytania filtru (o nazwie *For Review*), które filtruje recenzję, aby wykluczyć elementy nieistotne, zduplikowane lub niewłącznie. Spowoduje to, że w zestawie przeglądów zostaną wyświetlone tylko reprezentatywne, unikatowe i inkluzywne elementy.

Aby zastosować zapytanie filtru **For Review** do zestawu przeglądów, wybierz listę rozwijaną **Zapisane zapytania filtru** , a następnie wybierz pozycję **\[AutoGen] Do przeglądu**.

![Wybierz pozycję Przejrzyj z listy rozwijanej Zapisane zapytania filtru](..\media\ForReviewFilterQuery1.png)

Oto składnia zapytania filtru **For Review** :

`(((FileClass="Email") AND (InclusiveType="InclusiveMinus" OR InclusiveType="Inclusive")) OR ((FileClass="Attachment") AND (UniqueInEmailSet="true")) OR ((FileClass="Document") AND (MarkAsRepresentative="Unique")) OR (FileClass="Conversations"))`

Na poniższej liście opisano wynik zapytania filtru pod względem zawartości wyświetlanej po zastosowaniu jej do zestawu przeglądów.

- **Wiadomość e-mail**. Wyświetla elementy oznaczone jako **Inkluzywne** lub **InclusiveMinus**. Element inkluzywny to ostatnia wiadomość w wątku wiadomości e-mail. Zawiera całą poprzednią zawartość w wątku wiadomości e-mail. Inkluzywny minus zawiera co najmniej jeden załącznik skojarzony z określoną wiadomością w wątku wiadomości e-mail. Recenzent może użyć wartości minus inkluzywnej, aby określić, które konkretne wiadomości w wątku wiadomości e-mail mają skojarzone załączniki.

- **Załączniki**. Filtruje zduplikowane załączniki w tym samym zestawie poczty e-mail. Wyświetlane są tylko załączniki unikatowe w wątku wiadomości e-mail.

- **Dokumenty i inne**. Filtruje zduplikowane dokumenty. Wyświetlane są tylko dokumenty unikatowe w zestawie przeglądów.

- **Teams konwersacje**. Wyświetlane są wszystkie konwersacje Teams (i Yammer) w zestawie przeglądów.

Aby uzyskać więcej informacji na temat typów inkluzywnych i unikatowości dokumentów, zobacz [Wątek wiadomości e-mail w funkcji zbierania elektronicznych materiałów dowodowych (Premium)](email-threading-in-advanced-ediscovery.md).

> [!NOTE]
> W publicznej wersji zapoznawczej [nowego formatu przypadku](advanced-ediscovery-new-case-format.md) w funkcji zbierania elektronicznych materiałów dowodowych (Premium) zapytanie filtru **For Review** nie zwróciło Teams ani Yammer konwersacji dla zestawów przeglądów (w przypadkach, w których jest używany format dużych przypadków) utworzonych przed 4 listopada 2021 r. Ten problem został rozwiązany. Oznacza to, że jeśli ponownie zastosujesz zapytanie **For Review** do zestawu przeglądów w przypadku, który używa formatu dużego przypadku, może zostać wyświetlonych więcej elementów zgodnych z zapytaniem filtru, ponieważ uwzględniono wszystkie konwersacje Teams lub Yammer.

## <a name="analytics-report"></a>Raport analizy

Aby wyświetlić raport analizy dla zestawu przeglądów:

1. Otwórz zestaw przeglądów.

2. Kliknij pozycję **AnalizaJak** >  **raporty**.

Raport **analizy** zawiera siedem składników analizy:

- **Populacja docelowa:** Liczba wiadomości e-mail, załączników i luźnych dokumentów znalezionych w zestawie przeglądów.

- **Dokumenty (z wyłączeniem załączników):** Liczba luźnych dokumentów, które są tabelami przestawnymi, unikatowych w pobliżu duplikatów tabeli przestawnej lub dokładnego duplikatu innego dokumentu.

- **Wiadomości e-mail:** Liczba wiadomości e-mail oznaczonych jako inkluzywna, inkluzywna kopia, włącznie minus lub żadna z powyższych.

- **Załączniki:** Liczba załączników wiadomości e-mail, które są unikatowe lub duplikaty innego załącznika wiadomości e-mail w zestawie przeglądów.

- **Numeruj dokumenty według typu pliku:** Liczba plików identyfikowanych przez rozszerzenie pliku.

- **Dokumenty według źródła:** Podsumowanie zawartości według oryginalnego źródła danych.

- **Dokumenty zagregowane według procesu:** Podsumowanie zawartości według procesów zestawu przeglądów. 
