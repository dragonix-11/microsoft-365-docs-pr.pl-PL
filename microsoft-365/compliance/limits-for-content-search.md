---
title: Limity wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych (standard) w centrum zgodności
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Dowiedz się więcej o limitach dotyczących funkcji wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych (Standard) w portalu zgodności usługi Microsoft Purview.
ms.openlocfilehash: f20c33781b8dd9f92091e1b0c459137a4edd33ed
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014877"
---
# <a name="limits-for-ediscovery-search"></a>Limity wyszukiwania zbierania elektronicznych materiałów dowodowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Różne limity są stosowane do narzędzi wyszukiwania zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview. Obejmuje to wyszukiwania uruchamiane na stronie **wyszukiwania zawartości** i wyszukiwania skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych na stronie **zbierania elektronicznych materiałów dowodowych (Standardowa** ). Te limity pomagają utrzymać kondycję i jakość usług dostarczanych organizacjom. Istnieją również ograniczenia związane z indeksowaniem wiadomości e-mail w Exchange Online wyszukiwania. Nie można modyfikować limitów wyszukiwania zbierania elektronicznych materiałów dowodowych ani indeksowania wiadomości e-mail, ale należy pamiętać o nich, aby uwzględnić te limity podczas planowania, uruchamiania i rozwiązywania problemów z wyszukiwaniami zbierania elektronicznych materiałów dowodowych.

Aby uzyskać limity związane z narzędziem Microsoft Purview eDiscovery (Premium), zobacz [Limity w zakresie zbierania elektronicznych materiałów dowodowych (Premium)](limits-ediscovery20.md)

## <a name="search-limits"></a>Limity wyszukiwania

W poniższej tabeli wymieniono limity wyszukiwania podczas korzystania z narzędzia do wyszukiwania zawartości w portalu zgodności oraz wyszukiwania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Standardowa).

<br>

****

