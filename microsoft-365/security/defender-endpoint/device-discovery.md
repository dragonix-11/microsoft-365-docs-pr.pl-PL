---
title: Omówienie odnajdowania urządzeń
description: Dowiedz się, jak korzystać z odnajdowania punktów końcowych Microsoft 365 Defender w celu znalezienia urządzeń nieza zarządzania w Twojej sieci
keywords: odnajdowanie urządzeń, odnajdowanie, pasywne, aktywne, sieci, widoczność, serwer, stacja robocza, urządzenia w trybie onboard, urządzenia nieza zarządzania
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
ms.openlocfilehash: 926d23cb4e9abcecd9d34e976dee60851471613b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472930"
---
# <a name="device-discovery-overview"></a>Omówienie odnajdowania urządzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ochrona środowiska wymaga spisu urządzeń dostępnych w sieci. Jednak urządzenia do mapowania w sieci często mogą być kosztowne, trudne i czasochłonne.

Ochrona punktu końcowego w usłudze Microsoft Defender oferuje funkcję odnajdowania urządzeń, która ułatwia znajdowanie niezakierowane urządzeń połączonych z siecią firmową bez konieczności obsługi dodatkowych urządzeń czy uciążliwych zmian w procesach. Odnajdowanie urządzeń używa w sieci nowych punktów końcowych do zbierania, skanowania lub skanowania sieci w celu odnalezienia urządzeń niezakierowanych. Funkcja odnajdowania urządzeń umożliwia odnajdowanie:

- Enterprise punkty końcowe (stacje robocze, serwery i urządzenia przenośne), które nie zostały jeszcze Ochrona punktu końcowego w usłudze Microsoft Defender
- Urządzenia sieciowe, takie jak routery i przełączniki
- Urządzenia IoT, takie jak drukarki i kamery

Nieznane i niezakierowane urządzenia mogą stanowić istotne ryzyko dla sieci — niezależnie od tego, czy jest to drukarka bez wysyłki, urządzenia sieciowe z słabymi konfiguracjami zabezpieczeń, czy serwer bez kontroli zabezpieczeń. Po odnalezioniu urządzeń możesz:

- Wdowywają nieza zarządzania punktami końcowymi usługi, zwiększając widoczność zabezpieczeń na tych usługach.
- Zmniejsz powierzchnię ataków, identyfikując i oceniając luki w zabezpieczeniach oraz wykrywając luki w konfiguracji.

Obejrzyj ten klip wideo, aby szybko dowiedzieć się, jak odnajdować urządzenia:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWORdQ]

W połączeniu z tą funkcją w ramach istniejącego Zarządzanie zagrożeniami i lukami dostępne jest zalecenie dotyczące zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia.

## <a name="discovery-methods"></a>Metody odnajdowania

Możesz wybrać tryb odnajdowania, który ma być używany przez urządzenia dołączane. Tryb steruje poziomem widoczności, który możesz uzyskać dla urządzeń niezawiązywnych w Twojej sieci firmowej.

Dostępne są dwa tryby odnajdowania:

- **Podstawowe odnajdowanie**: W tym trybie punkty końcowe będą pasywnie zbierać zdarzenia w Twojej sieci i wyodrębniać z nich informacje o urządzeniach. Podstawowe odnajdowanie używa danych binarnych SenseNDR.exe pasywnego zbierania danych sieciowych i ruch sieciowy nie zostanie zainicjowany. Punkty końcowe będą po prostu wyodrębniać dane z każdego ruchu sieciowego widocznego na urządzeniu wewnegłym. W przypadku podstawowego odnajdowania uzyskasz tylko ograniczoną widoczność nieza zarządzania punktami końcowymi w Twojej sieci.

- **Odnajdowanie standardowe** (zalecane): Ten tryb umożliwia punktom końcowym aktywnie znajdowanie urządzeń w Twojej sieci w celu wzbogacenia zebranych danych i znalezienia większej liczby urządzeń — pomaga w budowaniu niezawodnego i spójnego spisu urządzeń. Oprócz urządzeń obserwowanych przy użyciu metody pasywnej tryb standardowy korzysta również z typowych protokołów odnajdowania, które korzystają z zapytań wielocastowych w sieci, aby znaleźć jeszcze więcej urządzeń. W trybie standardowym są używane inteligentne, aktywne funkcje  probowania w celu odnajdowania dodatkowych informacji o obserwowanych urządzeniach w celu wzbogacenia istniejących informacji o urządzeniach. Po włączeniu trybu standardowego aktywność sieciowa wygenerowana przez czujnik odnajdowania może być niewielka i generowana przez ten czujnik, co może być obserwowane przez narzędzia do monitorowania sieci w organizacji.

