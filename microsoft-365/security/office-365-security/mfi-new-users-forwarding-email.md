---
title: Nowi użytkownicy przesyłający dalej informacje o wiadomościach e-mail
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Administratorzy mogą dowiedzieć się, jak za pomocą szczegółowych informacji o nowych użytkownikach przesyłających dalej wiadomości e-mail w Centrum zgodności usługi & Security & zbadać, kiedy użytkownicy w ich organizacji będą przesyłać dalej wiadomości do nowych domen.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 7e7f97f2f246be609db813f1d42ef6aed6a152a9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470268"
---
# <a name="new-users-forwarding-email-insight-in-the-security--compliance-center"></a>Nowi użytkownicy mogą przesyłać dalej informacje dotyczące poczty e-mail w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jest to podejrzane, gdy nowe konta użytkowników w Twojej organizacji nagle zaczną przesyłać dalej wiadomości e-mail do domen zewnętrznych.

Szczegółowe **informacje o nowych** domenach w Centrum & zabezpieczeń [](https://protection.office.com) i zgodności informują o tym, gdy nowo utworzeni użytkownicy w organizacji będą przesyłać wiadomości do domen zewnętrznych. Ten warunek może wskazywać, że do utworzenia nowych użytkowników zostały użyte naruszone konta administratora. Jeśli podejrzewasz, że konta zostały naruszone, zobacz Odpowiadanie na [naruszone konto e-mail](responding-to-a-compromised-email-account.md).

Ta informacja jest widoczna tylko po wykryciu problemu i pojawia się na stronie [Raport przesyłany](view-mail-flow-reports.md#forwarding-report) dalej.

:::image type="content" source="../../media/mfi-new-users-forwarding-email.png" alt-text="Nowi użytkownicy przesyłający dalej informacje o wiadomościach e-mail" lightbox="../../media/mfi-new-users-forwarding-email.png":::

Po kliknięciu widżetu zostanie wyświetlone wysuwne okno, w którym można znaleźć więcej szczegółowych informacji na temat wiadomości przesyłanych dalej, w tym [](#forwarding-modifications-report) link do raportu o zmianach w przesyłaniu dalej zgodnie z opisem w dalszej części tego artykułu.

:::image type="content" source="../../media/mfi-new-users-forwarding-email-details.png" alt-text="Wysuw szczegółów wyświetlany po kliknięciu pozycji Nowi użytkownicy przesyłający dalej informacje e-mail" lightbox="../../media/mfi-new-users-forwarding-email-details.png":::

Możesz również przejść do tej strony szczegółów, gdy wybierzesz szczegółowe informacje po kliknięciu przycisku Wyświetl wszystkie w obszarze Najważniejsze informacje **& zalecenia** na (**Pulpit** \> nawigacyjny **Raporty** lub <https://protection.office.com/insightdashboard>).

Możesz kliknąć link Zobacz **raport skojarzony z informacjami** , aby przejść do raportu do przesyłania dalej **zmian zgodnie z** opisem w następnej sekcji.

## <a name="forwarding-modifications-report"></a>Forwarding modifications report

Raport **Modyfikacje przesyłania dalej** zawiera szczegółowe informacje o wiadomościach automatycznie przesyłanych dalej od nadawców w organizacji:

- Nowo utworzone konta, które przesyła dalej wiadomości do domen zewnętrznych.
- Konta, które przesyłają dalej wiadomości do domen zewnętrznych, które nigdy nie zostały przekazane przez innych nadawców w organizacji.

Tego typu wiadomości przekazane mogą stanowić zagrożenie bezpieczeństwa lub zgodności, a także wskazywać na naruszone konta.

Raport zawiera dane do 90 dni. Domyślnie raport zawiera dane z ostatnich 7 dni.

Ten raport nie jest dostępny bezpośrednio na pulpicie nawigacyjnym [przepływu poczty](mail-flow-insights-v2.md) ani na [pulpicie nawigacyjnym Raporty](view-mail-flow-reports.md). Aby uzyskać do **raportu nie tylko** link Zobacz raport skojarzony z skojarzoną z informacjami w szczegółowych informacjach o nowych użytkownikach, ale również:

- Kliknięcie **linku do raportu powiadomienia dalej** w szczegółach szczegółowych informacji o nowych [domenach przesyłanych dalej wiadomości e-mail](mfi-new-domains-being-forwarded-email.md).
- Otwieranie <https://protection.office.com/reportv2?id=MailFlowNewForwarding>.

### <a name="report-view-for-the-forwarding-modifications-report"></a>Widok raportu dla raportu do przesyłania dalej zmian

W widoku raportu są dostępne następujące wykresy:

- **Pokaż dane dla: Nowi użytkownicy przesyłania dalej**:

    :::image type="content" source="../../media/forwarding-modifications-report-new-forwarding-users.png" alt-text="Widok Nowi użytkownicy przesyłający dalej w raporcie Modyfikowanie przesyłania dalej" lightbox="../../media/forwarding-modifications-report-new-forwarding-users.png":::

- **Pokaż dane dla: Nowe domeny przesyłania dalej**:

    :::image type="content" source="../../media/forwarding-modifications-report-new-forwarded-domains.png" alt-text="Widok Nowe domeny przekazane dalej w raporcie Modyfikowanie przesyłania dalej" lightbox="../../media/forwarding-modifications-report-new-forwarded-domains.png":::

Jeśli klikniesz **pozycję Filtry** w widoku raportu, możesz określić zakres dat w **datach Rozpoczęcie** i **Data zakończenia**.

### <a name="details-table-view-for-the-forwarding-modifications-report"></a>Widok tabeli Szczegóły dla raportu do przesyłania dalej modyfikacji

Jeśli **klikniesz pozycję Wyświetl** tabelę szczegółów, wyświetlane informacje zależą od wyświetlanego wykresu:

- **Pokaż dane dla: Nowi użytkownicy przesyłania dalej**:

  - **Nazwa**: adres e-mail nadawcy.
  - **Typ przesyłania dalej**
  - **Adres adresata**
  - **Szczegóły**
  - **Liczba**
  - **Data pierwszej wiadomości przesyłanych dalej**

- **Pokaż dane dla: Nowe domeny przesyłania dalej**:

  - **Nazwa**: domena adresu e-mail nadawcy.
  - **Typ przesyłania dalej**
  - **Adres adresata**
  - **Szczegóły**
  - **Liczba**
  - **Data pierwszej wiadomości przesyłanych dalej**

Jeśli klikniesz **pozycję Filtry** w widoku tabeli szczegółów, możesz określić zakres dat z **datami rozpoczęcia** i **datami zakończenia**.

W przypadku wybrania wiersza z tabeli zostanie wyświetlone **wysuwne okno** Szczegóły z następującymi informacjami:

- **Nazwa**: Adres e-mail nadawcy (w widoku Pokaż dane dla **:** Nowi użytkownicy przesyłający dalej) lub domena poczty e-mail nadawcy (z pokaż dane **dla:** Nowy widok domen przesyłania dalej).
- **Typ przesyłania dalej**
- **Adresat**
- **Szczegóły**
- **Liczba**
- **Data rozpoczęcia**
- **Zalecenie**: W tym miejscu możesz kliknąć link, aby zarządzać użytkownikiem w Centrum administracyjne platformy Microsoft 365.

  :::image type="content" source="../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png" alt-text="The Details flyout from the details table of the New forwarding users view in the Forwarding modifications report" lightbox="../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png":::

Aby wrócić do widoku raportów, kliknij pozycję **Wyświetl raport**.

## <a name="related-topics"></a>Tematy pokrewne

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).
