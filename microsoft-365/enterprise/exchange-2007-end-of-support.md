---
title: Exchange 2007 end of support roadmap
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Dowiedz się więcej o opcjach po zakończeniu wsparcia technicznego Exchange Server 2007 r. i rozpocznij planowanie migracji do Microsoft 365, Office 365 lub Exchange 2016 r.
ms.openlocfilehash: 8aecc835fbdde21f6651946acd15c4c70788b3da
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824405"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Exchange 2007 end of support roadmap

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Exchange Server 2007 r. osiągnęła koniec wsparcia w kwietniu 2017 r. Jeśli migracja nie została rozpoczęta z Exchange 2007 r. do Microsoft 365, Office 365 lub Exchange 2016 r., nadszedł czas na rozpoczęcie planowania.

## <a name="what-does-end-of-support-mean"></a>Co oznacza *koniec wsparcia* ?

Exchange Server, podobnie jak prawie wszystkie produkty firmy Microsoft, ma cykl życia pomocy technicznej, podczas którego udostępniamy nowe funkcje, poprawki usterek, poprawki zabezpieczeń itd. Ten cykl życia zazwyczaj trwa 10 lat od początkowej wersji produktu. Koniec tego cyklu życia jest określany jako koniec wsparcia technicznego produktu. Ponieważ 11 kwietnia 2017 r. Exchange 2007 r., firma Microsoft nie zapewnia już:

- Pomoc techniczna dotycząca problemów, które mogą wystąpić.

- Poprawki błędów w przypadku problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.

- Poprawki zabezpieczeń dla luk w zabezpieczeniach, które mogą narazić serwer na naruszenia zabezpieczeń.

- Aktualizacje stref czasowych.

Instalacja programu Exchange 2007 będzie kontynuowana po dacie zakończenia wsparcia technicznego. Jednak ze względu na brak nowych aktualizacji ani pomocy technicznej zdecydowanie zalecamy jak najszybszą migrację z Exchange 2007 r.

Aby uzyskać więcej informacji na temat serwerów Office 2007, które zbliżają się do końca wsparcia, zobacz [Planowanie uaktualniania z serwerów i produktów Office 2007](upgrade-from-office-2007-servers-and-products.md).

## <a name="what-are-my-options"></a>Jakie są moje opcje?

Można:

- Migrowanie do Microsoft 365 przy użyciu migracji jednorazowej, przejściowej lub hybrydowej.

- Migrowanie serwerów Exchange 2007 do nowszej wersji Exchange na serwerach lokalnych.

Poniższe sekcje bardziej szczegółowo eksplorują każdą opcję.

### <a name="migrate-to-microsoft-365"></a>Migracja do platformy Microsoft 365

Migrowanie poczty e-mail do Microsoft 365 jest najlepszą i najprostszą opcją ułatwiającą wycofanie wdrożenia Exchange 2007 r. Dzięki migracji do Microsoft 365 możesz utworzyć jeden przeskok z 10-letniej technologii do najnowocześniejszej funkcji, w tym:

- Możliwości zgodności, takie jak zasady przechowywania, In-Place i blokada postępowania sądowego, wykrywanie elektroniczne w miejscu i nie tylko

- Grupy Microsoft 365

- Priorytetowa skrzynka odbiorcza

- MyAnalytics

- Interfejsy API REST do programowego dostępu do poczty e-mail, kalendarzy, kontaktów itd.

Microsoft 365 otrzymujemy również nowe funkcje i środowiska, dzięki czemu Ty i Twoi użytkownicy zazwyczaj od razu zaczniecie z nich korzystać. I nie musisz się martwić o:

- Zakup i konserwacja sprzętu.

- Płacenie za ciepło i chłodzenie serwerów.

- Aktualizowanie poprawek zabezpieczeń, produktów i stref czasowych.

- Obsługa magazynu i oprogramowania w celu obsługi wymagań dotyczących zgodności.

- Uaktualnianie do nowej wersji Exchange. Dzięki Microsoft 365 zawsze korzystasz z najnowszej wersji Exchange.

#### <a name="how-should-i-migrate-to-microsoft-365"></a>Jak przeprowadzić migrację do Microsoft 365?

Masz kilka opcji migracji. Należy wziąć pod uwagę kilka kwestii, w tym:

- Liczba miejsc lub skrzynek pocztowych, które należy przenieść.
- Jak długo ma trwać migracja.
- Bez względu na to, czy podczas migracji potrzebna jest bezproblemowa integracja między instalacją lokalną a Microsoft 365.

W tej tabeli przedstawiono opcje migracji i najważniejsze czynniki, które określają, która metoda ma być używana:

|Opcja migracji|Rozmiar organizacji|Długość|
|---|---|---|
|Migracja jednorazowa|Mniej niż 150 miejsc|Tydzień lub mniej|
|Migracja etapowa|Ponad 150 miejsc|Kilka tygodni|
|Pełna migracja hybrydowa|Od kilkuset do tysięcy miejsc|Kilka miesięcy lub więcej|

Poniższe sekcje zawierają omówienie tych metod. Aby uzyskać więcej szczegółów, zobacz [Wybieranie ścieżki migracji](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

#### <a name="cutover-migration"></a>Migracja jednorazowa

Podczas migracji jednorazowej migrujesz wszystkie skrzynki pocztowe, grupy dystrybucyjne, kontakty itd., aby Microsoft 365 wstępnie wybranej dacie i godzinie. Po zakończeniu migracji należy zamknąć lokalne serwery Exchange i rozpocząć korzystanie z Microsoft 365 wyłącznie.

Migracja jednorazowa doskonale sprawdza się w przypadku małych organizacji, które nie mają wielu skrzynek pocztowych, chcą szybko Microsoft 365 i nie chcą zajmować się niektórymi złożonościami innych metod. Jednak powinien zostać ukończony za tydzień lub mniej i wymaga od użytkowników ponownej konfiguracji profilów Outlook. Migracja jednorazowa może obsłużyć do 2000 skrzynek pocztowych, ale zdecydowanie zalecamy jej użycie do migracji maksymalnie 150 skrzynek pocztowych. Jeśli spróbujesz przeprowadzić więcej migracji, może minąć czas na przeniesienie wszystkich skrzynek pocztowych przed upływem terminu, a personel pomocy technicznej IT może zostać przytłoczony prośbami o pomoc użytkownikom w ponownym skonfigurowaniu Outlook.

Jeśli myślisz o migracji jednorazowej, oto kwestie, które należy wziąć pod uwagę:

- Microsoft 365 będzie musiał nawiązać połączenie z serwerami Exchange 2007 przy użyciu Outlook Anywhere przez port TCP 443.

- Wszystkie lokalne skrzynki pocztowe zostaną przeniesione do Microsoft 365.

- Potrzebne będzie konto administratora lokalnego, które ma dostęp do odczytu do skrzynek pocztowych użytkowników.

- Zaakceptowane domeny Exchange 2007, których chcesz użyć w Microsoft 365 muszą zostać dodane jako zweryfikowane domeny w usłudze.

- Między rozpoczęciem migracji a rozpoczęciem fazy ukończenia Microsoft 365 okresowo synchronizuje skrzynki pocztowe Microsoft 365 i lokalne. Dzięki temu można ukończyć migrację bez obaw o pozostawienie wiadomości e-mail w lokalnych skrzynkach pocztowych.

- Użytkownicy otrzymają nowe hasła tymczasowe dla swoich kont Microsoft 365. Podczas pierwszego logowania się do skrzynki pocztowej należy zmienić hasło.

- Potrzebna będzie licencja Microsoft 365 obejmująca Exchange Online dla każdej migrowanych skrzynek pocztowych użytkownika.

- Użytkownicy będą musieli skonfigurować nowy profil Outlook na każdym z urządzeń i ponownie pobrać wiadomość e-mail. Ilość wiadomości e-mail pobranych przez Outlook może się różnić. Aby uzyskać więcej informacji, zobacz [Zmienianie ilości poczty w trybie offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).

Aby uzyskać więcej informacji na temat migracji jednorazowej, zobacz:

- [Co musisz wiedzieć o migracji e-mail z jednorazowym dostępem](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)

- [Przeprowadzanie migracji jednorazowej wiadomości e-mail](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

#### <a name="staged-migration"></a>Migracja etapowa

W przypadku migracji etapowej masz kilkaset lub kilka tysięcy skrzynek pocztowych, które chcesz migrować do Microsoft 365, musisz zająć tydzień lub więcej, aby ukończyć migrację i nie potrzebujesz żadnych zaawansowanych funkcji migracji hybrydowej, takich jak udostępnione informacje o kalendarzu Wolny/Zajęty.

Migracja etapowa jest doskonałym rozwiązaniem dla organizacji, które muszą poświęcić więcej czasu na migrację swoich skrzynek pocztowych do Microsoft 365 ale nadal planują ukończenie migracji w ciągu kilku tygodni. Skrzynki pocztowe można migrować w partiach. Określasz, ile i które skrzynki pocztowe są migrowane w danym momencie. Możesz na przykład wsadowe skrzynki pocztowe użytkowników w tym samym dziale, aby upewnić się, że wszystkie są przenoszone w tym samym czasie. Możesz też pozostawić skrzynki pocztowe kadry kierowniczej do ostatniej partii. Podobnie jak w przypadku migracji jednorazowych, użytkownicy będą musieli ponownie utworzyć swoje profile Outlook.

Jeśli myślisz o przeprowadzaniu migracji etapowej, oto kwestie, które należy wziąć pod uwagę:

- Microsoft 365 będzie musiał nawiązać połączenie z serwerami Exchange 2007 przy użyciu Outlook Anywhere przez port TCP 443.

- Potrzebne będzie konto administratora lokalnego, które ma dostęp do odczytu do skrzynek pocztowych użytkowników.

- Akceptowane domeny Exchange 2007, które mają być używane w Microsoft 365 muszą zostać dodane jako zweryfikowane domeny w usłudze.

- Musisz utworzyć plik CSV z pełną nazwą i adresem e-mail każdej skrzynki pocztowej, którą planujesz przeprowadzić migrację w partii. Konieczne będzie również uwzględnienie nowego hasła dla każdej migrowanych skrzynek pocztowych i wysłanie tego hasła do każdego użytkownika. Użytkownik zostanie poproszony o zmianę hasła przy pierwszym zalogowaniu się do nowej skrzynki pocztowej Microsoft 365.

- Między rozpoczęciem partii migracji a rozpoczęciem fazy ukończenia Microsoft 365 okresowo synchronizuje skrzynki pocztowe Microsoft 365 i lokalne zawarte w partii. Dzięki temu można ukończyć migrację bez obaw o pozostawienie wiadomości e-mail w lokalnych skrzynkach pocztowych.

- Potrzebna będzie licencja Microsoft 365 obejmująca Exchange Online dla każdej migrowanych skrzynek pocztowych użytkownika.

- Użytkownicy będą musieli skonfigurować nowy profil Outlook na każdym z urządzeń i ponownie pobrać wiadomość e-mail. Ilość wiadomości e-mail pobranych przez Outlook może się różnić. Aby uzyskać więcej informacji, zobacz [Zmienianie ilości poczty w trybie offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).

Aby uzyskać więcej informacji na temat migracji etapowych, zobacz:

- [Co musisz wiedzieć o etapowej migracji poczty e-mail](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)

- [Przeprowadzanie migracji etapowej wiadomości e-mail](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)

#### <a name="full-hybrid"></a>Pełna hybryda

W przypadku pełnej migracji hybrydowej organizacja ma wiele setek, do dziesiątek tysięcy skrzynek pocztowych i chcesz przenieść niektóre lub wszystkie z nich do Microsoft 365. Ponieważ te migracje są zazwyczaj długoterminowe, migracje hybrydowe umożliwiają:

- Pokaż użytkownikom lokalnym informacje o kalendarzu wolny/zajęty dla użytkowników w Microsoft 365 i na odwrót.

- Zobacz ujednoliconą globalną listę adresów zawierającą adresatów zarówno w środowisku lokalnym, jak i w Microsoft 365.

- Wyświetl pełne Outlook właściwości adresatów dla wszystkich użytkowników, niezależnie od tego, czy są oni lokalni, czy w Microsoft 365.

- Bezpieczna komunikacja poczty e-mail między lokalnymi serwerami Exchange i Microsoft 365 przy użyciu protokołu TLS i certyfikatów.

- Traktuj komunikaty wysyłane między lokalnymi serwerami Exchange i Microsoft 365 jako wewnętrzne, umożliwiając:

  - Być prawidłowo oceniane i przetwarzane przez agentów transportu i zgodności kierowania komunikatów wewnętrznych.

  - Pomiń filtry antyspamowe.

Pełna migracja hybrydowa jest najlepsza dla organizacji, które oczekują, że pozostaną w konfiguracji hybrydowej przez wiele miesięcy lub dłużej. Uzyskasz funkcje wymienione wcześniej w tej sekcji, a także synchronizację katalogów, lepsze zintegrowane funkcje zgodności oraz możliwość przenoszenia skrzynek pocztowych do i z Microsoft 365 przy użyciu ruchów skrzynki pocztowej online. Microsoft 365 staje się rozszerzeniem organizacji lokalnej.

Jeśli myślisz o pełnej migracji hybrydowej, oto kwestie, które należy wziąć pod uwagę:

- Pełna migracja hybrydowa nie jest odpowiednia dla wszystkich typów organizacji. Ze względu na złożoność pełnych migracji hybrydowych organizacje z mniej niż kilkuset skrzynkami pocztowymi zwykle nie widzą korzyści, które uzasadniają nakład pracy i koszty potrzebne do jego skonfigurowania. Jeśli brzmi to jak organizacja, zalecamy rozważenie migracji jednorazowej lub etapowej.

- Musisz wdrożyć co najmniej jeden serwer Exchange 2013 w organizacji Exchange 2007, aby działał jako "serwer hybrydowy". Ten serwer będzie komunikować się z Microsoft 365 w imieniu serwerów Exchange 2007.

- Microsoft 365 będzie musiał nawiązać połączenie z "serwerem hybrydowym" przy użyciu Outlook Anywhere przez port TCP 443.

- Musisz skonfigurować synchronizację katalogów przy użyciu Połączenie Azure Active Directory (Azure AD) między serwerami lokalna usługa Active Directory i Microsoft 365.

- Użytkownicy będą mogli zalogować się do swojej skrzynki pocztowej Microsoft 365 przy użyciu tej samej nazwy użytkownika i hasła, co podczas logowania się do sieci lokalnej. (Ta funkcja wymaga usługi Azure AD Połączenie z synchronizacją haseł i/lub Active Directory Federation Services).

- Potrzebna będzie licencja Microsoft 365 obejmująca Exchange Online dla każdej migrowanych skrzynek pocztowych użytkownika.

- Użytkownicy nie muszą konfigurować nowego profilu Outlook na większości swoich urządzeń, chociaż niektóre starsze telefony z systemem Android mogą potrzebować nowego profilu. Użytkownicy nie będą musieli ponownie załadować wiadomości e-mail.

Jeśli pełna migracja hybrydowa brzmi prawidłowo, zapoznaj się z następującymi zasobami, które pomogą w migracji:

- [asystent wdrażania Exchange](/exchange/exchange-deployment-assistant)

- [wdrożenia hybrydowe Exchange Server](/exchange/exchange-hybrid)

- [Kreator konfiguracji hybrydowej](/exchange/hybrid-configuration-wizard)

- [Kreator konfiguracji hybrydowej — często zadawane pytania](/exchange/hybrid-configuration-wizard-faqs)

- [Wymagania wstępne wdrożenia hybrydowego](/exchange/hybrid-deployment-prerequisites)

### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrowanie do nowszej wersji Exchange Server

Jesteśmy przekonani, że możesz osiągnąć najlepszą wartość i środowisko użytkownika, migrując do Microsoft 365. Rozumiemy jednak również, że niektóre organizacje muszą przechowywać pocztę e-mail w środowisku lokalnym. Może to wynikać z wymagań prawnych, aby zagwarantować, że dane nie są przechowywane w centrum danych znajdującym się w innym kraju lub podobnym. Jeśli zdecydujesz się zachować lokalną pocztę e-mail, możesz przeprowadzić migrację środowiska Exchange 2007 do Exchange 2010 r., Exchange 2013 r. lub Exchange 2016 r.

Jeśli nie możesz przeprowadzić migracji do Microsoft 365, zalecamy przeprowadzenie migracji do Exchange 2016 r. Exchange 2016 r. zawiera wszystkie funkcje poprzednich wersji Exchange. Jest również najbardziej dopasowany do środowiska dostępnego w Microsoft 365, chociaż niektóre funkcje są dostępne tylko w Microsoft 365. Zapoznaj się z kilkoma rzeczami, których ci brakowało:

|wersja Exchange|Funkcje|
|---|---|
|Exchange 2010| Role-Based Access Control (uprawnienia bez list ACL) <br/> zasady skrzynki pocztowej Outlook Web App <br/> Możliwość udostępniania wolnych/zajętych kalendarzy i delegowania między organizacjami|
|Exchange 2013 r.| *Funkcje z Exchange 2010 r. i ...* <br/> Uproszczona architektura, która zmniejszyła liczbę ról serwera do trzech (skrzynka pocztowa, dostęp klienta, transport brzegowy) <br/> Zasady ochrony przed utratą danych (DLP), które pomagają chronić poufne informacje przed wyciekami <br/> Ulepszone środowisko Outlook Web App|
|Exchange 2016 r.| *Funkcje z Exchange 2013 r. i ...* <br/> Dalsze uproszczone role serwera tylko do skrzynki pocztowej i usługi Edge Transport <br/> Ulepszono DLP wraz z integracją z SharePoint <br/> Zwiększona odporność bazy danych <br/> Współpraca dokumentów online|

#### <a name="which-version-should-i-migrate-to"></a>Do której wersji należy przeprowadzić migrację?

Zalecamy, aby początkowo zakładać, że przeprowadzisz migrację do Exchange 2016 r. Następnie użyj poniższych informacji, aby potwierdzić założenie lub wykluczyć Exchange 2016 roku. Jeśli z jakiegoś powodu nie możesz przeprowadzić migracji do Exchange 2016 r., wykonaj ten sam proces z Exchange 2013 r. itd.

|Kwestie do rozważenia|Więcej informacji|
|---|---|
|Daty zakończenia wsparcia technicznego| Podobnie jak Exchange 2007 r., każda wersja Exchange ma własną datę zakończenia wsparcia: <br/> *Exchange 2010* r. — styczeń 2020 r. <br/> *Exchange 2013* r. — kwiecień 2023 r. <br/> *Exchange 2016* r. — październik 2025 r. <br/> Im wcześniej zakończą się wsparcie, tym szybciej będzie trzeba przeprowadzić kolejną migrację.|
|Ścieżka migracji do Exchange 2010 i 2013 r.|Poniżej przedstawiono ogólne fazy migracji do Exchange 2010 r. lub Exchange 2013 r.: <br/> — Zainstaluj program Exchange 2010 lub 2013 w istniejącej organizacji Exchange 2007 r. <br/>— Przenoszenie usług i innej infrastruktury do Exchange 2010 lub 2013 r.<br/>— Przenoszenie skrzynek pocztowych i folderów publicznych do Exchange 2010 lub 2013 r.<br/>— Likwiduj pozostałe serwery Exchange 2007.|
|Ścieżka migracji do Exchange 2016 r.|Poniżej przedstawiono ogólne fazy migracji do Exchange 2016 r.: <br/> — Zainstaluj program Exchange 2013 w istniejącej organizacji Exchange 2007 r.<br/>— Przenoszenie usług i innej infrastruktury do Exchange 2013 r.<br/>— Przenoszenie skrzynek pocztowych i folderów publicznych do Exchange 2013 r.<br/>— Likwiduj pozostałe serwery Exchange 2007.<br/>— Zainstaluj program Exchange 2016 w istniejącej organizacji Exchange 2013 r.<br/>— Przenieś skrzynki pocztowe, foldery publiczne, usługi i inną infrastrukturę do Exchange 2016 r. (zamówienie nie ma znaczenia). Likwiduj pozostałe serwery Exchange 2013.<br/><br/> **Uwaga:** Migracja z Exchange 2013 r. do Exchange 2016 r. jest prosta. Obie wersje mają prawie takie same wymagania sprzętowe, a te wersje są bardzo zgodne. Możesz więc ponownie skompilować serwer kupiony za Exchange 2013 r. i zainstalować na nim Exchange 2016 r. W przypadku przenoszenia skrzynki pocztowej online większość użytkowników nawet nie zauważy, że ich skrzynka pocztowa została przeniesiona z serwera, a następnie z powrotem po jej odbudowie za pomocą Exchange 2016 roku.|
|Współistnienie wersji| Podczas migracji do ... <br/> **Exchange 2016 r.:** nie można zainstalować Exchange 2016 r. w organizacji obejmującej serwer Exchange 2007. Najpierw należy przeprowadzić migrację do Exchange 2010 lub 2013 r. (zdecydowanie zalecamy Exchange 2013 r.), usunąć wszystkie serwery Exchange 2007 r., a następnie przeprowadzić migrację do Exchange 2016 r. <br/> **Exchange 2010 lub Exchange 2013:** możesz zainstalować program Exchange 2010 lub Exchange 2013 w istniejącej organizacji Exchange 2007 r. Umożliwia to zainstalowanie co najmniej jednego serwera Exchange 2010 lub 2013 i przeprowadzenie migracji.|
|Sprzęt serwera| Wymagania sprzętowe serwera uległy zmianie z Exchange 2007 r. Upewnij się, że sprzęt jest zgodny. Aby uzyskać szczegółowe informacje, zobacz: <br/> [wymagania systemowe Exchange 2016](/Exchange/plan-and-deploy/system-requirements) <br/> [wymagania systemowe Exchange 2013](/exchange/exchange-2013-system-requirements-exchange-2013-help) <br/> [wymagania systemowe Exchange 2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141)) <br/> Zauważysz, że znaczne ulepszenia wydajności Exchange oraz zwiększona moc obliczeniowa i pojemność magazynu na nowszych serwerach oznaczają, że prawdopodobnie będziesz potrzebować mniejszej liczby serwerów do obsługi tej samej liczby skrzynek pocztowych.|
|Wersja systemu operacyjnego| Minimalna obsługiwana wersja systemu operacyjnego dla każdej wersji to: <br/> **Exchange 2016** - Windows Server 2012 <br/> **Exchange 2013** r. — Windows Server 2008 R2 SP1 <br/> **Exchange 2010** r. — Windows Server 2008 SP2 <br/> Więcej informacji na temat obsługi systemu operacyjnego można znaleźć w [witrynie Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).|
|Poziom funkcjonalności lasu usługi Active Directory| Minimalne obsługiwane poziomy funkcjonalności lasu usługi Active Directory dla każdej wersji to: <br/> **Exchange 2016** Windows Server 2008 R2 SP1 <br/> **Exchange 2013** Windows Server 2003 <br/> **Exchange 2010** Windows Server 2003 <br/> Więcej informacji na temat obsługi poziomu funkcjonalności lasu można znaleźć w [witrynie Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).|
|Office wersje klienta| Minimalna obsługiwana Office wersji klienta dla każdej wersji to: <br/> **Exchange 2016** r. — Office 2010 r. (z najnowszymi aktualizacjami) <br/> **Exchange 2013** — Office 2007 SP3 <br/> **Exchange 2010** r. — Office 2003 r. <br/> Więcej informacji na temat obsługi klienta Office można znaleźć w [witrynie Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).|

#### <a name="how-do-i-migrate"></a>Jak mogę migrować?

Jeśli zdecydujesz się zachować lokalną pocztę e-mail, skorzystaj z następujących zasobów, aby ułatwić migrację:

- [asystent wdrażania Exchange](/exchange/exchange-deployment-assistant)

- Zmiany schematu usługi Active Directory dla Exchange [2016](/Exchange/plan-and-deploy/active-directory/ad-schema-changes), [2013](/exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)

- Wymagania systemowe dla Exchange [2016](/Exchange/plan-and-deploy/system-requirements), [2013](/exchange/exchange-2013-system-requirements-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141))

- Wymagania wstępne dotyczące Exchange [2016](/Exchange/plan-and-deploy/prerequisites), [2013](/exchange/exchange-2013-prerequisites-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/bb691354(v=exchg.141))

## <a name="get-help"></a>Uzyskiwanie pomocy

Jeśli przeprowadzasz migrację do Microsoft 365, możesz kwalifikować się do korzystania z naszej usługi Microsoft FastTrack. FastTrack udostępnia najlepsze rozwiązania, narzędzia i zasoby, dzięki czemu migracja do Microsoft 365 jest możliwie bezproblemowa. Co najlepsze, inżynier pomocy technicznej przeprowadzi Cię przez migrację, od planowania i projektowania aż po migrację ostatniej skrzynki pocztowej. Aby uzyskać więcej informacji na temat FastTrack, zobacz [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Jeśli podczas migracji do Microsoft 365 wystąpią problemy i nie używasz FastTrack ani migracji do nowszej wersji Exchange Server, pomożemy. Oto niektóre zasoby, których można użyć:

- [Społeczność techniczna](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)

- [Obsługa klienta](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-topics"></a>Tematy pokrewne

[Zasoby ułatwiające uaktualnienie serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md)
