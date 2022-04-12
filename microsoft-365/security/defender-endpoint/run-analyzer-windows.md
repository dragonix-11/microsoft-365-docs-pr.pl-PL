---
title: Uruchom analizator klienta w systemie Windows
description: Dowiedz się, jak uruchomić analizator klienta Ochrona punktu końcowego w usłudze Microsoft Defender na Windows.
keywords: analizator klienta, rozwiązywanie problemów z czujnikiem, analizatorem, mdeanalyzerem, oknami
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
ms.openlocfilehash: 5ac27241297b9943f1559653777b8e1668fe7f89
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783034"
---
# <a name="run-the-client-analyzer-on-windows"></a>Uruchom analizator klienta w systemie Windows

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

1. Pobierz [narzędzie ANALIZATOR KLIENTA MDE](https://aka.ms/mdatpanalyzer) na maszynę Windows, którą należy zbadać.

2. Wyodrębnij zawartość MDEClientAnalyzer.zip na maszynie.

3. Otwórz wiersz polecenia z podwyższonym poziomem poziomu:
    1. Przejdź do **pozycji Start** i wpisz **cmd**.
    2. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

4. Wprowadź następujące polecenie i naciśnij **klawisz Enter**:

   ```dos
   HardDrivePath\MDEClientAnalyzer.cmd
   ```

   **Zastąp ciąg HardDrivePath ścieżką, do której zostało wyodrębnione narzędzie, na przykład:**

   ```dos
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

Oprócz powyższego istnieje również opcja [zbierania dzienników obsługi analizatora przy użyciu odpowiedzi na żywo.](troubleshoot-collect-support-log.md)

> [!NOTE]
> W Windows 10/11, Windows Server 2019/2022 lub Windows Server 2012R2/2016 z [zainstalowanym nowoczesnym ujednoliconym rozwiązaniem](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) skrypt analizatora klienta wywołuje plik wykonywalny o nazwie `MDEClientAnalyzer.exe` w celu uruchomienia testów łączności z adresami URL usługi w chmurze.
>
> W Windows 8.1, Windows Server 2016 lub dowolnej poprzedniej wersji systemu operacyjnego, w której do dołączania jest używany Microsoft Monitoring Agent (MMA), skrypt analizatora klienta wywołuje plik wykonywalny o nazwie `MDEClientAnalyzerPreviousVersion.exe` w celu uruchomienia testów łączności dla adresów URL poleceń i kontroli (CnC) podczas wywoływania narzędzie do łączności `TestCloudConnection.exe` Microsoft Monitoring Agent dla adresów URL kanału Cyber Data.


Wszystkie skrypty i moduły programu PowerShell dołączone do analizatora są podpisane przez firmę Microsoft.
Jeśli pliki zostały zmodyfikowane w jakikolwiek sposób, oczekuje się, że analizator zakończy pracę z następującym błędem:

:::image type="content" source="images/sigerror.png" alt-text="Błąd analizatora klienta" lightbox="images/sigerror.png":::


Jeśli ten błąd zostanie wyświetlony, dane wyjściowe issuerInfo.txt będą zawierać szczegółowe informacje o tym, dlaczego tak się stało i jaki plik został dotknięty:

:::image type="content" source="images/issuerinfo.png" alt-text="Informacje o wystawcy" lightbox="images/issuerinfo.png":::


Przykładowa zawartość po zmodyfikowaniu MDEClientAnalyzer.ps1:

:::image type="content" source="images/modified-ps1.png" alt-text="Zmodyfikowany plik ps1" lightbox="images/modified-ps1.png":::



## <a name="result-package-contents-on-windows"></a>Zawartość pakietu wyników w Windows

> [!NOTE]
> Dokładne przechwycone pliki mogą ulec zmianie w zależności od czynników, takich jak:
>
> - Wersja okien, w których jest uruchamiany analizator.
> - Dostępność kanału dziennika zdarzeń na maszynie.
> - Stan początkowy czujnika EDR (czujnik zostaje zatrzymany, jeśli maszyna nie została jeszcze dołączona).
> - Jeśli użyto zaawansowanego parametru rozwiązywania problemów z poleceniem analizatora.

Domyślnie rozpakowany plik MDEClientAnalyzerResult.zip będzie zawierać następujące elementy.

- MDEClientAnalyzer.htm

  Jest to główny plik wyjściowy HTML, który będzie zawierał wyniki i wskazówki, które może wygenerować skrypt analizatora uruchamiany na maszynie.

- Folder SystemInfoLogs \[\]
  - AddRemovePrograms.csv

    Opis: Lista oprogramowania zainstalowanego w systemie operacyjnym x86 w systemie operacyjnym x64 zebranych z rejestru.

  - AddRemoveProgramsWOW64.csv

    Opis: Lista oprogramowania zainstalowanego w systemie operacyjnym x86 w systemie operacyjnym x64 zebranych z rejestru.

    - CertValidate.log

      Opis: Szczegółowy wynik odwołania certyfikatu wykonany przez wywołanie polecenia [CertUtil](/windows-server/administration/windows-commands/certutil).

    - dsregcmd.txt

      Opis: Dane wyjściowe z uruchamiania [dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd). Zawiera on szczegółowe informacje o stanie maszyny w usłudze Azure AD.

    - IFEO.txt

      Opis: dane [wyjściowe opcji wykonywania pliku obrazu](/previous-versions/windows/desktop/xperf/image-file-execution-options) skonfigurowanych na maszynie

    - MDEClientAnalyzer.txt

      Opis: Jest to pełny plik tekstowy ze szczegółami wykonywania skryptu analizatora.

    - MDEClientAnalyzer.xml

      Opis: format XML zawierający wyniki skryptu analizatora.

    - RegOnboardedInfoCurrent.Json

      Opis: informacje o dołączonym komputerze zebrane w formacie JSON z rejestru.

  - RegOnboardingInfoPolicy.Json

    Opis: Konfiguracja zasad dołączania zebrana w formacie JSON z rejestru.

    - SCHANNEL.txt

      Opis: Szczegóły dotyczące [konfiguracji SCHANNEL](/windows-server/security/tls/manage-tls) zastosowane do maszyny, takie zebrane z rejestru.

    - SessionManager.txt

      Opis: Ustawienia specyficzne dla menedżera sesji zbierają się z rejestru.

    - SSL_00010002.txt

      Opis: Szczegóły dotyczące [konfiguracji protokołu SSL](/windows-server/security/tls/manage-tls) zastosowanej do maszyny zebranej z rejestru.

- EventLogs [Folder]

  - utc.evtx

    Opis: Eksportowanie dziennika zdarzeń DiagTrack

  - senseIR.evtx

    Opis: Eksportowanie dziennika zdarzeń zautomatyzowanego badania

  - sense.evtx

    Opis: Eksportowanie głównego dziennika zdarzeń czujnika

  - OperationsManager.evtx

    Opis: Eksportowanie dziennika zdarzeń Microsoft Monitoring Agent




## <a name="see-also"></a>Zobacz też

- [Omówienie funkcji analizatora klienta](overview-client-analyzer.md)
- [Pobierz i uruchom analizator klienta](download-client-analyzer.md)
- [ Zbieranie danych na potrzeby zaawansowanego rozwiązywania problemów w systemie Windows](data-collection-analyzer.md)
- [Zrozumienie raportu HTML analizatora](analyzer-report.md)
