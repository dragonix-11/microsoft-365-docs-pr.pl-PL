---
title: Krok nr 5. Opracuj i testuj przypadki użycia
description: Podstawy opracowywania i testowania przypadków użycia podczas integrowania Microsoft 365 Defender z operacjami zabezpieczeń.
keywords: zdarzenia, alerty, badanie, korelacja, ataki, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberataki, zabezpieczenia, operacje zabezpieczeń, soc
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
ms.openlocfilehash: 6621ca47356f87edd47a905e4edeb592d9b556ff
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499094"
---
# <a name="step-5-develop-and-test-use-cases"></a>Krok nr 5. Opracuj i testuj przypadki użycia

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Zalecane metody wdrażania usługi Microsoft 365 Defender w Centrum zabezpieczeń (SOC, Security Operations Center) zależą od bieżącego zestawu narzędzi, procesów i zestawów umiejętności dostępnych w zespole SOC. Zapewnienie ochrony przed cyberatakami na różnych platformach może być trudne ze względu na ogromną ilość danych pochodzących z dziesiątek, a nawet setek źródeł zabezpieczeń. 

Narzędzia zabezpieczeń są ze sobą powiązane. Włączenie jednej funkcji w technologii zabezpieczeń lub zmiana procesu może spowodować przerwę w pracy drugiej. Z tego powodu firma Microsoft zaleca, aby Twój zespół SOC sformalizować metodę definiowania i ustalania priorytetów przypadków użycia. Przypadki użycia ułatwiają definiowanie wymagań i procesów testowych dla operacji SOC w różnych zespołach. Tworzy metodologię przechwytywania metryk w celu określenia, czy właściwe role i kombinacje zadań są dostosowane do odpowiedniego zespołu za pomocą odpowiednich umiejętności. 

## <a name="develop-and-formalize-use-case-process"></a>Opracowywanie i sformalizowanie procesu przypadków użycia

SoC powinien zdefiniować wysokopoziomowy standard i proces opracowywania spraw użycia, który będzie uregulowany przez zespół soc nadzór. Zespół nadzorcy SOC powinien współpracować z Twoją firmą, IT, prawny, działem kadr i innymi grupami, aby ustalić priorytety przypadków użycia dla SOC, które ostatecznie trafią do podręczników i podręczników zespołu SOC. Priorytet przypadków użycia jest oparty na celach, takich jak zgodność z przepisami lub prywatność.

Działania nadzorowe SOC związane z tworzeniem przypadków użycia obejmują: 

- Wymagania
- Potrzeby w zakresie personelu lub szkolenia
- Licencje na oprogramowanie
- Dostawca zawierająca umowę
- Zarządzanie planem
- Obsługa rejestru przypadków użycia
- Obsługa/aktualizowanie szablonów

Aby ułatwić proces tworzenia podręcznika i podręcznika, utwórz drzewo decyzji o przypadku użycia. Na poniższym rysunku pokazano przykład.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png" alt-text="Proces decyzyjny w przypadku użycia" lightbox="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png":::

Po zatwierdzeniu i zatwierdzeniu standardu użycia wysokiego poziomu kolejnym krokiem jest utworzenie i przetestowanie rzeczywistego przypadku użycia. W poniższych sekcjach jako przykładów są wykorzystanie scenariuszy ochrony przed wyłudzaniem informacji oraz zagrożeniami i lukami w zabezpieczeniach.

## <a name="use-case-example-1-new-phishing-variant"></a>Przykład użycia przypadku 1: Nowy wariant wyłudzania informacji

Pierwszym krokiem podczas tworzenia przypadku użycia jest utworzenie konspektu przepływu pracy przy użyciu tablicy historii. Oto przykład wysokiej klasy historii dla nowego powiadomienia o wyłudzaniu informacji dla zespołu analizy zagrożeń.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png" alt-text="Przepływ pracy dla kampanii zapobiegającej wyłudzaniu informacji" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png":::

### <a name="invoke-the-use-case-workflow-for-example-1"></a>Wywoływanie przepływu pracy przypadek użycia, na przykład 1

