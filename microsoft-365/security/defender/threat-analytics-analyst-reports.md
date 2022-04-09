---
title: Omówienie sekcji raportów analityków w analizie zagrożeń w Microsoft 365 Defender
ms.reviewer: ''
description: Dowiedz się więcej o sekcji raportów analityków każdego raportu analizy zagrożeń. Informacje na temat zagrożeń, środków zaradczych, wykrywania, zaawansowanych zapytań dotyczących wyszukiwania zagrożeń i nie tylko.
keywords: raport analityków, analiza zagrożeń, wykrywanie, zaawansowane zapytania dotyczące zagrożeń, środki zaradcze,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 396be53e4c238a8de21082f025762a1a4243b57c
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731147"
---
# <a name="understand-the-analyst-report-in-threat-analytics-in-microsoft-365-defender"></a>Omówienie raportu analityka w analizie zagrożeń w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Każdy [raport analizy zagrożeń](threat-analytics.md) zawiera sekcje dynamiczne i kompleksową pisemną sekcję o nazwie _raport analityka_. Aby uzyskać dostęp do tej sekcji, otwórz raport o śledzonym zagrożeniu i wybierz kartę **Raport analityka** .

:::image type="content" source="../../media/threat-analytics/ta_analystreport_mtp.png" alt-text="Sekcja raportu analityka raportu analizy zagrożeń" lightbox="../../media/threat-analytics/ta_analystreport_mtp.png":::

_Sekcja raportu analityka raportu analizy zagrożeń_

## <a name="scan-the-analyst-report"></a>Skanowanie raportu analityka

Każda sekcja raportu analityka ma na celu dostarczenie praktycznych informacji. Chociaż raporty są różne, większość raportów zawiera sekcje opisane w poniższej tabeli.

