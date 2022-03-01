---
title: Włączanie i konfigurowanie Program antywirusowy Microsoft Defender ochrony
description: Włączanie ochrony opartej na zachowaniu, heuristic i w czasie rzeczywistym w programie Microsoft Defender AV.
keywords: heuristic, machine learning, behavior monitor, real-time protection, always-on, Program antywirusowy Microsoft Defender, antimalware, security, defender
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
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: f949623b7d0647d71f4c665ed2016ee14a765e5f
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014715"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Konfigurowanie ochrony zachowanie, heuristic i w czasie rzeczywistym


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Program antywirusowy Microsoft Defender stosuje kilka metod ochrony przed zagrożeniami:

- Ochrona chmury do natychmiastowego wykrywania i blokowania nowych i pojawiających się zagrożeń
- Zawsze on scanning, using file and process behavior monitoring and other heuristics (known known as "real-time protection")
- Dedykowane aktualizacje ochrony oparte na uczeniem maszynowym, analizie danych big-data przez ludzi oraz szczegółowe badania odporność na zagrożenia

Możesz skonfigurować sposób, w jaki Program antywirusowy Microsoft Defender tych metod używa się z usługą zasady grupy, System Center zarządzaniem konfiguracją, poleceniami cmdlet programu PowerShell i instrumentacją zarządzania Windows (WMI).

W tej sekcji opisano konfigurację skanowania zawsze przy jegotrzymaniu, w tym sposób wykrywania i blokowania aplikacji uznanych za niebezpieczne, ale mogą nie być wykrywane jako złośliwe oprogramowanie.

Zobacz [Korzystanie z technologii nowej Program antywirusowy Microsoft Defender przez](cloud-protection-microsoft-defender-antivirus.md) ochronę chmury, aby dowiedzieć się, jak włączyć Program antywirusowy Microsoft Defender ochrony w chmurze.

## <a name="in-this-section"></a>W tej sekcji

| Temat|Opis |
|---|---|
| [Wykrywanie i blokowanie potencjalnie niechcianych aplikacji](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Wykrywaj i blokuj aplikacje, które mogą być niechciane w Twojej sieci, takie jak oprogramowanie, modyfikatory i paski narzędzi przeglądarki oraz fałszywe lub rogue aplikacje antywirusowe. |
| [Włączanie i konfigurowanie Program antywirusowy Microsoft Defender ochrony](configure-real-time-protection-microsoft-defender-antivirus.md)|Włączanie i konfigurowanie ochrony w czasie rzeczywistym, heuristics i innych zawsze Program antywirusowy Microsoft Defender funkcji monitorowania |
