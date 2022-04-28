---
title: Eksportowanie raportu wyszukiwania zawartości
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExportReport
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 5c8c1db6-d8ac-4dbb-8a7a-f65d452169b9
description: Zamiast eksportować rzeczywiste wyniki wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview, możesz wyeksportować raport wyników wyszukiwania. Raport zawiera podsumowanie wyników wyszukiwania i dokument ze szczegółowymi informacjami o każdym wyeksportowanym elemencie.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 35e0a0b13594a6396ae1f757e3a1fc8a3e952173
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093070"
---
# <a name="export-a-content-search-report"></a>Eksportowanie raportu wyszukiwania zawartości

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Zamiast eksportować pełny zestaw wyników wyszukiwania z wyszukiwania zawartości w portalu zgodności usługi Microsoft Purview (lub z wyszukiwania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Standardowa), możesz wyeksportować te same raporty, które są generowane podczas eksportowania rzeczywistych wyników wyszukiwania.
  
Podczas eksportowania raportu pliki raportu są pobierane do folderu na komputerze lokalnym, który ma taką samą nazwę jak wyszukiwanie zawartości, ale jest dołączany do *_ReportsOnly*. Jeśli na przykład wyszukiwanie zawartości ma nazwę  *ContosoCase0815*, raport zostanie pobrany do folderu o nazwie *ContosoCase0815_ReportsOnly*. Aby zapoznać się z listą dokumentów uwzględnionych w raporcie, zobacz [What's included in the report (Co jest zawarte w raporcie](#whats-included-in-the-report)).

## <a name="before-you-export-a-search-report"></a>Przed wyeksportowaniem raportu wyszukiwania

- Aby wyeksportować raport wyszukiwania, musisz mieć przypisaną rolę zarządzania wyszukiwaniem zgodności w portalu zgodności. Ta rola jest domyślnie przypisywana do wbudowanych grup ról Menedżera zbierania elektronicznych materiałów dowodowych i zarządzania organizacją. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](assign-ediscovery-permissions.md).

- Podczas eksportowania raportu dane są tymczasowo przechowywane w lokalizacji Storage platformy Azure w chmurze firmy Microsoft przed ich pobraniem na komputer lokalny. Upewnij się, że twoja organizacja może nawiązać połączenie z punktem końcowym na platformie Azure, czyli **\*.blob.core.windows.net** (symbol wieloznaczny reprezentuje unikatowy identyfikator eksportu). Dane wyników wyszukiwania są usuwane z lokalizacji usługi Azure Storage dwa tygodnie po ich utworzeniu.

- Komputer używany do eksportowania raportu wyszukiwania musi spełniać następujące wymagania systemowe:
  
  - Najnowsza wersja Windows (32-bitowa lub 64-bitowa)
  
  - Microsoft .NET Framework w wersji 4.7 lub nowszej
  