Możesz zmienić i dostosować ustawienia odnajdowania, aby uzyskać więcej informacji, zobacz Konfigurowanie [odnajdowania urządzeń](configure-device-discovery.md).

> [!IMPORTANT]
> Odnajdowanie standardowe to tryb domyślny dla wszystkich klientów rozpoczynających się 19 lipca 2021 r. Możesz zmienić tę konfigurację na podstawową za pośrednictwem strony ustawień. W przypadku wybrania trybu podstawowego uzyskasz tylko ograniczoną widoczność nieza zarządzania punktami końcowymi w Twojej sieci.

> [!NOTE]
> Aparat odnajdowania rozróżnia zdarzenia sieciowe odbierane w sieci firmowej, a nie poza siecią firmową. Urządzenia, które nie są połączone z sieciami firmowymi, nie zostaną wykryte ani nie będą wymienione w spisie urządzeń.

## <a name="device-inventory"></a>Spis urządzeń

Urządzenia, które zostały odkryte, ale nie zostały jeszcze naniesone i zabezpieczone przez aplikację Ochrona punktu końcowego w usłudze Microsoft Defender zostaną podane w spisie urządzeń na karcie Komputery i urządzenia przenośne.

Aby ocenić te urządzenia, możesz użyć filtru na liście zasobów urządzeń o nazwie Stan dołączania, który może mieć dowolną z następujących wartości:

- Onboarded: Punkt końcowy jest dołączany do Ochrona punktu końcowego w usłudze Microsoft Defender.
- Może zostać wnoszony: Punkt końcowy został wykryty w sieci, a system operacyjny został zidentyfikowany jako obsługiwany przez program Ochrona punktu końcowego w usłudze Microsoft Defender, ale obecnie nie jest on dołączany. Zdecydowanie zalecamy dołączanie tych urządzeń.
- Nieobsługiwane: Punkt końcowy został wykryty w sieci, ale nie jest obsługiwany przez Ochrona punktu końcowego w usłudze Microsoft Defender.
- Za mało informacji: System nie mógł określić możliwości obsługi urządzenia. Włączenie standardowego odnajdowania na większej liczby urządzeń w sieci może wzbogacić wykryte atrybuty.

:::image type="content" source="images/2b62255cd3a9dd42f3219e437b956fb9.png" alt-text="Pulpit nawigacyjny spisu urządzeń" lightbox="images/2b62255cd3a9dd42f3219e437b956fb9.png":::

> [!TIP]
> Zawsze możesz zastosować filtry, aby wykluczyć urządzenia nieza zarządzanie z listy zasobów w spisie urządzeń. Możesz również użyć kolumny stanu dołączania w zapytaniach interfejsu API, aby odfiltrować urządzenia nieza zarządzanie.

Aby uzyskać więcej informacji, zobacz [Spis urządzeń](machines-view-overview.md).

## <a name="network-device-discovery"></a>Odnajdowanie urządzeń sieciowych

Duża liczba niezamanektowanych urządzeń sieciowych wdrożonych w organizacji jest dużym obszarem ataków i stanowi istotne ryzyko dla całego przedsiębiorstwa. Ochrona punktu końcowego w usłudze Microsoft Defender odnajdowania sieci pomagają zapewnić wykrywanie, dokładne klasyfikacje i dodanie urządzeń sieciowych do spisu zasobów.

Urządzenia sieciowe nie są zarządzane jako standardowe punkty końcowe, ponieważ program Defender for Endpoint nie ma wbudowanego czujnika w urządzenia sieciowe. Te typy urządzeń wymagają podejścia bez agenta, w którym skanowanie zdalne uzyska niezbędne informacje z urządzeń. W tym celu na każdym Ochrona punktu końcowego w usłudze Microsoft Defender sieci zostanie użyte wyznaczony urządzenie do wykonywania okresowych uwierzytelnionych skanów wstępnie skonfigurowanych urządzeń sieciowych. Po odkrytiu funkcje łączności usługi Defender for Endpoint Zarządzanie zagrożeniami i lukami zintegrowanych przepływów pracy w celu zabezpieczenia przełączników, routerów, kontrolerów WLAN, zapór i bram VPN.

