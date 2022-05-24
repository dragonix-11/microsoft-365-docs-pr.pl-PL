---
title: Jaka&apos; jest różnica między wiadomościami-śmieciami a wiadomościami e-mail zbiorczymi?
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
description: Administratorzy mogą dowiedzieć się więcej o różnicach między wiadomościami-śmieciami (spamem) i wiadomościami e-mail zbiorczymi (szara poczta) w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5f948b45c5f4b26f3fba74f3883511218daa0ef0
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647848"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>Jaka jest różnica między wiadomościami-śmieciami a zbiorczą wiadomością e-mail w ramach EOP?

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, klienci czasami pytają: "jaka jest różnica między wiadomościami-śmieciami a zbiorczymi wiadomościami e-mail?" W tym temacie wyjaśniono różnicę i opisano kontrolki dostępne w ramach EOP.

- **Wiadomości-śmieci** to spam, które są niechciane i powszechnie niechciane wiadomości (po prawidłowym zidentyfikowaniu). Domyślnie EOP odrzuca spam na podstawie reputacji źródłowego serwera poczty e-mail. Jeśli wiadomość przejdzie inspekcję źródłowego adresu IP, zostanie wysłana do filtrowania spamu. Jeśli wiadomość jest klasyfikowana jako spam przez filtrowanie spamu, wiadomość jest (domyślnie) dostarczana do zamierzonych adresatów i przenoszona do folderu Wiadomości-śmieci.

  - Możesz skonfigurować akcje do wykonania w przypadku werdyktów filtrowania spamu. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md).

  - Jeśli nie zgadzasz się z werdyktem dotyczącym filtrowania spamu, możesz zgłaszać wiadomości, które uważasz za spam lub niespamowanie do firmy Microsoft na kilka sposobów, zgodnie z opisem w [temacie Zgłaszanie wiadomości i plików firmie Microsoft](report-junk-email-messages-to-microsoft.md).

- **Zbiorcza wiadomość e-mail** (znana również jako _szara poczta_) jest trudniejsza do sklasyfikowania. Spam jest stałym zagrożeniem, ale zbiorcza wiadomość e-mail jest często jednorazową reklamą lub wiadomościami marketingowymi. Niektórzy użytkownicy chcą zbiorczych wiadomości e-mail (a w rzeczywistości celowo zarejestrowali się, aby je otrzymywać), podczas gdy inni użytkownicy uważają wiadomości e-mail zbiorcze za spam. Na przykład niektórzy użytkownicy chcą otrzymywać komunikaty reklamowe od firmy Contoso Corporation lub zaproszenia na nadchodzącą konferencję na temat bezpieczeństwa cybernetycznego, podczas gdy inni użytkownicy uważają te same wiadomości za spam.

  Aby uzyskać więcej informacji na temat identyfikowania zbiorczej poczty e-mail, zobacz [Poziom skarg zbiorczych (BCL) w ramach operacji EOP](bulk-complaint-level-values.md).

## <a name="how-to-manage-bulk-email"></a>Jak zarządzać zbiorczą pocztą e-mail

Ze względu na mieszaną reakcję na wiadomości e-mail zbiorcze nie ma uniwersalnych wskazówek, które dotyczą każdej organizacji.

Zasady ochrony przed spamem mają domyślny próg listy BCL, który służy do identyfikowania wiadomości e-mail zbiorczych jako spamu. Administratorzy mogą zwiększyć lub zmniejszyć próg. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md).

- [Ustawienia zasad ochrony przed spamem w usłudze EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

Inna opcja, którą można łatwo przeoczyć: jeśli użytkownik skarży się na odbieranie zbiorczych wiadomości e-mail, ale wiadomości pochodzą od renomowanych nadawców, którzy przekazują filtrowanie spamu w ramach operacji EOP, użytkownik sprawdzi opcję anulowania subskrypcji w zbiorczej wiadomości e-mail.
