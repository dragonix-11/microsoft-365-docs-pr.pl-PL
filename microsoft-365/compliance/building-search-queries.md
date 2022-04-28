---
title: Tworzenie zapytań wyszukiwania w usłudze eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-mar2020
description: Użyj słów kluczowych i warunków, aby zawęzić zakres wyszukiwania podczas wyszukiwania danych przy użyciu eDiscovery (Premium) w Microsoft 365.
ms.openlocfilehash: afb033a014528b7e79a6ce192896f4b2b3eef054
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096143"
---
# <a name="build-search-queries-for-collections-in-ediscovery-premium"></a>Tworzenie zapytań wyszukiwania dla kolekcji zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Podczas konfigurowania zapytania wyszukiwania podczas tworzenia [kolekcji](collections-overview.md) w przypadku zbierania elektronicznych materiałów dowodowych (Premium) można użyć słów kluczowych, aby znaleźć określoną zawartość i warunki, aby zawęzić zakres wyszukiwania w celu zwrócenia elementów, które są najbardziej istotne dla badania prawnego.

![Użyj słów kluczowych i warunków, aby zawęzić wyniki wyszukiwania.](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Wyszukiwania słów kluczowych

Wpisz zapytanie słowa kluczowego w polu **Słowa kluczowe** w zapytaniu wyszukiwania. Można określić słowa kluczowe, właściwości wiadomości e-mail, takie jak daty wysłania i odebrania, lub właściwości dokumentu, takie jak nazwy plików lub data ostatniej zmiany dokumentu. Możesz użyć bardziej złożonych zapytań, które używają operatora logicznego, takiego jak **AND**, **OR**, **NOT** i **NEAR**. Możesz również wyszukać poufne informacje (takie jak numery ubezpieczenia społecznego) w dokumentach w SharePoint i OneDrive (nie w wiadomościach e-mail) lub wyszukać dokumenty, które zostały udostępnione zewnętrznie. Jeśli pole **Słowa kluczowe** pozostanie puste, cała zawartość znajdująca się w określonych lokalizacjach zawartości znajduje się w wynikach wyszukiwania.

## <a name="keyword-list"></a>Lista słów kluczowych

Alternatywnie możesz zaznaczyć pole wyboru **Pokaż listę słów kluczowych** i w każdym wierszu wpisać słowo kluczowe lub frazę kluczową. Słowa kluczowe w każdym wierszu są połączone przez operator logiczny (który jest reprezentowany jako *c:s* w składni zapytania wyszukiwania), który jest podobny do operatora **OR** w utworzonym zapytaniu wyszukiwania. Oznacza to, że elementy zawierające dowolne słowo kluczowe w dowolnym wierszu znajdują się w wynikach wyszukiwania. Możesz dodać do 180 wierszy na liście słów kluczowych w zapytaniach wyszukiwania zbierania elektronicznych materiałów dowodowych (Premium).

![Użyj listy słów kluczowych, aby uzyskać statystyki dla każdego słowa kluczowego w zapytaniu.](../media/KeywordListSearch.png)

Dlaczego warto używać listy słów kluczowych? Możesz uzyskać statystyki pokazujące, ile elementów pasuje do każdego słowa kluczowego na liście słów kluczowych. Może to pomóc w szybkim zidentyfikowaniu słów kluczowych, które są najbardziej (i najmniej) skuteczne. Możesz również użyć frazy kluczowej (otoczonej nawiasami) w wierszu na liście słów kluczowych. Aby uzyskać więcej informacji na temat statystyk wyszukiwania, zobacz [Statystyki kolekcji i raporty](collection-statistics-reports.md)

## <a name="conditions"></a>Warunki

Możesz dodać warunki wyszukiwania, aby zawęzić zakres wyszukiwania i zwrócić bardziej uściślany zestaw wyników. Każdy warunek dodaje klauzulę do zapytania wyszukiwania, które jest tworzone i uruchamiane po rozpoczęciu wyszukiwania. Warunek jest logicznie połączony z zapytaniem słowa kluczowego określonym w polu słowa kluczowego przez operator logiczny (który jest reprezentowany jako *c:c* w składni zapytania wyszukiwania), który jest podobny do operatora **AND** . Oznacza to, że elementy muszą spełniać zarówno zapytanie słowa kluczowego, jak i co najmniej jeden warunk, który ma zostać uwzględniony w wynikach wyszukiwania. W ten sposób warunki pomagają zawęzić wyniki. Aby uzyskać listę i opis warunków, których można użyć w zapytaniu wyszukiwania, zobacz sekcję "Warunki wyszukiwania" w [temacie Zapytania słów kluczowych i warunki wyszukiwania](keyword-queries-and-search-conditions.md#search-conditions).
