---
title: Advanced eDiscovery ograniczenia
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Dowiedz się więcej o limitach przypadków, limitach indeksowania i limitach wyszukiwania, które są Advanced eDiscovery rozwiązania w Microsoft 365.
ms.openlocfilehash: fc658f4502bf510cf34297435db75bd7cdd7c136
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316201"
---
# <a name="limits-in-advanced-ediscovery"></a>Limity w programie Advanced eDiscovery

W tym artykule opisano limity w rozwiązaniu Advanced eDiscovery w programie Microsoft 365.

## <a name="case-and-review-set-limits"></a>Limity dotyczące sprawy i przeglądu

W poniższej tabeli wymieniono limity dotyczące spraw i zestawów recenzji w Advanced eDiscovery.

| Opis limitu | Limit |
|:-----|:-----|
|Łączna liczba dokumentów, które można dodać do sprawy (w przypadku wszystkich zestawów recenzji w przypadku sprawy).  <br/> |3 miliony <br/> |
|Całkowity rozmiar pliku według zestawu ładowania. Obejmuje to ładowanie niezwiązy Office 365 do zestawu recenzji.  <br/> |300 GB <br/> |
|Całkowita ilość danych załadowanych do wszystkich zestawów recenzji w organizacji dziennie.<br/> |2 TB <br/> |
|Maksymalna liczba zestawów obciążenia na przypadek.  <br/> |200 <br/> |
|Maksymalna liczba zestawów recenzji na sprawy.  <br/> |20 <br/> |
|Maksymalna liczba grup tagów na przypadek.  <br/> |1,000 |
|Maksymalna liczba unikatowych tagów na przypadek. <br/> |10001<sup></sup> |
|Maksymalna liczba jednoczesnych zadań w organizacji w celu dodania zawartości do zestawu recenzji. Te zadania mają nazwę **Dodawanie danych do zestawu** recenzji i są wyświetlane na **karcie** Zadania w przypadku.| <sup>102</sup> |
|Maksymalna liczba jednoczesnych zadań w celu dodania zawartości do zestawu recenzji dla każdego użytkownika. Te zadania mają nazwę **Dodawanie danych do zestawu** recenzji i są wyświetlane na **karcie** Zadania w przypadku. | 3 |
|||

## <a name="hold-limits"></a>Limity wstrzymywania

W poniższej tabeli wymieniono limity dotyczące zarchiwnień związanych Advanced eDiscovery przypadku.

| Opis limitu | Limit |
|:-----|:-----|
|Maksymalna liczba zasad blokowania w organizacji. Limit ten obejmuje łączną liczbę zasad przechowywania w przypadku podstawowych zbierania elektronicznych materiałów dowodowych Advanced eDiscovery spraw. <br/> |10.000<sup>3</sup>  <br/> |
|Maksymalna liczba skrzynek pocztowych z pojedynczymi skrzynkami pocztowymi. Ten limit obejmuje łączną liczbę skrzynek pocztowych użytkowników oraz skrzynek pocztowych skojarzonych Microsoft 365, grup Microsoft Teams i Yammer grupy. <br/> |1,000  <br/> |
|Maksymalna liczba witryn w pojedynczym przypadku. Ten limit obejmuje łączną liczbę OneDrive dla Firm, witryn SharePoint oraz witryn skojarzonych z grupami Microsoft 365, witrynami Microsoft Teams i Yammer grupy.  <br/> |100  <br/> |

## <a name="indexing-limits"></a>Limity indeksowania

W poniższej tabeli wymieniono limity indeksowania w Advanced eDiscovery.

| Opis limitu | Limit |
|:-----|:-----|
|Maksymalna liczba znaków wyodrębniona z jednego pliku.  <br/> |10 <sup>milionów4</sup> <br/> |
|Maksymalny rozmiar jednego pliku.   <br/> |150 <sup>MB4</sup> <br/> |
|Maksymalna głębokość osadzonych elementów w dokumencie.  <br/> |<sup>254</sup> <br/> |
|Maksymalny rozmiar plików przetwarzanych za pomocą optycznego rozpoznawania znaków (OCR).  <br/> |24 <sup>MB4</sup> <br/>  
|||

## <a name="search-limits"></a>Limity wyszukiwania

Limity opisane w tej sekcji są związane z używaniem narzędzia wyszukiwania na karcie  Wyszukiwania do zbierania danych dotyczących sprawy. Aby uzyskać więcej informacji, [zobacz Zbieranie danych dotyczących sprawy w Advanced eDiscovery](collecting-data-for-ediscovery.md).

