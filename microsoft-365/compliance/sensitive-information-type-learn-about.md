---
title: Dowiedz się więcej o typach informacji poufnych
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Ten artykuł zawiera omówienie typów informacji poufnych oraz sposobu wykrywania poufnych informacji, takich jak numer ubezpieczenia społecznego, karty kredytowej lub konta bankowego w celu identyfikacji poufnych elementów
ms.openlocfilehash: d814bd413fc95a02bc35ab05a804c544d9b84b1e
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014239"
---
# <a name="learn-about-sensitive-information-types"></a>Dowiedz się więcej o typach informacji poufnych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Identyfikowanie i klasyfikowanie poufnych elementów, które znajdują się pod kontrolą organizacji, jest pierwszym krokiem w [dziedzinie Information Protection](./information-protection.md).  Usługa Microsoft Purview udostępnia trzy sposoby identyfikowania elementów, dzięki czemu można je sklasyfikować:

- ręcznie przez użytkowników
- automatyczne rozpoznawanie wzorców, takie jak typy informacji poufnych
- [uczenie maszynowe](classifier-learn-about.md)

Typy informacji poufnych (SIT) to klasyfikatory oparte na wzorcach. Wykrywają poufne informacje, takie jak numer ubezpieczenia społecznego, karty kredytowej lub konta bankowego, aby zidentyfikować poufne elementy, zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md) , aby uzyskać pełną listę wszystkich SIC.

Firma Microsoft udostępnia dużą liczbę wstępnie skonfigurowanych interfejsów SIC lub możesz utworzyć własne.

## <a name="sensitive-information-types-are-used-in"></a>Typy informacji poufnych są używane w

- [Zasady ochrony przed utratą danych w usłudze Microsoft Purview](dlp-learn-about-dlp.md)
- [Etykiety wrażliwości](sensitivity-labels.md)
- [Etykiety przechowywania](retention.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)
- [Zgodność w komunikacji](communication-compliance.md)
- [Zasady automatycznego etykietowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Priva](/privacy/priva)

## <a name="categories-of-sensitive-information-types"></a>Kategorie typów informacji poufnych

### <a name="built-in-sensitive-information-types"></a>Wbudowane typy informacji poufnych

Te interfejsy SIC są domyślnie tworzone przez firmę Microsoft w konsoli zgodności. Tych interfejsów SIC nie można edytować, ale mogą być używane jako szablony i kopiowane w celu tworzenia niestandardowych typów informacji poufnych. Zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md) , aby uzyskać pełną listę wszystkich SIC.

### <a name="named-entity-sensitive-information-types"></a>Nazwane typy informacji poufnych jednostki

