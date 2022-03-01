---
title: 'Typ informacji poufnych: sprawdzanie prawidłowego tekstu REGEX i dodatkowe testy'
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak korzystać z funkcji sprawdzania weryfikacji REGEX i dodatkowych testów w typach informacji sentisitve.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 615d4757be16b3171005105aea8148536e6f3015
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014918"
---
# <a name="sensitive-information-type-regex-validators-and-additional-check"></a>Sprawdzanie poszczegliknych informacji typu REGEX i dodatkowe sprawdzanie

> [!IMPORTANT]
> Dział obsługi klienta & firmy Microsoft nie może pomóc w tworzeniu niestandardowych klasyfikacji lub wzorców wyrażeń regularnych. Inżynierowie pomocy technicznej mogą zapewnić ograniczoną obsługę tej funkcji, na przykład zapewnienie przykładowych wzorców wyrażeń regularnych na potrzeby testowania lub pomoc przy rozwiązywaniu problemów z istniejącym wzorcem wyrażeń regularnych, które nie wyzwalają zgodnie z oczekiwaniami, ale nie mogą zapewniać gwarancji, że jakiekolwiek niestandardowe opracowywanie dopasowywania zawartości spełni Twoje wymagania lub obowiązki.

## <a name="sensitive-information-type-regular-expression-validators"></a>Prawidłowy typ informacji poufnych

### <a name="checksum-validator"></a>Sprawdzanie prawidłowego sumy

Jeśli konieczne jest uruchomienie sumy kontrolnej w postaci cyfry w wyrażeniu regularnym, można użyć prawidłowego *sprawdzania.* Załóżmy na przykład, że należy utworzyć numer SIT dla ośmiu cyfr numeru licencji, gdzie ostatnia cyfra jest cyfrą sprawdzaną poprawność przy użyciu obliczenia mod 9. Ustaw algorytm sumy kontrolnej w ten sposób:

```console
Sum = digit 1 * Weight 1 + digit 2 * weight 2 + digit 3 * weight 3 + digit 4 * weight 4 + digit 5 * weight 5 + digit 6 * weight 6 + digit 7 * weight 7 + digit 8 * weight 8
Mod value = Sum % 9
If Mod value == digit 8
    Account number is valid
If Mod value != digit 8
    Account number is invalid
```

1. Zdefiniuj element podstawowy za pomocą tego wyrażenia regularnego:

   ```console
   \d{8}
   ```

2. Następnie dodaj sprawdzanie prawidłowego sumy kontrolnej.

