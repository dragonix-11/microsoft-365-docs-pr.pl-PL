---
title: Dodawanie wyników wyszukiwania do zestawu recenzji
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
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak dodać wyniki wyszukiwania lub przykłady tych wyników do zestawu Advanced eDiscovery przypadków.
ms.openlocfilehash: bce0301e7045eeb0dd5c42f8a119d56649120a11
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973790"
---
# <a name="add-search-results-to-a-review-set"></a>Dodawanie wyników wyszukiwania do zestawu recenzji

Jeśli wyniki wyszukiwania są zadowalace i możesz je przeglądać i analizować, możesz dodać je do zestawu recenzji w przypadku. Skopiowanie oryginalnych danych do zestawu recenzji ułatwia również proces przeglądania i analizy, udostępniając zaawansowane narzędzia do analizy, takie jak wykrywanie motywów, wykrywanie niemal duplikatów oraz rozpoznawanie wątku wiadomości e-mail. Do zestawu recenzji można również dodawać dane Microsoft 365 źródeł danych innych niż te, co umożliwia ich przeglądanie oprócz danych zebranych z Microsoft 365.

Po dodaniu wyników wyszukiwania do zestawu recenzji (zestawy recenzji w przypadku sprawy są wymienione na karcie Zestawy recenzji) występują następujące zdarzenia:

- Wyszukiwanie zostanie ponownie uruchomione. Oznacza to, że rzeczywiste wyniki wyszukiwania skopiowane do zestawu recenzji mogą być inne niż szacowane wyniki, które zostały zwrócone podczas ostatniego uruchomienia wyszukiwania.

- Wszystkie elementy w wynikach wyszukiwania są kopiowane z pierwotnego źródła danych w usługach na żywo i kopiowane do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

- Wszystkie elementy (w tym zawartość i metadane) są ponownie indeksowane, dzięki czemu można w pełni wyszukiwać wszystkie dane w zestawie recenzji podczas przeglądania danych sprawy. Ponowne indeksowanie wyników umożliwia dokładne i szybkie wyszukiwanie podczas przeszukiwania danych w zestawie recenzji podczas analizy przypadku.

- Plik zaszyfrowany przy użyciu technologii [szyfrowania firmy Microsoft](encryption.md) i dołączony do wiadomości e-mail zwróconej w wynikach wyszukiwania jest odszyfrowywany po dodaniu wiadomości e-mail i dołączonego pliku do zestawu recenzji. W zestawie recenzji możesz przeglądać odszyfrowany plik i odszyfrowywać go. Aby dodać odszyfrowane załączniki wiadomości e-mail do zestawu recenzji, musisz mieć przypisaną rolę odszyfrowywania usługi RMS. Aby uzyskać więcej informacji, zobacz [Odszyfrowywanie w narzędziu Microsoft 365 eDiscovery](ediscovery-decryption.md).

Aby dodać dane do zestawu recenzji, kliknij wyszukiwanie na karcie  Wyszukiwania, a następnie kliknij pozycję Dodaj wyniki do przejrzenia **ustawionego na** wysuwanych stronie.

Możesz dodać go do istniejącego zestawu recenzji lub utworzyć nowy zestaw recenzji.  Jeśli dodajesz do nowego zestawu recenzji, określ jego nazwę, a następnie kliknij przycisk **Dodaj** , aby wyświetlić stronę wysuwaną.

![Wybierz zestaw recenzji i skonfiguruj opcje kolekcji.](../media/AeD_AddToReviewSet.png)

Dodawanie danych do zestawu recenzji jest długim procesem. Ten proces obejmuje zbieranie elementów z oryginalnych źródeł danych w usłudze Microsoft 365 (na przykład ze skrzynek pocztowych i witryn), kopiowanie ich do lokalizacji usługi Azure Storage (ten proces kopiowania jest również nazywany wprowadzaniem *), a* następnie ponowne indeksowanie elementów. Możesz śledzić postęp na karcie Zadania lub  na karcie Wyszukiwania, monitorując stan w kolumnie Dodano dane **do przejrzenia zestawu**. Po zakończeniu przetwarzania zestawu recenzji kliknij  kartę Zestawy recenzji w przypadku, a następnie kliknij zestaw recenzji, aby rozpocząć proces filtrowania, reenzowania, znakowania i eksportowania danych w zestawie recenzji.

