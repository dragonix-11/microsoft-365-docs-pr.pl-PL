---
title: Rozwiązywanie problemów podczas przełączania się na Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się, jak rozwiązywać problemy podczas przełączania się na Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: migracja, usługa Windows Defender, zaawansowana ochrona punktu końcowego, oprogramowanie antywirusowe, ochrona przed złośliwym oprogramowaniem, tryb pasywny, tryb aktywny, rozwiązywanie problemów
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 8334ce03bac5b7d4518433f83ab34d5f86e71339
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634168"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Rozwiązywanie problemów podczas przełączania się na Ochrona punktu końcowego w usłudze Microsoft Defender

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ten artykuł zawiera informacje dotyczące rozwiązywania problemów dla administratorów zabezpieczeń, którzy mają problemy podczas przełączania rozwiązania ochrony punktu końcowego innych niż firma Microsoft na Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Program antywirusowy Microsoft Defender jest odinstalowywać na Windows Server

Po rozpoczęciu pracy z usługą Defender for Endpoint zaczniesz od ochrony przed oprogramowaniem antywirusowym/złośliwym firmy Microsoft w trybie aktywnym. W ramach procesu konfiguracji konfigurowane są ustawienia Program antywirusowy Microsoft Defender w trybie pasywnym. Czasami rozwiązanie inne niż firmy Microsoft w przypadku oprogramowania antywirusowego lub ochrony przed złośliwym oprogramowaniem może uniemożliwić Program antywirusowy Microsoft Defender na Windows Server. Wygląda na to, że Program antywirusowy Microsoft Defender usunięto z programu Windows Server.

Aby rozwiązać ten problem, zrób tak:

1. [Dodaj Ochrona punktu końcowego w usłudze Microsoft Defender do listy wykluczeń](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
2. [Ustaw Program antywirusowy Microsoft Defender tryb pasywny](#set-microsoft-defender-antivirus-to-passive-mode-manually) ręcznie.

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Dodawanie Ochrona punktu końcowego w usłudze Microsoft Defender do listy wykluczeń

Niektóre wykluczenia dla usługi Defender for Endpoint muszą być zdefiniowane w istniejącym rozwiązaniu ochrony punktu końcowego innym niż firma Microsoft. Pamiętaj o dodaniu następujących wykluczeń:

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>Ręczne ustawianie Program antywirusowy Microsoft Defender na tryb pasywny

Na Windows Server 2019, Windows Server, wersja 1803 lub nowsza, Windows Server 2016 lub Windows Server 2012 R2, musisz ręcznie ustawić tryb Program antywirusowy Microsoft Defender do trybu pasywnego. Ta akcja pomaga zapobiec problemom powodowany przez posiadanie wielu produktów antywirusowych zainstalowanych na serwerze. Możesz ustawić tryb Program antywirusowy Microsoft Defender pasywnego przy użyciu programu PowerShell, zasady grupy lub klucza rejestru.

Można ustawić tryb Program antywirusowy Microsoft Defender pasywnego, ustawiając następujący klucz rejestru:

Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

Nazwa: `ForceDefenderPassiveMode`

Typ: `REG_DWORD`

Wartość: `1`

> [!NOTE]
> Aby tryb pasywny działał na punktach końcowych z systemem Windows Server 2016 i Windows Server 2012 R2, te punkty końcowe muszą zostać uruchomione zgodnie z instrukcjami w te Windows sieci.[](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016)

Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender on Windows Server](microsoft-defender-antivirus-on-windows-server.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>Program antywirusowy Microsoft Defender wygląda na to, że zablokowano się w trybie pasywnym

Jeśli Program antywirusowy Microsoft Defender tryb pasywny, ustaw go ręcznie na tryb aktywny, korzystając z poniższych kroków:

1. Na tym Windows otwórz Edytor rejestru jako administrator.

2. Przejdź do `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

3. Ustaw lub **zdefiniuj wpis REG_DWORD** o nazwie `ForceDefenderPassiveMode`, a następnie ustaw jego wartość na `0`.

4. Uruchom ponownie urządzenie.

> [!IMPORTANT]
> Jeśli po zakończeniu tej procedury nadal masz problem z Program antywirusowy Microsoft Defender do trybu aktywnego, skontaktuj się [z pomocą techniczną](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>Mam problem z ponownym włączeniem funkcji Program antywirusowy Microsoft Defender na Windows Server 2016

Jeśli używasz na komputerze rozwiązania niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft, Windows Server 2016 istniejące rozwiązanie mogło wymagać wyłączenia lub odinstalowania Program antywirusowy Microsoft Defender firmy Microsoft. Możesz użyć narzędzia[ Malware Protection Command-Line Utility,](command-line-arguments-microsoft-defender-antivirus.md) aby ponownie włączyć Program antywirusowy Microsoft Defender na Windows Server 2016.

1. Jako administrator lokalny na serwerze otwórz wiersz polecenia.

2. Uruchom następujące polecenie: `MpCmdRun.exe -wdenable`

3. Uruchom urządzenie ponownie.

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md)

- [Narzędzia i metody dołączania do Windows w programie Defender for Endpoint](configure-endpoints.md) 
