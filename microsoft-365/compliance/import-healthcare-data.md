---
title: Konfigurowanie łącznika w celu importowania ogólnych danych inspekcji opieki zdrowotnej
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik danych w celu importowania elektronicznych danych ewidencji opieki zdrowotnej (EHR) z systemu opieki zdrowotnej na platformę Microsoft 365. Dzięki temu można używać danych EHR w zasadach zarządzania ryzykiem wewnętrznym, aby ułatwić wykrywanie nieautoryzowanego dostępu do danych pacjentów przez pracowników.
ms.openlocfilehash: be5429ea1a5fb4e2e2be6a7029f2401fcbdab94e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641389"
---
# <a name="set-up-a-connector-to-import-healthcare-ehr-audit-data-preview"></a>Konfigurowanie łącznika w celu importowania danych inspekcji EHR opieki zdrowotnej (wersja zapoznawcza)

Łącznik danych można skonfigurować w portal zgodności Microsoft Purview w celu zaimportowania danych inspekcji aktywności użytkowników w systemie Elektronicznej Dokumentacji Opieki Zdrowotnej (EHR) w organizacji. Dane inspekcji z systemu EHR opieki zdrowotnej obejmują dane dotyczące zdarzeń związanych z uzyskiwaniem dostępu do dokumentacji medycznej pacjenta. Dane inspekcji healthcare EHR mogą być używane przez [rozwiązanie do zarządzania ryzykiem wewnętrznym](insider-risk-management.md) platformy Microsoft 365, aby chronić organizację przed nieautoryzowanym dostępem do informacji o pacjentach.

Konfigurowanie łącznika opieki zdrowotnej składa się z następujących zadań:

- Tworzenie aplikacji w usłudze Azure Active Directory (Azure AD) w celu uzyskania dostępu do punktu końcowego interfejsu API, który akceptuje plik tekstowy rozdzielony tabulatorem zawierający dane inspekcji EHR opieki zdrowotnej.

- Tworzenie pliku tekstowego ze wszystkimi polami wymaganymi zgodnie ze schematem łącznika.

- Tworzenie wystąpienia łącznika opieki zdrowotnej w portalu zgodności.

- Uruchamianie skryptu wypychania danych inspekcji EHR opieki zdrowotnej do punktu końcowego interfejsu API.

- Opcjonalnie zaplanowanie automatycznego uruchomienia skryptu w celu zaimportowania danych inspekcji.

## <a name="before-you-set-up-the-connector"></a>Przed skonfigurowaniem łącznika

- Użytkownik, który tworzy łącznik opieki zdrowotnej w kroku 3, musi mieć przypisaną rolę łącznika danych Administracja. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Musisz określić sposób pobierania lub eksportowania danych z systemu EHR opieki zdrowotnej w organizacji (codziennie) i utworzyć plik tekstowy opisany w kroku 2. Skrypt uruchamiany w kroku 4 spowoduje wypchnięcie danych w pliku tekstowym do punktu końcowego interfejsu API.

- Przykładowy skrypt uruchamiany w kroku 4 wypycha dane inspekcji EHR opieki zdrowotnej z pliku tekstowego do interfejsu API łącznika, dzięki czemu mogą być używane przez rozwiązanie do zarządzania ryzykiem wewnętrznym. Ten przykładowy skrypt nie jest obsługiwany w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowy skrypt jest dostarczany jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowego skryptu i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w usłudze Azure Active Directory

Pierwszym krokiem jest utworzenie i zarejestrowanie nowej aplikacji w usłudze Azure Active Directory (Azure AD). Aplikacja będzie odpowiadać łącznikowi opieki zdrowotnej utworzonemu w kroku 3. Utworzenie tej aplikacji umożliwia Azure AD uwierzytelnianie żądania wypychania dla pliku tekstowego zawierającego dane inspekcji EHR opieki zdrowotnej. Podczas tworzenia tej aplikacji Azure AD zapisz następujące informacje. Te wartości będą używane w kolejnych krokach.

- Azure AD identyfikator aplikacji (nazywany również *identyfikatorem aplikacji* lub *identyfikatorem klienta*)

- Azure AD wpis tajny aplikacji (nazywany również *kluczem tajnym klienta*)

- Identyfikator dzierżawy (nazywany również *identyfikatorem katalogu*)

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji w Azure AD, zobacz [Rejestrowanie aplikacji przy użyciu Platforma tożsamości Microsoft](\azure\active-directory\develop\quickstart-register-app).

## <a name="step-2-prepare-a-text-file-with-healthcare-ehr-auditing-data"></a>Krok 2. Przygotowywanie pliku tekstowego z danymi inspekcji EHR opieki zdrowotnej

