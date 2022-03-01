---
title: Microsoft Defender for Endpoint partner opportunities and scenarios
ms.reviewer: ''
description: Dowiedz się, jak rozszerzyć istniejące oferty zabezpieczeń poza otwartą platformę i bogaty zestaw interfejsów API do tworzenia rozszerzeń i integracji z programem Microsoft Defender for Endpoint
keywords: API, partner, extend, open framework, apis, rozszerzenia, integracje, wykrywanie, zarządzanie, odpowiedź, luki, analizy
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a06f02fe216953d6d84fea205e06a9291f8902c9
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997382"
---
# <a name="microsoft-defender-for-endpoint-partner-opportunities-and-scenarios"></a>Microsoft Defender for Endpoint partner opportunities and scenarios

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Partnerzy mogą łatwo rozszerzyć swoje istniejące oferty zabezpieczeń poza otwartą platformę oraz bogaty i kompletny zestaw interfejsów API, aby tworzyć rozszerzenia i integracje z usługą Defender for Endpoint. 

Interfejsy API obejmują obszary funkcjonalne, takie jak wykrywanie, zarządzanie, reagowanie, luki w zabezpieczeniach i zakres przypadków użycia obejmujących analizę. W zależności od przypadku i potrzeby użycia partnerzy mogą przesyłać strumieniowo lub przesyłać zapytania do usługi Defender for Endpoint. 


## <a name="scenario-1-external-alert-correlation-and-automated-investigation-and-remediation"></a>Scenariusz 1. Korelacja alertu zewnętrznego oraz automatyczne badanie i rozwiązywanie problemów
Program Defender for Endpoint oferuje unikatowe automatyczne możliwości badania i rozwiązywania problemów w celu reagowania na incydenty na skalę. 

Integrowanie funkcji automatycznego badania i odpowiedzi z innymi rozwiązaniami, takimi jak produkty zabezpieczeń sieciowych lub inne produkty zabezpieczeń punktów końcowych, będzie pomocne w przypadku alertów. Integracja zminimalizuje również skomplikowanie związane z korelacją sieci i sygnału urządzenia, co prowadzi do usprawniania działań naprawczych w związku z badaniami i zagrożeniami na urządzeniach.

Program Defender for Endpoint dodaje obsługę tego scenariusza w następujących postaciach:

- Alerty zewnętrzne można wypychać do usługi Defender for Endpoint i prezentować obok siebie z dodatkowymi alertami opartymi na urządzeniu z usługą Defender for Endpoint. Ten widok udostępnia pełny kontekst alertu — z rzeczywistym procesem i pełną historią ataków.

- Po wygenerowaniu alertu sygnał jest udostępniany przez wszystkie punkty końcowe chronione przez usługę Defender w przedsiębiorstwie. Defender for Endpoint takes immediate automated or operator-assisted response to address the alert.

## <a name="scenario-2-security-orchestration-and-automation-response-soar-integration"></a>Scenariusz 2. Integracja z zabezpieczeniami i odpowiedziami automatyzacji (SOAR)
Rozwiązania techniczne mogą ułatwić tworzenie podręczników oraz integrację rozbudowanych modeli danych i akcji udostępnianych przez usługę Defender dla interfejsów API punktów końcowych w odpowiedziach, takich jak zapytanie dotyczące danych urządzenia, wyzwalanie izolacji urządzenia, blokowanie/zezwalanie, rozwiązywanie alertów i inne.

## <a name="scenario-3-indicators-matching"></a>Scenariusz 3. Dopasowywanie wskaźników 
Wskaźnik naruszenia zabezpieczeń (IoCs) to podstawowa funkcja w każdym rozwiązaniu ochrony punktu końcowego. Ta funkcja jest dostępna w programie Defender dla punktu końcowego i umożliwia ustawianie listy wskaźników do zapobiegania, wykrywania i wykluczenia obiektów. Można zdefiniować akcję, która ma zostać wykonane, oraz czas trwania, kiedy zastosować akcję.

Powyższe scenariusze służą jako przykłady rozszerzalności platformy. Nie ograniczasz się do tych przykładów i z pewnością zachęcamy do wykorzystania otwartej struktury do odnajdowania i eksplorowania innych scenariuszy.

Postępuj zgodnie z instrukcjami [w tece Zostań partnerem programu Microsoft Defender for Endpoint,](get-started-partner-integration.md) aby zintegrować swoje rozwiązanie z usługą Defender for Endpoint.

## <a name="related-topic"></a>Temat pokrewny
- [Omówienie zarządzania i interfejsów API](management-apis.md)
