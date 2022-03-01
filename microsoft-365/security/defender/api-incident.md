---
title: Microsoft 365 Defender interfejsów API zdarzeń i typu zasobu zdarzeń
description: Informacje o metodach i właściwościach zasobu Zdarzenia w programie Microsoft 365 Defender
keywords: zdarzenie, zdarzenia, interfejs API
search.product: eADQiWindows 10XVcnh
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: a1a3f119e0aafe75b58df9c2330a950d5ab31ead
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010376"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incidents-resource-type"></a>Microsoft 365 Defender API zdarzeń i typ zasobu zdarzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Zdarzenie [to](incidents-overview.md) zbiór powiązanych alertów, które pomagają opisać atak. Zdarzenia z różnych obiektów w organizacji są automatycznie agregowane według Microsoft 365 Defender. Interfejs API zdarzeń umożliwia programowy dostęp do zdarzeń organizacji i powiązanych alertów.

## <a name="quotas-and-resource-allocation"></a>Przydziały i alokacja zasobów

Możesz poprosić o maksymalnie 50 połączeń na minutę lub 1500 połączeń na godzinę. Każda metoda ma również własne przydziały. Aby uzyskać więcej informacji na temat przydziałów specyficznych dla metody, zobacz odpowiedni artykuł, w którym ojej metody chcesz użyć.

Kod `429` odpowiedzi HTTP oznacza, że osiągnięto przydział według liczby wysłanych żądań lub przydziału czasu bieżącego. Treść odpowiedzi będzie zawierać informacje o czasie, po osiągnięciu limitu przydziału.

## <a name="permissions"></a>Uprawnienia

Interfejs API zdarzeń wymaga różnego rodzaju uprawnień dla każdej z jego metod. Aby uzyskać więcej informacji o wymaganych uprawnieniach, zobacz artykuł odpowiedniej metody.

## <a name="methods"></a>Metody

Metoda | Zwracany typ | Opis
-|-|-
[Lista zdarzeń](api-list-incidents.md) | [Lista zdarzeń](api-incident.md) | Uzyskiwanie listy zdarzeń.
[Aktualizacja zdarzenia](api-update-incidents.md) | [Zdarzenie](api-incident.md) | Zaktualizuj zdarzenie.
[Pobierz zdarzenie](api-get-incident.md) | [Zdarzenie](api-incident.md) | Zajmij się jednym zdarzeniem.

## <a name="request-body-response-and-examples"></a>Treść wniosku, odpowiedź i przykłady

Więcej informacji na temat konstruowania żądania lub analizowania odpowiedzi oraz przykładów praktycznych znajdziesz w odpowiednich artykułach dotyczących metod.

## <a name="common-properties"></a>Właściwości wspólne

Właściwość | Wpisać | Opis
-|-|-
incidentId | długo | Unikatowy identyfikator zdarzenia.
redirectIncidentId | null long | Identyfikator zdarzenia, z który zostało scalone bieżące zdarzenie.
nazwa_zdarzenia | ciąg | Nazwa zdarzenia.
createdTime | DateTimeOffset | Data i godzina utworzenia zdarzenia (w czasie UTC).
lastUpdateTime | DateTimeOffset | Data i godzina (w czasie UTC) Ostatnia aktualizacja zdarzenia.
assignedTo | ciąg | Właściciel zdarzenia.
ważność | Wyli roku | Ważność zdarzenia. Dopuszczalne wartości to: ```UnSpecified```, ```Informational```, ```Low```, ```Medium```i ```High```.
stan | Wyli roku | Określa bieżący stan zdarzenia. Dopuszczalne wartości to: ```Active```, ```InProgress```, ```Resolved```i ```Redirected```.
klasyfikacja | Wyli roku | Specyfikacja zdarzenia. Dopuszczalne wartości: ```Unknown```, ```FalsePositive```, ```TruePositive```.
wyznaczanie | Wyli roku | Określa określenie zdarzenia. Dopuszczalne wartości to: ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel``````SecurityTesting```, ```UnwantedSoftware```, . ```Other```
tagi | ciąg Lista | Lista tagów zdarzeń.
komentarze | Lista komentarzy zdarzeń | Obiekt Komentarz zdarzenia zawiera: ciąg komentarza, utworzonyWłaściwą i createTime date time.
alerty | Lista alertów | Lista powiązanych alertów. Zobacz przykłady w [dokumentacji interfejsu API zdarzeń listy](api-list-incidents.md) .

## <a name="related-articles"></a>Artykuły pokrewne

- [Microsoft 365 Defender interfejsów API — omówienie](api-overview.md)
- [Omówienie zdarzeń](incidents-overview.md)
- [Interfejs API zdarzeń listy](api-list-incidents.md)
- [Aktualizowanie interfejsu API zdarzenia](api-update-incidents.md)
