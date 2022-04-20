---
title: Przeglądanie konwersacji w usłudze eDiscovery (Premium)
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
description: Dowiedz się więcej o funkcji rekonstrukcji konwersacji w usłudze Microsoft Purview eDiscovery (Premium) (nazywanej wątkami konwersacji), aby odtworzyć, przejrzeć i wyeksportować rozmowy na czacie w grupach Microsoft Teams i Yammer.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: c3cd05ab340775a7a923b9e4a0f66c3abaf559cb
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993277"
---
# <a name="conversation-threading-in-ediscovery-premium"></a>Wątkowość konwersacji w środowisku zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Wiadomości błyskawiczne to wygodny sposób zadawania pytań, dzielenia się pomysłami lub szybkiej komunikacji między dużymi odbiorcami. Ponieważ platformy wiadomości błyskawicznych, takie jak Microsoft Teams i grupy Yammer, stają się podstawą współpracy w przedsiębiorstwie, organizacje muszą ocenić, w jaki sposób przepływ pracy zbierania elektronicznych elektronicznych materiałów dowodowych obsługuje te nowe formy komunikacji i współpracy.

Funkcja rekonstrukcji konwersacji w usłudze Microsoft Purview eDiscovery (Premium) została zaprojektowana w celu ułatwienia identyfikowania zawartości kontekstowej i tworzenia odrębnych widoków konwersacji. Ta funkcja umożliwia wydajne i szybkie przeglądanie pełnych konwersacji wiadomości błyskawicznych (*nazywanych również konwersacjami wątkowymi*), które są generowane na platformach takich jak Microsoft Teams.

W przypadku rekonstrukcji konwersacji można używać wbudowanych możliwości do rekonstruowania, przeglądania i eksportowania konwersacji wątkowych. Użyj rekonstrukcji konwersacji zbierania elektronicznych materiałów dowodowych (Premium), aby:

- Zachowaj unikatowe metadane na poziomie komunikatów we wszystkich komunikatach w konwersacji.

- Zbieraj komunikaty kontekstowe wokół wyników wyszukiwania.

- Przeglądanie, adnotacja i redagowanie konwersacji wątkowych.

- Eksportowanie poszczególnych komunikatów lub konwersacji wątkowych

## <a name="terminology"></a>Terminologii

Poniżej przedstawiono kilka definicji ułatwiających rozpoczęcie korzystania z rekonstrukcji konwersacji.

- **Wiadomości:** Reprezentują najmniejszą jednostkę konwersacji. Komunikaty mogą różnić się rozmiarem, strukturą i metadanymi.

- **Konwersacji:** Reprezentuje grupowanie co najmniej jednego komunikatu. W różnych aplikacjach konwersacje mogą być reprezentowane na różne sposoby. W niektórych aplikacjach istnieje jawna akcja, która wynika z odpowiedzi na istniejącą wiadomość. Konwersacje są tworzone jawnie w wyniku tej akcji użytkownika. Na przykład poniżej przedstawiono zrzut ekranu konwersacji kanału w Microsoft Teams.

   ![Microsoft Teams konwersacji kanału.](../media/threadedchat.png)

   W innych aplikacjach (takich jak wiadomości czatu grupowego w Teams) nie istnieje formalny łańcuch odpowiedzi, a zamiast tego komunikaty są wyświetlane jako "płaska rzeka wiadomości" w jednym wątku. W aplikacjach tego typu konwersacje są wywnioskowane z grupy komunikatów, które występują w określonym czasie. To "grupowanie nietrwałe" komunikatów (w przeciwieństwie do łańcucha odpowiedzi) reprezentuje konwersację "tam iz powrotem" dotyczącą konkretnego tematu.

## <a name="step-1-create-a-draft-collection"></a>Krok 1. Tworzenie kolekcji roboczej

Po zidentyfikowaniu odpowiednich opiekunów i lokalizacji zawartości możesz utworzyć wyszukiwanie w celu znalezienia potencjalnie odpowiedniej zawartości. Na **karcie Kolekcje** w przypadku zbierania elektronicznych materiałów dowodowych (Premium) możesz utworzyć kolekcję, klikając pozycję **Nowa kolekcja** i postępując zgodnie z instrukcjami kreatora. Aby uzyskać informacje o sposobie tworzenia kolekcji, tworzenia zapytania wyszukiwania i wyświetlania podglądu wyników wyszukiwania, zobacz [Tworzenie kolekcji roboczej](create-draft-collection.md).

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>Krok 2. Zatwierdzanie kolekcji roboczej w zestawie przeglądów

