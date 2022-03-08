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
ms.openlocfilehash: 9b3171a0bcd30ec448d23a4b94a227aff9a9fb34
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320917"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Testowanie dokładnego dopasowania danych do typu informacji poufnych

Po utworzeniu dokładnego dopasowania danych (EDM) do typu informacji poufnych (SIT) i po upływie godziny od sprawdzenia, czy tabela informacji poufnych zakończyła przekazywanie i indeksowanie, możesz sprawdzić, czy wykrywa informacje, które chcesz wykryć, przy użyciu funkcji testowej w sekcji typów informacji poufnych w Centrum zgodności.
 
>[! UWAGA:] Propagowanie zmian w już utworzonym programie EDM SIT może trochę potrwać w całym systemie. Jeśli w typie informacji poufnych usługi EDM są zmiany dotyczące rozwiązywania problemów z wykrywaniem, przed użyciem funkcji testowej należy zaczekać co najmniej godzinę na ich wprowadzenie w celu weryfikacji ich wpływu.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Testowanie swojego konta EDM SIT w Centrum zgodności

1. Otwórz **Centrum zgodności** KlasyfikacjadanychUniące  >  > **typy informacji.**

2. Wybierz pozycję EDM SIT z listy, a następnie wybierz **pozycję Test w** okienku wysuwu. Ta opcja jest dostępna tylko w przypadku typów informacji poufnych.
 
3. Upload element zawierający dane, które chcesz wykryć. Na przykład utwórz element zawierający podzbiór wierszy w tabeli informacji poufnych. Jeśli w schemacie została użyta funkcja dopasowania konfigurowalna do zdefiniowania zignorowanych ograniczników, upewnij się, że element zawiera przykłady z tymi ogranicznikami i bez nich.

4. Po przesłaniu i zeskanowaniu pliku sprawdź, czy jego dopasowania są w Twoim systemie EDM SIT.

5. Jeśli funkcja **Test** w funkcji SIT wykryje dopasowanie, sprawdź, czy nie przycina go lub nie wyodrębnia go niepoprawnie. Na przykład wyodrębniając tylko ciąg podrzędny pełnego ciągu, który powinien zostać wykryć, lub wybierając tylko pierwszy wyraz w ciągu wielosłowowym, albo uwzględniając dodatkowe symbole lub znaki w wyodrębniania. Aby [uzyskać informacje o języku wyrażeń](/dotnet/standard/base-types/regular-expression-language-quick-reference) regularnych, zobacz Język wyrażeń regularnych — podręczny przewodnik. 

5. Możesz też użyć następującego polecenia cmdlet programu PowerShell:

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 W przypadku tworzenia lub edytowania typu informacji poufnych w programie EDM lub podstawowej wersji sit, na której jest oparty typ EDM, cała nowa zawartość i zawartość zmodyfikowana po zmianach w typach informacji poufnych zostanie przeszukana w przypadku tekstu, który pasuje do nowych definicji, ale wcześniejsza zawartość nie zostanie przeszukana do czasu jej zmodyfikowania lub ponownego indeksowania. 

Aby wymusić ponowne przeszukiwanie istniejącej zawartości w witrynie lub bibliotece programu SharePoint albo w bibliotece albo w programie OneDrive, postępuj zgodnie z instrukcjami w te sposób: Ręczne żądanie przeszukiwania i [ponownego](/sharepoint/crawl-site-content) indeksowania witryny, biblioteki lub listy.

## <a name="test-your-edm-sit-in-mip-policies"></a>Testowanie zasad EDM SIT w programie MIP

Dzięki zasadom można sprawdzić, gdzie jest używany program EDM SIT i jak dokładna jest ona w produkcji:

1. Utwórz zasady [automatycznego oznaczania i](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) uruchom je w omówienie **symulacyjnej.**

1. Dodaj zawartość, która wyzwoli usługę EDM SIT, oraz zawartość, która nie będzie wyzwalać usługi EDM SIT, do lokalizacji, która jest monitorowana przez zasady.

1. Otwieranie karty **Elementy do przejrzenia** w celu sprawdzenia dopasowania.

1. Dostosuj zasady zgodnie z potrzebami. 

Gdy wyniki testów i dostosowywania będą zadowałe, niestandardowy sit oparty na funkcji EDM będzie gotowy do użycia w zasadach ochrony informacji, takich jak:

