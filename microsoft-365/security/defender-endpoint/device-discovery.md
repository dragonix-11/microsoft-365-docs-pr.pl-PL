---
title: Omówienie wykrywania urządzeń
description: Dowiedz się, jak korzystać z odnajdywania punktów końcowych w Microsoft 365 Defender, aby znaleźć niezarządzane urządzenia w sieci
keywords: odnajdywanie, odnajdywanie, pasywne, proaktywne, sieć, widoczność, serwer, stacja robocza, dołączanie, urządzenia niezarządzane
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: siosulli
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7b76fff060b46cbe13c11eb90f521af61e8900f5
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172922"
---
# <a name="device-discovery-overview"></a>Omówienie wykrywania urządzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ochrona środowiska wymaga spisu urządzeń znajdujących się w sieci. Jednak mapowanie urządzeń w sieci często może być kosztowne, trudne i czasochłonne.

Ochrona punktu końcowego w usłudze Microsoft Defender zapewnia funkcję odnajdywania urządzeń, która ułatwia znajdowanie niezarządzanych urządzeń połączonych z siecią firmową bez konieczności stosowania dodatkowych urządzeń lub kłopotliwych zmian procesów. Odnajdywanie urządzeń używa dołączonych punktów końcowych w sieci do zbierania, sondowania lub skanowania sieci w celu odnalezienia urządzeń niezarządzanych. Funkcja odnajdywania urządzeń umożliwia odnajdywanie następujących elementów:

- Enterprise punkty końcowe (stacje robocze, serwery i urządzenia przenośne), które nie zostały jeszcze dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender
- Urządzenia sieciowe, takie jak routery i przełączniki
- Urządzenia IoT, takie jak drukarki i aparaty fotograficzne

Nieznane i niezarządzane urządzenia wiążą się ze znacznymi zagrożeniami dla sieci — niezależnie od tego, czy jest to drukarka nienadzorowana, urządzenia sieciowe ze słabymi konfiguracjami zabezpieczeń, czy serwer bez mechanizmów kontroli zabezpieczeń. Po odnalezieniu urządzeń można wykonywać następujące czynności:

- Dołączanie niezarządzanych punktów końcowych do usługi, co zwiększa widoczność zabezpieczeń.
- Zmniejsz obszar ataków, identyfikując i oceniając luki w zabezpieczeniach oraz wykrywając luki w konfiguracji.

Obejrzyj to wideo, aby zapoznać się z szybkim omówieniem sposobu odnajdywania urządzeń:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWORdQ]

W połączeniu z tą funkcją zalecenie dotyczące zabezpieczeń dołączania urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender jest dostępne w ramach istniejącego środowiska Zarządzanie zagrożeniami i lukami.

## <a name="discovery-methods"></a>Metody odnajdywania

Możesz wybrać tryb odnajdywania używany przez dołączone urządzenia. Tryb steruje poziomem widoczności, który można uzyskać dla urządzeń niezarządzanych w sieci firmowej.

Dostępne są dwa tryby odnajdywania:

- **Podstawowe odnajdywanie**: w tym trybie punkty końcowe będą pasywnie zbierać zdarzenia w sieci i wyodrębniać z nich informacje o urządzeniu. Podstawowe odnajdywanie używa danych binarnych SenseNDR.exe do pasywnego zbierania danych sieciowych i nie zostanie zainicjowany żaden ruch sieciowy. Punkty końcowe po prostu wyodrębnią dane z każdego ruchu sieciowego, który jest widoczny dla dołączonego urządzenia. W przypadku podstawowego odnajdywania uzyskasz tylko ograniczoną widoczność niezarządzanych punktów końcowych w sieci.

- **Odnajdywanie** standardowe (zalecane): ten tryb umożliwia punktom końcowym aktywne znajdowanie urządzeń w sieci w celu wzbogacenia zebranych danych i odnalezienia większej liczby urządzeń , co ułatwia tworzenie niezawodnego i spójnego spisu urządzeń. Oprócz urządzeń obserwowanych przy użyciu metody pasywnej tryb standardowy wykorzystuje również typowe protokoły odnajdywania korzystające z zapytań multiemisji w sieci w celu znalezienia jeszcze większej liczby urządzeń. Tryb standardowy używa inteligentnego, aktywnego sondowania w celu odnalezienia dodatkowych informacji o obserwowanych urządzeniach w celu wzbogacenia istniejących informacji o urządzeniu. Po włączeniu trybu standardowego minimalne i znikome działanie sieci generowane przez czujnik odnajdywania może być obserwowane przez narzędzia do monitorowania sieci w organizacji.

Aby uzyskać więcej informacji, możesz zmienić i dostosować ustawienia odnajdywania, aby uzyskać więcej informacji, zobacz [Konfigurowanie odnajdywania urządzeń](configure-device-discovery.md).

