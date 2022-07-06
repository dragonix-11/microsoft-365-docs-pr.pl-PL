---
title: Dokumentacja dotycząca niestandardowych filtrów typów informacji poufnych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: W tym artykule przedstawiono listę filtrów, które można zakodować do niestandardowych typów informacji poufnych.
ms.openlocfilehash: 79e4a2520ab922248f65adf1b0506219987fe832
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631964"
---
# <a name="custom-sensitive-information-type-filters-reference"></a>Dokumentacja dotycząca niestandardowych filtrów typów informacji poufnych

W firmie Microsoft można zdefiniować filtry lub inne testy podczas tworzenia niestandardowych typów informacji poufnych (SIT).

## <a name="list-of-supported-filters-and-use-cases"></a>Lista obsługiwanych filtrów i przypadków użycia

### <a name="alldigitssame-exclude"></a>AllDigitsSame Exclude

Opis: Umożliwia wykluczenie dopasowań, które mają wszystkie cyfry jako zduplikowane cyfry, takie jak 111111111 lub 111-111-111

Definiowanie filtrów
```xml
<Filters id="ssn_filters">
    <Filter type="AllDigitsSameFilter"></Filter>
</Filters>
```

Używanie go w pakiecie reguł na poziomie jednostki
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85"  filters="ssn_filters">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

Używanie go w pakiecie reguł na poziomie wzorca
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="ssn_filters">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

### <a name="textmatchfilter-startswith"></a>TextMatchFilter StartsWith 

Opis: umożliwia zdefiniowanie początkowych znaków jednostki. Ma dwa warianty, obejmują i wykluczają.

Aby na przykład wykluczyć liczby rozpoczynające się od 0500, 91, 091, 010 na liście w następujący sposób:

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Możesz użyć następującego kodu XML

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>
</Filters>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```
Aby na przykład uwzględnić liczby rozpoczynające się od 0500, 91, 091, 0100 na liście w następujący sposób: 

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Możesz użyć następującego kodu XML

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-endswith"></a>TextMatchFilter EndsWith 

Opis: umożliwia zdefiniowanie znaków końcowych dla jednostki. 

Aby na przykład wykluczyć liczby kończące się na 0500,91,091, 0100 na liście w następujący sposób:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Możesz użyć następującego kodu XML

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="EndsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```

Aby na przykład uwzględnić liczby kończące się wartościami 0500, 91, 091, 0100, na takiej liście:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Możesz użyć następującego kodu XML

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction=" EndsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-full"></a>TextMatchFilter — pełny

Opis: umożliwia zakazanie określonych dopasowań, aby uniemożliwić im wyzwolenie reguły. Na przykład wyklucz 4111111111111111 z listy prawidłowych dopasowań karty kredytowej.

Aby na przykład wykluczyć numery kart kredytowych, takie jak 4111111111111111 i 3241891031113111, na takiej liście:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Możesz użyć następującego kodu XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Full" logic="Exclude" textProcessorId="Keyword_false_positives_full">
</Filter>

  <Keyword id="Keyword_false_positives_full">
    <Group matchStyle="string">
      <Term>4111111111111111</Term>
      <Term>3241891031113111</Term>
    </Group>
  </Keyword>
```

Aby na przykład uwzględnić numery kart kredytowych, takie jak 4111111111111111 i 3241891031113111, na liście w następujący sposób:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Możesz użyć następującego kodu XML

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_false_positives_full">
</Filter>
```

### <a name="textmatchfilter-prefix"></a>Prefiks TextMatchFilter

Opis: umożliwia zdefiniowanie powyższych znaków, które powinny być zawsze uwzględniane lub wykluczane. Jeśli na przykład numer karty kredytowej jest poprzedzony ciągiem "Order ID:", usuń dopasowanie z prawidłowych dopasowań.

Aby na przykład wykluczyć wystąpienia numerów telefonów z **numerem telefonu** i **zadzwonić do mnie na** ciągi przed numerem telefonu, na poniższej liście:

- Numer telefonu 091-8974-653278
- Telefon 45-124576532-123
- 45-124576532-123

