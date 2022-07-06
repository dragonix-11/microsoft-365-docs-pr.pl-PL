---
title: Modyfikuj słownik słów kluczowych
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
description: Dowiedz się, jak zmodyfikować słownik słów kluczowych w portal zgodności Microsoft Purview.
ms.openlocfilehash: 8b2f2256be506f0ba01dc059bf0ac54e84c481c9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621716"
---
# <a name="modify-a-keyword-dictionary"></a>Modyfikuj słownik słów kluczowych

Może być konieczne zmodyfikowanie słów kluczowych w jednym ze słowników słów kluczowych lub zmodyfikowanie jednego z wbudowanych słowników. Można to zrobić za pośrednictwem programu PowerShell lub centrum zgodności.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>Modyfikowanie słownika słów kluczowych w Centrum zgodności

Słowniki słów kluczowych mogą być używane jako `Primary elements` lub `Supporting elements` w wzorcach typu informacji poufnych (SIT). Słownik słów kluczowych można edytować podczas tworzenia środowiska SIT lub istniejącego środowiska SIT. Aby na przykład edytować istniejący słownik słów kluczowych:

1. Otwórz wzorzec ze słownikiem słów kluczowych, który chcesz zaktualizować.
2. Znajdź słownik słów kluczowych, które chcesz zaktualizować, i wybierz pozycję Edytuj.
3. Wprowadź zmiany przy użyciu jednego słowa kluczowego na wiersz.

   ![zrzut ekranu przedstawiający edytowanie słów kluczowych.](../media/edit-keyword-dictionary.png)

4. Wybierz pozycję `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>Modyfikowanie słownika słów kluczowych przy użyciu programu PowerShell

Na przykład zmodyfikujemy niektóre terminy w programie PowerShell, zapiszemy terminy lokalnie, gdzie można je zmodyfikować w edytorze, a następnie zaktualizujemy poprzednie terminy.

Najpierw pobierz obiekt słownika:

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

Drukowanie `$dict` będzie wyświetlać różne właściwości. Same słowa kluczowe są przechowywane w obiekcie na zapleczu, ale `$dict.KeywordDictionary` zawierają ich reprezentację ciągu, której użyjesz do zmodyfikowania słownika.

Przed zmodyfikowaniem słownika należy ponownie przekształcić ciąg terminów w tablicę przy użyciu `.split(',')` metody . Następnie wyczyścisz niechciane spacje między słowami kluczowymi za pomocą `.trim()` metody , pozostawiając tylko słowa kluczowe do pracy.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

Teraz usuniesz niektóre terminy ze słownika. Ponieważ przykładowy słownik zawiera tylko kilka słów kluczowych, można równie łatwo pominąć eksportowanie słownika i edytowanie go w Notatniku, ale słowniki zwykle zawierają dużą ilość tekstu, więc najpierw dowiesz się, jak łatwo edytować go w programie PowerShell.

W ostatnim kroku zapisano słowa kluczowe w tablicy. Istnieje kilka sposobów [usuwania elementów z tablicy](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10)), ale w prosty sposób utworzysz tablicę terminów, które chcesz usunąć ze słownika, a następnie skopiuj do niej tylko terminy słownika, które nie znajdują się na liście terminów do usunięcia.

Uruchom polecenie `$terms` , aby wyświetlić bieżącą listę terminów. Dane wyjściowe polecenia wyglądają następująco:

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

Uruchom polecenie `$updatedTerms` , aby wyświetlić zaktualizowaną listę terminów. Dane wyjściowe polecenia wyglądają następująco (określone terminy zostały usunięte):

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

Teraz zapisz słownik lokalnie i dodaj jeszcze kilka terminów. Możesz dodać terminy w tym miejscu w programie PowerShell, ale nadal musisz wyeksportować plik lokalnie, aby upewnić się, że został zapisany przy użyciu kodowania Unicode i zawiera bom.

Zapisz słownik lokalnie, uruchamiając następujące polecenie:

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

Teraz otwórz plik, dodaj inne terminy i zapisz za pomocą kodowania Unicode (UTF-16). Teraz przekażesz zaktualizowane terminy i zaktualizujesz słownik.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

Teraz słownik został zaktualizowany. Pole `Identity` przyjmuje nazwę słownika. Jeśli chcesz również zmienić nazwę słownika przy użyciu polecenia cmdlet, wystarczy dodać `-Name` parametr do powyższych elementów przy użyciu `Set-` nowej nazwy słownika.

## <a name="see-also"></a>Zobacz też

- [Twórz słownik słów kluczowych](create-a-keyword-dictionary.md)
- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
