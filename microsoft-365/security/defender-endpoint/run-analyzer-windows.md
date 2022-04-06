---
title: Uruchamianie analizatora klienta na Windows
description: Dowiedz się, jak uruchomić analizatora Ochrona punktu końcowego w usłudze Microsoft Defender klienta w Windows.
keywords: analizator klienta, czujnik rozwiązywania problemów, analizator, mdeanalyzer, okna
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 5fa284f5c57214f356bb6b90e12ca60ae019d277
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467142"
---
# <a name="run-the-client-analyzer-on-windows"></a>Uruchamianie analizatora klienta na Windows

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

1. Pobierz narzędzie [analizator klienta MDE](https://aka.ms/mdatpanalyzer) na Windows komputera, który chcesz zbadać.

2. Wyodrębnianie zawartości MDEClientAnalyzer.zip na komputerze.

3. Otwieranie wiersza polecenia z podwyższonym poziomem uprawnień:
    1. Przejdź do **przycisku Start** i wpisz **cmd**.
    2. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

4. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   ```dos
   HardDrivePath\MDEClientAnalyzer.cmd
   ```

   **Zastąp ścieżkę narzędzia HardDrivePath ścieżką, do której narzędzie zostało wyodrębnione— na przykład:**

   ```dos
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

Poza powyższymi informacjami dostępna jest również opcja zbierania dzienników pomocy technicznej analizatora [przy użyciu funkcji odpowiedzi na żywo](troubleshoot-collect-support-log.md).

> [!NOTE]
> Na Windows 10/11, Windows Server 2019/2022 lub Windows Server 2012R2/2016 z zainstalowanym nowoczesnym, ujednoliconym rozwiązaniem skrypt [](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) `MDEClientAnalyzer.exe` analizatora klienta wywołuje do pliku wykonywalnego o nazwie w celu uruchomienia testów łączności z adresami URL usługi w chmurze.
>
> Na Windows 8.1, Windows Server 2016 lub dowolnej poprzedniej wersji systemu operacyjnego, w której do dołączania jest używany program Microsoft Monitoring Agent (MMA), `MDEClientAnalyzerPreviousVersion.exe` skrypt analizatora klienta wywołuje do pliku wykonywalnego nazywanego do uruchamiania testów łączności adresów URL poleceń i kontrolek (CnC, Command and Control) podczas wykonywania połączenia Microsoft Monitoring Agent dla adresów `TestCloudConnection.exe` URL kanału danych cyberprzestępczych.


Wszystkie skrypty i moduły programu PowerShell dołączone do analizatora są podpisane przez firmę Microsoft.
Jeśli pliki zostały w jakikolwiek sposób zmodyfikowane, analizator powinien zakończyć działanie z następującym błędem:

:::image type="content" source="images/sigerror.png" alt-text="Błąd analizatora klienta" lightbox="images/sigerror.png":::


Jeśli ten błąd jest wyświetlany, wynik issuerInfo.txt będzie zawierał szczegółowe informacje o tym, dlaczego wystąpił i jaki plik został w związku z tym:

:::image type="content" source="images/issuerinfo.png" alt-text="Informacje o wystawcy" lightbox="images/issuerinfo.png":::


Przykładowa zawartość po MDEClientAnalyzer.ps1 zmodyfikowania:

:::image type="content" source="images/modified-ps1.png" alt-text="Zmodyfikowany plik ps1" lightbox="images/modified-ps1.png":::



## <a name="result-package-contents-on-windows"></a>Wynik zawartości pakietu na Windows

> [!NOTE]
> Dokładne przechwycone pliki mogą się zmienić w zależności od takich czynników, jak:
>
> - Wersja okien, w których jest uruchamiany analizator.
> - Dostępność kanału dziennika zdarzeń na komputerze.
> - Stan startowy czujnika EDR (czujnik jest zatrzymywany, jeśli komputer nie jest jeszcze wnoszony).
> - Jeśli w poleceniu analizatora został użyty parametr zaawansowanego rozwiązywania problemów.

Domyślnie niezapakowany plik MDEClientAnalyzerResult.zip zawiera następujące elementy.

- MDEClientAnalyzer.htm

  Jest to główny plik wyjściowy HTML, który będzie zawierał ustalenia i wskazówki, które może uruchomić skrypt analizatora na komputerze.

- Folder SystemInfoLogs \[\]
  - AddRemovePrograms.csv

    Opis: Lista oprogramowania zainstalowanego w wersji x86 w oprogramowaniu systemu operacyjnego x64 zebranym z rejestru.

  - AddRemoveProgramsWOW64.csv

    Opis: Lista oprogramowania zainstalowanego w wersji x86 w oprogramowaniu systemu operacyjnego x64 zebranym z rejestru.

    - CertValidate.log

      Opis: Szczegółowy wynik odwołania certyfikatu wykonywanego przez wywołanie do [certyfikatu CertUtil](/windows-server/administration/windows-commands/certutil).

    - dsregcmd.txt

      Opis: Dane wyjściowe z [uruchomionych dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd). Zawiera on szczegółowe informacje o stanie usługi Azure AD na komputerze.

    - IFEO.txt

      Opis: Dane wyjściowe [opcji wykonywania pliku obrazu](/previous-versions/windows/desktop/xperf/image-file-execution-options) skonfigurowanych na komputerze

    - MDEClientAnalyzer.txt

      Opis: Jest to pełny plik tekstowy ze szczegółami wykonywania skryptu analizatora.

    - MDEClientAnalyzer.xml

      Opis: format XML zawierający ustalenia skryptów analizatora.

    - RegOnboardedInfoCurrent.Json

      Opis: Wniesienie informacji o komputerze zebranych w formacie JSON z rejestru.

  - RegOnboardingInfoPolicy.Json

    Opis: Konfiguracja zasad dołączania zebranych w formacie JSON z rejestru.

    - SCHANNEL.txt

      Opis: Szczegółowe informacje na temat [konfiguracji DLAOKINNEL](/windows-server/security/tls/manage-tls) zastosowanej do komputera, takie jak zebrane z rejestru.

    - SessionManager.txt

      Opis: Ustawienia Menedżera sesji zbierają się z rejestru.

    - SSL_00010002.txt

      Opis: Szczegóły dotyczące konfiguracji [protokołu SSL zastosowanej](/windows-server/security/tls/manage-tls) do komputera zebranego z rejestru.

- EventLogs [Folder]

  - utc.evtx

    Opis: Eksportowanie dziennika zdarzeń DiagTrack

  - senseIR.evtx

    Opis: Eksportowanie dziennika zdarzeń automatycznego badania

  - sense.evtx

    Opis: Eksportowanie głównego dziennika zdarzeń czujnika

  - OperationsManager.evtx

    Opis: eksportowanie dziennika Microsoft Monitoring Agent zdarzeń




## <a name="see-also"></a>Zobacz też

- [Omówienie analizatora klientów](overview-client-analyzer.md)
- [Pobieranie i uruchamianie analizatora klienta](download-client-analyzer.md)
- [Zbieranie danych na potrzeby zaawansowanego rozwiązywania problemów na Windows](data-collection-analyzer.md)
- [Opis raportu w formacie HTML analizatora](analyzer-report.md)
