---
title: Opis sekcji raportu analityka w analizie zagrożeń w programie Microsoft 365 Defender
ms.reviewer: ''
description: Dowiedz się więcej o sekcji raportu analityka dla każdego raportu analizy zagrożeń. Zrozumienie, jak zapewnia informacje o zagrożeniach, środki zaradcze, wykrywanie, zaawansowane zapytania myśliwskie i nie tylko.
keywords: raport analityka, analiza zagrożeń, wykrywanie, zaawansowane zapytania chowe, środki zaradcze,
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
ms.openlocfilehash: 3821f0738984c856650e8a455c0d83563a148a2a
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010380"
---
# <a name="understand-the-analyst-report-in-threat-analytics-in-microsoft-365-defender"></a>Analiza raportu analityka w analizie zagrożeń w programie Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

> Chcesz doświadczyć Microsoft 365 Defender? Można go [ocenić w środowisku laboratoryjnym](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) lub [uruchomić projekt pilotażowy w środowisku produkcyjnym](m365d-pilot.md?ocid=cx-evalpilot).
>

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Każdy [raport analizy zagrożeń zawiera](threat-analytics.md) dynamiczne sekcje i pełną pisemną sekcję nazywaną _raportem analityka_. Aby uzyskać dostęp do tej sekcji, otwórz raport o śledzeniu zagrożeń i wybierz **kartę Raport analityka** .

![Obraz sekcji raportu analityka w raporcie analizy zagrożeń.](../../media/threat-analytics/ta_analystreport_mtp.png)

_Sekcja raportu analityka w raporcie analizy zagrożeń_

## <a name="scan-the-analyst-report"></a>Skanowanie raportu analityka 
Każda sekcja raportu analityka ma na celu dostarczenie informacji z akcjami. Raporty mogą się różnić, jednak większość raportów zawiera sekcje opisane w poniższej tabeli.

