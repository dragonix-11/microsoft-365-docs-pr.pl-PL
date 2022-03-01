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
description: Użyj narzędzia Advanced eDiscovery do zarządzania pobłędniami, aby łatwo uzyskać dostęp do aktywności i wyszukać je w ramach sprawy.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: d0ea6e94bd48c055cac23d8a96477e036369dd5c
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017786"
---
# <a name="view-custodian-audit-activity"></a>Wyświetlaj aktywność inspekcji opiekuna

Chcesz sprawdzić, czy użytkownik przeglądał określony dokument lub czyszczył określony element ze skrzynki pocztowej? Advanced eDiscovery jest teraz zintegrowana z istniejącym narzędziem do przeszukiwania dziennika inspekcji w Centrum zgodności platformy Microsoft 365. Za pomocą tego osadzonego środowisko można użyć narzędzia do zarządzania Advanced eDiscovery w celu ułatwienia badania przez łatwe uzyskiwanie dostępu do aktywności osób zarządzających sprawą i wyszukiwanie w nich osób, które się w tym przypadku znajduje.

## <a name="get-permissions"></a>Uzyskiwanie uprawnień

Do przeszukiwania dziennika inspekcji View-Only musi być przypisana rola Dzienniki inspekcji Exchange Online Dzienniki inspekcji. Domyślnie te role są przypisane do grup ról Zarządzanie zgodnością i Zarządzanie organizacją na stronie Uprawnienia Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">administracyjnego</a>. Aby dać użytkownikowi możliwość przeszukiwania dziennika inspekcji usługi Advanced eDiscovery z minimalnym poziomem uprawnień, możesz utworzyć niestandardową grupę ról w programie Exchange Online, dodać rolę Dzienniki inspekcji lub Dzienniki inspekcji usługi View-Only, a następnie dodać użytkownika jako członka nowej grupy ról. Aby uzyskać więcej informacji, zobacz Zarządzanie grupami ról w Exchange Online.

> [!IMPORTANT]
> Jeśli przypiszesz użytkownikowi rolę dzienniki inspekcji View-Only lub Dzienniki inspekcji na stronie Uprawnienia w Centrum zgodności platformy Microsoft 365, ten użytkownik nie będzie mógł przeszukiwać dziennika inspekcji. Musisz przypisać uprawnienia w programie Exchange Online. Jest to spowodowane tym, że polecenie cmdlet służące do przeszukiwania dziennika inspekcji jest poleceniem cmdlet Exchange Online cmdlet.

## <a name="step-1-search-the-audit-log-for-activities-performed-by-a-custodian"></a>Krok 1. Wyszukiwanie w dzienniku inspekcji działań wykonywanych przez opiekuna

1. Przejdź do **okna zbierania elektronicznych > Advanced eDiscovery** i otwórz sprawę.
  
2. Kliknij **kartę Źródła** .
  
3. Na stronie **Pojedyrze** wybierz z listy opiekuna, a następnie kliknij pozycję **Wyświetl** aktywność karteczek w wysuwanych wiadomościach.

    Zostanie wyświetlona strona wyszukiwania Działania w szybkich działaniach. Zwróć uwagę, że w polu listy rozwijanej Wiad. W polu listy rozwijanej można wybrać różne typy treści, ale w każdej chwili można wyszukiwać tylko działania tylko dla jednego opiekuna.

    ![Strona wyszukiwania działań chłonnych.](../media/AeDCustodianActivities1.png)
   
4. Skonfiguruj następujące kryteria wyszukiwania:
      
   1. **Działania** — kliknij listę rozwijaną, aby wyświetlić działania, które można wyszukać. Po uruchomieniu wyszukiwania są wyświetlane tylko rekordy inspekcji dotyczące wybranych działań. Zaznaczenie **opcji Pokaż wyniki dla wszystkich działań** spowoduje wyświetlenie wyników dotyczących wszystkich działań wykonywanych przez opiekuna, które spełniają inne kryteria wyszukiwania.

      ![Lista działań.](../media/CustodianActivityAudit.PNG)
      
   1. **Data rozpoczęcia i Data zakończenia** — wybierz zakres dat i godzin, aby wyświetlić zdarzenia, które wystąpiły w tym okresie. Domyślnie jest zaznaczonych ostatnich siedem dni. Data i godzina są przedstawiane w formacie uniwersalnego czasu koordynowaowego (UTC). Maksymalny zakres dat, który można określić, to jeden rok.
      
   1. **Fortysy** — kliknij w tym polu, a następnie wybierz konkretny, który ma być wyświetlany w wynikach wyszukiwania. Na liście wyników zostaną wyświetlone rekordy inspekcji wybranych działań wykonanych przez użytkowników wybranych w tym polu.
      
5. Kliknij pozycję ![Przycisk Wyszukaj.](../media/SearchButton.PNG)  , aby uruchomić wyszukiwanie przy użyciu kryteriów wyszukiwania. Wyniki wyszukiwania zostaną załadowane i po chwili wyświetlone w obszarze Wyniki na stronie wyszukiwania Działania użytkownika. 

## <a name="step-2-view-the-audit-log-search-results"></a>Krok 2. Wyświetlanie wyników przeszukiwania dziennika inspekcji

Wyniki przeszukiwania dziennika inspekcji są wyświetlane w obszarze Wyniki na stronie Dziennik inspekcji w sz. Maksymalnie jest wyświetlanych 5000 (najnowszych) zdarzeń w przyrostach co 150 zdarzeń. Aby wyświetlić więcej zdarzeń, możesz użyć paska przewijania w okienku Wyniki lub nacisnąć klawisze Shift + End, aby wyświetlić 150 kolejnych zdarzeń.

