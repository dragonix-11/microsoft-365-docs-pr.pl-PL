---
title: Przeglądanie alertów w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Przejrzyj informacje alertów, w tym wizualizowane informacje alertów i szczegóły dla każdego etapu łańcucha.
keywords: zdarzenie, zdarzenia, komputery, urządzenia, użytkownicy, alerty, alerty, badanie, wykres, dowód
ms.prod: m365-security
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.date: 5/1/2020
ms.technology: mde
ms.openlocfilehash: 91cd06188a8337f3d0df0b9c67d7c98e389e4351
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466775"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>Przeglądanie alertów w Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Strona alertu w programie Ochrona punktu końcowego w usłudze Microsoft Defender udostępnia pełny kontekst alertu, łącząc sygnały ataków i alerty związane z wybranym alertem w celu skonstruowania szczegółowej historii alertów.

Możesz szybko sprawdzać, badać i podjąć skuteczne działania dotyczące alertów mających wpływ na organizację. Zrozumienie, dlaczego zostały wyzwolone, i ich wpływ z jednej lokalizacji. Dowiedz się więcej z tego o omówieniem.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>Wprowadzenie do alertu

Wybranie nazwy alertu w programie Defender dla punktu końcowego spowoduje powiadomienie Cię na stronie alertu. Na stronie alertu wszystkie informacje będą wyświetlane w kontekście wybranego alertu. Każda strona alertu składa się z 4 sekcji:

1. **Tytuł alertu zawiera** nazwę alertu i ma przypominać o tym, który alert rozpoczął bieżące badanie, niezależnie od tego, co zostało wybrane na stronie.
2. [**Zasoby, których**](#review-affected-assets) dotyczy problem, to karta urządzeń i użytkowników, których dotyczy ten alert, których kliknięcie umożliwia dodatkowe informacje i działania.
3. W **historii alertu** są wyświetlane wszystkie jednostki powiązane z alertem połączone widokiem drzewa. Alert w tytule będzie alertem w centrum uwagi, gdy po raz pierwszy znajdziesz się na stronie wybranego alertu. Encje w historii alertu można rozwinąć i kliknąć, aby zapewnić dodatkowe informacje i przyspieszyć reakcję, umożliwiając ci działanie bezpośrednio w kontekście strony alertu. Użyj historii alertu, aby rozpocząć badanie. Aby dowiedzieć się, jak [to zrobić, zobacz Badanie alertów w programie Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/investigate-alerts).
4. Na **początku w** okienku szczegółów będą wyświetlane szczegóły wybranego alertu wraz ze szczegółami i akcjami związanymi z tym alertem. Jeśli w wątku alertu wybierzesz dowolny z zasobów lub jednostek, których dotyczy problem, okienko szczegółów zmieni się, aby udostępnić informacje kontekstowe i akcje dla wybranego obiektu.

Zanotuj stan wykrywania alertu.

- Uniemożliwiane: próbowano podejmować podejrzane działania. Na przykład plik nie został zapisany na dysku lub nie został wykonany.

  :::image type="content" source="images/detstat-prevented.png" alt-text="Strona przedstawiająca zapobieganie zagrożeń" lightbox="images/detstat-prevented.png":::

- Zablokowane: Podejrzane zachowanie zostało wykonane, a następnie zablokowane. Na przykład proces został wykonany, ale ponieważ później były w nim realizowane podejrzane zachowania, ten proces został zakończony.

  :::image type="content" source="images/detstat-blocked.png" alt-text="Strona z pokazaną blokadą zagrożenia" lightbox="images/detstat-blocked.png":::

- Wykryto: Wykryto atak, który prawdopodobnie jest nadal aktywny.

  :::image type="content" source="images/detstat-detected.png" alt-text="Strona z wykrywaniem zagrożenia" lightbox="images/detstat-detected.png":::

Następnie możesz przejrzeć szczegóły automatycznego  badania w okienku szczegółów alertu, aby sprawdzić, jakie akcje zostały już wykonane, a także odczytać opis alertu dla zalecanych akcji.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="Okienko szczegółów z wyróżnionym opisem alertu i sekcjami automatycznego badania" lightbox="images/alert-air-and-alert-description.png":::

Gdy alert zostanie otwarty, w okienku szczegółów są dostępne inne informacje, takie jak techniki MITRE, źródło i dodatkowe informacje kontekstowe.

## <a name="review-affected-assets"></a>Przegląd zasobów, których dotyczy problem

Wybranie urządzenia lub karty użytkownika w sekcjach zasobów, których dotyczy problem, spowoduje przełączenie się do szczegółów urządzenia lub użytkownika w okienku szczegółów.

- **W przypadku** urządzeń w okienku szczegółów zostaną wyświetlane informacje o samym urządzeniu, takie jak domena, system operacyjny i adres IP. Dostępne są również aktywne alerty i zalogowani użytkownicy na tym urządzeniu. Możesz podjąć natychmiastowe działanie, odizolując urządzenie, ograniczając uruchamianie aplikacji lub uruchamiając skanowanie antywirusowe. Ewentualnie możesz zebrać pakiet badania, zainicjować zautomatyzowane badanie lub przejść na stronę urządzenia w celu zbadania z punktu widzenia urządzenia.

   :::image type="content" source="images/device-page-details.png" alt-text="Okienko szczegółów, gdy urządzenie jest zaznaczone" lightbox="images/device-page-details.png":::

- **W przypadku** użytkowników w okienku szczegółów zostaną wyświetlane szczegółowe informacje o użytkowniku, takie jak nazwa SAM i identyfikator SID użytkownika, a także typy logowania wykonywane przez tego użytkownika oraz związane z nim alerty i zdarzenia. Możesz wybrać pozycję *Otwórz stronę użytkownika* , aby kontynuować badanie z punktu widzenia tego użytkownika.

   :::image type="content" source="images/user-page-details.png" alt-text="Okienko szczegółów, gdy użytkownik jest zaznaczony" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Wyświetlanie i organizowanie kolejki zdarzeń](view-incidents-queue.md)
- [Badanie zdarzeń](investigate-incidents.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
