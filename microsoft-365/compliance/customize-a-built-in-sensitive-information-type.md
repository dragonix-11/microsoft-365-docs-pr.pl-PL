---
title: Dostosuj wbudowany typ informacji poufnych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak utworzyć niestandardowy typ informacji poufnych, który umożliwi korzystanie z reguł spełniających potrzeby organizacji.
ms.openlocfilehash: f0ebc1bb4b13f9e31ca1a8a1967fce007105cfe6
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753897"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>Dostosuj wbudowany typ informacji poufnych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Podczas wyszukiwania poufnych informacji w zawartości należy opisać te informacje w tak zwanej *regule*. Ochrona przed utratą danych w Microsoft Purview (DLP) zawiera reguły dla najczęściej używanych typów informacji poufnych, których można używać od razu. Aby korzystać z tych reguł, należy je uwzględnić w zasadach. Może się okazać, że chcesz dostosować te wbudowane reguły do konkretnych potrzeb organizacji i możesz to zrobić, tworząc niestandardowy typ informacji poufnych. W tym temacie przedstawiono sposób dostosowywania pliku XML zawierającego istniejącą kolekcję reguł w celu wykrycia szerszego zakresu potencjalnych informacji o kartach kredytowych.

Możesz skorzystać z tego przykładu i zastosować go do innych wbudowanych typów informacji poufnych. Aby uzyskać listę domyślnych typów informacji poufnych i definicji XML, zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md).

## <a name="export-the-xml-file-of-the-current-rules"></a>Eksportowanie pliku XML bieżących reguł

Aby wyeksportować kod XML, musisz [połączyć się z Centrum zabezpieczeń i zgodności za pośrednictwem zdalnego programu PowerShell.](/powershell/exchange/connect-to-scc-powershell)

