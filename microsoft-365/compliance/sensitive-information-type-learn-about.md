---
title: Informacje o typach informacji poufnych
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
description: W tym artykule opisano typy informacji poufnych oraz sposób wykrywania informacji poufnych, takich jak numery PESEL, kart kredytowych lub kont bankowych w celu identyfikowania elementów poufnych.
ms.openlocfilehash: fbe23bbb6c639857367cc0b8467f6084e9116af1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318847"
---
# <a name="learn-about-sensitive-information-types"></a>Informacje o typach informacji poufnych

Identyfikowanie i klasyfikowanie poufnych elementów, które są pod kontrolą Twojej organizacji, to pierwszy krok w dyscyplinie [ochrony informacji](./information-protection.md).  Microsoft 365 udostępnia trzy sposoby identyfikowania elementów w celu ich klasyfikowania:

- ręcznie przez użytkowników
- Automatyczne rozpoznawanie wzorców, takie jak typy informacji poufnych
- [uczenie maszynowe](classifier-learn-about.md)

Typy informacji poufnych (SIT) są klasyfikatorami opartymi na wzorcu. Wykrywają one informacje poufne, takie jak numery PESEL, kart kredytowych lub kont bankowych, [](sensitive-information-type-entity-definitions.md) w celu identyfikowania elementów poufnych, zobacz Definicje jednostek typów informacji poufnych, aby uzyskać pełną listę wszystkich list wszystkich typów danych.

Firma Microsoft udostępnia wiele wstępnie skonfigurowanych list adresowych użytkowników lub możesz utworzyć własne.

## <a name="sensitive-information-types-are-used-in"></a>Typy informacji poufnych są używane w

- [Zasady ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Etykiety wrażliwości](sensitivity-labels.md)
- [Etykiety przechowywania](retention.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md)
- [Zgodność komunikacji](communication-compliance.md)
- [Zasady automatycznego schowania](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Priva](/privacy/priva)

## <a name="categories-of-sensitive-information-types"></a>Kategorie typów informacji poufnych

### <a name="built-in-sensitive-information-types"></a>Wbudowane typy informacji poufnych

Te sits są tworzone przez firmę Microsoft domyślnie są wyświetlane w konsoli zgodności. Tych typów informacji poufnych nie można edytować, ale można ich używać jako szablonów i kopiować w celu tworzenia niestandardowych typów informacji poufnych. Zobacz [Definicje encji typu informacji poufnych](sensitive-information-type-entity-definitions.md) , aby uzyskać pełną listę wszystkich typów informacji (SIT).

### <a name="named-entity-sensitive-information-types"></a>Nazwane typy informacji poufnych encji

