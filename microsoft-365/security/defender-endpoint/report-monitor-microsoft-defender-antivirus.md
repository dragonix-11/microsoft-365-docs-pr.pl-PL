---
title: Monitorowanie ochrony sieci i zgłaszanie Program antywirusowy Microsoft Defender informacji
description: Używaj Menedżer konfiguracji informacji o zabezpieczeniach i zarządzaniu zdarzeniami, aby korzystać z raportów, oraz monitoruj program Microsoft Defender AV za pomocą programu PowerShell i WMI.
keywords: siem, monitor, raport, Microsoft Defender AV
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
ms.openlocfilehash: 8d801daed1ae9884d10d6a4eec7059096333ec6f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997270"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Raport z Program antywirusowy Microsoft Defender

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Program antywirusowy Microsoft Defender jest wbudowany w Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 i Windows Server 2016. Program antywirusowy Microsoft Defender ochronę następnej generacji w programie Microsoft Defender dla punktu końcowego. Ochrona następnej generacji pomaga chronić urządzenia przed zagrożeniami oprogramowania, np. wirusami, złośliwym oprogramowaniem i programami szpiegującymi w wiadomościach e-mail, aplikacjach, chmurze i sieci Web.

W Program antywirusowy Microsoft Defender masz kilka opcji przeglądania stanu ochrony i alertów. Alerty e [Microsoft Endpoint Manager-mail można Program antywirusowy Microsoft Defender](/configmgr/protect/deploy-use/monitor-endpoint-protection) [tworzyć](/configmgr/protect/deploy-use/endpoint-configure-alerts). Możesz też monitorować ochronę za pomocą [Microsoft Intune](/intune/introduction-intune).

Jeśli masz serwer zarządzania zdarzeniami i informacjami o zabezpieczeniach od innej firmy, możesz również Windows Defender [zdarzeń klienta](/windows/win32/events/windows-events).

Windows zdarzeń składa się z kilku źródeł zdarzeń zabezpieczeń, w tym zdarzeń Menedżera konta zabezpieczeń (SAM, Security Account Manager) (rozszerzone dla programu [Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511) można [](/windows/device-security/auditing/security-auditing-overview) również znaleźć w temacie Inspekcja zabezpieczeń) [Windows Defender zdarzeń](troubleshoot-microsoft-defender-antivirus.md).

Te zdarzenia można agregować centralnie przy [użyciu Windows zdarzenia](/windows/win32/wec/windows-event-collector). Serwery SIEM często mają łączniki Windows, co pozwala skorelować wszystkie zdarzenia zabezpieczeń na serwerze SIEM.

Możesz także [monitorować zdarzenia złośliwego oprogramowania za pomocą rozwiązania do oceny złośliwego oprogramowania w narzędziu Log Analytics](/azure/log-analytics/log-analytics-malware).

Informacje o stanie monitorowania lub określania stanu za pomocą programu PowerShell, usługi WMI Microsoft Azure można znaleźć w tabeli (Tabela Opcje wdrażania[, zarządzania i raportowania).](deploy-manage-report-microsoft-defender-antivirus.md#ref2)

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
