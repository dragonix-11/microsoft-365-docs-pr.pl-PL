---
title: Nazewnictwo zmian w Microsoft 365 Defender zaawansowanego schematu wyszukiwania zagrożeń
description: Śledzenie i przeglądanie zmian nazewnictwa tabel i kolumn w zaawansowanym schemacie wyszukiwania zagrożeń
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagroże Microsoft 365 Defender ń, wyszukiwanie zagrożeń, dokumentacja schematu, kusto, tabela, dane, zmiany nazw, zmiana nazwy
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 4e58bb3d8c8cc7c507c4136abcabeb7e42b6827d
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731510"
---
# <a name="advanced-hunting-schema---naming-changes"></a>Zaawansowany schemat wyszukiwania zagrożeń — zmiany nazewnictwa

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Zaawansowany schemat wyszukiwania zagrożeń](advanced-hunting-schema-tables.md) jest regularnie aktualizowany w celu dodawania nowych tabel i kolumn. W niektórych przypadkach nazwy istniejących kolumn są zmieniane lub zastępowane w celu ulepszenia środowiska użytkownika. Zapoznaj się z tym artykułem, aby przejrzeć zmiany nazewnictwa, które mogą mieć wpływ na zapytania.

Zmiany nazewnictwa są automatycznie stosowane do zapytań zapisanych w Defender dla Chmury, w tym zapytań używanych przez niestandardowe reguły wykrywania. Nie musisz aktualizować tych zapytań ręcznie. Należy jednak zaktualizować następujące zapytania:
- Zapytania uruchamiane przy użyciu interfejsu API
- Zapytania zapisane w innym miejscu poza Defender dla Chmury

## <a name="december-2020"></a>Grudzień 2020

| Nazwa tabeli | Oryginalna nazwa kolumny | Nowa nazwa kolumny | Powód zmiany
|--|--|--|--|
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailAction` | `EmailAction` | Opinie klientów |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicy` | `EmailActionPolicy` | Opinie klientów |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicyGuid` | `EmailActionPolicyGuid` | Opinie klientów |

## <a name="january-2021"></a>Styczeń 2021

| Nazwa kolumny | Oryginalna nazwa wartości | Nowa nazwa wartości | Powód zmiany
|--|--|--|--|
| `DetectionSource` | Defender for Cloud Apps | Microsoft Defender for Cloud Apps | Rebranding |
| `DetectionSource` | WindowsDefenderAtp| EDR| Rebranding |
| `DetectionSource` | WindowsDefenderAv | Antivirus | Rebranding |
| `DetectionSource` | WindowsDefenderSmartScreen |  Filtr smartscreen | Rebranding |
| `DetectionSource` | CustomerTI | Niestandardowy identyfikator TI | Rebranding |
| `DetectionSource` | OfficeATP | Ochrona usługi Office 365 w usłudze Microsoft Defender | Rebranding |
| `DetectionSource` | MTP | Microsoft 365 Defender | Rebranding |
| `DetectionSource` | AzureATP | Microsoft Defender for Identity | Rebranding |
| `DetectionSource` | CustomDetection | Wykrywanie niestandardowe | Rebranding |
| `DetectionSource` | AutomatedInvestigation |Zautomatyzowane badanie | Rebranding |
| `DetectionSource` | ThreatExperts | Microsoft Threat Experts | Rebranding |
| `DetectionSource` | TI innej firmy | Czujniki innych firm | Rebranding |
| `ServiceSource` | Microsoft Defender ATP| Ochrona punktu końcowego w usłudze Microsoft Defender | Rebranding |
|`ServiceSource` |Microsoft Threat Protection | Microsoft 365 Defender | Rebranding |
| `ServiceSource` | Office 365 ATP |Ochrona usługi Office 365 w usłudze Microsoft Defender | Rebranding |
| `ServiceSource` |Azure ATP |Microsoft Defender for Identity | Rebranding |

`DetectionSource` jest dostępna w tabeli [AlertInfo](advanced-hunting-alertinfo-table.md) . `ServiceSource` jest dostępna w tabelach [AlertEvidence](advanced-hunting-alertevidence-table.md) i [AlertInfo](advanced-hunting-alertinfo-table.md) . 

## <a name="february-2021"></a>Luty 2021 r.

1. W tabelach `MalwareFilterVerdict`[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) i [EmailEvents](advanced-hunting-emailevents-table.md) kolumny i `PhishFilterVerdict` zostały zastąpione kolumną`ThreatTypes`. Kolumny `MalwareDetectionMethod` i `PhishDetectionMethod` zostały również zastąpione kolumną `DetectionMethods` . Dzięki temu możemy udostępnić więcej informacji w nowych kolumnach. Poniżej przedstawiono mapowanie.

    | Nazwa tabeli | Oryginalna nazwa kolumny | Nowa nazwa kolumny | Powód zmiany
    |--|--|--|--|
    | `EmailAttachmentInfo` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Uwzględnij więcej metod wykrywania |
    | `EmailAttachmentInfo`  | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Uwzględnij więcej typów zagrożeń |
    | `EmailEvents` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Uwzględnij więcej metod wykrywania |
    | `EmailEvents` | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Uwzględnij więcej typów zagrożeń |


2. W tabelach `EmailAttachmentInfo` i `EmailEvents` kolumna `ThreatNames` została dodana, aby uzyskać więcej informacji na temat zagrożenia wiadomości e-mail. Ta kolumna zawiera wartości takie jak Spam lub Phish.

3. W tabeli [DeviceInfo](advanced-hunting-deviceinfo-table.md) kolumna `DeviceObjectId` została zastąpiona kolumną `AadDeviceId` na podstawie opinii klientów.

4. W tabeli [DeviceEvents](advanced-hunting-deviceevents-table.md) zmodyfikowano kilka nazw ActionType, aby lepiej odzwierciedlić opis akcji. Szczegóły zmian można znaleźć poniżej.

    | Nazwa tabeli | Oryginalna nazwa actiontype | Nowa nazwa actiontype | Powód zmiany
    |--|--|--|--|
    | `DeviceEvents` | `DlpPocPrintJob` | `FilePrinted` | Opinie klientów |
    | `DeviceEvents` | `UsbDriveMount` | `UsbDriveMounted` | Opinie klientów |
    | `DeviceEvents` | `UsbDriveUnmount` | `UsbDriveUnmounted` | Opinie klientów |
    | `DeviceEvents` | `WriteProcessMemoryApiCall` | `WriteToLsassProcessMemory` | Opinie klientów |

## <a name="march-2021"></a>Marzec 2021 r.

Tabela `DeviceTvmSoftwareInventoryVulnerabilities` została przestarzała. Zastępowanie go to tabele `DeviceTvmSoftwareInventory` i `DeviceTvmSoftwareVulnerabilities` .

## <a name="may-2021"></a>Maj 2021

Tabela `AppFileEvents` została przestarzała. Tabela `CloudAppEvents` zawiera informacje, które były używane w `AppFileEvents` tabeli, wraz z innymi działaniami w usługach w chmurze.

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
