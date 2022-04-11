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
ms.openlocfilehash: ff6a66b092d433fcfde7723f252fea679c2a3050
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759838"
---
# <a name="create-custom-sensitive-information-types-in-the-compliance-center"></a>Tworzenie niestandardowych typów informacji poufnych w Centrum zgodności

Jeśli wstępnie skonfigurowane typy informacji poufnych nie spełniają Twoich potrzeb, możesz utworzyć własne niestandardowe typy informacji poufnych, które zostały w pełni zdefiniowane, lub skopiować jeden ze wstępnie skonfigurowanych typów i zmodyfikować je.

Niestandardowe typy informacji poufnych tworzone przy użyciu tej metody są dodawane do pakietu reguł o nazwie `Microsoft.SCCManaged.CustomRulePack`.

Istnieją dwa sposoby tworzenia nowego typu informacji poufnych:

- [od podstaw, w którym w pełni definiuje się wszystkie elementy](#create-a-custom-sensitive-information-type)
- [kopiowanie i modyfikowanie istniejącego typu informacji poufnych](#copy-and-modify-a-sensitive-information-type)


## <a name="before-you-begin"></a>Przed rozpoczęciem

- Należy znać typy informacji poufnych i ich skład. Zobacz [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md). Kluczowe znaczenie ma zrozumienie ról:
  - [wyrażenia regularne](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/) — Microsoft 365 typów informacji poufnych używa aparatu Boost.RegEx 5.1.3
  - listy słów kluczowych — możesz utworzyć własne, definiując typ informacji poufnych lub wybierając istniejące listy słów kluczowych
  - [słownik słów kluczowych](create-a-keyword-dictionary.md)
  - [Funkcje typu informacji poufnych](sit-functions.md)
  - [poziomy ufności](sensitive-information-type-learn-about.md#more-on-confidence-levels)

- Aby utworzyć, przetestować i wdrożyć niestandardowy typ informacji poufnych za pośrednictwem interfejsu użytkownika, musisz mieć uprawnienia administratora globalnego lub administratora zgodności. Zobacz [Informacje o rolach administratora](/office365/admin/add-users/about-admin-roles) w Office 365.

- Twoja organizacja musi mieć subskrypcję, taką jak Office 365 Enterprise, która obejmuje zapobieganie utracie danych (DLP). Zobacz [Zasady obsługi komunikatów i zgodność ServiceDescription](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc).

> [!IMPORTANT]
> Obsługa & obsługi klienta firmy Microsoft nie może pomóc w tworzeniu niestandardowych klasyfikacji ani wzorców wyrażeń regularnych. Inżynierowie pomocy technicznej mogą zapewnić ograniczoną obsługę funkcji, taką jak dostarczanie przykładowych wzorców wyrażeń regularnych do celów testowych lub pomoc w rozwiązywaniu problemów z istniejącym wzorcem wyrażeń regularnych, który nie jest wyzwalany zgodnie z oczekiwaniami, ale nie może zapewnić, że dowolne niestandardowe dopasowywanie zawartości będzie spełniać twoje wymagania lub obowiązki.

## <a name="create-a-custom-sensitive-information-type"></a>Tworzenie niestandardowego typu informacji poufnych

Ta procedura umożliwia utworzenie w pełni zdefiniowanego nowego typu informacji poufnych.

1. W Centrum zgodności przejdź do pozycji Typy **informacji poufnych** **klasyfikacji** \> danych i wybierz pozycję **Utwórz typ informacji poufnych**.

2. Wypełnij wartości w polach **Nazwa** i **Opis** , a następnie wybierz pozycję **Dalej**.

3. Wybierz **pozycję Utwórz wzorzec**. Podczas definiowania nowego typu informacji poufnych można utworzyć wiele wzorców, z których każdy ma różne elementy i poziomy ufności.

4. Wybierz domyślny poziom ufności dla wzorca. Wartości to **Niskie zaufanie**, **Średnie zaufanie** i **Wysokie zaufanie**.

5. Wybierz i zdefiniuj **element Podstawowy**. Elementem podstawowym może być **wyrażenie regularne** z opcjonalnym modułem sprawdzania poprawności, **listą słów kluczowych**, **słownikiem słów kluczowych** lub jedną ze wstępnie **skonfigurowanych funkcji**. Aby uzyskać więcej informacji na temat funkcji DLP, zobacz [Funkcje typów informacji poufnych](sit-functions.md). Aby uzyskać więcej informacji na temat daty i modułów sprawdzania poprawności sum [kontrolnych, zobacz Weryfikacje wyrażeń regularnych typów informacji poufnych](sit-regex-validators-additional-checks.md#sensitive-information-type-regular-expression-validators).

6. Wypełnij wartość **bliskości znaku**.

7. (Opcjonalnie) Dodaj elementy pomocnicze, jeśli istnieją. Elementy pomocnicze mogą być wyrażeniem regularnym z opcjonalnym modułem sprawdzania poprawności, listą słów kluczowych, słownikiem słów kluczowych lub jedną ze wstępnie zdefiniowanych funkcji. Elementy pomocnicze mogą mieć własną **konfigurację zbliżeniowych znaków** .

8. (Opcjonalnie) Dodaj [**dodatkowe testy**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) z listy dostępnych testów.

9. Wybierz pozycję **Utwórz**.

10. Wybierz przycisk **Dalej**.

11. Wybierz **zalecany poziom ufności** dla tego typu informacji poufnych.

12. Sprawdź ustawienie i wybierz pozycję **Prześlij**.

    > [!IMPORTANT]
    > Microsoft 365 używa przeszukiwarki do identyfikowania i klasyfikowania poufnych informacji w witrynach SharePoint Online i OneDrive dla Firm. Aby zidentyfikować nowy niestandardowy typ informacji poufnych w istniejącej zawartości, zawartość musi zostać ponownie przeszukana. Zawartość jest przeszukiwana zgodnie z harmonogramem, ale można ręcznie ponownie przeszukać zawartość zbioru witryn, listy lub biblioteki. Aby uzyskać więcej informacji, zobacz [Ręczne przeszukiwanie żądań i ponowne indeksowanie witryny, biblioteki lub listy](/sharepoint/crawl-site-content).

13. Na stronie **Klasyfikacja danych** zostaną wyświetlone wszystkie typy informacji poufnych. Wybierz **pozycję Odśwież,** a następnie wyszukaj lub użyj narzędzia wyszukiwania, aby znaleźć utworzony typ informacji poufnych.

### <a name="copy-and-modify-a-sensitive-information-type"></a>Kopiowanie i modyfikowanie typu informacji poufnych

Ta procedura umożliwia utworzenie nowego typu informacji poufnych opartego na istniejącym typie informacji poufnych.

> [!NOTE]
> Nie można skopiować tych SIC:
>
> - Numer prawa jazdy w Kanadzie
> - Numer prawa jazdy UE
> - Krajowy numer identyfikacyjny UE
> - Numer paszportu UE
> - Numer ubezpieczenia społecznego UE lub równoważna identyfikacja
> - Numer identyfikacji podatkowej UE
> - Międzynarodowa klasyfikacja chorób (ICD-10-CM)
> - Międzynarodowa klasyfikacja chorób (ICD-9-CM)
> - Numer prawa jazdy w Stanach Zjednoczonych

Można również tworzyć niestandardowe typy informacji poufnych przy użyciu programu PowerShell i funkcji dokładnego dopasowania danych. Aby dowiedzieć się więcej o tych metodach, zobacz:

- [Tworzenie niestandardowego typu informacji poufnych w programie PowerShell Centrum zgodności & zabezpieczeń](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

1. W Centrum zgodności przejdź do **pozycji Typy informacji poufnych** **klasyfikacji** \> danych i wybierz typ informacji poufnych, który chcesz skopiować.

2. W wysuwanej pozycji wybierz pozycję **Kopiuj**.

3. Wybierz pozycję **Odśwież** na liście typów informacji poufnych i przejrzyj lub wyszukaj właśnie utworzoną kopię. Częściowe wyszukiwanie żądło działa, więc można po prostu wyszukać `copy` i wyszukać zwróci wszystkie typy informacji poufnych ze słowem `copy` w nazwie.

4. Wypełnij wartości w polach **Nazwa** i **Opis** , a następnie wybierz pozycję **Dalej**.

5. Wybierz kopię typu informacji poufnych i wybierz pozycję **Edytuj**.

6. Nadaj nowemu typowi informacji poufnych nową **nazwę** i **opis**.

7. Możesz edytować lub usuwać istniejące wzorce i dodawać nowe. Wybierz domyślny poziom ufności dla nowego wzorca. Wartości to **Niskie zaufanie**, **Średnie zaufanie** i **Wysokie zaufanie**.

8. Wybierz i zdefiniuj **element Podstawowy**. Elementem podstawowym może być **wyrażenie regularne**, **lista słów kluczowych**, **słownik słów kluczowych** lub jedna ze wstępnie **skonfigurowanych funkcji**. Zobacz [Funkcje typów informacji poufnych](sit-functions.md).

9. Wypełnij wartość **bliskości znaku**.

10. (Opcjonalnie) Jeśli masz **elementy pomocnicze** lub [**dodatkowe testy**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) , dodaj je. W razie potrzeby można grupować **elementy pomocnicze**.

11. Wybierz pozycję **Utwórz**.

12. Wybierz przycisk **Dalej**.

13. Wybierz **zalecany poziom ufności** dla tego typu informacji poufnych.

14. Sprawdź ustawienie i wybierz pozycję **Prześlij**.

## <a name="test-a-sensitive-information-type"></a>Testowanie typu informacji poufnych

Możesz przetestować dowolny typ informacji poufnych na liście. Zalecamy przetestowanie każdego typu informacji poufnych utworzonego przed użyciem go w zasadach.

1. Przygotuj dwa pliki, takie jak dokument programu Word. Jedna z zawartością zgodną z elementami określonymi w typie informacji poufnych i niezgodna.

2. W Centrum zgodności przejdź do pozycji **Typy informacji poufnych** **klasyfikacji** \> danych i wybierz typ informacji poufnych z listy, aby otworzyć okienko szczegółów i wybrać pozycję **Testuj**.

3. Upload pliku i wybierz pozycję **Testuj**.

4. Na stronie **Dopasowania wyników** przejrzyj wyniki i wybierz pozycję **Zakończ**.

## <a name="custom-sensitive-information-types-limits"></a>Limity niestandardowych typów informacji poufnych

Aby zapewnić wysoką wydajność i mniejsze opóźnienia, istnieją ograniczenia w niestandardowych konfiguracjach interfejsów SIC.

|Limit|Value|
|---|---|
|maksymalna liczba niestandardowych interfejsów API utworzonych za pośrednictwem Centrum zgodności| 500 |
|maksymalna długość wyrażenia regularnego| 1024 znaki|
|maksymalna długość danego terminu na liście słów kluczowych| 50 znaków|
|maksymalna liczba terminów na liście słów kluczowych| 2048|
|maksymalna liczba odrębnych rejestrów na typ informacji poufnych| 20|
|maksymalny rozmiar słownika słów kluczowych (kompresja po)| 1 MB (~1 000 000 znaków)|
|maksymalna liczba SIC opartych na słowniku słów kluczowych w dzierżawie|50 |

> [!NOTE]
> Jeśli masz firmową potrzebę utworzenia ponad 500 niestandardowych interfejsów API, zgłoś bilet pomocy technicznej.

### <a name="instance-count-supported-values-for-sit"></a>Obsługiwane wartości liczby wystąpień dla usługi SIT

Limit liczby wystąpień SIT ma zastosowanie, gdy w tych rozwiązaniach są używane interfejsy SIC:

- Zasady DLP
- Information Protection
- Zarządzanie informacjami
- Zgodność z komunikacją
- Zarządzanie rekordami
- Microsoft Defender for Cloud Apps
- Microsoft Priva

Aby zeskanowany element spełniał kryteria reguły, liczba unikatowych wystąpień funkcji SIT w dowolnym pojedynczym elemencie musi zawierać się między wartościami minimalnymi i maksymalnymi. Jest to nazywane **liczbą wystąpień**.

- **Pole minimalne** : dolny limit (minimalna liczba) unikatowych wystąpień usługi SIT, które należy znaleźć w elemencie w celu wyzwolenia dopasowania. Pole min obsługuje wartości:
  - Od 1 do 500
- **Pole maksymalne** : górny limit liczby unikatowych wystąpień usługi SIT, które można znaleźć w elemencie i nadal wyzwalać dopasowanie. Maksymalne pole obsługuje wartości:
  - Od 1 do 500 — użyj tego ustawienia, gdy chcesz ustawić określony górny limit, który wynosi 500 lub mniej w przypadku liczby wystąpień funkcji SIT w elemencie.
  - Dowolny — użyj polecenia `Any` , jeśli chcesz, aby kryteria liczby unikatowych wystąpień były spełnione, gdy niezdefiniowana liczba unikatowych wystąpień sita znajduje się w zeskanowanym elemencie, a liczba unikatowych wystąpień spełnia lub przekracza minimalną liczbę unikatowych wystąpień. Innymi słowy, kryteria liczby unikatowych wystąpień są spełnione tak długo, jak jest spełniony minimalna wartość.

Jeśli na przykład chcesz, aby reguła wyzwalała dopasowanie, gdy w jednym elemencie znajduje się co najmniej 500 unikatowych wystąpień interfejsu SIT, ustaw wartość **minimalną** na `500` , a **wartość maksymalną** na `Any`.

> [!NOTE]
> Microsoft 365 Information Protection obsługuje języki podwójnego zestawu znaków bajtowych dla:
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
> `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4})`
>
> Znaki specjalne dwu bajtów nie powinny być używane w słowie kluczowym.
>
> Zalecamy użycie dopasowania ciągu zamiast dopasowania wyrazów na liście słów kluczowych.
