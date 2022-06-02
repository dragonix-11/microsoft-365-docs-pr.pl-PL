---
title: Wyszukiwanie wiadomości e-mail i korygowanie zagrożeń przy użyciu Eksploratora zagrożeń w Microsoft 365 Defender
description: Kroki ręcznego korygowania w Eksploratorze zagrożeń w Microsoft 365 Defender, w tym jak uzyskać najlepszą wydajność i scenariusze, które wymagają korygowania.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 6bce250add79d4119f82730c05f3042f3e3dbafe
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842489"
---
# <a name="steps-to-use-manual-email-remediation-in-threat-explorer"></a>Kroki korzystania z ręcznego korygowania poczty e-mail w Eksploratorze zagrożeń

Korygowanie poczty e-mail to już istniejąca funkcja, która ułatwia administratorom działanie na wiadomościach e-mail, które są zagrożeniami.

## <a name="what-youll-need"></a>Co będzie potrzebne
- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2
- Wystarczające uprawnienia (pamiętaj o przyznaniu roli [Wyszukiwanie i przeczyszczanie](https://sip.security.microsoft.com/securitypermissions) konta)

## <a name="create-and-track-the-remediation"></a>Tworzenie i śledzenie korygowania

1. **Wybierz zagrożenie do skorygowania** w [Eksploratorze zagrożeń](https://security.microsoft.com/threatexplorer) i wybierz przycisk **Akcje komunikatów** , który zaoferuje opcje, takie jak *usuwanie nietrwałe* lub *usuwanie twarde*.
1. Okienko boczne zostanie otwarte i poprosi o podanie szczegółów, takich jak nazwa korygowania, ważności i opisu. Po przejrzeniu informacji naciśnij przycisk **Prześlij**.
1. Gdy tylko administrator zatwierdzi tę akcję, zobaczy [tutaj](https://security.microsoft.com/action-center/history) identyfikator zatwierdzenia i link do centrum akcji Microsoft 365 Defender. Na tej stronie **można śledzić akcje**.

    1. **alert akcji Administracja** — alert systemowy jest wyświetlany w kolejce alertów o nazwie "Akcja administracyjna przesłana przez administratora". Oznacza to, że administrator podjął akcję korygowania jednostki. Zawiera szczegółowe informacje, takie jak nazwa administratora, który podjął akcję, oraz link do badania i czas. Dzięki temu administratorzy są świadomi każdej ważnej akcji, takiej jak korygowanie, wykonywanych względem jednostek.
    1. **Administracja badanie akcji** — ponieważ analiza jednostek została już przeprowadzona przez administratora i to właśnie doprowadziło do podjęcia akcji, system nie przeprowadza żadnej dodatkowej analizy. Zawiera szczegółowe informacje, takie jak alert pokrewny, jednostka wybrana do korygowania, podjęta akcja, stan korygowania, liczba jednostek i osoba zatwierdzająca akcję. Dzięki temu administratorzy mogą *śledzić* badanie i akcje wykonywane ręcznie — badanie działania administratora.
1. **Dzienniki akcji w ujednoliconym centrum akcji** — dzienniki historii i akcji dla akcji poczty e-mail, takich jak usuwanie nietrwałe i przenoszenie do folderu usuniętych elementów, są *dostępne w scentralizowanym widoku* na **karcie Historia** ujednoliconego **centrum** >  akcji. 
1. **Filtry w ujednoliconym centrum akcji** — istnieje wiele filtrów, takich jak nazwa korygowania, identyfikator zatwierdzenia, identyfikator badania, stan, źródło akcji i typ akcji. Są one przydatne do znajdowania i śledzenia akcji poczty e-mail w ujednoliconym centrum akcji.

> [!IMPORTANT]
> Wydajność W celu zwiększenia wydajności korygowanie powinno odbywać się w partiach o rozmiarze *co najmniej 50 000*. Zawęź wynik wyszukiwania przy użyciu *najnowszej lokalizacji dostarczania* i wyzwól korygowanie wiadomości e-mail, jeśli wiadomość e-mail znajduje się na przykład w folderze korygowania, takim jak Skrzynka odbiorcza, Śmieci, Usunięte.

## <a name="scenarios-that-call-for-email-remediation"></a>Scenariusze wywołujące korygowanie poczty e-mail

Oto scenariusze korygowania poczty e-mail:

1. W ramach badania usługa SecOps identyfikuje zagrożenie w skrzynce pocztowej użytkownika końcowego i chce usunąć problemy z wiadomościami e-mail.
1. Jeśli sugerowane akcje poczty e-mail w programie Automated Investigation and Response (AIR) są zatwierdzane przez usługę SecOps, akcja korygowania jest wyzwalana automatycznie dla danego klastra poczty e-mail lub poczty e-mail.

Dwa scenariusze ręcznego korygowania poczty e-mail:

1. Główny scenariusz:
    1. Ręczne akcje wykonywane w wiadomościach e-mail (na przykład przy użyciu Eksploratora zagrożeń lub zaawansowanego wyszukiwania zagrożeń) są widoczne tylko w starszej wersji centrum Ochrona usługi Office 365 w usłudze Defender Action Center (Poczta e-mail i współpraca > Przeglądanie centrum akcji > w centrum akcji — Microsoft 365 zabezpieczenia).  
1. Dwuetapowy scenariusz zatwierdzania:
    1. Akcje ręczne oczekujące na zatwierdzenie przy użyciu dwuetapowego procesu zatwierdzania (1. Wiadomość e-mail została dodana do korygowania przez jednego analityka, 2. Wiadomość e-mail została przejrzana i zatwierdzona przez innego analityka).

Biorąc pod uwagę typowe scenariusze, korygowanie poczty e-mail może być wyzwalane na trzy różne sposoby.

1. **Korygowanie oparte na zapytaniach**: zaznaczając wszystkie wyniki wyszukiwania za pomocą zapytania (maksymalnie można przesłać 200 000 wiadomości e-mail).
1. **Ręczne korygowanie**: wybieranie wiadomości e-mail pojedynczo przez kliknięcie pola wyboru (100 wiadomości e-mail można przesłać jednocześnie).
1. **Korygowanie oparte na zapytaniach z wykluczeniami**: wybieranie wszystkich wiadomości e-mail, a następnie ręczne usuwanie kilku komunikatów (zapytanie może zawierać maksymalnie 1000 wiadomości e-mail, a maksymalna liczba wykluczeń wynosi 100).

## <a name="next-steps"></a>Następne kroki
1. Przejdź do [portalu Microsoft 365 Defender](https://security.microsoft.com) i zaloguj się.
1. W okienku nawigacji wybierz pozycję **Centrum akcji**.
1. Przejdź do karty **Historia** , kliknij dowolną listę oczekujących zatwierdzeń. Spowoduje to otwarcie okienka bocznego.  
1. Śledź stan akcji w ujednoliconym centrum akcji.

## <a name="more-information"></a>Więcej informacji

[Dowiedz się więcej o korygowaniu poczty e-mail](../../office-365-security/air-review-approve-pending-completed-actions.md)
