---
title: Konfigurowanie łącznika w celu importowania danych kadrowych do chmury amerykańskiej instytucji rządowych
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
ROBOTS: NOINDEX, NOFOLLOW
description: Administratorzy w chmurze dla instytucji rządowych Stanów Zjednoczonych mogą skonfigurować łącznik danych w celu importowania danych pracowników z systemu kadr w organizacji do Microsoft 365. Dzięki temu możesz używać danych kadrowych w zasadach zarządzania ryzykiem w niejawnym programie testów w celu wykrywania działań określonych użytkowników, które mogą stanowić zagrożenie wewnętrzne dla Organizacji.
ms.openlocfilehash: abfe43d1f0b61952c2dbc0f603250723965953a1
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009698"
---
# <a name="set-up-a-connector-to-import-hr-data-in-us-government"></a>Konfigurowanie łącznika w celu importowania danych kadrowych w administracji Stanów Zjednoczonych

Możesz skonfigurować łącznik danych w centrum danych Centrum zgodności platformy Microsoft 365 do importowania danych kadrowych do organizacji rządowej Stanów Zjednoczonych. Dane związane z kadrami obejmują datę przesłaną przez pracownika swoją rezygnację oraz datę ostatniego dnia tego pracownika. Te dane kadrowe mogą być następnie używane przez rozwiązania ochrona informacji firmy Microsoft, takie jak rozwiązanie do zarządzania ryzykiem w niejawnym programie testów[, aby](insider-risk-management.md) chronić organizację przed złośliwymi działaniami i kradzieżą danych w organizacji. Konfigurowanie łącznika kadr polega na utworzeniu aplikacji w programie Azure Active Directory używanej do uwierzytelniania za pomocą łącznika, utworzeniu plików mapowania PLIKÓW CSV z danymi HR, utworzeniu łącznika danych w centrum zgodności, a następnie uruchomieniu (według harmonogramu) skryptu służącego do pobierania danych hr z pliku CSV do chmury firmy Microsoft. Łącznik danych jest następnie używany przez narzędzie do zarządzania ryzykiem w niejawnym programie testów w celu uzyskania dostępu do danych kadrowych, które zaimportowano do Twojej organizacji Microsoft 365 Rząd Stanów Zjednoczonych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Użytkownik, który tworzy łącznik kadr w kroku 3, musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć nową grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Musisz określić, jak pobierać i eksportować dane z systemu kadr organizacji (regularnie) i dodawać je do pliku CSV zgodnie z opisem w kroku 2. Skrypt uruchomiony w kroku 4 spowoduje przekazanie danych hr z pliku CSV do chmury firmy Microsoft.

- Przykładowy skrypt uruchomiony w kroku 4 spowoduje przekazanie danych kadrowych do chmury firmy Microsoft, aby można ich było używać w innych narzędziach firmy Microsoft, takich jak rozwiązanie do zarządzania ryzykiem w niejawnym programie testów. Ten przykładowy skrypt nie jest obsługiwany w żadnym standardowym programie lub usłudze pomocy technicznej firmy Microsoft. Przykładowy skrypt jest dostarczany W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowego skryptu i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w aplikacji Azure Active Directory

Pierwszym krokiem jest utworzenie i zarejestrowanie nowej aplikacji w usłudze Azure Active Directory (Azure AD). Aplikacja będzie odpowiadać łącznikowi hr, który został utworzyć w kroku 3. Utworzenie tej aplikacji umożliwi usłudze Azure AD uwierzytelnienie łącznika kadr podczas jego uruchamiania i próby uzyskania dostępu do organizacji. Ta aplikacja będzie również używana do uwierzytelniania skryptu uruchomionego w kroku 4 w celu przekazania danych HR do chmury firmy Microsoft. Podczas tworzenia tej aplikacji Azure AD pamiętaj o zapisaniu poniższych informacji. Te wartości zostaną użyte w kolejnych krokach.

