---
title: Form a query to find sensitive data stored on sites
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Korzystaj z funkcji ochrony przed utratą danych (DLP, data loss prevention) w SharePoint Online, aby odnajdować dokumenty, które zawierają poufne dane w całej dzierżawie.
ms.openlocfilehash: af1ca8f28f80d58c0f366e1a002181e23db3d552
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985638"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>Form a query to find sensitive data stored on sites

Użytkownicy często przechowują w swoich witrynach poufne dane, takie jak numery kart kredytowych, numery PESEL czy osobiste, i z czasem może to narazić organizację na poważne ryzyko utraty danych. Dokumenty przechowywane w witrynach — OneDrive dla Firm witryn internetowych — mogą być udostępniane osobom spoza organizacji, które nie powinny mieć dostępu do informacji. Dzięki ochronie przed utratą danych (DLP, data loss prevention) w u SharePoint Online możesz odnajdować dokumenty, które zawierają poufne dane w całej dzierżawie. Po odnajdywaniu dokumentów możesz we współpracy z właścicielami dokumentów chronić dane. W tym temacie poszukasz danych poufnych, tworząc zapytanie.

> [!NOTE]
> Funkcja zbierania elektronicznych materiałów dowodowych i funkcja DLP to funkcje premium, które wymagają SharePoint [Online (plan 2](https://go.microsoft.com/fwlink/?LinkId=510080)).

## <a name="forming-a-basic-dlp-query"></a>Formowanie podstawowego zapytania DLP

Podstawowe zapytanie DLP obejmuje trzy elementy: SensitiveType, zakres zliczania i zakres ufności. Jak pokazano na poniższej ilustracji, wymagany jest parametr **SensitiveType:"\<type\>"** **|\<count range\>** oraz obie **|\<confidence range\>** te typy są opcjonalne.

![Przykładowe zapytanie podzielone na wymagane i opcjonalne.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>Typ poufny — wymagany

Czym więc są poszczególne części? SharePoint zapytań DLP `SensitiveType:"` zazwyczaj zaczynają się od właściwości i nazwy typu informacji z magazynu typów informacji poufnych[, a](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) kończyć na .`"` Możesz także użyć nazwy niestandardowego typu informacji [poufnych](create-a-custom-sensitive-information-type.md) utworzonego dla organizacji. Na przykład dokumenty zawierające numery kart kredytowych mogą być szukane. W takim przypadku należy użyć następującego formatu:  `SensitiveType:"Credit Card Number"`. Ponieważ nie uwzględniasz zakresu liczenia ani zakresu ufności, zapytanie zwraca każdy dokument, w którym jest wykrywany numer karty kredytowej. Jest to najprostsze zapytanie, które można uruchomić i zwraca ono najwięcej wyników. Pamiętaj, że pisownia i odstępy typu poufnego mają znaczenie.

### <a name="ranges---optional"></a>Zakresy — opcjonalne

Obie następne dwie części to zakresy, więc przyjrzyjmy się szybko zakresowi. W SharePoint DLP podstawowy zakres jest reprezentowany przez dwie liczby rozdzielone dwoma kropkami, co wygląda następująco: `[number]..[number]`. Jeśli zostanie on użyty  `10..20` , ten zakres będzie na przykład przechwytywał liczby z zakresu od 10 do 20. Istnieje wiele różnych kombinacji zakresów, a niektóre z nich zostały uwzględnione w tym temacie.

Dodajmy do zapytania zakres zliczania danych. Zakres liczenia umożliwia zdefiniowanie liczby wystąpień informacji poufnych, które dokument musi zawierać przed dodaniem go do wyników zapytania. Jeśli na przykład zapytanie ma zwracać tylko te dokumenty, które zawierają dokładnie pięć numerów kart kredytowych, użyj tej funkcji:  `SensitiveType:"Credit Card Number|5"`. Zakres zliczania może również ułatwić identyfikowanie dokumentów o wysokim poziomie ryzyka. Na przykład duże ryzyko może okazać się związane z dokumentami o numerach kart kredytowych 5 lub większej liczby kart kredytowych. Aby znaleźć dokumenty, które pasują do tego kryterium, użyj tego zapytania:  `SensitiveType:"Credit Card Number|5.."`. Możesz również znaleźć dokumenty o pięciu lub mniejszej liczbie numerów kart kredytowych, używając tego zapytania:  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>Zakres ufności

Natomiast zakres ufności to poziom ufności, że wykryty typ poufny faktycznie odpowiada. Wartości przedziału ufności działają podobnie, jak w przypadku zakresu. Kwerendę można utworzyć bez uwzględnienia zakresu liczenia. Aby na przykład wyszukiwać dokumenty z dowolną liczbą numerów kart kredytowych — o ile przedział ufności wynosi 85 procent lub więcej — można użyć tego zapytania:  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> Gwiazdka ( `*` ) jest znakiem wieloznacznym, który oznacza, że każda wartość działa. Symbolu wieloznacznego ( `*` ) można użyć w zakresie liczności lub w zakresie ufności, ale nie można go stosować w przypadku typu poufnego.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>Dodatkowe właściwości kwerendy i operatory wyszukiwania dostępne w Centrum zbierania elektronicznych materiałów dowodowych

W funkcji DLP w programie SharePoint wprowadzono również właściwość LastSensitiveContentScan, która może ułatwić wyszukiwanie plików skanowanych w określonym czasie. Aby uzyskać przykłady zapytań z właściwością  `LastSensitiveContentScan` , zobacz [Przykłady złożonych zapytań](#examples-of-complex-queries) w następnej sekcji.

Zapytania można tworzyć nie tylko za pomocą właściwości specyficznych dla funkcji DLP, ale również standardowych `Author` SharePoint wyszukiwania zbierania elektronicznych materiałów dowodowych, takich jak lub `FileExtension`. Za pomocą operatorów można tworzyć złożone zapytania. Aby uzyskać listę dostępnych właściwości i operatorów, zobacz wpis w blogu Używanie właściwości wyszukiwania i operatorów zbierania elektronicznych [materiałów](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) dowodowych.

## <a name="examples-of-complex-queries"></a>Przykłady złożonych zapytań

W poniższych przykładach pokazano, jak uściślić zapytania, aby znaleźć dokładnie to, czego szukasz, przy użyciu różnych typów poufnych, właściwości i operatorów.

<br>

****

|Zapytanie|Objaśnienie|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|Nazwa może wydawać się dziwne, ponieważ jest tak długa, ale jest to właściwa nazwa dla tego poufnego typu. Upewnij się, że należy dokładnie używać imion i nazwisk z wykazu [typów informacji poufnych](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help). Możesz także użyć nazwy niestandardowego typu informacji [poufnych](create-a-custom-sensitive-information-type.md) utworzonego dla organizacji.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|W ten sposób są zwracane dokumenty z co najmniej jednym dopasowaniem do typu poufnego "Numer karty kredytowej". Wartości dla każdego zakresu to odpowiednie wartości minimalne i maksymalne. Prostszy sposób na napisanie tego zapytania  `SensitiveType:"Credit Card Number"`to , ale gdzie w tym jest ciekawie?|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|W ten sposób można zwracać dokumenty z numerami kart kredytowych od 5 do 25, które były skanowane od 11 sierpnia 2018 r. do 13 sierpnia 2018 r.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|W ten sposób można zwracać dokumenty z numerami kart kredytowych od 5 do 25, które były skanowane od 11 sierpnia 2018 r. do 13 sierpnia 2018 r. Pliki z rozszerzeniem XLSX nie są uwzględniane w wynikach zapytania.  `FileExtension` jest jedną z wielu właściwości, które można uwzględnić w zapytaniu. Aby uzyskać więcej informacji, zobacz [Używanie właściwości wyszukiwania i operatorów zbierania elektronicznych materiałów dowodowych](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|Ta funkcja zwraca dokumenty zawierające numer karty kredytowej lub numer PESZ.|
|

## <a name="examples-of-queries-to-avoid"></a>Przykłady zapytań, których należy unikać

Nie wszystkie zapytania są tworzone jako równe. W poniższej tabeli popisano przykłady zapytań, które nie działają z zasadą DLP w programie SharePoint i dlaczego.

<br>

****

|Nieobsługiwane zapytanie|Przyczyna|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|Musisz dodać co najmniej jedną liczbę.|
|`SensitiveType:"NotARule"`|"NotARule" nie jest prawidłową nazwą typu poufnego. Tylko nazwy w [spisie typów informacji poufnych](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) działają w zapytaniach DLP.|
|`SensitiveType:"Credit Card Number|0"`|Zero nie jest prawidłowe jako wartość minimalna ani wartość maksymalna w zakresie.|
|`SensitiveType:"Credit Card Number"`|Może to być trudne do zobaczenia, ale istnieje dodatkowe odstępy między "kredytami" i "kartą", które powoduje, że zapytanie jest nieprawidłowe. Należy używać dokładnych nazw typów poufnych ze [spisu typów informacji poufnych](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help).|
|`SensitiveType:"Credit Card Number|1. .3"`|Części dwue okresowej nie należy rozdzielać spacją.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|Jest zbyt wiele ograniczników potoków (\|). Zamiast tego wykonaj następujące czynności w tym formacie: `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|Ponieważ wartości ufności reprezentują wartość procentową, nie mogą przekraczać 100. Zamiast tego wybierz liczbę z od 1 do 100.|
|

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Uruchamianie wyszukiwania zawartości](content-search.md)
- [Zapytania słów kluczowych i warunki wyszukiwania dla przeszukiwania zawartości](keyword-queries-and-search-conditions.md)
