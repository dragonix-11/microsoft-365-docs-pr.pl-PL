---
title: Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender
description: Zapoznaj się z omówieniem możliwości zautomatyzowanego badania i reagowania, nazywanych również samonaprawiającym się, w Microsoft 365 Defender
keywords: zautomatyzowane, badanie, alert, wyzwalacz, akcja, korygowanie, samonaprawianie
search.appverid: met150
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
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 332802150235ec6f47c4bdea34b34edb94ea1b90
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731334"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Jeśli Twoja organizacja korzysta z [Microsoft 365 Defender](microsoft-365-defender.md), twój zespół ds. operacji zabezpieczeń otrzymuje alert w portalu Microsoft 365 Defender za każdym razem, gdy zostanie wykryte złośliwe lub podejrzane działanie lub artefakt. Biorąc pod uwagę pozornie niekończący się przepływ zagrożeń, które mogą wystąpić, zespoły ds. zabezpieczeń często stoją przed wyzwaniem rozwiązania problemu dużej liczby alertów. Na szczęście Microsoft 365 Defender obejmuje funkcje zautomatyzowanego badania i reagowania (AIR), które mogą pomóc zespołowi ds. operacji zabezpieczeń w wydajniejszym i wydajniejszym reagowaniu na zagrożenia.

Ten artykuł zawiera omówienie funkcji AIR i zawiera linki do następnych kroków i dodatkowych zasobów.

## <a name="how-automated-investigation-and-self-healing-works"></a>Jak działa zautomatyzowane badanie i samonaprawianie

W miarę wyzwalania alertów zabezpieczeń zespół ds. operacji zabezpieczeń musi przeanalizować te alerty i podjąć kroki w celu ochrony organizacji. Określanie priorytetów i badanie alertów może być bardzo czasochłonne, zwłaszcza gdy nowe alerty ciągle przychodzą podczas badania. Zespoły ds. operacji zabezpieczeń mogą czuć się przytłoczone dużą ilością zagrożeń, które muszą monitorować i przed nimi chronić. Zautomatyzowane możliwości badania i reagowania, dzięki samonaprawianiu się, w Microsoft 365 Defender mogą pomóc.

Obejrzyj poniższy film wideo, aby zobaczyć, jak działa samonaprawianie: <p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

W Microsoft 365 Defender automatyczne badanie i reagowanie za pomocą funkcji samonaprawiania działa na urządzeniach, w wiadomościach e-mail & zawartości i tożsamościach.
 
> [!TIP]
> W tym artykule opisano, jak działa zautomatyzowane badanie i reagowanie. Aby skonfigurować te możliwości, zobacz [Konfigurowanie funkcji automatycznego badania i reagowania w Microsoft 365 Defender](m365d-configure-auto-investigation-response.md).

## <a name="your-own-virtual-analyst"></a>Twój własny analityk wirtualny

Imagine posiadanie wirtualnego analityka w zespole ds. operacji zabezpieczeń warstwy 1 lub 2. Analityk wirtualny naśladuje idealne kroki wykonywane przez operacje zabezpieczeń w celu zbadania i skorygowania zagrożeń. Analityk wirtualny może pracować 24x7, z nieograniczoną pojemnością, i podjąć znaczne obciążenie badań i korygowania zagrożeń. Taki wirtualny analityk może znacznie skrócić czas reagowania, zwalniając zespół ds. operacji zabezpieczeń w przypadku innych ważnych zagrożeń lub projektów strategicznych. Jeśli ten scenariusz brzmi jak science fiction, to nie jest! Taki wirtualny analityk jest częścią pakietu Microsoft 365 Defender, a jego nazwa to *zautomatyzowane badanie i reagowanie*.

Funkcje zautomatyzowanego badania i reagowania umożliwiają zespołowi ds. operacji zabezpieczeń znaczne zwiększenie zdolności organizacji do radzenia sobie z alertami zabezpieczeń i zdarzeniami. Dzięki zautomatyzowanemu badaniu i reagowaniu możesz zmniejszyć koszty prowadzenia działań związanych z badaniem i reagowaniem oraz jak najlepiej wykorzystać pakiet ochrony przed zagrożeniami. Funkcje zautomatyzowanego badania i reagowania ułatwiają zespołowi ds. operacji zabezpieczeń:

1. Określanie, czy zagrożenie wymaga działania.
2. Podejmowanie (lub zalecanie) wszelkich niezbędnych akcji korygowania.
3. Określanie, czy i jakie inne badania powinny zostać przeprowadzone.
4. Powtarzanie procesu w razie potrzeby w przypadku innych alertów.

