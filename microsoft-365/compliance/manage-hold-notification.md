---
title: Zarządzanie powiadomieniami o wstrzymaniu
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
description: Przepływ pracy komunikacji w programie Advanced eDiscovery do śledzenia stanu powiadomień o wstrzymaniu ze względu na prawo, a w razie potrzeby aktualizacji i ponownego ich wyślij.
ms.openlocfilehash: 276771b2a22f6db3e3d0620ee429a16626107bcc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987773"
---
# <a name="manage-hold-notifications"></a>Zarządzanie powiadomieniami o wstrzymaniu

Po zainicjowaniu przepływu pracy z powiadomieniem o wstrzymaniu ze względu na prawo możesz go użyć w programie Advanced eDiscovery do śledzenia stanu komunikacji. Karta Komunikacja zawiera listę wszystkich powiadomień w ramach Advanced eDiscovery przypadku. Można wyświetlić szczegółowe informacje, takie jak liczba przypisanych lub zaakceptowanych informacji.

## <a name="monitor-acknowledgments"></a>Monitoruj potwierdzanie

Po wybraniu komunikacji **na karcie Komunikacja** można wyświetlić listę elementów przechowywania, które potwierdziły powiadomienie o wstrzymaniu. 

1. W centrum zgodności przejdź do **tematu Zbierania elektronicznych materiałów dowodowych > Advanced eDiscovery**.

2. Zaznacz sprawę, a następnie kliknij **kartę** Komunikacja.

3. Wybierz komunikację, aby wyświetlić stronę **wysuwu komunikacji Pochłoń** .

Na wysuwanych stronie komunikacji zostanie wyświetlona lista elementów przechoczy skojarzonych z wybraną komunikacją. Na tej stronie są również wyświetlane szczegółowe informacje o tym, ile potwierdzeń odebrano i ile jest zaległych. Na stronie pokazano także, które programy przechowywania wysłały potwierdzenie, że otrzymały powiadomienie o wstrzymaniu.

## <a name="re-send-a-hold-notice"></a>Ponowne wysyłanie powiadomienia o wstrzymaniu

Czasami zdarza się, że schowek przechowywają wiadomości e-mail w swoich dniach pracy. W przypadku długiego sporu sądowego osoba, która od dawna jest w związku ze sporem sądowym, może skontaktować się z Tobą lub innymi osobami i poprosić o ponowne wysłanie powiadomienia. Gdy zarządzasz przepływem pracy komunikacji na potrzeby otrzymywania informacji prawnych, może być konieczne ponowne wysłanie powiadomienia w celu ponownego ustawienia go na "początku skrzynki pocztowej użytkownika".

Aby ponownie wysłać powiadomienie o wstrzymaniu do opiekuna:

1. W Advanced eDiscovery wybierz sprawę, a następnie kliknij **kartę Komunikacja**.

2. Wybierz komunikację, aby wyświetlić stronę **wysuwu komunikacji Pochłoń** .

3. Kliknij **przycisk Więcej > powiadomienie o ponownej wysłaniu.**

4. Na stronie **wysuwana informacja** o zleceniu ponownego wysłania wybierz opiekunów, dla których chcesz ponownie wysłać powiadomienie, i wpisz opcjonalną przyczynę.

5. Kliknij **pozycję Wyślij ponownie,** aby wysłać powiadomienie do wybranych osób- opiekunów.

Jeśli wołodniacy nie potwierdzili powiadomienia o wstrzymaniu, zostanie uruchomiony ponownie przepływ pracy przypomnienie i eskalacja. Jeśli informacje o wstrzymaniu zostały zaakceptowane przez opiekuna, otrzyma on kopię oryginalnego powiadomienia o wstrzymaniu.

> [!NOTE]
> Powiadomienie o wstrzymaniu ze względu na prawo można wysłać ponownie tylko do osób, które zostały przypisane do komunikacji. 

## <a name="update-preservation-requirements"></a>Aktualizowanie wymagań dotyczących zachowywania
  
W związku z postępem tej sytuacji może być wymagane zachowanie dodatkowych lub mniejszej niezbędnej do tego danych, niż zostało to wcześniej instrukcje. W przypadku zbierania elektronicznych materiałów dowodowych należy ponownie wydaje powiadomienie o wstrzymaniu ze zaktualizowaną zawartością.

Aby zaktualizować zawartość powiadomienia o początkowym wstrzymaniu:

1. W Advanced eDiscovery wybierz sprawę, a następnie kliknij **kartę Komunikacja**.

2. Zaznacz powiadomienie o wstrzymaniu, które chcesz zaktualizować, a następnie kliknij pozycję **Edytuj na** stronie **wysuwana** komunikacja Wi-Wi-Pan.

3. W **kreatorze Edytowanie komunikacji** kliknij pozycję **Definiuj** zawartość portalu w lewym okienku kreatora i zaktualizuj zawartość powiadomienia.

4. Kliknij **Zapisz**.

Powiadomienie o ponownym wydawaniu zostanie wysłane do wszystkich osób przechowywania przypisanych do powiadomienia o wstrzymaniu ich ze względu na przepisy prawne. Ponadto, jeśli jest włączone powiadomienie Przypomnienie lub Eskalacja, przepływy pracy dla tych typów zawiadomień zostaną uruchomione ponownie.

## <a name="update-legal-hold-notifications-and-settings"></a>Aktualizowanie powiadomień o wstrzymaniu ze strony prawnej i ustawień

Po zaktualizowaniu zawartości lub ustawień powiadomienia O wydaniu, wydaniu, ponownej aktualizacji, przypomnieniu lub eskalacji te zmiany będą stosowane do wszystkich przyszłych komunikatów generowanych przez przepływ pracy.

## <a name="more-information"></a>Więcej informacji

- [Dodawanie osób do sprawy](add-custodians-to-case.md)

- [Tworzenie informacji prawnych o wstrzymaniu ich od zesłania](create-hold-notification.md)

- [Potwierdzanie powiadomienia o wstrzymaniu](acknowledge-hold-notification.md)
