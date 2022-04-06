---
title: Microsoft Defender for Identity powiadomienia w aplikacji Microsoft 365 Defender
description: Dowiedz się, jak Microsoft Defender for Identity powiadomienia w aplikacji Microsoft 365 Defender.
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 89ed7ae50bf89c28bde81ea02e8905d0056ede53
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470928"
---
# <a name="defender-for-identity-notifications-in-microsoft-365-defender"></a>Powiadomienia usługi Defender dla tożsamości w programie Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak pracować z [powiadomieniami Microsoft Defender for Identity](/defender-for-identity) w aplikacji [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

## <a name="health-issues-notifications"></a>Powiadomienia dotyczące problemów z kondycją

W Microsoft 365 Defender usługi Defender dla tożsamości możesz dodać adresatów wiadomości e-mail z powiadomieniami o problemach dotyczących kondycji.

1. Na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **przejdź do Ustawienia** i **Tożsamości**.

  :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Opcja Tożsamości w kolumnie Nazwa" lightbox="../../media/defender-identity/settings-identities.png":::


1. Wybierz pozycję **Powiadomienia o problemach z kondycją**.

1. Wprowadź adres e-mail adresata. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/defender-identity/health-email-recipient.png" alt-text="Element podmenu Powiadomienia o problemach z kondycją" lightbox="../../media/defender-identity/health-email-recipient.png":::

1. Gdy program Defender dla tożsamości wykryje problem z kondycją, adresaci otrzymają wiadomość e-mail z powiadomieniem o szczegółach.

   :::image type="content" source="../../media/defender-identity/health-email.png" alt-text="Wiadomość e-mail o problemie z kondycją" lightbox="../../media/defender-identity/health-email.png":::

    > [!NOTE]
    > Wiadomość e-mail zawiera dwa linki do szczegółowych informacji o problemie. Możesz przejść do Centrum **kondycji MDI** lub nowego centrum **kondycji w uściślicie M365D**.

## <a name="alert-notifications"></a>Powiadomienia alertów

W Microsoft 365 Defender możesz dodać adresatów do powiadomień e-mail o wykrytych alertach.

1. Na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **przejdź do Ustawienia** i **Tożsamości**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Opcja Tożsamości" lightbox="../../media/defender-identity/settings-identities.png":::

1. Wybierz pozycję **Powiadomienia alertów**.

1. Wprowadź adres e-mail adresata. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/defender-identity/alert-email-recipient.png" alt-text="Element podmenu Powiadomienia alertów" lightbox="../../media/defender-identity/alert-email-recipient.png":::

## <a name="syslog-notifications"></a>Powiadomienia syslogu

Program Defender for Identity może powiadamiać Cię o wykryciu podejrzanych działań, wysyłając alerty o zabezpieczeniach i kondycji do serwera syslogów za pośrednictwem nominowego czujnika.

> [!NOTE]
> Aby dowiedzieć się, jak zintegrować usługę Defender for Identity z programem Microsoft Sentinel, zobacz Microsoft 365 Defender [integracji z programem Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).

1. Na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **przejdź do Ustawienia** i **Tożsamości**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Opcja Tożsamości w kolumnie Nazwa" lightbox="../../media/defender-identity/settings-identities.png":::

1. Wybierz **pozycję Powiadomienia syslogu**.

1. Aby włączyć powiadomienie systemu, ustaw przełącznik usługi **Syslog** w pozycji " **wł** ".

   :::image type="content" source="../../media/defender-identity/syslog-service.png" alt-text="Opcja usługi Syslog, która może być włączona" lightbox="../../media/defender-identity/syslog-service.png":::

1. Wybierz **pozycję Konfiguruj usługę**. Zostanie otwarte okienko, w którym możesz wprowadzić szczegóły usługi syslog.

   :::image type="content" source="../../media/defender-identity/syslog-sensor.png" alt-text="Strona, na której wprowadzasz szczegóły usługi Syslog" lightbox="../../media/defender-identity/syslog-sensor.png":::

1. Wprowadź następujące szczegóły:

    - **Czujnik** — z listy rozwijanej wybierz czujnik, który będzie wysyłał alerty.
    - **Punkt końcowy** usługi **i port** — wprowadź adres IP lub w pełni kwalifikowaną nazwę domeny (FQDN) dla serwera syslog i podaj numer portu. Możesz skonfigurować tylko jeden punkt końcowy systemu Syslog.
    - **Transport** — wybierz **protokół Transport** (TCP lub UDP).
    - **Format** — wybierz format (RFC 3164 lub RFC 5424).

1. Wybierz **pozycję Wyślij powiadomienie SIEM testu** , a następnie sprawdź, czy wiadomość została odebrana w rozwiązaniu infrastruktury systemu Syslog.

1. Wybierz **Zapisz**.

1. Po skonfigurowaniu usługi **Syslog** możesz wybrać typy powiadomień (alertów i problemów dotyczących kondycji) do wysyłania do serwera syslogu.

   :::image type="content" source="../../media/defender-identity/syslog-configured.png" alt-text="Zaznaczona opcja Skonfigurowano usługę Syslog" lightbox="../../media/defender-identity/syslog-configured.png":::

## <a name="see-also"></a>Zobacz też

- [Zarządzanie alertami zabezpieczeń usługi Defender for Identity](manage-security-alerts.md)
