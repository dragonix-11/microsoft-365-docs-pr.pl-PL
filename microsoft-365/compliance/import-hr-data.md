---
title: Konfigurowanie łącznika do importowania danych HR
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: Administratorzy mogą skonfigurować łącznik danych w celu importowania danych pracowników z systemu kadr (HR) swojej organizacji w celu Microsoft 365. Dzięki temu możesz używać danych kadrowych w zasadach zarządzania ryzykiem w niejawnym programie testów w celu wykrywania działań określonych użytkowników, które mogą stanowić zagrożenie wewnętrzne dla Organizacji.
ms.openlocfilehash: 64822b8ea5952f4fb6787dfd7832879c2e84c2d4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320959"
---
# <a name="set-up-a-connector-to-import-hr-data"></a>Konfigurowanie łącznika do importowania danych HR

Łącznik danych w aplikacji Centrum zgodności platformy Microsoft 365 można skonfigurować w celu importowania danych kadrowych związanych ze zdarzeniami, takimi jak ponowne przypisanie użytkownika lub zmiana na poziomie stanowiska użytkownika. Dane kadrowe mogą być następnie używane przez rozwiązanie [](insider-risk-management.md) do zarządzania ryzykiem w niejawnym programie testów do generowania wskaźników ryzyka, które mogą pomóc w tożsamości możliwych złośliwych działań lub kradzieży danych przez użytkowników w organizacji.

Konfigurowanie łącznika danych kadrowych, za pomocą których zasady zarządzania ryzykiem niejawnego programu testów mogą służyć do generowania wskaźników ryzyka, składa się z utworzenia pliku CSV zawierającego dane kadr, utworzenia aplikacji w programie Azure Active Directory używanej do uwierzytelniania, utworzenia łącznika danych kadrowych w aplikacji Centrum zgodności platformy Microsoft 365 , a następnie uruchamia (według harmonogramu) skrypt, który pozysuje dane dotyczące kadr w plikach CSV do chmury firmy Microsoft, aby była dostępna dla rozwiązania do zarządzania ryzykiem w niejawnym programie testów.

