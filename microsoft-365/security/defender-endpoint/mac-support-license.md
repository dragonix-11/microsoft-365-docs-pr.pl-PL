---
title: Rozwiązywanie problemów z licencjami na Ochrona punktu końcowego w usłudze Microsoft Defender komputerach Mac
description: Rozwiązywanie problemów z licencjami w Ochrona punktu końcowego w usłudze Microsoft Defender komputerach Mac.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, wydajność
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
ms.openlocfilehash: 35b77183ee9ceb00569c956d30debb0dd61e63f7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471742"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Rozwiązywanie problemów z licencjami dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](microsoft-defender-endpoint-mac.md)
 [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
[ Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Podczas przeprowadzania testów [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](microsoft-defender-endpoint-mac.md) i testowania [](mac-install-manually.md) ręcznego lub weryfikacji koncepcji (PoC) może zostać wyświetlany następujący komunikat o błędzie:

:::image type="content" source="images/no-license-found.png" alt-text="Błąd licencji" lightbox="images/no-license-found.png":::

**Komunikat:** 

Nie znaleziono licencji

Wygląda na to, że Twoja organizacja nie ma licencji na Microsoft 365 Enterprise subskrypcji.

Aby uzyskać pomoc, skontaktuj się z administratorem.

**Przyczyna:** 

Oprogramowanie Ochrona punktu końcowego w usłudze Microsoft Defender wdrożono i/lub zainstalowano w pakiecie macOS ("Pobierz pakiet instalacyjny"), ale być może nie został uruchomiony skrypt konfiguracji ("Pobierz pakiet wdrażania") lub licencja nie została przypisana do użytkownika.

Ten błąd może również wystąpić, gdy Ochrona punktu końcowego w usłudze Microsoft Defender w agentze macOS jest aktualny. 


**Rozwiązanie:**

Postępuj zgodnie z MicrosoftDefenderATPOnboardingMacOs.py w tym miejscu: [Konfiguracja klienta](mac-install-manually.md#client-configuration)

W scenariuszach Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS nie jest aktualny, musisz zaktualizować agenta. 
