---
title: Tworzenie słownika słów kluczowych
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
description: Podstawowe czynności tworzenia słownika słów kluczowych można uzyskać w Centrum Office 365 zabezpieczeń & zgodności.
ms.openlocfilehash: ca88c57739c8734f9fcdb5d3356a44dc6a72faa5
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009701"
---
# <a name="create-a-keyword-dictionary"></a>Tworzenie słownika słów kluczowych

Ochrona przed utratą danych (DLP, Data loss prevention) może identyfikować, monitorować i chronić poufne elementy. Zidentyfikowanie elementów poufnych czasami wymaga wyszukiwania słów kluczowych, zwłaszcza w przypadku identyfikowania zawartości ogólnej (na przykład komunikacji związanej z opiekią zdrowotną) albo nieodpowiedniego lub jawnego języka. Listy słów kluczowych można tworzyć w przypadku typów informacji poufnych, ale listy słów kluczowych mają ograniczony rozmiar i wymagają modyfikowania kodu XML w celu ich utworzenia lub edytowania. Słowniki słów kluczowych zapewniają prostsze zarządzanie słowami kluczowymi i na znacznie większą skalę, obsługując do 1 MB terminów (po kompresji) w słowniku i obsługują dowolny język. Limit dzierżawy to również 1 MB po kompresji. 1 MB limitu kompresji po kompresji oznacza, że wszystkie słowniki połączone w dzierżawie mogą mieć prawie milion znaków.

## <a name="keyword-dictionary-limits"></a>Limity słowników słów kluczowych

Istnieje limit 50 typów informacji poufnych opartych na słowniku słów kluczowych, które można utworzyć dla 1 dzierżawy. Aby dowiedzieć się, ile słowników słów kluczowych masz w dzierżawie, połącz się za pomocą procedur w programie Połączenie z programem [PowerShell centrum zabezpieczeń & w](/powershell/exchange/connect-to-scc-powershell) celu nawiązania połączenia z dzierżawą i uruchomienia tego skryptu programu PowerShell.

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

Słowa kluczowe dotyczące słownika mogą pochodzić z różnych źródeł, najczęściej z pliku (na przykład listy programu .csv lub .txt) zaimportowanych w usłudze lub przez polecenie cmdlet programu PowerShell, z listy  enter bezpośrednio w cmdlet programu PowerShell lub z istniejącego słownika. Podczas tworzenia słownika słów kluczowych wykonaj te same podstawowe czynności:

1. Użyj <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">*Centrum zgodności platformy Microsoft 365 lub</a> połącz się z **Centrum &amp; zgodności zabezpieczeń programu PowerShell**.

2. **Zdefiniuj lub załaduj słowa kluczowe z zamierzonego źródła**. Kreator i polecenie cmdlet akceptują rozdzieloną przecinkami listę słów kluczowych w celu utworzenia niestandardowego słownika słów kluczowych, więc ten krok będzie się nieco różnić w zależności od tego, skąd pochodzą słowa kluczowe. Po załadowaniu są one kodowane i konwertowane na tablicę bajtów przed ich zaimportowaniem.

3. **Utwórz słownik**. Wybierz nazwę i opis, a następnie utwórz słownik.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>Tworzenie słownika słów kluczowych za pomocą Centrum & zgodności

Aby utworzyć i zaimportować słowa kluczowe dla słownika niestandardowego, należy wykonać następujące czynności:

1. Połączenie <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">do Centrum zgodności platformy Microsoft 365.</a>

2. Przejdź do **klasyfikacji > typów informacji poufnych**.

3. Wybierz **pozycję** Utwórz i wprowadź **nazwę oraz** **opis dla** typu informacji poufnych, a następnie wybierz pozycję **Dalej.**

4. Wybierz **pozycję Dodaj element, a** następnie wybierz **pozycję Słownik (duże słowa kluczowe)** z listy **rozwijanej Wykryj zawartość** zawierającą.

5. Wybierz **pozycję Dodaj słownik**

6. W kontrolce Wyszukaj wybierz pozycję **Tutaj możesz utworzyć nowe słowniki słów kluczowych**.

7. Wprowadź nazwę **słownika** niestandardowego.

8. Wybierz **pozycję Importuj**, a następnie wybierz **pozycję Z tekstu** lub **Z pliku csv** , w zależności od typu pliku słowa kluczowego.

9. W oknie dialogowym pliku wybierz plik słowa kluczowego z lokalnego udziału plików PC lub sieciowego, a następnie wybierz pozycję **Otwórz**.

10. Wybierz **pozycję Zapisz**, a następnie wybierz słownik niestandardowy z listy **Słowniki słów** kluczowych.

11. Wybierz **pozycję Dodaj**, a następnie wybierz pozycję **Dalej**.

12. Przejrzyj i finalizuj wybrane typy informacji poufnych, a następnie wybierz pozycję **Zakończ**.

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>Tworzenie słownika słów kluczowych z pliku przy użyciu programu PowerShell