Kolejnym krokiem po zatwierdzeniu tablicy historii jest wywołanie przepływu pracy przypadków użycia. Oto przykładowy proces kampanii zapobiegającej wyłudzaniu informacji. 
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png" alt-text="Przepływ pracy ze szczegółową sprawą użycia dla kampanii zapobiegającej wyłudzaniu informacji" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png":::

## <a name="use-case-example-2-threat-and-vulnerability-scanning"></a>Przykład 2. Przykład użycia: Skanowanie w przypadku zagrożeń i luk w zabezpieczeniach

Inny scenariusz, w którym można użyć przypadku użycia, służy do skanowania zagrożeń i luk w zabezpieczeniach. W tym przykładzie SOC wymaga korygowania zagrożeń i luk w zabezpieczeniach przed zasobami za pośrednictwem zatwierdzonych procesów, które obejmują skanowanie zasobów. 

Oto przykładowy storyboard wysokiego poziomu dla Zarządzanie zagrożeniami i lukami zasobów.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png" alt-text="Przepływ pracy przypadek użycia dla Zarządzanie zagrożeniami i lukami" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png":::

### <a name="invoke-the-use-case-workflow-for-example-2"></a>Wywoływanie przepływu pracy przypadku użycia, na przykład 2

Oto przykładowy proces skanowania zagrożeń i luk w zabezpieczeniach.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png" alt-text="Przepływ pracy ze szczegółowymi informacjami o przypadku użycia dla Zarządzanie zagrożeniami i lukami" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png":::
 
### <a name="analyze-the-use-case-output-and-lessons-learned"></a>Analizowanie danych wyjściowych przypadków użycia i lekcji

Po zatwierdzeniu i przetestowaniu przypadku użycia należy zidentyfikować odstępy między zespołami zabezpieczeń, a także osoby, procesy i Microsoft 365 Defender technologii. Microsoft 365 Defender technologii powinny być analizowane w celu określenia, czy są one w stanie uzyskać oczekiwane wyniki. Można je śledzić za pomocą listy kontrolnej lub macierzy. 

Na przykład w scenariuszu ochrony przed wyłudzaniem informacji zespoły SOC mogły wykryć dane w tej tabeli.


| Zespół SOC | Wymaganie | Wymagania dotyczące osób spełniających wymagania | Proces, który spełnia wymagania | Odpowiednie technologie | Zidentyfikowano przerwę | Dziennik zmian przypadków użycia | Wykluczona (Y/N) |
|:-------|:-----|:-------|:-------|:-------|:-----|:-------|:-------|
| Zespół analizy i analizy zagrożeń | Źródła danych prawidłowo podające aparaty analizy zagrożeń. | Analityk/inżynier analizy zagrożeń | Ustanowione wymagania dotyczące źródeł danych, wyzwalacze analizy zagrożeń z zatwierdzonych źródeł | Microsoft Defender for Identity, Ochrona punktu końcowego w usłudze Microsoft Defender | Zespół analizy zagrożeń nie używa skryptu automatyzacji do łączenia interfejsu API Microsoft 365 Defender z wyszukiwarkami zagrożeń | Dodawanie Microsoft 365 Defender jako źródeł danych do aparatów zagrożeń <BR> <BR> Aktualizowanie książki uruchamiania przypadków użycia | N |
| Monitorowanie zespołu | Źródła danych są prawidłowo podawanie pulpitów nawigacyjnych monitorowania | Raporty i alerty analityków soc warstwy 1,2 & i alerty | Przepływ pracy do raportowania wyników bezpiecznego & Centrum zgodności | [Alerty w Centrum & zgodności](/microsoft-365/security/office-365-security/alerts)  <br><br> Monitorowanie bezpiecznego wyniku  | Brak mechanizmu dla analityków SOC do zgłaszania udanego nowego wykrywania wariantu wyłudzania informacji w celu zwiększenia bezpiecznego wyniku <br><br> [Raportowanie w Centrum & zabezpieczeń](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance)| Dodawanie procesu śledzenia poprawy bezpiecznego wyniku do raportowania przepływów pracy | N | 
| Zespół inżynierów i secops | Aktualizacje kontroli zmian są dokonywane w podręcznikach uruchamiania zespołu SOC | Inżynier SOC warstwy 2 | Procedura powiadomień o zmianie kontroli dla podręczników zespołu SOC | Zatwierdzone zmiany dotyczące urządzeń zabezpieczających | Zmiany w Microsoft 365 Defender technologii zabezpieczeń SOC wymagają zatwierdzenia | Dodaj Microsoft Defender for Cloud Apps, Defender for Identity, Defender for Endpoint, Security & Compliance Center to SOC runbooks | T |
|||||||||

