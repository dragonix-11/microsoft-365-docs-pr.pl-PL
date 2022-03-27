---
title: Limity dotyczące wyszukiwania zawartości i podstawowego zbierania elektronicznych materiałów dowodowych w centrum zgodności
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 78fe3147-1979-4c41-83bb-aeccf244368d
description: Dowiedz się więcej o limitach w mocy dla funkcji przeszukiwania zawartości i podstawowych funkcji zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365.
ms.openlocfilehash: ad72dfa1d599a908a56b3b6530433ccb5ed23df4
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715955"
---
# <a name="limits-for-ediscovery-search"></a>Limity dotyczące wyszukiwania zbierania elektronicznych materiałów dowodowych

Różne limity są stosowane do narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365. Obejmuje to wyszukiwania uruchamiane **na stronie** Przeszukiwanie zawartości oraz wyszukiwania skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych na stronie **Podstawowe zbierania** elektronicznych materiałów dowodowych. Te limity pomagają utrzymać kondycję i jakość usług oferowanych organizacjom. Istnieją również ograniczenia związane z indeksowaniem wiadomości e-mail w programie Exchange Online wyszukiwania. Nie można modyfikować limitów dotyczących przeszukiwania zbierania elektronicznych materiałów dowodowych ani indeksowania poczty e-mail, ale należy o nich pamiętać, aby uwzględniać te limity podczas planowania i uruchamiania wyszukiwań zbierania elektronicznych materiałów dowodowych oraz rozwiązywania związanych z nimi problemów.

Aby uzyskać informacje o limitach związanych Advanced eDiscovery narzędzia, [zobacz Limity w programie Advanced eDiscovery](limits-ediscovery20.md)

## <a name="search-limits"></a>Limity wyszukiwania

W poniższej tabeli wymieniono limity wyszukiwania podczas korzystania z narzędzia do wyszukiwania zawartości w aplikacji Centrum zgodności platformy Microsoft 365 oraz wyszukiwania skojarzone z podstawową sprawą zbierania elektronicznych materiałów dowodowych.

<br>

****

