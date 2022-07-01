---
title: Badanie i reagowanie za pomocą Microsoft 365 Defender
description: Badanie zdarzeń i reagowanie na nie przy użyciu funkcji Microsoft 365 Defender.
keywords: zdarzenia, alerty, badanie, analizowanie, reagowanie, korelacja, atak, maszyny, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, e-mail, 365, microsoft, m365, reagowanie na zdarzenia, cyberatak
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-incidentresponse
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: a919e8893fff0486d7a9a3eb89be1822a73ce437
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603555"
---
# <a name="investigate-and-respond-with-microsoft-365-defender"></a>Badanie i reagowanie za pomocą Microsoft 365 Defender

Poniżej przedstawiono podstawowe zadania badania i reagowania dla Microsoft 365 Defender:

- [Reagowanie na zdarzenia](#incident-response)
- [Przeglądanie i zatwierdzanie akcji automatycznego korygowania](#automated-investigation-and-remediation)
- [Wyszukiwanie znanych zagrożeń w danych](#proactive-search-for-threats-with-advanced-hunting)
- [Omówienie najnowszych cyberataków](#get-ahead-of-emerging-threats-with-threat-analytics)
- [Uzyskiwanie pomocy](#collaborate-with-microsoft-experts)

## <a name="incident-response"></a>Reagowanie na zdarzenia

Usługi i aplikacje platformy Microsoft 365 tworzą alerty po wykryciu podejrzanego lub złośliwego zdarzenia lub działania. Poszczególne alerty dostarczają cennych wskazówek dotyczących zakończonego lub trwającego ataku. Jednak ataki zwykle stosują różne techniki względem różnych typów jednostek, takich jak urządzenia, użytkownicy i skrzynki pocztowe. Wynikiem jest wiele alertów dla wielu jednostek w dzierżawie. Ponieważ łączenie poszczególnych alertów w celu uzyskania wglądu w atak może być trudne i czasochłonne, Microsoft 365 Defender automatycznie agreguje alerty i skojarzone z nimi informacje w zdarzeniu.

Na bieżąco należy zidentyfikować zdarzenia o najwyższym priorytecie do analizy i rozwiązania w kolejce zdarzeń i przygotować je do odpowiedzi. Jest to kombinacja następujących elementów:

- [Priorytetyzowanie](incident-queue.md) do określania zdarzeń o najwyższym priorytecie poprzez filtrowanie i sortowanie kolejki zdarzeń. Jest to również nazywane klasyfikacją.
- [Zarządzanie zdarzeniami](manage-incidents.md) przez modyfikowanie ich tytułu, przypisywanie ich do analityka, dodawanie tagów i komentarzy oraz po ich rozwiązaniu, klasyfikowanie ich.

W przypadku każdego zdarzenia użyj przepływu pracy reagowania na zdarzenia, aby przeanalizować zdarzenie oraz jego alerty i dane, aby powstrzymać atak, wyeliminować zagrożenie, odzyskać sprawę po ataku i wyciągnąć z niego wnioski. Zobacz [ten przykład](incidents-overview.md#example-incident-response-workflow-for-microsoft-365-defender), aby uzyskać Microsoft 365 Defender.

## <a name="automated-investigation-and-remediation"></a>Zautomatyzowane badanie i korygowanie

Jeśli Organizacja używa Microsoft 365 Defender, twój zespół ds. operacji zabezpieczeń otrzymuje alert w portalu Microsoft 365 Defender za każdym razem, gdy zostanie wykryte złośliwe lub podejrzane działanie lub artefakt. Biorąc pod uwagę niekończący się przepływ zagrożeń, które mogą wystąpić, zespoły ds. zabezpieczeń często stoją przed wyzwaniem rozwiązania problemu dużej liczby alertów. Na szczęście Microsoft 365 Defender obejmuje funkcje zautomatyzowanego badania i reagowania (AIR), które mogą pomóc zespołowi ds. operacji zabezpieczeń w wydajniejszym i wydajniejszym reagowaniu na zagrożenia.

Po zakończeniu zautomatyzowanego dochodzenia zostaje osiągnięty werdykt dla każdego dowodu zdarzenia. W zależności od werdyktu są identyfikowane akcje korygowania. W niektórych przypadkach akcje korygowania są wykonywane automatycznie; W innych przypadkach akcje korygowania oczekują na zatwierdzenie za pośrednictwem centrum Microsoft 365 Defender Action Center. 

Aby uzyskać więcej informacji, zobacz [Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender](m365d-autoir.md).

## <a name="proactive-search-for-threats-with-advanced-hunting"></a>Proaktywne wyszukiwanie zagrożeń z zaawansowanym wyszukiwaniem zagrożeń

Nie wystarczy reagować na ataki w miarę ich występowania. W przypadku rozszerzonych, wielofazowych ataków, takich jak oprogramowanie wymuszające okup, należy aktywnie wyszukiwać dowody na atak w toku i podjąć działania, aby go zatrzymać przed jego zakończeniem.

Zaawansowane wyszukiwanie zagrożeń to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń w Microsoft 365 Defender, które umożliwia eksplorowanie nieprzetworzonych danych przez maksymalnie 30 dni. Możesz proaktywnie sprawdzać zdarzenia w sieci, aby zlokalizować wskaźniki zagrożeń i jednostki. Ten elastyczny dostęp do danych Microsoft 365 Defender umożliwia nieograniczone wyszukiwanie zagrożeń zarówno w przypadku znanych, jak i potencjalnych zagrożeń.

Możesz użyć tych samych zapytań wyszukiwania zagrożeń, aby utworzyć niestandardowe reguły wykrywania. Te reguły są uruchamiane automatycznie w celu sprawdzania, a następnie reagowania na podejrzenie naruszenia zabezpieczeń, nieprawidłowo skonfigurowane maszyny i inne ustalenia.

Aby uzyskać więcej informacji[, zobacz Proaktywne wyszukiwanie zagrożeń z zaawansowanym wyszukiwaniem zagrożeń w Microsoft 365 Defender](advanced-hunting-overview.md).

## <a name="get-ahead-of-emerging-threats-with-threat-analytics"></a>Wyprzedzanie pojawiających się zagrożeń za pomocą analizy zagrożeń

Analiza zagrożeń to funkcja analizy zagrożeń w Microsoft 365 Defender zaprojektowana tak, aby pomóc zespołowi ds. zabezpieczeń być jak najbardziej wydajnym w obliczu pojawiających się zagrożeń. Zawiera ona szczegółową analizę i informacje na temat:

- Aktywni aktorzy zagrożeń i ich kampanie
- Popularne i nowe techniki ataków
- Krytyczne luki w zabezpieczeniach
- Typowe powierzchnie ataków
- Powszechnie stosowane złośliwe oprogramowanie

Analiza zagrożeń zawiera również informacje o powiązanych zdarzeniach i zasobach, których dotyczy problem, w ramach dzierżawy usługi Microsoft 365 dla każdego zidentyfikowanego zagrożenia.

Każde zidentyfikowane zagrożenie obejmuje raport analityków, kompleksową analizę zagrożenia napisaną przez badaczy zabezpieczeń firmy Microsoft, którzy są w czołówce wykrywania i analizy cyberbezpieczeństwa. Te raporty mogą również dostarczać informacji na temat sposobu, w jaki ataki pojawiają się w Microsoft 365 Defender.

Aby uzyskać więcej informacji, zobacz [Analiza zagrożeń w Microsoft 365 Defender](threat-analytics.md).

## <a name="collaborate-with-microsoft-experts"></a>Współpraca z ekspertami firmy Microsoft

Microsoft Threat Experts — docelowe powiadomienia o atakach to zarządzana usługa wyszukiwania zagrożeń. Po zastosowaniu i zaakceptowaniu otrzymasz powiadomienia o ukierunkowanych atakach od ekspertów firmy Microsoft w zakresie zagrożeń, dzięki czemu nie przegapisz krytycznych zagrożeń dla środowiska. Te powiadomienia pomogą Ci chronić punkty końcowe, pocztę e-mail i tożsamości organizacji. Microsoft Threat Experts — eksperci na żądanie pozwalają uzyskać specjalistyczne porady dotyczące zagrożeń, z którymi boryka się Twoja organizacja, i możesz skontaktować się z pomocą w zakresie zagrożeń, z którymi boryka się Twoja organizacja. Jest ona dostępna jako dodatkowa usługa subskrypcji.

Aby uzyskać więcej informacji, zobacz [Microsoft Threat Experts na platformie Microsoft 365 — omówienie](/microsoft-365/security/defender/microsoft-threat-experts).
