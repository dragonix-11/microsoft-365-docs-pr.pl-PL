---
title: Zarządzanie elementami dojścia w Advanced eDiscovery przypadku
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
description: Dowiedz się, jak wyświetlać szczegóły, edytować i edytować zbiorczo listę elementów przechoczynych w Advanced eDiscovery przypadku.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 794677c8675f044bafb1c9a441e6c2bbee3e1c86
ms.sourcegitcommit: b19e54b3888a0b07d08dbd23172daec303c7c95b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2021
ms.locfileid: "63007873"
---
# <a name="manage-custodians-in-an-advanced-ediscovery-case"></a>Zarządzanie elementami dojścia w Advanced eDiscovery przypadku

Strona **Pojedyńcze** na karcie Źródła danych w Advanced eDiscovery sprawy zawiera listę wszystkich elementów przechowywczych, które zostały dodane do sprawy. Po dodaniu osób do sprawy szczegóły dotyczące każdego opiekuna są automatycznie zbierane z Azure Active Directory i można je wyświetlać w Advanced eDiscovery.

## <a name="view-custodian-details"></a>Wyświetlanie szczegółów dotyczących tylko tych, których nie ma

Aby wyświetlić szczegółowe informacje o pochłonieniu, kliknij ten kartę z listy **na karcie Pochłoniaki** . Zostanie wyświetlona strona wysuuwana z następującymi informacjami na temat strony-tym, który się w niej znajduje.

![Szczegóły dotyczące pochłoń.](../media/CustodianDetails.PNG)

- Informacje kontaktowe

  - **Tytuł**. Stanowisko wytłaczeniowego.
  
  - **Główna nazwa użytkownika**. Główna nazwa użytkownika(GŁÓWNA nazwa użytkownika) dla użytkownika-opiekuna, na przykład AdeleV@contoso.onmicrosoft.com.
  
  - **Lokalizacja**. Lokalizacja biura w miejscu, w którym się znajduje firma.
  
  - **Kierownik**. Menedżer wołodniaka. Wyznaczony kierownik otrzyma wszelkie informacje o eskalacji dla tego opiekuna.
  
  - **Dział**. Nazwa działu, w którym działa ten opiekun.

- Informacje o sprawy

  - **Stan**. Stan opiekuna w ramach sprawy. Stan Aktywny **wskazuje** , że element przechowywczy należy do sprawy. Jeśli w związku ze sprawą zostanie wydany opiekun, stan tej sprawy zmieni się na **Released (Zwolniono**).
  
  - **Wstrzymaj**. Wskazuje, czy wstrzymano pochyloną osoby.

- Lokalizacje danych i informacje o przechowywaniach

  ![Informacje o lokalizacjach danych w jęz. wiad.](../media/CustodianHoldDetails.PNG)

  - **Lokalizacje wytyczane przez użytkownika**. Pokazuje liczbę i typ źródeł danych (skrzynek pocztowych, witryn i witryn Teams), które są skojarzone z opiekunem i są częścią sprawy.

    - W każdej lokalizacji danych jest pokazany stan jej przechowywania. Możliwe wartości stanu zawieszonego: **Wstrzymaj, Nie wstrzymaj** i **W toku**.

    - Jeśli nie widzisz stanu przechowywania źródła danych, sprawdź stan przechowywania, który jest wymieniony na karcie Wstrzymaj w przypadku tej sprawy. Wstrzymywanie w uchwycenie wskazuje konkretne źródła danych, które należy umieścić w tym  holdie.

## <a name="edit-a-custodian"></a>Edytowanie opiekuna

W trakcie realizacji sprawy może się okazać, że mogą się okazać dodatkowe źródła danych dotyczące określonego opiekuna i sprawy. W innych scenariuszach może być konieczne usunięcie niektórych źródeł danych, które zostały  reviewed i uznane za nie istotne.

Aby zaktualizować źródła danych skojarzone z opiekunem:

1. Przejdź do **okna zbierania elektronicznych > Advanced eDiscovery** i otwórz sprawę.
  
2. Kliknij **kartę Źródła** danych.
  
