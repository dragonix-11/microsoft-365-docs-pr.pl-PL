---
title: Definiowanie oferty usługi Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Instrukcje dotyczące wprowadzania informacji o ofertach usług, w tym nazwy usługi, opisu, lokalizacji, czasu trwania i cennika. Możesz również otagować pracowników, którzy są wykwalifikowani do świadczenia usługi.
ms.openlocfilehash: 2daae2139e3d2d4107f4aaed1b94ca655877000a
ms.sourcegitcommit: af2b570e76e074bbef98b665b5f9a731350eda58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2022
ms.locfileid: "66185088"
---
# <a name="define-your-service-offerings-in-bookings"></a>Definiowanie ofert usług w obszarze Rezerwacje

Podczas definiowania ofert usług w Microsoft Bookings należy ustawić nazwę usługi, opis, lokalizację (wybrać, czy chcesz spotkać się osobiście, czy spotkanie online), czas trwania, domyślne przypomnienia dla klientów i pracowników, wewnętrzne notatki dotyczące usługi i cennik. Możesz również otagować pracowników, którzy są wykwalifikowani do świadczenia usługi. Następnie, gdy klienci przychodzą do twojej firmowej witryny internetowej w celu zarezerwowania terminu, mogą dokładnie zobaczyć, jakie typy terminów są dostępne, wybrać osobę, którą chcą świadczyć usługę i ile będzie kosztować ich usługa.

Możesz również dodać dostosowane informacje i adresy URL do potwierdzenia wiadomości e-mail i przypomnień, które wysyłasz, gdy ktoś zarezerwuje usługę za pośrednictwem strony rezerwacji.

## <a name="watch-create-a-new-service"></a>Obejrzyj: Tworzenie nowej usługi

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuKXH]

## <a name="steps"></a>Kroki

1. W Microsoft 365 wybierz pozycję Uruchamianie aplikacji, a następnie wybierz pozycję **Rezerwacje**.

2. Przejdź do **pozycji Usługi kalendarza** >  i wybierz pozycję **Dodaj nową usługę**.

