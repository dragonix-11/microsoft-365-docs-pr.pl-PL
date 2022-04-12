---
title: Monitorowanie i raportowanie ochrony Program antywirusowy Microsoft Defender
description: Używaj Configuration Manager lub narzędzi do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM), aby korzystać z raportów i monitorować usługę Microsoft Defender AV przy użyciu programu PowerShell i usługi WMI.
keywords: siem, monitor, report, Microsoft Defender AV
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: b6593784b0df1109eb7729b3df91ef467d30c4bb
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788419"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Raportuj na temat programu antywirusowego Microsoft Defender

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender jest wbudowana w Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 i Windows Server 2016. Program antywirusowy Microsoft Defender jest twoją ochroną nowej generacji w Ochrona punktu końcowego w usłudze Microsoft Defender. Ochrona nowej generacji pomaga chronić urządzenia przed zagrożeniami oprogramowania, takimi jak wirusy, złośliwe oprogramowanie i programy szpiegujące w wiadomościach e-mail, aplikacjach, chmurze i Internecie.

W przypadku Program antywirusowy Microsoft Defender masz kilka opcji przeglądania stanu ochrony i alertów. Za pomocą Microsoft Endpoint Manager można [monitorować Program antywirusowy Microsoft Defender](/configmgr/protect/deploy-use/monitor-endpoint-protection) lub [tworzyć alerty e-mail](/configmgr/protect/deploy-use/endpoint-configure-alerts). Możesz też monitorować ochronę przy użyciu [Microsoft Intune](/intune/introduction-intune).

Jeśli masz serwer zarządzania informacjami o zabezpieczeniach i zdarzeniami innych firm (SIEM), możesz również korzystać [z Windows Defender zdarzeń klienta](/windows/win32/events/windows-events).

Windows zdarzenia obejmują kilka źródeł zdarzeń zabezpieczeń, w tym zdarzenia menedżera kont zabezpieczeń (SAM) ([rozszerzone dla Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511), zobacz również temat [Inspekcja zabezpieczeń](/windows/device-security/auditing/security-auditing-overview)) i [zdarzenia Windows Defender](troubleshoot-microsoft-defender-antivirus.md).

Te zdarzenia mogą być centralnie agregowane przy użyciu [modułu zbierającego zdarzenia Windows](/windows/win32/wec/windows-event-collector). Często serwery SIEM mają łączniki dla zdarzeń Windows, co umożliwia skorelowanie wszystkich zdarzeń zabezpieczeń na serwerze SIEM.

Zdarzenia [złośliwego oprogramowania można również monitorować przy użyciu rozwiązania Do oceny złośliwego oprogramowania w usłudze Log Analytics](/azure/log-analytics/log-analytics-malware).

Aby monitorować lub określać stan za pomocą programu PowerShell, WMI lub Microsoft Azure, zobacz [(Tabela opcji wdrażania, zarządzania i raportowania)](deploy-manage-report-microsoft-defender-antivirus.md#ref2).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
