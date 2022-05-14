---
title: Konfiguruj funkcje programu antywirusowego Microsoft Defender
description: Funkcje Program antywirusowy Microsoft Defender można skonfigurować przy użyciu Intune, Microsoft Endpoint Configuration Manager, zasady grupy i programu PowerShell.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, defender, konfigurowanie, konfiguracja, Config Manager, Microsoft Endpoint Configuration Manager, SCCM, Intune, MDM, zarządzanie urządzeniami przenośnymi, gp, zasady grupy, PowerShell
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/14/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 4047b4628c8b63996be29d77ec13712082fde182
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419225"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Konfiguruj funkcje programu antywirusowego Microsoft Defender


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Możesz skonfigurować Program antywirusowy Microsoft Defender za pomocą wielu narzędzi, takich jak:

- Microsoft Endpoint Manager (w tym Microsoft Intune i Microsoft Endpoint Configuration Manager)
- Zasady grupy
- Polecenia cmdlet programu PowerShell
- Instrumentacja zarządzania Windows (WMI)
- [Dołączanie dzierżawy](/mem/configmgr/tenant-attach/)

Można skonfigurować następujące szerokie kategorie funkcji:

- Ochrona dostarczana przez chmurę. Zobacz [Ochrona i Program antywirusowy Microsoft Defender dostarczane w chmurze](cloud-protection-microsoft-defender-antivirus.md)

- Zawsze włączona ochrona w czasie rzeczywistym, w tym ochrona behawioralna, heurystyczna i oparta na uczeniu maszynowym. Zobacz [Konfigurowanie ochrony behawioralnej, heurystycznej i ochrony w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md).

- Sposób interakcji użytkowników końcowych z klientem w poszczególnych punktach końcowych. Zobacz następujące zasoby:
  - [Uniemożliwianie użytkownikom korzystania z interfejsu użytkownika Program antywirusowy Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad Program antywirusowy Microsoft Defender lub zezwalanie na nie](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> Zapoznaj [się z tematami referencyjnymi dotyczącymi narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)