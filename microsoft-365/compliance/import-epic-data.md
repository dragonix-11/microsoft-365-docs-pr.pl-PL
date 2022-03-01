---
title: Konfigurowanie łącznika w celu importowania danych EHR
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
description: Administratorzy mogą skonfigurować łącznik danych w celu importowania danych elektronicznej dokumentacji zdrowia (EHR) z systemu Nas w organizacji, aby Microsoft 365. Dzięki temu można korzystać z danych EHR w zasadach zarządzania ryzykiem w niejawnym programie testów w celu wykrywania nieautoryzowanego dostępu do danych pacjentów przez pracowników.
ms.openlocfilehash: 0da7386aa2b230492fedd5fdac5477d204aa63a8
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009810"
---
# <a name="set-up-a-connector-to-import-epic-ehr-audit-data-preview"></a>Konfigurowanie łącznika w celu importowania danych inspekcji EHR (wersja zapoznawcza)

Możesz skonfigurować łącznik danych w aplikacji usługi Centrum zgodności platformy Microsoft 365 do importowania rekordów inspekcji aktywności użytkowników w systemie do obsługi elektronicznej opieki zdrowotnej (EHR, Electronic Healthcare Records) organizacji. Rekordy inspekcji z systemu EHR obejmują dane dotyczące zdarzeń związanych z uzyskiwaniem dostępu do dokumentacji zdrowia pacjenta. Za pomocą rozwiązania do zarządzania ryzykiem w niejawnym programie testów firmy [](insider-risk-management.md) Microsoft 365 organizacja może chronić Twoją organizację przed nieautoryzowanym dostępem do informacji o pacjentach.

Konfigurowanie łącznika Nasadka składa się z następujących zadań:

- Tworzenie aplikacji w usłudze Azure Active Directory (Azure AD) w celu uzyskania dostępu do punktu końcowego interfejsu API, który akceptuje plik tekstowy rozdzielany tabulatorami zawierający rekordy inspekcji EHR.

- Tworzenie pliku tekstowego ze wszystkimi wymaganymi polami zgodnie ze zdefiniowanymi w schemacie łącznika.

- Creating an Hero connector instance in the Centrum zgodności platformy Microsoft 365.

- Uruchamianie skryptu w celu wypychania rekordów inspekcji EHR do punktu końcowego interfejsu API.

- Opcjonalnie możesz zaplanować automatyczne uruchamianie skryptu w celu zaimportowania rekordów inspekcji.

## <a name="before-you-set-up-the-connector"></a>Przed skonfigurowaniem łącznika

- Użytkownik, który tworzy łącznik Na przykład w kroku 3, musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć nową grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Należy określić, jak codziennie pobierać i eksportować dane z systemu Jego organizacji Jego czas przechowywania oraz jak utworzyć plik tekstowy opisany w kroku 2. Skrypt uruchomiony w kroku 4 wypchnie dane z pliku tekstowego do punktu końcowego interfejsu API.

- Przykładowy skrypt uruchomiony w kroku 4 wypycha rekordy inspekcji EHR z pliku tekstowego do interfejsu API łącznika, dzięki czemu może być używany przez rozwiązanie do zarządzania ryzykiem niejawnego programu testów. Ten przykładowy skrypt nie jest obsługiwany w żadnym standardowym programie lub usłudze pomocy technicznej firmy Microsoft. Przykładowy skrypt jest dostarczany W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowego skryptu i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w aplikacji Azure Active Directory

Pierwszym krokiem jest utworzenie i zarejestrowanie nowej aplikacji w usłudze Azure Active Directory (Azure AD). Aplikacja będzie odpowiadać łącznikowi Grymu, który został utworzyć w kroku 3. Utworzenie tej aplikacji umożliwia usłudze Azure AD uwierzytelnienie żądania wypychanego dla pliku tekstowego zawierającego rekordy inspekcji EHR. Podczas tworzenia tej aplikacji Azure AD pamiętaj o zapisaniu poniższych informacji. Te wartości zostaną użyte w kolejnych krokach.

- Identyfikator aplikacji usługi Azure AD (nazywany również *identyfikatorem aplikacji* lub *identyfikatorem klienta*)

- Klucz tajny aplikacji usługi Azure AD (nazywany także *kluczem tajnym klienta*)

