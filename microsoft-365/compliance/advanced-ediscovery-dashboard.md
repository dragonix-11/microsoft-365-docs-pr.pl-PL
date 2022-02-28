---
title: Advanced eDiscovery pulpitu nawigacyjnego dla zestawów recenzji
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
description: Za pomocą Advanced eDiscovery pulpitu nawigacyjnego można szybko analizować zestawy recenzji, aby zidentyfikować trendy lub kluczowe statystyki, które pomogą w opracowywania strategii rerecenzentów.
ms.openlocfilehash: b7bc487e95c2dbae1a65aaad94face6bee19d39b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984613"
---
# <a name="advanced-ediscovery-dashboard-for-review-sets"></a>Advanced eDiscovery pulpitu nawigacyjnego dla zestawów recenzji

W niektórych przypadkach w Advanced eDiscovery może być duża liczba dokumentów i wiadomości e-mail do przejrzenia. Przed rozpoczęciem procesu przeglądu można szybko przeanalizować swoje dane w celu zidentyfikowania trendów lub kluczowych statystyk, które pomogą w opracowywania strategii przeglądu. W tym celu można szybko analizować swój zestaw Advanced eDiscovery pulpitu nawigacyjnego.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>Krok 1. Tworzenie widżetu na pulpicie nawigacyjnym zestawu recenzji

1. W Centrum zgodności platformy Microsoft 365 przejdź do tematu Zbierania elektronicznych materiałów dowodowych **> Advanced eDiscovery** aby wyświetlić listę spraw w organizacji.
  
2. Zaznacz istniejącą sprawę.
  
3. Kliknij **kartę Zestaw recenzji** , a następnie wybierz zestaw recenzji.
  
4. Na liście **rozwijanej Poszczególne** wyniki kliknij pozycję **Wyszukaj w widoku profilu**. 

   ![KreskbordPivot.](../media/dashboardpivot.png)

   Zostanie **wyświetlona strona Wyszukaj w** widoku profilu. Podczas wyświetlania tej strony po raz pierwszy wyświetlane są trzy domyślne widżety.

   ![Pulpit nawigacyjny.](../media/dashboardonly.png)
  
5. Kliknij widżet **Nowy** , a następnie wybierz jeden z następujących elementów:

   ![Nowa lista rozwijana widżetów.](../media/NewWidgetDropdownBox.png)

   - **Wybierz z biblioteki:** Wyświetla domyślną bibliotekę widżetów. Kliknij widżet, a następnie kliknij pozycję **Dodaj** , aby dodać go do widżetów na stronie **Przeszukaj widok profilu** .
  
   - **Tworzenie niestandardowego widżetu:** Wyświetla wysuwną stronę, za pomocą których można skonfigurować niestandardowy widżet. 

6. Aby utworzyć niestandardowy widżet, na stronie wysuwu dodaj **widżet** wykonaj następujące czynności:

   ![Utwórz widżet.](../media/addwidget.png)

    a. Wpisz nazwę widżetu, który będzie wyświetlany na pasku tytułu widżetu. Nazwa widżetu jest wymagana, ale warto zidentyfikować dane widżetu.

    b. Z listy rozwijanej **Wybierz tabelę** przestawną wybierz właściwość, która będzie używana dla danych widżetów. Elementy na tej liście są właściwościami, które można przeszukiwać dla elementów w zestawie recenzji. Aby uzyskać opis tych właściwości, zobacz [Pola metadanych dokumentu Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md). Opcje przestawne widżetu są wymienione w kolumnie Nazwa pola z **możliwością wyszukiwania** w tym temacie.

    c. Wybierz typ wykresu, aby wyświetlić dane z wybranej właściwości przestawnej.

  6. Kliknij **pozycję Dodaj** , aby utworzyć niestandardowy widżet i wyświetlić go na **stronie Przeszukaj widok profilu** .

## <a name="step-2-create-a-review-set-search-query"></a>Krok 2. Tworzenie kwerendy wyszukiwania zestawu recenzji

1. Kliknij **pozycję ...** na pasku tytułu widżetu, a następnie kliknij pozycję **Zastosuj warunek**.

   ![Pulpit nawigacyjny.](../media/searchprofilehome.png)

2. Na stronie wysuwu kliknij element na klawiszu widżetu lub wykresie widżetu, aby utworzyć filtr.

   ![CreateFilter.](../media/applyconditionfilter.png)

3. Powtórz kroki 1–2 dla innych widżetów. 

4. Gdy to zrobisz, kliknij pozycję **Zapisz jako zapytanie** , aby zapisać warunki jako nowe zapytanie wyszukiwania dla zestawu recenzji.

   ![Zapytanie.](../media/savequery.png)

5. Zamknij widok **profilu wyszukiwania,** aby powrócić do widoku wyników wyszukiwania.

   Jeśli utworzono jakiekolwiek filtry wizualne, wynikowe zapytanie zostanie zastosowane do wyświetlanych wyników wyszukiwania, a zapytanie wyszukiwania zapisane w kroku 4 zostanie wyświetlone w obszarze Zapisane **zapytania**. Aby uzyskać więcej informacji na temat zapytań zestawu recenzji, zobacz [Kwerenda danych w zestawie recenzji](review-set-search.md).
