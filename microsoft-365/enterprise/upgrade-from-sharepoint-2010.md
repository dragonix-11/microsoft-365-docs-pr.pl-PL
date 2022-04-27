---
title: Uaktualnianie z SharePoint 2010 r.
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 04/13/2020
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: Znajdź informacje i zasoby do uaktualnienia z SharePoint 2010 i SharePoint Server 2010. Pomoc techniczna dla obu kończy się 13 kwietnia 2021 r.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: be25dd1260c378146d292e6487329065a3020ac8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077398"
---
# <a name="upgrading-from-sharepoint-2010"></a>Uaktualnianie z SharePoint 2010 r.

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

**13 kwietnia** 2021 r. usługi Microsoft SharePoint 2010 i SharePoint Server 2010 zakończą wsparcie. Ten artykuł zawiera zasoby ułatwiające migrowanie istniejących danych SharePoint Server 2010 do usługi SharePoint Online w Microsoft 365 lub uaktualnienie lokalnego środowiska SharePoint Server 2010.

## <a name="what-is-end-of-support"></a>Co to jest *koniec wsparcia*?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, podczas którego otrzymują nowe funkcje, poprawki błędów, poprawki zabezpieczeń itd. Po dacie zakończenia wsparcia produkt nie przestaje działać, ale firma Microsoft nie zapewnia już następujących elementów:

- Pomoc techniczna dotycząca problemów, które mogą wystąpić.

- Poprawki błędów w przypadku problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.

- Poprawki zabezpieczeń dla luk w zabezpieczeniach, które mogą narazić serwer na naruszenia zabezpieczeń.

- Aktualizacje stref czasowych.

Oznacza to, że nie będzie żadnych dalszych aktualizacji, poprawek ani poprawek dla produktu (w tym poprawek/poprawek zabezpieczeń). pomoc techniczna firmy Microsoft w pełni przesunie wysiłki na rzecz wsparcia do nowszych wersji.

W miarę zbliżania się zakończenia obsługi programu SharePoint Server 2010 usuń dane, których nie potrzebujesz, zanim uaktualnisz produkt i zmigrujesz ważne dane.

