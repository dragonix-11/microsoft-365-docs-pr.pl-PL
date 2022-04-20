---
title: Konfigurowanie łącznika w celu importowania danych kadr do chmury instytucji rządowych USA
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
description: Administratorzy w chmurze dla instytucji rządowych USA mogą skonfigurować łącznik danych w celu importowania danych pracowników z systemu zasobów ludzkich (HR) organizacji w celu Microsoft 365. Dzięki temu dane kadrowe w zasadach zarządzania ryzykiem wewnętrznym ułatwiają wykrywanie działań określonych użytkowników, które mogą stanowić wewnętrzne zagrożenie dla organizacji.
ms.openlocfilehash: 76de79cd856c9f114d219ffefbc45cf5e7692d40
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934758"
---
# <a name="set-up-a-connector-to-import-hr-data-in-us-government"></a>Konfigurowanie łącznika w celu importowania danych kadr w us government

Łącznik danych można skonfigurować w portalu zgodności usługi Microsoft Purview w celu zaimportowania danych zasobów ludzkich (HR) do organizacji instytucji rządowych USA. Dane związane z kadrą obejmują datę złożenia rezygnacji przez pracownika oraz datę ostatniego dnia pracownika. Te dane kadrowe mogą być następnie używane przez rozwiązania do ochrony informacji firmy Microsoft, takie jak [rozwiązanie do zarządzania ryzykiem wewnętrznym](insider-risk-management.md), aby chronić organizację przed złośliwymi działaniami lub kradzieżą danych w organizacji. Konfigurowanie łącznika hr składa się z tworzenia aplikacji w Azure Active Directory, która jest używana do uwierzytelniania za pomocą łącznika, tworzenia plików mapowania CSV zawierających dane kadr, tworzenia łącznika danych w centrum zgodności, a następnie uruchamiania skryptu (zgodnie z harmonogramem), który pozyskuje dane kadr w pliku CSV do chmury firmy Microsoft. Następnie łącznik danych jest używany przez narzędzie do zarządzania ryzykiem wewnętrznym w celu uzyskania dostępu do danych kadr zaimportowanych do organizacji Microsoft 365 us government.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Użytkownik, który tworzy łącznik hr w kroku 3, musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Rola administratora łącznika danych nie jest obecnie obsługiwana w środowiskach US Government GCC High i DoD. W związku z tym użytkownik, który tworzy łącznik hr w środowiskach GCC High i DoD, musi mieć przypisaną rolę eksportu importu skrzynki pocztowej w Exchange Online. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę Import eksportu skrzynki pocztowej można dodać do grupy ról Zarządzanie organizacją w Exchange Online. Możesz też utworzyć nową grupę ról, przypisać rolę Importuj eksport skrzynki pocztowej, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) lub [Modyfikowanie grup ról](/Exchange/permissions-exo/role-groups#modify-role-groups) w artykule "Zarządzanie grupami ról w Exchange Online".

- Musisz określić sposób pobierania lub eksportowania danych z systemu kadr organizacji (regularnie) i dodać je do pliku CSV opisanego w kroku 2. Skrypt uruchamiany w kroku 4 przekaże dane hr w pliku CSV do chmury firmy Microsoft.

- Przykładowy skrypt uruchamiany w kroku 4 przekaże dane kadrowe do chmury firmy Microsoft, aby mogły być używane przez inne narzędzia firmy Microsoft, takie jak rozwiązanie do zarządzania ryzykiem wewnętrznym. Ten przykładowy skrypt nie jest obsługiwany w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowy skrypt jest dostarczany jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowego skryptu i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w Azure Active Directory

Pierwszym krokiem jest utworzenie i zarejestrowanie nowej aplikacji w usłudze Azure Active Directory (Azure AD). Aplikacja będzie odpowiadać łącznikowi HR utworzonemu w kroku 3. Utworzenie tej aplikacji umożliwi usłudze Azure AD uwierzytelnienie łącznika hr po uruchomieniu i próbie uzyskania dostępu do organizacji. Ta aplikacja będzie również używana do uwierzytelniania skryptu uruchamianego w kroku 4 w celu przekazania danych kadr do chmury firmy Microsoft. Podczas tworzenia tej aplikacji usługi Azure AD zapisz następujące informacje. Te wartości będą używane w kolejnych krokach.

- Identyfikator aplikacji usługi Azure AD (nazywany również *identyfikatorem aplikacji* lub *identyfikatorem klienta*)

- Wpis tajny aplikacji usługi Azure AD (nazywany również *kluczem tajnym klienta*)

- Identyfikator dzierżawy (nazywany również *identyfikatorem katalogu*)

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji w usłudze Azure AD, zobacz [Rejestrowanie aplikacji przy użyciu Platforma tożsamości Microsoft](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-csv-file-with-your-hr-data"></a>Krok 2. Przygotowywanie pliku CSV z danymi hr

Następnym krokiem jest utworzenie pliku CSV zawierającego informacje o pracownikach, którzy opuścili organizację. Jak wyjaśniono w sekcji Przed rozpoczęciem, należy określić sposób generowania tego pliku CSV z systemu kadr organizacji. W poniższym przykładzie przedstawiono ukończony plik CSV (otwarty w okienku notatek), który zawiera trzy wymagane parametry (kolumny). Znacznie łatwiej jest edytować plik CSV w Microsoft Excel.

```text
EmailAddress,TerminationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

Pierwszy wiersz lub wiersz nagłówka pliku CSV zawiera listę wymaganych nazw kolumn. Nazwa używana w każdym nagłówku kolumny zależy od Ciebie (te w poprzednim przykładzie to sugestie). Jednak te same nazwy kolumn, których używasz w pliku CSV *, należy określić* podczas tworzenia łącznika hr w kroku 3. Nie uwzględniaj spacji w nazwach kolumn.

W poniższej tabeli opisano każdą kolumnę w pliku CSV:

| Nazwa kolumny | Opis |
|:-----|:-----|
| **Emailaddress** <br/> |Określa adres e-mail zakończonego pracownika.|
| **TerminationDate** <br/> |Określa datę oficjalnego zakończenia zatrudnienia danej osoby w organizacji. Na przykład może to być data, kiedy pracownik powiadomił o opuszczeniu organizacji. Ta data może być inna niż data ostatniego dnia pracy danej osoby. Użyj następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest [formatem daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|**LastWorkingDate**|Określa ostatni dzień pracy dla zakończonego pracownika. Użyj następującego formatu daty: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, który jest [formatem daty i godziny ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

Po utworzeniu pliku CSV z wymaganymi danymi hr zapisz go w tym samym systemie co skrypt uruchomiony w kroku 4. Pamiętaj, aby zaimplementować strategię aktualizacji, aby plik CSV zawsze zawiera najbardziej aktualne informacje. Dzięki temu, niezależnie od uruchomienia skryptu, najbardziej aktualne dane dotyczące zakończenia pracy pracowników są przekazywane do chmury firmy Microsoft.

## <a name="step-3-create-the-hr-connector"></a>Krok 3. Tworzenie łącznika hr

Następnym krokiem jest utworzenie łącznika hr w portalu zgodności. Po uruchomieniu skryptu w kroku 4 utworzony łącznik hr pozyskuje dane kadr z pliku CSV do organizacji Microsoft 365. W tym kroku skopiuj identyfikator zadania wygenerowany podczas tworzenia łącznika. Identyfikator zadania będzie używany podczas uruchamiania skryptu.

1. Przejdź do portalu zgodności i wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">stronę **Łączniki danych**</a>.

2. Na stronie **Łączniki danych** w obszarze **HR** kliknij pozycję **Wyświetl**.

3. Na stronie **HR** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Poświadczenia uwierzytelniania** wykonaj następujące czynności, a następnie kliknij przycisk **Dalej**:

   1. Wpisz lub wklej identyfikator aplikacji usługi Azure AD dla aplikacji platformy Azure utworzonej w kroku 1.

   1. Wpisz nazwę łącznika HR.

5. Na stronie **Mapowanie pliku** wpisz nazwy trzech nagłówków kolumn (nazywanych również *parametrami*) z pliku CSV utworzonego w kroku 2 w każdym z odpowiednich pól. Nazwy nie uwzględniają wielkości liter. Jak wyjaśniono wcześniej, nazwy wpisane w tych polach muszą być zgodne z nazwami parametrów w pliku CSV. Na przykład poniższy zrzut ekranu przedstawia nazwy parametrów z przykładu w przykładowym pliku CSV pokazanym w kroku 2.

   ![Nazwy nagłówków kolumn są zgodne z nazwami w pliku CSV.](../media/HRConnectorWizard3.png)

6. Na stronie **Przegląd** przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

   Zostanie wyświetlona strona stanu, która potwierdza, że łącznik został utworzony. Ta strona zawiera dwie ważne rzeczy, które należy wykonać w następnym kroku, aby uruchomić przykładowy skrypt w celu przekazania danych kadr.

   ![Przejrzyj stronę z identyfikatorem zadania i link do witryny GitHub, aby zapoznać się z przykładowym skryptem.](../media/HRConnector_Confirmation.png)

   1. **Identyfikator zadania.** Ten identyfikator zadania będzie potrzebny do uruchomienia skryptu w następnym kroku. Możesz skopiować go z tej strony lub ze strony wysuwanej łącznika.
   
   1. **Łącze do przykładowego skryptu.** Kliknij **link tutaj**, aby przejść do witryny GitHub, aby uzyskać dostęp do przykładowego skryptu (link otwiera nowe okno). Pozostaw to okno otwarte, aby można było skopiować skrypt w kroku 4. Alternatywnie możesz dodać zakładkę do miejsca docelowego lub skopiować adres URL, aby uzyskać do niego dostęp ponownie w kroku 4. Ten link jest również dostępny na stronie wysuwanego łącznika.

7. Kliknij pozycję **Gotowe**.

   Nowy łącznik jest wyświetlany na liście na **karcie Łączniki** . 

8. Kliknij właśnie utworzony łącznik HR, aby wyświetlić stronę wysuwaną zawierającą właściwości i inne informacje o łączniku.

   ![Strona wysuwana dla nowego łącznika HR.](../media/HRConnectorWizard7.png)

   Jeśli jeszcze tego nie zrobiono, możesz skopiować wartości identyfikatora **aplikacja systemu Azure** i **identyfikatora zadania łącznika**. Będą one potrzebne do uruchomienia skryptu w następnym kroku. Możesz również pobrać skrypt ze strony wysuwanej (lub pobrać go przy użyciu linku w następnym kroku).

   Możesz również kliknąć pozycję **Edytuj**, aby zmienić identyfikator aplikacja systemu Azure lub nazwy nagłówków kolumn zdefiniowane na stronie **Mapowanie pliku**.

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Krok 4. Uruchamianie przykładowego skryptu w celu przekazania danych kadr

Ostatnim krokiem konfigurowania łącznika hr jest uruchomienie przykładowego skryptu, który przekaże dane kadr w pliku CSV (utworzonym w kroku 2) do chmury firmy Microsoft. W szczególności skrypt przekazuje dane do łącznika hr. Po uruchomieniu skryptu łącznik hr utworzony w kroku 3 importuje dane kadrowe do organizacji Microsoft 365, do której mogą uzyskiwać dostęp inne narzędzia zgodności, takie jak rozwiązanie do zarządzania ryzykiem niejawnych testerów. Po uruchomieniu skryptu rozważ zaplanowanie zadania, aby uruchamiać je automatycznie codziennie, aby najbardziej aktualne dane dotyczące kończania pracy pracowników były przekazywane do chmury firmy Microsoft. Zobacz [Planowanie automatycznego uruchamiania skryptu](#optional-step-6-schedule-the-script-to-run-automatically).

1. Przejdź do okna, które zostało otwarte w poprzednim kroku, aby uzyskać dostęp do witryny GitHub przy użyciu przykładowego skryptu. Możesz też otworzyć witrynę z zakładki lub użyć skopiowanego adresu URL.

2. Kliknij przycisk **Nieprzetworzone** , aby wyświetlić skrypt w widoku tekstowym.

3. Skopiuj wszystkie wiersze w przykładowym skryptycie, a następnie zapisz je w pliku tekstowym.

4. W razie potrzeby zmodyfikuj przykładowy skrypt dla organizacji.

5. Zapisz plik tekstowy jako plik skryptu Windows PowerShell przy użyciu sufiksu nazwy `.ps1`pliku , na przykład `HRConnector.ps1`.

6. Otwórz wiersz polecenia na komputerze lokalnym i przejdź do katalogu, w którym zapisano skrypt.

7. Uruchom następujące polecenie, aby przekazać dane hr w pliku CSV do chmury firmy Microsoft; na przykład:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -csvFilePath '<csvFilePath>'
    ```

   W poniższej tabeli opisano parametry do użycia z tym skryptem i ich wymagane wartości. Informacje uzyskane w poprzednich krokach są używane w wartościach tych parametrów.

   | Parametr | Opis |
   |:-----|:-----|:-----|
   |`tenantId`|Identyfikator organizacji Microsoft 365 uzyskany w kroku 1. Identyfikator dzierżawy organizacji można również uzyskać w bloku **Przegląd** w centrum administracyjnym usługi Azure AD. Służy to do identyfikowania organizacji.|
   |`appId` |Identyfikator aplikacji usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 1. Jest ona używana przez usługę Azure AD do uwierzytelniania, gdy skrypt próbuje uzyskać dostęp do organizacji Microsoft 365. |
   |`appSecret`|Wpis tajny aplikacji usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 1. Jest to również używane do uwierzytelniania.|
   |`jobId`|Identyfikator zadania łącznika hr utworzonego w kroku 3. Służy to do kojarzenia danych kadr przekazywanych do chmury firmy Microsoft z łącznikiem HR.|
   |`csvFilePath`|Ścieżka pliku CSV (przechowywana w tym samym systemie co skrypt) utworzona w kroku 2. Staraj się unikać spacji w ścieżce pliku; W przeciwnym razie użyj pojedynczych cudzysłowów.|
   |||
   
   Oto przykład składni skryptu łącznika hr przy użyciu rzeczywistych wartości dla każdego parametru:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Jeśli przekazywanie zakończy się pomyślnie, skrypt wyświetli **komunikat Upload Pomyślne**.

   > [!NOTE]
   > Jeśli masz problemy z uruchomieniem poprzedniego polecenia z powodu zasad wykonywania, zobacz [Informacje o zasadach wykonywania](/powershell/module/microsoft.powershell.core/about/about_execution_policies) i [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) , aby uzyskać wskazówki dotyczące ustawiania zasad wykonywania.

## <a name="step-5-monitor-the-hr-connector"></a>Krok 5. Monitorowanie łącznika hr

Po utworzeniu łącznika hr i uruchomieniu skryptu w celu przekazania danych kadr można wyświetlić łącznik i przekazać stan w portalu zgodności. Jeśli planujesz regularne uruchamianie skryptu automatycznie, możesz również wyświetlić bieżący stan po ostatnim uruchomieniu skryptu.

1. Przejdź do portalu zgodności i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a>.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik HR, aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

   ![Strona wysuwanego łącznika hr z właściwościami i stanem.](../media/HRConnectorFlyout1.png)

3. W obszarze **Postęp** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o każdym uruchomieniu skryptu i przekazaniu danych z pliku CSV do chmury firmy Microsoft. 

   ![Plik dziennika łącznika HR wyświetla wiersze numerów z przekazanego pliku CSV.](../media/HRConnectorLogFile.png)

   Pole `RecordsSaved` wskazuje liczbę wierszy w przekazanym pliku CSV. Jeśli na przykład plik CSV zawiera cztery wiersze, wartość `RecordsSaved` pól wynosi 4, jeśli skrypt pomyślnie przekazał wszystkie wiersze w pliku CSV.

Jeśli skrypt nie został uruchomiony w kroku 4, w obszarze **Ostatni import** zostanie wyświetlony link umożliwiający pobranie skryptu. Możesz pobrać skrypt, a następnie wykonać kroki opisane w kroku 4, aby go uruchomić.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Opcjonalnie) Krok 6. Planowanie automatycznego uruchamiania skryptu

Aby upewnić się, że najnowsze dane kadrowe organizacji są dostępne dla narzędzi takich jak rozwiązanie do zarządzania ryzykiem wewnętrznym, zalecamy zaplanowanie automatycznego uruchamiania skryptu cyklicznie, na przykład raz dziennie. Wymaga to również zaktualizowania danych kadr w pliku CSV zgodnie z podobnym (jeśli nie tym samym) harmonogramem, tak aby zawierała najnowsze informacje o pracownikach, którzy opuszczają organizację. Celem jest przekazanie najbardziej aktualnych danych kadrowych, aby łącznik HR mógł udostępnić je rozwiązaniu do zarządzania ryzykiem wewnętrznym.

Możesz użyć aplikacji Harmonogram zadań w Windows, aby codziennie automatycznie uruchamiać skrypt.

1. Na komputerze lokalnym kliknij przycisk **Windows Start**, a następnie wpisz **Harmonogram zadań**.

2. Kliknij aplikację **Harmonogram zadań** , aby ją otworzyć.

3. W sekcji **Akcje** kliknij pozycję **Utwórz zadanie**.

4. Na karcie **Ogólne** wpisz opisową nazwę zaplanowanego zadania; Na przykład **skrypt łącznika hr**. Możesz również dodać opcjonalny opis.

5. W obszarze **Opcje zabezpieczeń** wykonaj następujące czynności:

   1. Określ, czy skrypt ma być uruchamiany tylko wtedy, gdy użytkownik jest zalogowany na komputerze, czy uruchamiany po zalogowaniu.
   
   1. Upewnij się, że zaznaczono pole wyboru **Uruchom z najwyższymi uprawnieniami** .

6. Wybierz kartę **Wyzwalacze** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

   1. W **obszarze Ustawienia** wybierz opcję **Codziennie**, a następnie wybierz datę i godzinę, aby uruchomić skrypt po raz pierwszy. Skrypt będzie uruchamiany codziennie o tej samej określonej godzinie.
   
   1. W obszarze **Ustawienia zaawansowane** upewnij się, że **zaznaczono** pole wyboru Włączone.
   
   1. Kliknij przycisk **OK**.

7. Wybierz kartę **Akcje** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

   ![Ustawienia akcji umożliwiające utworzenie nowego zaplanowanego zadania dla skryptu łącznika hr.](../media/HRConnectorScheduleTask1.png)

   1. Na liście rozwijanej **Akcja** upewnij się, że **wybrano pozycję Uruchom program** .

   1. W polu **Program/skrypt** kliknij pozycję **Przeglądaj**, a następnie przejdź do następującej lokalizacji i wybierz ją, aby ścieżka była wyświetlana w polu : `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`.

   1. W polu **Dodawanie argumentów (opcjonalnie)** wklej to samo polecenie skryptu, które zostało uruchomione w kroku 4. Na przykład `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. W polu **Start in (opcjonalnie) wklej** lokalizację folderu skryptu uruchomionego w kroku 4. Na przykład `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Kliknij **przycisk OK** , aby zapisać ustawienia nowej akcji.

8. W oknie **Tworzenie zadania** kliknij przycisk **OK** , aby zapisać zaplanowane zadanie. Może zostać wyświetlony monit o wprowadzenie poświadczeń konta użytkownika.

   Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.

   ![Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.](../media/HRConnectorTaskSchedulerLibrary.png)

   Zostanie wyświetlony czas ostatniego uruchomienia skryptu i następnego zaplanowanego uruchomienia. Możesz kliknąć dwukrotnie zadanie, aby je edytować.

   Możesz również sprawdzić czas ostatniego uruchomienia skryptu na stronie wysuwanej odpowiedniego łącznika hr w centrum zgodności.