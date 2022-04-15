---
title: Odłączanie urządzenia od Microsoft Defender dla Firm
description: Dowiedz się, jak usunąć urządzenie z Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f702cb51e87777f0ac0e18e7caa794977df9c3dd
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862943"
---
# <a name="offboard-a-device-from-microsoft-defender-for-business"></a>Odłączanie urządzenia od Microsoft Defender dla Firm

Jeśli chcesz odłączyć urządzenie, użyj jednej z następujących procedur:

- [Odłączanie urządzenia Windows](#offboard-a-windows-device)
- [Odłączanie komputera z systemem macOS](#offboard-a-macos-computer)

## <a name="offboard-a-windows-device"></a>Odłączanie urządzenia Windows

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz **pozycję Ustawienia**, a następnie wybierz pozycję **Punkty końcowe**.

3. W obszarze **Zarządzanie urządzeniami** wybierz pozycję **Odłączanie**.

4. Wybierz system operacyjny, taki jak **Windows 10 i 11**, a następnie w obszarze **Odłącz urządzenie** w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

5. Na ekranie potwierdzenia przejrzyj informacje, a następnie wybierz pozycję **Pobierz** , aby kontynuować.

6. Wybierz pozycję **Pobierz pakiet odłączania**. Zalecamy zapisanie pakietu odłączania na dysku wymiennym.

7. Uruchom skrypt na każdym urządzeniu, które chcesz odłączyć.

## <a name="offboard-a-macos-computer"></a>Odłączanie komputera z systemem macOS

1. Przejdź do pozycji **FinderApplications** > . 

2. Kliknij prawym przyciskiem myszy Microsoft Defender dla Firm, a następnie wybierz pozycję **Przenieś do kosza**. <br/><br/>--- lub --- <br/><br/> Użyj następującego polecenia: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.

> [!IMPORTANT]
> Odłączenie urządzenia powoduje, że urządzenia przestają wysyłać dane do usługi Defender dla Firm. Jednak dane odebrane przed odłożeniem są przechowywane przez maksymalnie sześć (6) miesięcy.

## <a name="next-steps"></a>Następne kroki

