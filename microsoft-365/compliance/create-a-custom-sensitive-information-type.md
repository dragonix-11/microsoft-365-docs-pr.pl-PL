---
title: Tworzenie niestandardowych typów informacji poufnych
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
description: Dowiedz się, jak tworzyć, modyfikować, usuwać i testować niestandardowe typy informacji poufnych w Centrum zgodności.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2526ab9fdde4e5cedbbf3e831e6ec8ac9a6a5747
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014904"
---
# <a name="create-custom-sensitive-information-types-in-the-compliance-center"></a>Tworzenie niestandardowych typów informacji poufnych w Centrum zgodności

Jeśli wstępnie skonfigurowane typy informacji poufnych nie spełniają Twoich potrzeb, możesz utworzyć własne niestandardowe typy informacji poufnych, które są w pełni definiowane, lub skopiować jeden ze wstępnie skonfigurowanych i zmodyfikować te typy.

Niestandardowe typy informacji poufnych, które są dodawane przy użyciu tej metody, są dodawane do pakietu reguł `Microsoft.SCCManaged.CustomRulePack`o nazwie .

Istnieją dwa sposoby tworzenia nowego typu informacji poufnych:

- [od podstaw, gdzie wszystkie elementy są w pełni definiowane](#create-a-custom-sensitive-information-type)
- [Kopiowanie i modyfikowanie istniejącego typu informacji poufnych](#copy-and-modify-a-sensitive-information-type)


## <a name="before-you-begin"></a>Przed rozpoczęciem

- Należy zapoznać się z typami informacji poufnych i ich komponami. Zobacz Informacje [o typach informacji poufnych](sensitive-information-type-learn-about.md). Ważne jest zrozumienie ról:
    - [wyrażenia regularne](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/) — Microsoft 365 typów informacji poufnych używa aparatu Boost.RegEx 5.1.3
    - listy słów kluczowych — możesz utworzyć własne, definiując typ informacji poufnych, lub wybrać z istniejących list słów kluczowych
    - [słownik słów kluczowych](create-a-keyword-dictionary.md)
    - [Funkcje typów informacji poufnych](sit-functions.md)
    - [poziomy ufności](sensitive-information-type-learn-about.md#more-on-confidence-levels)
 
- Aby utworzyć, przetestować i wdrożyć niestandardowy typ informacji poufnych za pomocą interfejsu użytkownika, musisz mieć uprawnienia administratora globalnego lub administratora zgodności. Zobacz [Role administratora w programie](/office365/admin/add-users/about-admin-roles) Office 365.

- Twoja organizacja musi mieć subskrypcję, na przykład Office 365 Enterprise, która obejmuje zapobieganie utracie danych (DLP, Data Loss Prevention). Zobacz [Opis usługi obsługi wiadomości i zgodności](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc). 


> [!IMPORTANT]
> Dział obsługi klienta & firmy Microsoft nie może pomóc w tworzeniu niestandardowych klasyfikacji lub wzorców wyrażeń regularnych. Inżynierowie pomocy technicznej mogą zapewnić ograniczoną obsługę tej funkcji, na przykład zapewnienie przykładowych wzorców wyrażeń regularnych na potrzeby testowania lub pomoc przy rozwiązywaniu problemów z istniejącym wzorcem wyrażeń regularnych, które nie wyzwalają zgodnie z oczekiwaniami, ale nie mogą zapewniać gwarancji, że jakiekolwiek niestandardowe opracowywanie dopasowywania zawartości spełni Twoje wymagania lub obowiązki.

## <a name="create-a-custom-sensitive-information-type"></a>Tworzenie niestandardowego typu informacji poufnych

Za pomocą tej procedury można utworzyć nowy, w pełni definiowywny typ informacji poufnych. 

1. W Centrum zgodności przejdź do tematu **Typy** poufnych informacji klasyfikacji \> **danych** i wybierz **pozycję Utwórz typ informacji poufnych**.

2. Wypełnij wartości w **polach Nazwa** i **Opis** , a następnie wybierz przycisk **Dalej**.

3. Wybierz **pozycję Utwórz wzorzec**. Podczas definiowania nowego typu informacji poufnych można utworzyć wiele wzorców z różnymi elementami i poziomami ufności.

4. Wybierz domyślny poziom ufności wzorca. Dopuszczalne wartości to **: Niska ufność**, **Średnia ufność** i **Wysoka ufność**.

5. Wybierz i **zdefiniuj element Podstawowy**. Elementem podstawowym może **być wyrażenie regularne** z opcjonalnym modułem sprawdzania prawidłowego, listą Słów **kluczowych,** słownikiem Słowo kluczowe lub jedną ze wstępnie skonfigurowanych **funkcji**. Aby uzyskać więcej informacji na temat funkcji DLP, zobacz [Funkcje typów informacji poufnych](sit-functions.md). Aby uzyskać więcej informacji na temat daty i prawidłowych wartości sprawdzanych, zobacz Sprawdzanie prawidłowoności wyrażeń regularnych typu informacji [poufnych](sit-regex-validators-additional-checks.md#sensitive-information-type-regular-expression-validators).

6. Wypełnij wartość dla wartości **Odległość znaku**.

7. (Opcjonalnie) Dodaj elementy dodatkowe, jeśli takie są. Elementami obsługowymi może być zwykłe wyrażenie z opcjonalnym modułem sprawdzania prawidłowego, listą słów kluczowych, słownikiem słów kluczowych lub jedną z wstępnie zdefiniowanych funkcji. Elementy wsparcia mogą mieć własną **konfigurację odległości znaku** . 

8. (Opcjonalnie) Dodaj wszelkie [**dodatkowe testy**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) z listy dostępnych testów.

9. Wybierz pozycję **Utwórz**.

10. Wybierz przycisk **Dalej**.

11. Wybierz zalecany **poziom ufności** dla tego typu informacji poufnych.

12. Sprawdź swoje ustawienie i wybierz pozycję **Prześlij**.

    > [!IMPORTANT]
    > Microsoft 365 przeszukiwarce wyszukiwania do identyfikowania i klasyfikowania informacji poufnych w witrynach SharePoint Online i OneDrive dla Firm internetowych. Aby zidentyfikować nowy niestandardowy typ informacji poufnych w istniejącej zawartości, zawartość musi zostać ponownie przeszukana. Zawartość jest przeszukiwana zgodnie z harmonogramem, ale można ręcznie ponownie przeszukiwać zawartość zbioru witryn, listy lub biblioteki. Aby uzyskać więcej informacji, [zobacz Ręczne żądanie](/sharepoint/crawl-site-content) przeszukiwania i ponownego indeksowania witryny, biblioteki lub listy.

13. Na **stronie Klasyfikacja** danych zobaczysz wszystkie typy informacji poufnych na liście. Wybierz **pozycję Odśwież** , a następnie wyszukaj utworzony typ informacji poufnych lub skorzystaj z narzędzia wyszukiwania.

### <a name="copy-and-modify-a-sensitive-information-type"></a>Kopiowanie i modyfikowanie typu informacji poufnych

Ta procedura umożliwia utworzenie nowego typu informacji poufnych na podstawie istniejącego typu informacji poufnych. 

> [!NOTE]
> Nie można kopiować tych sits:
> - Numer prawa jazdy z Kanady
> - Numer prawa jazdy w UE
> - Krajowy numer identyfikacyjny UE
> - Numer paszportu UE
> - Numer PE PE PEŁ LUB równoważna identyfikacja
> - Numer identyfikacyjny podatku UE
> - Międzynarodowa klasyfikacja kwalifikacji (ICD-10-CM)
> - Międzynarodowa klasyfikacja kwalifikacji (ICD-9-CM)
> - Numer prawa jazdy w Stanach Zjednoczonych

Możesz również tworzyć niestandardowe typy informacji poufnych przy użyciu funkcji programu PowerShell i funkcji dokładnego dopasowania danych. Aby dowiedzieć się więcej o tych metodach, zobacz:
- [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell & w Centrum zgodności](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

1. W Centrum zgodności przejdź do tematu **Typy** \> poufnych informacji klasyfikacji danych i wybierz typ informacji poufnych, który chcesz skopiować.

2. W wysuwanych widokach wybierz pozycję **Kopiuj**.

3. Na **liście** typów informacji poufnych wybierz pozycję Odśwież, a następnie przejrzyj lub wyszukaj właśnie dokonaną kopię. Częściowe wyszukiwania działają, `copy` `copy` więc możesz po prostu wyszukiwać i zwracać wszystkie typy informacji poufnych z wyrazem w nazwie. 

4. Wypełnij wartości w **polach Nazwa** i **Opis** , a następnie wybierz przycisk **Dalej**.

5. Wybierz kopię typu informacji poufnych i wybierz pozycję **Edytuj**. 

6. Nadaj nowym informacjom poufnym nowe nazwy **i** **opisy**.

7. Możesz edytować lub usunąć istniejące wzorce i dodać nowe. Wybierz domyślny poziom ufności dla nowego wzorca. Dopuszczalne wartości to **: Niska ufność**, **Średnia ufność** i **Wysoka ufność**.

8. Wybierz i **zdefiniuj element Podstawowy**. Elementem podstawowym może **być wyrażenie regularne**, lista **Słowo kluczowe****, słownik Słowo** kluczowe lub jedna ze wstępnie skonfigurowanych **funkcji**. Zobacz Funkcje [typów informacji poufnych](sit-functions.md).

9. Wypełnij wartość dla wartości **Odległość znaku**.

10. (Opcjonalnie) Jeśli masz **elementy obsługi lub** dodatkowe [**testy, dodaj**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) je. W razie potrzeby możesz pogrupować **elementy pomocy technicznej**.

11. Wybierz pozycję **Utwórz**.

12. Wybierz przycisk **Dalej**.

13. Wybierz zalecany **poziom ufności** dla tego typu informacji poufnych.

14. Sprawdź swoje ustawienie i wybierz pozycję **Prześlij**.

## <a name="test-a-sensitive-information-type"></a>Testowanie typu informacji poufnych

Możesz przetestować dowolny typ informacji poufnych na liście. Przed użyciem zasad zalecamy przetestowanie każdego typu informacji poufnych, który utworzysz.

1. Przygotuj dwa pliki, takie jak dokument programu Word. Jeden z zawartością dopasowaną do elementów określonych w typie informacji poufnych i taki, który nie jest taki.

2. W Centrum zgodności przejdź do tematu **Typy** \> informacji poufnych klasyfikacji danych i wybierz z listy typ informacji poufnych, aby otworzyć okienko szczegółów, a następnie wybierz pozycję **Test**.

3. Upload pliku i wybierz pozycję **Testuj**.

4. Na stronie **Wyniki dopasowania** przejrzyj wyniki i wybierz pozycję **Zakończ**.

## <a name="custom-sensitive-information-types-limits"></a>Niestandardowe limity typów informacji poufnych

Aby zapewnić wysoką wydajność i niższe opóźnienia, istnieją ograniczenia w niestandardowych konfiguracjach sits.

|Limit|Value|
|--------|--------|
|Maksymalna liczba niestandardowych identyfikatorów SIT utworzonych za pośrednictwem Centrum zgodności| 500 |
|Maksymalna długość wyrażenia regularnego| 1024 znaki|
|Maksymalna długość danego terminu na liście słów kluczowych| 50 znaków|
|Maksymalna liczba terminów na liście słów kluczowych| 2048|
|maksymalna liczba odrębnych regexes na typ informacji poufnej| 20|
|maksymalny rozmiar słownika słów kluczowych (kompresja po kompresji)| 1 MB (~1 000 000 znaków)|
|Maksymalna liczba baz słów kluczowych na słownikach sieciowych (SIT) w dzierżawie|50 |

> [!NOTE] 
> Jeśli masz firmę, która musi utworzyć ponad 500 niestandardowych informacji o klientach, utwórz zgłoszenie do pomocy technicznej.

### <a name="instance-count-supported-values-for-sit"></a>Obsługiwane wartości liczby wystąpień dla usługi SIT

Limit liczby wystąpień sit ma zastosowanie, gdy w tych rozwiązaniach są używane punkty SIT:

- Zasady DLP
- Ochrona informacji
- Zarządzanie informacjami
- Zgodność komunikacji
- Zarządzanie rekordami
- Usługa Microsoft Defender dla aplikacji w chmurze
- Microsoft Priva

Aby zeskanowany element spełniał kryteria reguły, liczba unikatowych wystąpień numeru SIT w dowolnym pojedynczym wystąpieniu musi  temu podlegać między wartościami minimum i maksimum. Jest to tak **zwana liczba wystąpień**.

- **Pole Min** : dolny limit (minimalna liczba) unikatowych wystąpień numeru SIT, który należy znaleźć w pozycji w celu wyzwolenia dopasowania. Pole min obsługuje wartości:
    - Od 1 do 500
- **Pole Max** : górny limit liczby unikatowych wystąpień numeru SIT, który można znaleźć w pozycji i wyzwolić dopasowanie. Pole o maksymalnej wartości obsługuje wartości:
    - Od 1 do 500 — używaj tej funkcji, jeśli chcesz ustawić określony górny limit, który nie może być wyższy niż 500 lub mniejszy od liczby wystąpień numeru SIT w pozycji.
    - Dowolna `Any` — ta wartość jest wymagana, gdy nieokreślona liczba unikatowych wystąpień funkcji SIT zostanie znaleziona w zeskanowanym elementu, a liczba unikatowych wystąpień przekroczy lub przekroczy minimalną liczbę unikatowych wystąpień. Innymi słowy kryteria zliczania unikatowych wystąpień są spełnione, o ile spełni się wartość min.

Jeśli na przykład reguła ma wyzwalać dopasowanie, gdy w jednym miejscu znajduje się co najmniej 500 unikatowych wystąpień pozycji SIT, ustaw wartość **min** `500` i wartość **maksymalną** na `Any`.

> [!NOTE]
> Microsoft 365 Informacji obsługuje dwu bajtowe języki zestawu znaków dla:
> - Chiński (uproszczony)
> - Chiński (tradycyjny)
> - Korean
> - Japanese
>
>Ta obsługa jest dostępna w przypadku typów informacji poufnych. Aby uzyskać [więcej informacji](mip-dbcs-relnotes.md) , zobacz Obsługa ochrony informacji dla zestawów znaków dwuteowych (wersja Zapoznawcza).

> [!TIP]
> Aby wykryć wzorce zawierające znaki chińskie/japońskie i pojedyncze bajty lub wykryć wzorce zawierające chiński/japoński i angielski, zdefiniuj dwie warianty słowa kluczowego lub znaków regex. 
> - Aby na przykład wykryć słowo kluczowe, takie jak "机密的document", użyj dwóch wariantów słowa kluczowego; jeden z odstępem między tekstem japońskim i angielskim a innym bez spacji między tekstem japońskim i angielskim. Dlatego słowa kluczowe, które mają zostać dodane w dokumencie SIT, powinny mieć poszczególnych 机密的 dokumentu i 机密的document. Podobnie, aby wykryć frazę "ピオリンピック2020", należy użyć dwóch wariantów. "オオリンピック 2020" and "ピピリンピック2020".
>
> Jeśli oprócz chińskich/japońskich/dwu bajtowych znaków na liście słów kluczowych/fraz znajdują się również wyrazy inne niż chińskie/japońskie (na przykład tylko w języku angielskim), zaleca się utworzenie dwóch list słowników/słów kluczowych. Jeden dla słów kluczowych zawierających znaki chińskie/japońskie/dwu bajtowe, a drugi tylko w języku angielskim. 
> - Jeśli na przykład chcesz utworzyć słownik lub listę słów kluczowych z trzema frazami "Wysoce poufne", "機密性がいい" i "机密的document", należy utworzyć dwie listy słów kluczowych. 
>     1. Wysoce poufne
>     2. 機密性がい, 机密的document i 机密的 dokument
>
> Tworząc znak regex za pomocą dwu-bajtowego łącznika lub podwójnej litery bajtowej, należy pamiętać o znakach ucieczki przed łącznikiem lub przecięciem w znakach regex. Oto przykładowy regex do odwołania:
>    - (?<!\d) ([4][0-9]{3} [\-?\-\t]*[0-9]{4})
>
> Zalecamy użycie dopasowania ciągu zamiast dopasowania wyrazu na liście słów kluczowych.