> [!IMPORTANT]
> Odnajdywanie standardowe jest trybem domyślnym dla wszystkich klientów od 19 lipca 2021 r. Tę konfigurację można zmienić na podstawową za pośrednictwem strony ustawień. Jeśli wybierzesz tryb podstawowy, uzyskasz tylko ograniczoną widoczność niezarządzanych punktów końcowych w sieci.

> [!NOTE]
> Aparat odnajdywania rozróżnia zdarzenia sieciowe odbierane w sieci firmowej i poza siecią firmową. Urządzenia, które nie są połączone z sieciami firmowymi, nie zostaną odnalezione ani wymienione w spisie urządzeń.

## <a name="device-inventory"></a>Spisz urządzeń

Urządzenia, które zostały odnalezione, ale nie zostały jeszcze dołączone i zabezpieczone przez Ochrona punktu końcowego w usłudze Microsoft Defender, zostaną wymienione w spisie urządzeń na karcie Komputery i urządzenia przenośne.

Aby ocenić te urządzenia, możesz użyć filtru na liście spisu urządzeń o nazwie Stan dołączania, który może mieć dowolną z następujących wartości:

- Dołączone: punkt końcowy jest dołączany do Ochrona punktu końcowego w usłudze Microsoft Defender.
- Można dołączyć: punkt końcowy został odnaleziony w sieci, a system operacyjny został zidentyfikowany jako obsługiwany przez Ochrona punktu końcowego w usłudze Microsoft Defender, ale nie jest obecnie dołączony. Zdecydowanie zalecamy dołączenie tych urządzeń.
- Nieobsługiwane: punkt końcowy został odnaleziony w sieci, ale nie jest obsługiwany przez Ochrona punktu końcowego w usłudze Microsoft Defender.
- Niewystarczające informacje: system nie może określić możliwości obsługi urządzenia. Włączenie odnajdywania standardowego na większej liczby urządzeń w sieci może wzbogacić odnalezione atrybuty.

:::image type="content" source="images/2b62255cd3a9dd42f3219e437b956fb9.png" alt-text="Pulpit nawigacyjny spisu urządzeń" lightbox="images/2b62255cd3a9dd42f3219e437b956fb9.png":::

> [!TIP]
> Zawsze można stosować filtry, aby wykluczyć urządzenia niezarządzane z listy spisu urządzeń. Możesz również użyć kolumny stanu dołączania w zapytaniach interfejsu API, aby odfiltrować urządzenia niezarządzane.

Aby uzyskać więcej informacji, zobacz [Spis urządzeń](machines-view-overview.md).

## <a name="network-device-discovery"></a>Odnajdywanie urządzeń sieciowych

Duża liczba niezarządzanych urządzeń sieciowych wdrożonych w organizacji tworzy dużą powierzchnię ataku i stanowi znaczne zagrożenie dla całego przedsiębiorstwa. Ochrona punktu końcowego w usłudze Microsoft Defender możliwości odnajdywania sieci ułatwiają wykrywanie, dokładne klasyfikowanie i dodawanie urządzeń sieciowych do spisu zasobów.

Urządzenia sieciowe nie są zarządzane jako standardowe punkty końcowe, ponieważ usługa Defender dla punktu końcowego nie ma czujnika wbudowanego w same urządzenia sieciowe. Tego typu urządzenia wymagają podejścia bez agenta, w którym zdalne skanowanie będzie uzyskiwać niezbędne informacje z urządzeń. W tym celu wyznaczone urządzenie Ochrona punktu końcowego w usłudze Microsoft Defender będzie używane w każdym segmencie sieci do przeprowadzania okresowych uwierzytelnionych skanów wstępnie skonfigurowanych urządzeń sieciowych. Po odnalezieniu funkcje Zarządzanie zagrożeniami i lukami usługi Defender for Endpoint zapewniają zintegrowane przepływy pracy w celu zabezpieczenia odnalezionych przełączników, routerów, kontrolerów sieci WLAN, zapór i bram sieci VPN.

Aby uzyskać więcej informacji, zobacz [Urządzenia sieciowe](network-devices.md).

## <a name="device-discovery-integrations"></a>Integracje odnajdywania urządzeń

Aby sprostać wyzwaniu, które polega na uzyskaniu wystarczającej widoczności do lokalizowania, identyfikowania i zabezpieczania pełnego spisu zasobów OT/IOT, Ochrona punktu końcowego w usłudze Microsoft Defender teraz obsługuje następujące integracje:

- **Corelight**: Firma Microsoft nawiązała współpracę z firmą Corelight w celu odbierania danych z urządzeń sieciowych Corelight. Zapewnia to Microsoft 365 Defender ze zwiększonym wglądem w działania sieciowe urządzeń niezarządzanych, w tym komunikację z innymi urządzeniami niezarządzanymi lub sieciami zewnętrznymi. Aby uzyskać więcej informacji, zobacz [Włączanie integracji danych Corelight](corelight-integration.md).

