---
title: Twórz zapytania w celu znalezienia poufnych danych przechowywanych w witrynach
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
description: Użyj funkcji ochrony przed utratą danych (DLP) w usłudze SharePoint Online, aby odnajdywać dokumenty zawierające poufne dane w całej dzierżawie.
ms.openlocfilehash: 1bb3ed0286f719f9ea9210b4952044081213914f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638328"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>Twórz zapytania w celu znalezienia poufnych danych przechowywanych w witrynach

Użytkownicy często przechowują w swoich witrynach poufne dane, takie jak numery kart kredytowych, numery ubezpieczenia społecznego lub dane osobowe, a z czasem może to narazić organizację na znaczne ryzyko utraty danych. Dokumenty przechowywane w witrynach , w tym OneDrive dla Firm witrynach, mogą być udostępniane osobom spoza organizacji, które nie powinny mieć dostępu do informacji. Dzięki Ochrona przed utratą danych w Microsoft Purview (DLP) w usłudze SharePoint Online można odnajdywać dokumenty zawierające poufne dane w całej dzierżawie. Po odnalezieniu dokumentów możesz współpracować z właścicielami dokumentów, aby chronić dane. Ten temat może pomóc w utworzeniu zapytania w celu wyszukania poufnych danych.

> [!NOTE]
> Odnajdywanie elektroniczne lub elektroniczne wykrywanie i DLP to funkcje premium, które wymagają usługi [SharePoint Online Plan 2](https://go.microsoft.com/fwlink/?LinkId=510080).

## <a name="forming-a-basic-dlp-query"></a>Tworzenie podstawowego zapytania DLP

Istnieją trzy części, które tworzą podstawowe zapytanie DLP: SensitiveType, zakres liczby i zakres ufności. Jak pokazano na poniższej ilustracji, parametr **SensitiveType:"\<type\>"** jest wymagany i jest opcjonalny **|\<count range\>** **|\<confidence range\>** .

![Przykładowe zapytanie podzielone na wymagane i opcjonalne.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>Typ poufny — wymagany

Więc co to jest każda część? Zapytania DLP programu SharePoint zwykle zaczynają się od właściwości  `SensitiveType:"` i nazwy typu informacji ze [spisu typów informacji poufnych](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) i kończą się ciągiem  `"`. Możesz również użyć nazwy [niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md) utworzonego dla organizacji. Na przykład możesz szukać dokumentów zawierających numery kart kredytowych. W takim wystąpieniu należy użyć następującego formatu:  `SensitiveType:"Credit Card Number"`. Ponieważ nie uwzględniano zakresu liczby ani zakresu ufności, zapytanie zwraca każdy dokument, w którym wykryto numer karty kredytowej. Jest to najprostsze zapytanie, które można uruchomić i zwraca najwięcej wyników. Należy pamiętać, że pisownia i odstępy typów poufnych mają znaczenie.

### <a name="ranges---optional"></a>Zakresy — opcjonalnie

Obie kolejne dwie części to zakresy, więc szybko zbadajmy, jak wygląda zakres. W zapytaniach DLP programu SharePoint podstawowy zakres jest reprezentowany przez dwie liczby rozdzielone dwoma kropkami, co wygląda następująco:  `[number]..[number]`. Jeśli na przykład  `10..20` jest używany, ten zakres będzie przechwytywać liczby od 10 do 20. Istnieje wiele różnych kombinacji zakresów, a kilka z nich zostało omówionych w tym temacie.

Dodajmy zakres liczby do zapytania. Zakres liczb umożliwia zdefiniowanie liczby wystąpień poufnych informacji, które dokument musi zawierać, zanim zostaną uwzględnione w wynikach zapytania. Jeśli na przykład zapytanie ma zwracać tylko dokumenty zawierające dokładnie pięć numerów kart kredytowych, użyj następującego polecenia:  `SensitiveType:"Credit Card Number|5"`. Zakres liczby może również pomóc w zidentyfikowaniu dokumentów, które stanowią wysoki stopień ryzyka. Na przykład organizacja może uznać dokumenty z co najmniej pięcioma numerami kart kredytowych za wysokie ryzyko. Aby znaleźć dokumenty pasujące do tego kryterium, użyj następującego zapytania:  `SensitiveType:"Credit Card Number|5.."`. Możesz też znaleźć dokumenty z pięcioma lub mniejszą liczbą numerów kart kredytowych, korzystając z następującego zapytania:  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>Zakres ufności

Na koniec zakres ufności to poziom pewności, że wykryty typ poufny jest rzeczywiście zgodny. Wartości zakresu ufności działają podobnie do zakresu zliczania. Zapytanie można utworzyć bez uwzględniania zakresu liczb. Na przykład, aby wyszukać dokumenty z dowolną liczbą numerów kart kredytowych — o ile zakres ufności wynosi 85 procent lub więcej , użyj następującego zapytania:  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> Gwiazdka ( `*` ) jest symbolem wieloznacznym, co oznacza, że każda wartość działa. Symbol wieloznaczny ( `*` ) można użyć w zakresie liczby lub w zakresie ufności, ale nie w typie wrażliwym.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>Dodatkowe właściwości zapytania i operatory wyszukiwania dostępne w Centrum zbierania elektronicznych materiałów dowodowych

DLP w programie SharePoint wprowadza również właściwość LastSensitiveContentScan, która może pomóc w wyszukiwaniu plików skanowanych w określonym przedziale czasu. Aby uzyskać przykłady zapytań z właściwością  `LastSensitiveContentScan` , zobacz [Przykłady złożonych zapytań](#examples-of-complex-queries) w następnej sekcji.

Do utworzenia zapytania można użyć nie tylko właściwości specyficznych dla protokołu DLP, ale także standardowych właściwości wyszukiwania zbierania elektronicznych materiałów dowodowych programu SharePoint, takich jak  `Author` lub  `FileExtension`. Operatory umożliwiają tworzenie złożonych zapytań. Aby uzyskać listę dostępnych właściwości i operatorów, zobacz wpis w blogu [Using Search Properties and Operators with eDiscovery (Używanie właściwości wyszukiwania i operatorów zbierania elektronicznych materiałów dowodowych](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) ).

## <a name="examples-of-complex-queries"></a>Przykłady złożonych zapytań

W poniższych przykładach użyto różnych poufnych typów, właściwości i operatorów, aby zilustrować sposób uściślania zapytań w celu znalezienia dokładnie tego, czego szukasz.

<br>

****

|Kwerendy|Objaśnienie|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|Nazwa może wydawać się dziwna, ponieważ jest tak długa, ale jest to poprawna nazwa tego typu wrażliwego. Upewnij się, że używasz [dokładnych nazw ze spisu typów informacji poufnych](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help). Możesz również użyć nazwy [niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md) utworzonego dla organizacji.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|Spowoduje to zwrócenie dokumentów o co najmniej jednym dopasowaniu do typów poufnych "Numer karty kredytowej". Wartości dla każdego zakresu są odpowiednimi wartościami minimalnymi i maksymalnymi. Prostszym sposobem na napisanie tego zapytania jest  `SensitiveType:"Credit Card Number"`, ale gdzie jest w tym zabawa?|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|Spowoduje to zwrócenie dokumentów z 5–25 numerami kart kredytowych, które zostały zeskanowane od 11 sierpnia 2018 r. do 13 sierpnia 2018 r.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|Spowoduje to zwrócenie dokumentów z 5–25 numerami kart kredytowych, które zostały zeskanowane od 11 sierpnia 2018 r. do 13 sierpnia 2018 r. Pliki z rozszerzeniem XLSX nie są uwzględniane w wynikach zapytania.  `FileExtension` jest jedną z wielu właściwości, które można uwzględnić w zapytaniu. Aby uzyskać więcej informacji, zobacz [Using Search Properties and Operators with eDiscovery (Używanie właściwości wyszukiwania i operatorów zbierania elektronicznych materiałów dowodowych](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery)).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|Spowoduje to zwrócenie dokumentów zawierających numer karty kredytowej lub numer ubezpieczenia społecznego.|
|

## <a name="examples-of-queries-to-avoid"></a>Przykłady zapytań, których należy unikać

Nie wszystkie zapytania są tworzone równo. W poniższej tabeli przedstawiono przykłady zapytań, które nie działają z programem DLP w programie SharePoint, i opisano dlaczego.

<br>

****

|Nieobsługiwany zapytanie|Powodu|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|Musisz dodać co najmniej jedną liczbę.|
|`SensitiveType:"NotARule"`|"NotARule" nie jest prawidłową nazwą typu poufnego. Tylko nazwy w [spisie typów informacji poufnych](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) działają w zapytaniach DLP.|
|`SensitiveType:"Credit Card Number|0"`|Zero nie jest prawidłowe jako wartość minimalna lub maksymalna w zakresie.|
|`SensitiveType:"Credit Card Number"`|Może to być trudne do zobaczenia, ale istnieje dodatkowe białe miejsce między "Kredyt" i "Karta", które sprawia, że zapytanie jest nieprawidłowe. Użyj dokładnych nazw typów [poufnych ze spisu typów informacji poufnych](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help).|
|`SensitiveType:"Credit Card Number|1. .3"`|Część z dwóch okresów nie powinna być oddzielona spacjami.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|Istnieje zbyt wiele ograniczników rur (\|). Zamiast tego postępuj zgodnie z następującym formatem: `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|Ponieważ wartości ufności reprezentują wartość procentową, nie mogą przekraczać 100. Zamiast tego wybierz liczbę z zakresu od 1 do 100.|
|

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
- [Uruchamianie wyszukiwania zawartości](content-search.md)
- [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md)
