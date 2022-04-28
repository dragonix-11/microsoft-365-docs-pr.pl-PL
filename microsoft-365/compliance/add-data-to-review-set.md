---
title: Dodawanie wyników wyszukiwania do zestawu przeglądów
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak dodać wyniki wyszukiwania lub przykłady tych wyników wyszukiwania do zestawu przeglądu przypadków zbierania elektronicznych materiałów dowodowych (Premium).
ms.openlocfilehash: cda1a7fcf33a5fc1b299fd2d66f7241ab1cef229
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100968"
---
# <a name="add-search-results-to-a-review-set"></a>Dodawanie wyników wyszukiwania do zestawu przeglądów

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Gdy wyniki wyszukiwania są zadowalające i możesz je przejrzeć i przeanalizować, możesz dodać je do zestawu przeglądów w tym przypadku. Kopiowanie oryginalnych danych do zestawu przeglądów ułatwia również proces przeglądania i analizy, udostępniając zaawansowane narzędzia analityczne, takie jak wykrywanie motywów, wykrywanie niemal duplikatów i identyfikacja wątków poczty e-mail. Możesz również dodać dane ze źródeł danych innych niż Microsoft 365 do zestawu przeglądów, aby można było przeglądać te dane oprócz danych zbieranych z Microsoft 365.

Po dodaniu wyników wyszukiwania do zestawu przeglądów (zestawy przeglądów w przypadku są wymienione na karcie **Zestawy przeglądów** ) występują następujące rzeczy:

- Wyszukiwanie zostanie uruchomione ponownie. Oznacza to, że rzeczywiste wyniki wyszukiwania skopiowane do zestawu przeglądów mogą być inne niż szacowane wyniki, które zostały zwrócone podczas ostatniego uruchomienia wyszukiwania.

- Wszystkie elementy w wynikach wyszukiwania są kopiowane z oryginalnego źródła danych w usługach na żywo i kopiowane do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

- Wszystkie elementy (w tym zawartość i metadane) są ponownie indeksowane, aby wszystkie dane w zestawie przeglądów były w pełni przeszukiwane podczas przeglądania danych sprawy. Ponowne indeksowanie danych powoduje dokładne i szybkie wyszukiwanie podczas przeszukiwania danych w zestawie przeglądów podczas badania sprawy.

- Plik zaszyfrowany za pomocą [technologii szyfrowania firmy Microsoft](encryption.md) i dołączony do wiadomości e-mail zwracanej w wynikach wyszukiwania jest odszyfrowywany po dodaniu wiadomości e-mail i dołączonego pliku do zestawu przeglądów. Odszyfrowany plik można przeglądać i wykonywać zapytania w zestawie przeglądów. Musisz mieć przypisaną rolę odszyfrowywania usługi RMS, aby dodać odszyfrowane załączniki wiadomości e-mail do zestawu przeglądów. Aby uzyskać więcej informacji, zobacz [Decryption in Microsoft Purview eDiscovery tools (Odszyfrowywanie w narzędziach zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview](ediscovery-decryption.md)).

Aby dodać dane do zestawu przeglądów, kliknij wyszukiwanie na karcie **Wyszukiwania** , a następnie kliknij pozycję **Dodaj wyniki, aby przejrzeć zestaw** na stronie wysuwanej.

Możesz dodać do istniejącego zestawu przeglądów lub utworzyć nowy zestaw przeglądów.  W przypadku dodawania do nowego zestawu przeglądów określ nazwę, a następnie kliknij przycisk **Dodaj** , aby wyświetlić stronę wysuwaną.

![Wybierz zestaw przeglądów i skonfiguruj opcje kolekcji.](../media/AeD_AddToReviewSet.png)

Dodawanie danych do zestawu przeglądów jest długotrwałym procesem. Ten proces obejmuje zbieranie elementów z oryginalnych źródeł danych w Microsoft 365 (na przykład ze skrzynek pocztowych i witryn), kopiowanie ich do lokalizacji Storage platformy Azure (ten proces kopiowania jest również nazywany *pozyskiwaniem*), a następnie ponowne indeksowanie elementów. Postęp można śledzić na karcie **Zadania** lub na karcie **Wyszukiwania** , monitorując stan w kolumnie **Dodano dane, aby przejrzeć ustawioną** kolumnę. Po zakończeniu przetwarzania zestawu przeglądów kliknij kartę **Zestawy przeglądów** w tym przypadku, a następnie kliknij zestaw przeglądów, aby rozpocząć proces filtrowania, przeglądania, tagowania i eksportowania danych w zestawie przeglądów.

