---
title: Rozwiązywanie problemów z wydajnością programu Microsoft Defender dla punktu końcowego w systemie Linux
description: Rozwiązywanie problemów z wydajnością programu Microsoft Defender dla punktu końcowego w systemie Linux.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, performance
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
ms.openlocfilehash: 14424f0cdff908fc641d6de1c22d25546473cc13
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011373"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Rozwiązywanie problemów z wydajnością programu Microsoft Defender dla punktu końcowego w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Ten dokument zawiera instrukcje dotyczące ograniczania problemów z wydajnością związanych z programem Defender for Endpoint dla systemu Linux przy użyciu dostępnych narzędzi diagnostycznych w celu zrozumienia i ograniczenia istniejących niedoborów zasobów i procesów, które czynią system w takich sytuacjach. Problemy z wydajnością są spowodowane głównie wąskimi gardłami w co najmniej jednym podsystemie sprzętowym, w zależności od profilu użycia zasobów w systemie. Czasami aplikacje są poufne na dyskowe zasoby we/Wy i mogą wymagać większej pojemności procesora, a czasem niektóre konfiguracje nie są u nasadzeni i mogą wyzwalać zbyt wiele nowych procesów oraz otwierać zbyt wiele deskryptorów plików.

W zależności od uruchomionej aplikacji i charakterystyki urządzenia, uruchamianie programu Defender for Endpoint w systemie Linux może mieć suboptimalną wydajność. W szczególności aplikacje lub procesy systemowe, które przez krótki czas mają dostęp do wielu zasobów, takich jak procesor, dysk i pamięć, mogą powodować problemy z wydajnością w programie Defender for Endpoint w systemie Linux.

> [!WARNING]
> Przed rozpoczęciem **upewnij się, że na urządzeniu nie są obecnie uruchomione inne produkty zabezpieczające**. Mogą wystąpić konflikty wielu produktów zabezpieczeń i wpłynąć na wydajność hosta.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Rozwiązywanie problemów z wydajnością przy użyciu statystyki ochrony w czasie rzeczywistym

**Dotyczy:**
- Tylko problemy z wydajnością związane z audio/wideo

Ochrona w czasie rzeczywistym (RTP) to funkcja usługi Defender for Endpoint dla systemu Linux, która nieustannie monitoruje i chroni Twoje urządzenie przed zagrożeniami. Obejmuje on monitorowanie plików i procesów oraz inne heuristics.

Aby rozwiązać te problemy i zminimalizować te problemy, można wykonać następujące czynności:

1. Wyłącz ochronę w czasie rzeczywistym przy użyciu jednej z następujących metod i sprawdź, czy wydajność nie poprawia się. Takie podejście pomaga zawęzić zakres udziału programu Defender dla punktu końcowego w systemie Linux w przypadku problemów z wydajnością.

    Jeśli Twoje urządzenie nie jest zarządzane przez Twoją organizację, ochronę w czasie rzeczywistym można wyłączyć z poziomu wiersza polecenia:

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    Jeśli Twoje urządzenie jest zarządzane przez Twoją organizację, administrator może wyłączyć ochronę w czasie rzeczywistym, korzystając z instrukcji z tematu Ustawianie preferencji dla programu [Defender dla punktu końcowego w systemie Linux](linux-preferences.md).

    > [!NOTE]
    > Jeśli problem z wydajnością będzie nadal występował, gdy ochrona w czasie rzeczywistym jest wyłączona, źródłem problemu może być składnik wykrywanie i reagowanie w punktach końcowych (EDR). W takim przypadku wykonaj czynności opisane w sekcji Rozwiązywanie problemów z wydajnością przy użyciu programu **Microsoft Defender for Endpoint Client Analyzer** tego artykułu.