Aby uzyskać więcej informacji, zobacz [Urządzenia sieciowe](network-devices.md).

## <a name="device-discovery-integrations"></a>Integracje odnajdowania urządzeń

Aby rozwiązać problem uzyskania wystarczającej widoczności w celu zlokalizowania, zidentyfikowania i zabezpieczenia pełnego spisu wyposażeniaotowego/IOT Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje teraz następujące funkcje integracji:

- **Corelight**: Firma Microsoft współpracuje z firmą Corelight, aby odbierać dane z urządzeń sieciowych corelight. Zapewnia to Microsoft 365 Defender lepszą widoczność działań sieciowych urządzeń niezawiązyanych, w tym komunikacji z innymi urządzeniami niezamanektowymi lub sieciami zewnętrznymi. Aby uzyskać więcej informacji, zobacz [Włączanie integracji danych z programem Corelight](corelight-integration.md).

- **Microsoft Defender for IoT**: Ta integracja łączy możliwości odnajdowania urządzeń firmy Ochrona punktu końcowego w usłudze Microsoft Defender, z bezbłędnym monitorowaniem usługi Microsoft Defender dla IoT, aby zabezpieczyć urządzenia IoT przedsiębiorstwa połączone z siecią IT (na przykład VoIP, Voice over Internet Protocol), drukarki i inteligentne telewizory. Aby uzyskać więcej informacji, zobacz [Włączanie integracji z usługą Microsoft Defender dla IoT](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Ocena luk w zabezpieczeniach wykrytych urządzeń

Luki w zabezpieczeniach i czynniki ryzyka związane z urządzeniami, a także inne odkryte urządzenia w sieci, które nie są niezawiązane, są częścią bieżących przepływów telewizyjnych w ramach "Zabezpieczenia Rekomendacje" i reprezentujących je na stronach encji w portalu.
Wyszukaj zalecenia dotyczące zabezpieczeń związane z SSH, aby znaleźć luki w zabezpieczeniach związane z zabezpieczeniami SSH, które są związane z urządzeniami nieza zarządzaniem i zarządzanymi.

:::image type="content" source="images/1156c82ffadd356ce329d1cf551e806c.png" alt-text="Pulpit nawigacyjny z zaleceniami o zabezpieczeniach" lightbox="images/1156c82ffadd356ce329d1cf551e806c.png":::


## <a name="use-advanced-hunting-on-discovered-devices"></a>Użyj zaawansowanego wyszukiwania na wykrytych urządzeniach

Za pomocą zapytań wyszukiwania zaawansowanego możesz uzyskać widoczność na wykrytych urządzeniach.
Szczegółowe informacje o wykrytych punktach końcowych znajdziesz w tabeli DeviceInfo lub informacje o tych urządzeniach powiązane z siecią w tabeli DeviceNetworkInfo.

:::image type="content" source="images/f48ba1779eddee9872f167453c24e5c9.png" alt-text="Strona zaawansowanego wyszukiwania, na której można używać zapytań" lightbox="images/f48ba1779eddee9872f167453c24e5c9.png":::

Odnajdowanie urządzeń korzysta Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach podłączonych do sieci jako sieciowego źródła danych do atrybutu działań na urządzeniach niewnienych. Oznacza to, że jeśli urządzenie z systemem Ochrona punktu końcowego w usłudze Microsoft Defender jest komunikowane z urządzeniem niewłokim, działania na tym urządzeniu są widoczne na osi czasu oraz w tabeli Zaawansowane chłonie DeviceNetworkEvents.

Nowe zdarzenia są oparte na połączeniach TCP (Transmission Control Protocol) i będą dopasowane do bieżącego schematu DeviceNetworkEvents. Ruch wychodzący TCP do Ochrona punktu końcowego w usłudze Microsoft Defender z urządzenia bez włączonej Ochrona punktu końcowego w usłudze Microsoft Defender włączony.

Dodano również następujące typy akcji:

- ConnectionAttempt — próba nawiązania połączenia TCP (syn)
- ConnectionAcknowledged — potwierdzenie, że połączenie TCP zostało zaakceptowane (syn\ack)

Możesz wypróbować to zapytanie przykładowe:

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie odnajdowania urządzeń](configure-device-discovery.md)
- [Odnajdowanie urządzeń : często zadawane pytania](device-discovery-faq.md)