Ponadto zespoły SOC mogły także odkryć opisane w poniższej tabeli dotyczące opisanego powyżej Zarządzanie zagrożeniami i lukami scenariuszu:

| Zespół SOC | Wymaganie | Wymagania dotyczące osób spełniających wymagania | Proces, który spełnia wymagania | Odpowiednie technologie | Zidentyfikowano przerwę | Dziennik zmian przypadków użycia | Wykluczona (Y/N) |
|:-------|:-----|:-------|:-------|:-------|:-----|:-------|:-------|
| Nadzór SOC | Wszystkie zasoby połączone z zatwierdzonymi sieciami są identyfikowane i kategoryzowane | Nadzór SOC, właściciele BU, właściciele aplikacji, właściciele zasobów IT itp. | Scentralizowany system zarządzania zasobami do odnajdowania i tworzenia listy kategorii elementów zawartości oraz atrybutów na podstawie ryzyka. | ServiceNow lub inne zasoby. <br><br>[Microsoft 365 spisu urządzeń](/security/defender-endpoint/device-discovery) | Odnaleziono tylko 70% zasobów. Microsoft 365 Defender środków zaradczych obowiązuje tylko w przypadku znanych zasobów | Usługi zarządzania cyklem życia dla osób dorosłych, Microsoft 365 Defender mają dostęp do 100% zasobów | N |
| Funkcje & SecOps Teams | Rozwiązywanie problemów o wysokim wpływie i krytycznych luk w zabezpieczeniach zasobów jest korygowane zgodnie z zasadami | Inżynierowie secops, analitycy SOC: luka w & zgodności, inżynieria zabezpieczeń | Zdefiniowany proces kategoryzowania luk w zabezpieczeniach o wysokim poziomie ryzyka i krytycznym poziomie wykorzystania | [Pulpity nawigacyjne zarządzania zagrożeniami i lukami w zabezpieczeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) | Program Defender for Endpoint zidentyfikował urządzenia o wysokim poziomie wydajności i alertach bez planu rozwiązywania problemów ani wdrożenia zalecanych działań firmy Microsoft | Dodaj przepływ pracy do powiadamiania właścicieli zasobów, gdy działania naprawcze są wymagane w ciągu 30 dni od zasady. Wdrożenie systemu biletowania w celu powiadamiania właścicieli zasobów o krokach rozwiązywania problemów. | N |
| Monitorowanie Teams | Stan zagrożenia i luki w zabezpieczeniach jest zgłaszany za pośrednictwem firmowego portalu intranetowego | Analityk SOC warstwy 2 | Raporty wygenerowane automatycznie Microsoft 365 Defender z postępem rozwiązywania problemów dotyczących zasobów | [Alerty w Centrum & zgodności](/microsoft-365/security/office-365-security/alerts) <br><br> Monitorowanie bezpiecznego wyniku | Właściciele zasobów nie mogą raportować żadnych widoków ani raportów na pulpicie nawigacyjnym dotyczących zagrożeń i luk w zabezpieczeniach. | Utwórz skrypt automatyzacji, aby wypełnić stan rozwiązywania problemów z zabezpieczeniami o wysokim poziomie ryzyka i krytycznym poziomie wykorzystania zasobów w organizacji. | N |
|||||||||

