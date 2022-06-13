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
ms.openlocfilehash: deb50679702cec69187392337511b4dde2d1ceb3
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014393"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>Modyfikowanie niestandardowego typu informacji poufnych przy użyciu programu PowerShell

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W programie PowerShell security & Compliance modyfikowanie niestandardowego typu informacji poufnych wymaga:

1. Wyeksportuj istniejący pakiet reguł zawierający niestandardowy typ informacji poufnych do pliku XML (lub użyj istniejącego pliku XML, jeśli go masz).

2. Zmodyfikuj niestandardowy typ informacji poufnych w wyeksportowanym pliku XML.

3. Zaimportuj zaktualizowany plik XML z powrotem do istniejącego pakietu reguł.

Aby nawiązać połączenie z programem PowerShell & Zgodności z zabezpieczeniami, zobacz [Security & Compliance PowerShell .Security & Compliance PowerShell (Zabezpieczenia & zgodności z programem PowerShell](/powershell/exchange/exchange-online-powershell)).

## <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>Krok 1. Eksportowanie istniejącego pakietu reguł do pliku XML

> [!NOTE]
> Jeśli masz kopię pliku XML (na przykład właśnie go utworzono i zaimportowano), możesz przejść do następnego kroku, aby zmodyfikować plik XML.

1. Jeśli jeszcze tego nie wiesz, uruchom polecenie cmdlet [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtype) , aby znaleźć nazwę niestandardowego pakietu reguł:

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > Wbudowany pakiet reguł zawierający wbudowane typy informacji poufnych nosi nazwę Microsoft Rule Package. Pakiet reguł zawierający niestandardowe typy informacji poufnych utworzone w interfejsie użytkownika Centrum zgodności nosi nazwę Microsoft.SCCManaged.CustomRulePack.

2. Użyj polecenia cmdlet [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) , aby przechowywać niestandardowy pakiet reguł w zmiennej:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   Jeśli na przykład nazwa pakietu reguł to "Employee ID Custom Rule Pack", uruchom następujące polecenie cmdlet:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. Użyj następującej składni, aby wyeksportować niestandardowy pakiet reguł do pliku XML:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   Ten przykład eksportuje pakiet reguł do pliku o nazwie ExportedRulePackage.xml w folderze C:\My Documents.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

## <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>Krok 2. Modyfikowanie typu informacji poufnych w wyeksportowanym pliku XML

Typy informacji poufnych w pliku XML i inne elementy w pliku zostały opisane wcześniej w tym temacie.

## <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>Krok 3. Importowanie zaktualizowanego pliku XML z powrotem do istniejącego pakietu reguł

Aby zaimportować zaktualizowany kod XML z powrotem do istniejącego pakietu reguł, użyj polecenia cmdlet [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) :

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>Więcej informacji

- [Dowiedz się więcej o zapobieganiu utracie danych w usłudze Microsoft Purview](dlp-learn-about-dlp.md)
- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Funkcje typu informacji poufnych](sit-functions.md)
