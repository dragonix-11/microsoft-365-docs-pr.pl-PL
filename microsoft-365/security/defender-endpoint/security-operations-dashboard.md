---
title: Centrum zabezpieczeń usługi Microsoft Defender pulpit nawigacyjny Operacji zabezpieczeń
description: Pulpit nawigacyjny umożliwia identyfikowanie urządzeń, które są zagrożenia, śledzenie stanu usługi oraz wyświetlanie statystyk oraz informacji o urządzeniach i alertach.
keywords: dashboard, alerts, new, in progress, resolved, risk, devices at risk, threat, reporting, statistics, charts, graphs, health, active malware detections, threat category, categories, password stealer, ransomware, exploit, threat, low severity, active malware
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c08f592ac72be10bb4b967521e7e504a9ae70a86
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472644"
---
# <a name="microsoft-defender-security-center-security-operations-dashboard"></a>Centrum zabezpieczeń usługi Microsoft Defender pulpit nawigacyjny Operacji zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Pulpit **nawigacyjny Operacje zabezpieczeń** to miejsce, wykrywanie i reagowanie w punktach końcowych funkcje są nasłone. Zawiera on ogólne informacje na temat tego, gdzie wykrywanie było widziane, i wyróżnia, gdzie potrzebne są akcje odpowiedzi.

Pulpit nawigacyjny zawiera migawkę:

- Aktywne alerty
- Urządzenia, na których jest ryzykowny sposób
- Kondycja czujnika
- Kondycja usługi
- Raportowanie codziennych urządzeń
- Aktywne automatyczne badania
- Zautomatyzowana statystyka badania
- Ryzykowni użytkownicy
- Podejrzane działania

:::image type="content" source="images/atp-sec-ops-dashboard.png" alt-text="Pulpit nawigacyjny Operacji zabezpieczeń" lightbox="images/atp-sec-ops-dashboard.png":::

Możesz eksplorować i badać alerty i urządzenia, aby szybko określić, czy, gdzie i kiedy wystąpiły podejrzane działania w Twojej sieci, aby ułatwić zrozumienie kontekstu, w którym się pojawiły.

Na **pulpicie nawigacyjnym** Operacje zabezpieczeń zobaczysz zagregowane zdarzenia ułatwiające identyfikację istotnych zdarzeń lub zachowań na urządzeniu. Możesz również przejść do szczegółów szczegółowych zdarzeń i wskaźników niskiego poziomu.

Zawiera również kafelki, które można klikać, które zapewniają wskazówki wizualne dotyczące ogólnego stanu kondycji organizacji. Każdy kafelek powoduje otwarcie szczegółowego widoku odpowiedniego przeglądu.

## <a name="active-alerts"></a>Aktywne alerty

Na kafelku możesz wyświetlić ogólną liczbę aktywnych alertów z ostatnich 30 dni w Twojej sieci. Alerty są pogrupowane w **nowe i** **w toku**.

:::image type="content" source="images/active-alerts-tile.png" alt-text="Strona Aktywne alerty" lightbox="images/active-alerts-tile.png":::

Każda grupa jest dodatkowo skategoryzowana według odpowiednich poziomów ważności alertów. Kliknij liczbę alertów w każdym pierścieniu alertów, aby wyświetlić posortowany widok kolejki tej kategorii (**Nowy** **lub W toku**).

Aby uzyskać więcej informacji, zobacz [Omówienie alertów](alerts-queue.md).

Każdy wiersz zawiera kategorię ważności alertu i krótki opis alertu. Możesz kliknąć alert, aby wyświetlić jego szczegółowy widok. Aby uzyskać więcej informacji, zobacz [Omówienie Ochrona punktu końcowego w usłudze Microsoft Defender alertów](investigate-alerts.md) [i alertów](alerts-queue.md).

## <a name="devices-at-risk"></a>Urządzenia, na których jest ryzykowny sposób

Na tym kafelku jest wyświetlona lista urządzeń z największą liczbą aktywnych alertów. Całkowita liczba alertów dla każdego urządzenia jest wyświetlana w kółku obok nazwy urządzenia, a następnie dodatkowo skategoryzowana według poziomów ważności na końcu kafelka (umieść wskaźnik myszy na każdym pasku ważności, aby wyświetlić jego etykietę).

:::image type="content" source="images/devices-at-risk-tile.png" alt-text="Strona &quot;Urządzenia o ryzyku&quot;" lightbox="images/devices-at-risk-tile.png":::

Kliknij nazwę urządzenia, aby wyświetlić szczegółowe informacje o tym urządzeniu. Aby uzyskać więcej informacji, [zobacz Badanie urządzeń na Ochrona punktu końcowego w usłudze Microsoft Defender Urządzenia](investigate-machines.md).

Możesz również kliknąć **listę Urządzenia** u góry kafelka **, aby** przejść bezpośrednio do listy Urządzenia posortowane według liczby aktywnych alertów. Aby uzyskać więcej informacji, [zobacz Badanie urządzeń na Ochrona punktu końcowego w usłudze Microsoft Defender Urządzenia](investigate-machines.md).

## <a name="devices-with-sensor-issues"></a>Urządzenia z problemami z czujnikami

