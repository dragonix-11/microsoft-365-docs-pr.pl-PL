---
title: Operacjonalizuj reguły zmniejszania obszaru podatnego na ataki
description: Zawiera wskazówki dotyczące operacjonalizacji wdrożenia reguł zmniejszania obszaru ataków.
keywords: Wdrażanie reguł zmniejszania obszaru ataków, wdrażanie usługi ASR, włączanie reguł asr, konfigurowanie usługi ASR, system zapobiegania włamaniom do hostów, reguły ochrony, reguły ochrony przed lukami w zabezpieczeniach, reguły antyeksploatowania, reguły wykorzystujące luki w zabezpieczeniach, reguły zapobiegania zakażeniom, Ochrona punktu końcowego w usłudze Microsoft Defender, konfigurowanie reguł usługi ASR
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
ms.collection:
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 708d929376c029ba5ce448c93fd6c455a78ebec8
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602883"
---
# <a name="operationalize-attack-surface-reduction-asr-rules"></a>Operacjonalizuj reguły zmniejszania obszaru podatnego na ataki

Po w pełni wdrożonych regułach zmniejszania obszaru ataków (ASR) ważne jest, aby wdrożono procesy monitorowania działań związanych z usługą ASR i reagowania na nie.

## <a name="managing-false-positives"></a>Zarządzanie wynikami fałszywie dodatnimi

Wyniki fałszywie dodatnie/ujemne mogą wystąpić w przypadku dowolnego rozwiązania ochrony przed zagrożeniami. Wyniki fałszywie dodatnie to przypadki, w których jednostka (na przykład plik lub proces) jest wykrywana i identyfikowana jako złośliwa, chociaż jednostka w rzeczywistości nie stanowi zagrożenia. Natomiast wartość fałszywie ujemna to jednostka, która nie została wykryta jako zagrożenie, ale jest złośliwa. Aby uzyskać więcej informacji na temat wyników fałszywie dodatnich i fałszywie ujemnych, zobacz: [Address false positives/negatives in Ochrona punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>Nadążanie za raportami

Spójny, regularny przegląd raportów jest istotnym aspektem utrzymania wdrożenia reguł usługi ASR i na bieżąco z nowo pojawiającym się zagrożeniami. Organizacja powinna mieć zaplanowane przeglądy zdarzeń reguł usługi ASR w okresie, który będzie na bieżąco z zdarzeniami raportowanymi przez reguły usługi ASR. W zależności od rozmiaru organizacji przeglądy mogą być monitorowane codziennie, co godzinę lub w sposób ciągły.

## <a name="hunting"></a>Polowanie

Jedną z najpotężniejszych cech [Microsoft 365 Defender](https://security.microsoft.com) jest zaawansowane wyszukiwanie zagrożeń. Jeśli nie znasz zaawansowanych zagrożeń, zobacz: [Proaktywne wyszukiwanie zagrożeń z zaawansowanym wyszukiwaniem zagrożeń](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting2.png" alt-text="Strona Zaawansowane wyszukiwanie zagrożeń w portalu Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting2.png":::

Zaawansowane wyszukiwanie zagrożeń to oparte na zapytaniach (język zapytań Kusto) narzędzie do wyszukiwania zagrożeń, które umożliwia eksplorowanie do 30 dni przechwyconych (nieprzetworzonych) danych zbieranych przez program Microsoft Defender ATP Endpoint Detection and Response (EDR) ze wszystkich maszyn. Dzięki zaawansowanemu polowaniu można proaktywnie sprawdzać zdarzenia w celu zlokalizowania interesujących wskaźników i jednostek. Elastyczny dostęp do danych ułatwia nieograniczone wyszukiwanie zagrożeń zarówno w przypadku znanych, jak i potencjalnych zagrożeń.

Dzięki zaawansowanemu polowaniu można wyodrębnić informacje o regułach usługi ASR, utworzyć raporty i uzyskać szczegółowe informacje na temat kontekstu danego inspekcji reguły usługi ASR lub zdarzenia bloku.

 Zdarzenia reguł usługi ASR można wykonywać z tabeli DeviceEvents w sekcji zaawansowanego wyszukiwania zagrożeń w portalu Microsoft 365 Defender. Na przykład proste zapytanie, takie jak poniższe, może zgłaszać wszystkie zdarzenia, które mają reguły usługi ASR jako źródło danych, w ciągu ostatnich 30 dni i podsumowywać je według liczby actiontype, że w tym przypadku będzie to rzeczywista nazwa kodowa reguły ASR.

Zdarzenia usługi ASR wyświetlane w portalu wyszukiwania zagrożeń są ograniczane do unikatowych procesów obserwowanych co godzinę. Czas zdarzenia ASR to pierwszy raz, gdy zdarzenie jest widoczne w ciągu tej godziny.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting3.png" alt-text="Wiersz polecenia Zaawansowane zapytanie wyszukiwania zagrożeń w portalu Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting3.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4.png" alt-text="Zaawansowane zapytanie dotyczące wyszukiwania zagrożeń w portalu Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting4.png":::

Powyższe pokazuje, że zarejestrowano 187 zdarzeń dla asrLsassCredentialTheft:

- 102 dla zablokowanej
- 85 dla poddawanych inspekcji
- 2 zdarzenia dla asrOfficeChildProcess (1 dla inspekcji i 1 dla bloku)
- 8 zdarzeń dla asrPsexecWmiChildProcessAudited

Jeśli chcesz skupić się na regule AsrOfficeChildProcess i uzyskać szczegółowe informacje na temat rzeczywistych plików i procesów, zmień filtr actiontype i zastąp wiersz podsumowania projekcją żądanych pól (w tym przypadku są to DeviceName, FileName, FolderPath itp.).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4b.png" alt-text="Przykład zaawansowanego wyszukiwania zagrożeń w portalu Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting4b.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting5b.png" alt-text="Zaawansowane zapytanie wyszukiwania zagrożeń koncentruje wyniki w portalu Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting5b.png":::

Prawdziwą zaletą zaawansowanego wyszukiwania zagrożeń jest możliwość kształtowania zapytań zgodnie z potrzebami. Kształtując zapytanie, możesz zobaczyć dokładną historię tego, co się dzieje, niezależnie od tego, czy chcesz wskazać coś na poszczególnych maszynach, czy chcesz wyodrębnić szczegółowe informacje z całego środowiska.

Aby uzyskać więcej informacji na temat opcji wyszukiwania zagrożeń, zobacz: [Demistyfikacja reguł zmniejszania obszaru podatnego na ataki — część 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968).

## <a name="topics-in-this-deployment-collection"></a>Tematy w tej kolekcji wdrożeń

[Omówienie wdrażania reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment.md)

[Zaplanuj wdrażanie reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[Przetestuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-test.md)

[Włącz reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-implement.md)

[Odwołuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md)