- Identyfikator dzierżawy (nazywany również *identyfikatorem katalogu*)

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji w usłudze Azure AD, zobacz [Rejestrowanie](\azure\active-directory\develop\quickstart-register-app) aplikacji w Platforma tożsamości Microsoft.

## <a name="step-2-prepare-a-text-file-with-epic-ehr-audit-records"></a>Krok 2. Przygotowanie pliku tekstowego za pomocą rekordów inspekcji EHR

Następnym krokiem jest utworzenie pliku tekstowego zawierającego informacje o dostępie pracowników do dokumentacji zdrowia pacjentów w systemie EHR twojej organizacji. Jak wyjaśniono wcześniej, należy ustalić, jak wygenerować ten plik tekstowy na podstawie systemu Jego EHR. Przepływ pracy Łącznik na karcie wymaga pliku tekstowego z wartościami rozdzielanych tabulatorami do zamapowanie danych w pliku tekstowym na wymagany schemat łącznika. Obsługiwanym formatem pliku jest plik rozdzielany .txt pipetą lub .txt pliku.

> [!NOTE]
> Maksymalny rozmiar pliku tekstowego zawierającego dane inspekcji to 3 GB. Maksymalna liczba wierszy wynosi 5 milionów. Ponadto pamiętaj, aby uwzględnić tylko odpowiednie dane inspekcji z systemu EHR opieki zdrowotnej.

W poniższej tabeli wymieniono pola wymagane do włączenia scenariuszy zarządzania ryzykiem w niejawnym programie testów. Podzestaw tych pól jest obowiązkowy. Te pola są wyróżnione gwiazdką (*). Jeśli w pliku tekstowym brakuje dowolnego z obowiązkowych pól, nie zostanie sprawdzona poprawność pliku i dane w pliku nie zostaną zaimportowane.

|Pole|Kategoria|
|:----|:----------|
| ACCESS_LOG. *<br/>ACCESS_TIME ACCESS_LOG_METRIC. METRIC_NAME*<br/>ACCESS_LOG. WORKSTATION_ID<br/>ZCMETRIC\_\_ GROUP.NAME<br/>ZCACCESS\_\_ ACTION.NAME |Te pola służą do identyfikowania zdarzeń działań dostępu w systemie Poczty EHR.|
| PATIENT. PAT_MRN_ID<br/>PATIENT. PAT_FIRST_NAME* <br/>PATIENT. PAT_MIDDLE_NAME <br/>PATIENT. PAT_LAST_NAME* <br/>PATIENT. ADD_LINE_1* <br/>PATIENT. ADD_LINE_2  <br/>PATIENT. MIASTO* <br/>PATIENT.ZIP*  <br/>ZC_STATE.NAME <br/>ZC_COUNTRY.NAME <br/>CLARITY_DEP. DEPARTMENT_NAME              | Te pola służą do identyfikowania informacji o profilu pacjenta.|
| ZC_BTG_REASON.NAME*<br/> PAT_BTG_AUDIT. BTG_EXPLANATION | Te pola służą do identyfikowania dostępu do rekordów z ograniczeniami.|
| EMP. SYSTEM_LOGIN*<br/>CLARITY_EMP. USER_ID <br/> employee_last_name <sup>1</sup> <br/> employee_first_name <sup>1</sup>                | Te pola służą do identyfikowania informacji o profilu pracownika pod adresem i dopasowywaniem nazwisk wymaganych do określenia dostępu do rekordów Rodzina/Sąsiad/Pracownik. |
|||

> [!NOTE]
> Upewnij się, że eksportujesz tylko odpowiednie metryki dziennika z tego systemu. 
> <sup>1</sup> To pole nie jest domyślnie dostępne w programie Na wschowa. Musisz skonfigurować eksportowanie, aby mieć pewność, że plik tekstowy zawiera to pole.

## <a name="step-3-create-the-epic-connector"></a>Krok 3. Tworzenie łącznika Nasadka

Następnym krokiem jest utworzenie łącznika Na przykład w Centrum zgodności platformy Microsoft 365. Po uruchomieniu skryptu w kroku 4 plik tekstowy utworzony w kroku 2 zostanie przetworzony i wypychany do punktu końcowego interfejsu API ustawionego w kroku 1. W tym kroku pamiętaj o skopiowaniu dokumentu JobId wygenerowanego podczas tworzenia łącznika. Po uruchomieniu skryptu użyjesz polecenia JobId.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki danych** w lewym okienku narracji.

