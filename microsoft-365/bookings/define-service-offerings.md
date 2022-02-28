---
title: Definiowanie ofert usług w usłudze Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Instrukcje wprowadzania informacji o ofertach usług, takich jak nazwa usługi, opis, lokalizacja, czas trwania i ceny. Możesz również oznaczyć pracowników uprawnionych do świadczenia usługi.
ms.openlocfilehash: 6b276d9ec2d943527f1a6d8ab310fc91406f216c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977626"
---
# <a name="define-your-service-offerings-in-bookings"></a>Definiowanie ofert usług w usłudze Bookings

Definiując oferty usług w usłudze Microsoft Bookings, ustawiasz nazwę, opis, lokalizację usługi (określasz, czy chcesz spotkać się osobiście, czy ma się spotkać online), czas trwania, domyślne przypomnienia dla klientów i personelu, notatki wewnętrzne dotyczące usługi i cen. Możesz również oznaczyć pracowników uprawnionych do świadczenia usługi. Gdy klienci przychodzą do Twojej firmowej witryny sieci Web w celu zarezerwowania terminu, widzą, jakie typy terminów są dostępne, wybierają osobę, która ma świadczyć usługę, i ile będzie kosztować ich usługa.

Możesz również dodać dostosowane informacje i adresy URL do potwierdzenia wiadomości e-mail i przypomnień, które wysyłasz, gdy ktoś książka usługi za pośrednictwem Twojej strony rezerwacji.

## <a name="create-the-service-details"></a>Tworzenie szczegółów usługi

1. W Microsoft 365 kliknij przycisk Uruchamianie aplikacji, a następnie wybierz pozycję **Bookings**.

