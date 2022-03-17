---
title: Eksportowanie i importowanie modeli opisowych dokumentów za pomocą programu PowerShell
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: medium
description: Dowiedz się, jak eksportować i importować modele opisowe dokumentów za pomocą programu PowerShell w programie SharePoint Syntex.
ms.openlocfilehash: dc35d298ebd79752684c91ce944333277fcef621
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63527008"
---
# <a name="export-and-import-document-understanding-models-with-powershell"></a>Eksportowanie i importowanie modeli opisowych dokumentów za pomocą programu PowerShell

> [!IMPORTANT]
> Polecenia SharePoint Syntex programu PowerShell i wszystkie inne składniki PnP to narzędzia typu open source, których źródłem jest aktywna społeczność zapewniająca ich pomoc techniczną. Nie ma umowy SLA dotyczącej wsparcia narzędzia open source z oficjalnych kanałów pomocy technicznej firmy Microsoft.

SharePoint Syntex można eksportować jako szablonyPnP, co umożliwia ponowne używanie w centrach zawartości lub dzierżawach.

## <a name="export-all-models-in-a-content-center"></a>Eksportowanie wszystkich modeli w centrum zawartości

Aby wyeksportować wszystkie modele w centrum zawartości do jednego szablonu PnP, użyj następujących poleceń [cmdlet programu PnP PowerShell](https://pnp.github.io/powershell/) :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Handlers SyntexModels
```

## <a name="export-specific-models"></a>Eksportowanie określonych modeli

Aby wyeksportować określone modele z centrum zawartości do szablonu programu PnP, użyj następujących poleceń [cmdlet programu PnP PowerShell](https://pnp.github.io/powershell/) :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Configuration .\extract.json
```

Wartość extract.json określa modele do wyeksportowania, pozwalając na określanie modelu według nazwy lub identyfikatora i opcjonalne skonfigurowanie w celu nie wyodrębniania danych szkoleniowych.

### <a name="example---specify-model-by-name"></a>Przykład — określanie modelu według nazwy

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "name": "Sample - benefits change notice.classifier"
            }
        ]
    }
}
```

### <a name="example---specify-model-by-id"></a>Przykład — określanie modelu według identyfikatora

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "id": 3,
                "excludeTrainingData": true
            }
        ]
    }
}
```

Jeśli nie uwzględnisz właściwości "includeTrainingData", zachowaniem domyślnym będzie uwzględnianie.

> [!NOTE]
> Aby model można było edytować po zaimportowaniu do docelowego centrum zawartości, wymagane są dane szkoleniowe.

## <a name="import-models-to-a-content-center"></a>Importowanie modeli do centrum zawartości
Dokument opisowy modele, które zostały wyeksportowane do szablonówPnP, można zaimportować do centrum zawartości w dowolnej dzierżawie. Jeśli podczas eksportowania uwzględniono dane szkoleniowe, model będzie można edytować po zaimportowaniu.

Aby zaimportować model, użyj następujących poleceń:

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Invoke-PnPSiteTemplate -Path .\sampleModel.pnp
```