Następnym krokiem jest utworzenie pliku tekstowego zawierającego informacje o dostępie pracowników do dokumentacji medycznej pacjentów w systemie EHR opieki zdrowotnej w organizacji. Jak wyjaśniono wcześniej, należy określić sposób generowania tego pliku tekstowego z systemu EHR opieki zdrowotnej. Przepływ pracy łącznika opieki zdrowotnej wymaga pliku tekstowego z wartościami rozdzielonymi tabulatorami, aby zamapować te dane w pliku tekstowym przy użyciu wymaganego schematu łącznika. Obsługiwany format pliku to plik tekstowy rozdzielony przecinkami (.csv), potokiem (psv) lub kartą (tsv).

> [!NOTE]
> Maksymalny rozmiar pliku tekstowego zawierającego dane inspekcji wynosi 3 GB. Maksymalna liczba wierszy wynosi 5 milionów. Pamiętaj również, aby uwzględnić tylko odpowiednie dane inspekcji z systemu EHR opieki zdrowotnej.

W poniższej tabeli wymieniono pola wymagane do włączenia scenariuszy zarządzania ryzykiem wewnętrznym. Podzestaw tych pól jest obowiązkowy. Te pola są wyróżnione gwiazdką (*). Jeśli w pliku tekstowym brakuje dowolnego z obowiązkowych pól, plik nie zostanie zweryfikowany, a dane w pliku nie zostaną zaimportowane.

|Pole|Kategoria|
|:----|:----------|
| *Nazwa zdarzenia czasu<br/>* tworzenia<br/>Identyfikator stacji roboczej<br/>Sekcja zdarzenia<br/>Kategoria zdarzenia |Te pola służą do identyfikowania zdarzeń działania dostępu w systemie EHR opieki zdrowotnej.|
| Identyfikator rejestru pacjentów<br/>Nazwisko *pacjenta imię<br/>i nazwisko pacjenta drugie imię <br/>pacjenta* <br/>Adres pacjenta — wiersz 1* <br/>Adres pacjenta — wiersz 2<br/>Miasto pacjentów* <br/>Kod pocztowy pacjenta*  <br/>Stan pacjenta <br/>Kraj pacjenta <br/>Oddział pacjentów              | Te pola służą do identyfikowania informacji o profilu pacjenta.|
| Przyczyna ograniczonego dostępu*<br/> Komentarz dotyczący ograniczonego dostępu | Te pola służą do identyfikowania dostępu do rekordów z ograniczeniami.|
| Adres e-mail (UPN) lub SamAccountName*<br/>Nazwa użytkownika pracownika <br/> Identyfikator pracownika <br/> Nazwisko pracownika <sup>1</sup> <br/> Imię i nazwisko pracownika <sup>1</sup> | Te pola służą do identyfikowania informacji o profilu pracownika na potrzeby dopasowywania adresów i nazw wymaganych do określenia dostępu do rekordów Rodzina/Sąsiad/Pracownik. |
|||

> [!NOTE] 
> <sup>1</sup> To pole może być domyślnie niedostępne w systemie EHR opieki zdrowotnej. Musisz skonfigurować eksport, aby upewnić się, że plik tekstowy zawiera to pole.

## <a name="step-3-create-the-healthcare-connector"></a>Krok 3. Tworzenie łącznika opieki zdrowotnej

Następnym krokiem jest utworzenie łącznika opieki zdrowotnej w portalu zgodności. Po uruchomieniu skryptu w kroku 4 plik tekstowy utworzony w kroku 2 zostanie przetworzony i wypchnięty do punktu końcowego interfejsu API skonfigurowanego w kroku 1. W tym kroku skopiuj identyfikator JobId wygenerowany podczas tworzenia łącznika. Użyjesz identyfikatora JobId podczas uruchamiania skryptu.

1. Przejdź do strony <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Na karcie **Przegląd** kliknij pozycję **Healthcare (wersja zapoznawcza)**.

3. Na stronie **Healthcare (wersja zapoznawcza)** kliknij pozycję **Dodaj łącznik**.

4. Zaakceptuj warunki korzystania z usługi.

5. Na stronie **Poświadczenia uwierzytelniania** wykonaj następujące czynności, a następnie kliknij przycisk **Dalej**:

    1. Wpisz lub wklej identyfikator aplikacji Azure AD dla aplikacji platformy Azure utworzonej w kroku 1.

    2. Wpisz nazwę łącznika opieki zdrowotnej.

