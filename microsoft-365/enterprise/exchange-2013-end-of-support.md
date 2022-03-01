---
title: Exchange 2013 r. przewodnik po zakończeniu pomocy technicznej
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
description: Exchange 2013 zakończy się wsparcie techniczne w kwietniu 2023 r. Skorzystaj z tego planu planowania, aby przygotować się na uaktualnienie Exchange Online do nowszej wersji Exchange Server lokalnej.
ms.openlocfilehash: 2b949c113be16db97d68d92f2f1529245c287e48
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009580"
---
# <a name="exchange-2013-end-of-support-roadmap"></a>Exchange 2013 r. przewodnik po zakończeniu pomocy technicznej

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Exchange Server 2013 zakończy się wsparcie techniczne **11 kwietnia 2023 r**. Jeśli migracja z programu Exchange 2013 do programu Microsoft 365, Office 365 lub Exchange 2019 nie została jeszcze rozpoczęta, na tym etapie należy rozpocząć planowanie.

## <a name="what-does-end-of-support-mean"></a>Co oznacza *zakończenie obsługi* ?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, w trakcie którego uzyskać nowe funkcje, poprawki błędów, poprawki zabezpieczeń i tak dalej. Ten cykl życia zazwyczaj trwa 10 lat od początkowego wydania produktu. Koniec tego cyklu życia znany jest jako koniec wsparcia technicznego produktu. Ponieważ Exchange 2013 zakończy się świadczenie pomocy technicznej 11 kwietnia 2023 r., firma Microsoft udostępni już:

- pomoc techniczną w zakresie mogącego wystąpić problemów;
- Poprawki błędów dotyczące problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.
- Poprawki zabezpieczeń dotyczące luk, które mogą nabędać serwer na naruszenie bezpieczeństwa.
- Aktualizacje stref czasowych.

Instalacja pakietu Exchange 2013 będzie nadal działać po tym dniu. Jednak z powodu zmian wymienionych powyżej zdecydowanie zalecamy możliwie jak najszybciej przeprowadzić migrację z Exchange Exchange 2019 r.


## <a name="what-are-my-options"></a>Jakie są moje opcje?

To doskonały czas na eksplorowanie dostępnych opcji i przygotowywanie planu migracji. Można:

- Migrowanie do Microsoft 365. Migrowanie skrzynek pocztowych, folderów publicznych i innych danych przy użyciu migracji hybrydowej (minimalnej lub pełnej). Następnie usuń lokalne serwery Exchange i usługę Active Directory.
- Uaktualnianie Exchange 2013. Przejdź do Exchange 2019 dla serwerów lokalnych.

> [!IMPORTANT]
> Jeśli Twoja organizacja zdecyduje się na migrację skrzynek pocztowych do usługi Microsoft 365, ale planuje nadal korzystać z usługi Azure AD Połączenie do zarządzania kontami użytkowników w usłudze Active Directory, musisz przechowywać co najmniej jeden serwer microsoft Exchange lokalnie. Jeśli usuniesz wszystkie serwery Exchange, nie będzie można wprowadzać zmian w adresacie Exchange w usłudze Exchange Online, ponieważ źródłem uprawnień jest lokalna usługa Active Directory. W tym scenariuszu dostępne są następujące opcje:
>
>- *Zalecane:* Do 11 kwietnia 2023 Microsoft 365 przeprowadzić migrację skrzynek pocztowych do programu Exchange 2019 r. Użyj programu Exchange 2013 do łączenia się z Microsoft 365 i migrowania skrzynek pocztowych. Następnie uaktualnij system z wersji Exchange 2013 do wersji Exchange 2019 i likwiduj serwery z systemem Exchange 2013.
>- Jeśli do 11 kwietnia 2023 nie możesz ukończyć migracji do programu Exchange Online i uaktualnić serwerów lokalnych, najpierw uaktualnij program Exchange 2013 do programu Exchange 2019, a następnie przekieruj skrzynki pocztowe do programu Exchange 2019 do programu Microsoft 365.

Oto trzy ścieżki, które możesz wybrać, aby uniknąć zakończenia obsługi Exchange Server 2013.

## <a name="migrate-to-microsoft-365"></a>Migrowanie do Microsoft 365

Migracja do programu Microsoft 365 to najlepsza i najprostsza opcja ułatwiająca wycofanie wdrożenia w Exchange 2013. Dzięki migracji do Microsoft 365 można dokonać skoku ze starej technologii do bieżących funkcji, takich jak:

- większe skrzynki pocztowe o większej odporności na dane;
- Funkcje zabezpieczeń, takie jak ochrona przed spamem i złośliwym kodem, 
- Funkcje zgodności, takie jak ochrona przed utratą danych, zasady przechowywania, In-Place i postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych w miejscu i nie tylko.
- Integracja z usługami SharePoint Online, OneDrive, Teams, Power BI i innymi usługami Microsoft 365 online;
- Skoncentrowana skrzynka odbiorcza; i
- Analiza zaawansowana i usługa Viva Szczegółowe informacje.

