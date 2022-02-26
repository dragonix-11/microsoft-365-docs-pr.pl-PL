---
title: Ustawianie czasu buforu w uwitrynie Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Ustaw czas buforu przed lub po terminie w aplikacji Microsoft Bookings, aby zezwolić na oczyszczenie lub zresetowanie sprzętu.
ms.openlocfilehash: c3d07be3c858eca5f6e9a672581b386625f5dd80
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973522"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Ustawianie czasu buforu w uwitrynie Microsoft Bookings

Niektóre terminy mogą wymagać czasu przed spotkaniem z klientem lub po nim w celu skonfigurowania, oczyszczenia lub zresetowania pokoju oraz sprzętu. Jeśli jesteś w podróży między terminami z klientami, możesz potrzebować czasu, aby upewnić się, że Ty i Twój zespół możecie podróżować między terminami bez konieczności oczekiwania przez klienta.

Możesz ustawić czas buforu przed rozpoczęciem terminów, po zakończeniu terminów lub w obu tych przypadkach, aby zapewnić personelowi dodatkowy czas potrzebny do przygotowania się na następne terminy.

## <a name="set-buffer-time-defaults"></a>Ustawianie wartości domyślnych czasu buforu

Wartości domyślne buforu czasu są ustawiane na stronie **Szczegóły** usługi w usłudze Bookings. Podobnie jak wszystkie ustawienia domyślne usług ustawione na tej stronie, te wartości domyślne mogą być edytowane przez Ciebie w celu zaspokojenia konkretnych potrzeb klientów w przypadku określonej rezerwacji.

Ustawienie czasu buforu znajduje się tuż poniżej listy Domyślne  s wyboru czasu trwania na stronie **Szczegóły** usługi. Przed ustawieniem dla danej usługi należy włączyć ustawienie czasu buforu, wybierając przełącznik czasu buforu. Powoduje to **pojawianie** się  menu przed i po, które służą do wyboru domyślnego czasu przechowywania przed każdą rezerwacją i po każdej rezerwacji, jak pokazano poniżej:

   ![Obraz aplikacji Bookings z włączonym czasem buforu czasu.](../media/bookings-buffertime.png)

## <a name="buffer-time-and-appointment-timing"></a>Bufor czasu i chronometrażu terminu

Aby uniknąć zamieszania w sytuacji, gdy klienci spodziewają się spotkać się z Tobą, w kalendarzu aplikacji Bookings jest przedstawiany bufor czasu i rzeczywisty czas spotkań (czas, który klienci spodziewają się spotkania z Tobą), a także w potwierdzeniach e-mail i przypomnieniach dla odpowiedniego personelu. Na przykład poniżej przedstawiono to, co można zobaczyć w aplikacji Bookings w przypadku terminu z klientem, który obejmuje 15 minut buforu przed terminem.

Zwróć uwagę, że samo zdarzenie (po lewej stronie poniższej ilustracji) pokazuje jaśniejsze cieniowanie dla czasu buforu i ciemniejsze cieniowanie rzeczywistego terminu u klienta. W wywołaniu terminu (który jest otwierany po wybraniu zdarzenia) wyraźnie podano, że z 10:00 do 10:00 z Użytkownikiem Katie Jordan jest do dyspozycji 15 minut buforu czasu przed tym terminem i 0 minut po nim. Potwierdzenia i przypomnienia dla personelu w podobny sposób odwołują się do konkretnego buforu i czasu spotkania, podczas gdy klient może otrzymać tylko potwierdzenia i przypomnienia odwołujące się do terminu o godzinie 9:00 do 10:00.

   ![Obraz przedstawiający call-out appointment bookings z wyświetloną godziną buforu czasu.](../media/bookings-buffertime-callout.png)

## <a name="buffer-time-and-availability"></a>Bufor czasu i dostępności

Twoi klienci nie widzą bezpośrednio ustawionego czasu buforu i nie mogą ich zmienić. Ponieważ jednak czas buforu jest używany do obliczenia ogólnego czasu trwania usługi, klienci widzą, że Ty i Twoi odpowiedni personel rezerwujecie zarówno w czasie buforu, jak i w zwykłych terminach. Klienci widzą również dostępność tylko dla Ciebie i Twojego personelu, jeśli jest wystarczająco dużo czasu zarówno dla terminu, jak i jego buforu czasu.

Na przykład termin jednogodzinny z 15-minutowym czasem buforu przed terminem wymaga dostępnego bloku czasowego z co najmniej 1 godziną i 15 minutami. Termin dla tej usługi wypełni zatem 75-minutowy okres w kalendarzu i będzie wymagał 75 minut dostępności na rezerwację bez konfliktu.
