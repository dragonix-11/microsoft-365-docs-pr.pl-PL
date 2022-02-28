---
title: Informacje o formacie SKOS dla SharePoint taksonomii
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
ms.localizationpriority: high
description: Informacje o formacie SKOS dla SharePoint taksonomii
ms.openlocfilehash: 95183b64d76a70f69d08cd5a3c9dcf76f4e83bce
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62989749"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>Informacje o formacie SKOS dla SharePoint taksonomii

Ten artykuł zawiera słownictwo RDF używane do [SharePoint taksonomii](/dotnet/api/microsoft.sharepoint.taxonomy) i jest oparte na [języku SKOS](https://www.w3.org/TR/skos-primer/). Aby uzyskać numerowanie tej składni RDF, użyj funkcji ŻÓŁW.RDF.[](https://www.w3.org/TR/turtle/)

W poniższej tabeli przedstawiono [odpowiedniki SKOS](https://www.w3.org/TR/skos-primer/) dla [słownictwa SharePoint taksonomii](/dotnet/api/microsoft.sharepoint.taxonomy). SharePoint wartości [SKOS](https://www.w3.org/TR/skos-primer/), które nie mają odpowiednika SharePoint taksonomii.

|SharePoint taksonomii|Odpowiednik SKOS|
|:-----------------|:--------------|
|Sharepoint-taksonomia:Termin|skos:Concept|
|sharepoint-taksonomia:TermSet|skos:ConceptScheme|
|sharepoint-taksonomia:inTermSet|skos:inScheme|
|sharepoint-taksonomia:hasTopLevelTerm|skos:hasTopConcept|
|sharepoint-taksonomia:topLevelTermOf|skos:topConceptOf|
|sharepoint-taksonomia:etykieta domyślna|skos:prefLabel|
|sharepoint-taksonomia:termSetName|skos:prefLabel|
|sharepoint-taksonomia:nazwa_właściwości|skos:prefLabel|
|sharepoint-taksonomia:etykieta inna|skos:altLabel|
|sharepoint-taksonomia:opis|skos:definition|
|sharepoint-taksonomia:element nadrzędny|skos:broader|
|sharepoint-taksonomia:dziecko|skos:węższy|

W poniższej tabeli przedstawiono jednostki słownictwa SharePoint taksonomii pochodzące z [OWL](https://www.w3.org/TR/owl2-primer/).

|SharePoint słownictwa taksonomii|Pochodny od OWL|
|:-----------------------------|:----------------------|
|sharepoint-taksonomia:isAvailableForTagging|owl:datatypeproperty|
|sharepoint-taksonomia:SharedCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taksonomia:LocalCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taksonomia:CustomPropertyForTermSet|owl:ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>SharePoint słownictwa taksonomii

Taksonomia to formalny system klasyfikacji. Taksonomia grupuje wyrazy, etykiety i terminy opisujące informacje, a następnie rozmieszcza grupy w hierarchii.

**Sharepoint-taksonomia:Termin**

Reprezentuje termin lub słowo kluczowe w hierarchii zarządzanych metadanych.

Termin [jest](/dotnet/api/microsoft.sharepoint.taxonomy.term) niepodzielną jednostką niepodzielną SharePoint [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). Każdy [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) należy do [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) należącego do [grupy terminów](/dotnet/api/microsoft.sharepoint.taxonomy.group).

Składnia definiowania [terminu jest](/dotnet/api/microsoft.sharepoint.taxonomy.term) następująca:

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Termin [ten](/dotnet/api/microsoft.sharepoint.taxonomy.term) występuje w obrębie [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Etykieta Domyślna to [nazwa terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) wyświetlana w graficznej reprezentacji. Pola wymagane do zdefiniowania [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) to:

- sharepoint-taksonomia:etykieta domyślna
- sharepoint-taksonomia:inTermSet

Termin [może](/dotnet/api/microsoft.sharepoint.taxonomy.term) :

- Należy hierarchicznie związek z innym [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term) pod warunkiem, że oba [terminy](/dotnet/api/microsoft.sharepoint.taxonomy.term) należą do [tego samego zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Należy mieć wiele [terminów podrzędnych](/dotnet/api/microsoft.sharepoint.taxonomy.term), ale tylko jeden termin [nadrzędny](/dotnet/api/microsoft.sharepoint.taxonomy.term).
- Nie zdefiniowano [nadrzędnego terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) , jeśli jest to element najwyższego wielopoziomowego zestawu [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Have one defaultLabel, per [TermStore working](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) language.
- Nie istnieje, jeśli nie zawiera [nadrzędnego terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) ani najwyższego zestawu rekordów.[](/dotnet/api/microsoft.sharepoint.taxonomy.termset)
- Na tym samym poziomie hierarchii musi być tylko unikatowa etykieta domyślna.

**sharepoint-taksonomia:TermSet**

Reprezentuje hierarchiczny lub płaski zestaw obiektów terminów, nazywany "zestawem terminów".

Jak sama nazwa wskazuje, zestaw terminów jest zestawem [terminów](/dotnet/api/microsoft.sharepoint.taxonomy.term). Termin [w](/dotnet/api/microsoft.sharepoint.taxonomy.term) [łacie magazynu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) musi należeć do [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Żaden [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) nie może istnieć niezależnie.

Składnia definiowania [zestawu terminów jest](/dotnet/api/microsoft.sharepoint.taxonomy.termset) następująca:

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

[Zestawy terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) są logicznie grupowane w [grupach okresów](/dotnet/api/microsoft.sharepoint.taxonomy.group). Pole wymagane do zdefiniowania [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) jest:

- sharepoint-taksonomia:termSetName

W przypadku podanej nazwy termSetName nie jest unikatowa w grupie [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group), program SharePoint dołącza na końcu nazwy liczbę w celu zachowania unikatowości nazwy termSetName(y).

**sharepoint-taksonomia:hasTopLevelTerm**

SharePoint używa tej właściwości do zamapowania najważniejszego terminu w [](/dotnet/api/microsoft.sharepoint.taxonomy.term) obiekcie [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), który jest punktem wejścia do hierarchii terminów w [](/dotnet/api/microsoft.sharepoint.taxonomy.term) [zestawach terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Jest to odwrotna zależność do taksonomii sharepoint-taksonomii:topLevelTermOf.

Składnia definiowania tego jest następująca:

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> Nie można zdefiniować najwyższego [poziomu termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) [nadrzędny.](/dotnet/api/microsoft.sharepoint.taxonomy.term)

**sharepoint-taksonomia:topLevelTermOf**

Sharepoint-taksonomia:topLevelTermOf jest odwrotnością taksonomii sharepoint:hasTopLevelTerm

Składnia definiowania tego jest następująca:

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-taksonomia:inTermSet**

Skorzystaj z tej funkcji, [aby zamapować termin](/dotnet/api/microsoft.sharepoint.taxonomy.term) na [zestaw okresów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Termin [może](/dotnet/api/microsoft.sharepoint.taxonomy.term) istnieć tylko w jednym [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint tej właściwości podczas [definiowania terminu](https://github.com/MicrosoftDocs/microsoft-365-docs-pr/blob/3a3cd54dd076b18bdff1d43b3e342897f8704c23/microsoft-365/contentunderstanding/skos-format-reference.md#term).

## <a name="required-labels"></a>Wymagane etykiety

Organizacja może przed rozpoczęciem korzystania z zarządzanych metadanych wykonać staranne planowanie. Ilość planowania, która należy wykonać, zależy od tego, jak formalna jest taksonomia. Zależy to również od tego, ile kontroli chcesz narzucić na metadane. Na każdym poziomie hierarchii należy skonfigurować etykiety wymagane dla zestawu terminów lub okresów.

Termin może mieć co najmniej jedną etykietę w języku domyślnym oraz zero lub więcej etykiet w języku innym niż domyślny. Jeśli termin ma etykiety w języku, jedna z etykiet musi być etykietą domyślną.

**sharepoint-taksonomia:etykieta domyślna**

Tej domyślnej etykiety lexowej należy używać [w przypadku terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term) , który jest parametrem wymaganym dla [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term). Użyj, aby wizualnie przedstawiać [termin](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Składnia definiowania etykiety domyślnej to:

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Etykieta domyślna zawiera dwie części — ciąg i tag języka. Język musi być jednym z języków [roboczych sklepu TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . Etykieta domyślna musi być unikatowa dla wszystkich [warunków](/dotnet/api/microsoft.sharepoint.taxonomy.term) w tym samym [zestawu](/dotnet/api/microsoft.sharepoint.taxonomy.termset) terminów na tym samym poziomie hierarchii.

**sharepoint-taksonomia:termSetName**

Pobiera i ustawia nazwę bieżącego obiektu TermSet.

To etykieta lexyczna dla [zestawu warunków (TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset)) w języku pracy [magazynu](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) terminów. Jest to parametr wymagany dla [zestawu terminów](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Wizualne przedstawianie [zestawu okresów](/dotnet/api/microsoft.sharepoint.taxonomy.termset).

Składnia definiowania terminuSetName jest następująca:

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-taksonomia:nazwa_właściwości**

Pobiera i ustawia nazwę właściwości bieżącego obiektu TermSet.

To jest etykieta lexczna dla taksonomii sharepoint-taksonomii:SharedCustomPropertyForTerm, sharepoint-taksonomia:LocalCustomPropertyForTerm i sharepoint-taksonomia:CustomPropertyForTermSet w języku pracy witryny [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .

Właściwość sharepoint-taksonomia:nazwa_właściwości jest traktowana jak klucz właściwości CustomProperty.

Składnia definiowania nazwy właściwości to:

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>Etykiety opcjonalne

Możesz również dodać etykiety opcjonalne do taksonomii.

**sharepoint-taksonomia:etykieta inna**

Jest to alternatywna etykieta lexyczna dla [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Składnia definiowania etykiety innej jest następująca:

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>Relacje semantyczne

Taksonomie mają hierarchiczną, a czasami prostą "powiązaną" relację skojarzoną z terminem, ale niektóre z nich mają "relacje semantyczne" lub utworzone niestandardowe.

**sharepoint-taksonomia:element nadrzędny**

To hierarchiczne relacja terminu [z](/dotnet/api/microsoft.sharepoint.taxonomy.term) innym [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term). Termin [może](/dotnet/api/microsoft.sharepoint.taxonomy.term) być terminem najwyższego [](/dotnet/api/microsoft.sharepoint.taxonomy.term) poziomu w [zestawach](/dotnet/api/microsoft.sharepoint.taxonomy.termset) terminów, ale na wypadek, gdy nie musi mieć nadrzędnego [terminu](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Składnia definiowania elementu nadrzędnego jest następująca:

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

Oznacza to, że termA jest elementem nadrzędnym, a termA jest elementem podrzędnym.

**sharepoint-taksonomia:dziecko**

Obiekt zawiera co najmniej jedno wystąpienie podrzędne zestawu okresów, do których dostęp można uzyskać za pośrednictwem właściwości TermSets. Ta klasa zawiera również metody tworzenia nowych podrzędnych obiektów termset. Uprawnienia do edytowania wystąpień podrzędnego zestawu okresów i okresów są określone w grupie.

To hierarchiczne relacja terminu [z](/dotnet/api/microsoft.sharepoint.taxonomy.term) innym [terminem](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Składnia definiowania dziecka jest następująca:

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

Oznacza to, że termA jest elementem nadrzędnym, a termA jest elementem podrzędnym.

## <a name="documentation-notes"></a>Uwagi dotyczące dokumentacji

W tej sekcji omówiono taksonomię podaną w firmie Microsoft. SharePoint. Przestrzeń nazw taksonomii.

**sharepoint-taksonomia:opis**

Jest to szczegółowe objaśnienie dowolnego [podmiotu słownictwa SharePoint taksonomii](/dotnet/api/microsoft.sharepoint.taxonomy).

Składnia dodawania opisu jest następująca:

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>Właściwości niestandardowe

Pobiera kolekcję niestandardowych obiektów właściwości dla bieżącego obiektu Term ze słownika tylko do odczytu.

Właściwości niestandardowe to pary wartości kluczy, które można zdefiniować dla określonego terminu [](/dotnet/api/microsoft.sharepoint.taxonomy.term) lub zestawu terminów [w celu](/dotnet/api/microsoft.sharepoint.taxonomy.termset) dalszego opisu tego terminu lub [](/dotnet/api/microsoft.sharepoint.taxonomy.term) [zestawu.](/dotnet/api/microsoft.sharepoint.taxonomy.termset) SharePoint określa klucz właściwości niestandardowej za pomocą właściwościName.

**sharepoint-taksonomia:CustomPropertyForTermSet**

Składnia definiowania tego jest następująca:

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**sharepoint-taksonomia:SharedCustomPropertyForTerm**

Jeśli właściwość niestandardowa terminu [musi](/dotnet/api/microsoft.sharepoint.taxonomy.term) zostać zrealizowana razem z terminem[, to](/dotnet/api/microsoft.sharepoint.taxonomy.term) w przypadku ponownego użycia [](/dotnet/api/microsoft.sharepoint.taxonomy.term) terminu w innym miejscu należy zdefiniować go w obszarze SharedCustomPropertyForTerm.

Składnia definiowania tego jest następująca:

```SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**sharepoint-taksonomia:LocalCustomPropertyForTerm**

Jeśli właściwość niestandardowa terminu nie [](/dotnet/api/microsoft.sharepoint.taxonomy.term) musi być przesunana razem z terminem[, ponowne](/dotnet/api/microsoft.sharepoint.taxonomy.term) użycie tego terminu [](/dotnet/api/microsoft.sharepoint.taxonomy.term) będzie konieczne w obszarze LocalCustomPropertyForTerm.

Składnia definiowania tego jest następująca:

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>Właściwości danych

Na każdym poziomie hierarchii można skonfigurować określone właściwości danych dla zestawu okresów lub okresów.

**sharepoint-taksonomia:isAvailableForTagging**

Ten sposób określania, czy [termin lub](/dotnet/api/microsoft.sharepoint.taxonomy.term) zestaw [termów](/dotnet/api/microsoft.sharepoint.taxonomy.termset) jest dostępny w SharePoint listach i bibliotekach.

Składnia tej funkcji jest następująca:

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>Domena i zakres

W poniższej tabeli opisano domenę i zakres SharePoint słownictwa taksonomii.

|Predykaty/czasownik|Znaczenie|Domain (Domena)|Zakres|
|:--------------|:------|:-----|:----|
inTermSet|W zestawie okresów|Termin|Zestaw okresów|
inTermGroup|W grupie termin|TermSet|TermGroup|
topLevelTermOf|to najwyższego poziomu termin|Termin|TermSet|
hasTopLevelTerm|Ma termin najwyższego poziomu|Zestaw okresów|Termin|
termSetName|Zestaw okresów ma nazwę|Termin|Zwykły literał|
etykieta domyślna|Termin ma etykietę domyślną|Termin|Zwykły literał|
etykieta inna|Termin ma inną etykietę|Termin|Zwykły literał|
propertyName|Ma etykietę właściwości|SharedCustomPropertyForTerm, LocalCustomPropertyForTerm, CustomPropertyForTermSet |Wartość logiczna, ciąg, liczba całkowita, dziesiętna, podwójna|
|opis|Zawiera opis|Wszystkie|Zwykły literał|
|element nadrzędny|Ma rodzica|Termin|Termin|
|dziecko|Ma dziecko|Termin|Termin|
|isAvailableForTagging|Dostępne do otagowania|Termin, zestaw okresów|Wartość logiczna|
|SharedCustomPropertyForTerm|Ma udostępnioną właściwość niestandardową|Termin|Wartość logiczna, ciąg, liczba całkowita, dziesiętny, podwójna|
|LocalCustomPropertyForTerm|Ma lokalną właściwość niestandardową|Termin|Wartość logiczna, ciąg, liczba całkowita, dziesiętna, podwójna|
|CustomPropertyForTermSet|Ma właściwość niestandardową|TermSet|Wartość logiczna, ciąg, liczba całkowita, dziesiętna, podwójna|

[Prawidłowe scenariusze SKOS](https://www.w3.org/TR/skos-primer/), SharePoint nie zezwalają na [taksonomię](/dotnet/api/microsoft.sharepoint.taxonomy):

- Nadmiarowość hierarchiczna — koncepcję [SKOS](https://www.w3.org/TR/skos-primer/) można dołączyć do kilku szerszej koncepcji jednocześnie, ale taksonomia programu SharePoint:Termin może mieć tylko jedną taksonomię sharepoint:element nadrzędny, przez co zależność cykliczna warunków również nie jest dozwolona.
- Warunki oddzielone nie są dozwolone SharePoint taksonomii. Każda taksonomia programu SharePoint:Termin powinien mieć element sharepoint-taksonomia:element nadrzędny lub powinien to być taksonomia programu SharePoint:topLevelTerm zestawu terminów.
- SharePoint taksonomii nie obsługuje relacji skojarzeń.
- SharePoint tylko 2 typy relacji hierarchicznych — sharepoint-taksonomia:nadrzędny i sharepoint-taksonomia:dziecko.
- W [przeciwieństwie do SKOS](https://www.w3.org/TR/skos-primer/) relacji hierarchicznej w SharePoint słownictwa taksonomii, można określić tylko przy użyciu warunków w tym samym zestawu terminów.

## <a name="see-also"></a>Zobacz też

[Importowanie zestawu terminów przy użyciu formatu opartego na SKOS](import-term-set-skos.md)