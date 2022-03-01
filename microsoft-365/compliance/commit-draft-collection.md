---
title: Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Po utworzeniu i utworzeniu iteratu w wersji roboczej kolekcji możesz zatwierdzić go do zestawu recenzji. Po zatwierdzeniu wersji roboczej kolekcji zebrane elementy są dodawane do zestawu recenzji w tym przypadku. Po zakończeniu przeglądania zestawu zbierania elementów możesz je analizować, przeglądać i eksportować.
ms.openlocfilehash: d74d1b062101973d2d3cb055700c59a2d25c0d14
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014922"
---
# <a name="commit-a-draft-collection-to-a-review-set-in-advanced-ediscovery"></a>Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji w programie Advanced eDiscovery

Jeśli elementy zebrane w kolekcji roboczej są zadowerałe i mogą być analizowane, oznaczane i przeglądane, można dodać kolekcję do zestawu recenzji w tym przypadku. Po zatwierdzeniu kolekcji roboczej do zestawu recenzji zebrane elementy są kopiowane z ich oryginalnej lokalizacji zawartości w programie Microsoft 365 do zestawu recenzji. Zestaw recenzji to bezpieczna, podana przez firmę Microsoft Storage Azure lokalizacja w chmurze firmy Microsoft.

## <a name="commit-a-draft-collection-to-a-review-set"></a>Zatwierdzanie wersji roboczej kolekcji do zestawu recenzji

1. W Centrum zgodności platformy Microsoft 365 otwórz sprawę Advanced eDiscovery, a następnie wybierz **kartę** Kolekcje, aby wyświetlić listę kolekcji w przypadku.

   ![Lista kolekcji w przypadku sprawy.](../media/CommitDraftCollections1.png)

   > [!TIP]
   > Wartość w kolumnie `Estimated` **Stan** określa wersje robocze kolekcji, które można dodać do zestawu recenzji. Stan oznacza `Committed` , że kolekcja została już dodana do zestawu recenzji.

2. Na stronie **Kolekcje** wybierz kolekcję roboczą, którą chcesz zatwierdzić do zestawu recenzji.

3. U dołu strony wysuwana wybierz pozycję **ActionsEdit** >  collection.

4. W kreatorze edycji kolekcji kliknij przycisk **Dalej** , aż zostanie **wyświetlona** strona Zapisz wersje robocze lub Zbieranie.

