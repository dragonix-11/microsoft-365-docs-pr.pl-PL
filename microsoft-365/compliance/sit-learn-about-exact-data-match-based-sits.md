---
title: Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się więcej o dokładnych typach informacji poufnych zgodnych z danymi.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7f883d2509961ee07045949530f8fbb50629212f
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759772"
---
# <a name="learn-about-exact-data-match-based-sensitive-information-types"></a>Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych

[Typy informacji poufnych](sensitive-information-type-learn-about.md) służą do identyfikowania poufnych elementów, dzięki czemu można zapobiec ich nieumyślnemu lub niewłaściwemu udostępnianiu, aby ułatwić lokalizowanie odpowiednich danych w zakresie zbierania elektronicznych materiałów dowodowych oraz stosowanie akcji ładu do niektórych typów informacji. Niestandardowy typ informacji poufnych (SIT) definiuje się na podstawie:

- Wzorców
- dowody słów kluczowych, takie jak *pracownik*, *numer ubezpieczenia społecznego* lub *identyfikator*
- znak bliskości dowodów w określonym wzorze
- poziomy ufności

Ale co zrobić, jeśli chcesz niestandardowego typu informacji poufnych (SIT), który używa dokładnych lub prawie dokładnych wartości danych, zamiast takiego, który znalazł dopasowania na podstawie wzorców ogólnych? Dzięki klasyfikacji opartej na dokładnym dopasowaniu danych (EDM) można utworzyć niestandardowy typ informacji poufnych zaprojektowany w celu:

- dynamiczne i łatwe odświeżanie
- być bardziej skalowalne
- wynikiem mniejszej liczby wyników fałszywie dodatnich
- praca z danymi poufnymi ze strukturą
- bezpieczniej obsługiwać poufne informacje, nie udostępniając ich nikomu, w tym firmie Microsoft
- być używane z kilkoma usługami firmy Microsoft w chmurze

![Klasyfikacja oparta na protokole EDM.](../media/EDMClassification.png)

Klasyfikacja oparta na protokole EDM umożliwia tworzenie niestandardowych typów informacji poufnych odwołujących się do dokładnych wartości w bazie danych informacji poufnych. Bazę danych można odświeżać codziennie i zawierać do 100 milionów wierszy danych. W miarę jak pracownicy, pacjenci lub klienci przychodzą i odchodzą, a rekordy ulegają zmianie, niestandardowe typy informacji poufnych pozostają aktualne i stosowane. Ponadto można używać klasyfikacji opartej na rozwiązaniu EDM z zasadami, takimi jak [zasady zapobiegania utracie danych](dlp-learn-about-dlp.md) lub [zasady Microsoft Cloud App Security plików](/cloud-app-security/data-protection-policies).

> [!NOTE]
> Microsoft 365 Information Protection obsługuje języki podwójnego zestawu znaków bajtowych dla:
>
> - Chiński (uproszczony)
> - Chiński (tradycyjny)
> - Korean
> - Japanese
>
> Ta obsługa jest dostępna dla typów informacji poufnych. Aby uzyskać więcej informacji, zobacz [Obsługa ochrony informacji dla podwójnych zestawów znaków bajtowych (wersja zapoznawcza).](mip-dbcs-relnotes.md)

## <a name="whats-different-in-an-edm-sit"></a>Co się różni w środowisku EDM SIT

Podczas pracy z interfejsami SIC EDM warto zrozumieć kilka pojęć, które są dla nich unikatowe.  

### <a name="schema"></a>Schematu

Schemat jest plikiem XML, który definiuje:

- Nazwa schematu, później nazywana *magazynem danych*. 
- Nazwy pól, które zawiera tabela źródła informacji poufnych. Istnieje mapowanie 1:1 nazwy pola schematu na nazwę kolumny tabeli źródłowej informacji poufnych.
- Które pola można przeszukiwać.
- Dowolne parametry modyfikowania wyszukiwania, nazywane *konfigurowalnym dopasowaniem*, takie jak ignorowanie ograniczników i wielkości liter w wyszukiwanych wartościach.

### <a name="sensitive-information-source-table"></a>Tabela źródła informacji poufnych

Poufna tabela źródłowa zawiera poufne wartości informacji, których będzie szukać usługa EDM SIT. Składa się z kolumn i wierszy. Nagłówki kolumn to nazwy pól, wiersze są wystąpieniem danych, a każda komórka zawiera wartości dla tego wystąpienia dla tego pola.

Oto prosty przykład tabeli źródła informacji poufnych.

|Imię|Nazwisko|Data urodzenia|
|---|---|---|
|Izajasza|Langer| 05-05-1960|
|Ana|Bowman|11-24-1971|
|Oscar|Ward|02-12-1998|

### <a name="rule-package"></a>Pakiet reguł

Każdy sit ma pakiet reguł. Pakiet reguł w usłudze EDM SIT służy do definiowania następujących elementów:

- Dopasowania określające pole, które będzie elementem podstawowym do użycia w dokładnym wyszukiwaniu. Może to być wyrażenie regularne z weryfikacją sumy kontrolnej lub bez niej, listą słów kluczowych, słownikiem słów kluczowych lub funkcją.
- Klasyfikacja określająca poufne dopasowanie typu wyzwalające wyszukiwanie EDM.
- Element pomocniczy, który jest elementem, który po znalezieniu dostarcza dowodów potwierdzających, które pomagają zwiększyć pewność dopasowania. Na przykład słowo kluczowe "SSN" w pobliżu numeru SSN. Może to być wyrażenie regularne z weryfikacją sumy kontrolnej lub bez niej, listą słów kluczowych, słownikiem słów kluczowych.
- Poziomy ufności (wysoki, średni, niski) odzwierciedlają ilość wykrytych dowodów pomocniczych wraz z elementem podstawowym. Im więcej dowodów pomocniczych zawiera element, tym większa jest pewność, że dopasowany element zawiera informacje poufne, których szukasz. Zobacz [Podstawowe części typu informacji poufnych](sensitive-information-type-learn-about.md#fundamental-parts-of-a-sensitive-information-type) , aby uzyskać więcej informacji na temat poziomów ufności.
Bliskość — liczba znaków między elementem podstawowym i pomocniczym

### <a name="you-supply-your-own-schema-and-data"></a>Dostarczasz własny schemat i dane

[Microsoft 365 zawiera ponad 200 funkcji SITS](sensitive-information-type-entity-definitions.md) ze wstępnie zdefiniowanymi schematami, wzorcami regex, słowami kluczowymi i poziomami ufności. Za pomocą interfejsów SIC EDM odpowiadasz za definiowanie schematu, a także pól podstawowych i pomocniczych identyfikujących poufne elementy. Ponieważ schemat i podstawowe i pomocnicze wartości danych są wysoce poufne, szyfrujesz je za pomocą funkcji [skrótu](/dotnet/standard/security/ensuring-data-integrity-with-hash-codes) , która zawiera losowo wygenerowaną lub samodzielnie dostarczoną wartość [soli](https://en.wikipedia.org/wiki/Salt_(cryptography)#:~:text=The%20salt%20value%20is%20generated%20at%20random%20and,the%20salt%20value%20and%20hashed%20value%20are%20stored.) . Te wartości skrótu są następnie przekazywane do usługi, więc dane poufne nigdy nie są otwarte.

### <a name="primary-and-secondary-support-elements"></a>Podstawowe i pomocnicze elementy pomocy technicznej

Podczas tworzenia EDM SIT definiujesz pole *elementu podstawowego* w pakiecie reguł. Pola podstawowe to elementy, dla których będzie przeszukiwana cała zawartość, i które muszą być zgodne ze zdefiniowanym wzorcem w celu zidentyfikowania. Po znalezieniu elementu podstawowego w zeskanowanych elementach program EDM wyszuka pomocnicze *lub* pomocnicze elementy, które nie muszą być zgodne ze wzorcem i ich bliskość do elementu podstawowego. Program EDM wymaga, aby element podstawowy był najpierw wykrywalny za pośrednictwem istniejącego interfejsu SIT. Zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md) , aby uzyskać pełną listę dostępnych interfejsów API. Musisz znaleźć jedną z tych, które wykrywają klasę, którą chcesz wykryć w usłudze EDM SIT. Jeśli na przykład schemat EDM SIT ma numer ubezpieczenia społecznego w Stanach Zjednoczonych jako element podstawowy, podczas tworzenia schematu EDM skojarzysz go z numerem [ubezpieczenia społecznego (SSN) SIT w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn) .


## <a name="how-matching-works"></a>Jak działa dopasowywanie

Program EDM znajduje dopasowania, porównując zawartość, którą znajduje, z tabelą zdefiniowanych poufnych danych. Testowanie dopasowania odbywa się przy użyciu kombinacji tradycyjnych reguł i wzorców, aby upewnić się, że dopasowane dane są rzeczywistym wystąpieniem danych, które chcesz znaleźć i chronić. W swej istocie program EDM porównuje ciągi w dokumentach i wiadomościach e-mail z wartościami w podanej tabeli poufnych danych, aby dowiedzieć się, czy wartości w zawartości znajdują się w tabeli, porównując jednokierunkowe skróty kryptograficzne.

> [!TIP]
> Powszechną praktyką jest połączenie użycia typów informacji poufnych EDM i zwykłych typów informacji poufnych, na których są one oparte w regułach DLP, z różnymi progami. Na przykład można użyć typu informacji poufnych EDM, który wyszuka numerów ubezpieczenia społecznego i innych danych, ze ścisłymi wymaganiami i niską tolerancją, gdy co najmniej jedno dopasowanie spowoduje alert DLP, i użyć zwykłego typu informacji poufnych, takiego jak wbudowany numer ubezpieczenia społecznego w Stanach Zjednoczonych, aby uzyskać wyższą liczbę.  

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
   
