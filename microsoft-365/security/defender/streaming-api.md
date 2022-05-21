---
title: Przesyłanie strumieniowe zdarzeń Microsoft 365 Defender
description: Dowiedz się, jak skonfigurować Microsoft 365 Defender do przesyłania strumieniowego zdarzeń zaawansowanego wyszukiwania zagrożeń do usługi Event Hubs lub konta usługi Azure Storage
keywords: eksport danych pierwotnych, interfejs API przesyłania strumieniowego, interfejs API, centra zdarzeń, magazyn platformy Azure, konto magazynu, zaawansowane wyszukiwanie zagrożeń, nieprzetworzone udostępnianie danych
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
ms.openlocfilehash: d9f980656df636632c5903853c2784de81131d81
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621428"
---
# <a name="streaming-api"></a>Interfejs API przesyłania strumieniowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Przesyłanie strumieniowe zdarzeń zaawansowanego wyszukiwania zagrożeń do usługi Event Hubs i/lub konta usługi Azure Storage.

Microsoft 365 Defender obsługuje zdarzenia przesyłania strumieniowego za pośrednictwem [zaawansowanego wyszukiwania zagrożeń](../defender/advanced-hunting-overview.md) do usługi [Event Hubs](/azure/event-hubs/) i/lub [konta usługi Azure Storage](/azure/event-hubs/).

Aby uzyskać więcej informacji na temat Microsoft 365 Defender interfejsu API przesyłania strumieniowego, zobacz [wideo](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga).

## <a name="in-this-section"></a>W tej sekcji

Temat | Opis
:---|:---
[Przesyłanie strumieniowe zdarzeń do Azure Event Hubs](streaming-api-event-hub.md)| Dowiedz się więcej na temat włączania interfejsu API przesyłania strumieniowego w dzierżawie i konfigurowania Microsoft 365 Defender do przesyłania strumieniowego [zaawansowanego wyszukiwania zagrożeń](../defender/advanced-hunting-overview.md) do usługi Event Hubs.
[Przesyłanie strumieniowe zdarzeń do konta usługi Azure Storage](streaming-api-storage.md)| Dowiedz się więcej na temat włączania interfejsu API przesyłania strumieniowego w dzierżawie i konfigurowania Microsoft 365 Defender przesyłania strumieniowego [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md) do konta usługi Azure Storage.
[Obsługiwane typy zdarzeń](supported-event-types.md) | Dowiedz się, które zdarzenia zaawansowanego wyszukiwania zagrożeń są obsługiwane przez interfejs API przesyłania strumieniowego.

Obejrzyj ten krótki film wideo, aby dowiedzieć się, jak skonfigurować interfejs API przesyłania strumieniowego w celu dostarczania informacji o zdarzeniach bezpośrednio do usługi Azure Event Hubs w celu użycia przez usługi wizualizacji, aparaty przetwarzania danych lub magazyn platformy Azure na potrzeby długoterminowego przechowywania danych.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga]

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania zagrożeń](../defender/advanced-hunting-overview.md)
- [dokumentacja Azure Event Hubs](/azure/event-hubs/)
- [Dokumentacja konta usługi Azure Storage](/azure/storage/common/storage-account-overview)
