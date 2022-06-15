---
title: Inspekcja nowego wyszukiwania
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Funkcja Inspekcja nowego wyszukiwania weryfikuje ulepszenia wydajności, kompletność i spójność wyników.
ms.openlocfilehash: e24831eea8c176e8fdfa7608492a5393e786e2d3
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090643"
---
# <a name="audit-new-search-preview"></a>Inspekcja nowego wyszukiwania (wersja zapoznawcza)

Twoja organizacja wymaga dostępu do krytycznych danych zdarzeń dziennika inspekcji, aby uzyskać szczegółowe informacje i dokładniej zbadać działania użytkowników. Wcześniej zadania wyszukiwania w interfejsie użytkownika portal zgodności Microsoft Purview były ograniczone w zakresie możliwości tworzenia współbieżnych zadań wyszukiwania inspekcji i przeglądania historycznych zadań wyszukiwania. Te krytyczne zadania wyszukiwania inspekcji również miały zależność od okna przeglądarki, które pozostało otwarte do ukończenia.

Funkcja Inspekcja nowego wyszukiwania (wersja zapoznawcza) opiera się na istniejących funkcjach wyszukiwania i zawiera następujące kluczowe ulepszenia:

- Zadania wyszukiwania zainicjowane za pośrednictwem interfejsu użytkownika portalu zgodności nie wymagają już, aby okno przeglądarki internetowej pozostało otwarte do ukończenia. Te zadania będą nadal uruchamiane nawet po zamknięciu okna przeglądarki.
- Ukończone zadania wyszukiwania są teraz przechowywane, co daje klientom możliwość odwoływania się do historycznych wyszukiwań inspekcji. Te zadania wyszukiwania są prezentowane w interfejsie użytkownika, wyświetlając nazwę wyszukiwania, stan zadania wyszukiwania, postęp %, liczbę wyników, czas utworzenia i wyszukiwane przez.
- Każdy użytkownik konta inspekcji administratora może mieć maksymalnie 10 zadań wyszukiwania w toku naraz.

## <a name="information-to-get-started"></a>Informacje umożliwiające rozpoczęcie pracy

Wyświetl dostępną dokumentację Inspekcja w Microsoft Purview, ponieważ środowiska tworzenia i eksportowania zadań wyszukiwania mają wiele podobieństw do bieżącego środowiska wyszukiwania:

- [Przeszukaj dziennik inspekcji w portal zgodności Microsoft Purview](search-the-audit-log-in-security-and-compliance.md) (pamiętaj, że program PowerShell nie jest jeszcze zgodny z usługą Audit Search V2)
- [Szczegółowe właściwości w dzienniku inspekcji](detailed-properties-in-the-office-365-audit-log.md)
- [Eksportuj, konfiguruj i wyświetlaj rekordy dziennika inspekcji](export-view-audit-log-records.md)

Dodatkowe informacje:

- Wyszukiwanie za pośrednictwem sesji exo programu PowerShell przy użyciu polecenia cmdlet Search-UnifiedAuditLog nie jest obecnie zgodne z nowym wyszukiwaniem.
- Zadania wyszukiwania mogą spełniać następujące kryteria: zakres dat, zakres czasu, nazwa zadania wyszukiwania, działania, użytkownicy, pliki, foldery i witryny.
- Wyszukiwanie i filtrowanie przy użyciu daty, godziny, nazwy wyszukiwania, działań i użytkowników są w pełni funkcjonalne
- Dane dziennika inspekcji będą przechowywane dla zdefiniowanego okresu przechowywania, niezależnie od usunięcia zadania wyszukiwania
- Wyszukiwania utworzone w okresie prywatnej wersji zapoznawczej mogą nie zostać zachowane do przyszłego odwołania po przeniesieniu funkcji Nowe wyszukiwanie do publicznej wersji zapoznawczej.

## <a name="get-started-with-audit-new-search"></a>Wprowadzenie z inspekcją nowego wyszukiwania

Wykonaj poniższe kroki, aby przetestować i zweryfikować środowisko inspekcji nowego wyszukiwania:

1. Przejdź do compliance.microsoft.com
1. Wybierz kartę Inspekcja w lewym panelu strony głównej, aby przejść do narzędzia Inspekcja
1. Wybierz kartę "Nowe wyszukiwanie (wersja zapoznawcza)" w górnej części strony Inspekcja Przeglądu :::image type="content" source="../media/audit-search/audit-new-search.png" alt-text="nowego wyszukiwania w Microsoft Purview":::
1. Przetestuj różne zadania wyszukiwania w narzędziu Inspekcja nowego wyszukiwania przy użyciu różnych kryteriów wyszukiwania.
Niektóre przykłady różnych wyszukiwań obejmują następujące kryteria. Eksploruj te różne metody wyszukiwania podczas wyszukiwania w dzienniku inspekcji.
    - Wyszukiwanie w różnych przedziałach czasowych.
      - Jeden dzień
      - Tygodniu
      - Miesiąc
      - Kilka miesięcy
    - Wyszukiwanie między wybranymi użytkownikami
    - Określanie zakresu wyszukiwania przy użyciu pola działania
    - Dodawanie określonego pliku, folderu lub witryny :::image type="content" source="../media/audit-search/audit-new-search-create.png" alt-text="Opcje inspekcji nowego wyszukiwania w Microsoft Purview":::
