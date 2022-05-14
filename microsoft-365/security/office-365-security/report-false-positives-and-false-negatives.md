---
title: Zgłaszanie wyników fałszywie dodatnich i fałszywie ujemnych w programie Outlook
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak zgłaszać wyniki fałszywie dodatnie i fałszywie ujemne w Outlook przy użyciu funkcji Komunikat raportu.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 762f16916e03940f4d0f95c48f13751d3cbd63c7
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416977"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>Zgłaszanie wyników fałszywie dodatnich i fałszywie ujemnych w programie Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Jeśli jesteś administratorem w organizacji Microsoft 365 z Exchange Online skrzynkami pocztowymi, zalecamy użycie strony **Przesłane** w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Przesyłanie do firmy Microsoft podejrzanych spamów, adresów URL i plików za pomocą portalu Przesyłania](admin-submission.md).

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub lokalnych skrzynkach pocztowych przy użyciu nowoczesnego uwierzytelniania hybrydowego można przesyłać wyniki fałszywie dodatnie (dobra wiadomość e-mail, która została zablokowana lub wysłana do folderu wiadomości-śmieci) oraz fałszywe negatywy (niechciane wiadomości e-mail lub phish dostarczone do skrzynki odbiorczej) do Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby uzyskać najlepsze środowisko przesyłania danych przez użytkownika, użyj dodatku Komunikat raportu lub dodatku Wyłudzanie informacji o raportach.

- Dodatek Komunikat raportu i dodatek Report Phishing działają dla Outlook na wszystkich platformach (Outlook w sieci Web, iOS, Android i Desktop).

- Jeśli jesteś administratorem w organizacji z Exchange Online skrzynkami pocztowymi, użyj portalu Przesłane w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Przesyłanie przez administratora w celu przesyłania do firmy Microsoft podejrzanych wiadomości spamowych, phish, adresów URL i plików](admin-submission.md).

- Możesz skonfigurować wysyłanie wiadomości bezpośrednio do firmy Microsoft, określonej skrzynki pocztowej lub obu tych elementów. Aby uzyskać więcej informacji, zobacz [Zasady przesyłania użytkowników](user-submission.md).

- Aby uzyskać więcej informacji na temat pobierania i włączania komunikatu raportu lub dodatków wyłudzania informacji o raportach, zobacz [Włączanie komunikatu raportu lub dodatków wyłudzania informacji raportu](enable-the-report-message-add-in.md).

- Aby uzyskać więcej informacji na temat raportowania komunikatów do firmy Microsoft, zobacz [Raportowanie komunikatów i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

Obejrzyj ten krótki film wideo, aby dowiedzieć się, jak za pomocą Ochrona usługi Office 365 w usłudze Microsoft Defender można łatwo zbadać przesyłanie przez użytkowników w celu określenia zawartości wiadomości i odpowiedzieć na przesłanie, stosując odpowiednią akcję korygowania. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBHof]

### <a name="turn-off-the-built-in-reporting-experience"></a>Wyłączanie wbudowanego środowiska raportowania

Nie zalecamy wbudowanego środowiska raportowania w Outlook, ponieważ nie może ono korzystać z [zasad przesyłania użytkowników](./user-submission.md). Zamiast tego zalecamy użycie dodatku Komunikat raportu lub dodatku Wyłudzanie informacji o raportach.

Aby można było uruchomić to polecenie cmdlet, należy mieć przypisane odpowiednie uprawnienia. Aby znaleźć uprawnienia wymagane do uruchomienia dowolnego polecenia cmdlet lub parametru w organizacji, zobacz [Znajdowanie uprawnień wymaganych do uruchomienia dowolnego polecenia cmdlet Exchange](/powershell/exchange/find-exchange-cmdlet-permissions).

Uruchom następujące polecenie programu PowerShell, aby wyłączyć wbudowane środowisko raportowania w Outlook w sieci Web:

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```

## <a name="use-the-report-message-feature"></a>Korzystanie z funkcji komunikatu raportu

### <a name="report-junk-and-phishing-messages"></a>Zgłaszanie wiadomości-śmieci i wiadomości wyłudzających informacje

W przypadku wiadomości w skrzynce odbiorczej lub innym folderze poczty e-mail z wyjątkiem wiadomości-śmieci użyj następującej metody do zgłaszania wiadomości spamu i wyłudzania informacji:

1. Wybierz wielokropek **Więcej akcji** w prawym górnym rogu wybranej wiadomości, wybierz pozycję **Komunikat raportu** z menu rozwijanego, a następnie wybierz pozycję **Wiadomości-śmieci** lub **Wyłudzanie informacji**.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Ikona Więcej akcji" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-junk-phishing.png" alt-text="Opcja Wiadomości-śmieci i wyłudzanie informacji w okienku Komunikat raportu" lightbox="../../media/report-message-junk-phishing.png":::

2. Wybrane komunikaty zostaną wysłane do firmy Microsoft w celu analizy i:
   - Przeniesiono je do folderu Wiadomości-śmieci, jeśli zostały zgłoszone jako spam.
   - Usunięte, jeśli zostały zgłoszone jako wyłudzanie informacji.

### <a name="report-messages-that-are-not-junk"></a>Zgłaszanie komunikatów, które nie są wiadomościami-śmieciami

1. Wybierz wielokropek **Więcej akcji** w prawym górnym rogu wybranej wiadomości, wybierz pozycję **Komunikat raportu** z menu rozwijanego, a następnie wybierz pozycję **Nie śmieci**.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Ikona, która udostępnia więcej akcji" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-not-junk.png" alt-text="Opcja Nie śmieci w okienku Komunikat raportu" lightbox="../../media/report-message-not-junk.png":::

2. Wybrana wiadomość zostanie wysłana do firmy Microsoft w celu analizy i przeniesiona do skrzynki odbiorczej lub dowolnego innego określonego folderu.

## <a name="view-and-review-reported-messages"></a>Wyświetlanie i przeglądanie zgłoszonych komunikatów

Aby przejrzeć komunikaty, które użytkownicy zgłaszają firmie Microsoft, dostępne są następujące opcje:

- Użyj strony **Przesłane** w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Wyświetlanie przesyłania użytkowników do firmy Microsoft](admin-submission.md#view-user-submissions-to-microsoft).
- Utwórz regułę przepływu poczty (znaną również jako reguła transportu), aby wysyłać kopie zgłoszonych wiadomości. Aby uzyskać instrukcje, zobacz [Używanie reguł przepływu poczty, aby zobaczyć, co użytkownicy zgłaszają firmie Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