Microsoft 365 również najpierw otrzymuje nowe funkcje i możliwości, aby Twoja organizacja od razu zacząć z nich korzystać. Ponadto nie musisz się o nie martwić:

- zakup i konserwacja sprzętu;
- Płacenie za uruchomienie i schłodzenie serwerów;
- zapewnienie na bieżąco aktualizacji serwerów w zakresie poprawek zabezpieczeń, produktów i strefy czasowej;
- obsługa magazynu serwera i oprogramowania w celu zapewnienia zgodności z przepisami; lub
- Uaktualnianie do nowej wersji Exchange; zawsze masz najnowszą wersję z Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Jak przeprowadzić migrację do Microsoft 365?

W zależności od organizacji masz kilka opcji, aby uzyskać dostęp do Microsoft 365. Najpierw należy wziąć pod uwagę kilka rzeczy, takich jak:

- Liczba skrzynek pocztowych do przeniesienia.
- Jak długo ma trwać migracja; i
- Czy potrzebujesz bezproblemowej integracji między środowiskiem lokalnym a Microsoft 365 podczas migracji.

W poniższej tabeli przedstawiono opcje migracji i najważniejsze czynniki, które określają, której metody użyć.

<br>

****

|Opcja migracji|Rozmiar organizacji|Czas trwania|
|---|---|---|
|Migracja jednorazowa|Mniej niż 150 skrzynek pocztowych|Tydzień lub mniej|
|Migracja hybrydowa o minimalnej ilości|Mniej niż 150 skrzynek pocztowych|Co najmniej kilka tygodni|
|Pełna migracja hybrydowa|Ponad 150 skrzynek pocztowych|Co najmniej kilka tygodni|
|

