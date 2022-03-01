---
title: Etap 4 wdrażania reguł asr — operacyjne
description: Zapewnia wskazówki dotyczące wdrażania reguł ograniczania powierzchni ataków.
keywords: Wdrażanie reguł ograniczania powierzchni ataków, wdrażanie ASR, włączanie reguł asr, konfigurowanie funkcji asr, systemu ochrony przed nieuprawnianiem hosta, reguł ochrony, reguł ochrony przed wykorzystywaniem luk, ochrony przed wykorzystywaniem, regułami wykorzystania luk, regułami zapobiegania powstawaniu przed wirusami, program Microsoft Defender for Endpoint, konfigurowanie reguł asr
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: b668519b84037000610fa3fe76ec5462b9657b3d
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63013766"
---
# <a name="asr-rules-deployment-phase-4-operationalize"></a>Etap 4 wdrażania reguł asr: operacyjne

Po pełnym wdrożeniu reguł asr należy mieć procesy monitorowania działań związanych z asr i reagowania na nie.

## <a name="manage-false-positives"></a>Zarządzanie wynikami fałszywie dodatnimi

Wyniki fałszywie dodatnie/ujemne mogą występować w przypadku każdego rozwiązania ochrony przed zagrożeniami. Wyniki fałszywie dodatnie to przypadki, w których jednostka (taka jak plik lub proces) jest wykrywana i oznaczana jako złośliwa, chociaż w rzeczywistości nie jest to zagrożenie. Natomiast fałszywa wartość ujemna to jednostka, która nie została wykryta jako zagrożenie, ale jest złośliwa. Aby uzyskać więcej informacji na temat wyników fałszywie dodatnich i ujemnych, zobacz: Adres wyników fałszywie dodatnich/ujemnych w [programie Microsoft Defender dla punktu końcowego](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>Śledzenie raportów

Spójny, regularny przegląd raportów to podstawowy aspekt utrzymywania wdrożenia reguł asr i utrzymywania na bieżąco nowo pojawiających się zagrożeń. Organizacja powinna z harmonogramem przeglądać zdarzenia reguł asr z zachowaniem harmonogramu, który będzie na bieżąco informował o zdarzeniach zgłoszonych przez regułę ASR. W zależności od wielkości organizacji recenzje mogą być codzienne, co godzinę lub ciągłe monitorowanie.

## <a name="hunting"></a>Goniące

Jedną z najbardziej zaawansowanych funkcji programu [Microsoft 365 Defender](https://security.microsoft.com) jest zaawansowane szukanie. Jeśli nie wiesz, jak działa zaawansowane szukanie, zobacz: Aktywne wyszukiwanie zagrożeń za pomocą [zaawansowanego wyszukiwania](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender zaawansowanego chłonia](images/asr-defender365-advanced-hunting2.png)

Zaawansowane wyszukiwanie to oparte na zapytaniach (Język Kusto Query) narzędzie do wyszukiwania zagrożeń, które pozwala eksplorować nawet 30 dni przechwyconych (nieprzetworzonych) danych zbieranych przez program Microsoft Defender ATP Endpoint Detection and Response (EDR) ze wszystkich Twoich komputerów. W ramach zaawansowanego wyszukiwania możesz aktywnie sprawdzać zdarzenia, aby znaleźć interesujące wskaźniki i jednostki. Elastyczny dostęp do danych ułatwia niezaszkolone polunie zarówno w przypadku znanych, jak i potencjalnych zagrożeń.

Dzięki zaawansowanej czacie można wyodrębniać informacje reguł ASR, tworzyć raporty i uzyskać szczegółowe informacje na temat kontekstu danej inspekcji reguły asr lub blokowania zdarzenia.

 Możesz zapytanie dotyczące reguł ASR z tabeli DeviceEvents w sekcji zaawansowanego wyszukiwania w portalu Microsoft 365 Defender pracy. Na przykład proste zapytanie, takie jak poniższe, może raportować wszystkie zdarzenia, dla których jako źródło danych są używane reguły ASR z ostatnich 30 dni i podsumowuje je przez liczbę Akcji, że w tym przypadku będzie to rzeczywista nazwa kodowa reguły ASR.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender wiersza polecenia Zaawansowane zapytanie wyszukiwania](images/asr-defender365-advanced-hunting3.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender zaawansowane wyniki wyszukiwania](images/asr-defender365-advanced-hunting4.png)

Powyższe pokazuje, że zarejestrowano 187 zdarzeń dla ciągu AsrLsassCredentialTheft:

- 102 dla zablokowane
- 85 dla inspekcji
- 2 zdarzenia dla asrOfficeChildProcess (1 dla inspekcji i 1 dla bloku)
- 8 zdarzeń dla asrPsexecWmichildProcessAudited

Jeśli chcesz skoncentrować się na  regułach AsrOfficeChildProcess i uzyskać szczegółowe informacje na temat rzeczywistych plików i procesów, w których jest to działanie, zmień filtr dla typu Akcji i zastąp linię podsumowania projekcją poszukiwanych pól (w tym przypadku są to pola DeviceName, FileName, FolderPath itp.).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender zaawansowane zapytanie wyszukiwania](images/asr-defender365-advanced-hunting4b.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender wyników wyszukiwania zaawansowanego](images/asr-defender365-advanced-hunting5b.png)

Prawdziwą zaletą zaawansowanego wyszukiwania jest możliwość kształtowania zapytań do swoich potrzeb. Dzięki kształtowaniu zapytania można zobaczyć dokładną historię tego, co się działo, niezależnie od tego, czy chcesz przypiąć coś na poszczególnych komputerach, czy wyodrębnić wnioski z całego środowiska.

Aby uzyskać więcej informacji na temat opcji wyszukiwania, zobacz: [Reguły ograniczania powierzchni ataków bez zapadów — część 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968).

## <a name="topics-in-this-deployment-collection"></a>Tematy z tego zbioru wdrożeń

[Omówienie wdrażania reguł asr](attack-surface-reduction-rules-deployment.md)

[Etap 1. Planowanie](attack-surface-reduction-rules-deployment-phase-1.md)

[Etap 2. Testowanie](attack-surface-reduction-rules-deployment-phase-2.md)

[Etap 4. Operacyjne](attack-surface-reduction-rules-deployment-phase-4.md)
