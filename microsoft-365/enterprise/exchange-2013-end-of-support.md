---
title: Exchange 2013 r. plan zakończenia wsparcia
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2013 r. osiągnie koniec wsparcia w kwietniu 2023 r. Użyj tego planu planowania, aby przygotować się do uaktualnienia do Exchange Online lub do nowszej wersji Exchange Server lokalnie.
ms.openlocfilehash: 0d0cf068ad018e710c6d8e861ac04acfd261def9
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468509"
---
# <a name="exchange-2013-end-of-support-roadmap"></a>Exchange 2013 r. plan zakończenia wsparcia

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Exchange Server 2013 r. zakończy wsparcie **11 kwietnia 2023 r**. Jeśli migracja nie została jeszcze rozpoczęta z Exchange 2013 r. do Microsoft 365, Office 365 lub Exchange 2019 r., nadszedł czas na rozpoczęcie planowania.

## <a name="what-does-end-of-support-mean"></a>Co oznacza *koniec wsparcia* ?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, podczas którego otrzymują nowe funkcje, poprawki błędów, poprawki zabezpieczeń itd. Ten cykl życia zazwyczaj trwa 10 lat od początkowej wersji produktu. Koniec tego cyklu życia jest określany jako koniec wsparcia technicznego produktu. Ponieważ Exchange 2013 r. zakończy wsparcie 11 kwietnia 2023 r., firma Microsoft nie będzie już zapewniać następujących informacji po tej dacie:

- Pomoc techniczna dotycząca problemów, które mogą wystąpić.
- Poprawki błędów w przypadku problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.
- Poprawki zabezpieczeń dla luk w zabezpieczeniach, które mogą narazić serwer na naruszenia zabezpieczeń.
- Aktualizacje stref czasowych.

Instalacja programu Exchange 2013 będzie kontynuowana po tej dacie. Jednak ze względu na zmiany wymienione powyżej zdecydowanie zalecamy migrację z Exchange 2013 r. do Exchange 2019 r. tak szybko, jak to możliwe.


## <a name="what-are-my-options"></a>Jakie są moje opcje?

To świetny moment, aby zapoznać się z opcjami i przygotować plan migracji. Można:

- Migrowanie do Microsoft 365. Migrowanie skrzynek pocztowych, folderów publicznych i innych danych przy użyciu metody cutover, minimalnej migracji hybrydowej lub pełnej migracji hybrydowej. Następnie usuń lokalne serwery Exchange i usługę Active Directory.
- Uaktualnij Exchange 2013 r. Przejdź do Exchange 2019 r. dla serwerów lokalnych.

> [!IMPORTANT]
> Jeśli Organizacja zdecyduje się migrować skrzynki pocztowe do Microsoft 365 ale planuje nadal używać Azure AD Połączenie do zarządzania kontami użytkowników w usłudze Active Directory, musisz zachować co najmniej jeden serwer Exchange firmy Microsoft w środowisku lokalnym. Jeśli usuniesz wszystkie serwery Exchange, nie będzie można wprowadzać zmian w adresatach Exchange w Exchange Online, ponieważ źródłem urzędu jest lokalna usługa Active Directory. W tym scenariuszu dostępne są następujące opcje:
>
>- *Zalecane:* Migrowanie skrzynek pocztowych w celu Microsoft 365 i uaktualnienie środowiska do Exchange 2019 r. do 11 kwietnia 2023 r. Użyj Exchange 2013, aby nawiązać połączenie z Microsoft 365 i migrować skrzynki pocztowe. Następnie uaktualnij z Exchange 2013 r. do Exchange 2019 r. i likwiduj serwery z systemem Exchange 2013 r.
>- Jeśli nie możesz ukończyć migracji w celu Exchange Online i uaktualnienia serwerów lokalnych do 11 kwietnia 2023 r., najpierw uaktualnij z Exchange 2013 r. do Exchange 2019 r., a następnie użyj Exchange 2019 r., aby przeprowadzić migrację skrzynek pocztowych do Microsoft 365.

Oto trzy ścieżki, które można wykonać, aby uniknąć zakończenia wsparcia dla Exchange Server 2013 roku.

## <a name="migrate-to-microsoft-365"></a>Migracja do platformy Microsoft 365

