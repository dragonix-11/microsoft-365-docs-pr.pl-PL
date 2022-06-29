---
title: Odłączanie urządzeń z usługi Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dołączanie urządzeń z systemem Windows, serwerów, urządzeń z systemem innym niż Windows z usługi Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: offboarding, Ochrona punktu końcowego w usłudze Microsoft Defender offboarding, offboarding
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
ms.openlocfilehash: 3fec93e45fbdced0cc6c4106d24a29eb13087d02
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66531050"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>Odłączanie urządzeń z usługi Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platformy**
- macOS
- Linux
- Windows Server 2012 R2
- System Windows Server 2016

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-offboarddevices-abovefoldlink)

Postępuj zgodnie z odpowiednimi instrukcjami w zależności od preferowanej metody wdrażania.

> [!NOTE]
> Stan urządzenia zostanie przełączony na [Nieaktywne](fix-unhealthy-sensors.md#inactive-devices) 7 dni po odłączeniu.
>
> Dane urządzeń odłączonych (takie jak oś czasu, alerty, luki w zabezpieczeniach itp.) pozostaną w portalu do momentu wygaśnięcia skonfigurowanego [okresu przechowywania](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) .
>
> Profil urządzenia (bez danych) pozostanie na [liście urządzeń](machines-view-overview.md) przez nie dłużej niż 180 dni.
>
> Ponadto urządzenia, które nie są aktywne w ciągu ostatnich 30 dni, nie są uwzględniane w danych, które odzwierciedlają [wskaźnik ekspozycji](tvm-exposure-score.md) Zarządzanie zagrożeniami i lukami organizacji i wskaźnik bezpieczeństwa firmy Microsoft dla urządzeń.
>
> Aby wyświetlić tylko aktywne urządzenia, można filtrować według [stanu kondycji czujnika](machines-view-overview.md#use-filters-to-customize-the-device-inventory-views), [tagów urządzeń](machine-tags.md) lub [grup maszyn](machine-groups.md).

## <a name="offboard-windows-devices"></a>Odłączanie urządzeń z systemem Windows

- [Odłączanie urządzeń przy użyciu skryptu lokalnego](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [Odłączanie urządzeń przy użyciu zasady grupy](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Odłączanie urządzeń przy użyciu narzędzi mobile Zarządzanie urządzeniami](configure-endpoints-mdm.md#offboard-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>Serwery odłączone

- [Serwery odłączone](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>Odłączanie urządzeń z systemem innym niż Windows

- [Odłączanie urządzeń z systemem innym niż Windows](configure-endpoints-non-windows.md#offboard-non-windows-devices)
