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
description: Administratorzy mogą dowiedzieć się, jak używać widżetu Kolejki na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi Security & w celu monitorowania nieudanego przepływu poczty do organizacji lokalnych lub partnerskich za pośrednictwem łączników wychodzących.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 146ce26c32f1ff80a451b85fd343990db547a131
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972656"
---
# <a name="queues-insight-in-the-security--compliance-center"></a>Szczegółowe informacje o kolejkach w Centrum zgodności & zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Gdy nie można wysyłać komunikatów z organizacji do lokalnych lub partnerskich serwerów poczty e-mail przy użyciu łączników, komunikaty są umieszczane w kolejce w Microsoft 365. Typowe przykłady, które powodują ten warunek, to:

- Łącznik jest niepoprawnie skonfigurowany.
- Nastąpiła zmiana sieci lub zapory w środowisku lokalnym.

Microsoft 365 będzie nadal ponawiać próbę dostarczenia przez 24 godziny. Po upływie 24 godzin komunikaty wygasną i zostaną zwrócone nadawcom w raportach o braku dostawy (nazywanych również komunikatami OPR lub komunikatami odrzuceń).

Jeśli wolumin wiadomości e-mail w kolejce przekroczy wstępnie zdefiniowany próg (wartość domyślna to 200 komunikatów), informacje są dostępne w następujących lokalizacjach:

- Szczegółowe informacje **o kolejkach na pulpicie nawigacyjnym** [przepływu poczty](mail-flow-insights-v2.md) w [Centrum zgodności & zabezpieczeń](https://protection.office.com). Aby uzyskać więcej informacji, zobacz [szczegółowe informacje o kolejkach w sekcji Pulpit nawigacyjny przepływu poczty](#queues-insight-in-the-mail-flow-dashboard) w tym artykule.

- Alert jest wyświetlany w obszarze **Ostatnie alerty** pulpit nawigacyjny Alerty w [Centrum zgodności & zabezpieczeń](https://protection.office.com) (**pulpit nawigacyjny** **alertów** \> lub <https://protection.office.com/alertsdashboard>).

  :::image type="content" source="../../media/mfi-queued-messages-alert.png" alt-text="Ostatnie alerty na pulpicie nawigacyjnym Alerty w Centrum zgodności & zabezpieczeń" lightbox="../../media/mfi-queued-messages-alert.png":::

- Administratorzy otrzymają powiadomienie e-mail na podstawie konfiguracji domyślnych zasad alertów o nazwie **Komunikaty zostały opóźnione**. Aby skonfigurować ustawienia powiadomień dla tego alertu, zobacz następną sekcję.

  Aby uzyskać więcej informacji na temat zasad alertów, zobacz [Zasady alertów w Centrum zgodności & zabezpieczeń](../../compliance/alert-policies.md).

## <a name="customize-queue-alerts"></a>Dostosowywanie alertów kolejki

1. W [Centrum zgodności & zabezpieczeń](https://protection.office.com) przejdź do pozycji **Alerty Zasady alertów**  \> lub otwórz .<https://protection.office.com/alertpolicies>

2. Na stronie **Zasady alertów** znajdź i wybierz zasady o nazwie **Komunikaty zostały opóźnione**.

3. W wyświetlonym menu wysuwnym Komunikat, który **został opóźniony** , możesz włączyć lub wyłączyć alert i skonfigurować ustawienia powiadomień.

   :::image type="content" source="../../media/mfi-queued-messages-alert-policy.png" alt-text="Szczegóły alertu Komunikaty zostały opóźnione" lightbox="../../media/mfi-queued-messages-alert-policy.png":::

   - **Stan**: możesz włączyć lub wyłączyć alert.

   - **Adresaci wiadomości e-mail** i **dzienny limit powiadomień**: kliknij przycisk **Edytuj** , aby skonfigurować następujące ustawienia:

4. Aby skonfigurować ustawienia powiadomień, kliknij przycisk **Edytuj**. W wyświetlonym wysuwu **Edytuj zasady** skonfiguruj następujące ustawienia:

   - **Wysyłanie powiadomień e-mail**: wartość domyślna jest włączona.
   - **Adresaci wiadomości e-mail**: wartość domyślna to **TenantAdmins**.
   - **Dzienny limit powiadomień**: wartość domyślna **to Brak limitu**.
   - **Próg**: wartość domyślna to 200.

     :::image type="content" source="../../media/mfi-queued-messages-alert-policy-notification-settings.png" alt-text="Ustawienia powiadomień w alertach zostały opóźnione" lightbox="../../media/mfi-queued-messages-alert-policy-notification-settings.png":::

5. Po zakończeniu kliknij pozycję **Zapisz** i **zamknij**.

## <a name="queues-insight-in-the-mail-flow-dashboard"></a>Szczegółowe informacje o kolejkach na pulpicie nawigacyjnym przepływu poczty

Nawet jeśli wolumin komunikatów w kolejce nie przekroczył progu i wygenerował alert, możesz nadal używać **szczegółowych informacji o kolejkach** na [pulpicie nawigacyjnym przepływu poczty](mail-flow-insights-v2.md) , aby wyświetlić komunikaty, które były umieszczane w kolejce przez ponad godzinę, i podjąć działania, zanim liczba komunikatów w kolejce stanie się zbyt duża.

:::image type="content" source="../../media/mfi-queues-widget.png" alt-text="Widżet Kolejki na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności & zabezpieczeń" lightbox="../../media/mfi-queues-widget.png":::

Jeśli klikniesz liczbę komunikatów w widżecie, zostanie wyświetlone okno wysuwane **Komunikaty w kolejce** z następującymi informacjami:

- **Liczba komunikatów w kolejce**
- **Nazwa łącznika**: wybierz nazwę łącznika, aby zarządzać łącznikiem w centrum administracyjnym Exchange (EAC) pod adresem <https://admin.exchange.microsoft.com/#/connectors>.
- **Czas rozpoczęcia kolejki**
- **Najstarsze komunikaty wygasły**
- **Serwer docelowy**
- **Ostatni adres IP**
- **Ostatni błąd**
- **Jak rozwiązać**: dostępne są typowe problemy i rozwiązania. Jeśli link **Napraw teraz** jest dostępny, kliknij go, aby rozwiązać problem. W przeciwnym razie kliknij wszystkie dostępne linki, aby uzyskać więcej informacji o błędzie i możliwych rozwiązaniach.

:::image type="content" source="../../media/mfi-queues-details.png" alt-text="Szczegóły po kliknięciu szczegółowych informacji o kolejkach na pulpicie nawigacyjnym przepływu poczty" lightbox="../../media/mfi-queues-details.png":::

Ten sam wysuwany element jest wyświetlany po kliknięciu pozycji **Wyświetl kolejkę** w szczegółach alertu **Komunikaty zostały opóźnione** .

:::image type="content" source="../../media/mfi-queued-messages-alert-details.png" alt-text="Szczegóły alertu Komunikaty zostały opóźnione w Centrum zgodności & zabezpieczeń" lightbox="../../media/mfi-queued-messages-alert-details.png":::

## <a name="see-also"></a>Zobacz też

Aby uzyskać informacje o innych szczegółowych informacjach na pulpicie nawigacyjnym przepływu poczty, zobacz [Szczegółowe informacje o przepływie poczty w Centrum zgodności & zabezpieczeń](mail-flow-insights-v2.md).