W tych przykładowych przypadkach testów dostrzeżono kilka luk w wymaganiach zespołu SOC, które zostały określone jako linie bazowe obowiązków każdego zespołu. Lista kontrolna przypadków użycia może być tak wyczerpująca, jak to konieczne, aby upewnić się, że zespół SOC jest przygotowany na integrację tego Microsoft 365 Defender z nowymi lub istniejącymi wymaganiami soC. Ponieważ będzie to proces iteracyjny, proces opracowywania przypadków użycia i zawartość wyjściowa przypadków użycia w naturalny sposób będą służyć aktualizowaniu i wywrzeniu wniosków o zajęciach prowadzonych przez SOC.

## <a name="update-production-runbooks-and-playbooks"></a>Aktualizowanie podręczników i podręczników produkcyjnych

Po zakończeniu testowania przypadków użycia w przypadku wszystkich luk wnioski i zebrane w nich metryki można włączyć do podręczników produkcyjnych (procesów operacyjnych) i podręczników zespołu SOC (odpowiedzi na incydenty i procedury eskalacji). 

Konserwacja podręczników i podręczników zespołu SOC można zorganizować na wiele sposobów. Każdy zespół soc może być odpowiedzialny za własny lub może być dostępna jedna scentralizowana wersja dla wszystkich zespołów do udostępnienia w centralnym repozytorium. Zarządzanie podręcznikiem i podręcznikami dla poszczególnych organizacji jest oparte na wielkości, poszczególnych umiejętnościach, rolach i podziałze obowiązków. Po zaktualizowaniu podręcznika należy postępować zgodnie z procesem aktualizacji podręcznika. 

## <a name="use-a-standard-framework-for-escalation"></a>Używanie standardowej struktury do eskalacji

Podręczniki to czynności, które zespoły SOC będą musiały wykonać w przypadku wystąpienia rzeczywistego zdarzenia, na podstawie pomyślnej integracji i przetestowania przypadku użycia. Dlatego bardzo ważne jest, aby SOC podlegał formalnemu podejściem do reagowania na incydenty, takim jak standard [NIST Incident Response Standard](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) , który stał się jednym z najlepszych standardów branżowych w zakresie reagowania na incydenty.

Czteroetapowy proces reagowania na zdarzenia w programie NIST obejmuje cztery fazy:

1.  Przygotowanie
2.  Wykrywanie i analiza
3.  Zawieranie, tylko wiadowanie i odzyskiwanie
4.  Działania po zdarzeniu

### <a name="example-tracking-preparation-phase-activity"></a>Przykład: Śledzenie aktywności fazy przygotowawowej

Jedną z podstawowych podstaw podręcznika eskalacji jest zapewnienie niewielkiej niejednoznaczności co do tego, co każdy zespół soc powinien zrobić przed zdarzeniem lub zdarzeniem, w jego trakcie i po nim. Dlatego warto wyświetlić instrukcje krok po kroku. 

Na przykład faza przygotowawcza może zawierać macierz zadań jeżeli/to lub XoR. W przypadku nowego przykładu użycia wariantu wyłudzania informacji taka macierz może wyglądać tak:

| Dlaczego jest objęte gwarancją eskalacji? | Następny krok |
|:-------|:-----|
| Alert w monitorze SOC oceniony jako **krytyczny** wyzwolony > **500/godzinę** | Przejdź do podręcznika A, sekcji 2, Działania 5 (z linkiem do sekcji podręcznika) |
| Oprogramowanie e Commerce zgłosiło potencjalne ataki DDoS | Wywołaj podręcznik B-sekcja C, Działanie 19 (z linkiem do sekcji podręcznika) |
| Kierownictwo zgłosił podejrzaną wiadomość e-mail jako próbę wyłudzenia informacji | Przejdź do podręcznika 5, sekcji 2, działania 5 (z linkiem do sekcji podręcznika) |
|||

Po wykonaniu fazy przygotowawczych organizacje powinny wywoływać pozostałe fazy zgodnie z NIST:

- Wykrywanie i analiza
- Zawieranie, tylko wiadowanie i odzyskiwanie
- Działania po zdarzeniu 

## <a name="next-step"></a>Następny krok

[Krok 6. Identyfikowanie zadań konserwacji soc](integrate-microsoft-365-defender-secops-tasks.md)