| Sekcja raportu | Opis |
|--|--|
| Streszczenie | Omówienie zagrożenia, w tym informacje o tym, kiedy po raz pierwszy zaobserwowano, jego motywacje, znaczące zdarzenia, główne cele oraz różne narzędzia i techniki. Te informacje umożliwiają dalszą ocenę sposobu określania priorytetów zagrożenia w kontekście branży, lokalizacji geograficznej i sieci. |
| Analizę | Informacje techniczne dotyczące zagrożeń, w tym szczegóły ataku i sposobu, w jaki osoby atakujące mogą korzystać z nowej techniki lub powierzchni ataku |
| Obserwowane techniki&CK MITRE ATT | Jak obserwowane techniki są mapowane na [strukturę ataków MITRE ATT&CK](https://attack.mitre.org/) |
| [Czynniki](#apply-additional-mitigations) | Rekomendacje, które mogą zatrzymać lub zmniejszyć wpływ zagrożenia. Ta sekcja zawiera również środki zaradcze, które nie są śledzone dynamicznie w ramach raportu analizy zagrożeń. |
| [Szczegóły wykrywania](#understand-how-each-threat-can-be-detected) | Specyficzne i ogólne wykrycia udostępniane przez rozwiązania zabezpieczeń firmy Microsoft, które mogą eksplorować działania lub składniki związane z zagrożeniem. |
| [Zaawansowane wyszukiwanie zagrożeń](#find-subtle-threat-artifacts-using-advanced-hunting) | [Zaawansowane zapytania dotyczące wyszukiwania zagrożeń](advanced-hunting-overview.md) w celu proaktywnego identyfikowania możliwych działań związanych z zagrożeniami. Większość zapytań jest dostarczanych w celu uzupełnienia wykrywania, szczególnie w przypadku lokalizowania potencjalnie złośliwych składników lub zachowań, których nie można dynamicznie ocenić jako złośliwych. |
| Informacje | Publikacje firmy Microsoft i innych firm, do których odwołują się analitycy podczas tworzenia raportu. Zawartość analizy zagrożeń jest oparta na danych zweryfikowanych przez badaczy firmy Microsoft. Informacje z publicznie dostępnych źródeł innych firm są wyraźnie identyfikowane jako takie. |
| Dziennik zmian | Czas publikacji raportu i czas wprowadzania istotnych zmian w raporcie. |

## <a name="apply-additional-mitigations"></a>Stosowanie dodatkowych środków zaradczych

Analiza zagrożeń dynamicznie śledzi [stan aktualizacji zabezpieczeń i bezpiecznych konfiguracji](threat-analytics.md#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices). Te informacje są dostępne jako wykresy i tabele na **karcie Ograniczenia ryzyka & ekspozycji** .

Oprócz tych śledzonych środków zaradczych raport analityków omawia również środki zaradcze, które _nie_ są dynamicznie monitorowane. Oto kilka przykładów ważnych środków zaradczych, które nie są śledzone dynamicznie:

- Blokuj wiadomości e-mail z załącznikami _lnk_ lub innymi podejrzanymi typami plików
- Losowe hasła administratora lokalnego
- Informowanie użytkowników końcowych o wiadomościach e-mail dotyczących wyłudzania informacji i innych wektorach zagrożeń
- Włączanie określonych [reguł zmniejszania obszaru ataków](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)

Chociaż możesz użyć karty **ekspozycji & środków zaradczych** , aby ocenić stan bezpieczeństwa przed zagrożeniem, zalecenia te umożliwiają podjęcie dodatkowych kroków w kierunku poprawy stanu bezpieczeństwa. Uważnie przeczytaj wszystkie wskazówki dotyczące ograniczania ryzyka w raporcie analityka i zastosuj je zawsze, gdy jest to możliwe.

## <a name="understand-how-each-threat-can-be-detected"></a>Dowiedz się, jak można wykryć każde zagrożenie

Raport analityków zawiera również funkcje wykrywania Program antywirusowy Microsoft Defender i _wykrywanie i reagowanie w punktach końcowych_ (EDR).

### <a name="antivirus-detections"></a>Wykrywanie oprogramowania antywirusowego

Te wykrycia są dostępne na urządzeniach z [włączoną Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10). Gdy te wykrycia wystąpią na urządzeniach dołączonych do Ochrona punktu końcowego w usłudze Microsoft Defender, wyzwalają one również alerty, które rozświetlają wykresy w raporcie.

>[!NOTE]
>Raport analityków zawiera również listę **wykrywania ogólnego** , które może identyfikować szeroki zakres zagrożeń, oprócz składników lub zachowań specyficznych dla śledzonego zagrożenia. Te wykrywania ogólne nie są odzwierciedlane na wykresach.

### <a name="endpoint-detection-and-response-edr-alerts"></a>Alerty dotyczące wykrywania i reagowania na punkty końcowe (EDR)

EDR alerty są wywoływane dla [urządzeń dołączonych do Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure). Te alerty zwykle opierają się na sygnałach zabezpieczeń zbieranych przez czujnik Ochrona punktu końcowego w usłudze Microsoft Defender i inne możliwości punktów końcowych, takie jak oprogramowanie antywirusowe, ochrona sieci, ochrona przed naruszeniami , które służą jako zaawansowane źródła sygnału.

Podobnie jak na liście wykrywania programów antywirusowych, niektóre alerty EDR są przeznaczone do ogólnego oznaczania podejrzanych zachowań, które mogą nie być skojarzone ze śledzonym zagrożeniem. W takich przypadkach raport wyraźnie zidentyfikuje alert jako "ogólny" i nie będzie miał wpływu na żaden z wykresów w raporcie.

### <a name="email-related-detections-and-mitigations"></a>Wykrywanie i środki zaradcze związane z pocztą e-mail

Wykrywanie i środki zaradcze związane z pocztą e-mail z Ochrona usługi Office 365 w usłudze Microsoft Defender są uwzględniane w raportach analityków oprócz danych punktu końcowego już dostępnych z Ochrona punktu końcowego w usłudze Microsoft Defender.

Informacje o uniemożliwionej próbie wysłania wiadomości e-mail zapewniają szczegółowe informacje na temat tego, czy organizacja była celem zagrożenia, które zostało rozwiązane w raporcie analityka, nawet jeśli atak został skutecznie zablokowany przed dostarczeniem lub dostarczeniem do folderu wiadomości-śmieci.

## <a name="find-subtle-threat-artifacts-using-advanced-hunting"></a>Znajdowanie subtelnych artefaktów zagrożeń przy użyciu zaawansowanego wyszukiwania zagrożeń

Chociaż wykrywanie umożliwia automatyczne identyfikowanie i zatrzymywanie śledzonych zagrożeń, wiele działań związanych z atakiem pozostawia subtelne ślady, które wymagają dodatkowej inspekcji. Niektóre działania związane z atakiem wykazują zachowania, które mogą być również normalne, więc ich dynamiczne wykrywanie może spowodować szum operacyjny, a nawet fałszywie dodatnie.

[Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md) zapewnia interfejs zapytań oparty na język zapytań Kusto, który upraszcza lokalizowanie subtelnych wskaźników aktywności zagrożeń. Umożliwia również wyświetlanie informacji kontekstowych i sprawdzanie, czy wskaźniki są połączone z zagrożeniem.

Zaawansowane zapytania dotyczące wyszukiwania zagrożeń w raportach analityków zostały sprawdzone przez analityków firmy Microsoft i są gotowe do uruchomienia w [zaawansowanym edytorze zapytań wyszukiwania zagrożeń](https://security.microsoft.com/advanced-hunting). Zapytania umożliwiają również tworzenie [niestandardowych reguł wykrywania](custom-detection-rules.md) , które wyzwalają alerty dla przyszłych dopasowań.

>[!NOTE]
> Analiza zagrożeń jest również dostępna w [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics). Nie ma jednak integracji danych między usługą Microsoft Defender dla Office i Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="related-topics"></a>Tematy pokrewne

- [Analiza zagrożeń — omówienie](threat-analytics.md)
- [Proaktywne znajdowanie zagrożeń przy użyciu zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Niestandardowe reguły wykrywania](custom-detection-rules.md)
