---
title: Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 07/08/2021
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
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
ms.collection:
- M365-security-compliance
- Ent_O365
- SPO_Content
description: Dowiedz się, jak sprawdzić historię połączeń z komputerem klienckim, aby ułatwić wczesne wykrywanie pojawiających się problemów.
ms.openlocfilehash: ceb56f88d057d3a003f158369c9d35223852c7fa
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100440"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności

Istnieje kilka prostych sposobów sprawdzania wydajności połączeń między Office 365 a firmą, które pozwolą ustalić przybliżony punkt odniesienia łączności. Znajomość historii wydajności połączeń z komputerem klienckim może pomóc w wczesnym wykrywaniu pojawiających się problemów, identyfikowaniu i przewidywaniu problemów.
  
Jeśli nie pracujesz nad problemami z wydajnością, ten artykuł ma na celu ułatwienie rozważenia niektórych typowych pytań. Skąd wiesz, że problem, który widzisz, to problem z wydajnością, a nie zdarzenie usługi Office 365? Jak zaplanować dobrą wydajność, długoterminową? Jak można mieć oko na wydajność? Jeśli twój zespół lub klienci widzą niską wydajność podczas korzystania z Office 365 i zastanawiasz się nad dowolnym z tych pytań, przeczytaj dalej.
  
