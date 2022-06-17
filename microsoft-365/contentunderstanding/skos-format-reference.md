---
title: Dokumentacja formatu SKOS dla taksonomii SharePoint
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
ms.localizationpriority: high
description: Dokumentacja formatu SKOS dla taksonomii SharePoint
ms.openlocfilehash: c9dbaae4242155522eec2fff0f7fd4d721e697cc
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139678"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>Dokumentacja formatu SKOS dla taksonomii SharePoint

Ten artykuł zawiera słownictwo RDF używane do reprezentowania [taksonomii SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy) i jest oparte na [SKOS](https://www.w3.org/TR/skos-primer/). Do serializacji tej składni RDF użyj [ŻÓŁWIA](https://www.w3.org/TR/turtle/) RDF.

W poniższej tabeli [przedstawiono odpowiedniki SKOS](https://www.w3.org/TR/skos-primer/) dla [słownictwa taksonomii SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy). SharePoint nie obsługuje wartości [SKOS](https://www.w3.org/TR/skos-primer/), które nie mają odpowiednika taksonomii SharePoint.

|taksonomia SharePoint|Odpowiednik SKOS|
|:-----------------|:--------------|
|sharepoint-taksonomia:Termin|skos:Concept|
|sharepoint-taksonomia:TermSet|skos:ConceptScheme|
|sharepoint-taksonomia:inTermSet|skos:inScheme|
|sharepoint-taksonomia:hasTopLevelTerm|skos:hasTopConcept|
|sharepoint-taksonomia:topLevelTermOf|skos:topConceptOf|
|sharepoint-taksonomia:defaultLabel|skos:prefLabel|
|sharepoint-taksonomia:termSetName|skos:prefLabel|
|sharepoint-taksonomia:propertyName|skos:prefLabel|
|sharepoint-taksonomia:otherLabel|skos:altLabel|
|sharepoint-taksonomia:description|skos:definition|
|sharepoint-taksonomia:parent|skos:broader|
|sharepoint-taksonomia:child|skos:narrower|

W poniższej tabeli przedstawiono jednostki słownictwa taksonomii SharePoint pochodzące z [protokołu OWL](https://www.w3.org/TR/owl2-primer/).

|słownictwo taksonomii SharePoint|Pochodzi z OWL|
|:-----------------------------|:----------------------|
|sharepoint-taksonomia:isAvailableForTagging|owl:datatypeproperty|
|sharepoint-taksonomia:SharedCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taksonomia:LocalCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taksonomia:CustomPropertyForTermSet|owl:ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>słownictwo taksonomii SharePoint

Taksonomia jest formalnym systemem klasyfikacji. Taksonomia grupuje słowa, etykiety i terminy, które coś opisują, a następnie rozmieszcza grupy w hierarchii.

**sharepoint-taksonomia:Termin**

Reprezentuje termin lub słowo kluczowe w hierarchii zarządzanych metadanych.

[Termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) jest niepodzielną jednostką magazynu SharePoint [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). Każdy [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) należy do [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) , który należy do [grupy termgroup](/dotnet/api/microsoft.sharepoint.taxonomy.group).

Składnia definiująca [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) jest następująca:

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

[Termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) obowiązkowo istnieje w ramach [zestawu TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). DefaultLabel to nazwa [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) wyświetlana w wizualnej reprezentacji. Pola wymagane do zdefiniowania [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) obejmują:

- sharepoint-taksonomia:defaultLabel
- sharepoint-taksonomia:inTermSet

[Termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) może:

- Bądź hierarchicznie powiązany z innym [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term) , który jest dostarczany, [oba warunki](/dotnet/api/microsoft.sharepoint.taxonomy.term) należą do tego samego [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Mieć wiele [terminów podrzędnych](/dotnet/api/microsoft.sharepoint.taxonomy.term), ale tylko jeden [termin nadrzędny](/dotnet/api/microsoft.sharepoint.taxonomy.term).
- Nie zdefiniowano [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) nadrzędnego, jeśli jest to topLevelTermOf [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Na język roboczy [magazynu TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) należy mieć jedną wartość defaultLabel.
- Nie istnieje, jeśli nie zawiera [terminu nadrzędnego](/dotnet/api/microsoft.sharepoint.taxonomy.term) ani nie jest topLevelTermOf [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Na tym samym poziomie hierarchicznym ma tylko unikatowy element defaultLabel.

**sharepoint-taksonomia:TermSet**

Reprezentuje hierarchiczny lub płaski zestaw obiektów terminów znanych jako "TermSet".

Jak sugeruje nazwa, TermSet jest zestawem [warunków](/dotnet/api/microsoft.sharepoint.taxonomy.term). [Termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) w magazynie [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) musi należeć do [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Żaden [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) nie może istnieć niezależnie.

Składnia definiująca [zestaw terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) to:

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

[Zestawy terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) są logicznie pogrupowane w [grupach terminów](/dotnet/api/microsoft.sharepoint.taxonomy.group). Pole wymagane do zdefiniowania [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) to:

- sharepoint-taksonomia:termSetName

W przypadku podanej nazwy termSetName nie jest unikatowa w grupie [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group), SharePoint dołącza liczbę na końcu nazwy, aby zachować unikatowość nazw termSetName.s.

**sharepoint-taksonomia:hasTopLevelTerm**

SharePoint używa tej właściwości do mapowania najwięcej [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.term) w [zestawie terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset), który jest punktem wejścia do hierarchii [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.term) w [zestawie terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Jest to odwrotna relacja do elementu sharepoint-taksonomia:topLevelTermOf.

Składnia do zdefiniowania tego elementu to:

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> Nie można zdefiniować [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) najwyższego poziomu [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) nadrzędnego.

**sharepoint-taksonomia:topLevelTermOf**

Sharepoint-taksonomia:topLevelTermOf jest odwrotnością elementu sharepoint-taksonomia:hasTopLevelTerm

Składnia do zdefiniowania tego elementu to:

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-taksonomia:inTermSet**

Służy do mapowania [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) na [zestaw terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). [Termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) może istnieć tylko w jednym [zestawie terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint wymaga tej właściwości podczas [definiowania terminu](#sharepoint-taxonomy-vocabulary).

## <a name="required-labels"></a>Wymagane etykiety

Twoja organizacja może chcieć dokładnie zaplanować, zanim zaczniesz używać zarządzanych metadanych. Ilość planowania, które należy zrobić, zależy od tego, jak formalna jest taksonomia. Zależy to również od tego, ile kontroli chcesz nałożyć na metadane. Na każdym poziomie hierarchii należy skonfigurować wymagane etykiety dla zestawu terminów lub terminów.

Termin może mieć co najmniej jedną etykietę w języku domyślnym i zero lub więcej etykiet w języku innym niż domyślny. Jeśli termin zawiera etykiety w języku, jedną z etykiet musi być etykieta domyślna.

**sharepoint-taksonomia:defaultLabel**

Użyj tej domyślnej etykiety leksykalne dla [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) , który jest parametrem wymaganym dla [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term). Służy do wizualnego reprezentowania [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Składnia definiująca wartość defaultLabel to:

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Etykieta defaultLabel zawiera dwie części — ciąg i tag języka. Język musi być jednym z języków roboczych [magazynu TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . Wartość defaultLabel musi być unikatowa dla wszystkich [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.term) w tym samym [zestawie terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) na tym samym poziomie hierarchicznym.

**sharepoint-taksonomia:termSetName**

Pobiera i ustawia nazwę bieżącego obiektu TermSet.

Etykieta leksykalna dla zestawu [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) w języku roboczym [Magazynu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . Jest to parametr wymagany dla zestawu [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Służy do wizualnego reprezentowania [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset).

Składnia definiująca terminSetName to:

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-taksonomia:propertyName**

Pobiera i ustawia nazwę właściwości dla bieżącego obiektu TermSet.

Jest to etykieta leksykalna dla elementu sharepoint-taksonomii:SharedCustomPropertyForTerm, sharepoint-taksonomia:LocalCustomPropertyForTerm i sharepoint-taksonomia:CustomPropertyForTermSet w języku roboczym [magazynu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .

Element sharepoint-taksonomia:propertyName jest traktowany jako klucz właściwości CustomProperty.

Składnia definiująca propetyName to:

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>Etykiety opcjonalne

Możesz również dodać opcjonalne etykiety do taksonomii.

**sharepoint-taksonomia:otherLabel**

Jest to alternatywna etykieta leksykalna dla [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Składnia definiująca element otherLabel to:

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>Relacje semantyczne

Taksonomie mają hierarchiczną, a czasami prostą relację asocjacyjną "powiązanego terminu", ale niektóre z nich mają "relacje semantyczne" lub niestandardowe relacje.

**sharepoint-taksonomia:parent**

Ten hierarchicznie wiąże [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) z innym [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term). [Termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) może być [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term) najwyższego poziomu zestawu [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset), ale jeśli nie, musi mieć [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) nadrzędny.

Składnia definiująca element nadrzędny to:

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

Oznacza to, że terma jest elementem nadrzędnym, a terma jest elementem podrzędnym.

**sharepoint-taksonomia:child**

Obiekt zawiera co najmniej jedno podrzędne wystąpienie zestawu terminów, do których można uzyskać dostęp za pośrednictwem właściwości TermSets. Ta klasa udostępnia również metody tworzenia nowych podrzędnych obiektów TermSet. Uprawnienia do edytowania wystąpień podrzędnych terminów i zestawów terminów są określone w grupie.

Ten hierarchicznie wiąże [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) z innym [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Składnia definiująca element podrzędny to:

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

Oznacza to, że terma jest elementem nadrzędnym, a terma jest elementem podrzędnym.

## <a name="documentation-notes"></a>Informacje o dokumentacji

W tej sekcji omówiono taksonomię opisaną w artykule Microsoft. SharePoint. Przestrzeń nazw taksonomii.

**sharepoint-taksonomia:description**

Jest to szczegółowe wyjaśnienie każdej [jednostki słownictwa taksonomii SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy).

Składnia dodawania opisu to:

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>Właściwości niestandardowe

Pobiera kolekcję obiektów właściwości niestandardowych dla bieżącego obiektu Term ze słownika tylko do odczytu.

Właściwości niestandardowe to pary klucz-wartości, które można zdefiniować dla [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) lub [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) w celu dalszego opisu [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) lub [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint określa klucz właściwości niestandardowej za pomocą właściwości propertyName.

**sharepoint-taksonomia:CustomPropertyForTermSet**

Składnia do zdefiniowania tego elementu to:

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**sharepoint-taksonomia:SharedCustomPropertyForTerm**

Jeśli właściwość niestandardowa [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) musi być przenoszona wraz z [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term), podczas ponownego używania [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) w innym miejscu należy zdefiniować ją w obszarze SharedCustomPropertyForTerm.

Składnia do zdefiniowania tego elementu to:

```SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**sharepoint-taksonomia:LocalCustomPropertyForTerm**

Jeśli właściwość niestandardowa [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) nie musi być przenoszona wraz z [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term), podczas ponownego używania [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) w innym miejscu należy zdefiniować go w obszarze LocalCustomPropertyForTerm.

Składnia do zdefiniowania tego elementu to:

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>Właściwości danych

Na każdym poziomie hierarchii można skonfigurować określone właściwości danych dla zestawu terminów lub terminów.

**sharepoint-taksonomia:isAvailableForTagging**

Użyj tego polecenia, aby określić, czy [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) lub [zestaw terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) jest dostępny w SharePoint list i bibliotek.

W tym celu składnia to:

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>Domena i zakres

W poniższej tabeli opisano domenę i zakres słownictwa taksonomii SharePoint.

|Predykaty/czasownik|Znaczenie|Domain (Domena)|Zakres|
|:--------------|:------|:-----|:----|
inTermSet|W zestawie terminów|Okres|Zestaw terminów|
inTermGroup|W grupie terminów|Zestaw terminów|TermGroup|
topLevelTermOf|Jest terminem najwyższego poziomu|Okres|Zestaw terminów|
hasTopLevelTerm|Ma termin najwyższego poziomu|Zestaw terminów|Okres|
termSetName|Zestaw terminów ma nazwę|Okres|Zwykły literał|
defaultLabel|Termin ma etykietę domyślną|Okres|Zwykły literał|
otherLabel|Termin ma inną etykietę|Okres|Zwykły literał|
Propertyname|Ma etykietę właściwości|SharedCustomPropertyForTerm, LocalCustomPropertyForTerm, CustomPropertyForTermSet |Wartość logiczna, ciąg, liczba całkowita, liczba dziesiętna, podwójna|
|Opis|Ma opis|Wszystkie|Zwykły literał|
|Nadrzędny|Ma element nadrzędny|Okres|Okres|
|Dziecko|Ma element podrzędny|Okres|Okres|
|isAvailableForTagging|Jest dostępny do tagowania|Termin, zestaw terminów|Wartość logiczna|
|SharedCustomPropertyForTerm|Ma udostępnioną właściwość niestandardową|Okres|Wartość logiczna, ciąg, liczba całkowita, liczba dziesiętna, podwójna|
|LocalCustomPropertyForTerm|Ma lokalną właściwość niestandardową|Okres|Wartość logiczna, ciąg, liczba całkowita, liczba dziesiętna, podwójna|
|CustomPropertyForTermSet|Ma właściwość niestandardową|Zestaw terminów|Wartość logiczna, ciąg, liczba całkowita, liczba dziesiętna, podwójna|

[Prawidłowe scenariusze SKOS](https://www.w3.org/TR/skos-primer/), które [SharePoint taksonomii](/dotnet/api/microsoft.sharepoint.taxonomy), nie zezwalają na:

- Nadmiarowość hierarchiczna — koncepcja [SKOS](https://www.w3.org/TR/skos-primer/) może być jednocześnie dołączona do kilku szerszych pojęć, ale właściwość sharepoint-taksonomia:Termin może mieć tylko jedną taksonomię sharepoint-taksonomię:nadrzędną, stąd zależność cykliczna, warunków również nie jest dozwolona.
- Oddzielone terminy nie są dozwolone w SharePoint taksonomii. Każda taksonomia sharepoint:Term powinna mieć element sharepoint-taksonomia:parent lub powinien być elementem sharepoint-taksonomia:topLevelTermOf zestawu terminów.
- SharePoint taksonomia nie obsługuje stosunków asocjacyjnych.
- SharePoint taksonomia zezwala tylko na 2 typy relacji hierarchicznych — sharepoint-taksonomia:parent i sharepoint-Taxonomy:child.
- W przeciwieństwie do [usługi SKOS](https://www.w3.org/TR/skos-primer/) relację hierarchiczną w SharePoint słownictwa taksonomii można ustanowić tylko za pomocą warunków w ramach tego samego zestawu terminów.

## <a name="see-also"></a>Zobacz też

[Importowanie zestawu terminów przy użyciu formatu opartego na SKOS](import-term-set-skos.md)
