---
title: Definiowanie sposobu aktualizowania urządzeń przenośnych przez Program antywirusowy Microsoft Defender
description: Zarządzaj tym, jak urządzenia przenośne, takie jak komputery przenośne, powinny być aktualizowane za pomocą Program antywirusowy Microsoft Defender ochrony.
keywords: aktualizacje, ochrona, planowanie aktualizacji, bateria, urządzenie przenośne, laptop, notes, opt-in, microsoft update, wsus, override
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
ms.openlocfilehash: 3fc6d5a8b8fa7889f65f21111b3af82e124516b4
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997307"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>Zarządzanie aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Urządzenia przenośne i maszyny wirtualne mogą wymagać większej konfiguracji, aby aktualizacje nie miały wpływu na wydajność.

Istnieją dwa ustawienia, które są przydatne dla tych urządzeń:

- Opt in to Microsoft Update on mobile computers without a WSUS connection
- Zapobieganie aktualizacjom analizy zabezpieczeń podczas pracy z baterią

W następujących sytuacjach mogą być również przydatne następujące artykuły:
- [Konfigurowanie zaplanowanych i pochwytnych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Zarządzanie aktualizacjami dla punktów końcowych, które są aktualne](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Przewodnik po wdrażaniu Program antywirusowy Microsoft Defender w środowisku infrastruktury pulpitów wirtualnych (VDI, Virtual Desktop Infrastructure)](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>Opt in to Microsoft Update on mobile computers without a WSUS connection

Za pomocą usługi Microsoft Update możesz aktualizować zabezpieczenia na urządzeniach przenośnych z systemem Program antywirusowy Microsoft Defender aktualne, gdy nie są one połączone z siecią firmową lub nie mają połączenia programu WSUS.

Oznacza to, że aktualizacje ochrony mogą być dostarczane na urządzenia (za pośrednictwem usługi Microsoft Update), nawet jeśli program WSUS ma zastępować usługę Microsoft Update.

Usługę Microsoft Update na urządzeniu przenośnym możesz wybrać w jeden z następujących sposobów:

- Zmień ustawienie za pomocą zasady grupy.
- Użyj języka VBScript, aby utworzyć skrypt, a następnie uruchom go na każdym komputerze w sieci.
- Ręcznie wybierz opcję na każdym komputerze w twojej sieci, **Ustawienia menu.**

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>Używanie zasady grupy w celu korzystania z usługi Microsoft Update

1. Na komputerze zasady grupy zarządzania danymi otwórz konsolę [zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

3. Wybierz **pozycję Zasady** , **a następnie szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **aktualizacji podpisu**.

5. Ustaw **opcję Zezwalaj na aktualizacje analizy zabezpieczeń z usługi Microsoft Update** **na wartość Włączone**, a następnie wybierz przycisk  **OK**.

### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>Korzystanie z języka VBScript w celu korzystania z usługi Microsoft Update

1. Aby utworzyć kod VBScript, skorzystaj z instrukcji z artykułu w witrynie MSDN", w którym pobrano zgodę na usługę [Microsoft Update](/windows/win32/wua_sdk/opt-in-to-microsoft-update) .

2. Uruchom kod języka VBScript utworzony na każdym komputerze w sieci.

### <a name="manually-opt-in-to-microsoft-update"></a>Ręczne otrzymywanie zgody na usługę Microsoft Update

1. Otwórz **Windows aktualizacji w** **& ustawienia** zabezpieczeń na komputerze, na którym chcesz wybrać opcję.

2. Wybierz **pozycję Opcje** zaawansowane.

3. Zaznacz pole wyboru dla **opcji Aktualizuj mnie dla innych produktów firmy Microsoft, gdy aktualizuję Windows**.

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>Zapobieganie aktualizacjom analizy zabezpieczeń podczas pracy z baterią

Możesz tak skonfigurować Program antywirusowy Microsoft Defender pobierania aktualizacji ochrony tylko wtedy, gdy komputer jest podłączony do przewodowego źródła zasilania.

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>Zapobieganie aktualizacjom zasady grupy zabezpieczeń przy oszczędzaniu baterii za pomocą przycisków

1. Na komputerze zasady grupy zarządzania danymi [otwórz konsolę](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) zasady grupy zarządzania danymi, wybierz zasady grupy obiekt, który chcesz skonfigurować, a następnie otwórz go do edycji.

2. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

3. Wybierz **pozycję Zasady** , **a następnie szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki** \> **Program antywirusowy Microsoft Defender** \> aktualizacje **podpisu, a** następnie ustaw dla ustawienia Zezwalaj na aktualizacje analizy zabezpieczeń, gdy pracujesz na **baterii, wartość** **Wyłączone**. Następnie wybierz przycisk **OK**.

Ta akcja zapobiega pobieraniu aktualizacji ochrony, gdy komputer jest naładowany.

## <a name="related-articles"></a>Artykuły pokrewne

- [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Aktualizowanie i zarządzanie Program antywirusowy Microsoft Defender w Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)