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
description: Wyeksportuj wyniki wyszukiwania z przeszukiwania zawartości w Centrum zgodności platformy Microsoft 365 na komputer lokalny. Wyniki wiadomości e-mail są eksportowane jako pliki PST. Zawartość z witryn SharePoint i OneDrive dla Firm jest eksportowana jako natywne dokumenty Office dokumenty.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 22f66333a5fa2c5b570b564276c626fa0b41f83d
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989703"
---
# <a name="export-content-search-results"></a>Eksportowanie wyników wyszukiwania zawartości

Po pomyślnym uruchomieniu wyszukiwania zawartości możesz wyeksportować wyniki wyszukiwania na komputer lokalny. Wyniki eksportowania wiadomości e-mail są pobierane na komputer jako pliki PST. Podczas eksportowania zawartości z witryn SharePoint i OneDrive dla Firm są eksportowane kopie natywnych Office dokumentów. W eksportowanych wynikach wyszukiwania znajdują się inne dokumenty i raporty.
  
Eksportowanie wyników wyszukiwania zawartości wymaga przygotowania wyników, a następnie pobrania ich na komputer lokalny. Poniższe kroki eksportowania wyników wyszukiwania dotyczą również eksportowania wyników wyszukiwania skojarzonego z podstawowymi sprawami zbierania elektronicznych materiałów dowodowych.
  
## <a name="before-you-export-search-results"></a>Przed wyeksportowaniem wyników wyszukiwania

- Aby wyeksportować wyniki wyszukiwania, musisz mieć przypisaną rolę zarządzania eksportowaniem w programie Centrum zgodności platformy Microsoft 365. Ta rola jest przypisana do wbudowanej grupy ról Menedżer zbierania elektronicznych materiałów dowodowych. Nie jest ona domyślnie przypisywana do grupy ról Zarządzanie organizacją. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- Komputer, na który są eksportowane wyniki wyszukiwania, musi spełniać następujące wymagania systemowe:
  
  - Najnowsza wersja Windows (32-bitowa lub 64-bitowa)
  
  - Microsoft .NET Framework 4.7 lub wyższa
  
- Aby uruchomić narzędzie eDiscovery Export Tool, musisz użyć narzędzia Microsoft Edge <sup>1</sup>. Eksportowanie wyników wyszukiwania za pomocą programu Internet Explorer 11 nie jest już <sup>obsługiwane2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> W wyniku niedawnych zmian wprowadzonych w Microsoft Edge obsługa ClickOnce jest już domyślnie włączona. Aby uzyskać instrukcje dotyczące ClickOnce technicznej w programie Edge, zobacz [Korzystanie z narzędzia eDiscovery Export Tool w programie Microsoft Edge](configure-edge-to-export-search-results.md). Ponadto firma Microsoft nie produkcji rozszerzeń ani dodatków innych producentów dla ClickOnce aplikacji. Eksportowanie wyników wyszukiwania przy użyciu nieobsługiwanej przeglądarki z rozszerzeniami lub dodatków innych firm nie jest obsługiwane.
  >
  > <sup>2</sup> Począwszy od sierpnia 2021 r., aplikacje i usługi Microsoft 365 nie będą już obsługiwać programu Internet Explorer 11 (IE11) i użytkownicy mogą mieć środowisko o obniżonej wydajności lub nie mogą łączyć się z tymi aplikacjami i usługami. Te aplikacje i usługi wy wycofają się w ciągu najbliższych tygodni i miesięcy, aby zapewnić bezproblemowe zakończenie świadczenia pomocy technicznej. Poszczególne aplikacje i usługi są wyefane zgodnie z niezależnymi harmonogramami. Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Narzędzie eDiscovery Export Tool służące do pobierania wyników wyszukiwania w kroku 2 nie obsługuje automatyzacji (przy użyciu skryptu lub uruchamiania polecenia cmdlet). Zdecydowanie zalecamy, aby nie zautomatyzować procesu przygotowywania w kroku 1 ani w procesie pobierania w kroku 2. Jeśli zautomatyzowasz którykolwiek z tych procesów, pomoc techniczna firmy Microsoft nie udzieli pomocy w przypadku problemów.