Często podczas tworzenia dużego słownika używa się słów kluczowych z pliku lub listy wyeksportowanych z innego źródła. W takim przypadku utworzysz słownik słów kluczowych zawierający listę nieodpowiednich języków do ekranu w zewnętrznej wiadomości e-mail. Najpierw należy [Połączenie do programu PowerShell & w Centrum zgodności.](/powershell/exchange/connect-to-scc-powershell)

1. Skopiuj słowa kluczowe do pliku tekstowego i upewnij się, że każde słowo kluczowe znajduje się w osobnym wierszu.

2. Zapisz plik tekstowy przy użyciu kodowania Unicode. W Notatnik \> **Zapisz jako** \> **kodowanie** \> **Unicode**.

3. Odczytaj plik jako zmienną, uruchamiając to polecenie cmdlet:

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. Utwórz słownik, uruchamiając to polecenie cmdlet:

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>Używanie słowników słów kluczowych w niestandardowych typach informacji poufnych i zasadach DLP

Słowników słów kluczowych można używać jako części wymagań dotyczących dopasowania niestandardowych typów informacji poufnych lub jako samych typów informacji poufnych. Oba te typy wymagają utworzenia [niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type-in-scc-powershell.md). Postępuj zgodnie z instrukcjami w artykule, do których link zawiera, aby utworzyć typ informacji poufnych. Gdy masz już kod XML, potrzebujesz identyfikatora GUID słownika, aby go użyć.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

Aby uzyskać tożsamość słownika, uruchom to polecenie i skopiuj wartość **właściwości Identity** :

```powershell
Get-DlpKeywordDictionary -Name "Diseases"
```

Wynik polecenia wygląda następująco:

`RunspaceId        : 138e55e7-ea1e-4f7a-b824-79f2c4252255`
`Identity          : 8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f`
`Name              : Diseases`
`Description       : Names of diseases and injuries from ICD-10-CM lexicon`
`KeywordDictionary : aarskog's syndrome, abandonment, abasia, abderhalden-kaufmann-lignac, abdominalgia, abduction contracture, abetalipo` `proteinemia, abiotrophy, ablatio, ablation, ablepharia, abocclusion, abolition, aborter, abortion, abortus, aboulomania,`
                    `abrami's disease, abramo`
`IsValid           : True`
`ObjectState       : Unchanged`

Wklej tożsamość do kodu XML niestandardowego typu informacji poufnych i przekaż go. Teraz słownik pojawi się na liście typów informacji poufnych i będzie można go używać bezpośrednio w twoich zasadach, określając liczbę słów kluczowych wymaganych do dopasowania.

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
> Microsoft 365 informacji obsługuje dwu bajtowe języki zestawu znaków dla:
>
> - Chiński (uproszczony)
> - Chiński (tradycyjny)
> - Korean
> - Japanese
>
> Ta obsługa jest dostępna w przypadku typów informacji poufnych. Aby uzyskać [więcej informacji](mip-dbcs-relnotes.md) , zobacz Obsługa ochrony informacji dla zestawów znaków dwuteowych (wersja Zapoznawcza).

> [!TIP]
> Aby wykryć wzorce zawierające znaki chińskie/japońskie i pojedyncze bajty lub wykryć wzorce zawierające chiński/japoński i angielski, zdefiniuj dwie warianty słowa kluczowego lub znaków regex.
>
> - Aby na przykład wykryć słowo kluczowe, takie jak "机密的document", użyj dwóch wariantów słowa kluczowego; jeden z odstępem między tekstem japońskim i angielskim a innym bez spacji między tekstem japońskim i angielskim. Dlatego słowa kluczowe, które mają zostać dodane w dokumencie SIT, powinny mieć poszczególnych 机密的 dokumentu i 机密的document. Podobnie, aby wykryć frazę "ピオリンピック2020", należy użyć dwóch wariantów. "オオリンピック 2020" and "ピピリンピック2020".
>
> Jeśli oprócz chińskich/japońskich/dwu bajtowych znaków na liście słów kluczowych/fraz znajdują się również wyrazy inne niż chińskie/japońskie (na przykład tylko w języku angielskim), zaleca się utworzenie dwóch list słowników/słów kluczowych. Jeden dla słów kluczowych zawierających znaki chińskie/japońskie/dwu bajtowe, a drugi tylko w języku angielskim.
>
> - Jeśli na przykład chcesz utworzyć słownik lub listę słów kluczowych z trzema frazami "Wysoce poufne", "機密性がいい" i "机密的document", należy utworzyć dwie listy słów kluczowych.
>     1. Wysoce poufne
>     2. 機密性がい, 机密的document i 机密的 dokument
>
> Tworząc znak regex za pomocą dwu-bajtowego łącznika lub podwójnej litery bajtowej, należy pamiętać o znakach ucieczki przed łącznikiem lub przecięciem w znakach regex. Oto przykładowy regex do odwołania:
>
> - `(?<!\d)([４][０-９]{3}[\-?\－\t]*[０-９]{4}`
>
> Zalecamy użycie dopasowania ciągu zamiast dopasowania wyrazu na liście słów kluczowych.
