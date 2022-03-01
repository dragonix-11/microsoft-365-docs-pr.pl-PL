---
title: Skróty i przekazywanie tabeli źródła informacji poufnych w celu dokładnego dopasowania danych do typów informacji poufnych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Skróty i przekazywanie tabeli źródła informacji poufnych w celu dokładnego dopasowania danych do typów informacji poufnych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 85a65bc0d9d68a4a148fbc820985b6f40b6f6792
ms.sourcegitcommit: 8410a49995a084e4cc9b3f7286c8d506b7a85d79
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2021
ms.locfileid: "62999364"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>Skróty i przekazywanie tabeli źródła informacji poufnych w celu dokładnego dopasowania danych do typów informacji poufnych

W tym artykule pokazano, jak skrótować i przekazywać tabelę źródła informacji poufnych.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>Skróty i przekazywanie tabeli źródła informacji poufnych

W tym etapie:

1. konfigurowanie niestandardowej grupy zabezpieczeń i konta użytkownika
2. konfigurowanie narzędzia EDM Upload Agent
3. Za pomocą narzędzia EDM Upload Agent możesz za pomocą skrótu dodać wartość soli do tabeli źródła poufnych informacji i przekazać ją.

Skróty i przekazywanie można wykonać przy użyciu jednego komputera lub oddzielić krok skrótu od kroku przekazywania, aby zapewnić większe bezpieczeństwo.

Jeśli chcesz skrótować i przekazywać z jednego komputera, musisz to zrobić z komputera, który może bezpośrednio połączyć się z Twoją Microsoft 365 dzierżawy. Wymaga to, aby plik tabeli źródłowej z informacjami o poufnym tekście był na tym komputerze do skrótów.

Jeśli nie chcesz udostępnić pliku tabeli źródłowej z informacjami o poufnym tekście na komputerze z dostępem bezpośrednim, możesz go połączyć z komputerem, który znajduje się w bezpiecznym miejscu, a następnie skopiować plik skrótu i pliku soli do komputera, który może bezpośrednio połączyć się z dzierżawą usługi Microsoft 365 w celu przekazania. W scenariuszu rozdzielania skrótów i przekazywania będziesz potrzebować funkcji EDMUploadAgent na obu komputerach.

> [!IMPORTANT]
> Jeśli do utworzenia pliku schematu został użyty schemat dokładnego dopasowania danych i kreator typów informacji poufnych, musisz  pobrać schemat dla tej procedury, jeśli jeszcze tego nie zrobiono. Zobacz [Eksportowanie pliku schematu EDM w formacie XML](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> Jeśli w Twojej organizacji klucz klienta został Microsoft 365 [na](customer-key-overview.md) poziomie dzierżawy, funkcja dokładnego dopasowania danych automatycznie użyje funkcji szyfrowania. Ta usługa jest dostępna tylko dla licencjonowanych dzierżawców usługi E5 w chmurze komercyjnej.

### <a name="best-practices"></a>Najważniejsze wskazówki

Oddziel procesy skrótów i przekazywania poufnych danych, aby łatwiej wyizolować wszelkie problemy w procesie.
 
Po produkcji oddziel te dwa kroki w większości przypadków. Wykonanie procesu skrótów na odizolowanym komputerze, a następnie przeniesienie pliku w celu przekazania na komputer internetowy gwarantuje, że rzeczywiste dane nie są nigdy dostępne w postaci jednoznacznie tekstowej na komputerze, który mógł zostać naruszony ze względu na połączenie z Internetem.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>Upewnij się, że tabela danych poufnych nie ma problemów z formatowaniem. 

Przed rozpoczęciem skrótów i przekazania poufnych danych wykonaj wyszukiwanie w celu weryfikacji obecności znaków specjalnych, które mogą powodować problemy podczas analizowania zawartości. Aby sprawdzić, czy tabela jest w formacie odpowiednim do używania z usługą EDM, można użyć agenta przekazywania programu EDM z następującą składnią:

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file] 
```

Jeśli narzędzie wskazuje na niezgodność liczby kolumn, może to być spowodowane obecnością przecinków lub cudzysłowów w wartościach tabeli, które są mylone z ogranicznikami kolumn. O ile nie otaczają one całej wartości, pojedyncze i podwójne cudzysłowy mogą powodować błędne identyfikację miejsca, w którym zaczyna się lub kończy pojedyncza kolumna. 

**Jeśli znajdziesz pojedyncze lub podwójne cudzysłowy otaczające pełne wartości**: możesz zostawić je bez nich.

Jeśli w wartości znajdują się znaki cudzysłowu lub przecinki **pojedyncze:** imię i nazwisko osoby Tomasz O'Neil lub nazwa miasta 's-Gravenhage, które zaczyna się znakiem apostrofu, musisz zmodyfikować proces eksportowania danych użyty do wygenerowania tabeli informacji poufnych w taki sposób, aby takie kolumny znalazły się w podwójnych cudzysłowach.

**Jeśli wewnątrz wartości** znajdują się znaki podwójnego cudzysłowu, warto użyć formatu rozdzielanego tabulatorami dla tabeli, która jest mniej podatna na tego typu problemy.

### <a name="prerequisites"></a>Wymagania wstępne

- konto służbowe dla Microsoft 365, które zostanie dodane do **grupy zabezpieczeń EDMDataUploaders\_**
- komputer Windows 10 lub Windows Server 2016 z platformą .NET w wersji 4.6.2 <!--4.7.2 un comment this around 9/29-->do uruchamiania funkcji EDMUploadAgent
- katalog na komputerze do przekazywania dla:
  - [Agent Upload EDM](#links-to-edm-upload-agent-by-subscription-type)
  - poufnych elementów w formacie .csv, tsv lub pipeta (|) w **PatientRecords.csv** przykładach
  - Skróty wyjściowe i pliki soli utworzone w tej procedurze
  - nazwę magazynu danych z **plikuedm.xml** , na przykład jej `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>Konfigurowanie grupy zabezpieczeń i konta użytkownika