- **Microsoft Defender for IoT**: ta integracja łączy możliwości odnajdywania urządzeń Ochrona punktu końcowego w usłudze Microsoft Defender z funkcjami monitorowania bez agenta usługi Microsoft Defender for IoT, aby zabezpieczyć urządzenia IoT przedsiębiorstwa podłączone do sieci IT (na przykład voice over Internet Protocol (VoIP), drukarki i inteligentne telewizory). Aby uzyskać więcej informacji, zobacz [Włączanie integracji usługi Microsoft Defender for IoT](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Ocena luk w zabezpieczeniach na odnalezionych urządzeniach

Luki w zabezpieczeniach i zagrożenia na urządzeniach oraz inne odnalezione urządzenia niezarządzane w sieci są częścią bieżących przepływów programu TVM w obszarze "Rekomendacje zabezpieczeń" i są reprezentowane na stronach jednostek w portalu.
Wyszukaj rekomendacje dotyczące zabezpieczeń dotyczące protokołu "SSH", aby znaleźć luki w zabezpieczeniach protokołu SSH powiązane z urządzeniami niezarządzanymi i zarządzanymi.

:::image type="content" source="images/1156c82ffadd356ce329d1cf551e806c.png" alt-text="Pulpit nawigacyjny zaleceń dotyczących zabezpieczeń" lightbox="images/1156c82ffadd356ce329d1cf551e806c.png":::


## <a name="use-advanced-hunting-on-discovered-devices"></a>Używanie zaawansowanego wyszukiwania zagrożeń na odnalezionych urządzeniach

Zaawansowane zapytania dotyczące wyszukiwania zagrożeń umożliwiają uzyskanie wglądu w odnalezione urządzenia. Szczegółowe informacje o odnalezionych urządzeniach znajdują się w tabeli DeviceInfo lub informacje dotyczące sieci dotyczące tych urządzeń w tabeli DeviceNetworkInfo.

:::image type="content" source="images/f48ba1779eddee9872f167453c24e5c9.png" alt-text="Strona Zaawansowane wyszukiwanie zagrożeń, na której można używać zapytań" lightbox="images/f48ba1779eddee9872f167453c24e5c9.png":::

### <a name="query-discovered-devices-details"></a>Wykonywanie zapytań dotyczących odnalezionych urządzeń

Uruchom to zapytanie w tabeli DeviceInfo, aby zwrócić wszystkie odnalezione urządzenia wraz z najbardziej szczegółowymi informacjami dla każdego urządzenia:

```query
DeviceInfo
| summarize arg_max(Timestamp, *) by DeviceId  // Get latest known good per device Id
| where isempty(MergedToDeviceId) // Remove invalidated/merged devices
| where OnboardingStatus != "Onboarded" 
```

Wywołując funkcję **SeenBy** , w zaawansowanym zapytaniu wyszukiwania zagrożeń możesz uzyskać szczegółowe informacje na temat tego, które urządzenie zostało dołączone do odnalezionego urządzenia.Te informacje mogą pomóc w określeniu lokalizacji sieciowej każdego odnalezionego urządzenia, a następnie ułatwić jego identyfikację w sieci.  

```query
DeviceInfo
| where OnboardingStatus != "Onboarded" 
| summarize arg_max(Timestamp, *) by DeviceId  
| where isempty(MergedToDeviceId)  
| limit 100 
| invoke SeenBy() 
| project DeviceId, DeviceName, DeviceType, SeenBy  
```

Aby uzyskać więcej informacji, zobacz funkcję [SeenBy(](/microsoft-365/security/defender/advanced-hunting-seenby-function) ).

### <a name="query-network-related-information"></a>Informacje dotyczące sieci zapytań

Odnajdywanie urządzeń korzysta z Ochrona punktu końcowego w usłudze Microsoft Defender dołączonych urządzeń jako źródła danych sieciowych w celu przypisywania działań do urządzeń nieprzysłanych. Czujnik sieciowy na urządzeniu dołączonym do Ochrona punktu końcowego w usłudze Microsoft Defender identyfikuje dwa nowe typy połączeń:

- ConnectionAttempt — próba nawiązania połączenia TCP (syn)
- ConnectionAcknowledged — potwierdzenie, że połączenie TCP zostało zaakceptowane (syn\ack)

Oznacza to, że gdy urządzenie niewsładzone próbuje komunikować się z dołączonym urządzeniem Ochrona punktu końcowego w usłudze Microsoft Defender, próba wygeneruje element DeviceNetworkEvent, a działania urządzenia nienadsuwanego będą widoczne na osi czasu dołączonych urządzeń oraz za pośrednictwem tabeli DeviceNetworkEvents wyszukiwania zaawansowanego.

Możesz wypróbować to przykładowe zapytanie:

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="next-steps"></a>Następne kroki

- [Konfiguruj wykrywanie urządzeń](configure-device-discovery.md)
- [Często zadawane pytania dotyczące odnajdywania urządzeń](device-discovery-faq.md)
