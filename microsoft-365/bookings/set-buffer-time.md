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
ms.openlocfilehash: a33159b0b5f168bbb61c88bc9b4181e05c8abbb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329323"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Ustawianie czasu buforu w uwitrynie Microsoft Bookings

Niektóre terminy mogą wymagać czasu przed spotkaniem z klientem lub po nim w celu skonfigurowania, oczyszczenia lub zresetowania pokoju oraz sprzętu. Jeśli jesteś w podróży między terminami z klientami, możesz potrzebować czasu, aby upewnić się, że Ty i Twój zespół możecie podróżować między terminami bez konieczności oczekiwania przez klienta.

Możesz ustawić czas buforu przed rozpoczęciem terminów, po zakończeniu terminów lub w obu tych przypadkach, aby zapewnić personelowi dodatkowy czas potrzebny do przygotowania się na następne terminy.

## <a name="set-buffer-time-defaults"></a>Ustawianie wartości domyślnych czasu buforu

Wartości domyślne buforu czasu są ustawiane na stronie **Szczegóły** usługi w usłudze Bookings. Podobnie jak wszystkie ustawienia domyślne usług ustawione na tej stronie, te wartości domyślne mogą być edytowane przez Ciebie w celu zaspokojenia konkretnych potrzeb klientów w przypadku określonej rezerwacji.

Ustawienie czasu buforu znajduje się tuż poniżej listy Domyślne  s wyboru czasu trwania na stronie **Szczegóły** usługi. Przed ustawieniem dla danej usługi należy włączyć ustawienie czasu buforu, wybierając przełącznik czasu buforu. Powoduje to **pojawianie** się  menu przed i po, które służą do wyboru domyślnego czasu przechowywania przed każdą rezerwacją i po każdej rezerwacji, jak pokazano poniżej:

   ![Obraz aplikacji Bookings z włączonym czasem buforu czasu.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Bufor czasu i dostępności

Twoi klienci nie widzą bezpośrednio ustawionego czasu buforu i nie mogą ich zmienić. Ponieważ jednak czas buforu jest używany do obliczenia ogólnego czasu trwania usługi, klienci widzą, że Ty i Twoi odpowiedni personel rezerwujecie zarówno w czasie buforu, jak i w zwykłych terminach. Klienci widzą również dostępność tylko dla Ciebie i Twojego personelu, jeśli jest wystarczająco dużo czasu zarówno dla terminu, jak i jego buforu czasu.

Na przykład termin jednogodzinny z 15-minutowym czasem buforu przed terminem wymaga dostępnego bloku czasowego z co najmniej 1 godziną i 15 minutami. Termin dla tej usługi wypełni zatem 75-minutowy okres w kalendarzu i będzie wymagał 75 minut dostępności na rezerwację bez konfliktu.