1. Jako administrator globalny przejdź do centrum administracyjnego, używając odpowiedniego [linku](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) dla swojej subskrypcji, [i](/office365/admin/email/create-edit-or-delete-a-security-group) utwórz **grupę zabezpieczeń o nazwie EDMDataUploaders\_**.

2. Dodaj co najmniej jednego użytkownika do grupy zabezpieczeń **EDMDataUploaders\_**. (Ci użytkownicy będą zarządzać bazą danych informacji poufnych).

### <a name="hash-and-upload-from-one-computer"></a>Skróty i przekazywanie z jednego komputera

Ten komputer musi mieć bezpośredni dostęp do Microsoft 365 dzierżawy.

> [!NOTE]
> Przed rozpoczęciem tej procedury upewnij się, że jesteś członkiem grupy zabezpieczeń **EDMDataUploaders\_**.

> [!TIP] 
>Opcjonalnie można uruchomić sprawdzanie poprawności dla pliku tabeli źródłowej informacji poufnych, aby sprawdzić, czy nie występują w nim błędy przed przekazaniem przez uruchomienie:
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> Aby uzyskać więcej informacji na temat EdmUploadAgent.exe obsługiwanych parametrów
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>Linki do agenta przekazywania usługi EDM według typu subskrypcji

- [Komercyjna + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) — większość klientów komercyjnych powinna używać tej
- [GCC-wysoka —](https://go.microsoft.com/fwlink/?linkid=2137521) ta rozwiązanie jest przeznaczone specjalnie dla subskrybentów chmury o wysokim poziomie zabezpieczeń
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) — jest to przeznaczone specjalnie dla klientów w chmurze Działu Obrony Stanów Zjednoczonych

1. Utwórz katalog roboczy dla usługi EDMUploadAgent. Na przykład **C:\EDM\Dane**. Umieść tam **PatientRecords.csv** pliku.

