---
title: omówienie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się, jak wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender, przygotowując, konfigurując i dołączając punkty końcowe do tej usługi
keywords: wdrażanie, przygotowywanie, konfigurowanie, dołączanie, faza, wdrażanie, wdrażanie, wdrażanie, konfigurowanie
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
ms.openlocfilehash: 3520d249e7241eb1b890c3939fe6e6165d5c6011
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607614"
---
# <a name="microsoft-defender-for-endpoint-deployment-overview"></a>omówienie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Dowiedz się, jak wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender, aby przedsiębiorstwo miało możliwość korzystania z ochrony zapobiegawczej, wykrywania po naruszeniu zabezpieczeń, zautomatyzowanego badania i reagowania.

Ten przewodnik ułatwia pracę między osobami biorącymi udział w projekcie, aby przygotować środowisko, a następnie dołączyć urządzenia w sposób metodyczny, przechodząc od oceny do znaczącego pilotażu, do pełnego wdrożenia.

Każda sekcja odpowiada oddzielnemu artykułowi w tym rozwiązaniu.

:::image type="content" source="images/deployment-guide-phases.png" alt-text="Fazy wdrażania ze szczegółami z tabeli" lightbox="images/deployment-guide-phases.png":::


:::image type="content" source="images/phase-diagrams/deployment-phases.png" alt-text="Podsumowanie faz wdrażania: przygotowywanie, konfigurowanie, dołączanie" lightbox="images/phase-diagrams/deployment-phases.png":::

<br>

****

|Fazy|Opis|
|---|---|
|[Faza 1. Przygotowanie](prepare-deployment.md)|Dowiedz się, co należy wziąć pod uwagę podczas wdrażania usługi Defender for Endpoint, takich jak zatwierdzenia uczestników projektu, zagadnienia dotyczące środowiska, uprawnienia dostępu i kolejność wdrażania możliwości.|
|[Faza 2. Konfiguracja](production-deployment.md)|Uzyskaj wskazówki dotyczące początkowych kroków, które należy wykonać, aby uzyskać dostęp do portalu, takiego jak sprawdzanie poprawności licencjonowania, ukończenie pracy kreatora konfiguracji i konfiguracja sieci.|
|[Faza 3. Dołączenie](onboarding.md)|Dowiedz się, jak korzystać z pierścieni wdrażania, obsługiwanych narzędzi dołączania na podstawie typu punktu końcowego i konfigurowania dostępnych możliwości.|
|

Po ukończeniu tego przewodnika zostanie skonfigurowany z odpowiednimi uprawnieniami dostępu, punkty końcowe zostaną dołączone i będą raportować dane czujników do usługi, a możliwości, takie jak ochrona nowej generacji i redukcja obszaru ataków, zostaną wprowadzone.

Niezależnie od architektury środowiska i metody wdrażania wybranej w przewodniku [Plan deployment](deployment-strategy.md) guidance (Planowanie wdrożenia) ten przewodnik będzie obsługiwał punkty końcowe dołączania.

## <a name="key-capabilities"></a>Kluczowe możliwości

Chociaż Ochrona punktu końcowego w usłudze Microsoft Defender oferuje wiele możliwości, głównym celem tego przewodnika wdrażania jest rozpoczęcie pracy z dołączaniem urządzeń. Oprócz dołączania te wskazówki umożliwiają rozpoczęcie pracy z następującymi możliwościami.

<br>

****

|Możliwości|Opis|
|---|---|
|Wykrywanie i reagowanie dotyczące punktów końcowych|Funkcje wykrywania i reagowania na punkty końcowe są wprowadzane w celu wykrywania, badania i reagowania na próby włamań i aktywne naruszenia.|
|Ochrona nowej generacji|Aby jeszcze bardziej wzmocnić obwód zabezpieczeń sieci, Ochrona punktu końcowego w usłudze Microsoft Defender korzysta z ochrony nowej generacji przeznaczonej do przechwytywania wszystkich typów pojawiających się zagrożeń.|
|Zmniejszanie obszaru podatnego na ataki|Podaj pierwszy wiersz obrony w stosie. Dzięki zapewnieniu prawidłowego ustawienia konfiguracji i zastosowaniu technik ograniczania ryzyka luk w zabezpieczeniach te możliwości są odporne na ataki i eksploatację.|
|

Wszystkie te możliwości są dostępne dla Ochrona punktu końcowego w usłudze Microsoft Defender posiadaczy licencji. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące licencjonowania](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>Zakres

### <a name="in-scope"></a>W zakresie

- Używanie Configuration Manager microsoft Endpoint Manager i punktu końcowego firmy Microsoft do dołączania punktów końcowych do usługi i konfigurowania możliwości
- Włączanie funkcji wykrywania i reagowania punktu końcowego w usłudze Defender for Endpoint (EDR)
- Włączanie możliwości platformy ochrony punktów końcowych (EPP) w usłudze Defender for Endpoint
  - Ochrona nowej generacji
  - Zmniejszanie obszaru podatnego na ataki

### <a name="out-of-scope"></a>Poza zakresem

Poniżej przedstawiono zakres tego przewodnika wdrażania:

- Konfiguracja rozwiązań innych firm, które mogą zostać zintegrowane z usługą Defender for Endpoint
- Testy penetracyjne w środowisku produkcyjnym

## <a name="see-also"></a>Zobacz też

- [Faza 1. Przygotowanie](prepare-deployment.md)
- [Faza 2. Konfiguracja](production-deployment.md)
- [Faza 3. Dołączenie](onboarding.md)
- [Zaplanuj wdrożenie](deployment-strategy.md)
