---
title: Konfigurowanie łącznika w celu importowania danych z fizycznymi zabezpieczeniami badgingu
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
description: Administratorzy mogą skonfigurować łącznik danych w celu importowania danych z fizycznego systemu zarządzania zabezpieczeniami w organizacji w celu Microsoft 365. Dzięki temu można używać tych danych w zasadach zarządzania ryzykiem w niejawnym programie testów w celu wykrywania dostępu konkretnych użytkowników do budynków fizycznych, które mogą wskazywać na możliwe zagrożenia wewnętrzne organizacji.
ms.openlocfilehash: 7eddede8b98d1b676e51a95e4fed3787f56d0bf0
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009720"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Konfigurowanie łącznika w celu importowania danych z fizycznymi funkcjami badgingu (wersja zapoznawcza)

Możesz skonfigurować łącznik danych w aplikacji Centrum zgodności platformy Microsoft 365 w celu importowania danych zabezpieczających fizycznej, takich jak zdarzenia dostępu fizycznego pracownika lub dowolne alarmy dostępu fizycznego generowane przez system zarządzania zabezpieczeniami w organizacji. Przykładami fizycznych punktów dostępu są dane wejścia do budynku lub do serwera albo centrum danych. Dane do oceny fizycznej mogą być używane przez rozwiązanie firmy Microsoft 365 do [](insider-risk-management.md) zarządzania ryzykiem w niejawnym programie testów w celu ochrony organizacji przed złośliwymi działaniami i kradzieżą danych w organizacji.

Konfigurowanie fizycznego łącznika badgingu składa się z następujących zadań:

- Tworzenie aplikacji w usłudze Azure Active Directory (Azure AD) w celu uzyskania dostępu do punktu końcowego interfejsu API akceptującego ład JSON, który zawiera dane fizycznego oceniania.

- Creating the JSON payload with a schema defined by physical badging data connector.

- Tworzenie fizycznego łącznika danych w Centrum zgodności platformy Microsoft 365.

- Uruchamianie skryptu w celu wypychania danych fizycznych do punktu końcowego interfejsu API.

- Opcjonalnie możesz zaplanować automatyczne uruchamianie skryptu w celu zaimportowania aktualnie wybieranych danych.

## <a name="before-you-set-up-the-connector"></a>Przed skonfigurowaniem łącznika

- Użytkownik, który tworzy fizyczny łącznik z koszem w kroku 3, musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć nową grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Należy określić, jak pobrać lub wyeksportować dane z fizycznego systemu taki jak system taki organizacji (który jest pobierany codziennie) i utworzyć plik JSON opisany w kroku 2. Skrypt uruchomiony w kroku 4 wypchnie dane z pliku JSON do punktu końcowego interfejsu API.

- Przykładowy skrypt uruchomiony w kroku 4 wypycha fizyczne dane z pliku JSON do interfejsu API łącznika, dzięki czemu może być używany przez rozwiązanie do zarządzania ryzykiem w niejawnym programie testów. Ten przykładowy skrypt nie jest obsługiwany w żadnym standardowym programie lub usłudze pomocy technicznej firmy Microsoft. Przykładowy skrypt jest dostarczany W JAKIM JEST bez jakiejkolwiek gwarancji. Firma Microsoft dodatkowo nie udziela żadnych dorozumianych gwarancji, w tym, ale nie wyłącznie, żadnych dorozumianych gwarancji przydatności handlowej lub przydatności do określonego celu. Całe ryzyko związane z użyciem lub wykonaniem przykładowego skryptu i dokumentacji pozostaje tylko dla użytkownika. Firma Microsoft, jej autorzy ani nikt inny biorący udział w tworzeniu, produkcji lub dostarczaniu skryptów nie będą w żadnym wypadku ponosić odpowiedzialności za jakiekolwiek szkody (w tym, bez ograniczeń, szkody związane z utratą zysków, przerwami w działaniu firmy, utratą informacji biznesowych lub inne straty pieniężne) wynikające z korzystania z przykładowych skryptów lub dokumentacji lub nieumiejętnego korzystania z tych skryptów lub dokumentacji.  nawet jeśli firma Microsoft została powiadomiona o możliwości wystąpienia takich szkód.

