---
title: Importowanie plików PST organizacji za pomocą wysyłki dysków
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 40829b57-793c-4d41-b171-e9270129173d
ms.custom: seo-marvel-apr2020
description: Administrator może dowiedzieć się, jak zbiorczo importować pliki PST do Microsoft 365, kopiując pliki PST na dysk twardy, a następnie wysyłając je do firmy Microsoft.
ms.openlocfilehash: 2b0e6e08d6c324914aaf2fdd9ce24b9b55ca2d95
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020717"
---
# <a name="use-drive-shipping-to-import-your-organizations-pst-files"></a>Importowanie plików PST organizacji za pomocą wysyłki dysków

**Ten artykuł jest dla administratorów. Czy próbujesz zaimportować pliki PST do własnej skrzynki pocztowej? Zobacz [Importowanie wiadomości e-mail, kontaktów i kalendarza Outlook pliku pst.](https://go.microsoft.com/fwlink/p/?LinkID=785075)**
   
Użyj usługi Office 365 i wysyłki dysków, aby zbiorczo zaimportować pliki PST do skrzynek pocztowych użytkowników. Wysyłka dysków oznacza, że kopiujesz pliki PST na dysk twardy, a następnie fizycznie wysyłasz ten dysk do firmy Microsoft. Po otrzymaniu dysku twardego firma Microsoft kopiuje dane z tego dysku do obszaru magazynu w chmurze firmy Microsoft. Następnie masz możliwość przycięcia danych pst, które są importowane do docelowych skrzynek pocztowych, ustawiając filtry sterujące tym, które dane są importowane. Po uruchomieniu zadania importu usługa importowania zaimportuje dane pliku PST z obszaru przechowywania do skrzynek pocztowych użytkowników. Jednym ze sposobów migrowania poczty e-mail organizacji do skrzynek pocztowych użytkowników jest użycie wysyłki dysków do importowania plików PST do skrzynek pocztowych Office 365.
  
Aby zaimportować pliki PST do skrzynek pocztowych, wymagane jest użycie wysyłki dysków do Microsoft 365 pocztowych:
  
[Krok 1. Pobieranie narzędzia do importowania pliku PST](#step-1-download-the-pst-import-tool)

[Krok 2. Kopiowanie plików PST na dysk twardy](#step-2-copy-the-pst-files-to-the-hard-drive)

[Krok 3. Tworzenie pliku mapowania na importowanie pliku PST](#step-3-create-the-pst-import-mapping-file)

[Krok 4. Tworzenie zadania importu pliku PST w programie Office 365](#step-4-create-a-pst-import-job-in-office-365)

[Krok 5. Wysyłka dysku twardego do firmy Microsoft](#step-5-ship-the-hard-drive-to-microsoft)

[Krok 6. Filtrowanie danych i uruchamianie zadania importowania pliku PST](#step-6-filter-data-and-start-the-pst-import-job)
  
> [!IMPORTANT]
> Aby pobrać narzędzie importu, wykonaj krok 1 jeden raz. Po wykonaniu tych czynności wykonaj kroki od 2 do 6 za każdym razem, gdy chcesz wysłać dysk twardy do firmy Microsoft. 
  
Aby uzyskać odpowiedzi na często zadawane pytania dotyczące używania wysyłki dysków do importowania plików PST do Office 365, zobacz Często zadawane pytania dotyczące używania wysyłki dysków [do importowania plików PST](./faqimporting-pst-files-to-office-365.yml#using-drive-shipping-to-import-pst-files). 
  
## <a name="before-you-import-pst-files"></a>Przed zaimportowaniem plików PST

- Aby tworzyć zadania importowania w Exchange Online i importować pliki PST do skrzynek pocztowych użytkowników, musisz mieć przypisaną rolę importowania i eksportowania skrzynek Exchange Online Centrum zgodności platformy Microsoft 365 skrzynek pocztowych użytkowników. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać siebie jako członka. Aby uzyskać więcej informacji, zobacz sekcje "Dodawanie roli do grupy ról" lub "Tworzenie grupy ról" w tece Zarządzanie [grupami ról](/Exchange/permissions-exo/role-groups).

    Oprócz roli importowania i eksportowania skrzynek pocztowych należy również przypisać rolę adresatów poczty w programie Exchange Online. Domyślnie ta rola jest przypisana do grup ról Zarządzanie organizacją i Zarządzanie adresatami w programie Exchange Online.

    > [!TIP]
    > Rozważ utworzenie w programie Exchange Online grupy ról przeznaczonej specjalnie do importowania plików PST do Office 365. Aby uzyskać minimalny poziom uprawnień wymaganych do importowania plików PST, przypisz role importowania i eksportowania skrzynek pocztowych oraz adresatów poczty do nowej grupy ról, a następnie dodaj do nich członków.
  
- Pliki PST, które chcesz skopiować, muszą być przechowywane na dysku twardym na serwerze plików lub w folderze udostępnionym w organizacji. W kroku 2 uruchamiasz narzędzie Azure Import Export Tool (WAImportExport.exe), które kopiuje pliki PST przechowywane na tym serwerze plików lub udostępnionym folderze na dysk twardy.

- Duże pliki PST mogą mieć wpływ na wydajność procesu importowania pliku PST. Dlatego zalecamy, aby każdy plik PST kopiowany na dysk twardy w kroku 2 nie był większy niż 20 GB.

- Wewnętrzne dyski twarde SATA II/III 2,5 cala albo wewnętrzne dyski twarde SATA II/III 2,5 cala lub 2,5 cala są obsługiwane przez usługę importowania Office 365. Możesz korzystać z dysków twardych o pojemności do 10 TB. W przypadku zadań importu zostanie przetworzony tylko pierwszy wolumin danych na dysku twardym. Wolumin danych musi być sformatowany w systemie plików NTFS. Podczas kopiowania danych na dysk twardy możesz podłączyć go bezpośrednio za pomocą łącznika dysku SSD 2,5 cala albo SATA II/III 2,5 cala lub 3,5 cala. Możesz też podłączyć go zewnętrznie za pomocą zewnętrznego adaptera USB SSD 2,5 cala albo SATA II/III 2,5 cala lub 2,5 cala.
    
    > [!IMPORTANT]
    > Zewnętrzne dyski twarde z wbudowaną kartą USB nie są obsługiwane przez usługę importowania danych Office 365 importowania. Ponadto nie można używać dysku wewnątrz obudowy zewnętrznego dysku twardego. Prosimy nie wysyłać zewnętrznych dysków twardych. 
  
- Dysk twardy, na który kopiujesz pliki PST, musi być zaszyfrowany za pomocą funkcji BitLocker. Narzędzie WAImportExport.exe uruchamiane w kroku 2 pomoże Ci skonfigurować funkcję BitLocker. Generuje również klucz szyfrowania funkcji BitLocker, za pomocą których pracownik centrum danych firmy Microsoft uzyskuje dostęp do dysku w celu przekazywania plików PST do obszaru usługi Azure Storage w chmurze firmy Microsoft.
    
- Wysyłka dysków jest dostępna za pośrednictwem Enterprise Agreement Microsoft (EA). Wysyłka dysków nie jest dostępna w ramach umowy Microsoft Products and Services Agreement (MPSA).
    
- Koszt importowania plików PST do skrzynek pocztowych platformy Microsoft 365 przy użyciu wysyłki dysków wynosi 2 USD za GB danych. Jeśli na przykład wysyłasz dysk twardy zawierający 1000 GB (1 TB) plików PST, koszt wynosi 2000 USD. Opłatę za importowanie możesz zapłacić we współpracy z partnerem. Aby uzyskać informacje na temat znajdowania partnera, [zobacz Znajdowanie partnera lub odsprzedawcy firmy Microsoft](../admin/manage/find-your-partner-or-reseller.md).
    
- Użytkownik lub Twoja organizacja musi mieć konto w firmie FedEx lub DHL.
    
  - Konta fedex muszą być w organizacjach w Stanach Zjednoczonych, Brazylii i Europie.
    
  - Organizacje w Azji Wschodniej, Azji Południowo-Wschodniej, Japonii, Republice Korei i Australii muszą mieć konta DHL.
    
    Firma Microsoft używa tego konta (i nalicza opłaty) w celu zwrotu Ci dysku twardego.
    
- Dysk twardy, który wysyłasz do firmy Microsoft, może przekroczyć granice międzynarodowe. W takim przypadku ty ponosisz odpowiedzialność za zapewnienie, że dysk twardy i jego dane są importowane i/lub eksportowane zgodnie z obowiązującymi przepisami prawa. Przed wysyłką dysku twardego skontaktuj się z doradcami, aby upewnić się, że dysk i dane można legalnie wysłać do wskazanego centrum danych firmy Microsoft. Dzięki temu firma Microsoft może dotrzeć do niego w terminie.
    
- Ta procedura obejmuje kopiowanie i zapisywanie klucza szyfrowania funkcji BitLocker. Pamiętaj o podjęciu środków ostrożności dotyczących ochrony tych kluczy, takich jak hasła i inne informacje związane z zabezpieczeniami. Można je na przykład zapisać w chronionym hasłem dokumencie Microsoft Word na zaszyfrowanym dysku USB. Przykład [tych kluczy](#more-information) można znaleźć w sekcji Więcej informacji. 
    
- Po zaimportowaniu plików PST do skrzynki Microsoft 365 pocztowej ustawienie przechowywania dla tej skrzynki jest włączone na czas nieograniczony. Oznacza to, że zasady przechowywania przypisane do skrzynki pocztowej nie będą przetwarzane, dopóki nie wyłączysz przechowywania lub nie ustawisz daty wyłączenia tego przechowywania. Dlaczego to robimy? Jeśli wiadomości zaimportowane do skrzynki pocztowej są stare, mogą zostać trwale usunięte (usunięte), ponieważ ich okres przechowywania wygasł na podstawie ustawień przechowywania skonfigurowanych dla skrzynki pocztowej. Umieszczenie skrzynki pocztowej w stanie przechowywania zapewnia właścicielowi skrzynki pocztowej czas na zarządzanie tymi nowo zaimportowaymi wiadomościami lub na zmianę ustawień przechowywania skrzynki pocztowej. Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać sugestie dotyczące zarządzania przechowywaniem. 
    
- Domyślny maksymalny rozmiar wiadomości, jaki może odbierać skrzynka pocztowa Microsoft 365, wynosi 35 MB. Jest tak, ponieważ wartość domyślna właściwości  *MaxReceiveSize*  skrzynki pocztowej jest ustawiona na 35 MB. Jednak maksymalny rozmiar odbieranych wiadomości w programie Microsoft 365 wynosi 150 MB. Dlatego w przypadku importowania pliku PST zawierającego element o rozmiarze ponad 35 MB usługa importowania usługi Office 365 automatycznie zmieni wartość właściwości *MaxReceiveSize* docelowej skrzynki pocztowej na 150 MB. Dzięki temu wiadomości o rozmiarze do 150 MB mogą być importowane do skrzynek pocztowych użytkowników. 
    
    > [!TIP]
    > Aby określić rozmiar odbierania wiadomości dla skrzynki pocztowej, możesz uruchomić następujące polecenie w programie Exchange Online PowerShell: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`. 
  
- Możesz importować pliki PST do nieaktywnej skrzynki pocztowej w Office 365. Możesz to zrobić, określając identyfikator GUID nieaktywnej skrzynki pocztowej w  `Mailbox` parametrze w pliku mapowania importu pliku PST. Aby [uzyskać więcej informacji, zobacz Krok 3. Tworzenie pliku mapowania](#step-3-create-the-pst-import-mapping-file) importu pliku PST. 
    
- W Exchange hybrydowym możesz zaimportować pliki PST do archiwaowej skrzynki pocztowej w chmurze dla użytkownika, którego podstawowa skrzynka pocztowa jest lokalna. W tym celu w pliku mapowania importowania pliku PST wykonaj następujące czynności:
    
  - Określ adres e-mail lokalnej skrzynki pocztowej użytkownika w parametrze  `Mailbox` . 
    
  - Określ **wartość PRAWDA** w parametrze  `IsArchive` . 
    
    Aby [uzyskać więcej informacji, zobacz Krok 3. Tworzenie pliku mapowania](#step-3-create-the-pst-import-mapping-file) importu pliku PST. 

## <a name="step-1-download-the-pst-import-tool"></a>Krok 1. Pobieranie narzędzia do importowania pliku PST

Pierwszym krokiem jest pobranie narzędzia, za pomocą których korzystasz w kroku 2, aby skopiować pliki PST na dysk twardy.
  
> [!IMPORTANT]
> Do pomyślnego zaimportowania plików PST należy użyć narzędzia Azure Import/Export w wersji 1 (WAimportExportV1) przy użyciu metody wysyłki dysków. Wersja 2 narzędzia Azure Import/Export nie jest obsługiwane i użycie go spowoduje niepoprawne przygotowanie dysku twardego na zadanie importu. Pamiętaj o pobraniu narzędzia Azure Import/Export ze strony Centrum zgodności platformy Microsoft 365, korzystając z procedur w tym kroku. 
  
1. Przejdź do <https://compliance.microsoft.com> konta administratora w organizacji i zaloguj się przy użyciu poświadczeń administratora.

2. W okienku nawigacji po lewej stronie okna Centrum zgodności platformy Microsoft 365 pozycję **Importowanie zarządzania informacjami**\>.
    
    > [!NOTE]
    > Jak wspomniano wcześniej, musisz mieć odpowiednie uprawnienia, aby uzyskać dostęp do strony **Importowanie** w Centrum zgodności platformy Microsoft 365. 
  
3. Na karcie **Importowanie** kliknij pozycję ![Dodaj ikonę.](../media/ITPro-EAC-AddIcon.gif) **Nowe zadanie importu**.
    
4. W Kreatorze zadań importu wpisz nazwę zadania importu pliku PST, a następnie kliknij przycisk **Dalej**. Używaj małych liter, cyfr, łączników i podkreśleń. Nie można używać wielkich liter ani dołączać w nazwie spacji.
    
5. Na stronie **Wybierz typ zadania importu** kliknij pozycję Wyślij dyski **twarde** do jednego z naszych lokalizacji fizycznych, a następnie kliknij przycisk **Dalej**.
    
    ![Kliknij pozycję Wyślij dyski twarde do jednej z naszych lokalizacji fizycznych, aby utworzyć zadanie importu wysyłki dysków.](../media/1584fdc5-cd4c-4e47-932e-db6c8e07f5f8.png)
  
6. Na **stronie Importowanie** danych wykonaj następujące czynności:     
    
    **Pobierz narzędzie Azure Import/Export,** aby pobrać i zainstalować narzędzie Azure Import/Export (wersja 1).
    
    - W oknie podręcznym kliknij pozycję Zapisz jako, \> aby zapisać plik WaImportExportV1.zip w folderze na komputerze lokalnym. 
    
    - Wyodrębnij WaImportExportV1.zip pliku.
    
7. Kliknij **przycisk Anuluj** , aby zamknąć kreatora. 
    
    Powrócisz do strony **Importowanie** w Centrum zgodności platformy Microsoft 365 podczas tworzenia zadania importu w kroku 4. 

## <a name="step-2-copy-the-pst-files-to-the-hard-drive"></a>Krok 2. Kopiowanie plików PST na dysk twardy

Następnym krokiem jest skopiowanie plików PST WAImportExport.exe na dysk twardy za pomocą narzędzia do konwersji plików PST. To narzędzie szyfruje dysk twardy przy użyciu funkcji BitLocker, kopiuje pliki PST na dysk twardy i tworzy plik dziennika, w który są przechowywane informacje o procesie kopiowania. Aby można było wykonać ten krok, pliki PST muszą być umieszczone w udziałach plików lub na serwerze plików w organizacji. W poniższej procedurze jest on nazywany katalogiem źródłowym. 

 Jak wspomniano wcześniej, każdy plik PST kopiowany na dysk twardy nie powinien być większy niż 20 GB. Pliki PST o rozmiarze ponad 20 GB mogą mieć wpływ na wydajność procesu importowania pliku PST, który rozpoczyna się w kroku 6.
  
> [!IMPORTANT]
> Po pierwszym uruchomieniu WAImportExport.exe dysku twardego należy za każdym razem użyć innej składni. Tę składnię wyjaśniono w kroku 4 tej procedury kopiowania plików PST na dysk twardy. 
  
1. Otwórz wiersz polecenia na komputerze lokalnym.
    
    > [!TIP]
    > Po uruchomieniu wiersza polecenia jako administrator (przez wybranie opcji "Uruchom jako administrator" po otwarciu) w oknie wiersza polecenia będą wyświetlane komunikaty o błędach. Może to ułatwić rozwiązywanie problemów z uruchamianiem WAImportExport.exe. 
  
2. Przejdź do katalogu, w którym zainstalowano narzędzie WAImportExport.exe w kroku 1.
    
3. Uruchom następujące polecenie podczas pierwszego użycia pliku WAImportExport.exe w celu skopiowania plików PST na dysk twardy.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob /encrypt /logdir:<Log file location>
    ```

    W poniższej tabeli opisano parametry i ich wymagane wartości.
    
    |**Parametr**|**Opis**|**Przykład**|
    |:-----|:-----|:-----|
    | `/j:` <br/> |Określa nazwę pliku dziennika. Ten plik jest zapisywany w tym samym folderze, w którym WAImportExport.exe się narzędzie. Każdy dysk twardy, który wysyłasz do firmy Microsoft, musi mieć jeden plik dziennika. Za każdym razem, gdy WAImportTool.exe kopię plików PST na dysk twardy, informacje zostaną dołączone do pliku dziennika dla tego dysku.  <br/> Pracownicy centrum danych firmy Microsoft używają informacji z pliku dziennika do skojarzenia dysku twardego z zadaniem importu, które utworzysz w kroku 4, i przekazania plików PST do obszaru usługi Azure Storage w chmurze firmy Microsoft.  <br/> | `/j:PSTHDD1.jrn` <br/> |
    | `/t:` <br/> |Określa literę dysku twardego podłączonego do komputera lokalnego.  <br/> | `/t:h` <br/> |
    | `/id:` <br/> |Określa nazwę sesji kopiowania. Sesja jest definiowana za każdym razem, gdy jest uruchamiane narzędzie WAImportExport.exe kopiowanie plików na dysk twardy. Pliki PST są kopiowane do folderu o nazwie o nazwie sesji określonej w tym parametrze.  <br/> | `/id:driveship1` <br/> |
    | `/srcdir:` <br/> |Określa katalog źródłowy w organizacji zawierający pliki PST, które zostaną skopiowane podczas sesji. Pamiętaj, aby owijać wartość tego parametru znakami podwójnego cudzysłowu (" ").  <br/> | `/srcdir:"\\FILESERVER01\PSTs"` <br/> |
    | `/dstdir:` <br/> |Określa katalog docelowy w obszarze usługi Azure Storage w chmurze firmy Microsoft, do którego zostaną przekazane pliki PST. Musisz użyć wartości  `ingestiondata/`. Pamiętaj, aby owijać wartość tego parametru znakami podwójnego cudzysłowu (" ").  <br/> Opcjonalnie możesz również dodać dodatkową ścieżkę do pliku do wartości tego parametru. Możesz na przykład użyć ścieżki pliku katalogu źródłowego na dysku twardym (przekonwertowanej na format adresu URL), określonej w parametrze  `/srcdir:` . Na przykład zmienia  `\\FILESERVER01\PSTs` się na  `FILESERVER01/PSTs`. W tym przypadku nadal musisz dołączyć  `ingestiondata` do ścieżki pliku. W tym przykładzie wartość parametru  `/dstdir:` byłaby zatem taka:  `"ingestiondata/FILESERVER01/PSTs"`.  <br/> Jedną z przyczyn dodania dodatkowej ścieżki pliku jest to, że masz pliki PSTs o tej samej nazwie.  <br/> > [!NOTE]> Jeśli dołączysz opcjonalną nazwę ścieżki, przestrzeń nazw pliku PST po jej przesłaniu do obszaru Usługi Azure Storage będzie zawierać nazwę i nazwę pliku PST, `FILESERVER01/PSTs/annb.pst`na przykład . Jeśli nie uwzględnisz nazwy ścieżki, przestrzenią nazw będzie tylko nazwa pliku PST. na przykład  `annb.pst`.           | `/dstdir:"ingestiondata/"` <br/> Lub  <br/>  `/dstdir:"ingestiondata/FILESERVER01/PSTs"` <br/> |
    | `/blobtype:` <br/> |Określa typ obiektów blob w obszarze Azure Storage do importowania plików PST. Do importowania plików PST użyj wartości **BlockBlob**. Ten parametr jest wymagany.   <br/> | `/blobtype:BlockBlob` <br/> |
    | `/encrypt` <br/> |Ten przełącznik włącza funkcję BitLocker dla dysku twardego. Ten parametr jest wymagany podczas pierwszego uruchomienia narzędzia WAImportExport.exe parametru.  <br/> Klucz szyfrowania Funkcji BitLocker jest kopiowany do pliku dziennika i pliku dziennika, który jest tworzony, jeśli używasz parametru  `/logfile:` . Jak wyjaśniono wcześniej, plik dziennika jest zapisywany w tym samym folderze, w którym WAImportExport.exe się narzędzie.  <br/> | `/encrypt` <br/> |
    | `/logdir:` <br/> |Ten parametr opcjonalny określa folder, w którym mają być zapisywanie plików dziennika. Jeśli nie zostanie określony, pliki dziennika są zapisywane w tym samym folderze, w którym WAImportExport.exe się narzędzie. Pamiętaj, aby owijać wartość tego parametru znakami podwójnego cudzysłowu (" ").  <br/> | `/logdir:"c:\users\admin\desktop\PstImportLogs"` <br/> |
   
    Poniżej podano przykład składni narzędzia narzędzia WAImportExport.exe z rzeczywistymi wartościami dla każdego parametru:
    
    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER01\PSTs" /dstdir:"ingestiondata/" blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"
    ```

    Po uruchomieniu polecenia są wyświetlane komunikaty o stanie, które pokazują postęp kopiowania plików PST na dysk twardy. Końcowy komunikat o stanie pokazuje łączną liczbę plików, które zostały pomyślnie skopiowane.
    
4. Uruchom to polecenie po każdym kolejnym uruchomieniu narzędzia WAImportExport.ext w celu skopiowania plików PST na ten sam dysk twardy.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 
    ```

    Oto przykład składni uruchamiania kolejnych sesji w celu skopiowania plików PST na ten sam dysk twardy.

    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER01\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

## <a name="step-3-create-the-pst-import-mapping-file"></a>Krok 3. Tworzenie pliku mapowania na importowanie pliku PST

Gdy pracownik centrum danych firmy Microsoft przekaże pliki PST z dysku twardego do obszaru usługi Azure Storage, usługa importowania użyje informacji z pliku mapowania importu plików PST, który jest plikiem wartości rozdzielanych przecinkami (CSV), określającym, do których skrzynek pocztowych użytkowników są importowane pliki PST. Ten plik CSV należy przesłać w następnym kroku podczas tworzenia zadania importu pliku PST.
  
1. [Pobierz kopię pliku mapowania importu pliku PST](https://go.microsoft.com/fwlink/p/?LinkId=544717).
    
2. Otwórz lub zapisz plik CSV na komputerze lokalnym. W poniższym przykładzie pokazano ukończony plik mapowania importu pliku PST (otwarty w Notatniku). Edytowanie pliku CSV Microsoft Excel znacznie łatwiejsze.

    ```text
    Workload,FilePath,Name,Mailbox,IsArchive,TargetRootFolder,ContentCodePage,SPFileContainer,SPManifestContainer,SPSiteUrl
    Exchange,FILESERVER01/PSTs,annb.pst,annb@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,annb_archive.pst,annb@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,FILESERVER01/PSTs,donh.pst,donh@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,donh_archive.pst,donh@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,FILESERVER01/PSTs,pilarp.pst,pilarp@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,pilarp_archive.pst,pilarp@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,,tonyk.pst,tonyk@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,tonyk_archive.pst,tonyk@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,,zrinkam.pst,zrinkam@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,zrinkam_archive.pst,zrinkam@contoso.onmicrosoft.com,TRUE,,,,,
    ```

    Pierwszy wiersz w pliku CSV, czyli wiersz nagłówka, zawiera parametry, które będą używane przez usługę importowania plików PST do importowania plików PST do skrzynek pocztowych użytkowników. Poszczególne nazwy parametrów są rozdzielone przecinkami. Każdy wiersz poniżej wiersza nagłówka odzwierciedla wartości parametrów importowania pliku PST do określonej skrzynki pocztowej. Potrzebujesz wiersza dla każdego pliku PST, który został skopiowany na dysk twardy. Pamiętaj, aby zamienić dane zastępcze w pliku mapowania na rzeczywiste dane.

    > [!NOTE]
    > Nie zmieniaj niczego w wierszu nagłówka, w tym SharePoint parametrów; zostaną one zignorowane podczas procesu importowania pliku PST. 
  
3. Za pomocą informacji w poniższej tabeli wypełnij plik CSV wymaganymi informacjami.
    
    |**Parametr**|**Opis**|**Przykład**|
    |:-----|:-----|:-----|
    | `Workload` <br/> |Określa usługę, do która ma zostać zaimportowana dane. Aby zaimportować pliki PST do skrzynek pocztowych użytkowników, użyj formatu  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> | Określa lokalizację folderu w obszarze usługi Azure Storage, do których pliki PST zostaną skopiowane po wysłaniu dysku twardego do firmy Microsoft.  <br/>  To, co dodasz w tej kolumnie w pliku CSV,  `/dstdir:` zależy od danych parametru podanych w poprzednim kroku. Jeśli w lokalizacji źródłowej znajdują się podfoldery, `FilePath` wartość parametru musi zawierać ścieżkę względną dla podfolderu, na przykład /folder1/user1/.  <br/>  Jeśli został użyty  `/dstdir:"ingestiondata/"`, ten parametr pozostaw pusty w pliku CSV.  <br/>  Jeśli do parametru  `/dstdir:` dołączona została opcjonalna nazwa_ścieżki (  `/dstdir:"ingestiondata/FILESERVER01/PSTs"`na przykład , użyj tej nazwy ścieżki (bez "ingestiondata") dla tego parametru w pliku CSV. W przypadku tego parametru jest w tym parametrze zróżnicowana wielkość liter.  <br/>  W obu sposób  *nie dołączaj*  parametru "ingestiondata" do  `FilePath` wartości parametru. Pozostaw ten parametr pusty lub określ tylko opcjonalną nazwę_ścieżki.  <br/> > [!IMPORTANT]> Przypadku nazwy  `/dstdir:` ścieżki pliku musi być taka sama jak w przypadku parametru określonego w poprzednim kroku. Jeśli na przykład  `"ingestiondata/FILESERVER01/PSTs"` w poprzednim kroku został użyty dla nazwy podfolderu,  `fileserver01/psts`  `FilePath` a następnie został on użyty w parametrze w pliku CSV, importowanie pliku PST nie powiedzie się. Pamiętaj, aby w obu przypadkach użyć tej samej sprawy.           |(pozostaw puste)  <br/> Lub  <br/>  `FILESERVER01/PSTs` <br/> |
    | `Name` <br/> |Określa nazwę pliku PST, który zostanie zaimportowany do skrzynki pocztowej użytkownika. W przypadku tego parametru jest w tym parametrze zróżnicowana wielkość liter.  <br/> > [!IMPORTANT]> Przypadku nazwy pliku PST w pliku CSV musi być taka sama jak plik PST, który został przekazany do lokalizacji usługi Azure Storage w kroku 2. Jeśli na przykład użyjemy parametru  `annb.pst`  `Name` w pliku CSV, ale nazwa rzeczywistego pliku PST to , importowanie tego pliku PST  `AnnB.pst`nie powiedzie się. Upewnij się, że nazwa pliku PST w pliku CSV ma taką samą nazwę jak rzeczywisty plik PST.           | `annb.pst` <br/> |
    | `Mailbox` <br/> |Określa adres e-mail skrzynki pocztowej, do która ma zostać zaimportowany plik PST. Nie można określić folderu publicznego, ponieważ usługa importowania plików PST nie obsługuje importowania plików PST do folderów publicznych.  <br/> Aby zaimportować plik PST do nieaktywnej skrzynki pocztowej, musisz określić identyfikator GUID skrzynki pocztowej dla tego parametru. Aby uzyskać ten identyfikator GUID, uruchom następujące polecenie programu PowerShell w programie Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> > [!NOTE]> Czasami może być wiele skrzynek pocztowych z tym samym adresem e-mail, gdzie jedna skrzynka pocztowa jest aktywna, a druga znajduje się w stanie "miękkiego usunięcia" (lub "nieaktywnego"). W takich sytuacjach musisz określić identyfikator GUID skrzynki pocztowej, aby jednoznacznie zidentyfikować skrzynkę pocztową do zaimportowania pliku PST. Aby uzyskać ten identyfikator GUID dla aktywnych skrzynek pocztowych, uruchom następujące polecenie programu PowerShell:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Aby uzyskać identyfikator GUID dla skrzynek pocztowych w sposób nieaktywny (lub nieaktywny), uruchom następujące polecenie:  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.           | `annb@contoso.onmicrosoft.com` <br/> Lub  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Określa, czy zaimportować plik PST do archiwaowej skrzynki pocztowej użytkownika. Dostępne są dwie opcje:  <br/> **FAŁSZ** Importuje plik PST do podstawowej skrzynki pocztowej użytkownika.  <br/> **TRUE (PRAWDA)** Importuje plik PST do archiwaowej skrzynki pocztowej użytkownika. Założono, że [jest włączona archiwalne skrzynka pocztowa użytkownika](enable-archive-mailboxes.md). Jeśli ten parametr zostanie ustawiony i  `TRUE` archiwalne skrzynka pocztowa użytkownika nie będzie włączona, importowanie dla tego użytkownika nie powiedzie się. Jeśli importowanie zakończy się niepowodzeniem dla jednego użytkownika (  `TRUE`ponieważ jego archiwum nie jest włączone, a ta właściwość jest ustawiona na ), nie będzie to mieć wpływu na innych użytkowników w zadaniu importu.  <br/>  Jeśli pozostawisz ten parametr pusty, plik PST zostanie zaimportowany do podstawowej skrzynki pocztowej użytkownika.  <br/> **Uwaga:** Aby zaimportować plik PST do archiwaowej skrzynki pocztowej w chmurze dla użytkownika, którego podstawowa skrzynka pocztowa jest lokalna,  `TRUE` wystarczy określić dla tego parametru adres e-mail  `Mailbox` lokalnej skrzynki pocztowej użytkownika.  <br/> | `FALSE` <br/> Lub  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Określa folder skrzynki pocztowej, do których jest importowany plik PST.  <br/>  Jeśli pozostawisz ten parametr pusty, plik PST zostanie zaimportowany do nowego folderu o nazwie **Importowane** znajdującego się na poziomie głównym skrzynki pocztowej (na tym samym poziomie co folder Skrzynka odbiorcza i inne domyślne foldery skrzynek pocztowych).  <br/>  Jeśli określisz  `/`, elementy z pliku PST zostaną zaimportowane bezpośrednio do folderu Skrzynka odbiorcza użytkownika.  <br/>  Jeśli określisz  `/<foldername>`, elementy w pliku PST zostaną zaimportowane do folderu o nazwie  *\<foldername\>*. Na przykład w przypadku użycia pozycji  `/ImportedPst`, elementy zostaną zaimportowane do folderu o nazwie **ImportedPst**. Ten folder będzie znajdował się w skrzynce pocztowej użytkownika na tym samym poziomie, na którym znajduje się folder Skrzynka odbiorcza.  <br/> |(pozostaw puste)  <br/> Lub  <br/>  `/` <br/> Lub  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Ten parametr opcjonalny określa wartość liczbową dla strony kodowej do zaimportowania plików PST w formacie PLIKU ANSI. Ten parametr jest używany do importowania plików PST z organizacji chińskich, japońskich i koreańskich (CJK), ponieważ w tych językach kodowanie znaków jest zazwyczaj używane w zestawie znaków dwu bajtowych (DBCS). Jeśli ten parametr nie jest używany do importowania plików PST dla języków, w których dbcs są używane do nazw folderów skrzynek pocztowych, nazwy folderów są często zniekształcone po ich zaimportowaniu.  <br/> Aby uzyskać listę obsługiwanych wartości do użycia dla tego parametru, zobacz [Identyfikatory strony kodowej](/windows/win32/intl/code-page-identifiers).  <br/> > [!NOTE]> Jak wspomniano wcześniej, jest to parametr opcjonalny i nie trzeba go uwzględniać w pliku CSV. Możesz też ją dołączyć i pozostawić wartość pustą dla jednego lub większej liczby wierszy.           |(pozostaw puste)  <br/> Lub  <br/>  `932` (który jest identyfikatorem strony kodowej ANSI/OEM w języku japońskim)  <br/> |
    | `SPFileContainer` <br/> |W przypadku importowania pliku PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |
    | `SPManifestContainer` <br/> |W przypadku importowania pliku PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |
    | `SPSiteUrl` <br/> |W przypadku importowania pliku PST pozostaw ten parametr pusty.  <br/> |Nie dotyczy  <br/> |

## <a name="step-4-create-a-pst-import-job-in-office-365"></a>Krok 4. Tworzenie zadania importu pliku PST w programie Office 365

Następnym krokiem jest utworzenie zadania importowania pliku PST w usłudze importowania w programie Office 365. Jak wyjaśniono wcześniej, przesyłasz plik mapowania importowania pliku PST utworzony w kroku 3. Po utworzeniu zadania usługa importowania użyje informacji z pliku mapowania do zaimportowania plików PST do określonej skrzynki pocztowej użytkownika po skopiowaniu plików PST z dysku twardego do obszaru usługi Azure Storage i utworzysz i uruchamiasz zadanie importu.
  
1. Przejdź do <https://compliance.microsoft.com> konta administratora w organizacji i zaloguj się przy użyciu poświadczeń administratora.

2. W okienku nawigacji po lewej stronie okna Centrum zgodności platformy Microsoft 365 pozycję **Importowanie zarządzania informacjami**\>.

3. Na karcie **Importowanie** kliknij pozycję ![Dodaj ikonę.](../media/ITPro-EAC-AddIcon.gif) **Nowe zadanie importu**.

    > [!NOTE]
    > Jak wspomniano wcześniej, musisz mieć odpowiednie uprawnienia, aby uzyskać dostęp do strony **Importowanie** w Centrum zgodności platformy Microsoft 365.
  
4. Wpisz nazwę zadania importu pliku PST, a następnie kliknij przycisk **Dalej**. Używaj małych liter, cyfr, łączników i podkreśleń. Nie można używać wielkich liter ani dołączać w nazwie spacji.

5. Na stronie **Wybierz typ zadania importu** kliknij pozycję Wyślij dyski **twarde** do jednego z naszych lokalizacji fizycznych, a następnie kliknij przycisk **Dalej**.
  
6. W kroku 6 kliknij pole wyboru Przygotuję moje dyski twarde i mam dostęp do niezbędnych plików dziennika dysków. Mam też  dostęp do pliku mapowania, a następnie kliknij przycisk **Dalej**.

    ![Kliknij dwa pola wyboru w kroku 6.](../media/fad43078-ea68-4acd-b2ed-75a800183262.png)
  
7. Na stronie **Wybierz plik dysku** kliknij pozycję Wybierz plik **dysku, a** następnie przejdź do tego samego folderu, w którym znajduje się WAImportExport.exe dysku. Plik dziennika utworzony w kroku 2 został skopiowany do tego folderu.

    ![Kliknij pozycję Wybierz plik dysku, aby przesłać plik dziennika utworzony po uruchomieniu WAImportExport.exe dysku.](../media/1ea35c04-bd88-4d7e-b7d9-dc390149d94f.png)
  
8. Wybierz plik dziennika. na przykład `PSTHDD1.jrn`.

    > [!TIP]
    > Po narzędziu WAImportExport.exe kroku 2 nazwa pliku dziennika została określona przez parametr  `/j:` .
  
9. Gdy nazwa pliku dysku pojawi się w obszarze Nazwa **pliku** dysku, kliknij przycisk  Sprawdź poprawność, aby sprawdzić, czy plik dysku nie zawiera błędów.

    ![Kliknij przycisk Sprawdź poprawność, aby sprawdzić poprawność wybranego pliku dysku.](../media/4b707f5a-152a-4e74-b9f5-449c88d1fec4.png)
  
    Aby utworzyć zadanie importowania pliku PST, należy pomyślnie zweryfikować plik dysku. Po pomyślnym weryfikacji nazwa pliku zmieni się na zieloną. Jeśli sprawdzanie poprawności zakończy się niepowodzeniem, kliknij link **Wyświetl** dziennik. Zostanie otwarty raport o błędach sprawdzania poprawności z komunikatem o błędzie z informacją o tym, dlaczego plik nie powiódł się. 

    > [!NOTE]
    > Musisz dodać i zweryfikować plik dziennika dla każdego dysku twardego, który wysyłasz do firmy Microsoft. 
  
10. Po dodaniu i sprawdzania poprawności pliku dziennika dla każdego dysku twardego, który jest wysyłany do firmy Microsoft, kliknij przycisk **Dalej**.
    
11. Kliknij ![pozycję Dodaj ikonę.](../media/ITPro-EAC-AddIcon.gif) **Wybierz plik mapowania,** aby przesłać plik mapowania importu plików PST utworzony w kroku 3. 

    ![Kliknij pozycję Wybierz plik mapowania, aby przesłać utworzony plik CSV dla zadania importu.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
12. Gdy nazwa pliku CSV zostanie wyświetlona w obszarze Nazwa pliku **mapowania, kliknij** pozycję Sprawdź poprawność, aby sprawdzić, czy plik CSV nie zawiera błędów. 

    ![Kliknij przycisk Sprawdź poprawność, aby sprawdzić, czy plik CSV nie zawiera błędów.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    Aby utworzyć zadanie importowania pliku PST, należy pomyślnie zweryfikować plik CSV. Po pomyślnym weryfikacji nazwa pliku zmieni się na zieloną. Jeśli sprawdzanie poprawności zakończy się niepowodzeniem, kliknij link **Wyświetl** dziennik. Zostanie otwarty raport o błędach sprawdzania poprawności z komunikatem o błędzie dla każdego wiersza w pliku, który nie powiódł się. 

13. Po pomyślnym weryfikacji pliku mapowania plików PST kliknij przycisk **Dalej**.

14. Na stronie **Podaj informacje kontaktowe** wpisz swoje informacje kontaktowe w odpowiednich polach. 

    Zostanie wyświetlony adres lokalizacji firmy Microsoft, do która jest wysyłana na Twoje dyski twarde. Ten adres jest generowany automatycznie na podstawie lokalizacji centrum danych firmy Microsoft. Skopiuj ten adres do pliku lub zrób zrzut ekranu.

15. Przeczytaj dokument warunków i postanowień, kliknij pole wyboru, a następnie **kliknij przycisk Zapisz** , aby przesłać zadanie importu. 

    Po pomyślnym utworzeniu zadania importu zostanie wyświetlona strona stanu z wyjaśnieniem kolejnych kroków procesu wysyłki dysku.

16. Na karcie **Importowanie** kliknij ikonę ![Odśwież.](../media/O365-MDM-Policy-RefreshIcon.gif) **Odśwież** , aby wyświetlić nowe zadanie importu wysyłki dysków na liście zadań importu. Ma on wartość **Oczekiwanie na śledzenie numeru**. Możesz także kliknąć zadanie importu, aby wyświetlić stronę wysuwu stanu zawierającą bardziej szczegółowe informacje o zadaniu importu.

## <a name="step-5-ship-the-hard-drive-to-microsoft"></a>Krok 5. Wysyłka dysku twardego do firmy Microsoft

Następnym krokiem jest dostarczenie dysku twardego do firmy Microsoft, a następnie podanie numeru śledzenia wysyłki i wysyłki zwrotu dla zadania wysyłki dysków. Po otrzymaniu dysku przez firmę Microsoft przekazanie plików PST do usługi Azure Storage dla organizacji może potrwać od 7 do 10 dni roboczych.
  
> [!NOTE]
> Jeśli numer śledzenia i informacje o wysyłki nie zostaną podane w ciągu 14 dni od utworzenia zadania importu, zadanie importu utraci ważność. W takim przypadku musisz utworzyć nowe zadanie importu wysyłki dysków (zobacz Krok 4. Tworzenie zadania importu [pliku PST](#step-4-create-a-pst-import-job-in-office-365) w programie Office 365) i ponownie przesłać plik dysku i plik mapowania importu pliku PST.
  
### <a name="ship-the-hard-drive"></a>Wyślij dysk twardy

Podczas wysyłki dysków twardych do firmy Microsoft należy pamiętać o następujących kwestiach:
  
- Nie wysyłaj karty SATA-to-USB; musisz jedynie wysłać dysk twardy.

- Należy prawidłowo spakować dysk twardy; na przykład użyj nieskuchatycznych toczek lub zawijania bąbelków.

- Użyj wybranego operatora dostawy do wysłania dysku twardego do firmy Microsoft.

- Wyślij dysk twardy pod adres lokalizacji firmy Microsoft, która była wyświetlana podczas tworzenia zadania importu w kroku 4. Pamiętaj, aby w adresie wysyłki uwzględnić Office 365 "Usługa importu importu".

- Po wysłaniu dysku twardego zapisz nazwę operatora dostawy i numer śledzenia. Podasz je w następnym kroku.
    
### <a name="enter-the-tracking-number-and-other-shipping-information"></a>Wprowadź numer śledzenia i inne informacje wysyłkowe

Po wysłaniu dysku twardego do firmy Microsoft wykonaj poniższe czynności na stronie Importowanie usługi.
  
1. Przejdź do <https://compliance.microsoft.com> konta administratora w organizacji i zaloguj się przy użyciu poświadczeń administratora.

2. W okienku nawigacji po lewej stronie okna Centrum zgodności platformy Microsoft 365 pozycję **Zarządzanie informacjami > importowania**.

3. Na **karcie Importowanie** kliknij zadanie wysyłki dysku, dla którego chcesz wprowadzić numer śledzenia.

4. Na stronie wysuwu stanu kliknij pozycję **Wprowadź numer śledzenia**.

5. Podaj następujące informacje wysyłkowe:

   1. **Operator dostawy** Wpisz nazwę operatora dostawy użytego do wysłania dysku twardego do firmy Microsoft. 

   2. **Numer śledzenia** Wpisz numer śledzenia przesyłki z dyskiem twardym. 

   3. **Numer konta operatora zwrotu** Wpisz numer konta organizacji dla operatora wymienionego w obszarze **Zwrotny operator**. Firma Microsoft używa tego konta (i nalicza opłaty) do wysłania Twojego dysku twardego z powrotem do Ciebie. Organizacje w USA i Europie muszą mieć konto w fedex. Organizacje w Azji i na świecie muszą mieć konto w DHL.

6. Kliknij **przycisk Zapisz** , aby zapisać te informacje dla zadania importu. 

    Na karcie **Importowanie** kliknij ikonę ![Odśwież.](../media/O365-MDM-Policy-RefreshIcon.gif) **Odśwież** , aby zaktualizować informacje dotyczące zadania importu wysyłki dysków. Zwróć uwagę, że stan jest teraz ustawiony na Dyski **podczas przesyłania**.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Krok 6. Filtrowanie danych i uruchamianie zadania importowania pliku PST

Po otrzymaniu dysku twardego przez firmę Microsoft stan zadania importu na stronie Importowanie plików **PST** zmieni się na **Dyski odebrane**. Pracownicy centrum danych używają informacji z pliku dziennika do przekazywania plików PST do Storage Azure dla organizacji. Na tym etapie stan zmieni się na **Importowanie w toku**. Jak wspomniano wcześniej, przekazanie plików PST będzie potrwać od 7 do 10 dni roboczych po otrzymaniu dysku twardego.
  
Po przesłaniu plików PST do platformy Azure stan zmienia się na **Analiza w toku**. Oznacza to Microsoft 365 analizuje dane w plikach PST (w bezpieczny sposób) w celu zidentyfikowania wieku elementów i poszczególnych typów wiadomości zawartych w plikach PST. Po zakończeniu analizy i przygotowaniu danych do zaimportowania stan zadania importu zmienia się na **Ukończono analizę**. W tym momencie możesz zaimportować wszystkie dane zawarte w plikach PST lub przyciąć zaimportowane dane, ustawiając filtry sterujące tym, które dane są importowane.
  
1. Przejdź do <https://compliance.microsoft.com> konta administratora w organizacji i zaloguj się przy użyciu poświadczeń administratora.

2. W lewym okienku nawigacji okna Centrum zgodności platformy Microsoft 365 pozycję **Zarządzanie informacjami** \> **Importowanie****.

3. Na **karcie Importowanie** wybierz zadanie importu utworzone w kroku 4, a następnie kliknij pozycję **Importuj, aby Office 365**.
  
    Zostanie wyświetlona wysuwana strona z informacjami o plikach PST i innymi informacjami na temat zadania importu.

4. Kliknij **pozycję Importuj do Office 365**.

5. Zostanie **wyświetlona strona Filtrowanie** danych. Zawiera szczegółowe informacje na temat danych wynikające z analizy przeprowadzonej na plikach PST przez Office 365, łącznie z informacjami o wieku danych. W tym momencie możesz filtrować dane, które zostaną zaimportowane lub zaimportować wszystkie dane w stanie takim, w którym są. 

    ![Możesz przyciąć dane w plikach PST lub zaimportować je wszystkie.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
6. Wykonaj jeden z następujących kroków:

   1. Aby przyciąć importowane dane, kliknij pozycję **Tak, chcę je filtrować przed zaimportowaniem**.

      Aby uzyskać szczegółowe instrukcje krok po kroku dotyczące filtrowania danych w plikach PST, a następnie rozpoczynania zadania importowania, zobacz Filtrowanie danych podczas importowania plików [PST](filter-data-when-importing-pst-files.md) w celu Office 365.

      Lub

   1. Aby zaimportować wszystkie dane z plików PST, kliknij pozycję **Nie, chcę zaimportować wszystko, a** następnie kliknij przycisk **Dalej**.

7. Jeśli wybrano importowanie wszystkich danych, kliknij pozycję **Importuj dane** , aby rozpocząć zadanie importowania. 

    Stan zadania importu jest wyświetlany na stronie **Importowanie plików PST** . Kliknij ikonę ![Odśwież.](../media/O365-MDM-Policy-RefreshIcon.gif) **Odśwież** , aby zaktualizować informacje o statusie wyświetlane w **kolumnie Stan** . Kliknij zadanie importu, aby wyświetlić stronę wysuwu stanu z informacjami o stanie każdego importowanego pliku PST. Po zakończeniu importowania i zaimportowaniu plików PST do skrzynek pocztowych użytkowników stan zmieni się na **Ukończono**.

## <a name="view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>Wyświetlanie listy plików PST przekazanych do Microsoft 365

Za pomocą narzędzia Eksplorator usługi Microsoft Azure Storage (bezpłatnego narzędzia typu open source) można wyświetlić listę plików PST przekazanych przez nas (przez pracowników centrum danych firmy Microsoft) do obszaru usługi Azure Storage dla organizacji. Możesz to zrobić, aby sprawdzić, czy pliki PST z dysków twardych wysłanych do firmy Microsoft zostały pomyślnie przekazane do obszaru usługi Azure Storage dysków.
  
> [!IMPORTANT]
> Za pomocą tego pliku nie można Eksplorator usługi Azure Storage ani modyfikować plików PST. Jedyną obsługiwaną metodą importowania plików PST do Microsoft 365 jest użycie azcopy. Ponadto nie można usunąć plików PST przekazanych do obiektu blob platformy Azure. Jeśli spróbujesz usunąć plik PST, zostanie wyświetlony komunikat o błędzie z informacjami o tym, że nie masz wymaganych uprawnień. Wszystkie pliki PST są automatycznie usuwane z Storage Azure. Jeśli nie ma zadań importu w toku, wszystkie pliki PST w kontenerze ** ingestiondata ** zostaną usunięte 30 dni po utworzeniu najnowszego zadania importu.
  
Wykonaj poniższe czynności, aby uzyskać adres URL sas (Shared Access Signature) dla organizacji. Ten adres URL jest połączeniem sieciowego adresu URL dla usługi Azure Storage lokalizacji w chmurze firmy Microsoft dla organizacji i klucza SAS. Ten klucz zapewnia uprawnienia niezbędne do uzyskiwania dostępu do lokalizacji usługi Azure Storage Twojej organizacji.

Aby zainstalować Eksplorator usługi Azure Storage i połączyć się z obszarem usługi Azure Storage sieci:

1. Przejdź do <https://compliance.microsoft.com> konta administratora w organizacji i zaloguj się przy użyciu poświadczeń administratora.

2. W okienku po lewej stronie okna Centrum zgodności platformy Microsoft 365 pozycję **Zarządzanie informacjami > importowania**.

3. Na karcie **Importowanie** kliknij pozycję ![Dodaj ikonę.](../media/ITPro-EAC-AddIcon.gif) **Nowe zadanie importu**.

4. W Kreatorze zadań importu wpisz nazwę zadania importu pliku PST, a następnie kliknij przycisk **Dalej**. Używaj małych liter, cyfr, łączników i podkreśleń. Nie można używać wielkich liter ani dołączać w nazwie spacji.

5. Na stronie **Wybierz typ zadania importu** kliknij pozycję **Upload** danych, a następnie kliknij przycisk **Dalej**.

6. W kroku 2 kliknij pozycję **Pokaż adres URL SAS przekazywania sieciowego**.

7. Po wyświetlaniu adresu URL skopiuj go i zapisz w pliku. Pamiętaj, aby skopiować cały adres URL.

    > [!IMPORTANT]
    > Pamiętaj o podjęciu środków ostrożności w celu ochrony adresu URL SAS. Może z niego korzystać każdy, kto ma dostęp do obszaru magazynu platformy Azure dla Twojej organizacji.
  
8. Kliknij **przycisk Anuluj** , aby zamknąć Kreatora zadań importu.

9. Pobierz i zainstaluj [Eksplorator usługi Microsoft Azure Storage narzędzia](https://go.microsoft.com/fwlink/p/?LinkId=544842).

10. Uruchom okno Eksplorator usługi Microsoft Azure Storage kliknij prawym przyciskiem myszy pozycję Storage **Konta w** lewym okienku, a następnie kliknij polecenie Połączenie do usługi **Azure Storage**.

    ![Kliknij prawym przyciskiem myszy Storage Konta użytkowników, a następnie kliknij polecenie Połączenie do usługi Azure Storage.](../media/75b80cc3-c336-4f96-ad32-54ac9b96a7af.png)
  
11. Kliknij **pozycję Użyj podpisu dostępu udostępnionego (SAS) URI lub parametrów połączenia i** kliknij przycisk **Dalej**.

12. Kliknij **pozycję Użyj URI SAS**, wklej adres URL SAS uzyskany w kroku 1 do w polu w obszarze **URI**, a następnie kliknij przycisk **Dalej**.

13. Na **stronie Podsumowanie połączenia** możesz przejrzeć informacje o połączeniu, a następnie kliknąć przycisk **Połączenie**.

    Zostanie **otwarty kontener ingestiondata** . Zawiera on pliki PST z dysku twardego. Kontener **ingestiondata** znajduje się w Storage obiektów **blob** **kont** \> **(sas-attached services**\>).

    ![Eksplorator usługi Azure Storage zostanie wyświetlona lista przekazanych plików PST.](../media/12376fed-13a5-4a09-8fe6-e819e011b334.png)
  
14. Po zakończeniu korzystania z aplikacji Eksplorator usługi Microsoft Azure Storage kliknij prawym przyciskiem myszy **ingestiondata**, a następnie kliknij polecenie Odłącz, aby  odłączyć się od platformy Azure Storage obszarze. W przeciwnym razie przy następnej próbie dołączenia otrzymasz komunikat o błędzie. 

    ![Kliknij prawym przyciskiem myszy pozycję ingestion i kliknij polecenie Odłącz, aby rozłączyć się z obszarem Storage Azure.](../media/1e8e5e95-4215-4ce4-a13d-ab5f826a0510.png)

## <a name="troubleshooting-tips"></a>Porady dotyczące rozwiązywania problemów

- **Co się stanie, jeśli zadanie importu zakończy się niepowodzeniem z powodu błędów w pliku mapowania importu pliku PST?** Jeśli zadanie importu nie powiedzie się z powodu błędów w pliku mapowania, nie musisz ponownie przetworzyć dysku twardego do firmy Microsoft, aby utworzyć zadanie importu. Jest tak, ponieważ pliki PST z dysku twardego przesłane do zadania importu wysyłki dysków zostały już przekazane do obszaru usługi Azure Storage dla Organizacji. W takim przypadku wystarczy poprawić błędy w pliku mapowania importowania pliku CSV pliku PST, a następnie utworzyć nowe zadanie importu "przekazywanie sieciowe" i przesłać poprawiony plik mapowania plików CSV. Aby utworzyć i rozpocząć nowe zadanie importu przekazywania sieciowego, zobacz Krok [5.](use-network-upload-to-import-pst-files.md#step-5-create-a-pst-import-job) Tworzenie zadania importu pliku PST w programach Microsoft 365 i [Krok 6.](use-network-upload-to-import-pst-files.md#step-6-filter-data-and-start-the-pst-import-job) Filtrowanie danych i uruchamianie zadania importowania pliku PST w temacie "Importowanie plików PST za pomocą przekazywania sieciowego do importowania plików PST Office 365". 
    
    > [!NOTE]
    > Aby ułatwić rozwiązywanie problemów z plikiem mapowania importów plików PST na pliki CSV, użyj narzędzia [Eksplorator usługi Azure Storage](#view-a-list-of-the-pst-files-uploaded-to-microsoft-365) do wyświetlenia struktury folderów w kontenerze **ingestiondata** dla plików PST z dysku twardego, który został przekazany do obszaru magazynu platformy Azure. Błędy plików mapowania są zwykle spowodowane niepoprawną wartością parametru FilePath. Ten parametr określa lokalizację pliku PST w obszarze magazynu platformy Azure. Zobacz opis parametru FilePath w tabeli w [kroku 3](#step-3-create-the-pst-import-mapping-file). Jak wyjaśniono wcześniej, lokalizacja plików PST w obszarze magazynu platformy Azure  `/dstdir:` została określona przez parametr podczas korzystania z narzędzia do WAImportExport.exe w [kroku 2](#step-2-copy-the-pst-files-to-the-hard-drive). 
  
## <a name="more-information"></a>Więcej informacji

- Wysyłka dysków to skuteczny sposób importowania dużych ilości archiwalnych danych wiadomości Microsoft 365 w celu skorzystania z funkcji zgodności dostępnych dla Twojej organizacji. Po zaimportowaniu zarchiwizowanych danych do skrzynek pocztowych użytkowników możesz:

  - Włącz [archiwalne skrzynki pocztowe](enable-archive-mailboxes.md) i [automatyczne rozszerzanie archiwizacji](enable-autoexpanding-archiving.md) , aby zapewnić użytkownikom więcej miejsca do magazynowania danych w skrzynce pocztowej. 

  - Umieszczaj skrzynki pocztowe [w postępowaniem sądowym w](./create-a-litigation-hold.md) celu zachowania danych. 

  - Przeszukiwanie [danych przy użyciu narzędzi zbierania](search-for-content.md) elektronicznych materiałów dowodowych firmy Microsoft. 

  - Zastosuj [Microsoft 365 przechowywania,](retention.md) aby kontrolować, jak długo dane są przechowywane i jakie działania należy podjąć po wygaśnięciu okresu przechowywania. 

  - Wyszukaj [w dzienniku inspekcji](search-the-audit-log-in-security-and-compliance.md) zdarzenia związane z danymi. 

  - Zaimportuj [dane do nieaktywnych skrzynek pocztowych](inactive-mailboxes-in-office-365.md) , aby zarchiwizować dane w celu zachowania zgodności z przepisami. 

  - Chroń swoją organizację [przed utratą danych poufnych](dlp-learn-about-dlp.md) . 

- Oto przykład bezpiecznego klucza konta magazynu i klucza szyfrowania funkcji BitLocker. Ten przykład również zawiera składnię polecenia polecenia WAImportExport.exe służącego do kopiowania plików PST na dysk twardy. Pamiętaj o podjęciu środków ostrożności w celu ochrony tych haseł i innych informacji związanych z bezpieczeństwem.

    ```text
    Secure storage account key: 

    yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ==

    BitLocker encryption key:

    397386-221353-718905-535249-156728-127017-683716-083391

  COMMAND SYNTAX

  First time:

  WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob /encrypt /logdir:<Log file location>

  Subsequent times:

  WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 

  EXAMPLES

  First time:

  WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER1\PSTs" /dstdir:"ingestiondata/"
  /blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"

  Subsequent times:

  WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER1\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

- Jak wyjaśniono wcześniej, Office 365 import usługi włącza ustawienie blokowania przechowywania (na czas nieograniczony) po zaimportowaniu plików PST do skrzynki pocztowej. Oznacza to,  *że właściwość RentionHoldEnabled*  `True` jest tak ustawiona, że zasady przechowywania przypisane do skrzynki pocztowej nie są przetwarzane. Dzięki temu właściciel skrzynki pocztowej może zarządzać nowo zaimportowaną wiadomością, uniemożliwiając usuwanie lub archiwizowanie starszych wiadomości przez zasady usuwania lub archiwizacji. Oto kilka czynności, które możesz wykonać, aby zarządzać tym przechowywaniem: 

  - Po określonym czasie możesz wyłączyć przechowywanie, uruchamiając polecenie  `Set-Mailbox -RetentionHoldEnabled $false` . Aby uzyskać instrukcje, [zobacz Umieść skrzynkę pocztową w miejscu przechowywania](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Możesz skonfigurować przechowywanie w taki sposób, aby w przyszłości było ono wyłączone w przyszłości. Możesz to zrobić, uruchamiając  `Set-Mailbox -EndDateForRetentionHold <date>` to polecenie. Na przykład przy założeniu, że dzisiejszą datą jest 1 czerwca 2016 r. i chcesz wyłączyć przechowywanie w ciągu 30 dni, możesz uruchomić następujące polecenie:  `Set-Mailbox -EndDateForRetentionHold 7/1/2016`. W tym scenariuszu właściwość  *RentionHoldEnabled*  należy ustawić na  *wartość True*. Aby uzyskać więcej informacji, zobacz [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Możesz zmienić ustawienia zasad przechowywania przypisanych do skrzynki pocztowej, aby starsze elementy, które zostały zaimportowane, nie były natychmiast usuwane ani przenoszone do archiwaowej skrzynki pocztowej użytkownika. Można na przykład wydłużyć wiek przechowywania dla zasad usuwania lub archiwizacji przypisanych do skrzynki pocztowej. W tym scenariuszu można wyłączyć przechowywanie w skrzynce pocztowej po zmianie ustawień zasad przechowywania. Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad archiwizacji i usuwania dla skrzynek pocztowych w organizacji](set-up-an-archive-and-deletion-policy-for-mailboxes.md).