1. Zainicjuj kolejne wyszukiwania 2–9 w portalu zgodności. Maksymalnie 10 zadań wyszukiwania można uruchamiać równolegle na jednym koncie.
1. Zapoznaj się z historią zadań wyszukiwania i wybierz różne zadania wyszukiwania, aby uzyskać odpowiednie dane z wyników zadania wyszukiwania. Wyniki można sortować według czasu ich utworzenia, wybierając odpowiedni przycisk w górnej części tabeli.
      :::image type="content" source="../media/audit-search/audit-new-search-columns.png" alt-text="Przeprowadź inspekcję opcji sortowania nowych kolumn wyników wyszukiwania w Microsoft Purview":::
1. Wybierz zadanie wyszukiwania, aby wyświetlić wyniki zadania w formacie elementu wiersza. Poznaj różne funkcje interfejsu użytkownika, w tym:
    - Odwołując się do pełnego zapytania wyszukiwania w górnej części strony, które zawiera wszystkie kryteria wyszukiwania wprowadzone podczas wykonywania oryginalnego wyszukiwania
    - Klikając różne wyniki, aby uzyskać więcej informacji w oknie wysuwanym
    - Filtrowanie między zadaniem wyszukiwania przy użyciu adresu IP, użytkownika, działania, daty, elementu i szczegółów.
    - Eksportowanie niefiltrowanych i przefiltrowanych wyszukiwań
    - Posortuj wyniki, klikając odpowiednie przyciski w górnej części tabeli, w tym datę, adres IP (jeśli ma zastosowanie), użytkownika, działania, elementu i szczegółów (jeśli ma to zastosowanie).
      :::image type="content" source="../media/audit-search/audit-new-search-result-details.png" alt-text="Inspekcja szczegółów wyników nowego wyszukiwania w Microsoft Purview":::

## <a name="audit-search-job-overview"></a>Omówienie zadania wyszukiwania inspekcji

- Zadania wyszukiwania mogą spełniać następujące kryteria: zakres dat, zakres czasu, nazwa zadania wyszukiwania, działania, użytkownicy, pliki, foldery i witryny.
- Pole tekstowe wyszukiwania plików, folderów lub lokacji zwróci wszystkie powiązane wyniki dla odpowiednich plików, folderów i witryn
- Zadania wyszukiwania będą uruchamiane w dolnej części strony wyszukiwania.
  - Zadania wyszukiwania mogą być "w kolejce", "W toku" i "Ukończone"
  - Maksymalnie 10 zadań wyszukiwania "W toku" można ukończyć jednocześnie na użytkownika
- Pełne nazwy wyszukiwania dla zadań można wyświetlić, umieszczając kursor nad zadaniem wyszukiwania
- Zadania wyszukiwania będą wyświetlać nazwę wyszukiwania, stan, postęp %, liczbę wyników, czas tworzenia i przeszukiwane przez

Rysunek 1.1 Narzędzie do wyszukiwania inspekcji & podsumowania zadań wyszukiwania

## <a name="audit-search-results-overview"></a>Omówienie wyników wyszukiwania inspekcji

- Wyniki wyszukiwania są wyświetlane w elemencie wiersza po wybraniu zadania wyszukiwania
- Zapytanie wyszukiwania jest wyświetlane w górnej części strony wyników zadania wyszukiwania, aby uzyskać odwołanie i całkowitą liczbę elementów
  > [!NOTE]
  > Łączna liczba wyników odejmuje duplikaty, dlatego może być mniejsza niż liczba elementów w głównym oknie wyszukiwania inspekcji
- Informacje o dacie, adresie IP, użytkowniku, działaniu i elemencie można znaleźć na stronie wyników zadania wyszukiwania dla każdego elementu
- Wybierz działanie, aby wyświetlić okno wysuwane z większą ilością szczegółów dotyczących działania
- Funkcja filtrowania wyników zadania wyszukiwania może pomóc w przeanalizowaniu wyników.
- Eksport jest w pełni funkcjonalny i eksportuje wszystkie elementy zadania wyszukiwania do pliku .csv. Eksport obsługuje wyniki do 50 K. Rysunek 2.1 — Wyniki zadania wyszukiwania Rysunek 2.2 — Panel filtrowania zadań wyszukiwania Rysunek 2.3 — Przycisk Eksportuj

## <a name="frequently-asked-questions"></a>Często zadawane pytania

- **Czy istnieje maksymalna liczba zadań wyszukiwania na użytkownika?**
  Istnieje maksymalnie 10 zadań wyszukiwania "w toku" na użytkownika. Jeśli użytkownik wymaga więcej niż 10 zadań wyszukiwania, musi poczekać, aż zadanie "w toku" zakończy lub usunie zadanie wyszukiwania. Z pewnością docenimy Twoją opinię na temat tego limitu.
- **Czy usunięcie zadania wyszukiwania powoduje usunięcie danych zaplecza?**
  Nie, usunięcie zadania wyszukiwania spowoduje usunięcie tylko definicji zadania wyszukiwania i skojarzonego wyniku wyszukiwania.
