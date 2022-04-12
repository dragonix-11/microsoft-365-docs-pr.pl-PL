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
ms.openlocfilehash: 8a1aa78a153e11f1a36fe9f7dcbd85322e6f258d
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787957"
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
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)