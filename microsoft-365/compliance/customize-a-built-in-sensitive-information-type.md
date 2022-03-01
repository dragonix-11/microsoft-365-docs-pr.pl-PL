---
title: Dostosowywanie wbudowanego typu informacji poufnych
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
description: Dowiedz się, jak utworzyć niestandardowy typ informacji poufnych, który pozwoli na używanie reguł spełniających potrzeby Twojej organizacji.
ms.openlocfilehash: 8393da8e2b2607692983010783d9ae110f268f4c
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009694"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>Dostosowywanie wbudowanego typu informacji poufnych

Gdy szukasz poufnych informacji w zawartości, musisz opisać te informacje w tak zwaną *regułę*. Ochrona przed utratą danych (DLP, Data loss prevention) zawiera reguły najczęściej występujących typów informacji poufnych, których można używać od razu. Aby używać tych reguł, musisz je uwzględnić w zasadach. Może się okazać, że trzeba dostosować te wbudowane reguły do określonych potrzeb organizacji, a w tym celu utworzyć niestandardowy typ informacji poufnych. W tym temacie pokazano, jak dostosować plik XML zawierający istniejący zbiór reguł w celu wykrycia szerszego zakresu potencjalnych informacji o karcie kredytowej.

Możesz użyć tego przykładu i zastosować go do innych wbudowanych typów informacji poufnych. Aby uzyskać listę domyślnych typów informacji poufnych i definicji XML, zobacz [Definicje encji typu informacji poufnych](sensitive-information-type-entity-definitions.md).

## <a name="export-the-xml-file-of-the-current-rules"></a>Eksportowanie pliku XML bieżących reguł

Aby wyeksportować kod XML, musisz połączyć się z Centrum zabezpieczeń [i zgodności za pośrednictwem zdalnej obsługi programu PowerShell](/powershell/exchange/connect-to-scc-powershell).

