---
title: Informacje dotyczące raportowania dla usługi Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 03a9acc9-f29c-456b-9fb2-0f49474b2708
description: Dowiedz się, jak wyświetlić 4-miesięczny widok aktywności dotyczącej aplikacji Bookings
ms.openlocfilehash: 70d73da86e40555a5754a4284cbfbb0510e8c9e6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984616"
---
# <a name="reporting-info-for-bookings"></a>Informacje raportowania dla programu Bookings

W pliku TSV możesz teraz wyświetlać kalendarz aplikacji Bookings w widoku czterech miesięcy. Plik TSV zawiera dane z czterech miesięcy, ale można wybrać inne cztery okresy miesięczne w ciągu roku.

Te informacje o poziomie umówionej pracy mogą być używane do wizualizowania działań klientów wokół kalendarza aplikacji Bookings. Pliki TSV to pliki wartości oddzielone tabulatorami. Taki plik można wyświetlać lub edytować w dowolnym edytorze tekstów lub programie do arkuszy kalkulacyjnych, na przykład w Excel.

## <a name="see-four-months-of-booking-activity"></a>Zobacz cztery miesiące aktywności na temat rezerwacji

1. W Microsoft 365 kliknij przycisk Uruchamianie aplikacji, a następnie wybierz pozycję **Bookings**.

1. Na stronie głównej aplikacji Bookings wybierz pozycję **Eksportuj**.

1. Na **stronie Eksportowanie ostatnio wybranych danych** wybierz zakres dat i wybierz pozycję **Eksportuj**.

1. Zapisz plik pod nową nazwą i określ format .xls lub xlsx.

1. Otwórz plik, aby wyświetlić widok kalendarza aplikacji Bookings z czterema miesiącami.

1. Wybierz datę raportu, a następnie wybierz pozycję **Eksportuj**.

1. Pobrany raport zawiera nowy zestaw pól oprócz istniejących pól.

Raport zawiera następujące pola.

 - **Data & czas**
- **Nazwa klienta**
- **Adres e-mail klienta**
- **Informacje Telefon**
- **Adres klienta**
- **Personel**
- **Usługa**
- **Lokalizacja**
- **Czas trwania (minuty)**
- **Typ zdarzenia**

Ulepszony raport zawiera teraz następujące pola.

- **Typ ceny**   Domyślny typ cennika ustawiony dla usługi podczas tworzenia usługi.
- **Cena**   Cena odpowiadająca wybranego typu cen.
- **Waluta**   Zestaw typów waluty dla firmy.
- **Uczestnicy w polu DW**   Adresaci, którzy będą otrzymywać powiadomienia e-mail dotyczące rezerwacji. Można to określić w aplikacji Teams podczas tworzenia rezerwacji.
- **Liczba uczestników zalogowanych**   Ilu klientów rezerwowała usługę rezerwacji grupowych.
- **Włączone powiadomienia tekstowe**   Czy klienci mogą otrzymywać powiadomienia SMS dotyczące tekstu.
- **Pola niestandardowe**   Wszystkie pytania i odpowiedzi związane z pojedynczą rezerwacją są łączone w tym polu.
- **Identyfikator rezerwacji**   Jest to pomocne przy identyfikowaniu tych samych rezerwacji usługi grupy.
