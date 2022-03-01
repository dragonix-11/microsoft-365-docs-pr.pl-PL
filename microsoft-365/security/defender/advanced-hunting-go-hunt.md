---
title: Uzyskiwanie istotnych informacji o encji za pomocą poszukiwania
description: Dowiedz się, jak korzystać z narzędzia wyszukiwania w celu szybkiego wyszukiwania odpowiednich informacji na temat encji lub wydarzenia przy użyciu wyszukiwania zaawansowanego.
keywords: zaawansowane wyszukiwania, zdarzenia, przestaw, jednostki, idź szukać, odpowiednie wydarzenia, szukanie zagrożeń, szukanie przed cyberzagrożeniami, wyszukiwanie, zapytanie, telemetria, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e14f2d5e35585cf5b0edfe433084fa7c8a1d5280
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2021
ms.locfileid: "62996825"
---
# <a name="quickly-hunt-for-entity-or-event-information-with-go-hunt"></a>Szybkie poszukiwania informacji o encji lub zdarzeniach za pomocą ponagowego poszukiwania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Akcja wyszukiwania *w podróży umożliwia* szybkie badanie wydarzeń i różnych typów encji przy użyciu zaawansowanych możliwości wyszukiwania opartych [na](advanced-hunting-overview.md) zapytaniach. Ta akcja automatycznie uruchamia zaawansowane zapytanie wyszukiwania w celu znalezienia odpowiednich informacji na temat wybranego wydarzenia lub jednostki.

Akcja *poszukiwania w celu poszukiwania* miejsca jest dostępna w różnych sekcjach usługi Defender dla chmury po każdym wyświetlaniu szczegółów zdarzenia lub jednostki. Możesz na przykład skorzystać z funkcji *poszukiwania w* następujących sekcjach:

- Na stronie [zdarzenia możesz](investigate-incidents.md#summary) przeglądać szczegóły dotyczące użytkowników, urządzeń i wielu innych jednostek skojarzonych z zdarzeniem. Po wybraniu encji są dostępne dodatkowe informacje oraz różne działania, które można podjąć w encji. W poniższym przykładzie zaznaczono skrzynkę pocztową ze szczegółami skrzynki pocztowej, a także opcją poszukiwania dodatkowych informacji na temat skrzynki pocztowej.

    :::image type="content" source="../../media/go-hunt-1-incident.png" alt-text="Strona **Skrzynki pocztowe** z opcją **Go hunt** w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/go-hunt-1-incident.png":::

- Na stronie zdarzenia możesz również uzyskać dostęp do listy obiektów na karcie **Dowód** . Wybranie jednego z tych obiektów umożliwia szybkie poszukanie informacji o tej encji.

    :::image type="content" source="../../media/go-hunt-2-entity.png" alt-text="Opcja Przejdź do wyszukiwania informacji na temat dowodu na stronie **Zdarzenie** w portalu Microsoft 365 Defender informacje" lightbox="../../media/go-hunt-2-entity.png":::


- Podczas wyświetlania osi czasu dla urządzenia możesz wybrać zdarzenie na osi czasu, aby wyświetlić dodatkowe informacje o tym zdarzeniu. Po wybraniu wydarzenia możesz wybrać inne ważne wydarzenia podczas zaawansowanego wyszukiwania.

    :::image type="content" source="../../media/go-hunt-3-event.png" alt-text="Opcja **Wyszukiwania powiązanych zdarzeń** na stronie zdarzenia na karcie **Osie czasu** w Microsoft 365 Defender portalu" lightbox="../../media/go-hunt-3-event.png":::

Wybierz **pozycję Przejdź do wyszukiwania** lub **Pozycję Wyszukiwania, aby uzyskać** informacje o powiązanych zdarzeniach, w zależności od tego, czy wybrano encję, czy zdarzenie.

## <a name="query-for-entity-information"></a>Kwerenda dla informacji o encji
W przypadku *wyszukiwania informacji* o użytkowniku, urządzeniu lub encji dowolnego innego typu za pomocą wyszukiwania go zapytanie sprawdza wszystkie odpowiednie tabele schematu pod każdym zdarzeniami obejmującymi tę jednostkę. Aby zachować możliwość zarządzania wynikami, kwerenda jest związana z tym samym okresem czasu, co najwcześniejsze działanie w ciągu ostatnich 30 dni, które obejmuje encję i jest skojarzone z zdarzeniem.

Poniżej znajduje się przykładowa kwerenda wyszukiwania w celu wyszukiwania danych dla urządzenia:

```kusto
let selectedTimestamp = datetime(2020-06-02T02:06:47.1167157Z);
let deviceName = "fv-az770.example.com";
let deviceId = "device-guid";
search in (DeviceLogonEvents, DeviceProcessEvents, DeviceNetworkEvents, DeviceFileEvents, DeviceRegistryEvents, DeviceImageLoadEvents, DeviceEvents, DeviceImageLoadEvents, IdentityLogonEvents, IdentityQueryEvents)
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
and DeviceName == deviceName
// or RemoteDeviceName == deviceName
// or DeviceId == deviceId
| take 100
```
### <a name="supported-entity-types"></a>Obsługiwane typy encji
Możesz skorzystać z *opcji poszukiwania po* wybraniu dowolnego z następujących typów encji:

- Pliki
- Wiadomości e-mail
- Klastry poczty e-mail
- Skrzynki pocztowe
- Użytkownicy
- Urządzenia
- Adresy IP
- Adresy URL

## <a name="query-for-event-information"></a>Kwerenda do informacji o zdarzeniu
W przypadku *wyszukiwania informacji* o zdarzeniu osi czasu za pomocą opcji wyszukiwania w celu wyszukiwania informacji o zdarzeniu osi czasu zapytanie sprawdza wszystkie odpowiednie tabele schematu pod innymi zdarzeniami w czasie wybranego zdarzenia. Na przykład poniższe zapytanie zawiera listę zdarzeń z różnych tabel schematu, które miały miejsce w tym samym czasie na tym samym urządzeniu:

```kusto
// List relevant events 30 minutes before and after selected LogonAttempted event
let selectedEventTimestamp = datetime(2020-06-04T01:29:09.2496688Z);
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
    Timestamp between ((selectedEventTimestamp - 30m) .. (selectedEventTimestamp + 30m))
    and DeviceId == "079ecf9c5798d249128817619606c1c47369eb3e"
| sort by Timestamp desc
| extend Relevance = iff(Timestamp == selectedEventTimestamp, "Selected event", iff(Timestamp < selectedEventTimestamp, "Earlier event", "Later event"))
| project-reorder Relevance
```

## <a name="adjust-the-query"></a>Dostosowywanie zapytania
Mając trochę wiedzy na [temat języka](advanced-hunting-query-language.md) zapytań, możesz dostosować zapytanie do własnych preferencji. Możesz na przykład dostosować tę linię, która określa rozmiar okna czasu:

```kusto
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
```

Oprócz modyfikowania zapytania w celu uzyskania bardziej istotnych wyników można również:
- [Wyświetlanie wyników jako wykresów](advanced-hunting-query-results.md#view-query-results-as-a-table-or-chart)
- [Tworzenie reguły wykrywania niestandardowego](custom-detection-rules.md)

>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w programie Microsoft Defender for Endpoint. [Włącz Microsoft 365 Defender](m365d-enable.md), aby poszukać zagrożeń przy użyciu większej liczby źródeł danych. Możesz przenieść zaawansowane przepływy pracy wyszukiwania z programu Microsoft Defender for Endpoint do programu Microsoft 365 Defender, korzystając z procedury migrowania zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytania](advanced-hunting-query-results.md)
- [Niestandardowe reguły wykrywania](custom-detection-rules.md)
