---
title: Testowanie dokładnego dopasowania danych do typu informacji poufnych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: konfigurowanie usług
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3030a97e3ed80524d2170e74b3d35f897b6ed74c
ms.sourcegitcommit: 8410a49995a084e4cc9b3f7286c8d506b7a85d79
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2021
ms.locfileid: "62999363"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Testowanie dokładnego dopasowania danych do typu informacji poufnych

Po utworzeniu dokładnego dopasowania danych (EDM) do typu informacji poufnych (SIT) i po upływie godziny od sprawdzenia, czy tabela informacji poufnych zakończyła przekazywanie i indeksowanie, możesz sprawdzić, czy wykrywa informacje, które chcesz wykryć, przy użyciu funkcji testowej w sekcji typów informacji poufnych w Centrum zgodności.
 
>[! UWAGA:] Propagowanie zmian w już utworzonym programie EDM SIT może trochę potrwać w całym systemie. Jeśli w typie informacji poufnych usługi EDM są zmiany dotyczące rozwiązywania problemów z wykrywaniem, przed użyciem funkcji testowej należy zaczekać co najmniej godzinę na ich wprowadzenie w celu weryfikacji ich wpływu.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Testowanie swojego konta EDM SIT w Centrum zgodności

1. Otwórz **Centrum zgodności** KlasyfikacjadanychUniące  >  > **typy informacji.**

2. Wybierz pozycję EDM SIT z listy, a następnie wybierz **pozycję Test w** okienku wysuwu. Ta opcja jest dostępna tylko w programie for SIT w przypadku typów informacji poufnych.
 
3. Upload element zawierający dane, które chcesz wykryć. Na przykład utwórz element zawierający podzbiór wierszy w tabeli informacji poufnych. Jeśli w schemacie została użyta funkcja dopasowania konfigurowalna do zdefiniowania zignorowanych ograniczników, upewnij się, że element zawiera przykłady z tymi ogranicznikami i bez nich.

4. Po przesłaniu i zeskanowaniu pliku sprawdź, czy jego dopasowania są w Twoim systemie EDM SIT.

5. Jeśli funkcja **Test** w funkcji SIT wykryje dopasowanie, sprawdź, czy nie jest ona obcinana lub wyodrębniana niepoprawnie. Na przykład wyodrębniając tylko ciąg podrzędny pełnego ciągu, który może wykryć, lub wybierając tylko pierwszy wyraz w ciągu wielosłowowym, lub uwzględniając dodatkowe symbole lub znaki w wyodrębniania. Aby [uzyskać informacje o języku wyrażeń](/dotnet/standard/base-types/regular-expression-language-quick-reference) regularnych, zobacz Język wyrażeń regularnych — podręczny przewodnik. 

5. Możesz też użyć następującego polecenia cmdlet programu PowerShell:

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 W przypadku tworzenia lub edytowania typu informacji poufnych w programie EDM lub podstawowej wersji sit, na której jest oparty typ EDM, cała nowa zawartość i zawartość zmodyfikowana po zmianach w typach informacji poufnych zostanie przeszukana w przypadku tekstu, który pasuje do nowych definicji, ale wcześniejsza zawartość nie zostanie przeszukana do czasu jej zmodyfikowania lub ponownego indeksowania. 

Aby wymusić ponowne przeszukiwanie istniejącej zawartości w witrynie lub bibliotece programu SharePoint albo w bibliotece albo w programie OneDrive, postępuj zgodnie z instrukcjami w tece Ręczne żądanie przeszukiwania i ponownego indeksowania witryny[,](/sharepoint/crawl-site-content) biblioteki lub listy.

## <a name="test-your-edm-sit-in-mip-policies"></a>Testowanie zasad EDM SIT w programie MIP

Dzięki zasadom można sprawdzić, gdzie jest używany program EDM SIT i jak dokładna jest ona w produkcji:

1. Utwórz zasady [automatycznego oznaczania i](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) uruchom je w omówienie **symulacyjnej.**

1. Dodaj zawartość, która wyzwoli usługę EDM SIT, oraz zawartość, która nie będzie wyzwalać usługi EDM SIT, do lokalizacji, która jest monitorowana przez zasady.

1. Otwieranie karty **Elementy do przejrzenia** w celu sprawdzenia dopasowania.

1. Dostosuj zasady zgodnie z potrzebami. 

Gdy wyniki testów i dostosowywania będą zadowałe, niestandardowy sit oparty na funkcji EDM będzie gotowy do użycia w zasadach ochrony informacji, takich jak:

- [Zasady DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Zasady automatycznego schowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Cloud App Security dotyczące plików](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Porady dotyczące rozwiązywania problemów

Jeśli nie możesz znaleźć żadnych dopasowania, spróbuj wykonać następujące czynności:

- Upewnij się, że poufne dane zostały przekazane poprawnie za pomocą poleceń wyjaśnionych w wytycznych dotyczących przekazywania poufnych danych za pomocą narzędzia EDM.

- Sprawdź, czy przykłady wprowadzone w pozycji znajdują się w tabeli informacji poufnych i czy ignorowane ograniczniki są prawidłowe.

- Przetestuj usługę SIT używaną podczas konfigurowania podstawowego elementu w każdym z wzorców. Potwierdzi to, że sit jest w stanie dopasować przykłady w pozycji. Używanie nieprawidłowo zdefiniowanej funkcji SIT jako elementu klasyfikacji typu informacji poufnej usługi EDM jest najczęstszą przyczyną błędów wykrywania w funkcji EDM. 

- Jeśli pozycja SIT wybrana dla elementu podstawowego typu EDM nie znajdzie dopasowania w elemencie lub znajdzie mniej dopasowań, niż oczekiwano, sprawdź, czy obsługuje separatory i ograniczniki w zawartości. Pamiętaj, aby w schemacie uwzględnić zignorowane ograniczniki zdefiniowane.

- Jeśli funkcja Test w ogóle nie wykrywa żadnej zawartości, sprawdź, czy wybrana funkcja SIT nie zawiera wymagań dotyczących dodatkowych słów kluczowych lub innych reguł poprawności. Aby uzyskać informacje na temat wbudowanych typów informacji[](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions), zobacz Definicje jednostek typu informacji poufnych w celu sprawdzenia, jakie minimalne wymagania muszą spełniać poszczególne typy danych.

- Jeśli funkcja Testuj działa, ale elementy SharePoint lub OneDrive nie są wykrywane w zasadach DLP ani w zasadach autolabeli, sprawdź, czy dokumenty, których oczekujesz, są wyświetlane w Eksploratorze zawartości. Jeśli ich tam nie ma, pamiętaj, że dopasowania będą wyświetlane tylko w zawartości utworzonej po zmianie typu informacji poufnych. Aby wyświetlić istniejące elementy, należy ponownie przeszukać witryny i biblioteki. Zobacz [Ręczne żądanie przeszukiwania i ponownego](/sharepoint/crawl-site-content) indeksowania witryny, biblioteki lub listy, aby uzyskać szczegółowe informacje na temat ponownego przeszukiwania SharePoint i OneDrive. 

- Jeśli nie są wyzwalane reguły DLP lub automatyczne oznaczanie, które wymagają wielu dopasowania, sprawdź, czy są spełnione wymagania dotyczące odległości zarówno dla Twojego typu usług EDM, jak i podstawowych typów informacji poufnych. Jeśli na przykład maksymalna odległość między elementem podstawowym a obsługującymi słowa kluczowe wynosi 300 znaków, ale słowa kluczowe znajdują się tylko w pierwszym wierszu długiej tabeli, tylko kilka pierwszych wierszy pasujących wartości prawdopodobnie będzie spełniało wymagania dotyczące odległości. Zmodyfikuj definicje funkcji SIT, aby obsługiwać bardziej luźne reguły sąsiedztwa, lub użyj dowolnego miejsca w dokumencie, aby uzyskać dodatkowe informacje na temat warunków dowodowych. 

- Jeśli wykrywanie typu EDM jest niespójne lub błędne, sprawdź, czy typ informacji poufnych, który został użyty jako podstawa elementu podstawowego w typie EDM, nie wykrywa niepotrzebnej zawartości. Korzystanie z funkcji SIT w celu dopasowania zbyt dużej ilości niepowiązanej zawartości, tak jak dowolnego wyrazu, dowolnej liczby, może spowodować, że usługa nasyci i zignoruje odpowiednie dopasowania. Sprawdź liczbę fragmentów zawartości, które są zgodne z typem poufnym użytym dla podstawowych elementów w Eksploratorze zawartości. Aby oszacować, czy program SIT dopasowywuje zbyt dużo zawartości:
    1. Dzielenie liczby elementów zawartości w Eksploratorze zawartości przez liczbę dni od utworzenia typu poufnego.
    2. Jeśli liczba dopasowania na dzień należy do kilkuset tysięcy lub milionów, może to oznaczać, że podstawowy numer SIT jest zbyt szeroki. Aby [uzyskać zalecenia](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) i najlepsze rozwiązania dotyczące wybierania odpowiedniego typu informacji poufnych dla typu danych EDM, zobacz Informacje o dokładnym dopasowaniu danych na podstawie typów informacji poufnych. 

- Potwierdź, że poufne dane zostały przekazane poprawnie za pomocą poleceń wyjaśnionych w skrótie i przekaż tabelę źródła informacji poufnych, aby dokładnie dopasować dane [do typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types).

- Jeśli pozycja SIT wybrana dla elementu podstawowego typu EDM nie znajduje dopasowania w elemencie lub znajduje mniej dopasowań, niż oczekiwano, sprawdź, czy obsługuje separatory i ograniczniki istniejące w zawartości. Pamiętaj, aby w schemacie uwzględnić zignorowane ograniczniki zdefiniowane. 

