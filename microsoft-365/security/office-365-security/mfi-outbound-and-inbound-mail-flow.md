---
title: Szczegółowe informacje o przepływie poczty wychodzącej i przychodzącej na pulpicie nawigacyjnym przepływu poczty
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: f2738dec-41b0-43c4-b814-84c0a4e45c6d
description: Administratorzy mogą dowiedzieć się więcej o przepływie poczty wychodzącej i przychodzącej na pulpicie nawigacyjnym przepływu poczty w Centrum zabezpieczeń & zgodności.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5de9c699a12a7c3f282c4e1752eb23c5842a8c5d
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679615"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>Szczegółowe informacje o przepływie poczty wychodzącej i przychodzącej w Centrum & zabezpieczeń i zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Szczegółowe **informacje o** przepływie poczty wychodzącej i przychodzącej na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi [& Security &](https://protection.office.com) łączą [](view-mail-flow-reports.md#connector-report) informacje z raportu łącznika i byłego raportu przeglądu **usługi TLS** w jednym miejscu.[](mail-flow-insights-v2.md)

W widżecie jest wyświetlane szyfrowanie TLS używane na poziomie połączenia, gdy wiadomości są dostarczane do i z organizacji. Połączenia ustanowione z innymi usługami poczty e-mail są szyfrowane przez szyfrowanie TLS, gdy szyfrowanie TLS jest oferowane przez obie strony. Widżet umożliwia migawkę przepływu poczty z ostatniego tygodnia.

![Widżet przychodzącego i wychodzącego przepływu poczty e-mail na pulpicie nawigacyjnym przepływu poczty w Centrum & zabezpieczeń.](../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png)

Informacje w widżecie są związane z łącznikami i ochroną wiadomości TLS w Microsoft 365. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Konfigurowanie przepływu poczty e-mail przy użyciu łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [Jak Exchange Online usługi TLS do zabezpieczania połączeń e-mail](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [Informacje techniczne dotyczące szyfrowania w Microsoft 365](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>Wiadomość chroniona podczas przesyłania (przez TLS)

Gdy klikniesz **pozycję Wyświetl szczegóły** w widżecie, wysuuwana wiadomość chroniona podczas przesyłania **(przez TLS)** pokazuje ochronę TLS dla wiadomości wprowadzanych i opuszczających organizację.

![Wiadomości chronione podczas przesyłania (przez TLS) wyświetlane po kliknięciu przycisku Wyświetl szczegóły na widżetze wychodzącej i przychodzącej poczty e-mail.](../../media/mfi-outbound-and-inbound-mail-flow-report-details.png)

Obecnie TLS 1.2 jest najbezpiecznszą wersją usługi TLS oferowaną przez firmę Microsoft 365. Często musisz znać szyfrowanie TLS, które jest używane do inspekcji zgodności. Prawdopodobnie nie masz bezpośredniej relacji z większości źródłowych i docelowych serwerów poczty e-mail (nie jesteś ich właścicielem ani firmą Microsoft), dlatego nie masz wielu opcji ulepszenia szyfrowania TLS używanego przez te serwery.

Można jednak [użyć łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow), aby zapewnić najlepszą dostępną ochronę usługi TLS dla wiadomości wysyłanych między serwerami poczty e-mail a Microsoft 365. Przepływ poczty między usługą Microsoft 365 a własnymi serwerami e-mail lub serwerami, które należą do Twoich partnerów, jest często ważniejszy i poufny niż zwykłe wiadomości, dlatego warto zastosować do tych wiadomości dodatkowe zabezpieczenia i zasadność.

Możesz uaktualnić lub naprawić własne serwery poczty e-mail, aby ulepszyć używane szyfrowanie TLS, lub sesyjnie z partnerami w celu ich rozwiązania. Raport **łącznika wyświetla** zarówno głośność przepływu poczty, jak i szyfrowanie TLS dla wiadomości, które używają Microsoft 365 łączników.

Możesz kliknąć link Raport **łącznika** , aby przejść do raportu [łącznika](view-mail-flow-reports.md#connector-report). Na stronie raportu łącznika mogą być dostępne następujące **informacje, jeśli** został wykryty skojarzony warunek:

- **Przychodzący łącznik partnera z znaczącym przepływem poczty TLS1.0**
- **Przychodzący łącznik OnPremises ze znaczącym przepływem poczty TLS1.0**

W przypadku połączeń TLS 1.0 naprawdę musisz uaktualnić lub rozwiązać problemy związane z serwerem poczty e-mail lub serwerem partnera, aby uniknąć problemów, gdy obsługa usługi TLS 1.0 zostanie w końcu przestarzała w programie Microsoft 365.

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).