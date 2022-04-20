---
title: Wyświetlaj aktywność inspekcji opiekuna
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Użyj narzędzia do zarządzania opiekunami zbierania elektronicznych materiałów dowodowych (Premium), aby łatwo uzyskać dostęp do działania i wyszukać opiekunów w Twoim przypadku.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: e2de6209e08d6e8dd6f853724f26d026aec1c33f
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993715"
---
# <a name="view-custodian-audit-activity"></a>Wyświetlaj aktywność inspekcji opiekuna

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Czy chcesz sprawdzić, czy użytkownik wyświetlił określony dokument, czy oczyścił element ze swojej skrzynki pocztowej? Usługa Microsoft Purview eDiscovery (Premium) jest teraz zintegrowana z istniejącym narzędziem do wyszukiwania dzienników inspekcji w portalu zgodności usługi Microsoft Purview. Korzystając z tego osadzonego środowiska, możesz użyć narzędzia do zarządzania opiekunami zbierania elektronicznych materiałów dowodowych (Premium), aby ułatwić badanie, łatwo uzyskując dostęp do działań i przeszukując działania opiekunów w Twojej sprawie.

## <a name="get-permissions"></a>Uzyskiwanie uprawnień

Aby przeszukać dziennik inspekcji, musisz mieć przypisaną rolę dzienników inspekcji lub dzienników inspekcji View-Only w Exchange Online. Domyślnie te role są przypisywane do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie Uprawnienia w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>. Aby umożliwić użytkownikowi przeszukiwanie dziennika inspekcji zbierania elektronicznych materiałów dowodowych (Premium) z minimalnym poziomem uprawnień, możesz utworzyć niestandardową grupę ról w Exchange Online, dodać rolę dzienników inspekcji View-Only lub dzienników inspekcji, a następnie dodać użytkownika jako członka nowej grupy ról. Aby uzyskać więcej informacji, zobacz Zarządzanie grupami ról w Exchange Online.

> [!IMPORTANT]
> Jeśli przypiszesz użytkownikowi rolę View-Only Dzienniki inspekcji lub Dzienniki inspekcji na stronie Uprawnienia w portalu zgodności, nie będzie mógł przeszukiwać dziennika inspekcji. Musisz przypisać uprawnienia w Exchange Online. Dzieje się tak, ponieważ podstawowe polecenie cmdlet używane do przeszukiwania dziennika inspekcji jest Exchange Online poleceniem cmdlet.

## <a name="step-1-search-the-audit-log-for-activities-performed-by-a-custodian"></a>Krok 1. Wyszukaj w dzienniku inspekcji działania wykonywane przez opiekuna

1. Przejdź do **obszaru eDiscovery > eDiscovery (Premium)** i otwórz sprawę.
  
2. Kliknij kartę **Źródła** .
  
3. Na stronie **Opiekunowie** wybierz z listy opiekuna, a następnie kliknij pozycję **Wyświetl aktywność opiekuna** na stronie wysuwanej.

    Zostanie wyświetlona strona wyszukiwania działań opiekuna. Zwróć uwagę, że opiekun wybrany w poprzednim kroku jest wyświetlany w polu listy rozwijanej **Kustosz** . W polu listy rozwijanej możesz wybrać różnych opiekunów, ale możesz wyszukiwać tylko jednego opiekuna naraz.

    ![Strona wyszukiwania działań opiekuna.](../media/AeDCustodianActivities1.png)
   
4. Skonfiguruj następujące kryteria wyszukiwania:
      
   1. **Działania** — kliknij listę rozwijaną, aby wyświetlić działania, których można wyszukać. Po uruchomieniu wyszukiwania zostaną wyświetlone tylko rekordy inspekcji dla wybranych działań. Wybranie pozycji **Pokaż wyniki dla wszystkich działań** spowoduje wyświetlenie wyników dla wszystkich działań wykonywanych przez opiekuna zgodnych z innymi kryteriami wyszukiwania.

      ![Lista działań.](../media/CustodianActivityAudit.PNG)
      
   1. **Data rozpoczęcia i data zakończenia** — wybierz zakres dat i godzin, aby wyświetlić zdarzenia, które wystąpiły w tym okresie. Domyślnie wybierane są ostatnie siedem dni. Data i godzina są prezentowane w formacie Uniwersalny czas koordynowany (UTC). Maksymalny zakres dat, który można określić, to jeden rok.
      
   1. **Opiekunowie** — kliknij to pole, a następnie wybierz określonego opiekuna, aby wyświetlić wyniki wyszukiwania. Rekordy inspekcji dla wybranego działania wykonane przez użytkowników wybranych w tym polu są wyświetlane na liście wyników.
      
5. Kliknij ![Przycisk wyszukiwania.](../media/SearchButton.PNG)  , aby uruchomić wyszukiwanie przy użyciu kryteriów wyszukiwania. Wyniki wyszukiwania są ładowane i po kilku chwilach są wyświetlane w obszarze Wyniki na stronie wyszukiwania Działania opiekuna. 

## <a name="step-2-view-the-audit-log-search-results"></a>Krok 2. Wyświetlanie wyników wyszukiwania dziennika inspekcji

Wyniki wyszukiwania dziennika inspekcji są wyświetlane w obszarze Wyniki na stronie dziennika inspekcji opiekuna. Maksymalnie 5000 (najnowszych) zdarzeń jest wyświetlanych w przyrostach 150 zdarzeń. Aby wyświetlić więcej zdarzeń, możesz użyć paska przewijania w okienku Wyniki lub nacisnąć klawisze Shift + End, aby wyświetlić następne 150 zdarzeń.

