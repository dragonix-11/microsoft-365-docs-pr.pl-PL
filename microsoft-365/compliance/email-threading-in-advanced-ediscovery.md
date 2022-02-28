---
title: Wątkowanie wiadomości e-mail w Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Podczas przeprowadzania analizy Advanced eDiscovery e-mail wątki wiadomości e-mail analizuje konwersację e-mail i dzieli każdą wiadomość na różne kategorie.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 788858d6acaccbe07f3190b5adaaa05fe95c33a5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983659"
---
# <a name="email-threading-in-advanced-ediscovery"></a>Wątkowanie wiadomości e-mail w Advanced eDiscovery

Rozważ konwersację e-mail, która już trwa. W większości przypadków ostatnia wiadomość w wątku wiadomości e-mail będzie zawierać zawartość wszystkich poprzednich wiadomości. Dlatego przejrzenie ostatniej wiadomości zapewni pełny kontekst konwersacji, która się wydarzyła w wątku. W wątkach wiadomości e-mail takie wiadomości są identyfikowane, dzięki czemu recenzentzy mogą przeglądać ułamek zebranych dokumentów bez utraty kontekstu.

## <a name="what-does-email-threading-do"></a>Do czego działa wątkowanie wiadomości e-mail?

Wątki wiadomości e-mail analizuje każdy wątek wiadomości e-mail i dekonstruuje go do poszczególnych wiadomości. Każdy wątek wiadomości e-mail to łańcuch pojedynczych wiadomości. Advanced eDiscovery analizuje wszystkie błędy poczty e-mail w zestawie recenzji w celu ustalenia, czy wiadomość ma unikatową zawartość lub czy łańcuch (wiadomości nadrzędne) jest zawarty w ostatecznej wiadomości w wątku wiadomości e-mail. Wiadomości e-mail są podzielone na cztery wartości włącznie:

- **Włącznie**: Wiadomość *e-mail włącznie* to końcowa wiadomość e-mail w wątku wiadomości e-mail, która zawiera całą poprzednią zawartość tego wątku.

- **Minus włącznie**: Jeśli z określoną wiadomością w wątku wiadomości e-mail jest skojarzony co najmniej jeden załącznik, jest on oznaczony jako *Minus* włącznie. Recenzent może użyć wartości minus włącznie do określenia, które konkretne wiadomości e-mail w wątku mają skojarzone załączniki. 

- **Kopia włącznie**: Wiadomość e-mail jest uznawana za kopię *włącznie* , jeśli jest to dokładna kopia wiadomości minus inclusive lub inclusive. 

- **Brak**. Wartość *Brak* wskazuje, że treść wiadomości jest w całości zawarta w co najmniej jednej innej wiadomości e-mail oznaczonej jako Inclusive lub Inclusive minus.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Czym różnią się od konwersacji w Outlook?

W skrócie wygląda to podobnie do grup konwersacji w programie Outlook. Istnieje jednak pewne ważne rozróżnienie. Rozważ konwersację e-mail, która została widnieć na dwóch konwersacjach; Na przykład ktoś odpowiedział na wiadomość e-mail, która nie jest najnowszą wiadomością w konwersacji, więc dwie ostatnie wiadomości e-mail w konwersacji mają unikatową zawartość.

Outlook wiadomości e-mail będą nadal grupować w jedną konwersację; przeczytanie tylko ostatniej wiadomości e-mail oznaczałoby brak kontekstu drugiej do ostatniej wiadomości e-mail, która również zawiera unikatową zawartość. Ponieważ wątki wiadomości e-mail analizuje każdą wiadomość e-mail na poszczególne składniki i porównuje je, wątki wiadomości e-mail oznaczałyby obie ostatnie wiadomości e-mail jako takie włącznie, dzięki czemu nie przegapisz żadnego kontekstu, dopóki przeczytasz wszystkie wiadomości e-mail oznaczone jako uwzględniające różne elementy.
