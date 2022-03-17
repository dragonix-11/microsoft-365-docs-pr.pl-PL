---
title: Publikowanie dokumentu opisowego modeli za pomocą programu PowerShell
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
description: Dowiedz się, jak opublikować dokument SharePoint Syntex opis modeli za pomocą programu PowerShell.
ms.openlocfilehash: 5169e5ea5839cd5c341baa2477fd82281f5e5d76
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526488"
---
# <a name="publish-document-understanding-models-with-powershell"></a>Publikowanie dokumentu opisowego modeli za pomocą programu PowerShell

> [!IMPORTANT]
> Polecenia SharePoint Syntex programu PowerShell i wszystkie inne składniki PnP to narzędzia typu open source, których źródłem jest aktywna społeczność zapewniająca ich pomoc techniczną. Nie ma umowy SLA dotyczącej wsparcia narzędzia open source z oficjalnych kanałów pomocy technicznej firmy Microsoft.

SharePoint Syntex są zazwyczaj wdrażane w bibliotekach dokumentów w całej dzierżawie. Można to zrobić za pomocą witryny centrum zawartości, ale można to również zrobić przy użyciu programu [PnP PowerShell](https://pnp.github.io/powershell/) , co wyjaśniono w tym artykule.

## <a name="listing-the-available-models-in-a-content-center"></a>Wyświetlanie listy dostępnych modeli w centrum zawartości

Aby uzyskać przegląd modeli dodanych do bieżącej witryny centrum SharePoint Syntex zawartości, użyj polecenia cmdlet [Get-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModel.html):

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModel
```

## <a name="apply-a-model-to-a-library"></a>Stosowanie modelu do biblioteki

Aby zastosować model do biblioteki, użyj polecenia cmdlet [Publish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Publish-PnPSyntexModel.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Publish-PnPSyntexModel -Model "Contract Notice" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="understanding-where-a-model-is-used"></a>Opis miejsca, w którym jest używany model

Po wdrożeniu modelu w wielu bibliotekach warto przejrzeć listę bibliotek przy użyciu modelu. Można to zrobić za pomocą [polecenia cmdlet Get-PnPSyntexModelPublication](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModelPublication.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModelPublication -Identity "Contract Notice"
```

## <a name="removing-a-model-from-a-library"></a>Usuwanie modelu z biblioteki

Usuwanie modelu z biblioteki odbywa się zgodnie z tym samym wzorcem co stosowanie i można to zrobić za pomocą polecenia cmdlet [Unpublish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Unpublish-PnPSyntexModel.html) (interakcyjnego) lub jako partii wielu akcji.

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourSite"
Unpublish-PnPSyntexModel -Model "Invoice model" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="apply-models-in-bulk"></a>Zbiorcze stosowanie modeli

Jeśli chcesz opublikować wiele modeli w wielu bibliotekach, utwórz plik wejściowy CSV zawierający listę modeli i lokalizacji docelowych:

```CSV
ModelName,TargetSiteUrl,TargetWebServerRelativeUrl,TargetLibraryServerRelativeUrl
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/shared%20documents
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/other
Trade Confirmation,https://contoso.sharepoint.com/sites/Site2,/sites/Site2,/sites/site2/shared%20documents
```

Tego pliku CSV można następnie użyć jako danych wejściowych w skrypcie, który opublikuje wymienione modele w odpowiednich bibliotekach. W poniższym przykładzie wsadowanie jest używane w celu zwiększenia wydajności żądań.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourSite"
$targetsCSV = "./Publish-SyntexModelBulk.csv"

Connect-PnPOnline -url $contentCenterURL

$targetLibraries = Import-Csv -Path $targetsCSV

$batch = New-PnPBatch

foreach ($target in $targetLibraries) {
    Publish-PnPSyntexModel -Model $target.ModelName -TargetSiteUrl $target.TargetSiteUrl -TargetWebServerRelativeUrl $target.TargetWebServerRelativeUrl -TargetLibraryServerRelativeUrl $target.TargetLibraryServerRelativeUrl -Batch $batch
}

Invoke-PnPBatch -Batch $batch
```
