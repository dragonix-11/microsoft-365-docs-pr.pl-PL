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
ms.openlocfilehash: 852f9987b072f05dcf4f322f600bed23bcce7ef2
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014917"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>Usuwanie niestandardowego typu informacji poufnych przy użyciu programu PowerShell

W Centrum zgodności programu PowerShell istnieją dwie metody usuwania niestandardowych typów informacji poufnych:

- **Usuwanie poszczególnych niestandardowych typów informacji poufnych**: Użyj metody udokumentowanej w tece Modyfikowanie niestandardowego typu informacji [poufnych przy użyciu programu PowerShell](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell). Eksportujesz niestandardowy pakiet reguł zawierający niestandardowy typ informacji poufnych, usuwasz typ informacji poufnych z pliku XML i importujesz zaktualizowany plik XML z powrotem do istniejącego pakietu reguł niestandardowych.

- **Usuń niestandardowy pakiet reguł i wszystkie niestandardowe** typy informacji poufnych, które zawiera: Ta metoda została udokumentowana w tej sekcji.

> [!NOTE]
> Przed usunięciem niestandardowego typu informacji poufnych upewnij się, że żadne zasady DLP Exchange przepływu poczty e-mail (nazywane także regułami transportu) nadal odwołują się do typu informacji poufnych.

1. [Połączenie do Centrum zgodności w programie PowerShell](/powershell/exchange/exchange-online-powershell)

2. Aby usunąć niestandardowy pakiet reguł, użyj polecenia cmdlet [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) :

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   Do identyfikowania pakietu reguł można użyć wartości Name (Nazwa) (dla dowolnego języka) `RulePack id` lub wartości (GUID).

   W tym przykładzie usuwany jest pakiet reguł o nazwie "Niestandardowy pakiet reguł identyfikatorów pracowników".

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. Aby sprawdzić, czy niestandardowy typ informacji poufnych został pomyślnie usunięty, wykonaj dowolną z następujących czynności:

   - Uruchom polecenie [cmdlet Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) i sprawdź, czy pakiet reguł nie jest już wymieniony:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Uruchom polecenie [cmdlet Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) , aby sprawdzić, czy typy poufnych informacji w usuniętym pakiecie reguł nie są już wymienione:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     W przypadku niestandardowych typów informacji poufnych Publisher wartość właściwości będzie inna niż wartość firmy Microsoft Corporation.

   - Zamień \<Name\> na wartość Name (Nazwa) typu informacji poufnych (na przykład Identyfikator pracownika) i uruchom polecenie cmdlet [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) , aby sprawdzić, czy typ informacji poufnych nie jest już wymieniony:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>Więcej informacji

- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)

- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)

- [Funkcje typów informacji poufnych](sit-functions.md)