Wyniki zawierają następujące informacje na temat poszczególnych zdarzeń zwróconych przez wyszukiwanie.
- **Data**: data i godzina wystąpienia zdarzenia (w formacie UTC).

- **Adres IP**: adres IP urządzenia używanego w czasie rejestrowanego działania. Adres IP jest wyświetlany w formacie adresu IPv4 lub IPv6.

- **Użytkownik**: Użytkownik (lub konto usługi), który wykonał akcję, która wyzwoliła zdarzenie.

- **Działanie**: Działanie wykonane przez użytkownika. Ta wartość odpowiada czynnościom zaznaczonym na liście rozwijanej Działania. W przypadku zdarzenia z dziennika inspekcji Exchange wartość w tej kolumnie jest poleceniem cmdlet Exchange cmdlet.

- **Element**: obiekt utworzony lub zmodyfikowany w wyniku odpowiedniego działania. Może to być na przykład plik, który został przeglądany lub zmodyfikowany, albo zaktualizowane konto użytkownika. Nie wszystkie działania mają wartość w tej kolumnie.

- **Szczegóły**: Dodatkowe szczegóły dotyczące działania. Również nie wszystkie działania będą mieć wartość.

## <a name="step-3-filter-the-search-results"></a>Krok 3. Filtrowanie wyników wyszukiwania

Można nie tylko sortować, ale również filtrować wyniki przeszukiwania dziennika inspekcji. Może to ułatwić szybkie filtrowanie wyników dla określonego użytkownika lub działania. 

Aby filtrować wyniki:

 1. Tworzenie i uruchamianie wyszukiwania w dzienniku inspekcji.
  
2. Po wyświetlaniu wyników kliknij pozycję **Filtruj wyniki**.
 
3. Poniżej nagłówków kolumn zostaną wyświetlone pola słów kluczowych.
  
4. Kliknij jedno z pól poniżej nagłówka kolumny i wpisz słowo lub frazę, w zależności od kolumny, według których chcesz filtrować. Wyniki zostaną dynamicznie dopasowane, aby wyświetlić zdarzenia zgodne z filtrem.
  
5. Aby wyczyścić filtr, kliknij **znak X** w polu filtru lub po prostu kliknij pozycję **Ukryj filtrowanie**.

## <a name="export-the-search-results-to-a-file"></a>Eksportowanie wyników wyszukiwania do pliku

Wyniki przeszukiwania dziennika inspekcji można wyeksportować do pliku w formacie wartości rozdzielonych przecinkami (CSV) na komputerze lokalnym. Możesz otworzyć ten plik w programie Microsoft Excel i użyć funkcji, takich jak wyszukiwanie, sortowanie, filtrowanie i dzielenie jednej kolumny (zawierającej komórki wielowymiarowe) na wiele kolumn.

1. Uruchom przeszukiwanie dziennika inspekcji, a następnie poprawiaj kryteria wyszukiwania, aż zostaną uzyskane odpowiednie wyniki.
  
2. Kliknij pozycję Eksportuj wyniki i wybierz jedną z następujących opcji:

    - **Zapisz załadowane wyniki:** Wybierz tę opcję, aby wyeksportować tylko wpisy wyświetlane **w obszarze Wyniki** na **stronie Przeszukiwanie dziennika** inspekcji. Pobrany plik CSV zawiera te same kolumny (i dane), które są wyświetlane na stronie (Data, Użytkownik, Działanie, Element i Szczegóły). W pliku CSV **zostanie dołączona** dodatkowa kolumna (o tytule Więcej), zawierająca więcej informacji z wpisu dziennika inspekcji. Ponieważ eksportujesz te same wyniki, które zostały załadowane (i można wyświetlić) na stronie Przeszukiwanie dziennika inspekcji, eksportowanych jest maksymalnie 5000 wpisów.
        
    - **Pobierz wszystkie wyniki:** Wybierz tę opcję, aby wyeksportować wszystkie wpisy z dziennika inspekcji, które spełniają kryteria wyszukiwania. W przypadku dużego zestawu wyników wyszukiwania wybierz tę opcję, aby pobrać wszystkie wpisy z dziennika inspekcji, a nie tylko 5000 wyników, które mogą być wyświetlane na stronie Przeszukiwanie dziennika  inspekcji w związku z inspekcją. Ta opcja spowoduje pobranie do pliku CSV nieprzetworzonych danych z dziennika inspekcji oraz dodatkowe informacje z wpisu dziennika inspekcji w kolumnie o nazwie Dane inspekcji. W przypadku wybrania tej opcji eksportowania pobieranie pliku może potrwać dłużej, ponieważ plik może być znacznie większy niż plik pobierany w przypadku wybrania drugiej opcji.
    
      > [!IMPORTANT]
      > Z jednego przeszukiwania dziennika inspekcji do pliku CSV można pobrać maksymalnie 50 000 wpisów. Jeśli do pliku CSV zostanie pobranych 50 000 wpisów, można z pewnością założyć, że istnieje ponad 50 000 zdarzeń, które spełniają kryteria wyszukiwania. Aby wyeksportować dane powyżej tego limitu, spróbuj użyć zakresu dat w celu zmniejszenia liczby wpisów dziennika inspekcji. W celu wyeksportowania ponad 50 000 wpisów może być konieczne uruchomienie wielu wyszukiwań z mniejszymi zakresami dat.
        

3. Po wybraniu opcji eksportu u dołu okna zostanie wyświetlony komunikat z monitem o otwarcie pliku CSV, zapisanie go w folderze Pobrane lub zapisanie go w określonym folderze.

Aby uzyskać więcej informacji na temat wyświetlania, filtrowania i eksportowania wyników przeszukiwania dziennika inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).
