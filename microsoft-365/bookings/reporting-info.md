---
title: Raportowanie informacji dotyczących usługi Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 03a9acc9-f29c-456b-9fb2-0f49474b2708
description: Dowiedz się, jak można wyświetlić 4-miesięczny widok działania Bookings
ms.openlocfilehash: 191194d112fe231c1a2f64245d33850ecb1266c0
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714312"
---
# <a name="reporting-info-for-bookings"></a>Informacje dotyczące raportowania dla Bookings

> [!NOTE]
> Ten artykuł ułatwia interakcję z najnowszą wersją Microsoft Bookings. Poprzednie wersje zostaną wycofane w najbliższych miesiącach.

Teraz w pliku TSV można wyświetlić czteromiesięczny widok kalendarza Bookings. W pliku TSV zostaną wyświetlone dane z czterech miesięcy, ale w ciągu roku możesz wybrać różne okresy czterech miesięcy.

Te informacje na poziomie terminu mogą służyć do wizualizowania aktywności klienta wokół kalendarza Bookings. Pliki TSV są plikami wartości rozdzielonymi tabulatorami. Możesz wyświetlić lub edytować plik w ten sposób za pomocą dowolnego edytora tekstów lub programu arkusza kalkulacyjnego, takiego jak Excel.

## <a name="see-four-months-of-booking-activity"></a>Zobacz cztery miesiące działania Booking

1. W Microsoft 365 wybierz pozycję Uruchamianie aplikacji, a następnie wybierz pozycję **Bookings**.

1. Na stronie głównej Bookings wybierz pozycję **Eksportuj**.

1. Na stronie **Eksportowanie ostatnich danych** wybierz zakres dat i wybierz pozycję **Eksportuj**.

1. Zapisz plik z nową nazwą i określ format .xls lub xlsx.

1. Otwórz plik, aby wyświetlić czteromiesięczny widok kalendarza Bookings.

1. Wybierz datę raportu i wybierz pozycję **Eksportuj**.

1. Pobrany raport zawiera nowy zestaw pól oprócz istniejących pól.

Raport zawiera następujące pola.

 - **Data & godzina**
- **Nazwa klienta**
- **Adres e-mail klienta**
- **Telefon klienta**
- **Adres klienta**
- **Personel**
- **Usługa**
- **Lokalizacja**
- **Czas trwania (minuty)**
- **Typ zdarzenia**

Ulepszony raport zawiera teraz następujące pola.

- **Typ cennika**   Domyślny typ cen ustawiony dla usługi podczas tworzenia usługi.
- **Cena**   Cena odpowiadająca wybranemu typowi cennika.
- **Waluty**   Typ waluty ustawiony dla firmy.
- **Uczestnicy DW**   Adresaci, którzy będą otrzymywać powiadomienia e-mail o rezerwacji. Można to określić w aplikacji Teams podczas tworzenia rezerwacji.
- **Liczba uczestników z kontami**   Ilu klientów zarezerwowało usługę rezerwacji grupowej.
- **Włączone powiadomienia tekstowe**   Czy klienci mogą otrzymywać powiadomienia sms związane z tekstem.
- **Pola niestandardowe**   Wszystkie pytania i odpowiedzi związane z pojedynczą rezerwacją są łączone w tym polu.
- **Identyfikator rezerwacji**   Jest to przydatne do identyfikowania tych samych rezerwacji usługi grupowej.