- Ten łącznik jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w aplikacji Azure Active Directory

Pierwszym krokiem jest utworzenie i zarejestrowanie nowej aplikacji w usłudze Azure Active Directory (Azure AD). Aplikacja będzie odpowiadać fizycznemu łącznikowi do oznaczania, który został przez Ciebie utworzeniu w kroku 3. Utworzenie tej aplikacji umożliwi usłudze Azure AD uwierzytelnienie żądania wypychania dla obciążenia JSON zawierającego dane fizycznego oceniania. Podczas tworzenia tej aplikacji Azure AD pamiętaj o zapisaniu poniższych informacji. Te wartości zostaną użyte w kolejnych krokach.

- Identyfikator aplikacji usługi Azure AD (nazywany również *identyfikatorem aplikacji* lub *identyfikatorem klienta*)

- Klucz tajny aplikacji usługi Azure AD (nazywany także *kluczem tajnym klienta*)

- Identyfikator dzierżawy (nazywany również *identyfikatorem katalogu*)

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji w usłudze Azure AD, zobacz [Rejestrowanie](/azure/active-directory/develop/quickstart-register-app) aplikacji w Platforma tożsamości Microsoft.

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>Krok 2. Przygotowywanie pliku JSON z danymi fizycznymi do oszytowania

Następnym krokiem jest utworzenie pliku JSON zawierającego informacje o danych fizycznego dostępu pracowników. Zgodnie z wyjaśnieniami w sekcji przed rozpoczęciem musisz ustalić, jak wygenerować ten plik JSON na podstawie fizycznego systemu taki jak w Twojej organizacji.

Plik JSON musi być zgodny z definicją schematu wymaganą przez łącznik. Poniżej znajdują się opisy wymaganych właściwości schematu dla pliku JSON:

|Właściwość|Opis|Typ danych|
|---|---|---|
|UserId|Pracownik może mieć wiele tożsamości cyfrowych w systemach. Dane wejściowe muszą mieć już identyfikator Azure AD rozpoznany przez system źródłowy.|UpN lub adres e-mail|
|AssetId|Identyfikator odwołania zasobu fizycznego lub punktu dostępu fizycznego.|Ciąg alfanumeryczny|
|AssetName|Przyjazna nazwa zasobu fizycznego lub punktu dostępu fizycznego.|Ciąg alfanumeryczny|
|EventTime|Sygnatura czasowa dostępu.|Data i godzina w formacie UTC|
|AccessStatus|Wartość lub `Success``Failed`|Ciąg|
|||

Oto przykładowy plik JSON zgodny z wymaganym schematem:

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

Możesz również pobrać następującą definicję schematu dla pliku JSON z kreatora podczas tworzenia fizycznego łącznika wybierającego w kroku 3.

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

## <a name="step-3-create-the-physical-badging-connector"></a>Krok 3. Tworzenie łącznika z fizycznymi zabezpieczeniami

Następnym krokiem jest utworzenie fizycznego łącznika w Centrum zgodności platformy Microsoft 365. Po uruchomieniu skryptu w kroku 4 plik JSON utworzony w kroku 3 zostanie przetworzony i wypychany do punktu końcowego interfejsu API skonfigurowanego w kroku 1. W tym kroku pamiętaj o skopiowaniu dokumentu JobId wygenerowanego podczas tworzenia łącznika. Po uruchomieniu skryptu użyjesz polecenia JobId.

1. Przejdź do Centrum zgodności platformy Microsoft 365 i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a>.

2. Na stronie **Łączniki danych** w obszarze **Fizyczne krawędzie** kliknij pozycję **Widok**.

3. Na stronie **Fizyczne dodawanie podziałów stron** kliknij pozycję **Dodaj łącznik**.

