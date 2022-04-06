---
title: Rozwiązywanie problemów z wydajnością
description: Rozwiązywanie problemów z wysokim użyciem procesora związanych z usługą ochrony w czasie rzeczywistym w programie Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: rozwiązywanie problemów, wydajność, wysokie wykorzystanie procesora, wysokie użycie procesora, błąd, poprawka, aktualizacja zgodności, oms, monitor, raport, Program antywirusowy Microsoft Defender
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
ms.date: 10/19/2021
audience: ITPro
ms.topic: troubleshooting
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: acd778b614128dc4927766e329f8d63fcd3fad54
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467186"
---
# <a name="troubleshoot-performance-issues-related-to-real-time-protection"></a>Rozwiązywanie problemów z wydajnością związanych z ochroną w czasie rzeczywistym


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Jeśli Twój system ma wysokie zużycie procesora lub problemy z wydajnością związane z usługą ochrony w czasie rzeczywistym w programie Ochrona punktu końcowego w usłudze Microsoft Defender, możesz przesłać zgłoszenie do pomocy technicznej firmy Microsoft. Postępuj zgodnie z instrukcjami [w zbieranie Program antywirusowy Microsoft Defender diagnostycznych](collect-diagnostic-data.md).

Jako administrator możesz również samodzielnie rozwiązywać te problemy.

