---
title: 'Utwórz skrót i przekaż tabelę źródła informacji poufnych dla dokładnych typów informacji poufnych opartych na dopasowaniu danych '
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
description: Skrót i przekaż tabelę źródła informacji poufnych, aby uzyskać dokładne dane zgodne z typami informacji poufnych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dd484f10cf8dad76132ed2a68a34f87b253e76b3
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641301"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>Utwórz skrót i przekaż tabelę źródła informacji poufnych dla dokładnych typów informacji poufnych opartych na dopasowaniu danych 

W tym artykule przedstawiono sposób tworzenia skrótów i przekazywania tabeli źródła informacji poufnych.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>Skrót i przekazywanie tabeli źródła informacji poufnych

W tej fazie:

1. Konfigurowanie niestandardowej grupy zabezpieczeń i konta użytkownika
2. Konfigurowanie narzędzia EDM Upload Agent
3. Użyj narzędzia Agent przekazywania EDM, aby utworzyć skrót z wartością soli, tabelą źródła informacji poufnych i przekazać ją.

Mieszanie i przekazywanie można wykonać przy użyciu jednego komputera lub oddzielić krok skrótu od kroku przekazywania w celu zwiększenia bezpieczeństwa.

Jeśli chcesz utworzyć skrót i przekazać dane z jednego komputera, musisz to zrobić z komputera, który może bezpośrednio nawiązać połączenie z dzierżawą platformy Microsoft 365. Wymaga to, aby plik tabeli źródłowej informacji poufnych w postaci zwykłego tekstu był na tym komputerze na potrzeby tworzenia skrótów.

Jeśli nie chcesz uwidaczniać pliku tabeli źródłowej informacji poufnych w postaci zwykłego tekstu na komputerze z dostępem bezpośrednim, możesz użyć skrótu na komputerze znajdującym się w bezpiecznej lokalizacji, a następnie skopiować plik skrótu i plik soli na komputer, który może bezpośrednio połączyć się z dzierżawą usługi Microsoft 365 w celu przekazania. W scenariuszu rozdzielania skrótu i przekazywania potrzebny jest agent EDMUploadAgent na obu komputerach.

> [!IMPORTANT]
> Jeśli do utworzenia pliku schematu użyto kreatora dokładnego dopasowania danych i typów informacji poufnych, ***musisz*** pobrać schemat dla tej procedury, jeśli jeszcze tego nie zrobiono. Zobacz [Eksport pliku schematu EDM w formacie XML](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> Jeśli Twoja organizacja skonfigurowała [klucz klienta dla platformy Microsoft 365 na poziomie dzierżawy](customer-key-overview.md), dokładne dopasowanie danych automatycznie użyje jej funkcji szyfrowania. Jest to dostępne tylko dla dzierżaw licencjonowanych E5 w chmurze komercyjnej.

### <a name="best-practices"></a>Najważniejsze wskazówki

Oddziel procesy tworzenia skrótów i przekazywania poufnych danych, aby ułatwić izolowanie wszelkich problemów w tym procesie.

Po przejściu do środowiska produkcyjnego w większości przypadków należy oddzielić te dwa kroki. Wykonanie procesu tworzenia skrótów na izolowanym komputerze, a następnie przesłanie pliku do przekazania na komputer internetowy gwarantuje, że rzeczywiste dane nigdy nie będą dostępne w postaci zwykłego tekstu na komputerze, który mógł zostać naruszony z powodu połączenia z Internetem.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>Upewnij się, że poufna tabela danych nie ma problemów z formatowaniem

Przed utworzeniem skrótu i przekazaniem poufnych danych wykonaj wyszukiwanie w celu zweryfikowania obecności znaków specjalnych, które mogą powodować problemy z analizowaniem zawartości.
Możesz sprawdzić, czy tabela ma format odpowiedni do użycia z programem EDM, używając agenta przekazywania EDM z następującą składnią:

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]
```

Jeśli narzędzie wskazuje niezgodność liczby kolumn, może to być spowodowane obecnością przecinków lub znaków cudzysłowu w wartościach w tabeli, które są mylone z ogranicznikami kolumn. O ile nie otaczają one całej wartości, cudzysłowy pojedyncze i podwójne mogą powodować błędną identyfikację miejsca rozpoczęcia lub zakończenia pojedynczej kolumny.

**Jeśli znajdziesz pojedyncze lub podwójne znaki cudzysłowu otaczające pełne wartości**: możesz pozostawić je w ich postaci.

**Jeśli znajdziesz pojedyncze znaki cudzysłowu lub przecinki wewnątrz wartości**: na przykład imię osoby Tom O'Neil lub miasto 's-Gravenhage rozpoczynające się znakiem apostrofu, musisz zmodyfikować proces eksportowania danych używany do generowania poufnej tabeli informacji w celu otaczania takich kolumn podwójnymi cudzysłowami.

**Jeśli wewnątrz wartości znajdują się znaki podwójnego cudzysłowu**, lepszym rozwiązaniem może być użycie formatu rozdzielanego tabulatorem dla tabeli, który jest mniej podatny na takie problemy.

### <a name="prerequisites"></a>Wymagania wstępne

- konto służbowe platformy Microsoft 365, które zostanie dodane do grupy zabezpieczeń **EDM\_DataUploaders**
- maszyna Windows 10 lub Windows Server 2016 z platformą .NET w wersji 4.6.2 <!--4.7.2 un comment this around 9/29-->do uruchamiania EDMUploadAgent
- katalog na maszynie przekazywania dla:
  - [Agent przekazywania EDM](#links-to-edm-upload-agent-by-subscription-type)
  - plik poufnego elementu w formacie .csv, tsv lub potoku (|), **PatientRecords.csv** w naszych przykładach
  - wyjściowych plików skrótu i soli utworzonych w tej procedurze
  - nazwa magazynu danych z pliku **edm.xml** , na przykład jego `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>Konfigurowanie grupy zabezpieczeń i konta użytkownika

