---
title: Odwołanie do niestandardowych filtrów typów informacji poufnych
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
description: Ten artykuł zawiera listę filtrów, które można kodować w niestandardowych typach informacji poufnych.
ms.openlocfilehash: bcecc13776b20f8b4c61eaf499a99397931fe498
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015374"
---
# <a name="custom-sensitive-information-type-filters-reference"></a>Odwołanie do niestandardowych filtrów typów informacji poufnych

W firmie Microsoft można zdefiniować filtry lub inne testy podczas tworzenia niestandardowych typów informacji poufnych (SIT).

## <a name="list-of-supported-filters-and-use-cases"></a>Lista obsługiwanych filtrów i przypadków użycia

### <a name="alldigitssame-exclude"></a>AllDigitsSame Exclude

Opis: Umożliwia wykluczenie dopasowania ze wszystkimi cyframi jako zduplikowanych cyfr, takich jak 111111111 lub 111-111-111

Definiowanie filtrów
```xml
<Filters id="ssn_filters">
    <Filter type="AllDigitsSameFilter"></Filter>
</Filters>
```

Używanie jej w pakiecie reguł na poziomie jednostki
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85"  filters="ssn_filters">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

Używanie jej w pakiecie reguł na poziomie wzorca
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="ssn_filters">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

### <a name="textmatchfilter-startswith"></a>Rozpoczyna się Filtrowanie TextMatchWith 

Opis: Umożliwia definiowanie początkowych znaków dla encji. Ma dwie warianty, uwzględnij i wyklucz.

Aby na przykład wykluczyć liczby zaczynające się od 0500, 91, 091, 010, z listy w ten sposób:

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Można użyć następującego kodu XML

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
Aby na przykład do listy dołączyć liczby zaczynające się od 0500, 91, 091, 0100, do następującej listy: 

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Można użyć następującego kodu XML

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-endswith"></a>TextMatchFilter EndsWith 

Opis. Pozwala zdefiniować znaki końcowe dla encji. 

Aby na przykład wykluczyć liczby kończące się na 0500 91 091, 0100 na liście w ten sposób:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Można użyć następującego kodu XML

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

Aby na przykład do listy dołączyć liczby kończące się na 0500, 91, 091, 0100, na następującej liście:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Można użyć następującego kodu XML

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction=" EndsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-full"></a>TextMatchFilter Full

Opis: Umożliwia zakazanie określonych dopasowania, aby uniemożliwić im wyzwalanie reguły. Na przykład wyklucz 4111111111111111 z listy prawidłowych kart kredytowych.

Aby na przykład wykluczyć numery kart kredytowych, takie 4111111111111111 i 3241891031113111 na liście w ten sposób:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Można użyć następującego kodu XML

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

Aby na przykład dołączyć numery kart kredytowych, 4111111111111111 i 3241891031113111 do listy w ten sposób:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Można użyć następującego kodu XML

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_false_positives_full">
</Filter>
```

### <a name="textmatchfilter-prefix"></a>Prefiks FiltrMafikatora_tekstu

Opis. Pozwala definiować poprzedzające znaki, które powinny być zawsze uwzględniane lub wykluczane. Jeśli na przykład numer karty kredytowej jest poprzedzony przez "Identyfikator zamówienia", usuń dopasowanie z prawidłowych dopasowań.

Aby na przykład wykluczyć wystąpienia numerów telefonów z Telefon i  zadzwonić do mnie pod ciągi  przed numerem telefonu, na liście w ten sposób:

- Telefon numer 091-8974-653278
- Telefon 45-124576532-123
- 45-124576532-123

Można użyć następującego kodu XML

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

Aby na przykład do listy dołączyć wystąpienia,  w których ciągi # numeru karty kredytowej i numeru karty kredytowej są dołączane do listy w ten sposób:

- Karta kredytowa 45-124576532-123 
- 45-124576532-123 (może to być numer telefonu)

Można użyć następującego kodu XML

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

### <a name="textmatchfilter-suffix"></a>Sufiks filtru TextMatchFilter

Opis. Pozwala definiować następujące znaki, które powinny być zawsze uwzględniane lub wykluczane. Jeśli na przykład po numerze karty kredytowej widnieje znak "/xuid", usuń je z prawidłowych dopasowań.

Jeśli na przykład na liście istnieje jeszcze pięć wystąpień czterocyfrowych, w postaci sufiksu, wyklucz wystąpienie w sposób następujący:

- 1234-5678-9321 4500 9870 6321 48925566
- 1234-5678-9321

Można użyć następującego kodu XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Regex_false_positives_suffix">
</Filter>

  <Regexid="Regex_false_positives_suffix">(\d{4}){5,}</Regex>
```
Aby na przykład wykluczyć wystąpienia, jeśli po nich **następuje /xuidsuffix**, jak po tej liście:

- 1234-5678-9321 /xuid
- 1234-5678-9321

Możesz użyć tego pliku XML

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

Aby na przykład dołączyć wystąpienie tylko wtedy, gdy następuje ono po ciągu **cvv** lub **wygasa**, na przykład dwa z tej listy:

- 45-124576532-123 
- 45-124576532-123 cvv 966
- 45-124576532-123 wygasa 23-03

Możesz użyć tego pliku XML

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

Filtry można zdefiniować we wszystkich usługach SIT lub we wzorcu. Poniżej przedstawiono kilka przykładów fragmentów kodu. 

### <a name="at-sensitive-information-type-level"></a>Na poziomie typu informacji poufnych

Filtry w encji — obejmie wszystkie wzorce podrzędne

Filtry zostaną zastosowane **do wszystkich** wystąpień sklasyfikowanych według dowolnych wzorców w tej encji/typu poufnego

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
```

### <a name="at-the-individual-pattern-of-the-sensitive-information-type-level"></a>Na indywidualnym wzorcu poziomu typów informacji poufnych

Filtry są filtrami tylko na poziomie wzorca.

Filtr zostanie zastosowany do wystąpień dopasowanych według wzorca.

```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Keyword_cc_verification" />
      </Pattern>
</Entity>
```


### <a name="at-sensitive-information-type-level-and-an-additional-filter-on-some-of-the-patterns-of-that-entity"></a>Na poziomie typu informacji poufnych i dodatkowy filtr dla niektórych wzorców tej encji

Filtry w miejscu Encja + wzorzec

Filtry zostaną zastosowane **do wszystkich** wystąpień sklasyfikowanych według dowolnych wzorców w tej encji/typu poufnego. Filtr poziomu deseniu filtruje wystąpienia zgodne z tym wzorcem.

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85" filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
``` 

 

## <a name="more-information"></a>Więcej informacji

- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)

- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)

- [Funkcje typów informacji poufnych](sit-functions.md)