- Identyfikator aplikacji usługi Azure AD (nazywany również *identyfikatorem aplikacji* lub *identyfikatorem klienta*)

- Klucz tajny aplikacji usługi Azure AD (nazywany także *kluczem tajnym klienta*)

- Identyfikator dzierżawy (nazywany również *identyfikatorem katalogu*)

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji w usłudze Azure AD, zobacz [Rejestrowanie](/azure/active-directory/develop/quickstart-register-app) aplikacji w Platforma tożsamości Microsoft.

## <a name="step-2-prepare-a-csv-file-with-your-hr-data"></a>Krok 2. Przygotowanie pliku CSV z danymi hr

Następnym krokiem jest utworzenie pliku CSV zawierającego informacje o pracownikach, którzy odeszli z organizacji. Zgodnie z wyjaśnieniami w sekcji Przed rozpoczęciem musisz określić, jak wygenerować ten plik CSV z systemu kadr organizacji. W poniższym przykładzie pokazano ukończony plik CSV (otwarty w notatniku) zawierający trzy wymagane parametry (kolumny). Znacznie łatwiej jest edytować plik CSV w programie Microsoft Excel.

```text
EmailAddress,TerminationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

Pierwszy wiersz w pliku CSV, czyli wiersz nagłówka, zawiera listę wymaganych nazw kolumn. Nazwa używana w każdym nagłówku kolumny należy do Ciebie (nazwy z poprzedniego przykładu to sugestie). Jednak te same nazwy kolumn, których używasz w pliku *CSV, muszą* zostać określone podczas tworzenia łącznika kadr w kroku 3. Nie dołączaj spacji w nazwach kolumn.

W poniższej tabeli opisano każdą kolumnę w pliku CSV:

| Nazwa kolumny | Opis |
|:-----|:-----|
| **EmailAddress (Adres e-mail)** <br/> |Określa adres e-mail zakończonego pracownika.|
| **TerminationDate** <br/> |Określa datę oficjalnego zakończenia stosunku pracy danej osoby w organizacji. Może to być na przykład data, kiedy pracownik przekazał mu powiadomienie o odejściu z organizacji. Ta data może być inna niż data ostatniego dnia pracy danej osoby. Użyj następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest formatem [daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|**LastWorkingDate**|Określa ostatni dzień pracy dla zakończonego pracownika. Użyj następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest formatem [daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

Po utworzeniu pliku CSV z wymaganymi danymi HR przechowuj go w tym samym systemie co skrypt uruchomiony w kroku 4. Pamiętaj o wdrożeniu strategii aktualizacji, aby plik CSV zawsze zawierał najnowsze informacje. Dzięki temu będziesz mieć pewność, że skrypt zostanie uruchomiony, do chmury firmy Microsoft będą przekazywane najnowsze dane o zakończeniu pracy pracowników.

## <a name="step-3-create-the-hr-connector"></a>Krok 3. Tworzenie łącznika kadr

Następnym krokiem jest utworzenie łącznika kadr w Centrum zgodności platformy Microsoft 365. Po uruchomieniu skryptu w kroku 4 zostanie uruchomiony łącznik hr, który utworzysz, aby dane dotyczące kadr z pliku CSV trafiły do Twojej Microsoft 365 organizacji. W tym kroku pamiętaj o skopiowaniu identyfikatora zadania generowanego podczas tworzenia łącznika. Identyfikator zadania zostanie uruchomiony podczas uruchamiania skryptu.

1. Przejdź do strony Centrum zgodności platformy Microsoft 365 i wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**stronę Łączniki** danych</a>.

2. Na stronie **Łączniki danych** w obszarze **Kadry** kliknij pozycję **Widok**.

3. Na stronie **Kadry** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Poświadczenia uwierzytelniania** wykonaj następujące czynności, a następnie kliknij przycisk **Dalej**:

   1. Wpisz lub wklej identyfikator aplikacji usługi Azure AD dla aplikacji Azure utworzonej w kroku 1.

   1. Wpisz nazwę łącznika kadr.

5. Na stronie **Mapowanie** plików wpisz nazwy trzech nagłówków kolumn (nazywanych również parametrami *) z* pliku CSV utworzonego w kroku 2 w każdym z odpowiednich pól. W nazwach nie jestróżniana wielkość liter. Jak wyjaśniono wcześniej, nazwy wpisywania w tych polach muszą być zgodne z nazwami parametrów w pliku CSV. Na przykład poniższy zrzut ekranu przedstawia nazwy parametrów z przykładu w przykładowym pliku CSV pokazanym w kroku 2.

   ![Nazwy nagłówków kolumn są zgodne z nazwami w pliku CSV.](../media/HRConnectorWizard3.png)

6. Na stronie **Recenzja** przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

   Zostanie wyświetlona strona stanu z potwierdzeniem utworzenia łącznika. Ta strona zawiera dwie ważne czynności, które należy wykonać w następnym kroku w celu uruchomienia przykładowego skryptu w celu przekazania danych HR.

   ![Strona Recenzja z identyfikatorem zadania i linkiem do witryny github na przykładowy skrypt.](../media/HRConnector_Confirmation.png)

   1. **Identyfikator zadania.** Ten identyfikator zadania będzie potrzebny do uruchomienia skryptu w następnym kroku. Możesz skopiować ją z tej strony lub ze strony wysuwu łącznika.
   
   1. **Link do przykładowego skryptu.** Kliknij link **tutaj**, aby przejść do witryny GitHub w celu uzyskania dostępu do przykładowego skryptu (link otworzy nowe okno). Zachowaj to okno otwarte, aby można było skopiować skrypt w kroku 4. Możesz również dodać zakładkę do miejsca docelowego lub skopiować adres URL, aby ponownie uzyskać do niego dostęp w kroku 4. Ten link jest również dostępny na wysuwana strona łącznika.

7. Kliknij **przycisk Gotowe**.

   Nowy łącznik zostanie wyświetlony na liście na karcie **Łączniki** . 

8. Kliknij właśnie utworzony łącznik kadrowy, aby wyświetlić stronę wysuwu zawierającą właściwości i inne informacje o łączniku.

   ![Wysuuwana strona nowego łącznika KADR.](../media/HRConnectorWizard7.png)

   Jeśli jeszcze tego nie zrobiono, możesz skopiować wartości identyfikatorów aplikacji **Azure** i **identyfikatora zadania łącznika**. Będą one potrzebne do uruchomienia skryptu w następnym kroku. Skrypt można również pobrać ze strony wysuwu (lub za pomocą linku w następnym kroku).

   Możesz również kliknąć pozycję **Edytuj,** aby zmienić identyfikator aplikacji Azure lub nazwy nagłówków kolumn zdefiniowane na **stronie Mapowanie** plików.

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Krok 4. Uruchamianie przykładowego skryptu w celu przekazania danych HR

Ostatnim krokiem podczas konfigurowania łącznika kadr jest uruchomienie przykładowego skryptu, który przekaże dane dotyczące kadr w pliku CSV (utworzonym w kroku 2) do chmury firmy Microsoft. W szczególności skrypt przekaże dane do łącznika kadr. Po uruchomieniu skryptu łącznik kadr utworzony w kroku 3 zaim importuje dane kadr do Organizacji programu Microsoft 365, gdzie można uzyskać do nich dostęp za pomocą innych narzędzi do zgodności, takich jak rozwiązanie do zarządzania ryzykiem w niejawnym programie testów. Po uruchomieniu skryptu rozważ zaplanowanie zadania tak, aby było uruchamiane automatycznie codziennie, aby najnowsze dane o zakończeniu pracy pracownika były przekazywane do chmury firmy Microsoft. Zobacz [Planowanie automatycznego uruchamiania skryptu](#optional-step-6-schedule-the-script-to-run-automatically).

1. Przejdź do okna otwartego z poprzedniego kroku, aby uzyskać dostęp do witryny GitHub za pomocą przykładowego skryptu. Ewentualnie otwórz witrynę z zakładką lub użyj skopiowanego adresu URL.

2. Kliknij przycisk **Nieprzetworzone** , aby wyświetlić skrypt w widoku tekstu.

3. Skopiuj wszystkie wiersze w przykładowym skrypcie, a następnie zapisz je w pliku tekstowym.

4. W razie potrzeby zmodyfikuj przykładowy skrypt dla organizacji.

5. Zapisz plik tekstowy jako plik Windows PowerShell skryptu, używając sufiksu nazwy `.ps1`pliku , na przykład `HRConnector.ps1`.

6. Otwórz wiersz polecenia na komputerze lokalnym i przejdź do katalogu, w którym został zapisany skrypt.

7. Uruchom następujące polecenie, aby przekazać dane kadrowe z pliku CSV do chmury firmy Microsoft. na przykład:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -csvFilePath '<csvFilePath>'
    ```

   W poniższej tabeli opisano parametry, których należy użyć w tym skrypcie, oraz ich wymagane wartości. Informacje uzyskane w poprzednich krokach są używane w wartościach tych parametrów.

   | Parametr | Opis |
   |:-----|:-----|:-----|
   |`tenantId`|Identyfikator organizacji, Microsoft 365 uzyskany w kroku 1. Możesz również uzyskać identyfikator dzierżawy organizacji na stronie **Omówienie** w centrum administracyjnym usługi Azure AD. Służy on do identyfikowania Twojej organizacji.|
   |`appId` |Identyfikator aplikacji usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 1. Jest to używane przez usługę Azure AD do uwierzytelniania, gdy skrypt próbuje uzyskać dostęp do Twojej Microsoft 365 organizacji. |
   |`appSecret`|Aplikacja usługi Azure AD jest tajny dla aplikacji utworzonej w usłudze Azure AD w kroku 1. Ta metoda jest również używana do uwierzytelniania.|
   |`jobId`|Identyfikator zadania łącznika kadr utworzonego w kroku 3. Służy to do kojarzenia danych hr przekazywanych do chmury firmy Microsoft z łącznikiem kadr.|
   |`csvFilePath`|Ścieżka pliku CSV (zapisana w tym samym systemie, co skrypt) utworzona w kroku 2. Postaraj się uniknąć spacji w ścieżce pliku. w przeciwnym razie należy użyć cudzysłowów pojedynczych.|
   |||
   
   Oto przykład składni skryptu łącznika kadr z użyciem rzeczywistych wartości dla każdego parametru:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
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