|Opis limitu|Limit|
|---|---|
|Maksymalna liczba skrzynek pocztowych lub witryn, które można przeszukiwać w jednym wyszukiwaniu|Brak limitu <sup>1</sup>|
|Maksymalna liczba wyszukiwań, które mogą być uruchamiane w tym samym czasie w organizacji.|30|
|Maksymalna liczba wyszukiwań w całej organizacji, które mogą być uruchamiane w tym samym czasie.|3|
|Maksymalna liczba wyszukiwań, które pojedynczy użytkownik może rozpocząć w tym samym czasie. Ten limit jest najprawdopodobniej osiągnięty, gdy użytkownik próbuje uruchomić wiele wyszukiwań za pomocą polecenia **Get-ComplianceSearch \|Start-ComplianceSearch** w programie PowerShell Security & Compliance.|10|
|Maksymalna liczba elementów na skrzynkę pocztową użytkownika wyświetlana na stronie podglądu podczas wyświetlania podglądu wyników wyszukiwania zawartości.|100|
|Maksymalna liczba elementów znalezionych we wszystkich skrzynkach pocztowych użytkownika, które mogą być wyświetlane na stronie w wersji zapoznawczej podczas wyświetlania podglądu wyników wyszukiwania. Zostaną wyświetlone najnowsze elementy.|1000 <sup>2</sup>|
|Maksymalna liczba skrzynek pocztowych użytkownika, które można wyświetlić w wersji zapoznawczej wyników wyszukiwania. Jeśli istnieje ponad 1000 skrzynek pocztowych zawierających zawartość zgodną z zapytaniem wyszukiwania, co najwyżej tylko 1000 pierwszych skrzynek pocztowych z największą ilością wyników wyszukiwania będzie dostępnych w wersji zapoznawczej.|1,000|
|Maksymalna liczba elementów znalezionych w witrynach SharePoint i OneDrive dla Firm, które są wyświetlane na stronie podglądu podczas wyświetlania podglądu wyników wyszukiwania. Zostaną wyświetlone najnowsze elementy.|200|
|Maksymalna liczba witryn (w SharePoint i OneDrive dla Firm), które można wyświetlić w podglądzie wyników wyszukiwania. Jeśli istnieje ponad 200 witryn zawierających zawartość zgodną z zapytaniem wyszukiwania, tylko 200 pierwszych witryn z największą liczbą wyników wyszukiwania będzie dostępnych w wersji zapoznawczej.|200|
|Maksymalna liczba elementów na skrzynkę pocztową folderu publicznego wyświetlana na stronie podglądu podczas wyświetlania podglądu wyników wyszukiwania zawartości.|100|
|Maksymalna liczba elementów znalezionych we wszystkich skrzynkach pocztowych folderów publicznych, które są wyświetlane na stronie podglądu podczas wyświetlania podglądu wyników wyszukiwania zawartości.|200|
|Maksymalna liczba skrzynek pocztowych folderów publicznych, które można wyświetlić w podglądzie wyników wyszukiwania. Jeśli istnieje ponad 500 publicznych skrzynek pocztowych zawierających zawartość zgodną z zapytaniem wyszukiwania, tylko 500 pierwszych skrzynek pocztowych folderów publicznych z największą ilością wyników wyszukiwania będzie dostępnych w wersji zapoznawczej.|500|
|Maksymalny rozmiar elementu, który można wyświetlić na stronie podglądu.|10 000 000 bajtów (około 9,5 MB)|
|Maksymalna liczba znaków zapytania wyszukiwania (w tym operatorów i warunków) dla wyszukiwania. <p> **Uwaga:** Ten limit obowiązuje po rozwinieniu zapytania i obejmuje znaki z zapytania słowa kluczowego, filtry uprawnień wyszukiwania zastosowane do użytkownika oraz adresy URL wszystkich lokalizacji lokacji. Oznacza to, że zapytanie zostanie rozwinięte względem każdego słowa kluczowego. Jeśli na przykład zapytanie wyszukiwania zawiera 15 słów kluczowych oraz dodatkowe parametry i warunki, zapytanie zostanie rozwinięte 15 razy, z których każde zawiera inne parametry i warunki w zapytaniu. Dlatego nawet jeśli liczba znaków w zapytaniu wyszukiwania może być poniżej limitu, to rozwinięte zapytanie może przyczynić się do przekroczenia tego limitu.|**Skrzynki pocztowe:** 10 000. <p> **Witryny:** 4000 podczas przeszukiwania wszystkich witryn lub 2000 podczas wyszukiwania maksymalnie 20 witryn. <sup>3</sup>|
|Maksymalna liczba wariantów zwracanych podczas używania symbolu wieloznacznego prefiksu do wyszukiwania dokładnej frazy w zapytaniu wyszukiwania lub w przypadku używania symbolu wieloznacznego prefiksu i operatora logicznego **NEAR** .|10 000 <sup>4</sup>|
|Minimalna liczba znaków alfa dla symboli wieloznacznych prefiksu; na przykład , `time*`, `one*`lub `set*`.|3|
|Maksymalna liczba skrzynek pocztowych w wyszukiwaniu, w których można usuwać elementy, wykonując akcję "wyszukaj i przeczyszczaj" (za pomocą polecenia **New-ComplianceSearchAction -Purge** ). Jeśli wyszukiwanie, dla których wykonujesz akcję przeczyszczania, ma więcej źródłowych skrzynek pocztowych niż ten limit, akcja przeczyszczania zakończy się niepowodzeniem. Aby uzyskać więcej informacji na temat wyszukiwania i przeczyszczania, zobacz [Wyszukiwanie i usuwanie wiadomości e-mail w organizacji](search-for-and-delete-messages-in-your-organization.md).|50,000|
|Maksymalna liczba lokalizacji w wyszukiwaniu, z których można eksportować elementy. Jeśli eksportowane wyszukiwanie ma więcej lokalizacji niż ten limit, eksport zakończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md).|100,000|

