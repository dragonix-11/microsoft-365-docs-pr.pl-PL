---
title: Najlepsze rozwiązania dotyczące używania Office 365 w powolnej sieci
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/29/2016
audience: End User
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: W tym artykule przedstawiono najlepsze rozwiązania, które można zastosować do używania Office 365 w powolnej sieci.
ms.openlocfilehash: 5ed3a9dfc665d5067fb3f310fc74aa4b100190f2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091638"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Najlepsze rozwiązania dotyczące używania Office 365 w powolnej sieci

Czy nie byłoby miło, gdyby połączenie internetowe było zawsze szybkie i nigdy nie w dół? Być może ten dzień nadejdzie. Ale w międzyczasie, istnieją praktyczne rzeczy, które można zrobić, aby obejść balky sieci i nadal dostać swoją codzienną pracę. Mimo że Office 365 jest usługą opartą na chmurze, oferuje również wiele sposobów pracy z zawartością w trybie offline i płynnego synchronizowania zmian. Poza tym czasami bardziej wydajna jest praca z zawartością w trybie offline tylko dlatego, że aplikacje działają szybciej, a interfejs użytkownika jest bardziej responsywny. Chodzi o to: Office 365 daje to, co najlepsze z obu światów. Oto jak z tego skorzystać.

> [!TIP]
> Chcesz zobaczyć, jak powolne (lub szybkie) jest połączenie sieciowe? Wypróbuj [test szybkości OOKLA](https://www.speedtest.net/) lub [aplikację Network Speed Test](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70).

## <a name="why-is-my-network-so-slow"></a>Dlaczego moja sieć jest tak powolna?

Chociaż nie masz kontroli nad samą wydajnością sieci, pomaga to zrozumieć, co dzieje się w tle. Internet jest niezwykle złożony, ale istnieje kilka pojęć, które mogą znacznie lepiej zrozumieć sytuację. Zgodnie z najlepszymi rozwiązaniami w tym artykule może pomóc obejść problemy z wydajnością i zmniejszyć frustrację.

### <a name="major-factors-that-affect-network-performance"></a>Główne czynniki wpływające na wydajność sieci

![Czynniki wydajności sieci.](../media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)

 **Przepustowość i opóźnienie**: Dwie najważniejsze miary wydajności sieci to przepustowość i opóźnienie:

- Przepustowość to szybkość przepływności mierzona w bitach na sekundę. Większe jest lepsze. Przepustowość jest jak rura wodna. Tym większa rura, tym więcej wody można "przeprowadzić".

- Opóźnienie to czas potrzebny na pobranie zawartości z serwera lub usługi do urządzenia i zmierzenie jej w milisekundach. Szybciej jest lepiej. Opóźnienie może być spowodowane przez wiele czynników, w tym niską przepustowość, rozrzedzone połączenie lub czas transmisji.

 **Typowe problemy**: Oprócz przepustowości i opóźnienia inne problemy mają wpływ na wydajność sieci i często są nieprzewidywalne. Wydajność sieci może się zmieniać w zależności od godziny dnia lub lokalizacji fizycznej. Sieć może zostać zatkana, gdy wystąpią pewne zdarzenia, które mogą spowodować wzrost użycia Internetu, na przykład klęskę żywiołową lub poważne zdarzenie publiczne. Rozmiar i złożoność załadowanej strony oraz liczba i rozmiar przesyłanych plików mają bezpośredni wpływ na wydajność. Połączenie sieci Wi-Fi może tymczasowo ulec pogorszeniu: na przykład sondujesz duże spotkanie konferencyjne z tysiącami osób, prosząc wszystkich o tweety w tym samym czasie.

 **Zagadnienia dotyczące sieci satelitarnej**: Sieć satelitarna jest przydatna, gdy sieć naziemna nie jest możliwa, na przykład kraj powrotu, statek wycieczkowy lub zdalny obszar naukowy. Sieci te polegają na satelitach umieszczonych na orbicie geosynchronicznej 22 000 mil nad równikiem. Jednak transmisja faktycznie przemieszcza się około 90 000 mil, więc sieć satelitarna ma wolniejsze opóźnienie (500 ms lub więcej) niż sieć naziemna (20 do 50 ms). W najlepszych warunkach możesz nie zauważyć tego opóźnienia, ale w przypadku pobierania dużych plików, przesyłania strumieniowego wideo i grania w gry prawdopodobnie tak będzie. Innym problemem jest "zanikanie deszczu", w którym ciężka pogoda, taka jak burze z piorunami i zamieciami, może tymczasowo przerwać transmisję satelitarną.

## <a name="are-you-sure-its-the-network"></a>Czy na pewno jest to sieć?

Zawsze, gdy wystąpią problemy z wydajnością, najpierw upewnij się, że urządzenie nie jest główną przyczyną problemu. Istnieją dwie rzeczy, które można zrobić, które mogą wprowadzić dużą poprawę:

- Upewnij się, że urządzenie działa prawidłowo i na komputerze nie ma złośliwego oprogramowania.

- Jeśli to możliwe, kup więcej pamięci. Dodawanie pamięci jest najprostszym i często najskuteczniejszym sposobem poprawy wydajności na urządzeniu. Jest to szczególnie przydatne podczas pracy z dużymi plikami i filmami wideo.

Aby uzyskać więcej informacji, zobacz [Windows Performance and maintenance and](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) [Wskazówki to improve PC performance in Windows 10 (Windows Performance and maintenance and Wskazówki to improve PC performance in Windows 10 (Wydajność i konserwacja oraz Wskazówki w celu zwiększenia wydajności komputera w Windows 10](https://support.microsoft.com/help/4002019/windows-10-improve-pc-performance)).

## <a name="best-practices-for-using-your-browser"></a>Najlepsze rozwiązania dotyczące korzystania z przeglądarki

Twoja przeglądarka jest bramą do Office 365, więc może mieć wpływ na wydajność, zwłaszcza z czasem potrzebnym do załadowania strony i tym, jak często odbywa się podróż w obie strony do usługi Office 365.

### <a name="browsers-in-general"></a>Ogólnie przeglądarki

Poniżej przedstawiono niektóre sugestie dotyczące przeglądarek w ogóle:

- Wyłącz dodatki przeglądarki, które mogą mieć wpływ na wydajność lub których tak naprawdę nie potrzebujesz.

- Zwiększ rozmiar pamięci podręcznej tymczasowych plików internetowych.

- Po zalogowaniu się do konta służbowego pozostaw okno przeglądarki otwarte przez cały dzień. Możesz otworzyć inne karty i okna bez ponownego logowania. Jeśli musisz zalogować się do innego konta, użyj przeglądania prywatnego.

- Po pobraniu i otwarciu każdej strony pozostaw je otwarte przy użyciu kart. Łatwo jest nawigować między kartami i korzystać ze strony później w ciągu dnia. Odśwież stronę tylko wtedy, gdy potrzebujesz najnowszych danych na tej stronie.

- Jeśli otwarcie strony trwa zbyt długo, zatrzymaj pobieranie strony (naciśnij klawisz ESC), a następnie odśwież stronę (naciśnij klawisz F5).

- Jeśli to możliwe, zmniejsz liczbę rund do Office 365. Na przykład zamiast stronicować listy lub biblioteki, użyj funkcji wyszukiwania, aby zlokalizować pliki w dużej bibliotece, i przefiltruj je na liście, aby uzyskać dostęp bezpośrednio do żądanych wyników. Możesz też utworzyć widoki, które minimalizują czas ładowania strony. Aby uzyskać więcej informacji, zobacz [Zarządzanie dużymi listami i bibliotekami w Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).

- Jeśli wydajność wideo jest niska, możesz pobrać film wideo i obejrzeć go na urządzeniu. Link do pobierania może być dostępny lub możesz kliknąć prawym przyciskiem myszy link wideo i wybrać pozycję **Zapisz obiekt docelowy jako**.

### <a name="browser-specific"></a>Specyficzne dla przeglądarki

Oto kilka sugestii dotyczących konkretnej przeglądarki:

- **Internet Explorer**: uaktualnij program Internet Explorer w wersji 11 lub nowszej, aby uzyskać znaczne ulepszenia wydajności w stosunku do poprzednich wersji. Aby uzyskać więcej informacji, zobacz [Przewodnik rozwiązywania problemów dla programu Internet Explorer](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
- **FireFox**: Aby uzyskać więcej informacji, zobacz [Firefox działa wolno lub przestaje działać](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).
- **Safari**: Aby uzyskać więcej informacji, zobacz [Apple — Safari](https://www.apple.com/safari/).
- **Chrome**: Aby uzyskać więcej informacji, zobacz [Pomoc dla przeglądarki Chrome](https://support.google.com/chrome/?hl=en).

## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Najlepsze rozwiązania dotyczące używania Outlook i Outlook Web App

Czytanie, pisanie i organizowanie poczty e-mail to duża część dnia każdego. Zarówno Outlook, jak i Outlook Web App (OWA) oferują pomoc techniczną w trybie offline. Korzystanie z aplikacji poczty e-mail na smartfonie to kolejna przydatna alternatywa. Użyj następujących opcji, które najlepiej odpowiadają Twoim potrzebom:

- Uaktualnij do najnowszej wersji Outlook, aby uzyskać znaczne ulepszenia wydajności w stosunku do poprzednich wersji.

- Outlook Web App umożliwia tworzenie komunikatów, kontaktów i zdarzeń kalendarza w trybie offline, które są przekazywane, gdy usługa OWA będzie mogła nawiązać połączenie z Office 365. Aby uzyskać więcej informacji na temat konfigurowania i używania usługi OWA w trybie offline, zobacz [Using Outlook Web App offline (Używanie Outlook Web App offline](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)).

- Outlook umożliwia pracę w trybie pamięci podręcznej, w którym automatycznie nawiązuje połączenie, gdy tylko jest to możliwe. Możesz mieć Outlook pobrać całą skrzynkę pocztową lub tylko jej część. Aby uzyskać więcej informacji, zobacz [Włączanie trybu Exchange buforowanego](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) i [praca w trybie offline w Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

- Outlook oferuje również tryb offline. Aby tego użyć, należy najpierw skonfigurować tryb buforowany, aby informacje z twojego konta były kopiowane do komputera. W trybie offline Outlook spróbuje nawiązać połączenie przy użyciu ustawień wysyłania i odbierania lub po ręcznym ustawieniu go do pracy w trybie online. Aby uzyskać więcej informacji, zobacz [Praca w trybie offline, aby uniknąć opłat za połączenie danych](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [Zmienianie ustawień wysyłania i odbierania podczas pracy w trybie offline](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a) oraz [Przełączanie z pracy w trybie offline do trybu online](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).

- Jeśli masz smartfon, możesz go użyć do klasyfikacji poczty e-mail i kalendarza za pośrednictwem sieci operatora telefonicznego.

> [!NOTE]
> Poniżej przedstawiono wskazówki dotyczące korzystania z Outlook lub OWA. Jeśli miejsce na dysku nie stanowi problemu na urządzeniu, Outlook ma pełny zestaw funkcji i może działać najlepiej. Jeśli na urządzeniu występuje problem z miejscem na dysku, rozważ użycie funkcji OWA, która ma podzestaw funkcji, ale działa również najlepiej w sytuacji online. Oczywiście, można użyć albo dlatego, że dobrze ze sobą współpracują.

## <a name="best-practices-for-using-onedrive-for-business"></a>Najlepsze rozwiązania dotyczące używania OneDrive dla Firm

OneDrive dla Firm została zaprojektowana od podstaw do pracy z plikami w trybie online i offline. Po jego skonfigurowaniu synchronizacja zmian odbywa się automatycznie i niezawodnie wszędzie i wszędzie tam, gdzie je wprowadzasz. Jeśli sieć działa wolno, możesz pracować z wersją plików w trybie offline.

Aplikacja do synchronizacji OneDrive dla Firm jest dostarczana z subskrypcją usługi SharePoint Online i Office 365 business lub możesz [bezpłatnie pobrać](https://support.microsoft.com/kb/2903984) aplikację do synchronizacji OneDrive dla Firm. Ta aplikacja jest również szybsza niż przy użyciu poleceń **Otwórz w Eksploratorze** lub **Upload**. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do synchronizowania plików OneDrive dla Firm w Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).

Oto kilka dodatkowych wskazówek dotyczących korzystania z aplikacji synchronizacji OneDrive dla Firm:

- Jeśli synchronizujesz dużą bibliotekę po raz pierwszy, rozpocznij synchronizację poza godzinami pracy, na przykład z dnia na dzień.
- Aby tymczasowo zatrzymać synchronizację aktualizacji, możesz użyć funkcji [Zatrzymaj synchronizowanie biblioteki z funkcją aplikacji OneDrive dla Firm](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330). Ta funkcja jest jednak używana przez krótki czas, na przykład przez kilka godzin, aby uniknąć kolejkowania dużej liczby aktualizacji i zminimalizować ryzyko konfliktów scalania, jeśli kilka osób pracuje nad tym samym dokumentem.

## <a name="best-practices-for-using-onenote"></a>Najlepsze rozwiązania dotyczące używania OneNote

Każda witryna zespołu SharePoint ma wbudowany notes OneNote i możesz łatwo utworzyć własny. OneNote to doskonały sposób na zbieranie na czas informacji potrzebnych codziennie do wykonywania zadań. Na przykład wiele zespołów używa OneNote jako punktu zbierania cotygodniowych spotkań, notatek projektu, pomysłów, planów i raportów o stanie. Możesz starannie zorganizować te różne informacje przy użyciu stron, sekcji i kart.

Piękno OneNote jest to, że można uzyskać dostęp do zawartości z praktycznie każdego urządzenia, czy pulpitu, laptopa, tabletu lub smartfona. I nie musisz się martwić o zapisywanie lub synchronizowanie, ponieważ OneNote robi to za Ciebie.

Aby uzyskać więcej informacji, zobacz [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Najlepsze rozwiązania dotyczące korzystania z usług Skype dla firm i Lync Online

Poniżej przedstawiono ogólne wytyczne dotyczące korzystania z usługi Skype dla firm lub usługi Lync Online, gdy sieć działa wolno:

- Używaj wiadomości błyskawicznych, gdy tylko możesz, ponieważ działa dobrze w powolnej sieci.

- Unikaj nawiązywania połączeń telefonicznych za pośrednictwem wirtualnej sieci prywatnej (VPN) lub połączeń usługi dostępu zdalnego (RAS).

- Upewnij się, że urządzenie audio zostało zatwierdzone. Aby uzyskać więcej informacji, zobacz [Phone and Devices Qualified for Microsoft Lync (Telefony i urządzenia kwalifikowane do programu Microsoft Lync](/skypeforbusiness/lync-cert/ip-phones)).

- W przypadku korzystania z PowerPoint w prezentacji online zmniejsz rozmiar i złożoność slajdów. Aby uzyskać więcej informacji, zobacz [Wskazówki w celu zwiększenia wydajności prezentacji](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).

- Wydajność wideo jest bardzo zależna od wydajności sieci. Unikaj korzystania z wideo, jeśli sieć działa wolno.

Aby uzyskać więcej informacji, zobacz [Niska jakość dźwięku lub wideo w usłudze Lync Online](https://support.microsoft.com/kb/2386655) lub jak [rozwiązywać problemy z połączeniem w Skype dla firm](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).

## <a name="best-practices-for-using-sharepoint-lists"></a>Najlepsze rozwiązania dotyczące korzystania z list SharePoint

Praca z danymi listy w trybie offline w celu "szorowania", analizowania lub raportowania danych to doskonały sposób na zminimalizowanie wpływu powolnej sieci. Większość list z programu Microsoft Access 2019 i microsoft Access 2016 można odczytywać i pisać, łącząc się z nimi. Możesz również wyeksportować listę do tabeli Excel, która tworzy jednokierunkowe połączenie danych między tabelą Excel a listą. Dowiedz się, jak [pracować w trybie offline z tabelami połączonymi z listami SharePoint](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e).

Aby uzyskać więcej informacji, zobacz sekcję "Więcej informacji na temat zarządzania dużymi [listami" w temacie Zarządzanie dużymi listami i bibliotekami w Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).

## <a name="best-practices-for-customizing-web-pages"></a>Najlepsze rozwiązania dotyczące dostosowywania stron internetowych

Podczas dostosowywania strony internetowej może to spowodować nieumyślne pogorszenie wydajności strony. Może to mieć wpływ na wiele czynników, takich jak złożoność i rozmiar strony, liczba dodanych składników Web Part, liczba początkowo wyświetlanych elementów listy lub biblioteki oraz sposób kodowania strony.

Aby uzyskać więcej informacji, zobacz [Tune SharePoint Online performance (Dostosowywanie wydajności usługi SharePoint Online](tune-sharepoint-online-performance.md)).

## <a name="best-practices-for-using-project-online"></a>Najlepsze rozwiązania dotyczące używania Project Online

Poniższe wytyczne mogą pomóc zwiększyć wydajność sieci.

- Project Online i SharePoint Online wymagają synchronizacji, która może być czasochłonna. Jeśli twoje zespoły projektowe mają niskie obroty, wyłącz Project Site Sync, aby zwiększyć wydajność Project Publikowanie i Project stron szczegółów. Ogranicz synchronizację usługi Active Directory do grup zasobów, które faktycznie muszą korzystać z systemu, i monitoruj wszelkie potencjalne problemy z uprawnieniami po synchronizacji dużych grup.

- Jeśli organizacja korzysta z witryn projektów, utwórz je na żądanie, a nie automatycznie. Przyspiesza to pierwsze środowisko publikowania i pozwala uniknąć tworzenia niepotrzebnych witryn i zawartości.

- Project Detail Pages (PDP) może wyzwolić ponowne obliczenie całego projektu i rozpocząć akcje przepływu pracy, z których oba mogą być operacjami wymagającymi dużej wydajności. Aby uniknąć wyzwalania dwóch procesów aktualizacji w tym samym czasie w tym samym PDP, należy unikać aktualizowania pól kalendarza (data rozpoczęcia, data zakończenia, data stanu i bieżąca data) oraz nie zaplanowanych pól (nazwa projektu, opis i właściciel).

- Zmniejsz liczbę pól składniki Web Part i niestandardowych wyświetlanych na każdym PDP. Utwórz dedykowany PDP z jedynymi polami, które wymagają aktualizacji w celu zwiększenia obciążenia i zaoszczędzenia czasu.

- W przypadku korzystania z danych OData do raportowania ogranicz ilość danych wysyłanych w czasie wykonywania przy użyciu filtrowania po stronie serwera.

Aby uzyskać więcej informacji, zobacz [Tune Project Online performance (Dostosowywanie wydajności Project Online](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)).

## <a name="whats-the-best-way-to-report-problems"></a>Jaki jest najlepszy sposób zgłaszania problemów?

Firma Microsoft stale poprawia ogólną wydajność Office 365, monitorując sieć, mierząc przepustowość i opóźnienia, skracając czas ładowania strony, zmniejszając liczbę operacji we/wy dysku, przeprojektowując strony w celu użycia strategii minimalnego pobierania, dodając sprzęt do centrów danych i dodając więcej centrów danych. Aby uzyskać więcej informacji na temat sprawdzania bieżącego stanu i zgłaszania problemów, zobacz [Jak sprawdzić kondycję usługi Office 365](view-service-health.md).

## <a name="see-also"></a>Zobacz też

[Network planning and performance tuning for Office 365](network-planning-and-performance.md)

[zasady łączności sieciowej Office 365](microsoft-365-network-connectivity-principles.md)

[Zarządzanie punktami końcowymi usługi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 punktów końcowych — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
