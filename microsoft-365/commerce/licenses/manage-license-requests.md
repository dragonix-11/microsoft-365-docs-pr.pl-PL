---
title: Zarządzanie żądaniami licencji
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: micurn, nicholak
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- MACBillingLicensesRequests
- AdminSurgePortfolio
- commerce_licensing
search.appverid: MET150
description: Dowiedz się, jak przeglądać i zatwierdzać lub odrzucać żądania licencji od użytkowników w ramach Twojej Microsoft 365 dla firm.
ms.date: 06/07/2021
ms.openlocfilehash: 279894f8e6ffb3209a1b4f2a5201e62428f33b83
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985237"
---
# <a name="manage-license-requests"></a>Zarządzanie żądaniami licencji

> [!NOTE]
> Informacje zawarte w tym artykule dotyczą tylko produktów zakupionych samodzielnie. Aby dowiedzieć się więcej, zobacz [Często zadawane pytania dotyczące zakupu samoobsługi](../subscriptions/self-service-purchase-faq.yml).

Jeśli wyłączysz zakupy samoobsługowe w organizacji, możesz zarządzać procesem żądania licencji dla użytkowników za pomocą żądań licencji. Gdy użytkownik spróbuje dokonać zakupu samoobsługowego dla zablokowanego przez Ciebie produktu, może przesłać żądanie licencji do Ciebie, administratora. Gdy użytkownik poprosi o licencję, może dodać nazwy innych użytkowników, którzy także potrzebują licencji produktu.

> [!NOTE]
> Jeśli blokujesz użytkownikom dokonywanie zakupów samoobsługowych, firma Microsoft nie wysyła im marketingowych wiadomości e-mail. Ponadto, jeśli korzystasz z wersji próbnej produktu, nie widzą monitów o jego zakup. Aby dowiedzieć się więcej, zobacz [Zarządzanie zakupami samoobsługi (administrator](../subscriptions/manage-self-service-purchases-admins.md)).

Aby wyświetlić żądania licencji i zarządzać nimi, administrator używa karty **Wnioski** na **stronie Licencjonowanie** . Lista zawiera nazwę żądanego produktu, imię i nazwisko osoby żądacej licencji, żądaną datę oraz stan żądania. Administratorzy mogą filtrować listę, aby wyświetlić żądania oczekujące lub ukończone. Żądania są przechowywane przez 30 dni.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wykonać zadania z tego artykułu, musisz być administratorem globalnym. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).

## <a name="use-your-own-request-process"></a>Skorzystaj z własnego procesu żądania

Jeśli Twoja organizacja ma własny proces żądania, możesz go użyć zamiast tego. Tworzysz komunikat, który jest wyświetlany użytkownikom, gdy żądają licencji.

> [!IMPORTANT]
> Jeśli korzystasz z własnego procesu żądania, na karcie Żądania nie są wyświetlane **żadne** żądania. Istniejące żądania od zanim dodano wiadomość będą nadal wyświetlane do czasu ich zatwierdzenia lub odrzucenia.

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > , a następnie wybierz **kartę** Wnioski.
2. Zamiast **tego wybierz pozycję Użyj istniejącego procesu żądania**.
3. W prawym okienku w **polu Wiadomość** wpisz wiadomość, którą użytkownicy będą widzieć, gdy zażądają licencji. Jeśli chcesz dodać link do zasad organizacji lub innej dokumentacji, wprowadź adres URL w polu tekstowym Link do dokumentacji **(** opcjonalnie).
4. Wybierz **Zapisz**.

Po powrocie do listy **Żądania** zostanie wyświetlony komunikat Używasz **procesu żądania licencji**. Aby wprowadzić zmiany w wiadomości wysyłanej do użytkowników, wybierz pozycję Zamiast tego użyj **istniejącego procesu żądania**.

## <a name="stop-using-your-own-request-process"></a>Zaprzestanie korzystania z własnego procesu żądania

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > , a następnie wybierz **kartę** Wnioski.
2. Zamiast **tego wybierz pozycję Użyj istniejącego procesu żądania**.
3. W prawym okienku wyczyść pole wyboru Użyj procesu żądania **mojej** organizacji.
4. Wybierz **Zapisz**.

## <a name="approve-or-deny-a-license-request"></a>Zatwierdzanie lub odrzucanie wniosku o licencję

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > , a następnie wybierz **kartę** Wnioski.
2. Zaznacz wiersz zawierający żądanie, które chcesz przejrzeć. W prawym okienku są szczegółowe informacje o tym, którzy użytkownicy chcą mieć licencje na produkt.
3. Aby odrzucić cały wniosek **, wybierz pozycję** Nie zatwierdzaj, a w oknie dialogowym wybierz pozycję **Nie zatwierdzaj**.
4. Aby odrzucić niektórych użytkowników, ale zatwierdzić innych, wybierz znak X przy nazwie użytkownika, którego chcesz usunąć. Ich nazwy są przenoszone **w obszarze Nie przypisuj do tych użytkowników**.
5. Jeśli masz więcej niż jeden produkt, w **obszarze Wybierz produkt** wybierz ten, do którego chcesz przypisać licencje.
6. Aby uniemożliwić użytkownikom dostęp do określonych aplikacji i usług, rozwiń pozycję Włącz lub wyłącz aplikacje i **usługi, a** następnie wyczyść pola wyboru obok aplikacji, które chcesz wykluczyć.
7. W dolnej części okienka wpisz opcjonalną wiadomość w polu tekstowym.
8. Po zakończeniu wybierz pozycję **Zatwierdź**. W prawym okienku są szczegółowe informacje o żądaniu.
9. Zamykanie prawego okienka.
    Użytkownicy otrzymają wiadomość e-mail z powiadomieniem, że ich żądanie zostało zatwierdzone lub odrzucone.

## <a name="related-content"></a>Zawartość pokrewna

[Przypisywanie licencji użytkownikom](../../admin/manage/assign-licenses-to-users.md) (artykuł)\
[Przenoszenie użytkowników do innej subskrypcji](../subscriptions/move-users-different-subscription.md) (artykuł)\
[Kupowanie lub usuwanie licencji subskrypcji](buy-licenses.md) (artykuł)
