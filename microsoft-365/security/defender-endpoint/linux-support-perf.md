---
title: Rozwiązywanie problemów z wydajnością Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux
description: Rozwiązywanie problemów z wydajnością w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, performance
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3452f36068facc92885047184f7e00828f569cbc
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873011"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Rozwiązywanie problemów z wydajnością Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Ten dokument zawiera instrukcje dotyczące sposobu zawężenia problemów z wydajnością związanych z usługą Defender for Endpoint w systemie Linux przy użyciu dostępnych narzędzi diagnostycznych w celu zrozumienia i wyeliminowania istniejących braków zasobów oraz procesów, które sprawiają, że system znajduje się w takich sytuacjach. Problemy z wydajnością są spowodowane głównie wąskimi gardłami w co najmniej jednym podsystemie sprzętowym, w zależności od profilu wykorzystania zasobów w systemie. Czasami aplikacje są wrażliwe na zasoby we/wy dysku i mogą potrzebować większej pojemności procesora CPU, a czasami niektóre konfiguracje nie są trwałe i mogą wyzwalać zbyt wiele nowych procesów i otwierać zbyt wiele deskryptorów plików.

W zależności od uruchomionych aplikacji i charakterystyk urządzenia może wystąpić nieoptymalna wydajność podczas uruchamiania usługi Defender for Endpoint w systemie Linux. W szczególności aplikacje lub procesy systemowe uzyskujące dostęp do wielu zasobów, takich jak procesor CPU, dysk i pamięć w krótkim czasie, mogą prowadzić do problemów z wydajnością w usłudze Defender for Endpoint w systemie Linux.

> [!WARNING]
> Przed rozpoczęciem **upewnij się, że inne produkty zabezpieczające nie są obecnie uruchomione na urządzeniu**. Wiele produktów zabezpieczeń może powodować konflikt i wpływać na wydajność hosta.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Rozwiązywanie problemów z wydajnością przy użyciu statystyk ochrony w czasie rzeczywistym

**Dotyczy:**
- Tylko problemy z wydajnością związane z usługą AV

Ochrona w czasie rzeczywistym (RTP) to funkcja usługi Defender for Endpoint w systemie Linux, która stale monitoruje i chroni urządzenie przed zagrożeniami. Składa się z monitorowania plików i procesów oraz innych heurystycznych.

Poniższe kroki mogą służyć do rozwiązywania i rozwiązywania tych problemów:

1. Wyłącz ochronę w czasie rzeczywistym przy użyciu jednej z następujących metod i sprawdź, czy wydajność się poprawia. Takie podejście pomaga zawęzić, czy usługa Defender dla punktu końcowego w systemie Linux przyczynia się do problemów z wydajnością.

    Jeśli urządzenie nie jest zarządzane przez organizację, ochronę w czasie rzeczywistym można wyłączyć z poziomu wiersza polecenia:

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    Jeśli urządzenie jest zarządzane przez organizację, administrator może wyłączyć ochronę w czasie rzeczywistym, korzystając z instrukcji w [temacie Ustawianie preferencji dla usługi Defender dla punktu końcowego w systemie Linux](linux-preferences.md).

    > [!NOTE]
    > Jeśli problem z wydajnością będzie się powtarzać, gdy ochrona w czasie rzeczywistym jest wyłączona, źródłem problemu może być składnik wykrywanie i reagowanie w punktach końcowych (EDR). W takim przypadku wykonaj kroki opisane w sekcji **Rozwiązywanie problemów z wydajnością przy użyciu analizatora klienta Ochrona punktu końcowego w usłudze Microsoft Defender** w tym artykule.

