---
title: Zatwierdź kolekcję roboczą w zestawie do przeglądu
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Po utworzeniu i iteracji w kolekcji roboczej można zatwierdzić ją w zestawie przeglądów. Po zatwierdzeniu kolekcji roboczej zebrane elementy są dodawane do zestawu przeglądów w tym przypadku. Gdy zebrane elementy znajdują się w zestawie przeglądów, można je analizować, przeglądać i eksportować.
ms.openlocfilehash: e635489383026df0d8097a300eb49178dcffb6b5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632712"
---
# <a name="commit-a-draft-collection-to-a-review-set-in-ediscovery-premium"></a>Zatwierdzanie kolekcji roboczej do zestawu przeglądów w usłudze eDiscovery (Premium)

Jeśli elementy zebrane w kolekcji roboczej są zadowalające i są gotowe do ich analizowania, tagowania i przeglądania, możesz dodać kolekcję do zestawu przeglądów w tym przypadku. Po zatwierdzeniu kolekcji roboczej do zestawu przeglądów zebrane elementy są kopiowane z ich oryginalnej lokalizacji zawartości w usłudze Microsoft 365 do zestawu przeglądów. Zestaw przeglądów to bezpieczna lokalizacja usługi Azure Storage udostępniona przez firmę Microsoft w chmurze firmy Microsoft.

## <a name="commit-a-draft-collection-to-a-review-set"></a>Zatwierdź kolekcję roboczą w zestawie do przeglądu

1. W portal zgodności Microsoft Purview otwórz przypadek Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium), a następnie wybierz kartę **Kolekcje**, aby wyświetlić listę kolekcji w tym przypadku.

   ![Lista kolekcji w przypadku.](../media/CommitDraftCollections1.png)

   > [!TIP]
   > Wartość w `Estimated` kolumnie **Stan** identyfikuje kolekcje robocze, które można dodać do zestawu przeglądów. Stan `Committed` wskazuje, że kolekcja została już dodana do zestawu przeglądów.

2. Na stronie **Kolekcje** wybierz kolekcję roboczą, którą chcesz zatwierdzić w zestawie przeglądów.

3. W dolnej części strony wysuwanej wybierz pozycję **Akcje Edytuj** > **kolekcję**.

4. W kreatorze edycji kolekcji kliknij przycisk **Dalej** , dopóki nie zostanie wyświetlona strona **Zapisz wersję roboczą lub zbieranie** .