3. Na stronie **Szczegóły podstawowe** dodaj wybrane opcje.

   **Nazwa usługi**: wprowadź nazwę usługi. Jest to nazwa, która będzie wyświetlana w menu rozwijanym na stronie Kalendarz. Ta nazwa będzie również wyświetlana, gdy ktoś ręcznie doda termin na stronie Kalendarz i będzie wyświetlany jako kafelek na stronie Samoobsługowe.

   **Opis**: Wprowadzony opis jest wyświetlany, gdy użytkownik kliknie ikonę informacji na stronie Samoobsługowe.

   **Lokalizacja domyślna**: ta lokalizacja będzie wyświetlana w wiadomościach e-mail z potwierdzeniem i przypomnieniem zarówno dla pracowników, jak i klientów, i będzie wyświetlana w wydarzeniu kalendarza utworzonym dla rezerwacji.

   **Dodawanie spotkania online**: to ustawienie włącza lub wyłącza spotkania online dla każdego terminu za pośrednictwem Teams lub Skype, w zależności od tego, który z nich został skonfigurowany jako domyślny klient dla pracownika.

   - Włączone:
     - Link do spotkania Teams lub Skype, unikatowy dla rezerwacji, zostanie dodany do wydarzenia kalendarza zarówno w kalendarzu pracowników, jak i w kalendarzach klientów, wraz z informacjami o telefonie.
     - Link do dołączenia do spotkania zostanie dodany do wszystkich wiadomości e-mail z potwierdzeniem i przypomnieniami, jak pokazano w poniższym przykładzie:

       :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Przykład linku do Teams spotkania w bookings.":::

       > [!NOTE]
       > Teams spotkania można dołączać za pośrednictwem aplikacji mobilnej Teams, aplikacji klasycznej Teams, przeglądarki internetowej lub telefonicznego połączenia telefonicznego. Zdecydowanie zalecamy włączenie Teams jako domyślnej usługi spotkań online dla dzierżawy, aby jak najlepiej rezerwować terminy wirtualne.

   - Wyłączone:
     - Terminy nie będzie zawierać opcji spotkania, a wszystkie pola związane ze spotkaniem wyświetlane po włączeniu **funkcji Dodaj spotkanie online** nie będą wyświetlane.

   **Czas trwania**: Na ten czas będą zarezerwowane wszystkie spotkania. Czas jest blokowany od godziny rozpoczęcia, która jest wybierana podczas rezerwacji. Pełny czas mianowania zostanie zablokowany w kalendarzach personelu.

   **Czas buforowania**: włączenie tego ustawienia umożliwia dodanie dodatkowego czasu do kalendarza personelu przy każdym zarezerwowaniu terminu.

   Czas zostanie zablokowany w kalendarzu personelu i będzie mieć wpływ na informacje o wolnym/zajętym czasie. Oznacza to, że jeśli termin kończy się o godzinie 15:00 i do końca spotkania dodano 10 minut czasu buforowania, kalendarz personelu będzie wyświetlany jako zajęty i nie można go zarezerwować do godziny 15:10. Może to być przydatne, jeśli personel potrzebuje czasu przed spotkaniem w celu przygotowania, takiego jak lekarz przeglądujący wykres pacjenta lub doradca finansowy przygotowujący odpowiednie informacje o koncie. Może to być również przydatne po spotkaniu, na przykład gdy ktoś potrzebuje czasu na podróż do innej lokalizacji.

   **Nie ustawiono ceny**: wybierz opcje cen, które będą wyświetlane na stronie Self-Service. Jeśli **nie ustawiono opcji Cena** , nie zostanie wyświetlona żadna cena ani odwołanie do kosztu lub ceny.

   **Uwagi**: To pole pojawia się w przypadku rezerwacji dla zarezerwowanego personelu, a także w przypadku zdarzenia, które pojawia się na karcie Kalendarz w aplikacji internetowej Bookings.

   **Maksymalna liczba uczestników na wydarzenie**: to ustawienie umożliwia tworzenie usług, które wymagają wielu osób zarezerwowania tego samego czasu spotkania i tego samego personelu (na przykład zajęć fitness). Przedział czasu terminu dla wybranej usługi, personelu i czasu będzie dostępny do zarezerwowania do momentu osiągnięcia maksymalnej liczby uczestników, określonej przez Ciebie. Aktualną pojemność terminu i uczestników można wyświetlić na karcie Kalendarz w aplikacji internetowej Bookings.

   :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Przykład ustawiania maksymalnej liczby uczestników w obszarze Rezerwacje":::

   **Pozwól klientowi zarządzać rezerwacją**: to ustawienie określa, czy klient może zmodyfikować lub anulować rezerwację, pod warunkiem, że została ona zarezerwowana za pośrednictwem karty Kalendarz w aplikacji internetowej Bookings.

   - Włączone:

     Przycisk **Zarządzaj rezerwacją** zostanie wyświetlony w wiadomości e-mail z potwierdzeniem klienta. Po wybraniu tego przycisku przez klienta zostaną wyświetlone trzy opcje:

     - **Harmonogramu** Wybranie tej opcji powoduje przełączenie użytkownika na stronę Self-Service specyficzną dla usługi, gdzie może wybrać nową godzinę i/lub datę dla tej samej usługi i tego samego pracownika z oryginalnej rezerwacji. Należy pamiętać, że nawet jeśli pierwotny pracownik jest domyślnie dołączony do zarezerwowanej rezerwacji, użytkownik ma również możliwość zmiany członka personelu.
     - **Anulowanie rezerwacji** Spowoduje to anulowanie rezerwacji i usunięcie jej z kalendarza personelu.
     - **Nowa rezerwacja** Ta opcja powoduje przełączenie użytkownika na stronę Self-Service ze wszystkimi wymienionymi usługami i personelem w celu zaplanowania nowej rezerwacji.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Przycisk Zarządzaj rezerwacjami w obszarze Rezerwacje.":::

      Zalecamy pozostawienie tego ustawienia włączonego tylko wtedy, gdy klienci uzyskują dostęp do strony Self-Service.

   - Wyłączone:

     Użytkownik nie będzie mógł zmienić harmonogramu lub anulować rezerwacji podczas rezerwacji za pośrednictwem karty Kalendarz w aplikacji internetowej Bookings. Jednak podczas rezerwacji za pośrednictwem strony Self-Service klienci nadal będą mieć przycisk **Zarządzaj rezerwacją** i wszystkie jego opcje, nawet jeśli to ustawienie jest wyłączone.

     Zalecamy wyłączenie tego ustawienia, jeśli chcesz ograniczyć dostęp do strony Self-Service. Ponadto zalecamy dodanie tekstu do wiadomości e-mail z potwierdzeniem i przypomnieniem, które informują klientów, jak wprowadzić zmiany w rezerwacji za pośrednictwem innych środków, takich jak wywołanie biura lub wysłanie wiadomości e-mail do działu pomocy technicznej.

