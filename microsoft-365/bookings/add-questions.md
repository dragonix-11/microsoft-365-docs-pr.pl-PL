---
title: Dodaj pytania niestandardowe i wymagane do strony rezerwacji
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: fd6b7587-5055-4bcd-83a4-13bd4929bfff
description: Jeśli musisz zadawać klientom pytania podczas rezerwacji spotkania online, możesz dodać niestandardowe pytania i wymagane pytania do strony rezerwacji.
ms.openlocfilehash: d42f883f3d58882ec5a2e8e8e2bbe7baf7ed3232
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637698"
---
# <a name="add-custom-and-required-questions-to-the-booking-page"></a>Dodaj pytania niestandardowe i wymagane do strony rezerwacji

Bookings umożliwia tworzenie pytań, które należy zadać klientom podczas rezerwacji terminów. Pozwala również wybrać, które pytania są wymagane.

Pytania można skojarzyć z usługą, aby każda usługa mogła mieć inny zestaw pytań. Na przykład stylista włosów może zapytać klientów, którzy rezerwują termin kolorowania włosów, czy mają jakieś znane alergie na wybielenia lub odcienie. Dzięki temu Ty i Twoi klienci zaoszczędzicie czas, gdy przyjadą na spotkanie.

Klienci zobaczą niestandardowe pytania podczas tworzenia terminu na stronie rezerwacji. Pracownicy zobaczą niestandardowe pytania podczas tworzenia nowej rezerwacji z kalendarza Bookings lub podczas wyświetlania istniejącego terminu. Bookings zapisuje wszystkie pytania na liście wzorcowej, aby nie trzeba było ponownie tworzyć tych samych pytań dla każdej usługi. Możesz również wybrać, czy pytania są wymagane, czy opcjonalne.

> [!NOTE]
> Odpowiedzi klienta na pytania można znaleźć, gdy spojrzysz na jego termin w kalendarzu rezerwacji.

Aby uzyskać więcej informacji o sposobie personalizowania i dostosowywania strony rezerwacji, zobacz [Dostosowywanie strony rezerwacji](customize-booking-page.md).

## <a name="add-custom-questions-to-your-services"></a>Dodawanie niestandardowych pytań do usług

1. Zaloguj się do Microsoft 365 i przejdź do **Bookings**.

1. Wybierz kalendarz.

1. Przejdź do **obszaru Usługi** i edytuj **istniejącą usługę lub Dodaj usługę**.

1. Wybierz sekcję **Pola niestandardowe** .

   Dodaliśmy już kilka podstawowych pytań dotyczących informacji o kliencie: adres e-mail klienta, numer telefonu, adres klienta i notatki klienta. Przy pierwszym uruchomieniu pytania dotyczące informacji o kliencie są wyróżnione kolorem szarym. Oznacza to, że użytkownik zobaczy to pytanie. Jeśli wybierzesz pytanie, pole wyróżnienia wokół niego zniknie, a klient nie zostanie poproszony o to pytanie.

   W tym przykładzie numer telefonu i notatki klientów zostały wyłączone i utworzeliśmy dwa nowe pytania niestandardowe do zadawania.

   ![Obraz przedstawiający ekran pytań niestandardowych.](../media/bookings-questions-custom-fields.png)

1. Aby pytanie było wymagane, zaznacz pole wyboru **Wymagane** . Klient nie będzie mógł ukończyć rezerwacji, dopóki nie odpowie na wymagane pytania.

1. Aby utworzyć pytanie niestandardowe, wybierz **pozycję Dodaj pytanie** w górnej części panelu. Napisz pytanie, a następnie wybierz pozycję **Zapisz**.

1. Kliknij pytanie, aby go włączyć. Wokół niego zostanie wyświetlone wyróżnione pole i pytanie zostanie włączone.

1. Kliknij przycisk **OK** w górnej części strony, a następnie **zapisz usługę**.

Bookings zapisze wszystkie pytania niestandardowe na liście głównej, aby można było łatwo dodawać pytania do każdej usługi bez konieczności wielokrotnego wpisywania tych samych pytań. Jeśli na przykład otworzysz inną usługę, pytanie utworzone dla pierwszej usługi zostanie wyświetlone w sekcji Pola niestandardowe, ale zostanie wyłączone. Kliknij pytanie, aby wyświetlić wyróżniony prostokąt i włączyć pytanie.

W tym przykładzie widać, że pytania, które zostały dodane do pierwszej usługi, są dostępne dla tej usługi. Wszelkie pytania utworzone dla tej usługi będą dostępne dla wszystkich usług.

   ![Obraz przedstawiający pytania, które pojawiają się w przypadku wielu usług.](../media/bookings-questions-services.png)

Jeśli twoja strona rezerwacji jest już opublikowana, nie musisz robić nic innego. Klienci zobaczą pytania podczas następnej rezerwacji z Tobą. Jeśli strona rezerwacji nie została jeszcze opublikowana, przejdź do **strony rezerwacji** z Outlook w sieci Web, a następnie wybierz pozycję **Zapisz i opublikuj**.

> [!WARNING]
> Możesz również usunąć pytania z listy głównej. Jeśli jednak usuniesz pytanie, zostanie ono usunięte z każdej usługi. Zalecamy wyłączenie pytania, wybierając je, aby upewnić się, że nie ma to wpływu na żadne inne usługi. Widać, że pytanie jest wyłączone, jeśli nie jest otoczone wyróżnionym prostokątem.

## <a name="customer-experience"></a>Obsługa klienta

Gdy klienci zarezerwują spotkanie z Tobą, podstawowe pytania dotyczące informacji o kliencie zostaną wyświetlone w sekcji **Dodawanie szczegółów** . Wszelkie dodane niestandardowe pytania znajdują się w sekcji **Podaj dodatkowe informacje** .

![Obraz przedstawiający to, co klienci widzą po włączeniu pytań.](../media/bookings-questions-customer.png)

## <a name="staff-experience"></a>Doświadczenie personelu

Gdy klienci zarezerwują spotkanie z Tobą, pracownicy zobaczą pytania i odpowiedzi klienta w kalendarzu rezerwacji. Aby go zobaczyć, przejdź do **Bookings** \> **Calendar**, a następnie otwórz termin.

![Obraz przedstawiający informacje o tym, co pracownicy widzą, gdy pytania są włączone.](../media/bookings-questions-staff.png)
