---
title: Planowanie dynamicznych spotkań cyklicznych
ms.author: sarichardson
author: sallyri
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.reviewer: strettin
ms.localizationpriority: medium
description: Użytkownicy mogą dowiedzieć się więcej o planowaniu dynamicznych spotkań cyklicznych.
ms.openlocfilehash: d4f99b336088e7c565c741a8f631e4fefbada68f
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989717"
---
# <a name="scheduling-dynamic-recurring-meetings"></a>Planowanie dynamicznych spotkań cyklicznych

Dynamiczne spotkania harmonogramu działają w sposób zatłoczony harmonogramem użytkownika. Spotkania cykliczne zarządzane przez program Scheduler zachowują się inaczej niż tradycyjne spotkania cykliczne w programie Outlook. Aby zachować otwarty kalendarz w przyszłości i zminimalizować konflikty z uczestnikami, program Scheduler zaplanuje jedno wystąpienie spotkania cyklicznego na raz.

Na przykład poproszę o Cortana "Zaplanuj 30 minut czasu pracy nad pracą każdego dnia" spowoduje utworzenie początkowo jednego 30-minutowego terminu na następną dostępną datę w kalendarzu.  Po zakończeniu tego terminu program Scheduler przystąpi do rezerwy kolejnego wystąpienia w dniu następującym po tym dniu. Jeśli oryginalny slot czasu nie jest obecnie dostępny, harmonogram dostosuje czas na podstawie Twojej dostępności.

Taką samą heuristic można stosować do spotkań z zaproszonymi. Możesz dołączyć uczestników do żądania i poprosić uczestników o Cortana "Planowanie spotkania co dwa tygodnie". Pierwsze i każde kolejne spotkanie zostanie dynamicznie zaplanowane na podstawie bieżącej dostępności wszystkich uczestników w organizacji. Jeśli Ty lub uczestnik jesteście niedostępni lub poza biurem w następnym dniu, czas spotkania zostanie automatycznie dostosowany do tego, kiedy wszyscy są dostępni, a odpowiedni termin zostanie zachowany dla kolejnych wystąpień spotkania na podstawie nowo zaplanowanej daty.

## <a name="booking-with-attendees-outside-your-organization"></a>Rezerwacja z uczestnikami spoza organizacji

Podczas planowania spotkania z uczestnikami spoza organizacji wirtualny asystent wyśle uczestnikom zewnętrznym opcje czasu pierwszego spotkania. Wszystkie przyszłe spotkania są planowane automatycznie na podstawie dostępności organizatora i uczestników wewnętrznych.

Harmonogram obsługuje interwały dzienne, tygodniowe i miesięczne.

## <a name="examples-of-how-to-request-recurring-meetings"></a>Przykłady żądania spotkań cyklicznych

Oto kilka przykładów sposobu, w jaki możesz wysyłać wiadomości e-mail Cortana spotkania cykliczne:

- "Cortana, zaplanuj spotkanie co 2 tygodnie".
- "Zarezerwuj 30 minut miesięcznie na recenzję".
- "Cortana znajdziemy 30 minut na spotkanie we wtorek".
- "Cortana, zaplanuj 30 minut w każdy piątek o 15:30"

## <a name="changing-recurring-frequency"></a>Zmienianie częstotliwości cyklicznej

Częstotliwość dowolnego spotkania cyklicznego lub spotkania nie cyklicznego zarządzanego przez program Scheduler można zmienić. Odpowiedz na Cortana z ostatniej wiadomości e-mail z potwierdzeniem w wątku spotkania i powiedz Cortana:

- "Zmień to na raz w każdym miesiącu".
- "Cortana, zamieć to spotkanie dwatygodniowo".

## <a name="cancelling-recurring-meetings"></a>Anulowanie spotkań cyklicznych

Możesz odpowiedzieć na Cortana i poprosić o "anulowanie tego spotkania" w celu anulowania zaplanowanego wystąpienia. Jednak harmonogram nadal będzie planować przyszłe spotkania z taką samą częstotliwością. Ewentualnie możesz po prostu poprosić program Scheduler o ponowne zaplanowanie następnego wystąpienia na żądaną datę lub godzinę. Jeśli chcesz anulować całą serię cykliczną, odpowiedz "anuluj tę serię" i żadne przyszłe wystąpienia nie będą planowane.

## <a name="recurring-meeting-limitations"></a>Ograniczenia dotyczące spotkań cyklicznych

Pamiętaj, że z pewnymi ograniczeniami technicznymi dla typów cyklów, które może zrozumieć i obsługiwać program Scheduler:

- Wiele wystąpień w tym samym interwale nie jest obsługiwanych (na przykład "dwa razy w tygodniu").
- Daty zakończenia cyklu nie są obsługiwane (na przykład: "codziennie do 20 grudnia"). Ponieważ każde spotkanie jest zaplanowane po ukończeniu poprzedniego spotkania, wystarczy odpowiedzieć na najnowszą wiadomość z Cortana "anulować tę serię spotkań".
- Harmonogram obecnie nie obsługuje częstotliwości cyklu przekraczanych 90 dni.
