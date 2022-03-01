---
title: Badanie i odpowiadanie za pomocą Microsoft 365 Defender
description: Badanie zdarzeń i odpowiadanie na nie za pomocą funkcji Microsoft 365 Defender.
keywords: zdarzenia, alerty, badanie, analizowanie, odpowiedź, korelacja, ataki, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberatak
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-incidentresponse
- m365solution-scenario
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: f66f98d8de585d8b92fad50f70ad812b861d9202
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015384"
---
# <a name="investigate-and-respond-with-microsoft-365-defender"></a>Badanie i odpowiadanie za pomocą Microsoft 365 Defender

Poniżej podano podstawowe zadania w celu zbadania i odpowiadania na Microsoft 365 Defender:

- [Reagowanie na zdarzenia](#incident-response)
- [Przegląd i zatwierdzanie automatycznych działań naprawczych](#automated-investigation-and-remediation)
- [Wyszukiwanie znanych zagrożeń w danych](#proactive-search-for-threats-with-advanced-hunting)
- [Opis najnowszych cyberataków](#get-ahead-of-emerging-threats-with-threat-analytics)
- [Uzyskiwanie pomocy](#collaborate-with-microsoft-experts)

## <a name="incident-response"></a>Reagowanie na incydenty

Microsoft 365 i aplikacje tworzą alerty po wykryciu podejrzanych lub złośliwych zdarzeń bądź aktywności. Poszczególne alerty zawierają cenne wskazówki dotyczące ukończonych lub trwających ataków. Jednak zazwyczaj w atakach stosowane są różne techniki wobec różnych typów obiektów, takich jak urządzenia, użytkownicy i skrzynki pocztowe. Wynikiem jest wiele alertów dla wielu obiektów w dzierżawie. Ponieważ wspólne alerty w celu uzyskania wglądu w ataki mogą być trudne i czasochłonne, dlatego Microsoft 365 Defender automatycznie agreguje alerty i skojarzone z nimi informacje w zdarzenie.

Na bieżąco musisz zidentyfikować zdarzenia o najwyższym priorytecie do analizy i rozwiązania w kolejce zdarzeń i przygotować je do reakcji. Jest to kombinacja:

- [Określanie priorytetu](incident-queue.md) zdarzeń o najwyższym priorytecie za pomocą filtrowania i sortowania kolejki zdarzeń. Jest to nazywane również trygoniem.
- [Zarządzanie](manage-incidents.md) zdarzeniami przez zmodyfikowanie ich tytułu, przypisanie ich do analityka, dodanie tagów i komentarzy, a następnie ich klasyfikowanie, gdy zostanie rozwiązane.

W przypadku każdego zdarzenia użyj przepływu pracy reagowania na incydenty, aby przeanalizować zdarzenie, jego alerty i dane w celu przeanalizowania ataków, ochrony przed zagrożeniami, odzyskania go i uczenia się na jego temat. Zobacz [ten przykład dla](incidents-overview.md#example-incident-response-workflow-for-microsoft-365-defender) Microsoft 365 Defender.

## <a name="automated-investigation-and-remediation"></a>Zautomatyzowane badanie i rozwiązywanie problemów

Jeśli Twoja organizacja używa programu Microsoft 365 Defender, zespół operacji zabezpieczeń otrzymuje w portalu programu Microsoft 365 Defender alert w przypadku wykrycia złośliwego lub podejrzanego działania lub artefaktu. Mając na względzie niekończące się natłok zagrożeń, na które mogą napływać zespoły zabezpieczeń, często twarzą w wyzwanie związane z odpowiedzią na dużą ilość alertów. Na szczęście Microsoft 365 Defender funkcje automatycznego badania i odpowiedzi (AIR), które mogą ułatwić zespołowi ds. bezpieczeństwa wydajniejsze i skuteczniejsze reagowanie na zagrożenia.

Po zakończeniu zautomatyzowanego badania jest osiągany werdykt każdego dowodu zdarzenia. W zależności od werdyktu są identyfikowane akcje naprawcze. W niektórych przypadkach działania naprawcze są podejmowane automatycznie. w innych przypadkach działania naprawcze oczekują na zatwierdzenie przez Centrum Microsoft 365 Defender akcji. 

Aby [uzyskać więcej informacji, zobacz Automatyczne](m365d-autoir.md) badanie i Microsoft 365 Defender w programie.

## <a name="proactive-search-for-threats-with-advanced-hunting"></a>Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania

Nie wystarczy odpowiadać na ataki w ich przypadku. W przypadku rozszerzonych, wielofazowych ataków, takich jak oprogramowanie wymuszające okup, musisz aktywnie wyszukiwać dowód ataku w toku i podjąć działania w celu jego zatrzymania przed jego ukończeniem.

Zaawansowane szukanie to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń Microsoft 365 Defender które umożliwia eksplorowanie nawet 30 dni nieprzetworzonych danych. Możesz proaktywnie przeprowadzać inspekcje zdarzeń w sieci, aby zlokalizować wskaźniki zagrożeń i jednostki. Ten elastyczny dostęp do danych Microsoft 365 Defender umożliwia bezszkodne szkolenie w zakresie poszukiwań zarówno znanych, jak i potencjalnych zagrożeń.

Za pomocą tych samych zapytań wyszukiwania zagrożeń możesz tworzyć niestandardowe reguły wykrywania. Reguły te są uruchamiane automatycznie w celu sprawdzenia, czy są wykrywane i reagować na podejrzewane naruszenie, błędnie skonfigurowane komputery i inne ustalenia.

Aby [uzyskać więcej informacji, zobacz Aktywne wyszukiwanie zagrożeń za](advanced-hunting-overview.md) pomocą zaawansowanego wyszukiwania Microsoft 365 Defender informacji.

## <a name="get-ahead-of-emerging-threats-with-threat-analytics"></a>Wyprzedanie pojawiających się zagrożeń za pomocą analizy zagrożeń

Analiza zagrożeń to funkcja analizy zagrożeń w aplikacji Microsoft 365 Defender, która ma na celu pomóc Twojeowi zespołowi zabezpieczeń w jak najseksowniejszą ochronę przed pojawiającymi się zagrożeniami. Zawiera on szczegółową analizę i informacje dotyczące:

- Aktywne działania podszywają się pod użytkowników i ich kampanie
- Popularne i nowe techniki ataków
- Krytyczne luki w zabezpieczeniach
- Typowe powierzchnie ataków
- Rozpowszechnione złośliwe oprogramowanie

Analiza zagrożeń zawiera również informacje na temat powiązanych zdarzeń i zasobów, na które wpływa Microsoft 365 dzierżawie sieci, dotyczących poszczególnych zidentyfikowanych zagrożeń.

Każda zidentyfikowana zagrożeń zawiera raport analityka, pełną analizę zagrożeń napisanych przez służby bezpieczeństwa firmy Microsoft, którzy na pierwszym planie wykrywają i analizują bezpieczeństwo. Te raporty mogą także dostarczać informacji o tym, jak ataki pojawiają się w Microsoft 365 Defender.

Aby uzyskać więcej informacji, zobacz [Analiza zagrożeń w Microsoft 365 Defender](threat-analytics.md).

## <a name="collaborate-with-microsoft-experts"></a>Współpraca z ekspertami Firmy Microsoft

Microsoft Threat Experts — powiadomienia o atakach kierowanej to usługa zarządzanego chowania pod zagrożeniami. Po zastosowaniu i zaakceptowaniu będziesz otrzymywać powiadomienia o ukierunkowanych atakach od ekspertów do spraw zagrożeń firmy Microsoft, dzięki czemu nie przeoczysz krytycznych zagrożeń dla Twojego środowiska. Te powiadomienia pomogą Chronić punkty końcowe, wiadomości e-mail i tożsamości organizacji. Microsoft Threat Experts — funkcja Eksperci na żądanie pozwala uzyskać porady ekspertów dotyczące zagrożeń, przed którymi stoi Twoja organizacja, oraz możesz zasięgnąć pomocy dotyczącej zagrożeń, przed którymi stoi Twoja organizacja. Jest ona dostępna jako dodatkowa usługa subskrypcji.

Aby uzyskać więcej informacji, [zobacz Microsoft Threat Experts w Microsoft 365 omówienie](/security/mtp/microsoft-threat-experts.md).
