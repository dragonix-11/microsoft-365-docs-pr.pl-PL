---
title: Konfigurowanie grup urządzeń w aplikacji Jamf Pro
description: Dowiedz się, jak skonfigurować grupy urządzeń w programie Jamf Pro dla programu Microsoft Defender for Endpoint w systemie macOS
keywords: device, group, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 3b9d6255320b5d702768614059bb9edff28be3b3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019230"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego w grupach urządzeń macOS w programie Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Skonfiguruj grupy urządzeń podobnie jak jednostki organizacyjne zasad grupy, Microsoft Endpoint Configuration Manager kolekcję urządzeń i grupy urządzeń usługi Intune.

1. Przejdź do **strony Statyczne grupy komputerów**.

2. Wybierz pozycję **Nowy**. 

    ![Obraz jamf pro1.](images/jamf-pro-static-group.png)

3. Podaj nazwę wyświetlaną i wybierz **pozycję Zapisz**.

    ![Obraz jamf pro2.](images/jamfpro-machine-group.png)

4. Grupa komputerów firmy **Contoso** będzie teraz w obszarze **Statyczne grupy komputerów**.

    ![Obraz jamf pro3.](images/contoso-machine-group.png)

## <a name="next-step"></a>Następny krok
- [Konfigurowanie programu Microsoft Defender dla punktu końcowego w zasadach macOS w programie Jamf Pro](mac-jamfpro-policies.md)
