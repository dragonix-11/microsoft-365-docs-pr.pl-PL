---
title: Zarządzanie opiekunami w sprawie zbierania elektronicznych materiałów dowodowych (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Dowiedz się, jak wyświetlać szczegóły, edytować i zbiorczo edytować listę opiekunów w przypadku zbierania elektronicznych materiałów dowodowych (Premium).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: baffcb9d601d95d4be78cf47fcbc3037daff86c8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634033"
---
# <a name="manage-custodians-in-an-ediscovery-premium-case"></a>Zarządzanie opiekunami w sprawie zbierania elektronicznych materiałów dowodowych (Premium)

Strona **Opiekunowie** na karcie **Źródła danych** w sprawie Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) zawiera listę wszystkich opiekunów, którzy zostali dodani do sprawy. Po dodaniu opiekunów do sprawy szczegóły dotyczące każdego opiekuna są automatycznie zbierane z usługi Azure Active Directory i są widoczne w obszarze eDiscovery (Premium).

## <a name="view-custodian-details"></a>Wyświetlanie szczegółów opiekuna

Aby wyświetlić szczegóły dotyczące opiekuna, kliknij opiekuna z listy na karcie **Opiekunowie** . Zostanie wyświetlona strona wysuwana zawierająca następujące informacje o opiekunze.

![Szczegóły opiekuna.](../media/CustodianDetails.PNG)

- Informacje kontaktowe

  - **Tytuł**. Stanowisko opiekuna.
  
  - **Główna nazwa użytkownika**. Główna nazwa użytkownika (UPN) dla opiekuna, na przykład AdeleV@contoso.onmicrosoft.com.
  
  - **Lokalizacja**. Lokalizacja biura w miejscu prowadzenia działalności przez opiekuna.
  
  - **Menedżer**. Menedżer opiekuna. Wyznaczony menedżer otrzyma wszelkie komunikaty eskalacji dla tego opiekuna.
  
  - **Dział**. Nazwa działu, w którym pracuje opiekun.

- Informacje o przypadku

  - **Stan**. Status opiekuna w sprawie. Stan **Aktywny** wskazuje, że opiekun jest częścią sprawy. Jeśli opiekun zostanie zwolniony ze sprawy, stan zostanie zmieniony na **Zwolniony**.
  
  - **Przytrzymaj**. Wskazuje, czy opiekun został wstrzymany.

- Lokalizacje danych i informacje dotyczące przechowywania

  ![Lokalizacje danych opiekuna i przechowują informacje.](../media/CustodianHoldDetails.PNG)

  - **Miejsca opieki**. Pokazuje liczbę i typ źródeł danych (skrzynki pocztowe, witryny i aplikacje Teams), które są skojarzone z opiekunem i są częścią sprawy.

    - Każda lokalizacja danych pokazuje stan wstrzymania. Możliwe wartości stanu blokady: **Wstrzymane**, **Nie wstrzymane** i **W toku**.

    - Jeśli nie widzisz stanu wstrzymania dla źródła danych, sprawdź stan blokady opiekuna, która znajduje się na karcie **Blokada** dla danego przypadku. Blokada opiekuna identyfikuje określone źródła danych, które są wstrzymane.

## <a name="edit-a-custodian"></a>Edytowanie opiekuna

W miarę rozwoju twojej sprawy możesz odkryć, że mogą istnieć dodatkowe źródła danych istotne dla określonego opiekuna i sprawy. W innych scenariuszach można usunąć niektóre źródła danych, które zostały przejrzane i uznane za nieistotne.

Aby zaktualizować źródła danych skojarzone z opiekunem:

1. Przejdź do  **obszaru eDiscovery > eDiscovery (Premium)** i otwórz sprawę.
  
2. Kliknij kartę **Źródła danych** .
  
3. Wybierz opiekuna z listy, a następnie kliknij pozycję **Edytuj** na stronie wysuwanej.

    ![Edytuj źródła danych.](../media/EditCustodianDataSource.PNG)
  
