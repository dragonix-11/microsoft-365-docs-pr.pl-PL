---
title: Raportowanie i śledzenie wiadomości
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: f40253f2-50a1-426e-9979-be74ba74cb61
ms.custom:
- seo-marvel-apr2020
description: W tym artykule dowiesz się o raportach i narzędziach do rozwiązywania problemów dostępnych dla administratorów usługi Microsoft Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d4f0289054baec0e5bcedf4e9e3d434ab51ef92b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986435"
---
# <a name="reporting-and-message-trace-in-eop"></a>Raportowanie i śledzenie wiadomości w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online program EOP udostępnia wiele różnych raportów, które mogą pomóc w ustaleniu ogólnego stanu i kondycji organizacji. Dostępne są również narzędzia, które ułatwiają rozwiązywanie problemów z określonymi zdarzeniami (takimi jak wiadomości, które nie trafiają do określonych adresatów), oraz raporty inspekcji w celu zapewnienia zgodności z wymaganiami.

## <a name="usage-reports"></a>Raporty użycia

- **Microsoft 365 aktywności grup**: Wyświetl informacje o liczbie Microsoft 365, które zostały utworzone i użyte. Aby uzyskać więcej informacji, [zobacz Microsoft 365 w centrum administracyjnym — informacje Microsoft 365 grupy](../../admin/activity-reports/office-365-groups.md).
- **Aktywność poczty** e-mail: Wyświetl informacje o liczbie wysłanych, odebranych i przeczytanych wiadomości w całej organizacji i u określonych użytkowników. Aby uzyskać więcej informacji, [zobacz raporty Microsoft 365 w centrum administracyjnym — Aktywność poczty e-mail](../../admin/activity-reports/email-activity.md).
- **Użycie aplikacji poczty e-mail**: Wyświetlanie informacji o używanych aplikacjach poczty e-mail. Obejmuje to łączną liczbę połączeń dla poszczególnych aplikacji oraz wersje aplikacji, które Outlook połączenia. Aby uzyskać więcej informacji, [zobacz raporty Microsoft 365 w centrum administracyjnym — Użycie aplikacji poczty e-mail](../../admin/activity-reports/email-apps-usage.md).
- **Użycie skrzynki** pocztowej: Wyświetl informacje na temat użytego miejsca do magazynowania, wykorzystania przydziałów, liczby elementów i ostatniej aktywności (wysyłanie lub odczytywanie) dla skrzynek pocztowych. Aby uzyskać więcej informacji, zobacz [raporty Microsoft 365 w centrum administracyjnym — Użycie skrzynki pocztowej](../../admin/activity-reports/mailbox-usage.md).

## <a name="security-reports-in-the-microsoft-365-defender-portal"></a>Raporty zabezpieczeń w portalu Microsoft 365 Defender

Te rozszerzone raporty zapewniają interakcyjne środowisko raportowania dla administratorów usługi EOP, które zawiera podsumowanie informacji oraz możliwość przechodzenia do szczegółów w celu zwiększenia szczegółów.

- **Defender for Office 365**: View information about Sejf Links and Sejf Attachments that are part of Microsoft Defender for Office 365. Aby uzyskać więcej informacji, [zobacz Wyświetlanie raportów programu Defender Office 365 w portalu Microsoft 365 Defender użytkowników](view-reports-for-mdo.md).
- **EOP**: Wyświetlaj informacje o wykrywaniu złośliwego oprogramowania, spoofed mail, wykryciu spamu oraz przepływie poczty do i z Organizacji. Aby uzyskać więcej informacji, [zobacz Wyświetlanie raportów zabezpieczeń poczty e-mail w Microsoft 365 Defender poczty e-mail](view-email-security-reports.md).

## <a name="mail-flow-insights-in-the-security--compliance-center"></a>Szczegółowe informacje o przepływie poczty w Centrum & zgodności

Aby uzyskać więcej informacji, zobacz [Informacje o przepływie poczty e-mail w Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).

## <a name="custom-reports-using-microsoft-graph"></a>Raporty niestandardowe przy użyciu aplikacji Microsoft Graph

Programowo twórz raporty, które są dostępne w centrum administracyjnym, przy użyciu aplikacji Microsoft Graph. Aby uzyskać więcej informacji, zobacz [Omówienie usługi Microsoft Graph](/graph/overview) i [Praca z raportami użycia Office 365 w aplikacji Microsoft Graph](/graph/api/resources/report).

## <a name="message-trace"></a>Śledzenie wiadomości

Podczas podróży przez usługę EOP są one podążane za wiadomościami e-mail. Możesz określić, czy wiadomość e-mail została odebrana, odrzucona, odroczona lub doręczona przez usługę. Pokazano też, jakie działania zostały wykonane w wiadomości przed jej ostatecznym stanem.

Przy użyciu tych informacji możesz skutecznie odpowiadać na pytania użytkowników, rozwiązywać problemy z przepływem poczty e-mail, weryfikować zmiany zasad i rozwiązywać problemy z koniecznością skontaktowania się z pomocą techniczną w celu uzyskania pomocy.

Zobacz [Śledzenie wiadomości w portalu Microsoft 365 Defender sieci.](message-trace-scc.md)

## <a name="audit-logging"></a>Rejestrowanie inspekcji

Śledzenie konkretnych zmian wprowadzonych przez administratorów w organizacji. Te raporty mogą ułatwić rozwiązywanie problemów z konfiguracją lub znajdowanie przyczyny problemów związanych z zabezpieczeniami lub zgodnością. Zobacz [Raporty inspekcji w programie Exchange Online](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports).

## <a name="reporting-and-message-trace-data-availability-and-latency"></a>Raportowanie i śledzenie danych dotyczących dostępności i opóźnień

W poniższej tabeli opisano, kiedy i jak długo są dostępne dane raportowania i śledzenia wiadomości usługi EOP.

<br>

****

|Typ raportu|Dostępne dane (okres wstecz)|Opóźnienie|
|---|---|---|
|Raporty podsumowujące dotyczące ochrony poczty|90 dni|Agregacja danych wiadomości jest zazwyczaj ukończona w ciągu 24–48 godzin. Niektóre nieznaczne zagregowane zmiany przyrostowe mogą występować maksymalnie przez 5 dni.|
|Raporty szczegółowe dotyczące ochrony poczty|90 dni|W przypadku danych szczegółowych, które mają mniej niż 7 dni, dane powinny być wyświetlane w ciągu 24 godzin, ale mogą nie być ukończone do 48 godzin. Niektóre drobne zmiany przyrostowe mogą występować maksymalnie przez 5 dni. <p> Aby wyświetlić raporty szczegółowe dla wiadomości, które mają więcej niż 7 dni, wyniki mogą potrwać do kilku godzin.|
|Dane śledzenia wiadomości|90 dni|Po uruchomieniu śledzenia wiadomości w przypadku wiadomości, które mają mniej niż 7 dni, powinny one zostać wyświetlone w ciągu 5–30 minut.<p> W przypadku uruchomienia śledzenia wiadomości, które mają więcej niż 7 dni, wyniki mogą potrwać do kilku godzin.|
|

> [!NOTE]
> Dostępność i opóźnienie danych są takie same niezależnie od tego, czy zażądano ich za pośrednictwem centrum administracyjnego, czy zdalnej obsługi programu PowerShell.
