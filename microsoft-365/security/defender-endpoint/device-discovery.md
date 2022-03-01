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
ms.author: macapara
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
ms.openlocfilehash: 56c7c2ab6a8023be8a570c5b33c64112d8545df1
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019240"
---
# <a name="device-discovery-overview"></a>Omówienie odnajdowania urządzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ochrona środowiska wymaga spisu urządzeń dostępnych w sieci. Jednak urządzenia do mapowania w sieci często mogą być kosztowne, trudne i czasochłonne.

Program Microsoft Defender dla punktu końcowego oferuje funkcję odnajdowania urządzeń, która ułatwia znajdowanie nieza zarządzania urządzeniami połączonymi z siecią firmową bez konieczności obsługi dodatkowych urządzeń czy uciążliwych zmian w procesach. Odnajdowanie urządzeń używa w sieci nowych punktów końcowych do zbierania, skanowania lub skanowania sieci w celu odnalezienia urządzeń niezakierowanych. Funkcja odnajdowania urządzeń umożliwia odnajdowanie:

- Enterprise punktów końcowych (stacji roboczych, serwerów i urządzeń przenośnych), które nie są jeszcze podłączone do programu Microsoft Defender for Endpoint
- Urządzenia sieciowe, takie jak routery i przełączniki
- Urządzenia IoT, takie jak drukarki i kamery

Nieznane i niezakierowane urządzenia mogą stanowić istotne ryzyko dla sieci — niezależnie od tego, czy jest to drukarka bez wysyłki, urządzenia sieciowe z słabymi konfiguracjami zabezpieczeń, czy serwer bez kontroli zabezpieczeń. Po odnalezioniu urządzeń możesz:

- Wdowywają nieza zarządzania punktami końcowymi usługi, zwiększając widoczność zabezpieczeń na tych usługach.
- Zmniejsz powierzchnię ataków, identyfikując i oceniając luki w zabezpieczeniach oraz wykrywając luki w konfiguracji.

Obejrzyj ten klip wideo, aby szybko dowiedzieć się, jak odnajdować urządzenia:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWORdQ]

W połączeniu z tą funkcją, w ramach istniejącego zarządzania zagrożeniami i lukami dostępny jest program Microsoft Defender for Endpoint, czyli zalecenie dotyczące zabezpieczeń.

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

Urządzenia, które zostały odkryte, ale nie zostały jeszcze naniesone i zabezpieczone przez program Microsoft Defender for Endpoint, będą wymienione w spisie urządzeń na karcie Punkty końcowe.

Na liście zapasów urządzeń można użyć filtru o nazwie Stan dołączania, który może mieć dowolną z następujących wartości:

- Onboarded: Punkt końcowy jest dołączany do programu Microsoft Defender for Endpoint.
- Może zostać wnoszony: Punkt końcowy został wykryty w sieci, a system operacyjny został zidentyfikowany jako obsługiwany przez usługę Microsoft Defender for Endpoint, ale obecnie nie jest on dołączany. Zdecydowanie zalecamy dołączanie tych urządzeń.
- Nieobsługiwane: Punkt końcowy został wykryty w sieci, ale nie jest obsługiwany przez program Microsoft Defender for Endpoint.
- Za mało informacji: System nie mógł określić możliwości obsługi urządzenia. Włączenie standardowego odnajdowania na większej liczby urządzeń w sieci może wzbogacić wykryte atrybuty.

![Obraz pulpitu nawigacyjnego spisu urządzeń.](images/2b62255cd3a9dd42f3219e437b956fb9.png)

> [!TIP]
> Zawsze możesz zastosować filtry, aby wykluczyć urządzenia nieza zarządzanie z listy zasobów w spisie urządzeń. Możesz również użyć kolumny stanu dołączania w zapytaniach interfejsu API, aby odfiltrować urządzenia nieza zarządzanie.

## <a name="network-device-discovery"></a>Odnajdowanie urządzeń sieciowych

Duża liczba niezamanektowanych urządzeń sieciowych wdrożonych w organizacji jest dużym obszarem ataków i stanowi istotne ryzyko dla całego przedsiębiorstwa. Program Microsoft Defender for Endpoint, funkcje odnajdowania sieci pomagają zagwarantować, że urządzenia sieciowe zostaną odkryte, dokładnie klasyfikowane i dodane do spisu zasobów.

Urządzenia sieciowe nie są zarządzane jako standardowe punkty końcowe, ponieważ program Defender for Endpoint nie ma wbudowanego czujnika w urządzenia sieciowe. Te typy urządzeń wymagają podejścia bez agenta, w którym skanowanie zdalne uzyska niezbędne informacje z urządzeń. W tym celu w każdym segmencie sieci zostanie użyty wskazany program Microsoft Defender for Endpoint device do wykonywania okresowych uwierzytelnionych skanów wstępnie skonfigurowanych urządzeń sieciowych. Po odkrytiu funkcje łączności usługi Defender for Endpoint Zarządzanie zagrożeniami i lukami zintegrowanych przepływów pracy w celu zabezpieczenia przełączników, routerów, kontrolerów WLAN, zapór i bram VPN.

Aby uzyskać więcej informacji, zobacz [Urządzenia sieciowe](network-devices.md).

## <a name="device-discovery-integrations"></a>Integracje odnajdowania urządzeń