> [!NOTE]
> <sup>1</sup> Chociaż możesz przeszukiwać nieograniczoną liczbę skrzynek pocztowych w jednym wyszukiwaniu, możesz pobrać tylko wyeksportowane wyniki wyszukiwania z maksymalnie 100 000 skrzynek pocztowych przy użyciu narzędzia eksportu elektronicznego zbierania elektronicznych materiałów dowodowych w portalu zgodności.
>
> <sup>2</sup> Celem strony w wersji zapoznawczej jest pokazanie ograniczonej próbki wyników. Nawet w przypadku ogromnych wyszukiwań z tysiącami wyników liczba elementów wyświetlanych na stronie w wersji zapoznawczej może i często będzie znacznie mniejsza niż maksymalna możliwa wartość 1000. Aby wyświetlić pełne wyniki wyszukiwania, musisz wyeksportować wyniki.
>
> <sup>3</sup> Podczas wyszukiwania lokalizacji SharePoint i OneDrive dla Firm znaki w adresach URL wyszukiwanych witryn są liczone do tego limitu.
>
> <sup>4</sup> W przypadku zapytań innych niż frazy (wartość słowa kluczowego, która nie używa podwójnego cudzysłowu) używamy specjalnego indeksu prefiksu. Informuje nas to, że słowo występuje w dokumencie, ale nie w miejscu, w którym występuje w dokumencie. Aby wykonać zapytanie frazy (wartość słowa kluczowego z podwójnym cudzysłowem), musimy porównać pozycję w dokumencie dla wyrazów w frazie. Oznacza to, że nie możemy używać indeksu prefiksu dla zapytań fraz. W takim przypadku wewnętrznie rozwiniemy zapytanie o wszystkie możliwe wyrazy, do których rozwija się prefiks; na przykład `"time*"` można rozwinąć do `"time OR timer OR times OR timex OR timeboxed OR ..."`. 10 000 to maksymalna liczba wariantów, do których wyraz może się rozwinąć, a nie liczba dokumentów pasujących do zapytania. Nie ma górnego limitu terminów innych niż frazy.

## <a name="search-times"></a>Czasy wyszukiwania

Firma Microsoft zbiera informacje o wydajności wyszukiwań prowadzonych przez wszystkie organizacje. Chociaż złożoność zapytania wyszukiwania może mieć wpływ na czas wyszukiwania, największym czynnikiem wpływającym na czas wyszukiwania jest liczba wyszukiwanych skrzynek pocztowych. Mimo że firma Microsoft nie udostępnia umowy dotyczącej poziomu usług dla czasów wyszukiwania, w poniższej tabeli wymieniono średni czas wyszukiwania wyszukiwań kolekcji na podstawie liczby skrzynek pocztowych uwzględnionych w wyszukiwaniu.

<br>

****

|Liczba skrzynek pocztowych|Średni czas wyszukiwania|
|---|---|
|100|30 sekund|
|1,000|45 sekund|
|10,000|4 minuty|
|25,000|10 minut|
|50,000|20 minut|
|100,000|25 min.|

## <a name="export-limits"></a>Limity eksportu

W poniższej tabeli wymieniono limity podczas eksportowania wyników wyszukiwania zawartości. Te limity mają również zastosowanie podczas eksportowania zawartości z przypadku zbierania elektronicznych materiałów dowodowych (Standardowa).

<br>

****