2. Aby znaleźć aplikacje wyzwalające większość skanów, możesz użyć statystyk czasu rzeczywistego zebranych z programu Defender for Endpoint w systemie Linux.

    > [!NOTE]
    > Ta funkcja jest dostępna w wersji 100.90.70 lub nowszej.

    Ta funkcja jest domyślnie włączona w kanałach `Dogfood` i w kanałach `InsiderFast` . Jeśli korzystasz z innego kanału aktualizacji, tę funkcję można włączyć z wiersza polecenia:

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    Ta funkcja wymaga włączonej ochrony w czasie rzeczywistym. Aby sprawdzić stan ochrony w czasie rzeczywistym, uruchom następujące polecenie:

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    Sprawdź, czy wpis `real_time_protection_enabled` jest .`true` W przeciwnym razie uruchom następujące polecenie, aby je włączyć:

    ```bash
    mdatp config real-time-protection --value enabled
    ```

    ```Output
    Configuration property updated
    ```

    Aby zbierać bieżące statystyki, uruchom:

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > Użycie ```--output json``` podwójnej kreski (zanotuj podwójną kreskę) gwarantuje, że format wyjściowy jest gotowy do analizy.

    Wynik tego polecenia spowoduje pokazanie wszystkich procesów i ich skojarzonej aktywności skanowania.

3. Na komputerze z systemem Linux pobierz przykładowy parser **w języku Python high_cpu_parser.py** za pomocą tego polecenia:

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Wyniki tego polecenia powinny przypominać następujące:


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

      Powyższe dane wyjściowe to lista osób, które są najbardziej współautorami problemów z wydajnością. Pierwsza kolumna zawiera identyfikator procesu (PID), druga — nazwę procesu, a ostatnia — liczbę zeskanowanych plików, posortowaną według wpływu.
    Wynik polecenia będzie na przykład podobny do poniższego: 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool     1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd    407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    Aby poprawić wydajność programu Defender for Endpoint w systemie Linux, `Total files scanned` odszukaj program z największą liczbą pod wierszem i dodaj dla niego wykluczenie. Aby uzyskać więcej informacji, zobacz Konfigurowanie i weryfikowanie wykluczeń dla [programu Defender dla punktu końcowego w systemie Linux](linux-exclusions.md).

    > [!NOTE]
    > Aplikacja przechowuje statystyki w pamięci i śledzi tylko aktywność plików od jej rozpoczęcia i została włączona ochrona w czasie rzeczywistym. Nie są liczone procesy uruchomione przed lub podczas okresów, w których ochrona w czasie rzeczywistym była wyłączona. Ponadto zliczane są tylko zdarzenia, które wyzwoliły skany.

