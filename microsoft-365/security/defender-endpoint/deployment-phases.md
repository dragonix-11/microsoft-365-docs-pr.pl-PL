---
title: Fazy wdrażania
description: Dowiedz się, jak wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender przez przygotowanie, skonfigurowanie i wdrożenie punktów końcowych w tej usłudze
keywords: wdrażanie, przygotowywanie, konfiguracja, wdrożenie, faza, wdrożenie, wdrażanie, wdrażanie, konfigurowanie
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-overview
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c39ef92448317e625f3f2e6948f69a38093b1504
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467714"
---
# <a name="deployment-phases"></a>Fazy wdrażania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Dowiedz się, jak wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender, aby przedsiębiorstwa skorzystały z ochrony zapobiegatywnej, wykrywania po naruszeniu, automatycznego badania i reagowania.

Ten przewodnik ułatwia pracę uczestnikom projektu w celu przygotowania środowiska i wdrażania urządzeń w sposób metodyczny, od oceny do ważnego wdrożenia pilotażowego.

Każda sekcja odpowiada osobnemu artykułowi w tym rozwiązaniu.

:::image type="content" source="images/deployment-guide-phases.png" alt-text="Etapy wdrażania ze szczegółami z tabeli" lightbox="images/deployment-guide-phases.png":::


:::image type="content" source="images/phase-diagrams/deployment-phases.png" alt-text="Podsumowanie faz wdrażania: przygotowanie, konfiguracja, wdrożenie" lightbox="images/phase-diagrams/deployment-phases.png":::

<br>

****

|Faza|Opis|
|---|---|
|[Etap 1. Przygotowywanie](prepare-deployment.md)|Dowiedz się, co należy wziąć pod uwagę podczas wdrażania usługi Defender dla punktu końcowego, na przykład zatwierdzenia interesariuszy, zagadnienia dotyczące środowiska, uprawnienia dostępu i kolejność wdrażania funkcji.|
|[Etap 2. Konfigurowanie](production-deployment.md)|Uzyskaj wskazówki dotyczące początkowych czynności, które należy wykonać, aby uzyskać dostęp do portalu, na przykład sprawdzania poprawności licencjonowania, ukończenia kreatora konfiguracji i konfiguracji sieci.|
|[Etap 3. Wniesienie](onboarding.md)|Dowiedz się, jak korzystać ze pierścieni wdrażania, obsługiwanych narzędzi wdrażania na podstawie typu punktu końcowego i konfigurowania dostępnych możliwości.|
|

Po ukończeniu tego przewodnika skonfigurujesz odpowiednie uprawnienia dostępu, punkty końcowe zostaną do tej usługi wnosone i będą raportowane dane czujnika, a także zostaną ustawione funkcje, takie jak ochrona następnej generacji i zmniejszenie obszarów ataków.

Niezależnie od architektury środowiska i metody wdrożenia przedstawionych w wytycznych dotyczących wdrażania [](deployment-strategy.md) w planie ten przewodnik będzie obsługiwać Cię w zakresie punktów końcowych wdrażania.

## <a name="key-capabilities"></a>Najważniejsze funkcje

Chociaż Ochrona punktu końcowego w usłudze Microsoft Defender udostępnia wiele możliwości, głównym celem tego przewodnika po wdrażaniu jest wprowadzenie do pracy z urządzeniami przy wdrażaniu. Oprócz dodatku do pracy z usługą, z poniższych wskazówek możesz również rozpocząć pracę z następującymi możliwościami.

<br>

****

|Funkcja|Opis|
|---|---|
|Wykrywanie i reagowanie dotyczące punktów końcowych|Funkcje wykrywania punktu końcowego i reagowania są dostępne w celu wykrywania, badania i reagowania na próby dostępu oraz aktywnego naruszenia.|
|Ochrona nowej generacji|Aby dodatkowo zwiększyć wykorzystanie obwodu zabezpieczeń sieci, Ochrona punktu końcowego w usłudze Microsoft Defender ochrony następnej generacji w celu wychwytania wszystkich typów wyłaniających się zagrożeń.|
|Zmniejszanie obszaru podatnego na ataki|Udostępnij pierwszą linię obrony w stosie. Po upewnienia się, że ustawienia konfiguracji są poprawnie ustawione i są stosowane techniki wykorzystywania luk w wykorzystywaniu wykorzystywania, te funkcje opierają się na atakach i wykorzystywaniu.|
|

Wszystkie te funkcje są dostępne dla Ochrona punktu końcowego w usłudze Microsoft Defender licencji. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące licencjonowania](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>Zakres

### <a name="in-scope"></a>W zakresie

- Korzystanie z Microsoft Endpoint Manager i Microsoft Endpoint Configuration Manager do do konfigurowania usług i punktów końcowych
- Włączanie funkcji defender dla wykrywanie i reagowanie w punktach końcowych punktów końcowych (EDR)
- Włączanie funkcji platformy Ochrony punktów końcowych programu Defender (EPP)
  - Ochrona nowej generacji
  - Zmniejszanie obszaru podatnego na ataki

### <a name="out-of-scope"></a>Poza zakresem

Następujące informacje nie znajdują się w tym przewodniku po wdrażaniu:

- Konfiguracja rozwiązań innych firm, które mogą być zintegrowane z programem Defender for Endpoint
- Testy penetracyjnych w środowisku produkcyjnym

## <a name="see-also"></a>Zobacz też

- [Etap 1. Przygotowywanie](prepare-deployment.md)
- [Etap 2. Konfigurowanie](production-deployment.md)
- [Etap 3. Wniesienie](onboarding.md)
- [Planowanie wdrożenia](deployment-strategy.md)
