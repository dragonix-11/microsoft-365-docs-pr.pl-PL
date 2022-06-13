---
title: Krok nr 5. Opracowywanie i testowanie przypadków użycia
description: Podstawy tworzenia i testowania przypadków użycia podczas integrowania Microsoft 365 Defender z operacjami zabezpieczeń.
keywords: zdarzenia, alerty, badanie, korelacja, atak, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, adres e-mail, 365, microsoft, m365, reagowanie na zdarzenia, cyberatak, secops, operacje zabezpieczeń, soc
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
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: a039239545a5442592fe1a07f840cf75bebb0eca
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012951"
---
# <a name="step-5-develop-and-test-use-cases"></a>Krok nr 5. Opracowywanie i testowanie przypadków użycia

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Zalecane metody wdrażania Microsoft 365 Defender w centrum operacji zabezpieczeń (SOC) zależą od bieżącego zestawu narzędzi, procesów i zestawów umiejętności zespołu SOC. Utrzymanie higieny cybernetycznej na różnych platformach może być trudne ze względu na ogromną ilość danych pochodzących z dziesiątek, jeśli nie setek źródeł bezpieczeństwa.

Narzędzia zabezpieczeń są ze sobą powiązane. Włączenie jednej funkcji w technologii zabezpieczeń lub zmiana procesu może z kolei złamać inną. Z tego powodu firma Microsoft zaleca zespołowi SOC sformalizowanie metody definiowania i określania priorytetów przypadków użycia. Przypadki użycia ułatwiają definiowanie wymagań i procesów testowych dla operacji SOC w różnych zespołach. Tworzy metodologię przechwytywania metryk w celu określenia, czy odpowiednie role i kombinacja zadań są dopasowane do odpowiedniego zespołu z odpowiednimi zestawami umiejętności.

## <a name="develop-and-formalize-use-case-process"></a>Opracowywanie i formalizowanie procesu przypadków użycia

SOC powinna zdefiniować wysoki poziom standardu i proces opracowywania przypadków użycia, który byłby regulowany przez zespół nadzoru SOC. Zespół nadzoru SOC powinien współpracować z Twoją firmą, działem IT, działem prawnym, kadrą i innymi grupami, aby ustalić priorytet przypadków użycia soc, które ostatecznie trafią do elementów runbook i podręczników zespołu SOC. Priorytetowe przypadki użycia są oparte na celach, takich jak zgodność lub prywatność.

Działania związane z nadzorem SOC związane z opracowywaniem przypadków użycia obejmują:

- Wymagania
- Potrzeby kadrowe lub szkoleniowe
- Licencje na oprogramowanie
- Kontraktowanie dostawcy
- Zarządzanie planem
- Obsługa rejestru przypadków użycia
- Obsługa/aktualizowanie szablonów

Aby ułatwić procesy tworzenia elementów runbook i podręczników, utwórz drzewo decyzyjne przypadków użycia. Na tej ilustracji przedstawiono przykład.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png" alt-text="Proces podejmowania decyzji w sprawie użycia" lightbox="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png":::

Po zdefiniowaniu i zatwierdzeniu standardowego przypadku użycia wysokiego poziomu następnym krokiem jest utworzenie i przetestowanie rzeczywistego przypadku użycia. W poniższych sekcjach użyto scenariuszy ochrony przed wyłudzaniem informacji i zagrożeń oraz skanowania luk w zabezpieczeniach jako przykładów.

## <a name="use-case-example-1-new-phishing-variant"></a>Przykład przypadku użycia 1: nowy wariant wyłudzania informacji

Pierwszym krokiem tworzenia przypadku użycia jest przedstawienie przepływu pracy przy użyciu tablicy scenariuszy. Oto przykład tablicy historii wysokiego poziomu dla nowego powiadomienia o wyłudzaniu informacji dla zespołu analizy zagrożeń.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png" alt-text="Przepływ pracy przypadku użycia kampanii chroniącej przed wyłudzaniem informacji" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png":::

### <a name="invoke-the-use-case-workflow-for-example-1"></a>Wywołaj przepływ pracy przypadku użycia, na przykład 1

