---
title: Alerty usługi adresatów zewnętrznych
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Alerty usługi adresatów zewnętrznych monitorują skrzynki pocztowe w chmurze, które osiągają limit przydziału skrzynki pocztowej.
ms.openlocfilehash: 931be51ee51bd5557633415004eed9a1c7e77888
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705220"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>Alerty usługi dotyczące wiadomości oczekujących na dostarczenie do adresatów zewnętrznych w Exchange Online wiadomości

Alerty usługi informują administratorów o kolejkowania poczty do adresatów zewnętrznych spoza Exchange Online. Alerty te mogą wymagać działań naprawczych spoza firmy Microsoft, ale mogą dostarczyć Ci informacji potrzebnych do działania naprawczego.

Alerty usługi są wyświetlane w centrum administracyjne platformy Microsoft 365. Aby wyświetlić te alerty usługi, przejdź do strony Kondycja usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**HealthService**</a> >  >  **Exchange Online** a następnie kliknij **kartę Aktywne** problemy. Nazwa tych alertów usługi to "Kolejkowanie wiadomości do adresatów zewnętrznych powyżej progów".

![Alert usługi o wiadomościach oczekujących na dostarczenie do adresatów zewnętrznych wyświetlany na Exchange Online nawigacyjnym monitorowania poczty.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

Po dwukrotnym kliknięciu alertu usługi zostanie wyświetlona strona wysuuwana podobna do poniższej.

![Zawartość alertu usługi dla wiadomości oczekujących na dostarczenie wiadomości do adresatów zewnętrznych.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>Co oznaczają te alerty usługi?

Alerty usługi dla wiadomości oczekujących na dostarczenie do adresatów zewnętrznych informują o tym, że wiadomości przeznaczone do adresatów spoza Exchange Online mogą być opóźnione. Kolejkowanie wiadomości może być spowodowane przez środowisko lokalne lub rozwiązanie do obsługi wiadomości lub dziennika innej firmy.

Oto kilka typowych przyczyn kolejkowania wiadomości do adresatów zewnętrznych. Jednak problemy powodujące te alerty usługi mogą nie być ograniczone do tych powodów.

- Zmiany w systemie DNS

- Nadmiarowe stawki za wysyłanie

- Lokalne agenty transferu wiadomości (MTA) lub rozwiązania do dziennika z małą i bezpłatną przestrzenią dyskową

- MTA w backpressure

- Problemy z siecią, w tym równoważenie obciążenia

- Problemy z certyfikatem

Każdy alert usługi zawiera zalecenia wysokiego poziomu dotyczące rozwiązywania problemu. Alert usługi wskazuje również liczbę wiadomości w kolejce w czasie alertu, domenę, do której wiadomości są w kolejce, oraz kod błędu SMTP skojarzony z większość komunikatów w kolejce.

Aby uzyskać więcej informacji na temat określania głównej przyczyny tych alertów usługi, zobacz Inteligencja [przepływu poczty e-mail w programie Exchange Online](../security/office-365-security/mail-flow-intelligence-in-office-365.md). Ten artykuł zawiera również sugerowane działania mające na celu naprawienie głównej przyczyny.

> [!NOTE]
> Firma Microsoft nie może uwzględnić wszystkich kodów błędów SMTP dostarczonych przez innych dostawców. W związku z tym od administratorów może być wymagane badanie kodów błędów specyficznych dla ich platformy MTA lub rozwiązań dziennika używanych przez ich organizację.

## <a name="more-information"></a>Więcej informacji

Jeśli Twoja organizacja ostatnio utworzyła lub zmieniła łączniki przepływu poczty e-mail w Twojej organizacji lokalnej lub Exchange Online, zobacz następujące artykuły, aby uzyskać więcej informacji.

- [Konfigurowanie przepływu poczty e-mail przy użyciu łączników w Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [Konfigurowanie łączników do rozsyłania poczty](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [Najlepsze rozwiązania dotyczące przepływu poczty e-mail](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [Szczegółowe informacje o przepływie poczty w Centrum & zgodności](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [Szczegółowe informacje o kolejkach na pulpicie nawigacyjnym przepływu poczty](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [Śledzenie wiadomości e-mail w programie Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
