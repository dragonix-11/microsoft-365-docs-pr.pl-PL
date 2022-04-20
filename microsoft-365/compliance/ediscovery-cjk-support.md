---
title: Obsługa CJK/Double Byte dla zbierania elektronicznych materiałów dowodowych (Premium)
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
description: Dowiedz się, jak usługa Microsoft Purview eDiscovery (Premium) w Microsoft 365 obsługuje języki chiński, japoński i koreański (CJK), które używają zestawu znaków dwubajtowych.
ms.openlocfilehash: 70081341499f348f1bb8e226b4d3b5e9c0bab031
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934802"
---
# <a name="cjk-language-support-for-ediscovery-premium"></a>Obsługa języka CJK dla eDiscovery (Premium)

Usługa Microsoft Purview eDiscovery (Premium) obsługuje języki zestawu znaków dwubajtowych (obejmują one uproszczone języki chiński, chiński tradycyjny, japoński i koreański, które są łącznie znane jako języki *CJK*) dla następujących zaawansowanych scenariuszy w zestawie przeglądów:

- Podczas [wykonywania zapytań dotyczących danych w zestawie przeglądów](review-set-search.md).

- Podczas [tagowania dokumentów w zestawie przeglądów](tagging-documents.md).

- Podczas [analizowania danych przypadków w zestawie przeglądów](analyzing-data-in-review-set.md) przy użyciu wykrywania zbliżonego do duplikatów, wątków wiadomości e-mail i analizy motywów.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Jak mogę utworzyć wyszukiwanie w celu zbierania elementów zawierających znaki CJK?**

Znaków CJK można używać do [wyszukiwania słów kluczowych](building-search-queries.md#keyword-searches), [zapytań słów kluczowych i warunków wyszukiwania](keyword-queries-and-search-conditions.md) podczas wyszukiwania zawartości w środowisku zbierania elektronicznych materiałów dowodowych (Premium). Wyszukiwanie znaków CJK jest również obsługiwane podczas wyszukiwania zawartości w usługach Microsoft Purview eDiscovery (Standard) i Content Search.

Zapewniamy obsługę zestawu CJK dla wszystkich [operatorów wyszukiwania](keyword-queries-and-search-conditions.md#search-operators) i [warunków wyszukiwania](keyword-queries-and-search-conditions.md#search-conditions), w tym operatorów logicznych **ORAZ**, **OR**, **NOT** i **NEAR**.

Jeśli masz pewność, że lokalizacje zawartości lub elementy zawierają znaki CJK, ale wyszukiwania nie zwracają żadnych wyników, kliknij ikonę język-kraj/region zapytania ![Ikona języka/regionu zapytania w wyszukiwaniu zawartości.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) i wybierz odpowiednią wartość kodu kultury język-kraj dla wyszukiwania. Domyślny język/region jest neutralny.

**Czy mogę wyszukiwać wiele języków jednocześnie?**

Zależy to od scenariusza wyszukiwania.

- Podczas [wykonywania zapytań dotyczących danych w zestawie przeglądów](review-set-search.md) zbierania elektronicznych materiałów dowodowych (Premium) można wyszukiwać wiele języków.

- Podczas [tworzenia wyszukiwania w celu zbierania danych](create-draft-collection.md) utwórz oddzielne kolekcje dla każdego docelowego języka. Jeśli na przykład wyszukujesz dokument zawierający zarówno język chiński, jak i koreański, wybierz pozycję Chiński dla pierwszej kolekcji i wybierz pozycję Koreański dla drugiej kolekcji.

**Nie widzę ikony język-kraj/region zapytania, aby wybrać język zapytań w zestawie przeglądów. Jak określić język zapytań w wyszukiwaniu zestawu przeglądów?**

W przypadku zapytań zestawu przeglądów nie trzeba określać języka dokumentu. Funkcja zbierania elektronicznych materiałów dowodowych (Premium) automatycznie wykrywa języki dokumentów podczas dodawania zawartości do zestawu przeglądów. Pomaga to zoptymalizować wyniki zapytania w zestawie przeglądów.

**Czy w [metadanych plików](view-documents-in-review-set.md#file-metadata) są widoczne wykryte języki?**

Nie, w metadanych plików nie widać wykrytych języków.

**Czy można filtrować według języków dokumentów w zestawie przeglądów**?

Nie, nie można filtrować, sortować ani wyszukiwać według języków dokumentów w zestawie przeglądów.

**Czy ta wersja zestawu CJK dla scenariuszy zestawu przeglądów wpłynie na dowolne z moich istniejących wyszukiwań i zestawów przeglądów?**

Nie, żadne z istniejących wyszukiwań i zestawów przeglądów nie ulegnie zmianie. Nie musisz ponownie eksksplorować istniejących danych, a wyniki wyszukiwania tekstu w języku angielskim będą takie same.

**Jak mogę zmienić język wyświetlania na chiński, japoński lub koreański?**

Aby uzyskać informacje na temat zmiany języka wyświetlania i strefy czasowej, zobacz [How to set language and region settings for Office 365 (Jak ustawić ustawienia języka i regionu dla Office 365](/office365/troubleshoot/access-management/set-language-and-region)).

## <a name="known-issues"></a>Znane problemy

- Funkcja OCR nie obsługuje znaków CJK z plików obrazów

- Pliki poczty e-mail (takie jak *.eml i *.msg) w [widoku adnotacji](view-documents-in-review-set.md#annotate-view) nie są obsługiwane w językach CJK.

- Wyróżnianie trafień wyszukiwania w [widoku tekstowym](view-documents-in-review-set.md#text-view) nie jest obsługiwane w językach CJK.

- [Moduł Istotność](using-relevance.md) używany do analizowania danych nie obsługuje języków CJK.

- [Blokady oparte na zapytaniach](managing-holds.md#manage-non-custodial-holds) nie są obsługiwane w językach CJK.