---
title: Rozwiązywanie problemów podczas przełączania do programu Microsoft Defender dla punktu końcowego
description: Dowiedz się, jak rozwiązywać problemy podczas przełączania się do programu Microsoft Defender for Endpoint.
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
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 01/11/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 6729d136da90c674c0d726f2bfe7321a75bdb79a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028095"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Rozwiązywanie problemów podczas przełączania do programu Microsoft Defender dla punktu końcowego

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ten artykuł zawiera informacje dotyczące rozwiązywania problemów dla administratorów zabezpieczeń, którzy mają problemy podczas przełączania rozwiązania ochrony punktu końcowego innych niż firma Microsoft na program Microsoft Defender for Endpoint.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Program antywirusowy Microsoft Defender jest odinstalowywać na Windows Server

Po rozpoczęciu pracy z usługą Defender for Endpoint zaczniesz od ochrony przed oprogramowaniem antywirusowym/złośliwym firmy Microsoft w trybie aktywnym. W ramach procesu konfiguracji konfigurowane są ustawienia Program antywirusowy Microsoft Defender w trybie pasywnym. Czasami rozwiązanie inne niż firmy Microsoft w przypadku oprogramowania antywirusowego lub ochrony przed złośliwym oprogramowaniem może uniemożliwić Program antywirusowy Microsoft Defender na Windows Server. Wygląda na to, że Program antywirusowy Microsoft Defender usunięto z programu Windows Server.

Aby rozwiązać ten problem, zrób tak:

1. [Ustaw dla klucza rejestru DisableAntiSpyware wartość false](#set-the-disableantispyware-registry-key-to-false).
2. [Dodaj usługę Microsoft Defender for Endpoint do listy wykluczeń](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
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

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Dodawanie programu Microsoft Defender for Endpoint do listy wykluczeń

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

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>Mam problem z ponownym włączeniem funkcji Program antywirusowy Microsoft Defender na Windows Server 2016

Jeśli używasz na komputerze rozwiązania niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft, Windows Server 2016 istniejące rozwiązanie mogło wymagać wyłączenia lub odinstalowania Program antywirusowy Microsoft Defender firmy Microsoft. Możesz użyć narzędzia[ Malware Protection Command-Line Utility,](command-line-arguments-microsoft-defender-antivirus.md) aby ponownie włączyć Program antywirusowy Microsoft Defender na Windows Server 2016.

1. Jako administrator lokalny na serwerze otwórz wiersz polecenia.

2. Uruchom następujące polecenie: `MpCmdRun.exe -wdenable`

3. Uruchom urządzenie ponownie.

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md)

- [Narzędzia i metody dołączania do Windows w programie Defender for Endpoint](configure-endpoints.md) 