2. Aby znaleźć aplikacje wyzwalające najwięcej skanów, możesz użyć statystyk w czasie rzeczywistym zebranych przez usługę Defender for Endpoint w systemie Linux.

    > [!NOTE]
    > Ta funkcja jest dostępna w wersji 100.90.70 lub nowszej.

    Ta funkcja jest domyślnie włączona w kanałach `Dogfood` i `InsiderFast` . Jeśli używasz innego kanału aktualizacji, tę funkcję można włączyć z poziomu wiersza polecenia:

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    Ta funkcja wymaga włączenia ochrony w czasie rzeczywistym. Aby sprawdzić stan ochrony w czasie rzeczywistym, uruchom następujące polecenie:

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    Sprawdź, `real_time_protection_enabled` czy wpis to `true`. W przeciwnym razie uruchom następujące polecenie, aby go włączyć:

    ```bash
    mdatp config real-time-protection --value enabled
    ```

    ```Output
    Configuration property updated
    ```

    Aby zebrać bieżące statystyki, uruchom polecenie:

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > Użycie ```--output json``` (zwróć uwagę na podwójną kreskę) gwarantuje, że format danych wyjściowych jest gotowy do analizowania.

    W danych wyjściowych tego polecenia zostaną wyświetlone wszystkie procesy i skojarzone z nimi działania skanowania.