Migracja do Microsoft 365 jest najlepszą i najprostszą opcją ułatwiającą wycofanie wdrożenia Exchange 2013 r. Migracja do Microsoft 365 umożliwia utworzenie pojedynczego przeskoku ze starej technologii do bieżących funkcji, w tym:

- Większe skrzynki pocztowe z większą odpornością na dane;
- Funkcje zabezpieczeń, takie jak ochrona przed spamem i ochroną przed złośliwym kodem, 
- Możliwości zgodności, takie jak ochrona przed utratą danych, zasady przechowywania, In-Place i blokada postępowania sądowego, zbieranie elektronicznych elektronicznych materiałów dowodowych i nie tylko;
- Integracja z usługami SharePoint Online, OneDrive, Teams, Power BI i innymi usługami Microsoft 365;
- Skoncentrowana skrzynka odbiorcza; I
- Zaawansowana analiza i Szczegółowe informacje Viva.

Microsoft 365 otrzymuje również nowe funkcje i środowiska, dzięki czemu twoja organizacja może od razu zacząć z nich korzystać. Ponadto nie musisz się martwić o:

- Zakup i konserwacja sprzętu;
- Płacenie za uruchamianie i chłodzenie serwerów;
- Aktualizowanie serwerów na temat poprawek zabezpieczeń, produktu i strefy czasowej;
- Utrzymywanie magazynu serwera i oprogramowania w celu obsługi wymagań dotyczących zgodności; Lub
- Uaktualnianie do nowej wersji Exchange— zawsze korzystasz z najnowszej wersji z Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Jak przeprowadzić migrację do Microsoft 365?

W zależności od organizacji masz kilka opcji, aby uzyskać dostęp do Microsoft 365. Najpierw należy wziąć pod uwagę kilka kwestii, takich jak:

- Liczba skrzynek pocztowych, które należy przenieść;
- Jak długo ma trwać migracja; I
- Czy potrzebujesz bezproblemowej integracji między środowiskiem lokalnym i Microsoft 365 podczas migracji.

W tej tabeli przedstawiono opcje migracji i najważniejsze czynniki, które określają, której metody użyć.

<br>

****

|Opcja migracji|Rozmiar organizacji|Długość|
|---|---|---|
|Migracja jednorazowa|Mniej niż 150 skrzynek pocztowych|Tydzień lub mniej|
|Minimalna migracja hybrydowa|Mniej niż 150 skrzynek pocztowych|Co najmniej kilka tygodni|
|Pełna migracja hybrydowa|Ponad 150 skrzynek pocztowych|Kilka tygodni lub więcej|
|

