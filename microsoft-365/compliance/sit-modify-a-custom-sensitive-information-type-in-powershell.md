---
title: Modyfikowanie niestandardowego typu informacji poufnych przy użyciu programu PowerShell
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak zmodyfikować niestandardowe informacje poufne przy użyciu programu PowerShell.
ms.openlocfilehash: 2f1bc44dca9ec4a938c8cd3d4158163f9d5e2e2f
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014893"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>Modyfikowanie niestandardowego typu informacji poufnych przy użyciu programu PowerShell

W centrum zgodności programu PowerShell modyfikowanie niestandardowego typu informacji poufnych wymaga:

1. Wyeksportuj istniejący pakiet reguł zawierający niestandardowy typ informacji poufnych do pliku XML (lub użyj istniejącego pliku XML, jeśli go masz).

2. Zmodyfikuj niestandardowy typ informacji poufnych w wyeksportowanych plikach XML.

3. Zaimportuj zaktualizowany plik XML z powrotem do istniejącego pakietu reguł.

Aby nawiązać połączenie z centrum zgodności w programie PowerShell, Połączenie [się z Centrum zgodności w programie PowerShell](/powershell/exchange/exchange-online-powershell).

### <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>Krok 1. Eksportowanie istniejącego pakietu reguł do pliku XML

> [!NOTE]
> Jeśli masz kopię pliku XML (na przykład plik został właśnie utworzony i zaimportowany), możesz przejść do następnego kroku w celu zmodyfikowania pliku XML.

1. Jeśli jeszcze tego nie wiesz, uruchom polecenie cmdlet [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtype) , aby znaleźć nazwę niestandardowego pakietu reguł:

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > Wbudowany pakiet reguł, który zawiera wbudowane typy informacji poufnych, nosi nazwę Pakiet reguł firmy Microsoft. Pakiet reguł zawierający niestandardowe typy informacji poufnych utworzony w centrum zgodności ma nazwę Microsoft.SCCManaged.CustomRulePack.

2. Użyj polecenia [cmdlet Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) do przechowywania niestandardowego pakietu reguł do zmiennej:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   Jeśli na przykład nazwa pakietu reguł to "Niestandardowy pakiet reguł identyfikatora pracownika", uruchom następujące polecenie cmdlet:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. Aby wyeksportować niestandardowy pakiet reguł do pliku XML, użyj następującej składni:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   W tym przykładzie pakiet reguł jest eksportowany do pliku o nazwie ExportedRulePackage.xml w folderze C:\Moje dokumenty.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

#### <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>Krok 2. Modyfikowanie typu informacji poufnych w wyeksportowanych plikach XML

Typy informacji poufnych w pliku XML i inne elementy w pliku zostały opisane wcześniej w tym temacie.

#### <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>Krok 3. Importowanie zaktualizowanego pliku XML z powrotem do istniejącego pakietu reguł

Aby zaimportować zaktualizowany kod XML z powrotem do istniejącego pakietu reguł, użyj polecenia cmdlet [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) :

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>Więcej informacji

- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Funkcje typów informacji poufnych](sit-functions.md)
