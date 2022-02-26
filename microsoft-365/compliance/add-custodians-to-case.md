---
title: Dodawanie elementami do Advanced eDiscovery przypadku
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
description: Dowiedz się, jak używać wbudowanego w programie Advanced eDiscovery do koordynowania przepływów pracy i identyfikowania odpowiednich źródeł danych w przypadku sprawy.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b0a15610c84c9e1142cd1afa6ebf121f387ce807
ms.sourcegitcommit: 2e05865beeb2051fd9ece212a46179310b946a46
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2021
ms.locfileid: "62973802"
---
# <a name="add-custodians-to-an-advanced-ediscovery-case"></a>Dodawanie elementami do Advanced eDiscovery przypadku

Za pomocą wbudowanego narzędzia do zarządzania infrastrukturą w programie Advanced eDiscovery można skoordynować przepływy pracy w celu koordynacji zarządzania nimi i identyfikowania odpowiednich, przewczytczych źródeł danych skojarzonych ze sprawą. Po dodaniu opiekuna system może automatycznie identyfikować jego skrzynkę pocztową, a następnie umieszczać ją w Exchange pocztowej i OneDrive dla Firm konta. W trakcie procesu odnajdowania badania możesz także zidentyfikować inne źródła danych (takie jak skrzynki pocztowe, witryny lub Teams), do których dostęp lub który został współtworowany przez opiekuna. W takiej sytuacji można skojarzyć te źródła danych za pomocą narzędzia do zarządzania nimi. Po dodaniu osób do sprawy przechowywania i skojarzeniu z nimi innego źródła danych można szybko zachować dane i przeszukać dane tego typu.

W czterech krokach możesz dodawać osoby Advanced eDiscovery i zarządzać nimi w takich sytuacjach:

1. Zidentyfikuj opiekunów.

2. Wybierz lokalizacje danych w u użytkownikach.

3. Konfigurowanie ustawień blokowania.

4. Przejrzyj pogotowie i dokończ proces.

## <a name="make-sure-you-have-the-necessary-permissions"></a>Upewnij się, że masz niezbędne uprawnienia

Aby dodać opiekunów do sprawy, musisz być członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych. Zapewnia to uprawnienia niezbędne do dodawania osób do sprawy i blokowania tych źródeł danych. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions).

## <a name="step-1-identify-custodians"></a>Krok 1. Identyfikowanie schłoników

