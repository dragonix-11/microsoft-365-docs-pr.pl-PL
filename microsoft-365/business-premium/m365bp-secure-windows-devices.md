---
title: Zabezpieczanie urządzeń Windows
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: 21e5551f-fa35-4f13-9418-f80d668b6a2b
description: Dowiedz się więcej na temat konfigurowania ustawień domyślnych zasad urządzenia, które będą otrzymywać wszystkie Windows urządzenia po zalogowaniu się do konta służbowego.
ms.openlocfilehash: d8a32dd5378ed1b16e6126e9091f2bd2bb8515f5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094643"
---
# <a name="secure-windows-devices"></a>Zabezpieczanie urządzeń Windows

Ten artykuł dotyczy Microsoft 365 Business Premium.

Ustawienia skonfigurowane w tym miejscu są częścią domyślnych zasad urządzenia dla Windows 10 lub 11. Wszyscy użytkownicy, którzy łączą urządzenie Windows, w tym urządzenia przenośne i komputery, logując się przy użyciu konta służbowego, automatycznie otrzymają te ustawienia. Zalecane jest zaakceptowanie domyślnych zasad podczas instalacji i dodanie w późniejszym terminie zasad dotyczących konkretnych grup użytkowników.
  
## <a name="settings-to-secure-windows-10-devices"></a>Ustawienia zabezpieczające urządzenia z systemem Windows 10

Domyślnie wszystkie ustawienia są **Włączone**. Dostępne są następujące ustawienia:<br/><br/>

|Ustawienie  <br/> |Opis  <br/> |
|:-----|:-----|
|Chroń komputery przed wirusami i innymi zagrożeniami za pomocą ochrony antywirusowej programu Windows Defender  <br/> |Wymaga włączenia programu antywirusowego Windows Defender w celu ochrony komputerów przed zagrożeniami związanymi z połączeniem z Internetem.  <br/> |
|Chroń komputery przed zagrożeniami internetowymi w programie Microsoft Edge  <br/> |Włącza w programie Microsoft Edge ustawienia ułatwiające ochronę użytkowników przed złośliwymi witrynami i złośliwą zawartością do pobrania.  <br/> |
|Pomóż chronić pliki i foldery na komputerach przed nieautoryzowanym dostępem za pomocą funkcji BitLocker  <br/> |Funkcja BitLocker chroni dane przez szyfrowanie dysków twardych komputera i ochronę przed ujawnieniem danych w przypadku utraty lub kradzieży komputera. Aby uzyskać więcej informacji, zobacz [Funkcja BitLocker — często zadawane pytania](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Wyłącz ekran urządzenia po takim czasie bezczynności  <br/> |Zapewnia bezpieczeństwo danych firmowych podczas bezczynności użytkownika. Jeśli użytkownik pracuje w miejscu publicznym, na przykład kawiarni, i odejdzie na chwilę od urządzenia lub skupi uwagę na czymś innym, przypadkowe osoby mogą obejrzeć zawartość ekranu. To ustawienie pozwala kontrolować czas bezczynności użytkownika, po którym ekran zostanie wyłączony.  <br/> |