Możesz użyć następującego kodu XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_prefix">
</Filter>
  <Keyword id="Keyword_false_positives_prefix">
    <Group matchStyle="string">
      <Term>phone number</Term>
      <Term>call me at</Term>
    </Group>
  </Keyword>
```

Aby na przykład uwzględnić wystąpienia, które mają **ciągi kart kredytowych** i **kart** przed numerem karty kredytowej, na liście takiej jak ta:

- Karta kredytowa 45-124576532-123 
- 45-124576532-123 (co może być numerem telefonu)

Możesz użyć następującego kodu XML

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_prefix">
</Filter>

  <Keyword id="Keyword_true_positives_prefix">
    <Group matchStyle="string">
      <Term>credit card</Term>
      <Term>card #</Term>
    </Group>
  </Keyword
```

### <a name="textmatchfilter-suffix"></a>Sufiks TextMatchFilter

Opis: Umożliwia zdefiniowanie następujących znaków, które powinny być zawsze uwzględniane lub wykluczane. Jeśli na przykład po numerze karty kredytowej następuje ciąg "/xuid", usuń dopasowanie z prawidłowych dopasowań.

Jeśli na przykład istnieje pięć wystąpień z czterema cyframi jako sufiks na liście w następujący sposób, wyklucz wystąpienia z góry:

- 1234-5678-9321 4500 9870 6321 48925566
- 1234-5678-9321

Możesz użyć następującego kodu XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Regex_false_positives_suffix">
</Filter>

  <Regexid="Regex_false_positives_suffix">(\d{4}){5,}</Regex>
```
Aby na przykład wykluczyć wystąpienia, po których następuje **/xuidsuffix**, jak na tej liście:

- 1234-5678-9321 /xuid
- 1234-5678-9321

Możesz użyć tego kodu XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_suffix">
</Filter>

  <Keyword id="Keyword_false_positives_suffix">
    <Group matchStyle="string">
      <Term>/xuid</Term>
    </Group>
  </Keyword>
```

Na przykład, aby uwzględnić wystąpienie tylko wtedy, gdy następuje **cvv** lub **wygasa**, jak dwa na tej liście:

- 45-124576532-123 
- 45-124576532-123 cvv 966
- 45-124576532-123 wygasa 03/23

Możesz użyć tego kodu XML

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_suffix">
</Filter>

  <Keyword id="Keyword_true_positives_suffix">
    <Group matchStyle="string">
      <Term>cvv</Term>
      <Term>expires</Term>
    </Group>
  </Keyword>
```

## <a name="using-filters-in-rule-packages"></a>Używanie filtrów w pakietach reguł

Filtry można zdefiniować na całym serwerze SIT lub we wzorcu. Oto kilka przykładów fragmentów kodu. 

### <a name="at-sensitive-information-type-level"></a>Na poziomie typów informacji poufnych

Filtry w jednostce — będą obejmować wszystkie wzorce podrzędne

Filtry zostaną zastosowane do **wszystkich** wystąpień sklasyfikowanych według dowolnego wzorca w tej jednostce / typie wrażliwym

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
```

### <a name="at-the-individual-pattern-of-the-sensitive-information-type-level"></a>Na poziomie indywidualnego wzorca typu informacji poufnych

Filtruje tylko na poziomie wzorca.

Filtr zostanie zastosowany do wystąpień dopasowanych do wzorca.

```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Keyword_cc_verification" />
      </Pattern>
</Entity>
```


### <a name="at-sensitive-information-type-level-and-an-additional-filter-on-some-of-the-patterns-of-that-entity"></a>Na poziomie typów informacji poufnych i dodatkowym filtrze niektórych wzorców tej jednostki

Filtry w jednostce i wzorcu

Filtry zostaną zastosowane do **wszystkich** wystąpień sklasyfikowanych według dowolnego wzorca w tej jednostce / typie wrażliwym. Filtr poziomu wzorca filtruje wystąpienia dopasowane do tego wzorca.

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85" filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
``` 

 

## <a name="more-information"></a>Więcej informacji

- [Dowiedz się więcej o Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md)

- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)

- [Funkcje typu informacji poufnych](sit-functions.md)