6. Na stronie **Metoda mapowania plików** wybierz jedną z następujących opcji, a następnie kliknij przycisk **Dalej**.

   - **Przekaż przykładowy plik**. Jeśli wybierzesz tę opcję, kliknij pozycję **Przekaż przykładowy plik** , aby przekazać plik przygotowany w kroku 2. Ta opcja umożliwia szybkie wybieranie nazw kolumn w pliku tekstowym z listy rozwijanej w celu zamapowania kolumn na wymagany schemat łącznika opieki zdrowotnej. 

    Lub

   - **Ręcznie podaj szczegóły mapowania**. Jeśli wybierzesz tę opcję, musisz wpisać nazwę kolumn w pliku tekstowym, aby zamapować kolumny na wymagany schemat łącznika opieki zdrowotnej.

7. Na stronie **Szczegóły mapowania plików** wykonaj jedną z następujących czynności w zależności od tego, czy w poprzednim kroku przekazano przykładowy plik:

   - Listy rozwijane umożliwiają mapowanie kolumn z pliku przykładowego na każde wymagane pole łącznika opieki zdrowotnej.

    Lub

   - Dla każdego pola wpisz nazwę kolumny z pliku przygotowanego w kroku 2, który odpowiada polu łącznika opieki zdrowotnej.

8. Na stronie **Przegląd** przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

   Zostanie wyświetlona strona stanu, która potwierdza, że łącznik został utworzony. Ta strona zawiera dwie ważne rzeczy, które należy wykonać w następnym kroku, aby uruchomić przykładowy skrypt w celu przekazania danych inspekcji EHR opieki zdrowotnej.

    - **Identyfikator zadania.** Ten identyfikator zadania będzie potrzebny do uruchomienia skryptu w następnym kroku. Możesz skopiować go z tej strony lub ze strony wysuwanej łącznika.

    - **Łącze do przykładowego skryptu.** Kliknij **link tutaj** , aby przejść do witryny GitHub, aby uzyskać dostęp do przykładowego skryptu (link otwiera nowe okno). Pozostaw to okno otwarte, aby można było skopiować skrypt w kroku 4. Alternatywnie możesz dodać zakładkę do miejsca docelowego lub skopiować adres URL, aby uzyskać do niego dostęp ponownie po uruchomieniu skryptu. Ten link jest również dostępny na stronie wysuwanego łącznika.

9. Kliknij pozycję **Gotowe**.

   Nowy łącznik jest wyświetlany na liście na **karcie Łączniki** .

10. Kliknij właśnie utworzony łącznik opieki zdrowotnej, aby wyświetlić stronę wysuwaną zawierającą właściwości i inne informacje o łączniku.

Jeśli jeszcze tego nie zrobiono, możesz skopiować wartości identyfikatora **aplikacja systemu Azure** i **identyfikatora zadania łącznika**. Będą one potrzebne do uruchomienia skryptu w następnym kroku. Możesz również pobrać skrypt ze strony wysuwanej (lub pobrać go przy użyciu linku w następnym kroku).

Możesz również kliknąć pozycję **Edytuj**, aby zmienić identyfikator aplikacja systemu Azure lub nazwy nagłówków kolumn zdefiniowane na stronie **Mapowanie pliku**.

## <a name="step-4-run-the-sample-script-to-upload-your-healthcare-ehr-auditing-data"></a>Krok 4. Uruchamianie przykładowego skryptu w celu przekazania danych inspekcji EHR w służbie zdrowia