## <a name="the-automated-investigation-process"></a>Zautomatyzowany proces badania

Alert tworzy zdarzenie, które może rozpocząć zautomatyzowane badanie. Zautomatyzowane dochodzenie skutkuje werdyktem dla każdego dowodu. Werdykty mogą być:
- *Złośliwy*
- *Podejrzanych* 
- *Nie znaleziono zagrożeń* 

Identyfikowane są akcje korygowania dla złośliwych lub podejrzanych jednostek. Przykłady akcji korygowania obejmują:

- Wysyłanie pliku do kwarantanny
- Zatrzymywanie procesu
- Izolowanie urządzenia
- Blokowanie adresu URL 
- Inne akcje

Aby uzyskać więcej informacji, zobacz [Akcje korygowania w Microsoft 365 Defender](m365d-remediation-actions.md).

W zależności od tego [, jak zautomatyzowane możliwości badania i reagowania są skonfigurowane](m365d-configure-auto-investigation-response.md) dla Organizacji, akcje korygowania są wykonywane automatycznie lub tylko po zatwierdzeniu przez zespół ds. operacji zabezpieczeń. Wszystkie akcje, oczekujące lub ukończone, są wyświetlane w [Centrum akcji](m365d-action-center.md).

Gdy badanie jest uruchomione, wszelkie inne powiązane alerty, które pojawiają się, są dodawane do badania do czasu jego zakończenia. Jeśli jednostka, których dotyczy problem, jest widoczna gdzie indziej, zautomatyzowane badanie rozszerza swój zakres, aby uwzględnić tę jednostkę, a proces badania powtarza się. 

W Microsoft 365 Defender każde zautomatyzowane badanie koreluje sygnały między Microsoft Defender for Identity, Ochrona punktu końcowego w usłudze Microsoft Defender i Ochrona usługi Office 365 w usłudze Microsoft Defender, jak podsumowano w poniższej tabeli: 

|Podmioty |Usługi ochrony przed zagrożeniami  |
|:---------|:---------|
|Urządzenia (nazywane również punktami końcowymi lub maszynami) |[Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/automated-investigations.md) |      
|Lokalni użytkownicy usługi Active Directory, zachowanie jednostki i działania     |[Defender for Identity](/azure-advanced-threat-protection/what-is-atp) |      
|Zawartość wiadomości e-mail (wiadomości e-mail, które mogą zawierać pliki i adresy URL)     |[Ochrona usługi Office 365 w usłudze Defender](../office-365-security/defender-for-office-365.md) |

> [!NOTE]
> Nie każdy alert wyzwala zautomatyzowane badanie i nie każde badanie powoduje zautomatyzowane akcje korygowania. Zależy to od tego, jak zautomatyzowane badanie i reagowanie jest skonfigurowane dla Twojej organizacji. Zobacz [Konfigurowanie możliwości zautomatyzowanego badania i reagowania](m365d-configure-auto-investigation-response.md).

## <a name="viewing-a-list-of-investigations"></a>Wyświetlanie listy badań

Aby wyświetlić badania, przejdź do strony **Zdarzenia** . Wybierz zdarzenie, a następnie wybierz kartę **Badania** . Aby dowiedzieć się więcej, zobacz [Szczegóły i wyniki zautomatyzowanego badania](m365d-autoir-results.md).

## <a name="training-for-security-analysts"></a>Szkolenia dla analityków zabezpieczeń

Skorzystaj z tego modułu szkoleniowego z usługi Microsoft Learn, aby zrozumieć, w jaki sposób Microsoft 365 Defender korzysta z automatycznego samonaprawiania na potrzeby badania i reagowania na zdarzenia.

|Szkolenia:|Automatyzowanie samonaprawiania za pomocą Microsoft 365 Defender|
|---|---|
|![Automatyzuj samonaprawianie za pomocą ikony trenowania Microsoft 365 Defender.](../../media/m365d-autoir/m365-defender-auto-self-healing.svg)| Microsoft 365 Defender używa sztucznej inteligencji do automatyzowania korygowania zdarzeń, pomagając zespołowi ds. operacji zabezpieczeń efektywniej i wydajniej rozwiązywać problemy z zagrożeniami. <p> 11 min — 5 jednostek |

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/defender-self-healing/)

## <a name="next-steps"></a>Następne kroki

- [Zapoznaj się z wymaganiami wstępnymi dotyczącymi zautomatyzowanego badania i reagowania](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Konfigurowanie zautomatyzowanego badania i reagowania dla organizacji](m365d-configure-auto-investigation-response.md)
- [Dowiedz się więcej o Centrum akcji](m365d-action-center.md)