1. W programie PowerShell wpisz następujące polecenie, aby wyświetlić reguły organizacji na ekranie. Jeśli nie utworzono własnych, zobaczysz tylko domyślne, wbudowane reguły z etykietą "Pakiet reguł firmy Microsoft".

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. Zapisz reguły organizacji w zmiennej, wpisując następujące polecenie. Przechowywanie czegoś w zmiennej sprawia, że jest ona łatwo dostępna później w formacie, który działa w przypadku zdalnych poleceń programu PowerShell.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. Utwórz sformatowany plik XML ze wszystkimi danymi, wpisując następujące polecenie.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > Upewnij się, że używasz lokalizacji pliku, w której pakiet reguł jest faktycznie przechowywany. `C:\custompath\` jest symbolem zastępczym.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>Znajdź regułę, którą chcesz zmodyfikować w kodzie XML

Powyższe polecenia cmdlet wyeksportowano całą *kolekcję reguł*, która zawiera reguły domyślne, które udostępniamy. Następnie musisz wyszukać regułę numer karty kredytowej, którą chcesz zmodyfikować.

1. Użyj edytora tekstów, aby otworzyć plik XML wyeksportowany w poprzedniej sekcji.

2. Przewiń w dół do tagu `<Rules>` , który jest początkiem sekcji zawierającej reguły DLP. Ponieważ ten plik XML zawiera informacje dotyczące całej kolekcji reguł, zawiera inne informacje u góry, które należy przewinąć obok, aby przejść do reguł.

3. Wyszukaj *Func_credit_card* , aby znaleźć definicję reguły numer karty kredytowej. W kodzie XML nazwy reguł nie mogą zawierać spacji, więc spacje są zwykle zastępowane podkreśleniami, a nazwy reguł są czasami skracane. Przykładem tego jest reguła numeru ubezpieczenia społecznego USA, która jest skrócona _do nazwy SSN_. Kod XML reguły Numer karty kredytowej powinien wyglądać podobnie do poniższego przykładu kodu.

   ```xml
   <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085"
          patternsProximity="300" recommendedConfidence="85">
         <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_credit_card" />
           <Any minMatches="1">
             <Match idRef="Keyword_cc_verification" />
             <Match idRef="Keyword_cc_name" />
             <Match idRef="Func_expiration_date" />
           </Any>
         </Pattern>
       </Entity>
   ```

Po zlokalizowaniu definicji reguły numer karty kredytowej w kodzie XML możesz dostosować kod XML reguły zgodnie z potrzebami. Aby zapoznać się z odświeżaniem definicji XML, zobacz [słownik terminów](#term-glossary) na końcu tego tematu.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>Modyfikowanie kodu XML i tworzenie nowego typu informacji poufnych

Najpierw należy utworzyć nowy typ informacji poufnych, ponieważ nie można bezpośrednio modyfikować reguł domyślnych. Możesz wykonywać różne czynności przy użyciu niestandardowych typów informacji poufnych, które zostały opisane w temacie [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell Security & Compliance Center](create-a-custom-sensitive-information-type-in-scc-powershell.md). W tym przykładzie zachowamy prostotę i usuniemy tylko dowody potwierdzające i dodamy słowa kluczowe do reguły Numer karty kredytowej.

Wszystkie definicje reguł XML są oparte na następującym szablonie ogólnym. Musisz skopiować i wkleić kod XML definicji numeru karty kredytowej w szablonie, zmodyfikować niektóre wartości (zwróć uwagę na ". . ." symbole zastępcze w poniższym przykładzie), a następnie przekaż zmodyfikowany kod XML jako nową regułę, która może być używana w zasadach.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
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
   <!-- Paste the Credit Card Number rule definition here.-->
      <LocalizedStrings>
         <Resource idRef=". . .">
           <Name default="true" langcode=" . . . ">. . .</Name>
           <Description default="true" langcode=". . ."> . . .</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

Teraz masz coś, co wygląda podobnie do następującego kodu XML. Ponieważ pakiety reguł i reguły są identyfikowane przez ich unikatowe identyfikatory GUID, musisz wygenerować dwa identyfikatory GUID: jeden dla pakietu reguł i jeden, aby zastąpić identyfikator GUID reguły numer karty kredytowej. Identyfikator GUID identyfikatora jednostki w poniższym przykładzie kodu jest identyfikatorem dla naszej wbudowanej definicji reguły, którą należy zastąpić nową. Istnieje kilka sposobów generowania identyfikatorów GUID, ale można to łatwo zrobić w programie PowerShell, wpisując **ciąg [guid]::NewGuid()**.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id="8aac8390-e99f-4487-8d16-7f0cdee8defc">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="8d34806e-cd65-4178-ba0e-5d7d712e5b66" />
    <Details defaultLangCode="en">
      <LocalizedDetails langcode="en">
        <PublisherName>Contoso Ltd.</PublisherName>
        <Name>Financial Information</Name>
        <Description>Modified versions of the Microsoft rule package</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f"
       patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
      <LocalizedStrings>
         <Resource idRef="db80b3da-0056-436e-b0ca-1f4cf7080d1f">
<!-- This is the GUID for the preceding Credit Card Number entity because the following text is for that Entity. -->
           <Name default="true" langcode="en-us">Modified Credit Card Number</Name>
           <Description default="true" langcode="en-us">Credit Card Number that looks for additional keywords, and another version of Credit Card Number that doesn't require keywords (but has a lower confidence level)</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>Usuwanie wymogu dowodu potwierdzającego z typu informacji poufnych

Teraz, gdy masz nowy typ informacji poufnych, który możesz przekazać do portal zgodności Microsoft Purview, następnym krokiem jest uczynienie reguły bardziej szczegółową. Zmodyfikuj regułę tak, aby wyszukiwała tylko 16-cyfrowy numer, który przekazuje sumę kontrolną, ale nie wymaga dodatkowych (potwierdzających) dowodów, takich jak słowa kluczowe. W tym celu należy usunąć część kodu XML, która szuka dowodów potwierdzających. Dowody potwierdzające są bardzo pomocne w zmniejszaniu wyników fałszywie dodatnich. W takim przypadku zwykle istnieją pewne słowa kluczowe lub data wygaśnięcia w pobliżu numeru karty kredytowej. Jeśli usuniesz te dowody, dostosuj również pewność, że znaleziono numer karty kredytowej, obniżając `confidenceLevel`wartość , która w tym przykładzie wynosi 85.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>Wyszukaj słowa kluczowe specyficzne dla Twojej organizacji

Możesz wymagać dowodów potwierdzających, ale chcesz użyć innych lub dodatkowych słów kluczowych i być może chcesz zmienić miejsce wyszukiwania tych dowodów. Możesz dostosować element , `patternsProximity` aby rozwinąć lub zmniejszyć okno dla dowodów potwierdzających wokół 16-cyfrowej liczby. Aby dodać własne słowa kluczowe, musisz zdefiniować listę słów kluczowych i odwołać się do niej w regule. Poniższy kod XML dodaje słowa kluczowe "karta firmowa" i "karta Contoso", dzięki czemu każdy komunikat zawierający te frazy w ciągu 150 znaków numeru karty kredytowej zostanie zidentyfikowany jako numer karty kredytowej.

```xml
<Rules>
<! -- Modify the patternsProximity to be "150" rather than "300." -->
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="150" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
<!-- Add the following XML, which references the keywords at the end of the XML sample. -->
          <Match idRef="My_Additional_Keywords" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
<!-- Add the following XML, and update the information inside the <Term> tags with the keywords that you want to detect. -->
    <Keyword id="My_Additional_Keywords">
      <Group matchStyle="word">
        <Term caseSensitive="false">company card</Term>
        <Term caseSensitive="false">Contoso card</Term>
      </Group>
    </Keyword>