Domyślnie w konsoli zgodności są również wyświetlane nazwane SIC jednostek. Wykrywają imiona i nazwiska osób, adresy fizyczne oraz warunki i postanowienia medyczne. Nie można ich edytować ani kopiować. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o nazwanych jednostkach ](named-entities-learn.md#learn-about-named-entities) . Nazwane interfejsy SIC jednostki są dostępne w dwóch typach:

**un-bundled**

Te nazwane jednostki SIC mają węższe fokus, na przykład pojedynczy kraj lub jedną klasę terminów. Użyj ich, gdy potrzebujesz zasad DLP z węższym zakresem wykrywania. Zobacz [przykłady nazwanych SIC jednostek](named-entities-learn.md#examples-of-named-entity-sits).

**Pakiecie**

W pakiecie nazwane jednostki SIC wykrywają wszystkie możliwe dopasowania w klasie, takie jak Wszystkie adresy fizyczne. Użyj ich jako szerokich kryteriów w zasadach DLP do wykrywania poufnych elementów. Zobacz [przykłady nazwanych SIC jednostek](named-entities-learn.md#examples-of-named-entity-sits).

### <a name="custom-sensitive-information-types"></a>Niestandardowe typy informacji poufnych

Jeśli wstępnie skonfigurowane typy informacji poufnych nie spełniają Twoich potrzeb, możesz utworzyć własne niestandardowe typy informacji poufnych, które zostały w pełni zdefiniowane, lub skopiować jeden z wbudowanych i zmodyfikować je. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowego typu informacji poufnych w Centrum zgodności](create-a-custom-sensitive-information-type.md) .

### <a name="exact-data-match-sensitive-information-types"></a>Dokładne dane pasują do typów informacji poufnych

Wszystkie interfejsy SIC oparte na protokole EDM są tworzone od podstaw. Służy do wykrywania elementów, które mają dokładne wartości zdefiniowane w bazie danych informacji poufnych. Aby uzyskać więcej informacji, [zobacz Informacje o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) .

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Podstawowe części typu informacji poufnych

Każda jednostka typu informacji poufnych jest definiowana przez następujące pola:

- name: how the sensitive information type is referred to
- description: opisuje, czego szuka typ informacji poufnych
- wzorzec: wzorzec definiuje, co wykrywa typ informacji poufnych. Składa się z następujących składników.
  - Element podstawowy — główny element, którego szuka typ informacji poufnych. Może to być **wyrażenie regularne** z weryfikacją sumy kontrolnej lub bez niej, **listą słów kluczowych**, **słownikiem słów kluczowych** lub **funkcją**.
  - Element pomocniczy — elementy, które działają jako dowody potwierdzające, które pomagają zwiększyć pewność meczu. Na przykład słowo kluczowe "SSN" w pobliżu numeru SSN. Może to być wyrażenie regularne z weryfikacją sumy kontrolnej lub bez niej, listą słów kluczowych, słownikiem słów kluczowych.
  - Poziom ufności — poziomy ufności (wysoki, średni, niski) odzwierciedlają ilość wykrytych dowodów pomocniczych wraz z elementem podstawowym. Im więcej dowodów pomocniczych zawiera element, tym większa jest pewność, że dopasowany element zawiera informacje poufne, których szukasz.
  - Bliskość — liczba znaków między elementem podstawowym i pomocniczym.

![Diagram dowodów potwierdzających i okna bliskości.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Dowiedz się więcej o poziomach ufności w tym krótkim filmie wideo.

 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]

### <a name="example-sensitive-information-type"></a>Przykładowy typ informacji poufnych

#### <a name="argentina-national-identity-dni-number"></a>Numer tożsamości narodowej Argentyny (DNI)

### <a name="format"></a>Formatowanie

Osiem cyfr rozdzielonych kropkami

### <a name="pattern"></a>Wzór

Osiem cyfr:

- dwie cyfry
- okres
- trzy cyfry
- okres
- trzy cyfry

### <a name="checksum"></a>Suma kontrolna

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że wykryto ten typ informacji poufnych, jeśli w pobliżu 300 znaków:

- Wyrażenie regularne Regex_argentina_national_id znajduje zawartość zgodną ze wzorcem.
- Znaleziono słowo kluczowe z Keyword_argentina_national_id.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Słowa kluczowe

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Numer tożsamości narodowej Argentyny
- Tożsamości
- Identyfikacja krajowego dowodu osobistego
- DNI
- Krajowy rejestr osób karty sieciowej
- Documento Nacional de Identidad
- Registro Nacional de las Personas
- Identidad
- Identificación

### <a name="more-on-confidence-levels"></a>Więcej informacji na temat poziomów ufności

W definicji jednostki typu informacji poufnych **poziom ufności** odzwierciedla ilość dowodów pomocniczych wykrytych oprócz elementu podstawowego. Im więcej dowodów pomocniczych zawiera element, tym większa jest pewność, że dopasowany element zawiera informacje poufne, których szukasz. Na przykład dopasowania z wysokim poziomem ufności będą zawierać więcej dowodów pomocniczych w pobliżu elementu podstawowego, podczas gdy dopasowania z niskim poziomem ufności będą zawierać niewiele dowodów potwierdzających w bliskiej odległości.

Wysoki poziom ufności zwraca najmniejszą liczbę wyników fałszywie dodatnich, ale może spowodować więcej fałszywych negatywów. Niski lub średni poziom ufności zwraca więcej wyników fałszywie dodatnich, ale od kilku do zera fałszywych negatywów.

- **niska pewność**: dopasowane elementy będą zawierać najmniejszą liczbę fałszywych negatywów, ale najwięcej wyników fałszywie dodatnich. Niska pewność siebie zwraca wszystkie dopasowania niskiej, średniej i wysokiej ufności. Niski poziom ufności ma wartość 65.
- **średnie zaufanie**: dopasowane elementy będą zawierać średnią liczbę wyników fałszywie dodatnich i fałszywie ujemnych. Średnia pewność siebie zwraca wszystkie średnie i wysokie dopasowania ufności. Średni poziom ufności ma wartość 75.
- **wysoka pewność**: dopasowane elementy będą zawierać najmniejszą liczbę wyników fałszywie dodatnich, ale najwięcej fałszywych negatywów. Wysoka pewność siebie zwraca tylko wysokie dopasowania ufności i ma wartość 85.

Należy używać wzorców wysokiego poziomu ufności z niską liczbą, powiedzmy od pięciu do dziesięciu, oraz wzorców niskiej ufności z większą liczbą, na przykład 20 lub więcej.

> [!NOTE]
> Jeśli istnieją zasady lub niestandardowe typy informacji poufnych (SIC) zdefiniowane przy użyciu poziomów ufności na podstawie liczb (znanych również jako dokładność), zostaną one automatycznie zamapowane na trzy odrębne poziomy ufności; niski poziom ufności, średniego zaufania i wysokiego poziomu ufności w interfejsie użytkownika Security @ Compliance Center.
>
> - Wszystkie zasady z minimalną dokładnością lub niestandardowymi wzorcami SIT z poziomami ufności od 76 do 100 zostaną zamapowane na wysoką pewność.
> - Wszystkie zasady z minimalną dokładnością lub niestandardowymi wzorcami SIT z poziomami ufności od 66 do 75 zostaną zamapowane na średnie zaufanie.
> - Wszystkie zasady z minimalną dokładnością lub niestandardowymi wzorcami SIT z poziomami ufności mniejszymi lub równymi 65 zostaną zamapowane na niski poziom ufności.

## <a name="creating-custom-sensitive-information-types"></a>Tworzenie niestandardowych typów informacji poufnych

Możesz wybrać jedną z kilku opcji tworzenia niestandardowych typów informacji poufnych w Centrum zgodności.

- **Użyj interfejsu użytkownika** — możesz skonfigurować niestandardowy typ informacji poufnych przy użyciu interfejsu użytkownika Centrum zgodności. Ta metoda umożliwia używanie wyrażeń regularnych, słów kluczowych i słowników słów kluczowych. Aby dowiedzieć się więcej, zobacz [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md).

- **Użyj rozwiązania EDM** — możesz skonfigurować niestandardowe typy informacji poufnych przy użyciu klasyfikacji opartej na dokładnym dopasowaniu danych (EDM). Ta metoda umożliwia utworzenie dynamicznego typu informacji poufnych przy użyciu bezpiecznej bazy danych, którą można okresowo odświeżać. Zobacz [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

- **Użyj programu PowerShell** — możesz skonfigurować niestandardowe typy informacji poufnych przy użyciu programu PowerShell. Chociaż ta metoda jest bardziej złożona niż korzystanie z interfejsu użytkownika, masz więcej opcji konfiguracji. Zobacz [Create a custom sensitive information type in Security & Compliance PowerShell (Tworzenie niestandardowego typu informacji poufnych w programie PowerShell security & Compliance](create-a-custom-sensitive-information-type-in-scc-powershell.md)).

> [!NOTE]
> Ulepszone poziomy ufności są dostępne do natychmiastowego użycia w usługach ochrony przed utratą danych w usłudze Microsoft Purview, ochrony informacji, zgodności z komunikacją, zarządzania cyklem życia danych i zarządzania rekordami.
> Information Protection obsługuje teraz języki podwójnego zestawu znaków bajtów dla:
> - Chiński (uproszczony)
> - Chiński (tradycyjny)
> - Korean
> - Japanese
>
> Ta obsługa jest dostępna dla typów informacji poufnych. Aby uzyskać więcej informacji, zobacz [Obsługa ochrony informacji dla podwójnych zestawów znaków bajtowych](mip-dbcs-relnotes.md) .

> [!TIP]
> Aby wykryć wzorce zawierające znaki chińskie/japońskie i pojedyncze znaki bajtowe lub wykryć wzorce zawierające chiński/japoński i angielski, zdefiniuj dwa warianty słowa kluczowego lub wyrażenia regularnego.
>
> - Aby na przykład wykryć słowo kluczowe, takie jak "机密的document", użyj dwóch wariantów słowa kluczowego; jeden z odstępem między tekstem japońskim i angielskim a drugim bez odstępu między tekstem japońskim i angielskim. Dlatego słowa kluczowe, które mają zostać dodane w usłudze SIT, powinny mieć wartość "机密的 document" i "机密的document". Podobnie, aby wykryć frazę "東京オリnegoピック2020", należy użyć dwóch wariantów; "東京オリ":"ピック 2020" i "東京オリ":"ピック2020".
>
> Oprócz znaków chińskich/japońskich/podwójnych bajtów, jeśli lista słów kluczowych/fraz zawiera również wyrazy inne niż chińskie/japońskie (na przykład tylko angielski), należy utworzyć dwa słowniki/listy słów kluczowych. Jeden dla słów kluczowych zawierających znaki chiński/japoński/podwójny bajt, a drugi tylko dla języka angielskiego.
>
> - Jeśli na przykład chcesz utworzyć słownik/listę słów kluczowych z trzema frazami "Wysoce poufne", "機密性が高い" i "机密的document", należy utworzyć dwie listy słów kluczowych.
>     1. Wysoce poufne
>     2. 機密性が高い, 机密的document i 机密的 dokumentu
>
> Podczas tworzenia wyrażenia regularnego przy użyciu łącznika dwu bajtowego lub podwójnego kropki bajtowej upewnij się, że oba znaki, takie jak jeden, unikną łącznika lub kropki w rejestrze. Oto przykładowy rejestr referencyjny:
>
> `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> Zalecamy używanie dopasowania ciągu zamiast dopasowania wyrazów na liście słów kluczowych.

## <a name="for-further-information"></a>Aby uzyskać więcej informacji

- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
- [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)

Aby dowiedzieć się, jak używać typów informacji poufnych w celu zachowania zgodności z przepisami dotyczącymi prywatności danych, zobacz [Wdrażanie ochrony informacji dla przepisów dotyczących prywatności danych za pomocą Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->