3. Wybierz z listy wytyczaczanie, a następnie kliknij **pozycję Edytuj** na wysuwanych stronie.

    ![Edytowanie źródeł danych.](../media/EditCustodianDataSource.PNG)
  
4. Aby dodać lub usunąć podstawową skrzynkę pocztową i OneDrive dla osoby przechowawczej:

    - Rozwiń informacje o uchoczycie, aby wyświetlić podstawowe lokalizacje danych, które zostały wcześniej skojarzone z skojarzoną z nim lokalizacją.

    - Kliknij **pozycję Edytuj** **obok pozycji** Skrzynka **pocztowa OneDrive** aby dodać skrzynkę pocztową osoby OneDrive skrzynkę pocztową.

    - Wybierz **pozycję** Wyczyść obok  pozycji Skrzynka pocztowa **lub OneDrive**, aby usunąć skrzynkę pocztową osoby OneDrive lub konto sieci OneDrive z skojarzoną lokalizacją danych dla tego adresata.

5. Aby dodać lub usunąć inne skrzynki pocztowe, witryny, Teams lub grupy Yammer do określonego adresata, kliknij pozycję Edytuj obok usługi, aby  dodać lokalizację danych.

   - **Exchange**: Użyj, aby skojarzyć inne skrzynki pocztowe z opiekunem. Wpisz w polu wyszukiwania nazwę lub alias (co najmniej trzy znaki) skrzynek pocztowych użytkowników lub grup dystrybucyjnych. Zaznacz skrzynki pocztowe, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**.

   - **SharePoint**: Użyj, aby skojarzyć SharePoint witryn internetowych z opiekunem. Wybierz witrynę na liście lub wyszukaj witrynę, wpisując adres URL w polu wyszukiwania. Wybierz witryny, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**.

   - **Teams**: Użyj, aby przypisać Microsoft Teams, do których jest obecnie członkiem. Wybierz zespoły do przypisania do opiekuna, a następnie kliknij przycisk **Dodaj**. Po dodaniu zespołu system automatycznie identyfikuje i odszuka witrynę grupy SharePoint skojarzoną z tym zespołem skrzynkę pocztową, a następnie przypisze go do osoby, która przejmuje zadania.

   - **Yammer**: Użyj, aby przypisać grupy Yammer, których jest obecnie członkiem. Wybierz grupy, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**. Po dodaniu zespołu system automatycznie identyfikuje i odszuka witrynę grupy SharePoint skojarzoną z tą grupą skrzynkę pocztową, a następnie przypisuje ją do użytkownika- opiekuna.

   > [!NOTE]
   > Za pomocą s **pickerów** lokalizacji Exchange i **SharePoint** można skojarzyć dowolną skrzynkę pocztową lub witrynę w organizacji, w tym zespoły lub grupy Yammer, których członkiem nie jest opiekun. W tym celu musisz dodać zarówno skrzynkę pocztową, jak i witrynę skojarzoną z każdym zespołem lub Yammer grupy.

6. Po edytowaniu lokalizacji danych dla użytkownika przechwytowego **kliknij przycisk Dalej** , aby przejść do strony **Ustawień wstrzymywania** .  

7. Na stronie **Hold settings (** Ustawienia wstrzymywania) zaktualizuj ustawienia dotyczące przechowywania.

## <a name="reindex-custodian-data"></a>Ponowne indeksowanie danych indeksowych

W większości przepływów pracy zbierania elektronicznych materiałów dowodowych do dochodzenia prawnego przeszukiwany jest podzbiór danych użytkownika, który został dodany do postępowania sądowego. Ze względu na bardzo duże rozmiary plików lub ewentualne uszkodzenie danych niektóre elementy w źródłach danych skojarzonych z elementem przetwarzaczym mogą być częściowo indeksowane. W przypadku [używania](indexing-custodian-data.md) zaawansowanej funkcji indeksowania w p Advanced eDiscovery większość częściowo indeksowanych elementów można automatycznie naprawiać przez ponowne indeksowanie tych elementów na żądanie.