Aby rozwiązać problem uzyskania wystarczającej widoczności w celu zlokalizowania, zidentyfikowania i zabezpieczenia pełnego spisu zasobów usług OT/IOT usługa Microsoft Defender for Endpoint obsługuje teraz następujące funkcje integracji:

- **Corelight**: Firma Microsoft współpracuje z firmą Corelight, aby odbierać dane z urządzeń sieciowych corelight. Zapewnia to Microsoft 365 Defender lepszą widoczność działań sieciowych urządzeń niezawiązyanych, w tym komunikacji z innymi urządzeniami niezamanektowymi lub sieciami zewnętrznymi. Aby uzyskać więcej informacji, zobacz [Włączanie integracji danych z programem Corelight](corelight-integration.md).

- **Microsoft Defender for IoT**: Ta integracja łączy program Microsoft Defender for Endpoint z możliwościami odnajdowania urządzeń i bez agenta usługi Microsoft Defender dla IoT, aby zabezpieczyć urządzenia IoT przedsiębiorstwa połączone z siecią IT (na przykład VoIP, Voice over Internet Protocol), drukarki i inteligentne telewizory. Aby uzyskać więcej informacji, zobacz [Włączanie integracji z usługą Microsoft Defender dla IoT](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Ocena luk w zabezpieczeniach wykrytych urządzeń

Luki w zabezpieczeniach i czynniki ryzyka związane z urządzeniami, a także inne odkryte urządzenia w sieci, które nie są niezawiązane, są częścią bieżących przepływów telewizyjnych w ramach "Zabezpieczenia Rekomendacje" i reprezentujących je na stronach encji w portalu.
Wyszukaj zalecenia dotyczące zabezpieczeń związane z SSH, aby znaleźć luki w zabezpieczeniach związane z zabezpieczeniami SSH, które są związane z urządzeniami nieza zarządzaniem i zarządzanymi.

![Obraz pulpitu nawigacyjnego z zaleceniami zabezpieczeń.](images/1156c82ffadd356ce329d1cf551e806c.png)

## <a name="use-advanced-hunting-on-discovered-devices"></a>Użyj zaawansowanego wyszukiwania na wykrytych urządzeniach

Za pomocą zapytań wyszukiwania zaawansowanego możesz uzyskać widoczność na wykrytych urządzeniach.
Szczegółowe informacje o wykrytych punktach końcowych znajdziesz w tabeli DeviceInfo lub informacje o tych urządzeniach powiązane z siecią w tabeli DeviceNetworkInfo.

![Obraz zaawansowanego wyszukiwania.](images/f48ba1779eddee9872f167453c24e5c9.png)

Odnajdowanie urządzeń korzysta z usługi Microsoft Defender dla urządzeń onboarded Endpoint jako sieciowego źródła danych do atrybutów działań dla urządzeń niewnienych. Oznacza to, że jeśli urządzenie w onboarded programu Microsoft Defender for Endpoint jest komunikowane z urządzeniem niewłokim, działania na urządzeniu niewłokim są widoczne na osi czasu i w tabeli Zaawansowane chłonie DeviceNetworkEvents.

Nowe zdarzenia są oparte na połączeniach TCP (Transmission Control Protocol) i będą dopasowane do bieżącego schematu DeviceNetworkEvents. Ruch tcp do urządzenia z włączonym programem Microsoft Defender dla punktu końcowego z urządzeń innych niż Program Microsoft Defender dla punktu końcowego włączonego.

Dodano również następujące typy akcji:

- ConnectionAttempt — próba nawiązania połączenia TCP (syn)
- ConnectionAcknowledged — potwierdzenie, że połączenie TCP zostało zaakceptowane (syn\ack)

Możesz wypróbować to zapytanie przykładowe:

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="changed-behavior"></a>Zmieniono zachowanie

W poniższej sekcji wymieniono zmiany, które będą obserwować w programie Microsoft Defender dla punktu końcowego i Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu</a> po włączeniu tej funkcji.

1. Urządzenia, które nie są podłączone do programu Microsoft Defender for Endpoint, powinny być widoczne w spisie urządzeń, zapytaniach zaawansowanego wyszukiwania i zapytaniach interfejsu API. Może to znacząco zwiększyć rozmiar wyników zapytania.
    1. Tabele "DeviceInfo" i "DeviceNetworkInfo" w zaawansowanej chwycenią teraz urządzenie odnalezione. Te urządzenia można filtrować przy użyciu atrybutu "OnboardingStatus".
    2. Urządzenia odnalezione powinny być widoczne w wynikach zapytania interfejsu API przesyłania strumieniowego. Te urządzenia można filtrować przy użyciu filtru `OnboardingStatus` w zapytaniu.
2. Urządzenia niezamaniowane zostaną przypisane do istniejących grup urządzeń na podstawie zdefiniowanych kryteriów.
3. W rzadkich przypadkach funkcja odnajdowania standardowego może wyzwalać alerty na monitorach sieciowych lub narzędziach zabezpieczeń. Jeśli wystąpią takie zdarzenia, prosimy o opinie, aby zapobiec powtarzaniu się tych problemów. Możesz jawnie wykluczyć określone cele lub całe podsieci z aktywnego wykrywania standardowego.

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie odnajdowania urządzeń](configure-device-discovery.md)
- [Odnajdowanie urządzeń : często zadawane pytania](device-discovery-faq.md)
