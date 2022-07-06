---
title: Dziennik inspekcji zarządzania ryzykiem wewnętrznym
description: Dowiedz się więcej o dzienniku inspekcji zarządzania ryzykiem wewnętrznym w usłudze Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, ryzyko wewnętrzne, zarządzanie ryzykiem, zgodność
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
ms.openlocfilehash: 544c31205469bcb810bd3f05d9f686d650df6269
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638196"
---
# <a name="insider-risk-management-audit-log"></a>Dziennik inspekcji zarządzania ryzykiem wewnętrznym

Dziennik inspekcji zarządzania ryzykiem wewnętrznym umożliwia informowanie o działaniach, które zostały podjęte w przypadku funkcji zarządzania ryzykiem wewnętrznym. Ten dziennik umożliwia niezależne przeglądanie akcji wykonywanych przez użytkowników przypisanych do co najmniej jednej grupy ról zarządzania ryzykiem wewnętrznym. Dziennik inspekcji zarządzania ryzykiem wewnętrznym jest automatycznie włączany w organizacji i nie można go wyłączyć.

![Dziennik inspekcji zarządzania ryzykiem wewnętrznym.](../media/insider-risk-audit-log.png)

Dziennik inspekcji jest automatycznie i natychmiast aktualizowany za każdym razem, gdy są monitorowane działania, a dziennik zachowuje informacje o działaniu przez 180 dni (około sześciu miesięcy). Po upływie 180 dni dane działania zostaną trwale usunięte z dziennika.

Obszary uwzględnione w monitorowaniu aktywności obejmują:

- Policies (zasady)
- Przypadkach
- Alerty
- Ustawienia
- Użytkownicy
- Szablony powiadomień

Aby wyświetlić i wyeksportować dane z dziennika inspekcji, użytkownicy muszą być przypisani do grup ról *Insider Risk Management* lub *Insider Risk Management Auditors* . Aby dowiedzieć się więcej na temat grup ról zarządzania ryzykiem wewnętrznym, zobacz [Wprowadzenie do zarządzania ryzykiem wewnętrznym Krok 1. Włączanie uprawnień](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management).

> [!NOTE]
> Dziennik inspekcji zarządzania ryzykiem wewnętrznym nie jest skojarzony z dziennikiem inspekcji platformy Microsoft 365, są niezależnymi systemami inspekcji i przechwytują informacje o oddzielnych działaniach. Wyłączenie inspekcji platformy Microsoft 365 nie ma wpływu na inspekcję działań w ramach zarządzania ryzykiem wewnętrznym.

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Wyświetlanie aktywności w dzienniku inspekcji ryzyka wewnętrznego

Aby wyświetlić aktywność funkcji monitorowaną pod kątem zarządzania ryzykiem wewnętrznym, przejdź do strony i wybierz link **Dziennik inspekcji ryzyka niejawnego** w prawym górnym rogu dowolnej karty zarządzania ryzykiem wewnętrznym. Domyślnie zostaną wyświetlone następujące informacje dotyczące działań związanych z zarządzaniem ryzykiem wewnętrznym:

- **Działania:** Opis działania wykonywanego przez użytkownika w ramach rozwiązania do zarządzania ryzykiem wewnętrznym.
- **Kategorii:** Obszar lub element, w którym wykonano działanie. Na przykład po wykonaniu działań związanych ze zmianą zasad zobaczysz pozycję *Zasady* jako kategorię.
- **Działanie wykonywane przez:** Nazwa użytkownika, który wykonał działanie.
- **Data:** Data i godzina wykonania działania. Data i godzina to lokalna data i godzina organizacji.

Aby uzyskać więcej informacji na temat zarejestrowanego działania, wybierz działanie, aby wyświetlić okienko szczegółów działania. To okienko zawiera dodatkowe informacje o działaniu.

## <a name="columns-and-filtering"></a>Kolumny i filtrowanie

Aby ułatwić audytorom przeglądanie zarejestrowanych działań, filtrowanie jest obsługiwane w **dzienniku inspekcji ryzyka niejawnych testów**. W przypadku filtrowania podstawowego kolumny kolejek są dostępne do dodania do widoku w celu udostępnienia różnych elementów przestawnych dla plików i komunikatów. Działania można filtrować według pól **Kategoria, Zakres dat** i **Działanie wykonywane przez** pola.