> [!IMPORTANT]
> Dostępna jest teraz nowa wersja łącznika kadr w publicznej wersji zapoznawczej. Aby utworzyć nowy łącznik kadr lub zaimportować dane do nowego scenariusza [](#csv-file-for-employee-profile-data-preview) profilu pracownika w scenariuszu zasad opieki zdrowotnej na temat zarządzania ryzykiem w niejawnym programie testów, przejdź do strony Łączniki danych w programie Centrum zgodności platformy Microsoft 365, wybierz kartę Łączniki, a następnie kliknij pozycję Dodaj łącznik **> HR (wersja zapoznawcza),** aby rozpocząć konfigurowanie. Istniejące łączniki hr będą nadal działać bez zakłóceń.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Określanie scenariuszy kadrowych i danych do zaimportowania Microsoft 365. Pomoże to ustalić, ile plików CSV i łączników HR należy utworzyć, a także w jaki sposób wygenerować i określić strukturę plików CSV. Importowane dane kadrowe są określane przez zasady zarządzania ryzykiem niejawnego programu testów, które chcesz wdrożyć. Aby uzyskać więcej informacji, zobacz Krok 1.

- Określ, jak pobierać lub eksportować dane z systemu kadr organizacji (i regularnie) i dodawać je do plików CSV tworzyć w kroku 1. Skrypt uruchomiony w kroku 4 spowoduje przekazanie danych hr z plików CSV do chmury firmy Microsoft.

- Użytkownik, który tworzy łącznik kadr w kroku 3, musi mieć przypisaną rolę Administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Przykładowy skrypt uruchomiony w kroku 4 spowoduje przekazanie danych kadrowych do chmury firmy Microsoft, aby można ich było używać w rozwiązaniu do zarządzania ryzykiem w niejawnym programie testów. Ten przykładowy skrypt nie jest obsługiwany w żadnym standardowym programie lub usłudze pomocy technicznej firmy Microsoft. Przykładowy skrypt jest dostarczany W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowego skryptu i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

- Ten łącznik jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP. Aby uzyskać instrukcje krok po kroku dotyczące konfigurowania łącznika kadr w środowisku GCC, zobacz Konfigurowanie łącznika do importowania danych kadrowych w administracji [Stanów Zjednoczonych](import-hr-data-US-government.md).

## <a name="step-1-prepare-a-csv-file-with-your-hr-data"></a>Krok 1. Przygotowanie pliku CSV z danymi hr

Pierwszym krokiem jest utworzenie pliku CSV zawierającego dane dotyczące kadr, które łącznik zaimportuje do Microsoft 365. Te dane będą używane przez rozwiązanie do generowania potencjalnych wskaźników ryzyka przez niejawny program testów. Dane dotyczące następujących scenariuszy dotyczących kadr można importować do Microsoft 365:

- Rezygnowanie pracowników. Informacje o pracownikach, którzy odeszli z organizacji.

- Zmienia się poziom zadań. Informacje o zmianach na poziomie stanowiska pracowników, takich jak promocje i spadki.

- Oceny wydajności. Informacje o wynikach pracowników.

- Plany poprawy wydajności. Informacje o planach poprawy wydajności dla pracowników.

- Profil pracownika (podgląd). Ogólne informacje o pracowniku.

Typ danych HR do zaimportowania zależy od zasad zarządzania ryzykiem w niejawnym programie testów i odpowiedniego szablonu zasad, które chcesz zaimplementować. W poniższej tabeli przedstawiono wymagany typ danych HR dla każdego szablonu zasad:

|  Szablon zasad |  typ danych HR |
|:------------------------------|:--------------------------------|
| Kradzież danych przez odchodzące użytkowników | Rezygnacje pracowników|
| Ogólne wycieki danych                             | Nie dotyczy|
| Wycieki danych według priorytetowych użytkowników                   | Nie dotyczy |
| Wycieki danych przez niezadowoniętych użytkowników                | Zmiany na poziomie zadań, Oceny wydajności, Plany poprawy wydajności|
| Naruszenia ogólnych zasad zabezpieczeń             | Nie dotyczy |
| Naruszenia zasad zabezpieczeń przez odchodzące użytkowników  | Rezygnacje pracowników|
| Naruszenia zasad zabezpieczeń przez użytkowników priorytetowych   | Nie dotyczy|
| Naruszenia zasad zabezpieczeń przez niezadowoniętych użytkowników| Zmiany na poziomie zadań, Oceny wydajności, Plany poprawy wydajności |
| Obraźliwy język w wiadomościach e-mail                    | Nie dotyczy |
| Zasady opieki zdrowotnej| Profil pracownika |
|||

Aby uzyskać więcej informacji o szablonach zasad do zarządzania ryzykiem w niejawnym programie testów, zobacz [Zasady zarządzania ryzykiem w niejawnym programie testów](insider-risk-management-policies.md#policy-templates).

Dla każdego scenariusza kadrowego musisz podać odpowiednie dane dotyczące kadr w jednym lub większej liczby plikach CSV. W dalszej części tej sekcji omówiono liczbę plików CSV, których należy użyć na użytek implementacji zarządzania ryzykiem w niejawnym programie testów.

Po utworzeniu pliku CSV z wymaganymi danymi hr należy go przechowywać na komputerze lokalnym, na których uruchamiasz skrypt w kroku 4. Należy także wdrożyć strategię aktualizacji, aby upewnić się, że plik CSV zawsze zawiera najnowsze informacje, dzięki czemu wszystko, co zostanie uruchomione w skrypcie, najnowsze dane dotyczące kadr zostaną przekazane do chmury firmy Microsoft i dostępne dla rozwiązania do zarządzania ryzykiem w niejawnym programie testów.

> [!IMPORTANT]
> Nazwy kolumn opisane w poniższych sekcjach nie są parametrami wymaganymi, ale tylko przykładami. W plikach CSV możesz użyć dowolnej nazwy kolumny. Jednak nazwy kolumn, których używasz w pliku CSV, muszą  zostać zamapowane na typ danych podczas tworzenia łącznika kadr w kroku 3. Pamiętaj także, że przykładowe pliki CSV w poniższych sekcjach są wyświetlane w widoku notatnika. Znacznie łatwiej jest wyświetlać i edytować pliki CSV w Microsoft Excel.

W poniższych sekcjach opisano wymagane dane CSV dla każdego scenariusza kadrowego.

### <a name="csv-file-for-employee-resignation-data"></a>Plik CSV zawierający dane dotyczące ponownego przypisania pracowników

Oto przykładowy plik CSV zawierający dane dotyczące ponownego przypisania pracowników.

```text
EmailAddress,ResignationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

W poniższej tabeli opisano każdą kolumnę w pliku CSV zawierającą dane dotyczące ponownego przypisania pracowników.

|  Kolumna   |   Opis |
|:------------|:----------------|
|**EmailAddress (Adres e-mail)**| Określa adres e-mail (UPN) zakończonego użytkownika.|
| **ResignationDate** | Określa datę oficjalnego zakończenia stosunku pracy użytkownika w organizacji. Może to być na przykład data, kiedy użytkownik przekazał mu powiadomienie o opuszczeniu organizacji. Ta data może być inna niż data ostatniego dnia pracy danej osoby. Użyj następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest formatem [daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **LastWorkingDate** | Określa ostatni dzień pracy dla zakończonego użytkownika. Użyj następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest formatem [daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

### <a name="csv-file-for-job-level-changes-data"></a>Plik CSV zawierający dane na poziomie zadań zmienia dane

Oto przykładowy plik CSV, w który dane są zmieniane na poziomie zadań.

```text
EmailAddress,EffectiveDate,OldLevel,NewLevel
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 61 – Sr. Manager,Level 60- Manager
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 62 – Director,Level 60- Sr. Manager
```

W poniższej tabeli opisano każdą kolumnę w pliku CSV, w których dane są zmieniane na poziomie zadań.

|  Kolumna | Opis |
|:--------- |:------------- |
| **EmailAddress (Adres e-mail)**  | Określa adres e-mail użytkownika (UPN).|
| **EffectiveDate** | Określa datę oficjalnie zmienionego poziomu zadań użytkownika. Użyj następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest formatem [daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Spostrzeżenia**| Określa uwagi osoby oceniające dotyczące zmiany poziomu zadań. Możesz wprowadzić limit 200 znaków. Ten parametr jest opcjonalny. Nie musisz uwzględniać go w pliku CSV.|
| **OldLevel**| Określa poziom zadań użytkownika przed jego zmianą. Jest to parametr free-text, który może zawierać hierarchiczną taksonomię dla organizacji. Ten parametr jest opcjonalny. Nie musisz uwzględniać go w pliku CSV.|
| **NewLevel**| Określa poziom zadań użytkownika po jego zmianie. Jest to parametr free-text, który może zawierać hierarchiczną taksonomię dla organizacji. Ten parametr jest opcjonalny. Nie musisz uwzględniać go w pliku CSV.|
|||

### <a name="csv-file-for-performance-review-data"></a>Plik CSV zawierający dane recenzji wydajności

Oto przykładowy plik CSV zawierający dane dotyczące wydajności.

```text
EmailAddress,EffectiveDate,Remarks,Rating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

W poniższej tabeli opisano poszczególne kolumny w pliku CSV, w których przedstawiono dane dotyczące przeglądu wydajności.

|  Kolumna | Opis |
|:----------|:--------------|
| **EmailAddress (Adres e-mail)**  | Określa adres e-mail użytkownika (UPN).|
| **EffectiveDate** | Określa datę oficjalnie poinformowania użytkownika o wyniku przeglądu wydajności. Może to być data zakończenia cyklu przeglądu wydajności. Użyj następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest formatem [daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Spostrzeżenia**| Określa wszelkie uwagi przekazane użytkownikowi przez oceniającego podczas przeglądu wydajności. Jest to parametr tekstowy z ograniczeniem do 200 znaków. Ten parametr jest opcjonalny. Nie musisz uwzględniać go w pliku CSV.|
| **Ocena**| Określa ocenę podaną w przeglądzie wydajności. Jest to parametr tekstowy, który może zawierać dowolny tekst w dowolnej postaci, który jest używany w organizacji do rozpoznania oceny. Na przykład "3 Spełnione oczekiwania" lub "2 Poniżej średniej". Jest to parametr tekstowy z ograniczeniem do 25 znaków. Ten parametr jest opcjonalny. Nie musisz uwzględniać go w pliku CSV.|
|||

### <a name="csv-file-for-performance-improvement-plan-data"></a>Plik CSV zawierający dane planu poprawy wydajności

Oto przykładowy plik CSV zawierający dane dotyczące danych planu poprawy wydajności.

```text
EmailAddress,EffectiveDate,ImprovementRemarks,PerformanceRating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

W poniższej tabeli opisano poszczególne kolumny w pliku CSV, w których przedstawiono dane dotyczące przeglądu wydajności.

|  Kolumna |  Opis |
|:----------|:---------------|
| **EmailAddress (Adres e-mail)**  | Określa adres e-mail użytkownika (UPN).|
| **EffectiveDate** | Określa datę oficjalnie poinformowania użytkownika o planie poprawy wydajności. Należy użyć następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest formatem [daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Spostrzeżenia**| Określa wszelkie uwagi osoby oceniające dotyczące planu poprawy wydajności. Jest to parametr tekstowy z ograniczeniem do 200 znaków. Jest to parametr opcjonalny. Nie musisz uwzględniać go w pliku CSV. |
| **Ocena**| Określa ocenę lub inne informacje związane z przeglądem wydajności. Jest to parametr tekstowy, który może zawierać dowolny dowolny tekst formularza używany przez organizację do rozpoznania oceny. Na przykład "3 Spełnione oczekiwania" lub "2 Poniżej średniej". Jest to parametr tekstowy z ograniczeniem do 25 znaków. Jest to parametr opcjonalny. Nie musisz uwzględniać go w pliku CSV.|
|||

### <a name="csv-file-for-employee-profile-data-preview"></a>Plik CSV zawierający dane profilu pracownika (podgląd)

> [!NOTE]
> Możliwość tworzenia łącznika kadr dla danych profilu pracownika jest publiczna wersja zapoznawcza. Aby utworzyć łącznik kadr obsługujący dane profilu pracownika, przejdź do strony Łączniki danych w Centrum zgodności platformy Microsoft 365, wybierz kartę Łączniki,  a następnie kliknij pozycję Dodaj  **łącznikHR** >  **(podgląd)**. Postępuj zgodnie z instrukcjami, aby utworzyć łącznik w [Kroku 3: Tworzenie łącznika kadr](#step-3-create-the-hr-connector).

Oto przykładowy plik CSV zawierający dane dotyczące danych profilu pracownika.

```text
EmailAddress,UserName,EmployeeFirstName,EmployeeLastName,EmployeeAddLine1,EmployeeAddLine2,EmployeeCity,EmployeeState,EmployeeZipCode,EmployeeDept,EmployeeType,EmployeeRole
jackq@contoso.com,jackq,jack,qualtz,50 Oakland Ave,#206,City,Florida,32104,Orthopaedic,Regular,Nurse
```

W poniższej tabeli opisano każdą kolumnę w pliku CSV zawierającą dane profilów pracowników.

|  Kolumna |  Opis |
|:----------|:---------------|
| EmailAddress (Adres e-mail)<sup>*</sup>    | Główna nazwa użytkownika (UPN) lub adres e-mail pracownika.|
| EmployeeFirstName<sup>*</sup>   | Imię pracownika.|
| EmployeeLastName<sup>*</sup>   | Nazwisko pracownika.|
| EmployeeAddressLine1<sup>*</sup>    | Ulica pracownika.|
| EmployeeAddressLine2   | Dodatkowe informacje adresowe, takie jak numer telefonu pracownika.|
| EmployeeCity | Miasto zamieszkania pracownika.|
| EmployeeState | Stan zamieszkania pracownika.|
| EmployeeZipCode<sup>*</sup>  | Kod pocztowy miejsca zamieszkania pracownika. |
| EmployeeCountry| Kraj zamieszkania pracownika.|
| EmployeeDepartment | Dział pracownika w organizacji.|
| EmployeeType (Typ pracownika) |Typ zatrudnienia pracownika, na przykład Zwykły, Wykluczony lub Wykonawca.|
| Rejestracja pracownika |Rola, oznaczenie lub stanowisko pracowników w organizacji.|
|||

> [!NOTE]
> <sup>*</sup> Ta kolumna jest obowiązkowa. Jeśli brakuje obowiązkowej kolumny, nie zostanie sprawdzona poprawność pliku CSV i nie zostaną zaimportowane inne dane z pliku.

Zalecamy utworzenie łącznika kadr, który będzie importować tylko dane profilów pracowników. W przypadku tego łącznika pamiętaj, aby regularnie odświeżać dane profilu pracownika, najlepiej co 15 do 20 dni. Rekordy profilów pracowników zostaną usunięte, jeśli nie zostaną zaktualizowane w ciągu ostatnich 30 dni.

### <a name="determining-how-many-csv-files-to-use-for-hr-data"></a>Określanie ilu plików CSV należy użyć na podstawie danych hr

W kroku 3 możesz utworzyć osobne łączniki dla każdego typu danych HR lub utworzyć pojedynczy łącznik dla wszystkich typów danych. Możesz użyć osobnych plików CSV zawierających dane dla jednego scenariusza kadrowego (na przykład z przykładów plików CSV opisanych w poprzednich sekcjach). Możesz też użyć jednego pliku CSV zawierającego dane dla dwóch lub większej liczby scenariuszy kadrowych. Oto kilka wskazówek pomocnych w ustaleniu, ile plików CSV należy użyć na podstawie danych hr.

- Jeśli zasady zarządzania ryzykiem niejawnego programu testów, które chcesz zaimplementować, wymagają wielu typów danych HR, rozważ użycie jednego pliku CSV zawierającego wszystkie wymagane typy danych.

- Metoda generowania lub zbierania danych hr może określać liczbę plików CSV. Jeśli na przykład różne typy danych hr używanych do konfigurowania łącznika kadr znajdują się w jednym systemie kadr w organizacji, możesz wyeksportować dane do jednego pliku CSV. Jeśli jednak dane są rozłożone w różnych systemach KADR, łatwiej będzie wyeksportować dane do różnych plików CSV. Na przykład dane dotyczące ponownego stanowiska pracowników mogą się znaleźć w innym systemie kadr niż dane na poziomie stanowiska lub w danych przeglądu wydajności. W takim przypadku łatwiej jest mieć osobne pliki CSV zamiast ręcznego łączenia danych w jeden plik CSV. Dlatego sposób pobierania lub eksportowania danych z systemów hr może ustalić, jaka liczba plików CSV będzie potrzebna.

- Ogólnie rzecz biorąc, liczba łączników HR, które należy utworzyć, zależy od typów danych w pliku CSV. Jeśli na przykład plik CSV zawiera wszystkie typy danych wymagane do obsługi implementacji zarządzania ryzykiem w niejawnym programie testów, potrzebny jest tylko jeden łącznik kadr. Jeśli jednak masz dwa osobne pliki CSV, z których każdy zawiera jeden typ danych, musisz utworzyć dwa łączniki HR. Jedynym wyjątkiem jest to, że jeśli dodasz kolumnę **HRScentz** do pliku CSV (zobacz następną sekcję), możesz skonfigurować pojedynczy łącznik kadr, który będzie przetwarzał różne pliki CSV.

### <a name="configuring-a-single-csv-file-for-multiple-hr-data-types"></a>Konfigurowanie jednego pliku CSV dla wielu typów danych HR

Do jednego pliku CSV możesz dodać wiele typów danych HR. Jest to przydatne, jeśli wdrażane rozwiązanie do zarządzania ryzykiem w ramach niejawnego programu testów wymaga wielu typów danych hr lub jeśli typy danych znajdują się w jednym systemie kadr w organizacji. Mniejsza liczba plików CSV zawsze pozwala na utworzenie i zarządzanie mniej łącznikami HR.

Oto wymagania dotyczące konfigurowania pliku CSV z wieloma typami danych:

- Musisz dodać wymagane kolumny (i opcjonalnie, jeśli ich używasz) dla każdego typu danych i odpowiednią nazwę kolumny w wierszu nagłówka. Jeśli typ danych nie odpowiada kolumnie, możesz pozostawić wartość pustą.

- Aby użyć pliku CSV z wieloma typami danych HR, łącznik kadr musi wiedzieć, które wiersze w pliku CSV zawierają typ danych HR. Można to zrobić, dodając do pliku CSV dodatkową kolumnę **HRScentz** . Wartości w tej kolumnie identyfikują typ danych hr w każdym wierszu. Na przykład wartościami, \`które odpowiadają czterem scenariuszom kadr, może być Ponowne przypisanie,\`\` Zmiana stanowiska, \`\`Przegląd wydajności, \`Plan\`\` poprawy wydajności i Profil pracownika\`.\`

- Jeśli masz wiele plików CSV zawierających kolumnę HRScentz**, upewnij się, że każdy plik używa tej samej nazwy kolumny i tych samych wartości, które identyfikują określone scenariusze dotyczące kadr.

W poniższym przykładzie pokazano plik CSV zawierający **kolumnę HRScentz** . Wartości w kolumnie HRScentz identyfikują typ danych w odpowiednim wierszu.

```text
HRScenario,EmailAddress,ResignationDate,LastWorkingDate,EffectiveDate,Remarks,Rating,OldLevel,NewLevel
Resignation,sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30,,,,
Resignation,pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540,,,,
Job level change,sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,,,,,Level 61 Sr. Manager, Level 60 Manager
Job level change,pillarp@contoso.com,2019-04-23T15:18:02.4675041+05:30,,,,,Level 62 Director,Level 60 Sr Manager
Performance review,sarad@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2 Below expectations,,
Performance review,pillarp@contoso.com,,,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team,,
Performance improvement plan,sarad@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2 Below expectations,,
Performance improvement plan,pillarp@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Multiple conflicts with the team,,
```

> [!NOTE]
> Dla kolumny identyfikującej typ danych KADR można użyć dowolnej nazwy, ponieważ zamapuje się nazwę kolumny w pliku CSV jako kolumnę identyfikującą typ danych KADR podczas konfigurowanie łącznika w kroku 3. Zamapuje się też wartości używane dla kolumny typu danych podczas konfigurowanie łącznika.

### <a name="adding-the-hrscenario-column-to-a-csv-file-that-contains-a-single-data-type"></a>Dodawanie kolumny HRScentz do pliku CSV zawierającego jeden typ danych

Na podstawie systemów HR Twojej organizacji i sposobu eksportowania danych hr do pliku CSV może być konieczne utworzenie wielu plików CSV zawierających jeden typ danych HR. W takim przypadku można mimo to utworzyć pojedynczy łącznik kadr w celu zaimportowania danych z różnych plików CSV. Aby to zrobić, wystarczy dodać kolumnę HRScen tylko do pliku CSV i określić typ danych HR. Następnie można uruchomić skrypt dla każdego pliku CSV, ale dla łącznika użyj tego samego identyfikatora zadania. Zobacz [Krok 4](#step-4-run-the-sample-script-to-upload-your-hr-data).

## <a name="step-2-create-an-app-in-azure-active-directory"></a>Krok 2. Tworzenie aplikacji w aplikacji Azure Active Directory

Następnym krokiem jest utworzenie i zarejestrowanie nowej aplikacji w usłudze Azure Active Directory (Azure AD). Aplikacja będzie odpowiadać łącznikowi hr, który został utworzyć w kroku 3. Utworzenie tej aplikacji umożliwi usłudze Azure AD uwierzytelnienie łącznika kadr podczas jego uruchamiania i próby uzyskania dostępu do organizacji. Ta aplikacja będzie również używana do uwierzytelniania skryptu uruchomionego w kroku 4 w celu przekazania danych HR do chmury firmy Microsoft. Podczas tworzenia tej aplikacji Azure AD pamiętaj o zapisaniu poniższych informacji. Te wartości zostaną użyte w krokach 3 i 4.

- Identyfikator aplikacji usługi Azure AD (nazywany również *identyfikatorem aplikacji* lub *identyfikatorem klienta*)

- Klucz tajny aplikacji usługi Azure AD (nazywany także *kluczem tajnym klienta*)

- Identyfikator dzierżawy (nazywany również *identyfikatorem katalogu*)

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji w usłudze Azure AD, zobacz [Rejestrowanie](/azure/active-directory/develop/quickstart-register-app) aplikacji w Platforma tożsamości Microsoft.

## <a name="step-3-create-the-hr-connector"></a>Krok 3. Tworzenie łącznika kadr

Następnym krokiem jest utworzenie łącznika kadr w Centrum zgodności platformy Microsoft 365. Po uruchomieniu skryptu w kroku 4 zostanie uruchomiony łącznik hr, który utworzysz, aby dane dotyczące kadr z pliku CSV trafiły do Twojej Microsoft 365 organizacji. Przed utworzeniem łącznika upewnij się, że masz listę scenariuszy kadr i odpowiadające im nazwy kolumn w formacie CSV dla każdego z nich. Podczas konfigurowania łącznika musisz zamapować dane wymagane w każdym scenariuszu na rzeczywiste nazwy kolumn w pliku CSV. Możesz również przekazać przykładowy plik CSV podczas konfigurowania łącznika, a kreator pomoże Zamapować nazwy kolumn na wymagane typy danych.

Po zakończeniu tego kroku pamiętaj o skopiowaniu identyfikatora zadania wygenerowanego podczas tworzenia łącznika. Identyfikator zadania zostanie uruchomiony podczas uruchamiania skryptu.

1. Przejdź do Centrum zgodności platformy Microsoft 365 i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a>.

2. Na stronie **Łączniki** danych kliknij pozycję **Kadry (wersja zapoznawcza)**.

3. Na stronie **Kadry (wersja zapoznawcza)** kliknij **pozycję Dodaj łącznik**.

4. Na stronie **Konfigurowanie połączenia** wykonaj następujące czynności, a następnie kliknij przycisk **Dalej**:

   1. Wpisz lub wklej identyfikator aplikacji usługi Azure AD dla aplikacji azure utworzonej w kroku 2.

   2. Wpisz nazwę łącznika kadr.

5. Na stronie Scenariusze dotyczące kadr wybierz co najmniej jeden scenariusz kadrowy, do którego chcesz zaimportować dane, a następnie kliknij przycisk **Dalej**.

   ![Wybierz jeden lub więcej scenariuszy kadrowych.](../media/HRConnectorScenarios.png)

6. Na stronie metody mapowania plików wybierz w razie potrzeby typ pliku, wybierz jedną z następujących opcji, a następnie kliknij przycisk **Dalej**.

   - **Upload przykładowy plik**. Jeśli wybierzesz tę opcję, kliknij pozycję **Upload przykładowy plik**, aby przekazać plik CSV przygotowany w kroku 1. Ta opcja pozwala szybko wybrać nazwy kolumn w pliku CSV z listy rozwijanej, aby zamapować je na typy danych dla wybranych wcześniej scenariuszy dotyczących kadr.

   LUB

   - **Ręcznie podaj szczegóły mapowania**. Jeśli wybierzesz tę opcję, musisz wpisać nazwy kolumn w pliku CSV, aby zamapować je na typy danych dla wcześniej wybranych scenariuszy dotyczących kadr.

7. Na stronie Szczegóły mapowania plików wykonaj jedną z następujących czynności w zależności od tego, czy przekazany został przykładowy plik CSV i czy łącznik konfiguruje się dla jednego scenariusza kadr, czy dla wielu scenariuszy. Jeśli został przekazany przykładowy plik, nie musisz wpisywać nazw kolumn. Wybierasz je z listy rozwijanej.

    - Jeśli w poprzednim kroku wybrano pojedynczy scenariusz kadrowy, w każdym z odpowiednich pól wpisz nazwy nagłówków kolumn (nazywane również parametrami *) z* pliku CSV utworzonego w kroku 1. W wpisywania nazw kolumn nie jest uwzględniana wielkość liter, ale pamiętaj, aby uwzględnić spacje, jeśli nazwy kolumn w pliku CSV zawierają spacje. Jak wyjaśniono wcześniej, nazwy wpisywania w tych polach muszą być zgodne z nazwami parametrów w pliku CSV. Na przykład na poniższym zrzucie ekranu pokazano nazwy parametrów z przykładowego pliku CSV scenariusza kadry resignacji pracownika przedstawionego w kroku 1.

    - Jeśli w kroku powyżej wybrano wiele typów danych, musisz wprowadzić nazwę kolumny identyfikatora identyfikującego typ danych KADR w pliku CSV. Po wprowadzeniu nazwy kolumny identyfikatora wpisz wartość identyfikującą ten typ danych HR i wpisz nazwy nagłówków kolumn dla wybranych typów danych z plików CSV utworzonych w kroku 1 w każdym z odpowiednich pól dla każdego wybranego typu danych. Jak wyjaśniono wcześniej, nazwy wpisywania w tych polach muszą być zgodne z nazwami kolumn w pliku CSV.

8. Na stronie **Recenzja** przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

   Zostanie wyświetlona strona stanu z potwierdzeniem utworzenia łącznika. Ta strona zawiera dwie ważne czynności, które należy wykonać w następnym kroku w celu uruchomienia przykładowego skryptu w celu przekazania danych HR.

   ![Strona Recenzja z identyfikatorem zadania i linkiem do witryny github na przykładowy skrypt.](../media/HRConnector_Confirmation.png)

   1. **Identyfikator zadania.** Ten identyfikator zadania będzie potrzebny do uruchomienia skryptu w następnym kroku. Możesz skopiować ją z tej strony lub ze strony wysuwu łącznika.

   2. **Link do przykładowego skryptu.** Kliknij link **tutaj**, aby przejść do witryny GitHub w celu uzyskania dostępu do przykładowego skryptu (link otworzy nowe okno). Zachowaj to okno otwarte, aby można było skopiować skrypt w kroku 4. Alternatywnie możesz dodać zakładkę do miejsca docelowego lub skopiować adres URL, aby ponownie uzyskać do niego dostęp po uruchomieniu skryptu. Ten link jest również dostępny na wysuwana strona łącznika.

9. Kliknij **przycisk Gotowe**.

   Nowy łącznik zostanie wyświetlony na liście na karcie **Łączniki** .

10. Kliknij właśnie utworzony łącznik kadrowy, aby wyświetlić stronę wysuwu zawierającą właściwości i inne informacje o łączniku.

   ![Wysuuwana strona nowego łącznika KADR.](../media/HRConnectorWizard7.png)

Jeśli jeszcze tego nie zrobiono, możesz skopiować wartości identyfikatorów aplikacji **Azure** i **identyfikatora zadania łącznika**. Będą one potrzebne do uruchomienia skryptu w następnym kroku. Skrypt można również pobrać ze strony wysuwu (lub za pomocą linku w następnym kroku).

Możesz również kliknąć pozycję **Edytuj,** aby zmienić identyfikator aplikacji Azure lub nazwy nagłówków kolumn zdefiniowane na **stronie Mapowanie** plików.

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Krok 4. Uruchamianie przykładowego skryptu w celu przekazania danych HR

Ostatnim krokiem podczas konfigurowania łącznika kadr jest uruchomienie przykładowego skryptu, który przekaże dane dotyczące kadr w pliku CSV (utworzonym w kroku 1) do chmury firmy Microsoft. W szczególności skrypt przekaże dane do łącznika kadr. Po uruchomieniu skryptu łącznik kadr utworzony w kroku 3 zaim importuje dane kadr do Organizacji programu Microsoft 365, gdzie można uzyskać do nich dostęp za pomocą innych narzędzi do zgodności, takich jak rozwiązanie do zarządzania ryzykiem w niejawnym programie testów. Po uruchomieniu skryptu rozważ zaplanowanie zadania tak, aby było uruchamiane automatycznie codziennie, aby najnowsze dane o zakończeniu pracy pracownika były przekazywane do chmury firmy Microsoft. Zobacz [Planowanie automatycznego uruchamiania skryptu](#optional-step-6-schedule-the-script-to-run-automatically).

1. Przejdź do okna otwartego z poprzedniego kroku, aby uzyskać dostęp do witryny GitHub za pomocą przykładowego skryptu. Ewentualnie otwórz witrynę z zakładką lub użyj skopiowanego adresu URL. Możesz również uzyskać dostęp do skryptu [tutaj](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Kliknij przycisk **Nieprzetworzone** , aby wyświetlić skrypt w widoku tekstu.

3. Skopiuj wszystkie wiersze w przykładowym skrypcie, a następnie zapisz je w pliku tekstowym.

4. W razie potrzeby zmodyfikuj przykładowy skrypt dla organizacji.

5. Zapisz plik tekstowy jako plik Windows PowerShell skryptu, używając sufiksu nazwy `.ps1`pliku , na przykład `HRConnector.ps1`. Alternatywnie możesz użyć nazwy GitHub pliku dla skryptu, czyli `upload_termination_records.ps1`.

6. Otwórz wiersz polecenia na komputerze lokalnym i przejdź do katalogu, w którym został zapisany skrypt.

7. Uruchom następujące polecenie, aby przekazać dane kadrowe z pliku CSV do chmury firmy Microsoft. na przykład:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
    ```

   W poniższej tabeli opisano parametry, których należy użyć w tym skrypcie, oraz ich wymagane wartości. Informacje uzyskane w poprzednich krokach są używane w wartościach tych parametrów.

   | Parametr | Opis |
   |:-----|:-----|:-----|
   |`tenantId`|Jest to identyfikator organizacji, Microsoft 365 uzyskany w kroku 2. Możesz również uzyskać identyfikator dzierżawy organizacji na stronie **Omówienie** w centrum administracyjnym usługi Azure AD. Służy on do identyfikowania Twojej organizacji.|
   |`appId` |Jest to identyfikator aplikacji usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 2. Jest to używane przez usługę Azure AD do uwierzytelniania, gdy skrypt próbuje uzyskać dostęp do Twojej Microsoft 365 organizacji. | 
   |`appSecret`|Jest to tajny program usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 2. Ta metoda jest również używana do uwierzytelniania.|
   |`jobId`|Jest to identyfikator zadania łącznika kadr utworzonego w kroku 3. Służy to do kojarzenia danych hr przekazywanych do chmury firmy Microsoft z łącznikiem kadr.|
   |`filePath`|Jest to ścieżka do pliku (przechowywanego w tym samym systemie, co skrypt) utworzonego w kroku 1. Postaraj się uniknąć spacji w ścieżce pliku. w przeciwnym razie należy użyć cudzysłowów pojedynczych.|
   |||

   Oto przykład składni skryptu łącznika kadr z użyciem rzeczywistych wartości dla każdego parametru:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Jeśli przekazywanie się powiedzie, skrypt wyświetli komunikat o **błędzie Upload pomyślny**.

   > [!NOTE]
   > Jeśli masz problemy z uruchamianiem poprzedniego polecenia z powodu zasad wykonywania, zobacz [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) Informacje o zasadach wykonywania i Ustawianie [zasad](/powershell/module/microsoft.powershell.security/set-executionpolicy) wykonywania, aby uzyskać wskazówki dotyczące ustawiania zasad wykonywania.

## <a name="step-5-monitor-the-hr-connector"></a>Krok 5. Monitorowanie łącznika kadr

Po utworzeniu łącznika kadr i uruchomieniu skryptu w celu przekazania danych hr możesz wyświetlić łącznik i stan przekazywania w Centrum zgodności platformy Microsoft 365. Jeśli skrypt ma być uruchamiany automatycznie regularnie, można także wyświetlić bieżący stan po ostatnim uruchomieniu skryptu.

1. Przejdź do Centrum zgodności platformy Microsoft 365 i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a>.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik KADR, aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

   ![Wysuuwana strona łącznika kadr z właściwościami i stanem.](../media/HRConnectorFlyout1.png)

3. W **obszarze** Postęp kliknij link **Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o każdym uruchamianiu skryptu i przekazywaniu danych z pliku CSV do chmury firmy Microsoft. 

   ![W pliku dziennika łącznika kadr są wyświetlane wiersze liczb z przekazanego pliku CSV.](../media/HRConnectorLogFile.png)

   Pole `RecordsSaved` wskazuje liczbę wierszy w przekazanym pliku CSV. Jeśli na przykład plik CSV zawiera cztery wiersze, `RecordsSaved` wartość pól wynosi 4, jeśli skrypt pomyślnie przesłał wszystkie wiersze w pliku CSV.

Jeśli nie został uruchomiony skrypt w kroku 4, w obszarze Ostatni import jest wyświetlany link do pobierania **skryptu**. Możesz pobrać skrypt, a następnie wykonać te instrukcje, aby go uruchomić.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Opcjonalnie) Krok 6. Planowanie automatycznego uruchamiania skryptu

Aby upewnić się, że najnowsze dane kadrowe z Twojej organizacji są dostępne dla narzędzi, takich jak rozwiązanie do zarządzania ryzykiem w niejawnym programie testów, zalecamy cykliczne uruchamianie skryptu, na przykład raz dziennie. Wymaga to również zaktualizowania danych kadrowych w pliku CSV zgodnie z podobnym (jeśli nie tym samym) harmonogramem, tak aby zawierał najnowsze informacje o pracownikach opuszczanych twoją organizację. Celem jest przekazanie najbardziej aktualnych danych hr, aby łącznik kadr był dostępny w rozwiązaniu do zarządzania ryzykiem w niejawnym programie testów.

Za pomocą aplikacji Harmonogram zadań w programie Windows uruchamiać skrypt automatycznie każdego dnia.

1. Na komputerze lokalnym kliknij przycisk Windows **Start**, a następnie wpisz **Harmonogram zadań**.

2. Kliknij aplikację **Harmonogram zadań** , aby ją otworzyć.

3. W sekcji **Akcje** kliknij pozycję **Utwórz zadanie**.

4. Na **karcie** Ogólne wpisz opisową nazwę zaplanowanego zadania. Na przykład skrypt **łącznika KADR**. Możesz również dodać opcjonalny opis.

5. W **obszarze Opcje zabezpieczeń** wykonaj następujące czynności:

   1. Określ, czy skrypt ma być uruchamiany tylko po zalogowaniu się na komputerze, czy po zalogowaniu się.

   1. Upewnij się, że **jest zaznaczone pole** wyboru Uruchom z najwyższymi uprawnieniami.

6. Wybierz **kartę Wyzwalacze** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

   1. W **Ustawienia** **kliknij opcję Dzienny**, a następnie wybierz datę i czas do uruchomienia skryptu po raz pierwszy. Skrypt będzie uruchamiany każdego dnia o tej samej określonej godzinie.

   1. Upewnij **się, że** w obszarze Ustawienia zaawansowane jest **zaznaczone** pole wyboru Włączone.

   1. Kliknij **przycisk OK**.

7. Wybierz **kartę Akcje** , kliknij **pozycję Nowy**, a następnie wykonaj następujące czynności:

   ![Ustawienia akcji w celu utworzenia nowego zaplanowanego zadania dla skryptu łącznika kadr.](../media/HRConnectorScheduleTask1.png)

   1. Na liście **rozwijanej** Akcja upewnij się, że jest **wybrana opcja Uruchom** program.

   1. W **polu Program/skrypt** kliknij przycisk **Przeglądaj**, przejdź do następującej lokalizacji i wybierz ją, aby ścieżka była wyświetlana w polu: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`.

   1. W **polu Dodaj argumenty (opcjonalnie)** wklej to samo polecenie skryptu, które było uruchomiono w kroku 4. Na przykład `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. W polu **Rozpocznij w (opcjonalnie)** wklej lokalizację folderu skryptu, który został uruchomiony w kroku 4. Na przykład `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Kliknij **przycisk OK** , aby zapisać ustawienia nowej akcji.

8. W **oknie Tworzenie** zadania kliknij przycisk **OK** , aby zapisać zaplanowane zadanie. Może zostać wyświetlony monit o wprowadzenie poświadczeń konta użytkownika.

   Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.

   ![Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.](../media/HRConnectorTaskSchedulerLibrary.png)

   Zostanie wyświetlony czas ostatniego uruchomienia skryptu i następnego uruchomienia tego skryptu. Możesz kliknąć dwukrotnie zadanie, aby je edytować.

   Możesz także sprawdzić czas ostatniego uruchamiania skryptu na wysuwanych stronie odpowiedniego łącznika kadr w centrum zgodności.

## <a name="existing-hr-connectors"></a>Istniejące łączniki HR

13 grudnia 2021 r. opublikowano scenariusz danych profilu pracownika dla łączników hr. Jeśli przed tą datą utworzono łącznik kadr, przemigrujemy istniejące wystąpienia lub łączniki KADR Twojej organizacji, aby dane kadrowe nadal zostały zaimportowane do chmury firmy Microsoft. Nie musisz nic robić, aby zachować tę funkcję. Łączników tych można nadal używać bez zakłóceń.

Jeśli chcesz zaimplementować scenariusz danych profilu pracownika, utwórz nowy łącznik kadr i skonfiguruj go zgodnie z wymaganiami. Po utworzeniu nowego łącznika kadr uruchom skrypt, używając identyfikatora zadania nowego łącznika i plików CSV z danymi profilu pracownika [](#csv-file-for-employee-profile-data-preview) opisanymi wcześniej w tym artykule.
