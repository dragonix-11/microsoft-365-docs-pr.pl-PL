---
title: Exchange 2010 r. przewodnik po zakończeniu pomocy technicznej
ms.author: dstrome
author: dstrome
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2010 zakończyło wsparcie techniczne. Skorzystaj z tego planu planowania, aby przygotować się do uaktualnienia do Exchange Online lub nowszej wersji Exchange Server lokalnej.
ms.openlocfilehash: e49bf68ce2fb9b441ecd40ae4bb89ad88ea568c8
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990273"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 r. przewodnik po zakończeniu pomocy technicznej

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Exchange Server **13 października 2020** r. zakończyło się wsparcie techniczne. Jeśli migracja z programu Exchange 2010 do programu Microsoft 365, Office 365 lub Exchange 2016 nie została jeszcze rozpoczęta, na tym etapie należy rozpocząć planowanie.

## <a name="what-does-end-of-support-mean"></a>Co oznacza *zakończenie obsługi* ?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, w trakcie którego uzyskać nowe funkcje, poprawki błędów, poprawki zabezpieczeń i tak dalej. Ten cykl życia zazwyczaj trwa 10 lat od początkowego wydania produktu. Koniec tego cyklu życia znany jest jako koniec wsparcia technicznego produktu. Ponieważ Exchange 2010 r. zakończyło wsparcie techniczne 13 października 2020 r., firma Microsoft nie udostępnia już:

- pomoc techniczną w zakresie mogącego wystąpić problemów;
- Poprawki błędów dotyczące problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.
- Poprawki zabezpieczeń dotyczące luk, które mogą nabędać serwer na naruszenie bezpieczeństwa.
- Aktualizacje stref czasowych.

Instalacja programu Exchange 2010 będzie nadal działać po upływie tego terminu. Jednak z powodu zmian wymienionych powyżej zdecydowanie zalecamy możliwie jak najszybciej przeprowadzić migrację z Exchange 2010.

Aby uzyskać więcej informacji na temat zbliżania się do zakończenia wsparcia technicznego, zobacz Zasoby pomocne przy uaktualnieniu z serwerów i klientów programu [Office 2010](upgrade-from-office-2010-servers-and-products.md).

## <a name="what-are-my-options"></a>Jakie są moje opcje?

To doskonały czas na eksplorowanie dostępnych opcji i przygotowywanie planu migracji. Można:

- Migruj w pełni do Microsoft 365. Migrowanie skrzynek pocztowych przy użyciu migracji hybrydowej ( minimalnej lub pełnej). Następnie usuń lokalne serwery Exchange usługi Active Directory.
- Przemigruj Exchange 2010 do Exchange 2016 na serwerach lokalnych.

> [!IMPORTANT]
> Jeśli Twoja organizacja zdecyduje się na migrowanie skrzynek pocztowych do usługi Microsoft 365, ale planuje zachować synchronizację katalogów lub usługę Azure AD Połączenie w miejscu, aby nadal zarządzać kontami użytkowników z lokalnej usługi Active Directory, musisz zachować co najmniej jeden serwer programu Microsoft Exchange w środowisku lokalnym. Jeśli usuniesz wszystkie serwery Exchange, nie będzie można wprowadzać zmian w adresatach usługi Exchange w usłudze Exchange Online, ponieważ źródło uprawnień pozostaje w lokalnej usłudze Active Directory. Należy wprowadzić tam zmiany. W tym scenariuszu dostępne są następujące opcje:
>
>- *Zalecane:* Jeśli skrzynki pocztowe zostały zmigrowane do usługi Microsoft 365 i uaktualnione do 13 października 2020 r., użyj programu Exchange 2010 w celu nawiązania połączenia z programem Microsoft 365 i przeprowadzenia migracji skrzynek pocztowych. Następnie przemigruj Exchange 2010 do Exchange 2016 i likwiduj wszystkie pozostałe serwery Exchange 2010.
>- Jeśli do 13 października 2020 r. nie ukończono migracji skrzynek pocztowych i uaktualnienia serwera lokalnego, najpierw uaktualnij lokalne serwery programu Exchange 2010 do wersji Exchange 2016. Następnie użyj programu Exchange 2016, aby połączyć się z Microsoft 365 i przeprowadzić migrację skrzynek pocztowych.