**Kafelek Urządzenia z problemami** z czujnikiem umożliwia podanie informacji o możliwości poszczególnych urządzeń w celu wysyłania danych czujnika do Ochrona punktu końcowego w usłudze Microsoft Defender danych. Raportuje ono, ile urządzeń wymaga uwagi i ułatwia zidentyfikowanie urządzeń sprawiających problem.

:::image type="content" source="images/atp-tile-sensor-health.png" alt-text="Kafelek Urządzenia z problemami z czujnikiem" lightbox="images/atp-tile-sensor-health.png":::

Istnieją dwa wskaźniki stanu, które dostarczają informacji na temat liczby urządzeń, które nie zgłaszają poprawnie usługi:

- **Nieprawidłowo skonfigurowane**: Te urządzenia mogą częściowo zgłaszać dane czujnika do usługi Ochrona punktu końcowego w usłudze Microsoft Defender i mogą mieć błędy konfiguracji, które trzeba naprawić.
- **Nieaktywny**: Urządzenia, które wstrzymały raportowanie Ochrona punktu końcowego w usłudze Microsoft Defender usługi przez ponad siedem dni w ciągu ostatniego miesiąca.

Po kliknięciu dowolnej grupy zostanie wyświetlona lista urządzeń przefiltrowana według wyboru. Aby uzyskać więcej informacji, zobacz [Sprawdzanie stanu czujnika](check-sensor-status.md) i [Badanie urządzeń](investigate-machines.md).

## <a name="service-health"></a>Kondycja usługi

**Kafelek Kondycja usługi** informuje o tym, czy usługa jest aktywna lub czy występują problemy.

:::image type="content" source="images/status-tile.png" alt-text="Strona Kondycja usługi strony" lightbox="images/status-tile.png":::

Aby uzyskać więcej informacji na temat kondycji usługi, zobacz [Sprawdzanie Ochrona punktu końcowego w usłudze Microsoft Defender kondycji usługi](service-status.md).

## <a name="daily-devices-reporting"></a>Raportowanie codziennych urządzeń

**Kafelek Raportowanie urządzeń dziennych** przedstawia wykres słupkowy przedstawiający liczbę urządzeń raportowania codziennie w ciągu ostatnich 30 dni. Umieść wskaźnik myszy na poszczególnych słupkach na wykresie, aby zobaczyć dokładną liczbę urządzeń raportowania w każdym dniu.

:::image type="content" source="images/atp-daily-devices-reporting.png" alt-text="Kafelek codziennego raportowania urządzeń" lightbox="images/atp-daily-devices-reporting.png":::

## <a name="active-automated-investigations"></a>Aktywne automatyczne badania

Możesz wyświetlić ogólną liczbę zautomatyzowanych badań z ostatnich 30 dni w Twojej sieci, na kafelku Aktywne **automatyczne badania** . Badania są pogrupowane w akcje **Oczekujące**, **Oczekiwanie na urządzenie** i **Uruchomione**.

:::image type="content" source="images/atp-active-investigations-tile.png" alt-text="Aktywne zautomatyzowane badania" lightbox="images/atp-active-investigations-tile.png":::

## <a name="automated-investigations-statistics"></a>Zautomatyzowana statystyka badania

Ten kafelek zawiera statystykę związaną z automatycznymi badaniami z ostatnich siedmiu dni. Na tej stronie pokazano liczbę ukończonych analiz, liczbę pomyślnie naprawionych badań, średni czas oczekiwania na zainicjowanie badania, średni czas rozwiązywania alertów, liczbę badanych alertów oraz liczbę godzin automatyzacji zapisywanych w trakcie typowego badania ręcznego. 

:::image type="content" source="images/atp-automated-investigations-statistics.png" alt-text="Statystyki automatycznego badania" lightbox="images/atp-automated-investigations-statistics.png":::

Możesz kliknąć **pozycję Automatyczne badania****, Działania** naprawcze i Alerty badane, aby  przejść do strony Badania, przefiltrowane według odpowiedniej kategorii. Dzięki temu możesz wyświetlić szczegółowy wykaz analiz w kontekście.

## <a name="users-at-risk"></a>Ryzykowni użytkownicy

Na tym kafelku jest wyświetlona lista kont użytkowników z najbardziej aktywnymi alertami oraz liczba alertów dotyczących alertów wysokiego, średniego lub niskiego poziomu. 

:::image type="content" source="images/atp-users-at-risk.png" alt-text="Strona &quot;Ryzykowni użytkownicy&quot;" lightbox="images/atp-users-at-risk.png":::

Kliknij konto użytkownika, aby wyświetlić szczegółowe informacje o koncie użytkownika. Aby uzyskać więcej informacji [, zobacz Badanie konta użytkownika](investigate-user.md).

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-belowfoldlink)

## <a name="related-topics"></a>Tematy pokrewne

- [Opis Ochrona punktu końcowego w usłudze Microsoft Defender portalu](use.md)
- [Omówienie portalu](portal-overview.md)
- [Wyświetlanie pulpitu nawigacyjnego zarządzania & zagrożeniami](tvm-dashboard-insights.md)
- [Wyświetlanie pulpitu nawigacyjnego analizy zagrożeń i stosowanie zalecanych działań zaradczych](threat-analytics.md)
