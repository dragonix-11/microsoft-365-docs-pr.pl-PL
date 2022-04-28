---
title: Sprawdź, czy zapytanie wyszukiwania nie zawiera błędów
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
search.appverid:
- MOE150
- MET150
ms.assetid: 88898874-e262-4c5c-b6d2-4e697497fc74
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak wykrywać błędy i literówki w zapytaniu słowa kluczowego na potrzeby wyszukiwania zbierania elektronicznych materiałów dowodowych przed uruchomieniem wyszukiwania.
ms.openlocfilehash: 858db046cf78482e8540425a3f826f2ce28e78cd
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091792"
---
# <a name="check-your-search-query-for-errors"></a>Sprawdź, czy zapytanie wyszukiwania nie zawiera błędów

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
Poniżej przedstawiono listę nieobsługiwanych znaków, które sprawdzamy w zapytaniach wyszukiwania dotyczących wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Standard). Nieobsługiwane znaki są często ukryte i zwykle powodują błąd wyszukiwania lub zwracają niezamierzone wyniki.
  
- **Inteligentne cudzysłowy** — inteligentne znaki pojedynczego i podwójnego cudzysłowu (nazywane również cudzysłowami kręcone) nie są obsługiwane. W zapytaniu wyszukiwania można używać tylko prostych cudzysłowów. 

- **Znaki niedrukowalne i sterujące** — znaki niedrukowalne i sterujące nie reprezentują symbolu pisanego, takiego jak znak alfanumeryczny. Przykłady znaków niedrukowalnych i kontrolek obejmują znaki formatujące tekst lub oddzielne wiersze tekstu. 

- **Znaki od lewej do prawej i od prawej do lewej** — są to znaki sterujące używane do wskazywania kierunku tekstu dla języków od lewej do prawej (takich jak angielski i hiszpański) oraz języków od prawej do lewej (takich jak arabski i hebrajski).

- **Operatory logiczne o małych literach** — jeśli używasz operatora logicznego, takiego jak **AND**, **OR** i **NOT** w zapytaniu wyszukiwania, musi to być wielkie litery. Podczas sprawdzania zapytania pod kątem literówek składnia zapytania często wskazuje, że jest używany operator logiczny, nawet jeśli mogą być używane operatory o małych literach; na przykład  `(WordA or WordB) and (WordC or WordD)`.

## <a name="what-happens-if-a-query-has-an-unsupported-character"></a>Co się stanie, jeśli zapytanie ma nieobsługiwany znak?

Jeśli w zapytaniu znaleziono nieobsługiwanych znaków, zostanie wyświetlony komunikat ostrzegawczy z informacją o nieobsługiwanych znakach i sugeruje alternatywę. Następnie możesz zachować oryginalne zapytanie lub zastąpić je sugerowanym poprawionym zapytaniem.

Oto przykład komunikatu ostrzegawczego, który jest wyświetlany po kliknięciu przycisku **Sprawdź zapytanie pod kątem literówek** dla zapytania wyszukiwania na poprzednim zrzucie ekranu. Zwróć uwagę na oryginalne zapytanie, w których użyto inteligentnych cudzysłowów i operatorów logicznych o małych literach.
  
![Zostanie wyświetlony komunikat ostrzegawczy z sugerowaną poprawką zapytania.](../media/23214b30-8e52-412c-bd80-63fb1b3ed52d.png)
  
## <a name="how-to-prevent-unsupported-characters-in-your-search-queries"></a>Jak zapobiegać nieobsługiwanym znakom w zapytaniach wyszukiwania

Nieobsługiwanych znaków są zwykle dodawane do zapytania podczas kopiowania zapytania lub części zapytania z innych aplikacji (takich jak Microsoft Word lub Microsoft Excel) i wklej je w polu słowa kluczowego na stronie zapytania wyszukiwania zawartości. Najlepszym sposobem zapobiegania nieobsługiwanym znakom jest wpisanie zapytania w polu słowa kluczowego. Możesz też skopiować zapytanie z programu Word lub Excel, a następnie wkleić je w edytorze zwykłego tekstu, takim jak Microsoft Notatnik. Zapisz plik tekstowy i wybierz pozycję **ANSI** na liście rozwijanej **Kodowanie** . Spowoduje to usunięcie formatowania i nieobsługiwanych znaków. Następnie możesz skopiować i wkleić zapytanie z pliku tekstowego do pola zapytania słowa kluczowego.