Aby dodać lub usunąć nagłówki kolumn dla kolejki działań, użyj kontrolki **Dostosuj kolumny** i wybierz opcje kolumny. Te kolumny są mapowane na typowe warunki obsługiwane w **dzienniku inspekcji ryzyka niejawnego** i są wymienione w dalszej części tego artykułu.

## <a name="audit-log-export"></a>Eksportowanie dziennika inspekcji

Użytkownicy przypisani do grup ról *Insider Risk Management* lub *Insider Risk Management Auditors* mogą eksportować wszystkie działania w dzienniku inspekcji do pliku .csv (wartości rozdzielone przecinkami), wybierając pozycję **Eksportuj** na stronie **dziennika inspekcji ryzyka niejawnych testów** . W zależności od działania niektóre pola działania mogą nie mieć zastosowania do działania, a te pola będą wyświetlane jako puste w wyeksportowanym pliku.

Plik zawiera informacje o działaniach dla następujących pól:

- **Działanie wykonywane przez:** Nazwa użytkownika modyfikująca wartość elementu. Użytkownicy wymienieni tutaj zostali przypisani do co najmniej jednej z następujących [grup ról zarządzania ryzykiem wewnętrznym](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management): *Insider Risk Management*, *Insider Risk Management Admins*, *Insider Risk Management Analysts*, *Insider Risk Management Investigators*. Każda grupa ról ma różne poziomy uprawnień do zarządzania funkcjami ryzyka wewnętrznego.
- **Działania:** Działanie wykonane na elemencie. Wartości to *Wyświetl, Usunięte, Dodane, Edytowane zasady, Przypadek, Użytkownik, Alert* i *Ustawienia.*
- **Dodano**: Obiekty, które zostały dodane podczas działania, takie jak użytkownicy, typy plików lub domeny.
- **Wolumin alertów**: poziom woluminu alertu zdefiniowany w ustawieniach zarządzania ryzykiem wewnętrznym.
- **Kwota**: aktualnie wybrane niestandardowe kwoty wskaźnika dla zasad.
- **Identyfikator zasobu**: identyfikator zasobu priorytetowego zasobu fizycznego, na który wykonano działanie.
- **Kategorii:** Kategoria zmodyfikowanego elementu. Wartości to *zasady, przypadki, użytkownicy, alerty, ustawienia* i *szablony powiadomień.*
- **Data:** Data i godzina wymieniona w lokalnej dacie i godzinie organizacji.
- **Opis**: opis danych wejściowych przez użytkownika dla obiektu, na który działa (na przykład zasad lub grupy użytkowników o priorytecie).
- **Zasady DLP**: zasady Ochrona przed utratą danych w Microsoft Purview (DLP) wybrane w celu wyzwolenia włączenia do zasad zarządzania ryzykiem wewnętrznym.
- **Wskaźnik**: wskaźnik w ustawieniach ryzyka wewnętrznego, na których wykonano działanie (na przykład dodanie lub usunięcie wskaźnika).
- **Szablon powiadomienia**: szablon powiadomienia, na który wykonano działanie.
- **Liczba dni**: okno aktywacji zasad zdefiniowane w ustawieniach ryzyka niejawnego.
- **Liczba plików: limit woluminu** plików zdefiniowany w ustawieniach zarządzania ryzykiem wewnętrznym.
- **Szablon zasad**: szablon zasad, do którego należały wskaźniki.
- **Poprzednia kwota**: wcześniej wybrane niestandardowe kwoty wskaźnika dla zasad.
- **Grupa użytkowników o priorytecie**: priorytetowa grupa użytkowników, na która wykonano działanie.
- **Usunięte**: obiekty, które zostały usunięte podczas działania, takie jak użytkownicy, typy plików lub domeny.
- **Nadawca**: pole nadawcy szablonu powiadomienia, na które wykonano działanie.
- **Zasady docelowe**: zasady, na które wykonano działanie (takie jak dodawanie użytkownika do użytkownika lub usuwanie użytkownika).
- **Treść komunikatu szablonu**: treść komunikatu szablonu powiadomienia, na który wykonano działanie.
- **Temat szablonu**: pole tematu szablonu powiadomienia, na której wykonano działanie.
- **Użytkownika:** Użytkownik, na który wykonano działanie.