5. Skonfiguruj następujące ustawienia:

   1. Wybierz **pozycję Odbierz elementy i dodaj, aby przejrzeć zestaw**.

   2. Zdecyduj, czy chcesz dodać kolekcję do nowego zestawu recenzji (który jest tworzony po przesłaniu kolekcji), czy dodać ją do istniejącego zestawu recenzji. Ukończ tę sekcję na podstawie twojej decyzji.

   3. Skonfiguruj dodatkowe ustawienia kolekcji:

      ![Konfigurowanie dodatkowych ustawień kolekcji.](../media/AeDAdditionalCollectionSettings.png).

       a. **Teams i Yammer** wiadomości: Wybierz tę opcję, aby dodawać wątki konwersacji do kolekcji, które zawierają elementy czatu zwrócone przez zapytanie wyszukiwania w kolekcji. Oznacza to, że konwersacja na czacie zawierająca elementy zgodne z kryteriami wyszukiwania zostanie odtworzyć. Pozwala to przeglądać elementy czatu w kontekście konwersacji w tę i z powrotem. Aby uzyskać więcej informacji, zobacz [Wątki konwersacji w programie Advanced eDiscovery](conversation-review-sets.md).

       b. **Załączniki w** chmurze: wybierz tę opcję, aby uwzględnić nowoczesne załączniki lub pliki połączone po dodaniu wyników kolekcji do zestawu recenzji. Oznacza to, że do zestawu recenzji zostanie dodany plik docelowy nowoczesnego załącznika lub pliku połączonego.

       > [!NOTE]
       > Dwie opcje zbierania wiadomości Teams wiadomości Yammer i załączników w chmurze są domyślnie wybrane (wyszarzonych) w przypadku spraw utworzonych przy użyciu nowego formatu sprawy. Aby uzyskać więcej informacji, zobacz [Używanie nowego formatu sprawy](advanced-ediscovery-new-case-format.md).

       c. **Elementy częściowo indeksowane**: zaznacz tę opcję, aby dodać elementy częściowo indeksowane z dodatkowych źródeł danych do zestawu recenzji. Jeśli kolekcja przeszukała dodatkowe źródła danych (określone na stronie Dodatkowe lokalizacje w kreatorze kolekcji), mogą być częściowo indeksowane elementy z tych lokalizacji, które chcesz dodać do zestawu recenzji. Elementy zdyskułowane i niezabędące częściowe źródła danych zwykle nie zawierają częściowo indeksowanych elementów. Jest tak dlatego, że w procesie indeksowania zaawansowanego elementy są ponownie indeksowane w przypadku dodania do sprawy źródeł danych o niedobłędnych i niedobłędnych źródłach danych. Ponadto dodanie elementów częściowo indeksowanych spowoduje zwiększenie liczby elementów dodanych do zestawu recenzji. <p> Po dodaniu częściowo indeksowanych elementów do zestawu recenzji możesz zastosować filtr, aby wyświetlić te elementy. Aby uzyskać więcej informacji, zobacz [Filtrowanie elementów częściowo indeksowanych.](review-set-search.md#filter-partially-indexed-items)

      d. **SharePoint wersji**: Zaznacz tę opcję, aby włączyć kolekcję wszystkich wersji dokumentu pakietu SharePoint według limitów wersji i parametrów wyszukiwania w kolekcji. Zaznaczenie tej opcji znacząco zwiększy rozmiar elementów dodawanych do zestawu recenzji. Po dodaniu wersji dokumentu do zestawu recenzji 

   4. Skonfiguruj ustawienia w celu zdefiniowania skali kolekcji, która będzie dodawania do zestawu recenzji:

      - **Dodaj wszystkie wyniki kolekcji**: wybierz tę opcję, aby dodać do zestawu recenzji wszystkie elementy zgodne z kryteriami wyszukiwania kolekcji.

      - **Dodaj przykładowe wyniki** kolekcji: wybierz tę opcję, aby dodać przykładowe wyniki kolekcji do zestawu recenzji zamiast dodawania wszystkich wyników. Jeśli wybierzesz tę opcję, kliknij pozycję **Edytuj przykładowe parametry** i wybierz jedną z następujących opcji:

         - **Próbka oparta na pewności**: elementy z kolekcji są dodawane do zestawu recenzji na podstawie ustawionych parametrów statystycznych. Jeśli zazwyczaj podczas próbkowania wyników używasz poziomu ufności i interwału, określ je w polach rozwijanych. W przeciwnym razie użyj ustawień domyślnych.

         - **Losowo próbka**: Elementy z kolekcji są dodawane do zestawu recenzji na podstawie losowego zaznaczenia określonego procentu całkowitej liczby elementów zwróconych przez wyszukiwanie.

6. Na **stronie Przeglądanie kolekcji** możesz przejrzeć ustawienia kolekcji skonfigurowane na poprzedniej stronie. Kliknij **pozycję Edytuj** , jeśli chcesz je zmienić.

7. Kliknij **przycisk Prześlij** , aby utworzyć kolekcję roboczą. Zostanie wyświetlona strona z potwierdzeniem utworzenia kolekcji.

## <a name="what-happens-after-you-commit-a-draft-collection"></a>Co się dzieje po zatwierdzeniu wersji roboczej kolekcji

Po zatwierdzeniu kolekcji roboczej do zestawu recenzji są w tym przypadku następujące zdarzenia:

- Jeśli utworzono nowy zestaw recenzji w celu zatwierdzenia kolekcji, w tym przypadku zestaw recenzji zostanie utworzony i  wyświetlony na karcie Zestawy recenzji. Nowy zestaw recenzji ma stan **Gotowe**. Ta wartość stanu oznacza, że został utworzony zestaw recenzji. nie oznacza to, że kolekcja została dodana do zestawu recenzji. Stan dodawania elementów z kolekcji do zestawu recenzji jest wyświetlany na **karcie Kolekcje** .

- Zapytanie wyszukiwania kolekcji zostanie ponownie uruchomione. Oznacza to, że rzeczywiste wyniki wyszukiwania skopiowane do zestawu recenzji mogą być inne niż szacowane wyniki zwrócone podczas ostatniego wyszukiwania w kolekcji.

- Wszystkie elementy w wynikach wyszukiwania są kopiowane z oryginalnego źródła danych w usłudze na żywo i kopiowane do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

- Zaszyfrowane SharePoint i OneDrive oraz zaszyfrowane pliki dołączonych wiadomości e-mail zwracanych w wynikach wyszukiwania są odszyfrowywać po zatwierdzeniu kolekcji do zestawu recenzji. Możesz przeglądać odszyfrowane pliki i odszyfrowywać je w zestawie recenzji. Aby uzyskać więcej informacji, zobacz [Odszyfrowywanie w narzędziu Microsoft 365 zbierania elektronicznych materiałów dowodowych](ediscovery-decryption.md).

- Funkcja optycznego rozpoznawania znaków (OCR) wyodrębnia tekst z obrazów i uwzględnia tekst obrazu z zawartością dodaną do zestawu recenzji. Aby uzyskać więcej informacji, zobacz [sekcję optycznego](#optical-character-recognition) rozpoznawania znaków w tym artykule.

- Po pomyślnym ukończeniu zatwierdzania wartość kolumny stanu na karcie Kolekcje **zmienia się** na `Committed`.

## <a name="optical-character-recognition"></a>Optyczne rozpoznawanie znaków

Po zatwierdzeniu kolekcji do zestawu recenzji funkcja optycznego rozpoznawania znaków (OCR) w programie Advanced eDiscovery automatycznie wyodrębnia tekst z obrazów i dodaje tekst obrazu do zawartości dodanej do zestawu recenzji. Wyodrębniony tekst można wyświetlić w przeglądarce tekstu wybranego pliku obrazu w zestawie recenzji. Umożliwia to dalsze przeglądanie i analizowanie tekstu na obrazach. Funkcja OCR jest obsługiwana w przypadku luźnych plików, załączników wiadomości e-mail i obrazów osadzonych. Aby uzyskać listę formatów plików obrazów, które są obsługiwane przez OCR, zobacz [Obsługiwane typy](supported-filetypes-ediscovery20.md#image) plików w Advanced eDiscovery.

Musisz włączyć funkcję OCR dla każdej sprawy, która jest tworzyć w Advanced eDiscovery. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
