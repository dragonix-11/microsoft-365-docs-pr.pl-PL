---
title: Zabezpieczanie Windows urządzeniach
f1.keywords:
- CSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Dowiedz się, jak skonfigurować ustawienia domyślnych zasad dotyczących urządzeń, które Windows urządzenie otrzyma po zalogowaniu się do konta służbowego.
ms.openlocfilehash: b58e63abf19c3078eb5d4356b155df13804c95d5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704820"
---
# <a name="secure-windows-devices"></a>Zabezpieczanie Windows urządzeniach

Ten artykuł dotyczy wszystkich Microsoft 365 Business Premium.

Konfigurowane tutaj ustawienia są częścią domyślnych zasad dotyczących urządzeń dla Windows 10 lub 11. Wszyscy użytkownicy, którzy łączą się z Windows komputerami, w tym urządzeniami przenośnymi i komputerami, logując się przy użyciu swojego konta służbowego, automatycznie otrzymają te ustawienia. Zalecane jest zaakceptowanie domyślnych zasad podczas instalacji i dodanie w późniejszym terminie zasad dotyczących konkretnych grup użytkowników.
  
## <a name="settings-to-secure-windows-10-devices"></a>Ustawienia zabezpieczające urządzenia z systemem Windows 10

Domyślnie wszystkie ustawienia są **Włączone**. Dostępne są następujące ustawienia:<br/><br/>

|Ustawienie  <br/> |Opis  <br/> |
|:-----|:-----|
|Chroń komputery przed wirusami i innymi zagrożeniami za pomocą ochrony antywirusowej programu Windows Defender  <br/> |Wymaga włączenia programu antywirusowego Windows Defender w celu ochrony komputerów przed zagrożeniami związanymi z połączeniem z Internetem.  <br/> |
|Chroń komputery przed zagrożeniami internetowymi w programie Microsoft Edge  <br/> |Włącza w programie Microsoft Edge ustawienia ułatwiające ochronę użytkowników przed złośliwymi witrynami i złośliwą zawartością do pobrania.  <br/> |
|Pomóż chronić pliki i foldery na komputerach przed nieautoryzowanym dostępem za pomocą funkcji BitLocker  <br/> |Funkcji BitLocker chroni dane przez zaszyfrowanie dysków twardych komputera i zapewnianie ochrony przed dostępem do danych w razie zagubienia lub kradzieży komputera. Aby uzyskać więcej informacji, zobacz [Często zadawane pytania dotyczące funkcji BitLocker](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Wyłącz ekran urządzenia po takim czasie bezczynności  <br/> |Zapewnia bezpieczeństwo danych firmowych podczas bezczynności użytkownika. Jeśli użytkownik pracuje w miejscu publicznym, na przykład kawiarni, i odejdzie na chwilę od urządzenia lub skupi uwagę na czymś innym, przypadkowe osoby mogą obejrzeć zawartość ekranu. To ustawienie pozwala kontrolować czas bezczynności użytkownika, po którym ekran zostanie wyłączony.  <br/> |
