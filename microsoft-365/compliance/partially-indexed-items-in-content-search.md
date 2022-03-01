---
title: Częściowo indeksowane elementy w przeszukiwaniu zawartości i innych narzędziach zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnindexedItemsLearnMore
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: d1691de4-ca0d-446f-a0d0-373a4fc8487b
description: Dowiedz się więcej o elementach nieindeksowanych w Exchange i SharePoint, które można uwzględnić podczas wyszukiwania zbierania elektronicznych materiałów dowodowych uruchamianego w Centrum zgodności platformy Microsoft 365.
ms.openlocfilehash: b1adfaab1008cdfa9e7893273feaba38a71e85ac
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014905"
---
# <a name="partially-indexed-items-in-ediscovery"></a>Częściowo indeksowane elementy na zbierania elektronicznych materiałów dowodowych

Podczas wyszukiwania zbierania elektronicznych materiałów dowodowych elementy Centrum zgodności platformy Microsoft 365 są automatycznie uwzględniane częściowo indeksowane elementy w szacowanych wynikach wyszukiwania. Elementy częściowo indeksowane to elementy Exchange i dokumenty skrzynek pocztowych w witrynach SharePoint i OneDrive dla Firm, które z jakiegoś powodu nie zostały całkowicie zindeksowane w celu wyszukiwania. W Exchange element częściowo indeksowany zazwyczaj zawiera plik (typu pliku, który nie może być indeksowany) dołączony do wiadomości e-mail. Oto kilka innych powodów, dla których elementy nie mogą być indeksowane w celu wyszukiwania i są zwracane jako elementy częściowo indeksowane po uruchomieniu wyszukiwania zbierania elektronicznych materiałów dowodowych:
  
- Typ pliku jest nierozpoznany lub nieobsługiwany na przykład w przypadku indeksowania.

- Wiadomości mają dołączony plik, których nie można otworzyć, na przykład pliki obrazów. jest to najczęstsza przyczyna częściowo indeksowanych elementów poczty e-mail.

- Typ pliku jest obsługiwany w przypadku indeksowania, ale wystąpił błąd indeksowania w przypadku określonego pliku.

- Zbyt wiele plików dołączonych do wiadomości e-mail.

- Plik dołączony do wiadomości e-mail jest za duży.

- Plik jest szyfrowany przy użyciu technologii innych niż firmy Microsoft.

- Plik jest chroniony hasłem.

> [!NOTE]
> Większość organizacji ma mniej niż 1% zawartości według woluminu i mniej niż 12% rozmiaru częściowo indeksowanego. Przyczyną różnicy między woluminem a rozmiarem jest wyższe prawdopodobieństwo, że większe pliki będą zawierały zawartość, która nie może zostać całkowicie zindeksowana.
  
W przypadku dochodzenia prawnego od organizacji może być wymagane przejrzenie elementów częściowo indeksowanych. Można także określić, czy podczas eksportowania wyników wyszukiwania na komputer lokalny mają być dołączane elementy częściowo indeksowane, czy też podczas przygotowywania wyników do analizy za pomocą Advanced eDiscovery. Aby uzyskać więcej informacji, zobacz [Badanie elementów częściowo indeksowanych w zbierania elektronicznych materiałów dowodowych](investigating-partially-indexed-items-in-ediscovery.md).
  
## <a name="file-types-not-indexed-for-search"></a>Typy plików nieindeksowane do wyszukiwania

Niektóre typy plików, takie jak pliki map bitowych lub MP3, nie zawierają zawartości, która może być indeksowana. Z tego powodu serwery indeksowania wyszukiwania w Exchange i SharePoint nie wykonują indeksowania pełnoektowego dla plików tego typu. Te typy plików są uznawane za nieobsługiwane typy plików. Istnieją również typy plików, dla których indeksowanie w pełnym tekście zostało wyłączone domyślnie lub przez administratora. Nieobsługiwane i wyłączone typy plików są oznaczane w wyszukiwaniach zawartości jako elementy nieindeksowane. Jak wspomniano wcześniej, elementy częściowo indeksowane mogą być uwzględniane w zestawie wyników wyszukiwania podczas uruchamiania wyszukiwania, eksportowania wyników wyszukiwania na komputer lokalny lub przygotowywania wyników Advanced eDiscovery.
  
