---
title: Różnice między szacowanym a rzeczywistymi wynikami wyszukiwania zbierania elektronicznych materiałów dowodowych
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Dowiedz się, dlaczego szacowane i rzeczywiste wyniki wyszukiwania mogą się różnić w wyszukiwaniu przy użyciu narzędzi zbierania elektronicznych materiałów dowodowych w Office 365.
ms.openlocfilehash: 16b63b96421cfbf3f9d67e1373061b49ff5db225
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032113"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Różnice między szacowanym a rzeczywistymi wynikami wyszukiwania zbierania elektronicznych materiałów dowodowych

Ten temat dotyczy wyszukiwań, które można uruchamiać przy użyciu jednego z następujących narzędzi zbierania Microsoft 365 eDiscovery: 

- Przeszukiwanie zawartości
- Core eDiscovery

Po uruchomieniu wyszukiwania zbierania elektronicznych materiałów dowodowych narzędzie, z których korzystasz, zwróci szacowaną liczbę elementów (i ich całkowity rozmiar) spełniające kryteria wyszukiwania. Na przykład po uruchomieniu wyszukiwania w Centrum zgodności platformy Microsoft 365 zostaną wyświetlone szacowane wyniki wyszukiwania na wysuwanych stronie dla wybranego wyszukiwania.
  
![Szacowany wynik wyświetlany na wysuwanych stronie wyszukiwania.](../media/EstimatedSearchResults1.png)
  
Jest to ten sam szacowany całkowity rozmiar i liczba elementów, które są wyświetlane w narzędziu do eksportowania zbierania elektronicznych materiałów dowodowych podczas eksportowania wyników na komputer lokalny i w raporcie Podsumowanie eksportu, który został pobrany z wynikami wyszukiwania.
  
**Szacowane wyniki w narzędziu eksportowania zbierania elektronicznych materiałów dowodowych**