Ostatnim krokiem konfigurowania łącznika opieki zdrowotnej jest uruchomienie przykładowego skryptu, który przekaże dane inspekcji EHR opieki zdrowotnej w pliku tekstowym (utworzonym w kroku 1) do chmury firmy Microsoft. W szczególności skrypt przekazuje dane do łącznika opieki zdrowotnej. Po uruchomieniu skryptu łącznik opieki zdrowotnej utworzony w kroku 3 importuje dane inspekcji EHR opieki zdrowotnej do organizacji platformy Microsoft 365, do której można uzyskać dostęp za pomocą innych narzędzi zgodności, takich jak rozwiązanie do zarządzania ryzykiem wewnętrznym. Po uruchomieniu skryptu rozważ zaplanowanie zadania, aby uruchamiać je automatycznie codziennie, aby najbardziej aktualne dane dotyczące kończania pracy pracowników były przekazywane do chmury firmy Microsoft. Zobacz [(Opcjonalnie) Krok 6. Planowanie automatycznego uruchamiania skryptu](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Jak wspomniano wcześniej, maksymalny rozmiar pliku tekstowego zawierającego dane inspekcji wynosi 3 GB. Maksymalna liczba wierszy wynosi 5 milionów. Wykonanie skryptu w tym kroku potrwa od około 30 do 40 minut, aby zaimportować dane inspekcji z dużych plików tekstowych. Ponadto skrypt podzieli duże pliki tekstowe na mniejsze bloki z 100 000 wierszy, a następnie zaimportuje te bloki sekwencyjnie.

1. Przejdź do okna, które zostało otwarte w poprzednim kroku, aby uzyskać dostęp do witryny GitHub przy użyciu przykładowego skryptu. Możesz też otworzyć witrynę z zakładki lub użyć skopiowanego adresu URL. Możesz również uzyskać dostęp do skryptu [tutaj](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Kliknij przycisk **Nieprzetworzone** , aby wyświetlić skrypt w widoku tekstowym.

3. Skopiuj wszystkie wiersze w przykładowym skryptycie, a następnie zapisz je w pliku tekstowym.

4. W razie potrzeby zmodyfikuj przykładowy skrypt dla organizacji.

5. Zapisz plik tekstowy jako plik skryptu Windows PowerShell przy użyciu sufiksu nazwy `.ps1`pliku , na przykład `HealthcareConnector.ps1`.

6. Otwórz wiersz polecenia na komputerze lokalnym i przejdź do katalogu, w którym zapisano skrypt.

7. Uruchom następujące polecenie, aby przekazać dane inspekcji opieki zdrowotnej w pliku tekstowym do chmury firmy Microsoft; na przykład:

   ```powershell
   .\HealthcareConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

W poniższej tabeli opisano parametry do użycia z tym skryptem i ich wymagane wartości. Informacje uzyskane w poprzednich krokach są używane w wartościach tych parametrów.

|Parametr  |Opis|
|:----------|:----------|
|tenantId|Jest to identyfikator organizacji platformy Microsoft 365 uzyskany w kroku 1. Identyfikator dzierżawy organizacji można również uzyskać w bloku **Przegląd** w centrum administracyjnym Azure AD. Służy to do identyfikowania organizacji.|
|Appid|Jest to identyfikator aplikacji Azure AD dla aplikacji utworzonej w Azure AD w kroku 1. Jest to używane przez Azure AD do uwierzytelniania, gdy skrypt próbuje uzyskać dostęp do organizacji platformy Microsoft 365.|
|appSecret|Jest to Azure AD wpis tajny aplikacji dla aplikacji utworzonej w Azure AD w kroku 1. Jest to również używane do uwierzytelniania.|
|Jobid|Jest to identyfikator zadania łącznika opieki zdrowotnej utworzony w kroku 3. Służy to do kojarzenia danych inspekcji EHR opieki zdrowotnej, które są przekazywane do chmury firmy Microsoft za pomocą łącznika healthcare.|
|Filepath|Jest to ścieżka pliku tekstowego (przechowywana w tym samym systemie co skrypt) utworzona w kroku 2. Staraj się unikać spacji w ścieżce pliku; W przeciwnym razie użyj pojedynczych cudzysłowów.|
|||

Oto przykład składni skryptu łącznika opieki zdrowotnej z użyciem rzeczywistych wartości dla każdego parametru:

```powershell
.\HealthcareConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\healthcare_audit_records.csv'
```

Jeśli przekazywanie zakończy się pomyślnie, skrypt wyświetli komunikat **Przekaż pomyślnie** .

> [!NOTE]
> Jeśli masz problemy z uruchomieniem poprzedniego polecenia z powodu zasad wykonywania, zobacz [Informacje o zasadach wykonywania](/powershell/module/microsoft.powershell.core/about/about_execution_policies) i [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) , aby uzyskać wskazówki dotyczące ustawiania zasad wykonywania.

## <a name="step-5-monitor-the-healthcare-connector"></a>Krok 5. Monitorowanie łącznika opieki zdrowotnej

Po utworzeniu łącznika opieki zdrowotnej i wypchnięciu danych inspekcji EHR możesz wyświetlić łącznik i przekazać stan w portalu zgodności. Jeśli planujesz regularne uruchamianie skryptu automatycznie, możesz również wyświetlić bieżący stan po ostatnim uruchomieniu skryptu.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz łącznik Opieki zdrowotnej, aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Ostatni import** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o każdym uruchomieniu skryptu i przekazaniu danych z pliku tekstowego do chmury firmy Microsoft.

    Pole `RecordsSaved` wskazuje liczbę wierszy w przekazanym pliku tekstowym. Jeśli na przykład plik tekstowy zawiera cztery wiersze, wartość `RecordsSaved` pól wynosi 4, jeśli skrypt pomyślnie przekazał wszystkie wiersze w pliku tekstowym.

Jeśli skrypt nie został uruchomiony w kroku 4, w obszarze **Ostatni import** zostanie wyświetlony link umożliwiający pobranie skryptu. Możesz pobrać skrypt, a następnie wykonać kroki, aby uruchomić skrypt.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Opcjonalnie) Krok 6. Planowanie automatycznego uruchamiania skryptu

Aby upewnić się, że najnowsze dane inspekcji z systemu EHR opieki zdrowotnej są dostępne dla narzędzi takich jak rozwiązanie do zarządzania ryzykiem wewnętrznym, zalecamy zaplanowanie automatycznego uruchamiania skryptu na co dzień. Wymaga to również zaktualizowania danych inspekcji EHR w tym samym pliku tekstowym zgodnie z podobnym harmonogramem (jeśli nie tym samym), tak aby zawierała najnowsze informacje o działaniach związanych z dostępem do rekordów pacjentów przez pracowników. Celem jest przekazanie najnowszych danych inspekcji, aby łącznik opieki zdrowotnej mógł udostępnić je rozwiązaniu do zarządzania ryzykiem wewnętrznym.

Aplikacja Harmonogram zadań w systemie Windows umożliwia automatyczne uruchamianie skryptu każdego dnia.

1. Na komputerze lokalnym kliknij przycisk **Start** systemu Windows, a następnie wpisz **Harmonogram zadań**.

2. Kliknij aplikację **Harmonogram zadań** , aby ją otworzyć.

3. W sekcji **Akcje** kliknij pozycję **Utwórz zadanie**.

4. Na karcie **Ogólne** wpisz opisową nazwę zaplanowanego zadania; na przykład **skrypt łącznika opieki zdrowotnej**. Możesz również dodać opcjonalny opis.

5. W obszarze **Opcje zabezpieczeń** wykonaj następujące czynności:

    1. Określ, czy skrypt ma być uruchamiany tylko wtedy, gdy użytkownik jest zalogowany na komputerze, czy uruchamiany po zalogowaniu.

    2. Upewnij się, że zaznaczono pole wyboru **Uruchom z najwyższymi uprawnieniami** .

6. Wybierz kartę **Wyzwalacze** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

    1. W obszarze **Ustawienia** wybierz opcję **Codziennie** , a następnie wybierz datę i godzinę, aby uruchomić skrypt po raz pierwszy. Skrypt będzie uruchamiany codziennie o tej samej określonej godzinie.

    2. W obszarze **Ustawienia zaawansowane** upewnij się, że **zaznaczono** pole wyboru Włączone.

    3. Kliknij przycisk **OK**.

7. Wybierz kartę **Akcje** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

   ![Ustawienia akcji umożliwiające utworzenie nowego zaplanowanego zadania dla skryptu łącznika opieki zdrowotnej.](../media/GenericHealthCareConnectorScheduleTask1.png)

    1. Na liście rozwijanej **Akcja** upewnij się, że **wybrano pozycję Uruchom program** .

    2. W polu **Program/skrypt** kliknij pozycję **Przeglądaj**, a następnie przejdź do następującej lokalizacji i wybierz ją, aby ścieżka była wyświetlana w polu: C:.0.exe.

    3. W polu **Dodawanie argumentów (opcjonalnie)** wklej to samo polecenie skryptu, które zostało uruchomione w kroku 4. Na przykład `.\HealthcareConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Healthcare\audit\records.txt"`

    4. W polu **Start in (opcjonalnie) wklej** lokalizację folderu skryptu uruchomionego w kroku 4. Na przykład C:\Healthcare\audit.

    5. Kliknij **przycisk OK** , aby zapisać ustawienia nowej akcji.

8. W oknie **Tworzenie zadania** kliknij przycisk **OK** , aby zapisać zaplanowane zadanie. Może zostać wyświetlony monit o wprowadzenie poświadczeń konta użytkownika.

   Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.

   ![Nowe zadanie dla skryptu łącznika opieki zdrowotnej jest wyświetlane w bibliotece harmonogramu zadań.](../media/HealthcareConnectorTaskSchedulerLibrary.png)

   Zostanie wyświetlony czas ostatniego uruchomienia skryptu i następnego zaplanowanego uruchomienia. Możesz kliknąć dwukrotnie zadanie, aby je edytować.

   Możesz również sprawdzić czas ostatniego uruchomienia skryptu na stronie wysuwanej odpowiedniego łącznika opieki zdrowotnej w Centrum zgodności.
