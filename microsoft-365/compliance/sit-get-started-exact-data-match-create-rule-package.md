---
title: Tworzenie dokładnego dopasowania danych do typów informacji poufnych/pakietu reguł
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
description: Tworzenie dokładnego dopasowania danych do typów informacji poufnych/pakietu reguł
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e44d18bc1a779ace95fb2f64171ff0bf91de57ed
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526044"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>Tworzenie dokładnego dopasowania danych do typów informacji poufnych/pakietu reguł

Korzystając ze schematu EDM i kreatora SIT w Centrum zgodności, można utworzyć dokładny typ informacji poufnych ( [EDM](#use-the-edm-schema-and-sit-wizard) ) lub ręcznie utworzyć plik XML pakietu [reguł](#create-a-rule-package-manually). Schemat można też połączyć przy użyciu jednej z metod, a potem edytować go inną metodą.

Jeśli nie znasz programu SITS opartego na programie EDM ani jego implementacji, zapoznaj się z:

- [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Wprowadzenie do dokładnych typów informacji poufnych opartych na danych](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>Korzystanie ze schematu EDM i kreatora SIT

Za pomocą tego kreatora można tworzyć pliki typu informacji poufnych (SIT) w celu uproszczenia tego procesu.

Typ informacji poufnych w programie EDM składa się z jednego lub kilku wzorców. Każdy wzorzec zawiera kombinację dowodów (pól ze schematu), które zostaną użyte do zidentyfikowania poufnej zawartości w dokumencie lub wiadomości e-mail.

## <a name="pre-requisites"></a>Wymagania wstępne

Wykonaj czynności opisane w tych artykułach:

1. [Eksportowanie danych źródłowych w celu dokładnego dopasowania danych na podstawie typu informacji poufnych](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [Tworzenie schematu w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [Skróty i przekazywanie tabeli źródła informacji poufnych w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- Niezależnie od tego, czy chcesz utworzyć typ informacji poufnych usługi EDM przy użyciu kreatora, czy pliku XML pakietu reguł za pomocą programu PowerShell, musisz mieć uprawnienia administratora globalnego lub administratora zgodności, aby tworzyć, testować i wdrażać niestandardowy typ informacji poufnych za pomocą interfejsu użytkownika. Zobacz [Role administratora w programie Office 365](/office365/admin/add-users/about-admin-roles).
- Zidentyfikuj jeden z wbudowanych typów informacji ( SIT), który ma być źródłem informacji poufnych dla elementów podstawowych.
  - Jeśli żaden z wbudowanych typów informacji poufnych nie pasuje do danych w wybranej kolumnie, musisz utworzyć niestandardowy typ informacji poufnych, który zawiera informacje poufne.
  - Jeśli wybrano opcję Ignorowane ograniczniki dla podstawowej kolumny elementu w schemacie, upewnij się, że niestandardowa tworzyć sit będzie do siebie dorównać dane z wybranymi ogranicznikami i bez niego.
  - Jeśli używasz wbudowanej funkcji SIT, upewnij się, że wykryje ona dokładnie ciągi, które chcesz wybrać, i nie uwzględnia żadnych otaczających znaków ani nie wyklucza żadnej prawidłowej części ciągu, jak jest przechowywana w tabeli informacji poufnych.

Zobacz [Definicje encji typów informacji poufnych](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) i [Tworzenie niestandardowych typów informacji poufnych w Centrum zgodności](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Używanie dokładnego schematu dopasowania danych i kreatora wzorca typów informacji poufnych

1. W centrum Microsoft 365 zgodności dla dzierżawy przejdź do **Klasyfikacja danychKontaktowanie** >  **się ze dopasowaniami danych**.

2. Wybierz **typy informacji poufnych usługi EDM** i Utwórz typ informacji poufnych usługi **EDM** , aby otworzyć kreatora konfiguracji typu informacji poufnych.

3. Wybierz **pozycję Wybierz istniejący schemat EDM** i wybierz schemat utworzony w tabeli Tworzenie schematu, aby uzyskać dokładne dopasowanie danych [do typów informacji poufnych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

4. Wybierz **pozycję Dalej** i wybierz **pozycję Utwórz wzorzec**.

5. Wybierz poziom **ufności i** **element podstawowy**. Aby dowiedzieć się więcej o poziomach ufności, zobacz [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

6. Wybierz typ **informacji poufnych** elementu Podstawowego, z czym ma zostać skojarzony, aby określić, jaki tekst w dokumencie będzie porównywany ze wszystkimi wartościami w polu elementu podstawowego. Zobacz [Definicje encji typu](sensitive-information-type-entity-definitions.md) informacji poufnych, aby dowiedzieć się więcej o dostępnych typach informacji poufnych.

   > [!IMPORTANT]
   > Wybierz typ informacji poufnych, który ściśle odpowiada formatowi zawartości, którą chcesz znaleźć. Wybranie typu informacji poufnych, który odpowiada niepotrzebnej zawartości, na przykład takiego, który odpowiada wszystkim ciągom tekstowym, lub wszystkich liczb, może spowodować nadmiarowe ładowanie w systemie, co może spowodować nieodebrane informacje poufne. Zobacz sekcję Najlepsze rozwiązania w artykule Wprowadzenie do dokładnego dopasowywania danych w tej dokumentacji, aby uzyskać zalecenia dotyczące wybierania typu informacji poufnych do użycia tutaj.

7. Wybierz elementy **pomocy technicznej i** opcje dopasowania.

8. Wybierz **pozycję Gotowe** i **Dalej**.

9. Wybierz **żądany poziom ufności i odległość znaku**. Będzie to wartość domyślna dla całego typu informacji poufnych w programie EDM.

10. Wybierz **pozycję Utwórz wzorzec** , jeśli chcesz utworzyć dodatkowe wzorce dla typu informacji poufnych usługi EDM.

11. Wybierz **pozycję** Dalej i wypełnij pola **Nazwa** i **Opis dla administratorów**.

12. Przejrzyj i wybierz pozycję **Prześlij**.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>Edytowanie lub usuwanie wzorca typu informacji poufnych

1. Otwórz **Centrum zgodności** >  **KlasyfikacjadanychKontaktowanie** >  **dopasowania danych**.

2. Wybierz **pozycję Typy informacji poufnych w programie EDM**.

3. Wybierz pozycję EDM SIT, którą chcesz edytować.

4. W **wysuwanych informacjach** wybierz pozycję Edytuj typ informacji poufnych w uchmie lub Usuń typ informacji poufnych **EDM** .

## <a name="create-a-rule-package-manually"></a>Ręczne tworzenie pakietu reguł

W tej procedurze pokazano, jak utworzyć plik w formacie XML nazywanym pakietem reguł (za pomocą kodowania Unicode), a następnie przekazać go do programu Microsoft 365 przy użyciu poleceń cmdlet programu PowerShell w Centrum zgodności.

> [!NOTE]
> Jeśli zamapowany system SIT może wykryć wielosłowne dowody potwierdzające, elementy dodatkowe definiujące w ręcznie utworzonym pakiecie reguł można zamapować na usługę SIT. `John Smith` `John Smith` `Smith` `John` Na przykład nazwa nie będzie do siebie dopasowana jako element pomocniczy, ponieważ będziemy porównywać i znaleźć w zawartości osobno termin przekazany w jednym z pól, jeśli to pole dowodu potwierdzającego nie zostanie zamapowane na program SIT, który może wykryć ten wzorzec.
>
> W dzierżawie usługi Microsoft 365 reguł istnieje limit 10 pakietów reguł. Ponieważ pakiet reguł może zawierać dowolną liczbę typów informacji poufnych, można uniknąć tworzenia nowego pakietu reguł za każdym razem, gdy chcesz zdefiniować nowy typ informacji poufnych przy użyciu tej metody, zamiast tego wyeksportuj istniejący pakiet reguł i dodaj do pliku XML własne typy informacji poufnych przed jego przekazaniem ponownie.

1. Utwórz pakiet reguł w formacie XML (za pomocą kodowania Unicode), podobnie jak w poniższym przykładzie. (Możesz kopiować, modyfikować i używać naszego przykładu).

   Podczas konfigurowanie pakietu reguł upewnij się, że poprawnie odwołujesz się do pliku .csv, tsv lub pipety (|) rozdzielanego poufnymi informacjami pliku tabeli źródłowej i **edm.xmlpliku schematu** . Możesz kopiować, modyfikować i używać naszego przykładu. W tym przykładowym pliku XML należy dostosować następujące pola w celu utworzenia typu poufnego usługi EDM:

   - **Identyfikator RulePack & identyfikator ExactMatch**: [Użyj new-GUID](/powershell/module/microsoft.powershell.utility/new-guid) , aby wygenerować identyfikator GUID.

   - **Magazyn danych**: To pole określa używany magazyn danych odnośników funkcji EDM. Należy podać nazwę źródła danych skonfigurowanego schematu EDM.

   - **idMatch**: To pole wskazuje element podstawowy dla produktu EDM.
   - **Dopasowania**: określa pole, które ma zostać użyte w dokładnym odnośniku. Można podać nazwę pola z polem wyszukiwania w schemacie EDM dla magazynu danych.
   - **Klasyfikacja**: To pole określa typ informacji poufnych, który wyzwala odnośnik funkcji EDM. Możesz użyć nazwy lub identyfikatora GUID istniejącego wbudowanego lub niestandardowego typu informacji poufnych.

   > [!NOTE]
   > Należy pamiętać, że każdy ciąg, który odpowiada podanej funkcji SIT, będzie skrótowany i porównywany z każdym wpisem w tabeli źródła informacji poufnych. Aby uniknąć problemów z wydajnością w przypadku wybrania niestandardowej funkcji SIT dla elementu klasyfikacji, nie używaj elementu, który będzie odpowiadać dużej zawartości procentowej. Na przykład taki, który pasuje do wyrazu "dowolna liczba" lub "dowolny pięciolicienowy wyraz". Można ją rozróżnić, dodając słowa kluczowe obsługi lub dodając formatowanie w definicji klasyfikacji niestandardowej SIT.

   - **Dopasuj**: To pole wskazuje na dodatkowe dowody znalezione w odległości idMatch.
   - **Dopasowania**: W schemacie EDM dla magazynu danych należy podać dowolną nazwę pola.
   - **Identyfikator zasobuRef:** Ta sekcja określa nazwę i opis typu poufnego w wielu lokalizacjach regionalnych.
     - Identyfikator GUID należy podać dla identyfikatora ExactMatch.
     - **Nazwa** &  **opis**: dostosuj je do potrzeb.

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

2. Upload pakiet reguł, uruchamiając następujące polecenie programu PowerShell:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('.\\rulepack.xml'))
   ```

> [!NOTE]
> Składnia pliku pakietu reguł jest taka sama jak w przypadku innych typów informacji poufnych. Aby uzyskać pełne informacje na temat składni pliku pakietu reguł i dodatkowych opcji konfiguracji, a także uzyskać instrukcje dotyczące modyfikowania i usuwania typów informacji poufnych przy użyciu programu PowerShell, utwórz niestandardowy typ informacji poufnych przy użyciu programu [PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell).

## <a name="next-step"></a>Następny krok

- [Testowanie dokładnego dopasowania danych do typu informacji poufnych](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
