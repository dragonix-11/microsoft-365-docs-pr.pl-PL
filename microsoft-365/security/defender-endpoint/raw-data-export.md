---
title: Streamowanie zdarzenia Programu Microsoft Defender dla punktu końcowego
description: Dowiedz się, jak skonfigurować usługę Microsoft Defender dla punktu końcowego w celu przesyłania strumieniowego wydarzeń zaawansowanego chłonia do centrum wydarzeń lub konta magazynu platformy Azure
keywords: nieprzetworzone eksportowanie danych, interfejs API przesyłania strumieniowego, interfejs API, koncentratory wydarzeń, magazyn platformy Azure, konto magazynu, zaawansowane szukanie, pierwotne udostępnianie danych
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
ms.custom: api
ms.openlocfilehash: 94a815a6fc734c8e8e310a17f2e73931f4ffab5c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996263"
---
# <a name="raw-data-streaming-api"></a>Interfejs API nieprzetworzonego przesyłania strumieniowego danych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Przesyłanie strumieniowe zaawansowanych wydarzeń chłonianych do centrum wydarzeń i/lub konta magazynu platformy Azure

Program Microsoft Defender for Endpoint obsługuje przesyłanie strumieniowe wydarzeń dostępnych za pośrednictwem [zaawansowanego](../defender/advanced-hunting-overview.md) wyszukiwania do centrum [wydarzeń i/](/azure/event-hubs/) lub konta [magazynu platformy Azure](/azure/storage/common/storage-account-overview).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4ga]

## <a name="in-this-section"></a>W tej sekcji

Temat|Opis
:---|:---
[Przesyłanie strumieniowe usługi Microsoft Defender dla zdarzeń punktu końcowego do centrum zdarzeń platformy Azure](raw-data-export-event-hub.md)|Dowiedz się więcej na temat włączania interfejsu API przesyłania strumieniowego w dzierżawie i konfigurowania usługi Defender for Endpoint w celu przesyłania strumieniowego [zaawansowanego](advanced-hunting-overview.md) wyszukiwania do centrum wydarzeń.
[Stream Defender for Endpoint events to your Azure storage account](raw-data-export-storage.md)|Dowiedz się więcej o włączaniu interfejsu API przesyłania strumieniowego w dzierżawie i konfigurowaniu usługi Defender for Endpoint w celu przesyłania strumieniowego [zaawansowanego](advanced-hunting-overview.md) wyszukiwania do konta magazynu platformy Azure.

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie wyszukiwania zaawansowanego](advanced-hunting-overview.md)
- [Dokumentacja centrum wydarzeń azure](/azure/event-hubs/)
- [Dokumentacja Storage konta usługi Azure](/azure/storage/common/storage-account-overview)