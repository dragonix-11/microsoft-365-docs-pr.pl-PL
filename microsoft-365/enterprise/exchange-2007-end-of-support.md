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
description: Poznaj dostępne opcje po zakończeniu Exchange Server 2007 r. i rozpocznij planowanie migracji do programu Microsoft 365, Office 365 lub Exchange 2016.
ms.openlocfilehash: d5e79666c0e8e9804a63c89a0095a8725f14cd35
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984452"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Exchange 2007 end of support roadmap

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Exchange Server 2007 zakończyło się wsparcie techniczne w kwietniu 2017 r. Jeśli nie rozpoczęto migracji z programu Exchange 2007 do programu Microsoft 365, Office 365 lub Exchange 2016, na tym etapie należy rozpocząć planowanie.
  
## <a name="what-does-end-of-support-mean"></a>Co oznacza *zakończenie obsługi* ?

Exchange Server, tak jak niemal wszystkie produkty firmy Microsoft, ma cykl świadczenia pomocy technicznej, w trakcie którego dostarczamy nowe funkcje, poprawki błędów, poprawki zabezpieczeń i tak dalej. Ten cykl życia zazwyczaj trwa 10 lat od początkowego wydania produktu. Koniec tego cyklu życia znany jest jako koniec wsparcia technicznego produktu. Ponieważ Exchange 2007 r. zakończyło wsparcie techniczne 11 kwietnia 2017 r., firma Microsoft nie udostępnia już:
  
- pomoc techniczną w zakresie mogącego wystąpić problemów;
    
- Poprawki błędów dotyczące problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.
    
- Poprawki zabezpieczeń dotyczące luk, które mogą nabędać serwer na naruszenie bezpieczeństwa.
    
- Aktualizacje stref czasowych.
    
Instalacja pakietu Exchange 2007 będzie nadal działać po zakończeniu wsparcia technicznego. Ponieważ jednak nie ma żadnych nowych aktualizacji ani pomocy technicznej, zdecydowanie zalecamy możliwie jak najszybciej przeprowadzić migrację z programu Exchange 2007.
  
