---
title: Przygotowanie stanu zabezpieczeń do pierwszego incydentu
description: Skonfiguruj stan zabezpieczeń dzierżawy Microsoft 365 dla pierwszego incydentu w Microsoft 365 Defender.
keywords: zdarzenia, alerty, badanie, korelacja, atak, maszyny, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
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
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 0dbff9e88ed00dd8aa08fd64543266c3aef75d79
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664089"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>Przygotowanie stanu zabezpieczeń do pierwszego incydentu

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Przygotowanie do obsługi zdarzeń obejmuje skonfigurowanie wystarczającej ochrony sieci organizacji przed różnymi rodzajami zdarzeń zabezpieczeń. Aby zmniejszyć ryzyko zdarzeń związanych z bezpieczeństwem, National Institute of Standards and Technology (NIST) zaleca kilka praktyk w zakresie bezpieczeństwa, w tym oceny ryzyka, wzmocnienie zabezpieczeń hostów, bezpieczne konfigurowanie sieci i zapobieganie złośliwemu oprogramowaniu.

Microsoft 365 Defender może pomóc rozwiązać kilka aspektów zapobiegania zdarzeniom:

- Implementowanie struktury [Zero Trust](/security/zero-trust/)
- Określanie stanu zabezpieczeń przez przypisanie oceny za pomocą [wskaźnika bezpieczeństwa firmy Microsoft](microsoft-secure-score.md)
- Zapobieganie zagrożeniom za pomocą ocen luk w zabezpieczeniach w usłudze [Threat and Vulnerability Management](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Omówienie najnowszych zagrożeń bezpieczeństwa, dzięki czemu można przygotować się do nich za pomocą [analizy zagrożeń](threat-analytics.md)

## <a name="step-1-implement-zero-trust"></a>Krok nr 1. Implementowanie Zero Trust

[Zero Trust](/security/zero-trust/) jest zintegrowaną filozofią zabezpieczeń i kompleksową strategią, która uwzględnia złożony charakter każdego nowoczesnego środowiska, w tym pracowników mobilnych oraz użytkowników, urządzeń, aplikacji i danych, gdziekolwiek się znajdują. Udostępniając jedno okienko szkła do spójnego zarządzania wszystkimi wykryciami, Microsoft 365 Defender może ułatwić zespołowi ds. operacji zabezpieczeń [implementowanie zasad przewodnich](/security/zero-trust/#guiding-principles-of-zero-trust) Zero Trust.

Składniki Microsoft 365 Defender mogą wyświetlać naruszenia reguł, które zostały zaimplementowane w celu ustanowienia zasad dostępu warunkowego dla Zero Trust przez zintegrowanie danych z Ochrona punktu końcowego w usłudze Microsoft Defender  lub innych dostawców zabezpieczeń urządzeń przenośnych jako źródła informacji dla zasad zgodności urządzeń i implementacji zasad dostępu warunkowego opartego na urządzeniach.

Ryzyko urządzenia ma bezpośredni wpływ na zasoby dostępne dla użytkownika tego urządzenia. Odmowa dostępu do zasobów na podstawie określonych kryteriów jest głównym tematem Zero Trust, a Microsoft 365 Defender udostępnia informacje potrzebne do określenia kryteriów poziomu zaufania. Na przykład Microsoft 365 Defender może zapewnić poziom wersji oprogramowania urządzenia za pośrednictwem strony Zarządzanie zagrożeniami i lukami w zabezpieczeniach, podczas gdy zasady dostępu warunkowego ograniczają urządzenia, które mają nieaktualne lub wrażliwe wersje.

Automatyzacja jest kluczowym elementem implementowania i utrzymywania środowiska Zero Trust przy jednoczesnym zmniejszeniu liczby alertów, które mogą potencjalnie prowadzić do zdarzeń reagowania na zdarzenia (IR). Składniki Microsoft 365 Defender można zautomatyzować, takie jak [akcje korygowania](m365d-autoir.md) (znane jako badania dotyczące zdarzenia w portalu Microsoft 365 Defender), akcje powiadomień, a nawet tworzenie biletów pomocy technicznej, takich jak w [usłudze ServiceNow](https://microsoft.service-now.com/sp/).

## <a name="step-2-determine-your-organizations-security-posture"></a>Krok nr 2. Określanie stanu zabezpieczeń organizacji

Następnie organizacje mogą użyć wskaźnika [bezpieczeństwa firmy Microsoft](microsoft-secure-score.md) w Microsoft 365 Defender, aby określić aktualną postawę zabezpieczeń i rozważyć zalecenia dotyczące sposobu jej ulepszania. Im wyższy wynik, tym więcej zaleceń dotyczących zabezpieczeń i akcji poprawy zostało podjętych przez organizację. Rekomendacje dotyczące wskaźnika bezpieczeństwa można przyjmować w różnych produktach i umożliwić organizacjom podniesienie ich wyników jeszcze wyżej.

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="Strona Wskaźnik bezpieczeństwa firmy Microsoft w portalu Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-secure-score.png":::

## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>Krok nr 3. Ocena narażenia organizacji na luki w zabezpieczeniach

Zapobieganie incydentom może pomóc usprawnić działania operacji zabezpieczeń, aby skoncentrować się na bieżących krytycznych i ważnych zdarzeniach zabezpieczeń. Luki w zabezpieczeniach oprogramowania są często punktem wejścia, którym można zapobiec w przypadku ataków, które mogą prowadzić do kradzieży danych, utraty danych lub zakłóceń operacji biznesowych. Jeśli nie ma żadnych ataków, operacje zabezpieczeń muszą dążyć do osiągnięcia i utrzymania akceptowalnego poziomu [narażenia na luki w zabezpieczeniach](../defender-endpoint/tvm-exposure-score.md) w organizacji.

Aby sprawdzić postęp stosowania poprawek oprogramowania, odwiedź stronę [Zarządzanie zagrożeniami i lukami w zabezpieczeniach](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) w usłudze Defender for Endpoint, do której można uzyskać dostęp z Microsoft 365 Defender za pośrednictwem karty **Więcej zasobów**.

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="Strona Zagrożenia i luka w zabezpieczeniach w portalu Microsoft 365 Defender Portal" lightbox="../../media/first-incident-prepare/first-incident-vulnerability.png":::

## <a name="4-understand-emerging-threats"></a>4. Zrozumienie pojawiających się zagrożeń

Użyj [analizy zagrożeń](threat-analytics.md) w portalu Microsoft 365 Defender, aby być na bieżąco z bieżącym poziomem zagrożeń bezpieczeństwa. Eksperci badacze zabezpieczeń firmy Microsoft tworzą raporty, które szczegółowo opisują najnowsze zagrożenia cybernetyczne, dzięki czemu można zrozumieć, jak mogą one wpływać na subskrypcję Microsoft 365, urządzenia i użytkowników. Te raporty mogą obejmować:

- Aktywni aktorzy zagrożeń i ich kampanie
- Popularne i nowe techniki ataków
- Krytyczne luki w zabezpieczeniach
- Typowe powierzchnie ataków
- Powszechnie stosowane złośliwe oprogramowanie

Analiza zagrożeń analizuje również konfigurację i alerty, aby określić, jak bardzo jesteś zagrożony i czy istnieją aktywne alerty mające zastosowanie do raportu.

Możesz zaimplementować zalecenia dotyczące pojawiającego się zagrożenia, aby wzmocnić stan bezpieczeństwa i zminimalizować obszar obszaru podatnego na ataki.

Ustaw czas w harmonogramie, aby regularnie sprawdzać sekcję [Analiza zagrożeń](threat-analytics.md) w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [przykładowe operacje zabezpieczeń dla Microsoft 365 Defender](incidents-overview.md#example-security-operations-for-microsoft-365-defender).

## <a name="next-step"></a>Następny krok

Dowiedz się, jak [klasyfikować i analizować zdarzenia](first-incident-analyze.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Badanie zdarzeń](investigate-incidents.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