|Opis limitu|Limit|
|---|---|
|Maksymalna ilość danych możliwych do eksportowania z jednego wyszukiwania  <p> **Uwaga:** Jeśli wyniki wyszukiwania są większe niż 2 TB, rozważ użycie zakresów dat lub innych typów filtrów w celu zmniejszenia całkowitego rozmiaru wyników wyszukiwania.|2 TB|
|Maksymalna liczba eksportów organizacji w ciągu jednego dnia <p> **Uwaga:** Ten limit jest resetowany codziennie o godzinie 12:00 CZASU UTC|2 TB|
|Maksymalna liczba współbieżnych eksportów, które mogą być uruchamiane w tym samym czasie w organizacji <p> **Uwaga:** Uruchamianie eksportu **Tylko raport** jest liczona względem łącznej liczby równoczesnych eksportów dla organizacji. Jeśli trzech użytkowników wykonuje 3 eksporty, można wykonać tylko jeden eksport. Niezależnie od tego, czy eksportuje raport, czy wyniki wyszukiwania, nie można wykonywać żadnych innych eksportów, dopóki nie zostanie ukończony.|10|
|Maksymalna liczba eksportów, które pojedynczy użytkownik może uruchomić w dowolnym momencie|3|
|Maksymalna liczba skrzynek pocztowych dla wyników wyszukiwania, które można pobrać za pomocą narzędzia eksportu zbierania elektronicznych materiałów dowodowych|100,000|
|Maksymalny rozmiar pliku PST, który można wyeksportować <p> **Uwaga:** Jeśli wyniki wyszukiwania ze skrzynki pocztowej użytkownika są większe niż 10 GB, wyniki wyszukiwania dla skrzynki pocztowej zostaną wyeksportowane w co najmniej dwóch oddzielnych plikach PST. Jeśli zdecydujesz się wyeksportować wszystkie wyniki wyszukiwania w jednym pliku PST, plik PST zostanie rozlany na dodatkowe pliki PST, jeśli całkowity rozmiar wyników wyszukiwania będzie większy niż 10 GB. Jeśli chcesz zmienić ten rozmiar domyślny, możesz edytować rejestr Windows na komputerze używanym do eksportowania wyników wyszukiwania. Zobacz [Zmienianie rozmiaru plików PST podczas eksportowania wyników wyszukiwania zbierania elektronicznych materiałów dowodowych](change-the-size-of-pst-files-when-exporting-results.md). Wyniki wyszukiwania z określonej skrzynki pocztowej nie zostaną podzielone między wiele plików PST, chyba że zawartość z pojedynczej skrzynki pocztowej będzie większa niż 10 GB. Jeśli wybrano opcję wyeksportowania wyników wyszukiwania w jednym pliku PST zawierającym wszystkie komunikaty w jednym folderze, a wyniki wyszukiwania są większe niż 10 GB, elementy są nadal uporządkowane w kolejności chronologicznej, więc zostaną rozlane na dodatkowe pliki PST na podstawie daty wysłania.|10 GB|
|Oceń, z jaką wyniki wyszukiwania ze skrzynek pocztowych i witryn są przekazywane do lokalizacji Storage platformy Azure udostępnionej przez firmę Microsoft.|Maksymalnie 2 GB na godzinę|

## <a name="indexing-limits-for-email-messages"></a>Limity indeksowania wiadomości e-mail

W poniższej tabeli opisano limity indeksowania, które mogą spowodować zwrócenie wiadomości e-mail jako niewyeksplorowanego elementu lub częściowo zaindeksowanego elementu w wynikach wyszukiwania zawartości.

<br>

****

