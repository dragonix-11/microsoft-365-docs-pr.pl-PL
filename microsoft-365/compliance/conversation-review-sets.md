---
title: Przeglądanie konwersacji w Advanced eDiscovery
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
description: Dowiedz się więcej o funkcji konwersacji w Advanced eDiscovery (nazywanej wątkiem konwersacji), aby odtworzyć, przeglądać i eksportować konwersacje na czacie w Microsoft Teams i Yammer grupach.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 7bd13bdb01298d0cf1f37671f044a3405a2de0b6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033751"
---
# <a name="conversation-threading-in-advanced-ediscovery"></a>Wątkowanie konwersacji w Advanced eDiscovery

Wiadomości błyskawiczne to wygodny sposób zadawania pytań, dzielenia się pomysłami i szybkiego komunikowania się z dużą publicznością. Ponieważ platformy do obsługi wiadomości błyskawicznych, takie jak grupy Microsoft Teams i Yammer, stają się podstawowym elementem współpracy w przedsiębiorstwach, organizacje muszą ocenić, w jaki sposób ich przepływ pracy zbierania elektronicznych materiałów dowodowych uwzględnia te nowe formy komunikacji i współpracy.

Funkcja konwersacji w programie Advanced eDiscovery została zaprojektowana tak, aby ułatwić identyfikowanie zawartości kontekstowej i tworzenie oddzielnych widoków konwersacji. Ta funkcja umożliwia wydajne i szybkie przeglądanie ukończonych konwersacji za pomocą wiadomości błyskawicznych (nazywanych również konwersacjami w wątkach *)* generowanych na platformach, takich jak Microsoft Teams.

Dzięki funkcji konwersacji możesz korzystać z wbudowanych funkcji, aby odtworzyć, przeglądać i eksportować konwersacje z wątkami. Użyj Advanced eDiscovery konwersacji, aby:

- Zachowywanie unikatowych metadanych na poziomie wiadomości we wszystkich wiadomościach w konwersacji.

- Zbieraj wiadomości kontekstowe wokół wyników wyszukiwania.

- Przeglądanie, adnotacje i redagowanie konwersacji z wątkami.

- Eksportowanie poszczególnych wiadomości lub konwersacji z wątkami

## <a name="terminology"></a>Terminologia

Oto kilka definicji, które ułatwiają rozpoczęcie korzystania z konwersacji.

- **Wiadomości:** Reprezentuje najmniejszą jednostkę konwersacji. Wiadomości mogą mieć różne rozmiary, strukturę i metadane.

- **Konwersacja:** Reprezentuje grupowanie jednej lub większej liczby wiadomości. W różnych aplikacjach konwersacje mogą być reprezentowane na różne sposoby. W niektórych aplikacjach istnieje jawna akcja, która wynika z odpowiadania na istniejącą wiadomość. Konwersacje są formowane jawnie w wyniku tej akcji użytkownika. Oto przykładowy zrzut ekranu przedstawiający konwersację w kanale w Microsoft Teams.

   ![Microsoft Teams konwersacji w kanale.](../media/threadedchat.png)

   W innych aplikacjach (takich jak wiadomości czatu grupowego w Teams) nie ma formalnego łańcucha odpowiedzi, a zamiast tego wiadomości są wyświetlane jako "płaska rzeka wiadomości" w jednym wątku. W aplikacjach tego typu konwersacje są wywłaszane z grupy wiadomości wysyłanych w określonym czasie. To "miękkie grupowanie" wiadomości (w odróżnieniu od łańcucha odpowiedzi) reprezentuje konwersację "tam i z powrotem" na określony temat.

## <a name="step-1-create-a-draft-collection"></a>Krok 1. Tworzenie kolekcji roboczej

Po zidentyfikowaniu odpowiednich materiałów przechowywczych i lokalizacji zawartości można utworzyć wyszukiwanie w celu znalezienia potencjalnie odpowiedniej zawartości. Na **karcie Kolekcje** w Advanced eDiscovery przypadku możesz utworzyć kolekcję, klikając pozycję Nowa **kolekcja i korzystając** z kreatora. Aby uzyskać informacje na temat tworzenia kolekcji, tworzenia zapytania wyszukiwania i wyświetlania podglądu wyników wyszukiwania, zobacz Tworzenie [kolekcji roboczej](create-draft-collection.md).

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>Krok 2. Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji

Po przejrzeniu i sfinalizowaniu zapytania wyszukiwania w kolekcji możesz dodać wyniki wyszukiwania do zestawu recenzji. Po dodaniu wyników wyszukiwania do zestawu recenzji oryginalne dane są kopiowane do obszaru usługi Azure Storage w celu ułatwienia procesu przeglądu i analizy. Aby uzyskać więcej informacji na temat dodawania wyników wyszukiwania do zestawu recenzji, zobacz [Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji](commit-draft-collection.md).