5. Skonfiguruj usługę Microsoft Defender dla punktu końcowego w systemie Linux z wykluczeniami dla procesów lub lokalizacji dysków, które współtwoarzą problemy z wydajnością, i ponownie włącz ochronę w czasie rzeczywistym.

    Aby uzyskać więcej informacji, zobacz [Konfigurowanie i weryfikowanie wykluczeń usługi Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Rozwiązywanie problemów z wydajnością przy użyciu programu Microsoft Defender for Endpoint Client Analyzer

**Dotyczy:**
- Problemy z wydajnością wszystkich dostępnych składników programu Defender dla punktów końcowych, takich jak audio/wideo i EDR  

Program Microsoft Defender for Endpoint Client Analyzer (MDECA) może zbierać wyniki śledzenia, dzienniki i informacje diagnostyczne w celu rozwiązywania problemów z wydajnością na urządzeniach [onboarded](/microsoft-365/security/defender-endpoint/onboard-configure) na systemie Linux.

> [!NOTE]
> Narzędzie Microsoft Defender for Endpoint Client Analyzer jest regularnie używane przez usługi obsługi klienta firmy Microsoft (CSS) do zbierania takich informacji jak adresy IP (ale nie tylko) nazwy komputerów, które ułatwiają rozwiązywanie problemów, które mogą wystąpić w programie Microsoft Defender for Endpoint. Aby uzyskać więcej informacji na temat zasad zachowania poufności informacji, zobacz [Oświadczenie o ochronie prywatności firmy Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="requirements"></a>Wymagania

- Analizator klienta może być uruchamiany na obsługiwanych distronach systemu [Linux](microsoft-defender-endpoint-linux.md#system-requirements) przed lub po dojrzeniu do programu Microsoft Defender for Endpoint.
- Pobierz analizator klienta dla systemu Linux z najnowszej wersji Preview dostępnej do pobrania tutaj: <https://aka.ms/XMDEClientAnalyzer>
- Jeśli urządzenie znajduje się za serwerem proxy, możesz po prostu przekazać ten serwer jako zmienną środowiskową do skryptu mde_support_tool.sh. Na przykład: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>Uruchamianie analizatora klienta w systemie Linux

Otwórz terminal lub SSH na odpowiednim komputerze i uruchom następujące polecenia:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. Uruchom jako niebędące głównym zastosowaniem do instalacji wymaganych składników pip i lxml, które: `./mde_support_tool.sh`
6. Aby zebrać rzeczywisty pakiet diagnostyczny i wygenerować plik archiwum wyników, uruchom ponownie jako plik główny: `./mde_support_tool.sh -d` Przykład:

   ![Obraz przykładowego wiersza polecenia.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - Analizator wymaga użycia lxml do uzyskania wyniku. Jeśli nie zainstalowano, analizator spróbuje pobrać go z oficjalnego repozytorium dla pakietów w języku Python poniżej: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - Ponadto obecnie wymaga zainstalowania tego narzędzia w języku Python w wersji 3 lub nowszej.
>
> - Jeśli korzystasz z komputera, który nie może korzystać z języka Python 3 lub pobierać składnika lxml, możesz pobrać wersję binarną analizatora, który nie ma żadnych wymagań: [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary)

### <a name="additional-syntax-help"></a>Dodatkowa pomoc w składni:

**— h** \# Pomoc<br>
\# Pokaż komunikat pomocy

**wydajność** \# Wydajność<br>
\# Zbiera obszerne śledzenie na potrzeby analizy problemu z wydajnością, które można odtworzyć na żądanie. Umożliwia `--length=<seconds>` określenie czasu trwania wskaźnika odniesienia.

**— o** \# Dane wyjściowe<br>
\# Określanie ścieżki docelowej pliku wyników

**-nz** \# No-Zip<br>
\# W przypadku ustawienia zamiast wynikowego pliku archiwum zostanie utworzony katalog

**— f** \# Wymuszanie<br>
\# Zastąp, jeśli dane wyjściowe już istnieją w ścieżce docelowej

### <a name="result-package-contents"></a>Zawartość pakietu wyników

- report.html

  Opis: Główny plik wyjściowy HTML, który będzie zawierał ustalenia i wskazówki, które skrypt analizatora może uruchomić na komputerze.

- mde_diagnostic.zip

  Opis: Te same dane wyjściowe diagnostyczne, które są generowane podczas uruchamiania narzędzia *diagnostycznego MDATP, utwórz w* systemie [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Opis: Dane wyjściowe XML generowane podczas uruchamiania i używane do tworzenia pliku raportu HTML.

- Processes_information.txt

  Opis: zawiera szczegóły uruchomionych procesów związanych z programem Microsoft Defender for Endpoint w systemie.

- Log.txt

  Opis: zawiera te same wiadomości dziennika, które są zapisywane na ekranie podczas zbierania danych.

- Health.txt

  Opis: Takie same podstawowe dane wyjściowe kondycji, które są wyświetlane po uruchomieniu polecenia *Kondycja MDATP* .

- Events.xml

  Opis: Dodatkowy plik XML używany przez analizatora podczas tworzenia raportu HTML.

- Auditd_info.txt

  Opis: szczegóły dotyczące usługi inspekcji i pokrewnych składników dla [systemu operacyjnego Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events)

- perf_benchmark.tar.gz

  Opis: Raporty testów wydajności. Zobaczysz to tylko wtedy, gdy używasz parametru wydajności.

> [!NOTE]
> W przypadku, gdy po zakończeniu powyższych czynności problem z wydajnością będzie nadal występował, skontaktuj się z działem obsługi klienta, aby uzyskać dalsze instrukcje i środki zaradcze.



## <a name="see-also"></a>Zobacz też

- [Badanie problemów dotyczących kondycji agenta](health-status.md)
