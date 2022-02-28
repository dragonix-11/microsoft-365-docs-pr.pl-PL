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
ms.openlocfilehash: be5d1d93754707be8217c5c3e17ec7d9f158e501
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988057"
---
# <a name="configure-sms-text-notifications-and-reminders-in-microsoft-bookings"></a>Konfigurowanie powiadomień SMS i przypomnień w aplikacji Microsoft Bookings

Usługa Microsoft Bookings umożliwia skonfigurowanie powiadomień SMS w celu wysłania ich do osoby rezerwowej na termin. Powiadomienia SMS możesz skonfigurować w aplikacji Bookings w sieci Web lub aplikacji Bookings w aplikacji Teams. Uczestnicy, klienci lub partnerzy mogą również zrezygnować z otrzymywania powiadomień SMS na stronie rezerwacji samoobsługowej. Mogą również zrezygnować z otrzymywania powiadomień SMS, wysyłając odpowiedź **STOP** do nadawcy.

Powiadomienia SMS będą zawierać link Teams spotkania dla wirtualnych spotkań rezerwacji.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby uczestnicy, klienci lub partnerzy mogli otrzymywać powiadomienia SMS, muszą mieć prawidłowy numer telefonu w Stanach Zjednoczonych lub Kanadzie.

## <a name="configure-sms-notification-in-microsoft-bookings"></a>Konfigurowanie powiadomień SMS w uwitrynie Microsoft Bookings

> [!IMPORTANT]
> Aplikacja Microsoft Bookings będzie mieć nieograniczoną liczbę powiadomień SMS dla klientów z licencjami aplikacji Bookings do 28 lutego 2022 r. Gdy zbliżamy się do zakończenia okresu promocji, będziemy poprawnymi dodatkowymi informacjami na temat wymagań licencyjnych. Aby uzyskać więcej informacji na temat licencjonowania usług Bookings, zobacz [Licencjonowanie programu Bookings](/microsoft-365/bookings/bookings-faq?view=o365-worldwide#who-has-access-to-microsoft-bookings-).

Powiadomienie SMS w aplikacji Bookings możesz skonfigurować na kilka sposobów:

- W aplikacji sieci Web Bookings postępuj zgodnie z instrukcjami w  temacie Definiowanie ofert usług w aplikacji [Bookings](define-service-offerings.md), aby włączyć powiadomienia SMS.

- W aplikacji Booking in Teams przejdź do **Ustawienia** >  **Typ** >  punktu w programie Ustawienia Typ terminuDadanie typu terminu i wybierz pozycję **Wyślij do nich wiadomości SMS**.

## <a name="tracking-and-metrics-for-sms-notifications"></a>Śledzenie i metryki dla powiadomień SMS

> [!NOTE]
> Musisz być administratorem usługi Teams, aby widzieć Teams i aplikacji Bookings w centrum administracyjnym usługi Teams administracyjnego.

Kluczowe dane dotyczące użycia powiadomień SMS można śledzić w Twojej organizacji w centrum administracyjnym usługi Teams administracyjnego. Raporty użycia zawierają dane, takie jak godzina i data wysłania, numer pochodzenia, typ wiadomości, typ zdarzenia i stan dostarczenia. Telemetria powiadomień SMS może być pomocna w prognozowaniu i budżetze powiadomień SMS po 1 marca 2022 r.

1. W centrum Teams administracyjnym **: powiadomienia SMS o wirtualnych odwiedzinach**.

2. Na stronie **Raporty & wiadomości SMS** wybierz pozycję Użycie powiadomień SMS.

    :::image type="content" source="../media/analytics-reporting.png" alt-text="Zrzut ekranu: Strona analiza i raportowanie powiadomień SMS w centrum Teams administracyjnego":::

Zawartość pokrewna

[Microsoft Bookings](bookings-overview.md)\
[Włączanie i wyłączanie aplikacji Microsoft Bookings](turn-bookings-on-or-off.md)\
[Uzyskiwanie aplikacji Microsoft Bookings dla systemów iOS i Android](get-bookings-app.md)\
