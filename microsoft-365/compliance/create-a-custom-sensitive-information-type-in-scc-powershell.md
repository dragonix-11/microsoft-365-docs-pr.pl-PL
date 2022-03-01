---
title: Tworzenie niestandardowego typu informacji poufnych przy użyciu programu PowerShell
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak utworzyć i zaimportować niestandardowy typ informacji poufnych dla zasad w Centrum zgodności.
ms.openlocfilehash: 89c215ca52b255a6e3aed72ff032cdd2475c0d87
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015381"
---
# <a name="create-a-custom-sensitive-information-type-using-powershell"></a>Tworzenie niestandardowego typu informacji poufnych przy użyciu programu PowerShell

W tym artykule pokazano, jak utworzyć plik pakietu *reguł* XML definiujący niestandardowe [typy informacji poufnych](sensitive-information-type-entity-definitions.md). W tym artykule opisano niestandardowy typ informacji poufnych identyfikujący identyfikator pracownika. Przykładowy kod XML z tego artykułu może być punktem wyjścia dla własnego pliku XML.

Aby uzyskać więcej informacji o typach informacji poufnych, zobacz [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md).

Po utworzeniu dobrze utworzonego pliku XML możesz przekazać go do programu Microsoft 365 programu PowerShell. Następnie możesz rozpocząć korzystanie z niestandardowych typów informacji poufnych w zasadach. Możesz przetestować jego skuteczność w wykrywaniu poufnych informacji zgodnie z zamierzeniem.

> [!NOTE]
> Jeśli nie potrzebujesz szczegółowej kontroli zapewnianą przez program PowerShell, możesz utworzyć niestandardowe typy informacji poufnych w Centrum zgodności platformy Microsoft 365. Aby uzyskać więcej informacji, [zobacz Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md).

## <a name="important-disclaimer"></a>Ważne zastrzeżenie

Pomoc techniczna firmy Microsoft nie może pomóc w tworzeniu definicji pasujących do zawartości.

W celu opracowania, testowania i debugowania niestandardowego dopasowywania zawartości musisz skorzystać z własnych wewnętrznych zasobów IT lub skorzystać z usług doradczych, takich jak Microsoft Consulting Services (MCS). Inżynierowie pomocy technicznej firmy Microsoft mogą zapewnić ograniczoną obsługę tej funkcji, ale nie mogą zagwarantować, że niestandardowe sugestie dopasowywania zawartości w pełni spełnią Twoje potrzeby.

Firma MCS może dostarczać wyrażenia regularne do celów testowych. Mogą także pomóc w rozwiązywaniu problemów z istniejącym wzorcem RegEx, który nie działa zgodnie z oczekiwaniami, z jednym określonym przykładem zawartości.

