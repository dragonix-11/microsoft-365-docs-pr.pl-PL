---
title: Szczegółowe informacje o kolejkach na pulpicie nawigacyjnym przepływu poczty
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.custom: ''
ms.localizationpriority: medium
ms.assetid: 37640c80-ce6f-47e2-afd1-bc1d3c50e637
description: Administratorzy mogą dowiedzieć się, jak za pomocą widżetu Kolejki na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi & Security & monitorować nieudany przepływ poczty do ich lokalnych lub partnerskich organizacji przez łączniki ruchu wychodzącego.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 62da2d9654174bc2572a6d7cbb3acbd638757a6c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469476"
---
# <a name="queues-insight-in-the-security--compliance-center"></a>Szczegółowe informacje o kolejkach w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jeśli nie można wysyłać wiadomości z organizacji na lokalne lub partnerskie serwery poczty e-mail za pomocą łączników, są one w kolejce w Microsoft 365. Typowe przykłady przyczyn tego warunku to:

- Łącznik jest niepoprawnie skonfigurowany.
- W środowisku lokalnym zostały wprowadzone zmiany w sieci lub zaporze.

Microsoft 365 będzie ponawiana próby dostarczenia przez 24 godziny. Po 24 godzinach wiadomości wygasną i zostaną zwrócone do nadawców w raportach o niedo dostarczeniu (nazywanych również raportami o niedo dostarczenia lub wiadomościach zwróconych).

Jeśli liczba wiadomości e-mail w kolejce przekracza wstępnie zdefiniowany próg (wartość domyślna to 200 wiadomości), informacje są dostępne w następujących lokalizacjach:

- Szczegółowe **informacje o kolejkach** na [pulpicie nawigacyjnym przepływu](mail-flow-insights-v2.md) poczty w Centrum [& zgodności](https://protection.office.com). Aby uzyskać więcej informacji, zobacz sekcję [Kolejkowania w sekcji Pulpit](#queues-insight-in-the-mail-flow-dashboard) nawigacyjny przepływu poczty e-mail w tym artykule.

- Alert zostanie wyświetlony w menu Ostatnie **alerty na** pulpicie nawigacyjnym Alerty w Centrum [&](https://protection.office.com) zgodności (**pulpit nawigacyjny alertów** \> lub  <https://protection.office.com/alertsdashboard>).

  :::image type="content" source="../../media/mfi-queued-messages-alert.png" alt-text="Alerty w widoku Ostatnie na pulpicie nawigacyjnym Alerty w Centrum & zabezpieczeń" lightbox="../../media/mfi-queued-messages-alert.png":::


- Administratorzy otrzymają powiadomienie e-mail na podstawie konfiguracji domyślnych zasad alertów o nazwie Wiadomości **zostały opóźnione**. Aby skonfigurować ustawienia powiadomień dla tego alertu, zobacz następną sekcję.

  Aby uzyskać więcej informacji na temat zasad alertów, zobacz [Zasady alertów w Centrum zabezpieczeń & zgodności](../../compliance/alert-policies.md).

## <a name="customize-queue-alerts"></a>Dostosowywanie alertów kolejki

1. W Centrum [zabezpieczeń & zgodności](https://protection.office.com) przejdź do tematu **Zasady** \> **alertów alertów** lub otwórz menu <https://protection.office.com/alertpolicies>.

2. Na stronie **Zasady alertów** znajdź i wybierz zasady o nazwie **Wiadomości zostały opóźnione**.

3. W **wyświetlonym wysuwanym** czacie Wiadomość zostało opóźnione, możesz włączyć lub wyłączyć alert i skonfigurować ustawienia powiadomień.

   :::image type="content" source="../../media/mfi-queued-messages-alert-policy.png" alt-text="Szczegóły alertu Wiadomości zostały opóźnione" lightbox="../../media/mfi-queued-messages-alert-policy.png":::

   - **Stan**: Możesz włączyć lub wyłączyć alert.

   - **Limit adresatów wiadomości e-mail** **i powiadomień dziennych**: Kliknij **pozycję Edytuj** , aby skonfigurować następujące ustawienia:

4. Aby skonfigurować ustawienia powiadomień, kliknij pozycję **Edytuj**. W **wyświetlonym wysuwanych** zasadach Edytuj skonfiguruj następujące ustawienia:

   - **Wysyłanie powiadomień e-mail**: Wartość domyślna jest włączona.
   - **Adresaci poczty e-mail**: Wartość domyślna to **TenantAdmins**.
   - **Dzienny limit powiadomień**: Wartość domyślna to **Bez limitu**.
   - **Próg**: wartość domyślna to 200.

     :::image type="content" source="../../media/mfi-queued-messages-alert-policy-notification-settings.png" alt-text="Ustawienia powiadomień w alercie Wiadomości zostały opóźnione" lightbox="../../media/mfi-queued-messages-alert-policy-notification-settings.png":::

5. Po zakończeniu kliknij przycisk **Zapisz i** **zamknij**.

## <a name="queues-insight-in-the-mail-flow-dashboard"></a>Szczegółowe informacje o kolejkach na pulpicie nawigacyjnym przepływu poczty

Nawet jeśli wielkość wiadomości w kolejce nie przekroczyła progu i wygenerowano alert, nadal możesz użyć szczegółowych informacji o kolejkach na pulpicie nawigacyjnym przepływu [](mail-flow-insights-v2.md) poczty, aby wyświetlić wiadomości, które były w kolejce przez ponad godzinę, i podjąć działania, zanim liczba wiadomości w kolejce stanie się zbyt duża.

:::image type="content" source="../../media/mfi-queues-widget.png" alt-text="Widżet Kolejki na pulpicie nawigacyjnym przepływu poczty w Centrum & zabezpieczeń" lightbox="../../media/mfi-queues-widget.png":::

Jeśli klikniesz liczbę wiadomości na widżecie, zostanie wyświetlone **wysuwne** wysuwu Wiadomości w kolejce z następującymi informacjami:

- **Liczba wiadomości w kolejce**
- **Nazwa łącznika**: Wybierz nazwę łącznika, aby zarządzać łącznikiem w centrum administracyjnym usługi Exchange administracyjnego (EAC) w miejscu <https://admin.exchange.microsoft.com/#/connectors>.
- **Godzina rozpoczęcia kolejki**
- **Najstarsze wiadomości wygasły**
- **Serwer docelowy**
- **Ostatni adres IP**
- **Ostatni błąd**
- **Sposób rozwiązania: Dostępne są** typowe problemy i ich rozwiązania. Jeśli link **Napraw teraz** jest dostępny, kliknij go, aby rozwiązać problem. W przeciwnym razie kliknij dowolne dostępne linki, aby uzyskać więcej informacji na temat błędu i możliwych rozwiązań.

:::image type="content" source="../../media/mfi-queues-details.png" alt-text="The Details after clicking on the Queues insight in the Mail flow dashboard" lightbox="../../media/mfi-queues-details.png":::

Po kliknięciu przycisku Wyświetl kolejkę **w** szczegółach alertu Wiadomości są wyświetlane takie same wysuwu **.**

:::image type="content" source="../../media/mfi-queued-messages-alert-details.png" alt-text="Szczegóły alertu Wiadomości zostały opóźnione w Centrum zgodności & zabezpieczeń" lightbox="../../media/mfi-queued-messages-alert-details.png":::

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).
