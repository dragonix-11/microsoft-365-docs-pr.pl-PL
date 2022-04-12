---
title: Konfigurowanie Program antywirusowy Microsoft Defender przy użyciu Microsoft Endpoint Manager
description: Konfigurowanie Program antywirusowy Microsoft Defender i Endpoint Protection przy użyciu Microsoft Endpoint Manager i Microsoft Intune
keywords: scep, intune, endpoint protection, configuration
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 12/16/2021
ms.reviewer: phuijbr, oogunrinde
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: b25e57ee28ae0ef3f219a9adda1ff3f860d063db
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789299"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Konfigurowanie Program antywirusowy Microsoft Defender i zarządzanie nimi za pomocą Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Do konfigurowania skanowania Program antywirusowy Microsoft Defender można użyć [Microsoft Endpoint Manager](/mem/endpoint-manager-overview). [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Configuration Manager](/mem/configmgr/core/understand/introduction) są teraz częścią Endpoint Manager.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Konfigurowanie skanowania Program antywirusowy Microsoft Defender w Endpoint Manager

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Przejdź do **pozycji Zabezpieczenia punktu końcowego**.

3. W obszarze **Zarządzanie** wybierz pozycję **Program antywirusowy**.

4. Wybierz zasady Program antywirusowy Microsoft Defender.

5. W obszarze **Zarządzanie** wybierz pozycję **Właściwości**.

6. Obok pozycji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

   > [!IMPORTANT]
   > Ustawienia antywirusowe AllowOnAccessProtection i AllowIntrusionPreventionSystem są oficjalnie przestarzałe i jako takie nie można skonfigurować. 

7. Rozwiń sekcję **Skanowanie** i przejrzyj lub edytuj ustawienia skanowania.

8. Wybierz **pozycję Przejrzyj i zapisz**.

> [!TIP]
> Potrzebujesz pomocy? Zobacz [Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security).

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

- [Artykuły referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
