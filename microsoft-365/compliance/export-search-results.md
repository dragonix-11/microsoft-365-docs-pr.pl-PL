---
title: Eksportowanie wyników wyszukiwania zawartości
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExport
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ed48d448-3714-4c42-85f5-10f75f6a4278
description: Wyeksportuj wyniki wyszukiwania z wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview na komputer lokalny. Wyniki wiadomości e-mail są eksportowane jako pliki PST. Zawartość z witryn SharePoint i OneDrive dla Firm jest eksportowana jako natywne dokumenty Office.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 38faaf29087e67aef161e46a1fbc6c338d9c33e4
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995475"
---
# <a name="export-content-search-results"></a>Eksportowanie wyników wyszukiwania zawartości

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po pomyślnym uruchomieniu wyszukiwania zawartości można wyeksportować wyniki wyszukiwania na komputer lokalny. Podczas eksportowania wyników wiadomości e-mail są one pobierane na komputer jako pliki PST. Podczas eksportowania zawartości z witryn SharePoint i OneDrive dla Firm eksportowane są kopie natywnych dokumentów Office. Istnieją inne dokumenty i raporty dołączone do wyeksportowanych wyników wyszukiwania.
  
Eksportowanie wyników wyszukiwania zawartości polega na przygotowaniu wyników, a następnie pobraniu ich na komputer lokalny. Te kroki eksportowania wyników wyszukiwania dotyczą również eksportowania wyników wyszukiwania skojarzonego z przypadkami zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Standard).
  
## <a name="before-you-export-search-results"></a>Przed wyeksportowaniem wyników wyszukiwania

- Aby wyeksportować wyniki wyszukiwania, musisz mieć przypisaną rolę zarządzania eksportem w portalu zgodności usługi Microsoft Purview. Ta rola jest przypisywana do wbudowanej grupy ról menedżera zbierania elektronicznych materiałów dowodowych. Nie jest ona domyślnie przypisana do grupy ról Zarządzanie organizacją. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- Komputer używany do eksportowania wyników wyszukiwania musi spełniać następujące wymagania systemowe:
  
  - Najnowsza wersja Windows (32-bitowa lub 64-bitowa)
  
  - Microsoft .NET Framework w wersji 4.7 lub nowszej
  
