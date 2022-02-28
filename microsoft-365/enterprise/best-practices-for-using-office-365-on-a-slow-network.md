---
title: Najlepsze rozwiązania dotyczące korzystania Office 365 w wolno powolnej sieci
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Ten artykuł zawiera przewodniki po najlepszych rozwiązaniach, które można przyjąć w zakresie korzystania Office 365 w wolno wolno przyjętej sieci.
ms.openlocfilehash: 0b3b46bcc28b8c25f363268adfa720f4d1df47b8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984946"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Najlepsze rozwiązania dotyczące korzystania Office 365 w wolno powolnej sieci

Nie byłoby miło, jeśli połączenie internetowe zawsze działało szybko i nigdy nie zasypuje? Możliwe, że na ten dzień przyjdą. Jednak w międzyczasie istnieją pewne praktyczne rozwiązania, które można wykonać, aby omieć problemy z siecią i wykonać swoją pracę w ciągu dnia. Chociaż Office 365 to usługa oparta na chmurze, udostępnia ona również wiele sposobów pracy z zawartością w trybie offline i płynnego synchronizowania zmian. Poza tym czasem bardziej efektywna jest praca z zawartością w trybie offline tylko dlatego, że aplikacje działają szybciej, a interfejs użytkownika lepiej reaguje. Sęk w tym, że Office 365 zapewnia to, co najlepsze z obu światów. Poniżej opisano, jak to wykorzystać.

