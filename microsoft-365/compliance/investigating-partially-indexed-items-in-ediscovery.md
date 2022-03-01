---
title: Badanie elementów częściowo indeksowanych w zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 4e8ff113-6361-41e2-915a-6338a7e2a1ed
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak zarządzać elementami częściowo indeksowanych (nazywanymi również elementami nieindeksowanych) z Exchange, SharePoint i OneDrive dla Firm w organizacji.
ms.openlocfilehash: 308b99b8bcb8d11c53759700d43651e521987948
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033007"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>Badanie elementów częściowo indeksowanych w zbierania elektronicznych materiałów dowodowych

Podczas wyszukiwania zbierania elektronicznych materiałów dowodowych elementy Centrum zgodności platformy Microsoft 365 są automatycznie uwzględniane częściowo indeksowane elementy w szacowanych wynikach wyszukiwania. Elementy częściowo indeksowane to elementy Exchange i dokumenty skrzynek pocztowych w witrynach SharePoint i OneDrive dla Firm, które z jakiegoś powodu nie zostały całkowicie zindeksowane w celu wyszukiwania. Większość wiadomości e-mail i dokumentów witryny jest pomyślnie indeksowanych, ponieważ są one w granicach limitów indeksowania [wiadomości e-mail](limits-for-content-search.md#indexing-limits-for-email-messages). Jednak niektóre elementy mogą przekraczać te limity indeksowania i będą częściowo indeksowane. Oto inne przyczyny, dla których elementów nie można indeksować w celu wyszukiwania i są zwracane jako elementy częściowo indeksowane po uruchomieniu wyszukiwania zbierania elektronicznych materiałów dowodowych:
  
- Wiadomości e-mail mają dołączony plik, których nie można otworzyć, na przykład pliki obrazów. jest to najczęstsza przyczyna częściowo indeksowanych elementów poczty e-mail.

- Zbyt wiele plików dołączonych do wiadomości e-mail.

- Plik dołączony do wiadomości e-mail jest za duży.

- Typ pliku jest obsługiwany w przypadku indeksowania, ale wystąpił błąd indeksowania w przypadku określonego pliku.

Mimo że ten problem się różni, większość organizacji ma mniej niż 1% zawartości według woluminu i mniej niż 12% zawartości według rozmiaru, który jest częściowo indeksowany. Przyczyną różnicy między wielkością a wielkością woluminu jest wyższe prawdopodobieństwo, że większe pliki będą zawierały zawartość, która nie może zostać całkowicie zindeksowana.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>Dlaczego częściowo indeksowana liczba elementów zmienia się w wyszukiwaniu?

Po uruchomieniu wyszukiwania zbierania elektronicznych materiałów dowodowych w statystykach wyników wyszukiwania jest wyświetlana całkowita liczba i rozmiar częściowo indeksowanych elementów w lokalizacjach, które były przeszukiwane. Zauważ, że są to  *elementy nieindeksowane*  w statystyce wyszukiwania. Oto kilka elementów, które wpływają na liczbę częściowo indeksowanych elementów zwracanych w wynikach wyszukiwania:
  
- Jeśli element jest częściowo indeksowany i odpowiada zapytaniu wyszukiwania, jest uwzględniany zarówno w zlicie (i rozmiarze) elementów wyników wyszukiwania, jak i elementach częściowo indeksowanych. Jednak w przypadku eksportowania wyników tego samego wyszukiwania element jest uwzględniany tylko w zestawie wyników wyszukiwania. nie jest uwzględniany jako element częściowo indeksowany.

- Elementy częściowo indeksowane znajdujące się w witrynach SharePoint i OneDrive nie są uwzględniane w oszacowaniu częściowo indeksowanych elementów wyświetlanych w szczegółowych statystykach wyszukiwania. Jednak elementy częściowo indeksowane mogą być eksportowane podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych. Jeśli na przykład będziesz przeszukiwać tylko witryny, szacowana liczba częściowo indeksowanych elementów będzie równa zero.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>Obliczanie stosunku elementów częściowo indeksowanych w organizacji

Aby zrozumieć, czy Organizacja korzysta z elementów częściowo indeksowanych, możesz wyszukać całą zawartość wszystkich skrzynek pocztowych (za pomocą pustego zapytania słów kluczowych). W poniższym przykładzie jest 1 629 904 (146,46 GB) w pełni indeksowanych elementów i 10 025 (10,27 GB) elementów częściowo indeksowanych.
  
![Przykładowa statystyka wyszukiwania pokazująca elementy częściowo indeksowane.](../media/PartiallyIndexedItemsTest.png)
  
Wartość procentową elementów częściowo indeksowanych można ustalić, korzystając z następujących obliczeń.
  
 **Aby obliczyć współczynnik częściowo indeksowanych elementów w organizacji:**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

W wynikach wyszukiwania z poprzedniego przykładu 0,62% wszystkich elementów skrzynek pocztowych jest częściowo indeksowanych.
  
 **Aby obliczyć procent rozmiaru elementów częściowo indeksowanych w organizacji:**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

W poprzednim przykładzie 7% całkowitego rozmiaru elementów skrzynki pocztowej pochodzi z elementów częściowo indeksowanych. Jak wspomniano wcześniej, większość organizacji klientów ma mniej niż 1% zawartości według woluminu i mniej niż 12% zawartości według rozmiaru, który jest częściowo indeksowany.

## <a name="working-with-partially-indexed-items"></a>Praca z elementami częściowo indeksowanych

W przypadkach, gdy trzeba zbadać elementy częściowo indeksowane w celu zweryfikowania, że nie zawierają one istotnych informacji, możesz wyeksportować raport przeszukiwania zawartości zawierający informacje o elementach częściowo indeksowanych.[](export-a-content-search-report.md) Podczas eksportowania raportu przeszukiwania zawartości należy wybrać jedną z opcji eksportu, która zawiera częściowo indeksowane elementy.
  
![Wybierz drugą lub trzecią opcję eksportowania elementów częściowo indeksowanych.](../media/PartiallyIndexedItemsExportOptions.png)
  
W przypadku eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych lub raportu wyszukiwania przy użyciu jednej z tych opcji eksport obejmuje raport o nazwie Nieindeksowane Items.csv. Ten raport zawiera większość tych samych informacji, co plik ResultsLog.csv pliku; Plik nieindeksowany zawiera Items.csv także dwa pola powiązane z elementami częściowo indeksowanych **: Tagi** błędów i **Właściwości błędów**. Te pola zawierają informacje o błędzie indeksowania dla każdego częściowo indeksowanego elementu. Dzięki informacjom w tych dwóch polach można ustalić, czy błąd indeksowania dla określonego badania ma wpływ na dane badanie. 

> [!NOTE]
> Plik nieindeksowany Items.csv również pola o nazwach **Typ błędu** i **Komunikat o błędzie**. Są to starsze pola zawierające informacje podobne do informacji w polach Tagi błędów i Właściwości  błędów, ale  zawierające mniej szczegółowych informacji. Te starsze pola można bezpiecznie zignorować.
  
## <a name="errors-related-to-partially-indexed-items"></a>Błędy dotyczące elementów częściowo indeksowanych

Tagi błędów zawierają dwie informacje: błąd i typ pliku. Na przykład w tej pari błędu/typu pliku:

```text
 parseroutputsize_xls
```

 `parseroutputsize` jest błędem `xls` i jest typem pliku, w przypadku którego wystąpił błąd. W przypadkach, gdy typ pliku nie został rozpoznany lub typ pliku nie został zastosowania do błędu, `noformat` zobaczysz wartość w miejscu typu pliku.
  
Poniżej przedstawiono listę błędów indeksowania oraz opis możliwej przyczyny błędu.
  
| Tag błędu | Opis |
|:-----|:-----|
| `attachmentcount` <br/> |Wiadomość e-mail miała zbyt wiele załączników, a niektóre z tych załączników nie były przetwarzane.  <br/> |
| `attachmentdepth` <br/> |Pobieracz zawartości i parser dokumentów znalazły zbyt wiele poziomów załączników zagnieżdżonych wewnątrz innych załączników. Niektóre z tych załączników nie zostały przetworzone.  <br/> |
| `attachmentrms` <br/> |Dekodowanie załącznika nie powiodło się, ponieważ był chroniony usługą RMS.  <br/> |
| `attachmentsize` <br/> |Plik dołączony do wiadomości e-mail był za duży i nie można go było przetworzyć.  <br/> |
| `indexingtruncated` <br/> |Podczas pisania przetwarzanej wiadomości e-mail w indeksie jedna z właściwości indeksowanych była za duża i została obcięta. Właściwości obcięte są wyświetlane w polu Właściwości błędu.  <br/> |
| `invalidunicode` <br/> |Wiadomość e-mail zawierała tekst, który nie może zostać przetworzony jako prawidłowy standard Unicode. Indeksowanie tego elementu może być niekompletne.  <br/> |
| `parserencrypted` <br/> |Zawartość załącznika lub wiadomości e-mail jest szyfrowana i Microsoft 365 jej nie można odkodować.  <br/> |
| `parsererror` <br/> |Podczas analizowania wystąpił nieznany błąd. Zazwyczaj jest to skutkiem błędu oprogramowania lub awarii usługi.  <br/> |
| `parserinputsize` <br/> |Załącznik był za duży do obsługi przez parera, a analizowanie tego załącznika nie zostało wykonane lub nie zostało ukończone.  <br/> |
| `parsermalformed` <br/> |Załącznik został zniekształcony i nie mógł zostać obsługiwany przez analizowanie. Może to być spowodowane starymi formatami plików, plikami utworzonymi przez niezgodne oprogramowanie lub wirusami, które mogą być czymś innym niż roszczenia.  <br/> |
| `parseroutputsize` <br/> |Dane wyjściowe z analizy załącznika były za duże i trzeba było je obcięte.  <br/> |
| `parserunknowntype` <br/> |Załącznik miał typ pliku, który Microsoft 365 nie mógł wykryć.  <br/> |
| `parserunsupportedtype` <br/> |Załącznik miał typ pliku, który Office 365 wykryć, ale analizowanie tego typu pliku nie jest obsługiwane.  <br/> |
| `propertytoobig` <br/> |Wartość właściwości poczty e-mail w sklepie Exchange była za duża do pobrania i nie można było przetworzyć wiadomości. Zazwyczaj dzieje się tak tylko w przypadku właściwości treści wiadomości e-mail.  <br/> |
| `retrieverrms` <br/> |Pobieranie zawartości nie powiodło się, aby odkodować wiadomość chronioną przez usługę RMS.  <br/> |
| `wordbreakertruncated` <br/> |Podczas indeksowania w dokumencie zidentyfikowano zbyt wiele wyrazów. Przetwarzanie właściwości zostało zatrzymane po osiągnięciu limitu i ta właściwość jest obcinana.  <br/> |

Pola błędów określają, których pól dotyczy błąd przetwarzania wymieniony w polu Tagi błędów. Jeśli przeszukujesz właściwość  `subject` , taką jak lub  `participants`, błędy w treści wiadomości, nie mają wpływu na wyniki wyszukiwania. Może to być przydatne podczas ustalania dokładnie, które elementy częściowo indeksowane mogą wymagać dalszego zbadania.
  
## <a name="using-a-powershell-script-to-determine-your-organizations-exposure-to-partially-indexed-email-items"></a>Używanie skryptu programu PowerShell w celu określenia ekspozycji Twojej organizacji na częściowo zindeksowane elementy poczty e-mail

Poniższe kroki pokazują, jak uruchomić skrypt programu PowerShell, który wyszukuje wszystkie elementy we wszystkich skrzynkach pocztowych programu Exchange, a następnie generuje raport o współczynniku częściowo indeksowanych elementów poczty e-mail organizacji (według liczby i rozmiaru) oraz wyświetla liczbę elementów (i ich typ pliku) dla każdego wystąpienia błędu indeksowania. Do identyfikowania błędu indeksowania należy używać opisów tagów błędów w poprzedniej sekcji.
  
1. Zapisz poniższy tekst w pliku skryptu Windows PowerShell, używając sufiksu nazwy pliku programu .ps1, `PartiallyIndexedItems.ps1`na przykład .

   ```powershell
     write-host "**************************************************"
     write-host "     Security & Compliance Center PowerShell      " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "   eDiscovery Partially Indexed Item Statistics   " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "**************************************************"
     " " 
     # Create a search with Error Tags Refinders enabled
     Remove-ComplianceSearch "RefinerTest" -Confirm:$false -ErrorAction 'SilentlyContinue'
     New-ComplianceSearch -Name "RefinerTest" -ContentMatchQuery "size>0" -RefinerNames ErrorTags -ExchangeLocation ALL
     Start-ComplianceSearch "RefinerTest"
     # Loop while search is in progress
     do{
         Write-host "Waiting for search to complete..."
         Start-Sleep -s 5
         $complianceSearch = Get-ComplianceSearch "RefinerTest"
     }while ($complianceSearch.Status -ne 'Completed')
     $refiners = $complianceSearch.Refiners | ConvertFrom-Json
     $errorTagProperties = $refiners.Entries | Get-Member -MemberType NoteProperty
     $partiallyIndexedRatio = $complianceSearch.UnindexedItems / $complianceSearch.Items
     $partiallyIndexedSizeRatio = $complianceSearch.UnindexedSize / $complianceSearch.Size
     " "
     "===== Partially indexed items ====="
     "         Total          Ratio"
     "Count    {0:N0}{1:P2}" -f $complianceSearch.Items.ToString("N0").PadRight(15, " "), $partiallyIndexedRatio
     "Size(GB) {0:N2}{1:P2}" -f ($complianceSearch.Size / 1GB).ToString("N2").PadRight(15, " "), $partiallyIndexedSizeRatio
     " "
     Write-Host ===== Reasons for partially indexed items =====
     foreach($errorTagProperty in $errorTagProperties)
     {
         $name = $refiners.Entries.($errorTagProperty.Name).Name
         $count = $refiners.Entries.($errorTagProperty.Name).TotalCount
         $frag = $name.Split("{_}")
         $errorTag = $frag[0]
         $fileType = $frag[1]
         if ($errorTag -ne $lastErrorTag)
         {
             $errorTag
         }
         "    " + $fileType + " => " + $count
         $lastErrorTag = $errorTag
     }
   ```

2. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/exchange-online-powershell).

3. W centrum & zabezpieczeń w programie PowerShell przejdź do folderu, w którym został zapisany skrypt w kroku 1, a następnie uruchom skrypt. na przykład:

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

Oto przykład danych wyjściowych zwróconych przez skrypt.
  
![Przykład danych wyjściowych ze skryptu generującego raport o ekspozycji Twojej organizacji na częściowo zindeksowane elementy poczty e-mail.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> Zwróć uwagę na następujące kwestie:
>  
> - Całkowita liczba i rozmiar elementów poczty e-mail oraz współczynnik częściowego indeksowania elementów poczty e-mail w organizacji (według liczby i rozmiaru).
> 
> - Tagi błędów listy i odpowiadające im typy plików, dla których wystąpił błąd.
  
## <a name="see-also"></a>Zobacz też

[Częściowo indeksowane elementy na zbierania elektronicznych materiałów dowodowych](partially-indexed-items-in-content-search.md)
