---
title: Przeglądanie alertów w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Przejrzyj informacje o alertach, w tym zwizualizowaną historię alertu i szczegóły dla każdego kroku łańcucha.
keywords: zdarzenia, zdarzenia, maszyny, urządzenia, użytkownicy, alerty, alerty, badanie, wykres, dowody
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
ms.openlocfilehash: 76503c180dfdd2314254efc9315235c0802ab7f8
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607548"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>Przeglądanie alertów w Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Strona alertu w Ochrona punktu końcowego w usłudze Microsoft Defender zapewnia pełny kontekst alertu przez połączenie sygnałów ataku i alertów związanych z wybranym alertem w celu utworzenia szczegółowego scenariusza alertu.

Szybkie klasyfikowanie, badanie i podjęcie skutecznych działań w przypadku alertów wpływających na organizację. Dowiedz się, dlaczego zostały one wyzwolone, i ich wpływ z jednej lokalizacji. Dowiedz się więcej w tym przeglądzie.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>Wprowadzenie do alertu

Wybranie nazwy alertu w usłudze Defender for Endpoint spowoduje wylądowanie na jego stronie alertu. Na stronie alertu wszystkie informacje będą wyświetlane w kontekście wybranego alertu. Każda strona alertu składa się z 4 sekcji:

1. **Tytuł alertu** zawiera nazwę alertu i przypomina, który alert rozpoczął bieżące badanie, niezależnie od tego, co zostało wybrane na stronie.
2. [**Zasoby, których dotyczy**](#review-affected-assets) problem, wyświetla listę kart urządzeń i użytkowników, których dotyczy ten alert, które można kliknąć, aby uzyskać więcej informacji i akcji.
3. W **scenariuszu alertu** są wyświetlane wszystkie jednostki związane z alertem połączone przez widok drzewa. Alert w tytule będzie widoczny po pierwszym trafieniu na stronę wybranego alertu. Jednostki w scenariuszu alertu można rozszerzać i klikać, aby udostępnić dodatkowe informacje i przyspieszyć reagowanie, umożliwiając wykonywanie akcji bezpośrednio w kontekście strony alertu. Użyj scenariusza alertu, aby rozpocząć badanie. Dowiedz się, jak [w temacie Badanie alertów w Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/investigate-alerts).
4. W **okienku szczegółów najpierw zostaną wyświetlone** szczegóły wybranego alertu ze szczegółami i akcjami związanymi z tym alertem. Jeśli wybierzesz dowolne zasoby lub jednostki, których dotyczy problem, w wątku alertu okienko szczegółów zmieni się, aby udostępnić informacje kontekstowe i akcje dla wybranego obiektu.

Zanotuj stan wykrywania alertu.

- Zapobiec: próbowano uniknąć podejrzanej akcji. Na przykład plik nie został zapisany na dysku lub wykonany.

  :::image type="content" source="images/detstat-prevented.png" alt-text="Strona przedstawiająca zapobieganie zagrożeniu" lightbox="images/detstat-prevented.png":::

- Zablokowane: podejrzane zachowanie zostało wykonane, a następnie zablokowane. Na przykład proces został wykonany, ale ponieważ później wykazywał podejrzane zachowania, proces został zakończony.

  :::image type="content" source="images/detstat-blocked.png" alt-text="Strona przedstawiająca blokadę zagrożenia" lightbox="images/detstat-blocked.png":::

- Wykryto: Wykryto atak i prawdopodobnie nadal jest aktywny.

  :::image type="content" source="images/detstat-detected.png" alt-text="Strona przedstawiająca wykrywanie zagrożenia" lightbox="images/detstat-detected.png":::

Następnie możesz również przejrzeć *szczegóły zautomatyzowanego badania* w okienku szczegółów alertu, aby zobaczyć, które akcje zostały już wykonane, a także przeczytać opis alertu dla zalecanych akcji.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="Okienko szczegółów z wyróżnionym opisem alertu i sekcjami automatycznego badania" lightbox="images/alert-air-and-alert-description.png":::

Inne informacje dostępne w okienku szczegółów po otwarciu alertu obejmują techniki MITRE, źródło i dodatkowe szczegóły kontekstowe.

> [!NOTE]
> Jeśli widzisz stan alertu *Nieobsługiwany typ alertu* , oznacza to, że funkcje zautomatyzowanego badania nie mogą odebrać tego alertu w celu uruchomienia zautomatyzowanego badania. Można jednak [zbadać te alerty ręcznie](../defender/investigate-incidents.md#alerts).

## <a name="review-affected-assets"></a>Przeglądanie zasobów, których dotyczy problem

Wybranie urządzenia lub karty użytkownika w sekcjach elementów zawartości, których dotyczy problem, spowoduje przejście do szczegółów urządzenia lub użytkownika w okienku szczegółów.

- **W przypadku urządzeń** w okienku szczegółów zostaną wyświetlone informacje o samym urządzeniu, takie jak domena, system operacyjny i adres IP. Dostępne są również aktywne alerty i zalogowani użytkownicy na tym urządzeniu. Możesz podjąć natychmiastowe działania, izolowając urządzenie, ograniczając wykonywanie aplikacji lub uruchamiając skanowanie antywirusowe. Alternatywnie możesz zebrać pakiet badania, zainicjować zautomatyzowane badanie lub przejść do strony urządzenia, aby zbadać go z punktu widzenia urządzenia.

   :::image type="content" source="images/device-page-details.png" alt-text="Okienko szczegółów po wybraniu urządzenia" lightbox="images/device-page-details.png":::

- **W przypadku użytkowników** w okienku szczegółów zostaną wyświetlone szczegółowe informacje o użytkowniku, takie jak nazwa sam użytkownika i identyfikator SID, a także typy logowania wykonywane przez tego użytkownika oraz wszelkie związane z nim alerty i zdarzenia. Możesz wybrać pozycję *Otwórz stronę użytkownika* , aby kontynuować badanie z punktu widzenia tego użytkownika.

   :::image type="content" source="images/user-page-details.png" alt-text="Okienko szczegółów po wybraniu użytkownika" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Wyświetlanie i organizowanie kolejki zdarzeń](view-incidents-queue.md)
- [Badanie zdarzeń](investigate-incidents.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