4. Na stronie **Poświadczenia uwierzytelniania** wykonaj następujące czynności, a następnie kliknij przycisk **Dalej**:

   1. Wpisz lub wklej identyfikator aplikacji usługi Azure AD dla aplikacji Azure utworzonej w kroku 1.

   2. Pobierz przykładowy schemat referencyjny, aby utworzyć plik JSON.

   3. Wpisz unikatową nazwę łącznika z fizycznymi zabezpieczeniami.

5. Na stronie **Recenzja** przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

6. Zostanie wyświetlona strona stanu z potwierdzeniem utworzenia łącznika. Ta strona zawiera również identyfikator zadania. Możesz skopiować identyfikator zadania z tej strony lub ze strony wysuwanych łącznika. Ten identyfikator zadania jest potrzebny podczas uruchamiania skryptu.

   Strona stanu zawiera również link do skryptu. Skorzystaj z tego skryptu, aby dowiedzieć się, jak opublikować plik JSON w punkcie końcowym interfejsu API.

7. Kliknij **przycisk Gotowe**.

   Nowy łącznik zostanie wyświetlony na liście na karcie **Łączniki** .

8. Kliknij utworzony fizycznie łącznik z informacjami, aby wyświetlić stronę wysuwu zawierającą właściwości i inne informacje o łączniku.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>Krok 4. Uruchom skrypt, aby opublikować plik JSON zawierający dane fizycznego oceniania

Następnym krokiem podczas konfigurowania łącznika z fizycznymi zabezpieczeniami jest uruchomienie skryptu, który wypchnie fizyczne dane z pliku JSON (utworzonego w kroku 2) do punktu końcowego interfejsu API utworzonego w kroku 1. Zapewniamy przykładowy skrypt dla Twojego odwołania i możesz go użyć lub utworzyć własny skrypt w celu opublikować plik JSON w punkcie końcowym interfejsu API.

Po uruchomieniu skryptu plik JSON zawierający fizyczne dane oceny jest wypychany do Twojej organizacji Microsoft 365, gdzie może uzyskać do niego dostęp rozwiązanie do zarządzania ryzykiem w niejawnym programie testów. Zalecamy, aby codziennie publikować dane z fizycznymi listami. Możesz to zrobić, automatyzując proces generowania pliku JSON każdego dnia na podstawie fizycznego systemu oceny, a następnie planując skrypt w celu wypchania danych.

> [!NOTE]
> Maksymalna liczba rekordów w pliku JSON, które mogą być przetwarzane przez interfejs API, wynosi 50 000 rekordów.

