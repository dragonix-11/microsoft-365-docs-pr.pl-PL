---
title: Zamknij lub usuń sprawę
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
description: Dowiedz się, co się stanie, gdy dochodzenie lub sprawa prawna obsługiwana przez sprawę zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium) zostanie zamknięta lub usunięta.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: f6428360c76862a0c4ff0c81b1cb83fb8760d789
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096083"
---
# <a name="close-or-delete-an-ediscovery-premium-case"></a>Zamykanie lub usuwanie sprawy zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Gdy sprawa prawna lub dochodzenie obsługiwane przez sprawę zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium) zostaną zakończone, możesz zamknąć lub usunąć sprawę. Możesz również ponownie otworzyć zamkniętą sprawę.

## <a name="close-a-case"></a>Zamykanie sprawy

Oto, co się stanie po zamknięciu sprawy zbierania elektronicznych materiałów dowodowych (Premium):

- Jeśli przypadek zawiera jakiekolwiek lokalizacje zawartości wstrzymane, te blokady zostaną wyłączone. Po wyłączeniu blokady 30-dniowy okres prolongaty (nazywany *blokadą opóźnienia*) jest stosowany do lokalizacji zawartości, które zostały wstrzymane. Zapobiega to natychmiastowemu usuwaniu zawartości i daje administratorom możliwość wyszukiwania lub odzyskiwania zawartości, która zostanie trwale usunięta po upływie okresu wstrzymania opóźnienia. Aby uzyskać więcej informacji, zobacz [Usuwanie lokalizacji zawartości z blokady zbierania elektronicznych materiałów dowodowych](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Zamknięcie sprawy powoduje wyłączenie tylko blokad skojarzonych z tą sprawą. Jeśli inne blokady znajdują się w lokalizacji zawartości (takiej jak blokada postępowania sądowego, blokada zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Standardowa) lub blokada z innego przypadku zbierania elektronicznych materiałów dowodowych (Premium), te blokady będą nadal utrzymywane.

- Sprawa jest nadal wyświetlana na stronie zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview. Szczegóły, blokady, wyszukiwania i członkowie zamkniętej sprawy są zachowywane.

- Sprawę można edytować po jej zamknięciu. Możesz na przykład dodawać lub usuwać członków, tworzyć wyszukiwania, eksportować wyniki wyszukiwania i przygotowywać wyniki wyszukiwania do analizy w środowisku zbierania elektronicznych materiałów dowodowych (Premium). Podstawowa różnica między aktywnymi i zamkniętymi sprawami polega na tym, że blokady są wyłączone po zamknięciu sprawy.

Aby zamknąć przypadek:

1. Na stronie **eDiscovery (Premium)** wybierz przypadek, który chcesz zamknąć.

2. Na karcie **Ustawienia** w obszarze **Informacje o przypadku** kliknij pozycję **Wybierz**.

   ![Uzyskaj dostęp do strony wysuwanej informacji o przypadku w przypadku zbierania elektronicznych materiałów dowodowych (Premium).](..\media\AeDSelectCaseInformation.png) 

3. W dolnej części strony wysuwanej **Informacje o przypadku** kliknij pozycję **Akcje**, a następnie kliknij pozycję **Zamknij przypadek**.

   Ukończenie procesu zamykania może potrwać do 60 minut.

## <a name="reopen-a-closed-case"></a>Ponowne otwieranie zamkniętej sprawy

Po ponownym otwarciu sprawy zbierania elektronicznych materiałów dowodowych (Premium) wszelkie blokady, które istniały po zamknięciu sprawy, nie zostaną automatycznie przywrócone. Po ponownym otwarciu sprawy musisz przejść do karty **Blokady** i włączyć poprzednie blokady. Aby włączyć blokadę, wybierz ją, aby wyświetlić stronę wysuwaną, a następnie ustaw przełącznik **Stan** na **wartość Włączone**.

Aby ponownie otworzyć zamkniętą sprawę:

1. Na stronie **eDiscovery (Premium)** wybierz przypadek, który chcesz ponownie otworzyć.

2. Na karcie **Ustawienia** w obszarze **Informacje o przypadku** kliknij pozycję **Wybierz**.

3. W dolnej części strony wysuwanej **Informacje o przypadku** kliknij pozycję **Akcje**, a następnie kliknij pozycję **Otwórz ponownie przypadek**.

   Ukończenie procesu ponownego otwierania może potrwać do 60 minut.

## <a name="delete-a-case"></a>Usuwanie sprawy

Możesz usunąć zarówno aktywne, jak i zamknięte przypadki zbierania elektronicznych materiałów dowodowych (Premium). Po usunięciu sprawy wszystkie składniki skojarzone ze sprawą, takie jak lista opiekunów, komunikacja, wyszukiwania, zestawy przeglądów i zadanie eksportu, zostaną usunięte. Sprawa jest usuwana z listy przypadków na stronie **zbierania elektronicznych materiałów dowodowych (Premium)** w portalu zgodności usługi Microsoft Purview. Nie można odzyskać ani ponownie otworzyć usuniętego przypadku.

> [!NOTE]
> W scenariuszach rozlania danych jedynym sposobem usunięcia elementów w zestawie przeglądów jest usunięcie przypadku zbierania elektronicznych materiałów dowodowych (Premium). Inne metody "wyszukiwania i przeczyszczania" nie usuwają elementów z zestawu przeglądów.

Przed usunięciem sprawy (niezależnie od tego, czy jest ona aktywna, czy zamknięta) należy najpierw usunąć *wszystkie* blokady skojarzone ze sprawą. Obejmuje to usuwanie blokad ze stanem **Wyłączone**.

Aby usunąć blokady skojarzone ze sprawą:

1. Przejdź do karty **Blokady** w przypadku zbierania elektronicznych materiałów dowodowych (Premium), które chcesz usunąć.

2. Kliknij blokadę, którą chcesz usunąć.

3. Na stronie wysuwanej kliknij pozycję **Usuń blokadę**.

Aby usunąć przypadek:

1. Na stronie **eDiscovery (Premium)** wybierz przypadek, który chcesz usunąć.

2. Na karcie **Ustawienia** w obszarze **Informacje o przypadku** kliknij pozycję **Wybierz**.

3. W dolnej części strony wysuwanej **Informacje o przypadku** kliknij pozycję **Akcje**, a następnie kliknij pozycję **Usuń przypadek**.