> [!TIP]
> Chcesz sprawdzić, jak wolno (lub szybko) działa Twoje połączenie sieciowe? Wypróbuj test [szybkości OOKLA](https://www.speedtest.net/) lub [aplikację Network Speed Test](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70).

## <a name="why-is-my-network-so-slow"></a>Dlaczego moja sieć jest tak wolna?

Mimo że nie masz kontroli nad samą wydajnością sieci, warto zrozumieć, co się dzieje w tle. Internet jest niezwykle złożony, ale istnieje kilka pojęć, które mogą ułatwić znacznie lepsze zrozumienie sytuacji. Zastosowanie się do najlepszych rozwiązań w tym artykule może ułatwić obejście problemów z wydajnością i obniżyć frustrację.

### <a name="major-factors-that-affect-network-performance"></a>Główne czynniki wpływające na wydajność sieci

![Czynniki wydajności sieci.](../media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)

 **Przepustowość i opóźnienie**: Dwie najważniejsze miary wydajności sieci to przepustowość i opóźnienie:

- Przepustowość to wskaźnik przepływności mierzony w bitach na sekundę. Im większa, tym lepiej. Przepustowość można dorównać potokowi wody. Im większa rura, tym więcej wody można przez nie "odłożyć".

- Opóźnienie to czas, który należy mieć, aby zawartość pochodziła z serwera lub usługi na Twoje urządzenie, i jest mierzona w milisekundach. Im szybciej, tym lepiej. Opóźnienie może być spowodowane przez wiele czynników, takich jak niska przepustowość, słabe połączenie lub czas transmisji.

 **Typowe problemy**: Oprócz przepustowości i opóźnień wpływ na wydajność sieci mają inne problemy, które często są nieprzewidywalne. Wydajność sieci może się zmieniać w zależności od czasu dnia lub Twojej fizycznej lokalizacji. Sieć może zostać przesłonić w przypadku pewnych wydarzeń, które zniechęcą do korzystania z Internetu, takich jak klęska żywiołowa lub ważne wydarzenie publiczne. Bezpośredni wpływ na wydajność ma rozmiar i złożoność ładowanej strony oraz liczba i rozmiar przesyłanych plików. Połączenie Wi-Fi może ulec tymczasowemu pogorszeniu, na przykład podczas ankiety na dużym spotkaniu konferencyjnym z tysiącami użytkowników, z prośbą do wszystkich osób o jednocześnie tweety.

 **Zagadnienia związane z** siecią satelitarną: Sieć satelitarna jest przydatna, gdy jest możliwa sieć lądowa, na przykład back country, nadawca czy zdalna sieć naukowa. Te sieci korzystają z zdjęć satelitarnych umieszczonych na orbitzie geosynchronicznej 22 000 km powyżej równika. Jednak transmisja w rzeczywistości podróżuje około 90 000 km, więc w sieci satelitarnej jest mniejsze opóźnienie (500 ms lub więcej) niż sieć lądowa (20 do 50 ms). W najlepszych warunkach możesz nie zauważyć tego opóźnienia, ale prawdopodobnie będziesz pobierać duże pliki, przesyłać strumieniowo klipy wideo i grać w gry. Innym problemem jest zanikanie deszczu, w którym intensywne pogoda, taka jak burze i burze, może tymczasowo przerwać transmisję satelitarną.

## <a name="are-you-sure-its-the-network"></a>Czy na pewno to jest sieć?

Gdy wystąpią problemy z wydajnością, najpierw upewnij się, że główna przyczyna problemu nie jest taka, czy twoje urządzenie. Możesz wykonać dwie czynności, które mogą wprowadzić wiele ulepszeń:

- Upewnij się, że urządzenie działa dobrze i że na komputerze nie ma żadnego złośliwego oprogramowania.

- Jeśli to możliwe, kup więcej pamięci. Dodanie pamięci jest najprostszym i często najbardziej efektywnym sposobem na zwiększenie wydajności urządzenia. Jest to szczególnie przydatne w przypadku pracy z dużymi plikami i klipami wideo.

Aby uzyskać więcej informacji, [zobacz Windows Wydajność](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) i konserwacja [oraz Wskazówki, aby zwiększyć wydajność komputera w Windows 10](https://support.microsoft.com/help/4002019/windows-10-improve-pc-performance).

## <a name="best-practices-for-using-your-browser"></a>Najlepsze rozwiązania dotyczące korzystania z przeglądarki

Twoja przeglądarka jest Twoją bramą do Office 365, więc może mieć wpływ na wydajność, zwłaszcza w przypadku czasu ładowania strony i tego, jak często odbywa się zaokrąglenie do Office 365 usługi.

### <a name="browsers-in-general"></a>Przeglądarki ogólnie

Poniżej podano kilka wskazówek dotyczących przeglądarek ogólnie:

- Wyłącz dodatki przeglądarki, które mogą mieć wpływ na wydajność lub których w naprawdę nie potrzebujesz.

- Zwiększanie rozmiaru pamięci podręcznej tymczasowych plików internetowych.

- Po zalogowaniu się do konta służbowego nie otwieraj okna przeglądarki w ciągu dnia. Możesz otwierać inne karty i okna bez konieczności logowania się ponownie. Jeśli musisz zalogować się na inne konto, użyj przeglądania prywatnego.

- Po pobraniu i otwarciu każdej strony nie otwieraj ich, korzystając z kart. Przechodzenie między kartami i korzystanie ze strony w późniejszym czasie w ciągu dnia jest łatwe. Odśwież stronę tylko wtedy, gdy są potrzebne najnowsze dane na tej stronie.

- Jeśli otwieranie strony trwa zbyt długo, zatrzymaj jej pobieranie (naciśnij klawisz ESC), a następnie odśwież stronę (naciśnij klawisz F5).

- Gdy to możliwe, ogranicz liczbę odełęć do Office 365. Na przykład zamiast przechodzić przez strony list lub bibliotek, użyj wyszukiwania, aby zlokalizować pliki w dużej bibliotece, i filtrowania na liście, aby uzyskać bezpośredni dostęp do wyników. Możesz też utworzyć widoki, które zminimalizują czas ładowania stron. Aby uzyskać więcej informacji, zobacz [Zarządzanie dużymi listami i bibliotekami w Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).

- Jeśli wydajność wideo jest niska, możesz pobrać klip wideo i obejrzeć go na urządzeniu. Być może jest dostępny link pobierania lub możesz kliknąć prawym przyciskiem myszy link do klipu wideo i wybrać polecenie **Zapisz element docelowy jako**.

### <a name="browser-specific"></a>Specyficzne dla przeglądarki

Oto kilka sugestii dotyczących konkretnej przeglądarki:

- **Internet Explorer**: Uaktualnij program Internet Explorer do wersji 11 lub nowszej, aby uzyskać znaczne ulepszenia wydajności w poprzednich wersjach. Aby uzyskać więcej informacji, zobacz [Przewodnik po rozwiązywaniu problemów z programem Internet Explorer](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
- **FireFox**: Aby uzyskać więcej informacji, zobacz [Firefox działa wolno lub przestał działać](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).
- **Safari**: Aby uzyskać więcej informacji, zobacz [Apple — Safari](https://www.apple.com/safari/).
- **Chrome**: Aby uzyskać więcej informacji, zobacz [Pomoc przeglądarki Chrome](https://support.google.com/chrome/?hl=en).

## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Najlepsze rozwiązania dotyczące korzystania z usług Outlook i Outlook Web App

Czytanie, pisanie i porządkowanie wiadomości e-mail to duży fragment dnia każdego z nas. Zarówno Outlook, jak i Outlook Web App (OWA), oferują obsługę trybu offline. Inną przydatną alternatywą jest korzystanie z aplikacji poczty e-mail na smartfonie. Korzystaj z następujących opcji, które najlepiej pasują do Twoich potrzeb:

- Uaktualnij system do najnowszej wersji pakietu Outlook w celu znacznego ulepszenia wydajności w poprzednich wersjach.

- Outlook Web App umożliwia tworzenie w trybie offline wiadomości, kontaktów i zdarzeń kalendarza, które są przekazywane, gdy aplikacja OWA może następnym razem nawiązać połączenie z Office 365. Aby uzyskać więcej informacji na temat konfigurowania i używania aplikacji OWA w trybie offline, zobacz Korzystanie z aplikacji [Outlook Web App w trybie offline](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).

- Outlook umożliwia pracę w trybie buforowanej, w którym łączy się on automatycznie, gdy to możliwe. Możesz pobrać Outlook skrzynkę pocztową lub tylko jej część. Aby uzyskać więcej informacji, zobacz [Włączanie trybu buforowanej Exchange pracy](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) [w trybie offline w Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

- Outlook oferuje również tryb offline. Aby z nich korzystać, należy najpierw skonfigurować tryb buforowany, aby informacje z Twojego konta kopiowane są na komputer. W trybie offline Outlook spróbuje nawiązać połączenie za pomocą ustawień wysyłania i odbierania lub po ręcznym skonfigurowaniu go do pracy w trybie online. Aby uzyskać więcej informacji, zobacz Praca w trybie [offline](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282) w celu uniknięcia opłat za połączenie danych, Zmienianie ustawień wysyłania i odbierania podczas pracy w trybie [offline](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a) i Przełączanie się z pracy [w trybie offline do trybu online](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).

- Jeśli masz smartfon, możesz przy jego użyciu sprawdzić pocztę e-mail i kalendarz za pośrednictwem sieci operatora sieci telefonicznej.

> [!NOTE]
> Oto kilka wskazówek dotyczących tego, kiedy warto używać Outlook lub OWA. Jeśli na Twoim urządzeniu nie występuje problem z przestrzenią dyskową, Outlook ma pełny zestaw funkcji i może być dla Ciebie najlepszym rozwiązaniem. Jeśli na Twoim urządzeniu występuje problem z przestrzenią dyskową, rozważ korzystanie z aplikacji OWA, która zawiera podzbiór funkcji, ale również sprawdza się najlepiej w sytuacji online. Oczywiście możesz korzystać z obu tych funkcji, ponieważ dobrze ze sobą współpracują.

## <a name="best-practices-for-using-onedrive-for-business"></a>Najlepsze rozwiązania dotyczące korzystania z aplikacji OneDrive dla Firm

OneDrive dla Firm projektowane od podstaw pod kątem pracy z plikami w trybie online i offline. Po jej skonfigurowaniu synchronizacja zmian jest automatycznie i niezawodna, gdziekolwiek i kiedykolwiek wprowadzasz zmiany. Jeśli sieć działa wolno, możesz pracować z wersjami offline plików.

Aplikacja OneDrive dla Firm synchronizacji zawiera subskrypcję usługi SharePoint Online Office 365 dla firm lub możesz bezpłatnie pobrać OneDrive dla Firm synchronizacji.[](https://support.microsoft.com/kb/2903984) Ta aplikacja jest także szybsza niż używanie **poleceń otwórz w Eksploratorze** **Upload** plików. Aby uzyskać więcej informacji, zobacz Konfigurowanie na komputerze synchronizowania plików [OneDrive dla Firm w programie Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).

Oto kilka dodatkowych wskazówek dotyczących korzystania z OneDrive dla Firm synchronizacji:

- Jeśli synchronizujesz dużą bibliotekę po raz pierwszy, rozpocznij synchronizację w godzinach poza godzinami pracy, na przykład wieczorem.
- Aby tymczasowo zatrzymać synchronizację aktualizacji, możesz [użyć](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) funkcji Zatrzymaj OneDrive dla Firm z aplikacją. Funkcji tej należy jednak używać przez krótkie okresy, na przykład przez kilka godzin za jednym razem, aby uniknąć kolejkowania dużych liczb aktualizacji oraz aby zminimalizować ryzyko konfliktów scalania w przypadku pracy nad tym samym dokumentem przez kilka osób.

## <a name="best-practices-for-using-onenote"></a>Najlepsze rozwiązania dotyczące korzystania z aplikacji OneNote

Każda SharePoint zespołu ma wbudowany OneNote notes i możesz łatwo utworzyć własny. OneNote to świetny sposób na zbieranie terminowych informacji potrzebnych codziennie do wykonywania zadań. Na przykład wiele zespołów używa OneNote jako punktu zbierania cotygodniowych spotkań, notatek dotyczących projektów, pomysłów, planów i raportów o stanie. Te różne informacje możesz uporządkować, korzystając ze stron, sekcji i kart.

Piękno OneNote tym, że możesz uzyskać dostęp do zawartości praktycznie z dowolnego urządzenia, zarówno komputera stacjonarnego, laptopa, tabletu, czy smartfonu. Nie musisz też martwić się o zapisywanie lub synchronizowanie tych danych, ponieważ OneNote robi to za Ciebie.

Aby uzyskać więcej informacji, zobacz [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Najlepsze rozwiązania dotyczące korzystania z usług Skype dla firm i Lync Online

Poniżej przedstawiono ogólne wskazówki dotyczące korzystania z usług Skype dla firm i Lync Online, gdy sieć jest wolna:

- Korzystaj z wiadomości błyskawicznych zawsze, gdy jest to możliwe, ponieważ dobrze działa w wolno działaj sieci.

- Unikaj dzwonień przez połączenia wirtualnej sieci prywatnej (VPN) lub usługi dostępu zdalnego (RAS).

- Upewnij się, że Twoje urządzenie audio jest zatwierdzone. Aby uzyskać więcej informacji, zobacz [Telefony i urządzenia dla programu Microsoft Lync](/skypeforbusiness/lync-cert/ip-phones).

- Podczas PowerPoint prezentacji w trybie online zmniejsz rozmiar i złożoność slajdów. Aby uzyskać więcej informacji, [Wskazówki na temat poprawy wydajności prezentacji](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).

- Wydajność wideo w znacznym stopniu zależy od wydajności sieci. Unikaj korzystania z wideo, jeśli Twoja sieć jest wolna.

Aby uzyskać więcej informacji, zobacz [Niska jakość dźwięku lub wideo w usłudze Lync Online](https://support.microsoft.com/kb/2386655) lub rozwiązywanie problemów z połączeniem [w Skype dla firm](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).

## <a name="best-practices-for-using-sharepoint-lists"></a>Najlepsze rozwiązania dotyczące korzystania z list SharePoint list

Praca z danymi z list w trybie offline w celu "przesuwania", analizowania lub analizowania danych to świetny sposób na zminimalizowanie wpływu wolno działaj sieci. Większość list można odczytywać i zapisywać za pomocą programu Microsoft Access 2019 i microsoft Access 2016, łącząc się z nimi. Możesz również wyeksportować listę do tabeli Excel, co tworzy jednokierunkowe połączenie danych między tabelą Excel a listą. Dowiedz się, jak [pracować w trybie offline z tabelami połączonymi SharePoint listami.](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e)

Aby uzyskać więcej informacji, zobacz sekcję "Więcej informacji na temat zarządzania dużymi listami" w artykule Zarządzanie dużymi listami i bibliotekami w [Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).

## <a name="best-practices-for-customizing-web-pages"></a>Najlepsze rozwiązania dotyczące dostosowywania stron sieci Web

Podczas dostosowywania strony sieci Web możesz w sposób niezamierzony spowodować niską wydajność tej strony. Może to mieć wpływ na kilka czynników, takich jak złożoność i rozmiar strony, liczba dodanych składników Web Part, liczba wyświetlanych na początku elementów listy lub biblioteki oraz sposób kodów strony.

Aby uzyskać więcej informacji, [zobacz Dostosowywanie SharePoint online](tune-sharepoint-online-performance.md).

## <a name="best-practices-for-using-project-online"></a>Najlepsze rozwiązania dotyczące korzystania z aplikacji Project Online

Poniższe wskazówki mogą pomóc zwiększyć wydajność sieci.

- Project Online i SharePoint online wymagają synchronizacji, która może być czasochłonne. Jeśli rotacja w zespołach projektów jest niewielka, wyłącz synchronizację Project witrynę, aby zwiększyć Project publikowanie i Project szczegółów stron. Ogranicz synchronizację z usługą Active Directory do grup zasobów, które rzeczywiście potrzebują korzystać z systemu, i monitoruj potencjalne problemy z uprawnieniami po synchronizacji dużych grup.

- Jeśli organizacja korzysta z witryn projektów, twórz je na żądanie, a nie automatycznie. Przyspiesza to pierwsze publikowanie i pozwala uniknąć tworzenia niepotrzebnych witryn i zawartości.

- Project stron szczegółów (PDP) mogą wyzwalać ponowne obliczanie całego projektu i rozpoczynać akcje przepływu pracy, z których obie mogą być operacjami o dużej wydajności. Aby nie wyzwalać dwóch procesów aktualizacji jednocześnie na tej samej stronie pdP, unikaj aktualizowania pól kalendarza (data rozpoczęcia, data zakończenia, data stanu i bieżąca data) oraz pól nie zaplanowanych (nazwa projektu, opis i właściciel).

- Zmniejsz liczbę wyświetlanych składniki Web Part niestandardowych na każdej stronie pdP. Utwórz dedykowaną pdP z jedynymi polami, które wymagają aktualizacji, aby poprawić ładowanie i zaoszczędzić czas.

- Gdy używasz danych OData do raportowania, ogranicz ilość danych, o które zapytasz w czasie wykonywania, używając filtrowania po stronie serwera.

Aby uzyskać więcej informacji, [zobacz Dostosowywanie Project Online wydajności](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).

## <a name="whats-the-best-way-to-report-problems"></a>Jaki jest najlepszy sposób zgłaszania problemów?

Firma Microsoft stale ulepsza ogólną wydajność programu Office 365 przez monitorowanie sieci, mierzenie przepustowości i opóźnień, skracanie czasu ładowania stron, zmniejszenie liczby dyskowych operacji We/Wy, przeprojektowanie stron w celu zastosowania strategii minimalnego pobierania, dodanie sprzętu do centrów danych i dodanie większej liczby centrów danych. Aby uzyskać więcej informacji na temat sprawdzania bieżącego stanu i zgłaszania problemów, zobacz [Jak sprawdzić Office 365 kondycję usługi](view-service-health.md).

## <a name="see-also"></a>Zobacz też

[Network planning and performance tuning for Office 365](network-planning-and-performance.md)

[Office 365 zasad łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Zarządzanie Office 365 punktami końcowymi](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 punkty końcowe — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