> [!NOTE]
> Jest to nieco bardziej skomplikowane, ale możesz również przeprowadzić migrację skrzynek pocztowych do usługi Microsoft 365 podczas migrowania lokalnych serwerów programu Exchange 2010 do programu Exchange 2016.

Oto trzy ścieżki, które możesz wybrać, aby uniknąć zakończenia obsługi Exchange Server 2010.

![Exchange Server 2010 ścieżki uaktualniania.](../media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

W poniższych sekcjach opisano szczegółowo poszczególne opcje.

## <a name="migrate-to-microsoft-365"></a>Migrowanie do Microsoft 365

Migrowanie poczty e-mail do programu Microsoft 365 jest najlepszą i najprostszą opcją pomocną w wycofywaniu wdrożenia w Exchange 2010. Dzięki migracji do Microsoft 365 można dokonać skoku ze starej technologii do bieżących funkcji, takich jak:

- Funkcje zgodności, takie jak zasady przechowywania, In-Place i postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych w miejscu i nie tylko.
- Microsoft Teams.
- Power BI.
- Focused Inbox.
- MyAnalytics.

Microsoft 365 również najpierw otrzymuje nowe funkcje i możliwości, aby Twoja organizacja od razu zacząć z nich korzystać. Ponadto nie musisz się o nie martwić:

- Zakup i konserwacja sprzętu.
- Płacenie za upał i schłodzenie serwerów.
- Być na bieżąco z poprawkami zabezpieczeń, produktu i strefy czasowej.
- Obsługa magazynu i oprogramowania w celu zapewnienia zgodności z wymaganiami.
- Uaktualnianie do nowej wersji pakietu Exchange. Zawsze używasz najnowszej wersji programu Exchange w Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Jak przeprowadzić migrację do Microsoft 365?

W zależności od organizacji masz kilka opcji, aby uzyskać dostęp do Microsoft 365. Najpierw należy wziąć pod uwagę kilka rzeczy, takich jak:

- Liczba stanowisk lub skrzynek pocztowych, które należy przenieść.
- Jak długo ma trwać migracja.
- Czy potrzebujesz bezproblemowej integracji między lokalną instalacją a Microsoft 365 podczas migracji.

W poniższej tabeli przedstawiono opcje migracji i najważniejsze czynniki, które określają, której metody użyć.

<br>

****

|Opcja migracji|Rozmiar organizacji|Czas trwania|
|---|---|---|
|Migracja jednorazowa|Mniej niż 150 stanowisk|Tydzień lub mniej|
|Migracja hybrydowa o minimalnej ilości|Mniej niż 150 stanowisk|Co najmniej kilka tygodni|
|Pełna migracja hybrydowa|Ponad 150 stanowisk|Co najmniej kilka tygodni|
|

Poniższe sekcje zawierają omówienie tych metod. Aby uzyskać więcej informacji, zobacz [Wybierz ścieżkę migracji](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Migracja jednorazowa

W przypadku migracji Office 365 z ustawioną datą i godziną migrowane są wszystkie skrzynki pocztowe, grupy dystrybucyjne, kontakty i tak dalej. Po zamknięciu zamkniesz swoje lokalne serwery Exchange i zaczniesz używać wyłącznie Microsoft 365 serwerach.

Migracja cutover to doskonałe miejsce dla małych organizacji, które nie mają wielu skrzynek pocztowych, chcą szybko uzyskać Microsoft 365 i nie chcą zajmować się złożonością innych metod. Ale powinna zostać ukończona w tygodniu lub w krótszym tygodniu. Wymaga to ponownego skonfigurowania profilów Outlook profilów. Migracja cutover może przeprowadzić migrację maksymalnie 2000 skrzynek pocztowych, ale zalecamy jej użycie maksymalnie 150. Jeśli spróbujesz przeprowadzić migrację więcej, może zabraknie czasu na przeniesienie wszystkich skrzynek pocztowych przed upływem terminu, a pracownicy pomocy technicznej IT mogą zostać przytłoczeni wnioskami o pomoc użytkownikom w ponownej konfiguracji Outlook.

Oto kwestie do rozważenia w przypadku migracji cutover:

- Microsoft 365 będzie konieczne połączenie się z twoimi Exchange 2010 przy użyciu usługi Outlook Anywhere przez port TCP 443.
- Wszystkie lokalne skrzynki pocztowe zostaną przeniesione do Microsoft 365.
- Musisz mieć lokalne konto administratora, które ma dostęp do odczytu skrzynek pocztowych użytkowników.
- Domeny Exchange 2010, których chcesz używać w usłudze Microsoft 365 muszą zostać dodane jako zweryfikowane domeny w usłudze.
- Od czasu rozpoczęcia migracji do czasu rozpoczęcia fazy zakończenia program Microsoft 365 okresowo synchronizuje skrzynki pocztowe z Microsoft 365 lokalnymi skrzynkami pocztowymi. Dzięki temu nie musisz się martwić, że podczas migracji zostanie w Twoich lokalnych skrzynkach pocztowych poczty e-mail.
- Użytkownicy otrzymają nowe tymczasowe hasła dla swoich kont Microsoft 365 konta. Będą oni musieli je zmienić, gdy zalogują się do swoich skrzynek pocztowych po raz pierwszy.
- Potrzebna jest licencja Microsoft 365, która obejmuje Exchange Online skrzynek pocztowych użytkowników, które migrowane są.
- Użytkownicy będą musieli skonfigurować nowy profil Outlook na każdym ze swoich urządzeń i ponownie pobrać pocztę e-mail. Ilość wiadomości e-mail, które można Outlook, może się różnić. Aby uzyskać więcej informacji, zobacz [Praca w trybie offline w programie Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Aby dowiedzieć się więcej o migracji po kolei, zobacz:

- [Co należy wiedzieć o migracji po kolei z poczty e-mail](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [Przeprowadzanie migracji Office 365](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Migracja hybrydowa o minimalnej ilości

W minimalnej migracji hybrydowej (ekspresowej) możesz przenieść kilkaset skrzynek Microsoft 365 w ciągu kilku tygodni. Ta metoda nie obsługuje zaawansowanych funkcji migracji hybrydowej, takich jak udostępnione informacje o wolny/zajętym kalendarzu.

Minimalna migracja hybrydowa to doskonałe rozwiązanie dla organizacji, które potrzebują więcej czasu na migrowanie skrzynek pocztowych do usługi Microsoft 365, ale mimo to planują zakończyć migrację w ciągu kilku tygodni. Niektóre z zalet bardziej zaawansowanej migracji hybrydowej *bez* zbyt złożonej funkcji można uzyskać. Możesz kontrolować, ile skrzynek pocztowych i które mają zostać zmigrowane w danej chwili. Microsoft 365 zostaną utworzone skrzynki pocztowe z nazwami użytkowników i hasłami kont lokalnych. Ponadto, w przeciwieństwie do migracji ponownej, użytkownicy nie muszą ponownie tworzyć swoich Outlook profilów.

Oto kwestie do rozważenia w zakresie minimalnej migracji hybrydowej:

- Musisz wykonać jedną synchronizację katalogów między lokalnymi serwerami usługi Active Directory i usługą Microsoft 365.
- Użytkownicy będą mogli zalogować się do swoich skrzynek Microsoft 365 pocztowej przy użyciu tej samej nazwy użytkownika i hasła co przed skrzynką pocztową.
- Potrzebna jest licencja Microsoft 365, która obejmuje Exchange Online skrzynek pocztowych użytkowników, które będą migrowane.
- Użytkownicy nie będą musieli  skonfigurować nowego profilu aplikacji Outlook na większości swoich urządzeń, chociaż niektóre starsze telefony z systemem Android mogą wymagać nowego profilu. Użytkownicy nie będą musieli ponownie ładować swoich wiadomości e-mail.

Aby uzyskać więcej informacji, zobacz [Używanie minimalnej wersji](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate) hybrydowej do szybkiego migrowania Exchange pocztowych do Office 365.

### <a name="full-hybrid"></a>Pełna hybrydowa

W pełnej migracji hybrydowej masz od kilkuset do kilkudziesięciu tysięcy skrzynek pocztowych i przenosisz niektóre lub wszystkie do Microsoft 365. Ponieważ tego typu migracje mają zazwyczaj dłuższy czas, migracja hybrydowa umożliwia:

- Wyświetlanie użytkownikom lokalnym informacji o wolny/zajętym kalendarzu dla użytkowników Microsoft 365 i odwrotnie.
- Zobacz ujednoliconą globalną listę adresową zawierającą adresatów zarówno lokalnych, jak i Microsoft 365.
- Wyświetl pełne Outlook adresatów dla wszystkich użytkowników, niezależnie od tego, czy są lokalni, czy Microsoft 365.
- Zabezpieczanie komunikacji e-mail między lokalnymi serwerami Exchange i Office 365 przy użyciu usługi TLS i certyfikatów.
- Traktuj wiadomości wysyłane między lokalnymi serwerami poczty Exchange i Microsoft 365 jak wewnętrzne, co umożliwia im:
  - Należy prawidłowo oceniać i przetwarzać wiadomości przez agentów transportu i zgodności docelowych wiadomości wewnętrznych.
  - Pomijanie filtrów spamu.

Pełne migracje hybrydowe są najlepszym rozwiązaniem dla organizacji, które godzą się na pozostawanie w konfiguracji hybrydowej przez wiele miesięcy. Funkcje wymienione wcześniej w tej sekcji, funkcje synchronizacji katalogów, lepiej zintegrowane funkcje zgodności oraz możliwość przenoszenia skrzynek pocztowych do i z usługi Microsoft 365 przenoszenia skrzynek pocztowych w trybie online. Microsoft 365 stanie się rozszerzeniem Twojej organizacji lokalnej.

Kwestie do rozważenia w przypadku migracji w pełni hybrydowej:

- Nie są przeznaczone dla wszystkich organizacji. Ze względu na złożoność pełnej migracji hybrydowej organizacje mające mniej niż kilkaset skrzynek pocztowych zazwyczaj nie odsądają korzyści, które wyjustują nakład pracy i koszty. W takich przypadkach zalecamy, aby zamiast tego rozważyć migrację czasową lub minimalną migrację hybrydową.
- Musisz skonfigurować synchronizację katalogów przy użyciu usługi Azure Active Directory (Azure AD) Połączenie między lokalnymi serwerami usługi Active Directory i Microsoft 365.
- Użytkownicy będą mogli zalogować się do swoich skrzynek pocztowych usługi Microsoft 365, korzystając z tej samej nazwy użytkownika i hasła, których używają podczas logowania się do sieci lokalnej. (Ta funkcja wymaga usługi Azure AD Połączenie z synchronizacją haseł i/lub usługami federacyjną Active Directory.
- Potrzebna jest licencja Microsoft 365, która obejmuje Exchange Online skrzynek pocztowych poszczególnych użytkowników, które migrowane są.
- Użytkownicy nie muszą  skonfigurować nowego profilu Outlook na większości swoich urządzeń, chociaż niektóre starsze telefony z systemem Android mogą wymagać nowego profilu. Użytkownicy nie będą musieli ponownie ładować swoich wiadomości e-mail.

> [!IMPORTANT]
> Jeśli Twoja organizacja zdecyduje się na migrację skrzynek pocztowych do usługi Microsoft 365, ale planuje zachować synchronizację katalogów lub usługę Azure AD Połączenie w miejscu, aby nadal zarządzać kontami użytkowników z lokalnej usługi Active Directory, musisz zachować co najmniej jeden serwer usługi Exchange w środowisku lokalnym. Jeśli wszystkie Exchange zostaną usunięte, nie będzie można wprowadzać zmian w Exchange adresatów w Exchange Online. Jest to spowodowane tym, że źródło urzędu pozostaje w lokalnej usłudze Active Directory i należy tam wprowadzić zmiany.

Jeśli pełna migracja hybrydowa wydaje Ci się właściwa, zobacz następujące przydatne zasoby:

- [Exchange wdrażania](/exchange/exchange-deployment-assistant)
- [Exchange Server wdrożeń hybrydowych](/exchange/exchange-hybrid)
- [Kreator konfiguracji hybrydowej](/exchange/hybrid-configuration-wizard)
- [Kreator konfiguracji hybrydowej : często zadawane pytania](/exchange/hybrid-configuration-wizard-faqs)
- [Wymagania wstępne dotyczące wdrożenia hybrydowego](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Uaktualnianie do nowszej wersji Exchange Server lokalnej

Zdecydowanie uważamy, że najlepszą wartość i środowisko użytkownika można uzyskać dzięki pełnej migracji do Microsoft 365. Rozumiemy jednak, że niektóre organizacje muszą przechowywać niektóre Exchange lokalne serwery. Może Exchange być spowodowane wymaganiami prawnymi, w celu zagwarantowania, że dane nie są przechowywane w obcym centrum danych, ponieważ masz unikatowe ustawienia lub wymagania, które nie mogą być spełnione w chmurze, lub że musisz zarządzać skrzynkami pocztowymi w chmurze za pomocą usługi Exchange, ponieważ nadal korzystasz z lokalnej usługi Active Directory. W każdym przypadku, jeśli dbasz o Exchange lokalnie, upewnij się, że środowisko systemu Exchange 2010 jest uaktualniane do wersji Exchange 2013 lub Exchange 2016.

Aby uzyskać najlepsze wyniki, zalecamy uaktualnienie pozostałego środowiska lokalnego do wersji Exchange 2016. Nie musisz instalować pakietu Exchange Server 2013, jeśli chcesz przejść bezpośrednio z Exchange Server 2010 do Exchange Server 2016.

Exchange 2016 zawiera wszystkie funkcje poprzednich wersji programu Exchange. Jego środowisko jest najbardziej zbliżone do funkcji dostępnych w Microsoft 365, chociaż niektóre funkcje są dostępne tylko w Microsoft 365. Zapoznaj się z kilkoma rzeczami, których brakowało:

<br>

****

|Exchange wersji|Funkcje|
|---|---|
|**Exchange 2013**|Uproszczona architektura zmniejsza liczbę ról serwera do trzech (Skrzynka pocztowa, Dostęp klienta, Transport graniczny)|
||Zasady ochrony przed utratą danych (DLP) ułatwiają zapobieganie wyciekom poufnych informacji|
||Ulepszone Outlook Web App użytkownika|
|**Exchange 2016**|*Funkcje z Exchange 2013 i ...*|
||Jeszcze bardziej uproszczono role serwerów: skrzynka pocztowa i transport graniczny|
||Ulepszono DLP oraz integrację z SharePoint|
||Odporność bazy danych|
||Współpraca nad dokumentami online|
|

<br>

****

|Kwestie do rozważenia|Więcej informacji|
|---|---|
|Daty zakończenia pomocy technicznej|Podobnie Exchange 2010 r., każda Exchange ma własną datę zakończenia pomocy technicznej: <p> Exchange 2013–2023 <p> Exchange 2016– październik 2025 r. <p> Im wcześniejsza data zakończenia pomocy technicznej, tym szybciej zajdą kolejne migracje. Kwiecień 2023 r. jest o wiele bliżej, niż się myślisz!|
|Ścieżka migracji do Exchange 2013 lub 2016|Ścieżka migracji z programu Exchange 2010 do nowszej wersji jest taka sama niezależnie od tego, czy wybierzesz wersję Exchange 2013, czy Exchange 2016: <p> Zainstaluj Exchange 2013 lub 2016 w istniejącej Exchange 2010. <p> Przenoszenie usług i innej infrastruktury do programu Exchange 2013 lub 2016. <p> Przenieś skrzynki pocztowe i foldery publiczne do Exchange 2013 lub 2016 Likwidowanie pozostałych Exchange 2010.|
|Współistnienie wersji|Podczas migracji do wersji Exchange 2013 lub Exchange 2016 można zainstalować jedną z tych wersji w istniejącej organizacji korzystającej z pakietu Exchange 2010. Dzięki temu możesz zainstalować co najmniej jeden serwer Exchange 2013 lub Exchange 2016 i wykonać migrację.|
|Sprzęt serwera|Wymagania sprzętowe dotyczące serwera zmieniły się Exchange 2010. Upewnij się, że sprzęt jest zgodny. Dowiedz się więcej o wymaganiach sprzętowych poszczególnych wersji tutaj: <p> [wymagania Exchange 2016](/Exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true) <p> [Exchange 2013](/Exchange/exchange-2013-system-requirements-exchange-2013-help) <p> Dzięki znacznej ulepszeniom wydajności Exchange oraz zwiększonej mocy obliczeniowej i pojemności magazynu w nowych serwerach prawdopodobnie będzie potrzebnych mniej serwerów do obsługi takiej samej liczby skrzynek pocztowych.|
|Wersja systemu operacyjnego|Minimalne obsługiwane wersje systemu operacyjnego w poszczególnych wersjach: <p> Exchange 2016 – Windows Server 2012 <p> Exchange 2013 – Windows Server 2008 R2 z dodatkiem SP1 <p> Aby uzyskać więcej informacji na temat obsługi systemu operacyjnego, zobacz Exchange [Możliwości obsługi](/exchange/plan-and-deploy/supportability-matrix).|
|Poziom funkcjonalności lasu usługi Active Directory|Minimalne poziomy funkcjonalności lasu usługi Active Directory w poszczególnych wersjach są takie: <p> Exchange 2016 – Windows Server 2008 R2 z dodatkiem SP1 <p> Exchange 2013– Windows Server 2003 <p> Aby uzyskać więcej informacji na temat obsługi poziomu funkcjonalności lasu, [zobacz Exchange Możliwości obsługi](/exchange/plan-and-deploy/supportability-matrix).|
|Office wersji klienta|Minimalne obsługiwane Office klienta w poszczególnych wersjach są: <p> Exchange 2016–Office 2010 (z najnowszymi aktualizacjami) <p> Exchange 2013– Office 2007 z dodatkiem SP3 <p> Aby uzyskać więcej informacji na Office obsługi klientów, zobacz [Exchange macierz możliwości obsługi](/exchange/plan-and-deploy/supportability-matrix).|
|

Skorzystaj z następujących zasobów, aby pomóc w migracji:

- [Exchange wdrażania](/exchange/exchange-deployment-assistant)
- Zmiany schematu usługi Active Directory dla Exchange [2016](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help)
- Wymagania systemowe dotyczące Exchange [2016](/exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-system-requirements-exchange-2013-help)
- Wymagania wstępne dotyczące Exchange [2016](/exchange/plan-and-deploy/prerequisites?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-prerequisites-exchange-2013-help)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Podsumowanie opcji dla klientów Office 2010 i serwerów oraz Windows 7

Aby uzyskać wizualne podsumowanie opcji uaktualnienia, migracji i przenoszenia do chmury dla klientów i serwerów programu Office 2010 oraz systemu Windows 7, zobacz koniec plakatu pomocy [technicznej](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Zakończenie obsługi klientów i Office 2010 i serwerów oraz Windows 7.](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Ten jednostronicowy plakat przedstawia różne sposoby odpowiadania na produkty klienckie i serwerowe programu Office 2010 oraz zakończenie wsparcia technicznego w programie Windows 7 z wyróżnieniami preferowanych ścieżek i opcji obsługi Microsoft 365 Enterprise.

Możesz również pobrać [ten plakat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) i wydrukować go w formacie letter, legal lub tabloid (11 x 17).

## <a name="what-if-i-need-help"></a>Co zrobić, jeśli potrzebuję pomocy?

Jeśli migrujesz do usługi Microsoft 365, być może kwalifikujesz się do korzystania z naszej usługi FastTrack Microsoft. FastTrack zawiera najlepsze rozwiązania, narzędzia i zasoby, dzięki których migracja do Microsoft 365 się tak bezproblemowo, jak to tylko możliwe. Co więcej, inżynier pomocy technicznej może przejść przez proces od planowania i projektowania do migrowania ostatniej skrzynki pocztowej. Aby uzyskać więcej informacji FastTrack, zobacz [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Jeśli podczas migracji do usługi Microsoft 365 występują problemy i nie korzystasz z programu FastTrack lub migrujesz do nowszej wersji programu Exchange Server, oto niektóre zasoby, z których możesz skorzystać:

- [Społeczność techniczna](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Obsługa klienta](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-articles"></a>Artykuły pokrewne

[Zasoby pomocne w uaktualnieniu serwerów i klientów Office 2010](upgrade-from-office-2010-servers-and-products.md)