4. Na stronie **Opcje dostępności** można wyświetlić opcje wybrane na **stronie Rezerwacja** dla zasad planowania i dostępności dla personelu. Aby uzyskać więcej informacji, zobacz [Ustawianie zasad planowania](set-scheduling-policies.md).

5. **Cena domyślna**  Jest to cena wyświetlana na stronie Self-Service. Jeśli **nie ustawiono opcji Cena** , nie zostanie wyświetlona żadna cena ani odwołanie do kosztu lub ceny.

6. **Notatki** To pole jest wyświetlane w przypadku rezerwacji dla zarezerwowanego personelu, a także w przypadku zdarzenia, które pojawia się na karcie Kalendarz w aplikacji internetowej Rezerwacje.

7. **Pola niestandardowe** mogą być przydatne podczas zbierania informacji potrzebnych za każdym razem, gdy zostanie zarezerwowany konkretny termin. Przykłady obejmują dostawcę ubezpieczeń przed wizytą w klinice, typ pożyczki na konsultacje pożyczkowe, studia na potrzeby doradztwa akademickiego lub identyfikator wnioskodawcy na rozmowy kwalifikacyjne. Te pola pojawią się na stronie Rezerwacja, gdy klienci zarezerwują terminy u Ciebie i Twoich pracowników.

   Adres e-mail klienta, numer telefonu, adres i notatki to pola, które nie są wymienne, ale możesz je dodać jako opcjonalne, usuwając zaznaczenie pola **Wymagane** obok każdego pola.

8. Na stronie **Przypomnienia i potwierdzenia** możesz skonfigurować wysyłane przypomnienia i powiadomienia. Przypomnienia i powiadomienia są wysyłane do klientów, pracowników lub obu tych osób w określonym czasie przed terminem. Dla każdego terminu można utworzyć wiele komunikatów zgodnie z preferencjami.

   :::image type="content" source="media/bookings-remind-confirm-2.png" alt-text="Wiadomość e-mail z potwierdzeniem z rezerwacji.":::

   W tym miejscu możesz dołączyć dowolny dodatkowy tekst, taki jak informacje o zmianach terminu lub o tym, co klienci powinni wnieść na spotkanie. Poniżej przedstawiono przykład dostosowanego tekstu dodanego do oryginalnej wiadomości e-mail z potwierdzeniem widocznej w polu **Dodatkowe informacje dotyczące potwierdzenia wiadomości e-mail** :

   :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Dodatkowe informacje w wiadomości e-mail dotyczącej rezerwacji.":::

9. **Włączanie powiadomień sms dla klienta** Jeśli ta opcja zostanie wybrana, SMS wiadomości są wysyłane do klienta, ale tylko wtedy, gdy się zdecydują.

   - Pole wyboru na stronie rezerwacji ręcznej i Self-Service:

     :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Pole wyboru w obszarze Rezerwacje.":::

   - Powiadomienia sms będą wyglądać następująco (zwróć uwagę, że powiadomienia SMS są obecnie dostępne tylko w Ameryka Północna):

     :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="Powiadomienie tekstowe z rezerwacji.":::

10. **Domyślne opcje planowania** są domyślnie włączone. Wyłącz przełącznik, jeśli chcesz dostosować sposób, w jaki klienci rezerwują określonego pracownika.

11. **Opcje publikowania** Określ, czy ta usługa ma być wyświetlana jako rezerwowalna na stronie Self-Service, czy też usługa ma być zarezerwowana tylko na karcie Kalendarz w aplikacji internetowej Bookings.
