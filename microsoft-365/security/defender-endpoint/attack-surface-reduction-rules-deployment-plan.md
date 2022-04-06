---
title: Planowanie wdrożenia reguł asr w celu ataków na zmniejszenie reguł wdrażania
description: Ten temat zawiera wskazówki dotyczące planowania wdrożenia reguł zmniejszenia powierzchni ataków (ASR).
keywords: Wdrażanie reguł ograniczania powierzchni ataków, wdrażanie asr, włączanie reguł asr, konfigurowanie funkcji asr, systemu ochrony przed nieuprawnianiem hostów, reguł ochrony, reguł ochrony przed wykorzystywaniem luk, ochrony przed wykorzystywaniem, regułami wykorzystania luk, regułami zapobiegania powstawaniu dzieci, Ochrona punktu końcowego w usłudze Microsoft Defender, konfigurowanie reguł asr
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
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 9342e4b3868e5bc0d5701b4a0cfa2e8f0a56937b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477330"
---
# <a name="step-1-plan-asr-rules-deployment"></a>Krok 1. Planowanie wdrożenia reguł ASR

Podczas testowania reguł zmniejszania powierzchni ataków (ASR, attack surface reduction) należy zacząć od odpowiedniej jednostki biznesowej. Na początek chcesz zacząć od małej grupy osób w konkretnej jednostce biznesowej. Możesz zidentyfikować niektórych liderów ASR w ramach określonej jednostki biznesowej, którzy mogą mieć rzeczywisty wpływ na reguły ASR i ułatwić dostosowanie implementacji.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-planning-steps.png" alt-text="Kroki planowania reguł asr" lightbox="images/asr-rules-planning-steps.png":::

## <a name="start-with-the-right-business-unit"></a>Rozpoczynanie pracy od odpowiedniej jednostki biznesowej

Sposób wybierania jednostki biznesowej do wdrożenia reguł asr będzie zależny od takich czynników, jak:

- Rozmiar jednostki biznesowej
- Dostępność mistrzów reguł ASR  
- Rozpowszechnianie i używanie:
  - Oprogramowanie
  - Foldery udostępnione
  - Używanie skryptów
  - Office makra
  - Inne jednostki, na które mają wpływ reguły ASR

W zależności od potrzeb biznesowych możesz wybrać wiele jednostek biznesowych, aby pobrać próbkę oprogramowania, folderów udostępnionych, skryptów, makr itp. W odwrotnej kolejności możesz ograniczyć zakres pierwszej reguły asr do jednej jednostki biznesowej, a następnie powtórzyć proces rozsyłania całych reguł asr do innych jednostek biznesowych pojedynczo.

## <a name="identify-asr--rules-champions"></a>Identyfikacja mistrzów reguł ASR

Mistrzowie reguł ASR to członkowie w Twojej organizacji, którzy pomogą w wdrożeniu początkowych reguł asr na etapie wstępnych testów i implementacji. Twoimi mistrzami są zazwyczaj pracownicy, którzy bardziej technicznie pracują we wschowie i nie są dezneminowane ze sporadyczne przerwy w pracy. Zaangażowanie mistrzów będzie kontynuowane w ramach szerszego rozszerzenia wdrożenia reguł ASR na twoją organizację. Mistrzowie reguł ASR będą w pierwszej kolejności doświadczać poszczególnych poziomu zasad asr.

Ważne jest dostarczenie opinii i kanału odpowiedzi dla mistrzów reguł ASR w celu powiadamiania Cię o zakłóceniach w pracy związanej z regułami ASR i otrzymywaniu komunikacji związanej z regułami asr.

## <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>Uzyskiwanie spisu aplikacji biznesowych i zrozumienie procesów jednostek biznesowych

Pełna znajomość aplikacji i procesów poszczególnych jednostek biznesowych używanych w całej organizacji jest bardzo ważna dla pomyślnego wdrożenia reguł asr. Ponadto konieczne jest zrozumienie sposobu, w jaki te aplikacje są używane w różnych jednostkach biznesowych organizacji.
Aby rozpocząć, należy uzyskać spis aplikacji, które są zatwierdzone do użytku w całej organizacji. Możesz użyć narzędzi, takich jak centrum Aplikacje Microsoft 365 administracyjnego, aby ułatwić spis aplikacji. Zobacz: [Omówienie spisu w centrum Aplikacje Microsoft 365 administracyjnego](/deployoffice/admincenter/inventory).

## <a name="define-reporting-and-response-team-roles-and-responsibilities"></a>Definiowanie ról i obowiązków zespołu w zakresie raportowania i reagowania

Wyraźnie wyartykułowanie ról i obowiązków osób odpowiedzialnych za monitorowanie statusu i działanie reguł ASR i komunikowanie się z nich jest podstawową czynnością konserwacji ASR. Dlatego ważne jest ustalenie:

- Osoba lub zespół odpowiedzialny za zbieranie raportów
- Jak i komu są udostępniane raporty
- Jak zostanie rozwiązana eskalacja w przypadku nowo zidentyfikowanych zagrożeń lub niechcianych zablokowania spowodowanych przez reguły asr

Typowe role i obowiązki:

- Administratorzy IT: implementowanie reguł asr, zarządzanie wykluczeniami. Praca z różnymi jednostkami biznesowymi nad aplikacjami i procesami. Łączenie i udostępnianie raportów uczestnikom projektu
- Certyfikowany analityk Centrum zabezpieczeń (CSOC): odpowiedzialny za inwestycje o wysokim priorytecie i zablokowane procesy w celu ustalenia, że zagrożenie jest ważne, czy nie
- Główny inspektor ds. zabezpieczeń informacji (CISO): odpowiada za ogólną kondycję i stan zabezpieczeń organizacji.

## <a name="ring-deployment"></a>Wdrożenie pierścienia

W dużych przedsiębiorstwach firma Microsoft zaleca wdrażanie reguł asr w "pierścieniach". Pierścienie to grupy urządzeń, które są wizualnie reprezentowane jako sępne okręgi promieniujące na zewnątrz jak niesądzające się pierścienie drzewa. Po pomyślnym wdrożeniu pierścienia wewnętrznego możesz przejść do fazy testowania następnego pierścienia. Dokładne ocenianie jednostek biznesowych, reguł ASR, mistrzów, aplikacji i procesów jest konieczne, aby definiować swoje pierścienie.
W większości przypadków w organizacji zostaną zaprojektowane pierścienie wdrażania dla etapowego wdrażania Windows aktualizacji. Możesz użyć istniejącego projektu pierścienia, aby zaimplementować reguły asr.
Zobacz: [Tworzenie planu wdrażania dla Windows](/windows/deployment/update/create-deployment-plan)

## <a name="additional-topics-in-this-deployment-collection"></a>Dodatkowe tematy w tym zbiorze wdrożeń

[Wymagania wstępne wdrażania reguł asr](attack-surface-reduction-rules-deployment.md)

[Krok 2. Testowanie reguł asr](attack-surface-reduction-rules-deployment-test.md)

[Krok 3. Implementowanie reguł asr](attack-surface-reduction-rules-deployment-implement.md)

[Krok 4. Operacyjne reguły asr](attack-surface-reduction-rules-deployment-operationalize.md)