> [!NOTE]
> Cykl życia oprogramowania zazwyczaj trwa dziesięć lat od pierwszej wersji. [Dostawcy rozwiązań firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) mogą pomóc w uaktualnieniu do następnej wersji oprogramowania lub migracji do Microsoft 365 migracji (lub obu). Upewnij się, że znasz również daty zakończenia wsparcia dla krytycznych technologii bazowych, szczególnie w przypadku wersji Microsoft SQL Server używanych z SharePoint. Aby uzyskać więcej informacji, zobacz [Zasady stałego cyklu życia](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planować

Sprawdź daty zakończenia pomocy technicznej w [witrynie cyklu życia produktu](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). Zaplanuj uaktualnienia lub migracje z myślą o tych datach. Pamiętaj, że produkt *nie przestanie działać* w podanym dniu. Ponieważ jednak instalacja nie będzie już poprawiana po tej dacie, należy zaplanować płynne przejście do następnej wersji produktu.

Ta macierz pomaga wykreślić kurs między opcjami migracji:

|Koniec produktu pomocy technicznej|Dobry |Najlepszych|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (lokalnie)|SharePoint Online|
||hybrydowy serwer SharePoint Server 2013 z usługą SharePoint Online|SharePoint Server 2016 (lokalnie)|
|||wyszukiwanie hybrydowe w chmurze SharePoint|

Jeśli wybierzesz opcję na niskim końcu skali (dobrej), musisz rozpocząć planowanie kolejnego uaktualnienia wkrótce po migracji z programu SharePoint Server 2010.

Poniżej przedstawiono trzy ścieżki, które można wykonać, aby uniknąć zakończenia obsługi programu SharePoint Server 2010.

![SharePoint Ścieżki uaktualnienia serwera 2010.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> Zakończenie wsparcia dla SharePoint Server 2010 i SharePoint Foundation 2010 jest obecnie zaplanowane na 13 kwietnia 2021 r. Pamiętaj jednak, aby sprawdzić [witrynę cyklu życia produktu](https://support.microsoft.com/lifecycle) pod kątem najbardziej aktualnych dat.

## <a name="whats-next"></a>Co dalej?

SharePoint Server 2013 i SharePoint Foundation 2013 można zainstalować lokalnie na własnych serwerach. Możesz też użyć usługi SharePoint Online, która jest usługą online, która jest częścią Microsoft 365. Możesz wybrać następujące opcje:

- Migrowanie do usługi SharePoint Online.

- Uaktualnij lokalny serwer SharePoint Lub SharePoint Foundation.

- Wykonaj oba powyższe czynności.

- Zaimplementuj [rozwiązanie hybrydowe SharePoint](/sharepoint/hybrid/hybrid).

Rozważ ukryte koszty utrzymania farmy serwerów, w tym utrzymywanie lub migrowanie dostosowań i uaktualnianie sprzętu. Jeśli zostały uwzględnione te czynniki, uaktualnienie lokalne będzie łatwiejsze. Jeśli uruchamiasz farmę na starszych serwerach SharePoint Bez dużych dostosowań, możesz skorzystać z planowanej migracji do usługi SharePoint Online. W przypadku lokalnego środowiska SharePoint Server możesz również rozważyć przeniesienie niektórych danych w usłudze SharePoint Online, aby zmniejszyć obciążenie związane z zarządzaniem sprzętem.

> [!NOTE]
> SharePoint administratorzy mogą utworzyć subskrypcję Microsoft 365, skonfigurować nowe witryny SharePoint Online, a następnie odciąć się od SharePoint Server 2010, pobierając tylko podstawowe dokumenty do nowych witryn. Następnie wszystkie pozostałe dane można opróżnić z lokacji programu SharePoint Server 2010 do archiwów lokalnych.

|SharePoint Online|lokalny serwer SharePoint|
|---|---|
|Wysoki koszt w czasie (planowanie/wykonywanie/weryfikacja)|Wysoki koszt w czasie (planowanie/wykonywanie/weryfikacja)|
|Niższy koszt w funduszach (bez zakupów sprzętu)|Wyższy koszt w funduszach (zakupy sprzętu)|
|Jednorazowy koszt migracji|Jednorazowy koszt powtórzony na przyszłą migrację|
|Niski całkowity koszt posiadania/konserwacji|Wysoki całkowity koszt posiadania/konserwacji|

Jednorazowe przejście do Microsoft 365 będzie miało wyższy koszt podczas organizowania danych i decydowania o tym, co należy zabrać do chmury i co pozostawić. Jednak po migracji danych przyszłe uaktualnienia będą automatyczne, ponieważ nie trzeba już zarządzać aktualizacjami sprzętu i oprogramowania. A czas dostępności farmy będzie wspierany przez [umowę dotyczącą poziomu usług firmy Microsoft (SLA).](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)

### <a name="migrate-to-sharepoint-online"></a>Migrowanie do usługi SharePoint Online

Upewnij się, że usługa SharePoint Online oferuje wszystkie potrzebne funkcje. Zobacz [opis usługi SharePoint](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

Nie można migrować bezpośrednio z programu SharePoint Server 2010 (lub SharePoint Foundation 2010) do usługi SharePoint Online. Tak wiele prac związanych z migracją jest wykonywanych ręcznie. Jednak ten etap daje możliwość przyśwłaszczenia danych i witryn, które nie są już potrzebne przed przeniesieniem. Inne dane można zarchiwizować w magazynie. 

Pamiętaj, że SharePoint Server 2010 i SharePoint Foundation 2010 nie przestaną działać po zakończeniu wsparcia technicznego. Dzięki temu administratorzy mogą mieć okres, kiedy SharePoint nadal działa, jeśli ich klienci zapomną przenieść część swoich danych.

W przypadku uaktualnienia do wersji SharePoint Server 2013 lub SharePoint Server 2016 i podjęcia decyzji o umieszczeniu danych w usłudze SharePoint Online możesz użyć [interfejsu API migracji SharePoint do migracji](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) informacji do OneDrive dla Firm.

|zalety usługi SharePoint Online|SharePoint w trybie online|
|---|---|
|Firma Microsoft dostarcza sprzęt SPO i całą administrację sprzętem.|Dostępne funkcje mogą się różnić w zależności od lokalnego serwera SharePoint i spo.|
|Jesteś administratorem programu Sharepoint lub administratorem globalnym subskrypcji i możesz przypisywać administratorów do witryn SPO.|Niektóre akcje dostępne dla administratora farmy w środowisku lokalnym SharePoint Server nie istnieją (lub nie są konieczne) w roli administratora SharePoint w Microsoft 365. Jednak SharePoint Administracja, Administracja zbiorem witryn i Własność witryny są lokalne dla Organizacji.|
|Firma Microsoft stosuje poprawki, poprawki i aktualizacje bazowego sprzętu i oprogramowania, w tym serwerów SQL, na których działa SharePoint Online.|Ponieważ nie ma dostępu do podstawowego systemu plików w usłudze, dostosowywanie jest ograniczone.|
|Firma Microsoft publikuje [umowy dotyczące poziomu usług](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) i szybko przechodzi do rozwiązywania zdarzeń na poziomie usługi.|Kopie zapasowe i przywracanie oraz inne opcje odzyskiwania są zautomatyzowane przez usługę w usłudze SharePoint Online. Kopie zapasowe są zastępowane, jeśli nie są używane.|
|Testy zabezpieczeń i dostrajanie wydajności serwera są stale przeprowadzane w usłudze przez firmę Microsoft.|Zmiany interfejsu użytkownika i innych funkcji SharePoint są instalowane przez usługę i mogą wymagać włączania lub wyłączania.|
|Microsoft 365 spełnia wiele standardów branżowych: [oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home).|[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) pomoc dotycząca migracji jest ograniczona.  <br/> Znaczna część uaktualnienia będzie wykonywana ręcznie lub za pośrednictwem interfejsu API migracji spo opisanego w [planie migracji zawartości SharePoint Online i OneDrive Migration](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|pomoc techniczna firmy Microsoft inżynierowie i pracownicy centrum danych nie mają nieograniczonego dostępu administratora do Subskrypcji.|Mogą wystąpić dodatkowe koszty, jeśli infrastruktura sprzętowa musi zostać uaktualniona w celu obsługi nowszej wersji SharePoint lub jeśli do uaktualnienia jest wymagana farma pomocnicza.|
|Dostawcy rozwiązań mogą pomóc w jednorazowym zadaniu migrowania danych do usługi SharePoint Online.|Nie wszystkie zmiany w usłudze SharePoint Online znajdują się w twojej kontroli. Po migracji różnice w projekcie w menu, bibliotekach i innych funkcjach mogą tymczasowo wpływać na użyteczność.|
|Produkty online są automatycznie aktualizowane w całej usłudze. Funkcje mogą być przestarzałe, ale nie ma prawdziwego końca cyklu życia pomocy technicznej.|Istnieje cykl życia usługi SharePoint Server lub SharePoint Foundation, a także podstawowe serwery SQL.|

Jeśli zdecydujesz się utworzyć nową witrynę Microsoft 365 i ręcznie zmigrujesz do niej dane zgodnie z potrzebami, sprawdź [opcje Microsoft 365](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Uaktualnianie lokalnego serwera SharePoint

Od SharePoint Server 2019 uaktualnienia muszą być uaktualnione *szeregowo*. Nie ma możliwości uaktualnienia z programu SharePoint Server 2010 do SharePoint Server 2016 lub bezpośrednio do SharePoint 2019. Ścieżka uaktualniania szeregowego:

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

To zajmie trochę czasu i planuje podążać całą ścieżką od SharePoint 2010 do SharePoint Server 2016.It will take time and planning to follow the entire path from SharePoint 2010 to SharePoint Server 2016. Uaktualnienia obejmują koszty sprzętu (serwery SQL również muszą zostać uaktualnione), oprogramowania i administracji. Ponadto dostosowania mogą wymagać uaktualnienia lub nawet porzucenia. Przed uaktualnieniem farmy SharePoint Server upewnij się, że dokumentujesz dostosowania krytyczne.

> [!NOTE]
> Istnieje możliwość utrzymania farmy SharePoint 2010 r., zainstalowania farmy SharePoint Server 2016 na nowym sprzęcie (tak aby oddzielne farmy działały obok siebie), a następnie zaplanować i wykonać ręczną migrację zawartości (na przykład w celu pobrania i ponownego przekazania zawartości). Istnieją jednak potencjalne pułapki dla tych ręcznych ruchów, takie jak dokumenty pochodzące z 2010 r. posiadające bieżące konto ostatnio zmodyfikowane z aliasem konta, które wykonuje ręczne przenoszenie. A niektóre prace muszą być wykonane z wyprzedzeniem, takie jak ponowne tworzenie witryn, podwitryn, uprawnień i struktur listy. Pamiętaj, aby wyczyścić środowisko przed uaktualnieniem. Zastanów się, jakie dane można przenieść do magazynu lub które nie są już potrzebne. Może to zmniejszyć wpływ migracji. Upewnij się, że istniejąca farma działa przed uaktualnieniem i (na pewno) przed likwidacją!

Pamiętaj, aby przejrzeć *obsługiwane i nieobsługiwane ścieżki uaktualniania*:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Jeśli masz *dostosowania*, ważne jest, aby zaplanować każdy krok w ścieżce migracji:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Przewaga lokalna|Niekorzystna sytuacja w środowisku lokalnym|
|---|---|
|Pełna kontrola nad wszystkimi aspektami farmy SharePoint (i jej SQL) od sprzętu serwera do góry.|Wszystkie przerwy i poprawki są odpowiedzialne za firmę. Ale możesz zaangażować płatne pomoc techniczna firmy Microsoft, jeśli twój produkt nie jest po zakończeniu wsparcia.|
|Pełny zestaw funkcji lokalnego serwera SharePoint z opcją połączenia farmy lokalnej z subskrypcją usługi SharePoint Online za pośrednictwem hybrydowej.|Uaktualnianie, poprawki, poprawki zabezpieczeń, uaktualnienia sprzętu i cała konserwacja serwera SharePoint Server i jego farmy SQL są zarządzane lokalnie.|
|Pełny dostęp do większych opcji dostosowywania niż w przypadku usługi SharePoint Online.|[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home) muszą być ręcznie skonfigurowane lokalnie.|
|Testowanie zabezpieczeń i dostrajanie wydajności serwera odbywa się w środowisku lokalnym pod kontrolą użytkownika.|Microsoft 365 mogą udostępniać funkcje SharePoint Online, które nie współdziałają z lokalnym serwerem SharePoint.|
|Dostawcy rozwiązań mogą pomóc w migracji danych do następnej wersji programu SharePoint Server (i nie tylko).|Lokacje serwera SharePoint nie będą automatycznie używać certyfikatów [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), jak pokazano w SharePoint Online.|
|Pełna kontrola nad konwencjami nazewnictwa oraz tworzeniem i przywracaniem kopii zapasowych oraz innymi opcjami odzyskiwania w środowisku lokalnym serwera SharePoint.|SharePoint Serwer lokalny jest wrażliwy na cykle życia produktów.|

### <a name="upgrade-resources"></a>Uaktualnianie zasobów

Rozpocznij od porównania wymagań dotyczących sprzętu i oprogramowania. Jeśli bieżące środowisko nie spełnia podstawowych wymagań, może być konieczne uaktualnienie sprzętu w farmie lub serwerów SQL. 

Możesz zdecydować się na przeniesienie niektórych witryn na "wiecznie zielony" sprzęt SharePoint Online. Po dokonaniu oceny postępuj zgodnie z obsługiwanymi ścieżkami i metodami uaktualniania.

- *Wymagania dotyczące sprzętu/oprogramowania dla:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Granice i limity oprogramowania dla:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Omówienie procesu uaktualniania dla:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>Tworzenie rozwiązania hybrydowego przy użyciu usługi SharePoint Online i lokalnego serwera SharePoint Server

Konfiguracja hybrydowa zapewnia najlepsze rozwiązanie zarówno w środowisku lokalnym, jak i online w przypadku niektórych potrzeb związanych z migracją. Możesz połączyć farmy SharePoint Server 2013, 2016 lub 2019 z usługą SharePoint Online, aby utworzyć hybrydową SharePoint: [dowiedz się więcej o SharePoint rozwiązaniach hybrydowych](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).

Jeśli celem migracji jest hybrydowa farma serwerów SharePoint Server, ustal, które witryny i użytkownicy mają zostać przeniesione w tryb online, a którzy muszą pozostać lokalnie. Klasyfikowanie zawartości farmy serwera SharePoint jako wysokiego, średniego lub niskiego wpływu na firmę może pomóc w podjęciu tej decyzji. Może być konieczne udostępnienie kont użytkowników tylko na potrzeby logowania i indeksu wyszukiwania serwera SharePoint za pomocą usługi SharePoint Online. Jednak ten czynnik może nie być jasny, dopóki nie przyjrzysz się, w jaki sposób witryny są używane. Jeśli firma zdecyduje się później przeprowadzić migrację całej zawartości do usługi SharePoint Online, możesz przenieść wszystkie pozostałe konta i dane do trybu online i zlikwidować farmę lokalną. Zarządzanie farmą SharePoint i administrowanie nią będzie od tego momentu wykonywane za pośrednictwem konsoli Microsoft 365.

Pamiętaj, aby zapoznać się z istniejącymi typami hybryd i skonfigurować połączenie między lokalną farmą SharePoint a subskrypcją Microsoft 365.

|Opcja|Opis|
|---|---|
|[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home).|[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pomoc dotycząca migracji jest ograniczona.<br/><br/> Znaczna część uaktualnienia będzie wykonywana ręcznie lub za pośrednictwem interfejsu API migracji spo opisanego w [planie migracji zawartości SharePoint Online i OneDrive Migration](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|pomoc techniczna firmy Microsoft inżynierowie i pracownicy centrum danych nie mają nieograniczonego dostępu administratora do Subskrypcji.|Mogą wystąpić dodatkowe koszty, jeśli infrastruktura sprzętowa musi zostać uaktualniona w celu obsługi nowszej wersji SharePoint lub jeśli wymagana jest farma pomocnicza.|
|Partnerzy mogą pomóc w jednorazowym zadaniu migrowania danych do SharePoint Online.||
|Produkty online są automatycznie aktualizowane w całej usłudze. Funkcje mogą być przestarzałe, ale nie ma prawdziwego końca obsługi.||

Jeśli zdecydujesz się utworzyć nową witrynę Microsoft 365 i ręcznie migrować do niej dane zgodnie z potrzebami, sprawdź [opcje Microsoft 365](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Uaktualnianie lokalnego serwera SharePoint

Nie ma możliwości pominięcia wersji w SharePoint uaktualnień. Oznacza to, że uaktualnienia są uruchamiane szeregowo:

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Aby wykonać całą ścieżkę z SharePoint 2007 do SharePoint Server 2016 będzie oznaczać znaczną inwestycję czasu i będzie obejmować sprzęt (SQL serwery muszą być również uaktualnione), oprogramowanie i koszty administracyjne. Dostosowania będą musiały zostać uaktualnione lub porzucone zgodnie z krytycznością funkcji.

> [!NOTE]
> Istnieje możliwość utrzymania farmy SharePoint 2007 r., zainstalowania farmy SharePoint Server 2016 na nowym sprzęcie (tak aby oddzielne farmy działały obok siebie), a następnie zaplanować i wykonać ręczną migrację zawartości (na przykład w celu pobrania i ponownego przekazania zawartości). Istnieją jednak pewne wady tych ręcznych ruchów, takie jak przenoszenie dokumentów zastępujących ostatnie zmodyfikowane konto aliasem konta, które wykonuje ręczne przenoszenie. Z wyprzedzeniem należy wykonać wiele pracy, na przykład ponownie utworzyć witryny, podwitryny, uprawnienia i struktury listy. W każdym razie zastanów się, jakie dane można przenieść do magazynu lub które nie są już potrzebne, aby zmniejszyć wpływ migracji.

Przed uaktualnieniem upewnij się, że środowisko zostało wyczyszczone. Przed uaktualnieniem upewnij się, że istniejąca farma działa, a na pewno przed likwidacją!

Pamiętaj, aby przejrzeć *obsługiwane i nieobsługiwane ścieżki uaktualniania*:

- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Jeśli masz *dostosowania*, niezwykle ważne jest zaplanowanie uaktualnienia dla każdego kroku w ścieżce migracji:

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Lokalny pro|Lokalna konfiguracja|
|---|---|
|Pełna kontrola nad wszystkimi aspektami farmy SharePoint od sprzętu serwera do góry.|Wszystkie przerwy i poprawki są odpowiedzialne za firmę. (Ale możesz zaangażować płatne pomoc techniczna firmy Microsoft, jeśli twój produkt nie jest po zakończeniu wsparcia).|
|Pełny zestaw funkcji lokalnego serwera SharePoint z opcją połączenia farmy lokalnej z subskrypcją usługi SharePoint Online za pośrednictwem hybrydowej.|Uaktualnianie, poprawki, poprawki zabezpieczeń i cała konserwacja lokalnie zarządzanego serwera SharePoint Server.|
|Pełny dostęp w celu większego dostosowania.|[Oferty zgodności firmy Microsoft](/compliance/regulatory/offering-home) muszą być ręcznie skonfigurowane lokalnie.|
|Testowanie zabezpieczeń i dostrajanie wydajności serwera odbywa się w środowisku lokalnym pod kontrolą użytkownika.|Microsoft 365 mogą udostępniać funkcje SharePoint Online, które nie współdziałają z lokalnym serwerem SharePoint.|
|Partnerzy mogą pomóc w migracji danych do następnej wersji programu SharePoint Server (i nie tylko).|Lokacje serwera SharePoint nie będą automatycznie używać certyfikatów [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), jak pokazano w SharePoint Online.|
|Pełna kontrola nad konwencjami nazewnictwa oraz tworzeniem i przywracaniem kopii zapasowych oraz innymi opcjami odzyskiwania w środowisku lokalnym serwera SharePoint.|SharePoint Serwer lokalny jest wrażliwy na cykle życia produktów.|

### <a name="upgrade-resources"></a>Uaktualnianie zasobów

Zacznij od wiedzy, że spełniasz wymagania sprzętowe i programowe, a następnie postępuj zgodnie z obsługiwanymi metodami uaktualniania.

- *Wymagania dotyczące sprzętu/oprogramowania dla*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Granice i limity oprogramowania dla*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Omówienie procesu uaktualniania dla*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Tworzenie rozwiązania hybrydowego SharePoint między usługą SharePoint Online a środowiskiem lokalnym

Jeśli odpowiedź na potrzeby migracji znajduje się gdzieś między kontrolą oferowaną przez środowisko lokalne a niższym kosztem posiadania oferowanym przez usługę SharePoint Online, możesz połączyć farmy SharePoint Server 2013 lub 2016 z usługą SharePoint Online za pośrednictwem hybrydowych. [Dowiedz się więcej o rozwiązaniach hybrydowych SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Jeśli zdecydujesz, że hybrydowa farma SharePoint Server przyniesie korzyści Twojej firmie, zapoznaj się z istniejącymi typami hybryd i sposobem konfigurowania połączenia między lokalną farmą SharePoint a subskrypcją Microsoft 365.

Możesz utworzyć Microsoft 365 środowisko deweloperskie/testowe, które można skonfigurować za pomocą [przewodników laboratorium testowego](m365-enterprise-test-lab-guides.md). Po uzyskaniu wersji próbnej lub zakupie subskrypcji Microsoft 365 można utworzyć zbiory witryn, sieci Web i biblioteki dokumentów w usłudze SharePoint Online, do której można migrować dane. Możesz przeprowadzić migrację ręcznie, za pomocą interfejsu API migracji lub, jeśli chcesz przeprowadzić migrację zawartości witryny Moja witryna do OneDrive dla Firm, za pomocą kreatora hybrydowego.

> [!NOTE]
> Aby użyć opcji hybrydowej, farma SharePoint Server 2010 musi zostać najpierw uaktualniona lokalnie do SharePoint Server 2013 lub 2016. SharePoint Foundation 2010 i SharePoint Foundation 2013 nie obsługują połączeń hybrydowych z usługą SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Podsumowanie opcji dla klientów i serwerów Office 2010 oraz Windows 7

Aby zapoznać się z wizualnym podsumowaniem opcji uaktualniania, migracji i przenoszenia do chmury dla klientów i serwerów Office 2010 r. oraz Windows 7, zobacz [plakat zakończenia pomocy technicznej](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Koniec wsparcia dla klientów i serwerów Office 2010 oraz plakat Windows 7.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Ten plakat przedstawia różne ścieżki, które można wykonać, aby uniknąć Office produktów klienckich i serwerowych 2010 oraz Windows 7 koniec wsparcia, z preferowanymi ścieżkami i obsługą opcji w Microsoft 365 Enterprise wyróżnione.

Możesz również [pobrać](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) ten plakat i wydrukować go w formacie literowym, prawnym lub tabloidowym (11 x 17).

## <a name="related-articles"></a>Artykuły pokrewne

[Zasoby ułatwiające uaktualnienie z serwerów i klientów Office 2007 lub 2010](upgrade-from-office-2010-servers-and-products.md)

[Omówienie procesu uaktualniania z SharePoint 2010 r. do SharePoint 2013 r.](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[Najlepsze rozwiązania dotyczące uaktualniania z SharePoint 2010 r. do SharePoint 2013 r.](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[Rozwiązywanie problemów z uaktualnianiem bazy danych w SharePoint 2013 r.](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[Wyszukaj dostawców rozwiązań firmy Microsoft, aby ułatwić uaktualnienie](https://go.microsoft.com/fwlink/?linkid=841249)

[Zaktualizowano zasady obsługi produktu dla SharePoint 2013 r.](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[Zaktualizowano zasady obsługi produktu dla SharePoint Server 2016](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