5. Skonfiguruj następujące ustawienia:

   1. Wybierz pozycję **Zbierz elementy i dodaj, aby przejrzeć zestaw**.

   2. Zdecyduj, czy dodać kolekcję do nowego zestawu przeglądów (który zostanie utworzony po przesłaniu kolekcji), czy dodać ją do istniejącego zestawu przeglądów. Ukończ tę sekcję na podstawie decyzji.

   3. Skonfiguruj dodatkowe ustawienia kolekcji:

      ![Skonfiguruj dodatkowe ustawienia kolekcji.](../media/AeDAdditionalCollectionSettings.png).

       a. **Komunikaty usługi Teams i Yammer**: wybierz tę opcję, aby dodać wątki konwersacji do kolekcji, które zawierają elementy czatu zwrócone przez zapytanie wyszukiwania w kolekcji. Oznacza to, że konwersacja czatu zawierająca elementy zgodne z kryteriami wyszukiwania jest rekonstruowana. Umożliwia to przeglądanie elementów czatu w kontekście konwersacji tam iz powrotem. Aby uzyskać więcej informacji, zobacz [Konwersacja wątków w eDiscovery (Premium)](conversation-review-sets.md).

       b. **Załączniki w chmurze**: wybierz tę opcję, aby uwzględnić nowoczesne załączniki lub połączone pliki, gdy wyniki kolekcji zostaną dodane do zestawu przeglądów. Oznacza to, że plik docelowy nowoczesnego załącznika lub połączonego pliku jest dodawany do zestawu przeglądów.

       > [!NOTE]
       > Dwie opcje zbierania kontekstowych komunikatów usługi Teams i Yammer oraz załączników w chmurze są domyślnie wybierane (i wyszarzone) dla przypadków utworzonych przy użyciu nowego formatu przypadku. Aby uzyskać więcej informacji, zobacz [Używanie nowego formatu przypadku](advanced-ediscovery-new-case-format.md).

       c. **Elementy częściowo indeksowane**: wybierz tę opcję, aby dodać częściowo indeksowane elementy z dodatkowych źródeł danych do zestawu przeglądów. Jeśli kolekcja przeszukała dodatkowe źródła danych (zgodnie z opisem na stronie **Dodatkowe lokalizacje** w kreatorze kolekcji), mogą istnieć częściowo zaindeksowane elementy z tych lokalizacji, które chcesz dodać do zestawu przeglądów. Źródła danych bez nadzoru zazwyczaj nie mają częściowo zaindeksowanych elementów. Dzieje się tak dlatego, że zaawansowany proces indeksowania ponownie indeksuje elementy, gdy źródła danych będące przedmiotem nadzoru i nienadzorowane są dodawane do sprawy. Ponadto dodanie częściowo indeksowanych elementów zwiększy liczbę elementów dodanych do zestawu przeglądów. <p> Po dodaniu częściowo indeksowanych elementów do zestawu przeglądów można zastosować filtr w celu wyświetlenia tych elementów. Aby uzyskać więcej informacji, zobacz [Filtrowanie częściowo indeksowanych elementów](review-set-search.md#filter-partially-indexed-items)

      d. **Wersje programu SharePoint**: wybierz tę opcję, aby włączyć kolekcję wszystkich wersji dokumentu programu SharePoint zgodnie z limitami wersji i parametrami wyszukiwania kolekcji. Wybranie tej opcji znacznie zwiększy rozmiar elementów dodanych do zestawu przeglądów. Po dodaniu wersji dokumentu do zestawu przeglądów 

   4. Skonfiguruj ustawienia, aby zdefiniować skalę kolekcji, aby dodać ją do zestawu przeglądów:

      - **Dodaj wszystkie wyniki kolekcji**: wybierz tę opcję, aby dodać wszystkie elementy zgodne z kryteriami wyszukiwania kolekcji do zestawu przeglądów.

      - **Dodaj przykład wyników kolekcji**: wybierz tę opcję, aby dodać przykład wyników kolekcji do zestawu przeglądów zamiast dodawać wszystkie wyniki. Jeśli wybierzesz tę opcję, kliknij pozycję **Edytuj przykładowe parametry** i wybierz jedną z następujących opcji:

         - **Przykład na podstawie ufności**: elementy z kolekcji są dodawane do zestawu przeglądów będą określane przez ustawione parametry statystyczne. Jeśli zwykle używasz poziomu ufności i interwału podczas próbkowania wyników, określ je w polach listy rozwijanej. W przeciwnym razie użyj ustawień domyślnych.

         - **Próbka losowa**: elementy z kolekcji są dodawane do zestawu przeglądów na podstawie losowego wyboru określonej wartości procentowej całkowitej liczby elementów zwróconych przez wyszukiwanie.

6. Na stronie **Przeglądanie kolekcji** możesz przejrzeć ustawienia kolekcji skonfigurowane na poprzedniej stronie. Kliknij przycisk **Edytuj** , jeśli chcesz je zmienić.

7. Kliknij pozycję **Prześlij** , aby utworzyć kolekcję roboczą. Zostanie wyświetlona strona potwierdzająca, że kolekcja została utworzona.

## <a name="what-happens-after-you-commit-a-draft-collection"></a>Co się stanie po zatwierdzeniu kolekcji roboczej

Po zatwierdzeniu kolekcji roboczej do zestawu przeglądów dzieje się następujące rzeczy:

- Jeśli utworzono nowy zestaw przeglądów w celu zatwierdzenia kolekcji, zestaw przeglądów zostanie utworzony i wyświetlony na karcie **Zestawy przeglądów** w tym przypadku. Stan nowego zestawu przeglądów to **Gotowe**. Ta wartość stanu oznacza, że zestaw przeglądów został utworzony. Nie oznacza to, że kolekcja została dodana do zestawu przeglądów. Stan dodawania elementów w kolekcji do zestawu przeglądów jest wyświetlany na **karcie Kolekcje** .

- Zapytanie wyszukiwania kolekcji zostanie uruchomione ponownie. Oznacza to, że rzeczywiste wyniki wyszukiwania skopiowane do zestawu przeglądów mogą być inne niż szacowane wyniki zwrócone podczas ostatniego uruchomienia wyszukiwania kolekcji.

- Wszystkie elementy w wynikach wyszukiwania są kopiowane z oryginalnego źródła danych w usłudze na żywo i kopiowane do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

- Zaszyfrowane dokumenty programu SharePoint i oneDrive oraz zaszyfrowane pliki dołączone wiadomości e-mail zwracane w wynikach wyszukiwania są odszyfrowywane po zatwierdzeniu kolekcji w zestawie przeglądów. W zestawie przeglądów można przeglądać odszyfrowane pliki i wykonywać względem nieodszyfrowanych plików. Aby uzyskać więcej informacji, zobacz [Decryption in Microsoft 365 eDiscovery tools (Odszyfrowywanie w narzędziach zbierania elektronicznych materiałów dowodowych platformy Microsoft 365](ediscovery-decryption.md)).

- Funkcja optycznego rozpoznawania znaków (OCR) wyodrębnia tekst z obrazów i zawiera tekst obrazu z zawartością dodaną do zestawu przeglądów. Aby uzyskać więcej informacji, zobacz sekcję [Optyczne rozpoznawanie znaków](#optical-character-recognition) w tym artykule.

- Po pomyślnym zakończeniu zatwierdzania wartość kolumny stanu na karcie **Kolekcje** zostanie zmieniona na `Committed`.

## <a name="optical-character-recognition"></a>Optyczne rozpoznawanie znaków

Po zatwierdzeniu kolekcji do zestawu przeglądów funkcja optycznego rozpoznawania znaków (OCR) w funkcji eDiscovery (Premium) automatycznie wyodrębnia tekst z obrazów i zawiera tekst obrazu z zawartością dodaną do zestawu przeglądów. Wyodrębniony tekst można wyświetlić w przeglądarce Tekst wybranego pliku obrazu w zestawie przeglądów. Dzięki temu można przeprowadzać dalsze przeglądy i analizy tekstu na obrazach. Funkcja OCR jest obsługiwana w przypadku luźnych plików, załączników wiadomości e-mail i obrazów osadzonych. Aby zapoznać się z listą formatów plików obrazów obsługiwanych w usłudze OCR, zobacz [Obsługiwane typy plików w usłudze eDiscovery (Premium)](supported-filetypes-ediscovery20.md#image).

Musisz włączyć funkcję OCR dla każdego przypadku utworzonego w środowisku eDiscovery (Premium). Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