| Sekcja Raport | Opis |
|--|--|
| Podsumowanie dla kierownictwa | Omówienie zagrożenia, łącznie z jego motywacją, ważnymi zdarzeniami, głównymi celami oraz odrębnymi narzędziami i technikami. Możesz użyć tych informacji do dalszej oceny sposobu ustalania priorytetów zagrożeń w kontekście swojej branży, lokalizacji geograficznej i sieci. |
| Analiza | Informacje techniczne dotyczące zagrożeń, w tym szczegóły ataków i sposób, w jaki atakujący mogą korzystać z nowej techniki lub powierzchni ataków | 
| Obserwowane techniki CK&ATT MITRE | Jak obserwowane techniki są mapowanie na platformę ataków [miTRE ATT&CK](https://attack.mitre.org/) | 
| [Środki zaradcze](#apply-additional-mitigations) | Rekomendacje, które mogą zatrzymać lub zmniejszyć wpływ zagrożenia. Ta sekcja zawiera również środki zaradcze, które nie są dynamicznie śledzone w ramach raportu analizy zagrożeń. |
| [Szczegóły wykrywania](#understand-how-each-threat-can-be-detected) | Konkretne i ogólne wykrywanie udostępniane przez rozwiązania zabezpieczeń firmy Microsoft, które mogą powierzchnić aktywność lub składniki skojarzone z zagrożeniami. | 
| [Zaawansowane łowy](#find-subtle-threat-artifacts-using-advanced-hunting) | [Zaawansowane zapytania wyszukiwania w](advanced-hunting-overview.md) celu aktywnej identyfikacji możliwej aktywności podszywowej. Większość zapytań stanowi uzupełnienie wykrywania, zwłaszcza w celu lokalizowania potencjalnie złośliwych składników lub zachowań, których nie można dynamicznie ocenić jako złośliwych. | 
| Informacje | Podczas tworzenia raportu są do nich odwoływowane publikacje firmy Microsoft i innych firm, do których odwołyowali się analitycy. Zawartość analizy zagrożeń jest oparta na danych weryfikowanych przez firmę Microsoft. Informacje z publicznie dostępnych źródeł innych firm są wyraźnie określone jako takie. | 
| Dziennik zmian | Czas opublikowania raportu i istotne zmiany w raporcie. |

## <a name="apply-additional-mitigations"></a>Stosowanie dodatkowych środków zaradczych
Analiza zagrożeń dynamicznie śledzi [stan aktualizacji zabezpieczeń i bezpiecznych konfiguracji](threat-analytics.md#mitigations-review-list-of-mitigations-and-the-status-of-your-devices). Te informacje są dostępne jako wykresy i tabele na karcie **Środki zaradcze** .

Oprócz tych śledzone środki zaradcze, raport analityka omawia również środki zaradcze, które nie _są dynamicznie_ monitorowane. Oto kilka przykładów istotnych środków zaradczych, które nie są dynamicznie śledzone:

- Blokowanie wiadomości e-mail _z załącznikami lnk_ lub innymi podejrzanymi typami plików
- Randomize lokalnych haseł administratora
- Informacje dla użytkowników końcowych o wiadomościach e-mail wyłudzających informacje i innych wektorach zagrożeń
- Włączanie określonych [reguł zmniejszania powierzchni ataków](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)

Karta Środki zaradcze  umożliwia ocenę działania zabezpieczeń pod względem zagrożenia, ale te zalecenia pozwalają podjąć dodatkowe kroki w celu poprawy poziomu zabezpieczeń. Dokładnie przeczytaj wszystkie wskazówki dotyczące złagodzenia wpływu w raporcie analityka i zastosuj je, gdy tylko jest to możliwe.

## <a name="understand-how-each-threat-can-be-detected"></a>Zrozumienie, jak można wykrywać poszczególne zagrożenia
Raport analityka udostępnia również wykrywanie z funkcji Program antywirusowy Microsoft Defender i _wykrywanie i reagowanie w punktach końcowych_ (EDR).

### <a name="antivirus-detections"></a>Wykrywanie oprogramowania antywirusowego
Te wykrywanie jest dostępne na urządzeniach z [Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) włączone. Wykrywanie urządzeń, które zostały podłączone do programu Microsoft Defender for Endpoint, powoduje również wyzwolenie alertów, które zasłaniają wykresy w raporcie.

>[!NOTE]
>W raporcie analityka są również **wyszczególnione** ogólne wykrywanie, które mogą zidentyfikować szeroki zakres zagrożeń, a także składniki i zachowania specyficzne dla śledzenia zagrożeń. Te wykrywanie ogólne nie jest odzwierciedlane na wykresach.

### <a name="endpoint-detection-and-response-edr-alerts"></a>Wykrywanie punktu końcowego i alerty odpowiedzi (EDR)
EDR dla urządzeń podłączonych do programu [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure). Alerty te są zasadniczo zależne od sygnałów zabezpieczeń zbieranych przez czujnik programu Microsoft Defender for Endpoint i inne funkcje punktu końcowego, takie jak oprogramowanie antywirusowe, ochrona sieci i ochrona przed naruszeniami, które służą jako zaawansowane źródła sygnału.

Podobnie jak lista wykrywania oprogramowania antywirusowego niektóre alerty EDR zaprojektowane w celu ogólnego oznaczania podejrzanych zachowań, które mogą nie być skojarzone z śledzoną zagrożeniami. W takich przypadkach alert będzie wyraźnie identyfikowany jako "ogólny" i nie będzie miał wpływu na żadne wykresy w raporcie.

### <a name="email-related-detections-and-mitigations"></a>Wykrywanie i środki zaradcze związane z pocztą e-mail
Wykrywania i środki zaradcze związane z pocztą e-mail z usługi Microsoft Defender dla programu Office 365 są uwzględniane w raportach analityków, a także dane końcowe dostępne już w programie Microsoft Defender dla punktu końcowego. 

Informacje o próbach zablokowania wiadomości e-mail zawierają szczegółowe informacje na temat tego, czy twoja organizacja była obiektem docelowym zagrożenia w raporcie analityka, nawet jeśli atak został skutecznie zablokowany przed dostarczeniem lub dostarczeniem do folderu wiadomości-śmieci.

## <a name="find-subtle-threat-artifacts-using-advanced-hunting"></a>Znajdowanie subtelnych artefaktów zagrożeń podczas zaawansowanego chłonia
Wykrywanie pozwala automatycznie identyfikować i zatrzymywać śledzone zagrożenia, jednak wiele działań ataków pozostawia delikatne śledzenia wymagające dodatkowej inspekcji. Niektóre działania ataków są w eksponowane zachowaniach, które także mogą być normalne, więc dynamiczne wykrywanie ich może powodować szum operacyjny lub nawet wyniki fałszywie dodatnie.

[Zaawansowane wyszukiwania](advanced-hunting-overview.md) zapewnia interfejs zapytania oparty na języku Kusto Query, który upraszcza wyszukiwanie subtelnych wskaźników zagrożeń. Umożliwia to również powierzchnię informacji kontekstowych i sprawdzanie, czy wskaźniki są połączone z zagrożeniami.

Zaawansowane zapytania myśliwskie w raportach analityków zostały przesłoone przez analityków firmy Microsoft i są gotowe do pracy w zaawansowanym [edytorze zapytań myśliwnych](https://security.microsoft.com/advanced-hunting). Za pomocą tych zapytań można też tworzyć niestandardowe [](custom-detection-rules.md) reguły wykrywania, które powodują wyzwalanie alertów dotyczących przyszłych dopasowania.


>[!NOTE]
> Analiza zagrożeń jest również dostępna w programie [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics). Nie ma jednak integracji danych między programem Microsoft Defender for Office a programem Microsoft Defender for Endpoint, który Microsoft 365 Defender analizy zagrożeń.


## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie analizy zagrożeń](threat-analytics.md)
- [Aktywne wyszukiwanie zagrożeń dzięki zaawansowanym narzędziom do wyszukiwania](advanced-hunting-overview.md) 
- [Niestandardowe reguły wykrywania](custom-detection-rules.md)