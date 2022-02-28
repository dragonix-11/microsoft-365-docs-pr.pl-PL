---
title: Czym&apos; różnią się wiadomości-śmieci od poczty masowej?
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 8079f193-1b40-4081-9e5d-d0e50dfbcc59
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o różnicach między wiadomościami-śmieciami (spamem) a zbiorczą pocztą e-mail (szarą) w programie Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e8a896ac3360ccf799dbe34c7e298f76140ee6d5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983301"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>Jaka jest różnica między wiadomościami-śmieciami a zbiorczą pocztą e-mail w u usługi EOP?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach korzystających ze skrzynek pocztowych w Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online klienci czasami pytają: "Jaka jest różnica między wiadomościami-śmieciami a zbiorczą pocztą e-mail?". W tym temacie wyjaśniono różnice i opisano kontrolki dostępne w umacie EOP.

- **Wiadomości-śmieci** to spam, które są niechcianymi i uniwersalnymi niechcianymi wiadomościami (jeśli zostaną poprawnie zidentyfikowane). Domyślnie program EOP odrzuca spam na podstawie reputacji źródłowego serwera poczty e-mail. Jeśli wiadomość przejdzie inspekcję źródłowego adresu IP, zostanie wysłana do filtrowania spamu. Jeśli wiadomość jest klasyfikowana jako spam przez filtrowanie spamu, jest ona (domyślnie) dostarczana do adresatów i przenoszony do ich folderu Wiadomości-śmieci.

  - Możesz skonfigurować działania, które będą podejmowane w przypadku werdyktów filtrowania spamu. Aby uzyskać instrukcje, [zobacz Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md).

  - Jeśli nie zgadzasz się z werdyktem filtrowania spamu, możesz zgłosić firmie Microsoft wiadomości, które uważasz za spam lub niebędący spamem, na kilka sposobów, zgodnie z opisem w tece Zgłaszanie wiadomości i plików do [firmy Microsoft](report-junk-email-messages-to-microsoft.md).

- **Masowa** poczta e-mail (znana również jako _szara poczta_) jest trudniejsza do klasyfikowania. Spam jest stałym zagrożeniem, jednak masowa poczta e-mail często jest reklamem zbiorczym lub wiadomościami marketingowym. Niektórzy użytkownicy chcą rozsyłać zbiorcze wiadomości e-mail (a w rzeczywistości mają rozmyślnie, aby je odbierać), natomiast inni rozważają masową pocztę e-mail jako spam. Niektórzy użytkownicy chcą na przykład otrzymywać wiadomości reklamowe od firmy Contoso Corporation lub zaproszenia na zbliżającą się konferencję na temat zabezpieczeń cyberzabłędu, a inni — za spam.

  Aby uzyskać więcej informacji na temat sposobu zidentyfikowania zbiorczej poczty e-mail, zobacz Zbiorczy poziom [skarg (BCL, Bulk complaint level) w UOP](bulk-complaint-level-values.md).

## <a name="how-to-manage-bulk-email"></a>Jak zarządzać masową pocztą e-mail

Ze względu na mieszaną reakcję na masową pocztę e-mail nie ma uniwersalnych wskazówek dotyczących każdej organizacji.

Domyślną próg wartości BCL używaną do identyfikowania poczty masowej jako spamu. Administratorzy mogą zwiększyć lub zmniejszyć próg. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Skonfiguruj zasady ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md).

- [Ustawienia zasad ochrony przed spamem w utermie EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

Inna łatwo przeoczyć inną opcję: jeśli użytkownik skarży się na odbieranie zbiorczej poczty e-mail, ale wiadomości są od wiarygodnych nadawców, którzy przechodzą filtrowanie spamu w uchwale EOP, poproś użytkownika o sprawdzenie, czy opcja anulowania subskrypcji w masowej wiadomości e-mail nie jest dostępna.
