---
title: Sprawdzanie lokalizacji przechowywania danych i aktualizowanie ustawień przechowywania danych
description: Weryfikowanie lokalizacji przechowywania danych i aktualizowanie ustawień przechowywania danych dla programu Microsoft Defender dla punktu końcowego
keywords: dane, magazyn, ustawienia, przechowywanie, aktualizacja
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: fb27a097f2f9dfd26e1b611c56be6d078ecadc52
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996777"
---
# <a name="verify-data-storage-location-and-update-data-retention-settings-for-microsoft-defender-for-endpoint"></a>Weryfikowanie lokalizacji przechowywania danych i aktualizowanie ustawień przechowywania danych dla programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-gensettings-abovefoldlink)

W trakcie procesu dołączania kreator przechodzi przez ustawienia przechowywania i przechowywania danych usługi Defender dla punktu końcowego. 

Po zakończeniu dołączania możesz zweryfikować wybór na stronie ustawień przechowywania danych.

## <a name="verify-data-storage-location"></a>Weryfikowanie lokalizacji przechowywania danych
W [fazie konfigurowanie wybrano](production-deployment.md) lokalizację przechowywania danych. 


Lokalizację danych możesz sprawdzić, przechodząc  \> do pozycji przechowywanie danych Ustawienia **punktów** \> **końcowych** (w obszarze **Ogólne**).


## <a name="update-data-retention-settings"></a>Aktualizowanie ustawień przechowywania danych

Możesz zaktualizować ustawienia przechowywania danych. Domyślnie okres przechowywania wynosi 180 dni. 

1. W okienku nawigacji wybierz pozycję Przechowywanie **Ustawienia** \> **punktów** \> **końcowych** (w obszarze **Ogólne**).

2. Z listy rozwijanej wybierz czas trwania przechowywania danych.

    > [!NOTE]
    > Innych ustawień nie można edytować.

3. Kliknij **pozycję Zapisz preferencje**.

## <a name="related-topics"></a>Tematy pokrewne
- [Aktualizowanie ustawień przechowywania danych](data-retention-settings.md)
- [Konfigurowanie powiadomień alertów w programie Defender dla punktu końcowego](configure-email-notifications.md)
- [Konfigurowanie funkcji zaawansowanych](advanced-features.md)