Po zatwierdzeniu tablicy scenariuszy następnym krokiem jest wywołanie przepływu pracy przypadku użycia. Oto przykładowy proces kampanii chroniącej przed wyłudzaniem informacji.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png" alt-text="Szczegółowy przepływ pracy przypadków użycia dla kampanii chroniącej przed wyłudzaniem informacji" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png":::

## <a name="use-case-example-2-threat-and-vulnerability-scanning"></a>Przykład przypadku użycia 2: skanowanie zagrożeń i luk w zabezpieczeniach

Innym scenariuszem, w którym można użyć przypadku użycia, jest skanowanie zagrożeń i luk w zabezpieczeniach. W tym przykładzie soc wymaga, aby zagrożenia i luki w zabezpieczeniach były korygowane względem zasobów za pośrednictwem zatwierdzonych procesów, które obejmują skanowanie zasobów.

Oto przykładowa scenorys wysokiego poziomu dla Zarządzanie zagrożeniami i lukami zasobów.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png" alt-text="Przepływ pracy przypadku użycia dla Zarządzanie zagrożeniami i lukami" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png":::

### <a name="invoke-the-use-case-workflow-for-example-2"></a>Wywołaj przepływ pracy przypadku użycia, na przykład 2

Oto przykładowy proces skanowania zagrożeń i luk w zabezpieczeniach.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png" alt-text="Szczegółowy przepływ pracy przypadków użycia dla Zarządzanie zagrożeniami i lukami" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png":::

### <a name="analyze-the-use-case-output-and-lessons-learned"></a>Analizowanie danych wyjściowych przypadków użycia i wyciągniętych wniosków

Po zatwierdzeniu i przetestowaniu przypadku użycia należy zidentyfikować luki między zespołami ds. zabezpieczeń wraz z osobami, procesami i zaangażowanymi technologiami Microsoft 365 Defender. Microsoft 365 Defender technologie powinny być analizowane w celu określenia, czy są w stanie osiągnąć pożądane wyniki. Można je śledzić za pomocą listy kontrolnej lub macierzy.

Na przykład w przykładzie scenariusza ochrony przed wyłudzaniem informacji zespoły SOC mogły wprowadzić odkrycia w tej tabeli.

|Zespół SOC|Wymóg|Osoby spełniające wymagania|Proces spełniający wymagania|Odpowiednia technologia|Zidentyfikowano lukę|Dziennik zmian przypadków użycia|Wykluczenie (Y/N)|
|---|---|---|---|---|---|---|---|
|Zespół ds. analizy zagrożeń i analizy|Źródła danych prawidłowo zasilają aparaty analizy zagrożeń.|Analityk/inżynier analizy zagrożeń|Ustanowione wymagania dotyczące źródła danych, wyzwalacze analizy zagrożeń z zatwierdzonych źródeł|Microsoft Defender for Identity, Ochrona punktu końcowego w usłudze Microsoft Defender|Zespół analizy zagrożeń nie używał skryptu automatyzacji do łączenia interfejsu API Microsoft 365 Defender z aparatami intel zagrożeń|Dodawanie Microsoft 365 Defender jako źródeł danych do aparatów zagrożeń <p> Aktualizowanie książki przebiegu przypadku użycia|N|
|Zespół ds. monitorowania|Źródła danych prawidłowo podają pulpity nawigacyjne monitorowania|Alerty & monitorowania & warstwy 1,2 SOC|Przepływ pracy raportowania wskaźnika bezpieczeństwa centrum zgodności & zabezpieczeń|[Alerty w Centrum zgodności & zabezpieczeń](/microsoft-365/security/office-365-security/alerts) <p> Monitorowanie wskaźnika bezpieczeństwa|Brak mechanizmu zgłaszania przez analityków SOC pomyślnego wykrywania nowych wariantów wyłudzania informacji w celu poprawy wskaźnika bezpieczeństwa <p> [Wyświetlanie raportów zabezpieczeń poczty e-mail w portalu Microsoft 365 Defender](/microsoft-365/security/office-365-security/view-email-security-reports)|Dodawanie procesu śledzenia poprawy wskaźnika bezpieczeństwa do przepływów pracy raportowania|N|
|Zespół inżynierów i secops|Aktualizacje kontroli zmian są wprowadzane w elementach Runbook zespołu SOC|Inżynier SOC warstwy 2|Procedura powiadamiania o zmianie kontrolki dla elementów Runbook zespołu SOC|Zatwierdzone zmiany w urządzeniach zabezpieczeń|Zmiany Microsoft 365 Defender łączności z technologią zabezpieczeń SOC wymagają zatwierdzenia|Dodaj Microsoft Defender for Cloud Apps, Defender for Identity, Defender for Endpoint, Security & Compliance Center do elementów runbook SOC|T|