2. Przejdź do **Ustawienia** ->  [Nawłaściwość usług i](https://outlook.office.com/bookings/settings/services) wybierz **pozycję Dodaj nową usługę**.

3. Na **stronie Szczegóły podstawowe** dodaj wybrane opcje.

   **Nazwa usługi**: wprowadź nazwę usługi. Jest to nazwa, która będzie wyświetlana w menu rozwijaym na stronie Kalendarz. Ta nazwa będzie także wyświetlana, gdy ktoś ręcznie doda termin na stronie Kalendarz i będzie wyświetlana jako kafelek na stronie Samoobsługowa.

   **Opis**: Wprowadzany opis jest wyświetlany po kliknięciu przez użytkownika ikony informacji na stronie samoobsługi.

   **Lokalizacja domyślna**: Ta lokalizacja jest wyświetlana w wiadomościach e-mail z potwierdzeniem i przypomnieniem dla personelu i klientów, a także będzie wyświetlana w zdarzeniu kalendarza utworzonym dla rezerwacji.

   **Dodawanie spotkania online**: to ustawienie włącza lub wyłącza spotkania online dla każdego terminu za pośrednictwem programu Teams lub Skype w zależności od tego, który klient zostanie skonfigurowany jako klient domyślny dla członka personelu.

   - Włączone:
     - Link do spotkania Teams lub spotkania programu Skype( unikatowy dla rezerwacji) zostanie dodany do zdarzenia kalendarza zarówno w kalendarzu personelu, jak i w kalendarzach klientów, wraz z informacjami o połączeniach telefonicznych.
     - Link dołączania do spotkania zostanie dodany do wszystkich wiadomości e-mail z potwierdzeniem i przypomnieniem, jak pokazano w poniższym przykładzie:

       :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Przykład linku dołączania do spotkania Teams u programu Bookings.":::

       > [!NOTE]
       > Teams spotkania można dołączać za pomocą aplikacji Teams dla urządzeń przenośnych, aplikacji klasycznej Teams, w przeglądarce internetowej lub telefonicznie. Zdecydowanie zalecamy włączenie usługi Teams jako domyślnej usługi spotkań online dla Twojej dzierżawy w celu najlepszego środowiska rezerwowania wirtualnych terminów.

   - Wyłączone:
     - Terminy nie będą zawierać opcji spotkania, a wszystkie pola powiązane ze spotkaniem, które pojawią się po włączeniu opcji Dodaj spotkanie **online** , nie będą wyświetlane.

   **Czas** trwania: jest to czas, przez jaki zostaną zarezerwowane wszystkie spotkania. Czas jest blokowany od czasu rozpoczęcia, który jest wybrany podczas rezerwacji. Pełny czas terminu zostanie zablokowany w kalendarzach personelu.

   **Bufor czasu**: włączenie tego ustawienia umożliwia dodawanie dodatkowego czasu do kalendarza personelu przy każdej rezerwacji terminu.

   Ten czas zostanie zablokowany w kalendarzu personelu i będzie miał wpływ na informacje o czasie wolnym/zajętym. Oznacza to, że jeśli termin kończy się o 15:00 i do końca spotkania dodano 10 minut buforu czasu, kalendarz personelu będzie pokazywany jako zajęty i nie do zarezerwowania do godziny 15:10. Może to być przydatne, jeśli pracownicy potrzebują czasu przed spotkaniem na przygotowanie się, na przykład u lekarza przeglądając wykres pacjenta lub doradcę finansowego, który przygotowuje odpowiednie informacje o koncie. Może być także przydatny po spotkaniu, na przykład gdy ktoś potrzebuje czasu na podróż do innej lokalizacji.

   **Cena nieo ustawiana**: Wybierz opcje cen, które będą wyświetlane na Self-Service stronie. Jeśli **opcja Cena nie jest ustawiona** , nie będzie wyświetlana cena ani odwołanie się do kosztów lub cen.

   **Uwagi**: To pole jest wyświetlane w zdarzeniu rezerwacji dla rezerwowanych pracowników, a także w zdarzeniu wyświetlanym na karcie Kalendarz w aplikacji sieci Web Bookings.

   **Maksymalna liczba** uczestników na wydarzenie: to ustawienie pozwala utworzyć usługi wymagające możliwości zarezerwowania tego samego terminu i tego samego personelu przez wiele osób (na przykład zajęć fitness). Rezerwowany będzie przedziale czasu dla wybranej usługi, personelu i czasu aż do określonej przez Ciebie maksymalnej liczby uczestników. Bieżącą wydajność terminu i uczestników można wyświetlić na karcie Kalendarz w aplikacji Bookings Web App.

   :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Example of setting maximum attendees in Bookings":::

   **Pozwól klientowi** zarządzać rezerwacją: To ustawienie określa, czy klient może modyfikować lub anulować rezerwację, jeśli rezerwacja została zarezerwowana za pośrednictwem karty Kalendarz w aplikacji Bookings Web App.

   - Włączone:

     Przycisk **Zarządzaj rezerwacją** pojawi się w wiadomości e-mail z potwierdzeniem od klienta. Po wybraniu tego przycisku przez klienta zostaną wyświetlone trzy opcje:

     - **Ponowne harmonogramy** Zaznaczenie tej opcji powoduje, że użytkownik jest na stronie witryny usługi Self-Service, na której może wybrać nową datę i/lub czas dla tej samej usługi i tego samego członka personelu z oryginalnej rezerwacji. Pamiętaj, że mimo że oryginalny członek personelu jest domyślnie dołączony do rezerwowania według ponownego wyboru, użytkownik ma również możliwość zmiany tego członka personelu.
     - **Anulowanie rezerwacji** Spowoduje to anulowanie rezerwacji i usunięcie jej z kalendarza personelu.
     - **Nowa rezerwacja** Ta opcja powoduje poprowadzenie użytkownika do strony Self-Service z wymienionymi wszystkimi usługami i pracownikami do planowania nowej rezerwacji.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Przycisk Zarządzaj rezerwacjami w umiędzy bookings.":::

      Zalecamy pozostawienie tego ustawienia włączonego tylko w przypadku, gdy nie masz już dostępu do strony Self-Service sieci Web.

   - Wyłączone:

     Użytkownik nie będzie miał możliwości zmiany harmonogramu ani anulowania rezerwacji podczas rezerwowania przy użyciu karty Kalendarz w aplikacji Bookings Web App. Podczas rezerwacji za pośrednictwem Self-Service klienci nadal będą mieli przycisk Zarządzaj rezerwacją i  wszystkie jego opcje, nawet jeśli to ustawienie jest wyłączone.

     Zalecamy wyłączenie tego ustawienia, jeśli chcesz ograniczyć dostęp do Self-Service strony. Ponadto zalecamy dodanie tekstu do wiadomości e-mail z potwierdzeniem i przypomnieniem, który informuje klientów o tym, jak wprowadzać zmiany w rezerwacjach za pomocą innych środków, na przykład przez dzwonienie do biura lub wysyłanie pomocy technicznej pocztą e-mail.

4. Na **stronie Opcje dostępności** możesz zobaczyć opcje wybrane na stronie Rezerwacja dla zasad planowania i  dostępności dla personelu. Aby uzyskać więcej informacji, [zobacz Ustawianie zasad planowania](set-scheduling-policies.md).

    :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Example of setting maximum attendees in Bookings.":::

5. **Cena domyślna**  Jest to cena, która będzie wyświetlana na Self-Service stronie. Jeśli **opcja Cena nie jest ustawiona** , nie będzie wyświetlana cena ani odwołanie się do kosztów lub cen.

6. **Notatki** To pole jest wyświetlane w zdarzeniu rezerwacji dla zarezerwowanych pracowników, a także w zdarzeniu wyświetlanym na karcie Kalendarz w aplikacji sieci Web Bookings.

7. **Pola niestandardowe** mogą być przydatne podczas zbierania informacji potrzebnych przy każdej rezerwacji określonego terminu. Przykłady to dostawca ubezpieczenia przed wizytą lekarz, typ pożyczki na rozmowy kwalifikacyjne, główne badania na temat informacji akademickich lub identyfikator kandydata na rozmowy kwalifikacyjne kandydatów. Te pola będą wyświetlane na stronie rezerwacji, gdy klienci zarezerwują terminy z Tobą i Twoim personelem.

   Adres e-mail, numer telefonu, adres i notatki klienta to pola nie wymienne, ale można je ustawić jako opcjonalne, zaznaczając pole wyboru **Wymagane obok każdego** pola.

8. Na **stronie Przypomnienia i potwierdzenia** możesz skonfigurować wysyłane przypomnienia i powiadomienia. Przypomnienia i powiadomienia są wysyłane do klientów, członków personelu lub obu tych osób w określonym czasie przed terminem. Zgodnie z preferencjami dla każdego terminu można utworzyć wiele wiadomości.

   :::image type="content" source="media/bookings-remind-confirm.jpg" alt-text="Wiadomość e-mail z potwierdzeniem od usługi Bookings.":::

   W tym miejscu możesz dołączyć dowolny dodatkowy tekst, na przykład informacje o ponownej sporządzaniu terminów lub o tym, co klienci powinni wprowadzić na spotkanie. Poniżej przedstawiono przykład dostosowanego tekstu dodanego do oryginalnej wiadomości e-mail z potwierdzeniem widocznej w **polu Dodatkowe informacje o potwierdzeniu e-mail** :

   :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Dodatkowe informacje w wiadomości e-mail dotyczącej usługi Bookings.":::

9. **Włączanie powiadomień SMS dla klienta** Jeśli ta opcja jest zaznaczona, wiadomości SMS są wysyłane do klienta, ale tylko jeśli się na to zdecyduje.

   - Pole zgody na ręczną rezerwację i Self-Service stronie:

     :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Pole zgody na program Bookings.":::

   - Powiadomienia SMS będą wyglądać następująco (pamiętaj, że powiadomienia SMS są obecnie dostępne tylko w Ameryce Północnej):

     :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="Powiadomienie sms z bookings.":::

10. Opcja **Domyślne opcje planowania** jest domyślnie włączona. Wyłącz przełącznik, jeśli chcesz dostosować sposób, w jaki klienci rezerwają określonego członka personelu.

11. **Opcje publikowania** Określ, czy ta usługa ma być wyświetlana jako rezerwowa na stronie usługi Self-Service, czy też chcesz, aby można było rezerwować usługę tylko na karcie Kalendarz w aplikacji Bookings Web App.
