---
title: Konfigurowanie grup urządzeń w aplikacji Jamf Pro
description: Dowiedz się, jak skonfigurować grupy urządzeń w programie Jamf Pro dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS
keywords: device, group, microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, installation, deploy, dezinstalacja, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: c22a1a68af2722e6b17d155a37632c1f6417b605
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471764"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Konfigurowanie grup Ochrona punktu końcowego w usłudze Microsoft Defender macOS w aplikacji Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Skonfiguruj grupy urządzeń podobnie jak grupy organizacyjne zasad grupy, Microsoft Endpoint Configuration Manager kolekcję urządzeń grupy oraz grupy urządzeń Intune grupy urządzeń grupy.

1. Przejdź do **strony Statyczne grupy komputerów**.

2. Wybierz pozycję **Nowy**. 

   :::image type="content" source="images/jamf-pro-static-group.png" alt-text="Strona Jamf Pro1" lightbox="images/jamf-pro-static-group.png":::

3. Podaj nazwę wyświetlaną i wybierz **pozycję Zapisz**.

   :::image type="content" source="images/jamfpro-machine-group.png" alt-text="Strona Jamf Pro2" lightbox="images/jamfpro-machine-group.png":::

4. Grupa komputerów firmy **Contoso** będzie teraz w obszarze **Statyczne grupy komputerów**.

   :::image type="content" source="images/contoso-machine-group.png" alt-text="Strona Jamf Pro3" lightbox="images/contoso-machine-group.png":::

## <a name="next-step"></a>Następny krok
- [Konfigurowanie zasad Ochrona punktu końcowego w usłudze Microsoft Defender macOS w programie Jamf Pro](mac-jamfpro-policies.md)
