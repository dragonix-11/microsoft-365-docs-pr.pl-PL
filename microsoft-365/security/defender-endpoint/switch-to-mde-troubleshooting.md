---
title: Rozwiązywanie problemów podczas przełączania do Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się, jak rozwiązywać problemy podczas przełączania do Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: migration, windows defender, advanced endpoint protection, antivirus, antimalware, passive mode, active mode, troubleshooting
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
ms.date: 05/20/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 9a1a95c927c4f659510c587d2bbc81ad4b9c1264
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621634"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Rozwiązywanie problemów podczas przełączania do Ochrona punktu końcowego w usłudze Microsoft Defender

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ten artykuł zawiera informacje dotyczące rozwiązywania problemów dla administratorów zabezpieczeń, którzy napotykają problemy podczas przełączania się z rozwiązania ochrony punktów końcowych firmy innej niż Microsoft na Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Program antywirusowy Microsoft Defender jest odinstalowywany na serwerze Windows

Po przełączeniu do usługi Defender for Endpoint rozpoczynasz od ochrony przed oprogramowaniem antywirusowym/ochroną przed złośliwym kodem firmy Microsoft w trybie aktywnym. W ramach procesu konfiguracji skonfigurujesz Program antywirusowy Microsoft Defender w trybie pasywnym. Czasami oprogramowanie antywirusowe/chroniące przed złośliwym kodem firmy innej niż Microsoft może uniemożliwiać uruchamianie Program antywirusowy Microsoft Defender na serwerze Windows. W rzeczywistości może to wyglądać tak, jakby Program antywirusowy Microsoft Defender została usunięta z serwera Windows.

Aby rozwiązać ten problem, wykonaj następujące kroki:

1. [Dodaj Ochrona punktu końcowego w usłudze Microsoft Defender do listy wykluczeń](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
2. [Ręcznie ustaw Program antywirusowy Microsoft Defender na tryb pasywny](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Dodawanie Ochrona punktu końcowego w usłudze Microsoft Defender do listy wykluczeń

Niektóre wykluczenia dla usługi Defender for Endpoint muszą być zdefiniowane w istniejącym rozwiązaniu ochrony punktów końcowych innych niż Microsoft. Pamiętaj o dodaniu następujących wykluczeń:

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>Ręczne ustawianie trybu pasywnego Program antywirusowy Microsoft Defender

Na serwerze Windows Server 2019, Windows Server w wersji 1803 lub nowszej, Windows Server 2016 lub Windows Server 2012 R2 należy ręcznie ustawić tryb pasywny Program antywirusowy Microsoft Defender. Ta akcja pomaga zapobiegać problemom spowodowanym przez zainstalowanie wielu produktów antywirusowych na serwerze. Możesz ustawić Program antywirusowy Microsoft Defender na tryb pasywny przy użyciu programu PowerShell, zasady grupy lub klucza rejestru.

Możesz ustawić Program antywirusowy Microsoft Defender na tryb pasywny, ustawiając następujący klucz rejestru:

Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

Nazwa: `ForceDefenderPassiveMode`

Typu: `REG_DWORD`

Wartość: `1`

> [!NOTE]
> Aby tryb pasywny działał w punktach końcowych z uruchomionymi Windows Server 2016 i Windows Server 2012 R2, te punkty końcowe muszą zostać dołączone przy użyciu instrukcji w temacie [Dołączanie serwerów Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

Aby uzyskać więcej informacji, zobacz [Program antywirusowy Microsoft Defender w Windows](microsoft-defender-antivirus-windows.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>Program antywirusowy Microsoft Defender wydaje się być zablokowany w trybie pasywnym

Jeśli Program antywirusowy Microsoft Defender jest zablokowany w trybie pasywnym, ustaw go na tryb aktywny ręcznie, wykonując następujące kroki:

1. Na urządzeniu Windows otwórz Edytor rejestru jako administrator.

2. Przejdź do `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

3. Ustaw lub zdefiniuj wpis **REG_DWORD** o nazwie `ForceDefenderPassiveMode`i ustaw jego wartość na `0`.

4. Uruchom ponownie urządzenie.

> [!IMPORTANT]
> Jeśli po wykonaniu tej procedury nadal występują problemy z ustawieniem Program antywirusowy Microsoft Defender trybu aktywnego, [skontaktuj się z pomocą techniczną](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>Mam problem z ponownym włączeniem Program antywirusowy Microsoft Defender na Windows Server 2016

Jeśli używasz rozwiązania antywirusowego/chroniącego przed złośliwym kodem firmy innej niż Microsoft w Windows Server 2016, istniejące rozwiązanie może wymagać wyłączenia lub odinstalowania Program antywirusowy Microsoft Defender. Za pomocą[ narzędzia Command-Line ochrony przed złośliwym oprogramowaniem](command-line-arguments-microsoft-defender-antivirus.md) można ponownie włączyć Program antywirusowy Microsoft Defender na Windows Server 2016.

1. Jako administrator lokalny na serwerze otwórz wiersz polecenia.

2. Uruchom następujące polecenie: `MpCmdRun.exe -wdenable`

3. Uruchom urządzenie ponownie.

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md)

- [Narzędzia i metody dołączania dla urządzeń Windows w usłudze Defender for Endpoint](configure-endpoints.md) 
