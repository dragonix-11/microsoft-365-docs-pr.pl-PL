---
title: Konfigurowanie Program antywirusowy Microsoft Defender przy użyciu Microsoft Endpoint Manager
description: Konfigurowanie Microsoft Endpoint Manager i Microsoft Intune za pomocą Program antywirusowy Microsoft Defender i Endpoint Protection
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
ms.openlocfilehash: 1eb126481cc9872c42906e0311d1c771da44c693
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2021
ms.locfileid: "63017951"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Konfigurowanie Microsoft Endpoint Manager zarządzanie plikami i zarządzanie nimi Program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Za pomocą aplikacji [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) możesz skonfigurować Program antywirusowy Microsoft Defender skanów. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Menedżer konfiguracji](/mem/configmgr/core/understand/introduction) są teraz częścią Endpoint Manager.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Konfigurowanie Program antywirusowy Microsoft Defender skanowania w Endpoint Manager

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Przejdź do **zabezpieczeń punktu końcowego**.

3. W **obszarze Zarządzanie** wybierz pozycję **Oprogramowanie antywirusowe**.

4. Wybierz swoje Program antywirusowy Microsoft Defender konta.

5. W **obszarze Zarządzanie** wybierz pozycję **Właściwości**.

6. Obok opcji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

   > [!IMPORTANT]
   > Ustawienia oprogramowania antywirusowego AllowOnAccessProtection i AllowIntrusionPreventionSystem są oficjalnie przestarzałe i nie można ich skonfigurować. 

7. Rozwiń **sekcję** Skanowanie i przejrzyj lub edytuj ustawienia skanowania.

8. Wybierz **pozycję Recenzja + zapisywanie**.

> [!TIP]
> Potrzebujesz pomocy? Zobacz [Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security).

## <a name="related-articles"></a>Artykuły pokrewne

- [Artykuły referencyjne dotyczące narzędzi do zarządzania i konfiguracji](configuration-management-reference-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
