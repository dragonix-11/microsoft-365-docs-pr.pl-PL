---
title: Plan rozwiązywania problemów z wydajnością Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
ms.collection:
- M365-security-compliance
- Ent_O365
description: Ten artykuł może ułatwić rozwiązywanie Office 365 problemów z wydajnością, a nawet rozwiązywanie niektórych z najbardziej typowych problemów.
ms.openlocfilehash: 23779158c250a94873f44139faa783e0079ab642
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988398"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Plan rozwiązywania problemów z wydajnością Office 365

Chcesz poznać czynności, które należy wykonać, aby zidentyfikować i rozwiązać problemy z opóźnieniami, zawieszania się i wolnym działaniem między usługami SharePoint Online, OneDrive dla Firm, Exchange Online lub Skype dla firm Online a Twoim komputerem klienckim? Zanim skontaktujemy się z pomocą techniczną, w tym artykule Office 365 rozwiązywanie niektórych z najczęściej występujących problemów.

Ten artykuł to w rzeczywistości przykładowy plan działań, za pomocą którym możesz chwycić cenne dane dotyczące swojego problemu z wydajnością podczas jego wykonywania. Niektóre najważniejsze problemy są również uwzględnione w tym artykule.

Jeśli nie wiesz, jaka jest wydajność sieci i chcesz ująć w długoterminowy plan monitorowania wydajności między Twoimi komputerami klienckimi i programem Office 365 [Office 365](performance-tuning-using-baselines-and-history.md), zobacz Dostosowywanie wydajności i rozwiązywanie problemów — dla administratorów i administratorów Pro.

## <a name="sample-performance-troubleshooting-action-plan"></a>Przykładowy plan działań rozwiązywania problemów z wydajnością

Ten plan akcji składa się z dwóch części: fazę przygotowawcą i fazę rejestrowania. Jeśli masz problem z wydajnością już teraz i musisz gromadzenia danych, możesz od razu zacząć korzystać z tego planu.

### <a name="prepare-the-client-computer"></a>Przygotowywanie klienta

