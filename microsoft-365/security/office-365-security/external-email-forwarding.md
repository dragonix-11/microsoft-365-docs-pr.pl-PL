---
title: Konfigurowanie i kontrolowanie przekazywania zewnętrznych wiadomości e-mail na platformie Microsoft 365.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/17/2021
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
- adminvideo
description: W tym artykule opisano tematy, w tym zewnętrzne przekazywanie wiadomości e-mail, automatyczne przekazywanie dalej, komunikaty o odmowie dostępu 5.7.520, wyłączanie przekazywania zewnętrznego, komunikaty "Administrator wyłączył przekazywanie zewnętrzne", a także wychodzące zasady ochrony przed spamem.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c10433cd858ebe160ac4a38cfee78b57d39b80df
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487153"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Kontrolowanie automatycznego przekazywania zewnętrznych wiadomości e-mail na platformie Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jako administrator możesz mieć wymagania firmowe dotyczące ograniczania lub kontrolowania automatycznie przekazywanych wiadomości do adresatów zewnętrznych (adresatów spoza organizacji). Przekazywanie wiadomości e-mail może być przydatne, ale może również stanowić zagrożenie dla bezpieczeństwa ze względu na potencjalne ujawnienie informacji. Osoby atakujące mogą użyć tych informacji do ataku na organizację lub partnerów.

Na platformie Microsoft 365 są dostępne następujące typy automatycznego przekazywania dalej:

- Użytkownicy mogą skonfigurować [reguły skrzynki odbiorczej](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) , aby automatycznie przekazywać komunikaty do zewnętrznych nadawców (celowo lub w wyniku naruszenia zabezpieczeń konta).
- Administratorzy mogą skonfigurować [przekazywanie skrzynek pocztowych](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (nazywane również _przekazywaniem SMTP_), aby automatycznie przekazywać wiadomości do adresatów zewnętrznych. Administrator może wybrać, czy po prostu przekazywać wiadomości, czy przechowywać kopie wiadomości przesyłanych dalej w skrzynce pocztowej.

> [!NOTE]
> Użytkownicy z automatycznym przekazywaniem z lokalnych systemów poczty e-mail za pośrednictwem platformy Microsoft 365 będą podlegać tym samym kontrolom zasad co skrzynki pocztowe w chmurze w nadchodzącej aktualizacji. Ta aktualizacja zostanie przekazana za pośrednictwem wpisu w Centrum komunikatów.

Zasady filtrowania spamu wychodzącego umożliwiają sterowanie automatycznym przekazywaniem do adresatów zewnętrznych. Dostępne są trzy ustawienia:

- **Automatyczne — sterowane przez system**: jest to ustawienie domyślne. To ustawienie jest teraz takie samo jak **Wył**. Kiedy to ustawienie zostało pierwotnie wprowadzone, było **równoważne** wł. Z biegiem czasu, dzięki zasadom [bezpieczeństwa domyślnie](secure-by-default.md), to ustawienie było stopniowo zmieniane na **Wyłączone** dla wszystkich klientów. Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://techcommunity.microsoft.com/t5/exchange-team-blog/all-you-need-to-know-about-automatic-email-forwarding-in/ba-p/2074888).
- **Włączone**: Automatyczne przekazywanie zewnętrzne jest dozwolone i nie jest ograniczone.
- **Wyłączone**: automatyczne przekazywanie zewnętrzne jest wyłączone i spowoduje, że do nadawcy zostanie wysłany raport o braku dostarczania (znany również jako komunikat NDR lub bounce).

Aby uzyskać instrukcje dotyczące konfigurowania tych ustawień, zobacz [Konfigurowanie filtrowania spamu wychodzącego w ramach EOP](configure-the-outbound-spam-policy.md).

> [!NOTE]
>
> - Wyłączenie automatycznego przekazywania dalej powoduje wyłączenie wszelkich reguł skrzynki odbiorczej (użytkowników) lub przekazywania skrzynki pocztowej (administratorów), które przekierowują wiadomości na adresy zewnętrzne.
> - Ustawienia zasad filtru spamu wychodzącego nie mają wpływu na automatyczne przekazywanie wiadomości między użytkownikami wewnętrznymi.

## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Jak działają ustawienia zasad filtru spamu wychodzącego z innymi kontrolkami automatycznego przekazywania wiadomości e-mail

Jako administrator możesz już skonfigurować inne kontrolki w celu zezwalania na automatyczne przekazywanie wiadomości e-mail lub blokowania ich. Przykład:

- [Domeny zdalne](/exchange/mail-flow-best-practices/remote-domains/remote-domains) do zezwalania na automatyczne przekazywanie wiadomości e-mail lub blokowania ich do niektórych lub wszystkich domen zewnętrznych.
- Warunki i akcje w [regułach przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) programu Exchange (nazywane również regułami transportu) w celu wykrywania i blokowania automatycznie przekazywanych wiadomości do adresatów zewnętrznych.

Gdy jedno ustawienie zezwala na przekazywanie zewnętrzne, ale inne ustawienie blokuje przekazywanie zewnętrzne, blok zazwyczaj wygrywa. Przykłady opisano w poniższej tabeli:

|Scenariusz|Result (Wynik)|
|---|---|
|<ul><li>Ustawienia domeny zdalnej można skonfigurować w celu umożliwienia automatycznego przekazywania dalej.</li><li>Automatyczne przekazywanie dalej w zasadach filtru spamu wychodzącego ma wartość **Wyłączone**.</li></ul>|Automatycznie przekazywane wiadomości do adresatów w domenach, których dotyczy problem, są blokowane.|
|<ul><li>Ustawienia domeny zdalnej można skonfigurować w celu umożliwienia automatycznego przekazywania dalej.</li><li>Automatyczne przekazywanie dalej w zasadach filtru spamu wychodzącego ma wartość **Automatyczne — sterowane przez system**.</li></ul>|Automatycznie przekazywane wiadomości do adresatów w domenach, których dotyczy problem, są blokowane. <p> Jak opisano wcześniej, **automatyczne — sterowane przez system** **oznacza włączone**, ale ustawienie zmieniało się wraz z upływem czasu na **wartość Wyłączone** we wszystkich organizacjach. <p> Aby uzyskać absolutną przejrzystość, należy skonfigurować zasady filtru spamu wychodzącego na **wartość Włączone** lub **Wyłączone**.|
|<ul><li>Automatyczne przekazywanie dalej w zasadach filtru spamu wychodzącego ma wartość **Włączone**</li><li>Reguły przepływu poczty lub domeny zdalne są używane do blokowania automatycznie przesyłanych dalej wiadomości e-mail.</li></ul>|Automatycznie przekazywane wiadomości do adresatów, których dotyczy problem, są blokowane przez reguły przepływu poczty lub domeny zdalne.|

Za pomocą tego zachowania (na przykład) można zezwolić na automatyczne przekazywanie dalej w zasadach filtru spamu wychodzącego, ale używać domen zdalnych do kontrolowania domen zewnętrznych, do których użytkownicy mogą przekazywać wiadomości dalej.

## <a name="how-to-find-users-that-are-automatically-forwarding"></a>Jak znaleźć użytkowników, którzy automatycznie przesyłają dalej

Informacje o użytkownikach, którzy automatycznie przekazują komunikaty do adresatów zewnętrznych, są widoczne w [raporcie Automatyczne przekazywanie komunikatów](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) dla kont w chmurze. W przypadku użytkowników lokalnych, którzy automatycznie przekazują dane z lokalnego systemu poczty e-mail za pośrednictwem platformy Microsoft 365, należy utworzyć regułę przepływu poczty w celu śledzenia tych użytkowników. Aby uzyskać instrukcje dotyczące tworzenia reguły przepływu poczty, zobacz [Używanie umowy EAC do tworzenia reguły przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#use-the-eac-to-create-a-mail-flow-rule).

Do utworzenia reguły przepływu poczty w centrum administracyjnym programu Exchange (EAC) są wymagane następujące informacje:

- **Zastosuj tę regułę, jeśli** (warunek): **nagłówek** \> komunikatu **pasuje do tych wzorców tekstowych**. Pamiętaj, że może być konieczne **kliknięcie pozycji Więcej opcji** , aby wyświetlić tę opcję.
  - **Nazwa nagłówka**: `X-MS-Exchange-Inbox-Rules-Loop`
  - **Wartość nagłówka**: `.`

  Warunek wygląda następująco: nagłówek **"X-MS-Exchange-Inbox-Rules-Loop"** jest zgodny z **nagłówkiem "".**

  Ten warunek będzie zgodny z dowolną wartością nagłówka.

- (Opcjonalnie) **Wykonaj następujące** czynności (akcja): możesz skonfigurować opcjonalną akcję. Na przykład możesz użyć akcji **Modyfikuj właściwości** \> komunikatu, **ustawić nagłówek komunikatu z nazwą** nagłówka **X-Forwarded** i **wartością True**. Jednak skonfigurowanie akcji nie jest wymagane.
- Ustaw **wartość Audit this rue with severity level (Inspekcja tego rue z poziomem ważności** ) na wartość **Niska**, **Średnia** lub **Wysoka**. To ustawienie umożliwia użycie [raportu reguł transportu programu Exchange](view-email-security-reports.md#exchange-transport-rule-report) w celu uzyskania szczegółowych informacji o użytkownikach przesyłanych dalej.

:::image type="content" source="../../media/mail-flow-rule-for-forwarded-messages.png" alt-text="Właściwości reguły przepływu poczty w usłudze EAC dla reguły identyfikującej komunikaty przesyłane dalej" lightbox="../../media/mail-flow-rule-for-forwarded-messages.png":::

## <a name="blocked-email-forwarding-messages"></a>Zablokowane wiadomości e-mail przesyłające dalej

Gdy komunikat zostanie wykryty jako automatycznie przesłany dalej, a zasady [filtru spamu wychodzącego](configure-the-outbound-spam-policy.md) *zablokują* to działanie, wiadomość zostanie zwrócona do nadawcy w NDR, który zawiera następujące informacje:

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