Ponadto zespoły SOC mogły wykonać odkrycia opisane w poniższej tabeli w odniesieniu do scenariusza Zarządzanie zagrożeniami i lukami opisanego powyżej:

|Zespół SOC|Wymóg|Osoby spełniające wymagania|Proces spełniający wymagania|Odpowiednia technologia|Zidentyfikowano lukę|Dziennik zmian przypadków użycia|Wykluczenie (Y/N)|
|---|---|---|---|---|---|---|---|
|Nadzór SOC|Wszystkie zasoby połączone z zatwierdzonymi sieciami są identyfikowane i kategoryzowane|Nadzór SOC, właściciele BU, właściciele aplikacji, właściciele zasobów IT itp.|Scentralizowany system zarządzania zasobami umożliwiający odnajdywanie i wyświetlanie listy kategorii i atrybutów zasobów na podstawie ryzyka.|ServiceNow lub inne zasoby. <br><br>[spis urządzeń Microsoft 365](/microsoft-365/security/defender-endpoint/device-discovery)|Odnaleziono tylko 70% zasobów. Microsoft 365 Defender śledzenie korygowania obowiązujące tylko w przypadku znanych zasobów|Dojrzałe usługi zarządzania cyklem życia zasobów w celu zapewnienia, że Microsoft 365 Defender ma 100% pokrycia|N|
|Inżynieria & SecOps Teams|Wysoki wpływ i krytyczne luki w zabezpieczeniach zasobów są korygowane zgodnie z zasadami|Inżynierowie secOps, analitycy SOC: luka w zabezpieczeniach & zgodności, inżynieria zabezpieczeń|Zdefiniowany proces kategoryzowania luk w zabezpieczeniach wysokiego ryzyka i krytycznych|[Pulpity nawigacyjne zarządzania zagrożeniami i lukami w zabezpieczeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)|Usługa Defender for Endpoint zidentyfikowała urządzenia o dużym wpływie i wysokim poziomie alertów bez planu korygowania ani implementacji zalecanego działania firmy Microsoft|Dodaj przepływ pracy do powiadamiania właścicieli zasobów, gdy działanie korygujące jest wymagane w ciągu 30 dni dla zasad; Zaimplementuj system biletów, aby powiadomić właścicieli zasobów o krokach korygowania.|N|
|Monitorowanie Teams|Stan zagrożenia i luki w zabezpieczeniach jest zgłaszany za pośrednictwem firmowego portalu intranetowego|Analityk SOC warstwy 2|Automatycznie generowane raporty z Microsoft 365 Defender pokazujące postęp korygowania zasobów|[Alerty w Centrum zgodności & zabezpieczeń](/microsoft-365/security/office-365-security/alerts) <p> Monitorowanie wskaźnika bezpieczeństwa|Brak widoków ani raportów pulpitu nawigacyjnego przekazywanych właścicielom zasobów dotyczących zagrożeń i stanu luk w zabezpieczeniach zasobów.|Utwórz skrypt automatyzacji, aby wypełnić stan korygowania luk w zabezpieczeniach dotyczących wysokiego ryzyka i krytycznego zasobu w organizacji.|N|