2. Na stronie **Łączniki danych** w obszarze **Łącznik na przykład** kliknij pozycję **Widok**.

3. Na stronie **Łącznik na przykład** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Konfigurowanie połączenia** wykonaj następujące czynności, a następnie kliknij przycisk **Dalej**:

    1. Wpisz lub wklej identyfikator aplikacji usługi Azure AD dla aplikacji azure utworzonej w kroku 2.

    2. Wpisz nazwę łącznika Najbłędsza.

5. Na stronie **Recenzja** przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

   Zostanie wyświetlona strona stanu z potwierdzeniem utworzenia łącznika. Na tej stronie zajmą się dwie ważne czynności, które należy wykonać w celu uruchomienia przykładowego skryptu w celu przekazania danych rekordów inspekcji EHR.

    Strona Recenzja z identyfikatorem zadania i linkiem do witryny github na przykładowy skrypt

    1. **Identyfikator zadania.** Ten identyfikator zadania będzie potrzebny do uruchomienia skryptu w następnym kroku. Możesz skopiować ją z tej strony lub ze strony wysuwu łącznika.

    2. **Schemat referencyjny.** Skorzystaj ze schematu, aby dowiedzieć się, które pola ze swojego systemu Nas są akceptowane przez łącznik. Dzięki temu można utworzyć plik ze wszystkimi wymaganymi polami bazy danych Firmy Dane.

    3. **Link do przykładowego skryptu.** Kliknij link **tutaj**, aby przejść do witryny GitHub w celu uzyskania dostępu do przykładowego skryptu (link otworzy nowe okno). Zachowaj to okno otwarte, aby można było skopiować skrypt w kroku 4. Alternatywnie możesz dodać zakładkę do miejsca docelowego lub skopiować adres URL, aby ponownie uzyskać do niego dostęp po uruchomieniu skryptu. Ten link jest również dostępny na wysuwana strona łącznika.

6. Kliknij **przycisk Gotowe**.

   Nowy łącznik zostanie wyświetlony na liście na karcie **Łączniki** .

7. Kliknij właśnie utworzony łącznik Nasadka, aby wyświetlić stronę wysuwu zawierającą właściwości i inne informacje o łączniku.

Jeśli jeszcze tego nie zrobiono, możesz skopiować wartości identyfikatorów aplikacji **Azure** i **identyfikatora zadania łącznika**. Będą one potrzebne do uruchomienia skryptu w następnym kroku. Skrypt można również pobrać ze strony wysuwu (lub za pomocą linku w następnym kroku).

Możesz również kliknąć pozycję **Edytuj,** aby zmienić identyfikator aplikacji Azure lub nazwy nagłówków kolumn zdefiniowane na **stronie Mapowanie** plików.

## <a name="step-4-run-the-sample-script-to-upload-your-epic-ehr-audit-records"></a>Krok 4. Uruchamianie przykładowego skryptu w celu przekazania rekordów inspekcji EHR

