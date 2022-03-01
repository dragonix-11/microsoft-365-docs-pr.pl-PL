---
title: Modyfikowanie słownika słów kluczowych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak zmodyfikować słownik słów kluczowych w Centrum Microsoft 365 zgodności.
ms.openlocfilehash: acdf8b24aced21ed2f576fd57a3c685ef14debea
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009702"
---
# <a name="modify-a-keyword-dictionary"></a>Modyfikowanie słownika słów kluczowych

Może być konieczne zmodyfikowanie słów kluczowych w jednym ze słowników słów kluczowych lub zmodyfikowanie jednego z wbudowanych słowników. Możesz to zrobić za pomocą programu PowerShell lub Centrum zgodności.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>Modyfikowanie słownika słów kluczowych w Centrum zgodności

Słowniki słów kluczowych mogą być używane jako `Primary elements` wzorce `Supporting elements` informacji poufnych (SIT). Słownik słów kluczowych można edytować podczas tworzenia pliku SIT lub w istniejącym programie SIT. Aby na przykład edytować istniejący słownik słów kluczowych:

1. Otwórz wzorzec ze słownikiem słów kluczowych, który chcesz zaktualizować.
2. Znajdź słownik słów kluczowych, który chcesz zaktualizować, i wybierz pozycję edytuj.
3. Edytuj, używając jednego słowa kluczowego w wierszu.

   ![zrzut ekranu: edytowanie słów kluczowych.](../media/edit-keyword-dictionary.png)

4. Wybierz pozycję `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>Modyfikowanie słownika słów kluczowych przy użyciu programu PowerShell

Na przykład zmodyfikzemy niektóre terminy w programie PowerShell, zapiszemy terminy lokalnie, gdzie można je zmodyfikować w edytorze, a następnie zaktualizujemy poprzednie terminy w miejscu.

Najpierw pobierz obiekt słownika:

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

Podczas `$dict` drukowania będą wyświetlane różne właściwości. Same słowa kluczowe są przechowywane w obiekcie w zaplecza, `$dict.KeywordDictionary` ale zawierają postacie ich ciągów, których użyjesz do modyfikowania słownika.

Przed zmodyfikowaniem słownika należy przekształcić ciąg terminów z powrotem w tablicę przy użyciu tej `.split(',')` metody. Następnie oczyścisz niechciane spacje między `.trim()` słowami kluczowymi przy użyciu metody, pozostawiając tylko słowa kluczowe do pracy.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

Teraz usuniesz niektóre terminy ze słownika. Ponieważ słownik przykładowy zawiera tylko kilka słów kluczowych, możesz z łatwością przejść do eksportowania słownika i edytowania go w programie Notatnik, ale słowniki na ogół zawierają dużą ilość tekstu, więc najpierw dowiesz się, jak łatwo go edytować w programie PowerShell.

W ostatnim kroku zapisano słowa kluczowe w tablicy. Istnieje kilka sposobów usuwania elementów z tablicy [, ale](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10)) aby łatwo to zrobić, należy utworzyć tablicę terminów do usunięcia ze słownika, a następnie skopiować do niego tylko terminy słownika, których nie ma na liście terminów do usunięcia.

Uruchom polecenie, `$terms` aby wyświetlić bieżącą listę terminów. Wynik polecenia wygląda następująco:

```powershell
aarskog's syndrome
abandonment
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablatio
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

Uruchom to polecenie, aby określić terminy, które chcesz usunąć:

```powershell
$termsToRemove = @('abandonment','ablatio')
```

Uruchom to polecenie, aby faktycznie usunąć terminy z listy:

```powershell
$updatedTerms = $terms | Where-Object {$_ -notin $termsToRemove}
```

Uruchom polecenie, `$updatedTerms` aby wyświetlić zaktualizowaną listę terminów. Wynik polecenia wygląda następująco (określone terminy zostały usunięte):

```powershell
aarskog's syndrome
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

Teraz zapisz słownik lokalnie i dodaj jeszcze kilka terminów. Tutaj możesz dodać terminy w programie PowerShell, ale nadal musisz wyeksportować plik lokalnie, aby się upewnić, że jest on zapisywany przy użyciu kodowania Unicode i zawiera kodowanie BOM.

Zapisz słownik lokalnie, uruchamiając następujące czynności:

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

Teraz otwórz plik, dodaj inne terminy i zapisz go przy użyciu kodowania Unicode (UTF-16). Teraz przekażesz zaktualizowane terminy i zaktualizujesz słownik w miejscu.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

Teraz słownik został zaktualizowany. Pole `Identity` przyjmuje nazwę słownika. Jeśli chcesz również `Set-` zmienić nazwę słownika przy użyciu polecenia cmdlet, `-Name` wystarczy dodać parametr do powyższej listy z nową nazwą słownika.

## <a name="see-also"></a>Zobacz też

- [Tworzenie słownika słów kluczowych](create-a-keyword-dictionary.md)
- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
