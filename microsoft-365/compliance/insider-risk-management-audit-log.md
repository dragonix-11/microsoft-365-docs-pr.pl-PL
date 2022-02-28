---
title: Dziennik inspekcji zarządzania ryzykiem w niejawnym programie testów
description: Informacje o dzienniku inspekcji zarządzania ryzykiem niejawnego programu testów w programie Microsoft 365
keywords: Microsoft 365, zarządzanie ryzykiem w niejawnym programie testów, zarządzanie ryzykiem, zgodność
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 2bf453e8856f69e9ddb8c7c7a9264267ef77b4f0
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989701"
---
# <a name="insider-risk-management-audit-log"></a>Dziennik inspekcji zarządzania ryzykiem w niejawnym programie testów

Dziennik inspekcji zarządzania ryzykiem w ramach niejawnego programu testów umożliwia Ci pozostawanie na bieżąco z działaniami, które zostały wykonane w ramach funkcji zarządzania ryzykiem w ramach niejawnego programu testów. Ten dziennik umożliwia niezależną ocenę działań podejmowane przez użytkowników przypisanych do co najmniej jednej grupy ról zarządzania ryzykiem w niejawnym programie testów. Dziennik inspekcji zarządzania ryzykiem w niejawnym programie testów jest automatycznie włączony w organizacji i nie można go wyłączyć.

![Dziennik inspekcji zarządzania ryzykiem w niejawnym programie testów.](../media/insider-risk-audit-log.png)

Dziennik inspekcji jest automatycznie i natychmiast aktualizowany za każdym razem, gdy są monitorowane działania i w dzienniku są zachowywane informacje o aktywności przez 180 dni (około sześciu miesięcy). Po 180 dniach dane dotyczące tej aktywności zostaną trwale usunięte z dziennika.

Do obszarów monitorowania aktywności należą:

- Policies (zasady)
- Sprawy
- Alerty
- Ustawienia
- Użytkownicy
- Powiadomienia o szablonach

Aby można było wyświetlać i eksportować dane z dziennika inspekcji, należy przypisać użytkowników do grup ról Tester *Risk Management* lub *Insider Risk Management.* Aby dowiedzieć się więcej o grupach ról zarządzania ryzykiem w niejawnym programie testów, zobacz Wprowadzenie do zarządzania ryzykiem w niejawnym programie [testów Krok 1. Włączanie uprawnień](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management).

> [!NOTE]
> Dziennik inspekcji zarządzania ryzykiem w ramach niejawnego programu testów nie jest skojarzony z Microsoft 365 inspekcji, ale jest niezależnymi systemami inspekcji i rejestruje informacje dotyczące osobnych działań. Wyłączenie Microsoft 365 inspekcji nie ma wpływu na inspekcję aktywności w ramach zarządzania ryzykiem w ramach niejawnego programu testów.

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Wyświetlanie aktywności w dzienniku inspekcji ryzyka niejawnego programu testów

Aby wyświetlić aktywność funkcji monitorowaną w celu zarządzania ryzykiem w ramach niejawnego programu testów, przejdź do linku Dziennik inspekcji niejawnego programu testów i **wybierz link Dziennik** inspekcji ryzyka niejawnego programu testów w prawym górnym obszarze dowolnej karty zarządzanie ryzykiem w ramach niejawnego programu testów. W przypadku działań w zakresie zarządzania ryzykiem w niejawnym programie testów będą domyślnie wyświetlane następujące informacje:

- **Działanie:** Opis działania wykonanego przez użytkownika w ramach rozwiązania do zarządzania ryzykiem w ramach niejawnego programu testów.
- **Kategoria:** Obszar lub element, w którym wykonano dane działanie. Na przykład po wykonaniu *działań zmiany zasad* zobaczysz kategorię Zasady.
- **Działanie wykonywane przez:** Nazwa użytkownika, który wykonał działanie.
- **Data:** Data i godzina wykonania działania. Data i godzina to lokalna data i godzina dla Twojej organizacji.

Aby uzyskać więcej informacji o zarejestrowanym działaniu, wybierz je, aby wyświetlić okienko szczegółów aktywności. To okienko zawiera dodatkowe informacje o działaniu.

## <a name="columns-and-filtering"></a>Kolumny i filtrowanie

Aby ułatwić audytorom przeglądanie rejestrowanej aktywności, filtrowanie jest obsługiwane w dzienniku **inspekcji ryzyka niejawnego programu testów**. W przypadku podstawowego filtrowania dostępne są kolumny kolejki do dodania do widoku w celu zapewnienia różnych przestawnych danych dla plików i wiadomości. Możesz filtrować działania według **pól Kategoria, Zakres dat** i Aktywność **wykonywana przez** .

