---
title: Tworzenie zapytań wyszukiwania w aplikacji Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Użyj słów kluczowych i warunków, aby zawęzić zakres wyszukiwania podczas wyszukiwania danych przy użyciu Advanced eDiscovery w Microsoft 365.
ms.openlocfilehash: 8ad708b9733dd7d96f1025f116a31a92d757afd2
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027087"
---
# <a name="build-search-queries-for-collections-in-advanced-ediscovery"></a>Tworzenie zapytań wyszukiwania dla kolekcji w aplikacji Advanced eDiscovery

Konfigurując zapytanie wyszukiwania podczas tworzenia kolekcji [](collections-overview.md) w ramach sprawy Advanced eDiscovery, można użyć słów kluczowych w celu znalezienia określonej zawartości i warunków w celu zawężenia zakresu wyszukiwania w celu zwrócenia elementów, które są najbardziej istotne dla prowadzonego śledztwa prawnego.

![Użyj słów kluczowych i warunków, aby zawęzić wyniki wyszukiwania.](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Wyszukiwania słów kluczowych

Wpisz słowo kluczowe zapytanie w polu **Słowa** kluczowe w zapytaniu wyszukiwania. Możesz określić słowa kluczowe, właściwości wiadomości e-mail, takie jak daty wysłania i odebrania, lub właściwości dokumentu, takie jak nazwy plików lub data ostatniej zmiany dokumentu. Można używać bardziej złożonych zapytań, które korzystają z operatorów logicznych, takich jak **ORAZ**, **LUB**, **NIE** i **NEAR**. Możesz również wyszukiwać informacje poufne (na przykład numery PESEL) w dokumentach w programach SharePoint i OneDrive (nie w wiadomościach e-mail) lub wyszukiwać dokumenty udostępnione zewnętrznie. Jeśli pozostawisz pole **Słowa kluczowe** puste, cała zawartość w określonych lokalizacjach zawartości zostanie podana w wynikach wyszukiwania.

## <a name="keyword-list"></a>Lista słów kluczowych

Ewentualnie możesz zaznaczyć pole wyboru **Pokaż** listę słów kluczowych i wpisać słowo kluczowe lub frazę słowa kluczowego w każdym wierszu. Słowa kluczowe w każdym wierszu są połączone operatorem logicznym (który w składni zapytania wyszukiwania jest reprezentowany jako *c:s* ) i jest podobny do funkcji operatora **LUB** w utworzonym zapytaniu wyszukiwania. Oznacza to, że elementy zawierające dowolne słowo kluczowe w dowolnym wierszu znajdują się w wynikach wyszukiwania. Możesz dodać maksymalnie 180 wierszy na liście słów kluczowych w Advanced eDiscovery wyszukiwania.

![Użyj listy słów kluczowych, aby uzyskać statystykę na poszczególnych słowach kluczowych w zapytaniu.](../media/KeywordListSearch.png)

Dlaczego warto używać listy słów kluczowych? Możesz uzyskać statystykę, która pokazuje, ile elementów pasuje do poszczególnych słów kluczowych na liście słów kluczowych. Dzięki temu można szybko zidentyfikować słowa kluczowe, które są najbardziej (i najmniej) skuteczne. Możesz również użyć frazy słowa kluczowego (otoczonej nawiasami) w wierszu na liście słów kluczowych. Aby uzyskać więcej informacji na temat statystyk wyszukiwania, zobacz [Statystyka kolekcji i raporty.](collection-statistics-reports.md)

## <a name="conditions"></a>Warunki

Możesz dodać warunki wyszukiwania, aby zawęzić zakres wyszukiwania i zwrócić bardziej dopracowany zestaw wyników. Każdy warunek powoduje dodanie klauzuli do zapytania wyszukiwania, które jest tworzone i uruchamiane po rozpoczęciu wyszukiwania. Warunek jest logicznie połączony z zapytaniem słowa kluczowego określonym w polu słowa kluczowego przez operator logiczny (który w składni zapytania wyszukiwania jest reprezentowany jako *c:c* ), który jest podobny do funkcji operatora **AND** . Oznacza to, że elementy muszą spełniać zarówno zapytanie słów kluczowych, jak i jeden lub więcej warunków, aby zostały uwzględnione w wynikach wyszukiwania. W ten sposób warunki ułatwiają zawężenie wyników. Aby uzyskać listę i opis warunków, których można użyć w zapytaniu wyszukiwania, zobacz sekcję "Wyszukiwanie warunków" w tece Zapytania słów kluczowych [i warunki wyszukiwania](keyword-queries-and-search-conditions.md#search-conditions).
