---
title: Zarządzaj powiadomieniami o archiwum
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
ms.assetid: ''
description: Użyj przepływu pracy komunikacji w usłudze eDiscovery (Premium), aby śledzić stan powiadomień o blokadzie prawnej oraz w razie potrzeby aktualizować je i ponownie je przesyłać.
ms.openlocfilehash: 83e5331aaea59893f06cfa0629d627e500cfe1b1
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996179"
---
# <a name="manage-hold-notifications"></a>Zarządzaj powiadomieniami o archiwum

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po zainicjowaniu przepływu pracy powiadomień o blokadzie prawnej możesz użyć przepływu pracy komunikacji w usłudze Microsoft Purview eDiscovery (Premium) do śledzenia stanu komunikacji. Karta Komunikacja zawiera listę wszystkich powiadomień w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Możesz zobaczyć szczegóły, takie jak liczba opiekunów, którzy zostali przypisani lub potwierdzili powiadomienie.

## <a name="monitor-acknowledgments"></a>Monitorowanie potwierdzenia

Po wybraniu komunikacji na **karcie Komunikacja** możesz wyświetlić listę opiekunów, którzy potwierdzili wstrzymanie. 

1. W centrum zgodności przejdź do obszaru **eDiscovery > eDiscovery (Premium)**.

2. Wybierz przypadek, a następnie kliknij kartę **Komunikacja** .

3. Wybierz komunikację, aby wyświetlić stronę wysuwaną **komunikację opiekuna** .

Lista opiekunów skojarzonych z wybraną komunikacją jest wyświetlana na stronie wysuwanej komunikacji. Na tej stronie są również wyświetlane szczegółowe informacje oraz informacje o liczbie odebranych potwierdzeniach i liczbie zaległych. Na stronie pokazano również, którzy opiekunowie wysłali potwierdzenie, że otrzymali powiadomienie o blokadzie.

## <a name="re-send-a-hold-notice"></a>Ponowne wysyłanie powiadomienia o blokadzie

Czasami opiekunowie tracą śledzenie wiadomości e-mail w codziennej pracy. W przypadku długotrwałej sprawy sądowej opiekun może skontaktować się z Tobą lub innymi osobami i poprosić o ponowne wysłanie powiadomienia. Podczas zarządzania przepływem pracy komunikacji dla prawnych powiadomień o wstrzymaniu może być konieczne ponowne wysłanie powiadomienia w celu przywrócenia go do "górnej części skrzynki pocztowej użytkownika".

Aby ponownie wysłać powiadomienie o blokadzie do opiekuna:

1. W obszarze eDiscovery (Premium) wybierz przypadek, a następnie kliknij kartę **Komunikacja**.

2. Wybierz komunikację, aby wyświetlić stronę wysuwaną **komunikację opiekuna** .

3. Kliknij pozycję **Więcej > Wyślij powiadomienie o ponownym wysłaniu blokady**.

4. Na stronie **wysuwanej Powiadomienie o ponownym wysłaniu powiadomienia o wstrzymaniu** wybierz opiekunów, których chcesz ponownie wysłać, i wpisz opcjonalną przyczynę.

5. Kliknij przycisk **Wyślij ponownie** , aby wysłać powiadomienie do wybranych opiekunów.

Jeśli opiekun nie potwierdził powiadomienia o blokadzie, przepływ pracy przypomnienia i eskalacji zostanie uruchomiony ponownie. Jeśli opiekun potwierdzi wstrzymanie, opiekun otrzyma kopię pierwotnego zawiadomienia o wstrzymaniu.

> [!NOTE]
> Powiadomienie o wstrzymaniu ze względów prawnych można wysyłać tylko do opiekunów, którzy są przypisani do komunikacji. 

## <a name="update-preservation-requirements"></a>Aktualizowanie wymagań dotyczących zachowania
  
W miarę postępów sprawy opiekunowie mogą być zobowiązani do zachowania dodatkowych lub mniejszych danych, niż zostało to wcześniej poinstruowane. W kategoriach zbierania elektronicznych materiałów dowodowych należy ponownie wydać powiadomienie o blokadzie ze zaktualizowaną zawartością.

Aby zaktualizować zawartość początkowego powiadomienia o wstrzymaniu:

1. W obszarze eDiscovery (Premium) wybierz przypadek, a następnie kliknij kartę **Komunikacja**.

2. Wybierz powiadomienie o blokadzie, które chcesz zaktualizować, a następnie kliknij pozycję **Edytuj** na stronie **wysuwanej komunikacji kustosz** .

3. W kreatorze **edytowania komunikacji** kliknij pozycję **Zdefiniuj zawartość portalu** w lewym okienku kreatora i zaktualizuj zawartość powiadomienia.

4. Kliknij **Zapisz**.

Powiadomienie o ponownym wydaniu zostanie wysłane do wszystkich opiekunów przypisanych do powiadomienia o blokadzie prawnej. Ponadto, jeśli powiadomienie o przypomnieniu lub eskalacji jest włączone, przepływy pracy dla tych typów powiadomień zostaną ponownie uruchomione.

## <a name="update-legal-hold-notifications-and-settings"></a>Aktualizowanie legalnych powiadomień i ustawień blokady

Po zaktualizowaniu zawartości lub ustawień powiadomienia o wystawianiu, wydaniu, ponownym wydaniu, przypomnieniu lub eskalacji te zmiany będą miały zastosowanie do wszystkich przyszłych komunikatów generowanych przez przepływ pracy.

## <a name="more-information"></a>Więcej informacji

- [Dodaj opiekunów do sprawy](add-custodians-to-case.md)

- [Tworzenie powiadomienia o blokadzie prawnej](create-hold-notification.md)

- [Potwierdź powiadomienie o archiwum](acknowledge-hold-notification.md)
