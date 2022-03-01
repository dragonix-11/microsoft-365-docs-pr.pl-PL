---
title: Program Microsoft Defender for Endpoint API informacje o wersji
description: Informacje o wersji dotyczące aktualizacji w zestawie interfejsów API programu Microsoft Defender dla punktów końcowych.
keywords: Microsoft Defender for Endpoint API release notes, mde, API, Microsoft Defender for Endpoint API, updates, notes, release
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
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 2c34add5968021d6a31bffc80ec16e0ebed9baf0
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996892"
---
# <a name="microsoft-defender-for-endpoint-api-release-notes"></a>Program Microsoft Defender for Endpoint API informacje o wersji

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Poniższe informacje zawierają listę aktualizacji interfejsów API programu Microsoft Defender dla punktów końcowych i dat ich zawierania.

> [!TIP]
> Kanał informacyjny RSS: Otrzymuj powiadomienia o aktualizacji tej strony, kopiując i wklejając następujący adres URL do czytnika kanału informacyjnego:
>
> ```http
> /api/search/rss?search=%22Release+notes+for+updates+made+to+the+Microsoft+Defender+for+Endpoint+set+of+APIs%22&locale=en-us&facet=&%24filter=scopes%2Fany%28t%3A+t+eq+%27Windows+10%27%29
> ```

## <a name="release-notes---newest-to-oldest-ddmmyyyy"></a>Informacje o wersji — od najnowszych do najstarszych (dd.mm.yyyy)

### <a name="06102021"></a>06.10.2021

- Dodano nową metodę interfejsu API oceny eksportu — Ocena luk w zabezpieczeniach oprogramowania (odpowiedź _JSON) Eksportowanie metod_ i właściwości oceny eksportu [na urządzenie](get-assessment-methods-properties.md).

### <a name="05252021"></a>05.25.2021

- Dodano nowe metody [i właściwości oceny eksportu interfejsu API na urządzenie](get-assessment-methods-properties.md).

### <a name="03052021"></a>03.05.2021

- Dodano nowy interfejs API: [Metody i właściwości działań naprawczych](get-remediation-methods-properties.md).

### <a name="10022021"></a>10.02.2021

- Dodano nowy interfejs API: [Alerty aktualizacji partii](batch-update-alerts.md).

### <a name="25012021"></a>25.01.2021

- Zaktualizowano ograniczenia stawek [dla zaawansowanego](run-advanced-query-api.md) interfejsu API wyszukiwania z 15 do 45 żądań na minutę.

### <a name="21012021"></a>21.01.2021

- Dodano nowy interfejs API: [Znajdź urządzenia według tagu](machine-tags.md).
- Dodano nowy interfejs API: [Wskaźniki importu](import-ti-indicators.md).

### <a name="03012021"></a>03.01.2021

- Zaktualizowano właściwości argumentu alertu: dodano właściwości ***detectionStatus** _, _*_parentProcessFilePath_*_ i _ *_parentProcessFileName_**.
- [Zaktualizowano encję alertu](alerts.md): dodano ***właściwość nadaną identyfikatorowi***.

### <a name="15122020"></a>15.12.2020

- [Zaktualizowano jednostkę](machine.md) urządzenia: dodano ***listę IpInterfaces***. Zobacz [Lista urządzeń](get-machines.md).

### <a name="04112020"></a>04.11.2020

- Dodano nowy interfejs API: [Ustaw wartość urządzenia](set-device-value.md).
- [Zaktualizowano jednostkę](machine.md) urządzenia: ***dodano właściwość deviceValue***.

### <a name="01092020"></a>01.09.2020

- Dodano opcję rozwijania jednostki Alert z powiązanymi dowódami. Zobacz [Alerty listy](get-alerts.md).
