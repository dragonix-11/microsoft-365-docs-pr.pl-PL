---
title: Zarządzanie plikami przy użyciu wiersza Program antywirusowy Microsoft Defender
description: Uruchom Program antywirusowy Microsoft Defender skanowania i skonfiguruj ochronę następnej generacji przy użyciu dedykowanego narzędzia wiersza polecenia.
keywords: uruchamianie skanowania w programie Windows Defender, uruchamianie skanowania antywirusowego z wiersza polecenia, uruchamianie skanowania w programie Windows Defender z wiersza polecenia, mpcmdrun, defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.date: 05/24/2021
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: f7ae9c9d0986463b6d6368edd0dac050600e3373
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2021
ms.locfileid: "62996817"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>Konfigurowanie ustawień Program antywirusowy Microsoft Defender zarządzanie nimi mpcmdrun.exe narzędziu wiersza polecenia

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W aplikacji można wykonywać różne funkcje Program antywirusowy Microsoft Defender za pomocą dedykowanego narzędzia wiersza **polecenia, którempcmdrun.exe**. To narzędzie jest przydatne, gdy chcesz zautomatyzować Program antywirusowy Microsoft Defender zadań. Narzędzie można znaleźć w programie `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Uruchom ją z wiersza polecenia.

> [!TIP]
> Może być konieczne otwarcie wersji wiersza polecenia na poziomie administratora. Podczas wyszukiwania wiersza **polecenia na** stronie menu Start wybierz **pozycję Uruchom jako administrator**. Jeśli używasz zaktualizowanej wersji platformy programu Microsoft Defender ochrony przed złośliwym kodem, uruchom program `MpCmdRun` z następującej lokalizacji: `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`. Aby uzyskać więcej informacji na temat platformy ochrony przed złośliwym oprogramowaniem, [zobacz Program antywirusowy Microsoft Defender i planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md).

Narzędzie MpCmdRun używa następującej składni:

```console
MpCmdRun.exe [command] [-options]
```

Oto przykład:

```console
MpCmdRun.exe -Scan -ScanType 2
```

W naszym przykładzie narzędzie MpCmdRun uruchamia pełne skanowanie antywirusowe na urządzeniu.

## <a name="commands"></a>Polecenia

|Polecenie|Opis|
|---|---|
|`-?` **lub** `-h`|Wyświetla wszystkie dostępne opcje narzędzia MpCmdRun|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|Skanuje w poszukiwaniu złośliwego oprogramowania. Wartości dla **typu ScanType** to:<p>**0** Domyślne, zgodnie z konfiguracją<p>**1** Szybkie skanowanie<p>**2 Pełne** skanowanie<p>**3 Skanowanie** niestandardowe plików i katalogów.<p>ProcesorThrottling działa zgodnie z konfiguracjami zasad|
|`-Trace [-Grouping #] [-Level #]`|Rozpoczyna śledzenie diagnostyczne|
|`-GetFiles [-SupportLogLocation <path>]`|Zbiera informacje o pomocy technicznej. Zobacz "[zbieranie danych diagnostycznych](collect-diagnostic-data.md)"|
|`-GetFilesDiagTrack`|Taki sam jak `-GetFiles`, ale dane wyjściowe do tymczasowego folderu DiagTrack|
|`-RemoveDefinitions [-All]`|Przywraca zainstalowaną analizę zabezpieczeń do poprzedniej kopii zapasowej lub do pierwotnego zestawu domyślnego.|
|`-RemoveDefinitions [-DynamicSignatures]`|Usuwa tylko dynamicznie pobraną analizę zabezpieczeń.|
|`-RemoveDefinitions [-Engine]`|Przywracanie poprzedniego zainstalowanego aparatu|
|`-SignatureUpdate [-UNC \|-MMPC]`|Sprawdzanie nowych aktualizacji analizy zabezpieczeń|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|Przywraca lub wyświetla elementy poddane kwarantannie.|
|`-AddDynamicSignature [-Path]`|Ładowanie dynamicznej analizy zabezpieczeń|
|`-ListAllDynamicSignatures`|Lista załadowanych dynamicznych analiz zabezpieczeń.|
|`-RemoveDynamicSignature [-SignatureSetID]`|Usuwa dynamiczną analizę zabezpieczeń|
|`-CheckExclusion -path <path>`|Sprawdza, czy ścieżka jest wykluczona.|
|`-ValidateMapsConnection`|Sprawdza, czy sieć może komunikować się z usługą Program antywirusowy Microsoft Defender w chmurze. To polecenie działa tylko w Windows 10 wersji 1703 lub wyższej.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>Typowe błędy podczas uruchamiania poleceń za pośrednictwem mpcmdrun.exe

W poniższej tabeli wymieniono typowe błędy, które mogą wystąpić podczas korzystania z narzędzia MpCmdRun.

|Komunikat o błędzie|Możliwa przyczyna|
|---|---|
|**Sprawdzanie poprawności połączeniaMapsConnection nie powiodło się (800106BA)** **lub 0x800106BA**|Usługa Program antywirusowy Microsoft Defender jest wyłączona. Włącz usługę i spróbuj ponownie. Jeśli potrzebujesz pomocy dotyczącej ponownego włączania Program antywirusowy Microsoft Defender, zobacz Ponowne [instalowanie/włączanie Program antywirusowy Microsoft Defender na punktach końcowych](switch-to-mde-phase-2.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).<p> **PORADA**: W Windows 10 1909 lub starszym oraz w Windows Server 2019 lub starszym usługa była wcześniej nazywana *Program antywirusowy Windows Defender*.|
|**0x80070667**|To polecenie jest uruchomione `-ValidateMapsConnection` na komputerze w wersji Windows 10 1607 lub starszej albo Windows Server 2016 starszej wersji. Uruchom polecenie z komputera, na Windows 10 wersji 1703 lub nowszej albo z Windows Server 2019 lub nowszego.|
|**Plik MpCmdRun nie jest rozpoznawany jako polecenie wewnętrzne ani zewnętrzne, nie można go uruchomić ani jako plik wsadowy.**|Narzędzie musi być uruchamiane z albo (`2012.4-0`tam, `%ProgramFiles%\Windows Defender` `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` gdzie może się różnić, ponieważ aktualizacje platformy są comiesięczne z wyjątkiem marca)|
|**Sprawdź poprawność połączeniaMapsConnection z mapami (hr=80070005 httpcode=450)**|Podjęto próbę użycia niewystarczających uprawnień. Użyj wiersza polecenia (cmd.exe) jako administrator.|
|**Sprawdź poprawność połączeniaMapsConnection z mapami (hr=80070006 httpcode=451)**|Zapora blokuje połączenie lub przeprowadza inspekcję SSL.|
|**Sprawdź poprawność połączeniaMapsConnection z mapami (hr=80004005 httpcode=450)**|Możliwe problemy związane z siecią, takie jak problemy z rozpoznawania nazw|
|**Sprawdzanie poprawności usługiMapsConnection nie powiodło się, aby nawiązać połączenie z usługą MAPY (hr=0x80508015**|Zapora blokuje połączenie lub przeprowadza inspekcję SSL.|
|**Sprawdzanie poprawności aplikacjiMapsConnection nie powiodło się nawiązanie połączenia z usługą MAPY (hr=800722F0D)**|Zapora blokuje połączenie lub przeprowadza inspekcję SSL.|
|**Sprawdź poprawność połączeniaMapsConnection z mapami (hr=80072EE7 httpcode=451)**|Zapora blokuje połączenie lub przeprowadza inspekcję SSL.|

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie Program antywirusowy Microsoft Defender funkcji](configure-microsoft-defender-antivirus-features.md)
- [Konfigurowanie i sprawdzanie poprawności Program antywirusowy Microsoft Defender połączeń sieciowych](configure-network-connections-microsoft-defender-antivirus.md)
- [Tematy referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