1. Przejdź do [tej GitHub, aby](https://github.com/microsoft/m365-physical-badging-connector-sample-scripts/blob/master/push_physical_badging_records.ps1) uzyskać dostęp do przykładowego skryptu.

2. Kliknij przycisk **Nieprzetworzone** , aby wyświetlić skrypt w widoku tekstu

3. Skopiuj wszystkie wiersze w przykładowym skrypcie, a następnie zapisz je w pliku tekstowym.

4. W razie potrzeby zmodyfikuj przykładowy skrypt dla organizacji.

5. Zapisz plik tekstowy jako plik Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, na przykład PhysicalBadging.ps1.

6. Otwórz wiersz polecenia na komputerze lokalnym i przejdź do katalogu, w którym został zapisany skrypt.

7. Uruchom następujące polecenie, aby wypchnąć dane fizycznego zabezpieczenia w pliku JSON do chmury firmy Microsoft. na przykład:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   W poniższej tabeli opisano parametry, których należy użyć w tym skrypcie, oraz ich wymagane wartości. Informacje uzyskane w poprzednich krokach są używane w wartościach tych parametrów.

   |Parametr|Opis|
   |---|---|
   |tenantId|Jest to identyfikator organizacji, Microsoft 365 uzyskany w kroku 1. Możesz również uzyskać adres dzierżawy organizacji na stronie **Omówienie** w centrum administracyjnym usługi Azure AD. Służy on do identyfikowania Twojej organizacji.|
   |appId|Jest to identyfikator aplikacji usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 1. Jest to używane przez usługę Azure AD do uwierzytelniania, gdy skrypt próbuje uzyskać dostęp do Twojej Microsoft 365 organizacji.|
   |appSecret|Jest to tajny kod aplikacji usługi Azure AD dla aplikacji utworzonej w usłudze Azure AD w kroku 1. Ta metoda jest również używana do uwierzytelniania.|
   |jobId|Jest to identyfikator zadania łącznika fizycznego, który został utworzony w kroku 3. Służy to do kojarzenia fizycznych danych zabezpieczających, które są wypychane do chmury firmy Microsoft, z fizycznym łącznikiem stosowanym do oznaczania tej właściwości.|
   |JsonFilePath|Jest to ścieżka do pliku utworzonego w kroku 2 na komputerze lokalnym (na komputerze, za pomocą których uruchamiasz skrypt) do pliku JSON. Ten plik musi być postępować zgodnie z przykładowym schematem opisanym w kroku 3.|
   |||

   Oto przykład składni skryptu łącznika z wartościami rzeczywistymi dla każdego parametru:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -jsonFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Jeśli przekazywanie się powiedzie, skrypt wyświetli komunikat o **błędzie Upload pomyślny**.

   Jeśli masz wiele plików JSON, musisz uruchomić skrypt dla każdego pliku.

> [!NOTE]
> Możesz również wypchnąć fizyczne dane wybierane na stronie klienta do punktu końcowego interfejsu API przy użyciu metod innych niż uruchamianie poprzedniego skryptu. Oto przykładowy przykład użycia usługi Postman do wypychania danych do punktu końcowego interfejsu API.

## <a name="step-5-monitor-the-physical-badging-connector"></a>Krok 5. Monitorowanie fizycznego łącznika badgingu

Po utworzeniu fizycznego łącznika badgingu i wypchnieniu danych z fizycznego zabezpieczenia, możesz wyświetlić łącznik i stan przekazywania w Centrum zgodności platformy Microsoft 365. Jeśli skrypt ma być uruchamiany automatycznie regularnie, można także wyświetlić bieżący stan po ostatnim uruchomieniu skryptu.

1. Przejdź do Centrum zgodności platformy Microsoft 365 i wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Łączniki danych**</a>.

2. Kliknij **kartę Łączniki** , a następnie wybierz fizyczny łącznik, aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

   ![Wysuuwana strona stanu dla łącznika z fizycznymi zabezpieczeniami.](..\media\PhysicalBadgingStatusFlyout.png)

3. W **obszarze Ostatni import** **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o każdym uruchamianiu skryptu i przekazywaniu danych z pliku JSON do chmury firmy Microsoft.

   ![W pliku dziennika łączników z listą właściwości fizycznych jest wyświetlana liczba obiektów z przekazanego pliku JSON.](..\media\PhysicalBadgingConnectorLogFile.png)

   Pole **RecordsSaved** wskazuje liczbę obiektów w przekazanym pliku JSON. Jeśli na przykład plik JSON zawiera cztery obiekty, wartość pól **RecordsSaved** wynosi 4, jeśli skrypt pomyślnie przesłał wszystkie obiekty w pliku JSON.

Jeśli nie został uruchomiony skrypt w kroku 4, w obszarze Ostatni import jest wyświetlany link do pobierania **skryptu**. Możesz pobrać skrypt, a następnie wykonać czynności opisane w kroku 4, aby go uruchomić.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Opcjonalnie) Krok 6. Planowanie automatycznego uruchamiania skryptu