Najpierw warto sprawdzić, czy problem jest powodowany przez inne oprogramowanie. Przeczytaj [Sprawdzanie, czy dostawca nie ma wykluczeń oprogramowania antywirusowego](#check-with-vendor-for-antivirus-exclusions).

W przeciwnym razie można określić, które oprogramowanie jest związane z zidentyfikowanym problemem z wydajnością, korzystając z procedury opisanej w [analizowaniu dziennika ochrony firmy Microsoft](#analyze-the-microsoft-protection-log).

Możesz również udostępnić dodatkowe dzienniki do przesyłania do pomocy technicznej firmy Microsoft, korzystając z poniższych kroków:

- [Przechwytywanie dzienników procesów za pomocą Monitora procesu](#capture-process-logs-using-process-monitor)
- [Rejestrowanie dzienników wydajności przy Windows wydajności](#capture-performance-logs-using-windows-performance-recorder)

## <a name="check-with-vendor-for-antivirus-exclusions"></a>Skontaktuj się z dostawcą, aby uzyskać informacje o wykluczeniach oprogramowania antywirusowego

Jeśli możesz łatwo zidentyfikować oprogramowanie wpływające na wydajność systemu, przejdź do centrum pomocy technicznej baza wiedzy dostawcy. Wyszukaj, czy ma zalecenia dotyczące wykluczeń oprogramowania antywirusowego. Jeśli witryna internetowa dostawcy ich nie zawiera, możesz utworzyć zgłoszenie do pomocy technicznej wraz z nim i poprosić o opublikowanie go.

Zalecamy, aby dostawcy oprogramowania przestrzegali różnych wytycznych w zakresie współpracy z branżą [w celu zminimalizowania wyników fałszywie dodatnich](https://www.microsoft.com/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/). Dostawca może przesłać swoje oprogramowanie za [pośrednictwem portalu Microsoft Security Intelligence firmowego](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper).

## <a name="analyze-the-microsoft-protection-log"></a>Analizowanie dziennika ochrony firmy Microsoft

W **pliku MPLog-xxxxxxxx-xxxxxx.log** można znaleźć informacje o szacowanym wpływie na wydajność uruchamiania oprogramowania w formacie *EstimatedImpact*:

`Per-process counts:ProcessImageName: smsswd.exe, TotalTime: 6597, Count: 1406, MaxTime: 609, MaxTimeFile: \Device\HarddiskVolume3\_SMSTaskSequence\Packages\WQ1008E9\Files\FramePkg.exe, EstimatedImpact: 65%`

<br>

****

|Nazwa pola|Opis|
|---|---|
|ProcessImageName|Nazwa obrazu procesu|
|TotalTime|Skumulowany czas trwania (w milisekundach) spędzony na skanach plików dostępnych w tym procesie|
|Liczba|Liczba zeskanowanych plików, do których uzyskano dostęp w tym procesie|
|MaxTime|Czas trwania (w milisekundach) podczas najdłuższego pojedynczego skanowania pliku, do którego uzyskał dostęp ten proces|
|MaxTimeFile|Ścieżka pliku, do którego uzyskano dostęp w tym `MaxTime` procesie, dla którego był rejestrowany najdłuższy czas trwania|
|EstimatedImpact|Procent czasu spędzonego na skanach w poszukiwaniu plików, do których uzyskano dostęp w tym procesie, w okresie, w którym ten proces wystąpiła aktywność skanowania|
|

Jeśli wpływ na wydajność jest wysoki, spróbuj dodać ten proces do wykluczeń ścieżka/proces, wykonanie czynności z procedury Konfigurowanie i weryfikowanie wykluczeń dla Program antywirusowy Microsoft Defender [skanów](collect-diagnostic-data.md).

Jeśli wykonanie poprzedniego kroku nie rozwiąże problemu, możesz zebrać więcej informacji za pośrednictwem [Monitora procesu](#capture-process-logs-using-process-monitor) lub rejestratora Windows [](#capture-performance-logs-using-windows-performance-recorder) wydajności w poniższych sekcjach.

## <a name="capture-process-logs-using-process-monitor"></a>Przechwytywanie dzienników procesów za pomocą Monitora procesu

Monitor procesu (ProcMon) to zaawansowane narzędzie do monitorowania, które umożliwia pokazywanie procesów w czasie rzeczywistym. Za jego pomocą można przechwycić występujący problem z wydajnością.

1. Pobierz [monitor procesu w wersji 3.60](/sysinternals/downloads/procmon) do folderu, takiego jak `C:\temp`.

2. Aby usunąć znacznik pliku z sieci Web:
    1. Kliknij prawym przyciskiem myszy **ProcessMonitor.zip** a następnie wybierz **pozycję Właściwości**.
    1. Na karcie *Ogólne* odszukaj pozycję *Zabezpieczenia*.
    1. Zaznacz pole obok **odblokowania**.
    1. Wybierz **pozycję Zastosuj**.

    :::image type="content" source="images/procmon-motw.png" alt-text="Strona Usuń z aplikacji ZESZYT" lightbox="images/procmon-motw.png":::

3. Rozpakuj plik, aby `C:\temp` ścieżka folderu to .`C:\temp\ProcessMonitor`

4. Skopiuj **ProcMon.exe** do Windows klienta lub Windows, który chcesz rozwiązać.

5. Przed uruchomieniem procMon upewnij się, że wszystkie inne aplikacje, które nie są związane z wysokim użyciem procesora, są zamknięte. Zminimalizuj liczbę procesów do sprawdzenia.

6. ProcMon można uruchomić na dwa sposoby.
    1. Kliknij prawym przyciskiem myszy **ProcMon.exe** a następnie **wybierz pozycję Uruchom jako administrator**.

        Ponieważ rejestrowanie jest uruchamiane automatycznie, wybierz ikonę lupy, aby zatrzymać bieżące przechwytywanie, lub użyj skrótu klawiaturowego **Ctrl+E**.

        :::image type="content" source="images/procmon-magglass.png" alt-text="Ikona lupy" lightbox="images/procmon-magglass.png":::

        Aby sprawdzić, czy przechwytywanie zostało zatrzymane, sprawdź, czy ikona lupy jest teraz wyświetlana z czerwonym znakem X.

        :::image type="content" source="images/procmon-magglass-stop.png" alt-text="Czerwony ukośnik" lightbox="images/procmon-magglass-stop.png":::

        Następnie, aby wyczyścić wcześniejsze przechwytywanie, wybierz ikonę gumki.

        :::image type="content" source="images/procmon-eraser-clear.png" alt-text="Ikona wyczyść" lightbox="images/procmon-eraser-clear.png":::

        Możesz też użyć skrótu klawiaturowego **Ctrl+X**.

    2. Drugi sposób to uruchomienie wiersza polecenia **jako administrator,** a następnie uruchomienie ze ścieżki Monitor procesu:

       :::image type="content" source="images/cmd-procmon.png" alt-text="Polecenie cmd procmon" lightbox="images/cmd-procmon.png":::

        ```console
        Procmon.exe /AcceptEula /Noconnect /Profiling
        ```

        > [!TIP]
        > Podczas przechwytywania danych okno procMon może być jak najmniejsze, co pozwala na łatwe rozpoczęcie i zatrzymanie śledzenia.
        >
        > :::image type="content" source="images/procmon-minimize.png" alt-text="Strona z wyświetlonym zminimalizowanym procmonem" lightbox="images/procmon-minimize.png":::

7. Po zakończeniu jednej z procedur w kroku 6 zobaczysz opcję ustawienia filtrów. Wybierz przycisk **OK**. Zawsze możesz filtrować wyniki po zakończeniu przechwytywania.

   :::image type="content" source="images/procmon-filter-options.png" alt-text="Strona, na której zostanie wybrana nazwa Odfiltruj proces wyklucz" lightbox="images/procmon-filter-options.png":::

8. Aby rozpocząć przechwytywanie, ponownie wybierz ikonę lupy.

9. Odtprodukuj problem.

    > [!TIP]
    > Poczekaj, aż problem zostanie w pełni odtworzony, a następnie zwróć uwagę na sygnaturę czasową podczas rozpoczynania śledzenia.

10. Po dwóch do czterech minutach aktywności procesu podczas wysokiego obciążenia procesora zatrzymaj przechwytywanie, wybierając ikonę lupy.

11. Aby zapisać przechwycony obraz pod unikatową nazwą i w formacie pml, wybierz pozycję **Plik** , a następnie wybierz pozycję **Zapisz....** Pamiętaj, aby zaznaczyć przyciski radiowe **Wszystkie zdarzenia** i **Natywny format monitora procesu (PML**).

    :::image type="content" source="images/procmon-savesettings1.png" alt-text="Strona ustawień zapisywania" lightbox="images/procmon-savesettings1.png":::

12. Aby poprawić śledzenie, zmień ścieżkę domyślną z miejsca, w `C:\temp\ProcessMonitor\LogFile.PML` `C:\temp\ProcessMonitor\%ComputerName%_LogFile_MMDDYEAR_Repro_of_issue.PML` którym:
    - `%ComputerName%` to nazwa urządzenia
    - `MMDDYEAR` to miesiąc, dzień i rok
    - `Repro_of_issue` to nazwa problemu, który próbujesz odtworzyć.

    > [!TIP]
    > Jeśli masz system roboczy, możesz uzyskać przykładowy dziennik do porównania.

13. Spakuj plik pml i prześlij go do pomocy technicznej firmy Microsoft.

## <a name="capture-performance-logs-using-windows-performance-recorder"></a>Rejestrowanie dzienników wydajności przy Windows wydajności

Możesz użyć rejestratora Windows wydajności (WPR), aby dołączyć dodatkowe informacje do zgłoszenia do pomocy technicznej firmy Microsoft. WPR to zaawansowane narzędzie do nagrywania, które tworzy śledzenie zdarzeń dla Windows nagrań.

WK jest częścią zestawu Windows Assessment and Deployment Kit (Windows ADK) i można go pobrać ze strony Pobieranie i instalowanie pakietu [Windows ADK](/windows-hardware/get-started/adk-install). Możesz również pobrać go w ramach zestawu Windows 10 Software Development Kit na stronie [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/).

Za pomocą interfejsu użytkownika WPR możesz wykonać czynności opisane w tece Przechwytywanie dzienników wydajności [za pomocą interfejsu użytkownika funkcji WPR](#capture-performance-logs-using-the-wpr-ui).

Ewentualnie możesz również użyć narzędzia wiersza polecenia *wpr.exe*, które jest dostępne w programie Windows 8 i nowszych wersjach, zgodnie z instrukcjami w przechwytywaniu dzienników wydajności przy użyciu interfejsu [wideo usługi WPR](#capture-performance-logs-using-the-wpr-cli).

### <a name="capture-performance-logs-using-the-wpr-ui"></a>Przechwytywanie dzienników wydajności przy użyciu interfejsu użytkownika usług WPR

> [!TIP]
> Jeśli ten problem występuje na wielu urządzeniach, użyj tego, na którym jest najwięcej pamięci RAM.

1. Pobierz i zainstaluj wpr.

2. W *Windows wydajności kliknij* prawym przyciskiem myszy pozycję Windows **Wydajności**.

   :::image type="content" source="images/wpr-01.png" alt-text="The menu Start" lightbox="images/wpr-01.png":::

    Wybierz **pozycję Więcej**. Wybierz **pozycję Uruchom jako administrator**.

3. Gdy zostanie wyświetlone okno dialogowe Kontrola konta użytkownika, wybierz pozycję **Tak**.

   :::image type="content" source="images/wpt-yes.png" alt-text="Strona UAC" lightbox="images/wpt-yes.png":::

4. Następnie pobierz profil [Ochrona punktu końcowego w usłudze Microsoft Defender analizie](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp) danych i zapisz go jako `MDAV.wprp` w folderze, na przykład `C:\temp`.

5. W oknie dialogowym WPR wybierz pozycję **Więcej opcji**.

   :::image type="content" source="images/wpr-03.png" alt-text="Strona, na której można wybrać więcej opcji" lightbox="images/wpr-03.png":::


6. Wybierz **pozycję Dodaj profile i** przejdź do ścieżki `MDAV.wprp` pliku.

7. Następnie w obszarze Wymiary niestandardowe powinien być wyświetlony nowy zestaw profilów o nazwie Ochrona punktu końcowego w usłudze Microsoft Defender *pod* nim.

   :::image type="content" source="images/wpr-infile.png" alt-text="Plik w" lightbox="images/wpr-infile.png":::

    > [!WARNING]
    > Jeśli Twój Windows Server ma co najmniej 64 GB pamięci RAM, użyj niestandardowych miar `Microsoft Defender for Endpoint analysis for large servers` zamiast `Microsoft Defender for Endpoint analysis`. W przeciwnym razie system może zużywać dużą ilość niestronicowej puli pamięci lub buforów, które mogą prowadzić do niestabilności systemu. Można wybrać profile do dodania, rozwijając **analizę zasobów**.
    Ten profil niestandardowy zapewnia niezbędny kontekst do szczegółowej analizy wydajności.

8. Aby użyć niestandardowego profilu Ochrona punktu końcowego w usłudze Microsoft Defender szczegółowego profilu analizy w interfejsie użytkownika funkcji WPR:

    1. Upewnij się, że żadne profile nie są zaznaczone w grupach Klasy pierwszego *poziomu,* *Analiza zasobów* i *Analiza scenariuszy* .
    2. Wybierz **pozycję Wymiary niestandardowe**.
    3. Wybierz **Ochrona punktu końcowego w usłudze Microsoft Defender analizę**.
    4. Wybierz **pozycję Verbose (Pełne** informacje) *w obszarze Detail level (* Poziom szczegółów).
    5. W **obszarze Tryb** **rejestrowania wybierz** pozycję Plik lub Pamięć.

    > [!IMPORTANT]
    > Wybierz pozycję *Plik,* aby korzystać z trybu rejestrowania plików, jeśli problem z wydajnością może być odtworzony bezpośrednio przez użytkownika. Większość problemów należy do tej kategorii. Jeśli jednak użytkownik nie może bezpośrednio odtworzyć problemu, ale może go łatwo zauważyć, gdy ten problem wystąpi, powinien wybrać pozycję  Pamięć, aby użyć trybu rejestrowania pamięci. Dzięki temu dziennik śledzenia nie zostanie zawężone zbyt długo.

9. Teraz możesz już zbierać dane. Zamknij wszystkie aplikacje, które nie są istotne dla powtórzenia problemu z wydajnością. Możesz wybrać pozycję **Ukryj opcje,** aby zachować małą ilość miejsca zajmowanego przez okno WPR.

   :::image type="content" source="images/wpr-08.png" alt-text="Opcje ukrywania" lightbox="images/wpr-08.png":::

    > [!TIP]
    > Spróbuj uruchomić śledzenie od pełnej liczby sekund. Na przykład 01:30:00. Ułatwi to analizowanie danych. Ponadto staraj się śledzić sygnaturę czasową dokładnie tego, kiedy problem jest powtarzany.

10. Kliknij przycisk **Start**.

    :::image type="content" source="images/wpr-09.png" alt-text="Strona Record system information (Rejestrowanie informacji o systemie)" lightbox="images/wpr-09.png":::

11. Odtprodukuj problem.

    > [!TIP]
    > Zachęć zbieranie danych do nie więcej niż pięć minut. Dwie do trzech minut to dobry zakres, ponieważ zbierana jest sporo danych.

12. Wybierz **Zapisz**.

    :::image type="content" source="images/wpr-10.png" alt-text="Opcja Zapisz" lightbox="images/wpr-10.png":::

13. Wypełnij wpisz **szczegółowy opis problemu,** aby uzyskać informacje o problemie i instrukcje dotyczące jego odtworzenia.

    :::image type="content" source="images/wpr-12.png" alt-text="Okienko, w którym należy wypełnić" lightbox="images/wpr-12.png":::

    1. Wybierz **pozycję Nazwa pliku:,** aby określić miejsce, w którym zostanie zapisany plik śledzenia. Domyślnie jest on zapisywany w .`%user%\Documents\WPR Files\`
    1. Wybierz **Zapisz**.

14. Poczekaj na scalenie śledzenia.

    :::image type="content" source="images/wpr-13.png" alt-text="Ogólne śledzenia zbierania danych pZP" lightbox="images/wpr-13.png":::

15. Po zapisaniu śledzenia wybierz pozycję **Otwórz folder**.

    :::image type="content" source="images/wpr-14.png" alt-text="Strona z powiadomieniem o zapisaniu śledzenia wpr" lightbox="images/wpr-14.png":::

    Dołącz zarówno plik, jak i folder do swojego przesyłania do pliku pomoc techniczna firmy Microsoft.

    :::image type="content" source="images/wpr-15.png" alt-text="Szczegóły pliku i folderu" lightbox="images/wpr-15.png":::

### <a name="capture-performance-logs-using-the-wpr-cli"></a>Przechwytywanie dzienników wydajności przy użyciu interfejsu wideo usługi WPR

Narzędzie wiersza polecenia, *wpr.exe* jest częścią systemu operacyjnego, zaczynając od Windows 8. Aby zebrać dane śledzenia DANYCH SPR za pomocą narzędzia wiersza polecenia, wpr.exe:

1. Pobierz **[Ochrona punktu końcowego w usłudze Microsoft Defender analizy](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp)** wydajności, aby uzyskać `MDAV.wprp` wyniki śledzenia wydajności do pliku o nazwie w katalogu lokalnym, takim jak `C:\traces`.

2. Kliknij prawym przyciskiem myszy **ikonę Menu Start** i wybierz pozycję Windows PowerShell **(Administrator)** lub Wiersz polecenia **(Administrator),** aby otworzyć okno wiersza polecenia Administrator.

3. Gdy zostanie wyświetlone okno dialogowe Kontrola konta użytkownika, wybierz pozycję **Tak**.

4. W wierszu polecenia z podwyższonym poziomem uprawnień uruchom następujące polecenie, aby uruchomić Ochrona punktu końcowego w usłudze Microsoft Defender śledzenie wydajności:

    ```console
    wpr.exe -start C:\traces\MDAV.wprp!WD.Verbose -filemode
    ```

    > [!WARNING]
    > Jeśli Twój Windows serwera ma co najmniej 64 GB pamięci RAM, `WDForLargeServers.Light` `WDForLargeServers.Verbose` `WD.Light` `WD.Verbose`użyj profilów zamiast profilów i . W przeciwnym razie system może zużywać dużą ilość niestronicowej puli pamięci lub buforów, które mogą prowadzić do niestabilności systemu.

5. Odtprodukuj problem.

    > [!TIP]
    > Niech zbieranie danych nie może być większe niż pięć minut. W zależności od scenariusza dobrym zakresem są dwie do trzech minut, ponieważ zbierana jest wiele danych.

6. W wierszu z podwyższonym poziomem uprawnień uruchom następujące polecenie, aby zatrzymać śledzenie wydajności, upewniąc się, że podano informacje o problemie i  sposobu jego odtworzenia:

    ```console
    wpr.exe -stop merged.etl "Timestamp when the issue was reproduced, in HH:MM:SS format" "Description of the issue" "Any error that popped up"
    ```

7. Poczekaj na scalenie śledzenia.

8. Dołącz zarówno plik, jak i folder do przesłania do pomocy technicznej firmy Microsoft.

## <a name="see-also"></a>Zobacz też

- [Zbieranie Program antywirusowy Microsoft Defender diagnostycznych](collect-diagnostic-data.md)
- [Konfigurowanie i weryfikowanie wykluczeń Program antywirusowy Microsoft Defender skanowania](configure-exclusions-microsoft-defender-antivirus.md)
