---
title: Tworzenie schematu w celu dokładnego dopasowania danych do typów informacji poufnych
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
description: Tworzenie schematu w celu dokładnego dopasowania danych do typów informacji poufnych
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6bd411411c3075259bd3b9fc74ec3f558171fce7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526294"
---
# <a name="create-the-schema-for-exact-data-match-based-sensitive-information-types"></a>Tworzenie schematu w celu dokładnego dopasowania danych do typów informacji poufnych

Schemat i usługę EDM SIT można utworzyć za pomocą kreatora wzorca dokładnego dopasowania danych i typu informacji poufnych [lub](#use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard) [ręcznie](#create-exact-data-match-schema-manually-and-upload). Schemat można też połączyć przy użyciu jednej z metod, a potem edytować go inną metodą.

Jeśli nie znasz programu SITS opartego na programie EDM ani jego implementacji, zapoznaj się z:

- [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Wprowadzenie do dokładnych typów informacji poufnych opartych na danych](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

Jednego schematu EDM można użyć w wielu typach informacji poufnych, w których jest używana ta sama tabela danych poufnych. W dzierżawie można utworzyć maksymalnie 10 różnych schematów usługi EDM Microsoft 365 dzierżawie.

## <a name="working-with-specific-types-of-data"></a>Praca z określonymi typami danych

Ze względu na wydajność bardzo ważne jest stosowanie wzorców, które zminimalizują liczbę niepotrzebnych dopasowania. Na przykład możesz użyć typu informacji poufnych opartego na wyrażeniu regularnym.

`\b\w*\b`

Będzie to zgodne z każdym indywidualnym wyrazem lub numerem w dowolnym dokumencie lub wiadomości e-mail. Spowoduje to przeciążenie usługi dopasowaniami i nieodebrane wykrywanie prawdziwych trafień. Stosowanie bardziej precyzyjnych wzorców pozwala uniknąć takich sytuacji. Oto kilka zaleceń dotyczących identyfikowania odpowiedniej konfiguracji dla niektórych typowych typów danych.

**Adresy e-mail**: Adresy e-mail mogą być łatwe do zidentyfikowania, ale ponieważ są tak częste w zawartości, mogą powodować istotne obciążenie w systemie, jeśli są używane jako pole podstawowe. Należy ich używać tylko jako dodatkowych dowodów. Jeśli te informacje muszą zostać użyte jako podstawowe informacje, `From` `To` spróbuj zdefiniować niestandardowy typ informacji poufnych, który używa logiki, aby wykluczyć ich użycie jako lub pola w wiadomościach e-mail oraz wykluczyć te, które zawierają firmowy adres e-mail, w celu zmniejszenia liczby niepotrzebnych ciągów, które muszą zostać dopasowane.

**Telefon numery:** Telefon mogą być dostępne w wielu różnych formatach, łącznie z prefiksami krajów, numerami kierunkowym i separatorami (z wyjątkiem). Aby zmniejszyć wartości fałszywie ujemne przy jednoczesnym zachowaniu minimalnego obciążenia, używaj ich tylko jako elementów pomocniczych, wyklucz wszystkie możliwe separatory, takie jak nawiasy i kreski, i uwzględnij w tabeli poufnej tylko część, która będzie zawsze obecna w numerze telefonu.

**Imiona** i nazwiska osób. Nie należy używać imion i nazwisk osób jako elementów podstawowych, jeśli jako element klasyfikacji tego typu EDM używasz typu informacji poufnego opartego na wyrażeniu regularnym, ponieważ są one trudne do odróżnienia od popularnych wyrazów.

Jeśli musisz użyć elementu podstawowego, który jest trudno zidentyfikować z określoną wzorcem, na przykład nazwą kodu projektu, która może wygenerować wiele dopasowania do przetworzenia, pamiętaj, aby uwzględnić słowa kluczowe w poufnym typie informacji, który jest elementem klasyfikacji dla twojego typu EDM. Na przykład w przypadku używania nazw kodów projektu, które mogą być zwykłymi wyrazami, `project` możesz użyć tego wyrazu jako wymaganego dodatkowego dowodu w pobliżu nazwy projektu ze wzorcem regularnym opartym na wyrażeniu w typie poufnym używanym jako element klasyfikacji dla twojego typu usługi EDM. Możesz również rozważyć użycie typu poufnego opartego na zwykłym słowniku jako elementu klasyfikacji dla funkcji EDM SIT.

Podczas próby dopasowania ciągów liczbowych określ dozwolone zakresy liczb, takie jak liczba cyfr lub cyfr początkowych, jeśli są znane. Jeśli musisz dopasować do stosunkowo elastycznego zakresu liczb, możesz użyć słów kluczowych w podstawowej funkcji SIT, aby zmniejszyć liczbę dopasowań. Jeśli na przykład próbujesz dopasować numery kont składające się z 7–11 cyfr, `account`dodaj wyrazy , `customer`do `acct.` numeru SIT jako wymagane dodatkowe dowód. Zmniejsza to prawdopodobieństwo, że niepotrzebne dopasowania mogą spowodować przekroczenie limitu dopasowania przetwarzanego przez EDM.

Jeśli pole, które ma zostać użycia jako element podstawowy, jest zgodny z prostym wzorcem, który może powodować wiele dopasowania i nie można dodać informacji o obecności słów kluczowych jako dodatkowych dowodów w przypadku poufnego typu informacji, można także zażądać minimalnej liczby wystąpień tego wzorca. Można na przykład użyć niestandardowego typu informacji poufnych zdefiniowanego w następujący sposób w celu wykrycia co najmniej 29 innych pięciocyfrowych liczb otaczających potencjalną pięciocyfrową liczbę dopasowaną do funkcji EDM:

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

W niektórych przypadkach może być konieczne zidentyfikowanie konta lub numeru identyfikacyjnego rekordu, które ze względów historycznych nie są zgodne ze standardowym wzorcem. Może na przykład `Medical Record Numbers` składać się z wielu różnych permutacji liter i liczb w tej samej organizacji. Mimo że zidentyfikowanie wzorca może być trudne, ściślejsza inspekcja często pozwala zawęzić wzorzec opisujący wszystkie prawidłowe wartości bez powodowania nadmiarowej liczby nieprawidłowych dopasowania. Na przykład może zostać wykryty, że "wszystkie sieci MRN mają długość co najmniej siedmiu znaków, mają co najmniej dwie cyfry liczbowe i jeśli znajdują się w nich jakiekolwiek litery, zaczynają się od jednej". Utworzenie wyrażenia regularnego na podstawie takich kryteriów powinno pozwolić na zminimalizowanie niepotrzebnych dopasowania podczas przechwytywania wszystkich żądanych wartości, a dalsza analiza może umożliwić większą precyzję, definiując oddzielne wzorce opisujące różne formaty.

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-wizard"></a>Korzystanie z Kreatora dokładnego dopasowania danych do schematu i kreatora typów informacji poufnych

Za pomocą tego kreatora można uprościć proces tworzenia pliku schematu.

## <a name="pre-requisites"></a>Wymagania wstępne

- Wykonaj czynności opisane w [eksportowaniu danych źródłowych, aby uzyskać dokładne dopasowanie danych na podstawie typu informacji poufnych](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type).

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Używanie dokładnego schematu dopasowania danych i kreatora wzorca typów informacji poufnych

1. W centrum Microsoft 365 zgodności dla dzierżawy przejdź do **Klasyfikacja danychExact** **data matchesEDM** >  >  **schemas**.

2. Wybierz **pozycję Utwórz schemat EDM** , aby otworzyć okno wysuwu konfiguracji kreatora schematu.

   ![Wysuuwane informacje o konfiguracji kreatora tworzenia schematu EDM.](../media/edm-schema-wizard-1.png)

3. Wypełnij odpowiednie pola **Nazwa i** **Opis**.

4. Wybierz **pozycję Ignoruj ograniczniki i znaki interpunktowe** dla wszystkich pól schematu, jeśli chcesz, aby takie zachowanie było dla całego schematu. Aby dowiedzieć się więcej na temat konfigurowania narzędzia EDM w celu ignorowania ograniczników lub liter, zobacz Używanie pól [inensywnych i ignorowanychDelimiters](#using-the-caseinsensitive-and-ignoreddelimiters-fields) , aby uzyskać więcej informacji na temat tej funkcji.

5. Wypełnij żądane wartości dla pola **schematu nr 1** i dodaj więcej pól zgodnie z potrzebami. Każde pole schematu musi być identyczne z nagłówkami kolumn w pliku źródłowym poufnych informacji.

6. Jeśli chcesz, ustaw dla każdego pola wartości:
    1. **Pole można wyszukiwać**
    1. **W polu nie jest uwzględniania liter**
    1. **Wybierz ograniczniki i znaki interpunktowe do zignorowania dla tego pola**
    1. **W tym polu wprowadź ograniczniki niestandardowe i znaki interpunktowe**

   > [!IMPORTANT]
   > Co najmniej jedno, ale nie więcej niż pięć pól schematu musi zostać wskazanych jako można wyszukiwać.

7. Wybierz pozycję **Zapisz**. Schemat zostanie wymieniony na liście i będzie dostępny do użycia.

   > [!IMPORTANT]
   > Jeśli chcesz usunąć schemat, który jest już skojarzony z typem informacji poufnych usługi EDM, musisz najpierw usunąć typ informacji poufnych EDM, a następnie usunąć schemat. Usunięcie schematu, z który jest skojarzony magazyn danych, powoduje również usunięcie magazynu danych w ciągu 24 godzin.

## <a name="export-of-the-edm-schema-file-in-xml-format"></a>Eksportowanie pliku schematu EDM w formacie XML

Jeśli schemat EDM został utworzony w kreatorze schematu EDM, musisz wyeksportować plik schematu EDM w formacie XML. Będzie potrzebna w tabeli Skrót, a następnie przekaż tabelę źródła informacji poufnych, aby dokładnie dopasować dane do fazy [typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) .

1. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

2. Aby wyeksportować plik schematu EDM, użyj tej składni:

   ```powershell
   $Schema = Get-DlpEdmSchema -Identity "[your EDM Schema name]"
   Set-Content -Path ".\Schemafile.xml" -Value $Schema.EdmSchemaXML
   ```

3. Zapisz ten plik do późniejszego użycia.

## <a name="create-exact-data-match-schema-manually-and-upload"></a>Ręczne tworzenie dokładnego schematu zgodnego z danymi i przekazywanie

W pliku schematu skonfiguruj wpis dla każdej kolumny w tabeli źródłowej informacji poufnych, stosując składnię:

```xml
<Field name="FieldName" searchable="true/false" caseInsensitive="true/false" ignoredDelimiters="delimiter characters" />
```

### <a name="using-the-caseinsensitive-and-ignoreddelimiters-fields"></a>Korzystanie z pól caseInsensitive i ignorowaneDelimiters

W poniższym przykładzie schematu XML są wykorzystania pól *caseInsensitive* i *ignorowanychdelimiters* .

Gdy uwzględnisz *sprawęZamówienie* pola ustawionego `true` na wartość w definicji schematu, program EDM nie będzie wykluczać elementu z względu na różnice dotyczące przypadków. Na przykład EDM będzie widzieć wartości **FOO-1234** i **fOo-1234** jako identyczne dla pola `PatientID` .

Jeśli uwzględnisz *zignorowane poleDelimiters* z obsługiwanymi znakami, program EDM zignoruje te znaki. W ten sposób funkcja NR.E.WEW będzie widzieć wartości **FOO-1234** i **FOO#1234** jako identyczne dla pola `PatienID` .

W tym przykładzie, `caseInsensitive` `ignoredDelimiters` gdy zarówno są używane, jak i są używane, funkcja NR.UM będzie widzieć dane **FOO-1234** i **fOo#1234** jako identyczne i sklasyfikować produkt jako dane wrażliwych pacjentów.

Oba te parametry są używane na podstawie  per pola.

> [!IMPORTANT]
> Jeśli *skonfigurujesz* ignorowane spacje, będzie to obowiązuje tylko w przypadku kolumn pól podstawowych i dla których zdefiniowano typ informacji poufnych, który może wykrywać ciągi wielosłowne. W przeciwnym razie porównanie zostanie porównane z poszczególnymi wyrazami w analizowanej zawartości.

*Ignorowana flagaDelimiters* obsługuje dowolny znak niealalnumeryczny. Oto kilka przykładów:

- \.
- \-
- \/
- \_
- \*
- \^
- \#
- \!
- \?
- \[
- \]
- \{
- \}
- \\
- \~
- \;

Flaga `ignoredDelimiters` nie obsługuje:

- znaki 0-9
- A–Z
- a-z
- \"
- \,

> [!IMPORTANT]
> Podczas definiowania typu informacji poufnych EDM *ignorowanieDelimiters* nie ma wpływu na sposób, w jaki typ Informacji poufnych Klasyfikacja skojarzona z elementem podstawowym w wzorcu EDM identyfikuje zawartość w elemencie. Dlatego jeśli skonfigurujesz *ignorujedelimiters* dla pola z polem, które można wyszukiwać, musisz upewnić się, że typ informacji poufnych używany dla elementu podstawowego opartego na tym polu wybierze ciągi zarówno z tymi znakami, jak i bez nich.
>
> Liczba kolumn w tabeli źródła informacji poufnych i liczba pól w schemacie muszą być zgodne, kolejność nie ma znaczenia.

1. Zdefiniuj schemat w formacie XML (podobnie jak w poniższym przykładzie). Nadaj plikowi **schematu nazwęedm.xml** i skonfiguruj go tak, aby dla każdej kolumny w tabeli źródłowej informacji poufnych był wiersz o takiej składni:

      `\<Field name="" searchable=""/\>`.

      - Użyj nazw kolumn dla *wartości Nazwa* pola.
      - Dla *pól,* które mają być przeszukiwane, oraz pól podstawowych (maksymalnie 5) użyj wartości "prawda". Można wyszukiwać co najmniej jedno pole.

      Poniższy plik XML definiuje na przykład schemat bazy danych dokumentacji pacjentów z pięcioma polami określonymi jako można wyszukiwać: *PatientID*, *MRN*, *SSN*, *Telefon* i *DOB*.

      (Możesz kopiować, modyfikować i używać naszego przykładu).

      ```xml
      <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
            <DataStore name="PatientRecords" description="Schema for patient records" version="1">
                  <Field name="PatientID" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
                  <Field name="MRN" searchable="true" />
                  <Field name="FirstName" />
                  <Field name="LastName" />
                  <Field name="SSN" searchable="true" />
                  <Field name="Phone" searchable="true" />
                  <Field name="DOB" searchable="true" />
                  <Field name="Gender" />
                  <Field name="Address" />
            </DataStore>
      </EdmSchema>
      ```

   Po utworzeniu pliku schematu EDM w formacie XML należy przekazać go do usługi w chmurze.

2. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

3. Aby przekazać schemat bazy danych, uruchom następujące polecenie:

      ```powershell
      New-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Zostanie wyświetlony monit o potwierdzenie w następujący sposób:

      > Potwierdź
      >
      > Czy na pewno chcesz wykonać tę akcję?
      >
      > Zostanie zaimportowany nowy schemat usługi EDM dla magazynu danych "patientrecords".
      >
      > \[Y Yes A Yes to All \[N\] No \[L\] No to All \[?\]\] \[\] Pomoc (domyślna wartość to "Y"):

   > [!TIP]
   > Jeśli chcesz, aby zmiany wprowadzały się bez potwierdzenia, nie używaj ich w kroku `-Confirm:$true` 3.

> [!NOTE]
> Zaktualizowanie programu EDMSmSema przy użyciu dodatków może potrwać od 10 do 60 minut. Aktualizacja musi zostać ukończona przed wykonaniem kroków z zastosowaniem dodatków.

## <a name="next-step"></a>Następny krok

- [Skróty i przekazywanie tabeli źródła informacji poufnych w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)