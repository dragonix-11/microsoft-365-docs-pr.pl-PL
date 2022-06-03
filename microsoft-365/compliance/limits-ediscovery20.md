---
title: Limity zbierania elektronicznych materiałów dowodowych (wersja Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się więcej o limitach przypadków, limitach indeksowania i limitach wyszukiwania dla rozwiązania zbierania elektronicznych materiałów dowodowych (Premium) w Microsoft 365.
ms.openlocfilehash: 3b52b36ebdaca429b37cf5784281d22d4dd4be74
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65864480"
---
# <a name="limits-in-ediscovery-premium"></a>Limity w zakresie zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W tym artykule opisano limity w rozwiązaniu Microsoft Purview eDiscovery (Premium) w Microsoft 365.

## <a name="case-and-review-set-limits"></a>Limity zestawu przypadków i przeglądów

W poniższej tabeli wymieniono limity dotyczące przypadków i zestawów przeglądów w obszarze eDiscovery (Premium).

|Opis limitu|Limit przypadków klasycznych|Limit nowych przypadków|
|---|---|---|
|Całkowita liczba dokumentów, które można dodać do sprawy (dla wszystkich zestawów przeglądów w danym przypadku).|3 miliony|40 milionów|
|Całkowity rozmiar pliku na zestaw ładowania. Obejmuje to ładowanie Office 365 do zestawu przeglądów.|300 GB|1 TB|
|Łączna ilość danych załadowanych do wszystkich zestawów przeglądów w organizacji dziennie.<br/>|2 TB|2 TB|
|Maksymalna liczba zestawów obciążenia na przypadek.|200|200|
|Maksymalna liczba zestawów przeglądów na przypadek.|20|20|
|Maksymalna liczba grup tagów na przypadek.|1,000|1,000|
|Maksymalna liczba unikatowych tagów na przypadek.|1000<sup>1</sup>|1000<sup>1</sup>|
|Maksymalna liczba współbieżnych zadań w organizacji w celu dodania zawartości do zestawu przeglądów. Te zadania mają nazwę **Dodawanie danych do zestawu przeglądów** i są wyświetlane na karcie **Zadania** w danym przypadku.|10<sup>2</sup>|10<sup>2</sup>|
|Maksymalna liczba współbieżnych zadań dodawania zawartości do zestawu przeglądów na użytkownika. Te zadania mają nazwę **Dodawanie danych do zestawu przeglądów** i są wyświetlane na karcie **Zadania** w danym przypadku.|3|3|

## <a name="hold-limits"></a>Limity blokady

W poniższej tabeli wymieniono limity dotyczące blokad skojarzonych z przypadkiem zbierania elektronicznych materiałów dowodowych (Premium).

| Opis limitu | Limit |
|:-----|:-----|
|Maksymalna liczba zasad blokady dla organizacji. Ten limit obejmuje łączną sumę zasad blokady w przypadkach Microsoft Purview eDiscovery (Standard) i Microsoft Purview eDiscovery (Premium). <br/> |10.000<sup>3</sup>  <br/> |
|Maksymalna liczba skrzynek pocztowych w jednym przypadku blokady. Ten limit obejmuje łączną sumę skrzynek pocztowych użytkowników oraz skrzynki pocztowe skojarzone z grupami Grupy Microsoft 365, Microsoft Teams i Yammer. <br/> |1,000  <br/> |
|Maksymalna liczba witryn w jednym przypadku blokady. Ten limit obejmuje łączną sumę witryn OneDrive dla Firm, witryn SharePoint oraz witryn skojarzonych z grupami Grupy Microsoft 365, Microsoft Teams i Yammer.  <br/> |100  <br/> |

## <a name="indexing-limits"></a>Limity indeksowania

W poniższej tabeli wymieniono limity indeksowania w obszarze eDiscovery (Premium).

|Opis limitu|Limit|
|---|---|
|Maksymalna liczba znaków wyodrębnionych z jednego pliku.|10 mln<sup>4</sup>|
|Maksymalny rozmiar pojedynczego pliku.|150 MB<sup>4</sup>|
|Maksymalna głębokość osadzonych elementów w dokumencie.|25<sup>4</sup>|
|Maksymalny rozmiar plików przetwarzanych przez optyczne rozpoznawanie znaków (OCR).|24 MB<sup>4</sup> <br/> |
|Maksymalna zaawansowana przepływność indeksowania | 2 GB na godzinę |

## <a name="search-limits"></a>Limity wyszukiwania

Limity opisane w tej sekcji są związane z używaniem narzędzia wyszukiwania na karcie **Wyszukiwania** w celu zbierania danych dla danego przypadku. Aby uzyskać więcej informacji, zobacz [Zbieranie danych w przypadku zbierania elektronicznych materiałów dowodowych (Premium)](collecting-data-for-ediscovery.md).

|Opis limitu|Limit|
|---|---|
|Maksymalna liczba skrzynek pocztowych lub witryn, które można przeszukiwać w jednym wyszukiwaniu.|Brak limitu|
|Maksymalna liczba wyszukiwań, które mogą być uruchamiane w tym samym czasie.|Brak limitu|
|Maksymalna liczba wyszukiwań, które pojedynczy użytkownik może rozpocząć w tym samym czasie.|10|
|Maksymalna liczba znaków zapytania wyszukiwania (w tym operatory i warunki).|10 000<sup>5</sup>|
|Maksymalna liczba znaków zapytania wyszukiwania dla witryn SharePoint i OneDrive dla Firm (w tym operatorów i warunków).|10,000<br>4000 z symbolami wieloznaczymi<sup>5</sup>|
|Minimalna liczba znaków alfa dla symboli wieloznacznych prefiksu; na przykład **one\**_ lub _* set\***.|3|
|Maksymalna liczba wariantów zwracanych w przypadku używania symbolu wieloznacznego prefiksu do wyszukiwania dokładnej frazy lub używania symbolu wieloznacznego prefiksu i operatora wartości logicznej **NEAR** .|10 000<sup>6</sup>|
|Maksymalna liczba elementów na skrzynkę pocztową użytkownika, które są wyświetlane na stronie podglądu dla wyszukiwań. Zostaną wyświetlone najnowsze elementy.|100|
|Maksymalna liczba elementów ze wszystkich skrzynek pocztowych wyświetlanych na stronie podglądu wyszukiwania.|1,000|
|Maksymalna liczba skrzynek pocztowych, dla których można wyświetlić podgląd wyników wyszukiwania.  Jeśli istnieje ponad 1000 skrzynek pocztowych zawierających elementy zgodne z zapytaniem wyszukiwania, tylko 1000 pierwszych skrzynek pocztowych z największą ilością wyników jest dostępnych w wersji zapoznawczej.|1,000|
|Maksymalna liczba elementów z witryn SharePoint i OneDrive dla Firm wyświetlanych na stronie w wersji zapoznawczej w celu wyszukiwania. Zostaną wyświetlone najnowsze elementy.|200|
|Maksymalna liczba witryn SharePoint i OneDrive dla Firm, dla których można wyświetlić podgląd wyników wyszukiwania. Jeśli istnieje ponad 200 witryn, które zawierają elementy zgodne z zapytaniem wyszukiwania, tylko 200 pierwszych witryn z największą ilością wyników jest dostępnych w wersji zapoznawczej.|200|
|Maksymalna liczba elementów na skrzynkę pocztową folderu publicznego wyświetlana na stronie podglądu dla wyszukiwań.|100|
|Maksymalna liczba elementów znalezionych we wszystkich elementach skrzynki pocztowej folderu publicznego wyświetlanych na stronie podglądu dla wyszukiwań.|200|
|Maksymalna liczba skrzynek pocztowych folderów publicznych, które można wyświetlić w wersji zapoznawczej dla wyników wyszukiwania. Jeśli istnieje ponad 500 publicznych skrzynek pocztowych zawierających elementy zgodne z zapytaniem wyszukiwania, tylko 500 pierwszych skrzynek pocztowych z największą ilością wyników jest dostępnych w wersji zapoznawczej.|500|
|Maksymalny rozmiar elementu, który można wyświetlić na przykładowej stronie kolekcji roboczej.|10 000 000 bajtów (około 9,5 MB)|

## <a name="search-times"></a>Czasy wyszukiwania

Firma Microsoft zbiera informacje o wydajności wyszukiwań prowadzonych przez wszystkie organizacje. Chociaż złożoność zapytania wyszukiwania może mieć wpływ na czas wyszukiwania, największym czynnikiem wpływającym na czas wyszukiwania jest liczba wyszukiwanych skrzynek pocztowych. Mimo że firma Microsoft nie udostępnia umowy dotyczącej poziomu usług dla czasów wyszukiwania, w poniższej tabeli wymieniono średni czas wyszukiwania wyszukiwań kolekcji na podstawie liczby skrzynek pocztowych uwzględnionych w wyszukiwaniu.
  
|Liczba skrzynek pocztowych|Średni czas wyszukiwania|
|---|---|
|100|30 sekund|
|1,000|45 sekund|
|10,000|4 minuty|
|25,000|10 minut|
|50,000|20 minut|
|100,000|25 min.|

## <a name="viewer-limits"></a>Limity przeglądarki

|Opis limitu|Limit|
|---|---|
|Maksymalny rozmiar pliku Excel, który można wyświetlić w natywnej przeglądarce.|4 MB|

## <a name="export-limits---final-export-out-of-review-set"></a>Limity eksportu — eksport końcowy z zestawu przeglądów

Limity opisane w tej sekcji są związane z eksportowaniem dokumentów z zestawu przeglądów.

|Opis limitu|Limit|
|---|---|
|Maksymalny rozmiar pojedynczego eksportu.|5 milionów dokumentów lub 500 GB, w zależności od tego, która z tych wartości jest mniejsza|
|Maksymalna liczba współbieżnych eksportów na zestaw przeglądów.|1|

## <a name="review-set-download-limits"></a>Przejrzyj ustawianie limitów pobierania

|Opis limitu|Limit|
|---|---|
|Całkowity rozmiar pliku lub maksymalna liczba dokumentów pobranych z zestawu przeglądów.|3 MB lub 50 dokumentów<sup>7</sup>|


## <a name="reference-notes"></a>Notatki referencyjne
<sup>1</sup> Jest to maksymalna liczba tagów, które można utworzyć w danym przypadku. Ten limit nie jest związany z liczbą dokumentów, które można otagować.

<sup>2</sup> Ten limit jest współużytkowany z eksportowaniem zawartości w innych narzędziach zbierania elektronicznych materiałów dowodowych. Oznacza to, że względem tego limitu są stosowane współbieżne eksporty w wyszukiwaniu zawartości i zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) (oraz dodawanie zawartości do przeglądania zestawów zbierania elektronicznych materiałów dowodowych (Premium)).

