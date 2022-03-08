---
title: Konfigurowanie powiadomień SMS i przypomnień w aplikacji Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Dowiedz się, jak skonfigurować powiadomienia SMS dla klientów, klientów i partnerów w uwitrynie Microsoft Bookings.
ms.openlocfilehash: 2aac74b89e5d83c4dec0840a7bb423a271e5eb5d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318027"
---
# <a name="configure-sms-text-notifications-and-reminders-in-microsoft-bookings"></a>Konfigurowanie powiadomień SMS i przypomnień w aplikacji Microsoft Bookings

Usługa Microsoft Bookings umożliwia skonfigurowanie powiadomień SMS w celu wysłania ich do osoby rezerwowej na termin. W aplikacji Bookings w sieci Web lub aplikacji Bookings w aplikacji Teams możesz skonfigurować powiadomienia SMS. Uczestnicy, klienci lub partnerzy mogą również zrezygnować z otrzymywania powiadomień SMS na stronie rezerwacji samoobsługowej. Mogą również zrezygnować z otrzymywania powiadomień SMS, wysyłając odpowiedź **STOP** do nadawcy.

Powiadomienia SMS będą zawierać link do spotkania aplikacji Teams dla wirtualnych spotkań rezerwacji.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby uczestnicy, klienci lub partnerzy mogli otrzymywać powiadomienia SMS, muszą mieć prawidłowy numer telefonu w Stanach Zjednoczonych lub Kanadzie.

## <a name="configure-sms-notification-in-microsoft-bookings"></a>Konfigurowanie powiadomień SMS w uwitrynie Microsoft Bookings

> [!IMPORTANT]
> Do 30 kwietnia 2022 r. usługa Microsoft Bookings będzie otrzymywać nieograniczoną liczbę powiadomień SMS dla klientów z licencjami aplikacji Bookings. Gdy zbliżamy się do zakończenia okresu promocji, będziemy poprawnymi dodatkowymi informacjami na temat wymagań licencyjnych.

Powiadomienie SMS w aplikacji Bookings możesz skonfigurować na kilka sposobów:

- W aplikacji sieci Web Bookings postępuj zgodnie z instrukcjami w  temacie Definiowanie ofert usług w aplikacji [Bookings](define-service-offerings.md), aby włączyć powiadomienia SMS.

- W aplikacji Booking w usłudze Teams przejdź do **ustawienia** >  **Typ punktu** >  **kontrolnegoDanie typu** terminu i wybierz **pozycję Wyślij do nich wiadomości SMS**.

## <a name="tracking-and-metrics-for-sms-notifications"></a>Śledzenie i metryki dla powiadomień SMS

> [!NOTE]
> Musisz być administratorem usługi Teams, aby widzieć dane aplikacji Teams i bookings w centrum administracyjnym usługi Teams.

W centrum administracyjnym aplikacji Teams możesz śledzić kluczowe dane dotyczące użycia powiadomień SMS w twojej organizacji. Raporty użycia zawierają dane, takie jak godzina i data wysłania, numer pochodzenia, typ wiadomości, typ zdarzenia i stan dostarczenia. Po 1 maja 2022 r. możesz użyć telemetrii powiadomień SMS w okresie promocyjnym, aby ułatwić prognozowanie i budżet powiadomień SMS.

1. W centrum administracyjnym aplikacji Teams: **powiadomienia SMS o wirtualnych odwiedzinach**.

2. Na stronie **Raporty & wiadomości SMS** wybierz pozycję Użycie powiadomień SMS.

    :::image type="content" source="../media/analytics-reporting.png" alt-text="Zrzut ekranu: Strona analiza i raportowanie powiadomień SMS w centrum administracyjnym aplikacji Teams":::

Zawartość pokrewna

[Microsoft Bookings](bookings-overview.md)\
[Włączanie i wyłączanie aplikacji Microsoft Bookings](turn-bookings-on-or-off.md)\
[Uzyskiwanie aplikacji Microsoft Bookings dla systemów iOS i Android](get-bookings-app.md)\