Poniższe sekcje zawierają omówienie tych metod. Aby uzyskać więcej informacji, zobacz [Wybieranie ścieżki migracji](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Migracja jednorazowa

Podczas migracji jednorazowej migrujesz wszystkie skrzynki pocztowe, grupy dystrybucyjne, kontakty itd., aby Office 365 w określonym dniu i o określonej godzinie. Po zakończeniu zamykasz lokalne serwery Exchange i rozpoczynasz korzystanie z Microsoft 365 wyłącznie.

Migracja jednorazowa doskonale nadaje się w przypadku małych organizacji, które nie mają wielu skrzynek pocztowych, chcą szybko Microsoft 365 i nie chcą zajmować się złożonością innych metod. Ale powinien zostać ukończony za tydzień lub mniej. Wymaga to od użytkowników ponownej konfiguracji profilów Outlook. Migracja jednorazowa może migrować do 2000 skrzynek pocztowych, ale zalecamy użycie jej maksymalnie przez 150. Jeśli spróbujesz przeprowadzić więcej migracji, może minąć czas na przeniesienie wszystkich skrzynek pocztowych przed upływem terminu, a personel pomocy technicznej IT może zostać przytłoczony prośbami o pomoc użytkownikom w ponownym skonfigurowaniu Outlook.

Oto kwestie, które należy wziąć pod uwagę podczas migracji jednorazowej:

- Microsoft 365 będzie musiał nawiązać połączenie z serwerami Exchange 2013 przy użyciu Outlook Anywhere przez port TCP 443.
- Wszystkie lokalne skrzynki pocztowe zostaną przeniesione do Microsoft 365.
- Potrzebne będzie konto administratora lokalnego, które ma dostęp do odczytu do skrzynek pocztowych użytkowników.
- Akceptowane domeny Exchange 2013, których chcesz używać w Microsoft 365 muszą zostać dodane jako zweryfikowane domeny w usłudze.
- Między rozpoczęciem migracji a rozpoczęciem fazy ukończenia Microsoft 365 będzie okresowo synchronizować skrzynki pocztowe Microsoft 365 i lokalne. Dzięki temu można ukończyć migrację bez obaw o pozostawienie wiadomości e-mail w lokalnych skrzynkach pocztowych.
- Użytkownicy otrzymają nowe hasła tymczasowe dla swojego konta Microsoft 365. Po pierwszym zalogowaniu się do skrzynek pocztowych będą musieli je zmienić.
- Potrzebna będzie licencja Microsoft 365 obejmująca Exchange Online dla każdej migrowanych skrzynek pocztowych użytkownika.
- Użytkownicy będą musieli skonfigurować nowy profil Outlook na każdym z urządzeń i ponownie pobrać wiadomość e-mail. Ilość wiadomości e-mail pobranych przez Outlook może się różnić. Aby uzyskać więcej informacji, zobacz [Praca w trybie offline w Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Aby dowiedzieć się więcej na temat migracji jednorazowej, zobacz:

- [Co musisz wiedzieć o migracji e-mail z jednorazowym dostępem](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [Przeprowadzanie migracji jednorazowej wiadomości e-mail do Office 365](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Minimalna migracja hybrydowa

W minimalnej wersji hybrydowej lub ekspresowej migracja przenosi kilkaset skrzynek pocztowych do Microsoft 365 w ciągu kilku tygodni. Ta metoda nie obsługuje zaawansowanych funkcji migracji hybrydowej, takich jak udostępnione informacje o kalendarzu wolny/zajęty.

Minimalna migracja hybrydowa jest doskonałym rozwiązaniem dla organizacji, które muszą poświęcić więcej czasu na migrację swoich skrzynek pocztowych do Microsoft 365, ale nadal planują ukończenie migracji w ciągu kilku tygodni. Niektóre korzyści wynikające z bardziej zaawansowanej *migracji w pełni hybrydowej* można uzyskać bez dużej złożoności. Możesz kontrolować, ile i które skrzynki pocztowe mają zostać zmigrowane w danym momencie. Microsoft 365 skrzynki pocztowe zostaną utworzone przy użyciu nazw użytkowników i haseł kont lokalnych. W przeciwieństwie do migracji jednorazowych użytkownicy nie muszą ponownie tworzyć swoich profilów Outlook.

Poniżej przedstawiono kwestie, które należy wziąć pod uwagę w kwestii minimalnej migracji hybrydowej:

- Konieczne będzie przeprowadzenie jednorazowej synchronizacji katalogów między serwerami lokalna usługa Active Directory i Microsoft 365.
- Użytkownicy będą mogli zalogować się do swojej skrzynki pocztowej Microsoft 365 przy użyciu tej samej nazwy użytkownika i hasła, co przed skrzynką pocztową.
- Potrzebna będzie licencja Microsoft 365 obejmująca Exchange Online dla każdej migrowanych skrzynek pocztowych użytkownika.
- Użytkownicy nie będą musieli konfigurować nowego profilu Outlook na większości swoich urządzeń, chociaż niektóre starsze telefony Android mogą potrzebować nowego profilu. Użytkownicy nie będą musieli ponownie załadować wiadomości e-mail.

Aby uzyskać więcej informacji, zobacz [Use Minimal Hybrid to quickly migrate Exchange mailboxes to Office 365 (Używanie minimalnej hybrydowej do szybkiej migracji Exchange skrzynek pocztowych do Office 365](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate)).

### <a name="full-hybrid"></a>Pełna hybryda

W przypadku pełnej migracji hybrydowej masz wiele setek, do dziesiątek tysięcy skrzynek pocztowych i przenosisz niektóre lub wszystkie do Microsoft 365. Ponieważ te migracje są zazwyczaj długoterminowe, migracje hybrydowe umożliwiają:

- Pokaż użytkownikom lokalnym informacje o kalendarzu wolny/zajęty dla użytkowników w Microsoft 365 i na odwrót.
- Zobacz ujednoliconą globalną listę adresów zawierającą adresatów zarówno w środowisku lokalnym, jak i w Microsoft 365.
- Wyświetl pełne Outlook właściwości adresatów dla wszystkich użytkowników, niezależnie od tego, czy są oni lokalni, czy w Microsoft 365.
- Bezpieczna komunikacja poczty e-mail między lokalnymi serwerami Exchange i Office 365 przy użyciu protokołu TLS i certyfikatów.
- Traktuj komunikaty wysyłane między lokalnymi serwerami Exchange i Microsoft 365 jako wewnętrzne, umożliwiając:
  - Być prawidłowo oceniane i przetwarzane przez agentów transportu i zgodności kierowania komunikatów wewnętrznych.
  - Pomiń filtry antyspamowe.

Pełne migracje hybrydowe są najlepsze dla organizacji, które oczekują, że pozostaną w konfiguracji hybrydowej przez wiele miesięcy lub dłużej. Funkcje wymienione wcześniej w tej sekcji oraz synchronizacja katalogów, lepsze zintegrowane funkcje zgodności oraz możliwość przenoszenia skrzynek pocztowych do i z Microsoft 365 przy użyciu ruchów skrzynki pocztowej online. Microsoft 365 staje się rozszerzeniem organizacji lokalnej.

Kwestie, które należy wziąć pod uwagę w przypadku migracji w pełni hybrydowej:

- Nie są one odpowiednie dla wszystkich organizacji. Ze względu na złożoność pełnych migracji hybrydowych organizacje z mniej niż kilkuset skrzynkami pocztowymi zwykle nie widzą korzyści, które uzasadniają nakład pracy i koszty. W takich przypadkach zalecamy rozważenie migracji jednorazowej lub minimalnej migracji hybrydowej.
- Synchronizację katalogów należy skonfigurować przy użyciu Połączenie Azure Active Directory (Azure AD) między serwerami lokalna usługa Active Directory i Microsoft 365.
- Użytkownicy będą mogli zalogować się do swojej skrzynki pocztowej Microsoft 365 przy użyciu tej samej nazwy użytkownika i hasła, których używają podczas logowania się do sieci lokalnej. (Ta funkcja wymaga Azure AD Połączenie z synchronizacją haseł i/lub Active Directory Federation Services).
- Potrzebna jest licencja Microsoft 365 obejmująca Exchange Online dla każdej migrowanych skrzynek pocztowych użytkownika.
- Użytkownicy nie muszą konfigurować nowego profilu Outlook na większości swoich urządzeń, chociaż niektóre starsze telefony Android mogą potrzebować nowego profilu. Użytkownicy nie będą musieli ponownie załadować wiadomości e-mail.

> [!IMPORTANT]
> Jeśli Organizacja zdecyduje się migrować skrzynki pocztowe do Microsoft 365 ale planuje zachować Azure AD Połączenie do zarządzania kontami użytkowników w usłudze Active Directory, musisz zachować co najmniej jeden serwer Exchange lokalnie. Jeśli wszystkie serwery Exchange zostaną usunięte, nie będzie można wprowadzać zmian Exchange adresatów. Dzieje się tak, ponieważ źródłem urzędu jest usługa Active Directory i należy wprowadzić tam zmiany.

Jeśli pełna migracja hybrydowa brzmi dobrze, zobacz następujące przydatne zasoby:

- [asystent wdrażania Exchange](/exchange/exchange-deployment-assistant)
- [wdrożenia hybrydowe Exchange Server](/exchange/exchange-hybrid)
- [Kreator konfiguracji hybrydowej](/exchange/hybrid-configuration-wizard)
- [Kreator konfiguracji hybrydowej — często zadawane pytania](/exchange/hybrid-configuration-wizard-faqs)
- [Wymagania wstępne wdrożenia hybrydowego](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Uaktualnianie do nowszej wersji Exchange Server lokalnej

Jesteśmy przekonani, że uzyskujesz najlepszą wartość i środowisko użytkownika, w pełni migrując do Microsoft 365. Rozumiemy jednak, że niektóre organizacje muszą utrzymywać niektóre serwery Exchange lokalnie. Może to wynikać z wymagań prawnych, aby zagwarantować, że dane nie są przechowywane w obcym centrum danych, ponieważ masz unikatowe ustawienia lub wymagania, których nie można spełnić w chmurze, lub dlatego, że potrzebujesz Exchange do zarządzania skrzynkami pocztowymi w chmurze, ponieważ nadal używasz lokalnej usługi Active Directory. W każdym razie, jeśli zachowasz Exchange lokalnie, upewnij się, że środowisko Exchange 2013 zostało uaktualnione.

Aby uzyskać najlepsze środowisko, zalecamy uaktualnienie pozostałego środowiska lokalnego do Exchange 2019 r. Nie musisz instalować Exchange Server 2016 r., ponieważ możesz przejść bezpośrednio z Exchange Server 2013 r. do Exchange Server 2019 r. Exchange 2019 najbardziej pasuje do środowiska dostępnego w Microsoft 365, chociaż niektóre funkcje są dostępne tylko w Microsoft 365.



****
Poniżej przedstawiono ważne zagadnienia dotyczące uaktualniania Exchange 2013 r.:

|Element|Więcej informacji|
|---|---|
|Daty zakończenia wsparcia technicznego|Podobnie jak Exchange 2013 r., każda wersja Exchange ma własną datę zakończenia wsparcia: <p> Exchange 2013 r. — kwiecień 2023 r. <p> Kwiecień 2023 r. jest o wiele bliżej niż myślisz!|
|Ścieżka migracji do Exchange 2019 r.|Ścieżka migracji z Exchange 2013 r. do nowszej wersji jest prosta: <p> Zainstaluj program Exchange 2019 w istniejącej organizacji Exchange 2013. <p> Przenoszenie usług i danych z Exchange 2013 r. do Exchange 2019 r. i likwidowanie serwerów Exchange 2013 r.|
|Sprzęt serwera|Wymagania sprzętowe serwera zostały zmienione z Exchange 2013 roku. Upewnij się, że sprzęt jest zgodny. Więcej informacji na temat wymagań sprzętowych można znaleźć tutaj: <p> [wymagania systemowe Exchange 2019 r.](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019) <p>Dzięki znacznej poprawie wydajności Exchange oraz zwiększonej mocy obliczeniowej i pojemności magazynu na nowszych serwerach prawdopodobnie będziesz potrzebować mniejszej liczby serwerów do obsługi tej samej liczby skrzynek pocztowych.|
|Wersja systemu operacyjnego|Minimalna obsługiwana wersja systemu operacyjnego dla Exchange 2019 to Windows Server 2019. Obsługa Windows Server 2022 już wkrótce <p> Więcej informacji na temat obsługi systemu operacyjnego można znaleźć na [stronie Exchange Supportability Matrix(Macierz możliwości obsługi](/exchange/plan-and-deploy/supportability-matrix)).|
|Poziom funkcjonalności lasu usługi Active Directory|Minimalny obsługiwany poziom funkcjonalności lasu usługi Active Directory to Windows Server 2012 R2. Więcej informacji na temat obsługi poziomu funkcjonalności lasu można znaleźć w [Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Office wersje klienta|Minimalna obsługiwana wersja klienta Office jest również udokumentowana w [macierzy Exchange supportability.](/exchange/plan-and-deploy/supportability-matrix?view=exchserver-2019#clients)|
|

Skorzystaj z następujących zasobów, aby ułatwić migrację:

- [asystent wdrażania Exchange](/exchange/exchange-deployment-assistant)
- Zmiany schematu usługi Active Directory [dla Exchange 2019 r](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2019).
- [Wymagania systemowe dotyczące Exchange 2019 r](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019).


## <a name="what-if-i-need-help"></a>Co zrobić, jeśli potrzebuję pomocy?

Jeśli przeprowadzasz migrację do Microsoft 365, możesz kwalifikować się do korzystania z naszej usługi Microsoft FastTrack. FastTrack udostępnia najlepsze rozwiązania, narzędzia i zasoby, dzięki czemu migracja do Microsoft 365 jest możliwie bezproblemowa. Co najlepsze, będziesz mieć inżyniera pomocy technicznej, który przeprowadzi Cię od planowania i projektowania po migrację ostatniej skrzynki pocztowej. Aby uzyskać więcej informacji na temat FastTrack, zobacz [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Jeśli podczas migracji do Microsoft 365 wystąpią problemy i nie używasz FastTrack lub migrujesz do nowszej wersji Exchange Server, oto kilka zasobów, których możesz użyć:

- [Społeczność techniczna](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Obsługa klienta](https://support.microsoft.com/gp/support-options-for-business)