## <a name="define-options-to-scope-your-collection-for-review"></a>Definiowanie opcji w celu określenia zakresu kolekcji do recenzji

Po dodaniu zawartości wyszukiwania do istniejącego lub nowego zestawu recenzji dostępne są następujące opcje zbierania zawartości do przejrzenia:

- **Uwzględnij wersje z SharePoint (beta)**: Użyj tej opcji, aby włączyć kolekcję wszystkich wersji dokumentu pakietu SharePoint według limitów wersji i parametrów wyszukiwania kolekcji. Zaznaczenie tej opcji znacząco zwiększy rozmiar elementów dodawanych do zestawu recenzji.

- **Opcje pobierania konwersacji**: Elementy dodawane do zestawu recenzji są włączone dla konwersacji z wątkami, co pomaga przeglądać zawartość w kontekście konwersacji w tę i z powrotem. Aby uzyskać więcej informacji, [zobacz Przeglądanie konwersacji w programie Advanced eDiscovery](conversation-review-sets.md).

- **Włącz pobieranie dla nowoczesnych załączników**. Użyj tej opcji, aby dołączyć do kolekcji nowoczesne załączniki lub pliki połączone w celu dalszego przejrzenia. Aby uzyskać więcej informacji na temat właściwości, które można wyszukiwać w przypadku nowoczesnych załączników, zobacz Pola [metadanych dokumentu w programie Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="add-a-sample-to-a-review-set"></a>Dodawanie próbki do zestawu recenzji

Jeśli chcesz dokładniej sprawdzić wyniki wyszukiwania przed dodaniem ich wszystkich do zestawu recenzji, możesz dodać przykładowe wyniki wyszukiwania do zestawu recenzji, zamiast dodawać wszystko.

Aby dodać przykład do zestawu recenzji, kliknij wyszukiwanie na karcie Wyszukiwania, a następnie **kliknij pozycję Przykład** na wysuwana stronie. Na stronie **Parametry próbkowania** wybierz jedną z następujących opcji:

- **Poziom ufności %** i Przedział ufności **%** — elementy dodane do zestawu recenzji będą określane przez ustawione parametry statystyczne. Jeśli zazwyczaj podczas próbkowania wyników używasz poziomu ufności i interwału, określ je w polach rozwijanych. W przeciwnym razie użyj ustawień domyślnych.

- **Losowe próbki %** — elementy dodane do zestawu recenzji są oparte na losowym zaznaczeniu określonej wartości procentowej całkowitej liczby elementów zwróconych przez wyszukiwanie.

Po wybraniu i skonfigurowaniu jednej z poprzednich opcji wybierz zestaw recenzji, do których chcesz dodać przykład, a następnie kliknij przycisk **Wyślij**. Ponownie możesz śledzić postęp na karcie Zadania lub na  karcie Wyszukiwania, monitorując  stan w kolumnie Dodano dane **do przejrzenia zestawu**.

## <a name="optical-character-recognition"></a>Optyczne rozpoznawanie znaków

Po dodaniu wyników wyszukiwania do zestawu recenzji funkcja optycznego rozpoznawania znaków (OCR) w programie Advanced eDiscovery automatycznie wyodrębnia tekst z obrazów i dodaje tekst obrazu do danych dodanych do zestawu recenzji. Wyodrębniony tekst można wyświetlić w przeglądarce tekstu wybranego pliku obrazu w zestawie recenzji. Umożliwia to dalsze przeglądanie i analizowanie tekstu na obrazach. Funkcja OCR jest obsługiwana w przypadku luźnych plików, załączników wiadomości e-mail i obrazów osadzonych. Aby uzyskać listę formatów plików obrazów, które są obsługiwane przez OCR, zobacz [Obsługiwane typy](supported-filetypes-ediscovery20.md#image) plików w Advanced eDiscovery.

Musisz włączyć funkcję OCR dla każdej sprawy, która jest tworzyć w Advanced eDiscovery. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
