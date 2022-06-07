---
title: Rozwiąż problemy z wydajnością
description: Rozwiązywanie problemów z wysokim użyciem procesora CPU związanych z usługą ochrony w czasie rzeczywistym w usłudze Microsoft Defender for Endpoint.
keywords: rozwiązywanie problemów, wydajność, wysokie wykorzystanie procesora CPU, wysokie użycie procesora CPU, błąd, poprawka, zgodność aktualizacji, oms, monitorowanie, raport, program antywirusowy Microsoft Defender
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
ms.openlocfilehash: 06bcba129646eb7c3f820d95dae5fd3fc77805dd
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923264"
---
# <a name="troubleshoot-performance-issues-related-to-real-time-protection"></a>Rozwiąż problemy z wydajnością związane z ochroną w czasie rzeczywistym


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Jeśli w systemie występuje wysokie użycie procesora CPU lub problemy z wydajnością związane z usługą ochrony w czasie rzeczywistym w usłudze Microsoft Defender for Endpoint, możesz przesłać bilet do pomocy technicznej firmy Microsoft. Wykonaj kroki opisane w [temacie Zbieranie danych diagnostycznych programu antywirusowego Microsoft Defender](collect-diagnostic-data.md).

Jako administrator możesz również samodzielnie rozwiązywać te problemy.

