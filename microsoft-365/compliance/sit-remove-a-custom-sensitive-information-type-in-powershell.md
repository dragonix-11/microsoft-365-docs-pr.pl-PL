---
title: Usuwanie niestandardowego typu informacji poufnych przy użyciu programu PowerShell
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
description: Dowiedz się, jak usunąć niestandardowy typ informacji poufnych przy użyciu programu PowerShell
ms.openlocfilehash: e935c9340c353561e71e25fdadfec5509da041e5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014745"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>Usuwanie niestandardowego typu informacji poufnych przy użyciu programu PowerShell

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W programie PowerShell security & Compliance istnieją dwie metody usuwania niestandardowych typów informacji poufnych:

- **Usuń poszczególne niestandardowe typy informacji poufnych**: użyj metody udokumentowanej w [artykule Modyfikowanie niestandardowego typu informacji poufnych przy użyciu programu PowerShell](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell). Można wyeksportować niestandardowy pakiet reguł zawierający niestandardowy typ informacji poufnych, usunąć typ informacji poufnych z pliku XML i zaimportować zaktualizowany plik XML z powrotem do istniejącego pakietu reguł niestandardowych.

- **Usuń niestandardowy pakiet reguł i wszystkie niestandardowe typy informacji poufnych, które zawiera**: Ta metoda jest udokumentowana w tej sekcji.

> [!NOTE]
> Przed usunięciem niestandardowego typu informacji poufnych sprawdź, czy żadne zasady DLP ani reguły przepływu poczty Exchange (nazywane również regułami transportu) nie odwołują się do typu informacji poufnych.

1. [Zgodność & zabezpieczeń w programie PowerShell](/powershell/exchange/exchange-online-powershell)

2. Aby usunąć niestandardowy pakiet reguł, użyj polecenia cmdlet [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) :

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   Aby zidentyfikować pakiet reguł, możesz użyć wartości Nazwa (dla dowolnego języka) lub `RulePack id` (IDENTYFIKATOR GUID).

   W tym przykładzie usunięto pakiet reguł o nazwie "Pakiet reguł niestandardowych identyfikatora pracownika".

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. Aby sprawdzić, czy typ niestandardowych informacji poufnych został pomyślnie usunięty, wykonaj dowolne z następujących kroków:

   - Uruchom polecenie cmdlet [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) i sprawdź, czy pakiet reguł nie znajduje się już na liście:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Uruchom polecenie cmdlet [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) , aby sprawdzić, czy typy informacji poufnych w usuniętym pakiecie reguł nie są już wyświetlane:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     W przypadku niestandardowych typów informacji poufnych wartość właściwości Publisher będzie inna niż Microsoft Corporation.

   - Zastąp \<Name\> ciąg wartością Nazwa typu informacji poufnych (na przykład Identyfikator pracownika) i uruchom polecenie cmdlet [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) , aby sprawdzić, czy typ informacji poufnych nie jest już wyświetlany:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>Więcej informacji

- [Dowiedz się więcej o zapobieganiu utracie danych w usłudze Microsoft Purview](dlp-learn-about-dlp.md)

- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)

- [Funkcje typu informacji poufnych](sit-functions.md)
