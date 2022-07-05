---
title: Porównanie planów Ochrona punktu końcowego w usłudze Microsoft Defender
description: Porównaj usługę Defender for Endpoint Plan 1 z planem 2. Dowiedz się więcej o różnicach między planami i wybierz plan odpowiadający potrzebom organizacji.
keywords: Defender for Endpoint, zaawansowana ochrona przed zagrożeniami, ochrona punktu końcowego
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 06/17/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: shlomi, efratka
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: e1cf2647ac8308d30b82e69cbb288fde330fdc5a
ms.sourcegitcommit: 0c87abc17fbfe8aa43d61510101acdad0d491cd2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2022
ms.locfileid: "66612200"
---
# <a name="compare-microsoft-defender-for-endpoint-plans"></a>Porównanie planów Ochrona punktu końcowego w usłudze Microsoft Defender

Ochrona punktu końcowego w usłudze Microsoft Defender to platforma zabezpieczeń punktu końcowego przedsiębiorstwa, która pomaga sieciom przedsiębiorstw w zapobieganiu zaawansowanym zagrożeniom, wykrywaniu i badaniu ich oraz reagowaniu na nie. Usługa Defender for Endpoint zapewnia zaawansowaną ochronę przed zagrożeniami, która obejmuje oprogramowanie antywirusowe, oprogramowanie chroniące przed złośliwym kodem, ograniczanie ryzyka wymuszania okupu i nie tylko, a także scentralizowane zarządzanie i raportowanie. Możesz wybrać jedną z następujących opcji dla Ochrona punktu końcowego w usłudze Microsoft Defender:

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Możesz użyć tego artykułu, aby wyjaśnić, jaka ochrona jest zapewniana przez różne funkcje dostępne w usłudze Defender for Endpoint Plan 1, Defender for Endpoint Plan 2, nowym dodatku Defender Vulnerability Management i Microsoft 365 Defender.

## <a name="compare-defender-for-endpoint-plans"></a>Porównanie planów ochrony punktu końcowego w usłudze Microsoft Defender

W poniższej tabeli przedstawiono podsumowanie elementów uwzględnionych w każdym planie usługi Defender for Endpoint.

| Plan | Co jest dołączone |
|:---|:---|
| [Ochrona punktu końcowego w usłudze Microsoft Defender — Plan 1](defender-endpoint-plan-1.md) | <ul><li>[Ochrona następnej generacji](defender-endpoint-plan-1.md#next-generation-protection) (w tym oprogramowanie chroniące przed złośliwym kodem i oprogramowanie antywirusowe)</li><li>[Zmniejszanie obszaru podatnego na ataki](defender-endpoint-plan-1.md#attack-surface-reduction)</li><li> [Ręczne akcje odpowiedzi](defender-endpoint-plan-1.md#manual-response-actions)</li><li>[Scentralizowane zarządzanie](defender-endpoint-plan-1.md#centralized-management)</li><li>[Raporty zabezpieczeń](defender-endpoint-plan-1.md#reporting)</li><li>[Interfejsów api](defender-endpoint-plan-1.md#apis)</li><li>[Obsługa urządzeń z Windows 10, iOS, Android OS i macOS](defender-endpoint-plan-1.md#cross-platform-support)</li></ul>|
| [Defender for Endpoint Plan 2](microsoft-defender-endpoint.md) | Wszystkie możliwości planu 1 usługi Defender for Endpoint oraz:<ul><li>[Wykrywanie urządzeń](device-discovery.md)</li><li>[Spisz urządzeń](machines-view-overview.md)</li><li>[Podstawowe możliwości zarządzania lukami w zabezpieczeniach usługi Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md)</li><li>[Analiza zagrożeń](threat-analytics.md)</li><li>[Zautomatyzowane badanie i reagowanie](automated-investigations.md)</li><li>[Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md)</li><li>[Wykrywanie i reagowanie dotyczące punktów końcowych](overview-endpoint-detection-response.md)</li><li>[Microsoft Threat Experts](microsoft-threat-experts.md)</li><li>Obsługa [systemów](configure-endpoints-non-windows.md) [Windows](configure-endpoints.md) (klienta i serwera) i platform innych niż Windows (macOS, iOS, Android i Linux)</li></ul> |
| [Dodatek usługi Defender Vulnerability Management](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md) | Dodatkowe możliwości zarządzania lukami w zabezpieczeniach usługi Defender dla usługi Defender for Endpoint Plan 2:<ul><li>[Ocena punktów odniesienia zabezpieczeń](../defender-vulnerability-management/tvm-security-baselines.md)</li><li>[Blokuj aplikacje podatne na zagrożenia](../defender-vulnerability-management/tvm-block-vuln-apps.md)</li><li>[Rozszerzenia przeglądarki](../defender-vulnerability-management/tvm-browser-extensions.md)</li><li>[Ocena certyfikatów cyfrowych](../defender-vulnerability-management/tvm-certificate-inventory.md)</li><li>[Analiza udziału sieciowego](../defender-vulnerability-management/tvm-network-share-assessment.md)</li><li>Obsługa [systemów](configure-endpoints-non-windows.md) [Windows](configure-endpoints.md) (klienta i serwera) i platform innych niż Windows (macOS, iOS, Android i Linux)</li></ul> |
| [Microsoft 365 Defender](../defender/microsoft-365-defender.md) | Usługi obejmują: <ul><li>[Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)</li><li>[Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/defender-vulnerability-management.md)</li><li>[Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/overview.md)</li><li>[Microsoft Defender for Identity](/defender-for-identity/)</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/)</li></ul>|