4. Aby dodać lub usunąć podstawową skrzynkę pocztową i konto usługi OneDrive dla opiekuna:

    - Rozwiń opiekuna, aby wyświetlić podstawowe lokalizacje danych, które były wcześniej skojarzone z opiekunem.

    - Kliknij pozycję **Edytuj** obok **pozycji Skrzynka pocztowa** lub **OneDrive** , aby dodać skrzynkę pocztową opiekuna lub lokalizację usługi OneDrive.

    - Wybierz pozycję **Wyczyść** obok **pozycji Skrzynka pocztowa** lub **OneDrive** , aby usunąć skrzynkę pocztową opiekuna lub konto usługi OneDrive z skojarzenia jako lokalizacji danych dla tego opiekuna.

5. Aby dodać lub usunąć inne skrzynki pocztowe, witryny, zespoły lub grupy usługi Yammer do określonego opiekuna, kliknij pozycję **Edytuj** obok usługi, aby dodać lokalizację danych.

   - **Exchange**: Służy do kojarzenia innych skrzynek pocztowych z opiekunem. Wpisz w polu wyszukiwania nazwę lub alias (co najmniej trzy znaki) skrzynek pocztowych użytkownika lub grup dystrybucyjnych. Wybierz skrzynki pocztowe, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**.

   - **SharePoint**: służy do kojarzenia witryn programu SharePoint z opiekunem. Wybierz witrynę na liście lub wyszukaj witrynę, wpisując adres URL w polu wyszukiwania. Wybierz witryny, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**.

   - **Teams**: służy do przypisywania usługi Microsoft Teams, do którego obecnie należy opiekun. Wybierz zespoły, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**. Po dodaniu zespołu system automatycznie identyfikuje i lokalizuje skrzynkę pocztową witryny programu SharePoint i grupy skojarzone z tym zespołem i przypisuje je do opiekuna.

   - **Yammer**: użyj polecenia , aby przypisać grupy usługi Yammer, do których obecnie należy opiekun. Wybierz grupy, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**. Po dodaniu zespołu system automatycznie identyfikuje i lokalizuje skrzynkę pocztową witryny programu SharePoint i grupy skojarzone z tą grupą i przypisuje je do opiekuna.

   > [!NOTE]
   > Możesz użyć selektorów lokalizacji **programu Exchange** i **programu SharePoint** , aby skojarzyć dowolną skrzynkę pocztową lub witrynę w organizacji, w tym zespoły lub grupy usługi Yammer, których opiekun nie jest członkiem, z opiekunem. W tym celu należy dodać zarówno skrzynkę pocztową, jak i witrynę skojarzoną z każdym zespołem lub grupą usługi Yammer.

6. Po edytowaniu lokalizacji danych dla opiekuna kliknij przycisk **Dalej** , aby przejść do strony **Ustawienia blokady** .  

7. Na stronie **Ustawienia blokady** zaktualizuj ustawienia blokady dla opiekuna.

## <a name="reindex-custodian-data"></a>Dane reaseksuj opiekuna

W większości przepływów pracy zbierania elektronicznych materiałów dowodowych na potrzeby dochodzeń prawnych podzbiór danych opiekuna jest przeszukiwany po dodaniu opiekuna do sprawy prawnej. Z powodu bardzo dużych rozmiarów plików lub możliwego uszkodzenia danych niektóre elementy w źródłach danych skojarzonych z opiekunem mogą być częściowo indeksowane. Korzystając z [zaawansowanej możliwości indeksowania](indexing-custodian-data.md) w środowisku zbierania elektronicznych materiałów dowodowych (Premium), większość częściowo indeksowanych elementów można automatycznie korygować przez ponowne indeksowanie tych elementów na żądanie.

