---
title: Szczegółowe informacje o klientach i raporty protokołu SMTP na pulpicie nawigacyjnym przepływu poczty
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak używać szczegółowych informacji o uwierzytelnieniu SMTP i raportów na pulpicie nawigacyjnym przepływu poczty w Centrum zgodności usługi & w celu monitorowania nadawców wiadomości e-mail w organizacji, które wysyłają wiadomości e-mail przy użyciu uwierzytelnionego protokołu SMTP (SMTP AUTH).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8c2152820e7f3d5dbf04534e5f0b0fec344ecc7b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474998"
---
# <a name="smtp-auth-clients-insight-and-report-in-the-security--compliance-center"></a>Szczegółowe informacje o klientach uwierzytelniania SMTP i raport w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Szczegółowe informacje dotyczące klientów **usługi SMTP Auth** na [](mail-flow-insights-v2.md) pulpicie nawigacyjnym przepływu poczty i skojarzonym z nim raportem Klienci uwierzytelniania [SMTP](#smtp-auth-clients-report) w Centrum zgodności [usługi Zabezpieczenia &](https://protection.office.com) wyróżnieniem użycia protokołu przesyłania klienta SMTP AUTH przez użytkowników lub konta systemowe w organizacji. Ten starszy protokół (który używa parametru smtp.office365.com) oferuje tylko uwierzytelnianie podstawowe i jest podatny na użycie przez naruszone konta do wysyłania wiadomości e-mail. Szczegółowe informacje i raporty pozwalają sprawdzić nietypowe działania dotyczące przesyłania wiadomości e-mail przy użyciu protokołu SMTP AUTH. Pokazano też dane użycia protokołu TLS dla klientów lub urządzeń korzystających z protokołu SMTP AUTH.

Widżet wskazuje liczbę użytkowników lub kont usług, które w ciągu ostatnich 7 dni używały protokołu SMTP Auth.

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-widget.png" alt-text="Widżet klientów uwierzytelniania SMTP na pulpicie nawigacyjnym przepływu poczty w Centrum & zabezpieczeń" lightbox="../../media/mfi-smtp-auth-clients-report-widget.png":::

Jeśli klikniesz liczbę wiadomości na widżecie, **zostanie wyświetlone wysuwne okno wysuwu klientów usługi SMTP Auth** . Wysuw zawiera zagregowany widok użycia i wielkości TLS z ostatniego tygodnia.

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-details.png" alt-text="Wysuwne menu Szczegóły po kliknięciu widżetu Klienci uwierzytelniania SMTP na pulpicie nawigacyjnym przepływu poczty" lightbox="../../media/mfi-smtp-auth-clients-report-details.png":::

Możesz kliknąć link raport klienci **uwierzytelniania SMTP** , aby przejść do raportu klientów usługi SMTP Auth zgodnie z opisem w następnej sekcji.

## <a name="smtp-auth-clients-report"></a>Raport Klienci uwierzytelniania SMTP

### <a name="report-view-for-the-smtp-auth-clients-report"></a>Widok raportu dla raportu klientów protokołu SMTP Auth

Domyślnie raport przedstawia dane z ostatnich 7 dni, ale są dostępne dane z ostatnich 90 dni.

Sekcja przeglądu zawiera następujące wykresy:

- **Wyświetlanie danych według:** Wysyłanie woluminu: Domyślnie na wykresie jest pokazana liczba wiadomości klienckich protokołu SMTP Auth, które zostały wysłane ze wszystkich domen (Pokaż dane dla **:** Domyślnie wybrana jest opcja Wszystkie domeny nadawcy). Możesz filtrować wyniki do określonej domeny nadawcy, klikając pozycję  Pokaż dane dla i wybierając domenę nadawcy z listy rozwijanej. Po umieszczeniu wskaźnika myszy na określonym punkcie danych (dzień) zostanie pokazana liczba wiadomości.

  :::image type="content" source="../../media/mfi-smtp-auth-clients-report-sending-volume-view.png" alt-text="The Sending volume view in the SMTP Auth clients report in the Security & Compliance Center" lightbox="../../media/mfi-smtp-auth-clients-report-sending-volume-view.png":::

- **Wyświetlanie danych według: Użycie protokołu TLS**: na wykresie przedstawiono procent użycia protokołu TLS dla wszystkich wiadomości klienta uwierzytelniania SMTP w wybranym okresie. Ten wykres pozwala identyfikować użytkowników i konta systemowe, które nadal używa starszych wersji usługi TLS, i podjąć w związku z tym działania.

  :::image type="content" source="../../media/mfi-smtp-auth-clients-report-tls-usage-view.png" alt-text="Widok użycia protokołu TLS w raporcie Klienci uwierzytelniania SMTP w Centrum & zabezpieczeń" lightbox="../../media/mfi-smtp-auth-clients-report-tls-usage-view.png":::

Jeśli klikniesz **pozycję Filtry** w widoku raportu, możesz określić zakres dat w **datach Rozpoczęcie** i **Data zakończenia**.

Kliknij **pozycję Poproś o** raport, aby uzyskać bardziej szczegółową wersję raportu w wiadomości e-mail. Można określić zakres dat i adresatów raportu.

### <a name="details-table-view-for-the-smtp-auth-clients-report"></a>Widok tabeli Szczegóły dla raportu klientów protokołu SMTP Auth

Jeśli **klikniesz pozycję Wyświetl** tabelę szczegółów, wyświetlane informacje zależą od wyświetlanego wykresu:

- **Wyświetlanie danych według: Wysyłanie głośności**: W tabeli przedstawiono następujące informacje:

  - **Adres nadawcy**
  - **Liczba wiadomości**

  Jeśli zaznaczysz wiersz, te same szczegóły będą wyświetlane w wysuwanych informacjach.

- **Wyświetlanie danych według: Użycie TLS**: W tabeli przedstawiono następujące informacje:

  - **Adres nadawcy**
  - **TLS1,0%**<sup>\*</sup>
  - **TLS1,1%**<sup>\*</sup>
  - **TLS1,2%**<sup>\*</sup>
  - **Liczba wiadomości**

  <sup>\*</sup> W tej kolumnie jest pokazana wartość procentowa i liczba wiadomości od nadawcy.

Jeśli klikniesz **pozycję Filtry** w widoku tabeli szczegółów, możesz określić zakres dat z **datami rozpoczęcia** i **datami zakończenia**.

Jeśli zaznaczysz wiersz, podobne szczegóły zostaną wyświetlone w wysuwanych informacjach:

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png" alt-text="Wysuwowe szczegóły z tabeli szczegółów widoku użycia protokołu TLS w raporcie Klienci protokołu SMTP Auth" lightbox="../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png":::

Kliknij **pozycję Poproś o** raport, aby uzyskać bardziej szczegółową wersję raportu w wiadomości e-mail. Można określić zakres dat i adresatów raportu.

Aby wrócić do widoku raportów, kliknij pozycję **Wyświetl raport**.

## <a name="related-topics"></a>Tematy pokrewne

Aby uzyskać więcej informacji na temat pulpitu nawigacyjnego przepływu poczty e-mail, zobacz Szczegółowe informacje o przepływie poczty w [Centrum & zabezpieczeń i zgodności](mail-flow-insights-v2.md).