Po dodaniu elementów z konwersacji do zestawu recenzji możesz użyć opcji konwersacji z wątkami, aby zbierać wiadomości kontekstowe z konwersacji, które zawierają elementy zgodne z kryteriami wyszukiwania kolekcji. Po wybraniu opcji konwersacji w wątkach mogą się zdarzyć następujące zdarzenia:

  ![Pobieranie konwersacji.](../media/messagesandconversations.png)

1. Za pomocą zapytania słowa kluczowego i zakresu dat wyszukiwanie zwróciło hit w *wiadomości 3*. Ta wiadomość była częścią większej konwersacji, jak wynika z *CRC1*.

2. Gdy dodasz dane do zestawu recenzji i włączysz opcje pobierania konwersacji, program Advanced eDiscovery wróci i zbierze inne elementy w *CRC1*.

3. Po dodaniu elementów do zestawu recenzji możesz przejrzeć wszystkie poszczególne wiadomości z *CRC1*.

Aby włączyć opcję konwersacji z wątkami, zobacz [Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set).

## <a name="step-3-review-and-export-threaded-conversations"></a>Krok 3. Przeglądanie i eksportowanie konwersacji z wątkami

Po przetworzeniu i dodaniu zawartości do zestawu recenzji możesz rozpocząć przeglądanie danych w zestawie recenzji. Poszczególne wiadomości są ze sobą wątkami i przedstawiane jako konwersacje. Pozwala to przeglądać i eksportować konwersacje kontekstowe.

  ![Zestaw recenzji konwersacji.](../media/ConversationRSOptions.PNG)

W poniższych sekcjach opisano przeglądanie i eksportowanie konwersacji.

### <a name="reviewing-conversations"></a>Przeglądanie konwersacji

W zestawie recenzji możesz użyć następujących opcji w celu ułatwienia procesu przeglądu.

- **Grupowanie według konwersacji:** Grupuje wiadomości w tej samej konwersacji, aby ułatwić użytkownikom uproszczenie i przyspieszyć proces sprawdzania.

- **Widok podsumowania:** Wyświetla konwersację z wątkami. W tym widoku możesz wyświetlić całą konwersację oraz uzyskać dostęp do metadanych poszczególnych wiadomości.

   - Wyświetlanie metadanych dla poszczególnych wiadomości

   - Pobieranie poszczególnych wiadomości

- **Widok tekstu:** Zapewnia wyodrębniony tekst dla całej konwersacji.

- **Widok adnotacji:** Umożliwia oznaczenie widoku konwersacji z wątkami. Wszystkie wiadomości w konwersacji mają ten sam dokument z adnotacjami.

- **Znakowanie:** Podczas wyświetlania konwersacji w zestawie recenzji możesz wyświetlać i stosować tagi, klikając **panel Tagowanie** w panelu Kodowanie.

- **Ponowne uruchomić konwersję konwersacji:** Po dodaniu wiadomości do zestawu recenzji konwersacji jest automatycznie uruchamiane zadanie konwersji w celu utworzenia podsumowania z wątkami i dodano adnotacje do widoków. Jeśli zadanie Konwersacja po schłoniu nie powiedzie się, możesz ponownie uruchomić to zadanie, klikając pozycję Akcja **> Utwórz pliki PDF** konwersacji w zestawie recenzji.

### <a name="exporting-conversations"></a>Eksportowanie konwersacji

Aby zapoznać się z opcjami, które można wybrać podczas eksportowania konwersacji z zestawu recenzji, zobacz [Eksportowanie dokumentów ze zestawu recenzji](export-documents-from-review-set.md#export-options).

W szczególności możesz wyeksportować całe konwersacje na czacie w jednym pliku PDF lub wyeksportować każdą wiadomość czatu w konwersacji jako pojedynczy plik.

## <a name="more-information"></a>Więcej informacji

Aby dowiedzieć się więcej na temat przeglądania danych dotyczących Advanced eDiscovery przypadku, zobacz następujące artykuły:

- [Wykonywanie kwerend i filtrowanie zawartości w zestawie recenzji](review-set-search.md)
- [Oznaczanie dokumentów w zestawie recenzji](tagging-documents.md)
- [Wyświetlanie danych sprawy](view-documents-in-review-set.md)
- [Analizowanie danych sprawy](analyzing-data-in-review-set.md)
- [Eksportowanie danych sprawy](exporting-data-ediscover20.md)