| Opis limitu | Limit |
|:-----|:-----|
|Maksymalna liczba skrzynek pocztowych lub witryn, które można przeszukiwać za pomocą jednego wyszukiwania. |Bez limitu|
|Maksymalna liczba wyszukiwań, które mogą być uruchamiane jednocześnie. |Bez limitu |
|Maksymalna liczba wyszukiwań, które może rozpocząć jeden użytkownik w tym samym czasie. |10 | 
|Maksymalna liczba znaków zapytania wyszukiwania (w tym operatorów i warunków). |10 <sup>0005</sup>|
|Maksymalna liczba znaków zapytania wyszukiwania dla witryn SharePoint i OneDrive dla Firm (w tym operatorów i warunków). |10,000<br>4000 z symbolami wieloznacznych5<sup></sup>|
|Minimalna liczba znaków alfa dla symboli wieloznacznych prefiksów; na przykład **one\**_ lub _* set\***.|3 |  
|Maksymalna liczba wariantów zwracanych podczas używania symbolu wieloznacznego prefiksu w celu wyszukania dokładnej frazy lub użycia symbolu wieloznacznego prefiksu oraz operatora NEAR Boolean ( **NEAR** ). |10 <sup>0006</sup>|
|Maksymalna liczba elementów w skrzynce pocztowej użytkownika wyświetlanych na stronie podglądu w przypadku wyszukiwania. Zostaną wyświetlone najnowsze elementy. |100|
|Maksymalna liczba elementów wyszukiwania ze wszystkich skrzynek pocztowych wyświetlanych na stronie podglądu.|1,000|
|Maksymalna liczba skrzynek pocztowych, których podgląd można wyświetlić w wynikach wyszukiwania.  Jeśli istnieje więcej niż 1000 skrzynek pocztowych zawierających elementy zgodne z zapytaniem wyszukiwania, do podglądu będzie dostępnych tylko 1000 najwyższych skrzynek pocztowych z najwięcej wyników.|1,000|
|Maksymalna liczba elementów z witryn SharePoint i OneDrive dla Firm wyświetlanych na stronie podglądu wyszukiwania. Zostaną wyświetlone najnowsze elementy. |200|
|Maksymalna liczba SharePoint witryn OneDrive dla Firm których można wyświetlić podgląd wyników wyszukiwania. Jeśli istnieje więcej niż 200 witryn zawierających elementy zgodne z zapytaniem wyszukiwania, do podglądu dostępnych jest tylko 200 najwyższych witryn o najbardziej efektach.|200|
|Maksymalna liczba elementów w skrzynce pocztowej folderu publicznego wyświetlana na stronie podglądu podczas wyszukiwania. |100|
|Maksymalna liczba elementów znalezionych we wszystkich elementach skrzynki pocztowej folderu publicznego wyświetlanych na stronie podglądu podczas wyszukiwania. |200|
|Maksymalna liczba skrzynek pocztowych folderów publicznych, których podgląd można wyświetlić w celu wyszukania wyników. Jeśli istnieje więcej niż 500 skrzynek pocztowych folderów publicznych, które zawierają elementy zgodne z zapytaniem wyszukiwania, tylko 500 najwyższych skrzynek pocztowych z najwięcej wyników jest dostępnych do podglądu.|500|
|||

## <a name="search-times"></a>Czas wyszukiwania

Firma Microsoft zbiera informacje o wydajności podczas wyszukiwania prowadzonego przez wszystkie organizacje. Złożoność zapytania wyszukiwania może mieć wpływ na czas wyszukiwania, ale największy wpływ na czas wyszukiwania ma liczba przeszukanych skrzynek pocztowych. Mimo że firma Microsoft nie zawiera umowy dotyczącej poziomu usług dla godzin wyszukiwania, w poniższej tabeli wymieniono średni czas wyszukiwania kolekcji na podstawie liczby skrzynek pocztowych uwzględnionych w wyszukiwaniu.
  
  | Liczba skrzynek pocztowych | Średni czas wyszukiwania |
  |:-----|:-----|
  |100  <br/> |30 sekund  <br/> |
  |1,000  <br/> |45 sekund  <br/> |
  |10,000  <br/> |4 minuty  <br/> |
  |25,000  <br/> |10 minut  <br/> |
  |50,000  <br/> |20 minut  <br/> |
  |100,000  <br/> |25 minut  <br/> |
  |||

## <a name="viewer-limits"></a>Ograniczenia przeglądarki

| Opis limitu | Limit |
|:-----|:-----|
|Maksymalny rozmiar Excel plików, które można wyświetlać w natywnej przeglądarce.  <br/> |4 MB  <br/> |
|||