Po dodaniu opiekuna do sprawy dane znajdujące się w źródłach danych skojarzonych z opiekunem są automatycznie ponownie indeksowane (przez zaawansowany proces indeksowania). Oznacza to, że możesz pozostawić dane w miejscu zamiast pobierać i korygować je, a następnie przeszukiwać w trybie offline). Jednak w trakcie cyklu życia sprawy prawnej nowe źródła danych mogą być skojarzone z opiekunem. W takim przypadku możesz ponownie przeanalizować dane opiekuna, uruchamiając zaawansowany proces indeksowania, aby skorygować wszystkie częściowo indeksowane elementy i zaktualizować indeks danych opiekuna.

Aby wyzwolić proces ponownego indeksowania w celu rozwiązania częściowo zaindeksowanych elementów:

1. Przejdź do  **obszaru eDiscovery > eDiscovery (Premium)** i otwórz sprawę.

2. Kliknij kartę **Źródła** .

3. Na stronie **Opiekunowie** wybierz opiekuna, którego dane muszą zostać ponownieexed.

4. Na stronie wysuwanej kliknij pozycję **Zaktualizuj indeks**.

   Zostanie wyświetlone okno dialogowe z informacją o utworzeniu zadania indeksu.

Ponowne ekskształcenie danych opiekuna jest długotrwałym procesem; Utworzone zadanie nosi nazwę **Ponowne indeksowanie danych opiekuna**. Postęp można śledzić na karcie **Zadania** lub na karcie **Opiekunowie** , monitorując stan w kolumnie **Stan zadania indeksowania** .

Więcej informacji można znaleźć w następujących artykułach:

- [Praca z błędami przetwarzania](processing-data-for-case.md)

- [Zarządzaj zadaniami](managing-jobs-ediscovery20.md)

## <a name="release-a-custodian-from-a-case"></a>Zwalnianie opiekuna ze sprawy

Opiekun zostaje zwolniony w sytuacjach, gdy sprawa jest zamknięta, opiekun nie jest już zobowiązany do zachowania treści w danej sprawie lub gdy opiekun jest uważany za niemałego znaczenia dla sprawy. 

Jeśli zwolnisz opiekuna po opublikowaniu powiadomienia o wstrzymaniu, powiadomienie o zwolnieniu zostanie wysłane do opiekuna. Ponadto wszelkie blokady umieszczone w źródłach danych skojarzonych z opiekunem są usuwane. Jeśli opiekun został umieszczony w *dyskretnym blokadzie*, gdzie nie zostały wydane żadne powiadomienia o blokadzie prawnej, powiadomienie o zwolnieniu nie zostanie wysłane, ale wszelkie blokady umieszczone w źródłach danych, które były związane z tym opiekunem, zostaną usunięte.

Aby zwolnić opiekuna:

1. Przejdź do  **obszaru eDiscovery > eDiscovery (Premium)** i otwórz sprawę.

2. Kliknij kartę **Źródła** .

3. Na stronie **Opiekunowie** wybierz opiekuna, który jest zwalniany ze sprawy.

4. Na wysuwanej stronie kliknij pozycję **Zwolnij opiekuna**.

   Zostanie wyświetlona strona ostrzegawcza wyjaśniająca, że jeśli blokada zostanie umieszczona w źródle danych skojarzonym z opiekunem, blokada zostanie usunięta, a wszelkie inne blokady skojarzone z innym przypadkiem zbierania elektronicznych materiałów dowodowych (Premium) nadal będą miały zastosowanie. Obejmuje to inne typy funkcji zachowania i przechowywania (na przykład zasady przechowywania platformy Microsoft 365).

5. Kliknij przycisk **Tak** , aby potwierdzić, że chcesz zwolnić opiekuna. 

    Stan tego użytkownika na karcie **Opiekunowie** jest ustawiony na **zwolniony** , a **stan blokady** na stronie wysuwanej jest zmieniany na **False**.

> [!NOTE]
> Opiekun może być jednocześnie zaangażowany w kilka spraw prawnych. Gdy opiekun zostanie zwolniony z konkretnej sprawy, blokady i powiadomienia w innych przypadkach nie będą miały wpływu.
