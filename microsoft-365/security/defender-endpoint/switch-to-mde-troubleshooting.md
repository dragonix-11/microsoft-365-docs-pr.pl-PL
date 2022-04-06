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
ms.date: 03/28/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 30218ea9b3b5ecbec20fdbc3364546d25c80bcab
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507519"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Rozwiązywanie problemów podczas przełączania się na Ochrona punktu końcowego w usłudze Microsoft Defender

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ten artykuł zawiera informacje dotyczące rozwiązywania problemów dla administratorów zabezpieczeń, którzy mają problemy podczas przełączania rozwiązania ochrony punktu końcowego innych niż firma Microsoft na Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Program antywirusowy Microsoft Defender jest odinstalowywać na Windows Server

Po rozpoczęciu pracy z usługą Defender for Endpoint zaczniesz od ochrony przed oprogramowaniem antywirusowym/złośliwym firmy Microsoft w trybie aktywnym. W ramach procesu konfiguracji konfigurowane są ustawienia Program antywirusowy Microsoft Defender w trybie pasywnym. Czasami rozwiązanie inne niż firmy Microsoft w przypadku oprogramowania antywirusowego lub ochrony przed złośliwym oprogramowaniem może uniemożliwić Program antywirusowy Microsoft Defender na Windows Server. Wygląda na to, że Program antywirusowy Microsoft Defender usunięto z programu Windows Server.

Aby rozwiązać ten problem, zrób tak:

1. [Ustaw dla klucza rejestru DisableAntiSpyware wartość false](#set-the-disableantispyware-registry-key-to-false).
2. [Dodaj Ochrona punktu końcowego w usłudze Microsoft Defender do listy wykluczeń](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
3. [Ustaw Program antywirusowy Microsoft Defender tryb pasywny](#set-microsoft-defender-antivirus-to-passive-mode-manually) ręcznie.

### <a name="set-the-disableantispyware-registry-key-to-false"></a>Ustawianie dla klucza rejestru DisableAntiSpyware wartości false

W przeszłości klawisz rejestru [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) był używany do wyłączania programu Program antywirusowy Microsoft Defender i wdrażania innego produktu antywirusowego, takiego jak firma McAfee, Oprogramowania lub inne. **Ogólnie rzecz biorąc,** ten klucz rejestru nie powinien być ustawiony na urządzeniach Windows i punktach końcowych.  `DisableAntiSpyware` Jeśli jednak to zrobisz, oto jak ustawić wartość tego klucza na fałsz:

1. Na urządzeniu Windows Server otwórz Edytor rejestru.

2. Przejdź do `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. W tym folderze odszukaj wpis DWORD o **nazwie DisableAntiSpyware**.
   - Jeśli nie widzisz tego wpisu, wszystko jest już ustawione.
   - Jeśli zostanie wyświetlony temat **DisableAntiSpyware**, przejdź do kroku 4.

4. Kliknij prawym przyciskiem myszy wartość DisableAntiSpyware DWORD, a następnie wybierz pozycję **Modify (Modyfikuj**).

5. Ustaw wartość na `0`. Ta akcja ustawia wartość klucza rejestru na *fałsz*.

> [!TIP]
> Aby dowiedzieć się więcej o tym kluczu rejestru, zobacz [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

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