> [!IMPORTANT]
> **Czy masz teraz problem z wydajnością między klientem a Office 365?** Wykonaj kroki opisane w [planie rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Coś, co należy wiedzieć o wydajności Office 365

Office 365 znajduje się w dedykowanej sieci firmy Microsoft o wysokiej pojemności, która jest monitorowana przez automatyzację i prawdziwych ludzi. Częścią utrzymania chmury Office 365 jest dostrajanie wydajności i usprawnianie tam, gdzie to możliwe. Ponieważ klienci chmury Office 365 muszą łączyć się przez Internet, trwają prace nad dostosowaniem wydajności również w usługach Office 365.

Ulepszenia wydajności nigdy nie kończą się w chmurze, więc nie ma doświadczenia w utrzymywaniu dobrej kondycji i szybkiego działania chmury. Jeśli masz problem z wydajnością podczas nawiązywania połączenia z lokalizacją do Office 365, najlepiej nie zaczynać od zgłoszenia pomocy technicznej ani czekać na nie. Zamiast tego należy rozpocząć badanie problemu od "wewnątrz". Oznacza to, że zacznij wewnątrz sieci i wypracuj wyjście do Office 365. Przed otwarciem sprawy z pomocą techniczną możesz zebrać dane i podjąć działania, które będą badać i rozwiązywać ten problem.
  
> [!IMPORTANT]
> Należy pamiętać o planowaniu pojemności i limitach w Office 365. Te informacje spoczą cię przed krzywą podczas próby rozwiązania problemu z wydajnością. Oto link do [opisów usług Microsoft 365 i Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Jest to centrum centralne, a wszystkie usługi oferowane przez Office 365 mają link do własnych opisów usług. Oznacza to, że jeśli na przykład musisz wyświetlić standardowe limity dla usługi SharePoint Online, kliknij pozycję [SharePoint Opis usługi online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description) i znajdź jej [sekcję SharePoint Limity online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).
  
Upewnij się, że przejdziesz do rozwiązywania problemów ze zrozumieniem, że wydajność jest skalą przesuwną. Nie chodzi o osiągnięcie wyidealizowanej wartości i utrzymanie jej na stałe. Sporadyczne zadania o wysokiej przepustowości, takie jak dołączanie dużej liczby użytkowników lub przeprowadzanie dużych migracji danych, będą stresujące, więc *zaplanuj* wpływ na wydajność. Należy mieć przybliżone pojęcie o celach wydajności, ale wiele zmiennych odgrywa rolę w wydajności, więc wydajność jest różna.
  
Rozwiązywanie problemów z wydajnością nie polega na spełnianiu określonych celów i utrzymywaniu tych liczb przez czas nieokreślony, ale na ulepszaniu istniejących działań, biorąc pod uwagę wszystkie zmienne. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>Jak wygląda problem z wydajnością?

Najpierw należy się upewnić, że problem z wydajnością, a nie zdarzenie usługi, jest rzeczywiście problemem z wydajnością. Problem z wydajnością różni się od zdarzenia usługi w Office 365. Oto jak je odróżnić.
  
Zdarzenia usługi występują, gdy sama usługa Office 365 ma problemy. W obszarze **Bieżąca kondycja** w Centrum administracyjne platformy Microsoft 365 mogą zostać wyświetlone czerwone lub żółte ikony. Możesz zauważyć, że wydajność na komputerach klienckich łączących się z Office 365 działa wolno. Jeśli na przykład funkcja Bieżąca kondycja zgłasza czerwoną ikonę i zobaczysz pozycję **Badanie** obok Exchange, możesz również otrzymywać połączenia od osób w organizacji, które skarżą się, że skrzynki pocztowe klientów korzystające z Exchange Online działają wolno. W takim przypadku uzasadnione jest założenie, że wydajność Exchange Online była ofiarą problemów z usługą.
  
![Pulpit nawigacyjny Office 365 Health ze wszystkimi obciążeniami wyświetlanymi na zielono, z wyjątkiem Exchange, który pokazuje przywróconą usługę.](../media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
W tym momencie ty, administrator Office 365, powinieneś sprawdzić **bieżącą kondycję**, a następnie często **wyświetlać szczegóły i historię**, aby być na bieżąco z konserwacją systemu. Na pulpicie nawigacyjnym **Bieżąca kondycja** wprowadzono aktualizację dotyczącą zmian w usłudze i problemów z usługą. Notatki i wyjaśnienia zapisane w historii kondycji, administrator do administratora, są tam, aby pomóc ocenić i zachować publikowane o bieżącej pracy.
  
![Obraz pulpitu nawigacyjnego kondycji Office 365 wyjaśniający, że usługa Exchange Online została przywrócona i dlaczego.](../media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Problem z wydajnością nie jest zdarzeniem usługi, mimo że zdarzenia mogą powodować niską wydajność. Problem z wydajnością wygląda następująco:
  
- Problem z wydajnością występuje niezależnie od tego, co centrum administracyjne Raport bieżącej **kondycji** dla usługi.
    
-  Działanie używane do przepływu zajmuje dużo czasu lub nigdy się nie kończy.
    
- Możesz również zreplikować problem lub wiedzieć, że wystąpi, jeśli wykonasz właściwą serię kroków.
    
-  Jeśli problem występuje sporadycznie, nadal może istnieć wzorzec. Na przykład wiesz, że do 10:00 będziesz mieć połączenia od użytkowników, którzy nie zawsze mają dostęp do Office 365. Połączenia zakończą się około południa.
    
Ta lista prawdopodobnie brzmi znajomo; może zbyt znajome. Gdy już wiesz, że jest to problem z wydajnością, pytanie brzmi: "Co zrobić dalej?" Dalsza część tego artykułu pomaga dokładnie to określić.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Jak zdefiniować i przetestować problem z wydajnością

Problemy z wydajnością często pojawiają się w czasie, więc zdefiniowanie rzeczywistego problemu może być trudne. Utwórz dobrą instrukcję problemu z dobrym pomysłem na kontekst problemu, a następnie musisz wykonać powtarzalne kroki testowania. Oto kilka przykładów instrukcji problemów, które nie zawierają wystarczających informacji:
  
- Przejście z skrzynki odbiorczej do kalendarza było czymś, czego nie zauważyłem, a teraz jest to przerwa na kawę. Czy możesz sprawić, by działał tak, jak kiedyś?
    
- Przekazywanie plików do usługi SharePoint Online trwa wiecznie. Dlaczego jest wolno po południu, ale za każdym razem, to szybko? Czy to nie może być po prostu szybkie?
    
Istnieje kilka dużych wyzwań, przed którymi stoją powyższe oświadczenia dotyczące problemów. W szczególności zbyt wiele niejasności, z których można sobie poradzić. Przykład:
  
- Nie jest jasne, jak przełączanie się między skrzynką odbiorczą a kalendarzem działało na laptopie.
    
- Gdy użytkownik mówi: "Nie można po prostu być szybko", co to jest "szybkie"?
    
- Jak długo jest "na zawsze"? Czy to kilka sekund? Albo wiele minut? A może użytkownik może zjeść lunch, a akcja zakończy się 10 minut po powrocie?
    
Administrator i narzędzie do rozwiązywania problemów nie mogą znać *szczegółów* problemu z ogólnych instrukcji, takich jak te. Na przykład nie wiedzą, kiedy problem zaczął występować. Narzędzie do rozwiązywania problemów może nie wiedzieć, że użytkownik działa z domu i tylko zawsze widzi powolne przełączanie w sieci domowej. Lub że użytkownik uruchamia inne aplikacje intensywnie korzystające z pamięci RAM na kliencie lokalnym. Administratorzy mogą nie wiedzieć, że użytkownik korzysta ze starszego systemu operacyjnego lub nie uruchamiał ostatnich aktualizacji.
  
Gdy użytkownicy zgłaszają problem z wydajnością, istnieje wiele informacji do zebrania. Pobieranie i rejestrowanie informacji jest nazywane określeniem zakresu problemu. Oto podstawowa lista określająca zakres, za pomocą których można zbierać informacje o problemach z wydajnością. Ta lista nie jest wyczerpująca, ale jest to miejsce do rozpoczęcia:
  
- W jakiej dacie wystąpił problem i o jakiej porze dnia lub nocy?
    
- Jakiego rodzaju komputera klienckiego używasz i jak łączy się z siecią biznesową (SIECI VPN, Przewodowe, Bezprzewodowe)?
    
- Czy pracowałeś zdalnie, czy byłeś w biurze?
    
- Czy próbujesz wykonać te same akcje na innym komputerze i widzisz to samo zachowanie?
    
- Przejrzyj kroki, które dają ci kłopoty, aby można było napisać akcje, które podejmujesz.
    
- Jak niska jest wydajność w sekundach lub minutach?
    
- Gdzie się znajdujesz na świecie?
    
Niektóre z tych pytań są bardziej oczywiste niż inne. Większość użytkowników zrozumie, że narzędzie do rozwiązywania problemów wymaga dokładnych kroków, aby odtworzyć problem. Po tym wszystkim, jak inaczej można zarejestrować, co jest nie tak, i jak inaczej można przetestować, czy problem został rozwiązany? Mniej oczywiste są takie rzeczy jak "Jaka data i godzina widzisz problem?", i "Gdzie na świecie się znajdujesz?", informacje, które mogą być używane w parze. W zależności od tego, kiedy użytkownik pracował, kilka godzin różnicy czasu może oznaczać, że konserwacja części sieci firmy jest już w toku. Na przykład twoja firma ma implementację hybrydową, taką jak hybrydowa SharePoint Search, która może wykonywać zapytania dotyczące indeksów wyszukiwania zarówno w usłudze SharePoint Online, jak i w lokalnym wystąpieniu SharePoint Server 2013, aktualizacje mogą być w toku w farmie lokalnej. Jeśli twoja firma znajduje się w chmurze, konserwacja systemu może obejmować dodawanie lub usuwanie sprzętu sieciowego, wprowadzanie aktualizacji w całej firmie lub wprowadzanie zmian w systemie DNS lub innej infrastrukturze podstawowej.
  
Kiedy rozwiązujesz problem z wydajnością, jest to trochę jak miejsce zbrodni, musisz być precyzyjny i uważny, aby wyciągnąć jakiekolwiek wnioski z dowodów. Aby to zrobić, musisz uzyskać dobre oświadczenie o problemie, zbierając dowody. Powinien on zawierać kontekst komputera, kontekst użytkownika, czas rozpoczęcia problemu oraz dokładne kroki, które ujawniły problem z wydajnością. Ta instrukcja problemu powinna być i pozostać najwyższą stroną w notatkach. Przechodząc ponownie przez instrukcję problemu po pracy nad rozwiązaniem, podejmujesz kroki, aby przetestować i udowodnić, czy wykonywane akcje rozwiązały problem. Ma to kluczowe znaczenie dla wiedzy o tym, kiedy twoja praca jest wykonywana.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Czy wiesz, jak wydajność była używana do wyświetlania, gdy była dobra?

Jeśli masz pecha, nikt nie wie. Nikt nie miał liczb. Oznacza to, że nikt nie może odpowiedzieć na proste pytanie "Ile sekund zajęło wyświetlenie skrzynki odbiorczej w Office 365?" lub "Jak długo trwało to, gdy kierownictwo miało spotkanie w usłudze Lync Online?", co jest typowym scenariuszem dla wielu firm.
  
Czego tu brakuje, to punkt odniesienia wydajności?
  
Punkty odniesienia zapewniają kontekst dla twojej wydajności. W zależności od potrzeb firmy należy czasami często stosować punkt odniesienia. Jeśli jesteś większą firmą, twój zespół ds. operacji może już przyjmować punkty odniesienia dla środowiska lokalnego. Jeśli na przykład poprawisz wszystkie serwery Exchange w pierwszy poniedziałek miesiąca i wszystkie serwery SharePoint w trzeci poniedziałek, zespół ds. operacji prawdopodobnie ma listę zadań i scenariuszy uruchamianych po poprawce, aby udowodnić, że funkcje krytyczne działają. Na przykład otwarcie skrzynki odbiorczej, kliknięcie pozycji Wyślij/Odbierz i upewnienie się, że foldery zostały zaktualizowane lub w SharePoint przeglądanie strony głównej witryny, przechodzenie do strony wyszukiwania w przedsiębiorstwie i wykonywanie wyszukiwania zwracającego wyniki.
  
Jeśli aplikacje znajdują się w Office 365, niektóre z najbardziej podstawowych punktów odniesienia można zmierzyć czas (w milisekundach) z komputera klienckiego wewnątrz sieci, do punktu ruchu wychodzącego lub punktu, w którym opuszczasz sieć i wychodzisz do Office 365. Poniżej przedstawiono kilka przydatnych punktów odniesienia, które można zbadać i zarejestrować:
  
- Zidentyfikuj urządzenia między komputerem klienckim a punktem ruchu wychodzącego, na przykład serwer proxy.
    
  - Musisz znać swoje urządzenia, aby mieć kontekst (adresy IP, typ urządzenia, et cetera) dla pojawiających się problemów z wydajnością.
    
  - Serwery proxy są typowymi punktami ruchu wychodzącego, więc możesz sprawdzić przeglądarkę internetową, aby sprawdzić, jakiego serwera proxy ma używać, jeśli istnieje.
    
  - Istnieją narzędzia innych firm, które mogą odnajdywać i mapować sieć, ale najbezpieczniejszym sposobem na poznanie urządzeń jest poproszenie członka zespołu sieciowego.
    
- Zidentyfikuj dostawcę usług internetowych (ISP), zapisz swoje informacje kontaktowe i zapytaj, ile obwodów masz przepustowości.
    
- W firmie zidentyfikuj zasoby dla urządzeń między klientem a punktem ruchu wychodzącego lub zidentyfikuj kontakt awaryjny, z którym chcesz porozmawiać o problemach z siecią.
    
Poniżej przedstawiono kilka punktów odniesienia, które można obliczyć za pomocą prostych testów za pomocą narzędzi:
  
- Czas od komputera klienckiego do punktu ruchu wychodzącego w milisekundach
    
- Czas od punktu ruchu wychodzącego do Office 365 w milisekundach
    
- Lokalizacja w świecie serwera, który rozpoznaje adresy URL Office 365 podczas przeglądania
    
- Szybkość rozpoznawania nazw DNS usługodawcy isp w milisekundach, niespójności w przyjeździe pakietów (zakłócenia sieci), przekazywanie i czas pobierania w milisekundach
    
Jeśli nie znasz sposobu wykonywania tych kroków, przejdziemy do bardziej szczegółowych informacji w tym artykule. 
  
## <a name="what-is-a-baseline"></a>Co to jest punkt odniesienia?

Poznasz wpływ, gdy będzie on zły, ale jeśli nie znasz historycznych danych dotyczących wydajności, nie możesz mieć kontekstu, jak źle mogło się stać i kiedy. Więc bez linii bazowej, brakuje kluczowej wskazówki do rozwiązania zagadki: obraz na puzzli. W przypadku rozwiązywania problemów z wydajnością potrzebny jest punkt  *porównania*. Proste punkty odniesienia wydajności nie są trudne do wykonania. Twoim zespołem operacyjnym może być wykonanie tych zadań w harmonogramie. Załóżmy na przykład, że połączenie wygląda następująco: 
  
![Podstawowa grafika sieciowa przedstawiająca klienta, serwer proxy i chmurę Office 365.](../media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Oznacza to, że skontaktowano się z zespołem sieciowym i okazało się, że opuszczasz firmę dla Internetu za pośrednictwem serwera proxy i że serwer proxy obsługuje wszystkie żądania wysyłane przez komputer kliencki do chmury. W takim przypadku należy narysować uproszczoną wersję połączenia, która zawiera listę wszystkich interweniujących urządzeń. Teraz wstaw narzędzia, których można użyć do testowania wydajności między klientem, punktem ruchu wychodzącego (gdzie opuszczasz sieć dla Internetu) i chmurą Office 365.
  
![Sieć podstawowa z klientem, serwerem proxy i chmurą oraz sugestiami dotyczącymi narzędzi PSPing, TraceTCP i śledzenia sieci.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Opcje są wymienione jako **Proste** i **Zaawansowane** ze względu na ilość wiedzy potrzebnej do znalezienia danych wydajności. Śledzenie sieci zajmie dużo czasu w porównaniu z uruchomionymi narzędziami wiersza polecenia, takimi jak PsPing i TraceTCP. Te dwa narzędzia wiersza polecenia zostały wybrane, ponieważ nie używają pakietów ICMP, które zostaną zablokowane przez Office 365, a ponieważ dają czas w milisekundach potrzebny do opuszczenia komputera klienckiego lub serwera proxy (jeśli masz dostęp) i docierają do Office 365. Każdy indywidualny przeskok z jednego komputera do drugiego będzie mieć wartość czasu, a to świetnie nadaje się do punktów odniesienia! Co równie ważne, te narzędzia wiersza polecenia umożliwiają dodanie numeru portu do polecenia. Jest to przydatne, ponieważ Office 365 komunikuje się za pośrednictwem portu 443, który jest portem używanym przez protokół Secure Sockets Layer i Transport Layer Security (SSL i TLS). Jednak inne narzędzia innych firm mogą być lepszym rozwiązaniem dla Twojej sytuacji. Firma Microsoft nie obsługuje wszystkich tych narzędzi, więc jeśli z jakiegoś powodu nie można uzyskać działania narzędzi PsPing i TraceTCP, przejdź do śledzenia sieci za pomocą narzędzia takiego jak Netmon. 
  
Punkt odniesienia można wykonać przed godzinami pracy, ponownie podczas intensywnego użytkowania, a następnie ponownie po godzinach. Oznacza to, że na końcu możesz mieć strukturę folderów, która wygląda nieco tak:
  
![Grafika przedstawiająca sposób organizowania danych wydajności w folderach.](../media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
Należy również wybrać konwencję nazewnictwa plików. Oto kilka przykładów:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf
    
Istnieje wiele różnych sposobów, aby to zrobić, ale używanie formatu **\<dateTime\>\<what's happening in the test\>** jest dobrym miejscem do rozpoczęcia. Staranność w tej kwestii bardzo pomoże, gdy spróbujesz później rozwiązać problemy. Później będzie można powiedzieć: "8 lutego zrobiłem dwa ślady, jeden pokazał dobrą wydajność, a drugi pokazał źle, więc możemy je porównać". Jest to przydatne w rozwiązywaniu problemów. 
  
Musisz mieć zorganizowany sposób utrzymywania historycznych punktów odniesienia. W tym przykładzie proste metody wygenerowały trzy dane wyjściowe wiersza polecenia, a wyniki zostały zebrane jako zrzuty ekranu, ale zamiast tego mogą być dostępne pliki przechwytywania sieci. Użyj metody, która działa najlepiej dla Ciebie. Przechowuj historyczne punkty odniesienia i odwołuj się do nich w punktach, w których można zauważyć zmiany w zachowaniu Usługi online. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Dlaczego warto zbierać dane dotyczące wydajności podczas pilotażu?

Nie ma lepszego czasu na rozpoczęcie tworzenia punktów odniesienia niż podczas pilotażu usługi Office 365. Twoje biuro może mieć tysiące użytkowników, setki tysięcy lub może mieć pięć, ale nawet przy kilku użytkownikach możesz wykonać testy, aby zmierzyć wahania wydajności. W przypadku dużej firmy reprezentatywna próbka kilkuset użytkowników pilotujących Office 365 może być rzutowana na zewnątrz do kilku tysięcy, aby wiedzieć, gdzie mogą wystąpić problemy, zanim się pojawią.
  
W przypadku małej firmy, gdzie wejście na pokład oznacza, że wszyscy użytkownicy przechodzą do usługi w tym samym czasie i nie ma pilotażu, zachowaj miary wydajności, aby mieć dane do pokazania wszystkim, którzy mogą być musieli rozwiązać problem z nieprawidłowo działającą operacją. Jeśli na przykład zauważysz, że nagle możesz chodzić po budynku w czasie potrzebnym do przekazania średniej wielkości grafiki, w której odbywała się ona szybko.
  
## <a name="how-to-collect-baselines"></a>Jak zbierać punkty odniesienia

W przypadku wszystkich planów rozwiązywania problemów należy zidentyfikować te elementy co najmniej:
  
- Używany komputer kliencki (typ komputera lub urządzenia, adres IP i akcje, które spowodowały problem)
    
- Gdzie komputer kliencki znajduje się na świecie (na przykład, czy ten użytkownik w sieci VPN do sieci, pracy zdalnej lub w intranecie firmy)
    
- Punkt ruchu wychodzącego używany przez komputer kliencki z sieci (punkt, w którym ruch opuszcza firmę dla usługodawcy internetowego lub Internetu)
    
 Układ sieci można znaleźć od administratora sieci. Jeśli korzystasz z małej sieci, przyjrzyj się urządzeniom łączącym Się z Internetem i zadzwoń do usługodawcy internetowego, jeśli masz pytania dotyczące układu. Utwórz grafikę końcowego układu dla odwołania. 
  
Ta sekcja jest podzielona na proste narzędzia i metody wiersza polecenia oraz bardziej zaawansowane opcje narzędzi. Najpierw omówimy proste metody. Jeśli jednak masz teraz problem z wydajnością, przejdź do zaawansowanych metod i wypróbuj przykładowy plan akcji rozwiązywania problemów z wydajnością.
  
### <a name="simple-methods"></a>Proste metody

Celem tych prostych metod jest naucz się przyjmować, rozumieć i prawidłowo przechowywać proste punkty odniesienia wydajności w czasie, dzięki czemu będziesz informowany o Office 365 wydajności. Oto prosty diagram, który jest prosty, jak pokazano wcześniej:
  
![Sieć podstawowa z klientem, serwerem proxy i chmurą oraz sugestiami dotyczącymi narzędzi PSPing, TraceTCP i śledzenia sieci.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> Funkcja TraceTCP jest uwzględniona w tym zrzutze ekranu, ponieważ jest to przydatne narzędzie do wyświetlania w milisekundach, jak długo trwa przetwarzanie żądania oraz ile przeskoków sieci lub połączeń z jednego komputera do następnego trwa, aby żądanie dotarło do miejsca docelowego. Funkcja TraceTCP może również nadać nazwy serwerów używanych podczas przeskoków, co może być przydatne w narzędziu do rozwiązywania problemów Microsoft Office 365 w pomocy technicznej. > polecenia TraceTCP mogą być bardzo proste, takie jak: >  `tracetcp.exe outlook.office365.com:443`> Pamiętaj, aby uwzględnić numer portu w poleceniu! > [TraceTCP](https://simulatedsimian.github.io/tracetcp_download.html) jest bezpłatne pobieranie, ale opiera się na Wincap. Wincap to narzędzie, które jest również używane i instalowane przez firmę Netmon. Firma Netmon jest również używana w sekcji metod zaawansowanych. 
  
 Jeśli masz wiele biur, musisz również przechowywać zestaw danych od klienta w każdej z tych lokalizacji. Ten test mierzy opóźnienie, które w tym przypadku jest wartością liczbową, która opisuje ilość czasu między wysłaniem żądania przez klienta do Office 365 a Office 365 odpowiedzią na żądanie. Testowanie pochodzi z domeny na komputerze klienckim i wygląda na to, aby zmierzyć rundę z wewnątrz sieci, przez punkt ruchu wychodzącego, przez Internet, aby Office 365 i z powrotem. 
  
Istnieje kilka sposobów radzenia sobie z punktem ruchu wychodzącego, w tym przypadku z serwerem proxy. Możesz śledzić od 1 do 2, a następnie od 2 do 3, a następnie dodać liczby w milisekundach, aby uzyskać ostateczną sumę na krawędzi sieci. Możesz też skonfigurować połączenie w celu obejścia serwera proxy dla adresów Office 365. W większej sieci z zaporą, zwrotnym serwerem proxy lub kombinacją tych dwóch może być konieczne wprowadzenie wyjątków na serwerze proxy, które umożliwią przekazywanie ruchu dla wielu adresów URL. Aby uzyskać listę punktów końcowych używanych przez Office 365, zobacz [Office 365 adresy URL i zakresy adresów IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Jeśli masz uwierzytelniający serwer proxy, rozpocznij od przetestowania wyjątków dla następujących elementów:
  
- Porty 80 i 443
    
- TCP i HTTPs
    
- Połączenia wychodzące do dowolnego z tych adresów URL:
    
- \*.microsoftonline.com
    
- \*.microsoftonline-p.com
    
- \*.sharepoint.com
    
- \*.outlook.com
    
- \*.lync.com
    
- osub.microsoft.com
    
Wszyscy użytkownicy muszą mieć możliwość uzyskania dostępu do tych adresów bez żadnych zakłóceń serwera proxy lub uwierzytelniania. W mniejszej sieci należy dodać je do listy obejść serwera proxy w przeglądarce internetowej. 
  
Aby dodać je do listy obejść serwera proxy w programie Internet Explorer, przejdź do pozycji **Narzędzia** \> **Opcje** \> internetowe **Ustawienia** \> **sieci LAN Ustawienia** \> sieci LAN **Zaawansowane**. Na karcie zaawansowane znajduje się również serwer proxy i port serwera proxy. Może być konieczne kliknięcie pola wyboru **Użyj serwera proxy dla sieci LAN**, aby uzyskać dostęp do przycisku **Zaawansowane** . Upewnij się, że zaznaczono opcję **Pomiń serwer proxy dla adresów lokalnych** . Po kliknięciu przycisku **Zaawansowane** zostanie wyświetlone pole tekstowe, w którym można wprowadzać wyjątki. Oddziel wymienione powyżej adresy URL symboli wieloznacznych średnikami, na przykład:
  
\*.microsoftonline.com; \*.sharepoint.com
  
Po pominięciu serwera proxy powinno być możliwe użycie polecenia ping lub narzędzia PsPing bezpośrednio na Office 365 adresIE URL. Następnym krokiem będzie przetestowanie **outlook.office365.com** ping. Jeśli używasz narzędzia PsPing lub innego narzędzia, które pozwoli ci podać numer portu do polecenia PsPing względem **portal.microsoftonline.com:443** , aby zobaczyć średni czas rundy w milisekundach. 
  
Czas rundy (RTT) to wartość liczbowa, która mierzy, jak długo trwa wysyłanie żądania HTTP do serwera, takiego jak outlook.office365.com, i uzyskiwanie odpowiedzi z powrotem, która potwierdza, że serwer wie, że to zrobiłeś. Czasami będziesz widzieć ten skrót jako RTT. Powinno to być stosunkowo krótki czas.
  
Aby wykonać ten test, musisz użyć narzędzia [PSPing](/sysinternals/downloads/psping) lub innego narzędzia, które nie używa pakietów ICMP zablokowanych przez Office 365. 
  
 **Jak uzyskać ogólny czas rundy w milisekundach przy użyciu narzędzia PsPing bezpośrednio z adresu URL Office 365**
  
1. Uruchom wiersz polecenia z podwyższonym poziomem uprawnień, wykonując następujące kroki:
    
1. Kliknij przycisk **Start**.
    
2. W polu **Rozpocznij wyszukiwanie** wpisz cmd, a następnie naciśnij klawisze CTRL+SHIFT+ENTER.
    
3. Jeśli zostanie wyświetlone okno dialogowe **Kontrola konta użytkownika** , upewnij się, że wyświetlana akcja jest żądana, a następnie kliknij przycisk **Kontynuuj**.
    
2. Przejdź do folderu, w którym jest zainstalowane narzędzie (w tym przypadku PsPing), i przetestuj te adresy URL Office 365:
    
  - psping admin.microsoft.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![Polecenie PSPing zostanie microsoft-my.sharepoint.com port 443.](../media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
Pamiętaj, aby uwzględnić numer portu 443. Pamiętaj, że Office 365 działa na zaszyfrowanym kanale. Jeśli psPing bez numeru portu, żądanie zakończy się niepowodzeniem. Po wykonaniu polecenia ping na krótkiej liście poszukaj wartości Średni czas w milisekundach (ms). To jest to, co chcesz nagrać!
  
![Grafika przedstawiająca ilustrację klienta do serwera proxy PSPing z czasem rundy wynoszącym 2,8 milisekund.](../media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Jeśli nie znasz obejścia serwera proxy i wolisz krok po kroku wykonywać czynności, musisz najpierw poznać nazwę serwera proxy. W programie Internet Explorer przejdź do pozycji **Narzędzia** \> **Opcje** \> internetowe **Ustawienia** \> **sieci LAN Ustawienia** \> sieci LAN **Zaawansowane**. Na karcie **Zaawansowane** zostanie wyświetlony serwer proxy. Wyślij polecenie ping do tego serwera proxy w wierszu polecenia, wykonując następujące zadanie: 
  
 **Aby wysłać polecenie ping do serwera proxy i uzyskać wartość rundy w milisekundach dla etapu od 1 do 2**
  
1. Uruchom wiersz polecenia z podwyższonym poziomem uprawnień, wykonując następujące kroki:
    
1. Kliknij przycisk **Start**.
    
2. W polu **Rozpocznij wyszukiwanie** wpisz cmd, a następnie naciśnij klawisze CTRL+SHIFT+ENTER.
    
3. Jeśli zostanie wyświetlone okno dialogowe **Kontrola konta użytkownika** , upewnij się, że wyświetlana akcja jest żądana, a następnie kliknij przycisk **Kontynuuj**.
    
2. Wpisz polecenie ping \<the name of the proxy server your browser uses, or the IP address of the proxy server\> , a następnie naciśnij klawisz ENTER. Jeśli masz zainstalowane narzędzie PsPing lub inne narzędzie, możesz zamiast tego użyć tego narzędzia. 
    
    Twoje polecenie może wyglądać jak dowolny z następujących przykładów: 
    
  - ourproxy.ourdomain.industry.business.com ping
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. Gdy śledzenie przestanie wysyłać pakiety testowe, otrzymasz małe podsumowanie, które wyświetla średnią w milisekundach i jest to wartość, którą otrzymujesz. Wykonaj zrzut ekranu przedstawiający monit i zapisz go przy użyciu konwencji nazewnictwa. W tym momencie może również pomóc wypełnić diagram wartością.
    
Być może wykonaliśmy ślad we wczesnych godzinach porannych, a klient może szybko dostać się do serwera proxy (lub dowolnego serwera ruchu wychodzącego z Internetu). W takim przypadku liczby mogą wyglądać następująco:
  
![Grafika przedstawiająca czas rundy od klienta do serwera proxy wynoszący 2,8 milisekund.](../media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Jeśli komputer kliencki jest jednym z kilku wybranych z dostępem do serwera proxy (lub wychodzącego), możesz uruchomić następny etap testu, zdalnie łącząc się z tym komputerem, uruchamiając wiersz polecenia do adresu URL Office 365. Jeśli nie masz dostępu do tego komputera, możesz skontaktować się z zasobami sieciowymi, aby uzyskać pomoc w następnym etapie i uzyskać dokładne liczby w ten sposób. Jeśli nie jest to możliwe, weź PsPing względem adresu URL Office 365 i porównaj go z czasem PsPing lub Ping względem serwera proxy. 
  
Jeśli na przykład masz 51,84 milisekund od klienta do adresu URL Office 365 i masz 2,8 milisekund od klienta do serwera proxy (lub punktu ruchu wychodzącego), masz 49,04 milisekund od ruchu wychodzącego do Office 365. Podobnie jeśli masz wartość PsPing wynoszącą 12,25 milisekund od klienta do serwera proxy w ciągu dnia i 62,01 milisekund od klienta do adresu URL Office 365, średnia wartość ruchu wychodzącego serwera proxy do adresu URL Office 365 wynosi 49,76 milisekund.
  
![Dodatkowa grafika przedstawiająca polecenie ping w milisekundach od klienta do serwera proxy obok klienta w celu Office 365, aby można było odjąć wartości.](../media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
Jeśli chodzi o rozwiązywanie problemów, możesz znaleźć coś interesującego tylko w przypadku utrzymania tych punktów odniesienia. Jeśli na przykład okaże się, że zwykle masz około 40 milisekund do 59 milisekund opóźnienia z serwera proxy lub punktu ruchu wychodzącego do adresu URL Office 365, i mieć klienta do serwera proxy lub opóźnienia punktu ruchu wychodzącego około 3 milisekund do 7 milisekund (w zależności od ilości ruchu sieciowego widzisz w tej porze dnia), to na pewno wiesz, coś jest problematyczne, jeśli ostatnich trzech klientów do serwera proxy lub wyjściowych punktów odniesienia pokaż opóźnienie wynoszące 45 milisekund.
  
### <a name="advanced-methods"></a>Metody zaawansowane

Jeśli naprawdę chcesz wiedzieć, co dzieje się z żądaniami internetowymi do Office 365, musisz zapoznać się ze śladami sieci. Nie ma znaczenia, które narzędzia wolisz dla tych śladów, HTTPWatch, Netmon, Message Analyzer, Wireshark, Fiddler, narzędzie pulpitu nawigacyjnego dewelopera lub inne będą robić tak długo, jak to narzędzie może przechwytywać i filtrować ruch sieciowy. W tej sekcji zobaczysz, że warto uruchomić więcej niż jedno z tych narzędzi, aby uzyskać bardziej kompletny obraz problemu. Podczas testowania niektóre z tych narzędzi działają również jako serwery proxy. Narzędzia używane w artykule towarzyszącym, [plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md), obejmują [Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/) lub [WireShark](https://www.wireshark.org/).
  
Wykonanie punktu odniesienia wydajności jest prostą częścią tej metody, a wiele kroków jest tych samych, co w przypadku rozwiązywania problemu z wydajnością. Bardziej zaawansowane metody tworzenia punktów odniesienia pod kątem wydajności wymagają śledzenia sieci i przechowywania ich. Większość przykładów w tym artykule korzysta z usługi SharePoint Online, ale należy opracować listę typowych akcji w usługach Office 365, do których subskrybujesz test i rejestrujesz. Oto przykład punktu odniesienia:
  
- Lista punktów odniesienia dla spo — ** Krok 1: ** Przeglądanie strony głównej witryny sieci Web spo i śledzenie sieci. Zapisz ślad. 
    
- Lista punktów odniesienia dla spo — **krok 2.** Wyszukaj termin (na przykład nazwę firmy) za pośrednictwem Enterprise Wyszukaj i wykonaj śledzenie sieci. Zapisz ślad. 
    
- Lista punktów odniesienia dla spo — **krok 3:** Upload duży plik do biblioteki dokumentów usługi SharePoint Online i wykonaj śledzenie sieci. Zapisz ślad. 
    
- Lista punktów odniesienia dla spo — **krok 4.** Przeglądanie strony głównej witryny internetowej OneDrive i śledzenie sieci. Zapisz ślad. 
    
Ta lista powinna zawierać najważniejsze typowe akcje, które użytkownicy podejmują względem usługi SharePoint Online. Zwróć uwagę, że ostatni krok, aby śledzić przechodzenie do OneDrive dla Firm, tworzy porównanie obciążenia strony głównej usługi SharePoint Online (która jest często dostosowywana przez firmy) i OneDrive dla Firm strony głównej, która rzadko jest dostosowywana. Jest to podstawowy test, jeśli chodzi o wolno ładującą się witrynę SharePoint Online. Możesz utworzyć rekord tej różnicy w testowaniu.
  
Jeśli występuje problem z wydajnością, wiele kroków jest tych samych, co w przypadku korzystania z punktu odniesienia. Ślady sieci stają się krytyczne, więc będziemy obsługiwać  *sposób*  wykonywania ważnych śladów w następnej kolejności. 
  
Aby rozwiązać problem z wydajnością, w  *tej chwili* musisz mieć ślad w momencie wystąpienia problemu z wydajnością. Musisz mieć odpowiednie narzędzia do zbierania dzienników i potrzebujesz planu działania, czyli listy akcji rozwiązywania problemów, które należy podjąć w celu zebrania najlepszych informacji, jakie możesz. Pierwszą rzeczą do wykonania jest zarejestrowanie daty i godziny testu, dzięki czemu pliki mogą być zapisywane w folderze, który odzwierciedla czas. Następnie zawęź do samych kroków problemu. Są to dokładne kroki, które zostaną użyte do testowania. Nie zapomnij o podstawach: jeśli problem dotyczy tylko Outlook, pamiętaj, aby zarejestrować, że problem występuje tylko w jednej usłudze Office 365. Zawężenie zakresu tego problemu pomoże Ci skupić się na czymś, co można rozwiązać. 
  
## <a name="see-also"></a>Zobacz też

[Zarządzanie punktami końcowymi usługi Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)