- Znajdź klienta, na który można odtworzyć problem z wydajnością. Ten komputer będzie używany w trakcie rozwiązywania problemów.
- Zapisz czynności, które powodują wystąpienia problemu z wydajnością, aby przygotować się do testowania.
- Zainstaluj narzędzia do zbierania i rejestrowania informacji:
  - Zainstaluj [narzędzie Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865) (lub użyj równoważnego narzędzia do śledzenia sieci).
  - Zainstaluj bezpłatną wersję Basic Edition programu [HTTPWatch](https://www.httpwatch.com/download/) (lub użyj równoważnego narzędzia do śledzenia sieci).
  - Skorzystaj z rejestratora ekranu lub uruchom Rejestratora problemów (PSR.exe) dostarczanych z systemem Windows Vista lub nowszym, aby zarejestrować czynności, które należy wykonać podczas testowania.

### <a name="log-the-performance-issue"></a>Rejestrowanie problemu z wydajnością

- Zamknij wszystkie zbędne przeglądarki internetowe.
- Uruchom Rejestratora problemów lub innego rejestratora ekranu.
- Uruchom przechwytywanie programu Netmon (lub narzędzie do śledzenia sieci).
- Wyczyść pamięć podręczną DNS na kliencie z wiersza polecenia, wpisując ipconfig /flushdns.
- Uruchom nową sesję przeglądarki i włącz program HTTPWatch.
- Opcjonalnie: Jeśli testujesz Exchange Online, uruchom Exchange Analizatora wydajności klienta z Office 365 administracyjnej.
- Odtomów dokładnie czynności, które powodują problem z wydajnością.
- Zatrzymaj śledzenie narzędzia Netmon lub innego narzędzia.
- W wierszu polecenia uruchom śledzenie trasy do subskrypcji usługi Office 365, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Zatrzymaj Rejestratora problemów i zapisz klip wideo. Pamiętaj, aby uwzględnić datę i godzinę przechwytywania oraz to, czy na wideo pokazaliśmy dobrą, czy niedosytną wydajność.
- Zapisz pliki śledzenia. Pamiętaj jeszcze raz, aby uwzględnić datę i godzinę przechwytywania oraz to, czy na wideo pokazaliśmy dobrą, czy niedosytną wydajność.

Jeśli nie wiesz, jak uruchamiać narzędzia wymienione w tym artykule, nie przejmuj się, ponieważ podamy te instrukcje poniżej. Jeśli wiesz, jak zrobić tego rodzaju przechwytywanie sieci, możesz przejść do sekcji Jak zbierać linie bazowe [, w](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines) której opisano filtrowanie i odczytywanie dzienników.

### <a name="flush-the-dns-cache-first"></a>Opróżnij najpierw pamięć podręczną DNS

Dlaczego? Opróżniając pamięć podręczną DNS, rozpoczynasz testy od początku. Wyczyszczenie pamięci podręcznej powoduje zresetowanie zawartości rozpoznawania nazw DNS do najbardziej aktualnych wpisów. Pamiętaj, że opróżnienie pamięci hosts nie powoduje usunięcia wpisów pliku z plikami hosts. Jeśli intensywnie korzystasz z wpisów w pliku HOSTA, skopiuj te wpisy do pliku w innym katalogu, a następnie opróżnij plik HOST.

#### <a name="flush-your-dns-resolver-cache"></a>Opróżnienie pamięci podręcznej rozpoznawania nazw DNS

1. Otwórz wiersz polecenia (**uruchom polecenie Uruchom** \>  \> **cmd** lub **Windows cmd**\>).
2. Wpisz następujące polecenie i naciśnij klawisz ENTER:

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

Narzędzie do monitorowania sieci ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) firmy Microsoft analizuje pakiety, czyli ruch przechodzący między komputerami w sieciach. Używając narzędzia Netmon do śledzenia ruchu za pomocą programu Office 365, można przechwytywać, wyświetlać i odczytywać nagłówki pakietów, identyfikować urządzenia interveningowe, sprawdzać ważne ustawienia na sprzęcie sieciowym, szukać upuszczanych pakietów i śledzić przepływ ruchu między komputerami w sieci firmowej i sieci Office 365. Ponieważ rzeczywista treść ruchu jest zaszyfrowana, czyli (jest przenoszona na porcie 443 za pośrednictwem protokołu SSL/TLS, nie można odczytywać wysyłanych plików. Zamiast tego można uzyskać niefiltrowany ślad ścieżki, którą pobiera pakiet, co może ułatwić śledzenie zachowania problemu.

Pamiętaj, aby na tym momencie nie stosować filtru. Zamiast tego przed zatrzymaniem śledzenia i zapisaniem należy wykonać czynności, które pokazują problem.

Po zainstalowaniu programu Netmon 3.4 otwórz narzędzie i zrób tak:

### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Sporządzanie śledzenia w programie Netmon i odtwarzanie problemu

1. Uruchom program Netmon 3.4.
Na stronie startowej znajdują się trzy  okienka **: Ostatnie** przechwycone **zdjęcia, Wybierz** sieci i Wprowadzenie do programu **Microsoft Network Monitor 3.4. Uwaga**. Na panelu Wybierz sieci jest również wyświetlona lista sieci domyślnych, z których można przechwytywać. Upewnij się, że w tym miejscu są zaznaczone karty sieciowe.

2. Kliknij **pozycję Nowe przechwytywanie** w górnej części **strony startowej** . Zostanie do niej dodano nową kartę obok **karty Strona** startowa o **nazwie Przechwytywanie 1**.
![Interfejs użytkownika programu Netmon z wyróżnioną  przyciskami Nowe przechwytywanie, Uruchamianie i Zatrzymywanie.](../media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Aby zrobić proste przechwytywanie, kliknij **przycisk Start** na pasku narzędzi.

4. Odtąd odtąd odtąd odtąd odtąd występuje problem z wydajnością.

5. Kliknij **pozycję Zatrzymaj** \> **zapisywanie** \> **pliku jako**. Pamiętaj, aby w strefie czasowej podać datę i czas oraz o tym, czy na przykład chodzi o niedoszłą, czy dobrą wydajność.

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) jest dostarczany z opłatą i bezpłatną edycją. Bezpłatna wersja Basic Edition zawiera wszystkie funkcje potrzebne do tego testu. HttpWatch monitoruje ruch sieciowy i czas ładowania strony bezpośrednio w oknie przeglądarki. HTTPWatch to wtyczka przeglądarki Internet Explorer, która graficznie opisuje wydajność. Analizę można zapisać i wyświetlić w programie HTTPWatch Studio.

> [!NOTE]
> Jeśli używasz innej przeglądarki, takiej jak Firefox lub Google Chrome, albo nie możesz zainstalować programu HTTPWatch w programie Internet Explorer, otwórz nowe okno przeglądarki i naciśnij klawisz F12 na klawiaturze. W dolnej części okna przeglądarki powinno zostać wyświetlony okno podręczne Narzędzia deweloperskiej. Jeśli korzystasz z przeglądarki Opera, naciśnij klawisze CTRL+SHIFT+I, aby użyć narzędzia  Web Inspector, a następnie kliknij kartę Sieć i wykonaj opisane poniżej testy. Informacje będą nieco inne, ale czasy ładowania nadal będą wyświetlane w milisekundach. > HTTPWatch jest również bardzo przydatny w przypadku problemów z SharePoint ładowania stron w trybie online.

### <a name="run-httpwatch-and-reproduce-the-issue"></a>Uruchamianie programu HTTPWatch i odtwarzanie problemu

HTTPWatch to wtyczka przeglądarki, więc sposób eksponowania narzędzia w przeglądarce różni się nieco w przypadku każdej wersji programu Internet Explorer. Zazwyczaj program HTTPWatch można znaleźć pod pasku poleceń w przeglądarce Internet Explorer. Jeśli nie widzisz wtyczki HTTPWatch w oknie przeglądarki,  \> sprawdź wersję przeglądarki **, klikając** pozycję Pomoc — informacje lub w nowszych wersjach programu Internet Explorer kliknij symbol koła zębatego i pozycję **Internet Explorer — informacje**. Aby uruchomić pasek **Polecenia** , kliknij prawym przyciskiem myszy pasek menu w programie Internet Explorer, a następnie kliknij polecenie **Pasek poleceń**.

W przeszłości narzędzie HTTPWatch było skojarzone zarówno z paskami poleceń, jak i z paskiem Eksploratora, więc jeśli po zainstalowaniu nie widzisz od razu ikony (nawet po ponownym uruchomieniu), zaznacz pole wyboru Narzędzia i paski narzędzi dla ikony. Pamiętaj, że paski narzędzi można dostosowywać i można do nich dodawać opcje.

![Pasek narzędzi poleceń programu Internet Explorer z wyświetloną ikoną narzędzia HTTPWatch.](../media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)

1. Uruchom program HTTPWatch w oknie przeglądarki Internet Explorer. Zostanie on zadokowany do przeglądarki u dołu tego okna. Kliknij **pozycję Nagraj**.

2. Odtąd odtąd odtąd występuje problem z wydajnością. Kliknij przycisk **Zatrzymaj** w programie HTTPWatch.

3. **Zapisz** program HTTPWatch lub **wyślij pocztą e-mail**. Plik należy nazwać tak, aby zawierał informacje o dacie i godzinie oraz informację o tym, czy czujka zawiera pokaz dobrej, czy słabej wydajności.

![Program HTTPWatch z kartą Network (Sieć) służy do ładowania strony Office 365 głównej.](../media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Ten zrzut ekranu pochodzi z Professional HTTPWatch. Możesz otworzyć ślady wykonane w wersji podstawowej na komputerze z nową Professional i odczytać ją tam. Dzięki tej metodzie można uzyskać dostęp do dodatkowych informacji.

## <a name="problem-steps-recorder"></a>Rejestrator problemów

Rejestrator problemów (PSR.exe umożliwia rejestrowanie problemów w ich przypadku. Jest to bardzo przydatne i łatwe w uruchomieniu narzędzie.

### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Uruchamianie Rejestratora problemów (PSR.exe) w celu nagrywania pracy

1. Użyj **przycisku Start** \> **Run** \> **,PSR.exe** \> **przycisk OK**, lub kliknij Windows **typ** \> klawisza **PSR.exe** \> a następnie naciśnij klawisz ENTER.

2. Gdy zostanie wyświetlone małe PSR.exe kliknij pozycję **Rozpocznij** rejestrowanie i odtąd występuje problem z wydajnością. W razie potrzeby możesz dodać komentarze, klikając pozycję **Dodaj komentarze**.

3. Po **zakończeniu** tych czynności kliknij przycisk Zatrzymaj rejestrowanie. Jeśli problem z wydajnością dotyczy renderowania strony, przed zatrzymaniem rejestrowania zaczekaj na renderowanie strony.

4. Kliknij **Zapisz**.

![Zrzut ekranu rejestratora problemów lub PSR.exe.](../media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)

Data i godzina są rejestrowane dla Ciebie. Dzięki temu narzędzie psr jest w czasie linkiem do narzędzia Netmon trace i narzędzia HTTPWatch, co ułatwia precyzyjne rozwiązywanie problemów. Data i godzina w rekordzie PSR może na przykład pokazywać, że między logowaniem i przeglądaniem adresu URL a częściowym renderowaniem witryny administratora minął minuta.

## <a name="read-your-traces"></a>Odczytywanie danych śledzenia

Nie jest możliwe, aby za pośrednictwem artykułu nauczyć wszystkiego na temat rozwiązywania problemów z siecią i wydajnością. Aby osiągać dobre wyniki, należy się wiedzę na temat sposobu działania sieci i osiąganych zwykle wydajności. Można jednak zaokrąglić listę najważniejszych problemów i pokazać, jak narzędzia mogą ułatwić ich wyeliminowanie.

Jeśli chcesz podnieść umiejętności czytania śledzenia sieci dla witryn sieci Office 365, nie ma lepszego nauczyciela niż regularne tworzenie śledzenia ładowania stron i uzyskiwanie doświadczenia podczas ich czytania. Jeśli na przykład masz szansę, załaduj usługę Office 365 i śledź proces. Przefiltruj wyniki śledzenia pod celu wyszukania ruchu DNS lub wyszukaj w danych ramek nazwę przeglądanej usługi. Zeskanuj wyniki śledzenia, aby uzyskać informacje o czynnościach, które należy wykonać podczas ładowania usługi. Dzięki temu dowiesz się, jak powinno wyglądać normalne ładowanie strony, a w przypadku rozwiązywania problemów (zwłaszcza dotyczących wydajności) porównanie dobrych i złych danych śledzenia może być bardzo przydatne.

W programie Netmon w polu filtru wyświetlania jest używana funkcja Microsoft IntelliSense. IntelliSense czyli funkcja uzupełniania kodu polega na tym, że po wpisaniu kropki w rozwijanym polu wyboru są wyświetlane wszystkie dostępne opcje. Jeśli na przykład martwisz się o skalowanie okna protokołu TCP, korzystając z tej funkcji, możesz znaleźć sposób na filtr (  `.protocol.tcp.window < 100`taki jak ).

![Zrzut ekranu monitora sieci pokazujący, że pole Filtr wyświetlania korzysta z technologii IntelliSense.](../media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)

Wyniki śledzenia z netmonu mogą mieć duże ilości ruchu. Jeśli nie masz doświadczenia w ich odczytywaniu, prawdopodobnie przy pierwszym otwarciu śledzenia będzie ich przytłaczać. Najpierw należy oddzielić sygnał od szumu tła w danych śledzenia. Zostały przetestowane pod Office 365 i jest to ruch, który chcesz zobaczyć. Jeśli masz już informacje o przechodzeniu między wynikami śledzenia, być może nie będziesz potrzebować tej listy.

Ruch między Twoim klientem i Office 365 jest przekierowywowyny przez TLS, co oznacza, że treść ruchu będzie zaszyfrowana i nieczylna w ogólnych wynikach śledzenia programu Netmon. Do analizy wydajności nie jest potrzebna szczegółowe informacje zawarte w pakietach. Nagłówki pakietów i zawarte w nich informacje są jednak bardzo ważne.

### <a name="tips-to-get-a-good-trace"></a>Wskazówki uzyskania dobrych śledzenia

- Poznaj adres IPv4 lub IPv6 swojego klienta. Możesz ją uzyskać z wiersza polecenia, wpisując **IPConfig** i naciskając klawisz ENTER. Znajomość tego adresu pozwala natychmiast ustalić, czy ruch w wynikach śledzenia dotyczy bezpośrednio Twojego klienta. Jeśli jest znany serwer proxy, przekieruj go za pomocą polecenia ping i uzyskaj także jego adres IP.

- Opróżnij pamięć podręczną rozpoznawania nazw DNS i, jeśli to możliwe, zamknij wszystkie przeglądarki oprócz tej, za którą są przeprowadzane testy. Jeśli nie możesz tego zrobić, na przykład jeśli pomoc techniczna używa narzędzia opartego na przeglądarce do obsługi pulpitu Twojego komputera, przygotuj się do filtrowania danych śledzenia.

- W przypadku napiętego śledzenia odszukaj Office 365, z których korzystasz. Jeśli jeszcze nigdy nie widziałeś/-asz ruchu, jest to pomocny krok oddzielenia problemu z wydajnością od innego szumu sieciowego. Można to zrobić na kilka sposobów. Bezpośrednio przed testem możesz użyć polecenia _ping_ lub _polecenia PsPing_ względem adresu URL określonej usługi (`ping outlook.office365.com` lub `psping -4 microsoft-my.sharepoint.com:443`na przykład). Polecenie ping lub polecenie PsPing można również łatwo znaleźć w wynikach śledzenia programu Netmon (według nazwy procesu). W ten sposób możesz zacząć szukać.

Jeśli śledzenie narzędzia Netmon jest możliwe tylko w czasie wystąpienia problemu, także jest to możliwe. Aby zorientować się w programie, użyj filtru, takiego jak `ContainsBin(FrameData, ASCII, "office")` lub `ContainsBin(FrameData, ASCII, "outlook")`. Możesz zarejestrować numer ramki z pliku śledzenia. Możesz także przewinąć okienko _Podsumowanie_ ramek do prawej strony i odszukać kolumnę Identyfikator konwersacji. Jest tam wskazana liczba identyfikatora tej konkretnej konwersacji, który można również zarejestrować i sprawdzić osobno później. Pamiętaj, aby usunąć ten filtr przed zastosowaniem innego filtrowania.

> [!TIP]
> Narzędzie Netmon ma wiele pomocnych filtrów wbudowanych. Wypróbuj przycisk **Załaduj** filtr u góry _okienka Wyświetl_ filtr.

![Znajdź swój adres IP za pomocą narzędzia PSPing w wierszu polecenia na komputerze klienckim.](../media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)

![Śledzenie programu Netmon z klienta pokazujące to samo polecenie PSPing za pośrednictwem filtru TCP. Flags.Syn == 1.](../media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)

Zapoznaj się z informacjami o ruchu i naucz się lokalizować potrzebne informacje. Naucz się na przykład, jak określić, który pakiet w danych śledzenia ma pierwsze odwołanie do Office 365, z której korzystasz (na przykład "Outlook").

Jeśli Office 365 Outlook w trybie online, ruch zaczyna się w następujący sposób:

- Standardowe zapytanie DNS i odpowiedź DNS dla outlook.office365.com pasujących identyfikatorów zapytań. Ważne jest, aby zanotować przesunięcie czasu dla tego zwrotu, a także miejsce na świecie, w którym Office 365 globalny system DNS wysyła żądanie rozpoznawania nazw. Najlepiej, aby to miejsce było jak najbardziej lokalne, a nie w połowie drogi na świecie.

- Żądanie HTTP GET, którego raport o stanie został trwale przeniesiony (301)

- Ruch RWS, w tym RWS, Połączenie żądania i Połączenie odpowiedzi. Oznacza to, że zdalna usługa Winsock nawiązaniu połączenia za Ciebie.

- Konwersacja TCP SYN i TCP SYN/ACK. Wiele ustawień w tej konwersacji ma wpływ na wydajność.

- Następnie seria ruchu TLS:TLS, w której odbywają się konwersacje między certyfikatem TLS a certyfikatem TLS. (Pamiętaj, że dane są szyfrowane przy użyciu protokołu SSL/TLS).

Wszystkie części ruchu są ważne i połączone, ale mała część wyników śledzenia zawiera informacje szczególnie ważne podczas rozwiązywania problemów z wydajnością, więc skoncentrujmy się na tych obszarach. Ponadto Office 365, ponieważ zrobiliśmy wystarczająco dużo rozwiązywania problemów z wydajnością w firmie Microsoft, aby skompilować 10 głównych problemów, skoncentrowaliśmy się na tych problemach i o tym, jak za ich pomocą je zasypować w następnej części.

Jeśli jeszcze nie zainstalowano ich wszystkich, w poniższej macierzy używa się kilku narzędzi. Tam, gdzie to możliwe. Linki do punktów instalacji. Lista zawiera typowe narzędzia do śledzenia sieci, takie jak [Netmon](https://www.microsoft.com/download/details.aspx?id=4865) i [Wireshark](https://www.wireshark.org/), ale użyj dowolnego narzędzia do śledzenia, które ci się podoba i w którym wiesz, jak filtrować ruch sieciowy. Podczas testowania pamiętaj:

- *Zamknij przeglądarki i przetestuj je*  przy użyciu tylko jednej uruchomionej przeglądarki — spowoduje to zmniejszenie ogólnej ilości ruchu do przechwycenia. Dzięki temu śledzenie danych jest mniej zajęte.
- *Opróżnij pamięć podręczną rozpoznawania nazw DNS*  na kliencie — dzięki temu po rozpoczęciu przechwytywania będziesz mieć dostęp do bardziej przejrzystych danych śledzenia.

## <a name="common-issues"></a>Typowe problemy

Niektóre typowe problemy, które mogą wystąpić, i sposób ich znalezienia w danych śledzenia sieci.

### <a name="tcp-windows-scaling"></a>Skalowanie Windows TCP

Można go znaleźć w aucie SYN – SYN/ACK. Starsze lub starzejące się urządzenia mogą nie korzystać ze skalowania okien protokołu TCP.  Bez odpowiednich ustawień skalowania okien protokołu TCP domyślny 16-bitowy bufor w nagłówkach TCP jest wypełniany w milisekundach.  Ruch nie może być przesyłany, dopóki klient nie otrzyma potwierdzenia, że oryginalne dane zostały odebrane, co powoduje opóźnienia.

#### <a name="tools"></a>Narzędzia

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Czego szukać

Poszukaj ruchu SYN – SYN/ACK w danych śledzenia sieci.  W programie Netmon użyj filtru, takiego jak  `tcp.flags.syn == 1`. Ten filtr jest taki sam w programie Wireshark.

![Filtrowanie pakietów Syn w narzędziu Netmon lub Wireshark dla obu narzędzi: TCP. Flags.Syn == 1.](../media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Zwróć uwagę, że dla każdej syn istnieje numer portu źródłowego (SrcPort) powiązany z portem docelowym (DstPort) pokrewnej potwierdzenia (SYN/ACK).

Aby wyświetlić Windows skalowania danych używane przez połączenie sieciowe, rozwiń najpierw wartość SYN, a następnie powiązaną z nią kartę SYN/ACK.

![Grafika przedstawiająca sposób dopasowania wartości SrcPort do DstPort w danych śledzenia w celu uzyskania różnicy czasu.](../media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)

### <a name="tcp-idle-time-settings"></a>Czas bezczynności protokołu TCP Ustawienia

Zeszytowo większość sieci obwodowych jest skonfigurowana do połączeń przejściowych, co oznacza, że bezczynne połączenia są na ogół zakończone. Bezczynne sesje TCP mogą być kończyne przez proxy i zapory po czasie większym niż 100–300 sekund. Może to być problematyczne Outlook online, ponieważ tworzy ona i używa długotrwałych połączeń, niezależnie od tego, czy są bezczynne.

Po zakończeniu połączenia przez urządzenia proxy lub zapory klient nie jest informowany i próba użycia usługi Outlook Online będzie oznaczać, że klient wielokrotnie będzie próbował przywrócić połączenie przed jego wprowadzeniem. Podczas ładowania strony mogą się pojawić zawieszanie się produktu, monity lub wolne działanie.

#### <a name="tools"></a>Narzędzia

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Czego szukać

W programie Netmon poszukaj czasu rundy w polu Time Offset (Przesunięcie czasu). Czas rundy to czas między wysłaniem przez klienta żądania do serwera a odebraniem odpowiedzi z powrotem. Sprawdzanie między klientem a punktem wyjścia (np. Klient --\> serwer proxy) lub klient do Office 365 (klient --\> Office 365). Można to zobaczyć w przypadku wielu typów pakietów.

Jako przykład filtr w programie Netmon może wyglądać podobnie do filtru w programie Netmon  `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`lub w programie Wireshark  `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.

> [!TIP]
> Nie wiesz, czy adres IP w danych śledzenia należy do Twojego serwera DNS? Spróbuj go znaleźć w wierszu polecenia. Kliknij **przycisk Start** \> **Run** \> i **wpisz cmd** lub naciśnij **klawisz Windows i** \> wpisz **cmd**. Po wyświetleniu monitu wpisz  `nslookup <the IP address from the network trace>`. Aby to sprawdzić, użyj funkcji nslookup z adresem IP własnego komputera. > Aby wyświetlić listę zakresów adresów IP firmy Microsoft, zobacz adresy URL Office 365 [i zakresy adresów IP](./urls-and-ip-address-ranges.md).

Jeśli występuje problem, należy oczekiwać długich przesunięć czasowych, które w tym przypadku (Outlook Online) są widoczne szczególnie w pakietach TLS:TLS, które pokazują przepływ danych aplikacji (na przykład w aplikacji Netmon `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`pakiety danych aplikacji można znaleźć za pośrednictwem ). W czasie sesji powinien być wyświetlony płynny postęp. Jeśli podczas odświeżania usługi Outlook Online występują duże opóźnienia, może to być spowodowane wysłaniem dużej długości resetowania.

### <a name="latencyround-trip-time"></a>Opóźnienie/czas rundy

Opóźnienie jest miarą, która może się znacznie zmieniać w zależności od wielu zmiennych, takich jak uaktualnienie starszych urządzeń, dodanie dużej liczby użytkowników do sieci czy ogólna wartość procentowa przepustowości zużywanej przez inne zadania w ramach połączenia sieciowego.

Na tej stronie planowanie i dostosowywanie wydajności sieci Office 365 kalkulatory przepustowości dla [Office 365](network-planning-and-performance.md) sieci.

Chcesz zmierzyć szybkość swojego połączenia lub przepustowość połączenia Twojego isp? Spróbuj użyć tej witryny (lub podobnych witryn): Oficjalna witryna programu [Speedtest](https://www.speedtest.net/) lub wyszukaj w ulubionej wyszukiwarce **frazę testową szybkości.**

#### <a name="tools"></a>Narzędzia

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Czego szukać

W celu śledzenia opóźnienia w danych śledzenia skorzystaj z zapisu adresu IP klienta i adresu IP serwera DNS w Office 365. Ułatwi to filtrowanie śledzenia. Jeśli łączysz się za pośrednictwem serwera proxy, aby ułatwić sobie pracę, będziesz potrzebować adresu IP swojego klienta, adresu IP serwera proxy/serwera wychodzącego i adresu IP serwera Office 365 DNS.

Żądanie  *ping wysłane*  do firmy outlook.office365.com będzie zawierało nazwę centrum danych, w przypadku gdy polecenie ping może nie być w stanie połączyć się ze znakiem towarowym wysyłanym po kolejnych pakietach ICMP. Jeśli używasz narzędzia PsPing (bezpłatnego narzędzia do pobrania) i określonego portu (443), a być może do używania protokołu IPv4 (-4), otrzymasz średni czas rundy dla wysyłanych pakietów. Będzie to działać w przypadku innych adresów URL w usługach Office 365, takich jak `psping -4 yourSite.sharepoint.com:443`. W rzeczywistości możesz określić liczbę pingów, aby uzyskać większą próbkę dla Twojej średniej. Możesz też użyć polecenia ping w rodzaju `psping -4 -n 20 yourSite-my.sharepoint.com:443`.

> [!NOTE]
> Program PsPing nie wysyła pakietów ICMP. Polecenie ping jest poleceniem ping z pakietami TCP przez określony port, dzięki czemu możesz użyć dowolnego otwartego portu. W Office 365 ssl/TLS spróbuj do swojego psPing dołączyć numer portu 443.

![Zrzut ekranu: polecenie ping rozpoznawce outlook.office365.com oraz polecenie PSPing wykonujące te same działania 443, ale również raportowanie średniej wartości RTT 6,5 cala.](../media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Jeśli podczas Office 365 wykonywania śledzenia sieci załadowano powolną stronę sieciową, należy odfiltrować wyniki śledzenia w programie Netmon lub Wireshark pod wartością `DNS`. Jest to jeden z poszukiwanych ip.

Oto czynności, które należy wykonać, aby przefiltrować konto Netmon w celu uzyskania adresu IP (i przyjrzyj się opóźnieniu DNS). W tym przykładzie outlook.office365.com adres URL dzierżawy usługi SharePoint Online (na hithere.sharepoint.com danych).

1. Przekieruj adres URL `ping outlook.office365.com` za pomocą polecenia ping i w wynikach wyszukiwania zanotuj nazwę i adres IP serwera DNS, na który zostało wysłane żądanie ping.
2. Przeszukaj sieć, otwierając stronę lub wykonując akcję, która powoduje problem z wydajnością, lub, jeśli zobaczysz duże opóźnienie podczas samego żądania ping, prześledzenia sieci.
3. Otwórz śledzenie w programie Netmon i przefiltruj rekordy DNS (ten filtr działa również w programie Wireshark, ale jest w nim rozróżniana wielkość liter `-- dns`). Ponieważ znasz nazwę serwera DNS na stronie ping, możesz także szybko filtrować w programie Netmon w ten sposób: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`, która wygląda następująco w systemie dns Wireshark, a ramka zawiera "namnorthwest".<br/>Otwórz pakiet odpowiedzi i w oknie Netmon **Frame Details (Szczegóły ramki programu** Netmon) kliknij pozycję **DNS** , aby rozwinąć pakiet, aby uzyskać więcej informacji. W informacjach DNS znajdziesz adres IP serwera DNS, do których żądanie przeszedło w Office 365. Ten adres IP będzie potrzebny do następnego kroku (narzędzia PsPing). Usuń filtr, kliknij prawym przyciskiem myszy odpowiedź DNS w witrynie Netmon (**podsumowanie** \>  \> ramki Znajdź konwersacje **DNS**), aby wyświetlić zapytanie DNS i odpowiedź obok siebie.
4. W programie Netmon zwróć też uwagę na kolumnę Time Offset (Przesunięcie czasu) między żądaniem DNS i odpowiedzią. W następnym kroku bardzo przydatne jest łatwe do zainstalowania i użycia narzędzie [PsPing](/sysinternals/downloads/psping) , które często jest blokowane w zaporach, oraz dlatego, że narzędzie PsPing łatwo śledzi opóźnienia w milisekundach. Program PsPing kończy połączenie TCP z adresem i portem (w tym przypadku należy otworzyć port 443).
5. Zainstaluj program PsPing.
6. Otwórz wiersz polecenia (\> \> rozpocznij uruchamianie, wpisz cmd lub Windows key \> type cmd) i zmień katalog na katalog, w którym zainstalowano polecenie PsPing, aby uruchomić polecenie PsPing. W przykładach widać, że mam folder Perf w katalogu głównym na C. Możesz to zrobić, aby uzyskać szybki dostęp.
7. Wpisz polecenie PsPing względem adresu IP serwera DNS programu Office 365 z wcześniejszego śledzenia programu Netmon, w tym numeru portu, takiego jak `psping -n 20 132.245.24.82:445`. Spowoduje to przysyłanie próbki 20 poleceniech ping i uśrednianie opóźnienia po zatrzymaniu polecenia PsPing.

Jeśli przechodzisz do programu Office 365 serwera proxy, czynności są nieco inne. Najpierw należy uruchomić program PsPing na serwerze proxy, aby uzyskać wartość średniego opóźnienia (w milisekundach) do serwera proxy/serwera wychodzącego i z powrotem, a następnie uruchomić program PsPing na serwerze proxy lub na komputerze z bezpośrednim połączeniem internetowym w celu uzyskania brakującej wartości (połączenia z siecią Office 365 i z powrotem).

Jeśli wybierzesz uruchomienie programu PsPing z serwera proxy, będą dwie wartości w milisekundach: Z klienta do serwera proxy lub punktu wychodzącego oraz z serwera proxy do Office 365. Gotowe! Mimo to rejestrowanie wartości.

Uruchomienie programu PsPing na innym komputerze klienckim z bezpośrednim połączeniem z Internetem, czyli bez serwera proxy, spowoduje dwie wartości w milisekundach: z klienta do serwera proxy lub punktu wyjścia oraz z klienta do serwera Office 365. W takim przypadku odejmij wartość klienta do serwera proxy lub punktu wyjścia od wartości klienta do Office 365 i będziesz mieć numery RTT od klienta do serwera proxy lub punktu wyjścia oraz od serwera proxy lub punktu wyjścia do Office 365.

Jeśli jednak możesz znaleźć klienta w lokalizacji, która jest podłączona bezpośrednio, lub pomija serwer proxy, możesz na początek sprawdzić, czy problem występuje na nim, a następnie sprawdzić, czy z niego korzystać.

Opóźnienie widoczne w danych śledzenia w programie Netmon może się liczyć na ich dodatkowe milisekundy, o ile jest ich wystarczająco dużo w danej sesji.

![Ogólne opóźnienie w programie Netmon z domyślną kolumną różnicy czasu programu Netmon dodaną do podsumowania ramki.](../media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> Twój adres IP może różnić się od przedstawionego tutaj adresu IP, na przykład polecenie ping może zwrócić wartość podobną do 157.56.0.0/16 lub podobnego zakresu. Aby uzyskać listę zakresów używanych przez Office 365, zapoznaj się z Office 365 [URL i zakresami adresów IP](./urls-and-ip-address-ranges.md).

Pamiętaj, aby rozwinąć wszystkie węzły (u góry znajduje się przycisk), jeśli chcesz wyszukać na przykład 132,245.

### <a name="proxy-authentication"></a>Uwierzytelnianie serwera proxy

Dotyczy to tylko osób, które mają dostęp do serwera proxy. Jeśli nie, możesz pominąć te kroki. Uwierzytelnianie serwera proxy, jeśli działa prawidłowo, powinno zawsze potrwać kilka milisekund. Nie powinien być przejściowy wzrost wydajności, na przykład w okresach szczytowego użytkowania.

Jeśli uwierzytelnianie serwera proxy jest w trybie wł., każdorazowo przy każdym nawiązaniu nowego połączenia TCP z serwerem Office 365 w celu uzyskania informacji w tle należy przejść przez proces uwierzytelniania. Uwierzytelnienie może na przykład przy przełączaniu z kalendarza do aplikacji Poczta Outlook Online. Jeśli na SharePoint w trybie online są wyświetlane multimedia lub dane z wielu witryn lub lokalizacji, należy uwierzytelnić je dla każdego różnych połączeń TCP potrzebnych do wyrenderowania danych.

W Outlook Online mogą wystąpić wolne czasy ładowania przy każdym przełączaniu między kalendarzem i skrzynką pocztową, a powolne ładowanie stron w u SharePoint Online. Jednak istnieją inne symptomy, których tu nie odano.

Uwierzytelnianie serwera proxy to ustawienie na wychodzącym serwerze proxy. Jeśli powoduje ono problemy z wydajnością Office 365 sieci, musisz skonsultować się z zespołem sieciowym.

#### <a name="tools"></a>Narzędzia

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Czego szukać

Uwierzytelnianie serwera proxy odbywa się za każdym razem, gdy należy wyzbyć nową sesję TCP, zazwyczaj w celu żądania plików lub informacji z serwera albo w celu podaniem informacji. Na przykład uwierzytelnianie serwera proxy może obejmować żądania HTTP GET lub HTTP POST. Jeśli chcesz wyświetlić w danych śledzenia ramki, w których są uwierzytelnione żądania, dodaj kolumnę "NTLMSSP Summary" do dodatku Netmon i odfiltruj element  `.property.NTLMSSPSummary`. Aby sprawdzić, jak długo trwa uwierzytelnianie, dodaj kolumnę Time Delta (Różnica czasu).

Aby dodać kolumnę do dodatku Netmon:

1. Kliknij prawym przyciskiem myszy kolumnę, taką jak **Opis**.
2. Kliknij **pozycję Wybierz kolumny**.
3. Na _liście znajdź wartości NTLMSSP Summary (Podsumowanie NTLMSSP)_ i _Time Delta_ (Różnicę czasu), a następnie kliknij przycisk **Add (Dodaj**).
4. Przenieś nowe kolumny przed lub za kolumnę _Description_ (Opis), aby można je było odczytać obok siebie.
5. Kliknij przycisk **OK**.

Nawet jeśli nie dodasz kolumny, filtr w programie Netmon będzie działać. Rozwiązywanie problemów będzie jednak znacznie prostsze, jeśli będziesz widzieć, na jakim etapie uwierzytelniania się używasz.

Podczas szukania wystąpień uwierzytelniania serwera proxy pamiętaj o przeanaliście wszystkich ramek, w których występuje wyzwanie NTLM lub uwierzytelnianie wiadomości. W razie potrzeby kliknij prawym przyciskiem myszy określony fragment ruchu i kliknij polecenie Tcp Znajdź konwersacje \> . W tych konwersacjach należy pamiętać o wartościach zmiany czasu.

![Śledzenie serwera netmon przedstawiające uwierzytelnianie serwera proxy filtrowane według konwersacji.](../media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

Czterosek sekundowe opóźnienie uwierzytelniania serwera proxy w programie Wireshark. Kolumna **Time delta from previous displayed frame** (Różnica czasu od poprzednio wyświetlonej ramki) została wykonana przez kliknięcie prawym przyciskiem myszy pola o tej samej nazwie w szczegółach ramki i wybranie pozycji Add as Column (Dodaj jako kolumnę).  <br/> ![W programie Wireshark kolumnę "Time delta from previous displayed frame" (Różnica czasu od poprzednio wyświetlonej ramki) można utworzyć przez kliknięcie prawym przyciskiem myszy pola o takiej samej nazwie w szczegółach ramki i wybranie pozycji Add as Column (Dodaj jako kolumnę).](../media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>Wydajność systemu DNS

Rozpoznawania nazw działa najlepiej i najszybciej, gdy odbywa się jak najbardziej blisko kraju klienta.

Jeśli rozpoznawanie nazw DNS odbywa się za granicą, może dodawać sekundy do ładowania stron. Najlepiej, jeśli rozdzielczość nazw występuje w obszarze poniżej 100 m. Jeśli nie, należy wykonać dalsze badanie.

> [!TIP]
> Nie masz pewności, jak działa łączność z Office 365? Tutaj znajdziesz dokument informacje na temat [łączności z klientem](/previous-versions//dn741250(v=technet.10)).

#### <a name="tools"></a>Narzędzia

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Czego szukać

Analizowanie wydajności serwera DNS jest zazwyczaj innym zadaniem w śledzonej sieci. Narzędzie PsPing jest jednak także pomocne w możliwych przyczynach.

Ruch DNS jest oparty na protokole TCP, a żądania i odpowiedzi UDP są wyraźnie oznaczone identyfikatorem, który pomaga dopasować określone żądanie do określonej odpowiedzi. Ruch DNS jest dosyć, gdy na przykład usługa SharePoint Online używa nazwy sieciowej lub adresu URL na stronie sieci Web. Z zasady większość ruchu, z wyjątkiem przenoszenia stref, działa za pośrednictwem protokołu UDP.

W programach Netmon i Wireshark najbardziej podstawowy filtr, który pozwala spojrzeć na ruch DNS, to po prostu `dns`. Pamiętaj, aby podczas określania filtru używać małe liter. Pamiętaj, aby przed rozpoczęciem odtworzenia problemu na kliencie opróżnić pamięć podręczną rozpoznawania nazw DNS. Na przykład w przypadku powolnego ładowania strony głównej usługi SharePoint Online należy zamknąć wszystkie przeglądarki, otworzyć nową przeglądarkę, uruchomić śledzenie, opróżnić pamięć podręczną rozpoznawania nazw DNS i przejść do witryny usługi SharePoint Online. Po rozpoznaniu całej strony należy zatrzymać i zapisać śledzenie.

![Podstawowy filtr systemu DNS w programie Netmon to DNS.](../media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

W tym miejscu chcemy przyjrzeć się przesuniętowi czasoweowi. Pomocne może też być dodanie kolumny **Time Delta** (Różnica czasu) do wykresu Netmon, co można zrobić, wykonując następujące czynności:

1. Kliknij prawym przyciskiem myszy kolumnę, taką jak **Opis**.
2. Kliknij **pozycję Wybierz kolumny**.
3. Na _liście znajdź pozycję Time Delta_ (Różnica czasu), a następnie kliknij przycisk **Add (Dodaj**).
4. Przenieś nową kolumnę przed lub za kolumnę _Description_ (Opis), aby można je było odczytać obok siebie.
5. Kliknij przycisk **OK**.

Jeśli znajdziesz interesujące zapytanie, rozważ jego odizolowanie, klikając je prawym przyciskiem myszy w panelu szczegółów ramki i wybierając pozycję **Znajdź konwersacje** \> **DNS**. Zwróć uwagę, że panel Konwersacje sieciowe przeskakuje bezpośrednio do określonej konwersacji w dzienniku ruchu UDP.

![Śledzenie ładowania w witrynie Netmon Outlook w trybie online filtrowane przez system DNS i za pomocą funkcji Znajdź konwersacje, a następnie serwera DNS w celu zawężenia wyników.](../media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

W programie Wireshark można utworzyć kolumnę zawierającą czas DNS. Przechowaj dane śledzenia (lub otwórz śledzenie) w programie Wireshark i przefiltruj `dns`je według . lub , bardziej pomocnie,  `dns.time`. Kliknij dowolne zapytanie DNS i rozwiń szczegóły w panelu ze szczegółami  `Domain Name System (response)` . Zobaczysz pole czasu (na przykład `[Time: 0.001111100 seconds]`. Kliknij prawym przyciskiem myszy ten czas i wybierz **pozycję Zastosuj jako kolumnę**. W ten sposób można szybciej **sortować** dane śledzenia w kolumnie Czas. Kliknij nową kolumnę, aby posortować wartości w kolejności malejącej, aby sprawdzić, które wywołanie DNS trwało najdłużej do rozwiązania.

[Przeglądanie witryny SharePoint Online filtrowane w programie Wireshark według wartości dns.time (małe litery), z godziną ze szczegółów w kolumnie i posortowaną rosnąco.](../media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Jeśli chcesz wykonać więcej badań czasu rozpoznawania DNS, spróbuj użyć zapytania PsPing względem portu DNS używanego przez protokół TCP (na przykład  `psping <IP address of DNS server>:53`) . Czy nadal widzisz problem z wydajnością? Jeśli tak się stanie, problem najprawdopodobniej będzie szerszym problemem z siecią niż problem z konkretną aplikacją DNS, na co ma polegać rozpoznawanie nazw. Warto również ponownie wspomnieć, że polecenie ping do serwera outlook.office365.com wskazuje, gdzie jest rozpoznawanie nazw DNS dla usługi Outlook Online (na przykład outlook-namnorthwest.office365.com).

Jeśli problem wygląda na specyficzny dla systemu DNS, może być konieczne skontaktowanie się z działem IT w celu dalszego zbadania tego problemu.

### <a name="proxy-scalability"></a>Skalowalność serwera proxy

Usługi takie Outlook Online w programie Office 365 udzielaj klientom wielu długotrwałych połączeń. Dlatego każdy użytkownik może korzystać z większej liczby połączeń, które wymagają dłuższego czasu życia.

#### <a name="tools"></a>Narzędzia

Matematyka

#### <a name="what-to-look-for"></a>Czego szukać

Nie ma narzędzia do śledzenia sieci ani rozwiązywania problemów specyficznego dla tego problemu. Zamiast tego należy się opierać na obliczeniach przepustowości, biorąc pod uwagę ograniczenia i inne zmienne.

### <a name="tcp-max-segment-size"></a>Maksymalny rozmiar segmentu TCP

Można go znaleźć w aucie SYN – SYN/ACK.  Przekonfiguruj to sprawdzanie w dowolnych wynikach śledzenia sieci wykonanego z wydajnością, aby upewnić się, że pakiety TCP są skonfigurowane do przenoszenia maksymalnej możliwej ilości danych.

Celem jest wyświetlanie 1460 bajtów pamięci mss do transmisji danych. Jeśli jesteś za serwerem proxy lub używasz nat, pamiętaj, aby uruchomić ten test z klienta do serwera proxy/serwera wychodzącego/serwera proxy/serwera proxy/serwera wychodzącego/serwera proxy do serwera Office 365, aby uzyskać najlepsze wyniki! Są to różne sesje TCP.

#### <a name="tools"></a>Narzędzia

Netmon

#### <a name="what-to-look-for"></a>Czego szukać

Maksymalny rozmiar segmentu TCP (MSS) jest jednym z parametrów trójkierunkowego rozwiązania śledzenia sieci, który oznacza, że potrzebne dane znajdują się w pakiecie SYN – SYN/ACK. MsS jest dość proste do zobaczenia.

Otwórz dowolne wyniki śledzenia sieci i znajdź połączenie, które chcesz śledzić lub które pokazuje problem z wydajnością.

> [!NOTE]
> Jeśli podczas wyszukiwania danych śledzenia chcesz znaleźć ruch związane z konwersacją, przefiltruj je według adresu IP klienta, adresu IP serwera proxy lub punktu ruchu wychodzącego albo obu tych adresów. Jeśli zamierzasz przejść bezpośrednio, musisz wysłać testowany adres URL za pomocą polecenia ping pod adres IP Office 365 w wynikach śledzenia i przefiltrować dane według tego adresu.

Patrząc na śledzenie z drugiej strony? Spróbuj użyć filtrów, aby zorientować się w sobie. W programie Netmon uruchom wyszukiwanie na podstawie adresu URL, `Containsbin(framedata, ascii, "sphybridExample")`takiego jak , zanotuj numer ramki.

W programie Wireshark użyj funkcji podobnej  `frame contains "sphybridExample"`do . Jeśli zauważysz, że ruch remote Winsock (RWS) został znaleziony (może być wyświetlany jako [PSH, ACK] w programie Wireshark), pamiętaj, że łączność RWS jest widoczne tuż przed odpowiednim połączeniami SYN – SYN/AKS, jak omówiono wcześniej.

W tym momencie możesz zarejestrować numer ramki, upuścić filtr i kliknąć pozycję  Cały ruch w oknie Network Conversations (Konwersacje sieciowe) w programie Netmon, aby sprawdzić najbliższą wartość SYN.

Co ważne, jeśli w czasie śledzenia nie otrzymaliśmy żadnych informacji o adresie IP, znalezienie adresu URL w wynikach śledzenia ( `sphybridExample-my.sharepoint.com`na przykład w części , na przykład), pozwoli Ci odfiltrować adresy IP.

Znajdź połączenie w wynikach śledzenia, które Cię interesuje. Możesz to zrobić, skanując dane śledzenia, filtrując według adresów IP lub wybierając określone identyfikatory konwersacji za pomocą okna Network Conversations (Konwersacje sieciowe) w programie Netmon. Po odnalezioniu pakietu SYN rozwiń protokół TCP (w programie Netmon) lub program Transmission Control Protocol (w programie Wireshark) w panelu Szczegółów ramki. Rozwiń opcje TCP i MaxSegmentSize. Znajdź powiązaną ramkę SYN-ACK i rozwiń opcje TCP i MaxSegmentSize. Mniejsza z tych dwóch wartości będzie maksymalnym rozmiarem segmentu. Na tym obrazie korzystam z wbudowanej w programie Netmon kolumny o nazwie TCP Troubleshoot (Rozwiązywanie problemów z protokołem TCP).

![Śledzenie sieci filtrowane w programie Netmon przy użyciu wbudowanych kolumn.](../media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

Wbudowana kolumna znajduje się w górnej części **panelu Szczegółów ramki** . Aby przełączyć się z powrotem do widoku normalnego, kliknij ponownie pozycję **Columns (Kolumny** ), a następnie wybierz **pozycję Time Zone (Strefa czasowa**).

![Gdzie można znaleźć menu rozwijane Kolumny dla opcji rozwiązywanie problemów z protokołem TCP (u góry podsumowania ramki).](../media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

Oto przefiltrowane śledzenie w programie Wireshark. Istnieje filtr specyficzny dla wartości MSS (`tcp.options.mss`). Ramki łączy się z dłoniami SYN, SYN/ACK, ACK w dolnej części okna wireshark, co odpowiada szczegółom ramki (tak więc ramka 47 ACK łączy się z ramką 46 SYN/ACK, łączy z ramką 43 SYN), co ułatwia tego rodzaju pracę.

![Śledzenie filtrowane w programie Wireshark według tcp.options.mss pod celu ustawienia maksymalnego rozmiaru segmentu (MSS).](../media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

Jeśli musisz sprawdzić potwierdzanie **selektywne** (następny temat w tej macierzy), nie zamykaj danych śledzenia!

### <a name="selective-acknowledgment"></a>Potwierdzanie selektywne

Można go znaleźć w aucie SYN – SYN/ACK. Musi zostać zgłoszone jako dozwolone zarówno w przypadku synów, jak i SYN/ACK. Potwierdzanie selektywne (SACK) umożliwia płynnnszą ponowną transmisję danych w przypadku brakującego pakietu lub pakietów. Urządzenia mogą wyłączać tę funkcję, co może powodować problemy z wydajnością.

Jeśli jesteś za serwerem proxy lub używasz nat, pamiętaj, aby uruchomić ten test z klienta do serwera proxy/serwera wychodzącego/serwera proxy/serwera proxy/serwera wychodzącego/serwera proxy do serwera Office 365, aby uzyskać najlepsze wyniki! Są to różne sesje TCP.

#### <a name="tools"></a>Narzędzia

Netmon

#### <a name="what-to-look-for"></a>Czego szukać

Potwierdzanie selektywne (SACK) jest innym parametrem w uściśliniu dłoni SYN–SYN/ACK. Śledzenie można filtrować pod względami SYN – SYN/ACK.

Znajdź odpowiednie połączenie w wynikach śledzenia, skanując je, filtrując według adresów IP lub klikając identyfikator konwersacji w oknie Network Conversations (Konwersacje sieciowe) w programie Netmon. Po odnalezioniu pakietu SYN rozwiń protokół TCP w programie Netmon lub rozwiń protokół sterowania transmisją w programie Wireshark w sekcji Szczegółów ramki. Rozwiń pozycję TCP Options (Opcje TCP), a następnie pozycję SACK . Znajdź powiązaną ramkę SYN-ACK i rozwiń opcje TCP oraz jej pole SACK. Upewnij się, że sack jest dozwolony zarówno w przypadku synów, jak i SYN/ACK. Poniżej znajdują się wartości SACK widoczne zarówno w programie Netmon, jak i w programie Wireshark.

![Potwierdzanie selektywne (SACK) w programie Netmon jako wynik wartości tcp.flags.syn == 1.](../media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![Pakiety SACK w programie Wireshark z filtrem tcp.flags.syn == 1.](../media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>Geolokalizacja DNS

To, gdzie na świecie Office 365 rozstrzygnie połączenia DNS, ma wpływ na szybkość połączenia.

Po Outlook DNS w trybie online lokalizacja tego serwera DNS zostanie użyta do nawiązania połączenia z najbliższym centrum danych. Zostanie nawiąż połączenie z serwerem CAS usługi Outlook Online, który będzie używać sieci szkieletowej do łączenia się z centrum danych, w którym są przechowywane Twoje dane. To szybszy sposób.

Podczas uzyskiwania dostępu do usługi SharePoint Online użytkownik podróżując za granicą zostanie przekierowywowany do swojego aktywnego centrum danych — jest to centrum danych, którego lokalizacja jest oparta na bazie głównej dzierżawcy usługi Spo (tak więc do centrum danych w USA, jeśli użytkownik znajduje się w USA).

Usługa Lync Online ma aktywne węzły jednocześnie w więcej niż jednym składniku danych. Podczas wysłania żądań do wystąpień usługi Lync Online system DNS firmy Microsoft określa, skąd na świecie pochodzi żądanie, i zwraca adresy IP najbliższego regionalnego centrum danych, w którym usługa Lync Online jest aktywna.

> [!TIP]
> Chcesz dowiedzieć się więcej o  połączeniach klientów z usługą Office 365? Zobacz artykuł z odwołaniami [do łączności z klientem](/previous-versions//dn741250(v=technet.10)) (i jego przydatną grafiką).

#### <a name="tools"></a>Narzędzia

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Czego szukać

Żądania rozpoznawania nazw od serwerów DNS klienta do serwerów DNS firmy Microsoft w większości przypadków powinny powodować, że system DNS firmy Microsoft zwróci adres IP regionalnego centrum danych. Co to oznacza dla Ciebie? Jeśli Twoja siedziba znajduje się w Bangalore w Indiach, ale podróżujesz po Stanach Zjednoczonych, kiedy Twoja przeglądarka wysyła żądanie do usługi Outlook Online, serwery DNS firmy Microsoft powinny ci podać adresy IP do regionalnych centrów danych w Stanach Zjednoczonych. Jeśli poczta będzie potrzebna Outlook, dane te będą przemieszczać się między centrami danych przez szybką sieć szkieletową firmy Microsoft.

System DNS działa najszybciej, gdy rozpoznawanie nazw jest wykonywane jak najbardziej blisko lokalizacji użytkownika. Jeśli jesteś w Europie, chcesz przejść do systemu Microsoft DNS w Europie i (najlepiej) zająć się centrum danych w Europie. Wydajność klienta w Europie przechodzącego do serwera DNS i centrum danych w Ameryce będzie mniejsza.

Uruchom narzędzie ping w celu outlook.office365.com, aby określić, dokąd na świecie są kierowane Twoje żądania DNS. Jeśli jesteś w Europie, odpowiedź powinna być podobna do outlook-emeawest.office365.com. W Ameryce Północnej i Południowej należy się spodziewać takich outlook-namnorthwest.office365.com.

Otwórz wiersz polecenia na komputerze klienckim (za pomocą polecenia Uruchom \> uruchom \> cmd lub Windows typu klucza \> cmd). Wpisz polecenie ping outlook.office365.com naciśnij klawisz ENTER. Pamiętaj, aby określić wartość -4, jeśli chcesz, aby polecenie ping wysyłało za pośrednictwem protokołu IPv4. Odpowiedź z pakietów ICMP może się nie powieść, ale powinna być widać nazwę serwera DNS, do którego żądanie zostało kierowane. Jeśli chcesz wyświetlić liczby opóźnień dla tego połączenia, spróbuj użyć programu PsPing do adresu IP serwera zwróconego przez polecenie ping.

![Polecenie ping outlook.office365.com przedstawiające rozwiązanie w przypadku outlook-namnorthwest.](../media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![Polecenie PSPing dla adresu IP zwracane przez polecenie ping w outlook.office365.com wyświetla średni czas oczekiwania 28 milisekund.](../media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Office 365 rozwiązywanie problemów z aplikacją

#### <a name="tools"></a>Narzędzia

- Netmon
- HTTPWatch
- Konsola F12 w przeglądarce

Ten artykuł dotyczy sieci, ale nie obejmuje narzędzi używanych podczas rozwiązywania problemów związanych z aplikacją. Na tej stronie znajdziesz jednak zasoby,  *których* [możesz użyć](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).

## <a name="related-topics"></a>Tematy pokrewne

[Zarządzanie Office 365 punktami końcowymi](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 punkty końcowe — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)