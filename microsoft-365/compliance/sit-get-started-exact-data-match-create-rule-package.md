---
title: Twórz dokładny typ/pakiet reguł informacji poufnych opartych na dopasowaniu danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Twórz dokładny typ/pakiet reguł informacji poufnych opartych na dopasowaniu danych
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d18147e576db356a5fb7904c3901003bbf48855e
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435264"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>Twórz dokładny typ/pakiet reguł informacji poufnych opartych na dopasowaniu danych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Możesz utworzyć dokładny typ informacji poufnych dopasowania danych (EDM) przy użyciu [schematu EDM i kreatora SIT](#use-the-edm-schema-and-sit-wizard) w Centrum zgodności lub [ręcznie](#create-a-rule-package-manually) utworzyć plik XML pakietu reguł. Można również połączyć oba przy użyciu jednej metody, aby utworzyć schemat, a następnie edytować go przy użyciu drugiej metody.

Jeśli nie znasz rozwiązania EDM based SITS lub ich implementacji, zapoznaj się z:

- [Dowiedz się więcej o typach informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Wprowadzenie do dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>Korzystanie ze schematu EDM i kreatora SIT

Ten kreator umożliwia tworzenie plików typu informacji poufnych (SIT), aby uprościć proces.

Typ informacji poufnych EDM składa się z co najmniej jednego wzorca. Każdy wzorzec opisuje kombinację dowodów (pól ze schematu), które będą używane do identyfikowania poufnej zawartości w dokumencie lub wiadomości e-mail.

## <a name="pre-requisites"></a>Wymagania wstępne

Wykonaj kroki opisane w następujących artykułach:

1. [Eksportuj dane źródłowe dla dokładnego typu informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [Twórz schemat dla dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [Utwórz skrót i przekaż tabelę źródła informacji poufnych dla dokładnych typów informacji poufnych opartych na dopasowaniu danych ](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- Niezależnie od tego, czy będziesz tworzyć typ informacji poufnych EDM przy użyciu kreatora, czy pliku XML pakietu reguł za pośrednictwem programu PowerShell, musisz mieć uprawnienia administratora globalnego lub administratora zgodności do tworzenia, testowania i wdrażania niestandardowego typu informacji poufnych za pośrednictwem interfejsu użytkownika. Zobacz [Informacje o rolach administratora w Office 365](/office365/admin/add-users/about-admin-roles).
- Zidentyfikuj jeden z wbudowanych interfejsów SIC do użycia jako typ informacji poufnych elementów podstawowych.
  - Jeśli żaden z wbudowanych typów informacji poufnych nie będzie zgodny z danymi w wybranej kolumnie, musisz utworzyć niestandardowy typ informacji poufnych.
  - Jeśli wybrano opcję Ignored Delimiters (Ignorowane ograniczniki) dla kolumny elementu podstawowego w schemacie, upewnij się, że utworzona niestandardowa funkcja SIT będzie zgodna z danymi z wybranymi ogranicznikami i bez tych ograniczników.
  - Jeśli używasz wbudowanego interfejsu SIT, upewnij się, że wykryje on dokładnie ciągi, które chcesz wybrać, i nie będzie zawierać żadnych otaczających znaków ani wykluczyć żadnej prawidłowej części ciągu przechowywanej w tabeli informacji poufnych.

Zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) i [Tworzenie niestandardowych typów informacji poufnych w Centrum zgodności](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Użyj kreatora dokładnego schematu dopasowania danych i wzorca typów informacji poufnych

1. W portal zgodności Microsoft Purview dla dzierżawy przejdź do pozycji **Klasyfikacja** >  **danychDopasowania danych**.

2. Wybierz **typy informacji poufnych EDM** i **Utwórz typ informacji poufnych EDM** , aby otworzyć kreatora konfiguracji typów informacji poufnych.

3. Wybierz **pozycję Wybierz istniejący schemat EDM** i wybierz schemat utworzony w [sekcji Tworzenie schematu dla dokładnych typów informacji poufnych zgodnych z danymi](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

4. Wybierz pozycję **Dalej** i wybierz pozycję **Utwórz wzorzec**.

5. Wybierz **poziom ufności** i **element Podstawowy**. Aby dowiedzieć się więcej na temat poziomów ufności, zobacz [Dowiedz się więcej o typach informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

6. Wybierz **typ informacji poufnych elementu podstawowego** , z który ma zostać skojarzony, aby zdefiniować tekst w dokumencie, który będzie porównywany ze wszystkimi wartościami w polu elementu podstawowego. Zobacz [Definicje jednostek typów informacji poufnych](sensitive-information-type-entity-definitions.md) , aby dowiedzieć się więcej o dostępnych typach informacji poufnych.

   > [!IMPORTANT]
   > Wybierz typ informacji poufnych, który jest ściśle zgodny z formatem zawartości, którą chcesz znaleźć. Wybranie typu informacji poufnych zgodnego z niepotrzebną zawartością, takiego jak taki, który pasuje do wszystkich ciągów tekstowych, lub wszystkie liczby mogą powodować nadmierne obciążenie systemu, co może spowodować pominięcie poufnych informacji.

7. Wybierz **elementy pomocnicze** i opcje dopasowania.

8. Wybierz **pozycję Gotowe** i **Dalej**.

9. Wybierz żądany **poziom ufności i bliskość znaków**. Będzie to wartość domyślna dla całego typu informacji poufnych EDM.

10. Wybierz **pozycję Utwórz wzorzec** , jeśli chcesz utworzyć dodatkowe wzorce dla typu informacji poufnych EDM.

11. Wybierz pozycję **Dalej** i wypełnij **pola Nazwa** i **Opis dla administratorów**.

12. Przejrzyj i wybierz pozycję **Prześlij**.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>Edytowanie lub usuwanie wzorca typów informacji poufnych

1. Otwórz **centrum** >  zgodności **Klasyfikacja danychAktualizaj** >  **dopasowania danych**.

2. Wybierz **typy informacji poufnych EDM**.

3. Wybierz pozycję EDM SIT, którą chcesz edytować.

4. Wybierz pozycję **Edytuj typ informacji poufnych EDM** lub **Usuń typ informacji poufnych EDM** z wysuwanego elementu.

## <a name="working-with-specific-types-of-data"></a>Praca z określonymi typami danych

Ze względu na wydajność bardzo ważne jest użycie wzorców, które zminimalizują liczbę niepotrzebnych dopasowań. Na przykład można użyć typu informacji poufnych na podstawie wyrażenia regularnego.

`\b\w*\b`

Będzie to zgodne z każdym pojedynczym słowem lub numerem w dowolnym dokumencie lub wiadomości e-mail. Spowodowałoby to przeciążenie usługi dopasowaniami i pominięcie wykrywania prawdziwych dopasowań. Użycie bardziej precyzyjnych wzorców może uniknąć tej sytuacji. Poniżej przedstawiono kilka zaleceń dotyczących identyfikowania właściwej konfiguracji niektórych typowych typów danych.

**Adresy e-mail**: Adresy e-mail mogą być łatwe do zidentyfikowania, ale ponieważ są tak powszechne w zawartości, mogą powodować znaczne obciążenie systemu, jeśli są używane jako pole podstawowe. Użyj ich tylko jako dowodów pomocniczych. Jeśli muszą być one używane jako podstawowe dowody, spróbuj zdefiniować niestandardowy typ informacji poufnych, który używa logiki do wykluczania ich użycia jako `From` lub `To` pól w wiadomościach e-mail, oraz wykluczyć te z adresem e-mail firmy, aby zmniejszyć liczbę niepotrzebnych ciągów, które muszą być dopasowane.

**liczby Telefon**: liczby Telefon mogą mieć różne formaty, w tym prefiksy kraju, kody kierunkowe i separatory. Aby zmniejszyć liczbę fałszywych negatywów przy zachowaniu minimalnego obciążenia, należy użyć ich tylko jako elementów pomocniczych, wykluczyć wszystkie prawdopodobne separatory, takie jak nawiasy i kreski, i uwzględnić tylko w poufnej tabeli danych część, która będzie zawsze obecna pod numerem telefonu.

**Imiona i nazwiska** osób: nie używaj nazw osób jako elementów podstawowych, jeśli używasz typu informacji poufnych opartego na wyrażeniu regularnym jako elementu klasyfikacji dla tego typu EDM, ponieważ trudno je odróżnić od typowych słów.

Jeśli musisz użyć elementu podstawowego, który jest trudny do zidentyfikowania za pomocą określonego wzorca, takiego jak nazwa kodu projektu, który może wygenerować wiele dopasowań do przetworzenia, upewnij się, że słowa kluczowe są uwzględniane w typie informacji poufnych używanym jako element klasyfikacji dla typu EDM. Jeśli na przykład używasz nazw kodu projektu, które mogą być zwykłymi wyrazami, możesz użyć słowa `project` jako wymaganego dodatkowego dowodu w pobliżu wzorca opartego na wyrażeniu regularnym nazwy projektu w typie poufnym używanym jako element klasyfikacji dla typu EDM. Możesz też rozważyć użycie poufnego typu opartego na zwykłym słowniku jako elementu klasyfikacji dla EDM SIT.

Podczas próby dopasowania ciągów liczbowych określ dozwolone zakresy liczb, takie jak liczba cyfr lub cyfry początkowe, jeśli są znane. Jeśli chcesz dopasować stosunkowo elastyczny zakres liczb, możesz użyć słów kluczowych w podstawowym interfejsie SIT, aby zmniejszyć liczbę dopasowań. Jeśli na przykład próbujesz dopasować numery kont składające się z cyfr 7–11, dodaj wyrazy `account`, `customer`, `acct.` do interfejsu SIT jako wymagany dodatkowy dowód. Zmniejsza to prawdopodobieństwo niepotrzebnych dopasowań, które mogą powodować przekroczenie limitów dopasowań przetwarzanych przez usługę EDM.

Jeśli pole, którego należy użyć jako elementu podstawowego, jest zgodne z prostym wzorcem, który może powodować dużą liczbę dopasowań i nie można dodać obecności słów kluczowych jako dodatkowych dowodów w typie informacji poufnych, możesz też wymagać minimalnej liczby wystąpień tego wzorca. Na przykład można użyć niestandardowego typu informacji poufnych zdefiniowanego w następujący sposób, aby wykryć co najmniej 29 innych pięciocyfrowych liczb otaczających potencjalną pięciocyfrową liczbę w celu dopasowania do EDM:

```xml
 <Entity id="98703510-18b3-43d4-961f-15317594beb7"
                  patternsProximity="300"
                  recommendedConfidence="85"
                  relaxProximity="false">
                  <Pattern confidenceLevel="85"
                              proximity="300">
                              <IdMatch idRef="MRN"/>
                              <Match idRef="30 AccountNrs"
                                    minCount="30"
                                    proximity="3000"
                                    uniqueResults="true"/>
                  </Pattern>
      </Entity>
      <Regex id="30 AccountNrs">\d{5}</Regex>
```

W niektórych przypadkach może być konieczne zidentyfikowanie pewnych numerów identyfikacyjnych kont lub rekordów, które ze względów historycznych nie są zgodne ze standardowym wzorcem. Można na przykład `Medical Record Numbers` składać się z wielu różnych permutacji liter i cyfr w tej samej organizacji. Mimo że na początku może być trudno zidentyfikować wzorzec, dokładniejsza kontrola często pozwala zawęzić wzorzec opisujący wszystkie prawidłowe wartości bez powodowania nadmiernej liczby nieprawidłowych dopasowań. Na przykład można wykryć, że "wszystkie nazwy MRN mają co najmniej siedem znaków, mają co najmniej dwie cyfry liczbowe, a jeśli mają jakieś litery, zaczynają się od jednej". Utworzenie wyrażenia regularnego na podstawie takich kryteriów powinno umożliwić zminimalizowanie niepotrzebnych dopasowań podczas przechwytywania wszystkich żądanych wartości, a dalsza analiza może pozwolić na większą precyzję przez zdefiniowanie oddzielnych wzorców opisujących różne formaty.

## <a name="create-a-rule-package-manually"></a>Ręczne tworzenie pakietu reguł

W tej procedurze pokazano, jak utworzyć plik w formacie XML nazywanym pakietem reguł (z kodowaniem Unicode), a następnie przekazać go do Microsoft Purview przy użyciu poleceń cmdlet programu PowerShell centrum zgodności.

> [!NOTE]
> Jeśli mapowany interfejs SIT może wykrywać wielowyrazowe dowody potwierdzające, elementy pomocnicze zdefiniowane w ręcznie utworzonym pakiecie reguł mogą zostać zamapowane na sit. Na przykład nazwa `John Smith` nie byłaby zgodna z elementem pomocniczym, ponieważ porównalibyśmy `John` zawartość i `Smith` znaleźliśmy ją oddzielnie z terminem `John Smith` przekazanym w jednym z pól, jeśli to pole dowodu potwierdzającego nie zostało zamapowane na funkcję SIT, która może wykryć ten wzorzec.
>
> W dzierżawie Microsoft 365 istnieje limit 10 pakietów reguł. Ponieważ pakiet reguł może zawierać dowolną liczbę typów informacji poufnych, można uniknąć tworzenia nowego pakietu reguł za każdym razem, gdy chcesz zdefiniować nowy typ informacji poufnych przy użyciu tej metody, zamiast tego wyeksportować istniejący pakiet reguł i dodać typy informacji poufnych do kodu XML przed ponownym przekazaniem.

1. Utwórz pakiet reguł w formacie XML (z kodowaniem Unicode), podobnie jak w poniższym przykładzie. (Możesz skopiować, zmodyfikować i użyć naszego przykładu).

   Podczas konfigurowania pakietu reguł upewnij się, że poprawnie odwołujesz się do pliku tabeli źródłowej .csv, tsv lub potoku (|) rozdzielanych poufnych informacji i **edm.xml** pliku schematu. Możesz skopiować, zmodyfikować i użyć naszego przykładu. W tym przykładowym kodzie XML należy dostosować następujące pola, aby utworzyć typ poufny EDM:

   - **Identyfikator RulePack & identyfikator ExactMatch**: użyj [nowego identyfikatora GUID](/powershell/module/microsoft.powershell.utility/new-guid) do wygenerowania identyfikatora GUID.

   - **Magazyn danych**: to pole określa magazyn danych wyszukiwania EDM do użycia. Podaj nazwę źródła danych skonfigurowanego schematu EDM.

   - **idMatch**: to pole wskazuje element podstawowy dla EDM.
   - **Dopasowania**: określa pole, które ma być używane w dokładnym wyszukiwaniu. Podaj nazwę pola z możliwością wyszukiwania w schemacie EDM dla magazynu danych.
   - **Klasyfikacja**: to pole określa dopasowanie typu informacji poufnych, które wyzwala wyszukiwanie EDM. Możesz użyć nazwy lub identyfikatora GUID istniejącego wbudowanego lub niestandardowego typu informacji poufnych.

   > [!NOTE]
   > Należy pamiętać, że każdy ciąg zgodny z podanym ciągiem SIT będzie skrótem i porównywany z każdym wpisem w tabeli źródła informacji poufnych. Aby uniknąć problemów z wydajnością w przypadku wybrania niestandardowego interfejsu SIT dla elementu klasyfikacji, nie używaj elementu, który będzie odpowiadał dużemu procentowi zawartości. Na przykład taki, który pasuje do "dowolnej liczby" lub "dowolnego słowa pięcioliterowego". Można go odróżnić, dodając pomocnicze słowa kluczowe lub uwzględniając formatowanie w definicji niestandardowej klasyfikacji SIT.

   - **Dopasowanie**: to pole wskazuje na dodatkowe dowody znalezione w pobliżu elementu idMatch.
   - **Dopasowania**: podaj dowolną nazwę pola w schemacie EDM dla magazynu danych.
   - **Zasób idRef:** Ta sekcja określa nazwę i opis typów poufnych w wielu ustawieniach regionalnych
     - Podaj identyfikator GUID dla identyfikatora ExactMatch.
     - **Nazwa** &  **description**: dostosuj w razie potrzeby.

      ```xml
      <RulePackage xmlns="http://schemas.microsoft.com/office/2018/edm">
        <RulePack id="fd098e03-1796-41a5-8ab6-198c93c62b11">
          <Version build="0" major="2" minor="0" revision="0" />
          <Publisher id="eb553734-8306-44b4-9ad5-c388ad970528" />
          <Details defaultLangCode="en-us">
            <LocalizedDetails langcode="en-us">
              <PublisherName>IP DLP</PublisherName>
              <Name>Health Care EDM Rulepack</Name>
              <Description>This rule package contains the EDM sensitive type for health care sensitive types.</Description>
            </LocalizedDetails>
          </Details>
        </RulePack>
        <Rules>
          <ExactMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB371" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
            <Pattern confidenceLevel="65">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
            </Pattern>
            <Pattern confidenceLevel="75">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
              <Any minMatches ="3" maxMatches ="6">
                <match matches="PatientID" />
                <match matches="MRN"/>
                <match matches="FirstName"/>
                <match matches="LastName"/>
                <match matches="Phone"/>
                <match matches="DOB"/>
              </Any>
            </Pattern>
          </ExactMatch>
          <LocalizedStrings>
            <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB371">
              <Name default="true" langcode="en-us">Patient SSN Exact Match.</Name>
              <Description default="true" langcode="en-us">EDM Sensitive type for detecting Patient SSN.</Description>
            </Resource>
          </LocalizedStrings>
        </Rules>
      </RulePackage>
      ```

2. Przekaż pakiet reguł, uruchamiając następujące polecenie programu PowerShell:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('.\\rulepack.xml'))
   ```

> [!NOTE]
> Składnia pliku pakietu reguł jest taka sama jak w przypadku innych typów informacji poufnych. Aby uzyskać szczegółowe informacje na temat składni pliku pakietu reguł oraz dodatkowych opcji konfiguracji oraz instrukcje dotyczące modyfikowania i usuwania typów informacji poufnych przy użyciu programu PowerShell, [utwórz niestandardowy typ informacji poufnych przy użyciu programu PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell).

## <a name="next-step"></a>Następny krok

- [Testuj dokładny typ informacji poufnych oparty na dopasowaniu danych](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
