---
title: Konfigurowanie ustawień wyszukiwania i analizy — Advanced eDiscovery
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
ms.custom: seo-marvel-mar2020
description: Skonfiguruj Advanced eDiscovery, które mają zastosowanie do wszystkich zestawie recenzji w przypadku. Dotyczy to również ustawień analizy i optycznego rozpoznawania znaków.
ms.openlocfilehash: 65175950a430dd6b43cac207e16a17cf02d1bbbf
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983174"
---
# <a name="configure-search-and-analytics-settings-in-advanced-ediscovery"></a>Konfigurowanie ustawień wyszukiwania i analizy w aplikacji Advanced eDiscovery

Możesz skonfigurować ustawienia dla poszczególnych Advanced eDiscovery przypadku, aby kontrolować następujące funkcje.

- Niemal duplikaty i wątki wiadomości e-mail

- Motywy

- Automatycznie wygenerowane zapytanie zestawu recenzji

- Ignoruj tekst

- Optyczne rozpoznawanie znaków

Aby skonfigurować ustawienia wyszukiwania i analizy dla sprawy:

1. Na **Advanced eDiscovery** wybierz sprawę.

2. Na karcie **Ustawienia** w obszarze **Analiza & kliknij** pozycję **Wybierz**.

   Zostanie wyświetlona strona ustawień sprawy. Te ustawienia są stosowane do wszystkich zestawów recenzji w przypadku.

   ![Konfigurowanie ustawień analizy i wyszukiwania dla Advanced eDiscovery przypadku.](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Niemal duplikaty i wątki wiadomości e-mail

W tej sekcji możesz ustawić parametry dotyczące wykrywania duplikatów, niemal automatycznego wykrywania duplikatów oraz wątków wiadomości e-mail. Aby uzyskać więcej informacji, zobacz [Wykrywanie w pobliżu zduplikowanych plików](near-duplicate-detection-in-advanced-ediscovery.md) i Wątkowanie [wiadomości e-mail](email-threading-in-advanced-ediscovery.md).

- **Blisko duplikatów/wątków wiadomości e-mail:** Po włączeniu wykrywania duplikatów, niemal automatycznego wykrywania duplikatów i wątków wiadomości e-mail podczas uruchamiania analizy danych w zestawie recenzji w ramach przepływu pracy są uwzględniane funkcje wykrywania duplikatów i wątków wiadomości e-mail.

- **Próg podobieństwa dokumentów i wiadomości e-mail:** Jeśli poziom podobieństwa dwóch dokumentów przekracza próg, oba dokumenty są umieszczane w tym samym zestawie niemal duplikatów.

- **Minimalna/maksymalna liczba wyrazów:** Te ustawienia określają, że niemal duplikaty i analiza wątków wiadomości e-mail są wykonywane tylko w przypadku dokumentów, które mają co najmniej najmniej minimalną liczbę wyrazów i co najwyżej maksymalną liczbę wyrazów.

## <a name="themes"></a>Motywy

W tej sekcji możesz ustawić parametry motywów. Aby uzyskać więcej informacji, zobacz [Motywy](themes-in-advanced-ediscovery.md).

- **Motywy:** Po włączeniu grupowanie motywów jest wykonywane jako część przepływu pracy po uruchomieniu analizy danych w zestawie recenzji.

- **Maksymalna liczba motywów:** Określa maksymalną liczbę motywów, które mogą być generowane podczas uruchamiania analizy danych w zestawie recenzji.

- **Uwzględnianie liczb w motywach:** Po włączeniu tej aplikacji podczas generowania motywów są uwzględniane liczby (identyfikujące motyw). 

- **Dynamicznie dopasuj maksymalną liczbę motywów:** W niektórych sytuacjach może być za mało dokumentów w zestawie recenzji, aby uzyskać odpowiednią liczbę motywów. Gdy to ustawienie jest włączone, program Advanced eDiscovery dynamicznie dostosowuje maksymalną liczbę motywów, zamiast próbować wymusić maksymalną liczbę motywów.

## <a name="review-set-query"></a>Zapytanie zestawu recenzji

Jeśli zaznaczysz pole wyboru **Automatycznie utwórz dla recenzji** zapisane wyszukiwanie po analizie, Advanced eDiscovery automatyczniegeneruje zapytanie zestawu recenzji o **nazwie Do przeglądu.** 

![Zapytanie automatycznie wygenerowane przez funkcję Do przeglądu.](../media/AeDForReviewQuery.png)

To zapytanie w zasadzie odfiltrowuje zduplikowane elementy z zestawu recenzji. Umożliwia to przeglądanie unikatowych elementów w zestawie recenzji. To zapytanie jest tworzone tylko w przypadku uruchomienia analizy zestawu recenzji w tym przypadku. Aby uzyskać więcej informacji na temat zapytań zestawu recenzji, zobacz [Kwerenda danych w zestawie recenzji](review-set-search.md).

## <a name="ignore-text"></a>Ignoruj tekst

Są sytuacje, w których określony tekst będzie zmniejszać jakość analiz, na przykład długie zastrzeżenia dodawane do wiadomości e-mail niezależnie od ich treści. Jeśli wiesz, że tekst, który powinien być ignorowany, możesz go wykluczyć z analizy, określając ciąg tekstowy i funkcje analizy (Niemal duplikaty, Wątki wiadomości e-mail, Motywy i Istotność), dla których należy wykluczyć ten tekst. Obsługiwane jest również używanie wyrażeń regularnych (RegEx) jako ignorowanego tekstu.

## <a name="optical-character-recognition-ocr"></a>Optyczne rozpoznawanie znaków (OCR)

Gdy to ustawienie jest włączone, przetwarzanie OCR będzie uruchamiane w plikach obrazów. Przetwarzanie OCR jest uruchamiane w następujących sytuacjach:

- W przypadku przechowywania oraz [źródeł](non-custodial-data-sources.md) danych niedychychowych są dodawane do sprawy. Po zastosowaniu funkcji OCR do plików obrazów tekst w tych plikach będzie można wyszukiwać w kolekcji. Przetwarzanie OCR jest wykonywane w trakcie [procesu indeksowania zaawansowanego](indexing-custodian-data.md) . Funkcja OCR jest uruchamiana tylko dla elementów, które są przetwarzane podczas indeksowania zaawansowanego. Jeśli na przykład duży plik PDF, który jest częściowo indeksowany lub zawierał inne błędy indeksowania, zostanie przetworzony podczas indeksowania zaawansowanego, do pliku zostanie również zastosowany OCR. Innymi słowy przetwarzanie OCR odbywa się tylko w przypadku plików ponownie zindeksowanych w trakcie procesu indeksowania zaawansowanego. Oznacza to, że niektóre załączniki wiadomości e-mail są dodawane do sprawy w pewnych sytuacjach, ale niektóre załączniki wiadomości e-mail nie są przetwarzane na poziomie funkcji OCR, ponieważ te pliki nie są przetwarzane podczas indeksowania zaawansowanego.

- W przypadku dodania zawartości z innych źródeł danych (które nie są skojarzone z obiektem do przechowywania i dodane do sprawy w źródle danych bez przechowywania) do zestawu recenzji.

Po dodaniu danych do zestawu recenzji można przeglądać, wyszukiwać, tagować i analizować tekst obrazu. Wyodrębniony tekst można wyświetlić w przeglądarce tekstu wybranego pliku obrazu w zestawie recenzji. Więcej informacji można znaleźć w następujących artykułach:

- [Zaawansowane indeksowanie danych przetwarzających](indexing-custodian-data.md)

- [Dodawanie wyników wyszukiwania do zestawu recenzji](add-data-to-review-set.md#optical-character-recognition)

- [Obsługiwane typy plików obrazów](supported-filetypes-ediscovery20.md#image)
