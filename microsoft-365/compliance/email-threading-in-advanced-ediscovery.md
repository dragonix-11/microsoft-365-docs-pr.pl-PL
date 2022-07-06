---
title: Wątkowość wiadomości e-mail w usłudze eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Podczas przeprowadzania analizy zbierania elektronicznych materiałów dowodowych (Premium) funkcja wątkowości wiadomości e-mail analizuje konwersację wiadomości e-mail i dzieli każdą wiadomość na różne kategorie.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: a17f746cb0c88fb68e4654d0dd7de528135d62ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629712"
---
# <a name="email-threading-in-ediscovery-premium"></a>Wątkowość wiadomości e-mail w usłudze eDiscovery (Premium)

Rozważmy konwersację e-mail, która trwa od jakiegoś czasu. W większości przypadków ostatnia wiadomość w wątku wiadomości e-mail będzie zawierać zawartość wszystkich poprzednich wiadomości. W związku z tym przejrzenie ostatniej wiadomości zapewni pełny kontekst konwersacji, która miała miejsce w wątku. Wątkowość wiadomości e-mail identyfikuje takie wiadomości, dzięki czemu recenzenci mogą przeglądać ułamek zebranych dokumentów bez utraty kontekstu.

## <a name="what-does-email-threading-do"></a>Co robi wątkowanie wiadomości e-mail?

Wątek wiadomości e-mail analizuje każdy wątek wiadomości e-mail i dekonstruuje go do poszczególnych wiadomości. Każdy wątek wiadomości e-mail jest łańcuchem poszczególnych wiadomości. Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) analizuje wszystkie wiadomości e-mail w zestawie przeglądów, aby ustalić, czy wiadomość e-mail ma unikatową zawartość, czy też łańcuch (wiadomości nadrzędne) jest całkowicie zawarty w końcowej wiadomości w wątku wiadomości e-mail. Wiadomości e-mail są podzielone na cztery wartości inkluzywne:

- **Inkluzywna**: *inkluzywna* wiadomość e-mail to ostatnia wiadomość e-mail w wątku wiadomości e-mail zawierająca całą poprzednią zawartość tego wątku wiadomości e-mail.

- **Minus inkluzywny**: wiadomość e-mail jest oznaczona jako *Inkluzywna minus* , jeśli istnieje co najmniej jeden załącznik skojarzony z określoną wiadomością w wątku wiadomości e-mail. Recenzent może użyć wartości Inclusive minus, aby określić, która konkretna wiadomość e-mail w wątku ma skojarzone załączniki. 

- **Kopiowanie inkluzywne**: wiadomość e-mail jest uznawana za *kopię inkluzywną* , jeśli jest dokładną kopią wiadomości inkluzywnej lub inkluzywnej minus. 

- **Brak**: wartość *None* wskazuje, że zawartość wiadomości jest w całości zawarta w co najmniej jednej innej wiadomości e-mail oznaczonej jako Inkluzywna lub Inkluzywna minus.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Czym różni się od konwersacji w programie Outlook?

W skrócie brzmi to podobnie do grupowania konwersacji w programie Outlook. Istnieją jednak pewne istotne różnice. Rozważmy konwersację w wiadomości e-mail, która została rozwidlenie w dwóch konwersacjach; Na przykład ktoś odpowiedział na wiadomość e-mail, która nie jest najnowsza w konwersacji, więc dwa ostatnie wiadomości e-mail w konwersacji mają unikatową zawartość.

Program Outlook nadal grupuje wiadomości e-mail w jedną konwersację. Odczytywanie tylko ostatniej wiadomości e-mail oznaczałoby brak kontekstu od drugiej do ostatniej wiadomości e-mail, która również zawiera unikatową zawartość. Ponieważ funkcja wątkowości wiadomości e-mail analizuje każdą wiadomość e-mail do poszczególnych składników i porównuje je, wątki wiadomości e-mail oznaczałyby oba ostatnie wiadomości e-mail jako inkluzywne, zapewniając, że nie przegapisz żadnego kontekstu, o ile przeczytasz wszystkie wiadomości e-mail oznaczone jako inkluzywne.