- [Zasady DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Zasady automatycznego oznaczania etykiet](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Cloud App Security dotyczące plików](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Porady dotyczące rozwiązywania problemów

Jeśli nie znajdziesz żadnych dopasowania, oto kilka porad dotyczących rozwiązywania problemów.


|Problem  |Porada w zakresie rozwiązywania problemów  |
|---------|---------|
|Nie znaleziono żadnych dopasowania     |  Upewnij się, że poufne dane zostały przekazane poprawnie za pomocą poleceń w tece Skrót i przekaż tabelę źródła informacji poufnych, aby dokładnie dopasować dane [do typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|
|Nie znaleziono żadnych dopasowania   | Przetestuj usługę SIT używaną podczas konfigurowania podstawowego elementu w każdym z wzorców. Potwierdzi to, że sit jest w stanie dopasować przykłady w pozycji. Używanie nieprawidłowo zdefiniowanej funkcji SIT jako elementu klasyfikacji typu informacji poufnej usługi EDM jest najczęstszą przyczyną błędów wykrywania w funkcji EDM.         |
|Pozycja SIT wybrana dla podstawowego elementu typu EDM nie znajduje dopasowania w elemencie lub znajduje mniej dopasowań niż oczekiwano    |  Sprawdź, czy obsługuje separatory i ograniczniki w zawartości. Pamiętaj, aby w schemacie uwzględnić zignorowane ograniczniki zdefiniowane.       |
|Element podstawowy SIT znajduje dopasowania w elemencie, ale nie ma w tym przypadku pozycji EDM SIT.     | - Sprawdź, czy instrukcje REGEX nie mają rozpoczynać lub kończyć przechwytywania ogranicznika whitespace, takiego jak /s. Odstępy nie będą zgodne z wartością skrótu w tabeli danych. Zamiast tego użyj ogranicznika słownego, takiego jak /b. </br> - Sprawdź instrukcje REGEX, aby upewnić się, że przechwycą one cały ciąg, który chcesz przechwycić, a nie tylko ciąg podrzędny. Na przykład ten wzorzec dla adresów e-mail [a-zA-Z]{30}@[a-zA-Z]{20}". a-zA-Z]{2,3} *będzie* odpowiadać user@contoso.com i *user@contoso.co.jp*.  |
|System EDM SIT z elementami podstawowymi i bez zdefiniowanych elementów pomocniczych wykrywa elementy, ale nie wykrywa ani nie wykrywa mniej niż oczekiwano, gdy są wymagane elementy podstawowe i pomocnicze.  | Upewnij się, że wartości pomocnicze składają się z jednego wyrazu lub ciągu, który nie zawiera spacji, lub użyj instrukcji REGEX, które wykryją ciągi wielosłowne. Na przykład \b[A-Z][a-z]{1,25}([ -][A-Z][a-z]{1,25}){0,4}\b, która będzie odpowiadać dowolnej sekwencji od jednego do pięciu następujących po sobie wyrazów zaczynanych od wielkie litery. Należy użyć tej funkcji SIT jako elementu klasyfikacji dla dodatkowych warunków dowodowych w pliku XML typu informacji poufnych funkcji EDM. Zobacz [Ręczne tworzenie pakietu reguł](sit-get-started-exact-data-match-create-rule-package.md#create-a-rule-package-manually)|
|Funkcja testowa SIT w ogóle nie wykrywa żadnych wyników.   | Sprawdź, czy wybrany program SIT uwzględnia wymagania dotyczące dodatkowych słów kluczowych lub innych reguł poprawności. Aby uzyskać informacje na temat wbudowanych typów informacji[](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions), zobacz Definicje jednostek typu informacji poufnych w celu sprawdzenia, jakie minimalne wymagania muszą spełniać poszczególne typy danych.        |
|Funkcja Testuj działa, ale SharePoint lub OneDrive nie są wykrywane w zasadach DLP ani w przypadku automatycznego oznaczania etykiet     | Sprawdź, czy dokumenty, których oczekujesz, są wyświetlane w Eksploratorze zawartości. Jeśli ich tam nie ma, pamiętaj, że jako dopasowania będzie pokazywana tylko zawartość utworzona po zmianie typu informacji poufnych. Aby wyświetlić istniejące wcześniej elementy, należy ponownie odszyfrować witryny i biblioteki. Zobacz [Ręczne żądanie przeszukiwania i ponownego](/sharepoint/crawl-site-content) indeksowania witryny, biblioteki lub listy, aby uzyskać szczegółowe informacje na temat ponownego SharePoint i OneDrive.        |
|Reguły DLP lub automatyczne oznaczanie wymagające wielu dopasowania nie powodują wyzwolenia     |Sprawdź, czy są spełnione wymagania dotyczące sąsiedztwa zarówno dla typu danych EDM, jak i podstawowych typów informacji poufnych. Jeśli na przykład maksymalna odległość między elementem podstawowym a obsługującymi słowa kluczowe wynosi 300 znaków, ale słowa kluczowe znajdują się tylko w pierwszym wierszu długiej tabeli, tylko kilka pierwszych wierszy pasujących wartości prawdopodobnie będzie spełniało wymagania dotyczące odległości. Zmodyfikuj definicje funkcji SIT, aby obsługiwać bardziej luźne reguły sąsiedztwa, lub użyj dowolnego miejsca w dokumencie, aby uzyskać dodatkowe informacje na temat warunków dowodowych.         |
|Wykrywanie typu EDM jest niespójne lub błędne     |Sprawdź, czy typ informacji poufnych, który został użyty jako podstawa elementu podstawowego w typie EDM, nie wykrywa niepotrzebnej zawartości. Korzystanie z funkcji SIT w celu dopasowania zbyt dużej ilości niepowiązanej zawartości, na przykład dowolnego wyrazu, dowolnej liczby lub wszystkich adresów e-mail, może spowodować, że usługa nasyci i zignoruje odpowiednie dopasowania. Sprawdź liczbę fragmentów zawartości, które są zgodne z typem poufnym użytym dla podstawowych elementów w Eksploratorze zawartości. </br> Aby oszacować, czy program SIT dopasowywuje zbyt dużo zawartości: </br> — Dzielenie liczby elementów zawartości w Eksploratorze zawartości przez liczbę dni od utworzenia typu poufnego. </br> - Jeśli liczba dopasowania dziennie należy do kilkuset tysięcy lub milionów, może to oznaczać, że podstawowy numer SIT jest zbyt szeroki. Aby [uzyskać zalecenia](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) i najlepsze rozwiązania dotyczące wybierania odpowiedniego typu informacji poufnych dla typu danych EDM, zobacz Informacje o dokładnym dopasowaniu danych na podstawie typów informacji poufnych.         |