Po przejrzeniu i sfinalizowaniu zapytania wyszukiwania w kolekcji możesz dodać wyniki wyszukiwania do zestawu przeglądów. Po dodaniu wyników wyszukiwania do zestawu przeglądów oryginalne dane są kopiowane do obszaru usługi Azure Storage w celu ułatwienia procesu przeglądu i analizy. Aby uzyskać więcej informacji na temat dodawania wyników wyszukiwania do zestawu przeglądów, zobacz [Zatwierdzanie kolekcji roboczej do zestawu przeglądów](commit-draft-collection.md).

Po dodaniu elementów z konwersacji do zestawu przeglądów można użyć opcji konwersacji wątkowych do zbierania komunikatów kontekstowych z konwersacji zawierających elementy zgodne z kryteriami wyszukiwania kolekcji. Po wybraniu opcji konwersacji wątku mogą wystąpić następujące rzeczy:

  ![Pobieranie konwersacji.](../media/messagesandconversations.png)

1. Za pomocą zapytania dotyczącego słowa kluczowego i zakresu dat wyszukiwanie zwróciło trafienie komunikatu *3*. Ta wiadomość była częścią większej konwersacji zilustrowanej przez *CRC1*.

2. Po dodaniu danych do zestawu przeglądów i włączeniu opcji pobierania konwersacji zbieranie elektronicznych materiałów dowodowych (Premium) spowoduje powrót i zebranie innych elementów w *crc1*.

3. Po dodaniu elementów do zestawu przeglądów możesz przejrzeć wszystkie poszczególne komunikaty z *listy CRC1*.

Aby włączyć opcję konwersacji wątkowych, zobacz [Zatwierdzanie kolekcji roboczej do zestawu przeglądów](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set).

## <a name="step-3-review-and-export-threaded-conversations"></a>Krok 3. Przeglądanie i eksportowanie konwersacji wątkowych

Po przetworzeniu i dodaniu zawartości do zestawu przeglądów możesz rozpocząć przeglądanie danych w zestawie przeglądów. Poszczególne komunikaty są połączone ze sobą i prezentowane jako konwersacje. Umożliwia to przeglądanie i eksportowanie konwersacji kontekstowych.

  ![Zestaw przeglądów konwersacji.](../media/ConversationRSOptions.PNG)

W poniższych sekcjach opisano przeglądanie i eksportowanie konwersacji.

### <a name="reviewing-conversations"></a>Przeglądanie konwersacji

W zestawie przeglądów można użyć następujących opcji, aby ułatwić proces przeglądu.

- **Grupuj według konwersacji:** Grupuje komunikaty w ramach tej samej konwersacji, aby ułatwić użytkownikom uproszczenie i przyspieszenie procesu przeglądu.

- **Widok podsumowania:** Wyświetla konwersację wątkową. W tym widoku można wyświetlić całą konwersację, a także uzyskać dostęp do metadanych dla każdej pojedynczej wiadomości.

   - Wyświetlanie metadanych dla poszczególnych komunikatów

   - Pobieranie poszczególnych komunikatów

- **Widok tekstowy:** Udostępnia wyodrębniony tekst dla całej konwersacji.

- **Widok adnotacji:** Umożliwia oznaczanie wątkowego widoku konwersacji. Wszystkie komunikaty w konwersacji mają ten sam dokument z adnotacjami.

- **Oznaczanie:** Podczas wyświetlania konwersacji w zestawie przeglądów można wyświetlać i stosować tagi, klikając **panel Tagowanie** w panelu Kodowanie.

- **Ponowne uruchamianie konwersji konwersacji:** Po dodaniu komunikatów do zestawu przeglądów konwersacji zadanie konwersji jest uruchamiane automatycznie w celu utworzenia wątkowego podsumowania i adnotacji widoków. Jeśli zadanie rekonstrukcji konwersacji nie powiedzie się, możesz ponownie uruchomić to zadanie, klikając pozycję **Akcja > Tworzenie plików PDF konwersacji w zestawie przeglądów** .

### <a name="exporting-conversations"></a>Eksportowanie konwersacji

Aby uzyskać opcje, które można wybrać podczas eksportowania konwersacji z zestawu przeglądów, zobacz [Eksportowanie dokumentów z zestawu przeglądów](export-documents-from-review-set.md#export-options).

W szczególności możesz wyeksportować całe konwersacje rozmów w jednym pliku PDF lub wyeksportować każdą wiadomość czatu w konwersacji jako pojedynczy plik.

## <a name="more-information"></a>Więcej informacji

Aby dowiedzieć się więcej na temat przeglądania danych przypadków w usłudze eDiscovery (Premium), zobacz następujące artykuły:

- [Wykonuj zapytania i filtruj zawartość w zestawie do przeglądu](review-set-search.md)
- [Taguj dokumenty w zestawie do przeglądu](tagging-documents.md)
- [Wyświetlanie danych wielkości liter](view-documents-in-review-set.md)
- [Analizowanie danych przypadków](analyzing-data-in-review-set.md)
- [Eksportowanie danych sprawy](exporting-data-ediscover20.md)
