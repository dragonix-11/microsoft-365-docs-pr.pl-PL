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
ms.openlocfilehash: 3d1ec22febe0c0072a4eed2a9b8fece3687762d7
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754280"
---
# <a name="quickly-hunt-for-entity-or-event-information-with-go-hunt"></a>Szybkie poszukiwania informacji o encji lub zdarzeniach za pomocą ponagowego poszukiwania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Akcja wyszukiwania *w podróży umożliwia* szybkie badanie wydarzeń i różnych typów encji przy użyciu zaawansowanych możliwości wyszukiwania opartych [na](advanced-hunting-overview.md) zapytaniach. Ta akcja automatycznie uruchamia zaawansowane zapytanie wyszukiwania w celu znalezienia odpowiednich informacji na temat wybranego wydarzenia lub jednostki.

Akcja *poszukiwania w podróży* jest dostępna w różnych sekcjach usługi Defender dla chmury. Ta akcja jest dostępna do wyświetlenia po wyświetlzeniu zdarzenia lub szczegółów encji. Możesz na przykład skorzystać z opcji *poszukiwania w następujących* sekcjach:

- Na stronie [zdarzenia możesz](investigate-incidents.md#summary) przeglądać szczegóły dotyczące użytkowników, urządzeń i wielu innych jednostek skojarzonych z zdarzeniem. Po wybraniu encji są dostępne dodatkowe informacje i różne działania, które można podjąć w encji. W poniższym przykładzie zaznaczono skrzynkę pocztową ze szczegółami skrzynki pocztowej i opcją poszukiwania dodatkowych informacji o skrzynce pocztowej.

    :::image type="content" source="../../media/go-hunt-1-incident.png" alt-text="Strona Skrzynki pocztowe z opcją przejdź do wyszukiwania w Microsoft 365 Defender poczty" lightbox="../../media/go-hunt-1-incident.png":::

- Na stronie zdarzenia możesz również uzyskać dostęp do listy obiektów na karcie **Dowód** . Wybranie jednego z tych obiektów umożliwia szybkie poszukanie informacji o tej encji.

    :::image type="content" source="../../media/go-hunt-2-entity.png" alt-text="Opcja Przejdź do wyszukiwania informacji na temat dowodu na stronie Zdarzenie w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/go-hunt-2-entity.png":::


- Podczas wyświetlania osi czasu dla urządzenia możesz wybrać zdarzenie na osi czasu, aby wyświetlić dodatkowe informacje o tym zdarzeniu. Po wybraniu wydarzenia możesz wybrać inne ważne wydarzenia podczas zaawansowanego wyszukiwania.

    :::image type="content" source="../../media/go-hunt-3-event.png" alt-text="Opcja Wyszukiwania powiązanych zdarzeń na stronie zdarzenia na karcie Osie czasu w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/go-hunt-3-event.png":::

Wybierz **pozycję Przejdź do wyszukiwania** lub **Pozycję Wyszukiwania, aby uzyskać** informacje o powiązanych zdarzeniach, w zależności od tego, czy wybrano encję, czy zdarzenie.

## <a name="query-for-entity-information"></a>Kwerenda dla informacji o encji
Możesz użyć funkcji *wyszukiwania w* celu wyszukiwania informacji o użytkowniku, urządzeniu lub encji dowolnego innego typu. Zapytanie sprawdza wszystkie odpowiednie tabele schematów pod każdym zdarzeniami obejmującymi tę jednostkę w celu zwrócenia informacji. Aby zachować możliwości zarządzania wynikami, zapytanie:
- obejmuje ten sam okres czasu, co najwcześniejsze działanie w ciągu ostatnich 30 dni, które obejmuje jednostkę
- skojarzone z tym zdarzeniem.

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
Możesz użyć opcji go *hunt* po wybraniu dowolnego z następujących typów encji:

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
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytań](advanced-hunting-query-results.md)
- [Niestandardowe reguły wykrywania](custom-detection-rules.md)
