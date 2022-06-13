---
title: Zarządzanie żądaniami licencji
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- MACBillingLicensesRequests
- AdminSurgePortfolio
search.appverid: MET150
description: Dowiedz się, jak przeglądać i zatwierdzać lub odrzucać żądania licencji od użytkowników dotyczące subskrypcji Microsoft 365 dla firm.
ms.date: 04/22/2022
ms.openlocfilehash: dfe8410ce894e19489664396866917e4c5bb3dd4
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044252"
---
# <a name="manage-license-requests"></a>Zarządzanie żądaniami licencji

> [!NOTE]
> Informacje zawarte w tym artykule dotyczą tylko produktów zakupionych samodzielnie. Aby dowiedzieć się więcej, zobacz [Samoobsługowy zakup — często zadawane pytania](../subscriptions/self-service-purchase-faq.yml).

Jeśli wyłączysz zakupy samoobsługowe w organizacji, możesz użyć żądań licencji do zarządzania procesem żądania licencji dla użytkowników. Gdy użytkownik próbuje dokonać zakupu samoobsługowego dla zablokowanego produktu, może przesłać do Ciebie żądanie licencji, administratora. Podczas tworzenia żądania mogą dodawać nazwy innych użytkowników, którzy również potrzebują licencji dla produktu.

> [!NOTE]
> Jeśli zablokujesz użytkownikom możliwość dokonywania zakupów samoobsługowych, firma Microsoft nie wyśle im marketingowych wiadomości e-mail. Ponadto jeśli używają wersji próbnej produktu, nie widzą monitów o jego zakup. Aby dowiedzieć się więcej, zobacz [Zarządzanie zakupami samoobsługowymi (administrator).](../subscriptions/manage-self-service-purchases-admins.md)

Aby wyświetlić żądania licencji i zarządzać nimi, administrator korzysta z karty **Żądania** na stronie **Licencjonowanie** . Lista zawiera nazwę żądanego produktu, nazwę osoby żądającej licencji, żądaną datę i stan żądania. Administratorzy mogą filtrować listę, aby wyświetlić żądania oczekujące lub zakończone. Żądania są przechowywane przez 30 dni.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wykonywać zadania opisane w tym artykule, musisz być administratorem globalnym. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).

## <a name="use-your-own-request-process"></a>Korzystanie z własnego procesu żądania

Jeśli Twoja organizacja ma własny proces żądania, możesz go zamiast tego użyć. Tworzysz komunikat, który jest wyświetlany użytkownikom podczas żądania licencji.

> [!IMPORTANT]
> Jeśli używasz własnego procesu żądania, żadne żądania nie są wyświetlane na karcie **Żądania** . Istniejące żądania przed dodaniem wiadomości będą nadal wyświetlane do momentu ich zatwierdzenia lub odrzucenia.

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licencje rozliczeniowe</a> > , a następnie wybierz kartę **Żądania**.
2. Zamiast tego wybierz pozycję **Użyj istniejącego procesu żądania**.
3. W okienku po prawej stronie w polu **Komunikat** wpisz komunikat, który użytkownicy mają zobaczyć podczas żądania licencji. Jeśli chcesz również dołączyć link do zasad organizacji lub innej dokumentacji, wprowadź adres URL w polu tekstowym **Link do dokumentacji (opcjonalnie** ).
4. Wybierz **Zapisz**.

Po powrocie do listy **Żądania zostanie wyświetlony** komunikat **Używasz własnego procesu żądania licencji**. Aby wprowadzić zmiany w wiadomości wysyłanej do użytkowników, wybierz pozycję **Użyj istniejącego procesu żądania**.

## <a name="stop-using-your-own-request-process"></a>Przestań korzystać z własnego procesu żądania

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licencje rozliczeniowe</a> > , a następnie wybierz kartę **Żądania**.
2. Zamiast tego wybierz pozycję **Użyj istniejącego procesu żądania**.
3. W okienku po prawej stronie wyczyść pole wyboru **Użyj procesu żądania mojej organizacji** .
4. Wybierz **Zapisz**.

## <a name="approve-or-deny-a-license-request"></a>Zatwierdzanie lub odrzucanie żądania licencji

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licencje rozliczeniowe</a> > , a następnie wybierz kartę **Żądania**.
2. Wybierz wiersz zawierający żądanie, które chcesz przejrzeć. W okienku po prawej stronie są wyświetlane szczegółowe informacje o tym, którzy użytkownicy chcą mieć licencje na produkt.
3. Aby odrzucić całe żądanie, wybierz pozycję **Nie zatwierdzaj**, a następnie w oknie dialogowym wybierz pozycję **Nie zatwierdzaj**.
4. Aby odmówić niektórym użytkownikom żądania, ale zatwierdzić innych, wybierz znak X według nazwy użytkowników, których chcesz usunąć. Ich nazwy są przenoszone w obszarze **Nie przypisuj do tych użytkowników**.
5. Jeśli masz więcej niż jeden produkt, w obszarze **Wybierz produkt** wybierz ten, dla którego chcesz przypisać licencje.
6. Aby uniemożliwić użytkownikom dostęp do określonych aplikacji i usług, **rozwiń węzeł Włącz lub wyłącz aplikacje i usługi**, a następnie wyczyść pola wyboru dla tych, które chcesz wykluczyć.
7. W dolnej części okienka wpisz opcjonalną wiadomość w polu tekstowym.
8. Po zakończeniu wybierz pozycję **Zatwierdź**. W okienku po prawej stronie są wyświetlane szczegóły żądania.
9. Zamknij okienko po prawej stronie.
    Użytkownicy otrzymują wiadomość e-mail z informacją, że ich żądanie zostało zatwierdzone lub odrzucone.

## <a name="related-content"></a>Zawartość pokrewna

[Przypisywanie licencji do użytkowników](../../admin/manage/assign-licenses-to-users.md) (artykuł)\
[Przenoszenie użytkowników do innej subskrypcji](../subscriptions/move-users-different-subscription.md) (artykuł)\
[Kupowanie lub usuwanie licencji subskrypcji](buy-licenses.md) (artykuł)\
[Samoobsługowy zakup — często zadawane pytania](../subscriptions/self-service-purchase-faq.yml)
