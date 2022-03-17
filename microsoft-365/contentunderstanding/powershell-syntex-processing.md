---
title: Żądanie przetworzenia przez model zrozumienia dokumentu za pomocą programu PowerShell
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
description: Dowiedz się, jak za pomocą programu PowerShell zażądać przetwarzania przez SharePoint Syntex opisowego dokumentu.
ms.openlocfilehash: 8f66a0cc5e59ad2ccb6b92d98cfaee8ce84470f2
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526446"
---
# <a name="use-powershell-to-request-processing-by-a-document-understanding-model"></a>Żądanie przetworzenia przez model zrozumienia dokumentu za pomocą programu PowerShell

> [!IMPORTANT]
> Polecenia SharePoint Syntex programu PowerShell i wszystkie inne składniki PnP to narzędzia typu open source, których źródłem jest aktywna społeczność zapewniająca ich pomoc techniczną. Nie ma umowy SLA dotyczącej wsparcia narzędzia open source z oficjalnych kanałów pomocy technicznej firmy Microsoft.

Dokument opisowy modele będą przetwarzać nowo przekazane pliki do biblioteki. Można również ręcznie zażądać przetwarzania w interfejsie użytkownika. Mogą jednak wystąpić sytuacje, w których bardziej wydajne jest wyzwalanie przetwarzania za pomocą programu PowerShell.

## <a name="request-processing-of-all-items-that-have-not-been-previously-classified"></a>Żądanie przetworzenia wszystkich elementów, które nie były wcześniej klasyfikowane

Możesz zażądać przetworzenia wszystkich elementów w bibliotece, które nie były wcześniej klasyfikowane, przy użyciu tego polecenia:

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents"
```

W przypadku przetwarzania o niższym priorytecie możesz również rozważyć użycie parametru -OffPeak, który spowoduje kolejkowanie plików do przetworzenia poza godzinami pracy, w których znajduje się dzierżawa. Aby [uzyskać więcej szczegółowych informacji, zobacz Request-PnPSyntexClassifyAndExtract](https://pnp.github.io/powershell/cmdlets/Request-PnPSyntexClassifyAndExtract.html) .

## <a name="request-processing-of-all-items-in-a-library"></a>Żądanie przetworzenia wszystkich elementów w bibliotece

Możesz zażądać przetwarzania wszystkich plików w bibliotece, nawet jeśli zostały one wcześniej sklasyfikowane. Może to być przydatne, jeśli zaktualizowano model lub dodano inny model do biblioteki.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents" -Force
```

> [!NOTE]
> Użycie opcji -Force z ponad 5000 elementami spowoduje automatyczne wyłączenie przetwarzania szczytowego.

## <a name="request-processing-of-all-items-based-on-a-property"></a>Żądanie przetworzenia wszystkich elementów na podstawie właściwości

Jeśli chcesz ograniczyć przetwarzanie do określonego podzestawu elementów w bibliotece, możesz użyć skryptu do wybrania określonej grupy plików. W poniższym przykładzie skrypt umożliwia wybranie pola, a następnie filtrowanie wartości pola. Bardziej złożone zapytania można wypełnić przy użyciu narzędzia [Get-PnPListItem](https://pnp.github.io/powershell/cmdlets/Get-PnPListItem.html).

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"
$list = Get-PnPList -Identity "Documents"
# Set the field name to filter items by
$fieldName = "Vendor"
# Set the field value to filter by
$fieldFilter = "Fabrikam"

$listItems = (Get-PnPListItem -List $list -fields $fieldName).fieldValues
$targetItems = $listItems | Where-Object -Property Provider -EQ -Value $fieldFilter

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
foreach ($listItem in $targetItems) {
    Request-PnPSyntexClassifyAndExtract -FileUrl $listItem.FileRef -Batch $classifyBatch
}

# Execute batch
Invoke-PnPBatch -Batch $batch
```

## <a name="request-processing-of-specific-files"></a>Żądanie przetworzenia określonych plików

Można również zażądać przetwarzania określonych plików.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx"
```

Plik według modelu plików obsługuje również wsady:

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx" -Batch $batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/relecloud contract.docx" -Batch $batch

# Execute batch
Invoke-PnPBatch -Batch $batch
```