Wyniki zawierają następujące informacje o każdym zdarzeniu zwracanym przez wyszukiwanie.
- **Data**: data i godzina (w formacie UTC), kiedy wystąpiło zdarzenie.

- **Adres IP**: adres IP urządzenia, które było używane podczas rejestrowania działania. Adres IP jest wyświetlany w formacie adresu IPv4 lub IPv6.

- **Użytkownik**: użytkownik (lub konto usługi), który wykonał akcję, która wyzwoliła zdarzenie.

- **Działanie**: działanie wykonywane przez użytkownika. Ta wartość odpowiada działaniom wybranym na liście rozwijanej Działania. W przypadku zdarzenia z dziennika inspekcji administratora Exchange wartość w tej kolumnie jest Exchange polecenia cmdlet.

- **Element**: obiekt, który został utworzony lub zmodyfikowany w wyniku odpowiedniego działania. Na przykład plik, który został wyświetlony lub zmodyfikowany, lub zaktualizowane konto użytkownika. Nie wszystkie działania mają wartość w tej kolumnie.

- **Szczegóły**: dodatkowe szczegóły dotyczące działania. Ponownie nie wszystkie działania będą miały wartość.

## <a name="step-3-filter-the-search-results"></a>Krok 3. Filtrowanie wyników wyszukiwania

Oprócz sortowania można również filtrować wyniki wyszukiwania w dzienniku inspekcji. Może to pomóc w szybkim filtrowaniu wyników dla określonego użytkownika lub działania. 

Aby filtrować wyniki:

 1. Tworzenie i uruchamianie wyszukiwania dzienników inspekcji.
  
2. Po wyświetleniu wyników kliknij pozycję **Filtruj wyniki**.
 
3. Pola słów kluczowych są wyświetlane pod każdym nagłówkiem kolumny.
  
4. Kliknij jedno z pól pod nagłówkiem kolumny i wpisz wyraz lub frazę, w zależności od kolumny, na której filtrujesz. Wyniki zostaną dynamicznie dostosowane do wyświetlania zdarzeń zgodnych z filtrem.
  
5. Aby wyczyścić filtr, kliknij przycisk **X** w polu filtru lub po prostu kliknij pozycję **Ukryj filtrowanie**.

## <a name="export-the-search-results-to-a-file"></a>Eksportowanie wyników wyszukiwania do pliku

Wyniki wyszukiwania dziennika inspekcji można wyeksportować do pliku wartości rozdzielanej przecinkami (CSV) na komputerze lokalnym. Możesz otworzyć ten plik w Microsoft Excel i użyć funkcji, takich jak wyszukiwanie, sortowanie, filtrowanie i dzielenie pojedynczej kolumny (zawierającej komórki wielowartościowe) na wiele kolumn.

1. Uruchom wyszukiwanie w dzienniku inspekcji, a następnie popraw kryteria wyszukiwania do momentu uzyskania żądanych wyników.
  
2. Kliknij pozycję Eksportuj wyniki i wybierz jedną z następujących opcji:

    - **Zapisz załadowane wyniki:** Wybierz tę opcję, aby wyeksportować tylko wpisy wyświetlane w obszarze **Wyniki** na stronie **wyszukiwania dziennika inspekcji opiekuna** . Pobrany plik CSV zawiera te same kolumny (i dane) wyświetlane na stronie (Data, Użytkownik, Działanie, Element i Szczegóły). W pliku CSV znajduje się dodatkowa kolumna (zatytułowana **Więcej**), która zawiera więcej informacji z wpisu dziennika inspekcji. Ponieważ eksportujesz te same wyniki, które są ładowane (i widoczne) na stronie wyszukiwania dziennika inspekcji, eksportowane jest maksymalnie 5000 wpisów.
        
    - **Pobierz wszystkie wyniki:** Wybierz tę opcję, aby wyeksportować wszystkie wpisy z dziennika inspekcji, które spełniają kryteria wyszukiwania. W przypadku dużego zestawu wyników wyszukiwania wybierz tę opcję, aby pobrać wszystkie wpisy z dziennika inspekcji oprócz 5000 wyników, które mogą być wyświetlane na stronie wyszukiwania **dziennika inspekcji opiekuna** . Ta opcja spowoduje pobranie nieprzetworzonych danych z dziennika inspekcji do pliku CSV i zawiera dodatkowe informacje z wpisu dziennika inspekcji w kolumnie o nazwie AuditData. Pobranie pliku może potrwać dłużej, jeśli wybierzesz tę opcję eksportu, ponieważ plik może być znacznie większy niż pobrany, jeśli wybierzesz inną opcję.
    
      > [!IMPORTANT]
      > Możesz pobrać maksymalnie 50 000 wpisów do pliku CSV z pojedynczego przeszukiwania dziennika inspekcji. Jeśli do pliku CSV zostanie pobranych 50 000 wpisów, można założyć, że istnieje ponad 50 000 zdarzeń spełniających kryteria wyszukiwania. Aby wyeksportować więcej niż ten limit, spróbuj użyć zakresu dat, aby zmniejszyć liczbę wpisów dziennika inspekcji. Może być konieczne uruchomienie wielu wyszukiwań z mniejszymi zakresami dat, aby wyeksportować ponad 50 000 wpisów.
        

3. Po wybraniu opcji eksportu w dolnej części okna zostanie wyświetlony komunikat z monitem o otwarcie pliku CSV, zapisanie go w folderze Pobrane lub zapisanie go w określonym folderze

Aby uzyskać więcej informacji na temat wyświetlania, filtrowania lub eksportowania wyników wyszukiwania dziennika inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).