> [!IMPORTANT]
> Autonomiczne wersje usług Defender for Endpoint Plan 1 i Plan 2 nie obejmują licencji serwera. Aby dołączyć serwery, takie jak punkty końcowe z systemem Windows Server lub Linux, musisz mieć usługę Defender for Servers Plan 1 lub Plan 2 w ramach [oferty usługi Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . Aby dowiedzieć się więcej. zobacz [Omówienie usługi Microsoft Defender dla serwerów](/azure/defender-for-cloud/defender-for-servers-introduction).

## <a name="mixed-licensing-scenarios"></a>Scenariusze licencjonowania mieszanego

Załóżmy, że Twoja organizacja korzysta z różnych subskrypcji zabezpieczeń punktu końcowego firmy Microsoft, takich jak Defender for Endpoint Plan 1 i Defender for Endpoint Plan 2. **Obecnie najwyższa funkcjonalna subskrypcja zabezpieczeń punktu końcowego firmy Microsoft ustawia środowisko dla twojej dzierżawy**. W tym przykładzie środowisko dzierżawy będzie mieć wartość Defender for Endpoint Plan 2 dla wszystkich użytkowników.

Można jednak **skontaktować się z pomocą techniczną i poprosić o zastąpienie środowiska dzierżawy**. Oznacza to, że możesz zażądać zastąpienia w celu zachowania środowiska usługi Defender for Endpoint Plan 1 dla wszystkich użytkowników. 

- Aby uzyskać szczegółowe informacje na temat licencji i postanowień dotyczących produktów, zobacz [Licencjonowanie i postanowienia dotyczące produktów dla subskrypcji platformy Microsoft 365](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/MCA).
- Aby uzyskać informacje o kontaktowaniu się z pomocą techniczną, zobacz [Kontakt z pomocą techniczną Ochrona punktu końcowego w usłudze Microsoft Defender](contact-support.md).

> [!TIP]
> Jeśli Twoja organizacja jest małą lub średnią firmą, zobacz następujące artykuły:
> - [Co to jest usługa Microsoft Defender dla Firm?](../defender-business/mdb-overview.md)
> - [Porównanie funkcji zabezpieczeń w planach platformy Microsoft 365 dla małych i średnich firm](../defender-business/compare-mdb-m365-plans.md).

## <a name="start-a-trial"></a>Rozpoczynanie wersji próbnej

- Aby wypróbować plan usługi Defender for Endpoint, przejdź do [strony rejestracji wersji próbnej usługi Defender for Endpoint](https://go.microsoft.com/fwlink/p/?LinkID=2168109).
- Aby wypróbować dodatek Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender dla usługi Defender for Endpoint Plan 2, odwiedź stronę [https://aka.ms/AddonPreviewTrial](https://aka.ms/AddonPreviewTrial). 

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do usługi Microsoft Security (oferty wersji próbnej)](https://www.microsoft.com/security/business/get-started/start-free-trial)

- [Microsoft Defender dla Firm](../defender-business/mdb-overview.md) (ochrona punktów końcowych dla małych i średnich firm)