1. Jako administrator globalny przejdź do centrum administracyjnego przy użyciu odpowiedniego [linku dla subskrypcji](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) i [utwórz grupę zabezpieczeń](/office365/admin/email/create-edit-or-delete-a-security-group) o nazwie **EDM\_DataUploaders**.

2. Dodaj co najmniej jednego użytkownika do grupy zabezpieczeń **EDM\_DataUploaders** . (Ci użytkownicy będą zarządzać bazą danych informacji poufnych).

### <a name="hash-and-upload-from-one-computer"></a>Skrót i przekazywanie z jednego komputera

Ten komputer musi mieć bezpośredni dostęp do dzierżawy usługi Microsoft 365.

> [!NOTE]
> Przed rozpoczęciem tej procedury upewnij się, że jesteś członkiem grupy zabezpieczeń **EDM\_DataUploaders** .

> [!TIP]
>Opcjonalnie możesz uruchomić walidację pliku tabeli źródła informacji poufnych, aby sprawdzić, czy występują błędy przed przekazaniem, uruchamiając polecenie:
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> Aby uzyskać więcej informacji na temat wszystkich uruchomionych EdmUploadAgent.exe obsługiwanych parametrów
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>Linki do agenta przekazywania EDM według typu subskrypcji

- [Komercyjne i GCC](https://go.microsoft.com/fwlink/?linkid=2088639) — większość klientów komercyjnych powinna z tego korzystać
- [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) — jest to przeznaczone specjalnie dla subskrybentów chmury dla instytucji rządowych o wysokim poziomie zabezpieczeń
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) — jest to przeznaczone specjalnie dla klientów w chmurze departamentu obrony Stany Zjednoczone

1. Utwórz katalog roboczy dla EDMUploadAgent. Na przykład **C:\EDM\Data**. Umieść tam plik **PatientRecords.csv** .

