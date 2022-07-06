---
title: Konfigurowanie łącznika w celu importowania fizycznych danych powodujących błędy
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
ms.custom: admindeeplinkCOMPLIANCE
description: Administratorzy mogą skonfigurować łącznik danych w celu importowania danych z fizycznego systemu rozwiązywania problemów organizacji na platformę Microsoft 365. Dzięki temu można użyć tych danych w zasadach zarządzania ryzykiem wewnętrznym, aby ułatwić wykrywanie dostępu do budynków fizycznych przez określonych użytkowników, które mogą wskazywać na możliwe wewnętrzne zagrożenie dla organizacji.
ms.openlocfilehash: 90e0a421397683fe05161b27b1743354713de516
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641433"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Konfigurowanie łącznika w celu importowania fizycznych danych powodujących błędy (wersja zapoznawcza)

Łącznik danych można skonfigurować w portal zgodności Microsoft Purview w celu zaimportowania fizycznych danych, takich jak nieprzetworzone zdarzenia dostępu fizycznego pracownika lub alarmy dostępu fizycznego generowane przez system złych zabezpieczeń organizacji. Przykładami fizycznych punktów dostępu jest wejście do budynku lub wejście do serwerowni lub centrum danych. Dane fizyczne mogą być używane przez [rozwiązanie do zarządzania ryzykiem wewnętrznym](insider-risk-management.md) platformy Microsoft 365, aby chronić organizację przed złośliwym działaniem lub kradzieżą danych w organizacji.

Konfigurowanie fizycznego łącznika powodującego błędy składa się z następujących zadań:

- Tworzenie aplikacji w usłudze Azure Active Directory (Azure AD) w celu uzyskania dostępu do punktu końcowego interfejsu API akceptującego ładunek JSON zawierający fizyczne dane powodujące błędy.

- Tworzenie ładunku JSON przy użyciu schematu zdefiniowanego przez fizyczny łącznik danych nieprawidłowego tworzenia.

- Tworzenie fizycznego łącznika danych powodującego niezgodność w portalu zgodności.

- Uruchamianie skryptu w celu wypchnięcia fizycznych danych powodujących nieprawidłowe działanie do punktu końcowego interfejsu API.

- Opcjonalnie zaplanowanie automatycznego uruchomienia skryptu w celu zaimportowania obecnie fizycznych danych powodujących nieprawidłowe działanie.

## <a name="before-you-set-up-the-connector"></a>Przed skonfigurowaniem łącznika

- Użytkownikowi, który tworzy fizyczny łącznik powodujący awarie w kroku 3, należy przypisać rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Rola Administracja łącznika danych nie jest obecnie obsługiwana w środowiskach US Government GCC High i DoD. W związku z tym użytkownik, który tworzy łącznik hr w środowiskach GCC High i DoD, musi mieć przypisaną rolę eksportu importu skrzynki pocztowej w Exchange Online. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę Import eksportu skrzynki pocztowej można dodać do grupy ról Zarządzanie organizacją w Exchange Online. Możesz też utworzyć nową grupę ról, przypisać rolę Importuj eksport skrzynki pocztowej, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) lub [Modyfikowanie grup ról](/Exchange/permissions-exo/role-groups#modify-role-groups) w artykule "Zarządzanie grupami ról w Exchange Online".

- Musisz określić sposób pobierania lub eksportowania danych z fizycznego systemu złego działania organizacji (codziennie) i utworzyć plik JSON opisany w kroku 2. Skrypt uruchamiany w kroku 4 spowoduje wypchnięcie danych w pliku JSON do punktu końcowego interfejsu API.

- Przykładowy skrypt uruchamiany w kroku 4 wypycha fizyczne nieprawidłowe dane z pliku JSON do interfejsu API łącznika, dzięki czemu mogą być używane przez rozwiązanie do zarządzania ryzykiem wewnętrznym. Ten przykładowy skrypt nie jest obsługiwany w ramach żadnego standardowego programu pomocy technicznej firmy Microsoft ani usługi. Przykładowy skrypt jest dostarczany jako is bez gwarancji jakiegokolwiek rodzaju. Firma Microsoft dodatkowo zrzeka się wszelkich dorozumianych gwarancji, w tym, bez ograniczeń, wszelkich domniemanych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko wynikające z użycia lub wydajności przykładowego skryptu i dokumentacji pozostaje z Tobą. W żadnym wypadku firma Microsoft, jej autorzy lub ktokolwiek inny zaangażowany w tworzenie, produkcję lub dostarczanie skryptów nie ponosi odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody za utratę zysków z działalności gospodarczej, przerwę w działalności, utratę informacji biznesowych lub inną stratę pieniężną) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub niemożności korzystania z nich,  nawet jeśli firma Microsoft została poinformowana o możliwości wystąpienia takich szkód.