Aby uzyskać więcej informacji Office o zbliżaniu się zakończenia wsparcia technicznego dla serwerów w wersji 2007, zobacz Planowanie uaktualnienia serwerów i produktów Office [2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Jakie są moje opcje?

Można:
  
- Przemigruj Microsoft 365 za pomocą migracji etapowej lub hybrydowej.
    
- Przemigruj serwery Exchange 2007 do nowszej wersji Exchange na serwerach lokalnych.
    
W poniższych sekcjach opisano szczegółowo poszczególne opcje.
  
### <a name="migrate-to-microsoft-365"></a>Migrowanie do Microsoft 365

Migrowanie poczty e-mail do programu Microsoft 365 jest najlepszą i najprostszą opcją pomaganą w wycofywaniu wdrożenia Exchange 2007. Dzięki migracji do Microsoft 365 można dokonać skoku technologicznego z 10-letniego roku do najnowych funkcji, takich jak:
  
- Funkcje zgodności, takie jak zasady przechowywania, In-Place i postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych w miejscu i nie tylko
    
- Microsoft 365 grupy
    
- Priorytetowa skrzynka odbiorcza
    
- MyAnalytics
    
- Interfejsy API usługi REST do programowego dostępu do poczty e-mail, kalendarzy, kontaktów i tak dalej
    
Microsoft 365 również najpierw otrzymujesz nowe funkcje i możliwości, więc Ty i Twoi użytkownicy możecie zazwyczaj zacząć z nich korzystać od razu. Nie musisz się o nie martwić:
  
- Zakup i konserwacja sprzętu.
    
- Płacenie za upał i schłodzenie serwerów.
    
- Być na bieżąco z poprawkami zabezpieczeń, produktu i strefy czasowej.
    
- Obsługa magazynu i oprogramowania w celu zapewnienia zgodności z wymaganiami.
    
- Uaktualnianie do nowej wersji pakietu Exchange. Dzięki Microsoft 365 zawsze masz najnowszą wersję pakietu Exchange.
    
#### <a name="how-should-i-migrate-to-microsoft-365"></a>Jak przeprowadzić migrację do Microsoft 365?

Dostępnych jest kilka opcji migracji. Należy wziąć pod uwagę kilka rzeczy, takich jak:

- Liczba stanowisk lub skrzynek pocztowych, które należy przenieść.
- Jak długo ma trwać migracja.
- Czy potrzebujesz bezproblemowej integracji między lokalną instalacją a Microsoft 365 podczas migracji.

W poniższej tabeli przedstawiono opcje migracji oraz najważniejsze czynniki, które określają, której metody użyć:
  

|**Opcja migracji**|**Rozmiar organizacji**|**Czas trwania**|
|:-----|:-----|:-----|
|Migracja jednorazowa  <br/> |Mniej niż 150 stanowisk  <br/> |Tydzień lub mniej  <br/> |
|Migracja etapowa  <br/> |Ponad 150 stanowisk  <br/> |Kilka tygodni  <br/> |
|Pełna migracja hybrydowa  <br/> |Od kilkuset do kilku tysięcy stanowisk  <br/> |Co najmniej kilka miesięcy  <br/> |
   
Poniższe sekcje zawierają omówienie tych metod. Aby uzyskać więcej szczegółowych informacji, [zobacz Wybierz ścieżkę migracji](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27). 
  
#### <a name="cutover-migration"></a>Migracja jednorazowa

W przypadku migracji Microsoft 365 z wcześniej wybraną datą i godziną migrowane są wszystkie skrzynki pocztowe, grupy dystrybucyjne, kontakty i tak dalej. Po zakończeniu migracji wyłączasz swoje lokalne serwery Exchange i rozpoczynasz korzystanie z Microsoft 365 migracji.
  
Migracja cutover to doskonałe miejsce dla małych organizacji, które nie mają wielu skrzynek pocztowych, chcą szybko Microsoft 365 skrzynek pocztowych i nie chcą zajmować się niektórymi ze złożonych metod. Jednak powinna ona zostać ukończona w tygodniu lub w krótszym tygodniu i wymaga ponownego skonfigurowania profilów Outlook profilów. Migracja cutover może obsługiwać do 2000 skrzynek pocztowych, ale zdecydowanie zalecamy jej użycie do migrowania maksymalnie 150 skrzynek pocztowych. Jeśli spróbujesz przeprowadzić migrację więcej, może zabraknie czasu na przeniesienie wszystkich skrzynek pocztowych przed upływem terminu, a pracownicy pomocy technicznej IT mogą zostać przytłoczeni wnioskami o pomoc użytkownikom w ponownej konfiguracji Outlook.
  
Jeśli zastanawiasz się nad wykonaniem migracji ponownej, weź pod uwagę kilka kwestii:
  
- Microsoft 365 będzie konieczne połączenie się z serwerami programu Exchange 2007 przy Outlook Anywhere przez port TCP 443.
    
- Wszystkie lokalne skrzynki pocztowe zostaną przeniesione do Microsoft 365.
    
- Musisz mieć lokalne konto administratora, które ma dostęp do odczytu skrzynek pocztowych użytkowników.
    
- Domeny Exchange 2007, których chcesz używać w usłudze Microsoft 365 muszą zostać dodane jako zweryfikowane domeny w usłudze.
    
- Od czasu rozpoczęcia migracji do czasu rozpoczęcia fazy zakończenia program Microsoft 365 okresowo synchronizuje skrzynki pocztowe z Microsoft 365 lokalnymi skrzynkami pocztowymi. Dzięki temu nie musisz się martwić, że podczas migracji zostanie w Twoich lokalnych skrzynkach pocztowych poczty e-mail.
    
- Użytkownicy otrzymają nowe tymczasowe hasła dla swoich Microsoft 365 konta. Gdy zalogują się do swoich skrzynek pocztowych po raz pierwszy, będą musieli zmienić swoje hasło.
    
- Potrzebna jest licencja Microsoft 365, która obejmuje Exchange Online skrzynek pocztowych użytkowników, które migrowane są.
    
- Użytkownicy będą musieli skonfigurować nowy profil Outlook na każdym ze swoich urządzeń i ponownie pobrać pocztę e-mail. Ilość wiadomości e-mail, które można Outlook, może się różnić. Aby uzyskać więcej informacji, [zobacz Zmienianie liczby wiadomości e-mail, które mają być nadal dostępne w trybie offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Aby uzyskać więcej informacji na temat migracji pojęciowej, zobacz:
  
- [Co należy wiedzieć o migracji po kolei z poczty e-mail](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Przeprowadzanie migracji częściowej poczty e-mail](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Migracja etapowa

W przypadku migracji etapowej masz od kilkuset do kilku tysięcy skrzynek pocztowych, które chcesz zmigrować do programu Microsoft 365, musisz potrwać tydzień lub więcej na ukończenie migracji oraz nie potrzebujesz żadnych zaawansowanych funkcji migracji hybrydowej, takich jak udostępnione informacje kalendarza Wolny/Zajęty.
  
Migracja etapowa to doskonałe rozwiązanie dla organizacji, które potrzebują więcej czasu na przeprowadzenie migracji skrzynek pocztowych do programu Microsoft 365 ale mimo to planują zakończyć migrację w ciągu kilku tygodni. Skrzynki pocztowe można migrować partiami. Możesz kontrolować, ile i które skrzynki pocztowe są migrowane w danym momencie. W jednej partii możesz na przykład zmieć skrzynki pocztowe użytkowników z tego samego działu, aby mieć pewność, że wszystkie zostaną przeniesione jednocześnie. Możesz także pozostawić skrzynki pocztowe kierownictwa do czasu ostatniej partii. Podobnie jak w przypadku migracji ponownej, użytkownicy będą musieli ponownie utworzyć swoje Outlook profilów.
  
Jeśli zastanawiasz się nad wykonaniem migracji etapowej, weź pod uwagę kilka kwestii:
  
- Microsoft 365 będzie konieczne połączenie się z serwerami programu Exchange 2007 przy użyciu usługi Outlook Anywhere przez port TCP 443.
    
- Musisz mieć lokalne konto administratora, które ma dostęp do odczytu skrzynek pocztowych użytkowników.
    
- Domeny zaakceptowane Exchange 2007, których zamierzasz używać w usłudze Microsoft 365 muszą zostać dodane jako zweryfikowane domeny w usłudze.
    
- Konieczne będzie utworzenie pliku CSV z pełnym imieniem i nazwiskiem oraz adresem e-mail każdej skrzynki pocztowej, która będzie migrowana w jednej partii. Konieczne będzie także dołączenie nowego hasła dla każdej migrowej skrzynki pocztowej i wysłanie tego hasła do każdego użytkownika. Użytkownik zostanie poproszony o zmianę hasła podczas pierwszego logowania do nowej skrzynki Microsoft 365 pocztowej.
    
- Od czasu rozpoczęcia partii migracji do czasu rozpoczęcia fazy zakończenia program Microsoft 365 okresowo synchronizuje skrzynki pocztowe zawarte w partii Microsoft 365 lokalnymi skrzynkami pocztowymi. Dzięki temu nie musisz się martwić, że podczas migracji zostanie w Twoich lokalnych skrzynkach pocztowych poczty e-mail.
    
- Potrzebna jest licencja Microsoft 365, która obejmuje Exchange Online skrzynek pocztowych użytkowników, które migrowane są.
    
- Użytkownicy będą musieli skonfigurować nowy profil Outlook na każdym ze swoich urządzeń i ponownie pobrać pocztę e-mail. Ilość wiadomości e-mail, które można Outlook, może się różnić. Aby uzyskać więcej informacji, [zobacz Zmienianie liczby wiadomości e-mail, które mają być nadal dostępne w trybie offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Aby uzyskać więcej informacji na temat migracji etapowej, zobacz:
  
- [Co należy wiedzieć o etapowej migracji poczty e-mail](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Przeprowadzanie etapowej migracji poczty e-mail](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Pełna hybrydowa

W pełnej migracji hybrydowej Twoja organizacja ma od kilkuset do kilkudziesięciu tysięcy skrzynek pocztowych, a niektóre lub wszystkie chcesz przenieść do Microsoft 365. Ponieważ tego typu migracje mają zazwyczaj dłuższy czas, migracja hybrydowa umożliwia:
  
- Wyświetlanie użytkownikom lokalnym informacji o wolny/zajętym kalendarzu dla użytkowników Microsoft 365 i odwrotnie.
    
- Zobacz ujednoliconą globalną listę adresową zawierającą adresatów zarówno lokalnych, jak i Microsoft 365.
    
- Wyświetl pełne Outlook adresatów dla wszystkich użytkowników, niezależnie od tego, czy są lokalni, czy Microsoft 365.
    
- Zabezpieczanie komunikacji e-mail między lokalnymi serwerami Exchange i Microsoft 365 przy użyciu usługi TLS i certyfikatów.
    
- Traktuj wiadomości wysyłane między lokalnymi serwerami poczty Exchange i Microsoft 365 jak wewnętrzne, co umożliwia im:
    
  - Należy prawidłowo oceniać i przetwarzać wiadomości przez agentów transportu i zgodności docelowych wiadomości wewnętrznych.
    
  - Pomijanie filtrów spamu.
    
Pełna migracja hybrydowa jest najlepszym rozwiązaniem dla organizacji, które godzą się na pozostawanie w konfiguracji hybrydowej przez wiele miesięcy. Otrzymasz funkcje wymienione wcześniej w tej sekcji, funkcje synchronizacji katalogów, lepiej zintegrowane funkcje zgodności oraz możliwość przenoszenia skrzynek pocztowych do i z usługi Microsoft 365 przy użyciu przenoszenia skrzynek pocztowych w trybie online. Microsoft 365 stanie się rozszerzeniem Twojej organizacji lokalnej.
  
Jeśli zastanawiasz się nad wykonaniem pełnej migracji hybrydowej, weź pod uwagę kilka kwestii:
  
- Pełna migracja hybrydowa nie jest odpowiednia dla wszystkich typów organizacji. Ze względu na złożoność pełnej migracji hybrydowej organizacje mające mniej niż kilkaset skrzynek pocztowych zazwyczaj nie odsądają korzyści, które wyjustują nakład pracy i koszty potrzebne do jej skonfigurowania. Jeśli Twoja organizacja jest właśnie taką organizacją, zalecamy rozważenie migracji etapowej lub etapowej.
    
- Aby działać jako "serwer hybrydowy" w organizacji programu Exchange 2007, musisz wdrożyć co najmniej jeden serwer programu Exchange 2013. Ten serwer będzie komunikować się Microsoft 365 w imieniu Twoich serwerów programu Exchange 2007.
    
- Microsoft 365 będzie konieczne połączenie się z "serwerem hybrydowym" przy użyciu protokołu Outlook Anywhere przez port TCP 443.
    
- Musisz skonfigurować synchronizację katalogów przy użyciu usługi Azure Active Directory (Azure AD) Połączenie między lokalnymi serwerami usługi Active Directory i Microsoft 365.
    
- Użytkownicy będą mogli zalogować się do swoich skrzynek pocztowych usługi Microsoft 365, używając tej samej nazwy użytkownika i hasła co podczas logowania się do sieci lokalnej. (Ta funkcja wymaga usługi Azure AD Połączenie z synchronizacją haseł i/lub usługami federacyjną Active Directory.
    
- Potrzebna jest licencja Microsoft 365, która obejmuje Exchange Online skrzynek pocztowych użytkowników, które migrowane są.
    
- Użytkownicy nie muszą  skonfigurować nowego profilu Outlook na większości swoich urządzeń, chociaż niektóre starsze telefony z systemem Android mogą wymagać nowego profilu. Użytkownicy nie będą muszą ponownie ładować swoich wiadomości e-mail.
    
Jeśli pełna migracja hybrydowa jest dla Ciebie właściwa, zobacz następujące zasoby, które pomogą Ci w migracji:
  
- [Exchange wdrażania](/exchange/exchange-deployment-assistant)
    
- [Exchange Server wdrożeń hybrydowych](/exchange/exchange-hybrid)
    
- [Kreator konfiguracji hybrydowej](/exchange/hybrid-configuration-wizard)
    
- [Kreator konfiguracji hybrydowej : często zadawane pytania](/exchange/hybrid-configuration-wizard-faqs)
    
- [Wymagania wstępne dotyczące wdrożenia hybrydowego](/exchange/hybrid-deployment-prerequisites)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrowanie do nowszej wersji programu Exchange Server

Zdecydowanie uważamy, że najlepszą wartość i środowisko użytkownika można osiągnąć, migrując do Microsoft 365. Rozumiemy jednak, że niektóre organizacje muszą przechowywać swoją pocztę e-mail lokalnie. Może to być spowodowane wymaganiami prawnymi, aby zagwarantować, że dane nie są przechowywane w centrum danych zlokalizowanym w innym kraju lub podobnym. Jeśli zdecydujesz się na lokalne zachowanie poczty e-mail, możesz przeprowadzić migrację środowiska usługi Exchange 2007 do środowiska Exchange 2010, Exchange 2013 lub Exchange 2016.
  
Jeśli nie możesz przeprowadzić migracji do Microsoft 365, zalecamy przeprowadzenie migracji do Exchange 2016. Exchange 2016 zawiera wszystkie funkcje poprzednich wersji programu Exchange. Jego środowisko jest najbardziej zbliżone do możliwości obsługi Microsoft 365, chociaż niektóre funkcje są dostępne tylko w Microsoft 365. Zapoznaj się z kilkoma rzeczami, których brakowało:
  
|**Exchange wersji**|**Funkcje**|
|:-----|:-----|
|Exchange 2010  <br/> | Role-Based kontroli dostępu (uprawnienia bez listy ACL)  <br/>  Outlook Web App zasad skrzynki pocztowej  <br/>  Możliwość udostępniania informacji o wolnym/zajętym i delegowaniu kalendarzy między organizacjami  <br/> |
|Exchange 2013  <br/> | *Funkcje z Exchange 2010 r. i ...*  <br/>  Uproszczona architektura, która zmniejsza liczbę ról serwera do trzech (Skrzynka pocztowa, Dostęp klienta, Transport graniczny)  <br/>  Zasady ochrony przed utratą danych (DLP) ułatwiają zapobieganie wyciekom poufnych informacji  <br/>  Ulepszone Outlook Web App użytkownika  <br/> |
|Exchange 2016  <br/> | *Funkcje z Exchange 2013 i ...*  <br/>  Jeszcze bardziej uproszczono role serwerów: skrzynka pocztowa i transport graniczny  <br/>  Ulepszono DLP oraz integrację z SharePoint  <br/>  Odporność bazy danych  <br/>  Współpraca nad dokumentami online |
   
#### <a name="which-version-should-i-migrate-to"></a>Do której wersji przeprowadzić migrację?

Na początku zalecamy założenie, że migracja będzie się Exchange 2016. Następnie należy skorzystać z poniższych informacji, aby potwierdzić lub wykluczyć założenia dotyczące Exchange 2016. Jeśli z jakiegoś powodu nie możesz przeprowadzić migracji do Exchange 2016, wykonaj tę samą migrację z programem Exchange 2013 i tak dalej.
  
|**Kwestie do rozważenia**|**Więcej informacji**|
|:-----|:-----|
|Daty zakończenia pomocy technicznej  <br/> | Podobnie Exchange 2007, każda wersja pakietu Exchange ma własną datę zakończenia obsługi:  <br/> *Exchange 2010 r*. do stycznia 2020 r.  <br/> *Exchange 2013*– kwiecień 2023 r.  <br/> *Exchange 2016–* październik 2025 r.  <br/>  Im wcześniej zakończy się obsługa techniczna, tym szybciej będzie konieczne przeprowadzenie kolejnej migracji.<br/> |
|Ścieżka migracji do Exchange 2010 i 2013.  <br/> |Poniżej znajdują się ogólne fazy migracji do Exchange 2010 Exchange 2013:  <br/> - Zainstaluj Exchange 2010 lub 2013 do istniejącej Exchange 2007. <br/>— Przenieść usługi i inną infrastrukturę do programu Exchange 2010 lub 2013.<br/>— Przenoszenie skrzynek pocztowych i folderów publicznych Exchange 2010 lub 2013.<br/>- Likwidowanie Exchange serwerach w roku 2007. |
|Ścieżka migracji do Exchange 2016  <br/> |Poniżej znajdują się ogólne fazy migracji do Exchange 2016:  <br/> - Zainstaluj Exchange 2013 do istniejącej Exchange 2007.<br/>— Przenieść usługi i inną infrastrukturę do programu Exchange 2013.<br/>— Przenoszenie skrzynek pocztowych i folderów publicznych Exchange 2013.<br/>- Likwidowanie Exchange serwerach w roku 2007.<br/>- Zainstaluj Exchange 2016 do istniejącej organizacji w Exchange 2013.<br/>— Przenieś skrzynki pocztowe, foldery publiczne, usługi i inną infrastrukturę do programu Exchange 2016 (kolejność nie ma znaczenia). Likwidowanie Exchange serwerach w roku 2013.<br/><br/> **Uwaga:** Migrowanie z Exchange 2013 do Exchange 2016 jest proste. Obie wersje mają niemal identyczne wymagania sprzętowe i są bardzo zgodne. W ten sposób możesz odbudować serwer kupiony na Exchange 2013 i zainstalować na nim Exchange 2016. W przypadku przenoszenia skrzynek pocztowych w trybie online większość użytkowników nawet nie zauważy, że ich skrzynka pocztowa została przeniesiona z serwera, a następnie ponownie przeniesiona po jego odbudowie na Exchange 2016.           |
|Współistnienie wersji  <br/> | Podczas migrowania do...  <br/> **Exchange 2016: Exchange** 2016 nie można zainstalować w organizacji, która zawiera serwer programu Exchange 2007. Najpierw należy przeprowadzić migrację do serwera Exchange 2010 lub 2013 (zdecydowanie zalecamy przeprowadzenie migracji do serwera Exchange 2013), usunąć wszystkie serwery Exchange 2007, a następnie przeprowadzić migrację do serwera Exchange 2016.  <br/> **Exchange 2010 lub Exchange 2013:** Można zainstalować pakiet Exchange 2010 lub Exchange 2013 w istniejącej organizacji Exchange 2007. Dzięki temu można zainstalować co najmniej jeden serwer Exchange 2010 lub 2013 i przeprowadzić migrację.  <br/> |
|Sprzęt serwera  <br/> | Wymagania sprzętowe dotyczące serwera zmieniły się w Exchange 2007. Upewnij się, że sprzęt jest zgodny. Aby uzyskać szczegółowe informacje, zobacz:  <br/> [wymagania Exchange 2016](/Exchange/plan-and-deploy/system-requirements) <br/> [Exchange systemowych do roku 2013](/exchange/exchange-2013-system-requirements-exchange-2013-help) <br/> [Exchange systemu windows 2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141)) <br/>  Można się przekonać, że dzięki znacznej ulepszeniom wydajności usługi Exchange oraz zwiększonej mocy obliczeniowej i pojemności magazynu w nowych serwerach będzie prawdopodobnie potrzebnych mniej serwerów do obsługi takiej samej liczby skrzynek pocztowych.  <br/> |
|Wersja systemu operacyjnego  <br/> | Minimalne obsługiwane wersje systemu operacyjnego w poszczególnych wersjach:  <br/> **Exchange 2016** — Windows Server 2012  <br/> **Exchange 2013** — Windows Server 2008 R2 z dodatkiem SP1  <br/> **Exchange 2010**– Windows Server 2008 z dodatkiem SP2  <br/>  Aby uzyskać więcej informacji na temat obsługi systemu operacyjnego, [Exchange macierz możliwości obsługi](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
|Poziom funkcjonalności lasu usługi Active Directory  <br/> | Minimalne poziomy funkcjonalności lasu usługi Active Directory w poszczególnych wersjach są takie:  <br/> **Exchange 2016** Windows Server 2008 R2 z dodatkiem SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange 2010** Windows Server 2003  <br/>  Aby uzyskać więcej informacji na temat obsługi poziomu funkcjonalności lasu, [Exchange macierz możliwości obsługi](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
|Office wersji klienta  <br/> | Minimalne obsługiwane Office klienta w poszczególnych wersjach są:  <br/> **Exchange 2016**–Office 2010 (z najnowszymi aktualizacjami)  <br/> **Exchange 2013**– Office 2007 z dodatkiem SP3  <br/> **Exchange 2010**–Office 2003  <br/>  Aby uzyskać więcej informacji na Office obsługi klientów, zobacz [Exchange macierz możliwości obsługi](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Jak przeprowadzić migrację?

Jeśli zdecydujesz się zachować pocztę e-mail lokalnie, skorzystaj z następujących zasobów, aby pomóc w migracji:
  
- [Exchange wdrażania](/exchange/exchange-deployment-assistant)
    
- Zmiany schematu usługi Active Directory Exchange [2016](/Exchange/plan-and-deploy/active-directory/ad-schema-changes), [2013](/exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Wymagania systemowe dotyczące Exchange [2016](/Exchange/plan-and-deploy/system-requirements), [2013](/exchange/exchange-2013-system-requirements-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141))
    
- Wymagania wstępne dotyczące Exchange [2016](/Exchange/plan-and-deploy/prerequisites), [2013](/exchange/exchange-2013-prerequisites-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/bb691354(v=exchg.141))
    
## <a name="get-help"></a>Uzyskiwanie pomocy

Jeśli migrujesz do usługi Microsoft 365, być może kwalifikujesz się do korzystania z naszej usługi FastTrack Microsoft. FastTrack zawiera najlepsze rozwiązania, narzędzia i zasoby, dzięki których migracja do Microsoft 365 się tak bezproblemowo, jak to tylko możliwe. Co więcej, inżynier pomocy technicznej pomoże Ci przejść przez proces migracji, od planowania i projektowania po migrację ostatniej skrzynki pocztowej. Aby uzyskać więcej informacji FastTrack, zobacz [Microsoft FastTrack](https://fasttrack.microsoft.com/).
  
Jeśli podczas migracji do programu Microsoft 365 występują problemy i nie korzystasz z programu FastTrack lub podczas migracji do nowszej wersji programu Exchange Server, tutaj znajdziesz pomoc. Oto niektóre zasoby, z których możesz skorzystać:
  
- [Społeczność techniczna](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
    
- [Obsługa klienta](https://support.microsoft.com/gp/support-options-for-business)
    
## <a name="related-topics"></a>Tematy pokrewne

[Zasoby ułatwiające uaktualnienie serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md)