Ostatnim krokiem podczas konfigurowania łącznika Na przykład jest uruchomienie przykładowego skryptu, który przekaże dane inspekcji Tej usługi w pliku tekstowym (utworzonym w kroku 1) do chmury firmy Microsoft. W szczególności skrypt przekaże dane do łącznika Na przykład. Po uruchomieniu skryptu łącznik Czas utworzony w kroku 3 zaim importuje dane inspekcji Dns EHR do Organizacji programu Microsoft 365, gdzie można uzyskać do niego dostęp za pomocą innych narzędzi do zgodności, takich jak rozwiązanie do zarządzania ryzykiem w ramach niejawnego programu testów. Po uruchomieniu skryptu rozważ zaplanowanie zadania tak, aby było uruchamiane automatycznie codziennie, aby najnowsze dane o zakończeniu pracy pracownika były przekazywane do chmury firmy Microsoft. Zobacz [(Opcjonalnie) Krok 6. Planowanie automatycznego uruchamiania skryptu](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Jak wspomniano wcześniej, maksymalny rozmiar pliku tekstowego zawierającego dane inspekcji wynosi 3 GB. Maksymalna liczba wierszy wynosi 5 milionów. Uruchomienie skryptu w tym kroku potrwa około 30 do 40 minut w celu zaimportowania danych inspekcji z dużych plików tekstowych. Ponadto skrypt podzieli duże pliki tekstowe na mniejsze bloki po 100 000 wierszy, a następnie zaimportuje te bloki kolejno.

1. Przejdź do okna otwartego z poprzedniego kroku, aby uzyskać dostęp do witryny GitHub za pomocą przykładowego skryptu. Ewentualnie otwórz witrynę z zakładką lub użyj skopiowanego adresu URL. Możesz również uzyskać dostęp do skryptu [tutaj](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Kliknij przycisk **Nieprzetworzone** , aby wyświetlić skrypt w widoku tekstu.

3. Skopiuj wszystkie wiersze w przykładowym skrypcie, a następnie zapisz je w pliku tekstowym.

4. W razie potrzeby zmodyfikuj przykładowy skrypt dla organizacji.

5. Zapisz plik tekstowy jako plik Windows PowerShell skryptu, używając sufiksu nazwy `.ps1`pliku , na przykład `EpicConnector.ps1`.

6. Otwórz wiersz polecenia na komputerze lokalnym i przejdź do katalogu, w którym został zapisany skrypt.

7. Uruchom następujące polecenie, aby przekazać dane inspekcji na pliku tekstowym do chmury firmy Microsoft. na przykład:

   ```powershell
   .\EpicConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

W poniższej tabeli opisano parametry, których należy użyć w tym skrypcie, oraz ich wymagane wartości. Informacje uzyskane w poprzednich krokach są używane w wartościach tych parametrów.

|Parametr  |Opis|
|:----------|:----------|
|tenantId|Jest to identyfikator organizacji, Microsoft 365 uzyskany w kroku 1. Możesz również uzyskać identyfikator dzierżawy organizacji na stronie **Omówienie** w centrum administracyjnym usługi Azure AD. Służy on do identyfikowania Twojej organizacji.|
|appId|Jest to identyfikator aplikacji usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 1. Jest to używane przez usługę Azure AD do uwierzytelniania, gdy skrypt próbuje uzyskać dostęp do Twojej Microsoft 365 organizacji.|
|appSecret|Jest to tajny kod aplikacji usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 1. Ta metoda jest również używana do uwierzytelniania.|
|jobId|Jest to identyfikator zadania łącznika Na przykład utworzony w kroku 3. Służy to do kojarzenia rekordów inspekcji EHR, które są przekazywane do chmury firmy Microsoft, z łącznikiem Tym.|
|filePath|Jest to ścieżka do pliku tekstowego (przechowywanego w tym samym systemie co skrypt) utworzonego w kroku 2. Postaraj się uniknąć spacji w ścieżce pliku. w przeciwnym razie należy użyć cudzysłowów pojedynczych.|
|||

Poniżej podano przykład składni skryptu łącznika Teraz, używając rzeczywistych wartości dla każdego parametru:

```powershell
.\EpicConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\epic_audit_records.txt'
```

Jeśli przekazywanie się powiedzie, skrypt wyświetli komunikat o **błędzie Upload pomyślny**.

> [!NOTE]
> Jeśli masz problemy z uruchamianiem poprzedniego polecenia z powodu zasad wykonywania, zobacz [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) Informacje o zasadach wykonywania i Ustawianie [zasad](/powershell/module/microsoft.powershell.security/set-executionpolicy) wykonywania, aby uzyskać wskazówki dotyczące ustawiania zasad wykonywania.

## <a name="step-5-monitor-the-epic-connector"></a>Krok 5. Monitorowanie łącznika Nasadka

Po utworzeniu łącznika Nagło i wypchnieniu rekordów inspekcji EHR można wyświetlać łącznik i stan przekazywania w Centrum zgodności platformy Microsoft 365. Jeśli skrypt ma być uruchamiany automatycznie regularnie, można także wyświetlić bieżący stan po ostatnim uruchomieniu skryptu.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik Nasadka, aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Ostatni import** **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o każdym uruchamianiu skryptu i przekazywaniu danych z pliku tekstowego do chmury firmy Microsoft.

    Plik dziennika łączników zawiera liczby wierszy z przekazanego pliku tekstowego

    Pole `RecordsSaved` wskazuje liczbę wierszy w przekazanym pliku tekstowym. Jeśli na przykład plik tekstowy zawiera cztery wiersze, `RecordsSaved` wartość pól wynosi 4, jeśli skrypt pomyślnie przesłał wszystkie wiersze w pliku tekstowym.

Jeśli nie został uruchomiony skrypt w kroku 4, w obszarze Ostatni import jest wyświetlany link do pobierania **skryptu**. Możesz pobrać skrypt, a następnie wykonać te instrukcje, aby go uruchomić.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Opcjonalnie) Krok 6. Planowanie automatycznego uruchamiania skryptu

Aby upewnić się, że najnowsze rekordy inspekcji z systemu Firmy Tester EHR są dostępne dla narzędzi, takich jak rozwiązanie do zarządzania ryzykiem w ramach niejawnego programu testów, zalecamy codzienne uruchamianie skryptu. Wymaga to również zaktualizowania danych inspekcji tego samego pliku tekstowego zgodnie z podobnym (jeśli nie tym samym) harmonogramem, tak aby zawierała najnowsze informacje na temat działań pacjentów, które są dostępne dla Twoich pracowników. Celem jest przekazanie najbardziej aktualnych rekordów inspekcji, tak aby łącznik Też udostępnił je w rozwiązaniu do zarządzania ryzykiem w niejawnym programie testów. 

Za pomocą aplikacji Harmonogram zadań w programie Windows uruchamiać skrypt automatycznie każdego dnia.

1. Na komputerze lokalnym kliknij przycisk Windows **Start**, a następnie wpisz **Harmonogram zadań**.

2. Kliknij aplikację **Harmonogram zadań** , aby ją otworzyć.

3. W sekcji **Akcje** kliknij pozycję **Utwórz zadanie**.

4. Na **karcie** Ogólne wpisz opisową nazwę zaplanowanego zadania. Na przykład skrypt **łącznika Nasadka**. Możesz również dodać opcjonalny opis.

5. W **obszarze Opcje zabezpieczeń** wykonaj następujące czynności:

    1. Określ, czy skrypt ma być uruchamiany tylko po zalogowaniu się na komputerze, czy po zalogowaniu się.

    2. Upewnij się, że **jest zaznaczone pole** wyboru Uruchom z najwyższymi uprawnieniami.

6. Wybierz **kartę Wyzwalacze** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

    1. W **Ustawienia** **kliknij opcję Dzienny**, a następnie wybierz datę i czas do uruchomienia skryptu po raz pierwszy. Skrypt będzie uruchamiany każdego dnia o tej samej określonej godzinie.

    2. Upewnij **się, że** w obszarze Ustawienia zaawansowane jest **zaznaczone** pole wyboru Włączone.

    3. Kliknij **przycisk OK**.

7. Wybierz **kartę Akcje** , kliknij **pozycję Nowy**, a następnie wykonaj następujące czynności:

   ![Ustawienia akcji w celu utworzenia nowego zaplanowanego zadania dla skryptu tego łącznika.](../media/EpicConnectorScheduleTask1.png)

    1. Na liście **rozwijanej** Akcja upewnij się, że jest **wybrana opcja Uruchom** program.

    2. W **polu Program/skrypt** kliknij przycisk **Przeglądaj, przejdź** do następującej lokalizacji i wybierz ją, aby ścieżka była wyświetlana w polu: C:.0.exe.

    3. W **polu Dodaj argumenty (opcjonalnie)** wklej to samo polecenie skryptu, które było uruchomiono w kroku 4. Na przykład `.\EpicConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Epic\audit\records.txt"`

    4. W polu **Rozpocznij w (opcjonalnie)** wklej lokalizację folderu skryptu, który został uruchomiony w kroku 4. Na przykład C:\Pochłoń\inspekcja.

    5. Kliknij **przycisk OK** , aby zapisać ustawienia nowej akcji.

8. W **oknie Tworzenie** zadania kliknij przycisk **OK** , aby zapisać zaplanowane zadanie. Może zostać wyświetlony monit o wprowadzenie poświadczeń konta użytkownika.

   Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.

   ![Nowe zadanie dla skryptu łącznika opieki zdrowotnej jest wyświetlane w bibliotece harmonogramu zadań.](../media/EpicConnectorTaskSchedulerLibrary.png)

   Zostanie wyświetlony czas ostatniego uruchomienia skryptu i następnego uruchomienia tego skryptu. Możesz kliknąć dwukrotnie zadanie, aby je edytować.

   Możesz także sprawdzić czas ostatniego uruchamiania skryptu na stronie wysuwanych odpowiedniego łącznika Teraz w centrum zgodności.
