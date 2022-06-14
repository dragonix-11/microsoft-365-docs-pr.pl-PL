---
title: Microsoft 365 Defender typy zdarzeń przesyłania strumieniowego obsługiwane w interfejsie API przesyłania strumieniowego zdarzeń
description: Dowiedz się, które typy zdarzeń przesyłania strumieniowego (tabele) są obsługiwane przez interfejs API przesyłania strumieniowego
keywords: eksport danych pierwotnych, interfejs API przesyłania strumieniowego, interfejs API, centra zdarzeń, magazyn platformy Azure, konto magazynu, wyszukiwanie zagrożeń, udostępnianie danych pierwotnych
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
ms.openlocfilehash: 4f6f098c9d2ec09a777110955b8acb1663e102ed
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057856"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Obsługiwane typy zdarzeń przesyłania strumieniowego Microsoft 365 Defender w interfejsie API przesyłania strumieniowego zdarzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


Interfejs API przesyłania strumieniowego zdarzeń jest stale rozwijany w celu obsługi większej liczby typów zdarzeń. Dowiedz się, które tabele wyszukiwania zagrożeń są ogólnie dostępne, obecnie w publicznej wersji zapoznawczej lub nie są jeszcze obsługiwane. 
**Nowe — typy/tabele zdarzeń poczty e-mail są teraz ogólnie dostępne**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Tabele wyszukiwania zagrożeń obsługują stan w interfejsie API przesyłania strumieniowego zdarzeń

Poniższa tabela zawiera tylko listę tabel obsługiwanych w interfejsie API przesyłania strumieniowego i nie obejmuje całego schematu AH. Aby uzyskać pełną listę interfejsu API, zobacz [Informacje o tabelach schematów](advanced-hunting-schema-tables.md#learn-the-schema-tables).

| Nazwa tabeli | Stan<br>(Komercyjne) | GCC | GCC wysoki | DoD |
|----|----|----|----|----|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | GA | GA | GA | GA |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |GA | GA | GA | GA |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |GA | GA | GA | GA |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | GA | GA | GA | GA |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | GA | GA | GA | GA |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | GA | GA | GA | GA |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |GA | GA | GA | GA |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | GA | GA | GA | GA |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | GA | GA | GA | GA |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | GA |![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | GA |![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | GA |![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | GA |![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)**|GA|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)**|GA|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)**|GA|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)**|GA|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|![Nie](../defender-endpoint/images/svg/check-no.svg)|