Po dodaniu do sprawy informacje znajdujące się w źródłach danych skojarzonych z tym obiektem jest automatycznie ponownie zindeksowany (przez zaawansowany proces indeksowania). Oznacza to, że możesz pozostawić te dane w miejscu, zamiast pobierać je i rekultywować, a następnie wyszukiwać w trybie offline). Jednak podczas cyklu życia sprawy prawnej nowe źródła danych mogą być skojarzone z opiekunem. W takim przypadku można ponownie zindeksować dane użytkownika- opiekuna, ponownie uruchomić zaawansowany proces indeksowania, aby rozwiązać wszystkie częściowo indeksowane elementy i zaktualizować indeks danych tego użytkownika.

Aby wyzwolić proces ponownego indeksowania w celu adresowania elementów częściowo indeksowanych:

1. Przejdź do **okna zbierania elektronicznych > Advanced eDiscovery** i otwórz sprawę.

2. Kliknij **kartę Źródła** .

3. Na stronie **Pojedyrzeni** wybierz opiekuna, którego dane muszą zostać ponownie zindeksowane.

4. Na stronie wysuwu kliknij pozycję **Aktualizuj indeks**.

   Zostanie wyświetlone okno dialogowe z informacją, że zadanie indeksu zostało utworzone.

Ponowne indeksowanie danych indeksjańskich jest długim procesem. odpowiadające im zadanie, które zostanie utworzone, nosi nazwę **Ponowne indeksowanie danych przechowywania**. Postęp zadań można śledzić **na karcie Zadania** lub na karcie Osoby-wartości, monitorując stan w kolumnie  Stan zadania **indeksowania**.

Więcej informacji można znaleźć w następujących artykułach:

- [Praca z błędami przetwarzania](processing-data-for-case.md)

- [Zarządzanie zadaniami](managing-jobs-ediscovery20.md)

## <a name="release-a-custodian-from-a-case"></a>Zwolnij pojedyńcę z sprawy

Opiekun jest zwalniany w sytuacjach, w których sprawa została zamknięta, opiekun nie jest już zobowiązany do zachowania treści danej sprawy lub gdy uważa się, że ten opiekun nie jest już istotny w danej sprawie. 

W przypadku zwolnienia po opublikowaniu powiadomienia o wstrzymaniu zostanie do tego osoby wysłane powiadomienie o wydaniu. Ponadto usuwane są wszelkie blokady umieszczone na źródłach danych, które były skojarzone z tym elementem. Jeśli w przypadku umieszczenia w trybie dyskretnego wstrzymywania dla *użytkownika, który* nie przesłał żadnych powiadomień prawnych, powiadomienie o wydaniu nie zostanie wysłane, ale wszelkie blokady umieszczone na źródłach danych powiązanych z tym powiązanym z tym opiekunem zostaną usunięte.

Aby zwolnić pojedyńcę:

1. Przejdź do **okna zbierania elektronicznych > Advanced eDiscovery** i otwórz sprawę.

2. Kliknij **kartę Źródła** .

3. Na stronie **Pojedyńcze** wybierz zatem opiekuna, który jest zwalniany ze sprawy.

4. Na stronie wysuwu kliknij pozycję **Zwolnij kartę projektową**.

   Zostanie wyświetlona strona ostrzegawczy z wyjaśnieniem, że jeśli do źródła danych skojarzonego ze źródłem danych skojarzonym z tym źródłem danych zostanie usunięte ostrzeżenie, a wszelkie inne warunki przechowywania skojarzone z innym Advanced eDiscovery będą nadal stosowane. Obejmuje to inne typy funkcji zachowywania i przechowywania (takie jak zasady Microsoft 365 przechowywania).

5. Kliknij **przycisk Tak** , aby potwierdzić, że chcesz zwolnić kartę dojścia. 

    Dla tego użytkownika na karcie Pochłonia jest ustawiona **wartość Zwolnij**, a **stan** Wstrzymaj na stronie wysuwanego zmienia się na **Fałsz**.

> [!NOTE]
> W kilku przypadkach osoby, które się w tym samym czasie uczestniczyły, mogą uczestniczyć w wielu postępowaniach prawnych. Jeśli w określonej sprawie zostanie wydany opiekun, nie wpłynie to na blokady i powiadomienia z innych spraw.
