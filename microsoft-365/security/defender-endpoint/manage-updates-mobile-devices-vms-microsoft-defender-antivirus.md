---
title: Definiowanie sposobu aktualizowania urządzeń przenośnych przez Program antywirusowy Microsoft Defender
description: Zarządzanie sposobem aktualizowania urządzeń przenośnych, takich jak laptopy, za pomocą Program antywirusowy Microsoft Defender aktualizacji ochrony.
keywords: updates, protection, schedule updates, battery, mobile device, laptop, notebook, opt-in, microsoft update, wsus, override
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: f582e33f2d77c8560b773b79d54026e38bcde8c9
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790377"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Urządzenia przenośne i maszyny wirtualne mogą wymagać większej konfiguracji, aby zapewnić, że aktualizacje nie będą miały wpływu na wydajność.

Istnieją dwa ustawienia, które są przydatne dla tych urządzeń:

- Zgoda na usługę Microsoft Update na komputerach przenośnych bez połączenia ZUS
- Zapobieganie aktualizacjom analizy zabezpieczeń podczas pracy z zasilaniem bateryjnym

Następujące artykuły mogą być również przydatne w takich sytuacjach:
- [Konfigurowanie zaplanowanych i uzupełniających skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są nieaktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Przewodnik wdrożenia programu antywirusowego Microsoft Defender w środowisku infrastruktury pulpitu wirtualnego](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>Zgoda na usługę Microsoft Update na komputerach przenośnych bez połączenia ZUS

Usługa Microsoft Update umożliwia aktualizowanie analizy zabezpieczeń na urządzeniach przenośnych działających Program antywirusowy Microsoft Defender, gdy nie są one połączone z siecią firmową lub w przeciwnym razie nie mają połączenia WSUS.

Oznacza to, że aktualizacje ochrony mogą być dostarczane do urządzeń (za pośrednictwem usługi Microsoft Update), nawet jeśli skonfigurowano usługę WSUS do zastępowania usługi Microsoft Update.

Możesz wyrazić zgodę na usługę Microsoft Update na urządzeniu przenośnym na jeden z następujących sposobów:

- Zmień ustawienie przy użyciu zasady grupy.
- Użyj skryptu VBScript, aby utworzyć skrypt, a następnie uruchom go na każdym komputerze w sieci.
- Ręcznie włącz każdy komputer w sieci za pośrednictwem menu **Ustawienia**.

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>Użyj zasady grupy, aby wyrazić zgodę na usługę Microsoft Update

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Wybierz pozycję **Zasady** , a następnie **szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **aktualizacje podpisu**.

5. Ustaw **opcję Zezwalaj na aktualizacje analizy zabezpieczeń z usługi Microsoft Update** na **wartość Włączone**, a następnie wybierz przycisk  **OK**.

### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>Korzystanie z języka VBScript, aby wyrazić zgodę na usługę Microsoft Update

1. Skorzystaj z instrukcji zawartych w artykule MSDN [Opt-In to Microsoft Update (Zgoda na korzystanie z usługi Microsoft Update](/windows/win32/wua_sdk/opt-in-to-microsoft-update) ), aby utworzyć język VBScript.

2. Uruchom skrypt VBScript utworzony na każdym komputerze w sieci.

### <a name="manually-opt-in-to-microsoft-update"></a>Ręczne włączanie usługi Microsoft Update

1. Otwórz **Windows Update** w **obszarze Aktualizowanie ustawień zabezpieczeń &** na komputerze, na który chcesz wyrazić zgodę.

2. Wybierz pozycję Opcje **zaawansowane** .

3. Zaznacz pole wyboru **Podaj mi aktualizacje dla innych produktów firmy Microsoft, gdy aktualizuję Windows**.

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>Zapobieganie aktualizacjom analizy zabezpieczeń podczas pracy z zasilaniem bateryjnym

Można skonfigurować Program antywirusowy Microsoft Defender do pobierania aktualizacji ochrony tylko wtedy, gdy komputer jest podłączony do przewodowego źródła zasilania.

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>Używanie zasady grupy do zapobiegania aktualizacjom analizy zabezpieczeń na zasilaniu bateryjnym

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), wybierz obiekt zasady grupy, który chcesz skonfigurować, i otwórz go do edycji.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Wybierz pozycję **Zasady** , a następnie **szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **aktualizacje sygnatur**, a następnie ustaw opcję **Zezwalaj na aktualizacje analizy zabezpieczeń podczas pracy z zasilaniem bateryjnym na** **wartość Wyłączone**. Następnie wybierz przycisk **OK**.

Ta akcja uniemożliwia pobieranie aktualizacji ochrony, gdy komputer jest zasilany z baterii.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="related-articles"></a>Artykuły pokrewne

- [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Aktualizowanie Program antywirusowy Microsoft Defender i zarządzanie nimi w Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)