1. Przejdź do [https://compliance.microsoft.com](https://compliance.microsoft.com) konta użytkownika z odpowiednimi uprawnieniami zbierania elektronicznych materiałów dowodowych i zaloguj się przy użyciu tego konta.

2. W lewym okienku nawigacji okna Centrum zgodności platformy Microsoft 365 wybierz pozycję **zbierania** >  elektronicznych materiałów dowodowych **Advanced eDiscovery** a następnie wybierz [**kartę**](https://go.microsoft.com/fwlink/p/?linkid=2173764) Sprawy.

3. Wybierz sprawę, do której chcesz dodać opiekunów.

4. Wybierz **kartę Źródła** danych, a następnie wybierz pozycję Dodaj **źródło danychDowierz** >  **nowe pliki przechowywania**.

5. Dodaj jednego lub więcej użytkowników w organizacji jako element składowy sprawy, wpisując pierwszą część imienia i nazwiska lub aliasu danej osoby. Po odnalezieniu odpowiedniej osoby wybierz jej nazwisko, aby dodać ją do listy.

## <a name="step-2-choose-custodian-data-locations"></a>Krok 2. Wybieranie lokalizacji danych przekierowywczych

Po wybraniu osób przechowywczych system automatycznie podejmie próbę zidentyfikowania i zweryfikowania tych użytkowników i ich źródeł danych. Po dodaniu elementów do listy elementów składowych narzędzie automatycznie uwzględnia podstawową skrzynkę pocztową i konto OneDrive każdego adresata. Można nie uwzględniać tych źródeł danych podczas dodawania osób do przechowywania danych.

Oprócz skrzynki pocztowej adresata i konta OneDrive można także skojarzyć inne lokalizacje danych ze współpracownikiem, takim jak witryna SharePoint lub zespół Microsoft Team, do których należy. Dzięki temu można zachowywać, zbierać, analizować i przeglądać zawartość innych źródeł danych skojarzonych z przechowaniami sprawy.

Aby usunąć zaznaczenie podstawowej skrzynki pocztowej i OneDrive dla osoby przechwytowej:

1. Rozwiń informacje o uchoczycie, aby wyświetlić podstawowe lokalizacje danych, które zostały automatycznie skojarzone z każdym opiekunem.

2. Wybierz **pozycję** Wyczyść obok  pozycji Skrzynka **pocztowa lub OneDrive**, aby usunąć skrzynkę pocztową osoby OneDrive lub konto OneDrive z skojarzoną lokalizacją danych dla tego adresata.

   ![Skonfiguruj lokalizacje do kojarzenia z opiekunem.](../media/ConfigureCustodianLocations.png)

Aby skojarzyć inne skrzynki pocztowe, Teams, grupy Yammer z określonym opiekunem:

1. Rozwiń informacje o uchoczycie, aby wyświetlić następujące usługi w celu skojarzenia lokalizacji danych z tym, który je przetwarza. Kliknij **pozycję Edytuj** obok usługi, aby dodać lokalizację danych.

   - **Exchange**: Użyj, aby skojarzyć inne skrzynki pocztowe z opiekunem. Wpisz w polu wyszukiwania nazwę lub alias (co najmniej trzy znaki) skrzynek pocztowych użytkowników lub grup dystrybucyjnych. Zaznacz skrzynki pocztowe, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**.

   - **SharePoint**: Użyj, aby skojarzyć SharePoint witryn internetowych z opiekunem. Wybierz witrynę na liście lub wyszukaj witrynę, wpisując adres URL w polu wyszukiwania. Wybierz witryny, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**.

   - **Teams**: Użyj, aby przypisać Microsoft Teams, do których jest obecnie członkiem. Wybierz zespoły do przypisania do opiekuna, a następnie kliknij przycisk **Dodaj**. Po dodaniu zespołu system automatycznie identyfikuje i odszuka witrynę grupy SharePoint skojarzoną z tym zespołem skrzynkę pocztową grupy i przypisze ją do osoby, która przejmuje zadania.

   - **Yammer**: Użyj, aby przypisać grupy Yammer których jest aktualnie członkiem. Wybierz grupy, które mają zostać przypisane do opiekuna, a następnie kliknij przycisk **Dodaj**. Po dodaniu zespołu system automatycznie identyfikuje i odszuka witrynę grupy SharePoint skojarzoną z tą grupą skrzynką pocztową, a następnie przypisze ją do osoby, która cię do tego dosyć.

   > [!NOTE]
   > Za pomocą **s Exchange i** SharePoint lokalizacji można  skojarzyć dowolną skrzynkę pocztową lub witrynę w organizacji z opiekunem. , Obejmuje to kojarzenie skrzynki pocztowej i witryny dla grupy usługi Microsoft Team lub Yammer, do których nie należy inicjał. W tym celu musisz dodać zarówno skrzynkę pocztową, jak i witrynę skojarzoną z każdym zespołem lub Yammer grupy.

2. Można wyświetlić łączną liczbę skrzynek pocztowych, witryn, Teams i grup Yammer przypisanych do każdego opiekuna, rozwijając każdego opiekuna w tabeli. Po sfinalizowaniu lokalizacji danych przypisanych do każdego zbioru elementów przechocznych te skojarzenia będą zachowywane i używane podczas zbierania, przetwarzania i przeglądania etapów przepływu pracy usługi Advanced eDiscovery pracy.

3. Po dodaniu osób do przechowywania i skonfigurowaniu ich lokalizacji danych kliknij przycisk **Dalej** , aby przejść do strony **Ustawień wstrzymywania** .  

## <a name="step-3-configure-hold-settings"></a>Krok 3. Konfigurowanie ustawień wstrzymywania

 Po zakończeniu przechowywania i lokalizacji danych można umieścić niektóre lub wszystkie je w agorze. Po umieszczenie w aarchiw uścisków cała zawartość we wszystkich lokalizacjach zawartości skojarzonych z tym opiekunem jest zachowywana do momentu usunięcia zdyskoarzonego lub zwolnienia wstrzymywania. W niektórych przypadkach możesz zechcieć dodać do sprawy przechowywania danych bez umieszczania ich w hold.

Aby umieścić w agorze źródła przechowywania i źródła danych:

1. Na stronie **Ustawienia wstrzymywania** możesz zastosować hold do poszczególnych przechowywania, zaznaczając pole wyboru w kolumnie **Wstrzymaj** .

   Ewentualnie możesz umieścić wszystkie części przechowywania, zaznaczając pole wyboru Wstrzymaj u góry kolumny.

2. Sprawdź ustawienia wieńcowe, a następnie kliknij przycisk **Dalej**.

   > [!NOTE]
   > Jeśli nie nacisniesz miejsca w alercie, do sprawy zostanie dodany opiekun i skojarzone z nim źródła danych, ale zawartość w tych źródłach danych nie zostanie zachowana przez więdło skojarzone ze sprawą.

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>Krok 4. Przeglądanie pochłoń i ukończenie procesu

Przed dodaniem elementów przechowywania do sprawy można przejrzeć listę elementów przechowywania, przypisane do nich lokalizacje danych i ustawienia przechowywania.

1. Sprawdź i przejrzyj wszystkie wartości licznika źródeł danych oraz ustawienie hold skojarzone z każdym oprawcą w tabeli. W razie potrzeby wróć na strony **identyfikuj kopię** zapasową lub strony ustawień Wstrzymaj, aby wprowadzić zmiany.

2. Kliknij **przycisk Submit** (Prześlij), aby dodać do sprawy urządzenia do przechowywania danych i lokalizacje ich danych oraz zastosować wszystkie ustawienia przechowywania.

   Nowe przechowywania zostaną dodane do sprawy i wyświetlone na **karcie Źródła** danych.

   [![Data sources listed on the Data sources tab.](../media/DataSourcesTab.png) ](../media/DataSourcesTab.png#lightbox)