2. Pobierz i zainstaluj odpowiedniego [agenta przekazywania EDM](#links-to-edm-upload-agent-by-subscription-type) dla subskrypcji do katalogu utworzonego w kroku 1.

   > [!NOTE]
   > Agent EDMUploadAgent w powyższych linkach został zaktualizowany w celu automatycznego dodania wartości soli do danych skrótu. Alternatywnie możesz podać własną wartość soli. Po użyciu tej wersji nie będzie można używać poprzedniej wersji EDMUploadAgent.
   >
   > Dane za pomocą EDMUploadAgent można przekazać do dowolnego magazynu danych tylko dwa razy dziennie.

3. Autoryzuj agenta przekazywania EDM, otwórz okno wiersza polecenia jako administrator, przejdź do katalogu **C:\EDM\Data** , a następnie uruchom następujące polecenie:

   `EdmUploadAgent.exe /Authorize`

   > [!IMPORTANT]
   > Należy uruchomić **narzędzie EdmUploadAgent** z folderu, w którym jest zainstalowany, i wskazać pełną ścieżkę do plików danych.

4. Zaloguj się przy użyciu konta służbowego platformy Microsoft 365, które zostało dodane do grupy zabezpieczeń EDM_DataUploaders. Informacje o dzierżawie są wyodrębniane z konta użytkownika w celu nawiązania połączenia.

   OPCJONALNIE: Jeśli do utworzenia schematu użyto kreatora dokładnego dopasowania danych i typów informacji poufnych, ***musisz*** go pobrać do użycia w tych procedurach, jeśli jeszcze tego nie zrobiono. Uruchom to polecenie w oknie wiersza polecenia:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. Aby utworzyć skrót i przekazać dane poufne, uruchom następujące polecenie w oknie wiersza polecenia:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```

   > [!NOTE]
   > Domyślnym formatem pliku danych poufnych są wartości rozdzielone przecinkami. Plik rozdzielony tabulatorem można określić, wskazując opcję "{Tab}" za pomocą parametru /ColumnSeparator lub można określić plik rozdzielony potokiem, wskazując opcję "|".
   >
   > Przykład: `EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5`

   Jeśli tabela informacji poufnych zawiera nieprawidłowo sformatowane wartości, ale chcesz zaimportować pozostałe dane, ignorując mimo to nieprawidłowe wiersze, możesz użyć parametru */AllowedBadLinesPercentage* w poleceniu. Powyższy przykład określa próg pięciu procent. Oznacza to, że narzędzie będzie uruchamiać skróty i przekazywać tabelę informacji poufnych, nawet jeśli maksymalnie pięć procent wierszy jest nieprawidłowych.

   To polecenie automatycznie doda losowo wygenerowaną wartość soli do skrótu w celu zwiększenia bezpieczeństwa. Opcjonalnie, jeśli chcesz użyć własnej wartości soli, dodaj **/Salt \<saltvalue\>** do polecenia . Ta wartość musi mieć długość 64 znaków i może zawierać tylko znaki a-z i od 0 do 9 znaków.

6. Sprawdź stan przekazywania, uruchamiając następujące polecenie:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   Przykład: `EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords`

   Poszukaj stanu **w obszarze ProcessingInProgress**. Sprawdzaj ponownie co kilka minut, aż stan zmieni się na **Ukończono**. Po zakończeniu stanu dane EDM są gotowe do użycia. W zależności od rozmiaru pliku tabeli źródła informacji poufnych może to potrwać od kilku minut do kilku godzin.

> [!TIP]
> Jeśli chcesz otrzymywać powiadomienia po przygotowaniu przekazanych poufnych danych do użycia, postępuj zgodnie z procedurami w [sekcji Tworzenie powiadomień, aby uzyskać dokładne działania dopasowania danych](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>Oddzielne skróty i przekazywanie

Wykonaj skrót na komputerze w bezpiecznym środowisku. Na obu komputerach musi być zainstalowany agent **EDMUploadAgent** .

OPCJONALNIE: Jeśli do utworzenia schematu użyto kreatora dokładnego dopasowania danych i typów informacji poufnych, a schemat nie został jeszcze pobrany, uruchom następujące polecenie w oknie wiersza polecenia, aby pobrać plik w formacie XML:

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
   > Domyślnym formatem pliku danych poufnych są wartości rozdzielone przecinkami. Plik rozdzielony tabulatorem można określić, wskazując opcję "{Tab}" za pomocą parametru /ColumnSeparator lub można określić plik rozdzielony potokiem, wskazując opcję "|".

   Spowoduje to wyświetlenie pliku skrótu i pliku solnego z tymi rozszerzeniami, jeśli nie określono opcji **/Salt \<saltvalue\>** :

   - . EdmHash
   - . EdmSalt

2. Skopiuj te pliki w bezpieczny sposób na komputer, którego użyjesz do przekazania pliku tabeli źródła informacji poufnych (PatientRecords) do dzierżawy.

3. Autoryzuj agenta przekazywania EDM, otwórz okno wiersza polecenia jako administrator, przejdź do katalogu **C:\EDM\Data** , a następnie uruchom następujące polecenie:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

   > [!IMPORTANT]
   > Należy uruchomić **narzędzie EdmUploadAgent** z folderu, w którym jest zainstalowany, i wskazać pełną ścieżkę do plików danych.

4. Zaloguj się przy użyciu konta służbowego platformy Microsoft 365, które zostało dodane do grupy zabezpieczeń EDM_DataUploaders. Informacje o dzierżawie są wyodrębniane z konta użytkownika w celu nawiązania połączenia.

5. Aby przekazać dane skrótu, uruchom następujące polecenie w wierszu polecenia systemu Windows:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   Przykład:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. Aby sprawdzić, czy dane poufne zostały przekazane, uruchom następujące polecenie w oknie wiersza polecenia:

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```

   Zostanie wyświetlona lista magazynów danych i czas ich ostatniej aktualizacji.

7. Jeśli chcesz wyświetlić wszystkie dane przekazane do określonego magazynu, uruchom następujące polecenie w wierszu polecenia systemu Windows, aby wyświetlić listę wszystkich magazynów danych i czasu ich aktualizacji:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```

> [!NOTE]
> Aby zautomatyzować proces skrótu i przekazywania po jego utworzeniu po raz pierwszy, zobacz [Odświeżanie dokładnego dopasowania danych do pliku tabeli źródła informacji poufnych](sit-use-exact-data-refresh-data.md).

## <a name="next-step"></a>Następny krok

- [Twórz dokładny typ/pakiet reguł informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)
