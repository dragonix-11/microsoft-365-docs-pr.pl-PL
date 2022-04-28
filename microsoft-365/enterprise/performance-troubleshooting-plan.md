---
title: Plan rozwiązywania problemów z wydajnością dla Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Ten artykuł może pomóc w rozwiązywaniu Office 365 problemów z wydajnością, a nawet rozwiązać niektóre z najczęstszych problemów.
ms.openlocfilehash: 7380d6beb89cdd128ccf86f47e1e3c236aabda77
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100572"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Plan rozwiązywania problemów z wydajnością dla Office 365

Czy musisz znać kroki, które należy wykonać, aby zidentyfikować i naprawić opóźnienia, zawieszenia i niską wydajność między SharePoint Online, OneDrive dla Firm, Exchange Online lub Skype dla firm Online, a komputerem klienckim? Przed wywołaniem pomocy technicznej ten artykuł może pomóc w rozwiązywaniu Office 365 problemów z wydajnością, a nawet rozwiązać niektóre z najczęstszych problemów.

Ten artykuł jest w rzeczywistości przykładowym planem działania, którego można użyć do przechwytywania cennych danych dotyczących problemu z wydajnością w miarę jego wystąpienia. Niektóre najważniejsze problemy są również zawarte w tym artykule.

Jeśli dopiero pracujesz nad wydajnością sieci i chcesz utworzyć długoterminowy plan monitorowania wydajności między maszynami klienckimi i Office 365, zapoznaj się [z Office 365 dostrajaniem wydajności i rozwiązywaniem problemów — administrator i Pro IT](performance-tuning-using-baselines-and-history.md).

## <a name="sample-performance-troubleshooting-action-plan"></a>Przykładowy plan akcji rozwiązywania problemów z wydajnością

Ten plan działania zawiera dwie części; faza przygotowania i faza rejestrowania. Jeśli masz teraz problem z wydajnością i musisz tworzyć zbieranie danych, możesz od razu rozpocząć korzystanie z tego planu.

### <a name="prepare-the-client-computer"></a>Przygotowywanie komputera klienckiego

