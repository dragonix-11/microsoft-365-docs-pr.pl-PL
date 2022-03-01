---
title: Konfigurowanie Program antywirusowy Microsoft Defender funkcji
description: Możesz konfigurować Program antywirusowy Microsoft Defender usługi Intune, Microsoft Endpoint Configuration Manager, zasady grupy i PowerShell.
keywords: Program antywirusowy Microsoft Defender, antimalware, security, defender, configure, configuration, Config Manager, Microsoft Endpoint Configuration Manager, SCCM, Intune, MDM, zarządzanie urządzeniami przenośnymi, GP, zasady grupy, PowerShell
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
ms.openlocfilehash: 183fedefbbb56411674ff80a9feedc507cff0530
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014713"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Konfigurowanie Program antywirusowy Microsoft Defender funkcji


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Użytkownik może Program antywirusowy Microsoft Defender za pomocą kilku narzędzi, takich jak:

- Microsoft Endpoint Manager (która obejmuje Microsoft Intune i Microsoft Endpoint Configuration Manager)
- zasady grupy
- Polecenia cmdlet programu PowerShell
- Windows instrumentacja zarządzania (WMI)
- [Dołączanie dzierżawy](/mem/configmgr/tenant-attach/)

Można skonfigurować następujące ogólne kategorie funkcji:

- Ochrona w chmurze. Zobacz [Ochrona i ochrona w chmurze Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- Zawsze w on-time protection, including behavioral, heuristic, and machine learning based protection. Zobacz [Konfigurowanie ochrony zachowanie, heuristic i w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md).

- Interakcja użytkowników końcowych z klientem na poszczególnych punktach końcowych. Zobacz następujące zasoby:
  - [Uniemożliwianie użytkownikom oglądania interfejsu Program antywirusowy Microsoft Defender interakcji z nim](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie Program antywirusowy Microsoft Defender zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> Przejrzyj [tematy referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md).