<sup>3</sup> Po wstrzymaniu ponad 1000 skrzynek pocztowych lub 100 witryn w zasadach jednego wstrzymania system automatycznie skaluje blokadę zgodnie z potrzebami. Oznacza to, że system automatycznie doda lokalizacje danych do wielu zasad przechowywania, zamiast dodawać je do jednej zasady blokady. Jednak limit 10 000 zasad przechowywania spraw na organizację nadal ma zastosowanie.

<sup>4</sup> Każdy element, który przekracza limit pojedynczego pliku, zostanie wyświetlony jako błąd przetwarzania.

<sup>5</sup> Podczas wyszukiwania lokalizacji SharePoint i OneDrive dla Firm znaki w adresach URL wyszukiwanych witryn są liczone względem tego limitu. Całkowita liczba znaków składa się z:

  - Wszystkie znaki w polach Użytkownicy i Filtry.
  - Wszystkie filtry uprawnień wyszukiwania, które mają zastosowanie do użytkownika.
  - Znaki z dowolnych właściwości lokalizacji w wyszukiwaniu, w tym ExchangeLocation, PublicFolderLocation, SharPointLocation, ExchangeLocationExclusion, PublicFolderLocationExclusion, SharePointLocationExclusion i OneDriveLocationExclusion. Na przykład uwzględnienie wszystkich witryn SharePoint i kont OneDrive w wyszukiwaniu będzie liczone jako sześć znaków, ponieważ wyraz "ALL" będzie wyświetlany zarówno dla pola SharePointLocation, jak i OneDriveLocation.