- Aby uruchomić narzędzie eksportu elektronicznego zbierania elektronicznych materiałów dowodowych, musisz użyć Microsoft Edge <sup>1</sup>. Eksportowanie wyników wyszukiwania przy użyciu programu Internet Explorer 11 nie jest już <sup>obsługiwane2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> W wyniku ostatnich zmian Microsoft Edge obsługa ClickOnce nie jest już domyślnie włączona. Aby uzyskać instrukcje dotyczące włączania obsługi ClickOnce w przeglądarce Edge, zobacz [Use the eDiscovery Export Tool in Microsoft Edge (Używanie narzędzia eksportu zbierania elektronicznych](configure-edge-to-export-search-results.md) materiałów dowodowych w Microsoft Edge). Ponadto firma Microsoft nie produkuje rozszerzeń ani dodatków innych firm dla aplikacji ClickOnce. Eksportowanie wyników wyszukiwania przy użyciu nieobsługiwanej przeglądarki z rozszerzeniami lub dodatkami innych firm nie jest obsługiwane.
  >
  > <sup>2</sup> Począwszy od sierpnia 2021 r., Microsoft 365 aplikacje i usługi nie będą już obsługiwać programu Internet Explorer 11 (IE11), a użytkownicy mogą mieć obniżoną wydajność lub nie mogą łączyć się z tymi aplikacjami i usługami. Te aplikacje i usługi będą stopniowo wycofywane w nadchodzących tygodniach i miesiącach, aby zapewnić bezproblemowe zakończenie wsparcia. Każda aplikacja i usługa są wycofywane w niezależnych harmonogramach. Aby uzyskać więcej informacji, zobacz ten [wpis w blogu](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Narzędzie eksportu zbierania elektronicznych materiałów dowodowych używane w kroku 2 do pobierania wyników wyszukiwania nie obsługuje automatyzacji (przy użyciu skryptu lub uruchomionych poleceń cmdlet). Zdecydowanie zalecamy, aby nie automatyzować procesu przygotowywania w kroku 1 ani w procesie pobierania w kroku 2. Jeśli zautomatyzujesz jeden z tych procesów, pomoc techniczna firmy Microsoft nie zapewni pomocy w przypadku wystąpienia problemów.

- Zalecamy pobranie wyników wyszukiwania na komputer lokalny. Aby wyeliminować zaporę lub infrastrukturę serwera proxy firmy z powodu problemów podczas pobierania wyników wyszukiwania, możesz rozważyć pobranie wyników wyszukiwania na pulpit wirtualny poza siecią. Może to zmniejszyć limity czasu występujące w połączeniach danych platformy Azure podczas eksportowania dużej liczby plików. Aby uzyskać więcej informacji na temat pulpitów wirtualnych, zobacz [Windows Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop).

- Aby zwiększyć wydajność podczas pobierania wyników wyszukiwania, rozważ podzielenie wyszukiwań zwracających duży zestaw wyników na mniejsze wyszukiwania. Można na przykład użyć zakresów dat w zapytaniach wyszukiwania, aby zwrócić mniejszy zestaw wyników, które można pobrać szybciej.
  
- Podczas eksportowania wyników wyszukiwania dane są tymczasowo przechowywane w lokalizacji Storage platformy Azure dostarczonej przez firmę Microsoft w chmurze firmy Microsoft przed pobraniem ich na komputer lokalny. Upewnij się, że twoja organizacja może nawiązać połączenie z punktem końcowym na platformie Azure, czyli **\*.blob.core.windows.net** (symbol wieloznaczny reprezentuje unikatowy identyfikator eksportu). Dane wyników wyszukiwania są usuwane z lokalizacji usługi Azure Storage dwa tygodnie po ich utworzeniu. 
  
- Jeśli organizacja używa serwera proxy do komunikowania się z Internetem, musisz zdefiniować ustawienia serwera proxy na komputerze używanym do eksportowania wyników wyszukiwania (aby narzędzie eksportu było uwierzytelniane przez serwer proxy). W tym celu otwórz plik *machine.config* w lokalizacji zgodnej z wersją Windows. 
  
  - **32-bitowe:** `%windir%\Microsoft.NET\Framework\[version]\Config\machine.config`
  
  - **64-bitowe:** `%windir%\Microsoft.NET\Framework64\[version]\Config\machine.config`
  
    Dodaj następujące wiersze do pliku  *machine.config*  gdzieś między  `<configuration>` tagami i  `</configuration>` . Pamiętaj, aby zastąpić  `ProxyServer` elementy i  `Port` odpowiednimi wartościami dla organizacji, `proxy01.contoso.com:80`na przykład . 
  
    ```xml
    <system.net>
       <defaultProxy enabled="true" useDefaultCredentials="true">
         <proxy proxyaddress="https://ProxyServer :Port " 
                usesystemdefault="False" 
                bypassonlocal="True" 
                autoDetect="False" />
       </defaultProxy>
    </system.net>
    ```

- Jeśli wyniki wyszukiwania są starsze niż 7 dni i przesyłasz zadanie eksportu, zostanie wyświetlony komunikat o błędzie z monitem o ponowne uruchomienie wyszukiwania w celu zaktualizowania wyników wyszukiwania. W takim przypadku anuluj eksport, uruchom ponownie wyszukiwanie, a następnie ponownie rozpocznij eksport.

## <a name="step-1-prepare-search-results-for-export"></a>Krok 1. Przygotowywanie wyników wyszukiwania do eksportu

Pierwszym krokiem jest przygotowanie wyników wyszukiwania do eksportowania. Podczas przygotowywania wyników są one przekazywane do lokalizacji Storage platformy Azure dostarczanej przez firmę Microsoft w chmurze firmy Microsoft. Zawartość ze skrzynek pocztowych i witryn jest przekazywana z maksymalną szybkością 2 GB na godzinę.
  
1. W portalu zgodności wybierz wyszukiwanie zawartości, z których chcesz wyeksportować wyniki.
  
2. W menu **Akcje** w dolnej części strony wysuwanej kliknij pozycję **Eksportuj wyniki**.

   ![Opcja Eksportuj wyniki w menu Akcje.](../media/ActionMenuExportResults.png)

   Zostanie wyświetlona strona wysuwanego **Eksportuj wyniki** . Opcje eksportu dostępne do eksportowania zawartości zależą od tego, czy wyniki wyszukiwania znajdują się w skrzynkach pocztowych, witrynach, czy też w obu tych obszarach.

3. W obszarze **Opcje danych wyjściowych** wybierz jedną z następujących opcji:
  
   ![Opcje eksportowania danych wyjściowych.](../media/ExportOutputOptions.png)

    - **Wszystkie elementy, z wyłączeniem tych, które mają nierozpoznany format, są szyfrowane lub nie były indeksowane z innych powodów**. Ta opcja eksportuje tylko indeksowane elementy.
  
    - **Wszystkie elementy, w tym te, które mają nierozpoznany format, są szyfrowane lub nie są indeksowane z innych powodów**. Ta opcja eksportuje indeksowane i niezaindeksowane elementy.
  
    - **Tylko elementy, które mają nierozpoznany format, są szyfrowane lub nie zostały z innych powodów indeksowane**. Ta opcja eksportuje tylko niewyświetlione elementy.

      Zobacz sekcję [Więcej informacji](#more-information) , aby uzyskać opis eksportowania częściowo indeksowanych elementów. Aby uzyskać więcej informacji na temat częściowo indeksowanych elementów, zobacz [Częściowo zaindeksowane elementy w wyszukiwaniu zawartości](partially-indexed-items-in-content-search.md).

4. W obszarze **Eksportuj Exchange zawartości jako** wybierz jedną z następujących opcji:
  
   ![opcje Exchange.](../media/ExchangeExportOptions.png)

    - **Jeden plik PST dla każdej skrzynki pocztowej**: eksportuje jeden plik PST dla każdej skrzynki pocztowej użytkownika zawierającej wyniki wyszukiwania. Wszystkie wyniki ze skrzynki pocztowej archiwum użytkownika są zawarte w tym samym pliku PST. Ta opcja odtwarza strukturę folderów skrzynki pocztowej ze źródłowej skrzynki pocztowej.
  
    - **Jeden plik PST zawierający wszystkie komunikaty**: eksportuje pojedynczy plik PST (o nazwie *Exchange.pst*), który zawiera wyniki wyszukiwania ze wszystkich źródłowych skrzynek pocztowych uwzględnionych w wyszukiwaniu. Ta opcja odtwarza strukturę folderów skrzynki pocztowej dla każdej wiadomości.
  
    - **Jeden plik PST zawierający wszystkie komunikaty w jednym folderze**: eksportuje wyniki wyszukiwania do pojedynczego pliku PST, w którym wszystkie komunikaty znajdują się w jednym folderze najwyższego poziomu. Ta opcja umożliwia recenzentom przeglądanie elementów w kolejności chronologicznej (elementy są sortowane według daty wysłania) bez konieczności nawigowania po oryginalnej strukturze folderów skrzynki pocztowej dla każdego elementu.
  
    - **Poszczególne wiadomości**: eksportuje wyniki wyszukiwania jako pojedyncze wiadomości e-mail przy użyciu formatu msg. Jeśli wybierzesz tę opcję, wyniki wyszukiwania wiadomości e-mail zostaną wyeksportowane do folderu w systemie plików. Ścieżka folderu dla poszczególnych komunikatów jest taka sama jak ta używana w przypadku wyeksportowania wyników do pliku PST.
  
5. Skonfiguruj następujące dodatkowe opcje:

   ![Skonfiguruj inne opcje eksportu.](../media/OtherExportOptions.png)

   1. Zaznacz pole wyboru **Włącz usuwanie duplikowania dla zawartości Exchange**, aby wykluczyć zduplikowane komunikaty.
  
      Jeśli wybierzesz tę opcję, tylko jedna kopia wiadomości zostanie wyeksportowana, nawet jeśli w przeszukanych skrzynkach pocztowych zostanie znalezionych wiele kopii tej samej wiadomości. Raport wyników eksportu (który jest plikiem o nazwie Results.csv) będzie zawierać wiersz dla każdej kopii zduplikowanej wiadomości, aby można było zidentyfikować skrzynki pocztowe (lub foldery publiczne), które zawierają kopię zduplikowanej wiadomości. Aby uzyskać więcej informacji na temat de-duplikowania i sposobu identyfikowania zduplikowanych elementów, zobacz [De-duplication in eDiscovery search results (De-duplikowanie w wynikach wyszukiwania zbierania elektronicznych materiałów dowodowych](de-duplication-in-ediscovery-search-results.md)).
  
   2. Zaznacz pole wyboru **Dołącz wersje dla plików SharePoint**, aby wyeksportować wszystkie wersje dokumentów SharePoint. Ta opcja jest wyświetlana tylko wtedy, gdy źródła zawartości wyszukiwania obejmują witryny SharePoint lub OneDrive dla Firm.
  
   3. Wybierz pozycję **Eksportuj pliki w skompresowanym (spakowanym) folderze. Zawiera tylko pojedyncze komunikaty i SharePoint dokumentów** pole wyboru, aby wyeksportować wyniki wyszukiwania do skompresowanych folderów. Ta opcja jest wyświetlana tylko wtedy, gdy zdecydujesz się wyeksportować elementy Exchange jako pojedyncze komunikaty, a wyniki wyszukiwania będą zawierać SharePoint lub OneDrive dokumentów. Ta opcja służy głównie do obejścia limitu 260 znaków w Windows nazw ścieżek plików podczas eksportowania elementów. Zobacz sekcję "Nazwy plików wyeksportowanych elementów" w sekcji [Więcej informacji](#more-information) .
   > [!IMPORTANT]
   > Eksportowanie plików w skompresowanym (spakowanym) folderze wydłuży czas eksportowania.
  
6. Kliknij **pozycję Eksportuj** , aby rozpocząć proces eksportowania. Wyniki wyszukiwania są przygotowywane do pobrania, co oznacza, że są zbierane z oryginalnych lokalizacji zawartości, a następnie przekazywane do lokalizacji Storage platformy Azure w chmurze firmy Microsoft. Może to potrwać kilka minut.

Zobacz następną sekcję, aby uzyskać instrukcje dotyczące pobierania wyeksportowanych wyników wyszukiwania.
  
## <a name="step-2-download-the-search-results"></a>Krok 2. Pobieranie wyników wyszukiwania

Następnym krokiem jest pobranie wyników wyszukiwania z lokalizacji Storage platformy Azure na komputer lokalny.

> [!NOTE]
> Wyeksportowane wyniki wyszukiwania należy pobrać w ciągu 14 dni od utworzenia zadania eksportu w kroku 1.
  
1. Na stronie **Wyszukiwanie zawartości** w portalu zgodności wybierz kartę **Eksporty**
  
   Może być konieczne **kliknięcie** przycisku Odśwież, aby zaktualizować listę zadań eksportu, aby wyświetlić utworzone zadanie eksportu. Zadania eksportu mają taką samą nazwę jak odpowiednie wyszukiwanie z **_Export** dołączone do nazwy wyszukiwania.
  
2. Wybierz zadanie eksportu utworzone w kroku 1.

3. Na stronie wysuwanej w obszarze **Klucz eksportu** kliknij pozycję **Kopiuj do schowka**. Użyjesz tego klucza w kroku 6, aby pobrać wyniki wyszukiwania.
  
   > [!IMPORTANT]
   > Ponieważ każdy może zainstalować i uruchomić narzędzie eksportu zbierania elektronicznych materiałów dowodowych, a następnie użyć tego klucza do pobrania wyników wyszukiwania, pamiętaj o podjęciu środków ostrożności w celu ochrony tego klucza, tak jak w przypadku ochrony haseł lub innych informacji związanych z zabezpieczeniami.

4. W górnej części strony wysuwanej kliknij pozycję **Pobierz wyniki**.

5. Jeśli zostanie wyświetlony monit o **zainstalowanie narzędzia eksportu zbierania elektronicznych materiałów dowodowych**, kliknij przycisk **Zainstaluj**.

6. W narzędziu **eDiscovery Export Tool** wykonaj następujące czynności:

   ![Narzędzie eksportu zbierania elektronicznych materiałów dowodowych.](../media/eDiscoveryExportTool.png)

   1. Wklej klucz eksportu skopiowany w kroku 3 w odpowiednim polu.
  
   2. Kliknij przycisk **Przeglądaj** , aby określić lokalizację, w której chcesz pobrać pliki wyników wyszukiwania.
  
      > [!IMPORTANT]
      >  Ze względu na dużą aktywność sieci podczas pobierania należy pobrać wyniki wyszukiwania tylko do lokalizacji na dysku wewnętrznym na komputerze lokalnym. Aby uzyskać najlepsze środowisko pobierania, postępuj zgodnie z następującymi wytycznymi: <br/>
      >- Nie pobieraj wyników wyszukiwania do ścieżki UNC, zamapowanego dysku sieciowego, zewnętrznego dysku USB ani zsynchronizowanego konta OneDrive dla Firm.<br/>
      >- Wyłącz skanowanie antywirusowe dla folderu, do który pobierasz wynik wyszukiwania.<br/>
      >- Pobierz wyniki wyszukiwania do różnych folderów dla współbieżnych zadań pobierania.

7. Kliknij **przycisk Start** , aby pobrać wyniki wyszukiwania na komputer.
  
    **Narzędzie eksportu elektronicznego** zbierania elektronicznych materiałów dowodowych wyświetla informacje o stanie procesu eksportowania, w tym oszacowanie liczby (i rozmiaru) pozostałych elementów do pobrania. Po zakończeniu procesu eksportowania można uzyskać dostęp do plików w lokalizacji, w której zostały pobrane.

## <a name="more-information"></a>Więcej informacji

Oto więcej informacji na temat eksportowania wyników wyszukiwania.
  
[Limity eksportu](#export-limits)
  
[Eksportowanie raportów](#export-reports)
  
[Eksportowanie częściowo indeksowanych elementów](#exporting-partially-indexed-items)

[Eksportowanie poszczególnych komunikatów lub plików PST](#exporting-individual-messages-or-pst-files)

[Odszyfrowywanie wiadomości e-mail chronionych przez usługę RMS i zaszyfrowanych załączników plików](#decrypting-rms-protected-email-messages-and-encrypted-file-attachments)

[Nazwy plików wyeksportowanych elementów](#filenames-of-exported-items)  
  
[Różne](#miscellaneous)
  
### <a name="export-limits"></a>Limity eksportu

Aby uzyskać informacje o limitach podczas eksportowania wyników wyszukiwania zawartości, zobacz sekcję "Limity eksportu" w sekcji [Limity wyszukiwania zawartości](limits-for-content-search.md#export-limits).

### <a name="export-reports"></a>Eksportowanie raportów
  
- Podczas eksportowania wyników wyszukiwania oprócz wyników wyszukiwania są uwzględniane następujące raporty.
  
  - **Podsumowanie eksportu** Dokument Excel zawierający podsumowanie eksportu. Obejmuje to informacje, takie jak liczba wyszukiwanych źródeł zawartości, szacowane i pobrane rozmiary wyników wyszukiwania oraz szacowana i pobrana liczba wyeksportowanych elementów.
  
  - **Manifestu** Plik manifestu (w formacie XML), który zawiera informacje o każdym elemencie uwzględnionym w wynikach wyszukiwania.
  
  - **Wyniki** Dokument Excel zawierający informacje o każdym elemencie, który jest pobierany w wyniku wyszukiwania. W przypadku poczty e-mail dziennik wyników zawiera informacje o każdej wiadomości, w tym:
  
    - Lokalizacja wiadomości w źródłowej skrzynce pocztowej (w tym, czy wiadomość znajduje się w podstawowej, czy archiwum skrzynki pocztowej).
  
    - Data wysłania lub odebrania wiadomości.

    - Wiersz tematu z wiadomości.

    - Nadawca i adresaci wiadomości.

    - Czy komunikat jest zduplikowanym komunikatem, jeśli włączono opcję de-duplikowania podczas eksportowania wyników wyszukiwania. Zduplikowane komunikaty mają wartość w kolumnie **Duplikuj do elementu** , która identyfikuje komunikat jako duplikat. Wartość w kolumnie **Duplikuj do elementu** zawiera tożsamość elementu wyeksportowanego komunikatu. Aby uzyskać więcej informacji, zobacz [De-duplication in eDiscovery search results (Usuwanie duplikowania w wynikach wyszukiwania zbierania elektronicznych materiałów dowodowych](de-duplication-in-ediscovery-search-results.md)).

      W przypadku dokumentów z witryn SharePoint i OneDrive dla Firm dziennik wyników zawiera informacje o każdym dokumencie, w tym:

      - Adres URL dokumentu.

      - Adres URL zbioru witryn, w którym znajduje się dokument.

      - Data ostatniej modyfikacji dokumentu.

      - Nazwa dokumentu (który znajduje się w kolumnie Podmiot w dzienniku wyników).

  - **Elementy bez rozszerzenia** Dokument Excel zawierający informacje o wszystkich częściowo indeksowanych elementach, które zostaną uwzględnione w wynikach wyszukiwania. Jeśli nie uwzględnisz częściowo zaindeksowanych elementów podczas generowania raportu wyników wyszukiwania, ten raport będzie nadal pobierany, ale będzie pusty.

  - **Błędy i ostrzeżenia** Zawiera błędy i ostrzeżenia dotyczące plików napotkanych podczas eksportowania. Zobacz kolumnę Szczegóły błędu, aby uzyskać informacje specyficzne dla poszczególnych błędów lub ostrzeżeń.

  - **Pominięte elementy** Podczas eksportowania wyników wyszukiwania z witryn SharePoint i OneDrive dla Firm eksport zazwyczaj będzie zawierać pominięty raport elementów (SkippedItems.csv). Elementy cytowane w tym raporcie są zazwyczaj elementami, które nie zostaną pobrane, takimi jak folder lub zestaw dokumentów. Nie eksportowanie tych typów elementów jest projektowe. W przypadku innych elementów, które zostały pominięte, pole "Typ błędu" i "Szczegóły błędu" w raporcie pominiętych elementów pokazuje przyczynę, dla którego element został pominięty i nie został pobrany z innymi wynikami wyszukiwania.

  - **Trace.log** Zawiera szczegółowe informacje dotyczące rejestrowania procesu eksportowania i może pomóc w odnalezieniu problemów podczas eksportowania. Jeśli otworzysz bilet z pomoc techniczna firmy Microsoft o problemie związanym z eksportowaniem wyników wyszukiwania, może zostać wyświetlony monit o podanie tego dziennika śledzenia.
  
    > [!NOTE]
    > Możesz po prostu wyeksportować te dokumenty bez konieczności eksportowania rzeczywistych wyników wyszukiwania. Zobacz [Eksportowanie raportu wyszukiwania zawartości](export-a-content-search-report.md).
  
### <a name="exporting-partially-indexed-items"></a>Eksportowanie częściowo indeksowanych elementów
  
- Jeśli eksportujesz elementy skrzynki pocztowej z wyszukiwania zawartości, które zwraca wszystkie elementy skrzynki pocztowej w wynikach wyszukiwania (ponieważ nie ma słów kluczowych uwzględnionych w zapytaniu wyszukiwania), częściowo zaindeksowane elementy nie zostaną skopiowane do pliku PST zawierającego niezaindeksowane elementy. Dzieje się tak, ponieważ wszystkie elementy, w tym wszystkie częściowo indeksowane elementy, są automatycznie uwzględniane w regularnych wynikach wyszukiwania. Oznacza to, że częściowo indeksowane elementy zostaną uwzględnione w pliku PST (lub jako pojedyncze komunikaty), który zawiera inne, indeksowane elementy.

    Jeśli wyeksportujesz zarówno indeksowane, jak i częściowo indeksowane elementy lub wyeksportujesz tylko indeksowane elementy z wyszukiwania zawartości zwracającego wszystkie elementy, zostanie pobrana ta sama liczba elementów. Dzieje się tak, mimo że szacowane wyniki wyszukiwania dla wyszukiwania zawartości (wyświetlane w statystykach wyszukiwania w portalu zgodności) nadal będą zawierać oddzielne oszacowanie liczby częściowo indeksowanych elementów. Załóżmy na przykład, że oszacowanie wyszukiwania zawierającego wszystkie elementy (bez słów kluczowych w zapytaniu wyszukiwania) pokazuje, że znaleziono 1000 elementów i odnaleziono również 200 częściowo zaindeksowanych elementów. W tym przypadku 1000 elementów zawiera częściowo indeksowane elementy, ponieważ wyszukiwanie zwraca wszystkie elementy. Innymi słowy, wyszukiwanie zwraca łącznie 1000 elementów, a nie 1200 elementów (zgodnie z oczekiwaniami). Jeśli wyeksportujesz wyniki tego wyszukiwania i wyeksportujesz indeksowane i częściowo indeksowane elementy (lub wyeksportujesz tylko częściowo indeksowane elementy), zostanie pobranych 1000 elementów. Ponownie dzieje się tak, ponieważ częściowo indeksowane elementy są uwzględniane w regularnych (indeksowanych) wynikach, gdy używasz pustego zapytania wyszukiwania do zwracania wszystkich elementów. W tym samym przykładzie, jeśli zdecydujesz się wyeksportować tylko częściowo zaindeksowane elementy, zostanie pobranych tylko 200 niezaindeksowanych elementów.

    Należy również pamiętać, że w poprzednim przykładzie (podczas eksportowania indeksowanych i częściowo indeksowanych elementów lub eksportowania tylko indeksowanych elementów) raport **Podsumowanie eksportu** dołączony do wyeksportowanych wyników wyszukiwania zawiera listę 1000 elementów szacowanych i 1000 pobranych elementów z tych samych powodów, co wcześniej opisano. 

- Jeśli wyszukiwanie, z których eksportujesz wyniki, było wyszukiwaniem określonych lokalizacji zawartości lub wszystkich lokalizacji zawartości w organizacji, tylko częściowe elementy z lokalizacji zawartości zawierające elementy zgodne z kryteriami wyszukiwania zostaną wyeksportowane. Innymi słowy, jeśli w skrzynce pocztowej lub witrynie nie zostaną znalezione żadne wyniki wyszukiwania, nie zostaną wyeksportowane żadne częściowo zaindeksowane elementy w tej skrzynce pocztowej lub witrynie. Przyczyną tego jest to, że eksportowanie częściowo indeksowanych elementów z wielu lokalizacji w organizacji może zwiększyć prawdopodobieństwo błędów eksportu i zwiększyć czas potrzebny na wyeksportowanie i pobranie wyników wyszukiwania.

    Aby wyeksportować częściowo indeksowane elementy ze wszystkich lokalizacji zawartości do wyszukiwania, skonfiguruj wyszukiwanie tak, aby zwracało wszystkie elementy (usuwając wszystkie słowa kluczowe z zapytania wyszukiwania), a następnie eksportować tylko częściowo indeksowane elementy podczas eksportowania wyników wyszukiwania.

    ![Użyj trzeciej opcji eksportu, aby wyeksportować tylko niewyeksportowane elementy.](../media/5d7be338-a0e5-425f-8ba5-92769c24bf75.png)
  
- Podczas eksportowania wyników wyszukiwania z witryn SharePoint lub OneDrive dla Firm możliwość eksportowania nieweksportowanych elementów zależy również od wybranej opcji eksportu i od tego, czy przeszukiwana witryna zawiera indeksowany element zgodny z kryteriami wyszukiwania. Jeśli na przykład wyszukasz określone witryny SharePoint lub OneDrive dla Firm i nie zostaną znalezione żadne wyniki wyszukiwania, żadne niezaindeksowane elementy z tych witryn nie zostaną wyeksportowane, jeśli wybierzesz drugą opcję eksportu, aby wyeksportować zarówno indeksowane, jak i niezaindeksowane elementy. Jeśli indeksowany element z witryny jest zgodny z kryteriami wyszukiwania, wszystkie niezaindeksowane elementy z tej witryny zostaną wyeksportowane podczas eksportowania zarówno indeksowanych, jak i niezaindeksowanych elementów. Na poniższej ilustracji opisano opcje eksportu na podstawie tego, czy witryna zawiera indeksowany element zgodny z kryteriami wyszukiwania.

    ![Wybierz opcję eksportu na podstawie tego, czy witryna zawiera indeksowany element zgodny z kryteriami wyszukiwania.](../media/94f78786-c6bb-42fb-96b3-7ea3998bcd39.png)

    a. Eksportowane są tylko indeksowane elementy zgodne z kryteriami wyszukiwania. Nie są eksportowane żadne częściowo indeksowane elementy.

    b. Jeśli żadne indeksowane elementy z witryny nie spełniają kryteriów wyszukiwania, częściowo zaindeksowane elementy z tej samej witryny nie zostaną wyeksportowane. Jeśli w wynikach wyszukiwania zostaną zwrócone indeksowane elementy z witryny, częściowo zaindeksowane elementy z tej witryny zostaną wyeksportowane. Innymi słowy, eksportowane są tylko częściowo indeksowane elementy z witryn, które zawierają elementy zgodne z kryteriami wyszukiwania.

    c. Wszystkie częściowo indeksowane elementy ze wszystkich witryn wyszukiwania są eksportowane niezależnie od tego, czy witryna zawiera elementy zgodne z kryteriami wyszukiwania.

    Jeśli zdecydujesz się wyeksportować częściowo indeksowane elementy, częściowo indeksowane elementy skrzynki pocztowej zostaną wyeksportowane w osobnym pliku PST niezależnie od opcji wybranej w obszarze **Eksportowanie Exchange zawartości jako**.

- Jeśli częściowo indeksowane elementy są zwracane w wynikach wyszukiwania (ponieważ inne właściwości częściowo indeksowanych elementów odpowiadały kryteriom wyszukiwania), te częściowo indeksowane są eksportowane z regularnymi wynikami wyszukiwania. Dlatego jeśli zdecydujesz się wyeksportować zarówno indeksowane elementy, jak i częściowo indeksowane elementy (wybierając opcję **Wszystkie elementy, w tym te, które mają nierozpoznany format, są zaszyfrowane lub nie zostały zindeksowane z innych powodów** ), częściowo indeksowane elementy wyeksportowane z regularnymi wynikami zostaną wyświetlone w raporcie Results.csv. Nie będą one wyświetlane w raporcie unindexed items.csv.
  
### <a name="exporting-individual-messages-or-pst-files"></a>Eksportowanie poszczególnych komunikatów lub plików PST
  
- Jeśli nazwa ścieżki pliku komunikatu przekracza maksymalny limit znaków dla Windows, nazwa ścieżki pliku jest obcinana. Ale oryginalna nazwa ścieżki pliku zostanie wyświetlona w manifeście i dzienniku wyników.
  
- Jak wyjaśniono wcześniej, wyniki wyszukiwania wiadomości e-mail są eksportowane do folderu w systemie plików. Ścieżka folderu dla poszczególnych wiadomości będzie replikować ścieżkę folderu w skrzynce pocztowej użytkownika. Na przykład w przypadku wyszukiwania o nazwie "ContosoCase101" komunikaty w skrzynce odbiorczej użytkownika będą znajdować się w ścieżce  `~ContosoCase101\\<date of export\Exchange\user@contoso.com (Primary)\Top of Information Store\Inbox`folderu .

- Jeśli wybierzesz wyeksportowanie wiadomości e-mail w jednym pliku PST zawierającym wszystkie komunikaty w jednym folderze, folder **Elementy usunięte** i folder **Foldery wyszukiwania** zostaną uwzględnione na najwyższym poziomie folderu PST. Te foldery są puste.

- Zgodnie z wcześniejszymi instrukcjami należy wyeksportować wyniki wyszukiwania wiadomości e-mail jako pojedyncze wiadomości w celu odszyfrowania wiadomości chronionych przez usługę RMS podczas ich eksportowania. Zaszyfrowane wiadomości pozostaną zaszyfrowane, jeśli wyniki wyszukiwania wiadomości e-mail zostaną wyeksportowane jako plik PST.
  
### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments"></a>Odszyfrowywanie wiadomości e-mail chronionych przez usługę RMS i zaszyfrowanych załączników plików

Wszystkie wiadomości e-mail chronione prawami (chronione przez usługę RMS) zawarte w wynikach wyszukiwania zawartości zostaną odszyfrowane podczas ich eksportowania. Ponadto każdy plik zaszyfrowany za pomocą [technologii szyfrowania firmy Microsoft](encryption.md) i dołączony do wiadomości e-mail dołączonej do wyników wyszukiwania również zostanie odszyfrowany podczas eksportowania. Ta funkcja odszyfrowywania jest domyślnie włączona dla członków grupy ról menedżera zbierania elektronicznych materiałów dowodowych. Dzieje się tak, ponieważ rola zarządzania odszyfrowywanie usługi RMS jest domyślnie przypisana do tej grupy ról. Podczas eksportowania zaszyfrowanych wiadomości e-mail i załączników należy pamiętać o następujących kwestiach:
  
- Jak wyjaśniono wcześniej, aby odszyfrować komunikaty chronione przez usługę RMS podczas ich eksportowania, należy wyeksportować wyniki wyszukiwania jako pojedyncze komunikaty. Jeśli wyeksportujesz wyniki wyszukiwania do pliku PST, komunikaty chronione przez usługę RMS pozostaną zaszyfrowane.

- Komunikaty odszyfrowane są identyfikowane w raporcie **ResultsLog** . Ten raport zawiera kolumnę o nazwie **Decode Status (Stan dekodowania**), a wartość **dekodowana** w tej kolumnie identyfikuje odszyfrowane komunikaty.

- Oprócz odszyfrowywania załączników plików podczas eksportowania wyników wyszukiwania można również wyświetlić podgląd odszyfrowanego pliku podczas podglądu wyników wyszukiwania. Wiadomość e-mail chronioną prawami można wyświetlić tylko po jej wyeksportowaniu.

- Obecnie funkcja odszyfrowywania podczas eksportowania wyników wyszukiwania nie obejmuje zaszyfrowanej zawartości z witryn SharePoint i OneDrive dla Firm. Jednak wkrótce pojawi się pomoc techniczna dotycząca dokumentów zaszyfrowanych za pomocą technologii szyfrowania firmy Microsoft i przechowywanych w usłudze SharePoint Online i OneDrive dla Firm.

- Jeśli chcesz uniemożliwić komuś odszyfrowanie komunikatów rms-protect i zaszyfrowanych załączników plików, musisz utworzyć niestandardową grupę ról (przez skopiowanie wbudowanej grupy ról menedżera zbierania elektronicznych materiałów dowodowych), a następnie usunąć rolę zarządzania odszyfrowywanie usługi RMS z niestandardowej grupy ról. Następnie dodaj osobę, której nie chcesz odszyfrowywać komunikatów jako członka niestandardowej grupy ról.
  
### <a name="filenames-of-exported-items"></a>Nazwy plików wyeksportowanych elementów
  
- Istnieje limit 260 znaków (narzucony przez system operacyjny) dla pełnej nazwy ścieżki dla wiadomości e-mail i dokumentów witryny wyeksportowanych na komputer lokalny. Pełna nazwa ścieżki dla wyeksportowanych elementów obejmuje oryginalną lokalizację elementu i lokalizację folderu na komputerze lokalnym, do którego są pobierane wyniki wyszukiwania. Jeśli na przykład określisz, że  `C:\Users\Admin\Desktop\SearchResults` chcesz pobrać wyniki wyszukiwania w narzędziu eDiscovery Export, pełna nazwa ścieżki pobranego elementu wiadomości e-mail będzie mieć  `C:\Users\Admin\Desktop\SearchResults\ContentSearch1\03.15.2017-1242PM\Exchange\sarad@contoso.com (Primary)\Top of Information Store\Inbox\Insider trading investigation.msg`wartość .

- Jeśli limit 260 znaków zostanie przekroczony, pełna nazwa ścieżki dla elementu zostanie obcięta na podstawie następujących elementów:

  - Jeśli pełna nazwa ścieżki jest dłuższa niż 260 znaków, nazwa pliku zostanie skrócona, aby przekroczyć limit; Pamiętaj, że obcięta nazwa pliku (z wyłączeniem rozszerzenia pliku) nie będzie mniejsza niż osiem znaków.

  - Jeśli pełna nazwa ścieżki jest nadal zbyt długa po skróceniu nazwy pliku, element zostanie przeniesiony z bieżącej lokalizacji do folderu nadrzędnego. Jeśli nazwa ścieżki jest nadal zbyt długa, proces jest powtarzany: skróć nazwę pliku i w razie potrzeby przenieś ponownie do folderu nadrzędnego. Ten proces jest powtarzany, dopóki pełna nazwa ścieżki nie przekracza limitu 260 znaków.

  - Jeśli obcięta pełna nazwa ścieżki już istnieje, numer wersji jest dodawany na końcu nazwy pliku; na przykład `statusmessage(2).msg`.

    Aby rozwiązać ten problem, rozważ pobranie wyników wyszukiwania do lokalizacji o krótkiej nazwie ścieżki; Na przykład pobranie wyników wyszukiwania do folderu o nazwie  `C:\Results` spowoduje dodanie mniejszej liczby znaków do nazw ścieżek wyeksportowanych elementów niż pobranie ich do folderu o nazwie  `C:\Users\Admin\Desktop\Results`.

- Podczas eksportowania dokumentów witryny możliwe jest również zmodyfikowanie oryginalnej nazwy pliku dokumentu. Dzieje się tak szczególnie w przypadku dokumentów usuniętych z witryny SharePoint lub OneDrive dla Firm, które zostały wstrzymane. Gdy dokument znajdujący się w witrynie, która jest wstrzymana, zostanie usunięty, usunięty dokument zostanie automatycznie przeniesiony do biblioteki archiwum konserwacji witryny (która została utworzona, gdy witryna została wstrzymana). Po przeniesieniu usuniętego dokumentu do biblioteki Archiwum zachowywania do oryginalnej nazwy pliku dokumentu dołączany jest losowo wygenerowany i unikatowy identyfikator. Jeśli na przykład nazwa pliku dokumentu jest  `FY2017Budget.xlsx` późniejsza i przeniesiona do biblioteki archiwum zachowywania, nazwa pliku dokumentu przeniesionego do biblioteki archiwum zachowywania jest modyfikowana na wartość podobną  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`do . Jeśli dokument w bibliotece Archiwum zachowania jest zgodny z zapytaniem wyszukiwania zawartości i wyeksportujesz wyniki tego wyszukiwania, wyeksportowany plik ma zmodyfikowaną nazwę pliku; W tym przykładzie nazwa pliku wyeksportowanego dokumentu to  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`.

    Gdy dokument w witrynie, która jest wstrzymana, jest modyfikowany (i włączono przechowywanie wersji biblioteki dokumentów w witrynie), kopia pliku jest automatycznie tworzona w bibliotece archiwizacji zachowania. W takim przypadku losowo wygenerowany i unikatowy identyfikator jest również dołączany do nazwy pliku dokumentu skopiowanego do biblioteki Archiwum zachowywania.

    Powodem, dla którego nazwy plików dokumentów, które są przenoszone lub kopiowane do biblioteki archiwizacji zachowania, jest zapobieganie konfliktom nazw plików. Aby uzyskać więcej informacji na temat umieszczania blokady w witrynach i biblioteki archiwum konserwacji, zobacz [Omówienie archiwum w miejscu na serwerze SharePoint Server 2016](https://support.office.com/article/5e400d68-cd51-444a-8fe6-e4df1d20aa95).

### <a name="miscellaneous"></a>Różne
  
- Podczas pobierania wyników wyszukiwania przy użyciu narzędzia eksportu zbierania elektronicznych materiałów dowodowych może zostać wyświetlony następujący błąd: `System.Net.WebException: The remote server returned an error: (412) The condition specified using HTTP conditional header(s) is not met.` Jest to błąd przejściowy, który zwykle występuje w lokalizacji Storage platformy Azure. Aby rozwiązać ten problem, spróbuj ponownie [pobrać wyniki wyszukiwania](#step-2-download-the-search-results), co spowoduje ponowne uruchomienie narzędzia eksportu zbierania elektronicznych materiałów dowodowych.

- Wszystkie wyniki wyszukiwania i raporty eksportu są zawarte w folderze o takiej samej nazwie jak wyszukiwanie zawartości. Wyeksportowane wiadomości e-mail znajdują się w folderze o nazwie **Exchange**. Dokumenty znajdują się w folderze o nazwie **SharePoint**.

- Metadane systemu plików dla dokumentów w witrynach SharePoint i OneDrive dla Firm są zachowywane podczas eksportowania dokumentów na komputer lokalny. Oznacza to, że właściwości dokumentu, takie jak daty utworzenia i ostatniej modyfikacji, nie są zmieniane podczas eksportowania dokumentów.

- Jeśli wyniki wyszukiwania zawierają element listy z SharePoint zgodny z zapytaniem wyszukiwania, wszystkie wiersze na liście zostaną wyeksportowane oprócz elementu zgodnego z zapytaniem wyszukiwania i załącznikami na liście. Przyczyną tego zachowania jest podanie kontekstu dla elementów listy zwracanych w wynikach wyszukiwania. Dodatkowe elementy listy i załączniki mogą spowodować, że liczba wyeksportowanych elementów będzie inna niż pierwotne oszacowanie wyników wyszukiwania.