|Limit indeksowania|Wartość maksymalna|Opis|
|---|---|---|
|Maksymalny rozmiar załącznika|150 MB|Maksymalny rozmiar załącznika wiadomości e-mail, który będzie analizowany pod kątem indeksowania. Wszelkie załączniki, które są większe niż ten limit, nie zostaną przeanalizowane pod kątem indeksowania, a komunikat z załącznikiem zostanie oznaczony jako częściowo zindeksowany. <p> **Uwaga:** Analizowanie to proces, w którym usługa indeksowania wyodrębnia tekst z załącznika, usuwa niepotrzebne znaki, takie jak interpunkcja i spacje, a następnie dzieli tekst na słowa (w procesie nazywanym tokenizacją), które są następnie przechowywane w indeksie.|
|Maksymalna liczba załączników|250|Maksymalna liczba plików dołączonych do wiadomości e-mail, które zostaną przeanalizowane pod kątem indeksowania. Jeśli komunikat zawiera więcej niż 250 załączników, pierwsze 250 załączników jest analizowanych i indeksowanych, a komunikat jest oznaczony jako częściowo zindeksowany, ponieważ zawiera dodatkowe załączniki, które nie zostały przeanalizowane.|
|Maksymalna głębokość załącznika|30|Maksymalna liczba zagnieżdżonych załączników, które są analizowane. Jeśli na przykład do wiadomości e-mail jest dołączona inna wiadomość, a dołączona wiadomość zawiera dołączony dokument programu Word, dokument programu Word i dołączona wiadomość zostaną zindeksowane. To zachowanie będzie kontynuowane dla maksymalnie 30 zagnieżdżonych załączników.|
|Maksymalna liczba dołączonych obrazów|0|Obraz dołączony do wiadomości e-mail jest pomijany przez analizator i nie jest indeksowany.|
|Maksymalny czas analizowania elementu|30 sekund|Na analizowanie elementu na potrzeby indeksowania jest poświęcana maksymalnie 30 sekund. Jeśli czas analizowania przekracza 30 sekund, element jest oznaczony jako częściowo zaindeksowany.|
|Maksymalne dane wyjściowe analizatora|2 miliony znaków|Maksymalna ilość danych wyjściowych tekstu z indeksowanego analizatora. Jeśli na przykład analizator wyodrębnił 8 milionów znaków z dokumentu, indeksowane są tylko pierwsze 2 miliony znaków.|
|Maksymalna liczba tokenów adnotacji|2 miliony|Gdy wiadomość e-mail jest indeksowana, każde słowo jest adnotowane za pomocą różnych instrukcji przetwarzania, które określają sposób indeksowania tego słowa. Każdy zestaw instrukcji przetwarzania jest nazywany tokenem adnotacji. Aby utrzymać jakość usług w Office 365, istnieje limit 2 milionów tokenów adnotacji dla wiadomości e-mail.|
|Maksymalny rozmiar treści w indeksie|67 milionów znaków|Całkowita liczba znaków w treści wiadomości e-mail i wszystkich jej załączników. Gdy wiadomość e-mail jest indeksowana, cały tekst w treści wiadomości i we wszystkich załącznikach jest połączony w jeden ciąg. Maksymalny rozmiar indeksowanego ciągu to 67 milionów znaków.|
|Maksymalna liczba unikatowych tokenów w treści|1 milion|Jak wyjaśniono wcześniej, tokeny są wynikiem wyodrębniania tekstu z zawartości, usuwania interpunkcji i spacji, a następnie dzielenia go na wyrazy (nazywane tokenami), które są przechowywane w indeksie. Na przykład fraza `"cat, mouse, bird, dog, dog"` zawiera 5 tokenów. Ale tylko 4 z nich to unikatowe tokeny. Istnieje limit 1 miliona unikatowych tokenów na wiadomość e-mail, co pomaga zapobiec zbyt dużemu rozmiarowi indeksu z losowymi tokenami.|
|||

## <a name="more-information"></a>Więcej informacji

Istnieją dodatkowe limity związane z różnymi aspektami wyszukiwania zawartości, takimi jak indeksowanie zawartości. Aby uzyskać więcej informacji na temat tych limitów, zobacz następujące tematy:

- [Częściowo zaindeksowane elementy w wyszukiwaniu zawartości](partially-indexed-items-in-content-search.md)

- [Badanie częściowo zaindeksowanych elementów w środowisku zbierania elektronicznych materiałów dowodowych](investigating-partially-indexed-items-in-ediscovery.md)

- [Limity wyszukiwania dla usługi SharePoint Online](/sharepoint/search-limits)

Aby uzyskać informacje o wyszukiwaniach zawartości, zobacz:

- [Wyszukiwanie zawartości w Microsoft 365](content-search.md)

- [Wyszukiwanie zawartości w przypadku zbierania elektronicznych materiałów dowodowych (standardowa)](search-for-content-in-core-ediscovery.md)

- [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md)

Aby uzyskać limity przypadków związane zbierania elektronicznych materiałów dowodowych (Standard) i eDiscovery (Premium), zobacz:

- [Limity w zakresie zbierania elektronicznych materiałów dowodowych (Standardowa)](limits-core-ediscovery.md)

- [Limity w zakresie zbierania elektronicznych materiałów dowodowych (Premium)](limits-ediscovery20.md)