Zobacz [temat Potencjalne problemy sprawdzania poprawności, o których należy pamiętać](#potential-validation-issues-to-be-aware-of) w tym artykule.

Aby uzyskać więcej informacji na temat aparatu Boost.RegEx (dawniej znanego jako RegEx++), który jest używany do przetwarzania tekstu, zobacz [Boost.Regex 5.1.3](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/).

> [!NOTE]
> Jeśli używasz znaku "i" (&) jako części słowa kluczowego w niestandardowym typie informacji poufnych, musisz dodać kolejny termin ze spacjami wokół znaku. Na _przykład nie ._ `L&P``L & P`

## <a name="sample-xml-of-a-rule-package"></a>Przykładowy kod XML pakietu reguł

Oto przykładowy kod XML pakietu reguł, który utworzymy w tym artykule. W poniższych sekcjach wyjaśniono elementy i atrybuty.

```xml
<?xml version="1.0" encoding="UTF-16"?>
<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
<RulePack id="DAD86A92-AB18-43BB-AB35-96F7C594ADAA">
  <Version build="0" major="1" minor="0" revision="0"/>
  <Publisher id="619DD8C3-7B80-4998-A312-4DF0402BAC04"/>
  <Details defaultLangCode="en-us">
    <LocalizedDetails langcode="en-us">
      <PublisherName>Contoso</PublisherName>
      <Name>Employee ID Custom Rule Pack</Name>
      <Description>
      This rule package contains the custom Employee ID entity.
      </Description>
    </LocalizedDetails>
  </Details>
</RulePack>
<Rules>
<!-- Employee ID -->
  <Entity id="E1CC861E-3FE9-4A58-82DF-4BD259EAB378" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="65">
      <IdMatch idRef="Regex_employee_id"/>
    </Pattern>
    <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_employee_id"/>
      <Match idRef="Func_us_date"/>
    </Pattern>
    <Pattern confidenceLevel="85">
      <IdMatch idRef="Regex_employee_id"/>
      <Match idRef="Func_us_date"/>
      <Any minMatches="1">
        <Match idRef="Keyword_badge" minCount="2"/>
        <Match idRef="Keyword_employee"/>
      </Any>
      <Any minMatches="0" maxMatches="0">
        <Match idRef="Keyword_false_positives_local"/>
        <Match idRef="Keyword_false_positives_intl"/>
      </Any>
    </Pattern>
  </Entity>
  <Regex id="Regex_employee_id">(\s)(\d{9})(\s)</Regex>
  <Keyword id="Keyword_employee">
    <Group matchStyle="word">
      <Term>Identification</Term>
      <Term>Contoso Employee</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_badge">
    <Group matchStyle="string">
      <Term>card</Term>
      <Term>badge</Term>
      <Term caseSensitive="true">ID</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_false_positives_local">
    <Group matchStyle="word">
      <Term>credit card</Term>
      <Term>national ID</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_false_positives_intl">
    <Group matchStyle="word">
      <Term>identity card</Term>
      <Term>national ID</Term>
      <Term>EU debit card</Term>
    </Group>
  </Keyword>
  <LocalizedStrings>
    <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB378">
      <Name default="true" langcode="en-us">Employee ID</Name>
      <Description default="true" langcode="en-us">
      A custom classification for detecting Employee IDs.
      </Description>
      <Description default="false" langcode="de-de">
      Description for German locale.
      </Description>
    </Resource>
  </LocalizedStrings>
</Rules>
</RulePackage>
```

## <a name="what-are-your-key-requirements-rule-entity-pattern-elements"></a>Jakie są Twoje kluczowe wymagania? [Reguła, jednostka, elementy deseniu]

Należy zrozumieć podstawową strukturę schematu XML reguły. Znajomość tej struktury pomoże niestandardowych typom informacji poufnych identyfikować właściwą zawartość.

Reguła definiuje co najmniej jeden obiekt (nazywany także typami informacji poufnych). Każda jednostka definiuje jedną lub więcej wzorców. Wzorcem jest to, co zasady wyszukuje podczas oceny zawartości (na przykład wiadomości e-mail i dokumentów).

W znacznikach XML "reguły" oznaczają wzorce definiujące typ informacji poufnych. Nie kojarzenie odwołań do reguł w tym artykule z "warunkami" lub "akcjami", które są wspólne dla innych funkcji firmy Microsoft.

### <a name="simplest-scenario-entity-with-one-pattern"></a>Najprostszy scenariusz: jednostka z jednym wzorcem

Oto prosty scenariusz: zasady mają określać zawartość zawierającą dziewięciocyfrowe identyfikatory pracowników używane w organizacji. Wzorzec odwołuje się do wyrażenia regularnego reguły identyfikującego liczby dziewięciocyfrowe. Każda zawartość zawierająca dziewięciocyfrową liczbę spełnia warunki.

![Diagram encji z jednym wzorcem.](../media/4cc82dcf-068f-43ff-99b2-bac3892e9819.png)

Ten wzorzec może jednak identyfikować wszystkie liczby w postaci dziewięciucyfrowej, w tym dłuższe liczby lub inne, dziesiętne cyfry, które nie są identyfikatorami pracowników. Ten typ niechcianego dopasowania jest nazywany wynikami *fałszywie dodatnimi*.

### <a name="more-common-scenario-entity-with-multiple-patterns"></a>Bardziej typowe scenariusz: jednostka z wieloma wzorcami

Ze względu na możliwość wyników fałszywie dodatnich zazwyczaj do zdefiniowania encji używa się więcej niż jednego wzorca. Wiele wzorców stanowi dowód na to, że jest to jednostka docelowa. Na przykład dodatkowe słowa kluczowe, daty lub inny tekst mogą pomóc w zidentyfikowaniu oryginalnej jednostki (na przykład dziewięciocyfrowego numeru pracownika).

Aby na przykład zwiększyć prawdopodobieństwo zidentyfikowania zawartości zawierającej identyfikator pracownika, można zdefiniować inne wzorce wyszukiwania:

- Wzorzec określający datę zatrudnienia.
- Wzorzec określający zarówno datę zatrudnienia, jak i słowo kluczowe "Identyfikator pracownika".

![Diagram encji z wieloma wzorcami.](../media/c8dc2c9d-00c6-4ebc-889a-53b41a90024a.png)

W przypadku wielokrotnego dopasowania wzorcowego należy wziąć pod uwagę kilka ważnych punktów:

- Wzorce wymagające dodatkowych dowodów mają wyższy poziom ufności. W zależności od poziomu ufności można podjąć następujące działania:
  - Używaj bardziej restrykcyjnych akcji (takich jak blokowanie zawartości) z wyższymi ufnościami.
  - Używaj mniej restrykcyjnych akcji (takich jak wysyłanie powiadomień) przy dopasowaniach z mniejszą ufnością.

- Obsługa i elementy odwołują `IdMatch` się `Match` do słów kluczowych RegExes i słów kluczowych, które w rzeczywistości są elementami kluczowymi`Rule`, a nie .`Pattern` Do tych elementów obsługi odwołuje się element `Pattern`, ale są zawarte w `Rule`. To zachowanie oznacza, że do pojedynczej definicji elementu wsparcia, na przykład zwykłego wyrażenia lub listy słów kluczowych, może odwoływać się wiele obiektów i wzorców.

## <a name="what-entity-do-you-need-to-identify-entity-element-id-attribute"></a>Jaki element należy zidentyfikować? [Element encja, atrybut identyfikatora]

Jednostka to typ informacji poufnych, na przykład numer karty kredytowej, który ma dobrze zdefiniowany wzorzec. Każda jednostka ma unikatowy identyfikator GUID.

### <a name="name-the-entity-and-generate-its-guid"></a>Nadaj nazwę encji i generuj jej identyfikator GUID

1. W wybranej edytorze XML dodaj elementy `Rules` i `Entity` .
2. Dodaj komentarz zawierający nazwę encji niestandardowej, na przykład Identyfikator pracownika. Później dodasz nazwę jednostki do sekcji zlokalizowanych ciągów i ta nazwa będzie wyświetlana w centrum administracyjnym podczas tworzenia zasad.
3. Wygeneruj unikatowy identyfikator GUID dla swojej jednostki. Na przykład w Windows PowerShell można uruchomić polecenie `[guid]::NewGuid()`. Później identyfikator GUID zostanie również dodajony do zlokalizowanej sekcji ciągów encji.

![Xml markup showing Rules and Entity elements.](../media/c46c0209-0947-44e0-ac3a-8fd5209a81aa.png)

## <a name="what-pattern-do-you-want-to-match-pattern-element-idmatch-element-regex-element"></a>Jaki deseń chcesz dopasować? [Element deseniu, element IdMatch, element Regex]

Wzorzec zawiera listę informacji szukanych przez typ informacji poufnych. Wzorzec może zawierać wyrażenia RegExes, słowa kluczowe i funkcje wbudowane. Funkcje to zadanie, takie jak uruchamianie programu RegExes w celu znalezienia dat lub adresów. Typy informacji poufnych mogą mieć wiele wzorców o unikatowych ufnościach.

Na poniższym diagramie wszystkie wzorce odwołują się do tego samego wyrażenia regularnego. Ten kod RegEx wyszukuje dziewięciocyfrową `(\d{9})` liczbę otoczoną białymi miejscami `(\s) ... (\s)`. Do tego wyrażenia regularnego odwołuje się `IdMatch` element i jest to typowe wymaganie dla wszystkich wzorców wyszukiwania encji Identyfikator pracownika. `IdMatch` to identyfikator, który próbuje się dopasować. Element `Pattern` musi mieć dokładnie jeden `IdMatch` element.

![Ad markup XML showing multiple Pattern elements referencing single Regex element.](../media/8f3f497b-3b8b-4bad-9c6a-d9abf0520854.png)

Dopasowanie zgodne z wzorcem zwraca poziom ufności i liczby, którego można używać w warunkach określonych w twoich zasadach. Dodanie do zasad warunku wykrywania typu informacji poufnych pozwala edytować poziom ufności i liczności, jak pokazano na poniższym diagramie. W dalszej części tego artykułu wyjaśniono poziom ufności (nazywany również dokładnością dopasowań).

![Opcje liczby wystąpień i dokładności dopasowania.](../media/sit-confidence-level.png)

Wyrażenia regularne są bardzo zaawansowane, dlatego musisz wiedzieć o nich kilka problemów. Na przykład program RegEx, który identyfikuje zbyt dużo zawartości, może mieć wpływ na wydajność. Aby dowiedzieć się więcej o tych problemach, [zobacz sekcję](#potential-validation-issues-to-be-aware-of) Potencjalne problemy sprawdzania poprawności, o których należy pamiętać w dalszej części tego artykułu.

## <a name="do-you-want-to-require-additional-evidence-match-element-mincount-attribute"></a>Chcesz wymagać dodatkowych dowodów? [Match element, minCount atrybut]

Oprócz wzorca można `IdMatch`użyć elementu `Match` w celu wymagania dodatkowych dowodów dodatkowych, takich jak słowo kluczowe, RegEx, data lub adres.

A `Pattern` może zawierać wiele `Match` elementów:

- Bezpośrednio w elemencie `Pattern` .
- Połączone przy użyciu `Any` elementu.

`Match` są połączone niejawnym operatorem AND. Innymi słowy, wszystkie `Match` elementy muszą być zgodne ze wzorcem.

Za jego pomocą można `Any` wprowadzać operatory AND lub OR. Ten `Any` element został opisany w dalszej części tego artykułu.

Możesz użyć atrybutu opcjonalnego `minCount` , aby określić, ile wystąpień dopasowania należy znaleźć dla poszczególnych `Match` elementów. Możesz na przykład określić, że wzorzec jest spełniony tylko wtedy, gdy znajdują się co najmniej dwa słowa kluczowe z listy słów kluczowych.

![Znacznik XML pokazujący element Match z atrybutem minOccurs.](../media/607f6b5e-2c7d-43a5-a131-a649f122e15a.png)

### <a name="keywords-keyword-group-and-term-elements-matchstyle-and-casesensitive-attributes"></a>Słowa kluczowe [Elementy słowa kluczowego, grupy i terminu, matchStyle i caseSensitive atrybuty]

Jak opisano wcześniej, zidentyfikowanie informacji poufnych często wymaga dodatkowych słów kluczowych jako dowodów potwierdzających. Oprócz dopasowania numeru dziesiętnego możesz na przykład poszukać słów takich jak "kartka", "znaczek" lub "identyfikator" za pomocą elementu Słowo kluczowe. Element `Keyword` ma atrybut, do `ID` których może odwoływać się wiele `Match` elementów w wielu wzorcach lub jednostkach.

Słowa kluczowe są uwzględniane jako lista elementów `Term` w `Group` elemencie. Element `Group` ma atrybut z `matchStyle` dwiema możliwymi wartościami:

- **matchStyle="word"**: Dopasowanie wyrazu identyfikuje całe wyrazy otoczone białym znakiem lub innymi ogranicznikami. Zawsze używaj wyrazów **,** chyba że trzeba dopasować części wyrazów lub wyrazów w językach azjatyckich.

- **matchStyle="string"**: Dopasowanie ciągu identyfikuje ciągi niezależnie od tego, co się w nich znajduje. Na przykład "Identyfikator" będzie odpowiadać "oferty" i "pomysłowi". Używaj `string` tylko wtedy, gdy chcesz dopasować wyrazy azjatyckie lub jeśli Twoje słowo kluczowe może być zawarte w innych ciągach.

Atrybut elementu umożliwia dokładne `caseSensitive` `Term` dopasowanie zawartości do słowa kluczowego, z uwzględnieniem małych i wielkich liter.

![Znacznik XML przedstawiający pole Dopasuj elementy odwołujące się do słów kluczowych.](../media/e729ba27-dec6-46f4-9242-584c6c12fd85.png)

### <a name="regular-expressions-regex-element"></a>Wyrażenia regularne [Element Regex]

W tym przykładzie `ID` `IdMatch` jednostka pracownika używa już elementu w celu odwołania się do zwykłego wyrażenia we wzorcu: dziesiętnego numeru dziesiętnego otoczonego białym znakiem. `Match` `Regex` Ponadto za pomocą wzorca można odwołać się do elementu w celu zidentyfikowania dowodu potwierdzającego, takiego jak pięciocyfrowy lub dziewięciocyfrowy numer w formacie kodu pocztowego Stanów Zjednoczonych.

### <a name="additional-patterns-such-as-dates-or-addresses-built-in-functions"></a>Dodatkowe wzorce, takie jak daty lub adresy [wbudowane funkcje]

Typy informacji poufnych mogą również używać wbudowanych funkcji do identyfikowania dowodów potwierdzania. Może to być na przykład data w USA, data UE, data wygaśnięcia lub adres w USA. Microsoft 365 nie obsługuje przekazywania własnych funkcji niestandardowych. Jednak po utworzeniu niestandardowego typu informacji poufnych jednostka może odwoływać się do wbudowanych funkcji.

Na przykład identyfikator pracownika zawiera datę zatrudnienia, `Func_us_date` więc ta jednostka niestandardowa może używać wbudowanej funkcji do identyfikowania daty w formacie używanym w USA.

Aby uzyskać więcej informacji, zobacz [Funkcje typu informacji poufnych](sit-functions.md).

![Znacznik XML przedstawiający pole Wyboru elementu odwołującego się do wbudowanej funkcji.](../media/dac6eae3-9c52-4537-b984-f9f127cc9c33.png)

## <a name="different-combinations-of-evidence-any-element-minmatches-and-maxmatches-attributes"></a>Różne kombinacje dowodów [dowolny element, atrybuty minMatches i maxMatches]

W elemencie `Pattern` wszystkie i `IdMatch` elementy `Match` są połączone niejawnym operatorem AND. Innymi słowy, wszystkie dopasowania muszą być spełnione, aby wzorzec był spełniony.

Możesz utworzyć bardziej elastyczną logikę dopasowywania, używając elementu `Any` do grupowania `Match` elementów. Możesz na przykład użyć elementu `Any` , aby dopasować wszystkie, brak lub dokładny podzbiór jego elementów podrzędnych `Match` .

Element `Any` ma atrybuty opcjonalne `minMatches` `maxMatches` `Match` i atrybuty, za pomocą których można określić, ile elementów podrzędnych musi spełniać wzorzec. Te atrybuty określają *liczbę elementów*`Match`, a nie liczbę znalezionych wystąpień dowodów na dopasowania. Aby zdefiniować minimalną liczbę wystąpień określonego dopasowania, na przykład dwa słowa kluczowe z listy, `minCount` `Match` użyj atrybutu dla elementu (patrz powyżej).

### <a name="match-at-least-one-child-match-element"></a>Match at least one child Match element

Aby wymagać tylko minimalnej liczby `Match` elementów, można użyć tego `minMatches` atrybutu. W efekcie te elementy `Match` są połączone niejawnym operatorem LUB. Ten `Any` element jest zadowoleni, jeśli zostanie znaleziona data w formacie US lub słowo kluczowe z jednej z list.

```xml
<Any minMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-an-exact-subset-of-any-children-match-elements"></a>Dopasowanie dokładnego podzbioru dowolnych elementów dopasowania dzieci

Aby wymagać dokładnej liczby `Match` elementów, należy ustawić `minMatches` tę `maxMatches` samą wartość. Ten `Any` element jest zadowoleni tylko w przypadku, gdy zostanie znaleziona dokładnie jedna data lub słowo kluczowe. Jeśli istnieje więcej dopasowań, wzorzec nie jest do siebie dopasowany.

```xml
<Any minMatches="1" maxMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-none-of-children-match-elements"></a>Dopasuj żadne elementy dopasowania dzieci

Jeśli chcesz wymagać braku określonych dowodów, aby wzorzec był spełniony, możesz ustawić zarówno wartość minMatches, jak i maxMatches na 0. Może to być przydatne, jeśli masz listę słów kluczowych lub inne dowody, które mogą wskazywać na wynik fałszywie dodatni.

Na przykład jednostka identyfikatora pracownika wyszukuje słowo kluczowe "karta", ponieważ może się ona odnosić do "identyfikatora". Jeśli jednak w tej zawartości pojawia się tylko fraza "karta kredytowa", to mało prawdopodobne, aby w treści pojawiała się fraza "Karta kredytowa". Dlatego możesz dodać "kartę kredytową" jako słowo kluczowe do listy terminów, które chcesz wykluczyć z spełniania tego wzorca.

```xml
<Any minMatches="0" maxMatches="0" >
    <Match idRef="Keyword_false_positives_local" />
    <Match idRef="Keyword_false_positives_intl" />
</Any>
```

### <a name="match-a-number-of-unique-terms"></a>Liczba unikatowych terminów

Jeśli chcesz dopasować kilka unikatowych terminów, użyj *parametru uniqueResults* ustawionego na wartość *true*, jak pokazano w poniższym przykładzie:

```xml
<Pattern confidenceLevel="75">
    <IdMatch idRef="Salary_Revision_terms" />
    <Match idRef=" Salary_Revision_ID " minCount="3" uniqueResults="true" />
</Pattern>
```

W tym przykładzie wzorzec jest zdefiniowany dla poprawki płac z co najmniej trzema unikatowymi dopasowaniami.

## <a name="how-close-to-the-entity-must-the-other-evidence-be-patternsproximity-attribute"></a>Jak blisko jednostki muszą znajdować się inne informacje? [atrybut patternsProximity]

Typ informacji poufnych szuka wzorca reprezentującego identyfikator pracownika, a w ramach tego wzorca szuka także dowodu w rodzaju dowodu potwierdzającego, takiego jak słowo kluczowe, takie jak "Identyfikator". Warto pamiętać, że im bliżej tych dowodów, tym większe prawdopodobieństwo, że będzie to rzeczywisty identyfikator pracownika. Możesz ustalić, jak blisko innych dowodów we wzorcu musi znajdować się jednostka, używając wymaganego atrybutu patternsProximity elementu Entity.

![Xml markup showing patternsProximity attribute.](../media/e97eb7dc-b897-4e11-9325-91c742d9839b.png)

Dla każdego wzorca w encji wartość atrybutu patternsProximity definiuje odległość (w znakach Unicode) od lokalizacji IdMatch dla wszystkich innych dopasowaniach określonych dla tego wzorca. Okno odległości jest zakotwiczone przez lokalizację IdMatch, a okno rozciąga się do lewej i prawej strony pozycji IdMatch.

![Diagram okna odległości.](../media/b593dfd1-5eef-4d79-8726-a28923f7c31e.png)

Poniższy przykład ilustruje, jak okno sąsiedztwa wpływa na wzorzec dopasowania, w którym element IdMatch dla encji niestandardowej Identyfikator pracownika wymaga co najmniej jednego dopasowania potwierdzenia słowa kluczowego lub daty. Tylko identyfikator 1 odpowiada, ponieważ w przypadku identyfikatorów ID2 i ID3 nie znaleziono dowodu tylko częściowego potwierdzenia w granicach okna sąsiedztwa.

![Diagram dowodu potwierdzania i okna sąsiedztwa.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

W przypadku wiadomości e-mail treść wiadomości i każdy załącznik są traktowane jako osobne elementy. Oznacza to, że okno odległości nie rozciąga się poza koniec każdego z tych elementów. W przypadku każdego elementu (załącznika lub treści) w tym elementie muszą się znajdować zarówno informacje idMatch, jak i dowód  corroborative.

## <a name="what-are-the-right-confidence-levels-for-different-patterns-confidencelevel-attribute-recommendedconfidence-attribute"></a>Jakie są właściwe poziomy ufności dla różnych wzorców? [atrybut confidenceLevel, zalecany atrybutConfidence]

Im więcej dowodów jest wymaganych we wzorcu, tym większa pewność, że po dopasowaniu wzorca zidentyfikowano rzeczywistą jednostkę (taką jak identyfikator pracownika). Na przykład masz większą pewność co do wzorca, który wymaga dziewięciocyfrowego numeru identyfikacyjnego, daty zatrudnienia i słowa kluczowego w niedalekiej odległości, niż w przypadku wzorca wymagającego tylko dziewięciocyfrowego numeru identyfikacyjnego.

Element Pattern ma wymagany atrybut ufności Poziom. Można sobie myślisz o wartości ufności Poziom (liczba całkowita z przedziału od 1 do 100) jako unikatowego identyfikatora dla każdego wzorca w encji — wzorce w encji muszą mieć przypisane różne poziomy ufności. Dokładna wartość liczby całkowitej nie ma znaczenia — wystarczy wybrać liczby, które mają sens dla zespołu zgodności. Po przesłaniu niestandardowego typu informacji poufnych i utworzeniu zasad można odwoływać się do tych poziomów ufności w warunkach tworzyć reguły.

![Xml markup showing Pattern elements with different values for confidenceLevel attribute.](../media/sit-xml-markedup-2.png)

Oprócz przedziału ufności Dla każdego wzorca encja ma zalecany atrybutConfidence. Zalecany atrybut ufności można określić jako domyślny poziom ufności reguły. Jeśli podczas tworzenia reguły w zasadach nie zostanie określony poziom ufności dla reguły, która ma być używania, reguła ta będzie odpowiadać zalecanemu poziomowi ufności dla encji. Pamiętaj, że zalecany atrybutConfidence jest obowiązkowy dla każdego identyfikatora jednostki w pakiecie reguł, jeśli go brakuje, nie będzie można zapisywać zasad, które korzystają z typu informacji poufnych.

## <a name="do-you-want-to-support-other-languages-in-the-ui-of-the-compliance-center-localizedstrings-element"></a>Czy chcesz obsługiwać inne języki w interfejsie użytkownika Centrum zgodności? [Element LocalizedStrings]

Jeśli Zespół zgodności tworzy zasady w Microsoft 365 ustawieniach regionalnych i w różnych językach za pomocą Centrum zgodności, możesz podać zlokalizowane wersje nazwy i opisu niestandardowego typu informacji poufnych. Jeśli Twój zespół zgodności Microsoft 365 w języku, który obsługujesz, w interfejsie użytkownika będzie widzieć nazwę zlokalizowany.

![Konfiguracja liczby wystąpień i dokładności dopasowania.](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

Element Reguły musi zawierać element LocalizedStrings, który zawiera element Zasobu, który odwołuje się do identyfikatora GUID encji niestandardowej. Z kolei każdy element Zasobu zawiera co najmniej jeden element Name (Nazwa) i Description (Opis), dla których każdy z nich używa atrybutu langcode w celu zapewnienia zlokalizowanego ciągu dla określonego języka.

![Znacznik XML przedstawiający zawartość elementu LocalizedStrings.](../media/a96fc34a-b93d-498f-8b92-285b16a7bbe6.png)

Należy pamiętać, że ciągi zlokalizowane są wykorzystywane tylko w celu zachowania niestandardowego typu informacji poufnych w interfejsie użytkownika Centrum zgodności. Zlokalizowanych ciągów nie można używać do zapewnienia różnych zlokalizowanych wersji listy słów kluczowych lub wyrażenia regularnego.

## <a name="other-rule-package-markup-rulepack-guid"></a>Inna znacznik wyboru pakietu reguł [Identyfikator GUID pakietu RulePack]

Na koniec na początku każdego pola RulePackage znajdują się pewne ogólne informacje, które należy wypełnić. Możesz użyć następującej  znacznika jako szablonu i zamienić znak ". . ." z własnymi informacjami.

Co najważniejsze, należy wygenerować identyfikator GUID dla zestawu RulePack. Powyżej wygenerowano identyfikator GUID dla encji; jest to drugi identyfikator GUID dla reguły RulePack. Istnieje kilka sposobów generowania identyfikatorów GUID, ale można to zrobić łatwo w programie PowerShell, wpisując [guid]::NewGuid().

Ważny jest również element Version (Wersja). Podczas przekazywania pakietu reguł po raz pierwszy Microsoft 365 numer wersji. Później, jeśli zaktualizujemy pakiet reguł i przekażemy nową wersję, zaktualizuj numer wersji lub Microsoft 365 nie wdroży pakietu reguł.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
  <RulePack id=". . .">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id=". . ." />
    <Details defaultLangCode=". . .">
      <LocalizedDetails langcode=" . . . ">
         <PublisherName>. . .</PublisherName>
         <Name>. . .</Name>
         <Description>. . .</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
  . . .
 </Rules>
</RulePackage>
```

Po zakończeniu element RulePack powinien wyglądać tak.

![Xml markup showing RulePack element.](../media/fd0f31a7-c3ee-43cd-a71b-6a3813b21155.png)

## <a name="validators"></a>Validators

Microsoft 365 nasyć procesory funkcji dla często używanych jako prawidłowych identyfikatorów (SIT). Oto ich lista.

### <a name="list-of-currently-available-validators"></a>Lista obecnie dostępnych validatorów

- `Func_credit_card`
- `Func_ssn`
- `Func_unformatted_ssn`
- `Func_randomized_formatted_ssn`
- `Func_randomized_unformatted_ssn`
- `Func_aba_routing`
- `Func_south_africa_identification_number`
- `Func_brazil_cpf`
- `Func_iban`
- `Func_brazil_cnpj`
- `Func_swedish_national_identifier`
- `Func_india_aadhaar`
- `Func_uk_nhs_number`
- `Func_Turkish_National_Id`
- `Func_australian_tax_file_number`
- `Func_usa_uk_passport`
- `Func_canadian_sin`
- `Func_formatted_itin`
- `Func_unformatted_itin`
- `Func_dea_number_v2`
- `Func_dea_number`
- `Func_japanese_my_number_personal`
- `Func_japanese_my_number_corporate`

Umożliwia to zdefiniowanie własnego konta RegEx i ich weryfikację. Aby użyć prawidłowych wartości, zdefiniuj własne ustawienia RegEx `Validator` i użyj tej właściwości, aby dodać procesor funkcji do wyboru. Po jej zdefiniowanym określonej funkcji można używać tego wyrażenia RegEx w programie SIT.

W poniższym przykładzie wyrażenie regularne — Regex_credit_card_AdditionalDelimiters dla karty kredytowej, a następnie sprawdzana jest poprawność jej użycia przy użyciu funkcji sprawdzania poprawności karty kredytowej przy użyciu funkcji Func_credit_card jako sprawdzania poprawności.

```xml
<Regex id="Regex_credit_card_AdditionalDelimiters" validators="Func_credit_card"> (?:^|[\s,;\:\(\)\[\]"'])([0-9]{4}[ -_][0-9]{4}[ -_][0-9]{4}[ -_][0-9]{4})(?:$|[\s,;\:\(\)\[\]"'])</Regex>
<Entity id="675634eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
<Pattern confidenceLevel="85">
<IdMatch idRef="Regex_credit_card_AdditionalDelimiters" />
<Any minMatches="1">
<Match idRef="Keyword_cc_verification" />
<Match idRef="Keyword_cc_name" />
<Match idRef="Func_expiration_date" />
</Any>
</Pattern>
</Entity>
```

Microsoft 365 udostępnia dwa ogólne prawidłowe wartości

### <a name="checksum-validator"></a>Sprawdzanie prawidłowego sumy

W tym przykładzie zdefiniowano sprawdzanie poprawności identyfikatora pracownika w celu zweryfikowania wartości RegEx dla employeeID.

```xml
<Validators id="EmployeeIDChecksumValidator">
<Validator type="Checksum">
<Param name="Weights">2, 2, 2, 2, 2, 1</Param>
<Param name="Mod">28</Param>
<Param name="CheckDigit">2</Param> <!-- Check 2nd digit -->
<Param name="AllowAlphabets">1</Param> <!— 0 if no Alphabets -->
</Validator>
</Validators>
<Regex id="Regex_EmployeeID" validators="ChecksumValidator">(\d{5}[A-Z])</Regex>
<Entity id="675634eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
<Pattern confidenceLevel="85">
<IdMatch idRef="Regex_EmployeeID"/>
</Pattern>
</Entity>
```

### <a name="date-validator"></a>Date Validator

W tym przykładzie dla części RegEx, której część to data, jest zdefiniowany prawidłowy data.

```xml
<Validators id="date_validator_1"> <Validator type="DateSimple"> <Param name="Pattern">DDMMYYYY</Param> <!—supported patterns DDMMYYYY, MMDDYYYY, YYYYDDMM, YYYYMMDD, DDMMYYYY, DDMMYY, MMDDYY, YYDDMM, YYMMDD --> </Validator> </Validators>
<Regex id="date_regex_1" validators="date_validator_1">\d{8}</Regex>
```

## <a name="changes-for-exchange-online"></a>Zmiany dotyczące Exchange Online

Wcześniej można było używać programu Exchange Online PowerShell do importowania niestandardowych typów informacji poufnych na platformie DLP. Teraz niestandardowe typy informacji poufnych mogą być używane zarówno w centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a>, jak i w Centrum zgodności. W ramach tego ulepszenia należy użyć programu PowerShell w Centrum zgodności do importowania niestandardowych typów informacji poufnych — nie można ich już importować z programu Exchange PowerShell. Niestandardowe typy informacji poufnych będą nadal działać tak samo jak wcześniej. Może jednak upłynieć do godziny, zanim zmiany wprowadzone w niestandardowych typach informacji poufnych w Centrum zgodności pojawią się w centrum Exchange administracyjnego.

Zwróć uwagę, że w Centrum zgodności możesz użyć polecenia cmdlet **[New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage)** w celu przekazania pakietu reguł. (Wcześniej w centrum administracyjnym Exchange było używane polecenie cmdlet **ClassificationRuleCollection**).

## <a name="upload-your-rule-package"></a>Upload pakietu reguł

Aby przekazać pakiet reguł, wykonaj następujące czynności:

1. Zapisz go jako plik .xml kodowaniem Unicode.

2. [Połączenie do Centrum zgodności w programie PowerShell](/powershell/exchange/exchange-online-powershell)

3. Należy stosować następującą składnię:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('PathToUnicodeXMLFile'))
   ```

   W tym przykładzie jest przesyłany plik XML Unicode o nazwie MyNewRulePack.xml z folderu C:\Moje dokumenty.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\MyNewRulePack.xml'))
   ```

   Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage).

   > [!NOTE]
   > Maksymalna obsługiwana liczba pakietów reguł wynosi 10, ale każdy pakiet może zawierać definicję wielu typów informacji poufnych.

4. Aby sprawdzić, czy nowy typ informacji poufnych został utworzony pomyślnie, wykonaj dowolną z następujących czynności:

   - Uruchom polecenie [cmdlet Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) , aby sprawdzić, czy na liście znajduje się nowy pakiet reguł:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Uruchom polecenie [cmdlet Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) , aby sprawdzić, czy na liście znajduje się typ informacji poufnych:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     W przypadku niestandardowych typów informacji poufnych Publisher wartość właściwości będzie inna niż wartość firmy Microsoft Corporation.

   - Zamień \<Name\> wartość Name (Nazwa) poufnego typu informacji (przykład: Identyfikator pracownika) i uruchom polecenie cmdlet [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) :

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="potential-validation-issues-to-be-aware-of"></a>Potencjalne problemy sprawdzania poprawności, o których należy pamiętać

Podczas przekazywania pliku XML pakietu reguł system sprawdza poprawność pliku XML i sprawdza znane złe wzorce oraz oczywiste problemy z wydajnością. Oto niektóre znane problemy, które są sprawdzane przez sprawdzanie poprawności — zwykłe wyrażenie:

- Bezbłędne asertywności w wyrażeniu regularnym powinny mieć tylko stałą długość. Asercja o zmiennej długości spowoduje błędy.

  Na przykład nie `"(?<=^|\s|_)"` zostanie zweryfikowana poprawności. Pierwszy wzorzec (`^`) ma długość zerową, natomiast kolejne dwa wzorce (`\s` i `_`) mają długość jedną. Innym sposobem na pisanie tego wyrażenia regularnego jest `"(?:^|(?<=\s|_))"`.

- Nie można rozpocząć ani zakończyć alternatorem `|`, który odpowiada wszystkim, ponieważ jest to uznawane za puste dopasowanie.

  Na przykład lub nie `|a` `b|` przejdzie weryfikacji.

- Nie można zaczynać ani kończyć wzorcem `.{0,m}` działania, który nie ma żadnego celu funkcjonalnego i tylko pogarsza wydajność.

  Na przykład lub nie `.{0,50}ASDF` `ASDF.{0,50}` przejdzie weryfikacji.

- Nie mogą mieć `.{0,m}` , `.{1,m}` ani w grupach, ani nie mogą mieć `.\*` ani `.+` w grupach.

  Na przykład nie `(.{0,50000})` zostanie zweryfikowana poprawności.

- Nie może mieć żadnych znaków z ani `{0,m}` powtórzeniami `{1,m}` w grupach.

  Na przykład nie `(a\*)` zostanie zweryfikowana poprawności.

- Nie można rozpoczynać ani kończyć się na `.{1,m}`; zamiast tego używać .`.`

  Na przykład nie `.{1,m}asdf` zostanie zweryfikowana poprawności. Zamiast tego użyj funkcji `.asdf`.

- Nie może mieć niepowiązanego powtarzania (takiego jak `*` lub `+`) w grupie.

  Nie zostanie na przykład `(xx)\*` zweryfikowana `(xx)+` poprawności.

- Słowa kluczowe mają długość maksymalnie 50 znaków.  Jeśli w grupie znajduje się słowo kluczowe przekraczające tę grupę, sugerowane rozwiązanie to utworzenie grupy terminów jako słownika słów kluczowych i [](./create-a-keyword-dictionary.md) odwołanie się do identyfikatora GUID słownika słów kluczowych w strukturze XML jako części elementu Entity for Match lub idMatch w pliku.

- Każdy niestandardowy typ informacji poufnych może mieć łącznie maksymalnie 2048 słów kluczowych.

- Maksymalny rozmiar słowników słów kluczowych w jednej dzierżawie to 480 KB skompresowanych w celu zapewnienia zgodności z limitami schematu AD. Podczas tworzenia niestandardowych typów informacji poufnych można odwoływać się do tego samego słownika tyle razy, ile jest to konieczne. Zacznij od utworzenia niestandardowych list słów kluczowych w typie informacji poufnych i użyj słowników słów kluczowych, jeśli na liście słów kluczowych znajduje się więcej niż 2048 słów kluczowych lub słowo kluczowe ma długość większą niż 50 znaków.

- W dzierżawie dozwolonych jest maksymalnie 50 typów informacji poufnych dotyczących słownika opartego na słowach kluczowych.

- Upewnij się, że każdy element encja zawiera zalecany atrybutConfidence.

- Podczas korzystania z polecenia cmdlet programu PowerShell maksymalny rozmiar zwracanych danych to około 1 megabajt.   Ma to wpływ na rozmiar pliku XML pakietu reguł. Ograniczenie przekazywanego pliku do 770 kilobajtów jako sugerowanego limitu spójnych wyników bez błędu podczas przetwarzania.

- Struktura XML nie wymaga formatowania znaków, takich jak spacje, tabulatory czy wpisy powrotu karetki/kanału liniowego.  Pamiętaj o tym podczas optymalizowania miejsca podczas przekazywania. Narzędzia, takie jak Microsoft Visual Code, zapewniają funkcje linii sprzężenia do kompaktowania pliku XML.

Jeśli niestandardowy typ informacji poufnych zawiera problem, który może wpłynąć na wydajność, nie zostanie on przekazany i może zostać wyświetlony jeden z tych komunikatów o błędach:

- `Generic quantifiers which match more content than expected (e.g., '+', '*')`

- `Lookaround assertions`

- `Complex grouping in conjunction with general quantifiers`

## <a name="recrawl-your-content-to-identify-the-sensitive-information"></a>Odszyfruj zawartość, aby zidentyfikować poufne informacje

Microsoft 365 przeszukiwarce wyszukiwania do identyfikowania i klasyfikowania informacji poufnych w zawartości witryny. Zawartość w SharePoint Online i OneDrive dla Firm jest automatycznie recrowana przy każdej aktualizacji. Jednak w celu zidentyfikowania nowego niestandardowego typu informacji poufnych we wszystkich istniejących treściach ta zawartość musi zostać wpisana ponownie.

W Microsoft 365 nie można ręcznie zażądać ponownego przeszyfru całej organizacji, ale można ręcznie zażądać ponownej przeszytki dla zbioru witryn, listy lub biblioteki. Aby uzyskać więcej informacji, [zobacz Ręczne żądanie](/sharepoint/crawl-site-content) przeszukiwania i ponownego indeksowania witryny, biblioteki lub listy.

## <a name="reference-rule-package-xml-schema-definition"></a>Informacje: definicja schematu XML pakietu reguł

Możesz skopiować tę znacznik, zapisać ją jako plik XSD i użyć jej do zweryfikowania pliku XML pakietu reguł.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:mce="http://schemas.microsoft.com/office/2011/mce"
           targetNamespace="http://schemas.microsoft.com/office/2011/mce"
           xmlns:xs="https://www.w3.org/2001/XMLSchema"
           elementFormDefault="qualified"
           attributeFormDefault="unqualified"
           id="RulePackageSchema">
  <!-- Use include if this schema has the same target namespace as the schema being referenced, otherwise use import -->
  <xs:element name="RulePackage" type="mce:RulePackageType"/>
  <xs:simpleType name="LangType">
    <xs:union memberTypes="xs:language">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value=""/>
        </xs:restriction>
      </xs:simpleType>
    </xs:union>
  </xs:simpleType>
  <xs:simpleType name="GuidType" final="#all">
    <xs:restriction base="xs:token">
      <xs:pattern value="[0-9a-fA-F]{8}\-([0-9a-fA-F]{4}\-){3}[0-9a-fA-F]{12}"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="RulePackageType">
    <xs:sequence>
      <xs:element name="RulePack" type="mce:RulePackType"/>
      <xs:element name="Rules" type="mce:RulesType">
        <xs:key name="UniqueRuleId">
          <xs:selector xpath="mce:Entity|mce:Affinity|mce:Version/mce:Entity|mce:Version/mce:Affinity"/>
          <xs:field xpath="@id"/>
        </xs:key>
        <xs:key name="UniqueProcessorId">
          <xs:selector xpath="mce:Regex|mce:Keyword|mce:Fingerprint"></xs:selector>
          <xs:field xpath="@id"/>
        </xs:key>
        <xs:key name="UniqueResourceIdRef">
          <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
          <xs:field xpath="@idRef"/>
        </xs:key>
        <xs:keyref name="ReferencedRuleMustExist" refer="mce:UniqueRuleId">
          <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
          <xs:field xpath="@idRef"/>
        </xs:keyref>
        <xs:keyref name="RuleMustHaveResource" refer="mce:UniqueResourceIdRef">
          <xs:selector xpath="mce:Entity|mce:Affinity|mce:Version/mce:Entity|mce:Version/mce:Affinity"/>
          <xs:field xpath="@id"/>
        </xs:keyref>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="RulePackType">
    <xs:sequence>
      <xs:element name="Version" type="mce:VersionType"/>
      <xs:element name="Publisher" type="mce:PublisherType"/>
      <xs:element name="Details" type="mce:DetailsType">
        <xs:key name="UniqueLangCodeInLocalizedDetails">
          <xs:selector xpath="mce:LocalizedDetails"/>
          <xs:field xpath="@langcode"/>
        </xs:key>
        <xs:keyref name="DefaultLangCodeMustExist" refer="mce:UniqueLangCodeInLocalizedDetails">
          <xs:selector xpath="."/>
          <xs:field xpath="@defaultLangCode"/>
        </xs:keyref>
      </xs:element>
      <xs:element name="Encryption" type="mce:EncryptionType" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="VersionType">
    <xs:attribute name="major" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="minor" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="build" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="revision" type="xs:unsignedShort" use="required"/>
  </xs:complexType>
  <xs:complexType name="PublisherType">
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="LocalizedDetailsType">
    <xs:sequence>
      <xs:element name="PublisherName" type="mce:NameType"/>
      <xs:element name="Name" type="mce:RulePackNameType"/>
      <xs:element name="Description" type="mce:OptionalNameType"/>
    </xs:sequence>
    <xs:attribute name="langcode" type="mce:LangType" use="required"/>
  </xs:complexType>
  <xs:complexType name="DetailsType">
    <xs:sequence>
      <xs:element name="LocalizedDetails" type="mce:LocalizedDetailsType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="defaultLangCode" type="mce:LangType" use="required"/>
  </xs:complexType>
  <xs:complexType name="EncryptionType">
    <xs:sequence>
      <xs:element name="Key" type="xs:normalizedString"/>
      <xs:element name="IV" type="xs:normalizedString"/>
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="RulePackNameType">
    <xs:restriction base="xs:token">
      <xs:minLength value="1"/>
      <xs:maxLength value="64"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="NameType">
    <xs:restriction base="xs:normalizedString">
      <xs:minLength value="1"/>
      <xs:maxLength value="256"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="OptionalNameType">
    <xs:restriction base="xs:normalizedString">
      <xs:minLength value="0"/>
      <xs:maxLength value="256"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="RestrictedTermType">
    <xs:restriction base="xs:string">
      <xs:minLength value="1"/>
      <xs:maxLength value="100"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="RulesType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Entity" type="mce:EntityType"/>
        <xs:element name="Affinity" type="mce:AffinityType"/>
        <xs:element name="Version" type="mce:VersionedRuleType"/>
      </xs:choice>
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Regex" type="mce:RegexType"/>
        <xs:element name="Keyword" type="mce:KeywordType"/>
        <xs:element name="Fingerprint" type="mce:FingerprintType"/>
        <xs:element name="ExtendedKeyword" type="mce:ExtendedKeywordType"/>
      </xs:choice>
      <xs:element name="LocalizedStrings" type="mce:LocalizedStringsType"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="EntityType">
    <xs:sequence>
      <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
      <xs:element name="Version" type="mce:VersionedPatternType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
    <xs:attribute name="patternsProximity" type="mce:ProximityType" use="required"/>
    <xs:attribute name="recommendedConfidence" type="mce:ProbabilityType"/>
    <xs:attribute name="workload" type="mce:WorkloadType"/>
  </xs:complexType>
  <xs:complexType name="PatternType">
    <xs:sequence>
      <xs:element name="IdMatch" type="mce:IdMatchType"/>
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
  </xs:complexType>
  <xs:complexType name="AffinityType">
    <xs:sequence>
      <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
      <xs:element name="Version" type="mce:VersionedEvidenceType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
    <xs:attribute name="evidencesProximity" type="mce:ProximityType" use="required"/>
    <xs:attribute name="thresholdConfidenceLevel" type="mce:ProbabilityType" use="required"/>
    <xs:attribute name="workload" type="mce:WorkloadType"/>
  </xs:complexType>
  <xs:complexType name="EvidenceType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
  </xs:complexType>
  <xs:complexType name="IdMatchType">
    <xs:attribute name="idRef" type="xs:string" use="required"/>
  </xs:complexType>
  <xs:complexType name="MatchType">
    <xs:attribute name="idRef" type="xs:string" use="required"/>
    <xs:attribute name="minCount" type="xs:positiveInteger" use="optional"/>
    <xs:attribute name="uniqueResults" type="xs:boolean" use="optional"/>
  </xs:complexType>
  <xs:complexType name="AnyType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="minMatches" type="xs:nonNegativeInteger" default="1"/>
    <xs:attribute name="maxMatches" type="xs:nonNegativeInteger" use="optional"/>
  </xs:complexType>
  <xs:simpleType name="ProximityType">
    <xs:union>
      <xs:simpleType>
        <xs:restriction base='xs:string'>
          <xs:enumeration value="unlimited"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType>
        <xs:restriction base="xs:positiveInteger">
          <xs:minInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:union>
  </xs:simpleType>
  <xs:simpleType name="ProbabilityType">
    <xs:restriction base="xs:integer">
      <xs:minInclusive value="1"/>
      <xs:maxInclusive value="100"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="WorkloadType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Exchange"/>
      <xs:enumeration value="Outlook"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="EngineVersionType">
    <xs:restriction base="xs:token">
      <xs:pattern value="^\d{2}\.01?\.\d{3,4}\.\d{1,3}$"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="VersionedRuleType">
    <xs:choice maxOccurs="unbounded">
      <xs:element name="Entity" type="mce:EntityType"/>
      <xs:element name="Affinity" type="mce:AffinityType"/>
    </xs:choice>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:complexType name="VersionedPatternType">
    <xs:sequence>
      <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:complexType name="VersionedEvidenceType">
    <xs:sequence>
      <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:simpleType name="FingerprintValueType">
    <xs:restriction base="xs:string">
      <xs:minLength value="2732"/>
      <xs:maxLength value="2732"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FingerprintType">
    <xs:simpleContent>
      <xs:extension base="mce:FingerprintValueType">
        <xs:attribute name="id" type="xs:token" use="required"/>
        <xs:attribute name="threshold" type="mce:ProbabilityType" use="required"/>
        <xs:attribute name="shingleCount" type="xs:positiveInteger" use="required"/>
        <xs:attribute name="description" type="xs:string" use="optional"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="RegexType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="KeywordType">
    <xs:sequence>
      <xs:element name="Group" type="mce:GroupType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="id" type="xs:token" use="required"/>
  </xs:complexType>
  <xs:complexType name="GroupType">
    <xs:sequence>
      <xs:choice>
        <xs:element name="Term" type="mce:TermType" maxOccurs="unbounded"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="matchStyle" default="word">
      <xs:simpleType>
        <xs:restriction base="xs:NMTOKEN">
          <xs:enumeration value="word"/>
          <xs:enumeration value="string"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
  <xs:complexType name="TermType">
    <xs:simpleContent>
      <xs:extension base="mce:RestrictedTermType">
        <xs:attribute name="caseSensitive" type="xs:boolean" default="false"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="ExtendedKeywordType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="LocalizedStringsType">
    <xs:sequence>
      <xs:element name="Resource" type="mce:ResourceType" maxOccurs="unbounded">
      <xs:key name="UniqueLangCodeUsedInNamePerResource">
        <xs:selector xpath="mce:Name"/>
        <xs:field xpath="@langcode"/>
      </xs:key>
      <xs:key name="UniqueLangCodeUsedInDescriptionPerResource">
        <xs:selector xpath="mce:Description"/>
        <xs:field xpath="@langcode"/>
      </xs:key>
    </xs:element>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="ResourceType">
    <xs:sequence>
      <xs:element name="Name" type="mce:ResourceNameType" maxOccurs="unbounded"/>
      <xs:element name="Description" type="mce:DescriptionType" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="idRef" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="ResourceNameType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="default" type="xs:boolean" default="false"/>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="DescriptionType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="default" type="xs:boolean" default="false"/>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
</xs:schema>
```

## <a name="more-information"></a>Więcej informacji

- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Funkcje typów informacji poufnych](sit-functions.md)
