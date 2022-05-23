---
title: Ustawianie czasu buforu Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Ustaw czas buforowania przed lub po terminie w Microsoft Bookings, aby dać czas na czyszczenie lub resetowanie sprzętu.
ms.openlocfilehash: 49e58d53cec466c824a40281e3199f1544e74744
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637588"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Ustawianie czasu buforu w Microsoft Bookings

Niektóre terminy mogą wymagać czasu przed lub po spotkaniu z klientem w celu skonfigurowania, oczyszczenia lub zresetowania pokoju i sprzętu. Lub jeśli jesteś w drodze między terminami klienta, może być potrzebny czas, aby upewnić się, że Ty i Twój zespół możecie podróżować między spotkaniami bez czekania klienta.

Możesz ustawić czas buforowania przed rozpoczęciem terminów, po zakończeniu terminów lub obu tych terminów, aby dać pracownikom dodatkowy czas potrzebny na przygotowanie się do następnego terminu.

## <a name="set-buffer-time-defaults"></a>Ustawianie wartości domyślnych czasu buforu

Wartości domyślne czasu buforu są ustawiane na stronie **Szczegóły usługi** w Bookings. Podobnie jak w przypadku wszystkich ustawień domyślnych usługi ustawionych na tej stronie, te wartości domyślne mogą być edytowane przez Ciebie dla określonej rezerwacji w celu spełnienia określonych potrzeb klientów.

Ustawienie czasu buforu można znaleźć na stronie **Szczegóły usługi** . Aby można było ustawić dla danej usługi, należy włączyć ustawienie czasu buforu, wybierając przełącznik czasu buforu. Powoduje to wyświetlenie list rozwijanych **Przed** i **Po** , które są używane do wybierania domyślnej ilości czasu do przechowywania przed i po każdej rezerwacji, jak pokazano tutaj:

   ![Obraz przedstawiający Bookings z włączonym czasem buforowania.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Czas buforowania i dostępność

Twoi klienci nie widzą bezpośrednio i nie mogą zmienić ustawionych czasów buforowania. Jednak ponieważ czas buforowania jest używany do obliczania ogólnego czasu trwania usługi, klienci będą widzieć Ciebie i Odpowiednich pracowników jako zarezerwowanych zarówno w buforze, jak i w regularnych terminach. Klienci widzą również dostępność dla Ciebie i Twoich pracowników tylko wtedy, gdy jest wystarczająco dużo czasu zarówno na spotkanie, jak i czas buforowania.

Na przykład jednogodzinne spotkanie z 15-minutowym czasem buforowania przed terminem wymaga dostępnego bloku czasu wynoszącego co najmniej 1 godzinę i 15 minut. Termin dla tej usługi wypełni zatem 75-minutowy blok czasu w kalendarzu i wymaga 75 minut dostępności, aby zarezerwować bez konfliktu.
