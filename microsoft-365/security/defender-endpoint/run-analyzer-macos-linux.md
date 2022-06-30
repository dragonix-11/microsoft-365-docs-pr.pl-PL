---
title: Uruchom analizator klienta w systemie macOS lub Linux
description: Dowiedz się, jak uruchomić analizator klienta Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS lub Linux
keywords: client analyzer, troubleshoot sensor, analyzer, mdeanalyzer, macos, linux, mdeanalyzer
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
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: fc5944be9fd209898b53203533f568ae7ccec70e
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554538"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>Uruchamianie analizatora klienta w systemach macOS i Linux


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

## <a name="running-the-analyzer-through-gui-scenario"></a>Uruchamianie analizatora za pomocą interfejsu UŻYTKOWNIKA

1. Pobierz narzędzie [XMDE Client Analyzer](https://aka.ms/XMDEClientAnalyzer) na maszynę z systemem macOS lub Linux, którą należy zbadać.

   > [!NOTE]
   > Bieżący skrót SHA256 "XMDEClientAnalyzer.zip" pobrany z powyższego linku to: "94DBD785249C10F37D7BE9C1E881AA096CF3A99F30E829DBBFD42683717BC5DA8".

2. Wyodrębnij zawartość XMDEClientAnalyzer.zip na maszynie.

3. Otwórz sesję terminalu, zmień katalog na wyodrębniona lokalizacja i uruchom polecenie:

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > Jeśli w systemie Linux skrypt nie ma uprawnień do wykonania, należy najpierw uruchomić polecenie:
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Uruchamianie analizatora przy użyciu terminalu lub scenariusza SSH

Otwórz terminal lub protokół SSH na odpowiedniej maszynie i uruchom następujące polecenia:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. Uruchom polecenie jako użycie inne niż root, aby zainstalować wymagane narzędzia pip i lxml, które składniki: `./mde_support_tool.sh`

4. Aby zebrać rzeczywisty pakiet diagnostyczny i wygenerować plik archiwum wyników ponownie uruchom jako główny: `./mde_support_tool.sh -d`

> [!NOTE]
> - W przypadku systemu Linux analizator wymaga pliku "lxml", aby wygenerować dane wyjściowe wyniku. Jeśli nie jest zainstalowany, analizator spróbuje pobrać go z oficjalnego repozytorium dla pakietów języka Python poniżej: <https://pypi.org/search/?q=lxml>
> 
> - Ponadto narzędzie obecnie wymaga zainstalowania języka Python w wersji 3 lub nowszej.
>
> - Jeśli używasz maszyny, która nie może korzystać z języka Python 3 lub pobrać składnika lxml, możesz pobrać binarną wersję analizatora opartą na pliku binarnym, która nie ma żadnych wymagań: [Binarny analizator klienta XMDE](https://aka.ms/XMDEClientAnalyzerBinary)
>
> - Jeśli urządzenie znajduje się za serwerem proxy, możesz po prostu przekazać serwer proxy jako zmienną środowiskową do skryptu mde_support_tool.sh. Przykład: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

Przykład:

:::image type="content" source="images/4ca188f6c457e335abe3c9ad3eddda26.png" alt-text="Przykład wiersza polecenia" lightbox="images/4ca188f6c457e335abe3c9ad3eddda26.png":::

Dodatkowa pomoc dotycząca składni:

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

## <a name="result-package-contents-on-macos-and-linux"></a>Zawartość pakietu wyników w systemach macOS i Linux

- report.html

  Opis: główny plik wyjściowy HTML zawierający wyniki i wskazówki, które może wygenerować skrypt analizatora na maszynie.

- mde_diagnostic.zip

  Opis: Te same dane wyjściowe diagnostyki, które są generowane podczas uruchamiania *narzędzia mdatp diagnostic create* w systemie [macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  lub

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

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