- Ten łącznik jest dostępny w środowiskach GCC w chmurze microsoft 365 us government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w usłudze Azure Active Directory

Pierwszym krokiem jest utworzenie i zarejestrowanie nowej aplikacji w usłudze Azure Active Directory (Azure AD). Aplikacja będzie odpowiadać fizycznemu łącznikowi, który zostanie utworzony w kroku 3. Utworzenie tej aplikacji umożliwi Azure AD uwierzytelnienie żądania wypychania ładunku JSON zawierającego fizyczne dane powodujące nieprawidłowe zabezpieczenia. Podczas tworzenia tej aplikacji Azure AD zapisz następujące informacje. Te wartości będą używane w kolejnych krokach.

- Azure AD identyfikator aplikacji (nazywany również *identyfikatorem aplikacji* lub *identyfikatorem klienta*)

- Azure AD wpis tajny aplikacji (nazywany również *kluczem tajnym klienta*)

- Identyfikator dzierżawy (nazywany również *identyfikatorem katalogu*)

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji w Azure AD, zobacz [Rejestrowanie aplikacji przy użyciu Platforma tożsamości Microsoft](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>Krok 2. Przygotowywanie pliku JSON z fizycznymi danymi powodującymi błędy

Następnym krokiem jest utworzenie pliku JSON zawierającego informacje o danych dostępu fizycznego pracowników. Jak wyjaśniono w sekcji przed rozpoczęciem, należy określić sposób generowania tego pliku JSON z fizycznego systemu rozwiązywania problemów w organizacji.

Plik JSON musi być zgodny z definicją schematu wymaganą przez łącznik. Poniżej przedstawiono opisy wymaganych właściwości schematu dla pliku JSON:

|Właściwość|Opis|Typ danych|
|---|---|---|
|Userid|Pracownik może mieć wiele tożsamości cyfrowych w różnych systemach. Dane wejściowe muszą mieć identyfikator Azure AD już rozpoznany przez system źródłowy.|Nazwa UPN lub adres e-mail|
|Identyfikator zasobu|Identyfikator referencyjny zasobu fizycznego lub fizycznego punktu dostępu.|Ciąg alfanumeryczny|
|AssetName|Przyjazna nazwa zasobu fizycznego lub fizycznego punktu dostępu.|Ciąg alfanumeryczny|
|Eventtime|Sygnatura czasowa dostępu.|Data i godzina w formacie UTC|
|AccessStatus|Wartość lub `Success``Failed`|Ciąg|
|||

Oto przykład pliku JSON, który jest zgodny z wymaganym schematem:

```json
[
    {
        "UserId":"sarad@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T01:57:49",
        "AccessStatus":"Failed"
    },
    {
        "UserId":"pilarp@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T02:57:49",
        "AccessStatus":"Success"
    }
]
```

Możesz również pobrać następującą definicję schematu pliku JSON z kreatora podczas tworzenia fizycznego łącznika rozwiązywania problemów w kroku 3.

```text
{
   "title" : "Physical Badging Signals",
   "description" : "Access signals from physical badging systems",
   "DataType" : {
      "description" : "Identify what is the data type for input signal",
      "type" : "string",
   },
   "type" : "object",
   "properties": {
      "UserId" : {
         "description" : "Unique identifier AAD Id resolved by the source system",
         "type" : "string",
      },
      "AssetId": {
         "description" : "Unique ID of the physical asset/access point",
         "type" : "string",
      },
      "AssetName": {
         "description" : "friendly name of the physical asset/access point",
         "type" : "string",
      },
      "EventTime" : {
         "description" : "timestamp of access",
         "type" : "string",
      },
      "AccessStatus" : {
         "description" : "what was the status of access attempt - Success/Failed",
         "type" : "string",
      },
   }
   "required" : ["UserId", "AssetId", "EventTime" "AccessStatus"]
}
```

## <a name="step-3-create-the-physical-badging-connector"></a>Krok 3. Tworzenie fizycznego łącznika powodującego błędy

Następnym krokiem jest utworzenie fizycznego łącznika powodującego niezgodność w portalu zgodności. Po uruchomieniu skryptu w kroku 4 plik JSON utworzony w kroku 3 zostanie przetworzony i wypchnięty do punktu końcowego interfejsu API skonfigurowanego w kroku 1. W tym kroku skopiuj identyfikator JobId wygenerowany podczas tworzenia łącznika. Użyjesz identyfikatora JobId podczas uruchamiania skryptu.

1. Przejdź do portalu zgodności i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a>.

2. Na stronie **Łączniki danych** w obszarze **Fizyczne błędy** kliknij pozycję **Wyświetl**.

3. Na stronie **Fizyczne błędy** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Poświadczenia uwierzytelniania** wykonaj następujące czynności, a następnie kliknij przycisk **Dalej**:

   1. Wpisz lub wklej identyfikator aplikacji Azure AD dla aplikacji platformy Azure utworzonej w kroku 1.

   2. Pobierz przykładowy schemat dla odwołania, aby utworzyć plik JSON.

   3. Wpisz unikatową nazwę fizycznego łącznika powodującego błędy.

5. Na stronie **Przegląd** przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

6. Zostanie wyświetlona strona stanu, która potwierdza, że łącznik został utworzony. Ta strona zawiera również identyfikator zadania. Identyfikator zadania można skopiować z tej strony lub ze strony wysuwanej łącznika. Ten identyfikator zadania jest potrzebny podczas uruchamiania skryptu.

   Strona stanu zawiera również link do skryptu. Zapoznaj się z tym skryptem, aby dowiedzieć się, jak opublikować plik JSON w punkcie końcowym interfejsu API.

7. Kliknij pozycję **Gotowe**.

   Nowy łącznik jest wyświetlany na liście na **karcie Łączniki** .

8. Kliknij utworzony właśnie łącznik fizycznego rozwiązywania problemów, aby wyświetlić stronę wysuwaną zawierającą właściwości i inne informacje o łączniku.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>Krok 4. Uruchamianie skryptu w celu opublikowania pliku JSON zawierającego fizyczne nieprawidłowe dane

Następnym krokiem konfigurowania fizycznego łącznika do rozwiązywania problemów jest uruchomienie skryptu, który wypchnie fizyczne dane powodujące nieprawidłowe działanie w pliku JSON (utworzonym w kroku 2) do punktu końcowego interfejsu API utworzonego w kroku 1. Udostępniamy przykładowy skrypt dla Twojego odwołania i możesz go użyć lub utworzyć własny skrypt do publikowania pliku JSON w punkcie końcowym interfejsu API.

Po uruchomieniu skryptu plik JSON zawierający fizyczne nieprawidłowe dane zostanie wypchnięty do organizacji platformy Microsoft 365, do której można uzyskać dostęp za pomocą rozwiązania do zarządzania ryzykiem wewnętrznym. Zalecamy codzienne publikowanie fizycznych danych powodujących złe kondycje. Można to zrobić, automatyzując proces generowania pliku JSON codziennie z fizycznego systemu badging, a następnie planując skrypt do wypychania danych.

> [!NOTE]
> Maksymalna liczba rekordów w pliku JSON, które mogą być przetwarzane przez interfejs API, wynosi 50 000 rekordów.

1. Przejdź do [tej witryny usługi GitHub](https://github.com/microsoft/m365-physical-badging-connector-sample-scripts/blob/master/push_physical_badging_records.ps1) , aby uzyskać dostęp do przykładowego skryptu.

2. Kliknij przycisk **Nieprzetworzone** , aby wyświetlić skrypt w widoku tekstowym

3. Skopiuj wszystkie wiersze w przykładowym skryptycie, a następnie zapisz je w pliku tekstowym.

4. W razie potrzeby zmodyfikuj przykładowy skrypt dla organizacji.

5. Zapisz plik tekstowy jako plik skryptu Windows PowerShell przy użyciu sufiksu nazwy pliku .ps1, na przykład PhysicalBadging.ps1.

6. Otwórz wiersz polecenia na komputerze lokalnym i przejdź do katalogu, w którym zapisano skrypt.

7. Uruchom następujące polecenie, aby wypchnąć dane fizyczne w pliku JSON do chmury firmy Microsoft; na przykład:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   W poniższej tabeli opisano parametry do użycia z tym skryptem i ich wymagane wartości. Informacje uzyskane w poprzednich krokach są używane w wartościach tych parametrów.

   |Parametr|Opis|
   |---|---|
   |tenantId|Jest to identyfikator organizacji platformy Microsoft 365 uzyskany w kroku 1. Identyfikator tenantId organizacji można również uzyskać w bloku **Przegląd** w centrum administracyjnym Azure AD. Służy to do identyfikowania organizacji.|
   |Appid|Jest to identyfikator aplikacji Azure AD dla aplikacji utworzonej w Azure AD w kroku 1. Jest to używane przez Azure AD do uwierzytelniania, gdy skrypt próbuje uzyskać dostęp do organizacji platformy Microsoft 365.|
   |appSecret|Jest to Azure AD wpis tajny aplikacji dla aplikacji utworzonej w Azure AD w kroku 1. Jest to również używane do uwierzytelniania.|
   |Jobid|Jest to identyfikator zadania fizycznego łącznika powodującego błędy, który został utworzony w kroku 3. Służy to do kojarzenia fizycznych danych, które są wypychane do chmury firmy Microsoft, z fizycznym łącznikiem powodującym błędy.|
   |JsonFilePath|Jest to ścieżka pliku na komputerze lokalnym (ta, której używasz do uruchamiania skryptu) dla pliku JSON utworzonego w kroku 2. Ten plik musi być zgodny ze schematem przykładowym opisanym w kroku 3.|
   |||

   Oto przykład składni fizycznego skryptu łącznika badging przy użyciu rzeczywistych wartości dla każdego parametru:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -jsonFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Jeśli przekazywanie zakończy się pomyślnie, skrypt wyświetli komunikat **Przekaż pomyślnie** .

   Jeśli masz wiele plików JSON, musisz uruchomić skrypt dla każdego pliku.

> [!NOTE]
> Możesz również wypchnąć dane fizyczne do punktu końcowego interfejsu API za pomocą metod innych niż uruchamianie poprzedniego skryptu. Oto przykład użycia narzędzia Postman do wypychania danych do punktu końcowego interfejsu API.

## <a name="step-5-monitor-the-physical-badging-connector"></a>Krok 5. Monitorowanie fizycznego łącznika rozwiązywania problemów

Po utworzeniu fizycznego łącznika powodującego niezgodność i wypchnięciu fizycznych danych powodujących niezgodność można wyświetlić łącznik i przekazać stan w portalu zgodności. Jeśli planujesz regularne uruchamianie skryptu automatycznie, możesz również wyświetlić bieżący stan po ostatnim uruchomieniu skryptu.

1. Przejdź do portalu zgodności i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a>.

2. Kliknij kartę **Łączniki,** a następnie wybierz fizyczny łącznik rozwiązywania problemów, aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

   ![Strona wysuwanego stanu dla fizycznego łącznika powodującego błędy.](..\media\PhysicalBadgingStatusFlyout.png)

3. W obszarze **Ostatni import** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o każdym uruchomieniu skryptu i przekazaniu danych z pliku JSON do chmury firmy Microsoft.

   ![Plik dziennika łącznika błędów fizycznych wyświetla liczbę obiektów z przekazanego pliku JSON.](..\media\PhysicalBadgingConnectorLogFile.png)

   Pole **RecordsSaved** wskazuje liczbę rekordów w przekazanym pliku JSON. Jeśli na przykład plik JSON zawiera cztery rekordy, wartość pól **Rekordynapisane** wynosi 4, jeśli skrypt pomyślnie przekazał wszystkie rekordy w pliku JSON. Pole **RecordsSkipped** wskazuje liczbę rekordów w pliku JSON, które zostały pominięte. Przed przekazaniem rekordów w pliku JSON zostaną zweryfikowane identyfikatory poczty e-mail rekordów. Każdy rekord o nieprawidłowym identyfikatorze poczty e-mail zostanie pominięty, a odpowiedni identyfikator wiadomości e-mail zostanie wyświetlony w polu **EmailIdsNotSaved**

Jeśli skrypt nie został uruchomiony w kroku 4, w obszarze **Ostatni import** zostanie wyświetlony link umożliwiający pobranie skryptu. Możesz pobrać skrypt, a następnie wykonać kroki opisane w kroku 4, aby go uruchomić.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Opcjonalnie) Krok 6. Planowanie automatycznego uruchamiania skryptu

Aby upewnić się, że najnowsze fizyczne dane z organizacji są dostępne dla narzędzi takich jak rozwiązanie do zarządzania ryzykiem wewnętrznym, zalecamy zaplanowanie automatycznego uruchamiania skryptu cyklicznie, na przykład raz dziennie. Wymaga to również zaktualizowania fizycznych danych błędnych do pliku JSON zgodnie z podobnym (jeśli nie tym samym) harmonogramem, tak aby zawierała najnowsze informacje o pracownikach opuszczających organizację. Celem jest przekazanie najbardziej aktualnych fizycznych danych powodujących błędy w zabezpieczeniach, aby fizyczny łącznik do rozwiązywania problemów mógł udostępnić je rozwiązaniu do zarządzania ryzykiem wewnętrznym.

Aplikacja Harmonogram zadań w systemie Windows umożliwia automatyczne uruchamianie skryptu każdego dnia.

1. Na komputerze lokalnym kliknij przycisk **Start** systemu Windows, a następnie wpisz **Harmonogram zadań**.

2. Kliknij aplikację **Harmonogram zadań** , aby ją otworzyć.

3. W sekcji **Akcje** kliknij pozycję **Utwórz zadanie**.

4. Na karcie **Ogólne** wpisz opisową nazwę zaplanowanego zadania; na przykład **fizyczny skrypt łącznika badging**. Możesz również dodać opcjonalny opis.

5. W obszarze **Opcje zabezpieczeń** wykonaj następujące czynności:

   1. Określ, czy skrypt ma być uruchamiany tylko wtedy, gdy użytkownik jest zalogowany na komputerze, czy uruchamiany po zalogowaniu.

   2. Upewnij się, że zaznaczono pole wyboru **Uruchom z najwyższymi uprawnieniami** .

6. Wybierz kartę **Wyzwalacze** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

   1. W obszarze **Ustawienia** wybierz opcję **Codziennie** , a następnie wybierz datę i godzinę, aby uruchomić skrypt po raz pierwszy. Skrypt będzie uruchamiany codziennie o tej samej określonej godzinie.

   2. W obszarze **Ustawienia zaawansowane** upewnij się, że **zaznaczono** pole wyboru Włączone.

   3. Kliknij przycisk **OK**.

7. Wybierz kartę **Akcje** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

   ![Ustawienia akcji umożliwiające utworzenie nowego zaplanowanego zadania dla skryptu łącznika fizycznego.](..\media\SchedulePhysicalBadgingScript1.png)

   1. Na liście rozwijanej **Akcja** upewnij się, że **wybrano pozycję Uruchom program** .

   2. W polu **Program/skrypt** kliknij pozycję **Przeglądaj**, a następnie przejdź do następującej lokalizacji i wybierz ją, aby ścieżka była wyświetlana w polu: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe.

   3. W polu **Dodawanie argumentów (opcjonalnie)** wklej to samo polecenie skryptu, które zostało uruchomione w kroku 4. Na przykład: .\PhysicalBadging.ps1-tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -jsonFilePath "C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json"

   4. W polu **Start in (opcjonalnie) wklej** lokalizację folderu skryptu uruchomionego w kroku 4. Na przykład C:\Users\contosoadmin\Desktop\Scripts.

   5. Kliknij **przycisk OK** , aby zapisać ustawienia nowej akcji.

8. W oknie **Tworzenie zadania** kliknij przycisk **OK** , aby zapisać zaplanowane zadanie. Może zostać wyświetlony monit o wprowadzenie poświadczeń konta użytkownika.

   Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.

   ![Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.](..\media\SchedulePhysicalBadgingScript2.png)

Zostanie wyświetlony czas ostatniego uruchomienia skryptu i następnego zaplanowanego uruchomienia. Możesz kliknąć dwukrotnie zadanie, aby je edytować.

Możesz również sprawdzić, kiedy ostatni raz skrypt był uruchamiany na stronie wysuwanej odpowiedniego fizycznego łącznika powodującego błędy w centrum zgodności.