- Znajdź komputer kliencki, który może odtworzyć problem z wydajnością. Ten komputer będzie używany w trakcie rozwiązywania problemów.
- Zapisz kroki, które powodują wystąpienie problemu z wydajnością, dzięki czemu będziesz gotowy, gdy nadejdzie czas na testowanie.
- Instalowanie narzędzi do zbierania i rejestrowania informacji:
  - Zainstaluj program [Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865) (lub użyj równoważnego narzędzia do śledzenia sieci).
  - Zainstaluj bezpłatną wersję podstawową [protokołu HTTPWatch](https://www.httpwatch.com/download/) (lub użyj równoważnego narzędzia do śledzenia sieci).
  - Użyj rejestratora ekranu lub uruchom rejestrator kroków (PSR.exe), który jest dostarczany z Windows Vista i nowszym, aby zachować zapis kroków, które należy wykonać podczas testowania.

### <a name="log-the-performance-issue"></a>Rejestrowanie problemu z wydajnością

- Zamknij wszystkie obce przeglądarki internetowe.
- Uruchom rejestrator kroków lub inny rejestrator ekranu.
- Uruchom przechwytywanie netmon (lub narzędzie do śledzenia sieci).
- Wyczyść pamięć podręczną DNS na komputerze klienckim z wiersza polecenia, wpisując ciąg ipconfig /flushdns.
- Uruchom nową sesję przeglądarki i włącz aplikację HTTPWatch.
- Opcjonalnie: jeśli testujesz Exchange Online, uruchom narzędzie Analizator wydajności klienta Exchange z konsoli administracyjnej Office 365.
- Odtwórz dokładne kroki, które powodują problem z wydajnością.
- Zatrzymaj śledzenie narzędzia Netmon lub innego narzędzia.
- W wierszu polecenia uruchom trasę śledzenia do subskrypcji Office 365, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Zatrzymaj rejestrator kroków i zapisz wideo. Pamiętaj, aby uwzględnić datę i godzinę przechwytywania oraz to, czy pokazuje ona dobrą, czy złą wydajność.
- Zapisz pliki śledzenia. Ponownie pamiętaj, aby uwzględnić datę i godzinę przechwytywania oraz to, czy pokazuje ona dobrą, czy złą wydajność.

Jeśli nie wiesz już, jak uruchamiać narzędzia wymienione w tym artykule, nie martw się, ponieważ te kroki zostaną przedstawione w następnej kolejności. Jeśli jesteś przyzwyczajony do wykonywania tego rodzaju przechwytywania sieci, możesz przejść do tematu [Jak zbierać punkty odniesienia](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), które opisują filtrowanie i odczytywanie dzienników.

### <a name="flush-the-dns-cache-first"></a>Najpierw opróżnij pamięć podręczną DNS

Dlaczego? Opróżniając pamięć podręczną DNS, uruchamiasz testy z czystym łupkiem. Usuwając pamięć podręczną, resetujesz zawartość programu rozpoznawania nazw DNS do najbardziej aktualnych wpisów. Pamiętaj, że opróżnienie nie powoduje usunięcia wpisów pliku HOSTs. W przypadku obszernego używania wpisów pliku HOST należy skopiować te wpisy do pliku w innym katalogu, a następnie opróżnić plik HOST.

#### <a name="flush-your-dns-resolver-cache"></a>Opróżnianie pamięci podręcznej programu rozpoznawania nazw DNS

1. Otwórz wiersz polecenia (**uruchom** \>  \> polecenie **cmd** lub **Windows klawisz** \> **cmd**).
2. Wpisz następujące polecenie i naciśnij klawisz ENTER:

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

Narzędzie do monitorowania sieci firmy Microsoft ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) analizuje pakiety, czyli ruch, który przechodzi między komputerami w sieciach. Korzystając z narzędzia Netmon do śledzenia ruchu za pomocą Office 365 można przechwytywać, wyświetlać i odczytywać nagłówki pakietów, identyfikować interweniujące urządzenia, sprawdzać ważne ustawienia sprzętu sieciowego, wyszukiwać porzucone pakiety i śledzić przepływ ruchu między komputerami w sieci firmowej i Office 365. Ponieważ rzeczywista treść ruchu jest szyfrowana, oznacza to, że (przemieszcza się na porcie 443 za pośrednictwem protokołu SSL/TLS, nie można odczytać wysyłanych plików. Zamiast tego uzyskasz niefiltrowany ślad ścieżki, którą pobiera pakiet, co może pomóc w śledzeniu zachowania problemu.

Upewnij się, że obecnie nie stosujesz filtru. Zamiast tego wykonaj kroki i zademonstruj problem przed zatrzymaniem śledzenia i zapisywania.

Po zainstalowaniu programu Netmon 3.4 otwórz narzędzie i wykonaj następujące kroki:

### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Prześlij ślad netmona i odtwórz problem

1. Uruchom program Netmon 3.4.
Na stronie **początkowej znajdują się** trzy okienka: **Ostatnie przechwycenia**, **Wybierz sieci** i **Wprowadzenie za pomocą programu Microsoft Network Monitor 3.4. Zwróć uwagę**. Panel Wybieranie sieci udostępnia również listę sieci domyślnych, z których można przechwycić. Upewnij się, że w tym miejscu wybrano karty sieciowe.

2. Kliknij pozycję **Nowe przechwytywanie** w górnej części strony **początkowej** . Spowoduje to dodanie nowej karty obok karty Strona **początkowa** o nazwie **Capture 1**.
![Interfejs użytkownika netmona z wyróżnionymi przyciskami Nowe przechwytywanie, Uruchamianie i Zatrzymywanie.](../media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Aby wykonać proste przechwytywanie, kliknij przycisk **Start** na pasku narzędzi.

4. Odtwórz kroki, które stanowią problem z wydajnością.

5. Kliknij pozycję **Zatrzymaj** \> **zapisywanie pliku** \> **jako**. Pamiętaj, aby podać datę i godzinę ze strefą czasową i wspomnieć, czy pokazuje ona złą lub dobrą wydajność.

## <a name="httpwatch"></a>HTTPWatch

[Protokół HTTPWatch](https://www.httpwatch.com/download/) jest dostępny w wersji płatnej i bezpłatnej. Bezpłatna wersja Podstawowa obejmuje wszystko, czego potrzebujesz do tego testu. Protokół HTTPWatch monitoruje ruch sieciowy i czas ładowania strony bezpośrednio z okna przeglądarki. HTTPWatch to wtyczka do programu Internet Explorer, która graficznie opisuje wydajność. Analizę można zapisać i wyświetlić w programie HTTPWatch Studio.

> [!NOTE]
> Jeśli używasz innej przeglądarki, takiej jak Firefox, Google Chrome lub jeśli nie możesz zainstalować aplikacji HTTPWatch w programie Internet Explorer, otwórz nowe okno przeglądarki i naciśnij klawisz F12 na klawiaturze. W dolnej części przeglądarki powinno zostać wyświetlone okno podręczne Narzędzie dla deweloperów. Jeśli używasz opery, naciśnij klawisze CTRL+SHIFT+I dla narzędzia Web Inspector, a następnie kliknij kartę **Sieć** i zakończ testowanie opisane poniżej. Informacje będą nieco inne, ale czas ładowania będzie nadal wyświetlany w milisekundach. > HTTPWatch jest również bardzo przydatne w przypadku problemów z czasem ładowania stron SharePoint Online.

### <a name="run-httpwatch-and-reproduce-the-issue"></a>Uruchom narzędzie HTTPWatch i odtwórz problem

HttpWatch jest wtyczką przeglądarki, więc uwidacznianie narzędzia w przeglądarce jest nieco inne dla każdej wersji programu Internet Explorer. Zazwyczaj httpwatch można znaleźć na pasku poleceń w przeglądarce Internet Explorer. Jeśli w oknie przeglądarki nie widzisz wtyczki HTTPWatch, sprawdź wersję przeglądarki, klikając pozycję **Pomoc** \> **dotyczącą** lub w nowszych wersjach programu Internet Explorer, kliknij symbol koła zębatego i **pozycję Informacje o programie Internet Explorer**. Aby uruchomić pasek **Poleceń** , kliknij prawym przyciskiem myszy pasek menu w programie Internet Explorer i kliknij **pozycję Pasek poleceń**.

W przeszłości protokół HTTPWatch był skojarzony zarówno z poleceniami, jak i paskami Eksploratora, więc po zainstalowaniu, jeśli ikona (nawet po ponownym uruchomieniu) nie zostanie natychmiast wyświetlona, sprawdź **narzędzia** i paski narzędzi dla ikony. Należy pamiętać, że paski narzędzi można dostosowywać i dodawać do nich opcje.

![Pasek narzędzi polecenia programu Internet Explorer z wyświetloną ikoną HTTPWatch.](../media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)

1. Uruchom aplikację HTTPWatch w oknie przeglądarki Internet Explorer. Pojawi się zadokowany do przeglądarki w dolnej części tego okna. Kliknij **pozycję Rekord**.

2. Odtwórz dokładne kroki związane z problemem z wydajnością. Kliknij przycisk **Zatrzymaj** w usłudze HTTPWatch.

3. **Zapisz** element HTTPWatch lub **Wyślij pocztą e-mail**. Pamiętaj, aby nazwać plik tak, aby zawierał informacje o dacie i godzinie oraz wskazanie, czy zegarek zawiera pokaz dobrej lub złej wydajności.

![HttpWatch przedstawiający kartę Sieć dla ładowania strony Office 365 strony głównej.](../media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Ten zrzut ekranu pochodzi z Professional wersji protokołu HTTPWatch. Możesz otworzyć ślady pobrane w wersji podstawowej na komputerze z wersją Professional i odczytać je tam. Dodatkowe informacje mogą być dostępne ze śledzenia za pośrednictwem tej metody.

## <a name="problem-steps-recorder"></a>Rejestrator kroków problemu

Funkcja rejestrowania kroków lub PSR.exe umożliwia rejestrowanie problemów w miarę ich występowania. Jest to bardzo przydatne narzędzie i bardzo proste do uruchomienia.

### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Uruchom rejestrator kroków problemu (PSR.exe), aby zarejestrować swoją pracę

1. Użyj typu **Uruchamianie** \> **początkowe** \> **PSR.exe** \> **OK** lub kliknij **PSR.exe** \> typ **klucza** \> Windows, a następnie naciśnij klawisz ENTER.

2. Gdy pojawi się małe okno PSR.exe, kliknij przycisk **Rozpocznij rekord** i odtwórz kroki, które odtworzyć problem z wydajnością. W razie potrzeby możesz dodawać komentarze, klikając pozycję **Dodaj komentarze**.

3. Po wykonaniu kroków kliknij pozycję **Zatrzymaj rekord** . Jeśli problem z wydajnością to renderowanie strony, poczekaj na renderowanie strony przed zatrzymaniem nagrywania.

4. Kliknij **Zapisz**.

![Zrzut ekranu przedstawiający rejestrator kroków lub PSR.exe.](../media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)

Data i godzina są rejestrowane dla Ciebie. Spowoduje to połączenie usługi PSR ze śledzeniem netmona i protokołem HTTPWatch w czasie oraz pomaga w precyzyjnym rozwiązywaniu problemów. Data i godzina w rekordzie psr może pokazać, że minuta minęła między logowaniem i przeglądaniem adresu URL a częściowym renderowaniem witryny administracyjnej, na przykład.

## <a name="read-your-traces"></a>Odczytywanie śladów

Nie można nauczyć wszystkiego o rozwiązywaniu problemów z siecią i wydajnością, które ktoś musi znać za pośrednictwem artykułu. Uzyskanie dobrej wydajności wymaga doświadczenia i wiedzy o tym, jak działa sieć i zwykle działa. Można jednak zaokrąglić listę najważniejszych problemów i pokazać, w jaki sposób narzędzia mogą ułatwić wyeliminowanie najczęstszych problemów.

Jeśli chcesz zdobyć umiejętności czytania śladów sieci dla Office 365 witryn, nie ma lepszego nauczyciela niż regularne tworzenie śladów obciążeń stron i zdobywanie doświadczenia w ich czytaniu. Jeśli na przykład masz szansę, załaduj usługę Office 365 i prześledzić proces. Przefiltruj ślad dla ruchu DNS lub wyszukaj w usłudze FrameData nazwę przeglądanej usługi. Przeskanuj ślad, aby zapoznać się z krokami, które występują podczas ładowania usługi. Pomoże ci to dowiedzieć się, jak powinno wyglądać normalne ładowanie strony, a w przypadku rozwiązywania problemów, szczególnie w zakresie wydajności, porównanie dobrych i złych śladów może cię wiele nauczyć.

Narzędzie Netmon używa funkcji Microsoft Intellisense w polu Filtr wyświetlania. Funkcja Intellisense, czyli inteligentne uzupełnianie kodu, to ta sztuczka, w której wpisujesz kropkę, a wszystkie dostępne opcje są wyświetlane w polu wyboru listy rozwijanej. Jeśli na przykład martwisz się skalowaniem okien protokołu TCP, możesz znaleźć sposób na filtr (na przykład  `.protocol.tcp.window < 100`) w ten sposób.

![Zrzut ekranu przedstawiający narzędzie Netmon pokazujące, że pole Filtr wyświetlania używa funkcji intellisense.](../media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)

Ślady netmonów mogą mieć duży ruch. Jeśli nie masz doświadczenia w ich czytaniu, prawdopodobnie po raz pierwszy otworzysz ślad. Pierwszą rzeczą do zrobienia jest oddzielenie sygnału od szumu tła w śledzeniu. Przetestowano Office 365 i jest to ruch, który chcesz zobaczyć. Jeśli używasz do nawigowania po śladach, ta lista może nie być potrzebna.

Ruch między klientem a Office 365 odbywa się za pośrednictwem protokołu TLS, co oznacza, że treść ruchu zostanie zaszyfrowana i nie będzie można jej odczytać w ogólnym śladzie Netmon. Analiza wydajności nie musi znać szczegółów informacji zawartych w pakietze. Jest jednak bardzo zainteresowany nagłówkami pakietów i informacjami, które zawierają.

### <a name="tips-to-get-a-good-trace"></a>Wskazówki, aby uzyskać dobry ślad

- Poznaj wartość adresu IPv4 lub IPv6 komputera klienckiego. Możesz to uzyskać z wiersza polecenia, wpisując ciąg **IPConfig** , a następnie naciskając klawisz ENTER. Znajomość tego adresu pozwala szybko określić, czy ruch w śledzeniu bezpośrednio dotyczy komputera klienckiego. Jeśli istnieje znany serwer proxy, wyślij polecenie ping i pobierz jego adres IP.

- Opróżnij pamięć podręczną programu rozpoznawania nazw DNS i, jeśli to możliwe, zamknij wszystkie przeglądarki z wyjątkiem tej, w której są uruchamiane testy. Jeśli nie możesz tego zrobić, na przykład jeśli obsługa korzysta z narzędzia opartego na przeglądarce w celu wyświetlenia pulpitu komputera klienckiego, przygotuj się do filtrowania śledzenia.

- W zajętym śledzeniu znajdź używaną usługę Office 365. Jeśli ruch nigdy wcześniej nie był widoczny lub rzadko występował, jest to pomocny krok w oddzieleniu problemu z wydajnością od innego szumu sieciowego. Istnieje kilka sposobów, aby to zrobić. Bezpośrednio przed testem można użyć _polecenia ping_ lub _psping_ względem adresu URL określonej usługi (`ping outlook.office365.com` lub `psping -4 microsoft-my.sharepoint.com:443`, na przykład). Możesz również łatwo znaleźć ten polecenie ping lub PsPing w śledzeniu Netmon (według nazwy procesu). To da Ci miejsce, aby zacząć szukać.

Jeśli używasz śledzenia netmonów tylko w momencie wystąpienia problemu, to też jest w porządku. Aby zorientować się, użyj filtru, takiego jak `ContainsBin(FrameData, ASCII, "office")` lub `ContainsBin(FrameData, ASCII, "outlook")`. Numer ramki możesz zarejestrować z pliku śledzenia. Możesz również przewinąć _okienko Podsumowanie ramki_ w prawo i wyszukać kolumnę Identyfikator konwersacji. Istnieje liczba wskazana dla identyfikatora tej konkretnej konwersacji, którą można również zarejestrować i przyjrzeć się w izolacji później. Pamiętaj, aby usunąć ten filtr przed zastosowaniem innego filtrowania.

> [!TIP]
> Netmon ma wiele przydatnych wbudowanych filtrów. Spróbuj użyć przycisku **Załaduj filtr** w górnej części okienka _Filtr wyświetlania_ .

![Znajdź swój adres IP przy użyciu narzędzia PSPing w wierszu polecenia na komputerze klienckim.](../media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)

![Śledzenie netmona z klienta pokazujące to samo polecenie PSPing za pośrednictwem filtru TCP. Flags.Syn == 1.](../media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)

Zapoznaj się z ruchem i dowiedz się, jak zlokalizować potrzebne informacje. Na przykład dowiedz się, który pakiet w śledzeniu ma pierwsze odwołanie do używanej usługi Office 365 (na przykład "Outlook").

Biorąc Office 365 Outlook Online jako przykład, ruch zaczyna się mniej więcej tak:

- Standardowa kwerenda DNS i odpowiedź DNS dla outlook.office365.com z pasującymi identyfikatorami QueryID. Ważne jest, aby zanotować przesunięcie czasu dla tego zwrotu, a także miejsce, w którym na świecie Office 365 globalny system DNS wysyła żądanie rozpoznawania nazw. Najlepiej, jak to możliwe lokalnie, a nie w połowie drogi na całym świecie.

- Żądanie HTTP GET, którego raport o stanie został przeniesiony na stałe (301)

- Ruch RWS, w tym żądania Połączenie RWS i odpowiedzi Połączenie. (To jest zdalne winsock nawiązywanie połączenia dla Ciebie).

- Konwersacja TCP SYN i TCP SYN/ACK. Wiele ustawień w tej konwersacji ma wpływ na wydajność.

- Następnie odbywa się seria ruchu TLS:TLS, w którym odbywa się uzgadnianie protokołu TLS i konwersacje certyfikatów TLS. (Pamiętaj, że dane są szyfrowane za pośrednictwem protokołu SSL/TLS).

Wszystkie części ruchu są ważne i połączone, ale małe fragmenty śledzenia zawierają informacje szczególnie ważne pod względem rozwiązywania problemów z wydajnością, dlatego skupimy się na tych obszarach. Ponadto, ponieważ wykonaliśmy wystarczająco dużo Office 365 rozwiązywania problemów z wydajnością w firmie Microsoft, aby skompilować listę 10 najczęstszych problemów, skupimy się na tych problemach i sposobie korzystania z narzędzi, które musimy wykorzenić w następnej kolejności.

Jeśli nie zainstalowano ich wszystkich gotowych, poniższa macierz korzysta z kilku narzędzi. Tam, gdzie to możliwe. Linki są dostarczane do punktów instalacji. Lista zawiera typowe narzędzia do śledzenia sieci, takie jak [Netmon](https://www.microsoft.com/download/details.aspx?id=4865) i [Wireshark](https://www.wireshark.org/), ale używasz dowolnego narzędzia do śledzenia, z którymi masz doświadczenie i w którym jesteś przyzwyczajony do filtrowania ruchu sieciowego. Podczas testowania pamiętaj:

- *Zamknij przeglądarki i przetestuj tylko jedną uruchomioną przeglądarkę*  — spowoduje to zmniejszenie ogólnego ruchu przechwytywania. To sprawia, że jest mniej zajęty ślad.
- *Opróżnij pamięć podręczną rozpoznawania nazw DNS na komputerze klienckim*  — zapewni to czystą listwę po rozpoczęciu przechwytywania w celu czyszczenia śledzenia.

## <a name="common-issues"></a>Typowe problemy

Niektóre typowe problemy, z jakimi możesz się zmierzyć i jak je znaleźć w śladzie sieci.

### <a name="tcp-windows-scaling"></a>Skalowanie Windows TCP

Znaleziono w interfejsie SYN — SYN/ACK. Starszy lub starzejący się sprzęt może nie korzystać ze skalowania okien TCP.  Bez odpowiednich ustawień skalowania okien TCP domyślny bufor 16-bitowy w nagłówkach TCP wypełnia się w milisekundach.  Ruch nie może nadal wysyłać, dopóki klient nie otrzyma potwierdzenia, że oryginalne dane zostały odebrane, co powoduje opóźnienia.

#### <a name="tools"></a>Narzędzia

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Czego szukać

Wyszukaj ruch SYN — SYN/ACK w śledzeniu sieci.  W narzędziu Netmon użyj filtru takiego jak  `tcp.flags.syn == 1`. Ten filtr jest taki sam w programie Wireshark.

![Filtruj w programie Netmon lub Wireshark pod kątem pakietów syn dla obu narzędzi: TCP. Flags.Syn == 1.](../media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Zwróć uwagę, że dla każdego synu istnieje numer portu źródłowego (SrcPort) dopasowany do portu docelowego (DstPort) powiązanego potwierdzenia (SYN/ACK).

Aby wyświetlić Windows wartość skalowania używaną przez połączenie sieciowe, rozwiń najpierw węzeł SYN, a następnie powiązaną aplikację SYN/ACK.

![Grafika przedstawiająca, jak dopasować port SrcPort do elementu DstPort w śledzeniu, aby uzyskać różnicę czasu.](../media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)

### <a name="tcp-idle-time-settings"></a>Ustawienia czasu bezczynności protokołu TCP

W przeszłości większość sieci obwodowych jest konfigurowana pod kątem połączeń przejściowych, co oznacza, że bezczynne połączenia są zazwyczaj przerywane. Bezczynne sesje TCP mogą być przerywane przez serwery proxy i zapory w czasie większym niż 100–300 sekund. Jest to problematyczne dla Outlook Online, ponieważ tworzy i używa połączeń długoterminowych, niezależnie od tego, czy są bezczynne, czy nie.

Gdy połączenia są przerywane przez serwer proxy lub urządzenia zapory, klient nie jest informowany, a próba użycia Outlook Online oznacza, że komputer kliencki będzie wielokrotnie podejmował próbę ożywienia połączenia przed utworzeniem nowego. Podczas ładowania strony mogą wystąpić zawieszenia w produkcie, monity lub niska wydajność.

#### <a name="tools"></a>Narzędzia

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Czego szukać

W narzędziu Netmon przyjrzyj się polu Przesunięcie czasu dla rundy. Podróż w obie strony to czas między wysłaniem żądania do serwera przez klienta a odebraniem odpowiedzi. Sprawdź między klientem a punktem ruchu wychodzącego (np. Klient —\> serwer proxy) lub klient do Office 365 (klient —\> Office 365). Można to zobaczyć w wielu typach pakietów.

Na przykład filtr w narzędziu Netmon może wyglądać następująco:  `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`lub w programie Wireshark  `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.

> [!TIP]
> Nie wiesz, czy adres IP w śledzeniu należy do serwera DNS? Spróbuj wyszukać go w wierszu polecenia. Kliknij **przycisk Uruchom uruchom** \> \> **i wpisz** **cmd** lub naciśnij **klawisz Windows** \> i wpisz **cmd**. W wierszu polecenia wpisz  `nslookup <the IP address from the network trace>`. Aby przetestować, użyj polecenia nslookup względem adresu IP komputera. > Aby wyświetlić listę zakresów adresów IP firmy Microsoft, zobacz [Office 365 adresy URL i zakresy adresów IP](./urls-and-ip-address-ranges.md).

Jeśli wystąpi problem, spodziewaj się, że w tym przypadku (Outlook Online) pojawią się długie przesunięcia czasu, szczególnie w pakietach TLS:TLS, które pokazują fragment danych aplikacji (na przykład w usłudze Netmon można znaleźć pakiety danych aplikacji za pośrednictwem `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`usługi ). Powinien zostać wyświetlony płynny postęp w czasie całej sesji. Jeśli podczas odświeżania Outlook Online występują duże opóźnienia, może to być spowodowane wysokim stopniem wysyłania resetowania.

### <a name="latencyround-trip-time"></a>Opóźnienie/czas rundy podróży

Opóźnienie to miara, która może wiele zmienić w zależności od wielu zmiennych, takich jak uaktualnianie starzejących się urządzeń, dodawanie dużej liczby użytkowników do sieci oraz procent ogólnej przepustowości używanej przez inne zadania w połączeniu sieciowym.

Na tej stronie [Planowanie sieci i dostrajanie wydajności dla Office 365](network-planning-and-performance.md) dostępne są kalkulatory przepustowości dla Office 365.

Musisz zmierzyć szybkość połączenia lub przepustowość połączenia usługodawcy internetowego? Wypróbuj tę witrynę (lub witryny podobne do niej): [Speedtest Official Site](https://www.speedtest.net/) lub wyślij zapytanie do ulubionej wyszukiwarki w celu **sprawdzenia szybkości** frazy.

#### <a name="tools"></a>Narzędzia

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Czego szukać

Aby śledzić opóźnienie w śledzeniu, możesz zarejestrować adres IP komputera klienckiego i adres IP serwera DNS w Office 365. Jest to przeznaczone do łatwiejszego filtrowania śledzenia. Jeśli nawiążesz połączenie za pośrednictwem serwera proxy, będziesz potrzebować adresu IP komputera klienckiego, adresu IP serwera proxy/ruchu wychodzącego oraz Office 365 adresu IP DNS, aby ułatwić pracę.

Żądanie ping wysłane do outlook.office365.com poinformuje o nazwie centrum danych odbierającego żądanie, nawet jeśli polecenie ping  *może*  nie być w stanie nawiązać połączenia w celu wysłania kolejnych pakietów ICMP znaku towarowego. Jeśli używasz narzędzia PsPing (bezpłatne narzędzie do pobrania) i określonego portu (443) i być może do korzystania z protokołu IPv4 (-4), otrzymasz średni czas podróży w obie strony dla wysłanych pakietów. Będzie to działać w przypadku innych adresów URL w usługach Office 365, takich jak `psping -4 yourSite.sharepoint.com:443`. W rzeczywistości możesz określić liczbę poleceń ping, aby uzyskać większą próbkę dla średniej, spróbuj użyć czegoś takiego jak `psping -4 -n 20 yourSite-my.sharepoint.com:443`.

> [!NOTE]
> Narzędzie PsPing nie wysyła pakietów ICMP. Wysyła on polecenie ping z pakietami TCP na określonym porcie, dzięki czemu można użyć dowolnego z nich, o których wiesz, że jest otwarty. W Office 365, który używa protokołu SSL/TLS, spróbuj dołączyć port :443 do usługi PsPing.

![Zrzut ekranu przedstawiający outlook.office365.com rozpoznawania ping i psping z 443 robi to samo, ale również raportowania 6.5ms średniej RTT.](../media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Jeśli podczas wykonywania śledzenia sieci załadowano wolno działającą stronę Office 365, należy filtrować ślad Netmon lub Wireshark pod kątem `DNS`elementu . Jest to jeden z adresów IP, których szukamy.

Poniżej przedstawiono kroki, które należy wykonać, aby odfiltrować aplikację Netmon w celu uzyskania adresu IP (i przyjrzeć się opóźnieniu DNS). W tym przykładzie użyto outlook.office365.com, ale może również użyć adresu URL dzierżawy usługi SharePoint Online (na przykład hithere.sharepoint.com).

1. Wyślij polecenie ping do adresu URL `ping outlook.office365.com` i w wynikach zapisz nazwę i adres IP serwera DNS, do którego wysłano żądanie ping.
2. Śledzenie sieci otwierające stronę lub wykonujące akcję, która daje problem z wydajnością, lub, jeśli widzisz duże opóźnienie na poleceniu ping, sam w sobie, prześledzić go w sieci.
3. Otwórz ślad w narzędziu Netmon i odfiltruj wartość DNS (ten filtr działa również w programie Wireshark, ale jest wrażliwy na przypadek `-- dns`). Ponieważ znasz nazwę serwera DNS z polecenia ping, możesz również szybciej filtrować w usłudze Netmon w następujący sposób: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`, co wygląda tak w systemie Dns i ramce Wireshark zawiera ciąg "namnorthwest".<br/>Otwórz pakiet odpowiedzi, a następnie w oknie **Szczegóły ramki** Netmon kliknij pozycję **DNS** , aby rozwinąć, aby uzyskać więcej informacji. W informacjach DNS znajdziesz adres IP serwera DNS, na który żądanie trafiło w Office 365. Ten adres IP będzie potrzebny do następnego kroku (narzędzia PsPing). Usuń filtr, kliknij prawym przyciskiem myszy odpowiedź DNS w netmon (**Podsumowanie ramki** \> **Znajdź konwersacje** \> **DNS**), aby wyświetlić zapytanie DNS i odpowiedź obok siebie.
4. W narzędziu Netmon zwróć również uwagę na kolumnę Przesunięcie czasu między żądaniem DNS a odpowiedzią. W następnym kroku łatwe w instalacji i użyciu narzędzie [PsPing](/sysinternals/downloads/psping) jest bardzo przydatne, zarówno dlatego, że protokół ICMP jest często blokowany w zaporach, jak i dlatego, że PsPing elegancko śledzi opóźnienia w milisekundach. Usługa PsPing kończy połączenie TCP z adresem i portem (w naszym przypadku otwórz port 443).
5. Zainstaluj narzędzie PsPing.
6. Otwórz wiersz polecenia (uruchom \> \> polecenie cmd lub Windows Typ klucza \> cmd) i zmień katalog na katalog, w którym zainstalowano narzędzie PsPing, aby uruchomić polecenie PsPing. W moich przykładach widać, że zrobiłem folder "Perf" w katalogu głównym języka C. Możesz zrobić to samo, aby uzyskać szybki dostęp.
7. Wpisz polecenie , aby wykonać narzędzie PsPing względem adresu IP Office 365 serwera DNS z wcześniejszego śledzenia netmona, w tym numeru portu, takiego jak `psping -n 20 132.245.24.82:445`. Spowoduje to pobranie próbkowania 20 poleceń ping i średnie opóźnienie po zatrzymaniu narzędzia PsPing.

Jeśli zamierzasz Office 365 za pośrednictwem serwera proxy, kroki są nieco inne. Najpierw należy użyć polecenia PsPing do serwera proxy, aby uzyskać średnią wartość opóźnienia w milisekundach do serwera proxy/ruchu wychodzącego i z powrotem, a następnie uruchomić narzędzie PsPing na serwerze proxy lub na komputerze z bezpośrednim połączeniem internetowym w celu uzyskania brakujących wartości (tej, która ma Office 365 i z powrotem).

Jeśli zdecydujesz się uruchomić narzędzie PsPing z serwera proxy, będziesz mieć dwie wartości milisekund: komputer kliencki do serwera proxy lub punktu ruchu wychodzącego oraz serwer proxy do Office 365. I gotowe! Cóż, nagrywanie wartości, tak czy inaczej.

Jeśli uruchomisz narzędzie PsPing na innym komputerze klienckim, który ma bezpośrednie połączenie z Internetem, oznacza to, że bez serwera proxy będą dostępne dwie milisekundy: komputer kliencki do serwera proxy lub punkt ruchu wychodzącego oraz komputer kliencki do Office 365. W takim przypadku odejmij wartość komputera klienckiego do serwera proxy lub punktu ruchu wychodzącego od wartości komputera klienckiego do Office 365. Będziesz mieć numery RTT z komputera klienckiego do serwera proxy lub punktu ruchu wychodzącego oraz z serwera proxy lub punktu ruchu wychodzącego do Office 365.

Jeśli jednak możesz znaleźć komputer kliencki w lokalizacji, która jest bezpośrednio połączona lub pomija serwer proxy, możesz sprawdzić, czy problem zostanie odtworzony na początku, i przetestować użycie go później.

Opóźnienie, jak widać w śledzeniu netmona, te dodatkowe milisekundy mogą się sumować, jeśli w danej sesji jest ich wystarczająco dużo.

![Ogólne opóźnienie w programie Netmon z domyślną kolumną Delta czasu Netmon dodawaną do podsumowania ramki.](../media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> Adres IP może być inny niż adres IP pokazany w tym miejscu, na przykład polecenie ping może zwrócić wartość podobną do 157.56.0.0/16 lub podobny zakres. Aby uzyskać listę zakresów używanych przez Office 365, zapoznaj się [z Office 365 adresami URL i zakresami adresów IP](./urls-and-ip-address-ranges.md).

Pamiętaj, aby rozwinąć wszystkie węzły (u góry znajduje się przycisk), jeśli chcesz wyszukać, na przykład 132.245.

### <a name="proxy-authentication"></a>Uwierzytelnianie serwera proxy

Dotyczy to tylko wtedy, gdy przechodzisz przez serwer proxy. Jeśli nie, możesz pominąć te kroki. W przypadku prawidłowego działania uwierzytelnianie serwera proxy powinno odbywać się w milisekundach, spójnie. Nie powinna być widoczna sporadyczna zła wydajność w okresach szczytowego użycia (na przykład).

Jeśli uwierzytelnianie serwera proxy jest włączone, przy każdym nawiązaniu nowego połączenia TCP z Office 365 w celu uzyskania informacji należy przejść przez proces uwierzytelniania w tle. Na przykład podczas przełączania się z kalendarza na pocztę w Outlook Online nastąpi uwierzytelnienie. Natomiast w SharePoint Online, jeśli strona wyświetla nośnik lub dane z wielu witryn lub lokalizacji, uwierzytelnisz się dla każdego innego połączenia TCP, które jest wymagane do renderowania danych.

W usłudze Outlook Online mogą wystąpić wolne czasy ładowania za każdym razem, gdy przełączasz się między kalendarzem a skrzynką pocztową, lub powolne ładowanie strony w usłudze SharePoint Online. Istnieją jednak inne objawy, których nie wymieniono tutaj.

Uwierzytelnianie serwera proxy to ustawienie na serwerze proxy ruchu wychodzącego. Jeśli powoduje to problem z wydajnością Office 365, należy skonsultować się z zespołem ds. sieci.

#### <a name="tools"></a>Narzędzia

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Czego szukać

Uwierzytelnianie serwera proxy odbywa się za każdym razem, gdy należy wykonać nową sesję TCP, często w celu żądania plików lub informacji z serwera lub podania informacji. Na przykład może zostać wyświetlone uwierzytelnianie serwera proxy wokół żądań HTTP GET lub HTTP POST. Jeśli chcesz wyświetlić ramki, w których uwierzytelniasz żądania w śledzeniu, dodaj kolumnę "Podsumowanie NTLMSSP" do narzędzia Netmon i odfiltruj wartość .`.property.NTLMSSPSummary` Aby zobaczyć, jak długo trwa uwierzytelnianie, dodaj kolumnę Delta czasu.

Aby dodać kolumnę do programu Netmon:

1. Kliknij prawym przyciskiem myszy kolumnę, taką jak **Opis**.
2. Kliknij **pozycję Wybierz kolumny**.
3. Znajdź _pozycję Podsumowanie NTLMSSP_ i _różnicę czasu_ na liście, a następnie kliknij pozycję **Dodaj**.
4. Przenieś nowe kolumny na miejsce przed kolumną _Description_ lub za nią, aby można było je odczytać obok siebie.
5. Kliknij przycisk **OK**.

Nawet jeśli kolumna nie zostanie dodana, filtr Netmon będzie działać. Jednak rozwiązywanie problemów będzie znacznie łatwiejsze, jeśli zobaczysz, na jakim etapie uwierzytelniania się znajdujesz.

Podczas wyszukiwania wystąpień uwierzytelniania serwera proxy należy zapoznać się ze wszystkimi ramkami, w których występuje wyzwanie NTLM lub jest obecna wiadomość uwierzytelnienia. W razie potrzeby kliknij prawym przyciskiem myszy określony element ruchu i znajdź konwersacje \> TCP. Należy pamiętać o wartościach różnicy czasu w tych konwersacjach.

![Ślad netmonu przedstawiający uwierzytelnianie serwera proxy, filtrowane według konwersacji.](../media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

Czterosekundowe opóźnienie uwierzytelniania serwera proxy, jak pokazano w usłudze Wireshark. **Różnicę czasu z poprzedniej wyświetlonej kolumny ramki** wykonano, klikając prawym przyciskiem myszy pole o tej samej nazwie w szczegółach ramki i wybierając pozycję Dodaj jako kolumnę.  <br/> ![W programie Wireshark kolumnę "Delta czasu z poprzedniej wyświetlonej ramki" można wykonać, klikając prawym przyciskiem myszy pole o tej samej nazwie w szczegółach ramki i wybierając pozycję Dodaj jako kolumnę.](../media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>Wydajność dns

Rozpoznawanie nazw działa najlepiej i najszybciej, gdy odbywa się tak blisko kraju klienta, jak to możliwe.

Jeśli rozpoznawanie nazw DNS odbywa się za granicą, może dodać sekundy do ładowania stron. Najlepiej, aby rozpoznawanie nazw odbywało się w obszarze poniżej 100 ms. Jeśli nie, należy przeprowadzić dalsze badania.

> [!TIP]
> Nie wiesz, jak działa łączność klienta w Office 365? Zapoznaj się z dokumentem Dokumentacja łączności klienta [tutaj](/previous-versions//dn741250(v=technet.10)).

#### <a name="tools"></a>Narzędzia

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Czego szukać

Analizowanie wydajności DNS to zazwyczaj inne zadanie śledzenia sieci. Jednak PsPing jest również pomocne w orzeczeniu w lub na zewnątrz, możliwą przyczyną.

Ruch DNS jest oparty na żądaniach TCP i UDP, a odpowiedzi są wyraźnie oznaczone identyfikatorem, który pomoże dopasować określone żądanie do jego konkretnej odpowiedzi. Ruch DNS będzie widoczny, gdy na przykład SharePoint Online używa nazwy sieci lub adresu URL na stronie internetowej. Zgodnie z regułą większość tego ruchu, z wyjątkiem przenoszenia stref, jest uruchamiana za pośrednictwem protokołu UDP.

W systemach Netmon i Wireshark najbardziej podstawowym filtrem, który umożliwia przyjrzenie się ruchowi DNS, jest po prostu `dns`. Pamiętaj, aby używać małych liter podczas określania filtru. Pamiętaj, aby opróżnić pamięć podręczną programu rozpoznawania nazw DNS przed rozpoczęciem odtwarzania problemu na komputerze klienckim. Jeśli na przykład masz powolne ładowanie strony SharePoint Online dla strony głównej, zamknij wszystkie przeglądarki, otwórz nową przeglądarkę, rozpocznij śledzenie, opróżnij pamięć podręczną programu rozpoznawania nazw DNS i przejdź do witryny usługi SharePoint Online. Po rozpoznaniu całej strony należy zatrzymać i zapisać ślad.

![Podstawowym filtrem dla systemu DNS w programie Netmon jest system DNS.](../media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

W tym miejscu chcesz przyjrzeć się przesunięciu czasu. Warto dodać kolumnę **Delta czasu** do narzędzia Netmon, co można wykonać, wykonując następujące kroki:

1. Kliknij prawym przyciskiem myszy kolumnę, taką jak **Opis**.
2. Kliknij **pozycję Wybierz kolumny**.
3. Znajdź pozycję _Delta czasu_ na liście i kliknij pozycję **Dodaj**.
4. Przenieś nową kolumnę na miejsce przed kolumną _Description_ lub za nią, aby można było ją odczytać obok siebie.
5. Kliknij przycisk **OK**.

Jeśli znajdziesz interesujące zapytanie, rozważ odizolowanie go, klikając je prawym przyciskiem myszy w panelu szczegółów ramki, wybierając pozycję **Znajdź konwersacje** \> **DNS**. Zwróć uwagę, że panel Konwersacje sieciowe przechodzi bezpośrednio do konkretnej konwersacji w dzienniku ruchu UDP.

![Śledzenie netmona obciążenia usługi Outlook Online filtrowane według systemu DNS i używanie funkcji Znajdź konwersacje, a następnie systemu DNS, aby zawęzić wyniki.](../media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

W programie Wireshark możesz utworzyć kolumnę dla czasu DNS. Prześlij swój ślad (lub otwórz ślad) w programie Wireshark i przefiltruj według `dns`, lub, co bardziej przydatne,  `dns.time`. Kliknij dowolne zapytanie DNS, a w panelu zawierającym szczegóły rozwiń  `Domain Name System (response)` szczegóły. Zobaczysz pole na czas (na przykład `[Time: 0.001111100 seconds]`. Kliknij prawym przyciskiem myszy tę godzinę i wybierz pozycję **Zastosuj jako kolumnę**. Dzięki temu uzyskasz kolumnę **Czas** na potrzeby szybszego sortowania śledzenia. Kliknij nową kolumnę, aby posortować według wartości malejących, aby zobaczyć, które wywołanie DNS trwało najdłużej.

[Przeglądanie SharePoint Online filtrowane w usłudze Wireshark według (małych liter) dns.time z czasem od szczegółów w kolumnie i posortowanymi rosnąco.](../media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Jeśli chcesz zrobić więcej badania czasu rozpoznawania DNS, spróbuj PsPing względem portu DNS używanego przez TCP (na przykład  `psping <IP address of DNS server>:53`) . Czy nadal występuje problem z wydajnością? Jeśli to zrobisz, problem jest bardziej prawdopodobne, aby być szerszy problem z siecią niż problem konkretnej aplikacji DNS, którą osiągasz, aby rozwiązać. Warto również wspomnieć, że polecenie ping do outlook.office365.com poinformuje, gdzie odbywa się rozpoznawanie nazw DNS dla usługi Outlook Online (na przykład outlook-namnorthwest.office365.com).

Jeśli problem wygląda na specyficzny dla systemu DNS, może być konieczne skontaktowanie się z działem IT w celu przyjrzenia się konfiguracjom DNS i usługom przesyłania dalej DNS w celu dalszego zbadania tego problemu.

### <a name="proxy-scalability"></a>Skalowalność serwera proxy

Usługi takie jak Outlook Online w Office 365 udzielają klientom wielu połączeń długoterminowych. W związku z tym każdy użytkownik może korzystać z większej liczby połączeń, które wymagają dłuższego okresu życia.

#### <a name="tools"></a>Narzędzia

Matematyki

#### <a name="what-to-look-for"></a>Czego szukać

Nie ma konkretnego narzędzia do śledzenia sieci ani rozwiązywania problemów. Zamiast tego jest ona oparta na obliczeniach przepustowości podanych ograniczeń i innych zmiennych.

### <a name="tcp-max-segment-size"></a>Maksymalny rozmiar segmentu TCP

Znaleziono w interfejsie SYN — SYN/ACK.  Należy to sprawdzić w dowolnym śladzie sieci wydajności wykonanym w celu upewnienia się, że pakiety TCP są skonfigurowane do przenoszenia maksymalnej możliwej ilości danych.

Celem jest wyświetlenie mss 1460 bajtów do transmisji danych. Jeśli jesteś za serwerem proxy lub używasz translatora adresów sieciowych, pamiętaj, aby uruchomić ten test z klienta do serwera proxy/ruchu wychodzącego/NAT i od serwera proxy/ruchu wychodzącego/TRANSLATOR do Office 365 w celu uzyskiwania najlepszych wyników! Są to różne sesje TCP.

#### <a name="tools"></a>Narzędzia

Netmon

#### <a name="what-to-look-for"></a>Czego szukać

Maksymalny rozmiar segmentu TCP (MSS) to kolejny parametr uzgadniania trójstopniowego w śledzenia sieci, co oznacza, że znajdziesz dane potrzebne w pakietach SYN — SYN/ACK. Mss jest rzeczywiście dość proste, aby zobaczyć.

Otwórz dowolny ślad sieci wydajności i znajdź połączenie, które Cię interesuje lub które pokazuje problem z wydajnością.

> [!NOTE]
> Jeśli szukasz śledzenia i musisz znaleźć ruch odpowiedni dla konwersacji, przefiltruj według adresu IP klienta, adresu IP serwera proxy lub punktu ruchu wychodzącego lub obu tych elementów. Przechodząc bezpośrednio, należy wysłać polecenie ping do adresu URL, który testujesz pod kątem adresu IP Office 365 w śledzeniu, i filtrować według niego.

Patrząc na ślad z drugiej ręki? Spróbuj użyć filtrów, aby zorientować się. W programie Netmon uruchom wyszukiwanie na podstawie adresu URL, takiego jak `Containsbin(framedata, ascii, "sphybridExample")`, zanotuj numer ramki.

W programie Wireshark użyj czegoś takiego jak  `frame contains "sphybridExample"`. Jeśli zauważysz, że odnaleziono ruch zdalnego protokołu Winsock (RWS) (może on być wyświetlany jako [PSH, ACK] w programie Wireshark), pamiętaj, że połączenia RWS można zobaczyć na krótko przed odpowiednimi zestawami SYN — SYN/ACK, jak wspomniano wcześniej.

W tym momencie możesz zarejestrować numer ramki, usunąć filtr, kliknąć pozycję **Cały ruch** w oknie Konwersacje sieciowe w usłudze Netmon, aby przyjrzeć się najbliższemu interfejsowi SYN.

Co ważne, jeśli w czasie śledzenia nie otrzymano żadnych informacji o adresie IP, znalezienie adresu URL w śledzeniu (na przykład w `sphybridExample-my.sharepoint.com`części ,) umożliwi filtrowanie adresów IP.

Znajdź połączenie w śladzie, który Cię interesuje. Można to zrobić, skanując ślad, filtrując według adresów IP lub wybierając określone identyfikatory konwersacji przy użyciu okna Konwersacje sieciowe w usłudze Netmon. Po znalezieniu pakietu SYN rozwiń węzeł TCP (w narzędziu Netmon) lub Protokół kontroli transmisji (w narzędziu Wireshark) w panelu Szczegóły ramki. Rozwiń pozycje Opcje TCP i MaxSegmentSize. Znajdź powiązaną ramkę SYN-ACK i rozwiń pozycje Opcje TCP i MaxSegmentSize. Mniejsza z tych dwóch wartości będzie maksymalny rozmiar segmentu. Na tym obrazie używam wbudowanej kolumny w narzędziu Netmon o nazwie Rozwiązywanie problemów z protokołem TCP.

![Ślad sieci filtrowany w usłudze Netmon przy użyciu wbudowanych kolumn.](../media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

Wbudowana kolumna znajduje się w górnej części panelu **Szczegóły ramki** . (Aby wrócić do normalnego widoku, kliknij ponownie pozycję **Kolumny** , a następnie wybierz pozycję **Strefa czasowa**).

![Gdzie znaleźć listę rozwijaną Kolumny dla opcji Rozwiązywanie problemów z protokołem TCP (na początku podsumowania ramki).](../media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

Oto przefiltrowany ślad w programie Wireshark. Istnieje filtr specyficzny dla wartości MSS (`tcp.options.mss`). Ramki uzgadniania SYN, SYN/ACK, ACK są połączone w dolnej części narzędzia Wireshark równoważne szczegółom ramki (więc ramka 47 ACK, linki do 46 SYN/ACK, linki do 43 SYN), aby ułatwić tego rodzaju pracę.

![Śledzenie przefiltrowane w programie Wireshark według pliku tcp.options.mss dla opcji Maksymalny rozmiar segmentu (MSS).](../media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

Jeśli chcesz sprawdzić **potwierdzenie selektywne** (następny temat w tej macierzy), nie zamykaj śladu!

### <a name="selective-acknowledgment"></a>Potwierdzenie selektywne

Znaleziono w interfejsie SYN — SYN/ACK. Musi być zgłaszane jako dozwolone zarówno w syn i SYN/ACK. Potwierdzenie selektywne (SACK) umożliwia płynniejsze ponowne przekazywanie danych w przypadku braku pakietu lub pakietów. Urządzenia mogą wyłączyć tę funkcję, co może prowadzić do problemów z wydajnością.

Jeśli jesteś za serwerem proxy lub używasz translatora adresów sieciowych, pamiętaj, aby uruchomić ten test z klienta do serwera proxy/ruchu wychodzącego/NAT i od serwera proxy/ruchu wychodzącego/TRANSLATOR do Office 365 w celu uzyskiwania najlepszych wyników! Są to różne sesje TCP.

#### <a name="tools"></a>Narzędzia

Netmon

#### <a name="what-to-look-for"></a>Czego szukać

Potwierdzenie selektywne (SACK) to kolejny parametr uzgadniania SYN-SYN/ACK. Ślad można filtrować na wiele sposobów: SYN — SYN/ACK.

Znajdź połączenie w śladzie, który Cię interesuje, skanując ślad, filtrując według adresów IP lub klikając identyfikator konwersacji przy użyciu okna Konwersacje sieciowe w usłudze Netmon. Po znalezieniu pakietu SYN rozwiń węzeł TCP w narzędziu Netmon lub protokół kontroli transmisji w programie Wireshark w sekcji Szczegóły ramki. Rozwiń pozycję Opcje TCP, a następnie pozycję SACK. Znajdź powiązaną ramkę SYN-ACK i rozwiń pozycję Opcje TCP i jej pole SACK. Upewnij się, że w systemie SYN i SYN/ACK jest dozwolony plik SACK. Poniżej przedstawiono wartości SACK widoczne zarówno w platformie Netmon, jak i w narzędziu Wireshark.

![Potwierdzenie selektywne (SACK) w narzędziu Netmon w wyniku tcp.flags.syn == 1.](../media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![SACK jak widać w wireshark z filtrem tcp.flags.syn == 1.](../media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>Geolokalizacja DNS

Gdzie na świecie Office 365 próbuje rozpoznać efekty wywołania DNS, szybkość połączenia.

W usłudze Outlook Online po zakończeniu pierwszego wyszukiwania DNS lokalizacja tego systemu DNS zostanie użyta do nawiązania połączenia z najbliższym centrum danych. Nastąpi połączenie z serwerem CAS usługi Outlook Online, który będzie używać sieci szkieletowej do nawiązywania połączenia z centrum danych (dC), w którym przechowywane są dane. Jest to szybsze.

Podczas uzyskiwania dostępu do usługi SharePoint Online użytkownik podróżujący za granicę zostanie skierowany do aktywnego centrum danych — to jest dC, którego lokalizacja jest oparta na bazie głównej dzierżawy spo (tak więc dC w USA, jeśli użytkownik ma siedzibę w USA).

Usługa Lync Online ma aktywne węzły w więcej niż jednym dC naraz. Gdy żądania są wysyłane dla wystąpień online programu Lync, system DNS firmy Microsoft określi, skąd na świecie pochodzi żądanie, i zwróci adresy IP z najbliższego regionalnego kontrolera dC, z którego jest aktywny program Lync Online.

> [!TIP]
> Chcesz dowiedzieć się więcej o tym, jak klienci łączą się z Office 365? Zapoznaj się z artykułem Dotyczącym [łączności klienta](/previous-versions//dn741250(v=technet.10)) (i jego przydatną grafiką).

#### <a name="tools"></a>Narzędzia

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Czego szukać

Żądania rozpoznawania nazw z serwerów DNS klienta do serwerów DNS firmy Microsoft powinny w większości przypadków spowodować zwrócenie adresu IP regionalnego centrum danych (dC) przez usługę Microsoft DNS. Co to oznacza dla Ciebie? Jeśli twoja siedziba znajduje się w Bangalore w Indiach, ale podróżujesz w Stany Zjednoczone, gdy przeglądarka wysyła żądanie Outlook Online, serwery DNS firmy Microsoft powinny przekazywać adresy IP do centrów danych w Stany Zjednoczone — regionalnym centrum danych. Jeśli poczta jest potrzebna z Outlook, dane te będą przesyłane przez sieć szybkiej sieci szkieletowej firmy Microsoft między centrami danych.

System DNS działa najszybciej, gdy rozpoznawanie nazw odbywa się tak blisko lokalizacji użytkownika, jak to możliwe. Jeśli jesteś w Europie, chcesz przejść do usługi Microsoft DNS w Europie i (najlepiej) zająć się centrum danych w Europie. Wydajność klienta w Europie przechodzącego do systemu DNS i centrum danych w Ameryce będzie wolniejsza.

Uruchom narzędzie ping względem outlook.office365.com, aby określić, gdzie na świecie jest kierowane żądanie DNS. Jeśli jesteś w Europie, powinieneś zobaczyć odpowiedź z czegoś takiego jak outlook-emeawest.office365.com. W Obu Amerykach spodziewaj się czegoś takiego jak outlook-namnorthwest.office365.com.

Otwórz wiersz polecenia na komputerze klienckim (za pośrednictwem polecenia cmd uruchamiania \> uruchamiania \> lub Windows \> klucza cmd). Wpisz polecenie ping outlook.office365.com i naciśnij klawisz ENTER. Pamiętaj, aby określić wartość -4, jeśli chcesz określić polecenie ping za pośrednictwem protokołu IPv4. Uzyskanie odpowiedzi z pakietów ICMP może zakończyć się niepowodzeniem, ale powinna zostać wyświetlona nazwa DNS, do której zostało przekierowane żądanie. Jeśli chcesz zobaczyć numery opóźnień dla tego połączenia, spróbuj użyć narzędzia PsPing do adresu IP serwera, który jest zwracany przez polecenie ping.

![Polecenie ping outlook.office365.com pokazujące rozdzielczość w programie outlook-namnorthwest.](../media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![PsPing do adresu IP zwróconego przez polecenie ping do outlook.office365.com pokazujące średnie opóźnienie 28 milisekund.](../media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Rozwiązywanie problemów z aplikacją Office 365

#### <a name="tools"></a>Narzędzia

- Netmon
- HTTPWatch
- Konsola F12 w przeglądarce

W tym artykule dotyczącym sieci nie opisano narzędzi używanych w rozwiązywaniu problemów specyficznych dla aplikacji. Na [tej stronie](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848) znajdziesz jednak zasoby, których *możesz* użyć.

## <a name="related-topics"></a>Tematy pokrewne

[Zarządzanie punktami końcowymi usługi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 punktów końcowych — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)