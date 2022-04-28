---
title: Konfigurowanie ustawień wyszukiwania i analizy — eDiscovery (Premium)
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
ms.custom: seo-marvel-mar2020
description: Skonfiguruj ustawienia zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium), które mają zastosowanie do wszystkich zestawów przeglądów w danym przypadku. Obejmuje to ustawienia analizy i optycznego rozpoznawania znaków.
ms.openlocfilehash: 0ef76833d18b44a2a1c39db41f7d6fa31f99293e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097145"
---
# <a name="configure-search-and-analytics-settings-in-ediscovery-premium"></a>Konfigurowanie ustawień wyszukiwania i analizy w usłudze eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Możesz skonfigurować ustawienia dla każdego przypadku zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium), aby kontrolować następujące funkcje.

- Niemal duplikaty i wątki wiadomości e-mail

- Motywy

- Autogenerowane zapytanie zestawu przeglądów

- Ignoruj tekst

- Optyczne rozpoznawanie znaków

Aby skonfigurować ustawienia wyszukiwania i analizy dla przypadku:

1. Na stronie **eDiscovery (Premium)** wybierz przypadek.

2. Na karcie **Ustawienia** w obszarze **Analiza & wyszukiwania** kliknij pozycję **Wybierz**.

   Zostanie wyświetlona strona ustawień przypadku. Te ustawienia są stosowane do wszystkich zestawów przeglądów w przypadku.

   ![Skonfiguruj ustawienia analizy i wyszukiwania dla przypadku zbierania elektronicznych materiałów dowodowych (Premium).](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Niemal duplikaty i wątki wiadomości e-mail

W tej sekcji można ustawić parametry wykrywania duplikatów, wykrywania zbliżonego do duplikatów i wątków wiadomości e-mail. Aby uzyskać więcej informacji, zobacz [Wykrywanie zduplikowanych zbliżeń](near-duplicate-detection-in-advanced-ediscovery.md) i [Wątki wiadomości e-mail](email-threading-in-advanced-ediscovery.md).

- **W pobliżu duplikatów/wątków wiadomości e-mail:** Po włączeniu wykrywanie duplikatów, wykrywanie niemal duplikatów i wątki wiadomości e-mail są uwzględniane w przepływie pracy podczas uruchamiania analizy danych w zestawie przeglądów.

- **Próg podobieństwa dokumentu i poczty e-mail:** Jeśli poziom podobieństwa dla dwóch dokumentów przekracza próg, oba dokumenty są umieszczane w tym samym zestawie zbliżonym do zduplikowanego.

- **Minimalna/maksymalna liczba wyrazów:** Te ustawienia określają, że w pobliżu duplikatów i analizy wątków wiadomości e-mail są wykonywane tylko w dokumentach, które mają co najmniej minimalną liczbę wyrazów i co najwyżej maksymalną liczbę wyrazów.

## <a name="themes"></a>Motywy

W tej sekcji można ustawić parametry motywów. Aby uzyskać więcej informacji, zobacz [Tematy](themes-in-advanced-ediscovery.md).

- **Tematy:** Po włączeniu klastrowanie motywów jest wykonywane w ramach przepływu pracy podczas uruchamiania analizy danych w zestawie przeglądów.

- **Maksymalna liczba motywów:** Określa maksymalną liczbę motywów, które mogą być generowane podczas uruchamiania analizy danych w zestawie przeglądów.

- **Uwzględnij liczby w motywach:** Po włączeniu podczas generowania motywów są uwzględniane liczby (identyfikujące motyw). 

- **Dynamicznie dostosuj maksymalną liczbę motywów:** W niektórych sytuacjach w zestawie przeglądowym może być za mało dokumentów, aby wygenerować żądaną liczbę motywów. Po włączeniu tego ustawienia funkcja eDiscovery (Premium) dostosowuje maksymalną liczbę motywów dynamicznie, zamiast próbować wymusić maksymalną liczbę motywów.

## <a name="review-set-query"></a>Przejrzyj zapytanie zestawu

Jeśli zaznaczysz pole wyboru **Automatycznie utwórz wyszukiwanie zapisane na potrzeby przeglądu po analizie**, funkcja zbierania elektronicznych materiałów dowodowych (Premium) automatycznie generuje zapytanie zestawu przeglądów o nazwie **For Review.** 

![Automatycznie wygenerowane zapytanie For Review.](../media/AeDForReviewQuery.png)

To zapytanie zasadniczo filtruje zduplikowane elementy z zestawu przeglądów. Umożliwia to przeglądanie unikatowych elementów w zestawie przeglądów. To zapytanie jest tworzone tylko wtedy, gdy uruchamiasz analizę dla zestawu przeglądów w tym przypadku. Aby uzyskać więcej informacji na temat zapytań zestawu przeglądów, zobacz [Wykonywanie zapytań dotyczących danych w zestawie przeglądów](review-set-search.md).

## <a name="ignore-text"></a>Ignoruj tekst

Istnieją sytuacje, w których określony tekst obniży jakość analizy, na przykład długie zastrzeżenia dodawane do wiadomości e-mail niezależnie od zawartości wiadomości e-mail. Jeśli znasz tekst, który powinien zostać zignorowany, możesz wykluczyć go z analizy, określając ciąg tekstowy i funkcje analizy (niemal duplikaty, wątki wiadomości e-mail, motywy i istotność), dla których tekst powinien zostać wykluczony. Obsługiwane jest również używanie wyrażeń regularnych (RegEx) jako ignorowanego tekstu.

## <a name="optical-character-recognition-ocr"></a>Optyczne rozpoznawanie znaków (OCR)

Po włączeniu tego ustawienia przetwarzanie OCR będzie uruchamiane w plikach obrazów. Przetwarzanie OCR jest uruchamiane w następujących sytuacjach:

- Gdy opiekunowie i [źródła danych niebędących opiekunami](non-custodial-data-sources.md) są dodawani do sprawy. Gdy funkcja OCR zostanie zastosowana do plików obrazów, tekst w tych plikach będzie można wyszukiwać podczas kolekcji. Przetwarzanie OCR jest wykonywane podczas zaawansowanego procesu [indeksowania](indexing-custodian-data.md) . Funkcja OCR jest uruchamiana tylko w przypadku elementów przetwarzanych podczas indeksowania zaawansowanego. Jeśli na przykład podczas indeksowania zaawansowanego jest przetwarzany duży plik PDF częściowo indeksowany lub z innymi błędami indeksowania, zostanie zastosowany również protokół OCR. Innymi słowy przetwarzanie OCR odbywa się tylko w przypadku plików, które są ponownie indeksowane podczas zaawansowanego procesu indeksowania. Oznacza to, że mogą wystąpić sytuacje, w których opiekunowie są dodawani do sprawy, ale niektóre załączniki wiadomości e-mail nie zostaną przetworzone dla usługi OCR, ponieważ te pliki nie są przetwarzane podczas zaawansowanego indeksowania.

- Gdy zawartość z innych źródeł danych (które nie są skojarzone z opiekunem i dodawane do sprawy w źródle danych bez nadzoru) jest dodawana do zestawu przeglądów.

Po dodaniu danych do zestawu przeglądów można przeglądać, wyszukiwać, oznaczać i analizować tekst obrazu. Wyodrębniony tekst można wyświetlić w przeglądarce Tekst wybranego pliku obrazu w zestawie przeglądów. Więcej informacji można znaleźć w następujących artykułach:

- [Zaawansowane indeksowanie danych opiekuna](indexing-custodian-data.md)

- [Dodawanie wyników wyszukiwania do zestawu przeglądów](add-data-to-review-set.md#optical-character-recognition)

- [Obsługiwane typy plików obrazów](supported-filetypes-ediscovery20.md#image)
