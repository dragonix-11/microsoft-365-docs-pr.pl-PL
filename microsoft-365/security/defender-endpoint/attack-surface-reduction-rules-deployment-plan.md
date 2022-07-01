---
title: Zaplanuj wdrażanie reguł zmniejszania powierzchni podatnej na ataki (ASR)
description: Zawiera wskazówki dotyczące planowania wdrożenia reguł zmniejszania obszaru ataków (ASR).
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
ms.openlocfilehash: 4e538a4e986ad0636c380ec2ba167249221ac3ec
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602497"
---
# <a name="plan-attack-surface-reduction-asr-rules-deployment"></a>Zaplanuj wdrażanie reguł zmniejszania powierzchni podatnej na ataki (ASR)

Podczas testowania reguł zmniejszania obszaru ataków (ASR) należy zacząć od odpowiedniej jednostki biznesowej. Warto zacząć od niewielkiej grupy osób w określonej jednostce biznesowej. W ramach określonej jednostki biznesowej można zidentyfikować niektórych mistrzów usługi ASR, którzy mogą zapewnić rzeczywisty wpływ na reguły usługi ASR i pomóc w dostrojeniu implementacji.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-planning-steps.png" alt-text="Kroki planowania reguł usługi ASR" lightbox="images/asr-rules-planning-steps.png":::

## <a name="start-with-the-right-business-unit"></a>Rozpocznij od właściwej jednostki biznesowej

Wybór jednostki biznesowej do wdrożenia reguł usługi ASR będzie zależeć od takich czynników, jak:

- Rozmiar jednostki biznesowej
- Dostępność mistrzów reguł usługi ASR  
- Dystrybucja i użycie:
  - Oprogramowanie
  - Foldery udostępnione
  - Korzystanie ze skryptów
  - Makra pakietu Office
  - Inne jednostki, których dotyczą reguły usługi ASR

W zależności od potrzeb biznesowych możesz zdecydować się na uwzględnienie wielu jednostek biznesowych w celu uzyskania szerokiego próbkowania oprogramowania, folderów udostępnionych, skryptów, makr itp. Z drugiej strony możesz zdecydować się ograniczyć zakres pierwszego wdrożenia reguł usługi ASR do jednej jednostki biznesowej, a następnie powtórzyć cały proces wdrażania reguł usługi ASR do innych jednostek biznesowych, pojedynczo.

## <a name="identify-asr--rules-champions"></a>Identyfikowanie mistrzów reguł usługi ASR

Mistrzowie reguł usługi ASR to członkowie organizacji, którzy pomogą w początkowym wdrożeniu reguł usługi ASR w fazie testowania wstępnego i implementacji. Mistrzowie są zazwyczaj pracownikami, którzy są bardziej technicznie biegli i którzy nie są wykolejone przez sporadyczne przerwy w przepływie pracy. Zaangażowanie mistrzów będzie kontynuowane w ramach szerszego rozszerzania wdrażania reguł usługi ASR w organizacji. Mistrzowie reguł usługi ASR będą musieli najpierw zapoznać się z każdym poziomem wdrażania reguł usługi ASR.

Ważne jest, aby udostępnić kanał opinii i odpowiedzi dla mistrzów reguł usługi ASR, aby otrzymywać alerty dotyczące zakłóceń pracy związanych z regułami usługi ASR i otrzymywać komunikaty związane z wdrażaniem reguł usługi ASR.

## <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>Uzyskiwanie spisu aplikacji biznesowych i zrozumienie procesów jednostki biznesowej

Pełne zrozumienie aplikacji i procesów jednostki biznesowej używanych w całej organizacji ma kluczowe znaczenie dla pomyślnego wdrożenia reguł usługi ASR. Ponadto konieczne jest zrozumienie sposobu, w jaki te aplikacje są używane w różnych jednostkach biznesowych w organizacji.
Aby rozpocząć, należy uzyskać spis aplikacji zatwierdzonych do użycia w całej organizacji. Możesz użyć narzędzi, takich jak centrum administracyjne Aplikacje Microsoft 365, aby ułatwić spis aplikacji. Zobacz: [Omówienie spisu w centrum administracyjnym Aplikacje Microsoft 365](/deployoffice/admincenter/inventory).

## <a name="define-reporting-and-response-team-roles-and-responsibilities"></a>Definiowanie ról i obowiązków zespołu ds. raportowania i reagowania

Jasne określenie ról i obowiązków osób odpowiedzialnych za monitorowanie i komunikowanie stanu i działania reguł usługi ASR jest podstawową działalnością konserwacji usługi ASR. Dlatego ważne jest, aby określić:

- Osoba lub zespół odpowiedzialny za zbieranie raportów
- Jak i komu są udostępniane raporty
- Jak rozwiązywana jest eskalacja dla nowo zidentyfikowanych zagrożeń lub niechcianych blokad spowodowanych przez reguły usługi ASR

Typowe role i obowiązki obejmują:

- Administratorzy IT: implementowanie reguł usługi ASR, zarządzanie wykluczeniami. Praca z różnymi jednostkami biznesowymi w aplikacjach i procesach. Składanie i udostępnianie raportów zainteresowanym stronom
- Certyfikowany analityk centrum operacji zabezpieczeń (CSOC): odpowiedzialny za inwestowanie procesów o wysokim priorytecie, zablokowanych w celu określenia, czy zagrożenie jest prawidłowe lub nie
- Dyrektor ds. zabezpieczeń informacji (CISO): odpowiedzialny za ogólną kondycję i stan bezpieczeństwa organizacji

## <a name="ring-deployment"></a>Wdrażanie pierścieniowe

W przypadku dużych przedsiębiorstw firma Microsoft zaleca wdrożenie reguł usługi ASR w "pierścieniach". Pierścienie to grupy urządzeń, które są wizualnie reprezentowane jako okręgi koncentryczne, które promieniują na zewnątrz, jak nie nakładające się pierścienie drzewa. Po pomyślnym wdrożeniu najbardziej wewnętrznego pierścienia można przenieść następny pierścień do fazy testowania. Dokładna ocena jednostek biznesowych, elementów nadrzędnych reguł usługi ASR, aplikacji i procesów jest niezbędna do zdefiniowania pierścieni.
W większości przypadków organizacja będzie projektować pierścienie wdrażania dla etapowych wdrożeń aktualizacji systemu Windows. Istniejący projekt pierścienia umożliwia zaimplementowanie reguł usługi ASR.
Zobacz: [Tworzenie planu wdrożenia dla systemu Windows](/windows/deployment/update/create-deployment-plan)

## <a name="additional-topics-in-this-deployment-collection"></a>Dodatkowe tematy w tej kolekcji wdrożeń

[Omówienie wdrażania reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment.md)

[Przetestuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-test.md)

[Włącz reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-implement.md)

[Operacjonalizuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-operationalize.md)

[Odwołuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md)
