---
title: Importowanie plików PST organizacji za pomocą przekazywania sieciowego
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
description: 'Dla administratorów: Dowiedz się, jak używać przekazywania sieciowego do zbiorczego importowania wielu plików PST do skrzynek pocztowych użytkowników w Microsoft 365.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b189be60efb48af33d26ea459bbee77878d4a93c
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020779"
---
# <a name="use-network-upload-to-import-your-organizations-pst-files-to-microsoft-365"></a>Użyj przekazywania sieciowego, aby zaimportować pliki PST twojej organizacji do Microsoft 365

> [!NOTE]
> Ten artykuł jest dla administratorów. Czy próbujesz zaimportować pliki PST do własnej skrzynki pocztowej? Zobacz [Importowanie wiadomości e-mail, kontaktów i kalendarza z pliku Outlook pst.](https://go.microsoft.com/fwlink/p/?LinkID=785075)
  
Poniżej znajdują się instrukcje krok po kroku wymagane do użycia przekazywania sieciowego do zbiorczego importowania wielu plików PST do Microsoft 365 pocztowych. Aby uzyskać odpowiedzi na często zadawane pytania dotyczące używania przekazywania sieciowego do zbiorczego importowania plików PST do skrzynek pocztowych Microsoft 365, zobacz Często zadawane pytania dotyczące używania przekazywania sieciowego do [importowania plików PST](./faqimporting-pst-files-to-office-365.yml#using-network-upload-to-import-pst-files).
  
[Krok 1. Kopiowanie adresu URL sas i pobieranie pliku AzCopy](#step-1-copy-the-sas-url-and-download-azcopy)

[Krok 2. Upload plików PST do Microsoft 365](#step-2-upload-your-pst-files-to-microsoft-365)

[(Opcjonalnie) Krok 3. Wyświetlanie listy przekazanych plików PST](#optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365)

[Krok 4. Tworzenie pliku mapowania na importowanie pliku PST](#step-4-create-the-pst-import-mapping-file)

[Krok 5. Tworzenie zadania importu pliku PST](#step-5-create-a-pst-import-job)

[Krok 6. Filtrowanie danych i uruchamianie zadania importowania pliku PST](#step-6-filter-data-and-start-the-pst-import-job)

Krok 1 należy wykonać tylko raz, aby zaimportować pliki PST do Microsoft 365 pocztowych. Po wykonanie tych czynności wykonaj kroki od 2 do 6 za każdym razem, gdy chcesz przekazać i zaimportować partię plików PST.

## <a name="before-you-import-pst-files"></a>Przed zaimportowaniem plików PST
  
- Aby tworzyć zadania importowania w Exchange Online i importować pliki PST do skrzynek pocztowych użytkowników, musisz mieć przypisaną rolę importowania i eksportowania skrzynek Exchange Online Centrum zgodności platformy Microsoft 365 skrzynek pocztowych użytkowników. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać siebie jako członka. Aby uzyskać więcej informacji, zobacz sekcje "Dodawanie roli do grupy ról" lub "Tworzenie grupy ról" w tece Zarządzanie [grupami ról](/Exchange/permissions-exo/role-groups).

    Oprócz roli importowania i eksportowania skrzynek pocztowych należy również przypisać rolę adresatów poczty w programie Exchange Online. Domyślnie ta rola jest przypisana do grup ról Zarządzanie organizacją i Zarządzanie adresatami w programie Exchange Online.

    > [!TIP]
    > Rozważ utworzenie nowej grupy ról w Exchange Online przeznaczonej specjalnie do importowania plików PST. Aby uzyskać minimalny poziom uprawnień wymaganych do importowania plików PST, przypisz role importowania i eksportowania skrzynek pocztowych oraz adresatów poczty do nowej grupy ról, a następnie dodaj do nich członków.
  
- Jedyną obsługiwaną metodą importowania plików PST do Microsoft 365 jest użycie narzędzia AzCopy, jak opisano w tym artykule. Za pomocą tego narzędzia nie można Eksplorator usługi Azure Storage przekazywać plików PST bezpośrednio do obszaru Storage Azure.

- Duże pliki PST mogą mieć wpływ na wydajność procesu importowania pliku PST. Dlatego zalecamy, aby każdy plik PST, który przekażemy do lokalizacji Storage Azure w kroku 2, nie powinien być większy niż 20 GB.

- Ta procedura obejmuje kopiowanie i zapisywanie kopii adresu URL zawierającego klucz dostępu. Te informacje zostaną użyte w kroku 2 do przekazania plików PST i w kroku 3, jeśli chcesz wyświetlić listę plików PST przekazanych do Microsoft 365. Pamiętaj o podjęciu środków ostrożności w celu ochrony tego adresu URL, tak jak w przypadku ochrony haseł i innych informacji związanych z zabezpieczeniami. Możesz go na przykład zapisać w chronionym hasłem dokumencie Microsoft Word na zaszyfrowanym dysku USB. Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać przykład tego połączonego adresu URL i klucza.

- Możesz importować pliki PST do nieaktywnej skrzynki pocztowej w programie Microsoft 365. Możesz to zrobić, określając identyfikator GUID nieaktywnej skrzynki pocztowej w  `Mailbox` parametrze w pliku mapowania importu pliku PST. Aby uzyskać informacje, zobacz Krok **4 na karcie** Instrukcje w tym artykule.

- W Exchange hybrydowym możesz zaimportować pliki PST do archiwaowej skrzynki pocztowej w chmurze dla użytkownika, którego podstawowa skrzynka pocztowa jest lokalna. W tym celu w pliku mapowania importowania pliku PST wykonaj następujące czynności:

  - Określ adres e-mail lokalnej skrzynki pocztowej użytkownika w parametrze  `Mailbox` .

  - Określ **wartość PRAWDA** w parametrze  `IsArchive` .

    Aby [uzyskać więcej informacji, zobacz Krok 4](#step-4-create-the-pst-import-mapping-file) .

- Po zaimportowaniu plików PST ustawienie przechowywania dla skrzynki pocztowej jest włączone na czas nieograniczony. Oznacza to, że zasady przechowywania przypisane do skrzynki pocztowej nie będą przetwarzane, dopóki nie wyłączysz przechowywania lub nie ustawisz daty wyłączenia tego przechowywania. Dlaczego to robimy? Jeśli wiadomości zaimportowane do skrzynki pocztowej są stare, mogą zostać trwale usunięte (usunięte), ponieważ ich okres przechowywania wygasł na podstawie ustawień przechowywania skonfigurowanych dla skrzynki pocztowej. Umieszczenie skrzynki pocztowej w stanie przechowywania zapewnia właścicielowi skrzynki pocztowej czas na zarządzanie tymi nowo zaimportowaymi wiadomościami lub na zmianę ustawień przechowywania skrzynki pocztowej. Zobacz [sekcję Więcej informacji](#more-information) w tym artykule, aby uzyskać sugestie dotyczące zarządzania przechowywaniem.

- Domyślny maksymalny rozmiar wiadomości, jaki może odbierać skrzynka pocztowa Microsoft 365, wynosi 35 MB. Jest tak, ponieważ wartość domyślna właściwości  *MaxReceiveSize*  skrzynki pocztowej jest ustawiona na 35 MB. Jednak maksymalny rozmiar odbieranych wiadomości w programie Microsoft 365 wynosi 150 MB. Jeśli więc importujesz plik PST zawierający element o rozmiarze ponad 35 MB, usługa importowania usługi Microsoft 365 automatycznie zmieni wartość właściwości *MaxReceiveSize* dla docelowej skrzynki pocztowej na 150 MB. Dzięki temu wiadomości o rozmiarze do 150 MB mogą być importowane do skrzynek pocztowych użytkowników.

    > [!TIP]
    > Aby określić rozmiar odbierania wiadomości dla skrzynki pocztowej, możesz uruchomić następujące polecenie w programie Exchange Online PowerShell: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`.

- Aby uzyskać ogólne omówienie procesu importowania pliku PST, zobacz [sekcję Jak działa proces importowania](#how-the-import-process-works) w tym artykule.

## <a name="step-1-copy-the-sas-url-and-download-azcopy"></a>Krok 1. Kopiowanie adresu URL sas i pobieranie pliku AzCopy

Pierwszym krokiem jest pobranie narzędzia AzCopy, które jest uruchamiane w kroku 2 w celu przekazania plików PST do Microsoft 365. Możesz również skopiować adres URL SAS dla swojej organizacji. Ten adres URL jest połączeniem sieciowego adresu URL folderu usługi Azure Storage w chmurze firmy Microsoft dla organizacji i klucza SAS (Shared Access Signature). Ten klucz zapewnia uprawnienia niezbędne do przekazywania plików PST do lokalizacji Storage Azure. Pamiętaj o podjęciu środków ostrożności w celu ochrony adresu URL SAS. Jest on unikatowy dla Twojej organizacji i będzie używany w kroku 2.

> [!IMPORTANT]
> Aby zaimportować pliki PST przy użyciu metody przekazywania sieciowego i składni poleceń udokumentowanych w tym artykule, należy użyć wersji narzędzia AzCopy, która może zostać pobrana w kroku 6b w poniższej procedurze. Z tego linku możesz również pobrać tę samą wersję produktu AzCopy[.](https://aka.ms/downloadazcopylatest) Używanie innej wersji narzędzia AzCopy nie jest obsługiwane.
  
1. Przejdź do <https://compliance.microsoft.com> konta administratora w organizacji i zaloguj się przy użyciu poświadczeń administratora.

2. W lewym okienku okna Centrum zgodności platformy Microsoft 365 pozycję **Importowanie zarządzania informacjami**\>.

    > [!NOTE]
    > Musisz mieć odpowiednie uprawnienia, aby uzyskać dostęp **do strony** Importowanie w Centrum zgodności platformy Microsoft 365. Aby uzyskać **więcej informacji, zobacz** sekcję Przed rozpoczęciem. 

3. Na karcie **Importowanie** kliknij pozycję ![Dodaj ikonę.](../media/ITPro-EAC-AddIcon.gif) **Nowe zadanie importu**.

    Zostanie wyświetlony Kreator zadań importu.

4. Wpisz nazwę zadania importu pliku PST, a następnie kliknij przycisk **Dalej**. Używaj małych liter, cyfr, łączników i podkreśleń. Nie można używać wielkich liter ani dołączać w nazwie spacji.

5. Na stronie **Czy chcesz przekazać lub wysłać dane?** kliknij pozycję Upload **danych**, a następnie kliknij przycisk **Dalej**.

    ![Kliknij Upload danych, aby utworzyć zadanie importu przekazywania sieciowego.](../media/e59f9dc3-ccde-44ff-ac38-c4e39d76ae85.png)
  
6. Na **stronie Importowanie** danych wykonaj następujące dwie czynności:

    ![Skopiuj adres URL SAS i pobierz narzędzie AzCopy na stronie Importowanie danych.](../media/74411014-ec4b-4e25-9065-404c934cce17.png)
  
    1. W kroku 2 kliknij pozycję **Pokaż adres URL SAS przekazywania sieciowego**. Po wyświetlaniu adresu URL SAS kliknij pozycję **Kopiuj do schowka** , a następnie wklej go i zapisz w pliku, aby można było później uzyskać do niego dostęp.

    2. W kroku 3 kliknij pozycję **Pobierz narzędzie Azure AzCopy** , aby pobrać narzędzie AzCopy na komputer lokalny. Ta wersja azcopy jest po prostu plikiem wykonywalnym, więc nie trzeba niczego instalować.

   > [!NOTE]
   > Możesz pozostawić **otwartą stronę Importowanie** danych (na wypadek, gdy trzeba ponownie skopiować adres URL SAS) lub kliknąć przycisk **Anuluj** , aby go zamknąć.

## <a name="step-2-upload-your-pst-files-to-microsoft-365"></a>Krok 2. Upload plików PST do Microsoft 365

Teraz możesz użyć narzędzia AzCopy do przekazywania plików PST do Microsoft 365. To narzędzie przekaże i przechowuje pliki PST w lokalizacji lokalizacji usługi Azure Storage chmurze firmy Microsoft podaną przez firmę Microsoft. Jak wyjaśniono wcześniej, lokalizacja usługi Azure Storage, do której są przekazywania plików PST, znajduje się w tym samym regionalnym centrum danych firmy Microsoft, w którym znajduje się Twoja organizacja. Aby wykonać ten krok, pliki PST muszą być umieszczone w udziałach plików lub na serwerze plików w organizacji lub w lokalizacji usługi Azure Storage zarządzanej przez Twoją organizację. W tej procedurze lokalizacja przechowywania pliku PST jest znana jako lokalizacja źródłowa. Przy każdym uruchomieniu narzędzia AzCopy możesz określić inną lokalizację źródłową.

> [!NOTE]
> Jak wspomniano wcześniej, każdy plik PST, który przekażemy do lokalizacji Storage Azure, nie powinien być większy niż 20 GB. Pliki PST o rozmiarze ponad 20 GB mogą mieć wpływ na wydajność procesu importowania pliku PST, który rozpoczyna się w kroku 6. Ponadto każdy plik PST musi mieć unikatową nazwę.

1. Otwórz wiersz polecenia na komputerze lokalnym.

2. Przejdź do katalogu, do którego pobrano azcopy.exe w kroku 1.

3. Uruchom następujące polecenie, aby przekazać pliki PST do Microsoft 365.

    ```powershell
    azcopy.exe copy "<Source location of PST files>" "<SAS URL>"
    ```

    > [!IMPORTANT]
    > W poprzednim poleceniu możesz określić lokalizację źródłową katalogu lub pliku usługi Azure Storage jako lokalizację źródłową. Nie możesz określić pojedynczego pliku PST. Wszystkie pliki PST w lokalizacji źródłowej zostaną przekazane.

    W poniższej tabeli opisano azcopy.exe pól i ich wymaganych wartości. Informacje uzyskane w poprzednim kroku są używane w wartościach tych pól.

    | Pole | Opis |
    |:-----|:-----|
    | Źródło |Pierwsze pole określa katalog źródłowy w organizacji zawierający pliki PST, które zostaną przekazane Microsoft 365. Ewentualnie możesz określić lokalizację pliku Azure Storage jako lokalizację źródłową plików PST do przekazania. <br/> Pamiętaj, aby owijać wartość tego pola znakami podwójnego cudzysłowu (" ").  <br/> <br/>**Przykłady**: <br/>`"\\FILESERVER01\PSTs"` <br/> Lub  <br/>`"https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx"`|  
    | Destination (Miejsce docelowe) |Określa adres URL SAS uzyskany w kroku 1.  <br/> Pamiętaj, aby owijać wartość tego parametru znakami podwójnego cudzysłowu (" ").<br/><br/>**Uwaga:** Jeśli używasz adresu URL SAS w skrypcie lub pliku wsadowym, uważaj na określone znaki, których należy uniknąć. Na przykład musisz zmienić na `%` `&` `%%` `^&`.<br/><br/>**Porada:** (Opcjonalnie) Możesz określić podfolder w usłudze Azure Storage lokalizacji przekazywania plików PST. Możesz to zrobić, dodając lokalizację podfolderu (po "ingestiondata") w adresie URL SAS. Pierwszy przykład nie określa podfolderu. Oznacza to, że pliki PST są przekazywane do katalogu głównego (*o nazwie ingestiondata*) usługi Azure Storage lokalizacji. Drugi przykład jest przekazywania plików PST do podfolderu (o nazwie *PSTFiles*) w katalogu głównym katalogu Storage Azure.  <br/><br/>**Przykłady**: <br/> `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> Lub  <br/>  `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata/PSTFiles?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> |
    | `--recursive` |Ta flaga opcjonalna określa tryb rekurencyjny, dzięki czemu narzędzie AzCopy kopiuje pliki PSTs znajdujące się w podfolderach w katalogu źródłowym określonym przez pole źródłowe. Domyślna wartość tej flagi to `true`. <br/>**Uwaga:** Jeśli dołączysz tę flagę, pliki PST w podfolderach będą mieć inną nazwę ścieżki w lokalizacji usługi Azure Storage po ich przesłaniu. Musisz określić dokładną nazwę ścieżki pliku w pliku CSV, który tworzysz w kroku 4.|
    | `--s2s-preserve-access-tier` | Ta opcjonalna flaga jest wymagana tylko wtedy, gdy lokalizacja źródłowa jest lokalizacją o przeznaszczenie do ogólnego przeznaczenia w 2 Storage Azure, która obsługuje warstwy dostępu. W scenariuszu importowania pliku PST nie ma potrzeby zachowywania warstwy dostępu podczas kopiowania plików PST z konta usługi Azure Storage do lokalizacji danych usługi Azure Storage dostarczonych przez firmę Microsoft. W tym przypadku możesz dołączyć tę flagę i użyć wartości `false`. Nie musisz używać tej flagi podczas kopiowania plików PST z klasycznego konta usługi Azure Storage, które nie obsługuje warstw dostępu.|
   |||

Aby uzyskać więcej informacji na **tematazcopy.exe kopiowania** , zobacz [azcopy copy](/azure/storage/common/storage-ref-azcopy-copy).

Poniżej przedstawiono przykłady składni narzędzia AzCopy z użyciem rzeczywistych wartości dla każdego parametru.

### <a name="example-1"></a>Przykład 1

Jest to przykład katalogu źródłowego znajdującego się na serwerze plików lub komputerze lokalnym.

```powershell
azcopy.exe copy "\\FILESERVER1\PSTs" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"
```

### <a name="example-2"></a>Przykład 2

Jest to przykład katalogu źródłowego znajdującego się w klasycznej usłudze Azure Storage z podkierunkowości.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --recursive
```

### <a name="example-3"></a>Przykład 3

Jest to przykład katalogu źródłowego znajdującego się na koncie usługi Azure w wersji 2 Storage ogólnego. Warstwy programu Access nie są zachowywane podczas przekazywanych plików PST.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --s2s-preserve-access-tier=false
```

Po uruchomieniu polecenia są wyświetlane komunikaty o stanie, które pokazują postęp przekazywania plików PST. Końcowy komunikat o stanie pokazuje łączną liczbę plików, które zostały pomyślnie przekazane.

> [!TIP]
> Po pomyślnym uruchomieniu polecenia Kopiuj w programie **azcopy.exe** i sprawdzeniu, czy wszystkie parametry są poprawne, zapisz kopię składni wiersza polecenia w tym samym (zabezpieczonym) pliku, w którym zostały skopiowane informacje uzyskane w kroku 1. Następnie możesz skopiować i wkleić to polecenie w wierszu polecenia za każdym razem, gdy chcesz uruchomić narzędzie AzCopy w celu przekazania plików PST do Microsoft 365. Jedyna wartość, która może być konieczne, jest dla pola źródłowego. Zależy to od katalogu źródłowego, w którym znajdują się pliki PST.

## <a name="optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>(Opcjonalnie) Krok 3. Wyświetlanie listy plików PST przekazanych do Microsoft 365

Krok opcjonalny to zainstalowanie i użycie programu Eksplorator usługi Microsoft Azure Storage (bezpłatnego narzędzia typu open source) w celu wyświetlenia listy plików PST przekazanych do obiektu blob platformy Azure. Istnieją dwa dobre powody do tego:
  
- Sprawdź, czy pliki PST z folderu udostępnionego lub serwera plików w Organizacji zostały pomyślnie przekazane do obiektu blob platformy Azure.

- Sprawdź nazwę pliku (i nazwę ścieżki podfolderu, jeśli została uwzględniona) dla każdego pliku PST przekazanego do obiektu blob platformy Azure. Jest to pomocne podczas tworzenia pliku mapowania plików PST w następnym kroku, ponieważ dla każdego pliku PST należy określić zarówno nazwę ścieżki folderu, jak i nazwę pliku. Zweryfikowanie tych nazw może zmniejszyć potencjalne błędy w pliku mapowania plików PST.

Autonomiczna Eksplorator usługi Azure Storage jest ogólnie dostępna. Najnowszą wersję możesz pobrać, korzystając z linku w poniższej procedurze.
  
> [!IMPORTANT]
> Za pomocą tego pliku nie można Eksplorator usługi Azure Storage ani modyfikować plików PST. Jedyną obsługiwaną metodą importowania plików PST jest użycie azcopy. Ponadto nie można usunąć plików PST przekazanych do obiektu blob platformy Azure. Jeśli spróbujesz usunąć plik PST, zostanie wyświetlony komunikat o błędzie z informacjami o tym, że nie masz wymaganych uprawnień. Zwróć uwagę, że wszystkie pliki PST są automatycznie usuwane z obszaru magazynu platformy Azure. Jeśli nie ma zadań importu w toku, wszystkie pliki PST w kontenerze **ingestiondata** są usuwane 30 dni po utworzeniu najnowszego zadania importu.
  
Aby zainstalować Eksplorator usługi Azure Storage i połączyć się z obszarem usługi Azure Storage sieci:
  
1. Pobierz i zainstaluj [Eksplorator usługi Microsoft Azure Storage narzędzia](https://go.microsoft.com/fwlink/p/?LinkId=544842).

2. Uruchom Eksplorator usługi Microsoft Azure Storage.

3. Na stronie **Wybieranie zasobu** w oknie **Połączenie do usługi Azure Storage** kliknij pozycję **Kontener obiektów blob**.
  
4. Na stronie **Wybieranie metody uwierzytelniania** wybierz opcję Podpis dostępu udostępnionego **(SAS),** a następnie kliknij przycisk **Dalej**.

5. Na stronie **Wprowadź informacje o połączeniu** wklej adres URL SAS uzyskany w kroku 1 w polu pod adresem **URL SAS kontenera obiektów blob**, a następnie kliknij przycisk **Dalej**. Po wklejeniu adresu URL funkcji SAS pole w obszarze Nazwa **wyświetlana** jest automatycznie zasypyane danymi **ingestiondata**.

6. Na stronie **Podsumowanie** możesz przejrzeć informacje o połączeniu, a następnie kliknąć przycisk **Połączenie**.

    Zostanie **otwarty kontener ingestiondata** . Zawiera ona pliki PST przekazane w kroku 2. Kontener **ingestiondata** znajduje się w obszarze **kontenerów obiektów blob Storage konta** \> **(dołączone kontenery**\>). 
  
7. Po zakończeniu korzystania z aplikacji Eksplorator usługi Microsoft Azure Storage kliknij prawym przyciskiem myszy **ingestiondata**, a następnie kliknij polecenie Odłącz, aby  odłączyć się od platformy Azure Storage obszarze. W przeciwnym razie przy następnej próbie dołączenia otrzymasz komunikat o błędzie.
  
## <a name="step-4-create-the-pst-import-mapping-file"></a>Krok 4. Tworzenie pliku mapowania na importowanie pliku PST

Po przesłaniu plików PST do lokalizacji usługi Azure Storage dla organizacji następnym krokiem jest utworzenie pliku w formacie wartości rozdzielanych przecinkami (CSV), który określa, do których skrzynek pocztowych użytkowników zostaną zaimportowane pliki PST. Ten plik CSV należy przesłać w następnym kroku podczas tworzenia zadania importu pliku PST.
  
1. [Pobierz kopię pliku mapowania importu pliku PST](https://go.microsoft.com/fwlink/p/?LinkId=544717).

2. Otwórz lub zapisz plik CSV na komputerze lokalnym. W poniższym przykładzie pokazano ukończony plik mapowania importu pliku PST (otwarty w Notatniku). Edytowanie pliku CSV Microsoft Excel znacznie łatwiejsze.

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

    Pierwszy wiersz w pliku CSV, czyli wiersz nagłówka, zawiera parametry, które będą używane przez usługę importowania plików PST do importowania plików PST do skrzynek pocztowych użytkowników. Poszczególne nazwy parametrów są rozdzielone przecinkami. Każdy wiersz poniżej wiersza nagłówka odzwierciedla wartości parametrów importowania pliku PST do określonej skrzynki pocztowej. Potrzebujesz wiersza dla każdego pliku PST, który chcesz zaimportować do skrzynki pocztowej użytkownika. Plik mapowania CSV może mieć maksymalnie 500 wierszy. Aby zaimportować więcej niż 500 plików PST, musisz utworzyć wiele plików mapowania i utworzyć wiele zadań importu w kroku 5.

    > [!NOTE]
    > Nie zmieniaj niczego w wierszu nagłówka, w tym SharePoint parametrów; zostaną one zignorowane podczas procesu importowania pliku PST. Pamiętaj też, aby zastąpić dane zastępcze w pliku mapowania danymi rzeczywistymi.

3. Za pomocą informacji w poniższej tabeli wypełnij plik CSV wymaganymi informacjami.

    | Parametr | Opis | Przykład |
    |:-----|:-----|:-----|
    | `Workload` <br/> |Określa usługę, do która ma zostać zaimportowana dane. Aby zaimportować pliki PST do skrzynek pocztowych użytkowników, użyj formatu  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> |Określa lokalizację folderu w usłudze Azure Storage, do których zostały przekazane pliki PST w kroku 2.  <br/> Jeśli nie uwzględnisz opcjonalnej nazwy podfolderu w adresie URL SAS  `/Dest:` w parametrze w kroku 2, pozostaw ten parametr pusty w pliku CSV. Jeśli dołączona jest nazwa podfolderu, określ ją w tym parametrze (zobacz drugi przykład). W przypadku tego parametru jest w tym parametrze zróżnicowana wielkość liter.  <br/> W obu sposób  *nie dołączaj*  parametru "ingestiondata" do  `FilePath` wartości parametru.  <br/><br/> **Ważne:** Sprawa nazwy ścieżki pliku musi być taka sama jak przypadek użyty w przypadku dołączona opcjonalna nazwa podfolderu w adresie URL SAS w polu docelowym w kroku 2. Jeśli na przykład  `PSTFiles` nazwa podfolderu została użyta w kroku 2  `pstfiles`  `FilePath` , a następnie użyta w parametrze w pliku CSV, importowanie pliku PST nie powiedzie się. Pamiętaj, aby w obu przypadkach użyć tej samej sprawy.  <br/> |(pozostaw puste)  <br/> Lub  <br/>  `PSTFiles` <br/> |
    | `Name` <br/> |Określa nazwę pliku PST, który zostanie zaimportowany do skrzynki pocztowej użytkownika. W przypadku tego parametru jest w tym parametrze zróżnicowana wielkość liter. Nazwa każdego pliku PST w pliku mapowania dla zadania importu musi być unikatowa. <br/> <br/>**Ważne:** Sprawa dla nazwy pliku PST w pliku CSV musi być taka sama jak plik PST, który został przekazany do lokalizacji usługi Azure Storage kroku 2. Jeśli na przykład użyjemy parametru  `annb.pst`  `Name` w pliku CSV, ale nazwa rzeczywistego pliku PST to , importowanie tego pliku PST `AnnB.pst`nie powiedzie się. Upewnij się, że nazwa pliku PST w pliku CSV ma taką samą nazwę jak rzeczywisty plik PST.  <br/> | `annb.pst` <br/> |
    | `Mailbox` <br/> |Określa adres e-mail skrzynki pocztowej, do która ma zostać zaimportowany plik PST. Nie można określić folderu publicznego, ponieważ usługa importowania plików PST nie obsługuje importowania plików PST do folderów publicznych.  <br/> Aby zaimportować plik PST do nieaktywnej skrzynki pocztowej, musisz określić identyfikator GUID skrzynki pocztowej dla tego parametru. Aby uzyskać ten identyfikator GUID, uruchom następujące polecenie programu PowerShell w programie Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> <br/>**Uwaga:** Czasami możesz mieć wiele skrzynek pocztowych z tym samym adresem e-mail, gdzie jedna skrzynka pocztowa jest aktywna, a druga znajduje się w stanie "miękkiego usunięcia" (lub "nieaktywnego"). W takich sytuacjach musisz określić identyfikator GUID skrzynki pocztowej, aby jednoznacznie zidentyfikować skrzynkę pocztową do zaimportowania pliku PST. Aby uzyskać ten identyfikator GUID dla aktywnych skrzynek pocztowych, uruchom następujące polecenie programu PowerShell:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Aby uzyskać identyfikator GUID dla skrzynek pocztowych nieaktywnych (lub nieaktywnych), uruchom to polecenie  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.  <br/> | `annb@contoso.onmicrosoft.com` <br/> Lub  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Określa, czy zaimportować plik PST do archiwaowej skrzynki pocztowej użytkownika. Dostępne są dwie opcje:  <br/><br/>**FAŁSZ:** Importuje plik PST do podstawowej skrzynki pocztowej użytkownika.  <br/> **PRAWDA:** Importuje plik PST do archiwaowej skrzynki pocztowej użytkownika. Założono, że [jest włączona archiwalne skrzynka pocztowa użytkownika](enable-archive-mailboxes.md). <br/><br/>Jeśli ten parametr zostanie ustawiony i  `TRUE` archiwalne skrzynka pocztowa użytkownika nie będzie włączona, importowanie dla tego użytkownika nie powiedzie się. Jeśli importowanie zakończy się niepowodzeniem dla jednego użytkownika (  `TRUE`ponieważ jego archiwum nie jest włączone, a ta właściwość jest ustawiona na ), nie będzie to mieć wpływu na innych użytkowników w zadaniu importu.  <br/>  Jeśli pozostawisz ten parametr pusty, plik PST zostanie zaimportowany do podstawowej skrzynki pocztowej użytkownika.  <br/> <br/>**Uwaga:** Aby zaimportować plik PST do archiwaowej skrzynki pocztowej w chmurze dla użytkownika, którego podstawowa skrzynka pocztowa jest lokalna,  `TRUE` wystarczy określić dla tego parametru adres e-mail  `Mailbox` lokalnej skrzynki pocztowej użytkownika.  <br/> | `FALSE` <br/> Lub  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Określa folder skrzynki pocztowej, do których jest importowany plik PST.  <br/> <br/> Jeśli pozostawisz ten parametr pusty, plik PST zostanie zaimportowany do nowego folderu o nazwie Zaimportowany  na poziomie głównym skrzynki pocztowej (na tym samym poziomie co folder Skrzynka odbiorcza i inne domyślne foldery skrzynek pocztowych).  <br/> <br/> Jeśli określisz  `/`, foldery i elementy w pliku PST zostaną zaimportowane na górę struktury folderów w docelowej skrzynce pocztowej lub archiwum. Jeśli w docelowej skrzynce pocztowej istnieje folder (na przykład foldery domyślne, takie jak Skrzynka odbiorcza, Elementy wysłane i Elementy usunięte), elementy w tym folderze w pliku PST są scalane z istniejącym folderem w docelowej skrzynce pocztowej. Jeśli na przykład plik PST zawiera folder Skrzynka odbiorcza, elementy z tego folderu są importowane do folderu Skrzynka odbiorcza w docelowej skrzynce pocztowej. Nowe foldery są tworzone, jeśli nie istnieją w strukturze folderów docelowej skrzynki pocztowej.  <br/><br/>  Jeśli określisz  `/<foldername>`, elementy i foldery w pliku PST zostaną zaimportowane do folderu o nazwie  *\<foldername\>*  . Na przykład w przypadku użycia pozycji  `/ImportedPst`, elementy zostaną zaimportowane do folderu o nazwie **ImportedPst**. Ten folder będzie znajdował się w skrzynce pocztowej użytkownika na tym samym poziomie, na którym znajduje się folder Skrzynka odbiorcza.  <br/><br/> **Porada:** Rozważ uruchomienie kilku partii testowych, aby poeksperymentować z tym parametrem, aby ustalić najlepszą lokalizację folderu do zaimportowania plików PST.  <br/> |(pozostaw puste)  <br/> Lub  <br/>  `/` <br/> Lub  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Ten parametr opcjonalny określa wartość liczbową dla strony kodowej do zaimportowania plików PST w formacie PLIKU ANSI. Ten parametr jest używany do importowania plików PST z organizacji chińskich, japońskich i koreańskich (CJK), ponieważ w tych językach kodowanie znaków jest zazwyczaj używane w zestawie znaków dwu bajtowych (DBCS). Jeśli ten parametr nie jest używany do importowania plików PST dla języków, w których dbcs są używane do nazw folderów skrzynek pocztowych, nazwy folderów są często zniekształcone po ich zaimportowaniu.  <br/><br/> Aby uzyskać listę obsługiwanych wartości do użycia dla tego parametru, zobacz [Identyfikatory strony kodowej](/windows/win32/intl/code-page-identifiers).  <br/> <br/>**Uwaga:** Jak wspomniano wcześniej, jest to parametr opcjonalny i nie trzeba go uwzględniać w pliku CSV. Możesz też ją dołączyć i pozostawić wartość pustą dla jednego lub większej liczby wierszy.  <br/> |(pozostaw puste)  <br/> Lub  <br/>  `932` (który jest identyfikatorem strony kodowej ANSI/OEM w języku japońskim)  <br/> |
    | `SPFileContainer` <br/> |W przypadku importowania pliku PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |
    | `SPManifestContainer` <br/> |W przypadku importowania pliku PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |
    | `SPSiteUrl` <br/> |W przypadku importowania pliku PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |

## <a name="step-5-create-a-pst-import-job"></a>Krok 5. Tworzenie zadania importu pliku PST

Następnym krokiem jest utworzenie zadania importowania pliku PST w usłudze importowania w programie Microsoft 365. Jak wyjaśniono wcześniej, przesyłasz plik mapowania importowania pliku PST utworzony w kroku 4. Po utworzeniu zadania program Microsoft 365 analizuje dane w plikach PST, Microsoft 365 następnie daje możliwość filtrowania danych, które w rzeczywistości są importowane do skrzynek pocztowych określonych w pliku mapowania importu pliku PST (zobacz Krok [6](#step-6-filter-data-and-start-the-pst-import-job)).
  
1. Przejdź do <https://compliance.microsoft.com> konta administratora w organizacji i zaloguj się przy użyciu poświadczeń administratora.

2. W okienku po lewej stronie okna Centrum zgodności platformy Microsoft 365 pozycję **Zarządzanie informacjami > importowania**.

3. Na karcie **Importowanie** kliknij pozycję ![Dodaj ikonę.](../media/ITPro-EAC-AddIcon.gif) **Nowe zadanie importu**.

   > [!NOTE]
   > Aby utworzyć zadanie importu, musisz mieć odpowiednie uprawnienia, aby uzyskać  dostęp do strony Importowanie Centrum zgodności platformy Microsoft 365 zadania importu. Aby uzyskać **więcej informacji, zobacz** sekcję Przed rozpoczęciem. 

4. Wpisz nazwę zadania importu pliku PST, a następnie kliknij przycisk **Dalej**. Używaj małych liter, cyfr, łączników i podkreśleń. Nie można używać wielkich liter ani dołączać w nazwie spacji.

5. Na stronie **Czy chcesz przekazać lub wysłać dane?** kliknij pozycję Upload **danych**, a następnie kliknij przycisk **Dalej**.
  
6. W kroku 4 na stronie Importowanie danych kliknij pola wyboru Gotowe  przekazywanie plików i mam dostęp do pliku mapowania,  a następnie kliknij przycisk **Dalej**.

    ![Kliknij dwa pola wyboru w kroku 4.](../media/9f2427e8-3af2-4e27-95e6-a9f08430d3d8.png)
  
7. Na stronie **Wybierz plik mapowania kliknij** pozycję **Wybierz** plik mapowania, aby przesłać plik mapowania CSV utworzony w kroku 4.

    ![Kliknij pozycję Wybierz plik mapowania, aby przesłać utworzony plik CSV dla zadania importu.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
8. Gdy nazwa pliku CSV zostanie wyświetlona w obszarze Nazwa pliku **mapowania, kliknij** pozycję Sprawdź poprawność, aby sprawdzić, czy plik CSV nie zawiera błędów.

    ![Kliknij przycisk Sprawdź poprawność, aby sprawdzić, czy plik CSV nie zawiera błędów.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    Aby utworzyć zadanie importowania pliku PST, należy pomyślnie zweryfikować plik CSV. Po pomyślnym weryfikacji nazwa pliku zmieni się na zieloną. Jeśli sprawdzanie poprawności zakończy się niepowodzeniem, kliknij link **Wyświetl** dziennik. Zostanie otwarty raport o błędach sprawdzania poprawności z komunikatem o błędzie dla każdego wiersza w pliku, który nie powiódł się.

   > [!NOTE]
   > Jak wyjaśniono wcześniej, plik mapowania może mieć maksymalnie 500 wierszy. Sprawdzanie poprawności nie powiedzie się, jeśli plik mapowania zawiera więcej niż 500 wierszy. Aby zaimportować więcej niż 500 plików PST, musisz utworzyć wiele plików mapowania i wiele zadań importu.

9. Po pomyślnym weryfikacji pliku mapowania przeczytaj dokument warunków i postanowień, a następnie kliknij pole wyboru.

10. Kliknij **pozycję Zapisz** , aby przesłać zadanie, a następnie kliknij przycisk **Zamknij** po pomyślnym utworzeniu zadania.

    Zostanie wyświetlona strona wysuuwana stanu ze stanem  Analiza w toku, a nowe zadanie importu jest wyświetlane na liście na stronie **Importowanie plików PST**.

11. Kliknij **pozycję Odśwież** ![ikona Odśwież.](../media/O365-MDM-Policy-RefreshIcon.gif) w celu zaktualizowania informacji o statusie wyświetlanych w **kolumnie** Stan. Po zakończeniu analizy i przygotowaniu danych do zaimportowania stan zmienia się na **Ukończono analizę**.

    Możesz kliknąć zadanie importu, aby wyświetlić stronę wysuwu stanu zawierającą bardziej szczegółowe informacje o zadaniu importu, takie jak stan każdego pliku PST wymienionego w pliku mapowania.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Krok 6. Filtrowanie danych i uruchamianie zadania importowania pliku PST

Po utworzeniu zadania importu w kroku 5 program Microsoft 365 analizuje dane w plikach PST (w bezpieczny sposób), identyfikując wiek elementów i różne typy wiadomości zawarte w plikach PST. Po zakończeniu analizy i przygotowaniu danych do zaimportowania możesz zaimportować wszystkie dane zawarte w plikach PST lub przyciąć importowane dane, ustawiając filtry kontrolek, które kontrolują, które dane są importowane.
  
1. Na **karcie Importowanie** w Centrum zgodności platformy Microsoft 365 wybierz zadania importu utworzone w kroku 5, a następnie kliknij pozycję Importuj, **aby Microsoft 365**.
  
   Zostanie **wyświetlona strona Filtrowanie** danych. Zawiera szczegółowe informacje o danych wynikające z analizy przeprowadzonej na plikach PST przez Microsoft 365, łącznie z informacjami o wieku danych. W tym momencie możesz filtrować dane, które zostaną zaimportowane lub zaimportować wszystkie dane w stanie takim, w którym są. 

    ![Możesz przyciąć dane w plikach PST lub zaimportować je wszystkie.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
2. Wykonaj jeden z następujących kroków:

   1. Aby przyciąć importowane dane, kliknij pozycję **Tak, chcę je filtrować przed zaimportowaniem**.

      Aby uzyskać szczegółowe instrukcje krok po kroku dotyczące filtrowania danych w plikach PST, a następnie rozpoczynania zadania importu, zobacz Filtrowanie danych podczas importowania plików [PST do Microsoft 365](filter-data-when-importing-pst-files.md).

      Lub

   2. Aby zaimportować wszystkie dane z plików PST, kliknij pozycję **Nie, chcę zaimportować wszystko, a** następnie kliknij przycisk **Dalej**.

3. Jeśli wybrano importowanie wszystkich danych, kliknij pozycję **Importuj dane** , aby rozpocząć zadanie importowania. 

   Stan zadania importu jest wyświetlany na stronie **Importowanie plików PST** . Kliknij ikonę ![Odśwież.](../media/O365-MDM-Policy-RefreshIcon.gif) **Odśwież** , aby zaktualizować informacje o statusie wyświetlane w **kolumnie Stan** . Kliknij zadanie importu, aby wyświetlić stronę wysuwu stanu z informacjami o stanie każdego importowanego pliku PST.

## <a name="more-information"></a>Więcej informacji

- Po co importować pliki PST do Microsoft 365?

  - Jest to dobry sposób na zaimportowanie danych archiwalnych wiadomości organizacji w celu Microsoft 365.

  - Dane są dostępne dla użytkownika na wszystkich urządzeniach, ponieważ są przechowywane w chmurze.

  - Pomaga ona w spełnianiu wymagań dotyczących zgodności w organizacji, pozwalając na stosowanie Microsoft 365 do danych z zaimportowanych plików PST. Obejmuje to:

  - Włączanie [archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md) [i automatyczne](enable-autoexpanding-archiving.md) rozszerzanie archiwizacji w celu umożliwienia użytkownikom dodatkowego miejsca do przechowywania zaimportowanych danych.

  - Umieszczanie skrzynek pocztowych w [przypadku postępowania sądowego](./create-a-litigation-hold.md) w celu zachowania zaimportowanych danych.

  - Przeszukiwanie [zaimportowanych](search-for-content.md) danych za pomocą narzędzi zbierania elektronicznych materiałów dowodowych firmy Microsoft.

  - Za [Microsoft 365 przechowywania](retention.md) można kontrolować, jak długo mają być przechowywane importowane dane i jakie działania należy podjąć po wygaśnięciu okresu przechowywania.

  - Przeszukiwanie [dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md) w poszukiwaniu zdarzeń związanych ze skrzynką pocztową, które wpływają na zaimportowane dane.

  - Importowanie danych do [nieaktywnych skrzynek pocztowych w](inactive-mailboxes-in-office-365.md) celu archiwizacji danych w celu zachowania zgodności. 

  - Stosowanie [zasad ochrony przed utratą danych w](dlp-learn-about-dlp.md) celu zapobiegania wyciekom poufnych danych poza organizację.

- Jak wyjaśniono wcześniej, Microsoft 365 import usługi włącza ustawienie blokowania przechowywania (na czas nieograniczony) po zaimportowaniu plików PST do skrzynki pocztowej. Oznacza to  *, że właściwość RetentionHoldEnabled*  jest ustawiona na wartość  **True** (Prawda), a zasady przechowywania przypisane do skrzynki pocztowej nie są przetwarzane. Dzięki temu właściciel skrzynki pocztowej może zarządzać nowo zaimportowaną wiadomością, uniemożliwiając usuwanie lub archiwizowanie starszych wiadomości przez zasady usuwania lub archiwizacji. Oto kilka czynności, które możesz wykonać, aby zarządzać tym przechowywaniem:

  - Po określonym czasie możesz wyłączyć przechowywanie, uruchamiając polecenie polecenia **Set-Mailbox -RetentionHoldEnabled $false** przechowywania. Aby uzyskać instrukcje, [zobacz Umieść skrzynkę pocztową w miejscu przechowywania](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Możesz skonfigurować przechowywanie w taki sposób, aby w przyszłości było ono wyłączone w przyszłości. Możesz to zrobić, uruchamiając **polecenie Set-Mailbox -EndDateForRetentionHold *date*** . Jeśli na przykład dzisiejszą datą jest 1 czerwca 2016 r. i chcesz wyłączyć przechowywanie w ciągu 30 dni, możesz uruchomić następujące polecenie:  **Set-Mailbox -EndDateForRetentionHold 7/1/2016**. W tym scenariuszu właściwość  **RetentionHoldEnabled**  należy zostawić ustawioną na  *wartość True*. Aby uzyskać więcej informacji, zobacz [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Możesz zmienić ustawienia zasad przechowywania przypisanych do skrzynki pocztowej, aby starsze elementy, które zostały zaimportowane, nie były natychmiast usuwane ani przenoszone do archiwaowej skrzynki pocztowej użytkownika. Można na przykład wydłużyć wiek przechowywania dla zasad usuwania lub archiwizacji przypisanych do skrzynki pocztowej. W tym scenariuszu można wyłączyć przechowywanie w skrzynce pocztowej po zmianie ustawień zasad przechowywania. Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad archiwizacji i usuwania dla skrzynek pocztowych w organizacji](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

### <a name="how-the-import-process-works"></a>Jak działa proces importowania
  
Za pomocą opcji przekazywania sieciowego i Microsoft 365 importu zbiorczego plików PST do skrzynek pocztowych użytkowników. Przekazywanie sieciowe oznacza, że przekażemy pliki PST do tymczasowego obszaru przechowywania w chmurze firmy Microsoft. Następnie Microsoft 365 import usługi kopiuje pliki PST z obszaru przechowywania do skrzynek pocztowych użytkowników docelowych.
  
Poniżej przedstawiono ilustrację i opis procesu przekazywania sieciowego do importowania plików PST do skrzynek pocztowych w aplikacji Microsoft 365.
  
![Przepływ pracy procesu przekazywania sieciowego do importowania plików PST do Microsoft 365.](../media/9e05a19e-1e7a-4f1f-82df-9118f51588c4.png)
  
1. Pobierz narzędzie do importowania pliku PST i klucz do prywatnej lokalizacji usługi **Azure Storage:** Pierwszym krokiem jest pobranie narzędzia wiersza polecenia AzCopy i klucza dostępu służącego do przekazywania plików PST do lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Można je uzyskać na **stronie Importowanie** w Centrum zgodności platformy Microsoft 365. Klucz (nazywany kluczem podpisu bezpiecznego dostępu ( SAS) zapewnia uprawnienia niezbędne do przekazywania plików PST do prywatnej i bezpiecznej lokalizacji Storage danych Azure. Ten klucz dostępu jest unikatowy dla Twojej organizacji i pomaga zapobiec nieautoryzowanemu dostępowi do plików PST po ich przesłaniu do chmury firmy Microsoft. Importowanie plików PST nie wymaga, aby Twoja organizacja posiadała osobną subskrypcję platformy Azure. 

2. Upload pliki PST do lokalizacji usługi **Azure Storage:** Następnym krokiem jest użycie narzędzia azcopy.exe (pobranego w kroku 1) do przekazania i przechowywania plików PST w lokalizacji usługi Azure Storage, która znajduje się w tym samym regionalnym centrum danych firmy Microsoft, w którym znajduje się Twoja organizacja. Aby można było je przekazać, pliki PST, które chcesz zaimportować, muszą być umieszczone w udziałach plików lub na serwerze plików w organizacji.

    Istnieje opcjonalny krok, który możesz wykonać, aby wyświetlić listę plików PST po ich przesłaniu do usługi Azure Storage lokalizacji.

3. **Utwórz plik mapowania na importowanie pliku PST:** Po przesłaniu plików PST do lokalizacji usługi Azure Storage następnym krokiem jest utworzenie pliku w formacie wartości rozdzielanych przecinkami (CSV) określającygo skrzynki pocztowe użytkowników, do których zostaną zaimportowane pliki PST. Zwróć uwagę, że plik PST można zaimportować do podstawowej skrzynki pocztowej użytkownika lub jego archiwaowej skrzynki pocztowej. Usługa Microsoft 365 import korzysta z informacji z pliku CSV do importowania plików PST.

4. **Tworzenie zadania importu pliku PST:** Następnym krokiem jest utworzenie zadania importu pliku PST na stronie Importowanie plików **PST** w aplikacji Centrum zgodności platformy Microsoft 365 i przesłanie pliku mapowania importu PST utworzonego w poprzednim kroku. Po utworzeniu zadania importu program Microsoft 365 analizuje dane w plikach PST, Microsoft 365 następnie umożliwia ustawienie filtrów sterujących tym, jakie dane są faktycznie importowane do skrzynek pocztowych określonych w pliku mapowania importu pliku PST. 

5. **Przefiltruj dane pliku PST, które zostaną zaimportowane do skrzynek pocztowych:** Po utworzeniu i utworzeniu zadania importu program Microsoft 365 bezpiecznie analizuje dane w plikach PST, identyfikując wiek elementów i różne typy wiadomości zawarte w plikach PST. Po zakończeniu analizy i przygotowaniu danych do zaimportowania możesz zaimportować wszystkie dane zawarte w plikach PST lub przyciąć importowane dane, ustawiając filtry kontrolek, które kontrolują, które dane są importowane.

6. **Uruchom zadanie importowania pliku PST:** Po zakończeniu zadania importowania program Microsoft 365 informacje z pliku mapowania importu pliku PST do zaimportowania plików PST z lokalizacji usługi Azure Storage do skrzynek pocztowych użytkowników. Informacje o stanie zadania importu (w tym informacje o każdym importowanych plikach PST) są wyświetlane na stronie Importowanie plików **PST** w Centrum zgodności platformy Microsoft 365. Po zakończeniu zadania importu stan zadania ma ustawioną wartość **Ukończono**.