3. Dodaj wartości wagi rozdzielone przecinkami, położenie cyfry kontrolnej i wartości Mod. Aby uzyskać więcej informacji na temat operacji Moduł, zobacz [Operacja Moduleo](https://en.wikipedia.org/wiki/Modulo_operation).

   > [!NOTE]
   > Jeśli cyfra kontrolna nie jest częścią obliczenia sumy kontrolnej, należy użyć liczby 0 jako wartości wagi dla cyfry kontrolnej. Na przykład w powyższym przypadku waga 8 będzie równa 0, jeśli do obliczenia cyfry kontrolnej nie ma być używana cyfra sprawdzania.

   :::image type="content" alt-text="zrzut ekranu przedstawiający skonfigurowany sprawdzanie prawidłowego sumy kontrolnej." source="../media/checksum-validator.png" lightbox="../media/checksum-validator.png":::

### <a name="date-validator"></a>Date validator

Jeśli wartość daty osadzona w wyrażeniu regularnym jest częścią nowo tworzynego wzorca, można użyć sprawdzania, czy wartość spełnia  określone kryteria. Załóżmy na przykład, że chcesz utworzyć numer identyfikacyjny SIT dla dziewięciucyfrowego numeru identyfikacyjnego pracownika. Pierwsze sześć cyfr to data zatrudnienia w formacie DDMMYY, a ostatnie trzy są liczbami wygenerowanym losowo. Aby sprawdzić, czy pierwsze sześć cyfr ma poprawny format.

1. Zdefiniuj element podstawowy za pomocą tego wyrażenia regularnego:

   ```console
   \d{9}
   ```

2. Następnie dodaj validator daty.

3. Wybierz format daty i przesunięcie startowe. Ponieważ ciąg daty jest pierwszymi sześcioma cyframi, przesunięcie to `0`.

   :::image type="content" alt-text="zrzut ekranu przedstawiający skonfigurowany validator daty." source="../media/date-validator.png" lightbox="../media/date-validator.png":::

### <a name="functional-processors-as-validators"></a>Procesory funkcjonalne jako validatory

Jako prawidłowych punktów sprawdzania można używać procesorów funkcji w przypadku niektórych najczęściej używanych kodów SIT. Umożliwia to zdefiniowanie własnego wyrażenia regularnego przy jednoczesnym upewnieniu się, że te wyrażenia przechodzą dodatkowe testy wymagane przez usługę SIT. Na przykład Func_India_Aadhar, że niestandardowe wyrażenie regularne określone przez Ciebie przejdzie logikę poprawności wymaganą dla karty Indian Aadhar. Aby uzyskać więcej informacji na temat funkcji DLP, które mogą być używane jako prawidłowe wartości, zobacz [Funkcje typu informacji poufnych](sit-functions.md). 

### <a name="luhn-check-validator"></a>Sprawdzanie sprawdzania przez Luhna

Jeśli masz niestandardowy typ informacji poufnych, który zawiera zwykłe wyrażenie, które powinno przejść do [algorytmu Luhna](https://en.wikipedia.org/wiki/Luhn_algorithm), możesz użyć sprawdzanie luhna.

## <a name="sensitive-information-type-additional-checks"></a>Dodatkowe testy typu informacji poufnych

Oto definicje i kilka przykładów dostępnych dodatkowych testów.

**Wyklucz określone dopasowania**: ten sprawdzanie pozwala definiować słowa kluczowe, które mają być wykluczone podczas wykrywania dopasowania edytowanego wzorca. Możesz na przykład wykluczyć testowe numery kart kredytowych, takie jak "4111111111111111", aby nie były zgodne jako prawidłowe numery.

**Zaczyna się od** znaków lub nie zaczyna się od znaków: Ten check pozwala definiować znaki, od których muszą lub nie muszą zaczynać się dopasowane elementy. Jeśli na przykład chcesz, aby wzorzec wykrywał tylko numery kart kredytowych, które zaczynają się od cyfr 41, 42 lub 43, wybierz  pozycję Zaczyna się od i dodaj do listy liczby 41, 42 i 43, rozdzielając je przecinkami. 

**Kończy się znakami** lub nie kończy się znakami: Ten check pozwala definiować znaki, na które muszą lub nie muszą się kończyć dopasowane elementy. Jeśli na przykład Twój numer identyfikacyjny pracownika nie może kończyć się 0 lub 1, zaznacz pole  wyboru Nie kończy się na i dodaj do listy liczby 0 i 1, rozdzielając je przecinkami.

**Wyklucz zduplikowane** znaki: ten sprawdzanie pozwala zignorować dopasowania, w których wszystkie cyfry są takie same. Jeśli na przykład sześciocyfrowy numer identyfikacyjny pracownika nie może mieć wszystkich cyfr, możesz wybrać pozycję Wyklucz zduplikowane  znaki, aby wykluczyć ze 111111, 222222, 333333, 444444, 555555, 666666, 777777, 888888, 999999 i 0000000 z listy prawidłowych dopasowania identyfikatora pracownika.

**Dołączanie lub wykluczanie prefiksów**: ten kod wyboru umożliwia zdefiniowanie słów kluczowych, które muszą lub nie mogą zostać znalezione bezpośrednio przed dopasowaną jednostką. W zależności od wybranego wyboru, jednostki zostaną dopasowane lub nie, jeśli będą poprzedzone prefiksami, które tutaj dołączysz. Jeśli na przykład **zostanie** wykluczony prefiks **GUID:**, żadne jednostki poprzedzone identyfikatorem **GUID:** nie zostaną uznane za zgodne.

**Uwzględnianie lub wykluczanie sufiksów** Ten sprawdzanie umożliwia zdefiniowanie słów kluczowych, które muszą lub nie muszą znajdować się bezpośrednio po pasującej encji. W zależności od wybranego wyboru zostaną dopasowane jednostki, jeśli po nich będą stosowane sufiksy, które dołączysz tutaj. Jeśli na przykład wykluczysz **sufiks** **:GUID**, nie zostanie dopasowany żaden tekst, po którym następuje **:GUID** .
