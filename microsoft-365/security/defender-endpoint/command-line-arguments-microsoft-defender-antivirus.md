---
title: Zarządzanie Program antywirusowy Microsoft Defender za pomocą wiersza polecenia
description: Uruchom Program antywirusowy Microsoft Defender skanuje i skonfiguruj ochronę nowej generacji za pomocą dedykowanego narzędzia wiersza polecenia.
keywords: uruchamianie skanowania usługi Windows Defender, uruchamianie skanowania antywirusowego z poziomu wiersza polecenia, uruchamianie skanowania usługi Windows Defender z poziomu wiersza polecenia, mpcmdrun, defender
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
ms.openlocfilehash: d459c87f7d996d70d37e84f4e21bc261c720b443
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418681"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>Konfigurowanie Program antywirusowy Microsoft Defender i zarządzanie nimi za pomocą narzędzia wiersza polecenia mpcmdrun.exe

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender 

**Platformy**
- System Windows

Różne funkcje można wykonywać w Program antywirusowy Microsoft Defender przy użyciu dedykowanego narzędzia wiersza polecenia **mpcmdrun.exe**. To narzędzie jest przydatne, gdy chcesz zautomatyzować zadania Program antywirusowy Microsoft Defender. Narzędzie można znaleźć w pliku `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Uruchom go w wierszu polecenia.

> [!TIP]
> Może być konieczne otwarcie wersji wiersza polecenia na poziomie administratora. Podczas wyszukiwania **wiersza polecenia** w menu Start wybierz pozycję **Uruchom jako administrator**. Jeśli używasz zaktualizowanej wersji platformy ochrony przed złośliwym kodem w usłudze Microsoft Defender, uruchom polecenie `MpCmdRun` z następującej lokalizacji: `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`. Aby uzyskać więcej informacji na temat platformy ochrony przed złośliwym kodem, zobacz [Program antywirusowy Microsoft Defender aktualizacje i linie bazowe](manage-updates-baselines-microsoft-defender-antivirus.md).

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

|Polecenia|Opis|
|---|---|
|`-?`**Lub** `-h`|Wyświetla wszystkie dostępne opcje dla narzędzia MpCmdRun|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|Skanuje pod kątem złośliwego oprogramowania. Wartości **parametru ScanType** to:<p>**0** Wartość domyślna zgodnie z konfiguracją<p>**1** Szybkie skanowanie<p>**2** Pełne skanowanie<p>**3** Skanowanie niestandardowe plików i katalogów.<p>CpuThrottling działa zgodnie z konfiguracjami zasad|
|`-Trace [-Grouping #] [-Level #]`|Rozpoczyna śledzenie diagnostyczne|
|`-GetFiles [-SupportLogLocation <path>]`|Zbiera informacje o pomocy technicznej. Zobacz "[Zbieranie danych diagnostycznych](collect-diagnostic-data.md)"|
|`-GetFilesDiagTrack`|Tak samo jak `-GetFiles`, ale dane wyjściowe do tymczasowego folderu DiagTrack|
|`-RemoveDefinitions [-All]`|Przywraca zainstalowaną analizę zabezpieczeń do poprzedniej kopii zapasowej lub oryginalnego zestawu domyślnego|
|`-RemoveDefinitions [-DynamicSignatures]`|Usuwa tylko dynamicznie pobraną analizę zabezpieczeń|
|`-RemoveDefinitions [-Engine]`|Przywraca poprzedni zainstalowany aparat|
|`-SignatureUpdate [-UNC \|-MMPC]`|Sprawdzanie pod kątem nowych aktualizacji analizy zabezpieczeń|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|Przywraca lub wyświetla listy elementów poddanych kwarantannie|
|`-AddDynamicSignature [-Path]`|Ładuje dynamiczną analizę zabezpieczeń|
|`-ListAllDynamicSignatures`|Wyświetla listę załadowanych dynamicznych analiz zabezpieczeń|
|`-RemoveDynamicSignature [-SignatureSetID]`|Usuwa dynamiczną analizę zabezpieczeń|
|`-CheckExclusion -path <path>`|Sprawdza, czy ścieżka jest wykluczona|
|`-ValidateMapsConnection`|Sprawdza, czy sieć może komunikować się z usługą w chmurze Program antywirusowy Microsoft Defender. To polecenie będzie działać tylko w Windows 10 w wersji 1703 lub nowszej.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>Typowe błędy podczas uruchamiania poleceń za pośrednictwem mpcmdrun.exe

W poniższej tabeli wymieniono typowe błędy, które mogą wystąpić podczas korzystania z narzędzia MpCmdRun.

|Komunikat o błędzie|Możliwa przyczyna|
|---|---|
|**Niepowodzenie validateMapsConnection (800106BA)** lub **0x800106BA**|Usługa Program antywirusowy Microsoft Defender jest wyłączona. Włącz usługę i spróbuj ponownie. Jeśli potrzebujesz pomocy przy ponownym włączeniu Program antywirusowy Microsoft Defender, zobacz [Ponowne instalowanie/włączanie Program antywirusowy Microsoft Defender w punktach końcowych](switch-to-mde-phase-2.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).<p> **PORADA**: W Windows 10 1909 lub starszym i Windows Server 2019 lub starszym usługa była wcześniej nazywana *Program antywirusowy Windows Defender*.|
|**0x80070667**|Uruchamiasz `-ValidateMapsConnection` polecenie z komputera, który jest Windows 10 wersji 1607 lub starszej lub Windows Server 2016 lub starszej. Uruchom polecenie z maszyny Windows 10 wersji 1703 lub nowszej albo Windows Server 2019 lub nowszej.|
|**MpCmdRun nie jest rozpoznawany jako wewnętrzne lub zewnętrzne polecenie, program operacyjny lub plik wsadowy.**|Narzędzie musi być uruchamiane z poziomu lub `%ProgramFiles%\Windows Defender` `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` (gdzie `2012.4-0` mogą się różnić, ponieważ aktualizacje platformy są co miesiąc z wyjątkiem marca)|
|**ValidateMapsConnection nie może nawiązać połączenia z usługą MAPS (hr=80070005 httpcode=450)**|Próbowano użyć polecenia z niewystarczającymi uprawnieniami. Użyj wiersza polecenia (cmd.exe) jako administrator.|
|**ValidateMapsConnection nie może nawiązać połączenia z usługą MAPS (hr=80070006 httpcode=451)**|Zapora blokuje połączenie lub przeprowadza inspekcję protokołu SSL.|
|**ValidateMapsConnection nie może nawiązać połączenia z usługą MAPS (hr=80004005 httpcode=450)**|Możliwe problemy związane z siecią, takie jak problemy z rozpoznawaniem nazw|
|**ValidateMapsConnection nie może nawiązać połączenia z usługą MAPS (hr=0x80508015**|Zapora blokuje połączenie lub przeprowadza inspekcję protokołu SSL.|
|**ValidateMapsConnection nie może nawiązać połączenia z usługą MAPS (hr=800722F0D)**|Zapora blokuje połączenie lub przeprowadza inspekcję protokołu SSL.|
|**ValidateMapsConnection nie może nawiązać połączenia z usługą MAPS (hr=80072EE7 httpcode=451)**|Zapora blokuje połączenie lub przeprowadza inspekcję protokołu SSL.|

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Konfiguruj funkcje programu antywirusowego Microsoft Defender](configure-microsoft-defender-antivirus-features.md)
- [Skonfiguruj i zweryfikuj połączenia sieciowe programu antywirusowego Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)
- [Tematy referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
