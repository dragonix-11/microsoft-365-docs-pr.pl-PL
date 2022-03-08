---
title: Urządzenia wye webboard z usługi Microsoft Defender for Endpoint
description: Urządzenia Windows, serwery i urządzenia Windows z usługi Microsoft Defender for Endpoint
keywords: wyniesienie, usługa Microsoft Defender do obsługi wywęzienia i wye dołączania do punktu końcowego
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
ms.openlocfilehash: c2ec837ebc9fef0aabd2810dbd22db24597c52da
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322607"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>Urządzenia wye webboard z usługi Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platformy**
- macOS
- Linux
- Windows Server 2012 R2
- System Windows Server 2016

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-offboarddevices-abovefoldlink)

Postępuj zgodnie z odpowiednimi instrukcjami w zależności od preferowanej metody wdrażania.

> [!NOTE]
> Status urządzenia zostanie przełączony na Nieaktywny [po 7](fix-unhealthy-sensors.md#inactive-devices) dniach od wyeksłowania.
>
> Dane urządzeń wyłączonych (takie jak oś czasu, alerty, luki w zabezpieczeniach itp.) pozostaną w portalu do momentu wygaśnięcia skonfigurowanego [okresu przechowywania](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) .
>
> Profil urządzenia (bez danych) pozostanie na liście urządzeń nie dłużej niż [](machines-view-overview.md) 180 dni.
>
> Ponadto urządzenia, które nie są aktywne w ciągu ostatnich 30 dni, nie są wniesiene do danych, które odzwierciedlają Zarządzanie zagrożeniami i lukami organizacji oraz bezpiecznego wyniku działania firmy [](tvm-exposure-score.md) Microsoft dla urządzeń.
>
> Aby wyświetlić tylko aktywne urządzenia, możesz filtrować według stanu kondycji [czujnika](machines-view-overview.md#use-filters-to-customize-the-device-inventory-views), [tagów urządzeń lub](machine-tags.md) [grup maszynowych](machine-groups.md).

## <a name="offboard-windows-devices"></a>Urządzenia Windows wyeksłowy

- [Urządzenia wye korzystające ze skryptu lokalnego](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [Urządzenia wye korzystające z zasady grupy](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Urządzenia przenośne korzystające z narzędzi do zarządzania urządzeniami przenośnymi](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>Serwery odsuwowe

- [Serwery wye obszarów pozagiełd](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>Urządzenia niezwiązy Windows od urządzenia

- [Urządzenia niezwiązy Windows od urządzenia](configure-endpoints-non-windows.md#offboard-non-windows-devices)
