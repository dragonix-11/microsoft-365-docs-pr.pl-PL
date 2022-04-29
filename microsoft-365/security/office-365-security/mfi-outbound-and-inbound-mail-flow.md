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
description: Administratorzy mogą dowiedzieć się więcej na temat szczegółowych informacji o przepływie poczty wychodzącej i przychodzącej na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności & zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f856e2b9a4829531966802f2594f26c19e6ab7e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131201"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>Szczegółowe informacje o przepływie poczty wychodzącej i przychodzącej w Centrum zgodności & zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Szczegółowe informacje o **przepływie poczty wychodzącej i przychodzącej** na [pulpicie nawigacyjnym przepływu poczty](mail-flow-insights-v2.md) w [Centrum zgodności & zabezpieczeń](https://protection.office.com) łączą informacje z [raportu łącznika](view-mail-flow-reports.md#connector-report) i poprzedniego **raportu przeglądu protokołu TLS** w jednym miejscu.

Widżet wyświetla szyfrowanie TLS używane na potrzeby połączenia, gdy komunikaty są dostarczane do i z organizacji. Połączenia nawiązywane z innymi usługami poczty e-mail są szyfrowane przez protokół TLS, gdy protokół TLS jest oferowany przez obie strony. Widżet oferuje migawkę z ostatniego tygodnia przepływu poczty.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png" alt-text="Widżet Przepływ poczty wychodzącej i przychodzącej na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności & zabezpieczeń" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png":::

Informacje w widżecie są związane z łącznikami i ochroną komunikatów protokołu TLS w Microsoft 365. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Konfigurowanie przepływu poczty przy użyciu łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [Jak Exchange Online używa protokołu TLS do zabezpieczania połączeń poczty e-mail](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [Informacje techniczne dotyczące szyfrowania w Microsoft 365](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>Komunikat chroniony podczas przesyłania (przez protokół TLS)

Po kliknięciu pozycji **Wyświetl szczegóły** w widżecie wysuwany **komunikat chroniony podczas przesyłania (przez protokół TLS)** pokazuje ochronę protokołu TLS dla komunikatów wprowadzających i opuszczających organizację.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png" alt-text="Wysuwany wysuwany komunikaty chronione podczas przesyłania (przez protokół TLS), który pojawia się po kliknięciu pozycji Wyświetl szczegóły w widżecie wychodzącej i przychodzącej poczty e-mail" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png":::

Obecnie protokół TLS 1.2 jest najbezpieczniejszą wersją protokołu TLS oferowaną przez Microsoft 365. Często musisz znać szyfrowanie TLS używane na potrzeby inspekcji zgodności. Prawdopodobnie nie masz bezpośredniej relacji z większością źródłowych i docelowych serwerów poczty e-mail (nie jesteś ich właścicielem, podobnie jak firma Microsoft), więc nie masz wielu opcji ulepszania szyfrowania TLS używanego przez te serwery.

Można jednak użyć [łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow), aby zapewnić najlepszą dostępną ochronę protokołu TLS dla komunikatów wysyłanych między serwerami poczty e-mail i Microsoft 365. Przepływ poczty między Microsoft 365 a własnymi serwerami lub serwerami poczty e-mail należącymi do partnerów jest często ważniejszy i bardziej poufny niż zwykłe wiadomości, dlatego należy zastosować dodatkowe zabezpieczenia i czujność do tych wiadomości.

Możesz uaktualnić lub naprawić własne serwery poczty e-mail, aby poprawić szyfrowanie TLS, które jest używane, lub skontaktować się z partnerami, aby zrobić to samo. **Raport łącznika** wyświetla zarówno wolumin przepływu poczty, jak i szyfrowanie TLS dla komunikatów korzystających z łączników Microsoft 365.

Możesz kliknąć link **do raportu łącznika** , aby przejść do [raportu łącznika](view-mail-flow-reports.md#connector-report). Jeśli wykryto skojarzony warunek, na stronie **raportu łącznika** mogą być dostępne następujące szczegółowe informacje:

- **Łącznik partnerów przychodzących widzi znaczący przepływ poczty TLS1.0**
- **Łącznik OnPremises dla ruchu przychodzącego widzi znaczący przepływ poczty TLS1.0**

W przypadku połączeń TLS 1.0 naprawdę musisz uaktualnić serwer poczty e-mail lub serwer partnera lub rozwiązać je, aby uniknąć problemów, gdy obsługa protokołu TLS 1.0 zostanie ostatecznie wycofana w Microsoft 365.

## <a name="see-also"></a>Zobacz też

Aby uzyskać informacje o innych szczegółowych informacjach na pulpicie nawigacyjnym przepływu poczty, zobacz [Szczegółowe informacje o przepływie poczty w Centrum zgodności & zabezpieczeń](mail-flow-insights-v2.md).
