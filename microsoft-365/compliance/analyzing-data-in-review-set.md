---
title: Analizowanie danych w zestawie przeglądów w usłudze eDiscovery (Premium)
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
description: Dowiedz się więcej o narzędziach dostępnych do organizowania zestawów dokumentów podczas analizowania przypadku Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 822c21c05b865bdf1208f7679eaff9ea35b10a9e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634836"
---
# <a name="analyze-data-in-a-review-set-in-ediscovery-premium"></a>Analizowanie danych w zestawie przeglądów w usłudze eDiscovery (Premium)

Gdy liczba zebranych dokumentów jest duża, przeglądanie ich wszystkich może być trudne. Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) udostępnia szereg narzędzi do analizowania dokumentów w celu zmniejszenia ilości dokumentów, które mają być przeglądane bez utraty informacji, oraz ułatwia organizowanie dokumentów w spójny sposób. Aby dowiedzieć się więcej o tych możliwościach, zobacz:

- [Wykrywanie niepełnych duplikatów](near-duplicate-detection-in-advanced-ediscovery.md)

- [Wątki wiadomości e-mail](email-threading-in-advanced-ediscovery.md)

- [Motywy](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Uruchamianie analizy dla zestawu przeglądów

Aby analizować dane w zestawie przeglądów:

1. Skonfiguruj ustawienia analizy dla danego przypadku. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Otwórz zestaw przeglądów, który chcesz przeanalizować.

3. Kliknij pozycję **Analiza** > **Uruchom dokument & analizy poczty e-mail**.

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

- **Rozmowy w usłudze Teams**. Wyświetlane są wszystkie konwersacje usługi Teams (i Yammer) w zestawie przeglądów.

Aby uzyskać więcej informacji na temat typów inkluzywnych i unikatowości dokumentów, zobacz [Wątek wiadomości e-mail w usłudze eDiscovery (Premium)](email-threading-in-advanced-ediscovery.md).

> [!NOTE]
> W publicznej wersji zapoznawczej [nowego formatu przypadku](advanced-ediscovery-new-case-format.md) w usłudze eDiscovery (Premium) zapytanie filtru **For Review** nie zwróciło konwersacji usługi Teams ani Yammer dla zestawów przeglądów (w przypadkach, w których jest używany format dużych przypadków) utworzonych przed 4 listopada 2021 r. Ten problem został rozwiązany. Oznacza to, że jeśli ponownie zastosujesz zapytanie **For Review** do zestawu przeglądów w przypadku, w którym jest używany format dużych przypadków, może zostać wyświetlonych więcej elementów zgodnych z zapytaniem filtru, ponieważ uwzględniono wszystkie konwersacje usługi Teams lub Yammer.

## <a name="analytics-report"></a>Raport analizy

Aby wyświetlić raport analizy dla zestawu przeglądów:

1. Otwórz zestaw przeglądów.

2. Kliknij pozycję **Analiza** > **Pokaż raporty**.

Raport **analizy** zawiera siedem składników analizy:

- **Populacja docelowa:** Liczba wiadomości e-mail, załączników i luźnych dokumentów znalezionych w zestawie przeglądów.

- **Dokumenty (z wyłączeniem załączników):** Liczba luźnych dokumentów, które są tabelami przestawnymi, unikatowych w pobliżu duplikatów tabeli przestawnej lub dokładnego duplikatu innego dokumentu.

- **Wiadomości e-mail:** Liczba wiadomości e-mail oznaczonych jako inkluzywna, inkluzywna kopia, włącznie minus lub żadna z powyższych.

- **Załączniki:** Liczba załączników wiadomości e-mail, które są unikatowe lub duplikaty innego załącznika wiadomości e-mail w zestawie przeglądów.

- **Numeruj dokumenty według typu pliku:** Liczba plików identyfikowanych przez rozszerzenie pliku.

- **Dokumenty według źródła:** Podsumowanie zawartości według oryginalnego źródła danych.

- **Dokumenty zagregowane według procesu:** Podsumowanie zawartości według procesów zestawu przeglądów. 
