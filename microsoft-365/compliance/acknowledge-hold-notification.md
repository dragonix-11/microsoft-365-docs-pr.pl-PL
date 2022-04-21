---
title: Potwierdź powiadomienie o archiwum
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak używać funkcji zbierania elektronicznych materiałów dowodowych (Premium) do wysyłania powiadomień o wstrzymaniu ze względów prawnych za pośrednictwem poczty e-mail oraz monitorowania stanu obowiązków.
ms.openlocfilehash: db13ed4a148238dbb677ece55999fd3fb907a1a1
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999591"
---
# <a name="acknowledge-a-hold-notification"></a>Potwierdź powiadomienie o archiwum

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W odpowiedzi na wniosek regulacyjny lub dochodzenie może być wymagane poinformowanie opiekunów o obowiązku zachowania elektronicznie przechowywanych informacji (ESI) oraz wszelkich materiałów, które mogą być istotne dla aktywnej lub rychłej sprawy prawnej. Po wysłaniu zespoły prawne muszą wiedzieć, że każdy opiekun otrzymał, przeczytał, zrozumiał i zgodził się postępować zgodnie z podanymi instrukcjami.

Aby skrócić czas, koszty i nakład pracy związane z obserwowaniem opiekunów, funkcja zbierania elektronicznych materiałów dowodowych (Premium) umożliwia wysyłanie i śledzenie powiadomień o blokadzie prawnej za pośrednictwem poczty e-mail. Oprócz powiadomień e-mail, każdy opiekun będzie miał dostęp do zindywidualizowanego Portalu zgodności, dzięki czemu opiekunowie będą informowani o zmianach ich statusu obowiązku.

## <a name="email-notifications"></a>Powiadomienia e-mail

Po wydaniu powiadomienia o blokadzie prawnej każdy opiekun otrzyma unikatową i spersonalizowaną wiadomość e-mail zawierającą zdefiniowane powiadomienie o wstrzymaniu ze względów prawnych i dodane instrukcje. 

> [!TIP]
> Zobacz, jak za pomocą wbudowanego  [Edytora komunikacji](using-communications-editor.md) zezwolić opiekunom na potwierdzenie powiadomienia lub dostęp do portalu zgodności bezpośrednio z poczty e-mail.

Na podstawie konfiguracji powiadomienia o blokadzie prawnej opiekunowie mogą otrzymać następujące powiadomienia: 

- **Powiadomienie o wystawienie:** Pierwsze powiadomienie wysłane do opiekuna. To powiadomienie będzie zawierać instrukcje wystawiania i powiadomienie o wstrzymaniu dołączone na końcu wiadomości.

- **Powiadomienie o przypomnieniach:** Jeśli ta opcja jest włączona, powiadomienie o przypomnieniu zostanie wysłane do opiekunów na podstawie określonej częstotliwości i interwału. Przypomnienia będą nadal wysyłane do czasu potwierdzenia powiadomienia przez opiekuna lub do momentu wyczerpania liczby przypomnień.

- **Powiadomienie o eskalacji:** Jeśli zostanie włączone, powiadomienie o eskalacji zostanie wysłane do opiekuna i jego kierownika po wyczerpaniu powiadomień o przypomnieniu. System automatycznie wysyła powiadomienia o eskalacji do momentu ukończenia określonej liczby eskalacji lub do momentu potwierdzenia powiadomienia o blokadzie przez opiekuna.

- **Powiadomienie o ponownym zakończeniu:** W trakcie dochodzenia, jeśli treść powiadomienia o wstrzymaniu zostanie zaktualizowana, zaktualizowane powiadomienie zostanie automatycznie wysłane do opiekuna.

- **Powiadomienie o wersji:** Gdy opiekun zostanie zwolniony ze sprawy, otrzyma powiadomienie o zwolnieniu. 

## <a name="compliance-portal"></a>Portal zgodności

Oprócz powiadomień e-mail każdy opiekun będzie miał dostęp do unikatowego portalu zgodności. Za pośrednictwem portalu każdy opiekun może wyświetlać i potwierdzać aktywne powiadomienia o blokadzie oraz uzyskiwać do nich dostęp.

![Portal zgodności dla opiekuna.](../media/CustodianPortal.jpg)