2. Pobierz i zainstaluj [odpowiedniego agenta usługi EDM Upload twojej](#links-to-edm-upload-agent-by-subscription-type) subskrypcji do katalogu utworzonego w kroku 1.

   > [!NOTE]
   > Funkcja EDMUploadAgent w powyższych linkach została zaktualizowana w celu automatycznego dodania wartości soli do skrótów danych. Można też podać własną wartość soli. Po użyciu tej wersji nie będzie można używać poprzedniej wersji programu EDMUploadAgent.
   >
   > Dane z EDMUploadAgent można przekazywać do dowolnego magazynu danych tylko dwa razy dziennie.

3. Autoryzuj agenta Upload usługi EDM, otwórz okno Wiersza polecenia jako administrator, przełącz się do katalogu **C:\EDM\Data**, a następnie uruchom następujące polecenie:

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> Należy uruchomić **folder EdmUploadAgent** z folderu, w którym jest zainstalowany, i wskazać pełną ścieżkę do plików danych. 

4. Zaloguj się za pomocą konta służbowego lub szkolnego, Microsoft 365 które zostało dodane do EDM_DataUploaders zabezpieczeń. Informacje o dzierżawie są wyodrębnione z konta użytkownika w celu nawiązaniu połączenia.

   OPCJONALNIE: Jeśli do utworzenia schematu został użyty schemat dokładnego dopasowania danych i kreatora typów informacji poufnych,  należy pobrać schemat do użycia w tych procedurach, jeśli jeszcze tego nie zrobić. Uruchom to polecenie w oknie wierszu polecenia:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. Aby skrótować i przekazać poufne dane, uruchom następujące polecenie w oknie Wiersz polecenia:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```
   > [!NOTE]
> Domyślnym formatem pliku danych poufnych są wartości rozdzielane przecinkami. Możesz określić plik rozdzielany tabulatorami, wskazując opcję "{Tab}" z parametrem /ColumnSeparator lub plik rozdzielany potokami, wskazując opcję "|".

   Przykład: **EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5**

Jeśli tabela z informacjami poufnymi ma jakieś niepoprawnie sformatowane wartości, ale chcesz zaimportować pozostałe dane, ignorując nieprawidłowe wiersze, możesz użyć *parametru /AllowedBadLinesPercentage* w poleceniu. W powyższym przykładzie określono próg pięciu procentów. Oznacza to, że narzędzie będzie skrótować i przekazać tabelę z informacjami poufnymi, nawet jeśli maksymalnie pięć procent wierszy jest nieprawidłowych. 

To polecenie automatycznie dodaje do skrótu losowo wygenerowaną wartość soli, co zapewnia większe bezpieczeństwo. Opcjonalnie, jeśli chcesz użyć własnej wartości soli, dodaj do polecenia polecenie **/Salt <saltvalue>** . Ta wartość musi mieć długość 64 znaków i może zawierać tylko znaki a-z oraz 0-9 znaków.

6. Sprawdź stan przekazywania, uruchamiając to polecenie:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   Przykład: **EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords**

   Poszukaj stanu w **przetwarzaniuInProgress**. Sprawdzaj ponownie co kilka minut, aż stan zmieni się na **Ukończone**. Po ukończeniu stanu dane funkcji nr.EM będą gotowe do użycia. W zależności od rozmiaru pliku tabeli z informacjami poufnymi może to potrwać od kilku minut do kilku godzin. 

> [!TIP]
> Jeśli chcesz otrzymywać powiadomienia, gdy przekazane poufne dane będą gotowe do użycia, wykonaj procedury w te sposób: Tworzenie powiadomień w celu dokładnego dopasowania [danych](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>Oddziel skrót i przekaż

Wykonaj skrót na komputerze w bezpiecznym środowisku. Na obu komputerach musi być zainstalowany program **EDMUploadAgent** .

OPCJONALNIE: Jeśli do utworzenia schematu został użyty kreator dokładnego dopasowania danych i kreatora typów informacji poufnych, a schemat nie został jeszcze pobrany, uruchom następujące polecenie w oknie wiersza polecenia, aby pobrać plik w formacie XML:

```dos
EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
````

1. Na komputerze w bezpiecznym środowisku uruchom następujące polecenie w oknach wiersza polecenia:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /AllowedBadLinesPercentage [value]
   ```

   Przykład:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5
   ```

> [!NOTE]
> Domyślnym formatem pliku danych poufnych są wartości rozdzielane przecinkami. Możesz określić plik rozdzielany tabulatorami, wskazując opcję "{Tab}" z parametrem /ColumnSeparator lub plik rozdzielany potokami, wskazując opcję "|".


   Spowoduje to wyprowadzenie pliku skrótu i pliku soli z tymi rozszerzeniami, jeśli nie określono opcji **/Salt <saltvalue>** :

   - . EdmHash
   - . EdmSalt


2. Skopiuj te pliki w bezpieczny sposób do komputera, na który chcesz przekazać plik tabeli źródłowej poufnych informacji (PatientRecords) do dzierżawy.

3. Autoryzuj agenta Upload usługi EDM, otwórz okno Wiersza polecenia jako administrator, przełącz się do katalogu **C:\EDM\Data**, a następnie uruchom następujące polecenie:

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> Należy uruchomić **folder EdmUploadAgent** z folderu, w którym jest zainstalowany, i wskazać pełną ścieżkę do plików danych. 

4. Zaloguj się za pomocą konta służbowego lub szkolnego, Microsoft 365 które zostało dodane do EDM_DataUploaders zabezpieczeń. Informacje o dzierżawie są wyodrębnione z konta użytkownika w celu nawiązaniu połączenia.

5. Aby przekazać skróty danych, uruchom następujące polecenie w wierszu Windows polecenia:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   Przykład:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. Aby sprawdzić, czy poufne dane zostały przekazane, uruchom następujące polecenie w oknie Wiersz polecenia:

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```
   Zostanie wyświetlona lista magazynów danych oraz data ich ostatniej aktualizacji.

7. Jeśli chcesz wyświetlić wszystkie dane przesłane do określonego magazynu, uruchom następujące polecenie w wierszu polecenia aplikacji Windows, aby wyświetlić listę wszystkich magazynów danych oraz informacje o tym, kiedy zostały zaktualizowane:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```
     
## <a name="next-step"></a>Następny krok

- [Tworzenie dokładnego dopasowania danych do typów informacji poufnych/pakietu reguł](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)

