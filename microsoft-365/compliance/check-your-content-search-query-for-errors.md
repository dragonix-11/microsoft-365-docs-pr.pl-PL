---
title: Sprawdzanie błędów w zapytaniu wyszukiwania
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
search.appverid:
- MOE150
- MET150
ms.assetid: 88898874-e262-4c5c-b6d2-4e697497fc74
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak wykrywać błędy i literówki w wyszukiwaniu zbierania elektronicznych materiałów dowodowych za pomocą słów kluczowych przed uruchomieniem wyszukiwania.
ms.openlocfilehash: c820b72ea54e338d4f2fde475568bf2b1c22ba3b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984012"
---
# <a name="check-your-search-query-for-errors"></a>Sprawdzanie błędów w zapytaniu wyszukiwania
  
Oto lista nieobsługiwanych znaków sprawdzanych w zapytaniach wyszukiwania dotyczących wyszukiwania zawartości i podstawowego zbierania elektronicznych materiałów dowodowych. Nieobsługiwane znaki są często ukryte i zwykle powodują błąd wyszukiwania lub zwracają niezamierzone wyniki.
  
- **Cudzysłowy** inteligentne — pojedyncze i podwójne cudzysłowy inteligentne (nazywane również cudzysłowami klamrymi) nie są obsługiwane. W zapytaniu wyszukiwania można używać tylko cudzysłowów prostych. 

- **Znaki niedrukowalne i kontrolne** — znaki niedrukowalne i kontrolne nie reprezentują pisemnego symbolu, takiego jak znak alfanumerycznych. Przykładami znaków niedrukowalnych i kontrolnych są znaki formatowane tekst lub oddzielne wiersze tekstu. 

- Znaczniki **od lewej** do prawej i od prawej do lewej — te znaczniki to znaki kontrolne służące do wskazywania kierunku tekstu w językach z lewej do prawej (takich jak angielski i hiszpański) i językach od prawej do lewej (takich jak arabski i hebrajski).

- **Małe operatory logiczne** — jeśli w zapytaniu wyszukiwania jest użycie operatora logicznych, takiego jak **AND(ORAZ**), **OR** (LUB) i **NOT** (NIE), należy użyć wielkich liter. Podczas sprawdzania literówek w kwerendzie składnia zapytania często wskazuje, że jest używany operator logiczny, mimo że mogą być używane operatory małych liter. na przykład  `(WordA or WordB) and (WordC or WordD)`.

## <a name="what-happens-if-a-query-has-an-unsupported-character"></a>Co się stanie, jeśli zapytanie ma nieobsługiwany znak?

Jeśli w zapytaniu zostaną znalezione nieobsługiwane znaki, zostanie wyświetlony komunikat ostrzegawczy z ostrzeżeniem informujący, że znaleziono nieobsługiwane znaki i sugeruje alternatywę. Następnie możesz zachować oryginalne zapytanie lub zamienić je na sugerowane poprawione zapytanie.

Oto przykład komunikatu ostrzegawczego wyświetlanego po kliknięciu przycisku Sprawdź literówki zapytania  wyszukiwania na poprzednim zrzucie ekranu. Zwróć uwagę, że oryginalne zapytanie używało cudzysłowów inteligentnych i małych liter operatorów logicznych.
  
![Zostanie wyświetlony komunikat ostrzegawczy z sugerowaną poprawek dla kwerendy.](../media/23214b30-8e52-412c-bd80-63fb1b3ed52d.png)
  
## <a name="how-to-prevent-unsupported-characters-in-your-search-queries"></a>Jak zapobiec nieobsługiwanym znakom w kwerendach wyszukiwania

Nieobsługiwane znaki są zazwyczaj dodawane do zapytania podczas kopiowania zapytania lub jego części z innych aplikacji (takich jak Microsoft Word lub Microsoft Excel) i wklejania ich w polu słowa kluczowego na stronie zapytania wyszukiwania zawartości. Najlepszym sposobem uniknięcia nieobsługiwanych znaków jest po prostu wpisanie zapytania w polu słowa kluczowego. Możesz również skopiować zapytanie z programu Word lub Excel, a następnie wkleić je do edytora tekstów, takiego jak microsoft Notatnik. Zapisz plik tekstowy i wybierz pozycję **ANSI** **z listy** rozwijanej Kodowanie. Spowoduje to usunięcie wszelkiego formatowania i nieobsługiwanych znaków. Następnie możesz skopiować zapytanie z pliku tekstowego i wkleić je w polu zapytania słowa kluczowego.