## <a name="define-options-to-scope-your-collection-for-review"></a>Definiowanie opcji zakresu kolekcji do przeglądu

Po dodaniu zawartości wyszukiwania do istniejącego lub nowego zestawu przeglądów dostępne są następujące opcje zbierania zawartości do przeglądu:

- **Dołącz wersje z SharePoint (beta)**: użyj tej opcji, aby włączyć kolekcję wszystkich wersji dokumentu SharePoint zgodnie z limitami wersji i parametrami wyszukiwania kolekcji. Wybranie tej opcji znacznie zwiększy rozmiar elementów dodanych do zestawu przeglądów.

- **Opcje pobierania konwersacji**: elementy dodane do zestawu przeglądów są włączone dla konwersacji wątkowych, aby ułatwić przeglądanie zawartości w kontekście konwersacji tam iz powrotem. Aby uzyskać więcej informacji, zobacz [Przeglądanie konwersacji w usłudze eDiscovery (Premium)](conversation-review-sets.md).

- **Włącz pobieranie dla nowoczesnych załączników**: użyj tej opcji, aby uwzględnić nowoczesne załączniki lub połączone pliki w kolekcji w celu dalszego przeglądu. Aby uzyskać więcej informacji na temat właściwości z możliwością wyszukiwania związanych z nowoczesnymi załącznikami, zobacz [Pola metadanych dokumentu w obszarze eDiscovery (Premium)](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="add-a-sample-to-a-review-set"></a>Dodawanie przykładu do zestawu przeglądów

Jeśli chcesz dokładniej zweryfikować wyniki wyszukiwania przed dodaniem ich wszystkich do zestawu przeglądów, możesz dodać próbkę wyników wyszukiwania do zestawu przeglądów zamiast dodawać wszystko.

Aby dodać przykład do zestawu przeglądów, kliknij wyszukiwanie na karcie **Wyszukiwania** i kliknij pozycję **Przykład** na stronie wysuwanej. Na stronie **Parametry próbkowania** wybierz jedną z następujących opcji:

- **Procent poziomu ufności** i **procent interwału ufności** — elementy dodane do zestawu przeglądów będą określane przez ustawione parametry statystyczne. Jeśli zwykle używasz poziomu ufności i interwału podczas próbkowania wyników, określ je w polach listy rozwijanej. W przeciwnym razie użyj ustawień domyślnych.

- **Procent próbki losowej** — elementy dodane do zestawu przeglądów są oparte na losowym wyborze określonej wartości procentowej całkowitej liczby elementów zwróconych przez wyszukiwanie.

Po wybraniu i skonfigurowaniu jednej z poprzednich opcji wybierz zestaw przeglądów, aby dodać przykład, a następnie kliknij pozycję **Wyślij**. Ponownie możesz śledzić postęp na karcie **Zadania** lub na karcie **Wyszukiwania** , monitorując stan w kolumnie **Dodano dane, aby przejrzeć ustawioną** kolumnę.

## <a name="optical-character-recognition"></a>Optyczne rozpoznawanie znaków

Po dodaniu wyników wyszukiwania do zestawu przeglądów funkcja optycznego rozpoznawania znaków (OCR) w funkcji eDiscovery (Premium) automatycznie wyodrębnia tekst z obrazów i zawiera tekst obrazu z danymi dodanymi do zestawu przeglądów. Wyodrębniony tekst można wyświetlić w przeglądarce Tekst wybranego pliku obrazu w zestawie przeglądów. Dzięki temu można przeprowadzać dalsze przeglądy i analizy tekstu na obrazach. Funkcja OCR jest obsługiwana w przypadku luźnych plików, załączników wiadomości e-mail i obrazów osadzonych. Aby uzyskać listę formatów plików obrazów obsługiwanych w usłudze OCR, zobacz [Obsługiwane typy plików w funkcji zbierania elektronicznych materiałów dowodowych (Premium)](supported-filetypes-ediscovery20.md#image).

Musisz włączyć funkcję OCR dla każdego przypadku utworzonego w środowisku eDiscovery (Premium). Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wyszukiwania i analizy](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
