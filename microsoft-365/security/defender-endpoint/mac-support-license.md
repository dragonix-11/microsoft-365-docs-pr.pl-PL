---
title: Rozwiązywanie problemów z licencjami programu Microsoft Defender dla punktu końcowego na komputerze Mac
description: Rozwiązywanie problemów z licencjami w programie Microsoft Defender dla punktu końcowego na komputerze Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, performance
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b0a328ffeee6ee5796cb92f00b8491b257e88a65
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011343"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Rozwiązywanie problemów z licencją programu Microsoft Defender dla punktu końcowego w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Program Microsoft Defender for Endpoint w systemie macOS](microsoft-defender-endpoint-mac.md)
 [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
 [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Podczas korzystania z programu [Microsoft Defender for Endpoint w systemie macOS](microsoft-defender-endpoint-mac.md) i [](mac-install-manually.md) podczas testowania ręcznego lub weryfikacji koncepcji może zostać wyświetlany następujący komunikat o błędzie:

![Obraz błędu licencji.](images/no-license-found.png)

**Komunikat:** 

Nie znaleziono licencji

Wygląda na to, że Twoja organizacja nie ma licencji na Microsoft 365 Enterprise subskrypcji.

Aby uzyskać pomoc, skontaktuj się z administratorem.

**Przyczyna:** 

Wdrożono i/lub zainstalowano program Microsoft Defender for Endpoint w pakiecie macOS ("Pobierz pakiet instalacyjny"), ale być może nie został uruchomiony skrypt konfiguracji ("Pobierz pakiet wdrażania") lub licencja nie została przypisana do użytkownika.

Ten błąd może również wystąpić, gdy program Microsoft Defender for Endpoint w agentze macOS jest aktualny. 


**Rozwiązanie:**

Postępuj zgodnie z MicrosoftDefenderATPOnboardingMacOs.py w tym miejscu: [Konfiguracja klienta](mac-install-manually.md#client-configuration)

W scenariuszach, w których program Microsoft Defender for Endpoint w systemie macOS nie jest aktualny, musisz zaktualizować agenta. 