Nazwane jednostki SIT są domyślnie także wyświetlane w konsoli zgodności. Wykrywa imiona i nazwiska, adresy fizyczne oraz warunki medyczne. Nie można ich edytować ani kopiować. Aby uzyskać więcej informacji, zobacz Informacje [o nazwanych jednostkach (wersja zapoznawcza](named-entities-learn.md#learn-about-named-entities-preview) ). Identyfikatory SIT nazwanej jednostki są dwa typy:

**niepodajęcie pakietu**

Te nazwane jednostki SI mają węższą uwagę, na przykład jeden kraj lub jedną klasę terminów. Używaj ich, gdy potrzebujesz zasad DLP o węższym zakresie wykrywania. Zobacz [Przykłady nazwanych identyfikatorów STS jednostki](named-entities-learn.md#examples-of-named-entity-sits).

**pakiet**

Powiązane nazwane jednostki SIT wykryją wszystkie możliwe dopasowania w klasie, na przykład Wszystkie adresy fizyczne. Korzystaj z nich jako szerokiego kryterium wykrywania poufnych elementów w zasadach ochrony przed użyciem funkcji DLP. Zobacz [Przykłady nazwanych identyfikatorów STS jednostki](named-entities-learn.md#examples-of-named-entity-sits).

### <a name="custom-sensitive-information-types"></a>Niestandardowe typy informacji poufnych

Jeśli wstępnie skonfigurowane typy informacji poufnych nie spełniają Twoich potrzeb, możesz utworzyć własne niestandardowe typy informacji poufnych, które są w pełni definiowane, lub skopiować jeden z wbudowanych i zmodyfikować go. Aby uzyskać więcej informacji, zobacz Tworzenie [niestandardowego typu informacji poufnych w Centrum](create-a-custom-sensitive-information-type.md) zgodności.

### <a name="exact-data-match-sensitive-information-types"></a>Dokładne dopasowanie danych do typów informacji poufnych

Wszystkie informacje OIT oparte na programie EDM są tworzone od podstaw. Za ich pomocą można wykrywać elementy z dokładnymi wartościami, które są w bazie danych definiujące poufne informacje. Aby uzyskać [więcej informacji, zobacz](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) Informacje o dokładnie tych typach informacji, na których są oparte informacje poufne.

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Podstawowe części typu informacji poufnych

Każda jednostka typu informacji poufnych jest definiowana przez następujące pola:

- nazwa: sposób, w jaki jest określany typ informacji poufnych
- opis: zawiera opis szukanych informacji poufnych
- deseń: deseń określa, co wykrywa typ informacji poufnych. Składa się on z następujących składników.
    - Element podstawowy — główny element, którego szuka typ informacji poufnych. Może to być **zwykłe wyrażenie ze** sprawdzaniem poprawności sumy sprawdzanej lub bez **, listą** słów kluczowych, słownikiem **słów kluczowych** lub **funkcją**.
    - Element obsługujący — elementy, które działają jako dowody, które pomagają zwiększyć pewność dopasowania. Na przykład słowo kluczowe "SSN" w odległości od numeru SSN. Może to być zwykłe wyrażenie ze sprawdzaniem poprawności sumy sprawdzanej lub bez, listą słów kluczowych, słownikiem słów kluczowych.
    - Poziom ufności — poziom ufności (wysoki, średni, niski) odzwierciedla poziom wykrycia dowodów potwierdzających wraz z podstawowym elementem. Im więcej dowodów ważnych dla elementu zawiera, tym większa pewność, że dopasowany element zawiera szukane informacje poufne.
    - Odległość — liczba znaków między elementem podstawowym a elementem obsługowym.

![Diagram dowodu potwierdzania i okna sąsiedztwa.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Z tego krótkiego klipu wideo dowiesz się więcej o poziomach ufności.


 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]  



### <a name="example-sensitive-information-type"></a>Przykładowy typ informacji poufnych


#### <a name="argentina-national-identity-dni-number"></a>Numer tożsamości państwowej Argentyny (DNI)

### <a name="format"></a>Formatowanie

Osiem cyfr rozdzielonych kropkami

### <a name="pattern"></a>Deseń

Osiem cyfr:
- dwie cyfry
- okres
- trzy cyfry
- okres
- trzy cyfry

### <a name="checksum"></a>Checksum

Nie

### <a name="definition"></a>Definicja

Zasady DLP mają średnią pewność, że są wykrywane tego typu informacje poufne, jeśli w odległości 300 znaków:
- Wyrażenie regularne Regex_argentina_national_id umożliwia znalezienie zawartości, która odpowiada wzorcowi.
- Słowo kluczowe z Keyword_argentina_national_id znajduje się.

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

- Argentyna ( numer tożsamości państwowej) 
- Tożsamości 
- Identification National Identity Card 
- DNI 
- NIC National Registry of Persons 
- Documento Nacional de Identidad 
- Registro Nacional de las Personas 
- Identidad 
- Identificación 

### <a name="more-on-confidence-levels"></a>Więcej informacji na temat poziomów ufności

W definicji jednostki typu informacji poufnych  poziom ufności oprócz elementu podstawowego odzwierciedla poziom dowodu potwierdzającego. Im więcej dowodów ważnych dla elementu zawiera, tym większa pewność, że dopasowany element zawiera szukane informacje poufne. Na przykład dopasowania z wysokim poziomem ufności będą zawierały więcej dowodów pomocnych w pobliżu podstawowego elementu, podczas gdy dopasowania o niskim poziomie ufności nie będą zawierać żadnych dowodów na ich temat w pobliżu. 

Wysoki poziom ufności zwraca najmniej wyników fałszywie dodatnich, ale może prowadzić do większej liczby wyników fałszywie ujemnych. Niskie lub średnie poziomy ufności zwraca więcej wyników fałszywie dodatnich, ale od kilku do zerowych wartości fałszywie ujemnych.

- **niska ufność**: Dopasowane elementy będą zawierały najmniejszą wartość fałszywą ujemną, ale najwięcej wyników fałszywie dodatnich. Niskie ufność zwraca wszystkie dopasowania do niskiej, średniej i wysokiej ufności. Wartość niskiej ufności wynosi 65.
- **średnia ufność**: pozycje dopasowane będą zawierać średnią liczbę wyników fałszywie dodatnich i ujemnych. Średnia ufność zwraca wartość dopasowania średniego i wysokiego ufności. Średni poziom ufności ma wartość 75.
- **wysoka pewność**: Elementy dopasowane będą zawierały najmniej wyników fałszywie dodatnich, ale najwięcej wyników fałszywie ujemnych. Tylko wysoka ufność zwraca dopasowania z wysoką ufnością i ma wartość 85.  

Wzorców wysokiego poziomu ufności należy używać przy niskiej liczności, na przykład od 5 do dziesięciu, a wzorców niskiej ufności przy wyższych liczbach (na przykład 20 lub więcej).

> [!NOTE]
> W przypadku istniejących zasad lub niestandardowych typów informacji poufnych zdefiniowanych przy użyciu poziomów ufności opartych na liczbach (określanych również jako dokładność) zostaną one automatycznie zamapowane na trzy osobne poziomy ufności. niskiej ufności, średniej ufności i wysokiego ufności w interfejsie użytkownika Centrum zabezpieczeń @ zgodności.
> - Wszystkie zasady o minimalnej dokładności lub niestandardowe wzorce sit (SIT) ze poziomami ufności między 76 a 100 zostaną zamapowane na wysokie ufności. 
> - Wszystkie zasady o minimalnej dokładności lub niestandardowe wzorce sit (SIT) ze poziomami ufności między 66 a 75 zostaną zamapowane na średnie ufności.
> - Wszystkie zasady o minimalnej dokładności lub niestandardowe wzorce sit (SIT) o poziomach ufności mniejszej lub równej 65 zostaną zamapowane na mało ufne. 

## <a name="creating-custom-sensitive-information-types"></a>Tworzenie niestandardowych typów informacji poufnych

Możesz wybrać jedną z kilku opcji, aby utworzyć niestandardowe typy informacji poufnych w Centrum zgodności.

- **Interfejs użytkownika —** za pomocą interfejsu użytkownika Centrum zgodności można skonfigurować niestandardowy typ informacji poufnych. Przy użyciu tej metody można używać wyrażeń regularnych, słów kluczowych i słowników słów kluczowych. Aby dowiedzieć się więcej, [zobacz Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md).

- **Korzystanie z usługi EDM** — możesz skonfigurować niestandardowe typy informacji poufnych przy użyciu klasyfikacji opartej na dokładnie danych (EDM). Ta metoda umożliwia utworzenie dynamicznego typu informacji poufnych przy użyciu bezpiecznej bazy danych, która będzie okresowo odświeżana. Zobacz [Informacje o dokładnie typach informacji poufnych opartych na danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

- **Użyj programu PowerShell** — możesz skonfigurować niestandardowe typy informacji poufnych przy użyciu programu PowerShell. Ta metoda jest bardziej złożona niż używanie interfejsu użytkownika, ale dostępnych jest więcej opcji konfiguracji. Zobacz [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell & Zabezpieczeń i zgodności](create-a-custom-sensitive-information-type-in-scc-powershell.md).

> [!NOTE]
> Ulepszone poziomy ufności są dostępne do natychmiastowego użycia w ramach funkcji Ochrona przed utratą danych dla usług firmy Microsoft 365, Microsoft Information Protection dla usług firmy Microsoft 365, zgodności komunikacji, zarządzania informacjami i zarządzania rekordami.
> Microsoft 365 informacji obsługuje teraz języki zestawu znaków dwu bajtowych dla:
> - Chiński (uproszczony)
> - Chiński (tradycyjny)
> - Korean
> - Japanese
> 
> Ta obsługa jest dostępna w przypadku typów informacji poufnych. Aby uzyskać [więcej informacji](mip-dbcs-relnotes.md) , zobacz Obsługa ochrony informacji dla zestawów znaków dwu bajtowych.

> [!TIP]
> Aby wykryć wzorce zawierające znaki chińskie/japońskie i pojedyncze bajty lub wykryć wzorce zawierające chiński/japoński i angielski, zdefiniuj dwie warianty słowa kluczowego lub znaków regex.
> - Aby na przykład wykryć słowo kluczowe, takie jak "机密的document", użyj dwóch wariantów słowa kluczowego; jeden z odstępem między tekstem japońskim i angielskim a innym bez spacji między tekstem japońskim i angielskim. Dlatego słowa kluczowe, które mają zostać dodane w dokumencie SIT, powinny mieć poszczególnych 机密的 dokumentu i 机密的document. Podobnie, aby wykryć frazę "ピオリンピック2020", należy użyć dwóch wariantów. "オオリンピック 2020" and "ピピリンピック2020".
> 
> Jeśli oprócz chińskich/japońskich/dwu bajtowych znaków na liście słów kluczowych/fraz znajdują się również wyrazy inne niż chińskie/japońskie (na przykład tylko w języku angielskim), należy utworzyć dwie listy słowników/słów kluczowych. Jeden dla słów kluczowych zawierających znaki chińskie/japońskie/dwu bajtowe, a drugi tylko w języku angielskim. 
> - Jeśli na przykład chcesz utworzyć słownik lub listę słów kluczowych z trzema frazami "Wysoce poufne", "機密性がいい" i "机密的document", należy utworzyć dwie listy słów kluczowych. 
>     1. Wysoce poufne
>     2. 機密性がい, 机密的document i 机密的 dokument
> 
> Tworząc znak regex za pomocą dwu-bajtowego łącznika lub podwójnej litery bajtowej, należy pamiętać o znakach ucieczki przed łącznikiem lub przecięciem w znakach regex. Oto przykładowy regex do odwołania:
>    - (?<!\d) ([4][0-9]{3} [\-?\-\t]*[0-9]{4}
>
> Zalecamy używanie dopasowania ciągów zamiast dopasowania wyrazów na liście słów kluczowych.

## <a name="for-further-information"></a>Więcej informacji
- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
- [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)

Aby dowiedzieć się, jak korzystać z typów informacji poufnych w celu zachowania zgodności z przepisami dotyczącymi prywatności danych, zobacz Wdrażanie ochrony informacji w przypadku przepisów dotyczących prywatności danych za pomocą [Microsoft 365 (aka.ms/m365dataprivacy](../solutions/information-protection-deploy.md)).

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->
