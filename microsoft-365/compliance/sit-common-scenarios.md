---
title: Typowe scenariusze użycia dla typów informacji poufnych
f1.keywords:
- NOCSH
ms.author: chrfox
author: v-tophillips
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
description: Jak wdrożyć typowe typy informacji poufnych w scenariuszach użycia przypadków
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 39afa17fc7bf258848de9d5554b3dd56a1ce21b5
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525740"
---
# <a name="common-usage-scenarios-for-sensitive-information-types"></a>Typowe scenariusze użycia dla typów informacji poufnych

W tym artykule opisano sposób wdrażania niektórych typowych scenariuszy przypadków użycia informacji poufnych (SIT). Możesz użyć tych procedur jako przykładów i dostosować je do określonych potrzeb.

## <a name="protect-credit-card-numbers"></a>Ochrona numerów kart kredytowych

Bank Contoso musi sklasyfikować numery kart kredytowych, które wydaje jako poufne. Karty kredytowe zaczynają się od zestawu 6-cyfrowych wzorców. Chcą dostosować definicję wyjściowej karty kredytowej, aby wykrywać wyłącznie numery kart kredytowych, zaczynając od wzorców 6-cyfrowych.

**Sugerowane rozwiązanie**

1. Utwórz kopię karty kredytowej SIT. Należy wykonać podane czynności [, aby skopiować](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) i zmodyfikować typ informacji poufnych w celu skopiowania karty kredytowej SIT.
1. Edytuj wzorzec ufności. Postępuj zgodnie z instrukcjami [edycji lub usuwania wzorca typów informacji poufnych](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Dodaj pole wyboru "zaczyna się od" i dodaj listę cyfr  koszy (sformatowanych & niesformatowanych). Aby na przykład zagwarantować, że tylko karty kredytowe rozpoczynające się od 411111 & 433512 będą uznawane za prawidłowe, dodaj poniższe informacje do listy 4111 11, 4111-11, 411111, 4335 12, 4335-12, 433512.
1. Powtórz krok 2 & 3, aby uzyskać wzorzec niskiej ufności.

## <a name="test-numbers-similar-to-social-security-numbers"></a>Numery testowe podobne do numerów PESEL

Firma Contoso zidentyfikuje kilka 9-cyfrowych numerów testów, które powodują wyzwolenie wyników fałszywie dodatnich w zasadach ochrony przed utratą danych (DLP, Data Loss Prevention) numerów PESEL. Te numery powinny być wykluczone z listy prawidłowych dopasowania dla numeru SSN.

**Sugerowane rozwiązanie**

1. Utwórz kopię SSN SIT. Instrukcje kopiowania [i modyfikowania typu informacji poufnych](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) w celu skopiowania pliku SSN SIT.
1. Edytuj wzorzec ufności. Postępuj zgodnie z instrukcjami [edycji lub usuwania wzorca typów informacji poufnych](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Dodaj liczby do wykluczenia podczas dodatkowego sprawdzania "wykluczaj określone wartości". Aby na przykład wykluczyć 239-23-532 & 23923532, wystarczy dodać 23923532 wystarczy
1. Powtórz krok 2 & 3, aby uzyskać również inne wzorce ufności

## <a name="phone-numbers-in-signature-trigger-match"></a>Telefon w wyzwalaczu podpisu

Firma Contoso w australii znajduje, że numery telefonów w podpisach wiadomości e-mail powodują wyzwolenie dopasowania dla zasad DLP ich numerów firmy w Australii.

**Sugerowane rozwiązanie**

Dodaj grupę "not" do elementów obsługi, używając listy słów kluczowych zawierającej często używane słowa kluczowe w podpisie wiadomości e-mail, na przykład "Telefon", "Telefon komórkowy", "poczta e-mail", "Dziękuję i uważaj" itp. Aby zapewnić większą dokładność, odległość tej listy słów kluczowych do mniejszej wartości, takiej jak 50 znaków. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do niestandardowych typów informacji poufnych](create-a-custom-sensitive-information-type.md).

## <a name="unable-to-trigger-aba-routing-policy"></a>Nie można wyzwolić zasad routingu ABA

Zasady DLP nie mogą wyzwalać zasad routingu ABA w dużych plikach programu Excel, ponieważ wymagane słowo kluczowe nie znajduje się w ciągu 300 znaków.

**Sugerowane rozwiązanie**

Utwórz kopię wbudowanego programu SIT i edytuj ją, aby zmienić odległość listy słów kluczowych od "300 znaków" na "Dowolne miejsce w dokumencie".

> [!TIP]
> Możesz edytować listę słów kluczowych, aby uwzględnić/wykluczyć słowa kluczowe związane z Twoją organizacją.

## <a name="unable-to-detect-credit-card-numbers-with-unusual-delimiters"></a>Nie można wykryć numerów kart kredytowych za pomocą nietypowych ograniczników

Firma Contoso Bank wykryła, że niektórzy pracownicy mają numery kart kredytowych ze znakiem "/" jako ogranicznikiem, na przykład 1111/4111/1111/1111, który nie jest wykrywany przez definicję karty kredytowej w pudełku. Firma Contoso chce zdefiniować własne regex i zweryfikować je przy użyciu narzędzia LuhnCheck.

**Sugerowane rozwiązanie**

1. Utwórz kopię karty kredytowej SIT, korzystając z procedury opisanej w dostosowywanie wbudowanego [typu informacji poufnych](customize-a-built-in-sensitive-information-type.md).
1. Dodawanie nowego deseniu
1. W elemencie podstawowym wybierz wyrażenie regularne
1. Zdefiniuj wyrażenie regularne, które zawiera wyrażenie regularne "/", a następnie wybierz pozycję validator i wybierz pozycję luhncheck lub func_credit_card, aby zapewnić, że polecenie regex także przejdzie przez wyrażenie LuhnCheck.

## <a name="ignore-a-disclaimer-notice"></a>Ignorowanie powiadomienia o zrzeczeniu odpowiedzialności

Wiele organizacji dodaje zastrzeżenia prawne, oświadczenia o ujawnianiu informacji, podpisy i inne informacje u góry lub u dołu wiadomości e-mail, które odbierają lub opuszczają te organizacje, a w niektórych przypadkach nawet w organizacji. Sami pracownicy umieszczają podpisy, w tym cytaty motywacji, wiadomości społecznościowe i tak dalej. Zastrzeżenie lub podpis może zawierać warunki, które są obecne w teksie dw i mogą powodować wiele fałszywie dodatnich wyników.  

Na przykład typowe zastrzeżenie może zawierać wyrazy, takie jak poufne lub poufne, a zasady szukające informacji poufnych wykryją je jako zdarzenie, prowadzące do wielu wyników fałszywie dodatnich. Udostępnienie klientom opcji ignorowania zastrzeżenia może zmniejszyć liczbę wyników fałszywie dodatnich i zwiększyć wydajność zespołu zgodności.

### <a name="example-of-disclaimer"></a>Przykład zastrzeżenia

Rozważ następujące zastrzeżenie:

WAŻNE UWAGA: Ta wiadomość e-mail jest przeznaczona do odbierania tylko przez osoby uprawnione do odbierania poufnych informacji, które może ona zawierać. Wiadomości e-mail do klientów firmy Contoso mogą zawierać informacje poufne i mające uprawnienia prawne. Prosimy nie odczytywać, kopiować, przesyłać dalej ani przechowywać tej wiadomości, chyba że jesteś jej zamierzony adresatem. Jeśli ta wiadomość została odebrana w błędzie, przekaż ją dalej do nadawcy i całkowicie usuń z systemu komputera.

Jeśli w funkcji SIT skonfigurowano wykrywanie słowa kluczowego poufnego, wzorzec będzie wywoływać dopasowanie za każdym razem, gdy w wiadomości e-mail zostanie użyte zastrzeżenie, co prowadzi do wielu wyników fałszywie dodatnich.

### <a name="ignore-disclaimer-using-prefix-and-suffix-in-sit"></a>Ignorowanie zastrzeżenia przy użyciu prefiksu i sufiksu w funkcji SIT

Jednym ze sposobów ignorowania wystąpień słów kluczowych w zastrzemieniu jest wykluczenie wystąpień słów kluczowych poprzedzonych prefiksem i sufiksem.

Rozważ to zastrzeżenie:

WAŻNE UWAGA: Ta wiadomość e-mail jest przeznaczona do odbierania tylko przez osoby uprawnione do odbierania *poufnych* informacji **, które może ona zawierać**. Wiadomości e-mail do klientów firmy Contoso mogą zawierać informacje poufne i mające uprawnienia prawne. Prosimy nie odczytywać, kopiować, przesyłać dalej ani przechowywać tej wiadomości, chyba że jesteś jej zamierzony adresatem. Jeśli ta wiadomość została odebrana w błędzie, przekaż ją dalej do nadawcy i całkowicie usuń z systemu komputera.

Mamy dwa wystąpienia słowa kluczowego "poufne", a jeśli skonfigurujemy sit tak, aby ignorował wystąpienia tego słowa kluczowego poprzedzone prefiksami (kursywą w przykładzie), a następnie sufiksami (pogrubionymi w przykładzie), w większości przypadków można zignorować zastrzeżenia.

Aby zignorować zastrzeżenie przy użyciu prefiksu i sufiksu:

1. Dodaj dodatkowe testy w bieżącej wersji usługi SIT, aby wykluczyć tekst prefiksu i sufiksu do słowa kluczowego, które chcemy zignorować w zastrzegeniu.
1. Wybierz opcję wykluczenia prefiksu, a w polu **tekstowym Prefiksy** wprowadź **informacje, które są.**
1. Wybierz, aby wykluczyć sufiks i w polu **tekstowym Sufiksy** wprowadź **sufiks i ustaw uprawnienia prawne**.
1. Powtórz tę procedurę dla innych wystąpień słów kluczowych w zastrzeniu, jak pokazano na poniższej ilustracji.

### <a name="ignore-disclaimer-by-excluding-secondary-elements"></a>Ignoruj zastrzeżenie, wykluczając elementy dodatkowe

Innym sposobem na dodanie listy elementów pomocniczych (wystąpień w zrzeczeniu odpowiedzialności), które należy wykluczyć, jest wykluczenie elementów pomocniczych.

Rozważ to zastrzeżenie:

WAŻNE UWAGA: Ta wiadomość e-mail jest przeznaczona do odbierania tylko przez osoby uprawnione do odbierania poufnych informacji, które może ona zawierać. Wiadomości e-mail do klientów firmy Contoso mogą zawierać informacje poufne i mające uprawnienia prawne. Prosimy nie odczytywać, kopiować, przesyłać dalej ani przechowywać tej wiadomości, chyba że jesteś jej zamierzony adresatem. Jeśli ta wiadomość została odebrana w błędzie, przekaż ją dalej do nadawcy i całkowicie usuń z systemu komputera.

W tym przykładzie mamy dwa wystąpienia słowa kluczowego "poufne". Jeśli skonfigurujemy usługę SIT tak, aby ignorowała wystąpienia tego słowa kluczowego w zrzeczeniu odpowiedzialności (podkreślona na czerwono), w większości przypadków możemy zignorować zastrzeżenia.

:::image type="content" source="../media/sit-scenario-edit-pattern.png" alt-text="Możesz dodać więcej warunków do wzorca, aby wykluczyć dodatkowe wystąpienia w zrzeczeniu odpowiedzialności.":::

Aby zignorować zastrzeżenie przy użyciu elementów pomocniczych:

1. W **elementach pomocnych** wybierz pozycję Nie ma żadnej z tych grup.
1. Dodaj wystąpienia zastrzeżenia, które chcemy zignorować jako listę słów kluczowych/słownik.
1. Dodaj słowa kluczowe jako nowy wiersz, który chcemy zignorować. Pamiętaj, że długość każdego tekstu nie może być większa niż 50 znaków.
1. Ustaw odległość tego elementu od 50 do 60 znaków elementu podstawowego.