## <a name="export-limits---final-export-out-of-review-set"></a>Limity eksportowania — końcowy eksport poza zestaw recenzji

Limity opisane w tej sekcji są związane z eksportowaniem dokumentów z zestawu recenzji.

| Opis limitu | Limit |
|:-----|:-----|
|Maksymalny rozmiar pojedynczego eksportu.|5 milionów dokumentów lub 500 GB, w zależności od tego, co jest mniejsze|
|Maksymalna liczba jednoczesnych eksportów według zestawu recenzji. | 1 |
|||

## <a name="review-set-download-limits"></a>Przejrzyj ustawione limity pobierania

| Opis limitu | Limit |
|:-----|:-----|
|Całkowity rozmiar pliku lub maksymalna liczba dokumentów pobranych z zestawu recenzji.  <br/> |3 MB lub 50 <sup>dokumentów7</sup>|
|||

## <a name="notes"></a>Uwagi

> [!NOTE]
> <sup>1</sup> Jest to maksymalna liczba tagów, które można utworzyć w przypadku przypadku. Ten limit nie jest związany z liczbą dokumentów, które można otagować.
>
> <sup>2</sup> Ten limit jest udostępniany podczas eksportowania zawartości z innych narzędzi zbierania elektronicznych materiałów dowodowych. Oznacza to, że jednoczesne eksporty w przeszukiwaniu zawartości i podstawowym zbierania elektronicznych materiałów dowodowych (i dodawaniu zawartości do recenzji zestawów w programie Advanced eDiscovery) są stosowane do tego limitu.
>
> <sup>3</sup> Jeśli w ramach jednej zasady dotyczącej przechowywania wstrzymasz więcej niż 1000 skrzynek pocztowych lub 100 witryn, system automatycznie przeskaluje to hold. Oznacza to, że system automatycznie doda lokalizacje danych do zasad wielokrotnego blokowania, zamiast dodawać je do pojedynczych zasad przechowywania. Nadal jednak obowiązuje limit 10 000 zasad przechowywania przypadków na organizację.
>
> <sup>4</sup> Każdy element, który przekracza limit jednego pliku, będzie wyświetlany jako błąd przetwarzania.
>
> <sup>5</sup> Podczas SharePoint i OneDrive dla Firm adresach URL przeszukiwanych witryn znaki z adresów URL przeszukiwanych witryn są wliczane do tego limitu. Całkowita liczba znaków składa się z:<br>
> - Wszystkie znaki zarówno w polach Użytkownicy, jak i w polach Filtry.
> - Wszystkie filtry uprawnień wyszukiwania, które dotyczą użytkownika.
> - Znaki z dowolnych właściwości lokalizacji w wyszukiwaniu; to między innymi ExchangeLocation, PublicFolderLocation, SharPointLocation, ExchangeLocationExclusion, PublicFolderLocationExclusion, SharePointLocationExclusion, OneDriveLocationExclusion.
>   Na przykład w przypadku wszystkich SharePoint i kont OneDrive w wynikach wyszukiwania zostanie wyświetlonych sześć znaków, ponieważ zarówno dla pola SharePointLocation, jak i oneDriveLocation zostanie wyświetlone słowo "ALL".
>
> <sup>6</sup> W przypadku zapytań nie frazowych (wartość słowa kluczowego, która nie używa cudzysłowów podwójnych) jest używamy specjalnego indeksu prefiksu. Oznacza to, że wyraz występuje w dokumencie, ale nie w miejscu, w którym występuje w dokumencie. Aby wykonać zapytanie frazy (wartość słowa kluczowego z podwójnym cudzysłowem), musimy porównać pozycję w dokumencie dla wyrazów w tej frazie. Oznacza to, że nie można użyć indeksu prefiksu dla zapytań fraz. W tym przypadku wewnętrznie rozszerzamy zapytanie o wszystkie możliwe wyrazy, na które ten prefiks się rozszerza; na przykład argument  **czas\**_ można rozwinąć do argumentu _*"czas LUB czasomierz LUB czasomierz LUB timex OR timeboxed OR ..."**. Limit liczby 10 000 to maksymalna liczba wariantów, do których wyraz może rozwinąć się, a nie liczba dokumentów odpowiadających zapytaniu. Nie ma górnego ograniczenia dla terminów niebędących frazami.
>
> <sup>7</sup> Ten limit dotyczy pobierania wybranych dokumentów z zestawu recenzji. Nie dotyczy eksportowania dokumentów z zestawu recenzji. Aby uzyskać więcej informacji na temat pobierania i eksportowania dokumentów, zobacz [Eksportowanie danych sprawy w programie Advanced eDiscovery](exporting-data-ediscover20.md).
