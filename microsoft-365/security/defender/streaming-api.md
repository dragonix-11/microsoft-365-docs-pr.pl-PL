---
title: Przesyłanie strumieniowe Microsoft 365 Defender zdarzeń
description: Dowiedz się, jak skonfigurować usługę Microsoft 365 Defender przesyłania strumieniowego wydarzeń zaawansowanego chłonia do centrum wydarzeń lub konta magazynu platformy Azure
keywords: nieprzetworzone eksportowanie danych, interfejs API przesyłania strumieniowego, interfejs API, koncentratory wydarzeń, magazyn platformy Azure, konto magazynu, zaawansowane szukanie, pierwotne udostępnianie danych
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c6c3cedffb1b827d441d37cc8beb53b20f3521f2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984944"
---
# <a name="streaming-api"></a>Interfejs API przesyłania strumieniowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Przesyłaj strumieniowo zaawansowane wydarzenia łęgowe do centrum wydarzeń i/lub do konta magazynu platformy Azure.

Microsoft 365 Defender obsługuje przesyłanie strumieniowe wydarzeń za pośrednictwem [zaawansowanego](../defender/advanced-hunting-overview.md) wyszukiwania do centrum [wydarzeń i/](/azure/event-hubs/)lub konta [magazynu platformy Azure](/azure/event-hubs/).

Aby uzyskać więcej informacji na Microsoft 365 Defender interfejsu API przesyłania strumieniowego, zobacz [klip wideo](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga).

## <a name="in-this-section"></a>W tej sekcji

Temat | Opis
:---|:---
[Przesyłanie strumieniowe wydarzeń do Centrum zdarzeń Azure](streaming-api-event-hub.md)| Dowiedz się więcej o włączaniu interfejsu API przesyłania strumieniowego w dzierżawie i Microsoft 365 Defender [strumieniowego wyszukiwania zaawansowanego](../defender/advanced-hunting-overview.md) do centrum wydarzeń.
[Przesyłanie strumieniowe zdarzeń do konta magazynu platformy Azure](streaming-api-storage.md)| Dowiedz się więcej o włączaniu interfejsu API przesyłania strumieniowego w dzierżawie i Microsoft 365 Defender [strumieniowego wyszukiwania zaawansowanego](advanced-hunting-overview.md) do konta magazynu platformy Azure.
[Obsługiwane typy zdarzeń](supported-event-types.md) | Dowiedz się, jakie typy zaawansowanych wydarzeń łowiectwo są obsługujące interfejs API przesyłania strumieniowego.


## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie wyszukiwania zaawansowanego](../defender/advanced-hunting-overview.md)
- [Dokumentacja centrum wydarzeń azure](/azure/event-hubs/)
- [Dokumentacja Storage konta usługi Azure](/azure/storage/common/storage-account-overview)
