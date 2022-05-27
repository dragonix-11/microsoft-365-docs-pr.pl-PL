---
title: Testuj dokładny typ informacji poufnych oparty na dopasowaniu danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: konfigurowanie usług
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5b2ae7e5d6e434cd5502373b04a055c6fb2fb4a9
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754239"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Testuj dokładny typ informacji poufnych oparty na dopasowaniu danych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po utworzeniu dokładnego typu informacji poufnych (EDM) i godzinie po sprawdzeniu, czy tabela informacji poufnych zakończyła przekazywanie i indeksowanie, można sprawdzić, czy wykryto informacje, które chcesz wykryć, za pomocą funkcji testowej w sekcji typy informacji poufnych w Centrum zgodności.
 
>[! UWAGA:] Propagowanie zmian w już utworzonym środowisku EDM SIT może zająć trochę czasu. Jeśli wprowadzasz zmiany w typie informacji poufnych EDM w celu rozwiązywania problemów z wykrywaniem, poczekaj co najmniej godzinę po wprowadzeniu tych zmian przed użyciem funkcji testowej w celu zweryfikowania ich wpływu.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Testowanie aplikacji EDM SIT w Centrum zgodności

1. Otwórz **centrum** >  zgodności **Typy informacji poufnych** **klasyfikacji** >  danych.

2. Wybierz z listy pozycję EDM SIT, a następnie wybierz pozycję **Testuj** w okienku wysuwanym. Ta opcja jest dostępna tylko w przypadku typów informacji poufnych.
 
3. Przekaż element zawierający dane, które chcesz wykryć. Na przykład utwórz element zawierający podzestaw wierszy w tabeli informacji poufnych. Jeśli w schemacie użyto konfigurowalnej funkcji dopasowania do definiowania ignorowanych ograniczników, upewnij się, że element zawiera przykłady z tymi ogranicznikami i bez nich.

4. Po przekazaniu i zeskanowaniu pliku sprawdź, czy nie ma dopasowań do interfejsu EDM SIT.

5. Jeśli funkcja **Test** w usłudze SIT wykryje dopasowanie, sprawdź, czy nie przycina jej ani nie wyodrębnia niepoprawnie. Na przykład przez wyodrębnienie tylko podciągu pełnego ciągu, który ma zostać wykryty, lub pobranie tylko pierwszego słowa w ciągu wielowyrazowym lub uwzględnienie dodatkowych symboli lub znaków w wyodrębnianiu. Zobacz [Język wyrażeń regularnych — szybkie odwołanie](/dotnet/standard/base-types/regular-expression-language-quick-reference) do odwołania do języka wyrażeń regularnych. 

5. Alternatywnie możesz użyć następującego polecenia cmdlet programu PowerShell:

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 Podczas tworzenia lub edytowania typu informacji poufnych EDM lub podstawowego interfejsu SIT, na którym jest oparty typ EDM, cała nowa zawartość i zawartość, które zostały zmodyfikowane po wprowadzeniu zmian w interfejsach SIC, zostaną przeszukane pod kątem tekstu zgodnego z nowymi definicjami, ale istniejąca wcześniej zawartość nie zostanie przeszukana, dopóki nie zostanie zmodyfikowana lub ponownie istniejąca. 

Aby wymusić ponowne przeszukiwanie istniejącej zawartości w witrynie lub bibliotece SharePoint lub w OneDrive, postępuj zgodnie z instrukcjami w [temacie Ręczne przeszukiwanie i ponowne indeksowanie lokacji, biblioteki lub listy](/sharepoint/crawl-site-content).

## <a name="test-your-edm-sit-with-information-protection-policies"></a>Testowanie aplikacji EDM SIT przy użyciu zasad ochrony informacji

Możesz zobaczyć, gdzie jest używane środowisko EDM SIT i jak dokładne jest w środowisku produkcyjnym, używając ich w zasadach:

1. Utwórz [zasady automatycznego etykietowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) i uruchom ją w **obszarze Omówienie symulacji**.

1. Dodaj zawartość, która wyzwoli interfejs EDM SIT, oraz zawartość, która nie wyzwoli EDM SIT, do lokalizacji monitorowanej przez zasady.

1. Otwórz kartę **Items to review (Elementy do przeglądu** ), aby sprawdzić dopasowania.

1. Dostosuj zasady odpowiednio do potrzeb. 

Gdy wyniki testowania i dostrajania będą zadowalające, niestandardowe środowisko SIT oparte na usłudze EDM będzie gotowe do użycia w zasadach ochrony informacji, takich jak:

- [Zasady DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Zasady automatycznego etykietowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Porady dotyczące rozwiązywania problemów

Jeśli nie znajdziesz żadnych dopasowań, oto kilka wskazówek dotyczących rozwiązywania problemów.

|Problem  |Porada dotycząca rozwiązywania problemów  |
|---------|---------|
|Nie znaleziono dopasowań     |  Upewnij się, że dane poufne zostały prawidłowo przekazane przy użyciu poleceń opisanych w artykule [Skrót i przekaż tabelę źródła informacji poufnych, aby uzyskać dokładne dane zgodne z typami informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|
|Nie znaleziono dopasowań   | Przetestuj interfejs SIT używany podczas konfigurowania elementu podstawowego w każdym z wzorców. Spowoduje to potwierdzenie, że usługa SIT jest w stanie dopasować przykłady w elemencie. Użycie nieprawidłowo zdefiniowanego interfejsu SIT jako elementu klasyfikacji typu informacji poufnych EDM jest najczęstszą przyczyną błędów wykrywania w usłudze EDM.         |
|Pozycja SIT wybrana dla elementu podstawowego w typie EDM nie znajduje dopasowania w elemencie lub znajduje mniej dopasowań niż oczekiwano    |  Sprawdź, czy obsługuje separatory i ograniczniki znajdujące się w zawartości. Pamiętaj, aby uwzględnić ignorowane ograniczniki zdefiniowane w schemacie.       |
|Podstawowy element SIT znajduje dopasowania w elemencie, ale EDM SIT nie.     | — Sprawdź instrukcje REGEX pod kątem uruchamiania lub kończenia ogranicznika przechwytywania białych znaków, takiego jak /s. Biały obszar nie będzie zgodny z wartością skrótu w tabeli danych. Zamiast tego użyj ogranicznika wyrazów, takiego jak /b. </br> — Sprawdź instrukcje REGEX, aby upewnić się, że przechwytują cały ciąg, który chcesz przechwycić, a nie tylko podciąg. Na przykład ten wzorzec dla adresów e-mail [a-zA-Z]{30}@[a-zA-Z]{20}.[ a-zA-Z]{2,3} będzie odpowiadać *user@contoso.com* i *user@contoso.co.jp*.  |
|Interfejs EDM SIT z elementami podstawowymi i bez zdefiniowanych elementów pomocniczych wykrywa elementy, ale nie wykrywa ani nie wykrywa mniej niż oczekiwano, gdy wymagane są elementy podstawowe i pomocnicze.  | Upewnij się, że wartości pomocniczych dowodów składają się z jednego słowa lub ciągu, który nie zawiera spacji, lub użyj instrukcji REGEX, które wykrywają ciągi wielowyrazowe. Na przykład \b[A-Z][a-z]{1,25}([ -][A-Z][a-z]{1,25}){0,4}\b, który będzie odpowiadał dowolnej sekwencji od jednego do pięciu kolejnych wyrazów rozpoczynających się wielkimi literami. Użyj tego interfejsu SIT jako elementu klasyfikacji dodatkowych warunków dowodowych w pliku XML typu informacji poufnych EDM. Zobacz [Ręczne tworzenie pakietu reguł](sit-get-started-exact-data-match-create-rule-package.md#create-a-rule-package-manually)|
|Funkcja testu SIT w ogóle nie wykrywa żadnych dopasowań.   | Sprawdź, czy wybrana funkcja SIT zawiera wymagania dotyczące dodatkowych słów kluczowych lub innych weryfikacji. Aby zapoznać się z wbudowanymi interfejsami SIC, zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) , aby sprawdzić, jakie są minimalne wymagania dotyczące dopasowywania poszczególnych typów.        |
|Funkcja testowania działa, ale elementy SharePoint lub OneDrive nie są wykrywane w regułach DLP lub automatycznego etykietowania     | Sprawdź, czy dokumenty, które mają być zgodne, są wyświetlane w Eksploratorze zawartości. Jeśli ich tam nie ma, pamiętaj, że tylko zawartość utworzona po zmianie typu informacji poufnych będzie wyświetlana jako dopasowana. Należy ponownie zszywać witryny i biblioteki, aby były wyświetlane wstępnie istniejące elementy. Aby uzyskać szczegółowe informacje na temat ponownego przeszukiwania SharePoint [i OneDrive, zobacz Ręczne przeszukiwanie i ponowne indeksowanie witryny, biblioteki lub listy](/sharepoint/crawl-site-content).        |
|Reguły DLP lub automatycznego etykietowania, które wymagają wielu dopasowań, nie są wyzwalane     |Sprawdź, czy są spełnione wymagania dotyczące bliskości zarówno typu EDM, jak i podstawowych typów informacji poufnych. Jeśli na przykład maksymalna odległość między elementem podstawowym a słowami kluczowymi pomocniczymi wynosi 300 znaków, ale słowa kluczowe znajdują się tylko w pierwszym wierszu długiej tabeli, tylko kilka pierwszych wierszy pasujących wartości prawdopodobnie spełni wymagania dotyczące bliskości. Zmodyfikuj definicje SIT, aby obsługiwać bardziej swobodne reguły zbliżeniowe lub użyj dowolnego miejsca w dokumencie w celu spełnienia dodatkowych warunków dowodowych.         |
|Wykrywanie typu EDM jest niespójne lub niekonsekwentne     |Sprawdź, czy typ informacji poufnych użyty jako podstawa elementu podstawowego w typie EDM nie wykrywa niepotrzebnej zawartości. Użycie funkcji SIT, która pasuje do zbyt dużej ilości niepowiązanej zawartości, takiej jak dowolne słowo, dowolna liczba lub wszystkie adresy e-mail, może spowodować nasycenie i zignorowanie odpowiednich dopasowań przez usługę. Sprawdź liczbę elementów zawartości odpowiadających typowi wrażliwemu użytemu dla elementów podstawowych w Eksploratorze zawartości. </br> Aby oszacować, czy funkcja SIT pasuje do zbyt dużej ilości zawartości: </br> — Dzielenie liczby elementów zawartości w Eksploratorze zawartości przez liczbę dni od utworzenia poufnego typu. </br> - Jeśli liczba meczów dziennie jest w zakresie setek tysięcy lub milionów, możliwe, że podstawowy SIT jest zbyt szeroki. Aby uzyskać zalecenia i najlepsze rozwiązania dotyczące wybierania odpowiedniego typu informacji poufnych dla typu EDM, zobacz [Informacje o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) .         |