W takich przykładowych przypadkach użycia testy ujawniły kilka luk w wymaganiach zespołu SOC, które zostały ustanowione jako punkty odniesienia dla obowiązków każdego zespołu. Lista kontrolna przypadków użycia może być tak kompleksowa, jak to konieczne, aby upewnić się, że zespół SOC jest przygotowany do integracji Microsoft 365 Defender z nowymi lub istniejącymi wymaganiami SOC. Ponieważ będzie to proces iteracyjny, proces tworzenia przypadków użycia i zawartość wyjściowa przypadku użycia będą naturalnie służyć do aktualizowania i dojrzewania elementów Runbook SOC z wyciągniętymi doświadczeniami.

## <a name="update-production-runbooks-and-playbooks"></a>Aktualizowanie produkcyjnych elementów Runbook i podręczników

Po skorygowaniu wszystkich luk w testach przypadków użycia zebrane w nich wnioski i metryki można włączyć do produkcyjnych elementów Runbook zespołu SOC (procesów operacyjnych) i podręczników (odpowiedzi na zdarzenia i procedury eskalacji).

Konserwację elementów runbook i podręczników zespołu SOC można organizować na wiele sposobów. Każdy zespół SOC może być odpowiedzialny za własne lub może istnieć jedna scentralizowana wersja dla wszystkich zespołów do udostępniania w centralnym repozytorium. Zarządzanie elementami runbook i podręcznikami dla poszczególnych organizacji zależy od rozmiaru, zestawu umiejętności, ról i podziału obowiązków. Po zaktualizowaniu elementu Runbook powinien nastąpić proces aktualizacji podręcznika.

## <a name="use-a-standard-framework-for-escalation"></a>Używanie standardowej struktury na potrzeby eskalacji

Podręczniki to kroki, które zespoły SOC będą musiały wykonać w przypadku wystąpienia rzeczywistego zdarzenia w oparciu o pomyślną integrację i test przypadku użycia. Dlatego konieczne jest, aby SOC przestrzegała sformalizowanego podejścia do reagowania na zdarzenia, takiego jak [NIST Incident Response Standard](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) , który stał się jednym z wiodących standardów branżowych w zakresie reagowania na zdarzenia.

Czteroetapowy proces reagowania na zdarzenia NIST obejmuje cztery fazy:

1. Przygotowanie
2. Wykrywanie i analiza
3. Hermetyzowanie, eliminowanie i odzyskiwanie
4. Działanie po zdarzeniu

### <a name="example-tracking-preparation-phase-activity"></a>Przykład: Śledzenie działania fazy przygotowywania

Jedną z podstawowych podstaw podręcznika eskalacji jest zapewnienie niewielkiej dwuznaczności co do tego, co każdy zespół SOC ma robić przed, w trakcie i po zdarzeniu lub zdarzeniu. W związku z tym dobrym rozwiązaniem jest wyświetlenie listy instrukcji krok po kroku.

Na przykład faza przygotowania może obejmować macierz zadań if/then lub XoR. W przypadku nowego przykładowego przypadku użycia wariantu wyłudzania informacji taka macierz może wyglądać następująco:

|Dlaczego eskalacja jest uzasadniona?|Następny krok|
|---|---|
|Alert w monitorowaniu SOC oceniony jako wyzwalany **krytycznie** > **500/godzinę**|Przejdź do podręcznika A, sekcji 2, działania 5 (z linkiem do sekcji podręcznika)|
|eCommerce zgłosiło potencjalny atak DDoS|Wywoływanie podręcznika B-Sekcja C, Działanie 19 (z linkiem do sekcji podręcznika)|
|Kierownictwo zgłosiło podejrzaną wiadomość e-mail jako próbę wyłudzania informacji|Przejdź do podręcznika 5, sekcji 2, działania 5 (z linkiem do sekcji podręcznika)|

Po wykonaniu fazy przygotowania organizacje powinny wywoływać pozostałe fazy zgodnie z opisem WUS:

- Wykrywanie i analiza
- Hermetyzowanie, eliminowanie i odzyskiwanie
- Działanie po zdarzeniu

## <a name="next-step"></a>Następny krok

[Krok 6. Identyfikowanie zadań konserwacji SOC](integrate-microsoft-365-defender-secops-tasks.md)