- Zalecamy pobranie wyników wyszukiwania na komputer lokalny. Aby wyeliminować firmową zaporę lub infrastrukturę serwera proxy, powodując problemy podczas pobierania wyników wyszukiwania, rozważ pobranie wyników wyszukiwania na pulpit wirtualny poza siecią. Może to zmniejszyć limity czasu występujące w połączeniach danych platformy Azure podczas eksportowania dużej liczby plików. Aby uzyskać więcej informacji na temat pulpitów wirtualnych, zobacz [Windows pulpitu wirtualnego](https://azure.microsoft.com/services/virtual-desktop).

- Aby zwiększyć wydajność podczas pobierania wyników wyszukiwania, rozważ podzielenie wyszukiwań zwracających duży zestaw wyników na mniejsze wyszukiwania. Możesz na przykład użyć zakresów dat w zapytaniach wyszukiwania, aby zwrócić mniejszy zestaw wyników, które można pobrać szybciej.
  
- Podczas eksportowania wyników wyszukiwania dane są tymczasowo przechowywane w lokalizacji lokalizacji usługi Azure Storage firmy Microsoft w chmurze firmy Microsoft przed pobraniem ich na komputer lokalny. Upewnij się, że Twoja organizacja może połączyć się z punktem końcowym na platformie Azure, **\*** którym jest blob.core.windows.net (symbol wieloznaczny identyfikator unikatowy eksportu). Dwa tygodnie po utworzeniu dane wyników wyszukiwania zostaną usunięte z Storage Azure. 
  
- Jeśli organizacja komunikuje się z Internetem za pomocą serwera proxy, należy zdefiniować ustawienia serwera proxy na komputerze używanym do eksportowania wyników wyszukiwania (aby narzędzie eksportu było uwierzytelniane przez serwer proxy). W tym celu otwórz *plikmachine.config* lokalizacji, która jest taka, jak w Twojej wersji Windows. 
  
  - **32-bitowa:** `%windir%\Microsoft.NET\Framework\[version]\Config\machine.config`
  
  - **64-bitowa:** `%windir%\Microsoft.NET\Framework64\[version]\Config\machine.config`
  
    Dodaj poniższe wiersze do pliku  *machine.config*  między tagami  `<configuration>` i  `</configuration>` . Pamiętaj, aby zastąpić  `ProxyServer` prawidłowe  `Port` wartości dla organizacji, `proxy01.contoso.com:80`na przykład . 
  
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

- Jeśli wyniki wyszukiwania są starsze niż 7 dni i przesłasz zadanie eksportu, zostanie wyświetlony komunikat o błędzie z monitem o ponowne uruchomić wyszukiwanie w celu zaktualizowania wyników wyszukiwania. W takim przypadku anuluj eksportowanie, uruchom ponownie wyszukiwanie, a następnie ponownie rozpocznij eksportowanie.

## <a name="step-1-prepare-search-results-for-export"></a>Krok 1. Przygotowywanie wyników wyszukiwania do eksportu

Pierwszym krokiem jest przygotowanie wyników wyszukiwania do wyeksportowania. Podczas przygotowywania wyników są one przekazywane do lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Zawartość ze skrzynek pocztowych i witryn jest przesyłana z prędkością 2 GB na godzinę.
  
1. W Centrum zgodności platformy Microsoft 365 wybierz wyszukiwanie zawartości, z której chcesz wyeksportować wyniki.
  
2. W menu **Akcje** u dołu strony wysuwu kliknij polecenie **Eksportuj wyniki**.

   ![Opcja Eksportuj wyniki w menu Akcje.](../media/ActionMenuExportResults.png)

   Zostanie **wyświetlona strona wysuwana** Eksportuj wyniki. Opcje eksportowania dostępne w celu wyeksportowania zawartości zależą od tego, czy wyniki wyszukiwania znajdują się w skrzynkach pocztowych, witrynach, czy w ich kombinacji.

3. W **obszarze Opcje danych** wyjściowych wybierz jedną z następujących opcji:
  
   ![Eksportowanie opcji danych wyjściowych.](../media/ExportOutputOptions.png)

    - **Wszystkie elementy z wyjątkiem tych**, które mają nierozpoznany format, są szyfrowane lub nie zostały zindeksowane z innych powodów. Ta opcja powoduje wyeksportowanie tylko elementów indeksowanych.
  
    - **Wszystkie elementy, w tym te**, które mają nierozpoznany format, są szyfrowane lub nie zostały zindeksowane z innych powodów. Ta opcja powoduje wyeksportowanie elementów indeksowanych i nieindeksowanych.
  
    - **Tylko elementy, które mają nierozpoznany format, są szyfrowane lub nie zostały zindeksowane z innych powodów**. Ta opcja powoduje wyeksportowanie tylko elementów nieindeksowanych.

      W sekcji [Więcej informacji](#more-information) opisano sposób eksportowania elementów częściowo indeksowanych. Aby uzyskać więcej informacji na temat elementów częściowo indeksowanych, zobacz [Częściowo indeksowane elementy w przeszukiwaniu zawartości](partially-indexed-items-in-content-search.md).

4. W **obszarze Exchange jako wybierz** jedną z następujących opcji:
  
   ![Exchange opcje.](../media/ExchangeExportOptions.png)

    - **Jeden plik PST dla każdej skrzynki pocztowej**: eksportuje jeden plik PST dla każdej skrzynki pocztowej użytkownika zawierającej wyniki wyszukiwania. Wszystkie wyniki z archiwaowej skrzynki pocztowej użytkownika są zawarte w tym samym pliku PST. Ta opcja odtworzy strukturę folderów skrzynki pocztowej ze źródłowej skrzynki pocztowej.
  
    - **Jeden plik PST zawierający wszystkie wiadomości**: eksportuje pojedynczy plik PST (o *nazwie Exchange.pst*), który zawiera wyniki wyszukiwania ze wszystkich źródłowych skrzynek pocztowych uwzględnionych w wyszukiwaniu. Ta opcja odtworzy strukturę folderów skrzynki pocztowej dla każdej wiadomości.
  
    - **Jeden plik PST zawierający wszystkie wiadomości w jednym folderze**: Eksportuje wyniki wyszukiwania do jednego pliku PST, w którym wszystkie wiadomości znajdują się w jednym folderze najwyższego poziomu. Ta opcja umożliwia recenzentom przeglądanie elementów w kolejności chronologicznej (elementy są sortowane według daty wysłania) bez poruszania się po oryginalnej strukturze folderów skrzynki pocztowej dla każdego elementu.
  
    - **Poszczególne wiadomości**: Eksportuje wyniki wyszukiwania jako pojedyncze wiadomości e-mail, używając formatu msg. Jeśli wybierzesz tę opcję, wyniki wyszukiwania poczty e-mail zostaną wyeksportowane do folderu w systemie plików. Ścieżka folderu dla poszczególnych wiadomości jest taka sama jak ścieżka używana w przypadku eksportowania wyników do pliku PST.
  
5. Skonfiguruj następujące dodatkowe opcje:

   ![Skonfiguruj inne opcje eksportowania.](../media/OtherExportOptions.png)

   1. Zaznacz pole **wyboru Włącz duplikowanie duplikatów Exchange,** aby wykluczyć zduplikowane wiadomości.
  
      Jeśli wybierzesz tę opcję, zostanie wyeksportowana tylko jedna kopia wiadomości, nawet jeśli w przeszukanych skrzynkach pocztowych znajduje się wiele kopii tej samej wiadomości. Raport wyników eksportowania (czyli plik o nazwie Results.csv) będzie zawierał wiersz dla każdej kopii zduplikowanej wiadomości, dzięki czemu będzie można zidentyfikować skrzynki pocztowe (lub foldery publiczne), które zawierają kopię zduplikowanej wiadomości. Aby uzyskać więcej informacji na temat de duplikowania i sposobu identyfikowania zduplikowanych elementów, zobacz [Duplikowanie w wynikach wyszukiwania zbierania elektronicznych materiałów dowodowych](de-duplication-in-ediscovery-search-results.md).
  
   2. Zaznacz pole **wyboru Dołącz wersje dla SharePoint,** aby wyeksportować wszystkie wersje SharePoint dokumentów. Ta opcja jest wyświetlana tylko wtedy, gdy źródła zawartości wyszukiwania obejmują SharePoint lub OneDrive dla Firm witryn.
  
   3. Wybierz pozycję **Eksportuj pliki w folderze skompresowanym (skompresowanym). Uwzględnia tylko pojedyncze wiadomości i SharePoint dokumentów, aby** wyeksportować wyniki wyszukiwania do folderów skompresowanych. Ta opcja jest wyświetlana tylko w przypadku eksportowania Exchange jako pojedynczych wiadomości i gdy wyniki wyszukiwania obejmują dokumenty SharePoint lub OneDrive wiadomości. Ta opcja jest używana przede wszystkim do pracy z ograniczeniem do 260 znaków w Windows nazwach ścieżek pliku podczas eksportowania elementów. Zobacz sekcję "Nazwy plików eksportowanych elementów" w [sekcji Więcej](#more-information) informacji.
   > [!IMPORTANT]
   > Eksportowanie plików w folderze skompresowanym (skompresowanym) spowoduje zwiększenie czasu eksportu.
  
6. Kliknij **przycisk Eksportuj** , aby rozpocząć proces eksportowania. Wyniki wyszukiwania są przygotowane do pobrania, co oznacza, że są one zbierane z oryginalnych lokalizacji zawartości, a następnie przekazywane do lokalizacji usługi Azure Storage w chmurze firmy Microsoft. Może to potrwać kilka minut.

Instrukcje pobierania wyeksportowanych wyników wyszukiwania można znaleźć w następnej sekcji.
  
## <a name="step-2-download-the-search-results"></a>Krok 2. Pobieranie wyników wyszukiwania

Następnym krokiem jest pobranie wyników wyszukiwania z usługi Azure Storage lokalizacji na komputer lokalny.

> [!NOTE]
> Wyeksportowane wyniki wyszukiwania należy pobrać w ciągu 14 dni od utworzenia zadania eksportu w kroku 1.
  
1. Na **stronie Przeszukiwanie zawartości** w Centrum zgodności platformy Microsoft 365 wybierz **kartę Eksporty**
  
   Może być konieczne kliknięcie **przycisku Odśwież** w celu zaktualizowania listy zadań eksportu tak, aby wyświetlała utworzone zadanie eksportu. Zadania eksportowania mają taką samą nazwę jak odpowiadające im wyszukiwanie **z _Export** dołączona do nazwy wyszukiwania.
  
2. Wybierz zadanie eksportu utworzone w kroku 1.

3. Na wysuwana strona w obszarze **Klawisz Eksportuj** kliknij pozycję **Kopiuj do schowka**. Użyj tego klucza w kroku 6, aby pobrać wyniki wyszukiwania.
  
   > [!IMPORTANT]
   > Ponieważ każdy może zainstalować i uruchomić narzędzie eDiscovery Export, a następnie użyć tego klucza do pobrania wyników wyszukiwania, pamiętaj o podjęciu środków ostrożności w celu ochrony tego klucza tak samo, jak w przypadku haseł i innych informacji związanych z zabezpieczeniami.

4. U góry wysuwana strona kliknij pozycję **Pobierz wyniki**.

5. Jeśli zostanie wyświetlony monit o zainstalowanie narzędzia **eDiscovery Export Tool**, kliknij pozycję **Zainstaluj**.

6. W **narzędziu eDiscovery Export Tool** wykonaj następujące czynności:

   ![Narzędzie eDiscovery Export Tool.](../media/eDiscoveryExportTool.png)

   1. Wklej klucz eksportu skopiowany w kroku 3 w odpowiednim polu.
  
   2. Kliknij **przycisk** Przeglądaj, aby określić lokalizację, do której chcesz pobrać pliki wyników wyszukiwania.
  
      > [!IMPORTANT]
      >  Ze względu na dużą aktywność sieciową podczas pobierania należy pobierać wyniki wyszukiwania tylko do lokalizacji na dysku wewnętrznym na komputerze lokalnym. Aby uzyskać najlepsze środowisko pobierania, postępuj zgodnie z tymi wytycznymi: <br/>
      >- Nie pobieraj wyników wyszukiwania na ścieżkę UNC, zamapowany dysk sieciowy, zewnętrzny dysk USB ani zsynchronizowane konto OneDrive dla Firm sieciowe.<br/>
      >- Wyłącz funkcje skanowania antywirusowego folderu, do który chcesz pobrać wynik wyszukiwania.<br/>
      >- Pobieranie wyników wyszukiwania do różnych folderów na zadania współbieżnych pobierania.

7. Kliknij **przycisk Start** , aby pobrać wyniki wyszukiwania na komputer.
  
    Narzędzie **eDiscovery Export Tool** wyświetla informacje o stanie procesu eksportowania, łącznie z szacowaną liczbą (i rozmiarem) pozostałych elementów do pobrania. Po zakończeniu procesu eksportowania możesz uzyskać dostęp do plików w lokalizacji, w której zostały pobrane.

## <a name="more-information"></a>Więcej informacji

Tutaj znajdziesz więcej informacji na temat eksportowania wyników wyszukiwania.
  
[Limity eksportu](#export-limits)
  
[Eksportowanie raportów](#export-reports)
  
[Eksportowanie elementów częściowo indeksowanych](#exporting-partially-indexed-items)

[Eksportowanie pojedynczych wiadomości lub plików PST](#exporting-individual-messages-or-pst-files)

[Odszyfrowywanie wiadomości e-mail chronionych usługą RMS i zaszyfrowanych załączników plików](#decrypting-rms-protected-email-messages-and-encrypted-file-attachments)

[Nazwy plików eksportowanych elementów](#filenames-of-exported-items)  
  
[Postanowienia różne](#miscellaneous)
  
### <a name="export-limits"></a>Limity eksportu

Aby uzyskać informacje o limitach podczas eksportowania wyników wyszukiwania zawartości, zobacz sekcję "Limity eksportowania" w sekcji Limity [wyszukiwania zawartości](limits-for-content-search.md#export-limits).

### <a name="export-reports"></a>Eksportowanie raportów
  
- Podczas eksportowania wyników wyszukiwania oprócz wyników wyszukiwania są uwzględniane poniższe raporty.
  
  - **Podsumowanie eksportu** Dokument Excel zawierający podsumowanie eksportu. Obejmują one informacje, takie jak liczba przeszukanych źródeł zawartości, szacowane i pobrane rozmiary wyników wyszukiwania oraz szacowana i pobrana liczba wyeksportowanych elementów.
  
  - **Manifest** Plik manifestu (w formacie XML), który zawiera informacje o każdym z elementów uwzględnionych w wynikach wyszukiwania.
  
  - **Wyniki** Dokument Excel zawierający informacje o każdym pobieraniu elementu jako wyniku wyszukiwania. W przypadku wiadomości e-mail dziennik wyników zawiera informacje o każdej wiadomości, w tym:
  
    - Lokalizacja wiadomości w źródłowej skrzynce pocztowej (w tym to, czy wiadomość znajduje się w podstawowej, czy archiwaowej skrzynce pocztowej).
  
    - Data wysłania lub odebrania wiadomości.

    - Wiersz Temat wiadomości.

    - Nadawca i adresaci wiadomości.

    - Informacja o tym, czy wiadomość jest zduplikowana, jeśli podczas eksportowania wyników wyszukiwania włączono opcję de duplikowania. Zduplikowane wiadomości mają wartość w kolumnie Duplikuj **jako** element, która identyfikuje wiadomość jako duplikat. Wartość w kolumnie Duplikuj **do** elementu zawiera tożsamość elementu eksportowanej wiadomości. Aby uzyskać więcej informacji, [zobacz Duplikowanie w wynikach wyszukiwania zbierania elektronicznych materiałów dowodowych](de-duplication-in-ediscovery-search-results.md).

      W przypadku dokumentów SharePoint i OneDrive dla Firm dziennika wyników znajdują się informacje o każdym dokumencie, takie jak:

      - Adres URL dokumentu.

      - Adres URL zbioru witryn, w którym znajduje się dokument.

      - Data ostatniej modyfikacji dokumentu.

      - Nazwa dokumentu (która znajduje się w kolumnie Temat w dzienniku wyników).

  - **Elementy nieindeksowane** Dokument Excel zawierający informacje o elementach częściowo indeksowanych, które zostaną uwzględnione w wynikach wyszukiwania. Jeśli nie uwzględnisz elementów częściowo indeksowanych podczas generowania raportu wyników wyszukiwania, ten raport nadal zostanie pobrany, ale będzie pusty.

  - **Błędy i ostrzeżenia** Zawiera błędy i ostrzeżenia dotyczące plików napotkanych podczas eksportowania. Zobacz kolumnę Szczegóły błędu, aby uzyskać informacje dotyczące poszczególnych błędów lub ostrzeżeń.

  - **Pominięte elementy** Podczas eksportowania wyników wyszukiwania z witryn SharePoint i OneDrive dla Firm eksport zazwyczaj będzie zawierać raport o pominiętych elementach (SkippedItems.csv). Elementy cytowane w tym raporcie są zazwyczaj elementami, które nie zostaną pobrane, takimi jak folder lub zestaw dokumentów. Elementy tego typu nie są eksportowane domyślnie. W przypadku pozostałych pominiętych elementów pola "Typ błędu" i "Szczegóły błędu" w raporcie o pominiętych elementach pokazują przyczynę tego, że element został pominięty i nie został pobrany wraz z innymi wynikami wyszukiwania.

  - **Trace.log** Zawiera szczegółowe informacje dotyczące procesu eksportowania i może pomóc w odkrywaniu problemów podczas eksportowania. Jeśli otworzysz bilet pomocy technicznej firmy Microsoft związany z problemem związanym z eksportowaniem wyników wyszukiwania, może pojawić się monit o podanie tego dziennika śledzenia.
  
    > [!NOTE]
    > Możesz po prostu wyeksportować te dokumenty bez konieczności eksportowania rzeczywistych wyników wyszukiwania. Zobacz [Eksportowanie raportu przeszukiwania zawartości](export-a-content-search-report.md).
  
### <a name="exporting-partially-indexed-items"></a>Eksportowanie elementów częściowo indeksowanych
  
- Jeśli elementy skrzynki pocztowej są eksportowane z wyszukiwania zawartości, które zwraca wszystkie elementy skrzynek pocztowych w wynikach wyszukiwania (ponieważ nie ma słów kluczowych uwzględnianych w zapytaniu wyszukiwania), elementy częściowo indeksowane nie będą kopiowane do pliku PST zawierającego elementy nieindeksowane. Wynika to z tego, że wszystkie elementy, w tym elementy częściowo indeksowane, są automatycznie uwzględniane w wynikach zwykłego wyszukiwania. Oznacza to, że elementy częściowo indeksowane będą uwzględniane w pliku PST (lub jako pojedyncze wiadomości) zawierającym inne elementy indeksowane.

    W przypadku eksportowania zarówno elementów indeksowanych, jak i częściowo indeksowanych lub eksportowania tylko elementów indeksowanych z przeszukiwania zawartości, które zwraca wszystkie elementy, zostanie pobrana ta sama liczba elementów. Dzieje się tak, nawet jeśli szacowane wyniki wyszukiwania zawartości (wyświetlane w statystyce wyszukiwania w Centrum zgodności platformy Microsoft 365) nadal będą zawierać oddzielną szacowaną liczbę częściowo indeksowanych elementów. Załóżmy na przykład, że szacowana wartość wyszukiwania, które obejmuje wszystkie elementy (bez słów kluczowych w zapytaniu wyszukiwania), wskazuje, że znaleziono 1000 elementów, a 200 elementów zostało znalezionych częściowo. W tym przypadku 1000 elementów zawiera elementy częściowo indeksowane, ponieważ wyszukiwanie zwraca wszystkie elementy. Innymi słowy, wyszukiwanie zwróci 1000 elementów, a nie 1200 elementów (jak można by się spodziewać). W przypadku eksportowania wyników tego wyszukiwania i wybrania eksportowania elementów indeksowanych i częściowo indeksowanych (lub eksportowania tylko elementów częściowo indeksowanych) zostanie pobranych 1000 elementów. Jest tak również dlatego, że elementy częściowo indeksowane są uwzględniane w wynikach zwykłego (indeksowanego) po użyciu pustego zapytania wyszukiwania w celu zwrócenia wszystkich elementów. W tym samym przykładzie, jeśli zdecydujesz się wyeksportować tylko elementy częściowo indeksowane, zostaną pobrane tylko 200 elementów nieindeksowanych.

    Należy również pamiętać, że w poprzednim przykładzie (podczas eksportowania elementów indeksowanych i częściowo indeksowanych lub eksportowania tylko elementów indeksowanych)  raport Podsumowanie eksportu zawarty w eksportowanych wynikach wyszukiwania zawierał listę 1000 elementów szacowanych elementów i 1000 pobranych elementów z tych samych powodów, co opisano wcześniej. 

- Jeśli wyszukiwanie, z których są eksportowane wyniki, dotyczyło wyszukiwania określonych lokalizacji zawartości lub wszystkich lokalizacji zawartości w organizacji, zostaną wyeksportowane tylko częściowe elementy z lokalizacji zawartości, które zawierają elementy zgodne z kryteriami wyszukiwania. Innymi słowy, jeśli w skrzynce pocztowej lub witrynie nie zostaną znalezione żadne wyniki wyszukiwania, elementy częściowo indeksowane w tej skrzynce pocztowej lub witrynie nie zostaną wyeksportowane. Przyczyną tego jest to, że eksportowanie elementów częściowo indeksowanych z wielu lokalizacji w organizacji może zwiększyć prawdopodobieństwo błędów eksportu i zwiększyć czas eksportowania oraz czas eksportowania i pobierania wyników wyszukiwania.

    Aby wyeksportować elementy częściowo indeksowane ze wszystkich lokalizacji zawartości do wyszukiwania, skonfiguruj wyszukiwanie tak, aby zwracało wszystkie elementy (usuwając słowa kluczowe z zapytania wyszukiwania), a następnie wyeksportuj tylko częściowo indeksowane elementy podczas eksportowania wyników wyszukiwania.

    ![Użyj trzeciej opcji eksportu, aby wyeksportować tylko elementy nieindeksowane.](../media/5d7be338-a0e5-425f-8ba5-92769c24bf75.png)
  
- Podczas eksportowania wyników wyszukiwania z witryn SharePoint lub OneDrive dla Firm możliwość eksportowania elementów nieindeksowanych zależy również od wybranej opcji eksportowania i od tego, czy przeszukana witryna zawiera element indeksowany, który odpowiada kryteriom wyszukiwania. Jeśli na przykład wyszukuje się w konkretnych witrynach SharePoint lub OneDrive dla Firm i nie zostaną znalezione żadne wyniki wyszukiwania, nie zostaną wyeksportowane żadne elementy nieindeksowane z tych witryn, jeśli wybierzesz drugą opcję eksportowania w celu wyeksportowania zarówno elementów indeksowanych, jak i nieindeksowanych. Jeśli element indeksowany z witryny spełnia kryteria wyszukiwania, wszystkie elementy nieindeksowane z tej witryny zostaną wyeksportowane podczas eksportowania zarówno elementów indeksowanych, jak i nieindeksowanych. Na poniższej ilustracji opisano opcje eksportowania zależnie od tego, czy witryna zawiera indeksowany element, który odpowiada kryteriom wyszukiwania.

    ![Wybierz opcję eksportowania zależnie od tego, czy witryna zawiera indeksowany element, który odpowiada kryteriom wyszukiwania.](../media/94f78786-c6bb-42fb-96b3-7ea3998bcd39.png)

    a. Eksportowane są tylko elementy indeksowane zgodne z kryteriami wyszukiwania. Elementy częściowo indeksowane nie są eksportowane.

    b. Jeśli żadne elementy indeksowane z witryny nie spełniają kryteriów wyszukiwania, elementy częściowo indeksowane z tej samej witryny nie są eksportowane. Jeśli w wynikach wyszukiwania są zwracane elementy indeksowane z witryny, częściowo indeksowane elementy z tej witryny są eksportowane. Innymi słowy są eksportowane tylko częściowo indeksowane elementy z witryn zawierających elementy zgodne z kryteriami wyszukiwania.

    c. Wszystkie częściowo indeksowane elementy ze wszystkich witryn w wyszukiwaniu są eksportowane bez względu na to, czy witryna zawiera elementy zgodne z kryteriami wyszukiwania.

    Jeśli zdecydujesz się wyeksportować elementy częściowo indeksowane, elementy częściowo indeksowanych skrzynek pocztowych są eksportowane w osobnym pliku PST, niezależnie od opcji w obszarze Eksportuj zawartość Exchange **jako**.

- Jeśli elementy częściowo indeksowane są zwracane w wynikach wyszukiwania (ponieważ inne właściwości elementów częściowo indeksowanych są zgodne z kryteriami wyszukiwania), elementy częściowo indeksowane są eksportowane ze zwykłymi wynikami wyszukiwania. Jeśli zdecydujesz się wyeksportować zarówno elementy indeksowane, jak i elementy częściowo indeksowane (przez wybranie opcji Wszystkie elementy, łącznie z elementami, które mają nierozpoznany **format,** są szyfrowane lub nie zostały zindeksowane z innych przyczyn opcji eksportu), elementy częściowo indeksowane wyeksportowane z wynikami regularnymi zostaną wyświetlone w raporcie w programie Results.csv. Nie będą one wyświetlane w raporcie items.csv indeksowane.
  
### <a name="exporting-individual-messages-or-pst-files"></a>Eksportowanie pojedynczych wiadomości lub plików PST
  
- Jeśli nazwa ścieżki pliku wiadomości przekracza maksymalny limit Windows znaków, nazwa ścieżki pliku jest obcinana. Oryginalna nazwa ścieżki pliku będzie jednak wymieniona w pliku Manifest i ResultsLog.
  
- Jak wyjaśniono wcześniej, wyniki wyszukiwania poczty e-mail są eksportowane do folderu w systemie plików. Ścieżka folderu dla poszczególnych wiadomości replikuje ścieżkę folderu w skrzynce pocztowej użytkownika. Na przykład wyszukiwanie wiadomości o nazwie "ContosoCase101" w skrzynce odbiorczej użytkownika będzie umieszczone na ścieżce folderu  `~ContosoCase101\\<date of export\Exchange\user@contoso.com (Primary)\Top of Information Store\Inbox`.

- Jeśli zdecydujesz się wyeksportować wiadomości e-mail w jednym pliku PST zawierającym wszystkie wiadomości w **jednym folderze** , folder Elementy usunięte **i folder** foldery wyszukiwania są uwzględniane na najwyższym poziomie folderu PST. Te foldery są puste.

- Jak wspomniano wcześniej, podczas eksportowania wiadomości e-mail należy wyeksportować wyniki wyszukiwania poczty e-mail jako pojedyncze wiadomości do odszyfrowywania wiadomości chronionych usługą RMS. Zaszyfrowane wiadomości pozostaną zaszyfrowane, jeśli wyniki wyszukiwania poczty e-mail zostaną wyeksportowane jako plik PST.
  
### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments"></a>Odszyfrowywanie wiadomości e-mail chronionych usługą RMS i zaszyfrowanych załączników plików

Wszelkie wiadomości e-mail chronione prawami (chronione przez usługę RMS) zawarte w wynikach wyszukiwania zawartości będą odszyfrowywać podczas eksportowania. Ponadto każdy plik, który jest zaszyfrowany przy użyciu technologii szyfrowania [firmy Microsoft](encryption.md) i dołączony do wiadomości e-mail dołączonej do wyników wyszukiwania, również zostanie odszyfrowany po wyeksportowaniu. Ta funkcja odszyfrowywania jest domyślnie włączona dla członków grupy ról Menedżera zbierania elektronicznych materiałów dowodowych. Jest tak, ponieważ do tej grupy ról jest domyślnie przypisana rola zarządzania odszyfrowywaniem usługi RMS. Podczas eksportowania zaszyfrowanych wiadomości e-mail i załączników należy pamiętać o następujących kwestiach:
  
- Jak wyjaśniono wcześniej, aby podczas eksportowania odszyfrowywać wiadomości chronione przez usługę RMS, należy wyeksportować wyniki wyszukiwania jako pojedyncze wiadomości. W przypadku eksportowania wyników wyszukiwania do pliku PST wiadomości chronione przez usługę RMS będą szyfrowane.

- Odszyfrowane wiadomości są identyfikowane w **raporcie ResultsLog** . Ten raport zawiera kolumnę o nazwie **Stan dekodowania**, a wartość w kolumnie **Dekodowane** wskazuje wiadomości, które zostały odszyfrowane.

- Oprócz odszyfrowywania załączników plików podczas eksportowania wyników wyszukiwania możesz także wyświetlić podgląd odszyfrowany plik podczas wyświetlania podglądu wyników wyszukiwania. Wiadomość e-mail, która jest chroniona prawami dostępu, jest dostępna tylko po jej wyeksportowaniu.

- Obecnie funkcja odszyfrowywania podczas eksportowania wyników wyszukiwania nie obejmuje zaszyfrowanej zawartości z witryn SharePoint i OneDrive dla Firm wyszukiwania. Jednak wkrótce będzie już można obsługiwać dokumenty szyfrowane przy użyciu technologii szyfrowania firmy Microsoft i przechowywane w usługach SharePoint Online i OneDrive dla Firm.

- Jeśli chcesz uniemożliwić odszyfrowywanie wiadomości z ochroną usługi RMS i zaszyfrowanych załączników plików, musisz utworzyć niestandardową grupę ról (przez skopiowanie wbudowanej grupy ról Menedżera zbierania elektronicznych materiałów dowodowych), a następnie usunąć rolę zarządzania odszyfrowywaniem usługi RMS z niestandardowej grupy ról. Następnie dodaj osobę, która nie ma odszyfrowywać wiadomości jako członka niestandardowej grupy ról.
  
### <a name="filenames-of-exported-items"></a>Nazwy plików eksportowanych elementów
  
- Istnieje limit 260 znaków (nałożony przez system operacyjny) na pełną nazwę ścieżki dla wiadomości e-mail i dokumentów witryny wyeksportowanych na komputer lokalny. Pełna nazwa eksportowanych elementów zawiera oryginalną lokalizację elementu i lokalizację folderu na komputerze lokalnym, na który są pobierane wyniki wyszukiwania. Jeśli na przykład określisz `C:\Users\Admin\Desktop\SearchResults` pobranie wyników wyszukiwania w narzędziu eDiscovery Export, wówczas pełna nazwa ścieżki pobranego elementu poczty e-mail będzie mieć .`C:\Users\Admin\Desktop\SearchResults\ContentSearch1\03.15.2017-1242PM\Exchange\sarad@contoso.com (Primary)\Top of Information Store\Inbox\Insider trading investigation.msg`

- Po przekroczeniu limitu 260 znaków pełna nazwa ścieżki elementu zostanie obcięta w zależności od następujących informacji:

  - Jeśli pełna nazwa ścieżki będzie dłuższa niż 260 znaków, nazwa pliku zostanie skrócona, aby uzyskać wartość poniżej limitu. Zwróć uwagę, że obcięta nazwa pliku (z wyjątkiem rozszerzenia pliku) nie będzie mniejsza niż osiem znaków.

  - Jeśli pełna nazwa ścieżki jest jeszcze za długa po skróceniu nazwy pliku, element zostanie przeniesiony z jego bieżącej lokalizacji do folderu nadrzędnego. Jeśli nazwa ścieżki jest nadal zbyt długa, ten proces jest powtarzany: skróć nazwę pliku i w razie potrzeby ponownie przenieś do folderu nadrzędnego. Ten proces jest powtarzany, dopóki pełna nazwa ścieżki nie będzie czekać więcej niż 260 znaków.

  - Jeśli pełna nazwa obciętej pełnej ścieżki już istnieje, na końcu nazwy pliku jest dodawany numer wersji. na przykład `statusmessage(2).msg`.

    Aby zmniejszyć ten problem, rozważ pobranie wyników wyszukiwania do lokalizacji o krótkiej nazwie ścieżki; Na przykład pobranie wyników  `C:\Results` wyszukiwania do folderu o nazwie powoduje dodanie mniejszej liczby znaków do nazw ścieżek eksportowanych elementów niż pobranie ich do folderu o nazwie  `C:\Users\Admin\Desktop\Results`.

- Podczas eksportowania dokumentów witryny możliwe jest również zmodyfikowanie oryginalnej nazwy pliku dokumentu. Dzieje się tak w szczególności w przypadku dokumentów usuniętych SharePoint lub OneDrive dla Firm, które zostały umieszczone w wstrzymaniu. Po usunięciu dokumentu umieszczonego w witrynie usunięty dokument jest automatycznie przenoszony do biblioteki Zachowywanie witryny (która została utworzona, gdy witryna została umieszczona w a hold). Po usunięciu dokumentu zostanie przeniesiony do biblioteki Wstrzymaj zachowywanie do oryginalnej nazwy pliku zostanie dołączony losowo wygenerowany i unikatowy identyfikator. `FY2017Budget.xlsx` Jeśli na przykład nazwa pliku dokumentu jest taka, a dokument zostanie później usunięty i przeniesiony do biblioteki Zachowywanie, nazwa pliku dokumentu, który jest przenoszony do biblioteki Wstrzymaj zachowywania, `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`zostanie zmodyfikowana w podobny sposób. Jeśli dokument w bibliotece Funkcji zachowywania odpowiada zapytaniu przeszukiwanego zawartości i wyniki tego wyszukiwania zostaną wyeksportowane, wyeksportowany plik będzie zawierał zmodyfikowaną nazwę pliku. w tym przykładzie nazwa pliku eksportowanego dokumentu byłaby taka jak  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`.

    W przypadku zmodyfikowania dokumentu w witrynie, która znajduje się w wstrzymaniu (i włączony jest przechowywanie wersji dla biblioteki dokumentów w witrynie), kopia pliku jest tworzona automatycznie w bibliotece Hold (Przechowywanie). W tym przypadku do nazwy pliku dokumentu skopiowanego do biblioteki z zachowywania jest również dołączany losowo wygenerowany i unikatowy identyfikator.

    Dlatego nazwy plików dokumentów, które są przenoszone lub kopiowane do biblioteki wstrzymywania zachowywania, mają zapobiegać nazwom plików, które są w konflikcie. Aby uzyskać więcej informacji na temat umieszczania w zawartości witryn i biblioteki funkcji zachowywania, zobacz Omówienie przechowywania miejscowego w [programie SharePoint Server 2016](https://support.office.com/article/5e400d68-cd51-444a-8fe6-e4df1d20aa95).

### <a name="miscellaneous"></a>Postanowienia różne
  
- Podczas pobierania wyników wyszukiwania za pomocą narzędzia eDiscovery Export Tool może zostać wyświetlony następujący błąd: `System.Net.WebException: The remote server returned an error: (412) The condition specified using HTTP conditional header(s) is not met.` Jest to błąd przejściowy, który zazwyczaj występuje w lokalizacji usługi Azure Storage. Aby rozwiązać ten problem [, ponownie pobierz](#step-2-download-the-search-results) wyniki wyszukiwania, co spowoduje ponowne uruchomienie narzędzia eDiscovery Export Tool.

- Wszystkie wyniki wyszukiwania i raporty eksportu są uwzględniane w folderze o takiej samej nazwie jak wyszukiwanie zawartości. Wyeksportowane wiadomości e-mail znajdują się w folderze o **nazwie Exchange**. Dokumenty znajdują się w folderze o **nazwie SharePoint**.

- Metadane systemu plików dla dokumentów w witrynach SharePoint i OneDrive dla Firm są zachowywane podczas eksportowania dokumentów na komputer lokalny. Oznacza to, że właściwości dokumentu, takie jak daty utworzenia i ostatniej modyfikacji, nie są zmieniane podczas eksportowania dokumentów.

- Jeśli wyniki wyszukiwania zawierają element listy z programu SharePoint, który jest dopasowania do zapytania wyszukiwania, wszystkie wiersze na liście zostaną wyeksportowane oprócz elementu, który pasuje do zapytania wyszukiwania, oraz wszystkich załączników na liście. Przyczyną tego zachowania jest zapewnienie kontekstu dla elementów listy zwracanych w wynikach wyszukiwania. Dodatkowe elementy list i załączniki mogą powodować, że liczba wyeksportowanych elementów może różnić się od pierwotnej szacunkowej wartości wyników wyszukiwania.