Aby uzyskać listę obsługiwanych i wyłączonych formatów plików, zobacz następujące tematy:
  
-  -  Exchange [Pliki indeksowane przez Exchange wyszukiwania](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

-  -  Exchange [Get-SearchDocumentFormat](/powershell/module/exchange/get-searchdocumentformat)

-  -  SharePoint [Default rozszerzenia nazw plików przeszukanych i typy plików analizowanych w programie SharePoint](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
  
## <a name="messages-and-documents-with-partially-indexed-file-types-can-be-returned-in-search-results"></a>Wiadomości i dokumenty z częściowo indeksowanych typów plików mogą być zwracane w wynikach wyszukiwania

Nie każda wiadomość e-mail z częściowo indeksowanym załącznikiem pliku lub co częściowo zindeksowany dokument SharePoint jest automatycznie zwracany jako element częściowo indeksowany. Wynika to z tego, że inne właściwości wiadomości lub dokumentu, takie  jak właściwość Temat w wiadomościach e-mail  oraz właściwości Tytuł lub Autor dla dokumentów, są indeksowane i można je przeszukiwać. Na przykład wyszukiwanie słów kluczowych "finansowe" zwraca elementy z częściowo indeksowanym załącznikiem pliku, jeśli to słowo kluczowe pojawia się w temacie wiadomości e-mail albo w nazwie pliku bądź tytule dokumentu. Jeśli jednak słowo kluczowe pojawia się tylko w treści pliku, wiadomość lub dokument zostanie zwrócony jako element częściowo indeksowany.
  
Podobnie wiadomości z częściowo indeksowanych załącznikami plików i dokumentami o częściowo indeksowanych typach plików są uwzględniane w wynikach wyszukiwania, gdy inne właściwości wiadomości lub dokumentu, indeksowane i dostępne do wyszukiwania, spełniają kryteria wyszukiwania. Do właściwości wiadomości indeksowanych w celu wyszukiwania należą: daty wysłania i odebrania, nadawca i adresat, nazwa pliku załącznika i tekst w treści wiadomości. Do właściwości dokumentu indeksowanego w celu wyszukiwania należą daty utworzenia i modyfikacji. Mimo że załącznik wiadomości może być elementem częściowo zindeksowany, wiadomość zostanie uwzględniona w wynikach zwykłego wyszukiwania, jeśli wartość innej wiadomości lub właściwości dokumentu będzie odpowiadać kryteriom wyszukiwania.
  
Aby uzyskać listę właściwości wiadomości e-mail i dokumentów, które można wyszukać przy użyciu narzędzi zbierania elektronicznych materiałów dowodowych w p Centrum zgodności platformy Microsoft 365, zobacz Zapytania kluczowe i warunki wyszukiwania dotyczące zbierania [elektronicznych materiałów dowodowych](keyword-queries-and-search-conditions.md).
  
> [!NOTE]
> Jeśli element skrzynki pocztowej zostanie przeniesiony z folderu indeksowanego do folderu, który nie jest indeksowany, flaga zostanie ustawiona na dezindowanie elementu, a element zostanie usunięty z indeksu i nie będzie można go przeszukiwać. Później ten sam element zostanie przeniesiony z powrotem do folderu indeksowanego, flaga nie zostanie zresetowana. Oznacza to, że element pozostanie nieindeksowany i nie będzie można go przeszukiwać.

## <a name="partially-indexed-items-included-in-the-search-results"></a>Elementy częściowo indeksowane uwzględnione w wynikach wyszukiwania

Organizacja może być wymagana do zidentyfikowania i przeprowadzenia dodatkowej analizy elementów częściowo indeksowanych w celu określenia, co to jest, co zawierają, i czy są one istotne dla określonego badania. Jak wyjaśniono wcześniej, częściowo indeksowane elementy w przeszukiwanych lokalizacjach zawartości są automatycznie uwzględniane w szacowanych wynikach wyszukiwania. Możesz uwzględnić te częściowo indeksowane elementy podczas eksportowania wyników wyszukiwania lub przygotowywania wyników wyszukiwania dla Advanced eDiscovery.
  
Należy pamiętać o elementach częściowo indeksowanych:
  
- Po uruchomieniu wyszukiwania zbierania elektronicznych materiałów dowodowych całkowita liczba i rozmiar częściowo indeksowanych elementów Exchange (zwróconych przez zapytanie wyszukiwania) są wyświetlane w statystyce wyszukiwania na stronie wysuwanych i oznaczane jako elementy nieindeksowane. Statystyki dotyczące elementów częściowo indeksowanych wyświetlanych na stronie wysuwanych nie obejmują elementów częściowo indeksowanych w witrynach SharePoint ani kontach OneDrive wysuwanych.

- Jeśli wyszukiwanie, z których są eksportowane wyniki, dotyczyło wyszukiwania określonych lokalizacji zawartości lub wszystkich lokalizacji zawartości w organizacji, zostaną wyeksportowane tylko elementy nieindeksowane z lokalizacji zawartości, które zawierają elementy zgodne z kryteriami wyszukiwania. Innymi słowy, jeśli w skrzynce pocztowej lub witrynie nie zostaną znalezione żadne wyniki wyszukiwania, nie zostaną wyeksportowane żadne elementy nieindeksowane w tej skrzynce pocztowej lub witrynie. Przyczyną tego jest to, że eksportowanie elementów częściowo indeksowanych z wielu lokalizacji w organizacji może zwiększyć prawdopodobieństwo błędów eksportu i zwiększyć czas eksportowania oraz czas eksportowania i pobierania wyników wyszukiwania.

    Aby wyeksportować elementy częściowo indeksowane ze wszystkich lokalizacji zawartości do wyszukiwania, skonfiguruj wyszukiwanie tak, aby zwracało wszystkie elementy (usuwając słowa kluczowe z zapytania wyszukiwania), a następnie wyeksportuj tylko częściowo indeksowane elementy podczas eksportowania wyników wyszukiwania (klikając pozycję Tylko elementy, które mają nierozpoznany format **,** są szyfrowane lub nie zostały zindeksowane z innych powodów w obszarze Opcje danych wyjściowych **).**

- Jeśli zdecydujesz się uwzględnić wszystkie elementy skrzynki pocztowej w wynikach wyszukiwania lub jeśli zapytanie wyszukiwania nie określa żadnych słów kluczowych lub tylko zakresu dat, częściowo indeksowane elementy mogą nie zostać skopiowane do pliku PST zawierającego częściowo indeksowane elementy. Wynika to z tego, że wszystkie elementy, w tym elementy częściowo indeksowane, będą automatycznie uwzględniane w wynikach zwykłego wyszukiwania.

- Elementy częściowo indeksowane nie są dostępne do podglądu. Aby wyświetlić częściowo indeksowane elementy zwrócone przez wyszukiwanie, należy wyeksportować wyniki wyszukiwania.

   Ponadto w przypadku eksportowania wyników wyszukiwania i częściowego indeksowania elementów w eksporcie elementy częściowo indeksowane z programu SharePoint są eksportowane do folderu o nazwie **Nieszyfrowane**. Podczas eksportowania elementów Exchange indeksowanych są one eksportowane w różny sposób w zależności od tego, czy elementy częściowo indeksowane były zgodne z zapytaniem wyszukiwania i konfiguracją ustawień eksportu. 

- W poniższej tabeli przedstawiono zachowanie eksportowania elementów indeksowanych i częściowo indeksowanych oraz informacje o tym, czy każdy z nich został uwzględniony w różnych ustawieniach konfiguracji eksportu.

  |**Konfiguracja eksportu**|**Elementy indeksowane zgodne z zapytaniem wyszukiwania**|**Częściowo indeksowane elementy, które są zgodne z zapytaniem wyszukiwania**|**Elementy częściowo indeksowane, które nie są zgodne z zapytaniem wyszukiwania**|
  |:-----|:-----|:-----|:-----|
  |Eksportowanie tylko elementów indeksowanych  <br/> |Wyeksportowano<br/> |Wyeksportowane (uwzględnione w eksportowanych elementach indeksowanych)<br/>  |Nie wyeksportowano <br/>|
  |Eksportowanie tylko elementów częściowo indeksowanych  <br/> |Nie wyeksportowano  <br/> |Wyeksportowano (jako elementy częściowo indeksowane)<br/> |Wyeksportowano (jako elementy częściowo indeksowane)|
  |Eksportowanie elementów indeksowanych i częściowo indeksowanych  <br/> |Wyeksportowano<br/> |Wyeksportowane (uwzględnione w eksportowanych elementach indeksowanych)<br/>  |Wyeksportowano (jako elementy częściowo indeksowane)<br/>|
  ||||
  
## <a name="workaround-for-using-a-date-range-to-exclude-partially-indexed-items"></a>Obejście dotyczące używania zakresu dat w celu wykluczenia elementów częściowo indeksowanych

W zakresach Przeszukiwanie zawartości i Podstawowe zbierania elektronicznych materiałów dowodowych nie można użyć zakresu dat w celu wykluczenia częściowo indeksowanych elementów z wyników zapytania wyszukiwania. Oznacza to, że elementy częściowo indeksowane spoza zakresu dat są nadal uwzględniane w statystykach wyszukiwania jako elementy częściowo indeksowane i elementy częściowo indeksowane. W Advanced eDiscovery wyszukiwania elementy częściowo indeksowane można wykluczyć przy użyciu zakresu dat.

Aby obejść to ograniczenie, zalecamy następującą procedurę.

1. Utwórz i uruchom wyszukiwanie za pomocą zapytania wyszukiwania spełniającego Twoje wymagania i zwraca odpowiednie wyniki.

2. Wyeksportuj wyniki wyszukiwania z kroku 1, ale nie uwzględniaj w eksporcie elementów częściowo indeksowanych. W tym celu należy zaznaczyć opcję Wszystkie elementy z wyjątkiem elementów, które mają nierozpoznany **format,** są szyfrowane lub nie zostały zindeksowane z innych powodów. <sup>1</sup>

   ![Eksportowanie opcji danych wyjściowych.](../media/ExportOutputOptions.png)

3. Utwórz i uruchom drugie wyszukiwanie, które korzysta z tego samego zapytania wyszukiwania (i przeszukuje te same lokalizacje), które zostało użyte w kroku 1. Dołącz następującą klauzulę do zapytania pierwotnego przy użyciu **operatora AND** :

   ```text
   <original query> AND ((IndexingErrorCode>0 OR IndexingErrorCode<0) AND sent:date1..date2)
   ```

   Dodanie tej klauzuli spowoduje zwrócenie częściowo indeksowanych elementów, które pasują do pierwotnego zapytania wyszukiwania i należą do określonego zakresu dat. <sup>2</sup>

4. Wyeksportuj wyniki wyszukiwania z kroku 3, a tym razem uwzględnij częściowo indeksowane elementy w eksporcie. W tym celu należy zaznaczyć opcję Wszystkie elementy, łącznie z elementami, które mają nierozpoznany **format,** są szyfrowane lub nie zostały zindeksowane z innych powodów.

   > [!NOTE]
   > <sup>1</sup> Wynik kroku 2 powoduje wyeksportowanie tylko elementów indeksowanych.<br/>
   > <sup>2</sup> Warunek używany w kroku 3 określa tylko elementy z błędami indeksowania, które należą do określonego zakresu dat. Nie zwraca żadnych elementów, które są w pełni zindeksowane. Oznacza to, że elementy wyeksportowane w kroku 4 obejmują tylko elementy nieindeksowane, które należą do zakresu dat. Eksport nie obejmuje elementów indeksowanych. W wyniku tego połączone dane wyjściowe kroków 2 i 4 zawierają wszystkie elementy indeksowane i nieindeksowane, które znajdują się w określonym zakresie dat.

Drugie wyszukiwanie utworzone w kroku 3 i odpowiadający mu eksport umożliwia wyświetlenie i zrozumienie częściowo indeksowanych elementów odpowiadających pierwotnej kwerendzie wyszukiwania. Eksport z drugiego wyszukiwania obejmuje również wszystkie częściowo indeksowane elementy, które zostały wyeksportowane, aby można je było w razie potrzeby przejrzeć.

> [!TIP]
> W poprzedniej procedurze można wyeksportować rzeczywiste wyniki wyszukiwania lub wyeksportować tylko raport.

## <a name="indexing-limits-for-messages"></a>Limity indeksowania wiadomości

W poniższej tabeli opisano limity indeksowania, które mogą powodować zwrócenie wiadomości e-mail jako częściowo zindeksowanego elementu podczas wyszukiwania zbierania elektronicznych materiałów dowodowych w programie Microsoft 365.
  
Aby uzyskać listę limitów indeksowania dotyczących SharePoint, zobacz [Limity](/sharepoint/search-limits) wyszukiwania dotyczące SharePoint online.
  
|**Limit indeksowania**|**Wartość maksymalna**|**Opis**|
|:-----|:-----|:-----|
|Maksymalny rozmiar załączników (z wyjątkiem Excel załączników)  <br/> |150 MB  <br/> |Maksymalny rozmiar załącznika wiadomości e-mail do analizy w celu zindeksowania. Żadne załączniki, których rozmiary są większe niż ten limit, nie będą analizowane w celu zindeksowania, a wiadomość z załącznikiem zostanie oznaczona jako częściowo zindeksowana.  <br/><br/> **Uwaga:** Analizowanie jest procesem, w którym usługa indeksowania wyodrębnia z załącznika tekst, usuwa niepotrzebne znaki, takie jak znaki interpunpunczne i spacje, a następnie dzieli tekst na wyrazy (w procesie nazywanym tokenizacją), które są następnie przechowywane w indeksie.           |
|Maksymalny rozmiar Excel plików  <br/> |4 MB  <br/> |Maksymalny rozmiar pliku Excel w witrynie lub dołączonego do wiadomości e-mail do analizy w celu zindeksowania. Pliki Excel większe niż ten limit nie będą analizowane, a plik lub wiadomość e-mail z dołączonym plikiem zostanie oznaczona jako nieindeksowana.  <br/> |
|Maksymalna liczba załączników  <br/> |250  <br/> |Maksymalna liczba plików dołączonych do wiadomości e-mail do analizy w celu zindeksowania. Jeśli wiadomość ma więcej niż 250 załączników, pierwszych 250 załączników zostanie analizowanych i zindeksowanych, a wiadomość zostanie oznaczona jako częściowo zindeksowana ze względu na dodatkowe załączniki, które nie zostaną rozsyłane.  <br/> |
|Maksymalna głębokość załączników  <br/> |30  <br/> |Maksymalna liczba zagnieżdżonych załączników do analizy. Jeśli na przykład do wiadomości e-mail dołączono inną wiadomość i dołączono do niej dokument programu Word, ten dokument programu Word i dołączona wiadomość zostaną zindeksowane. Takie działanie jest kontynuowane dla maksymalnie 30 zagnieżdżonych załączników.  <br/> |
|Maksymalna liczba załączonych obrazów  <br/> |0  <br/> |Obraz dołączony do wiadomości e-mail jest pomijany przez analizowanie i nie jest indeksowany.  <br/> |
|Maksymalny czas spędzony na analizowaniu elementu  <br/> |30 sekund  <br/> |Maksymalny czas analizowania elementu w celu zindeksowania go wynosi 30 sekund. Jeśli czas analizowania przekracza 30 sekund, element jest oznaczany jako częściowo zindeksowany.  <br/> |
|Maksymalna ilość danych wyjściowych analizowania  <br/> |2 miliony znaków  <br/> |Maksymalna ilość zindeksowanego tekstu wyjściowego analizowania. Jeśli na przykład analizowanie wyodrębniło z dokumentu 8 milionów znaków, zindeksowane zostaną tylko pierwsze 2 miliony.  <br/> |
|Maksymalna liczba tokenów adnotacji  <br/> |2 miliony  <br/> |Gdy wiadomość e-mail jest indeksowana, do każdego wyrazu jest donoszona adnotacja z innymi instrukcjami dotyczącymi przetwarzania, które określają sposób indeksowania tego wyrazu. Każdy zestaw instrukcji dotyczących przetwarzania jest nazywany tokenem adnotacji. Aby zachować jakość usługi w Office 365, istnieje ograniczenie do 2 milionów tokenów adnotacji na wiadomość e-mail.  <br/> |
|Maksymalny rozmiar treści w indeksie  <br/> |67 milionów znaków  <br/> |Całkowita liczba znaków w treści wiadomości e-mail i wszystkich jej załączników. Gdy wiadomość e-mail jest indeksowana, cały tekst w treści wiadomości i wszystkich załączników jest concatenated w jeden ciąg. Maksymalny rozmiar indeksowanego ciągu to 67 milionów znaków.  <br/> |
|Maksymalna liczba unikatowych tokenów w treści  <br/> |1 milion  <br/> |Jak wyjaśniono wcześniej, tokeny są wynikiem wyodrębnienia tekstu z zawartości, usunięcia znaków interpunkcji i spacji, a następnie podzielenia go na wyrazy (nazywane tokenami), które są przechowywane w indeksie. Na przykład fraza zawiera  `"cat, mouse, bird, dog, dog"` 5 tokenów. Ale tylko 4 z nich są tokenami unikatowymi. Istnieje ograniczenie do 1 miliona unikatowych tokenów na wiadomość e-mail, co pomaga zapobiec za duży indeks z przypadkowymi tokenami.  <br/> |
||||

## <a name="more-information-about-partially-indexed-items"></a>Więcej informacji na temat elementów częściowo indeksowanych

- Jak wspomniano wcześniej, ponieważ właściwości wiadomości i dokumentu oraz ich metadane są indeksowane, wyszukiwanie słów kluczowych może zwrócić wyniki, jeśli to słowo kluczowe pojawi się w indeksowanych metadanych. Jednak to samo wyszukiwanie słów kluczowych może nie zwrócić tego samego elementu, jeśli słowo kluczowe występuje tylko w zawartości elementu z nieobsługiwanym typem pliku. W tym przypadku element zostanie zwrócony jako element częściowo indeksowany.

- Jeśli element częściowo indeksowany zostanie uwzględniony w wynikach wyszukiwania ze względu na jego dopasowanie do kryteriów zapytania wyszukiwania, nie zostanie on uwzględniony jako element częściowo indeksowany w szacowanej statystyce wyszukiwania. Ponadto nie będzie on uwzględniany w elementach częściowo indeksowanych podczas eksportowania wyników wyszukiwania.

- Mimo że typ pliku jest obsługiwany w indeksowaniu i jest indeksowany, mogą wystąpić błędy indeksowania lub wyszukiwania, które spowoduje, że plik zostanie zwrócony jako element częściowo zindeksowany. Na przykład wyszukiwanie w dużym pliku Excel może się częściowo zakończyć pomyślnie (ponieważ pierwsze 4 MB są indeksowane), ale kończy się niepowodzeniem, ponieważ został przekroczony limit rozmiaru pliku. W takim przypadku ten sam plik może być zwracany razem z wynikami wyszukiwania i jako element częściowo indeksowany.

- Pliki, które są szyfrowane przy użyciu technologii szyfrowania firmy [Microsoft](encryption.md) i dołączone do wiadomości e-mail, która spełnia kryteria wyszukiwania, mogą być przeglądane i odszyfrowywać podczas eksportowania. Obecnie pliki, które są szyfrowane przy użyciu technologii szyfrowania firmy Microsoft (i przechowywane w SharePoint lub OneDrive dla Firm) są częściowo indeksowane.

- Wiadomości e-mail zaszyfrowane za pomocą S/MIME są częściowo indeksowane. Dotyczy to zaszyfrowanych wiadomości z plikami załączników lub bez nich.

- Wiadomości e-mail chronione za pomocą usługi Azure Rights Management są indeksowane i będą uwzględniane w wynikach wyszukiwania, jeśli są zgodne z zapytaniem wyszukiwania. Wiadomości e-mail chronione prawami są odszyfrowywać i można je wyświetlać w wersji zapoznawczej oraz eksportować. Ta funkcja wymaga przypisania roli odszyfrowywania usługi RMS, która jest domyślnie przypisana do grupy ról Menedżer zbierania elektronicznych materiałów dowodowych.

- Jeśli utworzysz hold oparte na kwerendach, które jest skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych, wszystkie częściowo indeksowane elementy zostaną umieszczone w a hold. Dotyczy to elementów częściowo indeksowanych, które nie są zgodne z kryteriami zapytania wyszukiwania dla hold. Aby uzyskać więcej informacji na temat tworzenia opartych na zapytaniach zbierania elektronicznych materiałów dowodowych, zobacz [Tworzenie blokady zbierania elektronicznych materiałów dowodowych](create-ediscovery-holds.md).

## <a name="see-also"></a>Zobacz też

[Badanie elementów częściowo indeksowanych w zbierania elektronicznych materiałów dowodowych](investigating-partially-indexed-items-in-ediscovery.md)