Poniższe sekcje zawierają omówienie tych metod. Aby uzyskać więcej informacji, zobacz [Wybierz ścieżkę migracji](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Migracja jednorazowa

W przypadku migracji Office 365 z ustawioną datą i godziną migrowane są wszystkie skrzynki pocztowe, grupy dystrybucyjne, kontakty i tak dalej. Po zamknięciu zamkniesz swoje lokalne serwery Exchange i zaczniesz używać wyłącznie Microsoft 365 serwerach.

Migracja cutover to doskonałe miejsce dla małych organizacji, które nie mają wielu skrzynek pocztowych, chcą szybko uzyskać Microsoft 365 i nie chcą zajmować się złożonością innych metod. Ale powinna zostać ukończona w tygodniu lub w krótszym tygodniu. Wymaga to ponownego skonfigurowania profilów Outlook profilów. Migracja cutover może przeprowadzić migrację maksymalnie 2000 skrzynek pocztowych, ale zalecamy jej użycie maksymalnie 150. Jeśli spróbujesz przeprowadzić migrację więcej, może zabraknie czasu na przeniesienie wszystkich skrzynek pocztowych przed upływem terminu, a pracownicy pomocy technicznej IT mogą zostać przytłoczeni wnioskami o pomoc użytkownikom w ponownej konfiguracji Outlook.

Oto kwestie do rozważenia w przypadku migracji cutover:

- Microsoft 365 będzie konieczne połączenie się z serwerami programu Exchange 2013 przy użyciu usługi Outlook Anywhere przez port TCP 443.
- Wszystkie lokalne skrzynki pocztowe zostaną przeniesione do Microsoft 365.
- Musisz mieć lokalne konto administratora, które ma dostęp do odczytu skrzynek pocztowych użytkowników.
- Domeny Exchange 2013, których chcesz używać w usłudze Microsoft 365 muszą zostać dodane jako zweryfikowane domeny w usłudze.
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
> Jeśli Twoja organizacja zdecyduje się na migrację skrzynek pocztowych do usługi Microsoft 365, ale planuje zachować usługę Azure AD Połączenie w celu zarządzania kontami użytkowników w usłudze Active Directory, musisz przechowywać co najmniej jeden Exchange serwera lokalnego. Jeśli wszystkie Exchange zostaną usunięte, nie będzie można wprowadzać zmian w Exchange adresatów. Jest to spowodowane tym, że źródłem uprawnień jest usługa Active Directory i należy wprowadzić w tym miejscu zmiany.

Jeśli pełna migracja hybrydowa wydaje Ci się właściwa, zobacz następujące przydatne zasoby:

- [Exchange wdrażania](/exchange/exchange-deployment-assistant)
- [Exchange Server wdrożeń hybrydowych](/exchange/exchange-hybrid)
- [Kreator konfiguracji hybrydowej](/exchange/hybrid-configuration-wizard)
- [Kreator konfiguracji hybrydowej : często zadawane pytania](/exchange/hybrid-configuration-wizard-faqs)
- [Wymagania wstępne dotyczące wdrożenia hybrydowego](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Uaktualnianie do nowszej wersji Exchange Server lokalnej

Zdecydowanie uważamy, że najlepszą wartość i środowisko użytkownika można uzyskać dzięki pełnej migracji do Microsoft 365. Rozumiemy jednak, że niektóre organizacje muszą przechowywać niektóre Exchange lokalne. Może Exchange być spowodowane wymaganiami prawnymi, w celu zagwarantowania, że dane nie są przechowywane w obcym centrum danych, ponieważ masz unikatowe ustawienia lub wymagania, które nie mogą być spełnione w chmurze, lub że musisz zarządzać skrzynkami pocztowymi w chmurze za pomocą usługi Exchange, ponieważ nadal korzystasz z lokalnej usługi Active Directory. W każdym przypadku, jeśli dbasz o Exchange lokalnym, upewnij się, że twoje środowisko Exchange 2013 jest uaktualnione.

Aby uzyskać najlepsze wyniki, zalecamy uaktualnienie pozostałego środowiska lokalnego do wersji Exchange 2019. Nie musisz instalować pakietu Exchange Server 2016, ponieważ możesz przejść bezpośrednio z pakietu Exchange Server 2013 do Exchange Server 2019. Exchange 2019 r. najlepiej pasuje do funkcji dostępnych w programie Microsoft 365, chociaż niektóre funkcje są dostępne tylko w Microsoft 365.



****
Poniżej przedstawiono ważne informacje o uaktualnianiu do Exchange 2013:

|Element|Więcej informacji|
|---|---|
|Daty zakończenia pomocy technicznej|Podobnie Exchange 2013, każda Exchange ma własną datę zakończenia obsługi: <p> Exchange 2013–2023 <p> Kwiecień 2023 r. jest o wiele bliżej, niż się myślisz!|
|Ścieżka migracji do Exchange 2019 r.|Ścieżka migracji z programu Exchange 2013 do nowszej wersji jest prosta: <p> Zainstaluj Exchange 2019 do swojej istniejącej Exchange 2013. <p> Przenoszenie usług i danych z Exchange 2013 do Exchange 2019 r. i likwidowanie Exchange 2013.|
|Sprzęt serwera|Wymagania sprzętowe dotyczące serwera zmieniły się w Exchange 2013. Upewnij się, że sprzęt jest zgodny. Dowiedz się więcej o wymaganiach sprzętowych, tutaj: <p> [wymagania Exchange 2019 r.](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019) <p>Dzięki znacznej ulepszeniom wydajności Exchange oraz zwiększonej mocy obliczeniowej i pojemności magazynu w nowych serwerach prawdopodobnie będzie potrzebnych mniej serwerów do obsługi takiej samej liczby skrzynek pocztowych.|
|Wersja systemu operacyjnego|Minimalny obsługiwany system operacyjny w wersji Exchange 2019 to Windows Server 2019. Windows server 2022 zostanie wkrótce w wkrótce wyd. <p> Aby uzyskać więcej informacji na temat obsługi systemu operacyjnego, zobacz Exchange [Możliwości obsługi](/exchange/plan-and-deploy/supportability-matrix).|
|Poziom funkcjonalności lasu usługi Active Directory|Minimalny obsługiwany poziom funkcjonalności lasu usługi Active Directory to Windows Server 2012 R2. Aby uzyskać więcej informacji na temat obsługi poziomu funkcjonalności lasu, [zobacz Exchange Możliwości obsługi](/exchange/plan-and-deploy/supportability-matrix).|
|Office wersji klienta|Minimalna obsługiwana Office klienta jest również udokumentowana w Exchange [możliwości obsługi](/exchange/plan-and-deploy/supportability-matrix?view=exchserver-2019#clients).|
|

Skorzystaj z następujących zasobów, aby pomóc w migracji:

- [Exchange wdrażania](/exchange/exchange-deployment-assistant)
- Zmiany schematu usługi Active Directory [Exchange 2019 r](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2019).
- Wymagania [systemowe dotyczące Exchange 2019 r](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019).


## <a name="what-if-i-need-help"></a>Co zrobić, jeśli potrzebuję pomocy?

Jeśli migrujesz do usługi Microsoft 365, być może kwalifikujesz się do korzystania z naszej usługi FastTrack Microsoft. FastTrack zawiera najlepsze rozwiązania, narzędzia i zasoby, dzięki których migracja do Microsoft 365 się tak bezproblemowo, jak to tylko możliwe. Co więcej, inżynier pomocy technicznej może przejść przez proces od planowania i projektowania do migrowania ostatniej skrzynki pocztowej. Aby uzyskać więcej informacji FastTrack, zobacz [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Jeśli podczas migracji do usługi Microsoft 365 występują problemy i nie korzystasz z programu FastTrack lub migrujesz do nowszej wersji programu Exchange Server, oto niektóre zasoby, z których możesz skorzystać:

- [Społeczność techniczna](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Obsługa klienta](https://support.microsoft.com/gp/support-options-for-business)


