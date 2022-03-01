---
title: Pilotażowa usługa Microsoft Defender dla tożsamości
description: Pilotażowa usługa Microsoft Defender for Identity, ustawianie wzorców, m.in. samouczki dotyczące renaissance, naruszonych poświadczeń, ruchu bocznego, dominowania domen i exfiltrowania alertów.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: c30e6d318801dbfb63f4bfb7b5bbaf64dad24ac0
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013687"
---
# <a name="pilot-microsoft-defender-for-identity"></a>Pilotażowa usługa Microsoft Defender dla tożsamości


**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 3 z 3](eval-defender-identity-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender dla tożsamości. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-identity-overview.md).

Aby skonfigurować pilotaż usługi Microsoft Defender dla tożsamości, należy wykonać poniższe czynności. Zalecenia nie obejmują konfigurowania grupy pilotażowej. Najlepszym rozwiązaniem jest zainstalowanie czujnika na wszystkich serwerach z systemem usług Usługi domenowe w usłudze Active Directory (AD DS) i usług federowanych Active Directory (AD FS).

![Procedura dodawania usługi Microsoft Defender dla tożsamości do środowiska oceny usługi Defender.](../../media/defender/m365-defender-identity-pilot-steps.png)

W poniższej tabeli opisano kroki na ilustracji.

- [Krok 1. Konfigurowanie zaleceń dotyczących wzorców dla środowiska tożsamości](#step-1-configure-benchmark-recommendations-for-your-identity-environment)
- [Krok 2. Wypróbuj możliwości — samouczki dotyczące identyfikowania i rozwiązywania problemów z różnymi typami ataków ](#step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types)

## <a name="step-1-configure-benchmark-recommendations-for-your-identity-environment"></a>Krok nr 1. Konfigurowanie rekomendacji wzorcowych dla środowiska tożsamości

Firma Microsoft udostępnia zalecenia dotyczące poziomu odniesienia zabezpieczeń dla klientów korzystających z usług firmy Microsoft w chmurze. Narzędzie [Azure Security Benchmark](/security/benchmark/azure/overview) (ASB) zawiera wstępnie sformułowane najlepsze rozwiązania i zalecenia dotyczące poprawy bezpieczeństwa obciążeń, danych i usług na platformie Azure.

Te zalecenia dotyczące poziomu odniesienia obejmują [plan bazowy zabezpieczeń platformy Azure dla programu Microsoft Defender dla tożsamości](/security/benchmark/azure/baselines/defender-for-identity-security-baseline). Wdrożenie tych zaleceń może zająć trochę czasu na zaplanowanie i zaimplementowanie. Ponieważ będą one znacznie zwiększały bezpieczeństwo Twojego środowiska tożsamości, nie powinny one uniemożliwiać dalszego oceniania i wdrażania usługi Microsoft Defender dla tożsamości. Te informacje zostały podane tutaj, aby uzyskać informacje na ten temat.

## <a name="step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types"></a>Krok nr 2. Wypróbuj możliwości — omów samouczki dotyczące identyfikowania i korygowania różnych typów ataków

Dokumentacja usługi Microsoft Defender dla tożsamości zawiera serię samouczków, w których osą się o proces identyfikowania i korygowania różnych typów ataków.

Wypróbuj samouczki dotyczące usługi Defender dla tożsamości:
- [Alerty renaissance](/defender-for-identity/reconnaissance-alerts)
- [Naruszone alerty poświadczeń](/defender-for-identity/compromised-credentials-alerts)
- [Alerty ruchu bocznego](/defender-for-identity/lateral-movement-alerts)
- [Alerty dotyczące dominującej domeny](/defender-for-identity/domain-dominance-alerts)
- [Alerty ex przekłoce](/defender-for-identity/exfiltration-alerts)
- [Badanie użytkownika](/defender-for-identity/investigate-a-user)
- [Badanie komputera](/defender-for-identity/investigate-a-computer)
- [Badanie ścieżek ruchu bocznego](/defender-for-identity/investigate-lateral-movement-path)
- [Badanie jednostek](/defender-for-identity/investigate-entity)

## <a name="next-steps"></a>Następne kroki

[Oceń program Microsoft Defender pod Office 365](eval-defender-office-365-overview.md)

Wróć do przeglądu [szacowania programu Microsoft Defender dla programu Office 365](eval-defender-office-365-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)