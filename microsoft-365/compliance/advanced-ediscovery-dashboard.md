---
title: Pulpit nawigacyjny zbierania elektronicznych materiałów dowodowych (Premium) na potrzeby zestawów przeglądów
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Pulpit nawigacyjny zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium) umożliwia zestawy przeglądów, aby szybko przeanalizować swoje ciało w celu zidentyfikowania trendów lub kluczowych statystyk, które pomogą Ci opracować strategię przeglądu.
ms.openlocfilehash: 00d4c6648d74fdf459965ed410dd43c73e698c23
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097871"
---
# <a name="ediscovery-premium-dashboard-for-review-sets"></a>Pulpit nawigacyjny zbierania elektronicznych materiałów dowodowych (Premium) na potrzeby zestawów przeglądów

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W niektórych przypadkach w usłudze Microsoft Purview eDiscovery (Premium) może istnieć duża liczba dokumentów i wiadomości e-mail, które należy przejrzeć. Przed rozpoczęciem procesu przeglądu możesz szybko przeanalizować swoje ciało, aby zidentyfikować trendy lub kluczowe statystyki, które pomogą Ci opracować strategię przeglądu. W tym celu możesz użyć pulpitu nawigacyjnego zbierania elektronicznych elektronicznych materiałów dowodowych (Premium) na potrzeby zestawów przeglądów, aby szybko przeanalizować swoje ciało.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>Krok 1. Tworzenie widżetu na pulpicie nawigacyjnym zestawu przeglądów

1. W portalu zgodności usługi Microsoft Purview przejdź do obszaru **eDiscovery > eDiscovery (Premium),** aby wyświetlić listę przypadków w organizacji.
  
2. Wybierz istniejący przypadek.
  
3. Kliknij kartę **Przejrzyj zestaw** , a następnie wybierz zestaw przeglądów.
  
4. Na liście rozwijanej **Indywidualne wyniki** kliknij pozycję **Widok profilu wyszukiwania**. 

   ![DashbordPivot.](../media/dashboardpivot.png)

   Zostanie wyświetlona strona **Widok profilu wyszukiwania** . podczas pierwszego wyświetlania tej strony zostaną wyświetlone trzy domyślne widżety.

   ![Pulpitu nawigacyjnego.](../media/dashboardonly.png)
  
5. Kliknij **widżet Nowy,** a następnie wybierz jeden z następujących elementów:

   ![Lista rozwijana nowego widżetu.](../media/NewWidgetDropdownBox.png)

   - **Wybierz z biblioteki:** Wyświetla domyślną bibliotekę widżetów. Kliknij widżet, a następnie kliknij przycisk **Dodaj** , aby dodać go do widżetów na stronie **Widok profilu wyszukiwania** .
  
   - **Utwórz niestandardowy widżet:** Wyświetla stronę wysuwaną, za pomocą którego można skonfigurować niestandardowy widżet. 

6. Aby utworzyć niestandardowy widżet, wykonaj następujące czynności na stronie wysuwanej **dodawanie widżetu** :

   ![Utwórz widżet.](../media/addwidget.png)

    a. Wpisz nazwę widżetu, która jest wyświetlana na pasku tytułu widżetu. Nazwa widżetu jest wymagana, ale warto zidentyfikować dane widżetu.

    b. Wybierz właściwość z listy rozwijanej **Wybieranie tabeli przestawnej** , która będzie używana dla danych widżetu. Elementy na tej liście są właściwościami, które można przeszukiwać dla elementów w zestawie przeglądów. Opis tych właściwości można znaleźć [w temacie Document metadata fields in eDiscovery (Premium) (Pola metadanych dokumentu w Premium).](document-metadata-fields-in-Advanced-eDiscovery.md) Opcje tabeli przestawnej dla widżetu są wyświetlane w kolumnie **Nazwa pola z możliwością wyszukiwania** w tym temacie.

    c. Wybierz typ wykresu, aby wyświetlić dane z wybranej właściwości tabeli przestawnej.

  6. Kliknij **przycisk Dodaj** , aby utworzyć niestandardowy widżet i wyświetlić go na stronie **Widok profilu wyszukiwania** .

## <a name="step-2-create-a-review-set-search-query"></a>Krok 2. Tworzenie zapytania wyszukiwania zestawu przeglądów

1. Kliknij **przycisk ...** na pasku tytułu widżetu, a następnie kliknij przycisk **Zastosuj warunek**.

   ![Pulpitu nawigacyjnego.](../media/searchprofilehome.png)

2. Na stronie wysuwanej kliknij element na kluczu widżetu lub wykresie widżetu, aby utworzyć filtr.

   ![CreateFilter.](../media/applyconditionfilter.png)

3. Powtórz kroki 1–2 dla innych widżetów z wieloma widżetami. 

4. Po zakończeniu kliknij pozycję **Zapisz jako zapytanie** , aby zapisać warunki jako nowe zapytanie wyszukiwania dla zestawu przeglądów.

   ![Kwerendy.](../media/savequery.png)

5. Zamknij **widok Profilu wyszukiwania** , aby powrócić do widoku wyników wyszukiwania.

   Jeśli utworzono jakiekolwiek filtry wizualne, wynikowe zapytanie zostanie zastosowane do wyświetlanych wyników wyszukiwania, a zapytanie wyszukiwania zapisane w kroku 4 zostanie **wyświetlone w obszarze Zapisane zapytania**. Aby uzyskać więcej informacji na temat zapytań zestawu przeglądów, zobacz [Wykonywanie zapytań dotyczących danych w zestawie przeglądów](review-set-search.md).
