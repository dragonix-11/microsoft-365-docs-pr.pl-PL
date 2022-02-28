---
title: Microsoft 365 Defender strumieniowego przesyłania strumieniowego obsługiwane w interfejsie API przesyłania strumieniowego zdarzeń
description: Dowiedz się, które typy zdarzeń przesyłania strumieniowego (tabele) są obsługiwane przez interfejs API przesyłania strumieniowego
keywords: nieprzetworzone eksportowanie danych, interfejs API przesyłania strumieniowego, interfejs API, centra wydarzeń, magazyn platformy Azure, konto magazynu, czas pracy, pierwotne udostępnianie danych
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
ms.openlocfilehash: e8264ccb9e3181f6b58a6206417eb2b842bec6e7
ms.sourcegitcommit: 317fab13e84b2867087a6ba0a593313ecf43bbed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2021
ms.locfileid: "62988662"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Obsługiwane Microsoft 365 Defender zdarzeń przesyłania strumieniowego w interfejsie API przesyłania strumieniowego zdarzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


Interfejs API strumieniowego przesyłania zdarzeń jest stale rozszerzany w celu obsługi większej liczby typów zdarzeń. Dowiedz się, które tabele z programem Hunting są ogólnie dostępne, obecnie w podglądzie publicznym, lub nie są jeszcze obsługiwane. 
**Nowe — typy/tabele zdarzeń poczty e-mail są teraz ga**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Informacje o stanie obsługi tabel w interfejsie API przesyłania strumieniowego wydarzeń

W poniższej tabeli znajduje się tylko lista tabel obsługiwanych w interfejsie API przesyłania strumieniowego i nie zawiera wszystkich schematów AH. Aby uzyskać pełną listę interfejsu API, zobacz [Informacje o tabelach schematów](advanced-hunting-schema-tables.md#learn-the-schema-tables).


| Nazwa tabeli | Stan |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | GA |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | GA  |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |GA |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |GA |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | GA |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | GA |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | GA |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | GA |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |GA |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | GA |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | GA |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | GA |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | GA |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | GA |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | GA |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | GA |