Aby upewnić się, że najnowsze fizyczne dane dotyczące umówiania są dostępne dla narzędzi, takich jak rozwiązanie do zarządzania ryzykiem w niejawnym programie testów, zaleca się cykliczne uruchamianie skryptu, na przykład raz dziennie. Wymaga to również zaktualizowania danych fizycznych do pliku JSON zgodnie z podobnym (jeśli nie tym samym) harmonogramem, tak aby zawierał najnowsze informacje o pracownikach, którzy opuszczają Twoją organizację. Celem tego jest przekazanie najbardziej aktualnych danych dotyczących fizycznego zabezpieczenia, tak aby łącznik taki był dostępny dla rozwiązania do zarządzania ryzykiem w niejawnym programie testów.

Za pomocą aplikacji Harmonogram zadań w programie Windows uruchamiać skrypt automatycznie każdego dnia.

1. Na komputerze lokalnym kliknij przycisk Windows **Start**, a następnie wpisz **Harmonogram zadań**.

2. Kliknij aplikację **Harmonogram zadań** , aby ją otworzyć.

3. W sekcji **Akcje** kliknij pozycję **Utwórz zadanie**.

4. Na **karcie** Ogólne wpisz opisową nazwę zaplanowanego zadania. Na przykład skrypt **łącznika z fizycznymi zabezpieczeniami.** Możesz również dodać opcjonalny opis.

5. W **obszarze Opcje zabezpieczeń** wykonaj następujące czynności:

   1. Określ, czy skrypt ma być uruchamiany tylko po zalogowaniu się na komputerze, czy po zalogowaniu się.

   2. Upewnij się, że **jest zaznaczone pole** wyboru Uruchom z najwyższymi uprawnieniami.

6. Wybierz **kartę Wyzwalacze** , kliknij pozycję **Nowy**, a następnie wykonaj następujące czynności:

   1. W **Ustawienia** **kliknij opcję Dzienny**, a następnie wybierz datę i czas do uruchomienia skryptu po raz pierwszy. Skrypt będzie uruchamiany każdego dnia o tej samej określonej godzinie.

   2. Upewnij **się, że** w obszarze Ustawienia zaawansowane jest **zaznaczone** pole wyboru Włączone.

   3. Kliknij **przycisk OK**.

7. Wybierz **kartę Akcje** , kliknij **pozycję Nowy**, a następnie wykonaj następujące czynności:

   ![Ustawienia akcji służące do tworzenia nowego zaplanowanego zadania dla fizycznego skryptu łącznika, który zawiera już zabezpieczenia.](..\media\SchedulePhysicalBadgingScript1.png)

   1. Na liście **rozwijanej** Akcja upewnij się, że jest **wybrana opcja Uruchom** program.

   2. W **polu Program/skrypt** kliknij przycisk **Przeglądaj, przejdź** do następującej lokalizacji i wybierz ją, aby ścieżka była wyświetlana w polu: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe.

   3. W **polu Dodaj argumenty (opcjonalnie)** wklej to samo polecenie skryptu, które było uruchomiono w kroku 4. Na przykład: \PhysicalBadging.ps1-tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -jsonFilePath "C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json"

   4. W polu **Rozpocznij w (opcjonalnie)** wklej lokalizację folderu skryptu, który został uruchomiony w kroku 4. Na przykład C:\Użytkownicy\contosoadmin\Pulpit\Skrypty.

   5. Kliknij **przycisk OK** , aby zapisać ustawienia nowej akcji.

8. W **oknie Tworzenie** zadania kliknij przycisk **OK** , aby zapisać zaplanowane zadanie. Może zostać wyświetlony monit o wprowadzenie poświadczeń konta użytkownika.

   Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.

   ![Nowe zadanie zostanie wyświetlone w bibliotece harmonogramu zadań.](..\media\SchedulePhysicalBadgingScript2.png)

Zostanie wyświetlony czas ostatniego uruchomienia skryptu i następnego uruchomienia tego skryptu. Możesz kliknąć dwukrotnie zadanie, aby je edytować.

Możesz także sprawdzić czas ostatniego uruchamiania skryptu na stronie wysuwanych odpowiednich fizycznych łączników sprawdzanych w Centrum zgodności.
