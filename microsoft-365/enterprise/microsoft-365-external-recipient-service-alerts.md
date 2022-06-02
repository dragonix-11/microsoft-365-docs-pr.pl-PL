---
title: Alerty usługi adresatów zewnętrznych
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
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
description: Użyj alertów usługi adresatów zewnętrznych, aby monitorować skrzynki pocztowe w stanie wstrzymania, które osiągają limit przydziału skrzynki pocztowej.
ROBOTS: NOINDEX
ms.openlocfilehash: 2eac85b5a4b6f0f1c7c8737041edc9de50b5a074
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840458"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>Alerty usługi dotyczące komunikatów oczekujących na dostarczenie do adresatów zewnętrznych w ramach monitorowania Exchange Online

Alerty usługi informują administratorów o kolejkowaniu poczty do zewnętrznych adresatów spoza Exchange Online. Te alerty mogą wymagać akcji korygowania spoza firmy Microsoft, ale mogą dostarczyć informacji potrzebnych do skorygowania.

Te alerty usługi są wyświetlane w Centrum administracyjne platformy Microsoft 365. Aby wyświetlić te alerty usługi, przejdź do pozycji **Kondycja** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Kondycja usługi**</a> >  **Exchange Online** a następnie kliknij kartę **Aktywne problemy**. Nazwa tych alertów usługi to "Kolejkowanie komunikatów do zewnętrznych adresatów powyżej progów".

![Alert usługi dla komunikatów oczekujących na dostarczenie do adresatów zewnętrznych wyświetlany na pulpicie nawigacyjnym monitorowania Exchange Online.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

Po dwukrotnym kliknięciu alertu usługi zostanie wyświetlona strona wysuwana podobna do poniższej.

![Zawartość alertu usługi dla komunikatów oczekujących na dostarczenie do adresatów zewnętrznych.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>Co wskazują te alerty usługi?

Alerty usługi dotyczące komunikatów oczekujących na dostarczenie do adresatów zewnętrznych informują o tym, że wiadomości przeznaczone dla adresatów spoza Exchange Online mogą być opóźnione. Kolejkowanie komunikatów może być spowodowane przez środowisko lokalne lub rozwiązanie do obsługi komunikatów lub dzienników innych firm.

Poniżej przedstawiono niektóre typowe przyczyny kolejkowania komunikatów do adresatów zewnętrznych. Jednak problemy powodujące te alerty usługi nie mogą być ograniczone do tych przyczyn.

- Zmiany dns

- Nadmierne szybkości wysyłania

- Lokalni agenci transferu komunikatów (MTA) lub rozwiązania do rejestrowania z małą lub małą ilością wolnego miejsca na dysku

- MtAs w backpressure

- Problemy z siecią, w tym moduły równoważenia obciążenia

- Problemy z certyfikatem

Każdy alert usługi zawiera zalecenia wysokiego poziomu dotyczące korygowania problemu. Alert usługi wskazuje również liczbę komunikatów umieszczonych w kolejce w czasie alertu, domenę, do której są umieszczane komunikaty w kolejce, oraz kod błędu SMTP skojarzony z większością komunikatów w kolejce.

Aby uzyskać więcej informacji na temat określania głównej przyczyny tych alertów usługi, zobacz [Analiza przepływu poczty w Exchange Online](../security/office-365-security/mail-flow-intelligence-in-office-365.md). Ten artykuł zawiera również sugerowane akcje naprawy głównej przyczyny.

> [!NOTE]
> Firma Microsoft nie może uwzględnić każdego kodu błędu SMTP dostarczonego przez dostawców innych firm. W związku z tym administratorzy mogą być zobowiązani do zbadania kodów błędów specyficznych dla ich rozwiązań mta lub dzienników używanych przez organizację.

## <a name="more-information"></a>Więcej informacji

Jeśli Twoja organizacja niedawno utworzyła lub zmieniła łączniki przepływu poczty w organizacji lokalnej lub Exchange Online, zobacz następujące artykuły, aby uzyskać więcej informacji.

- [Konfigurowanie przepływu poczty przy użyciu łączników w Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [Konfigurowanie łączników do kierowania poczty](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [Najlepsze rozwiązania dotyczące przepływu poczty](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [Szczegółowe informacje o przepływie poczty w Centrum zgodności & zabezpieczeń](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [Szczegółowe informacje o kolejkach na pulpicie nawigacyjnym przepływu poczty](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [Śledzenie wiadomości e-mail w Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
