---
title: Zamykanie lub usuwanie sprawy
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
description: Dowiedz się, co się stanie, gdy śledztwo lub sprawa prawna obsługiwana przez Advanced eDiscovery zostanie zamknięta lub usunięta.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 88e0892bec3f220d9c405f3886c37fa89ad2c647
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983559"
---
# <a name="close-or-delete-an-advanced-ediscovery-case"></a>Zamykanie lub usuwanie Advanced eDiscovery przypadku

Po zakończeniu postępowania sądowego lub dochodzenia obsługiwanego przez Advanced eDiscovery postępowaniu sądowego można zamknąć lub usunąć sprawę. Możesz także ponownie otworzyć zamkniętą sprawę.

## <a name="close-a-case"></a>Zamykanie sprawy

Oto co się dzieje po zamknięciu sprawy Advanced eDiscovery przypadku:

- Jeśli sprawa zawiera jakiekolwiek lokalizacje zawartości w wstrzymaniu, blokady te zostaną wyłączone. Po zakończeniu stosowania blokowania do lokalizacji zawartości, które były wstrzymywane, jest stosowany 30-dniowy okres prolongaty (nazywany opóźnieniem). Pomaga to zapobiec natychmiastowemu usunięciu zawartości i daje administratorom możliwość wyszukania lub odzyskania zawartości, która zostanie trwale usunięta po wygaśnięciu okresu opóźnienia. Aby uzyskać więcej informacji, [zobacz Usuwanie lokalizacji zawartości z zawieszonego zbierania elektronicznych materiałów dowodowych](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Zamknięcie sprawy powoduje tylko wyłączenie zarchiwów, które są skojarzone z tą sprawą. Jeśli w lokalizacji zawartości znajdują się inne blokady (na przykład w związku z postępowaniem sądowym, podstawowe zbierania elektronicznych materiałów dowodowych lub blokady z innego Advanced eDiscovery przypadku), te blokady nadal będą zachowywane.

- Sprawa nadal znajduje się na stronie zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365. Szczegóły, blokady, wyszukiwania i członkowie zamkniętej sprawy zostaną zachowane.

- Możesz edytować sprawę po jej zamknięciu. Na przykład możesz dodawać lub usuwać członków, tworzyć wyszukiwania, eksportować wyniki wyszukiwania i przygotowywać wyniki wyszukiwania do analizy w programie Advanced eDiscovery. Podstawową różnicą między sprawami aktywnymi i zamkniętymi jest wyłączenie blokady w przypadku zamknięcia sprawy.

Aby zamknąć sprawę:

1. Na **Advanced eDiscovery** głównej wybierz sprawę, którą chcesz zamknąć.

2. Na karcie **Ustawienia** w obszarze **Informacje o przypadku** kliknij pozycję **Wybierz**.

   ![Uzyskiwanie dostępu do wysuwanych stron informacji o przypadku Advanced eDiscovery przypadku.](..\media\AeDSelectCaseInformation.png) 

3. U dołu strony **wysuwu informacje o przypadku** **kliknij pozycję Akcje**, a następnie kliknij **pozycję Zamknij sprawę**.

   Ukończenie procesu zamykania może potrwać do 60 minut.

## <a name="reopen-a-closed-case"></a>Ponowne otwieranie zamkniętej sprawy

Po ponownym otwarciu sprawy Advanced eDiscovery, wszelkie blokady, które miały miejsce w chwili zamknięcia sprawy, nie zostaną automatycznie przywrócone. Po ponownym otwarciu sprawy musisz przejść do karty Z blokady i włączyć poprzednie  blokady. Aby włączyć wstrzymaj, wybierz ją, aby wyświetlić stronę wysuwaną, a następnie ustaw przełącznik **Status** na **Wł**.

Aby ponownie otworzyć zamkniętą sprawę:

1. Na **Advanced eDiscovery wybierz** sprawę, którą chcesz otworzyć ponownie.

2. Na karcie **Ustawienia** w obszarze **Informacje o przypadku** kliknij pozycję **Wybierz**.

3. U dołu strony **wysuwu informacje o sprawie** **kliknij pozycję Akcje**, a następnie kliknij pozycję **Otwórz ponownie sprawę**.

   Ponowne otwarcie może potrwać do 60 minut.

## <a name="delete-a-case"></a>Usuwanie sprawy

Możesz usunąć zarówno aktywne, jak i zamknięte Advanced eDiscovery przypadku. Usunięcie sprawy powoduje usunięcie wszystkich składników skojarzonych ze sprawą, takich jak lista elementów składowych, korespondencja, wyszukiwania, zestawy recenzji i zadanie eksportu. Sprawa zostanie usunięta z listy spraw **na stronie Advanced eDiscovery** w Centrum zgodności platformy Microsoft 365. Usuniętej sprawy nie można odzyskać ani ponownie otworzyć.

> [!NOTE]
> W scenariuszach z rozlaniem danych jedynym sposobem na usunięcie elementów w zestawie recenzji jest usunięcie Advanced eDiscovery przypadku. Inne metody wyszukiwania i przeczyszczania nie usuwają elementów z zestawu recenzji.

Przed usunięciem sprawy (aktywnej lub zamkniętej) należy najpierw usunąć wszystkie blokady skojarzone ze sprawą. Obejmuje to usuwanie blokady ze stanem **Wyłączone**.

Aby usunąć blokady skojarzone ze sprawą:

1. Przejdź na **kartę Odchyłki** w Advanced eDiscovery przypadku, który chcesz usunąć.

2. Kliknij wstrzymaj, który chcesz usunąć.

3. Na wysuwanych stronie kliknij pozycję **Usuń przytrzymaj**.

Aby usunąć sprawę:

1. Na **Advanced eDiscovery** głównej zaznacz sprawę, którą chcesz usunąć.

2. Na karcie **Ustawienia** w obszarze **Informacje o przypadku** kliknij pozycję **Wybierz**.

3. U dołu strony **wysuwu informacji o sprawie** **kliknij pozycję Akcje**, a następnie kliknij pozycję **Usuń sprawę**.