```

## <a name="upload-your-rule"></a>Przekazywanie reguły

Aby przekazać regułę, należy wykonać następujące czynności.

1. Zapisz go jako plik .xml z kodowaniem Unicode. Jest to ważne, ponieważ reguła nie będzie działać, jeśli plik zostanie zapisany przy użyciu innego kodowania.

2. [Połączenie do Centrum zabezpieczeń i zgodności za pośrednictwem zdalnego programu PowerShell.](/powershell/exchange/connect-to-scc-powershell)

3. W programie PowerShell wpisz następujące polecenie.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > Upewnij się, że używasz lokalizacji pliku, w której pakiet reguł jest faktycznie przechowywany. `C:\custompath\` jest symbolem zastępczym.

4. Aby potwierdzić, wpisz Y, a następnie naciśnij **klawisz Enter**.

5. Sprawdź, czy nowa reguła została przekazana i jej nazwa wyświetlana, wpisując:

   ```powershell
   Get-DlpSensitiveInformationType
   ```

Aby rozpocząć używanie nowej reguły do wykrywania informacji poufnych, należy dodać regułę do zasad DLP. Aby dowiedzieć się, jak dodać regułę do zasad, zobacz [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>Słownik terminów

Są to definicje terminów napotkanych podczas tej procedury.

<br>

****

|Okres|Definicja|
|---|---|
|Jednostki|Jednostki są typami informacji poufnych, takimi jak numery kart kredytowych. Każda jednostka ma unikatowy identyfikator GUID jako swój identyfikator. Jeśli skopiujesz identyfikator GUID i wyszukasz go w kodzie XML, znajdziesz definicję reguły XML i wszystkie zlokalizowane tłumaczenia tej reguły XML. Tę definicję można również znaleźć, lokalizując identyfikator GUID tłumaczenia, a następnie wyszukując ten identyfikator GUID.|
|Functions|Plik XML odwołuje się do `Func_credit_card`funkcji , która jest funkcją w skompilowanym kodzie. Funkcje są używane do uruchamiania złożonych rejestrów i sprawdzania, czy sumy kontrolne są zgodne z naszymi wbudowanymi regułami). Ponieważ dzieje się tak w kodzie, niektóre zmienne nie są wyświetlane w pliku XML.|
|IdMatch|Jest to identyfikator, który wzorzec próbuje dopasować — na przykład numer karty kredytowej.|
|Listy słów kluczowych|Plik XML odwołuje się również do elementów `keyword_cc_verification` i `keyword_cc_name`, które są listami słów kluczowych, z których szukamy dopasowań w obrębie `patternsProximity` jednostki. Nie są one obecnie wyświetlane w kodzie XML.|
|Wzór|Wzorzec zawiera listę tego, czego szuka poufny typ. Obejmuje to słowa kluczowe, rejestry i funkcje wewnętrzne, które wykonują zadania, takie jak weryfikowanie sum kontrolnych. Typy informacji poufnych mogą mieć wiele wzorców z unikatowymi ufnościami. Jest to przydatne podczas tworzenia poufnego typu informacji, który zwraca wysoką pewność siebie w przypadku znalezienia dowodów potwierdzających i mniejszą pewność siebie, jeśli znaleziono niewiele dowodów potwierdzających lub ich nie znaleziono.|
|Wzorzec confidenceLevel|Jest to poziom pewności, że aparat DLP znalazł dopasowanie. Ten poziom ufności jest skojarzony z dopasowaniem wzorca, jeśli zostały spełnione wymagania wzorca. Jest to miara ufności, którą należy wziąć pod uwagę podczas korzystania z reguł przepływu poczty Exchange (nazywanych również regułami transportu).|
|patternsProximity|Gdy znajdziemy, co wygląda jak wzorzec numeru karty kredytowej, to bliskość tej liczby, `patternsProximity` w której będziemy szukać dowodów potwierdzających.|
|recommendedConfidence|Jest to poziom ufności zalecany dla tej reguły. Zalecane zaufanie dotyczy jednostek i koligacji. W przypadku jednostek ta liczba nigdy nie jest oceniana `confidenceLevel` względem wzorca. Jest to jedynie sugestia ułatwiająca wybranie poziomu ufności, jeśli chcesz go zastosować. W przypadku koligacji `confidenceLevel` wzorzec musi być wyższy niż `recommendedConfidence` liczba wywołania akcji reguły przepływu poczty. Jest `recommendedConfidence` to domyślny poziom ufności używany w regułach przepływu poczty, który wywołuje akcję. Jeśli chcesz, możesz ręcznie zmienić regułę przepływu poczty, która ma być wywoływana na podstawie poziomu ufności wzorca.|
|

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
