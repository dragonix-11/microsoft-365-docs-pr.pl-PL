---
title: Użyj przekazywania sieciowego w celu importu plików PST
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 103f940c-0468-4e1a-b527-cc8ad13a5ea6
description: 'Dla administratorów: dowiedz się, jak używać przekazywania sieci do zbiorczego importowania wielu plików PST do skrzynek pocztowych użytkowników w Microsoft 365.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8d63b83f8052fdd3ce973bba15df72ee4c7d6989
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935440"
---
# <a name="use-network-upload-to-import-your-organizations-pst-files-to-microsoft-365"></a>Importowanie plików PST organizacji do Microsoft 365 przy użyciu przekazywania sieci

> [!NOTE]
> Ten artykuł jest przeznaczony dla administratorów. Czy próbujesz zaimportować pliki PST do własnej skrzynki pocztowej? Zobacz [Importowanie wiadomości e-mail, kontaktów i kalendarza z pliku pst Outlook](https://go.microsoft.com/fwlink/p/?LinkID=785075)
  
Poniżej przedstawiono instrukcje krok po kroku wymagane do użycia przekazywania sieci do zbiorczego importowania wielu plików PST do Microsoft 365 skrzynek pocztowych. Aby uzyskać często zadawane pytania dotyczące używania przekazywania sieci do zbiorczego importowania plików PST do Microsoft 365 skrzynek pocztowych, zobacz [Często zadawane pytania dotyczące używania przekazywania sieci do importowania plików PST](./faqimporting-pst-files-to-office-365.yml#using-network-upload-to-import-pst-files).
  
[Krok 1. Skopiuj adres URL sygnatury dostępu współdzielonego i pobierz narzędzie AzCopy](#step-1-copy-the-sas-url-and-download-azcopy)

[Krok 2. Upload pliki PST do Microsoft 365](#step-2-upload-your-pst-files-to-microsoft-365)

[(Opcjonalnie) Krok 3. Wyświetlanie listy przekazanych plików PST](#optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365)

[Krok 4. Tworzenie pliku mapowania importu PST](#step-4-create-the-pst-import-mapping-file)

[Krok 5. Tworzenie zadania importowania PST](#step-5-create-a-pst-import-job)

[Krok 6. Filtrowanie danych i uruchamianie zadania importowania PST](#step-6-filter-data-and-start-the-pst-import-job)

Aby zaimportować pliki PST do Microsoft 365 skrzynek pocztowych, należy wykonać krok 1 tylko raz. Po wykonaniu tych kroków wykonaj kroki od kroku 2 do kroku 6 za każdym razem, gdy chcesz przekazać i zaimportować partię plików PST.

## <a name="before-you-import-pst-files"></a>Przed zaimportowaniem plików PST
  
- Musisz mieć przypisaną rolę eksportu importu skrzynki pocztowej w Exchange Online, aby utworzyć zadania importu w portalu zgodności usługi Microsoft Purview i zaimportować pliki PST do skrzynek pocztowych użytkowników. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę Import eksportu skrzynki pocztowej można dodać do grupy ról Zarządzanie organizacją. Możesz też utworzyć grupę ról, przypisać rolę Importuj eksport skrzynki pocztowej, a następnie dodać siebie jako członka. Aby uzyskać więcej informacji, zobacz sekcje "Dodawanie roli do grupy ról" lub "Tworzenie grupy ról" w sekcji [Zarządzanie grupami ról](/Exchange/permissions-exo/role-groups).

    Oprócz roli Importuj eksport skrzynki pocztowej musisz również mieć przypisaną rolę Adresaci poczty w Exchange Online. Domyślnie ta rola jest przypisywana do grup ról Zarządzanie organizacjami i Zarządzanie adresatami w Exchange Online.

    > [!TIP]
    > Rozważ utworzenie nowej grupy ról w Exchange Online, która jest przeznaczona specjalnie do importowania plików PST. Aby uzyskać minimalny poziom uprawnień wymaganych do importowania plików PST, przypisz role Eksportuj i Adresaci poczty skrzynki pocztowej do nowej grupy ról, a następnie dodaj członków.
  
- Jedyną obsługiwaną metodą importowania plików PST do Microsoft 365 jest użycie narzędzia AzCopy zgodnie z opisem w tym artykule. Nie można użyć Eksplorator usługi Azure Storage do przekazywania plików PST bezpośrednio do obszaru usługi Azure Storage.

- Duże pliki PST mogą mieć wpływ na wydajność procesu importowania PST. Dlatego zalecamy, aby każdy plik PST przekazany do lokalizacji Storage platformy Azure w kroku 2 nie był większy niż 20 GB.

- Ta procedura obejmuje kopiowanie i zapisywanie kopii adresu URL zawierającego klucz dostępu. Te informacje zostaną użyte w kroku 2 do przekazania plików PST i w kroku 3, jeśli chcesz wyświetlić listę plików PST przekazanych do Microsoft 365. Pamiętaj, aby podjąć środki ostrożności, aby chronić ten adres URL, tak jak w przypadku ochrony haseł lub innych informacji związanych z zabezpieczeniami. Możesz na przykład zapisać go w dokumencie Microsoft Word chronionym hasłem lub na zaszyfrowanym dysku USB. Zobacz sekcję [Więcej informacji](#more-information) , aby zapoznać się z przykładem tego połączonego adresu URL i klucza.

- Pliki PST można zaimportować do nieaktywnej skrzynki pocztowej w Microsoft 365. W tym celu należy określić identyfikator GUID nieaktywnej skrzynki pocztowej w parametrze  `Mailbox` w pliku mapowania importu PST. Aby uzyskać informacje, zobacz Krok 4 na **karcie Instrukcje** w tym artykule.

- W Exchange wdrożenia hybrydowego można zaimportować pliki PST do chmurowej skrzynki pocztowej archiwum dla użytkownika, którego podstawowa skrzynka pocztowa jest lokalna. Można to zrobić, wykonując następujące czynności w pliku mapowania importu PST:

  - W parametrze określ adres e-mail lokalnej skrzynki pocztowej  `Mailbox` użytkownika.

  - Określ wartość **TRUE** w parametrze  `IsArchive` .

    Aby uzyskać więcej informacji [, zobacz Krok 4](#step-4-create-the-pst-import-mapping-file) .

- Po zaimportowaniu plików PST ustawienie przechowywania dla skrzynki pocztowej jest włączone przez czas nieokreślony. Oznacza to, że zasady przechowywania przypisane do skrzynki pocztowej nie zostaną przetworzone, dopóki nie wyłączysz blokady przechowywania lub nie ustawisz daty wyłączenia blokady. Dlaczego to robimy? Jeśli wiadomości zaimportowane do skrzynki pocztowej są stare, mogą zostać trwale usunięte (przeczyszczane), ponieważ ich okres przechowywania wygasł na podstawie ustawień przechowywania skonfigurowanych dla skrzynki pocztowej. Umieszczenie skrzynki pocztowej w blokadzie przechowywania daje właścicielowi skrzynki pocztowej czas na zarządzanie tymi nowo zaimportowanymi wiadomościami lub daje czas na zmianę ustawień przechowywania skrzynki pocztowej. Zobacz sekcję [Więcej informacji](#more-information) w tym artykule, aby uzyskać sugestie dotyczące zarządzania blokadą przechowywania.

- Domyślnie maksymalny rozmiar wiadomości, który może zostać odebrany przez skrzynkę pocztową Microsoft 365, wynosi 35 MB. Dzieje się tak, ponieważ wartość domyślna właściwości  *MaxReceiveSize*  dla skrzynki pocztowej jest ustawiona na 35 MB. Jednak limit maksymalnego rozmiaru odbierania komunikatów w Microsoft 365 wynosi 150 MB. Jeśli więc zaimportujesz plik PST zawierający element o rozmiarze większym niż 35 MB, usługa Microsoft 365 Import automatycznie zmieni wartość właściwości *MaxReceiveSize* w docelowej skrzynce pocztowej na 150 MB. Dzięki temu do skrzynek pocztowych użytkowników można importować wiadomości o rozmiarze do 150 MB.

    > [!TIP]
    > Aby zidentyfikować rozmiar odbierania wiadomości dla skrzynki pocztowej, możesz uruchomić to polecenie w programie Exchange Online programu PowerShell: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`.

- Aby zapoznać się z ogólnym omówieniem procesu importowania PST, zobacz [sekcję Jak działa proces importowania](#how-the-import-process-works) w tym artykule.

## <a name="step-1-copy-the-sas-url-and-download-azcopy"></a>Krok 1. Skopiuj adres URL sygnatury dostępu współdzielonego i pobierz narzędzie AzCopy

Pierwszym krokiem jest pobranie narzędzia AzCopy, czyli narzędzia uruchomionego w kroku 2 w celu przekazania plików PST do Microsoft 365. Skopiuj również adres URL sygnatury dostępu współdzielonego dla swojej organizacji. Ten adres URL jest kombinacją adresu URL sieci dla lokalizacji Storage platformy Azure w chmurze firmy Microsoft dla Organizacji i klucza sygnatury dostępu współdzielonego (SAS). Ten klucz zapewnia uprawnienia niezbędne do przekazywania plików PST do lokalizacji Storage platformy Azure. Pamiętaj, aby podjąć środki ostrożności w celu ochrony adresu URL sygnatury dostępu współdzielonego. Jest unikatowa dla Twojej organizacji i będzie używana w kroku 2.

> [!IMPORTANT]
> Aby zaimportować pliki PST przy użyciu metody przekazywania sieci i składni poleceń udokumentowanej w tym artykule, należy użyć wersji narzędzia AzCopy, którą można pobrać w kroku 6b w poniższej procedurze. Możesz również pobrać tę samą wersję narzędzia AzCopy [tutaj.](https://aka.ms/downloadazcopylatest) Używanie innej wersji narzędzia AzCopy nie jest obsługiwane.
  
1. Przejdź do strony <https://compliance.microsoft.com> i zaloguj się przy użyciu poświadczeń konta administratora w organizacji.

2. W lewym okienku portalu zgodności kliknij pozycję **Importowanie** **ładu** \> informacji.

    > [!NOTE]
    > Musisz mieć przypisane odpowiednie uprawnienia, aby uzyskać dostęp do strony **Importuj** w portalu zgodności. Aby uzyskać więcej informacji, zobacz sekcję **Przed rozpoczęciem** . 

3. Na karcie **Import** kliknij pozycję Dodaj ikonę ![.](../media/ITPro-EAC-AddIcon.gif) **Nowe zadanie importu**.

    Zostanie wyświetlony kreator zadań importowania.

4. Wpisz nazwę zadania importu PST, a następnie kliknij przycisk **Dalej**. Użyj małych liter, cyfr, łączników i podkreślenia. Nie można używać wielkich liter ani dołączać spacji w nazwie.

5. Na stronie **Czy chcesz przekazać lub wysłać dane?** kliknij **Upload dane**, a następnie kliknij przycisk **Dalej**.

    ![Kliknij Upload danych, aby utworzyć zadanie importowania przekazywania sieci.](../media/e59f9dc3-ccde-44ff-ac38-c4e39d76ae85.png)
  
6. Na stronie **Importowanie danych** wykonaj następujące dwie czynności:

    ![Skopiuj adres URL sygnatury dostępu współdzielonego i pobierz narzędzie AzCopy na stronie Importuj dane.](../media/74411014-ec4b-4e25-9065-404c934cce17.png)
  
    1. W kroku 2 kliknij pozycję **Pokaż adres URL sygnatury dostępu współdzielonego przekazywania sieci**. Po wyświetleniu adresu URL sygnatury dostępu współdzielonego kliknij pozycję **Kopiuj do schowka** , a następnie wklej go i zapisz w pliku, aby uzyskać do niego dostęp później.

    2. W kroku 3 kliknij pozycję **Pobierz narzędzie Azure AzCopy** , aby pobrać narzędzie AzCopy na komputer lokalny. Ta wersja narzędzia AzCopy jest tylko plikiem wykonywalnym, więc nie ma nic do zainstalowania.

   > [!NOTE]
   > Możesz pozostawić otwartą stronę **Importuj dane** (na wypadek potrzeby ponownego skopiowania adresu URL sygnatury dostępu współdzielonego) lub kliknąć przycisk **Anuluj** , aby go zamknąć.

## <a name="step-2-upload-your-pst-files-to-microsoft-365"></a>Krok 2. Upload pliki PST do Microsoft 365

Teraz możesz przystąpić do przekazywania plików PST do Microsoft 365 za pomocą narzędzia AzCopy. To narzędzie przekazuje i przechowuje pliki PST w lokalizacji Storage platformy Azure udostępnionej przez firmę Microsoft w chmurze firmy Microsoft. Jak wyjaśniono wcześniej, lokalizacja usługi Azure Storage, do której przekazujesz pliki PST, znajduje się w tym samym regionalnym centrum danych firmy Microsoft, w którym znajduje się Twoja organizacja. Aby wykonać ten krok, pliki PST muszą znajdować się w udziale plików lub serwerze plików w organizacji lub w lokalizacji Storage platformy Azure zarządzanej przez organizację. Lokalizacja magazynu PST jest znana jako lokalizacja źródłowa w tej procedurze. Za każdym razem, gdy uruchamiasz narzędzie AzCopy, możesz określić inną lokalizację źródłową.

> [!NOTE]
> Jak wspomniano wcześniej, każdy plik PST przekazany do lokalizacji Storage platformy Azure nie powinien być większy niż 20 GB. Pliki PST większe niż 20 GB mogą mieć wpływ na wydajność procesu importowania PST rozpoczętego w kroku 6. Ponadto każdy plik PST musi mieć unikatową nazwę.

1. Otwórz wiersz polecenia na komputerze lokalnym.

2. Przejdź do katalogu, w którym pobrano plik azcopy.exe w kroku 1.

3. Uruchom następujące polecenie, aby przekazać pliki PST do Microsoft 365.

    ```powershell
    azcopy.exe copy "<Source location of PST files>" "<SAS URL>"
    ```

    > [!IMPORTANT]
    > W poprzednim poleceniu można określić katalog lub lokalizację usługi Azure Storage jako lokalizację źródłową. Nie można określić pojedynczego pliku PST. Wszystkie pliki PST w lokalizacji źródłowej zostaną przekazane.

    W poniższej tabeli opisano pola azcopy.exe i ich wymagane wartości. Informacje uzyskane w poprzednim kroku są używane w wartościach dla tych pól.

    | Pole | Opis |
    |:-----|:-----|
    | Źródło |Pierwsze pole określa katalog źródłowy w organizacji zawierający pliki PST, które zostaną przekazane do Microsoft 365. Alternatywnie możesz określić lokalizację Storage platformy Azure jako lokalizację źródłową plików PST do przekazania. <br/> Pamiętaj, aby otoczyć wartość tego pola podwójnym cudzysłowem (" ").  <br/> <br/>**Przykłady**: <br/>`"\\FILESERVER01\PSTs"` <br/> Lub  <br/>`"https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx"`|  
    | Destination (Miejsce docelowe) |Określa adres URL sygnatury dostępu współdzielonego uzyskany w kroku 1.  <br/> Pamiętaj, aby otoczyć wartość tego parametru podwójnym cudzysłowem (" ").<br/><br/>**Uwaga:** Jeśli używasz adresu URL sygnatury dostępu współdzielonego w skryptze lub pliku wsadowym, zwróć uwagę na niektóre znaki, które muszą zostać uciekły. Na przykład musisz zmienić `%` wartość na `%%` i zmienić `&` na `^&`.<br/><br/>**Porada:** (Opcjonalnie) Możesz określić podfolder w lokalizacji Storage platformy Azure, do którą mają zostać przekazane pliki PST. Można to zrobić, dodając lokalizację podfolderu (po "ingestiondata") w adresie URL sygnatury dostępu współdzielonego. Pierwszy przykład nie określa podfolderu. Oznacza to, że usługi PST są przekazywane do katalogu głównego (o nazwie *ingestiondata*) lokalizacji Storage platformy Azure. Drugi przykład przekazuje pliki PST do podfolderu (o nazwie *PSTFiles*) w katalogu głównym lokalizacji usługi Azure Storage.  <br/><br/>**Przykłady**: <br/> `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> Lub  <br/>  `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata/PSTFiles?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> |
    | `--recursive` |Ta opcjonalna flaga określa tryb cykliczny, dzięki czemu narzędzie AzCopy kopiuje pliki PSTs znajdujące się w podfolderach w katalogu źródłowym określonym przez pole źródłowe. Wartość domyślna tej flagi to `true`. <br/>**Uwaga:** Jeśli uwzględnisz tę flagę, pliki PST w podfolderach będą miały inną nazwę ścieżki pliku w lokalizacji Storage platformy Azure po ich przekazaniu. Musisz określić dokładną nazwę ścieżki pliku w pliku CSV utworzonym w kroku 4.|
    | `--s2s-preserve-access-tier` | Ta opcjonalna flaga jest wymagana tylko wtedy, gdy lokalizacja źródłowa jest lokalizacją ogólnego przeznaczenia w wersji 2 azure Storage, która obsługuje warstwy dostępu. W przypadku scenariusza importowania PST nie trzeba zachowywać warstwy dostępu podczas kopiowania plików PST z konta usługi Azure Storage do lokalizacji Storage platformy Azure udostępnionej przez firmę Microsoft. W takim przypadku możesz dołączyć tę flagę i użyć wartości `false`. Nie musisz używać tej flagi podczas kopiowania plików PST z klasycznego konta usługi Azure Storage, które nie obsługuje warstw dostępu.|
   |||

Aby uzyskać więcej informacji na temat **poleceniaazcopy.exe copy** , zobacz [azcopy copy (Kopiuj narzędzia azcopy](/azure/storage/common/storage-ref-azcopy-copy)).

Poniżej przedstawiono przykłady składni narzędzia AzCopy przy użyciu rzeczywistych wartości dla każdego parametru.

### <a name="example-1"></a>Przykład 1

Jest to przykład katalogu źródłowego znajdującego się na serwerze plików lub komputerze lokalnym.

```powershell
azcopy.exe copy "\\FILESERVER1\PSTs" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"
```

### <a name="example-2"></a>Przykład 2

Jest to przykład katalogu źródłowego znajdującego się na klasycznym koncie Storage platformy Azure z podkatalogami.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --recursive
```

### <a name="example-3"></a>Przykład 3

Jest to przykład katalogu źródłowego znajdującego się na koncie usługi Azure Storage ogólnego przeznaczenia w wersji 2. Warstwy dostępu nie są zachowywane po przekazaniu plików PST.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --s2s-preserve-access-tier=false
```

Po uruchomieniu polecenia są wyświetlane komunikaty o stanie, które pokazują postęp przekazywania plików PST. Końcowy komunikat o stanie pokazuje całkowitą liczbę plików, które zostały pomyślnie przekazane.

> [!TIP]
> Po pomyślnym uruchomieniu **poleceniaazcopy.exe copy** i sprawdzeniu, czy wszystkie parametry są poprawne, zapisz kopię składni wiersza polecenia w tym samym (zabezpieczonym) pliku, w którym skopiowano informacje uzyskane w kroku 1. Następnie możesz skopiować i wkleić to polecenie w wierszu polecenia za każdym razem, gdy chcesz uruchomić narzędzie AzCopy, aby przekazać pliki PST do Microsoft 365. Jedyną wartością, którą można zmienić, jest pole źródłowe. Zależy to od katalogu źródłowego, w którym znajdują się pliki PST.

## <a name="optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>(Opcjonalnie) Krok 3. Wyświetlanie listy plików PST przekazanych do Microsoft 365

Opcjonalnie możesz zainstalować i użyć Eksplorator usługi Microsoft Azure Storage (czyli bezpłatnego narzędzia typu open source), aby wyświetlić listę plików PST przekazanych do obiektu blob platformy Azure. Istnieją dwa dobre powody, aby to zrobić:
  
- Sprawdź, czy pliki PST z folderu udostępnionego lub serwera plików w organizacji zostały pomyślnie przekazane do obiektu blob platformy Azure.

- Sprawdź nazwę pliku (i nazwę ścieżki podfolderu, jeśli została uwzględniona) dla każdego pliku PST przekazanego do obiektu blob platformy Azure. Jest to przydatne podczas tworzenia pliku mapowania PST w następnym kroku, ponieważ musisz określić zarówno nazwę ścieżki folderu, jak i nazwę pliku dla każdego pliku PST. Zweryfikowanie tych nazw może pomóc zmniejszyć potencjalne błędy w pliku mapowania PST.

Aplikacja autonomiczna Eksplorator usługi Azure Storage jest ogólnie dostępna. Najnowszą wersję można pobrać, korzystając z linku w poniższej procedurze.
  
> [!IMPORTANT]
> Nie można użyć Eksplorator usługi Azure Storage do przekazywania ani modyfikowania plików PST. Jedyną obsługiwaną metodą importowania plików PST jest użycie narzędzia AzCopy. Ponadto nie można usunąć plików PST przekazanych do obiektu blob platformy Azure. Jeśli spróbujesz usunąć plik PST, zostanie wyświetlony błąd dotyczący braku wymaganych uprawnień. Pamiętaj, że wszystkie pliki PST są automatycznie usuwane z obszaru magazynu platformy Azure. Jeśli nie są w toku żadne zadania importu, wszystkie pliki PST w kontenerze **ingestiondata** zostaną usunięte 30 dni po utworzeniu ostatniego zadania importu.
  
Aby zainstalować Eksplorator usługi Azure Storage i nawiązać połączenie z obszarem usługi Azure Storage:
  
1. Pobierz i zainstaluj [narzędzie Eksplorator usługi Microsoft Azure Storage](https://go.microsoft.com/fwlink/p/?LinkId=544842).

2. Uruchom Eksplorator usługi Microsoft Azure Storage.

3. Na stronie **Wybieranie zasobu** w oknie dialogowym **Połączenie do usługi Azure Storage** kliknij pozycję **Kontener obiektów blob**.
  
4. Na stronie **Wybieranie metody uwierzytelniania** wybierz opcję **Sygnatura dostępu współdzielonego (SAS** ), a następnie kliknij przycisk **Dalej**.

5. Na stronie **Wprowadź informacje o połączeniu** wklej adres URL sygnatury dostępu współdzielonego uzyskany w kroku 1 w polu **Adres URL sygnatury dostępu współdzielonego kontenera obiektów blob**, a następnie kliknij przycisk **Dalej**. Po wklejeniu adresu URL sygnatury dostępu współdzielonego pole w obszarze **Nazwa wyświetlana** jest automatycznie wypełniane przy **użyciu danych pozyskiwania**.

6. Na stronie **Podsumowanie** możesz przejrzeć informacje o połączeniu, a następnie kliknąć **pozycję Połączenie**.

    Kontener **ingestiondata** jest otwarty. Zawiera pliki PST przekazane w kroku 2. Kontener **ingestiondata** znajduje się w obszarze **kontenerów obiektów blob** **kont** \> Storage **(dołączonych kontenerów**\>). 
  
7. Po zakończeniu korzystania z Eksplorator usługi Microsoft Azure Storage kliknij prawym przyciskiem myszy pozycję **ingestiondata**, a następnie kliknij przycisk **Odłącz**, aby odłączyć się od obszaru usługi Azure Storage. W przeciwnym razie podczas następnej próby dołączenia zostanie wyświetlony błąd.
  
## <a name="step-4-create-the-pst-import-mapping-file"></a>Krok 4. Tworzenie pliku mapowania importu PST

Po przekazaniu plików PST do lokalizacji usługi Azure Storage organizacji następnym krokiem jest utworzenie pliku wartości rozdzielanej przecinkami (CSV), który określa, do których skrzynek pocztowych użytkowników zostaną zaimportowane pliki PST. Ten plik CSV zostanie przesłany w następnym kroku podczas tworzenia zadania importu PST.
  
1. [Pobierz kopię pliku mapowania importu PST](https://go.microsoft.com/fwlink/p/?LinkId=544717).

2. Otwórz lub zapisz plik CSV na komputerze lokalnym. W poniższym przykładzie przedstawiono ukończony plik mapowania importu PST (otwarty w Notatniku). Znacznie łatwiej jest użyć Microsoft Excel do edytowania pliku CSV.

    ```console
    Workload,FilePath,Name,Mailbox,IsArchive,TargetRootFolder,ContentCodePage,SPFileContainer,SPManifestContainer,SPSiteUrl
    Exchange,,annb.pst,annb@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,annb_archive.pst,annb@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,,donh.pst,donh@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,donh_archive.pst,donh@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,PSTFiles,pilarp.pst,pilarp@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,PSTFiles,pilarp_archive.pst,pilarp@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,PSTFiles,tonyk.pst,tonyk@contoso.onmicrosoft.com,FALSE,,,,,
    Exchange,PSTFiles,tonyk_archive.pst,tonyk@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,PSTFiles,zrinkam.pst,zrinkam@contoso.onmicrosoft.com,FALSE,,,,,
    Exchange,PSTFiles,zrinkam_archive.pst,zrinkam@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    ```

    Pierwszy wiersz lub wiersz nagłówka pliku CSV zawiera listę parametrów, które będą używane przez usługę importu PST do importowania plików PST do skrzynek pocztowych użytkownika. Każda nazwa parametru jest oddzielona przecinkiem. Każdy wiersz w wierszu nagłówka reprezentuje wartości parametrów importowania pliku PST do określonej skrzynki pocztowej. Dla każdego pliku PST, który chcesz zaimportować do skrzynki pocztowej użytkownika, potrzebny jest wiersz. W pliku mapowania woluminów CSV może znajdować się maksymalnie 500 wierszy. Aby zaimportować ponad 500 plików PST, należy utworzyć wiele plików mapowania i utworzyć wiele zadań importu w kroku 5.

    > [!NOTE]
    > Nie zmieniaj niczego w wierszu nagłówka, w tym parametrów SharePoint; zostaną one zignorowane podczas procesu importowania PST. Pamiętaj również, aby zastąpić dane symboli zastępczych w pliku mapowania rzeczywistymi danymi.

3. Użyj informacji w poniższej tabeli, aby wypełnić plik CSV wymaganymi informacjami.

    | Parametr | Opis | Przykład |
    |:-----|:-----|:-----|
    | `Workload` <br/> |Określa usługę, do którą zostaną zaimportowane dane. Aby zaimportować pliki PST do skrzynek pocztowych użytkownika, użyj polecenia  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> |Określa lokalizację folderu w lokalizacji Storage platformy Azure, do których przekazano pliki PST w kroku 2.  <br/> Jeśli opcjonalna nazwa podfolderu nie została podfolderem w adresie URL sygnatury dostępu współdzielonego  `/Dest:` w parametrze w kroku 2, pozostaw ten parametr pusty w pliku CSV. Jeśli dołączono nazwę podfolderu, określ ją w tym parametrze (zobacz drugi przykład). Wartość tego parametru uwzględnia wielkość liter.  <br/> Tak czy inaczej,  *nie*  uwzględniaj wartości "ingestiondata" w wartości parametru  `FilePath` .  <br/><br/> **Ważne:** W przypadku nazwy ścieżki pliku musi być taka sama jak w przypadku, gdy w polu docelowym w kroku 2 dołączono opcjonalną nazwę podfolderu w adresie URL sygnatury dostępu współdzielonego. Jeśli na przykład użyto  `PSTFiles` nazwy podfolderu w kroku 2, a następnie użyto  `pstfiles` parametru  `FilePath` w pliku CSV, importowanie pliku PST zakończy się niepowodzeniem. Pamiętaj, aby używać tego samego przypadku w obu wystąpieniach.  <br/> |(pozostaw puste)  <br/> Lub  <br/>  `PSTFiles` <br/> |
    | `Name` <br/> |Określa nazwę pliku PST, który zostanie zaimportowany do skrzynki pocztowej użytkownika. Wartość tego parametru uwzględnia wielkość liter. Nazwa pliku każdego pliku PST w pliku mapowania zadania importu musi być unikatowa. <br/> <br/>**Ważne:** W przypadku nazwy pliku PST w pliku CSV musi być taka sama jak plik PST, który został przekazany do lokalizacji usługi Azure Storage w kroku 2. Jeśli na przykład używasz  `annb.pst` parametru  `Name` w pliku CSV, ale nazwa rzeczywistego pliku PST to `AnnB.pst`, importowanie tego pliku PST zakończy się niepowodzeniem. Upewnij się, że nazwa PST w pliku CSV używa tego samego przypadku co rzeczywisty plik PST.  <br/> | `annb.pst` <br/> |
    | `Mailbox` <br/> |Określa adres e-mail skrzynki pocztowej, do którą zostanie zaimportowany plik PST. Nie można określić folderu publicznego, ponieważ usługa importowania PST nie obsługuje importowania plików PST do folderów publicznych.  <br/> Aby zaimportować plik PST do nieaktywnej skrzynki pocztowej, należy określić identyfikator GUID skrzynki pocztowej dla tego parametru. Aby uzyskać ten identyfikator GUID, uruchom następujące polecenie programu PowerShell w Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> <br/>**Uwaga:** Czasami możesz mieć wiele skrzynek pocztowych o tym samym adresie e-mail, gdzie jedna skrzynka pocztowa jest aktywną skrzynką pocztową, a druga jest w stanie nietrwałym (lub nieaktywnym). W takich sytuacjach należy określić identyfikator GUID skrzynki pocztowej, aby jednoznacznie zidentyfikować skrzynkę pocztową, do której ma zostać zaimportowany plik PST. Aby uzyskać ten identyfikator GUID dla aktywnych skrzynek pocztowych, uruchom następujące polecenie programu PowerShell:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Aby uzyskać identyfikator GUID dla nietrwałych (lub nieaktywnych) skrzynek pocztowych, uruchom to polecenie  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.  <br/> | `annb@contoso.onmicrosoft.com` <br/> Lub  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Określa, czy zaimportować plik PST do skrzynki pocztowej archiwum użytkownika. Dostępne są dwie opcje:  <br/><br/>**FALSE:** Importuje plik PST do podstawowej skrzynki pocztowej użytkownika.  <br/> **TRUE:** Importuje plik PST do archiwum skrzynki pocztowej użytkownika. Przyjęto założenie, że [skrzynka pocztowa archiwum użytkownika jest włączona](enable-archive-mailboxes.md). <br/><br/>Jeśli ten parametr zostanie ustawiony na  `TRUE` wartość , a skrzynka pocztowa archiwum użytkownika nie zostanie włączona, importowanie tego użytkownika zakończy się niepowodzeniem. Jeśli importowanie jednego użytkownika zakończy się niepowodzeniem (ponieważ jego archiwum nie jest włączone i ta właściwość jest ustawiona na  `TRUE`), nie będzie to miało wpływu na innych użytkowników w zadaniu importu.  <br/>  Jeśli ten parametr pozostanie pusty, plik PST zostanie zaimportowany do podstawowej skrzynki pocztowej użytkownika.  <br/> <br/>**Uwaga:** Aby zaimportować plik PST do skrzynki pocztowej archiwum opartej na chmurze dla użytkownika, którego podstawowa skrzynka pocztowa jest lokalna, wystarczy określić  `TRUE` ten parametr i określić adres e-mail lokalnej skrzynki pocztowej użytkownika dla parametru  `Mailbox` .  <br/> | `FALSE` <br/> Lub  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Określa folder skrzynki pocztowej, do których jest importowany plik PST.  <br/> <br/> Jeśli ten parametr pozostanie pusty, plik PST zostanie zaimportowany do nowego folderu o nazwie **Importowane** na poziomie głównym skrzynki pocztowej (na tym samym poziomie co folder Skrzynka odbiorcza i inne domyślne foldery skrzynki pocztowej).  <br/> <br/> Jeśli określisz  `/`, foldery i elementy w pliku PST zostaną zaimportowane na szczyt struktury folderów w docelowej skrzynce pocztowej lub archiwum. Jeśli folder istnieje w docelowej skrzynce pocztowej (na przykład foldery domyślne, takie jak Skrzynka odbiorcza, Elementy wysłane i Elementy usunięte), elementy w tym folderze w PST są scalane z istniejącym folderem w docelowej skrzynce pocztowej. Jeśli na przykład plik PST zawiera folder Skrzynka odbiorcza, elementy w tym folderze są importowane do folderu Skrzynka odbiorcza w docelowej skrzynce pocztowej. Nowe foldery są tworzone, jeśli nie istnieją w strukturze folderów docelowej skrzynki pocztowej.  <br/><br/>  Jeśli określisz  `/<foldername>`elementy i foldery w pliku PST, zostaną zaimportowane do folderu o nazwie  *\<foldername\>*  . Jeśli na przykład używasz programu  `/ImportedPst`, elementy zostaną zaimportowane do folderu o nazwie **ImportedPst**. Ten folder będzie znajdować się w skrzynce pocztowej użytkownika na tym samym poziomie co folder Skrzynka odbiorcza.  <br/><br/> **Wskazówka:** Rozważ uruchomienie kilku partii testowych, aby poeksperymentować z tym parametrem, aby określić najlepszą lokalizację folderu do zaimportowania plików PSTs.  <br/> |(pozostaw puste)  <br/> Lub  <br/>  `/` <br/> Lub  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Ten opcjonalny parametr określa wartość liczbową strony kodowej, która ma być używana do importowania plików PST w formacie pliku ANSI. Ten parametr jest używany do importowania plików PST z organizacji chińskich, japońskich i koreańskich (CJK), ponieważ te języki zwykle używają zestawu znaków dwubajtowych (DBCS) do kodowania znaków. Jeśli ten parametr nie jest używany do importowania plików PST dla języków korzystających z usługi DBCS dla nazw folderów skrzynki pocztowej, nazwy folderów są często zniekształcone po ich zaimportowaniu.  <br/><br/> Aby uzyskać listę obsługiwanych wartości do użycia dla tego parametru, zobacz [Identyfikatory strony kodowej](/windows/win32/intl/code-page-identifiers).  <br/> <br/>**Uwaga:** Jak wspomniano wcześniej, jest to parametr opcjonalny i nie trzeba go dołączać do pliku CSV. Możesz też dołączyć ją i pozostawić wartość pustą dla co najmniej jednego wiersza.  <br/> |(pozostaw puste)  <br/> Lub  <br/>  `932` (który jest identyfikatorem strony kodowej dla języka japońskiego ANSI/OEM)  <br/> |
    | `SPFileContainer` <br/> |W przypadku importowania PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |
    | `SPManifestContainer` <br/> |W przypadku importowania PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |
    | `SPSiteUrl` <br/> |W przypadku importowania PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |

## <a name="step-5-create-a-pst-import-job"></a>Krok 5. Tworzenie zadania importowania PST

Następnym krokiem jest utworzenie zadania importu PST w usłudze Import w Microsoft 365. Jak wyjaśniono wcześniej, przesyłasz plik mapowania importu PST utworzony w kroku 4. Po utworzeniu zadania Microsoft 365 analizuje dane w plikach PST, a następnie umożliwia filtrowanie danych faktycznie importowanych do skrzynek pocztowych określonych w pliku mapowania importu PST (zobacz [Krok 6](#step-6-filter-data-and-start-the-pst-import-job)).
  
1. Przejdź do strony <https://compliance.microsoft.com> i zaloguj się przy użyciu poświadczeń konta administratora w organizacji.

2. W lewym okienku portalu zgodności kliknij pozycję **Zarządzanie informacjami > Importuj**.

3. Na karcie **Import** kliknij pozycję Dodaj ikonę ![.](../media/ITPro-EAC-AddIcon.gif) **Nowe zadanie importu**.

   > [!NOTE]
   > Musisz mieć przypisane odpowiednie uprawnienia, aby uzyskać dostęp do strony **Import** w portalu zgodności, aby utworzyć zadanie importu. Aby uzyskać więcej informacji, zobacz sekcję **Przed rozpoczęciem** . 

4. Wpisz nazwę zadania importu PST, a następnie kliknij przycisk **Dalej**. Użyj małych liter, cyfr, łączników i podkreślenia. Nie można używać wielkich liter ani dołączać spacji w nazwie.

5. Na stronie **Czy chcesz przekazać lub wysłać dane?** kliknij **Upload dane**, a następnie kliknij przycisk **Dalej**.
  
6. W kroku 4 na stronie **Importuj dane** kliknij przycisk **Zakończono przekazywanie plików** i **mam dostęp do pól wyboru pliku mapowania** , a następnie kliknij przycisk **Dalej**.

    ![Kliknij dwa pola wyboru w kroku 4.](../media/9f2427e8-3af2-4e27-95e6-a9f08430d3d8.png)
  
7. Na stronie **Wybierz plik mapowania** kliknij **pozycję Wybierz plik mapowania** , aby przesłać plik mapowania CSV utworzony w kroku 4.

    ![Kliknij pozycję Wybierz plik mapowania, aby przesłać plik CSV utworzony dla zadania importu.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
8. Po wyświetleniu nazwy pliku CSV w obszarze **Nazwa pliku mapowania** kliknij pozycję **Weryfikuj** , aby sprawdzić, czy w pliku CSV występują błędy.

    ![Kliknij pozycję Weryfikuj, aby sprawdzić, czy w pliku CSV występują błędy.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    Plik CSV musi zostać pomyślnie zweryfikowany w celu utworzenia zadania importu PST. Po pomyślnym zweryfikowaniu nazwy pliku zostanie zmieniona na zielona. Jeśli weryfikacja nie powiedzie się, kliknij link **Wyświetl dziennik** . Zostanie otwarty raport o błędzie weryfikacji z komunikatem o błędzie dla każdego wiersza w pliku, który nie powiódł się.

   > [!NOTE]
   > Jak wyjaśniono wcześniej, plik mapowania może zawierać maksymalnie 500 wierszy. Weryfikacja zakończy się niepowodzeniem, jeśli plik mapowania zawiera więcej niż 500 wierszy. Aby zaimportować ponad 500 plików PST, należy utworzyć wiele plików mapowania i wiele zadań importu.

9. Po pomyślnym zweryfikowaniu pliku mapowania przeczytaj dokument warunki i postanowienia, a następnie kliknij pole wyboru.

10. Kliknij **przycisk Zapisz** , aby przesłać zadanie, a następnie kliknij przycisk **Zamknij** po pomyślnym utworzeniu zadania.

    Zostanie wyświetlona strona wysuwanego stanu ze stanem **Analizy w toku** , a nowe zadanie importu zostanie wyświetlone na liście na stronie **Importuj pliki PST** .

11. Kliknij **ikonę Odśwież odświeżanie**![.](../media/O365-MDM-Policy-RefreshIcon.gif) , aby zaktualizować informacje o stanie wyświetlane w kolumnie **Stan** . Po zakończeniu analizy i przygotowaniu danych do zaimportowania stan zostanie zmieniony na **Ukończono analizę**.

    Możesz kliknąć zadanie importu, aby wyświetlić stronę wysuwanego stanu, która zawiera bardziej szczegółowe informacje o zadaniu importowania, takie jak stan każdego pliku PST wymienionego w pliku mapowania.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Krok 6. Filtrowanie danych i uruchamianie zadania importowania PST

Po utworzeniu zadania importu w kroku 5 Microsoft 365 analizuje dane w plikach PST (w bezpieczny i bezpieczny sposób), identyfikując wiek elementów i różne typy komunikatów zawarte w plikach PST. Po zakończeniu analizy i przygotowaniu danych do zaimportowania można zaimportować wszystkie dane zawarte w plikach PST lub przyciąć zaimportowane dane, ustawiając filtry kontrolujące importowane dane.
  
1. Na karcie **Import** w portalu zgodności wybierz zadania importu utworzone w kroku 5, a następnie kliknij pozycję **Importuj, aby Microsoft 365**.
  
   Zostanie wyświetlona strona **Filtrowanie danych** . Zawiera ona szczegółowe informacje o danych wynikające z analizy przeprowadzonej na plikach PST przez Microsoft 365, w tym informacje o wieku danych. W tym momencie możesz filtrować dane, które zostaną zaimportowane lub zaimportować wszystkie dane w takim stanie, w jakim są. 

    ![Możesz przyciąć dane w plikach PST lub zaimportować je wszystkie.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
2. Wykonaj jeden z następujących kroków:

   1. Aby przyciąć importowane dane, kliknij przycisk **Tak, chcę je filtrować przed zaimportowaniem**.

      Aby uzyskać szczegółowe instrukcje krok po kroku dotyczące filtrowania danych w plikach PST, a następnie uruchamiania zadania importowania, zobacz [Filtrowanie danych podczas importowania plików PST do Microsoft 365](filter-data-when-importing-pst-files.md).

      Lub

   2. Aby zaimportować wszystkie dane w plikach PST, kliknij przycisk **Nie, chcę zaimportować wszystko,** a następnie kliknij przycisk **Dalej**.

3. Jeśli zdecydujesz się zaimportować wszystkie dane, kliknij pozycję **Importuj dane** , aby rozpocząć zadanie importowania. 

   Stan zadania importowania jest wyświetlany na stronie **Importowanie plików PST** . Kliknij ![ikonę Odśwież.](../media/O365-MDM-Policy-RefreshIcon.gif) **Odśwież** , aby zaktualizować informacje o stanie wyświetlane w kolumnie **Stan** . Kliknij zadanie importu, aby wyświetlić stronę wysuwanego stanu, która wyświetla informacje o stanie każdego importowanego pliku PST.

## <a name="more-information"></a>Więcej informacji

- Dlaczego warto importować pliki PST do Microsoft 365?

  - Jest to dobry sposób importowania archiwalnych danych komunikatów organizacji do Microsoft 365.

  - Dane są dostępne dla użytkownika ze wszystkich urządzeń, ponieważ są przechowywane w chmurze.

  - Pomaga ona zaspokoić potrzeby organizacji w zakresie zgodności, umożliwiając stosowanie funkcji usługi Microsoft Purview do danych z zaimportowanych plików PST. Obejmuje to:

  - Włączenie [archiwizowanych skrzynek pocztowych](enable-archive-mailboxes.md) i [automatyczne rozszerzanie archiwizacji](enable-autoexpanding-archiving.md) w celu zapewnienia użytkownikom dodatkowego miejsca do przechowywania zaimportowanych danych.

  - Umieszczanie skrzynek pocztowych w [blokadzie postępowania sądowego](./create-a-litigation-hold.md) w celu zachowania zaimportowanych danych.

  - Wyszukiwanie zaimportowanych danych przy użyciu [narzędzi microsoft eDiscovery](search-for-content.md) .

  - Używanie [zasad przechowywania Microsoft 365](retention.md) do kontrolowania, jak długo zaimportowane dane zostaną zachowane i jakie działania należy wykonać po upływie okresu przechowywania.

  - Przeszukiwanie [dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md) pod kątem zdarzeń związanych ze skrzynką pocztową, które mają wpływ na zaimportowane dane.

  - Importowanie danych do [nieaktywnych skrzynek pocztowych w](inactive-mailboxes-in-office-365.md) celu archiwizowania danych na potrzeby zgodności. 

  - Używanie [zasad ochrony przed utratą danych](dlp-learn-about-dlp.md) w celu zapobiegania wyciekowi poufnych danych poza organizację.

- Jak wyjaśniono wcześniej, usługa Microsoft 365 Import włącza ustawienie przechowywania blokady (na czas nieokreślony) po zaimportowaniu plików PST do skrzynki pocztowej. Oznacza to, że  *właściwość RetentionHoldEnabled*  jest ustawiona na  **wartość True** , dzięki czemu zasady przechowywania przypisane do skrzynki pocztowej nie będą przetwarzane. Dzięki temu właściciel skrzynki pocztowej może zarządzać nowo zaimportowanymi wiadomościami, uniemożliwiając usunięcie lub archiwizowanie starszych wiadomości przez zasady usuwania lub archiwizowania. Oto kilka kroków, które można wykonać, aby zarządzać tym przechowywaniem:

  - Po pewnym czasie możesz wyłączyć blokadę przechowywania, uruchamiając polecenie **Set-Mailbox -RetentionHoldEnabled $false** . Aby uzyskać instrukcje, zobacz [Umieszczanie skrzynki pocztowej w blokadzie przechowywania](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Przechowywanie można skonfigurować w taki sposób, aby w przyszłości było wyłączone w określonym dniu. Można to zrobić, uruchamiając polecenie **Set-Mailbox -EndDateForRetentionHold *date*** . Na przykład przy założeniu, że dzisiejsza data to 1 czerwca 2016 r. i chcesz wyłączyć blokadę przechowywania w ciągu 30 dni, uruchom następujące polecenie:  **Set-Mailbox -EndDateForRetentionHold 7/1/2016**. W tym scenariuszu należy pozostawić właściwość  **RetentionHoldEnabled**  ustawioną na  *wartość True*. Aby uzyskać więcej informacji, zobacz [Set-Mailbox (Set-Mailbox](/powershell/module/exchange/set-mailbox)).

  - Możesz zmienić ustawienia zasad przechowywania przypisanych do skrzynki pocztowej, aby starsze elementy, które zostały zaimportowane, nie były natychmiast usuwane ani przenoszone do archiwum skrzynki pocztowej użytkownika. Można na przykład wydłużyć wiek przechowywania dla zasad usuwania lub archiwum przypisanych do skrzynki pocztowej. W tym scenariuszu należy wyłączyć przechowywanie w skrzynce pocztowej po zmianie ustawień zasad przechowywania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad archiwum i usuwania dla skrzynek pocztowych w organizacji](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

### <a name="how-the-import-process-works"></a>Jak działa proces importowania
  
Możesz użyć opcji przekazywania sieci i usługi Microsoft 365 Import, aby zbiorczo importować pliki PST do skrzynek pocztowych użytkowników. Przekazywanie sieci oznacza przekazanie plików PST do tymczasowego obszaru magazynowania w chmurze firmy Microsoft. Następnie usługa Microsoft 365 Import kopiuje pliki PST z obszaru magazynowania do skrzynek pocztowych użytkownika docelowego.
  
Oto ilustracja i opis procesu przekazywania sieci w celu zaimportowania plików PST do skrzynek pocztowych w Microsoft 365.
  
![Przepływ pracy procesu przekazywania sieci w celu zaimportowania plików PST do Microsoft 365.](../media/9e05a19e-1e7a-4f1f-82df-9118f51588c4.png)
  
1. **Pobierz narzędzie i klucz importu PST do prywatnej lokalizacji Storage platformy Azure:** pierwszym krokiem jest pobranie narzędzia wiersza polecenia AzCopy i klucza dostępu używanego do przekazywania plików PST do lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Można je uzyskać na stronie **Import** w portalu zgodności. Klucz (nazywany kluczem sygnatury dostępu bezpiecznego (SAS) zapewnia niezbędne uprawnienia do przekazywania plików PST do prywatnej i bezpiecznej lokalizacji Storage platformy Azure. Ten klucz dostępu jest unikatowy dla Twojej organizacji i zapobiega nieautoryzowanemu dostępowi do plików PST po ich przekazaniu do chmury firmy Microsoft. Importowanie plików PST nie wymaga od organizacji posiadania oddzielnej subskrypcji platformy Azure.

2. **Upload plików PST do lokalizacji usługi Azure Storage:** następnym krokiem jest użycie narzędzia azcopy.exe (pobranego w kroku 1) do przekazywania i przechowywania plików PST w lokalizacji Storage platformy Azure, która znajduje się w tym samym regionalnym centrum danych firmy Microsoft, w którym znajduje się Twoja organizacja. Aby je przekazać, pliki PST, które chcesz zaimportować, muszą znajdować się w udziale plików lub serwerze plików w organizacji.

    Istnieje opcjonalny krok, który można wykonać, aby wyświetlić listę plików PST po ich przekazaniu do lokalizacji usługi Azure Storage.

3. **Utwórz plik mapowania importu PST:** Po przekazaniu plików PST do lokalizacji usługi Azure Storage następnym krokiem jest utworzenie pliku wartości rozdzielanej przecinkami (CSV), który określa, do których skrzynek pocztowych użytkowników zostaną zaimportowane pliki PST, należy pamiętać, że plik PST może zostać zaimportowany do podstawowej skrzynki pocztowej użytkownika lub jego archiwum. Usługa Microsoft 365 Import używa informacji w pliku CSV do importowania plików PST.

4. **Utwórz zadanie importu PST:** Następnym krokiem jest utworzenie zadania importu PST na stronie **Import plików PST** w portalu zgodności i przesłanie pliku mapowania importu PST utworzonego w poprzednim kroku. Po utworzeniu zadania importowania Microsoft 365 analizuje dane w plikach PST, a następnie umożliwia ustawienie filtrów, które kontrolują, jakie dane są faktycznie importowane do skrzynek pocztowych określonych w pliku mapowania importu PST.

5. **Przefiltruj dane PST, które zostaną zaimportowane do skrzynek pocztowych:** Po utworzeniu i uruchomieniu zadania importowania Microsoft 365 analizuje dane w plikach PST (bezpiecznie i bezpiecznie), identyfikując wiek elementów i różne typy komunikatów zawarte w plikach PST. Po zakończeniu analizy i przygotowaniu danych do zaimportowania można zaimportować wszystkie dane zawarte w plikach PST lub przyciąć zaimportowane dane, ustawiając filtry kontrolujące importowane dane.

6. **Uruchom zadanie importu PST:** Po uruchomieniu zadania importowania Microsoft 365 używa informacji w pliku mapowania importu PST do importowania plików PSTs z lokalizacji usługi Azure Storage do skrzynek pocztowych użytkowników. Informacje o stanie zadania importu (w tym informacje o każdym importowanym pliku PST) są wyświetlane na stronie **Importowanie plików PST** w portalu zgodności. Po zakończeniu zadania importowania stan zadania jest ustawiony na **Ukończono**.