|Opis limitu|Limit|
|---|---|
|Maksymalna liczba skrzynek pocztowych lub witryn, które można przeszukiwać za pomocą jednego wyszukiwania|Bez limitu <sup>1</sup>|
|Maksymalna liczba wyszukiwań, które mogą być uruchamiane jednocześnie w organizacji.|30|
|Maksymalna liczba wyszukiwań w całej organizacji, które można uruchomić jednocześnie.|3|
|Maksymalna liczba wyszukiwań, które może rozpocząć jeden użytkownik w tym samym czasie. Ten limit prawdopodobnie oznacza próbę uruchomienia wielu wyszukiwań za pomocą polecenia **Get-ComplianceSearch \|Start-ComplianceSearch** w programie PowerShell w centrum zabezpieczeń & zgodności.|10|
|Maksymalna liczba elementów w skrzynce pocztowej użytkownika, które są wyświetlane na stronie podglądu podczas wyświetlania podglądu wyników przeszukiwania zawartości.|100|
|Maksymalna liczba elementów znalezionych we wszystkich skrzynkach pocztowych użytkowników, które mogą być prawdopodobnie wyświetlane na stronie podglądu podczas wyświetlania podglądu wyników wyszukiwania. Zostaną wyświetlone najnowsze elementy.|1000 <sup>2</sup>|
|Maksymalna liczba skrzynek pocztowych użytkowników, których podgląd można wyświetlić w wynikach wyszukiwania. Jeśli istnieje więcej niż 1000 skrzynek pocztowych zawierających zawartość, która odpowiada zapytaniu wyszukiwania, co najwyżej 1000 najwyższych skrzynek pocztowych z najbardziej wynikami wyszukiwania będzie dostępnych do podglądu.|1,000|
|Maksymalna liczba elementów znalezionych w witrynach SharePoint i OneDrive dla Firm wyświetlanych na stronie podglądu podczas wyświetlania podglądu wyników wyszukiwania. Zostaną wyświetlone najnowsze elementy.|200|
|Maksymalna liczba witryn (w SharePoint i OneDrive dla Firm), których podgląd można wyświetlić w celu wyszukania wyników. Jeśli istnieje więcej niż 200 witryn zawierających łącznie zawartość, która jest odpowiada zapytaniu wyszukiwania, tylko 200 najwyższych witryn z najbardziej wynikami wyszukiwania będzie dostępnych do podglądu.|200|
|Maksymalna liczba elementów w skrzynce pocztowej folderu publicznego, które są wyświetlane na stronie podglądu podczas wyświetlania podglądu wyników wyszukiwania zawartości.|100|
|Maksymalna liczba elementów znalezionych we wszystkich skrzynkach pocztowych folderów publicznych wyświetlanych na stronie podglądu podczas wyświetlania podglądu wyników wyszukiwania zawartości.|200|
|Maksymalna liczba skrzynek pocztowych folderów publicznych, których podgląd można wyświetlić w wynikach wyszukiwania. Jeśli istnieje więcej niż 500 skrzynek pocztowych folderów publicznych, które zawierają zawartość, która jest odpowiada zapytaniu wyszukiwania, do podglądu będą dostępne tylko 500 najwyższych skrzynek pocztowych folderów publicznych z najbardziej wynikami wyszukiwania.|500|
|Maksymalny rozmiar elementu, który można wyświetlić na stronie podglądu.|10 000 000 bajtów (około 9,5 MB)|
|Maksymalna liczba znaków zapytania wyszukiwania (w tym operatorów i warunków) dla wyszukiwania. <p> **Uwaga:** Ten limit szerzy się po rozwinięciu zapytania i zawiera znaki z zapytania słów kluczowych, filtry uprawnień wyszukiwania zastosowane do użytkownika oraz adresy URL wszystkich lokalizacji witryny. Oznacza to, że zapytanie zostanie rozszerzone na wszystkie słowa kluczowe. Jeśli na przykład zapytanie wyszukiwania ma 15 słów kluczowych oraz dodatkowe parametry i warunki, zapytanie zostanie rozwinięte 15 razy, z każdym z innymi parametrami i warunkami w zapytaniu. Tak więc mimo że liczba znaków w zapytaniu wyszukiwania może być poniżej limitu, może to być rozszerzone zapytanie, które może pomóc w przekroczeniu tego limitu.|**Skrzynki pocztowe:** 10 000. <p> **Witryny:** 4000 podczas wyszukiwania we wszystkich witrynach lub 2000 podczas wyszukiwania do 20 witryn. <sup>3</sup>|
|Maksymalna liczba wariantów zwracanych w przypadku użycia symbolu wieloznacznego prefiksu do wyszukania dokładnej frazy w zapytaniu wyszukiwania lub użycia symbolu wieloznacznego prefiksu i operatora NEAR Boolean ( **NEAR** ).|10 000 <sup>4</sup>|
|Minimalna liczba znaków alfa dla symboli wieloznacznych prefiksów. na przykład `time*`, `one*`lub `set*`.|3|
|Maksymalna liczba skrzynek pocztowych w wyszukiwaniu, w których można usuwać elementy, wykonując akcję "wyszukiwanie i przeczyszczanie" (za pomocą polecenia "Czyszczenie" ( **New-ComplianceSearchAction -Purge** ). Jeśli w wyszukiwaniu, w przypadku wykonywania akcji przeczyszczania, jest więcej źródłowych skrzynek pocztowych niż ten limit, akcja przeczyszczania nie powiedzie się. Aby uzyskać więcej informacji na temat wyszukiwania i przeczyszczania, zobacz [Wyszukiwanie i usuwanie wiadomości e-mail w organizacji](search-for-and-delete-messages-in-your-organization.md).|50,000|
|Maksymalna liczba lokalizacji w wyszukiwaniu, z których można eksportować elementy. Jeśli eksportowane wyszukiwanie ma więcej lokalizacji niż ten limit, eksport nie powiedzie się. Aby uzyskać więcej informacji, zobacz [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md).|100,000|

> [!NOTE]
> <sup>1</sup> Mimo że za pomocą jednego wyszukiwania można przeszukać dowolną liczbę skrzynek pocztowych, można pobrać wyniki wyszukiwania tylko z maksymalnie 100 000 skrzynek pocztowych przy użyciu narzędzia eDiscovery Export Tool w Centrum zgodności platformy Microsoft 365.
>
> <sup>2</sup> Celem strony podglądu jest pokazanie ograniczonej próbki wyników. Nawet w przypadku olbrzymich wyszukiwań z tysiącami wyników liczba elementów wyświetlanych na stronie podglądu często może być znacznie mniejsza niż maksymalna możliwa wartość 1000. Aby wyświetlić pełne wyniki wyszukiwania, musisz wyeksportować wyniki.
>
> <sup>3</sup> Podczas SharePoint i OneDrive dla Firm adresach URL przeszukiwanych witryn znaki z adresów URL przeszukiwanych witryn są wliczane do tego limitu.
>
> <sup>4 W zapytaniach</sup> nie frazowych (wartość słowa kluczowego, która nie korzysta z cudzysłowów podwójnych), używamy specjalnego indeksu prefiksu. Oznacza to, że wyraz występuje w dokumencie, ale nie w miejscu, w którym występuje w dokumencie. Aby wykonać zapytanie frazy (wartość słowa kluczowego z podwójnym cudzysłowem), musimy porównać pozycję w dokumencie dla wyrazów w tej frazie. Oznacza to, że nie można użyć indeksu prefiksu dla zapytań fraz. W tym przypadku wewnętrznie rozszerzamy zapytanie o wszystkie możliwe wyrazy, na które ten prefiks się rozszerza; można na przykład `"time*"` rozwinąć do `"time OR timer OR times OR timex OR timeboxed OR ..."`. 10 000 to maksymalna liczba wariantów, do których wyraz może rozwinąć się, a nie liczba dokumentów odpowiadających zapytaniu. Nie ma górnego ograniczenia dla terminów niebędących frazami.

## <a name="search-times"></a>Czas wyszukiwania

Firma Microsoft zbiera informacje o wydajności podczas wyszukiwania prowadzonego przez wszystkie organizacje. Złożoność zapytania wyszukiwania może mieć wpływ na czas wyszukiwania, ale największy wpływ na czas wyszukiwania ma liczba przeszukanych skrzynek pocztowych. Mimo że firma Microsoft nie zawiera umowy dotyczącej poziomu usług dla godzin wyszukiwania, w poniższej tabeli wymieniono średni czas wyszukiwania kolekcji na podstawie liczby skrzynek pocztowych uwzględnionych w wyszukiwaniu.

<br>

****

|Liczba skrzynek pocztowych|Średni czas wyszukiwania|
|---|---|
|100|30 sekund|
|1,000|45 sekund|
|10,000|4 minuty|
|25,000|10 minut|
|50,000|20 minut|
|100,000|25 minut|

## <a name="export-limits"></a>Limity eksportu

W poniższej tabeli wymieniono limity podczas eksportowania wyników wyszukiwania zawartości. Limity te mają również zastosowanie w przypadku eksportowania zawartości ze sprawy core eDiscovery.

<br>

****

|Opis limitu|Limit|
|---|---|
|Maksymalna ilość eksportowanych danych z pojedynczego wyszukiwania  <p> **Uwaga:** Jeśli rozmiar wyników wyszukiwania jest większy niż 2 TB, rozważ użycie zakresów dat lub filtrów innych typów w celu zmniejszenia całkowitego rozmiaru wyników wyszukiwania.|2 TB|
|Maksymalna liczba organizacji może eksportować w ciągu jednego dnia <p> **Uwaga:** Ten limit jest resetowany codziennie o godzinie 12:00 czasu UTC|2 TB|
|Maksymalna liczba jednoczesnych eksportów, które mogą być wykonywane jednocześnie w organizacji <p> **Uwaga:** Uruchamianie raportu **Tylko eksport jest** wliczane do łącznej liczby jednoczesnych eksportów dla organizacji. Jeśli trzech użytkowników wykonuje 3 eksporty, wówczas można wykonać tylko jeden eksport. Niezależnie od tego, czy raport jest eksportowany, czy też wyniki wyszukiwania, żadne inne eksporty nie są możliwe do momentu jego ukończenia.|10|
|Maksymalny eksport jednego użytkownika może być uruchamiany w dowolnym momencie|3|
|Maksymalna liczba skrzynek pocztowych wyników wyszukiwania, które można pobrać za pomocą narzędzia eDiscovery Export Tool|100,000|
|Maksymalny rozmiar pliku PST, który można wyeksportować <p> **Uwaga:** Jeśli wyniki wyszukiwania ze skrzynki pocztowej użytkownika są większe niż 10 GB, wyniki wyszukiwania dotyczące skrzynki pocztowej zostaną wyeksportowane do dwóch (lub więcej) osobnych plików PST. Jeśli zdecydujesz się wyeksportować wszystkie wyniki wyszukiwania w jednym pliku PST, plik TEN zostanie rozlany do dodatkowych plików PST, jeśli całkowity rozmiar wyników wyszukiwania będzie większy niż 10 GB. Jeśli chcesz zmienić ten rozmiar domyślny, możesz edytować rejestr Windows na komputerze, którego używasz do eksportowania wyników wyszukiwania. Zobacz [Zmienianie rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych](change-the-size-of-pst-files-when-exporting-results.md). Wyniki wyszukiwania z określonej skrzynki pocztowej nie zostaną podzielone między wiele plików PST, chyba że zawartość z jednej skrzynki pocztowej będzie większa niż 10 GB. Jeśli wyeksportowano wyniki wyszukiwania w jednym pliku PST, który zawiera wszystkie wiadomości w jednym folderze, a wyniki wyszukiwania są większe niż 10 GB, elementy są nadal uporządkowane w porządku chronologicznym, więc zostaną rozlane do dodatkowych plików PST na podstawie daty wysłania.|10 GB|
|Oceń, z jaką wyniki wyszukiwania ze skrzynek pocztowych i witryn są przekazywane do lokalizacji adresatów danych Storage Azure dostarczonych przez firmę Microsoft.|Maksymalnie 2 GB na godzinę|

## <a name="indexing-limits-for-email-messages"></a>Limity indeksowania wiadomości e-mail

W poniższej tabeli opisano limity indeksowania, które mogą powodować zwrócenie wiadomości e-mail jako elementu nieindeksowanego lub częściowo indeksowanego elementu w wynikach wyszukiwania zawartości.

<br>

****

|Limit indeksowania|Wartość maksymalna|Opis|
|---|---|---|
|Maksymalny rozmiar załącznika|150 MB|Maksymalny rozmiar załącznika wiadomości e-mail do analizy w celu zindeksowania. Żadne załączniki, których rozmiary są większe niż ten limit, nie będą analizowane w celu zindeksowania, a wiadomość z załącznikiem zostanie oznaczona jako częściowo zindeksowana. <p> **Uwaga:** Analizowanie jest procesem, w którym usługa indeksowania wyodrębnia z załącznika tekst, usuwa niepotrzebne znaki, takie jak znaki interpunpunczne i spacje, a następnie dzieli tekst na wyrazy (w procesie nazywanym tokenizacją), które są następnie przechowywane w indeksie.|
|Maksymalna liczba załączników|250|Maksymalna liczba plików dołączonych do wiadomości e-mail do analizy w celu zindeksowania. Jeśli wiadomość ma więcej niż 250 załączników, pierwszych 250 załączników zostanie analizowanych i zindeksowanych, a wiadomość zostanie oznaczona jako częściowo zindeksowana ze względu na dodatkowe załączniki, które nie zostaną rozsyłane.|
|Maksymalna głębokość załączników|30|Maksymalna liczba zagnieżdżonych załączników do analizy. Jeśli na przykład do wiadomości e-mail dołączono inną wiadomość i dołączono do niej dokument programu Word, ten dokument programu Word i dołączona wiadomość zostaną zindeksowane. Takie działanie jest kontynuowane dla maksymalnie 30 zagnieżdżonych załączników.|
|Maksymalna liczba załączonych obrazów|0|Obraz dołączony do wiadomości e-mail jest pomijany przez analizowanie i nie jest indeksowany.|
|Maksymalny czas spędzony na analizowaniu elementu|30 sekund|Maksymalny czas analizowania elementu w celu zindeksowania go wynosi 30 sekund. Jeśli czas analizowania przekracza 30 sekund, element jest oznaczany jako częściowo zindeksowany.|
|Maksymalna ilość danych wyjściowych analizowania|2 miliony znaków|Maksymalna ilość zindeksowanego tekstu wyjściowego analizowania. Jeśli na przykład analizowanie wyodrębniło z dokumentu 8 milionów znaków, zindeksowane zostaną tylko pierwsze 2 miliony.|
|Maksymalna liczba tokenów adnotacji|2 miliony|Gdy wiadomość e-mail jest indeksowana, do każdego wyrazu jest donoszona adnotacja z innymi instrukcjami dotyczącymi przetwarzania, które określają sposób indeksowania tego wyrazu. Każdy zestaw instrukcji dotyczących przetwarzania jest nazywany tokenem adnotacji. Aby zachować jakość usługi w Office 365, istnieje ograniczenie do 2 milionów tokenów adnotacji na wiadomość e-mail.|
|Maksymalny rozmiar treści w indeksie|67 milionów znaków|Całkowita liczba znaków w treści wiadomości e-mail i wszystkich jej załączników. Gdy wiadomość e-mail jest indeksowana, cały tekst w treści wiadomości i wszystkich załączników jest concatenated w jeden ciąg. Maksymalny rozmiar indeksowanego ciągu to 67 milionów znaków.|
|Maksymalna liczba unikatowych tokenów w treści|1 milion|Jak wyjaśniono wcześniej, tokeny są wynikiem wyodrębnienia tekstu z zawartości, usunięcia znaków interpunkcji i spacji, a następnie podzielenia go na wyrazy (nazywane tokenami), które są przechowywane w indeksie. Na przykład fraza zawiera `"cat, mouse, bird, dog, dog"` 5 tokenów. Ale tylko 4 z nich są tokenami unikatowymi. Istnieje ograniczenie do 1 miliona unikatowych tokenów na wiadomość e-mail, co pomaga zapobiec za duży indeks z przypadkowymi tokenami.|
|||

## <a name="more-information"></a>Więcej informacji

Istnieją dodatkowe ograniczenia dotyczące różnych aspektów wyszukiwania zawartości, takich jak indeksowanie zawartości. Aby uzyskać więcej informacji o tych limitach, zobacz następujące tematy:

- [Elementy częściowo indeksowane w przeszukiwaniu zawartości](partially-indexed-items-in-content-search.md)

- [Badanie elementów częściowo indeksowanych w zbierania elektronicznych materiałów dowodowych](investigating-partially-indexed-items-in-ediscovery.md)

- [Limity wyszukiwania dotyczące SharePoint Online](/sharepoint/search-limits)

Aby uzyskać informacje na temat przeszukiwania zawartości, zobacz:

- [Wyszukiwanie zawartości w programie Microsoft 365](content-search.md)

- [Wyszukiwanie zawartości w podstawowej sprawie zbierania elektronicznych materiałów dowodowych](search-for-content-in-core-ediscovery.md)

- [Zapytania słów kluczowych i warunki wyszukiwania dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md)

Aby uzyskać limity dotyczące podstawowych zbierania elektronicznych materiałów dowodowych Advanced eDiscovery, zobacz:

- [Ograniczenia podstawowe zbierania elektronicznych materiałów dowodowych](limits-core-ediscovery.md)

- [Limity w programie Advanced eDiscovery](limits-ediscovery20.md)
