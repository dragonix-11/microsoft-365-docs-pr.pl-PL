---
title: Twórz słownik słów kluczowych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Poznaj podstawowe kroki tworzenia słownika słów kluczowych w centrum Office 365 Security & Compliance Center.
ms.openlocfilehash: 64e431b5d2ef01e85eff55f39f4436786f45664b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758602"
---
# <a name="create-a-keyword-dictionary"></a>Twórz słownik słów kluczowych

Ochrona przed utratą danych (DLP) może identyfikować, monitorować i chronić poufne elementy. Identyfikowanie poufnych elementów czasami wymaga wyszukania słów kluczowych, szczególnie w przypadku identyfikowania zawartości ogólnej (takiej jak komunikacja związana z opieką zdrowotną) lub nieodpowiedniego lub jawnego języka. Mimo że listy słów kluczowych można tworzyć w typach informacji poufnych, listy słów kluczowych mają ograniczony rozmiar i wymagają modyfikacji kodu XML w celu ich utworzenia lub edytowania. Słowniki słów kluczowych zapewniają prostsze zarządzanie słowami kluczowymi i w znacznie większej skali, obsługując do 1 MB terminów (po kompresji) w słowniku i obsługują dowolny język. Limit dzierżawy wynosi również 1 MB po kompresji. 1 MB limitu po kompresji oznacza, że wszystkie słowniki połączone w dzierżawie mogą mieć blisko 1 milion znaków.

## <a name="keyword-dictionary-limits"></a>Limity słownika słów kluczowych

Istnieje limit 50 typów informacji poufnych opartych na słowniku słów kluczowych, które można utworzyć dla dzierżawy. Aby dowiedzieć się, ile słowników słów kluczowych masz w dzierżawie, połącz się przy użyciu procedur w [Połączenie z programem PowerShell Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell), aby nawiązać połączenie z dzierżawą i uruchomić ten skrypt programu PowerShell.

```powershell
$rawFile = $env:TEMP + "\rule.xml"

$kd = Get-DlpKeywordDictionary
$ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
[System.IO.File]::WriteAllBytes((Resolve-Path $rawFile), $ruleCollections.SerializedClassificationRuleCollection)
$UnicodeEncoding = New-Object System.Text.UnicodeEncoding
$FileContent = [System.IO.File]::ReadAllText((Resolve-Path $rawFile), $unicodeEncoding)

if($kd.Count -gt 0)
{
$count = 0
$entities = $FileContent -split "Entity id"
for($j=1;$j -lt $entities.Count;$j++)
{
for($i=0;$i -lt $kd.Count;$i++)
{
$Matches = Select-String -InputObject $entities[$j] -Pattern $kd[$i].Identity -AllMatches
$count = $Matches.Matches.Count + $count
if($Matches.Matches.Count -gt 0) {break}
}
}

Write-Output "Total Keyword Dictionary SIT:"
$count
}
else
{
$Matches = Select-String -InputObject $FileContent -Pattern $kd.Identity -AllMatches
Write-Output "Total Keyword Dictionary SIT:"
$Matches.Matches.Count
}

Remove-Item $rawFile
```

## <a name="basic-steps-to-creating-a-keyword-dictionary"></a>Podstawowe kroki tworzenia słownika słów kluczowych

Słowa kluczowe słownika mogą pochodzić z różnych źródeł, najczęściej z pliku (na przykład listy .csv lub .txt) zaimportowanej w usłudze lub za pomocą polecenia cmdlet programu PowerShell, z listy wprowadzonej bezpośrednio w poleceniu cmdlet programu PowerShell lub z istniejącego słownika. Podczas tworzenia słownika słów kluczowych należy wykonać te same podstawowe kroki:

1. Użyj programu PowerShell *<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> lub połącz się z **centrum zgodności zabezpieczeń&amp;**.

2. **Zdefiniuj lub załaduj słowa kluczowe z zamierzonego źródła**. Kreator i polecenie cmdlet akceptują rozdzielaną przecinkami listę słów kluczowych w celu utworzenia niestandardowego słownika słów kluczowych, więc ten krok będzie się nieznacznie różnić w zależności od tego, skąd pochodzą słowa kluczowe. Po załadowaniu są one kodowane i konwertowane na tablicę bajtów przed ich zaimportowaniem.

3. **Utwórz słownik**. Wybierz nazwę i opis i utwórz słownik.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>Tworzenie słownika słów kluczowych przy użyciu Centrum zgodności & zabezpieczeń

Wykonaj następujące kroki, aby utworzyć i zaimportować słowa kluczowe dla słownika niestandardowego:

1. Połączenie do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>.

2. Przejdź do **pozycji Klasyfikacje > typy informacji poufnych**.

3. Wybierz pozycję **Utwórz** i wprowadź **nazwę** i **opis** dla swojego typu informacji poufnych, a następnie wybierz pozycję **Dalej**

4. Wybierz **pozycję Dodaj element**, a następnie wybierz pozycję **Słownik (duże słowa kluczowe)** z listy rozwijanej **Wykryj zawartość zawierającą** .

5. Wybierz **pozycję Dodaj słownik**

6. W obszarze kontrolki Wyszukiwanie wybierz pozycję **Możesz tutaj utworzyć nowe słowniki słów kluczowych**.

7. Wprowadź **nazwę** słownika niestandardowego.

8. Wybierz pozycję **Importuj** i wybierz pozycję **Z tekstu** lub **Z pliku csv** w zależności od typu pliku słowa kluczowego.

9. W oknie dialogowym pliku wybierz plik słowa kluczowego z lokalnego komputera lub udziału plików sieciowych, a następnie wybierz pozycję **Otwórz**.

10. Wybierz pozycję **Zapisz**, a następnie wybierz słownik niestandardowy z listy **Słowniki słów kluczowych** .

11. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Dalej**.

12. Przejrzyj i finalizuj wybrane typy informacji poufnych, a następnie wybierz pozycję **Zakończ**.

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>Tworzenie słownika słów kluczowych na podstawie pliku przy użyciu programu PowerShell

Często podczas tworzenia dużego słownika należy używać słów kluczowych z pliku lub listy wyeksportowanej z innego źródła. W takim przypadku utworzysz słownik słów kluczowych zawierający listę nieodpowiednich języków do wyświetlania w zewnętrznej wiadomości e-mail. Najpierw należy [Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell).

1. Skopiuj słowa kluczowe do pliku tekstowego i upewnij się, że każde słowo kluczowe znajduje się w osobnym wierszu.

2. Zapisz plik tekstowy przy użyciu kodowania Unicode. W Notatnik \> **zapisz jako** \> **kodowanie** \> **Unicode**.

3. Przeczytaj plik do zmiennej, uruchamiając następujące polecenie cmdlet:

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. Utwórz słownik, uruchamiając następujące polecenie cmdlet:

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>Używanie słowników słów kluczowych w niestandardowych typach informacji poufnych i zasadach DLP

Słowniki słów kluczowych mogą być używane jako część wymagań dopasowania dla niestandardowego typu informacji poufnych lub jako typ informacji poufnych. Oba wymagają utworzenia [niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type-in-scc-powershell.md). Postępuj zgodnie z instrukcjami w artykule połączonym, aby utworzyć typ informacji poufnych. Po utworzeniu kodu XML będziesz potrzebować identyfikatora GUID dla słownika, aby go używać.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

Aby uzyskać tożsamość słownika, uruchom to polecenie i skopiuj wartość właściwości **Identity** :

```powershell
Get-DlpKeywordDictionary -Name "Diseases"
```

Dane wyjściowe polecenia wyglądają następująco:

`RunspaceId        : 138e55e7-ea1e-4f7a-b824-79f2c4252255`
`Identity          : 8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f`
`Name              : Diseases`
`Description       : Names of diseases and injuries from ICD-10-CM lexicon`
`KeywordDictionary : aarskog's syndrome, abandonment, abasia, abderhalden-kaufmann-lignac, abdominalgia, abduction contracture, abetalipo` `proteinemia, abiotrophy, ablatio, ablation, ablepharia, abocclusion, abolition, aborter, abortion, abortus, aboulomania,`
                    `abrami's disease, abramo`
`IsValid           : True`
`ObjectState       : Unchanged`

Wklej tożsamość do pliku XML niestandardowego typu informacji poufnych i przekaż ją. Teraz słownik pojawi się na liście typów informacji poufnych i będzie można go używać bezpośrednio w zasadach, określając, ile słów kluczowych jest wymaganych do dopasowania.

```xml
<Entity id="d333c6c2-5f4c-4131-9433-db3ef72a89e8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f" />
      </Pattern>
    </Entity>
    <LocalizedStrings>
      <Resource idRef="d333c6c2-5f4c-4131-9433-db3ef72a89e8">
        <Name default="true" langcode="en-us">Diseases</Name>
        <Description default="true" langcode="en-us">Detects various diseases</Description>
      </Resource>
    </LocalizedStrings>
```

> [!NOTE]
> Microsoft 365 Information Protection obsługuje języki zestawu znaków dwu bajtowych dla:
>
> - Chiński (uproszczony)
> - Chiński (tradycyjny)
> - Korean
> - Japanese
>
> Ta obsługa jest dostępna dla typów informacji poufnych. Aby uzyskać więcej informacji, zobacz [Obsługa ochrony informacji dla podwójnych zestawów znaków bajtowych (wersja zapoznawcza).](mip-dbcs-relnotes.md)

> [!TIP]
> Aby wykryć wzorce zawierające znaki chińskie/japońskie i pojedyncze znaki bajtowe lub wykryć wzorce zawierające chiński/japoński i angielski, zdefiniuj dwa warianty słowa kluczowego lub wyrażenia regularnego.
>
> - Aby na przykład wykryć słowo kluczowe, takie jak "机密的document", użyj dwóch wariantów słowa kluczowego; jeden z odstępem między tekstem japońskim i angielskim a drugim bez odstępu między tekstem japońskim i angielskim. Dlatego słowa kluczowe, które mają zostać dodane w usłudze SIT, powinny mieć wartość "机密的 document" i "机密的document". Podobnie, aby wykryć frazę "東京オリnegoピック2020", należy użyć dwóch wariantów; "東京オリ":"ピック 2020" i "東京オリ":"ピック2020".
>
> Oprócz znaków chińskich/japońskich/podwójnych bajtów, jeśli lista słów kluczowych/fraz zawiera również słowa inne niż chińskie/japońskie (na przykład tylko angielski), zaleca się utworzenie dwóch słowników/list słów kluczowych. Jeden dla słów kluczowych zawierających znaki chiński/japoński/podwójny bajt, a drugi tylko dla języka angielskiego.
>
> - Jeśli na przykład chcesz utworzyć słownik/listę słów kluczowych z trzema frazami "Wysoce poufne", "機密性が高い" i "机密的document", należy utworzyć dwie listy słów kluczowych.
>   1. Wysoce poufne
>   2. 機密性が高い, 机密的document i 机密的 dokumentu
>
> Podczas tworzenia wyrażenia regularnego przy użyciu łącznika dwu bajtowego lub podwójnego kropki bajtowej upewnij się, że oba znaki, takie jak jeden, unikną łącznika lub kropki w rejestrze. Oto przykładowy rejestr referencyjny:
>
> - `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> Zalecamy użycie dopasowania ciągu zamiast dopasowania wyrazów na liście słów kluczowych.