<sup>6</sup> W przypadku zapytań innych niż frazy (wartość słowa kluczowego, która nie używa podwójnego cudzysłowu) używamy specjalnego indeksu prefiksu. Informuje nas to, że słowo występuje w dokumencie, ale nie w miejscu, w którym występuje w dokumencie. Aby wykonać zapytanie frazy (wartość słowa kluczowego z podwójnym cudzysłowem), musimy porównać pozycję w dokumencie dla wyrazów w frazie. Oznacza to, że nie możemy używać indeksu prefiksu dla zapytań fraz. W takim przypadku wewnętrznie rozwiniemy zapytanie o wszystkie możliwe wyrazy, do których rozwija się prefiks; na przykład  **time\**_ może rozwinąć się do _*"czasomierza LUB czasomierza LUB czasu LUB czasu lub czasomierza lub przedziału czasowego LUB ..."**. Limit 10 000 to maksymalna liczba wariantów, do których wyraz może się rozwinąć, a nie liczba dokumentów pasujących do zapytania. Nie ma górnego limitu terminów innych niż frazy.

<sup>7</sup> Okres przedwyższania obiektów blob platformy Azure, w których przechowywane są kolekcje zbierania elektronicznych materiałów dowodowych (Premium), wynosi jeden rok. Każda kolekcja utworzona rok temu może nie być już dostępna.
 
<sup>8</sup> Ten limit dotyczy pobierania wybranych dokumentów z zestawu przeglądów. Nie dotyczy eksportowania dokumentów z zestawu przeglądów. Aby uzyskać więcej informacji na temat pobierania i eksportowania dokumentów, zobacz [Export case data in eDiscovery (Premium) (Eksportowanie danych przypadków w usłudze eDiscovery (Premium)).](exporting-data-ediscover20.md)
