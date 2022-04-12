---
title: Włączanie i konfigurowanie funkcji ochrony Program antywirusowy Microsoft Defender
description: Włączanie ochrony opartej na zachowaniu, heurystycznej i w czasie rzeczywistym w usłudze Microsoft Defender AV.
keywords: heurystyczne, uczenie maszynowe, monitorowanie zachowania, ochrona w czasie rzeczywistym, zawsze włączona, Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, obrońca
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
ms.openlocfilehash: 59754ac5186b87045e8126114fd7342f5aa9532c
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788859"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Konfiguruj ochronę behawioralną, heurystyczną i w czasie rzeczywistym


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender 

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender używa kilku metod w celu zapewnienia ochrony przed zagrożeniami:

- Ochrona chmury przed niemal natychmiastowym wykrywaniem i blokowaniem nowych i pojawiających się zagrożeń
- Zawsze włączone skanowanie przy użyciu monitorowania zachowania plików i procesów oraz innych heurystycznych (znanych również jako "ochrona w czasie rzeczywistym")
- Dedykowane aktualizacje ochrony oparte na uczeniu maszynowym, ludzkiej i zautomatyzowanej analizie danych big data oraz szczegółowych badaniach nad odpornością na zagrożenia

Można skonfigurować sposób, w jaki Program antywirusowy Microsoft Defender korzysta z tych metod za pomocą zasady grupy, zarządzania konfiguracją System Center, poleceń cmdlet programu PowerShell i instrumentacji zarządzania Windows (WMI).

W tej sekcji opisano konfigurację zawsze włączonego skanowania, w tym sposób wykrywania i blokowania aplikacji, które są uważane za niebezpieczne, ale nie mogą być wykrywane jako złośliwe oprogramowanie.

Zobacz [Korzystanie z technologii Program antywirusowy Microsoft Defender nowej generacji za pośrednictwem ochrony w chmurze](cloud-protection-microsoft-defender-antivirus.md), aby dowiedzieć się, jak włączyć i skonfigurować Program antywirusowy Microsoft Defender ochrony w chmurze.

## <a name="in-this-section"></a>W tej sekcji

| Temat|Opis |
|---|---|
| [Wykryj i blokuj potencjalnie niechciane aplikacje](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Wykrywanie i blokowanie aplikacji, które mogą być niepożądane w sieci, takich jak adware, modyfikatory przeglądarki i paski narzędzi oraz nieautoryzowane lub fałszywe aplikacje antywirusowe |
| [Włączanie i konfigurowanie funkcji ochrony Program antywirusowy Microsoft Defender](configure-real-time-protection-microsoft-defender-antivirus.md)|Włączanie i konfigurowanie ochrony w czasie rzeczywistym, heurystyki i innych zawsze włączonych funkcji monitorowania Program antywirusowy Microsoft Defender |

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)
