---
title: Uruchamianie analizatora klienta w systemie macOS lub Linux
description: Dowiedz się, jak uruchomić program Microsoft Defender for Endpoint Client Analyzer w systemie macOS lub Linux
keywords: analizator klienta, czujnik rozwiązywania problemów, analizator, mdeanalyzer, macos, linux, mdeanalyzer
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
ms.openlocfilehash: bbd4100466fbfef75363848bc5b89bbb9a769265
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401080"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>Uruchamianie analizatora klienta w systemach macOS i Linux


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>Uruchamianie analizatora przy użyciu scenariusza graficznego interfejsu użytkownika

1. Pobierz narzędzie [analizatora klienta XMDE](https://aka.ms/XMDEClientAnalyzer) na komputer macOS lub Linux, który chcesz zbadać.

   > [!NOTE]
   > Bieżący skrót SHA256 "XMDEClientAnalyzer.zip" pobrany z powyższego linku jest taki: 'B95E2E21D5A93E0AC88BA401ACB20E5F721727B409D4186147C8D17468185583'.

2. Wyodrębnianie zawartości XMDEClientAnalyzer.zip na komputerze.

3. Otwórz sesję terminalową, zmień katalog na wyodrębnione miejsce i uruchom:

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > W systemie Linux, jeśli skrypt nie ma uprawnień do wykonywania, należy najpierw uruchomić polecenie:
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Uruchamianie analizatora przy użyciu scenariusza terminalu lub SSH

Otwórz terminal lub SSH na odpowiednim komputerze i uruchom następujące polecenia:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. Uruchom jako niebędące głównym zastosowaniem do instalacji wymaganych składników pip i lxml, które: `./mde_support_tool.sh`

4. Aby zebrać rzeczywisty pakiet diagnostyczny i wygenerować ponownie uruchomienie pliku archiwum wyników jako katalogu głównego: `./mde_support_tool.sh -d`

> [!NOTE]
> - W przypadku systemu Linux analizator wymaga ,,lxml' do uzyskania wyniku. Jeśli nie zainstalowano, analizator spróbuje pobrać go z oficjalnego repozytorium dla pakietów w języku Python poniżej: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - Ponadto obecnie wymaga zainstalowania tego narzędzia w języku Python w wersji 3 lub nowszej.
>
> - Jeśli korzystasz z komputera, który nie może korzystać z języka Python 3 lub pobierać składnika lxml, możesz pobrać wersję binarną analizatora, który nie ma żadnych wymagań: [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary)
>
> - Jeśli urządzenie znajduje się za serwerem proxy, możesz po prostu przekazać ten serwer jako zmienną środowiskową do skryptu mde_support_tool.sh. Na przykład: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

Przykład:

![Obraz przykładowego wiersza polecenia.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

Dodatkowa pomoc w składni:

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

## <a name="result-package-contents-on-macos-and-linux"></a>Zawartość pakietu wyników w systemach macOS i Linux

- report.html

  Opis: Główny plik wyjściowy HTML, który będzie zawierał ustalenia i wskazówki, które skrypt analizatora może uruchomić na komputerze.

- mde_diagnostic.zip

  Opis: Te same dane wyjściowe diagnostyczne, które są generowane podczas uruchamiania narzędzia *diagnostycznego MDATP, utwórz w* [obu systemach macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  lub

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

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