3. W systemie Linux pobierz przykładowy analizator języka Python **high_cpu_parser.py** przy użyciu polecenia:

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Dane wyjściowe tego polecenia powinny być podobne do następujących:


    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in 0s
    ```

4. Następnie wpisz następujące polecenia:

    ```bash
    chmod +x high_cpu_parser.py
    ```

    ```bash
    cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
    ```

      Dane wyjściowe powyższych elementów to lista najważniejszych współautorów problemów z wydajnością. Pierwsza kolumna to identyfikator procesu (PID), druga kolumna to nazwa procesu, a ostatnia kolumna to liczba zeskanowanych plików posortowanych według wpływu.
    Na przykład dane wyjściowe polecenia będą podobne do poniższych: 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool    1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd     407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    Aby zwiększyć wydajność usługi Defender for Endpoint w systemie Linux, znajdź usługę z największą liczbą w wierszu `Total files scanned` i dodaj dla niej wykluczenie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i weryfikowanie wykluczeń dla usługi Defender dla punktu końcowego w systemie Linux](linux-exclusions.md).

    > [!NOTE]
    > Aplikacja przechowuje statystyki w pamięci i śledzi tylko aktywność plików od momentu jej uruchomienia i włączono ochronę w czasie rzeczywistym. Procesy, które zostały uruchomione przed lub w okresach, w których ochrona w czasie rzeczywistym była wyłączona, nie są liczone. Ponadto są liczone tylko zdarzenia, które wyzwoliły skanowania.

5. Skonfiguruj Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux z wykluczeniami dla procesów lub lokalizacji dysków, które przyczyniają się do problemów z wydajnością i ponownie włącz ochronę w czasie rzeczywistym.

    Aby uzyskać więcej informacji, zobacz [Konfigurowanie i weryfikowanie wykluczeń usługi Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Rozwiązywanie problemów z wydajnością przy użyciu analizatora klienta Ochrona punktu końcowego w usłudze Microsoft Defender

**Dotyczy:**
- Problemy z wydajnością wszystkich dostępnych składników usługi Defender for Endpoint, takich jak AV i EDR  

Narzędzie Ochrona punktu końcowego w usłudze Microsoft Defender Client Analyzer (MDECA) może zbierać ślady, dzienniki i informacje diagnostyczne w celu rozwiązywania problemów z wydajnością [na dołączonych urządzeniach](/microsoft-365/security/defender-endpoint/onboard-configure) w systemie Linux.

> [!NOTE]
> Narzędzie Ochrona punktu końcowego w usłudze Microsoft Defender Client Analyzer jest regularnie używane przez usługi pomocy technicznej firmy Microsoft (CSS) do zbierania informacji, takich jak (ale nie tylko) adresy IP, nazwy komputerów, które pomogą rozwiązać problemy, z jakimi mogą wystąpić problemy Ochrona punktu końcowego w usłudze Microsoft Defender. Aby uzyskać więcej informacji na temat zasad zachowania poufności informacji, zobacz [Zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="requirements"></a>Wymagania

- Analizator klienta może działać w obsługiwanych dystrybucjach [systemu Linux](microsoft-defender-endpoint-linux.md#system-requirements) przed dołączeniem do Ochrona punktu końcowego w usłudze Microsoft Defender lub po jego dołączeniu.
- Pobierz analizator klienta dla systemu Linux z najnowszej wersji zapoznawczej dostępnej do pobrania tutaj: <https://aka.ms/XMDEClientAnalyzer>
- Jeśli urządzenie znajduje się za serwerem proxy, możesz po prostu przekazać serwer proxy jako zmienną środowiskową do skryptu mde_support_tool.sh. Przykład: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>Uruchamianie analizatora klienta w systemie Linux

Otwórz terminal lub protokół SSH na odpowiedniej maszynie i uruchom następujące polecenia:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. Uruchom polecenie jako użycie inne niż root, aby zainstalować wymagane narzędzia pip i lxml, które składniki: `./mde_support_tool.sh`
6. Aby zebrać rzeczywisty pakiet diagnostyczny i ponownie wygenerować plik archiwum wyników jako główny: `./mde_support_tool.sh -d` przykład:

   ![Obraz przedstawiający przykład wiersza polecenia.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - Analizator wymaga pliku "lxml", aby wygenerować dane wyjściowe wyniku. Jeśli nie jest zainstalowany, analizator spróbuje pobrać go z oficjalnego repozytorium dla pakietów języka Python poniżej: <https://pypi.org/search/?q=lxml>
> 
> - Ponadto narzędzie obecnie wymaga zainstalowania języka Python w wersji 3 lub nowszej.
>
> - Jeśli używasz maszyny, która nie może korzystać z języka Python 3 lub pobrać składnika lxml, możesz pobrać binarną wersję analizatora opartą na pliku binarnym, która nie ma żadnych wymagań: [Binarny analizator klienta XMDE](https://aka.ms/XMDEClientAnalyzerBinary)

### <a name="additional-syntax-help"></a>Dodatkowa pomoc dotycząca składni:

**-h** \# Pomoc<br>
\# Pokaż komunikat pomocy

**Wydajności** \# Wydajności<br>
\# Zbiera obszerne śledzenie w celu analizy problemu z wydajnością, który można odtworzyć na żądanie. Użyj `--length=<seconds>` polecenia , aby określić czas trwania testu porównawczego.

**-o** \# Wyjście<br>
\# Określanie ścieżki docelowej dla pliku wyników

**-nz** \# No-Zip<br>
\# Jeśli zostanie ustawiony, zostanie utworzony katalog zamiast wynikowego pliku archiwum

**-f** \# Życie<br>
\# Zastąp, jeśli dane wyjściowe już istnieją w ścieżce docelowej

### <a name="result-package-contents"></a>Zawartość pakietu wyników

- report.html

  Opis: główny plik wyjściowy HTML zawierający wyniki i wskazówki, które może wygenerować skrypt analizatora na maszynie.

- mde_diagnostic.zip

  Opis: Te same dane wyjściowe diagnostyki, które są generowane podczas uruchamiania *narzędzia mdatp diagnostic create* w [systemie Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Opis: dane wyjściowe XML generowane podczas uruchamiania i używane do kompilowania pliku raportu HTML.

- Processes_information.txt

  Opis: zawiera szczegółowe informacje o uruchomionych Ochrona punktu końcowego w usłudze Microsoft Defender powiązanych procesach w systemie.

- Log.txt

  Opis: zawiera te same komunikaty dziennika zapisane na ekranie podczas zbierania danych.

- Health.txt

  Opis: te same podstawowe dane wyjściowe kondycji, które są wyświetlane podczas uruchamiania polecenia *mdatp health* .

- Events.xml

  Opis: Dodatkowy plik XML używany przez analizator podczas tworzenia raportu HTML.

- Audited_info.txt

  Opis: szczegółowe informacje na temat inspekcji usługi i powiązanych składników systemu [operacyjnego Linux](/microsoft-365/security/defender-endpoint/linux-resources)

- perf_benchmark.tar.gz

  Opis: raporty testów wydajnościowych. Zobaczysz to tylko wtedy, gdy używasz parametru wydajności.

> [!NOTE]
> Jeśli po wykonaniu powyższych kroków problem z wydajnością będzie się powtarzać, skontaktuj się z pomocą techniczną, aby uzyskać dalsze instrukcje i środki zaradcze.



## <a name="see-also"></a>Zobacz też

- [Badaj problemy z kondycją agenta](health-status.md)
