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
description: Jak zaimplementować typowe typy informacji poufnych w scenariuszach przypadków użycia
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 54945a3ac6f13ed541cef212305f713d8b5d2b73
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633372"
---
# <a name="common-usage-scenarios-for-sensitive-information-types"></a>Typowe scenariusze użycia dla typów informacji poufnych

W tym artykule opisano sposób implementowania niektórych typowych scenariuszy przypadków użycia typu informacji poufnych (SIT). Możesz użyć tych procedur jako przykładów i dostosować je do konkretnych potrzeb.

## <a name="protect-credit-card-numbers"></a>Ochrona numerów kart kredytowych

Firma Contoso Bank musi sklasyfikować numery kart kredytowych, które wystawiają jako poufne. Ich karty kredytowe zaczynają się od zestawu sześciocyfrowych wzorców. Chcą dostosować definicję wbudowanej karty kredytowej, aby wykrywać tylko numery kart kredytowych, zaczynając od ich sześciocyfrowych wzorców.

**Sugerowane rozwiązanie**

1. Utwórz kopię karty kredytowej SIT. Wykonaj kroki, aby [skopiować i zmodyfikować typ informacji poufnych](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) , aby skopiować kartę kredytową SIT.
1. Edytuj wzorzec wysokiej ufności. Wykonaj kroki [edytowania lub usuwania wzorca typów informacji poufnych](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Dodaj zaznaczenie "zaczyna się od" i dodaj listę cyfry pojemnika (sformatowana & niesformatowana). Aby na przykład upewnić się, że tylko karty kredytowe rozpoczynające się od 411111 & 433512 powinny być uznawane za prawidłowe, dodaj następujące elementy do listy 4111 11, 4111-11, 411111, 4335 12, 4335-12, 433512.
1. Powtórz krok 2 & 3 dla wzorca niskiej ufności.

## <a name="test-numbers-similar-to-social-security-numbers"></a>Numery testowe podobne do numerów ubezpieczenia społecznego

Firma Contoso zidentyfikowała kilka dziewięciocyfrowych liczb testowych, które wyzwalają fałszywie dodatnie dopasowania w zasadach ochrony przed utratą danych (DLP) w numerze ubezpieczenia społecznego (SSN). Chcą wykluczyć te liczby z listy prawidłowych dopasowań dla nazwy SSN.

**Sugerowane rozwiązanie**

1. Utwórz kopię SSN SIT. Wykonaj kroki, aby [skopiować i zmodyfikować typ informacji poufnych](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) , aby skopiować nazwę SSN SIT.
1. Edytuj wzorzec wysokiej ufności. Wykonaj kroki [edytowania lub usuwania wzorca typów informacji poufnych](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Dodaj liczby do wykluczenia w dodatkowym czeku "wyklucz określone wartości". Aby na przykład wykluczyć & 23923532 239-23-532, wystarczy dodać 23923532
1. Powtórz krok 2 & 3 również dla innych wzorców ufności

## <a name="phone-numbers-in-signature-trigger-match"></a>Numery telefonów w dopasowanym wyzwalaczu podpisu

Firma Contoso z siedzibą w Australii stwierdza, że numery telefonów w sygnaturach e-mail wyzwalają dopasowanie do zasad DLP numeru firmy w Australii.

**Sugerowane rozwiązanie**

Dodaj grupę "nie" w elementach pomocniczych przy użyciu listy słów kluczowych zawierającej często używane słowa kluczowe w podpisie wiadomości e-mail, takie jak "Telefon", "Mobile", "email", "Thanks and regards" itp. Zachowaj bliskość tej listy słów kluczowych do mniejszej wartości, takiej jak 50 znaków, aby uzyskać lepszą dokładność. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do niestandardowych typów informacji poufnych](create-a-custom-sensitive-information-type.md).

## <a name="unable-to-trigger-aba-routing-policy"></a>Nie można wyzwolić zasad routingu usługi ABA

Zasady DLP nie mogą wyzwalać zasad numerów routingu ABA w dużych plikach programu Excel, ponieważ wymagane słowo kluczowe nie znajduje się w ciągu 300 znaków.

**Sugerowane rozwiązanie**

Utwórz kopię wbudowanego interfejsu SIT i edytuj ją, aby zmienić bliskość listy słów kluczowych z "300 znaków" na "Anywhere in the document".

> [!TIP]
> Możesz edytować listę słów kluczowych w celu uwzględnienia/wykluczenia słów kluczowych, które są istotne dla Twojej organizacji.

## <a name="unable-to-detect-credit-card-numbers-with-unusual-delimiters"></a>Nie można wykryć numerów kart kredytowych z nietypowymi ogranicznikami

Contoso Bank zauważył, że niektórzy z ich pracowników udostępniają numery kart kredytowych z ogranicznikiem "/", na przykład 4111/1111/1111/1111, który nie jest wykrywany przez definicję karty kredytowej. Firma Contoso chce zdefiniować własne regex i zweryfikować go przy użyciu narzędzia LuhnCheck.

**Sugerowane rozwiązanie**

1. Utwórz kopię karty kredytowej SIT, wykonując kroki opisane [w temacie Dostosowywanie wbudowanego typu informacji poufnych](customize-a-built-in-sensitive-information-type.md).
1. Dodawanie nowego wzorca
1. W elemencie podstawowym wybierz wyrażenie regularne
1. Zdefiniuj wyrażenie regularne, które zawiera wyrażenie "/" jako część wyrażenia regularnego, a następnie wybierz moduł sprawdzania poprawności i wybierz pozycję luhncheck lub func_credit_card, aby upewnić się, że regex również przekazuje pole Wyboru Luhna.

## <a name="ignore-a-disclaimer-notice"></a>Ignoruj powiadomienie o zrzeczeniu się odpowiedzialności

Wiele organizacji dodaje zastrzeżenia prawne, oświadczenia o ujawnieniu, podpisy lub inne informacje w górnej lub dolnej części wiadomości e-mail, które wprowadzają lub opuszczają swoje organizacje, a w niektórych przypadkach nawet w organizacjach. Sami pracownicy umieszczają podpisy, w tym – cytaty motywacyjne, wiadomości społecznościowe itd. Zastrzeżenie lub podpis może zawierać terminy, które są obecne w leksykonie CC i mogą generować wiele wyników fałszywie dodatnich.  

Na przykład typowe zastrzeżenie może zawierać wyrazy takie jak poufne lub poufne, a zasady szukające poufnych informacji wykryje ją jako zdarzenie, co prowadzi do wielu fałszywie dodatnich wyników. Dzięki temu zapewnienie klientom opcji ignorowania zrzeczenia się może zmniejszyć liczbę wyników fałszywie dodatnich i zwiększyć wydajność zespołu ds. zgodności.

### <a name="example-of-disclaimer"></a>Przykład zastrzeżenia

Rozważ następujące zastrzeżenie:

WAŻNA UWAGA: Ta wiadomość e-mail ma być odbierana tylko przez osoby uprawnione do otrzymywania poufnych informacji, które mogą zawierać. Wiadomości e-mail do klientów firmy Contoso mogą zawierać informacje poufne i prawnie uprzywilejowane. Nie odczytuj, nie kopiuj, nie przesyłaj dalej ani nie przechowuj tej wiadomości, chyba że jesteś jej zamierzonym odbiorcą. Jeśli ten komunikat został wyświetlony o błędzie, prześlij go do nadawcy i usuń go całkowicie z systemu komputerowego.

Jeśli usługa SIT została skonfigurowana do wykrywania słowa kluczowego poufnego, wzorzec wywoła dopasowanie za każdym razem, gdy w wiadomości e-mail jest używane zastrzeżenie, co prowadzi do wielu wyników fałszywie dodatnich.

### <a name="ignore-disclaimer-using-prefix-and-suffix-in-sit"></a>Ignoruj zastrzeżenie przy użyciu prefiksu i sufiksu w usłudze SIT

Jednym ze sposobów ignorowania wystąpień słów kluczowych w zastrzeżeniu jest wykluczenie wystąpień słów kluczowych, które są poprzedzone prefiksem, a następnie sufiksem.

Rozważ to zastrzeżenie:

WAŻNA UWAGA: Ta wiadomość e-mail ma być odbierana tylko przez osoby *uprawnione do otrzymywania* poufnych **informacji, które mogą zawierać**. Wiadomości e-mail do klientów firmy Contoso mogą zawierać informacje poufne i prawnie uprzywilejowane. Nie odczytuj, nie kopiuj, nie przesyłaj dalej ani nie przechowuj tej wiadomości, chyba że jesteś jej zamierzonym odbiorcą. Jeśli ten komunikat został wyświetlony o błędzie, prześlij go do nadawcy i usuń go całkowicie z systemu komputerowego.

Mamy dwa wystąpienia słowa kluczowego "poufne" i jeśli skonfigurujemy interfejs SIT do ignorowania wystąpień tego słowa kluczowego poprzedzonego prefiksami (kursywą w przykładzie), a następnie sufiksami (pogrubionymi w przykładzie), możemy osiągnąć ignorowanie zastrzeżeń w większości przypadków.

Aby zignorować zastrzeżenie przy użyciu prefiksu i sufiksu:

1. Dodaj dodatkowe kontrole w bieżącym środowisku SIT, aby wykluczyć prefiks i tekst sufiksu do słowa kluczowego, które chcemy zignorować w zastrzeżeniu.
1. Wybierz opcję wykluczenia prefiksu, a w polu tekstowym **Prefiksy** wprowadź **informacje, które są**.
1. Wybierz, aby wykluczyć sufiks i w polu tekstowym **Sufiksy** wprowadź **i uprawnienia prawne**.
1. Powtórz ten proces dla innych wystąpień słów kluczowych w zastrzeżeniu, jak pokazano na poniższej ilustracji.

### <a name="ignore-disclaimer-by-excluding-secondary-elements"></a>Ignoruj zastrzeżenie, wykluczając elementy pomocnicze

Innym sposobem dodania listy elementów pomocniczych (wystąpień w zastrzeżeniu), które należy wykluczyć, jest wykluczenie elementów pomocniczych.

Rozważ to zastrzeżenie:

WAŻNA UWAGA: Ta wiadomość e-mail ma być odbierana tylko przez osoby uprawnione do otrzymywania poufnych informacji, które mogą zawierać. Wiadomości e-mail do klientów firmy Contoso mogą zawierać informacje poufne i prawnie uprzywilejowane. Nie odczytuj, nie kopiuj, nie przesyłaj dalej ani nie przechowuj tej wiadomości, chyba że jesteś jej zamierzonym odbiorcą. Jeśli ten komunikat został wyświetlony o błędzie, prześlij go do nadawcy i usuń go całkowicie z systemu komputerowego.

W tym przykładzie mamy dwa wystąpienia słowa kluczowego "poufne". Jeśli skonfigurujemy funkcję SIT tak, aby ignorowała wystąpienia tego słowa kluczowego w zastrzeżeniu (podkreślonym jako czerwony), w większości przypadków możemy ignorować zastrzeżenia.

:::image type="content" source="../media/sit-scenario-edit-pattern.png" alt-text="Możesz dodać więcej warunków do wzorca, aby wykluczyć dodatkowe wystąpienia w zastrzeżeniu.":::

Aby zignorować zastrzeżenie przy użyciu elementów pomocniczych:

1. Wybierz pozycję **Nie ma żadnej z tych** grup w elementach pomocniczych.
1. Dodaj wystąpienia zastrzeżenia, które chcemy zignorować jako listę/słownik słów kluczowych.
1. Dodaj słowa kluczowe jako nowy wiersz, który chcemy zignorować. Pamiętaj, że długość każdego tekstu nie może być większa niż 50 znaków.
1. Ustaw bliskość tego elementu na 50–60 znaków elementu podstawowego.