Jeśli nie został uruchomiony skrypt w kroku 4, w obszarze Ostatni import jest wyświetlany link do pobierania **skryptu**. Możesz pobrać skrypt, a następnie wykonać czynności opisane w kroku 4, aby go uruchomić.

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

   1. W **polu Dodaj argumenty (opcjonalnie)** wklej to samo polecenie skryptu, które było uruchomiono w kroku 4. Na przykład `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. W polu **Rozpocznij w (opcjonalnie)** wklej lokalizację folderu skryptu, który został uruchomiony w kroku 4. Na przykład `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Kliknij **przycisk OK** , aby zapisać ustawienia nowej akcji.

8. W **oknie Tworzenie** zadania kliknij przycisk **OK** , aby zapisać zaplanowane zadanie. Może zostać wyświetlony monit o wprowadzenie poświadczeń konta użytkownika.

   Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.

   ![Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.](../media/HRConnectorTaskSchedulerLibrary.png)

   Zostanie wyświetlony czas ostatniego uruchomienia skryptu i następnego uruchomienia tego skryptu. Możesz kliknąć dwukrotnie zadanie, aby je edytować.

   Możesz także sprawdzić czas ostatniego uruchamiania skryptu na wysuwanych stronie odpowiedniego łącznika kadr w centrum zgodności.