Najpierw możesz sprawdzić, czy problem jest spowodowany przez inne oprogramowanie. Przeczytaj [artykuł Sprawdź u dostawcy, czy nie ma wykluczeń programu antywirusowego](#check-with-vendor-for-antivirus-exclusions).

W przeciwnym razie można określić, które oprogramowanie jest związane z zidentyfikowanym problemem z wydajnością, wykonując kroki opisane w [temacie Analizowanie dziennika ochrony firmy Microsoft](#analyze-the-microsoft-protection-log).

Możesz również udostępnić dodatkowe dzienniki do przesyłania do pomocy technicznej firmy Microsoft, wykonując kroki opisane w temacie:

- [Przechwytywanie dzienników procesów przy użyciu monitora procesów](#capture-process-logs-using-process-monitor)
- [Przechwytywanie dzienników wydajności przy użyciu rejestratora wydajności systemu Windows](#capture-performance-logs-using-windows-performance-recorder)

## <a name="check-with-vendor-for-antivirus-exclusions"></a>Skontaktuj się z dostawcą w celu wyszukania wykluczeń antywirusowych

Jeśli możesz łatwo zidentyfikować oprogramowanie wpływające na wydajność systemu, przejdź do bazy wiedzy lub centrum pomocy technicznej dostawcy oprogramowania. Wyszukaj, czy mają zalecenia dotyczące wykluczeń antywirusowych. Jeśli witryna internetowa dostawcy ich nie ma, możesz otworzyć z nim bilet pomocy technicznej i poprosić go o opublikowanie go.

Zalecamy, aby dostawcy oprogramowania postępowali zgodnie z różnymi wytycznymi w temacie [Współpraca z branżą w celu zminimalizowania wyników fałszywie dodatnich](https://www.microsoft.com/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/). Dostawca może przesłać swoje oprogramowanie za pośrednictwem [portalu Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper).

## <a name="analyze-the-microsoft-protection-log"></a>Analizowanie dziennika ochrony firmy Microsoft
Plik dziennika ochrony firmy Microsoft można znaleźć w folderze **C:\ProgramData\Microsoft\Windows Defender\Support**.

W **pliku MPLog-xxxxxxxx-xxxxxx.log** można znaleźć informacje o szacowanym wpływie na wydajność uruchamiania oprogramowania jako *EstimatedImpact*:

`Per-process counts:ProcessImageName: smsswd.exe, TotalTime: 6597, Count: 1406, MaxTime: 609, MaxTimeFile: \Device\HarddiskVolume3\_SMSTaskSequence\Packages\WQ1008E9\Files\FramePkg.exe, EstimatedImpact: 65%`

<br>

****

|Nazwa pola|Opis|
|---|---|
|ProcessImageName|Nazwa obrazu procesu|
|Totaltime|Skumulowany czas trwania w milisekundach poświęcony na skanowanie plików, do których uzyskuje się dostęp w tym procesie|
|Liczba|Liczba zeskanowanych plików, do których uzyskuje się dostęp w tym procesie|
|MaxTime|Czas trwania w milisekundach w najdłuższym pojedynczym skanowaniu pliku uzyskanego przez ten proces|
|MaxTimeFile|Ścieżka pliku, do którego uzyskano dostęp w ramach tego procesu, dla którego zarejestrowano najdłuższe skanowanie `MaxTime` czasu trwania|
|EstimatedImpact|Procent czasu spędzonego na skanowaniach plików, do których ten proces uzyskiwał dostęp poza okresem, w którym ten proces doświadczył działania skanowania|
|

Jeśli wpływ na wydajność jest wysoki, spróbuj dodać proces do wykluczeń ścieżki/procesu, wykonując kroki opisane w [temacie Konfigurowanie i weryfikowanie wykluczeń dla skanowania programu antywirusowego Microsoft Defender](collect-diagnostic-data.md).

Jeśli poprzedni krok nie rozwiąże problemu, możesz zebrać więcej informacji za pośrednictwem [monitora procesów](#capture-process-logs-using-process-monitor) lub [rejestratora wydajności systemu Windows](#capture-performance-logs-using-windows-performance-recorder) w poniższych sekcjach.

## <a name="capture-process-logs-using-process-monitor"></a>Przechwytywanie dzienników procesów przy użyciu monitora procesów

Process Monitor (ProcMon) to zaawansowane narzędzie do monitorowania, które może wyświetlać procesy w czasie rzeczywistym. Można go użyć do przechwycenia problemu z wydajnością w miarę jego występowania.

1. Pobierz [monitor procesów w wersji 3.60](/sysinternals/downloads/procmon) do folderu takiego jak `C:\temp`.

2. Aby usunąć znacznik pliku sieci Web:
    1. Kliknij prawym przyciskiem myszy **ProcessMonitor.zip** i wybierz pozycję **Właściwości**.
    1. Na karcie *Ogólne* poszukaj pozycji *Zabezpieczenia*.
    1. Zaznacz pole wyboru obok **pozycji Odblokuj**.
    1. Wybierz pozycję **Zastosuj**.

    :::image type="content" source="images/procmon-motw.png" alt-text="Strona Remove MOTW (Usuwanie motw)" lightbox="images/procmon-motw.png":::

3. Rozpakuj plik w `C:\temp` pliku, aby ścieżka folderu to `C:\temp\ProcessMonitor`.

4. Skopiuj **ProcMon.exe**  do klienta systemu Windows lub serwera z systemem Windows, z którym są rozwiązywane problemy.

5. Przed uruchomieniem narzędzia ProcMon upewnij się, że wszystkie inne aplikacje niezwiązane z problemem z wysokim użyciem procesora CPU zostały zamknięte. Spowoduje to zminimalizowanie liczby procesów do sprawdzenia.

6. Aplikację ProcMon można uruchomić na dwa sposoby.
    1. Kliknij prawym przyciskiem myszy **ProcMon.exe** i wybierz pozycję **Uruchom jako administrator**.

        Ponieważ rejestrowanie rozpoczyna się automatycznie, wybierz ikonę lupy, aby zatrzymać bieżące przechwytywanie lub użyć skrótu klawiaturowego **Ctrl+E**.

        :::image type="content" source="images/procmon-magglass.png" alt-text="Ikona lupy" lightbox="images/procmon-magglass.png":::

        Aby sprawdzić, czy przechwytywanie zostało zatrzymane, sprawdź, czy ikona lupy jest teraz wyświetlana z czerwonym symbolem X.

        :::image type="content" source="images/procmon-magglass-stop.png" alt-text="Czerwony ukośnik" lightbox="images/procmon-magglass-stop.png":::

        Następnie, aby wyczyścić wcześniejsze przechwytywanie, wybierz ikonę gumki.

        :::image type="content" source="images/procmon-eraser-clear.png" alt-text="Ikona wyczyść" lightbox="images/procmon-eraser-clear.png":::

        Możesz też użyć skrótu klawiaturowego **Ctrl+X**.

    2. Drugim sposobem jest uruchomienie **wiersza polecenia** jako administratora, a następnie z poziomu ścieżki Monitor procesu uruchom polecenie:

       :::image type="content" source="images/cmd-procmon.png" alt-text="Narzędzie cmd procmon" lightbox="images/cmd-procmon.png":::

        ```console
        Procmon.exe /AcceptEula /Noconnect /Profiling
        ```

        > [!TIP]
        > Ustaw okno ProcMon tak małe, jak to możliwe podczas przechwytywania danych, aby można było łatwo uruchomić i zatrzymać ślad.
        >
        > :::image type="content" source="images/procmon-minimize.png" alt-text="Strona z minimalizowaniem procmona" lightbox="images/procmon-minimize.png":::

7. Po wykonaniu jednej z procedur w kroku 6 zostanie wyświetlona opcja ustawienia filtrów. Wybierz przycisk **OK**. Zawsze można filtrować wyniki po zakończeniu przechwytywania.

   :::image type="content" source="images/procmon-filter-options.png" alt-text="Strona, na której wybrano opcję Wykluczenie systemu jako nazwę procesu filtrowania" lightbox="images/procmon-filter-options.png":::

8. Aby rozpocząć przechwytywanie, ponownie wybierz ikonę lupy.

9. Odtwórz problem.

    > [!TIP]
    > Poczekaj na pełne odtworzenie problemu, a następnie zanotuj sygnaturę czasowa rozpoczęcia śledzenia.

10. Po upływie od dwóch do czterech minut działania procesu w warunku wysokiego użycia procesora CPU zatrzymaj przechwytywanie, wybierając ikonę lupy.

11. Aby zapisać przechwytywanie z unikatową nazwą i formatem pml, wybierz pozycję **Plik**, a następnie wybierz pozycję **Zapisz...**. Upewnij się, że wybrano przyciski **radiowe Wszystkie zdarzenia** i **Format natywnego monitora procesów (PML).**

    :::image type="content" source="images/procmon-savesettings1.png" alt-text="Strona zapisywania ustawień" lightbox="images/procmon-savesettings1.png":::

12. Aby lepiej śledzić, zmień domyślną ścieżkę z `C:\temp\ProcessMonitor\LogFile.PML` miejsca:`C:\temp\ProcessMonitor\%ComputerName%_LogFile_MMDDYEAR_Repro_of_issue.PML`
    - `%ComputerName%` to nazwa urządzenia
    - `MMDDYEAR` to miesiąc, dzień i rok
    - `Repro_of_issue` to nazwa problemu, który próbujesz odtworzyć

    > [!TIP]
    > Jeśli masz działający system, możesz pobrać przykładowy dziennik do porównania.

13. Skompresuj plik pml i prześlij go do pomocy technicznej firmy Microsoft.

## <a name="capture-performance-logs-using-windows-performance-recorder"></a>Przechwytywanie dzienników wydajności przy użyciu rejestratora wydajności systemu Windows

Możesz użyć rejestratora wydajności systemu Windows (WPR), aby uwzględnić dodatkowe informacje w przesłaniu do pomocy technicznej firmy Microsoft. WPR to zaawansowane narzędzie do rejestrowania, które tworzy śledzenie zdarzeń dla nagrań systemu Windows.

Funkcja WPR jest częścią zestawu Windows Assessment and Deployment Kit (Windows ADK) i można go pobrać z [witryny Pobierz i zainstaluj zestaw Windows ADK](/windows-hardware/get-started/adk-install). Można go również pobrać w ramach zestawu Windows 10 Software Development Kit w zestawie [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/).

Interfejsu użytkownika funkcji WPR można użyć, wykonując kroki opisane w [temacie Przechwytywanie dzienników wydajności przy użyciu interfejsu użytkownika funkcji WPR](#capture-performance-logs-using-the-wpr-ui).

Alternatywnie możesz również użyć narzędzia wiersza polecenia *wpr.exe*, które jest dostępne w systemie Windows 8 i nowszych wersjach, wykonując kroki opisane w [temacie Przechwytywanie dzienników wydajności przy użyciu interfejsu wiersza polecenia funkcji WPR](#capture-performance-logs-using-the-wpr-cli).

### <a name="capture-performance-logs-using-the-wpr-ui"></a>Przechwytywanie dzienników wydajności przy użyciu interfejsu użytkownika funkcji WPR

> [!TIP]
> Jeśli ten problem występuje na wielu urządzeniach, użyj tego, które ma najwięcej pamięci RAM.

1. Pobierz i zainstaluj samoobsługowe resetowanie hasła.

2. W obszarze *Zestawy systemu Windows* kliknij prawym przyciskiem myszy pozycję **Rejestrator wydajności systemu Windows**.

   :::image type="content" source="images/wpr-01.png" alt-text="Menu Start" lightbox="images/wpr-01.png":::

    Wybierz pozycję **Więcej**. Wybierz pozycję **Uruchom jako administrator**.

3. Po wyświetleniu okna dialogowego Kontrola konta użytkownika wybierz pozycję **Tak**.

   :::image type="content" source="images/wpt-yes.png" alt-text="Strona funkcji UAC" lightbox="images/wpt-yes.png":::

4. Następnie pobierz profil [analizy usługi Microsoft Defender for Endpoint](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp) i zapisz jako `MDAV.wprp` w folderze takim jak `C:\temp`.

5. W oknie dialogowym WPR wybierz pozycję **Więcej opcji**.

   :::image type="content" source="images/wpr-03.png" alt-text="Strona, na której można wybrać więcej opcji" lightbox="images/wpr-03.png":::


6. Wybierz pozycję **Dodaj profile...** i przejdź do ścieżki `MDAV.wprp` pliku.

7. Następnie powinien zostać wyświetlony nowy profil ustawiony w obszarze *Pomiary niestandardowe* o nazwie *Microsoft Defender dla analizy punktu końcowego* pod nim.

   :::image type="content" source="images/wpr-infile.png" alt-text="Plik w pliku" lightbox="images/wpr-infile.png":::

    > [!WARNING]
    > Jeśli system Windows Server ma co najmniej 64 GB pamięci RAM, użyj miary `Microsoft Defender for Endpoint analysis for large servers` niestandardowej `Microsoft Defender for Endpoint analysis`zamiast . W przeciwnym razie system może zużywać dużą ilość niestronicowanej pamięci lub buforów puli, co może prowadzić do niestabilności systemu. Możesz wybrać profile do dodania, rozwijając pozycję **Analiza zasobów**.
    Ten profil niestandardowy zapewnia kontekst niezbędny do szczegółowej analizy wydajności.

8. Aby użyć niestandardowego profilu analizy usługi Microsoft Defender for Endpoint w interfejsie użytkownika funkcji WPR:

    1. Upewnij się, że nie wybrano żadnych profilów w grupach *Klasyfikacja pierwszego poziomu*, *Analiza zasobów* i *Analiza scenariuszy* .
    2. Wybierz pozycję **Miary niestandardowe**.
    3. Wybierz pozycję **Microsoft Defender na potrzeby analizy punktów końcowych**.
    4. Wybierz pozycję **Pełne w** obszarze Poziom *szczegółów* .
    5. Wybierz pozycję **Plik** lub **Pamięć** w trybie rejestrowania.

    > [!IMPORTANT]
    > Wybierz pozycję *Plik* , aby użyć trybu rejestrowania plików, jeśli problem z wydajnością może zostać odtworzony bezpośrednio przez użytkownika. Większość problemów należy do tej kategorii. Jeśli jednak użytkownik nie może bezpośrednio odtworzyć problemu, ale może go łatwo zauważyć po wystąpieniu problemu, użytkownik powinien wybrać pozycję *Pamięć* , aby użyć trybu rejestrowania pamięci. Dzięki temu dziennik śledzenia nie będzie nadmiernie rozszerzany ze względu na długi czas trwania.

9. Teraz możesz już zbierać dane. Zamknij wszystkie aplikacje, które nie mają zastosowania do odtwarzania problemu z wydajnością. Możesz wybrać pozycję **Ukryj opcje** , aby zachować małe miejsce zajmowane przez okno WPR.

   :::image type="content" source="images/wpr-08.png" alt-text="Opcje Ukryj" lightbox="images/wpr-08.png":::

    > [!TIP]
    > Spróbuj uruchomić ślad o pełnej liczbie sekund. Na przykład 01:30:00. Ułatwi to analizowanie danych. Spróbuj również śledzić znacznik czasu dokładnie po odtworzeniu problemu.

10. Kliknij przycisk **Start**.

    :::image type="content" source="images/wpr-09.png" alt-text="Strona Rejestrowanie informacji o systemie" lightbox="images/wpr-09.png":::

11. Odtwórz problem.

    > [!TIP]
    > Zachowaj zbieranie danych nie dłużej niż pięć minut. Od dwóch do trzech minut jest to dobry zakres, ponieważ zbieranych jest wiele danych.

12. Wybierz **Zapisz**.

    :::image type="content" source="images/wpr-10.png" alt-text="Opcja Zapisz" lightbox="images/wpr-10.png":::

13. Wypełnij **pozycję Wpisz w szczegółowym opisie problemu:** z informacjami o problemie i sposobie odtworzenia problemu.

    :::image type="content" source="images/wpr-12.png" alt-text="Okienko, w którym wypełniasz" lightbox="images/wpr-12.png":::

    1. Wybierz **pozycję Nazwa pliku:** aby określić, gdzie zostanie zapisany plik śledzenia. Domyślnie jest on zapisywany w pliku `%user%\Documents\WPR Files\`.
    1. Wybierz **Zapisz**.

14. Poczekaj na scalanie śledzenia.

    :::image type="content" source="images/wpr-13.png" alt-text="Ogólny ślad zbierania WPR" lightbox="images/wpr-13.png":::

15. Po zapisaniu śledzenia wybierz pozycję **Otwórz folder**.

    :::image type="content" source="images/wpr-14.png" alt-text="Strona z powiadomieniem o zapisaniu śledzenia funkcji WPR" lightbox="images/wpr-14.png":::

    Uwzględnij plik i folder w przesłaniu do pomocy technicznej firmy Microsoft.

    :::image type="content" source="images/wpr-15.png" alt-text="Szczegóły pliku i folderu" lightbox="images/wpr-15.png":::

### <a name="capture-performance-logs-using-the-wpr-cli"></a>Przechwytywanie dzienników wydajności przy użyciu interfejsu wiersza polecenia funkcji WPR

Narzędzie wiersza polecenia *wpr.exe* jest częścią systemu operacyjnego, począwszy od systemu Windows 8. Aby zebrać ślad WPR przy użyciu narzędzia wiersza polecenia wpr.exe:

1. Pobierz profil **[analizy usługi Microsoft Defender for Endpoint](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp)** w celu śledzenia wydajności do pliku o nazwie `MDAV.wprp` w katalogu lokalnym, takim jak `C:\traces`.

2. Kliknij prawym przyciskiem myszy ikonę **Menu Start** i wybierz pozycję **Windows PowerShell (Administrator)** lub **Wiersz polecenia (administrator),** aby otworzyć okno wiersza polecenia administratora.

3. Po wyświetleniu okna dialogowego Kontrola konta użytkownika wybierz pozycję **Tak**.

4. W wierszu polecenia z podwyższonym poziomem uprawnień uruchom następujące polecenie, aby uruchomić śledzenie wydajności usługi Microsoft Defender for Endpoint:

    ```console
    wpr.exe -start C:\traces\MDAV.wprp!WD.Verbose -filemode
    ```

    > [!WARNING]
    > Jeśli system Windows Server ma co najmniej 64 GB pamięci RAM, użyj profilów `WDForLargeServers.Light` i `WDForLargeServers.Verbose` zamiast profilów `WD.Light` oraz `WD.Verbose`odpowiednio . W przeciwnym razie system może zużywać dużą ilość niestronicowanej pamięci lub buforów puli, co może prowadzić do niestabilności systemu.

5. Odtwórz problem.

    > [!TIP]
    > Zachowaj zbieranie danych nie dłużej niż pięć minut. W zależności od scenariusza od dwóch do trzech minut jest to dobry zakres, ponieważ zbieranych jest wiele danych.

6. W wierszu polecenia z podwyższonym poziomem uprawnień uruchom następujące polecenie, aby zatrzymać śledzenie wydajności, zapewniając informacje o problemie i sposobie odtworzenia problemu:

    ```console
    wpr.exe -stop merged.etl "Timestamp when the issue was reproduced, in HH:MM:SS format" "Description of the issue" "Any error that popped up"
    ```

7. Poczekaj, aż ślad zostanie scalony.

8. Dołącz plik i folder do przesyłania do pomocy technicznej firmy Microsoft.

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Zbieranie danych diagnostycznych programu antywirusowego Microsoft Defender](collect-diagnostic-data.md)
- [Konfigurowanie i weryfikowanie wykluczeń dla skanowania programu antywirusowego Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