- Aby uruchomić narzędzie eksportu elektronicznego zbierania elektronicznych materiałów dowodowych, musisz użyć Microsoft Edge <sup>1</sup>. Eksportowanie wyników wyszukiwania przy użyciu programu Internet Explorer 11 nie jest już <sup>obsługiwane2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> W wyniku ostatnich zmian Microsoft Edge obsługa ClickOnce nie jest już domyślnie włączona. Aby uzyskać instrukcje dotyczące włączania obsługi ClickOnce w przeglądarce Edge, zobacz [Use the eDiscovery Export Tool in Microsoft Edge (Używanie narzędzia eksportu zbierania elektronicznych](configure-edge-to-export-search-results.md) materiałów dowodowych w Microsoft Edge). Ponadto firma Microsoft nie produkuje rozszerzeń ani dodatków innych firm dla aplikacji ClickOnce. Eksportowanie wyników wyszukiwania przy użyciu nieobsługiwanej przeglądarki z rozszerzeniami lub dodatkami innych firm nie jest obsługiwane.
  > 
  > <sup>2</sup> Począwszy od sierpnia 2021 r., Microsoft 365 aplikacje i usługi nie będą już obsługiwać programu Internet Explorer 11 (IE11), a użytkownicy mogą mieć obniżoną wydajność lub nie mogą łączyć się z tymi aplikacjami i usługami. Te aplikacje i usługi będą stopniowo wycofywane w nadchodzących tygodniach i miesiącach, aby zapewnić bezproblemowe zakończenie wsparcia. Każda aplikacja i usługa są wycofywane w niezależnych harmonogramach. Aby uzyskać więcej informacji, zobacz ten [wpis w blogu](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Jeśli szacowany całkowity rozmiar wyników zwracanych przez wyszukiwanie przekracza 2 TB, eksportowanie raportów kończy się niepowodzeniem. Aby pomyślnie wyeksportować raporty, spróbuj zawęzić zakres i ponownie uruchomić wyszukiwanie, aby szacowany rozmiar wyników był mniejszy niż 2 TB.

- Jeśli wyniki wyszukiwania są starsze niż 7 dni i przesyłasz zadanie raportu eksportu, zostanie wyświetlony komunikat o błędzie z monitem o ponowne uruchomienie wyszukiwania w celu zaktualizowania wyników wyszukiwania. W takim przypadku anuluj eksport, uruchom ponownie wyszukiwanie, a następnie ponownie rozpocznij eksport.

- Eksportowanie raportów wyszukiwania oblicza maksymalną liczbę eksportów uruchomionych w tym samym czasie oraz maksymalną liczbę eksportów, które może uruchomić jeden użytkownik. Aby uzyskać więcej informacji na temat limitów eksportu, zobacz [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md#export-limits).
  
## <a name="step-1-generate-the-report-for-export"></a>Krok 1. Generowanie raportu na potrzeby eksportu

Pierwszym krokiem jest przygotowanie raportu do pobrania na eksport komputera. Podczas eksportowania raportu dokumenty raportu są przekazywane do obszaru usługi Azure Storage w chmurze firmy Microsoft.
  
1. W portalu zgodności wybierz wyszukiwanie zawartości, z których chcesz wyeksportować raport.
  
2. W menu **Akcje** w dolnej części strony wysuwanej wyszukiwania kliknij pozycję **Eksportuj raport**.

   ![Opcja Eksportuj raport w menu Akcje.](../media/ActionMenuExportReport.png)

   Zostanie wyświetlona strona **eksportowania** wysuwanego raportu. Opcje eksportu raportu dostępne do eksportowania informacji o wyszukiwaniu zależą od tego, czy wyniki wyszukiwania znajdują się w skrzynkach pocztowych lub witrynach, czy też w obu tych obszarach.
  
3. W obszarze **Opcje danych wyjściowych** wybierz jedną z następujących opcji:
  
   ![Opcje eksportowania danych wyjściowych.](../media/ExportOutputOptions.png)

    - **Wszystkie elementy, z wyłączeniem tych, które mają nierozpoznany format, są szyfrowane lub nie były indeksowane z innych powodów**. Ta opcja eksportuje tylko informacje o indeksowanych elementach.
  
    - **Wszystkie elementy, w tym te, które mają nierozpoznany format, są szyfrowane lub nie są indeksowane z innych powodów**. Ta opcja eksportuje informacje o indeksowanych i niezaindeksowanych elementach.
  
    - **Tylko elementy, które mają nierozpoznany format, są szyfrowane lub nie zostały z innych powodów indeksowane**. Ta opcja eksportuje tylko informacje o elementach bez certyfikatu.

4. Skonfiguruj opcję **Włącz usuwanie duplikowania dla Exchange zawartości**.
  
   - Jeśli wybierzesz tę opcję, liczba zduplikowanych komunikatów (przed deplikacją i po wycofaniu duplikacji) zostanie uwzględniona w raporcie podsumowania eksportu. Ponadto tylko jedna kopia wiadomości zostanie uwzględniona w pliku manifest.xml. Ale raport wyników eksportu będzie zawierać wiersz dla każdej kopii zduplikowanej wiadomości, dzięki czemu można zidentyfikować skrzynki pocztowe zawierające kopię zduplikowanej wiadomości. Aby uzyskać więcej informacji na temat wyeksportowanych raportów, zobacz [Co jest zawarte w raporcie](#whats-included-in-the-report).

   - Jeśli nie wybierzesz tej opcji, raporty eksportu będą zawierać informacje o wszystkich komunikatach zwracanych przez wyszukiwanie, w tym o duplikatach.

     Aby uzyskać więcej informacji na temat de-duplikowania i sposobu identyfikowania zduplikowanych elementów, zobacz [De-duplication in eDiscovery search results (De-duplikowanie w wynikach wyszukiwania zbierania elektronicznych materiałów dowodowych](de-duplication-in-ediscovery-search-results.md)).

5. Kliknij **pozycję Generuj raport**.

   Raporty wyszukiwania są przygotowywane do pobrania, co oznacza, że dokumenty raportu są przekazywane do lokalizacji Storage platformy Azure w chmurze firmy Microsoft. Może to potrwać kilka minut.

Zobacz następną sekcję, aby uzyskać instrukcje dotyczące pobierania wyeksportowanych raportów wyszukiwania.
  
## <a name="step-2-download-the-report"></a>Krok 2. Pobieranie raportu

Następnym krokiem jest pobranie raportu z obszaru usługi Azure Storage na komputer lokalny.

> [!NOTE]
> Wyeksportowany raport wyszukiwania musi zostać pobrany w ciągu 14 dni od wygenerowania raportu w kroku 1.

1. Na stronie **Wyszukiwanie zawartości** w portalu zgodności wybierz kartę **Eksporty**
  
   Może być konieczne **kliknięcie** przycisku Odśwież, aby zaktualizować listę zadań eksportu, aby wyświetlić utworzone zadanie eksportu. Zadania raportu eksportu mają taką samą nazwę jak odpowiednie wyszukiwanie z **_ReportsOnly** dołączone do nazwy wyszukiwania.
  
2. Wybierz zadanie eksportu utworzone w kroku 1.

3. Na stronie **wysuwanej Eksportuj raport** w obszarze **Klucz eksportu** kliknij pozycję **Kopiuj do schowka**. Użyjesz tego klucza w kroku 6, aby pobrać wyniki wyszukiwania.
  
   > [!IMPORTANT]
   > Ponieważ każdy może zainstalować i uruchomić narzędzie eksportu zbierania elektronicznych materiałów dowodowych, a następnie użyć tego klucza do pobrania raportu wyszukiwania, należy podjąć środki ostrożności w celu ochrony tego klucza, tak jak w przypadku ochrony haseł lub innych informacji związanych z zabezpieczeniami.

4. W górnej części strony wysuwanej kliknij pozycję **Pobierz wyniki**.

5. Jeśli zostanie wyświetlony monit o **zainstalowanie narzędzia eksportu zbierania elektronicznych materiałów dowodowych**, kliknij przycisk **Zainstaluj**.

6. W narzędziu **eDiscovery Export Tool** wykonaj następujące czynności:

   ![Narzędzie eksportu zbierania elektronicznych materiałów dowodowych.](../media/eDiscoveryExportTool.png)

   1. Wklej klucz eksportu skopiowany w kroku 3 w odpowiednim polu.
  
   2. Kliknij przycisk **Przeglądaj** , aby określić lokalizację, w której chcesz pobrać pliki raportu wyszukiwania.

7. Kliknij **przycisk Start** , aby pobrać wyniki wyszukiwania na komputer.
  
    **Narzędzie eksportu elektronicznego** zbierania elektronicznych materiałów dowodowych wyświetla informacje o stanie procesu eksportowania, w tym oszacowanie liczby (i rozmiaru) pozostałych elementów do pobrania. Po zakończeniu procesu eksportowania można uzyskać dostęp do plików w lokalizacji, w której zostały pobrane.
  
## <a name="whats-included-in-the-report"></a>Co jest zawarte w raporcie

Podczas generowania i eksportowania raportu dotyczącego wyników wyszukiwania zawartości są pobierane następujące dokumenty:
  
- **Podsumowanie eksportu:** Dokument Excel zawierający podsumowanie eksportu. Obejmuje to informacje, takie jak liczba wyszukiwanych źródeł zawartości, liczba wyników wyszukiwania z każdej lokalizacji zawartości, szacowana liczba elementów, rzeczywista liczba elementów, które zostaną wyeksportowane, oraz szacowany i rzeczywisty rozmiar elementów, które zostaną wyeksportowane.

   Jeśli podczas eksportowania raportu zostaną uwzględnione elementy niezawłaszczone, liczba nieweksportowanych elementów zostanie uwzględniona w łącznej liczbie szacowanych wyników wyszukiwania oraz w łącznej liczbie pobranych wyników wyszukiwania (jeśli chcesz wyeksportować wyniki wyszukiwania), które są wymienione w raporcie podsumowania eksportu. Innymi słowy, łączna liczba pobranych elementów jest równa łącznej liczbie szacowanych wyników i łącznej liczbie elementów niewyświetlonych.
  
- **Manifestu:** Plik manifestu (w formacie XML), który zawiera informacje o każdym elemencie uwzględnionym w wynikach wyszukiwania. Jeśli włączono opcję de-duplikowania, zduplikowane komunikaty nie zostaną uwzględnione w pliku manifestu.

- **Wyniki:** Dokument Excel zawierający wiersz z informacjami o każdym indeksowanym elemencie, który zostanie wyeksportowany z wynikami wyszukiwania. W przypadku poczty e-mail dziennik wyników zawiera informacje o każdej wiadomości, w tym: 

  - Lokalizacja wiadomości w źródłowej skrzynce pocztowej (w tym, czy wiadomość znajduje się w podstawowej, czy archiwum skrzynki pocztowej).

  - Data wysłania lub odebrania wiadomości.

  - Wiersz tematu z wiadomości.

  - Nadawca i adresaci wiadomości.

  W przypadku dokumentów z witryn SharePoint i OneDrive dla Firm dziennik wyników zawiera informacje o każdym dokumencie, w tym:

  - Adres URL dokumentu.

  - Adres URL zbioru witryn, w którym znajduje się dokument.

  - Data ostatniej modyfikacji dokumentu.

  - Nazwa dokumentu (który znajduje się w kolumnie Podmiot w dzienniku wyników).

  > [!NOTE]
  > Liczba wierszy w raporcie **Wyników** powinna być równa łącznej liczbie wyników wyszukiwania pomnożonej całkowitą liczbą elementów wymienionych w raporcie **Elementy unindexed** .
  
- **Trace.log:** Dziennik śledzenia, który zawiera szczegółowe informacje dotyczące rejestrowania procesu eksportowania i może pomóc w odnalezieniu problemów podczas eksportowania. Jeśli otworzysz bilet z pomoc techniczna firmy Microsoft o problemie związanym z eksportowaniem raportów wyszukiwania, może zostać wyświetlony monit o podanie tego dziennika śledzenia.

- **Elementy niewymierne:** Dokument Excel zawierający informacje o wszelkich niewyeksponowanych elementach zawartych w wynikach wyszukiwania. Jeśli podczas generowania raportu wyników wyszukiwania nie uwzględnisz elementów niezaimportowanych, ten raport będzie nadal pobierany, ale będzie pusty.