![Szacowane wyniki w narzędziu eksportowania zbierania elektronicznych materiałów dowodowych.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Szacowane wyniki w raporcie Podsumowanie eksportu**

![Szacowane wyniki wyszukiwania są uwzględniane w raporcie Podsumowanie eksportu.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Jak jednak widać na poprzednim zrzucie ekranu raportu Podsumowanie eksportu, rozmiar i liczba pobieranych rzeczywistych wyników wyszukiwania różnią się od rozmiaru i liczby szacowanych wyników wyszukiwania.
  
![Różnica między szacowanym a pobranym wynikami wyszukiwania.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Oto kilka powodów tych różnic:
  
- **Sposób szacowania wyników**. Szacowana wartość wyników wyszukiwania to tylko szacowana (a nie rzeczywista liczba) elementów spełniających kryteria wyszukiwania. Aby skompilować szacowaną Exchange elementów, w bazie danych usługi Exchange jest wymagana lista identyfikatorów wiadomości spełniających kryteria wyszukiwania za pomocą narzędzia zbierania elektronicznych materiałów dowodowych. Jednak podczas eksportowania wyników wyszukiwania jest ponownie uruchomić wyszukiwanie i z bazy danych są pobierane rzeczywiste Exchange danych. Dlatego te różnice mogą wynikać z tego, jak jest określana szacowana liczba elementów i rzeczywista liczba elementów.

- **Zmiany, które mają miejsce między szacowaniem i eksportowaniem wyników wyszukiwania**. Podczas eksportowania wyników wyszukiwania jest ponownie uruchamiany w celu zebrania najnowszych elementów w indeksie wyszukiwania, które spełniają kryteria wyszukiwania. Istnieje możliwość, że utworzono, wysłano lub odebrano dodatkowe elementy spełniające kryteria wyszukiwania w okresie między zebraniami szacowanych wyników wyszukiwania a eksportowaniem wyników wyszukiwania. Możliwe jest również, że elementy, które były w indeksie wyszukiwania podczas szacowania wyników wyszukiwania, nie są już dostępne, ponieważ przed wyeksportowaniu wyników wyszukiwania zostały one wyczyszżone z lokalizacji zawartości. Jednym ze sposobów ograniczenia tego problemu jest określenie zakresu dat dla wyszukiwania zbierania elektronicznych materiałów dowodowych. Innym sposobem jest umieszczenie w miejscu zawartości lokalizacji zawartości, aby elementy zostały zachowane i nie można ich przeczyścić. 

   Chociaż zdarza się to rzadko, nawet w przypadku zastosowania hold'a, od czasu do czasu może zostać usunięta konserwacja wbudowanych elementów kalendarza (których nie można edytować, ale które są zawarte w wielu wynikach wyszukiwania). Tego rodzaju okresowe usuwanie elementów kalendarza spowoduje mniej eksportowanych elementów.

- **Elementy nieindeksowane**. Elementy nieindeksowane do wyszukiwania mogą powodować różnice między szacowanym a rzeczywistymi wynikami wyszukiwania. Podczas eksportowania wyników wyszukiwania możesz uwzględnić elementy nieindeksowane. Jeśli podczas eksportowania wyników wyszukiwania uwzględnisz elementy nieindeksowane, wyeksportowane elementy mogą zawierać więcej elementów. Spowoduje to różnicę między szacowanym a wyeksportowanych wynikami wyszukiwania.

    Podczas korzystania z narzędzia Przeszukiwanie zawartości możesz uwzględnić elementy nieindeksowane podczas eksportowania wyników wyszukiwania. Liczba nieindeksowanych elementów zwróconych przez wyszukiwanie jest wymieniona na wysuwanych stronie wraz z innymi szacowanmi wynikami wyszukiwania. Wszystkie elementy nieindeksowane będą również uwzględniane w łącznym rozmiarze szacowanych wyników wyszukiwania. Podczas eksportowania wyników wyszukiwania możesz uwzględnić elementy nieindeksowane lub ich nie uwzględniać. Sposób skonfigurowania tych opcji może spowodować różnice między szacowanym a rzeczywistymi wynikami wyszukiwania, które są pobierane.

- **Eksportowanie wyników wyszukiwania zawartości, które obejmuje wszystkie lokalizacje zawartości**. Jeśli wyszukiwanie, z których są eksportowane wyniki, było wyszukiwaniem wszystkich lokalizacji zawartości w organizacji, zostaną wyeksportowane tylko elementy nieindeksowane z lokalizacji zawartości, które zawierają elementy zgodne z kryteriami wyszukiwania. Innymi słowy, jeśli w skrzynce pocztowej lub witrynie nie zostaną znalezione żadne wyniki wyszukiwania, nie zostaną wyeksportowane żadne elementy nieindeksowane w tej skrzynce pocztowej lub witrynie. Jednak elementy nieindeksowane ze wszystkich lokalizacji zawartości (nawet tych, które nie zawierają elementów, które pasują do zapytania wyszukiwania) będą uwzględniane w szacowanych wynikach wyszukiwania.

    Jeśli eksportowane wyniki wyszukiwania są eksportowane z określonych lokalizacji zawartości, elementy nieindeksowane (niewykluczone przez kryteria wyszukiwania) ze wszystkich lokalizacji zawartości określonych w wyszukiwaniu są eksportowane. W tym przypadku szacowana liczba elementów nieindeksowanych i eksportowane elementy nieindeksowane powinny być takie same.

    Przyczyną niewyeksywności elementów nieindeksowanych z każdej lokalizacji w organizacji jest zwiększenie prawdopodobieństwa wystąpienia błędów eksportu i zwiększenie czasu trwającego do wyeksportowania i pobrania wyników wyszukiwania.

- **Elementy nieindeksowane SharePoint i OneDrive nie są uwzględniane w oszacowaniu wyszukiwania**. Elementy nieindeksowane SharePoint witryn i OneDrive dla Firm nie są uwzględniane w szacowanych wynikach wyszukiwania. Wynika to z tego SharePoint indeks nie zawiera danych dla elementów nieindeksowanych. W oszacowaniu wyszukiwania uwzględniane są tylko elementy nieindeksowane ze skrzynek pocztowych. Jeśli jednak podczas eksportowania wyników wyszukiwania zostaną uwzględnione elementy nieindeksowane, zostaną uwzględnione elementy nieindeksowane w programach SharePoint i OneDrive, co spowoduje zwiększenie liczby faktycznie eksportowanych elementów. Spowoduje to różnice między szacowanym wynikiem (które nie zawierają elementów nieindeksowanych w witrynach SharePoint i OneDrive) a rzeczywistymi pobranymi elementami. Reguła eksportowania elementów nieindeksowanych tylko z lokalizacji zawartości, które zawierają elementy zgodne z kryteriami wyszukiwania, nadal ma zastosowanie w tej sytuacji.

- **Wersje dokumentów w SharePoint i OneDrive**. Podczas wyszukiwania SharePoint witryn i kont OneDrive nie uwzględnia się wielu wersji dokumentu w liczniku szacowanych wyników wyszukiwania. Możesz jednak uwzględnić wszystkie wersje dokumentów podczas eksportowania wyników wyszukiwania. Jeśli podczas eksportowania wyników wyszukiwania uwzględnisz wersje dokumentów, rzeczywista liczba (i całkowity rozmiar) eksportowanych elementów zostanie zwiększona.

- **SharePoint folderów**. Jeśli nazwa folderów w programie SharePoint pasuje do zapytania wyszukiwania, szacowana wartość wyszukiwania będzie uwzględniać ich liczbę (ale nie elementy w tych folderach). Podczas eksportowania wyników wyszukiwania elementy w folderze są eksportowane, ale rzeczywiste foldery nie są eksportowane. W wyniku tego liczba eksportowanych elementów będzie większa niż liczba szacowanych wyników wyszukiwania. Jeśli folder jest pusty, liczba wyeksportowanych wyników wyszukiwania zostanie zmniejszona o jeden element, ponieważ rzeczywisty folder nie jest eksportowany.

- **SharePoint listy.** Jeśli nazwa listy SharePoint odpowiada zapytaniu wyszukiwania, szacowany czas wyszukiwania będzie uwzględniać liczbę wszystkich elementów na liście. Podczas eksportowania wyników wyszukiwania lista (i elementy listy) jest eksportowana jako pojedynczy plik CSV. Zmniejszy to rzeczywistą liczbę faktycznie wyeksportowanych elementów. Jeśli lista zawiera załączniki, załączniki zostaną wyeksportowane jako osobne dokumenty, co spowoduje również zwiększenie liczby eksportowanych elementów.

- **Nieprzetworzone formaty plików a formaty wyeksportowanych plików**. W Exchange elementów szacowany rozmiar wyników wyszukiwania jest obliczany przy użyciu nieprzetworzonych Exchange wiadomości. Jednak wiadomości e-mail są eksportowane w pliku PST lub jako pojedyncze wiadomości (które są sformatowane jako pliki EML). Obie te opcje eksportowania używają innego formatu pliku niż nieprzetworzone wiadomości Exchange, co powoduje, że całkowity rozmiar eksportowanego pliku jest inny niż szacowany rozmiar pliku.

- **W trakcie eksportowania Exchange duplikowanie elementów**. W Exchange elementów duplikowanie zmniejsza liczbę eksportowanych elementów. Możesz usunąć zduplikowane wyniki wyszukiwania podczas ich eksportowania. W Exchange wiadomości oznacza to, że eksportowane jest tylko pojedyncze wystąpienie wiadomości, mimo że ta wiadomość może znaleźć się w wielu skrzynkach pocztowych. Szacowane wyniki wyszukiwania obejmują każde wystąpienie wiadomości. Jeśli wybierzesz opcję de duplikowania podczas eksportowania wyników wyszukiwania, eksportowana liczba eksportowanych elementów może być znacznie mniejsza niż szacowana liczba elementów.

Raport wyników wyszukiwania (Results.csv pliku) zawiera wpis dla każdej zduplikowanej wiadomości i identyfikuje źródłową skrzynkę pocztową, w której znajduje się zduplikowana wiadomość. Dzięki temu można zidentyfikować wszystkie skrzynki pocztowe zawierające zduplikowaną wiadomość.

> [!NOTE]
> Jeśli podczas eksportowania wyników wyszukiwania nie zaznaczysz opcji Uwzględnij elementy, które są zaszyfrowane lub mają nierozpoznany **format** lub po prostu pobierzesz raporty, raporty o błędach indeksu zostaną pobrane, ale nie będą zawierać żadnych pozycji. Nie oznacza to, że nie wystąpiły żadne błędy indeksowania. Oznacza to jedynie, że elementy nieindeksowane nie zostały uwzględnione w eksporcie.
