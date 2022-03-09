---
title: Zbieranie dzienników pomocy technicznej w programie Microsoft Defender dla punktu końcowego przy użyciu funkcji odpowiedzi na żywo
description: Dowiedz się, jak zbierać dzienniki przy użyciu funkcji odpowiedzi na żywo w celu rozwiązania problemów z programem Microsoft Defender w przypadku punktu końcowego
keywords: support, log, collect, troubleshoot, live response, liveanalyzer, analyzer, live, response
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: a0d0f470a2af18dab298ba3a1af642362590da4c
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401164"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Zbieranie dzienników pomocy technicznej w programie Microsoft Defender dla punktu końcowego przy użyciu funkcji odpowiedzi na żywo


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Podczas kontaktowania się z pomocą techniczną może zostaćsz poproszony o dostarczenie pakietu wyjściowego narzędzia Microsoft Defender for Endpoint Client Analyzer.

Ten temat zawiera instrukcje dotyczące uruchamiania narzędzia za pośrednictwem usługi Live Response.

1. Pobieranie i pobieranie wymaganych skryptów dostępnych w podfolderze "Narzędzia" usługi [Microsoft Defender for Endpoint Client Analyzer](https://aka.ms/BetaMDEAnalyzer). <br>
Aby na przykład pobrać podstawowy czujnik i dzienniki kondycji urządzenia, uzyskaj zdalnego dostępu ".. \Tools\MDELiveAnalyzer.ps1".<br>
Jeśli potrzebujesz również dzienników obsługi oprogramowania antywirusowego Defender (MpSupportFiles.cab), pobierz ".. \Tools\MDELiveAnalyzerAV.ps1" 

2. [Zainicjuj sesję live response](live-response.md#initiate-a-live-response-session-on-a-device) na komputerze, który chcesz zbadać.

3. Wybierz **Upload plik do biblioteki**.

    ![Obraz przekazywania pliku.](images/upload-file.png)

4. Wybierz **pozycję Wybierz plik**.

    ![Obraz przycisku wybierz plik1.](images/choose-file.png)

5. Zaznacz pobrany plik o nazwie MDELiveAnalyzer.ps1 a następnie kliknij pozycję **Potwierdź**

   ![Obraz przycisku wybierz plik2.](images/analyzer-file.png)

6. W trakcie sesji LiveResponse użyj poniższych poleceń, aby uruchomić analizatora i zebrać plik wyników:

    ```console
    Run MDELiveAnalyzer.ps1
    GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
    ```

    [![Obraz poleceń.](images/analyzer-commands.png)](images/analyzer-commands.png#lightbox)

> [!NOTE]
>
> - Najnowszą wersję Preview aplikacji MDEClientAnalyzer można pobrać tutaj: [https://aka.ms/Betamdeanalyzer](https://aka.ms/Betamdeanalyzer).
>
> - Skrypt LiveAnalyzer pobiera pakiet rozwiązywania problemów na komputerze docelowym z: https://mdatpclientanalyzer.blob.core.windows.net.
>
>   Jeśli nie możesz zezwolić komputerowi na osiągnięcie powyższego adresu URL, przekaż plik MDEClientAnalyzerPreview.zip do biblioteki przed uruchomieniem skryptu LiveAnalyzer:
>
>   ```console
>   PutFile MDEClientAnalyzerPreview.zip -overwrite
>   Run MDELiveAnalyzer.ps1
>   GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
>   ```
>
> - Aby uzyskać więcej informacji na temat gromadzenia danych lokalnie na komputerze, jeśli komputer nie komunikuje się z usługami w chmurze programu Microsoft Defender for Endpoint lub nie jest widoczny w portalu programu Microsoft Defender for Endpoint zgodnie z oczekiwaniami, zobacz Weryfikowanie łączności klienta z usługą [Microsoft Defender](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls) dla usługi punktów końcowych.
> 
> - Zgodnie [z opisem w](live-response-command-examples.md) przykładach poleceń na żywo możesz chcieć użyć symbolu "&" na końcu polecenia, aby zbierać dzienniki jako akcję tła:
>   ```console
>   Run MDELiveAnalyzer.ps1&
>   ```


## <a name="see-also"></a>Zobacz też
- [Omówienie analizatora klientów](overview-client-analyzer.md)
- [Pobieranie i uruchamianie analizatora klienta](download-client-analyzer.md)
- [Uruchamianie analizatora klienta na Windows](run-analyzer-windows.md)
- [Uruchamianie analizatora klienta w systemie macOS lub Linux](run-analyzer-macos-linux.md)
- [Zbieranie danych na potrzeby zaawansowanego rozwiązywania problemów na Windows](data-collection-analyzer.md)
- [Opis raportu w formacie HTML analizatora](analyzer-report.md)