1. W programie PowerShell wpisz następujące informacje, aby wyświetlić reguły organizacji na ekranie. Jeśli nie masz utworzonego własnego, zobaczysz tylko domyślne, wbudowane reguły z etykietą "Pakiet reguł firmy Microsoft".

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. Przechowuj reguły organizacji w zmiennej, wpisując następujące informacje. Przechowywanie danych w zmiennej powoduje, że jest ona łatwo dostępna później w formacie, który działa w przypadku zdalnych poleceń programu PowerShell.

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. Sformatuj plik XML ze wszystkimi danymi, wpisując następujące informacje.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > Upewnij się, że używasz lokalizacji pliku, w której w rzeczywistości jest przechowywany pakiet reguł. `C:\custompath\` jest symbolem zastępczym.

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>Znajdowanie reguły, którą chcesz zmodyfikować w pliku XML

Powyższe polecenia cmdlet wyeksportowały *cały* zbiór reguł, który zawiera domyślne reguły, które udostępniliśmy. Następnie musisz poszukać reguły numeru karty kredytowej, którą chcesz zmodyfikować.

1. Użyj edytora tekstu, aby otworzyć plik XML wyeksportowany w poprzedniej sekcji.

2. Przewiń w dół do `<Rules>` tagu, który jest początek sekcji zawierającej reguły DLP. Ponieważ ten plik XML zawiera informacje dotyczące całego zbioru reguł, w górnej części tego pliku znajdują się inne informacje, które trzeba przewijać w przeszłości, aby przejść do reguł.

3. *Odszukaj Func_credit_card*, aby znaleźć definicję reguły Numer karty kredytowej. W pliku XML nazwy reguł nie mogą zawierać spacji, więc są one zwykle zamieniane na podkreślenia, a nazwy reguł są czasami skracane. Przykładem jest reguła numerowana U.S. Social Security, która jest skrócona _SSN_. Kod XML z regułą numeru karty kredytowej powinien wyglądać podobnie do poniższego przykładu kodu.

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

Teraz, gdy w pliku XML znajduje się definicja reguły numer karty kredytowej, można dostosować kod XML reguły do swoich potrzeb. Aby odświeżyć informacje na temat definicji XML [, zobacz słownik](#term-glossary) terminów na końcu tego tematu.

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>Modyfikowanie pliku XML i tworzenie nowego typu informacji poufnych

Najpierw należy utworzyć nowy typ informacji poufnych, ponieważ nie można bezpośrednio modyfikować reguł domyślnych. Za pomocą niestandardowych typów informacji poufnych można wykonać wiele różnych czynności, które opisano w tece Tworzenie niestandardowego typu informacji poufnych w programie [PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md) w centrum zabezpieczeń & zgodności. W tym przykładzie zachowajemy prostotę i usuniemy tylko dowody potwierdzający oraz dodam słowa kluczowe do reguły Numer karty kredytowej.

Wszystkie definicje reguł XML są zbudowane na następującym szablonie ogólnym. Musisz skopiować i wkleić w szablonie kod XML definicji numeru karty kredytowej, zmodyfikować niektóre wartości (zwróć uwagę na ". . ." w poniższym przykładzie), a następnie przekaż zmodyfikowany kod XML jako nową regułę, która może być używana w zasadach.

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

Masz coś podobnego do następującego XML. Pakiety reguł i reguły są identyfikowane przez ich unikatowe identyfikatory GUID, dlatego należy wygenerować dwa identyfikatory GUID: jeden dla pakietu reguł i jeden, aby zastąpić identyfikator GUID reguły Numer karty kredytowej. Identyfikator GUID dla identyfikatora jednostki w poniższym przykładzie kodu jest identyfikatorem dla naszej wbudowanej definicji reguły, którą należy zamienić na nową. Istnieje kilka sposobów generowania identyfikatorów GUID, ale można to zrobić łatwo w programie PowerShell, wpisując **[guid]::NewGuid()**.

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

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>Usuwanie wymagania dotyczącej dowodu potwierdzającego z typu informacji poufnych

Teraz, gdy masz nowy typ informacji poufnych, &amp; który możesz przekazać do Centrum zgodności zabezpieczeń, następnym krokiem jest zawęowanie reguły. Zmodyfikuj regułę tak, aby wyszukiwała tylko 16-cyfrowy numer, który przejdzie sprawdzanie, ale nie wymaga dodatkowych (chroboracyjnych) dowodów, takich jak słowa kluczowe. W tym celu należy usunąć część pliku XML, która wyszukuje dowód potwierdzający. Dowód potwierdzający jest bardzo pomocny w zmniejszania wyników fałszywie dodatnich. W tym przypadku w pobliżu numeru karty kredytowej zazwyczaj znajdują się określone słowa kluczowe lub data wygaśnięcia. Jeśli usuniesz te informacje, `confidenceLevel`musisz również dostosować pewność, że znaleziono numer karty kredytowej, obniżając , co w przykładzie wynosi 85.

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>Odszukaj słowa kluczowe specyficzne dla Twojej organizacji

Być może trzeba będzie wymagać dowodów potwierdzających, ale trzeba użyć innych lub dodatkowych słów kluczowych, a być może trzeba zmienić miejsce, w którym należy szukać tych dowodów. Możesz dostosować to, `patternsProximity` aby rozszerzyć lub zmniejszyć okno dowodów potwierdzania cofający się wokół numeru 16-cyfrowego. Aby dodać własne słowa kluczowe, musisz zdefiniować listę słów kluczowych i odwoływać się do jej w ramach reguły. W poniższym pliku XML słowa kluczowe "wizytówka firmy" i "Wizytówka Contoso" są w ten sposób oznaczane, że każda wiadomość zawierająca te frazy w obrębie 150 znaków numeru karty kredytowej będzie identyfikowana jako numer karty kredytowej.

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

## <a name="upload-your-rule"></a>Upload reguły

Aby przekazać regułę, musisz wykonać następujące czynności.

1. Zapisz go jako plik .xml kodowaniem Unicode. Jest to ważne, ponieważ reguła nie zadziała, jeśli plik zostanie zapisany z innym kodowaniem.

2. [Połączenie się z Centrum zabezpieczeń i zgodności za pośrednictwem zdalnej obsługi programu PowerShell.](/powershell/exchange/connect-to-scc-powershell)

3. W programie PowerShell wpisz następujące informacje.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > Upewnij się, że używasz lokalizacji pliku, w której w rzeczywistości jest przechowywany pakiet reguł. `C:\custompath\` jest symbolem zastępczym.

4. Aby potwierdzić, wpisz Y, a następnie naciśnij klawisz **Enter**.

5. Sprawdź, czy nowa reguła została przesłana i jej nazwa wyświetlana, wpisując:

   ```powershell
   Get-DlpSensitiveInformationType
   ```

Aby rozpocząć wykrywanie informacji poufnych przy użyciu nowej reguły, musisz dodać ją do zasad DLP. Aby dowiedzieć się, jak dodać regułę do zasad, zobacz [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md).

## <a name="term-glossary"></a>Słownik terminów

Są to definicje terminów, które wystąpiły podczas tej procedury.

<br>

****

|Termin|Definicja|
|---|---|
|Jednostka|Jednostki to typy informacji poufnych, takie jak numery kart kredytowych. Każda jednostka ma unikatowy identyfikator GUID. Jeśli skopiujesz identyfikator GUID i wyszukasz go w formacie XML, znajdziesz definicję reguły XML oraz wszystkie zlokalizowane tłumaczenia tej reguły XML. Tę definicję można również znaleźć, lokalizując identyfikator GUID tłumaczenia, a następnie wyszukując ten identyfikator GUID.|
|Funkcje|Odwołania do plików `Func_credit_card`XML , które są funkcją w skompilowanym kodzie. Funkcje służą do uruchamiania złożonych regexes i sprawdzania, czy sumy kontrolne są zgodne z naszymi wbudowanymi regułami). Ponieważ tak się dzieje w kodzie, niektóre zmienne nie są wyświetlane w pliku XML.|
|IdMatch|Jest to identyfikator, który próbuje się dopasować — na przykład numer karty kredytowej.|
|Listy słów kluczowych|Plik XML odwołuje się również `keyword_cc_verification` do oraz `keyword_cc_name`, które są listami słów kluczowych, na których szukamy dopasowania w obrębie `patternsProximity` encji. Nie są one obecnie wyświetlane w pliku XML.|
|Deseń|Wzorzec zawiera listę elementów szukanych przez typ poufny. Należą do nich słowa kluczowe, regexes i funkcje wewnętrzne, które wykonują zadania, takie jak weryfikowanie podsumowy. Typy informacji poufnych mogą mieć wiele wzorców o unikatowych ufnościach. Jest to przydatne w przypadku tworzenia typu informacji poufnych, który zwraca dużą pewność, jeśli zostanie znaleziony dowód potwierdzający, i niższy poziom ufności, jeśli zostanie odnaleziony mały dowód potwierdzający lub nie zostanie on odnaleziony.|
|Ufność deseniu Poziom|Jest to poziom pewności, że aparat DLP znalazł dopasowanie. Ten poziom ufności jest skojarzony z dopasowaniem do wzorca, jeśli są spełnione wymagania wzorca. Jest to miara ufności, która należy rozważyć podczas Exchange przepływu poczty e-mail (nazywane również regułami transportu).|
|patternsProximity|Gdy znajdziemy wzorzec numeru karty kredytowej, zbliżymy się do tej liczby, `patternsProximity` gdzie będziemy szukać dowodów potwierdzających.|
|zalecanaConfidence|Jest to poziom ufności, który zalecamy w przypadku tej reguły. Zalecana pewność dotyczy obiektów i chętnych. W przypadku obiektów ta liczba nigdy nie jest szacowana względem wzorca `confidenceLevel` . To tylko sugestia, która pomoże Ci wybrać poziom ufności, jeśli chcesz go zastosować. W przypadku koligacji `confidenceLevel` `recommendedConfidence` wzorzec musi być większy niż liczba akcji reguły przepływu poczty e-mail, która ma zostać wywołana. Jest `recommendedConfidence` to domyślny poziom ufności używany w zasadach przepływu poczty e-mail, które wywołują akcję. Jeśli chcesz, możesz zamiast tego ręcznie zmienić regułę przepływu poczty e-mail, aby wywołać ją na podstawie poziomu ufności wzorca.|
|

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