Aby dodać lub usunąć nagłówki kolumn dla kolejki działań, użyj kontrolki Dostosuj **kolumny** i wybierz jedną z opcji kolumn. Te kolumny są mapowane na typowe warunki obsługiwane w **dzienniku** inspekcji ryzyka niejawnego programu testów i są wymienione w dalszej części tego artykułu.

## <a name="audit-log-export"></a>Eksportowanie dziennika inspekcji

Użytkownicy przypisani do grup  ról Zarządzanie ryzykiem niejawnego programu testów lub Niejawny program testów zarządzania ryzykiem mogą wyeksportować wszystkie działania w dzienniku inspekcji do pliku programu .csv (wartości rozdzielone przecinkami),  wybierając pozycję Eksportuj na stronie dziennika inspekcji ryzyka niejawnego programu testów.  W zależności od działania niektóre pola działania mogą nie mieć zastosowania do tego działania i będą wyświetlane jako puste w eksportowanych plikach.

Plik zawiera informacje o aktywności w następujących polach:

- **Działanie wykonywane przez:** Nazwa użytkownika modyfikującego wartość elementu. Użytkownicy wymienini w tym miejscu zostali przypisani do co najmniej jednej z następujących grup ról ról zarządzania ryzykiem w niejawnym programie testów [: Zarządzanie](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management) ryzykiem niejawnego programu testów *,* Administratorzy zarządzania ryzykiem w niejawnym programie testów *,* Analitycy zarządzający niejawnym programem testów i zarządzania *ryzykiem.* Każda grupa ról ma różne poziomy uprawnień do zarządzania funkcjami ryzyka niejawnego programu testów.
- **Działanie:** Działanie wykonane na pozycji. Wartości są *przeglądane, usunięte, dodane, edytowane zasady, sprawy, użytkownika, alerty* *i Ustawienia.*
- **Dodano**: obiekty, które zostały dodane podczas działania, takie jak użytkownicy, typy plików lub domeny.
- **Głośność alertu**: Poziom głośności alertów zdefiniowany w ustawieniach zarządzania ryzykiem w niejawnym programie testów.
- **Kwota**: aktualnie wybrane kwoty wskaźników niestandardowych dla zasad.
- **Identyfikator środka** trwałego: Identyfikator zasobu o priorytecie środka trwałego, na który wykonano dane działanie.
- **Kategoria:** Kategoria zmodyfikowanego elementu. Wartościami *są szablony Zasady, Sprawy, Użytkownicy, Alerty Ustawienia i* *Powiadomienia.*
- **Data:** Data i godzina, które są wyświetlane w lokalnej dacie i godzinie organizacji.
- **Opis**: dane wprowadzane przez użytkownika dla obiektu, na który ma być podejmowane działanie (na przykład zasady lub grupa użytkowników priorytetu).
- **Zasady DLP**: Wybrane zasady ochrony przed utratą danych (DLP), które mają wyzwalać dołączenie do zasad zarządzania ryzykiem w niejawnym programie testów.
- **Wskaźnik**: wskaźnik w ustawieniach ryzyka niejawnego programu testów, na których wykonano dane działanie (na przykład dodanie lub usunięcie wskaźnika).
- **Szablon powiadomienia**: w szablonie powiadomienia wykonano dane działanie.
- **Liczba dni**: Okno aktywacji zasad zdefiniowane w ustawieniach ryzyka niejawnego programu testów.
- **Liczba plików**: Limit liczby plików zdefiniowany w ustawieniach zarządzania ryzykiem w niejawnym programie testów.
- **Szablon zasad**: należy do szablonu zasad, na podstawie którego działają wskaźniki.
- **Poprzednia kwota**: Wcześniej wybrane kwoty wskaźników niestandardowych dla zasad.
- **Grupa użytkowników o priorytecie**: grupa użytkowników o priorytecie, na podstawie których wykonano działanie.
- **Usunięto**: obiekty, które zostały usunięte podczas działania, takie jak użytkownicy, typy plików lub domeny.
- **Nadawca**: pole nadawcy szablonu powiadomienia, na podstawie których wykonano działanie.
- **Zasady docelowe**: zasady, na których wykonano dane działanie (takie jak dodanie użytkownika lub usunięcie użytkownika).
- **Treść wiadomości szablonu**: Treść wiadomości szablonu powiadomienia, na podstawie których wykonano dane działanie.
- **Temat szablonu**: pole tematu szablonu powiadomienia, na podstawie których wykonano dane działanie.
- **Użytkownik:** Użytkownik, na podstawie których wykonano dane działanie.
