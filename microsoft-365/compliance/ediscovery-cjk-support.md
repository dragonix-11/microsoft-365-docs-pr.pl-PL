---
title: Obsługa CJK/Double Byte dla Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się Advanced eDiscovery jak Microsoft 365 językach chińskich, japońskich i koreańskich (CJK) z zestawem znaków dwu bajtowych.
ms.openlocfilehash: 4c1871eb49754ba93d762989e3cff9c53950d2c6
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027081"
---
# <a name="cjk-language-support-for-advanced-ediscovery"></a>Obsługa języków CJK dla Advanced eDiscovery

Advanced eDiscovery obsługuje języki zestawu znaków dwu bajtowych (są to między innymi chiński uproszczony, chiński tradycyjny, japoński i koreański, które są zbiorczo nazywane językami *CJK*) dla następujących zaawansowanych scenariuszy w zestawie recenzji:

- Zapytania [dotyczące danych w zestawie recenzji](review-set-search.md).

- Oznaczanie [dokumentów w zestawie recenzji](tagging-documents.md).

- Podczas [analizowania danych case in a review set](analyzing-data-in-review-set.md) by using near duplicate detection, email threading, and themes analytics.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Jak utworzyć wyszukiwanie w celu zbierania elementów, które zawierają znaki CJK?**

Znaków CJK można używać do wyszukiwania słów [kluczowych, zapytań](building-search-queries.md#keyword-searches) dotyczących słów kluczowych i warunków wyszukiwania podczas wyszukiwania zawartości w Advanced eDiscovery. [](keyword-queries-and-search-conditions.md) Wyszukiwanie znaków CJK jest również obsługiwane podczas wyszukiwania zawartości w core eDiscovery i przeszukiwaniu zawartości.

Zapewniamy obsługę języka CJK dla [](keyword-queries-and-search-conditions.md#search-operators) wszystkich operatorów wyszukiwania i warunków [wyszukiwania, w](keyword-queries-and-search-conditions.md#search-conditions) tym operatorów logicznych **ORAZ**, **LUB**, **NIE** i **NEAR**.

Jeśli masz pewność, że lokalizacje lub elementy zawartości zawierają znaki CJK, ale wyszukiwania nie zwracają żadnych wyników, kliknij ikonę języka/regionu kwerendy ![Query language-country/region icon in Content Search.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) i wybierz odpowiednią wartość kodu kultury kraju/języka dla wyszukiwania. Domyślny język/region jest neutralny.

**Czy można wyszukiwać wiele języków jednocześnie?**

Zależy to od scenariusza wyszukiwania.

- Podczas wykonywania [zapytań dotyczących danych w zestawie recenzji](review-set-search.md) w programie Advanced eDiscovery można wyszukiwać wiele języków.

- Podczas tworzenia [wyszukiwania w celu zbierania danych](create-draft-collection.md) utwórz osobne kolekcje dla każdego języka, do których jest skierowana opcja. Jeśli na przykład wyszukujesz dokument zawierający zarówno chiński, jak i koreański, wybierz pozycję Chiński dla pierwszej kolekcji, a następnie wybierz koreański dla drugiej kolekcji.

**Nie widzę ikony języka/regionu zapytania, aby wybrać język zapytań w zestawie recenzji. Jak określić język zapytania w wyszukiwaniu zestawu recenzji?**

W przypadku zapytań zestawu recenzji nie trzeba określać języka dokumentu. Advanced eDiscovery automatycznie wykrywa języki dokumentów podczas dodawania zawartości do zestawu recenzji. Pozwala to zoptymalizować wyniki kwerendy w zestawie recenzji.

**Czy w metadanych pliku [widzę wykryte języki](view-documents-in-review-set.md#file-metadata)?**

Nie, w metadanych plików nie widać wykrytych języków.

**Czy można filtrować według języków dokumentów w zestawie recenzji**?

Nie, w zestawie recenzji nie można filtrować, sortować ani wyszukiwać według języków dokumentów.

**Czy ta wersja CJK do przeglądu zestawu scenariuszy będzie mieć wpływ na którekolwiek z istniejących zestawów wyszukiwania i rerecenzentów?**

Nie, żadne z istniejących zestawów wyszukiwań i recenzji nie zmieni się. Nie musisz ponownie indeksować istniejących danych, a wyniki wyszukiwania tekstu w języku angielskim będą takie same.

**Jak zmienić język wyświetlania na chiński, japoński lub koreański?**

Aby uzyskać informacje na temat zmieniania języka wyświetlania i strefy czasowej, zobacz Jak skonfigurować ustawienia języka [i regionu dla Office 365](/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>Znane problemy

- OCR nie obsługuje znaków CJK z plików obrazów

- Pliki wiadomości e-mail (na przykład *.eml i *.msg[](view-documents-in-review-set.md#annotate-view)) w widoku adnotacji nie są obsługiwane w językach CJK.

- Wyróżnianie hitów wyszukiwania w [widoku tekstu](view-documents-in-review-set.md#text-view) nie jest obsługiwane w językach CJK.

- Moduł [Istotność używany](using-relevance.md) do analizowania danych nie obsługuje języków CJK.

- [W językach](managing-holds.md#manage-non-custodial-holds) CJK nie są obsługiwane blokady oparte na zapytaniach.