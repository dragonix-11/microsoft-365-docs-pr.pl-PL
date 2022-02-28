---
title: Uaktualnianie z SharePoint 2010 r.
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
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
description: Znajdź informacje i zasoby do uaktualnienia z wersji SharePoint 2010 i SharePoint Server 2010. Obsługa obu tych dni zakończy się 13 kwietnia 2021 r.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7ce6b333e39d02000514c174579a1ad0fa816771
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988331"
---
# <a name="upgrading-from-sharepoint-2010"></a>Uaktualnianie z SharePoint 2010 r.

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Z SharePoint 13 kwietnia 2021 r. zakończy się wsparcie techniczne dla oprogramowania Microsoft SharePoint 2010 i SharePoint Server **2010**. Ten artykuł zawiera zasoby pomocne podczas migracji istniejących danych z programu SharePoint Server 2010 do usługi SharePoint Online w programie Microsoft 365 lub uaktualniania lokalnego środowiska programu SharePoint Server 2010.

## <a name="what-is-end-of-support"></a>Co oznacza *zakończenie wsparcia technicznego*?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, w trakcie którego uzyskają nowe funkcje, poprawki, poprawki zabezpieczeń i tak dalej. Po zakończeniu wsparcia technicznego produkt nie przestanie działać, ale firma Microsoft już nie udostępnia:

- pomoc techniczną w zakresie mogącego wystąpić problemów;

- Poprawki błędów dotyczące problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.

- Poprawki zabezpieczeń dotyczące luk, które mogą nabędać serwer na naruszenie bezpieczeństwa.

- Aktualizacje stref czasowych.

Oznacza to, że nie będą dostępne żadne dalsze aktualizacje, poprawki ani poprawki dla tego produktu (w tym poprawki zabezpieczeń/poprawki). Pomoc techniczna firmy Microsoft całkowicie przesunięła swoje działania na rzecz obsługi najnowszych wersji.

Po zakończeniu obsługi programu SharePoint Server 2010 usuń dane, których już nie potrzebujesz, przed uaktualnieniem produktu i przeprowadzeniem migracji ważnych danych.

> [!NOTE]
> Cykl życia oprogramowania zazwyczaj trwa dziesięć lat od wydania początkowego. [Dostawcy rozwiązań firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) mogą pomóc w uaktualnieniu do następnej wersji oprogramowania lub migracji do nowej Microsoft 365 migracji (lub obu). Upewnij się, że wiesz, kiedy kończysz wsparcie techniczne dla krytycznych technologii, zwłaszcza w przypadku wersji programu Microsoft SQL Server, z SharePoint. Aby uzyskać więcej informacji, zobacz [Stałe zasady cyklu życia](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planowanie z wyprzedzeniem

Sprawdź daty zakończenia obsługi w [witrynie Cyklu życia produktu](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). Planuj uaktualnienia i migracje, pamiętasz o tych datach. Pamiętaj, że produkt *nie przestanie działać w* dniu na liście. Jednak ponieważ po tym dniu instalacja nie będzie już poprawiana, należy zaplanować płynne przejście do następnej wersji produktu.

Ta macierz pomaga w kreślenia kursu wśród opcji migracji:

|Zakończenie produktu pomocy technicznej|Dobra |Najlepsza|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (lokalnie)|SharePoint Online|
||SharePoint hybrydowy programu SharePoint Server 2013 z usługą SharePoint Online|SharePoint Server 2016 (lokalnie)|
|||SharePoint wyszukiwania hybrydowego w chmurze|

Jeśli wybierzesz opcję na końcu skali (dobra), wkrótce po migracji z programu SharePoint Server 2010 musisz rozpocząć planowanie kolejnego uaktualnienia.

Oto trzy ścieżki, które możesz wybrać, aby uniknąć zakończenia obsługi programu SharePoint Server 2010.

![SharePoint uaktualnianie do programu Server 2010.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> Zakończenie obsługi dla programu SharePoint Server 2010 i SharePoint Foundation 2010 jest obecnie zaplanowane na 13 kwietnia 2021 r. Jednak upewnij się, że w [witrynie cyklu życia produktu](https://support.microsoft.com/lifecycle) nie ma aktualnych dat.

## <a name="whats-next"></a>Co dalej?

SharePoint Server 2013 i SharePoint Foundation 2013 można zainstalować lokalnie na Twoich własnych serwerach. Możesz też użyć usługi SharePoint Online, która jest usługą online, która jest częścią Microsoft 365. Możesz:

- Migrowanie do usługi SharePoint Online.

- Uaktualnienie SharePoint serwera lub SharePoint lokalnej programu Foundation.

- Wykonaj oba powyższe.

- Wdrożenie SharePoint [hybrydowego](/sharepoint/hybrid/hybrid).

Rozważ ukryte koszty konserwacji farmy serwerów, w tym utrzymywanie lub migrowanie dostosowań i uaktualnianie sprzętu. Jeśli uwzględnić te czynniki, łatwiej będzie uaktualnić go lokalnie. Jeśli twoja farma będzie działać na starszych serwerach SharePoint bez intensywnego dostosowania, możesz skorzystać z planowanej migracji do usługi SharePoint Online. W przypadku lokalnego środowiska programu SharePoint Server możesz również rozważyć przeniesienie części danych do usługi SharePoint Online w celu zmniejszenia obciążenia związanego z zarządzaniem sprzętem.

> [!NOTE]
> SharePoint administratorzy mogą utworzyć subskrypcję usługi Microsoft 365, skonfigurować nowe witryny usługi SharePoint Online, a następnie odciąć się od programu SharePoint Server 2010, przejmować do nowych witryn tylko podstawowe dokumenty. Następnie wszelkie pozostałe dane mogą zostać rozładowane z witryny programu SharePoint Server 2010 do archiwów lokalnych.

|SharePoint Online|SharePoint serwera lokalnego|
|---|---|
|Wysoki koszt w czasie (planowanie/wykonywanie/weryfikacja)|Wysoki koszt w czasie (planowanie/wykonywanie/weryfikacja)|
|Niższy koszt w funduszach (brak zakupów sprzętu)|Wyższy koszt w funduszach (zakupy sprzętu)|
|One-time cost in migration|Koszt powtarzany raz na jedną przyszłą migrację|
|Niski całkowity koszt utrzymania/konserwacji|Wysoki całkowity koszt utrzymania/konserwacji|

Przejście do centrum danych Microsoft 365 będzie kosztować więcej podczas organizowania danych i decydowania, co przenieść do chmury, a co zostawić. Jednak po migracji danych przyszłe uaktualnienia będą automatyczne, ponieważ nie będzie już konieczne zarządzanie aktualizacjami sprzętu i oprogramowania. Okres świadczenia pomocy technicznej dla farmy będzie sięgać w umowie dotyczącej [poziomu usług (SLA) firmy Microsoft](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement).

### <a name="migrate-to-sharepoint-online"></a>Migrowanie do usługi SharePoint Online

Upewnij się, SharePoint online oferuje wszystkie funkcje, których potrzebujesz. Zobacz [SharePoint opis usługi](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

Nie można przeprowadzić migracji bezpośrednio z programu SharePoint Server 2010 (ani programu SharePoint Foundation 2010) do usługi SharePoint Online. Praca nad migracją jest więc praca ręczna. Jednak ten etap umożliwia dostęp do danych i witryn, które nie są już potrzebne przed przeniesieniem. Możesz zarchiwizować inne dane w magazynie. 

Pamiętaj, że SharePoint Server 2010 i SharePoint Foundation 2010 nie przestaną działać po zakończeniu wsparcia technicznego. Dzięki temu administratorzy mogą mieć czas, SharePoint nadal działać, jeśli ich klienci zapomnią przenieść część danych.

Jeśli po uaktualnieniu do programu SharePoint Server 2013 lub SharePoint Server 2016 zdecydujesz się na przeniesienie danych do usługi SharePoint Online, możesz przeprowadzić migrację informacji do usługi OneDrive dla Firm za pomocą interfejsu [API](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) migracji systemu SharePoint.

|SharePoint online|SharePoint online|
|---|---|
|Firma Microsoft dostarcza sprzęt usługi SPO i całe administrowanie sprzętem.|Dostępne funkcje mogą się różnić SharePoint lokalnym serwerem i usługą SPO.|
|Jesteś administratorem programu SharePoint lub administratorem globalnym swojej subskrypcji i możesz przypisywać administratorów do witryn usługi SPO.|Niektóre akcje dostępne dla administratora farmy w lokalnym programie SharePoint Server nie istnieją (lub nie są potrzebne) w roli administratora SharePoint w programie Microsoft 365. Jednak SharePoint, Administracja zbiorem witryn i Własność witryny są lokalne dla Twojej organizacji.|
|Firma Microsoft stosuje poprawki i aktualizacje sprzętu i oprogramowania, w tym do serwerów SQL, na których działa aplikacja SharePoint Online.|Ponieważ nie ma dostępu do źródłowego systemu plików w usłudze, dostosowywanie jest ograniczone.|
|Firma Microsoft publikuje [umowy dotyczące poziomu usług](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) i szybko przechodzi w celu rozwiązania problemów z poziomem usług.|Tworzenie i przywracanie kopii zapasowych oraz inne opcje odzyskiwania są zautomatyzowane przez usługę w usłudze SharePoint Online. Jeśli nie są używane, kopie zapasowe są zastępowane.|
|Testowanie zabezpieczeń i dostosowywanie wydajności serwera są w sposób ciągły przeprowadzane przez firmę Microsoft w usłudze.|Zmiany w interfejsie użytkownika i SharePoint są instalowane przez usługę i może być konieczne ich wyłączenie lub wyłączenie.|
|Microsoft 365 spełnia wiele standardów branżowych: oferty [firmy Microsoft dotyczące zgodności](/compliance/regulatory/offering-home).|[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) pomocy dotyczącej migracji jest ograniczona.  <br/> Większość uaktualnienia będzie ręcznych lub za pośrednictwem interfejsu API migracji usługi SPO opisanego w te [SharePoint Online i OneDrive Przewodnik po zawartości migracji](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Inżynierowie pomocy technicznej firmy Microsoft i pracownicy centrum danych nie mają nieograniczonego dostępu administratora do Twojej subskrypcji.|Jeśli infrastruktura sprzętowa wymaga uaktualnienia w celu obsługi nowszej wersji pakietu SharePoint lub jeśli do uaktualnienia jest wymagana farma pomocnicza, mogą zostać związane dodatkowe koszty.|
|Dostawcy rozwiązań mogą pomóc w czasie migracji danych do usługi SharePoint Online.|Nie wszystkie zmiany w u SharePoint online są pod Twoją kontrolą. Po migracji różnice w projekcie menu, bibliotek i innych funkcji mogą tymczasowo wpłynąć na użyteczność.|
|Produkty online są aktualizowane automatycznie w całej usłudze. Funkcje mogą przestać być dostępne, ale nie ma prawdziwej zakończenia cyklu pomocy technicznej.|Istnieje cykl życia pomocy technicznej dla programu SharePoint Server lub SharePoint Foundation, a także podstawowe SQL serwerach.|

Jeśli zdecydowano się na utworzenie nowej witryny Microsoft 365 i w razie potrzeby przeprowadzić ręczną migrację danych do tej witryny, sprawdź dostępne [Microsoft 365 użytkowników](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Uaktualnianie SharePoint serwera lokalnego

Od SharePoint Server 2019 uaktualnień muszą być *uaktualnień posiewu*. Nie można bezpośrednio uaktualnić programu SharePoint Server 2010 do programu SharePoint Server 2016 lub do wersji SharePoint 2019. Szeregowa ścieżka uaktualniania:

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Zaplanowanie śledzenia całej ścieżki od SharePoint 2010 do SharePoint Server 2016. Uaktualnienie obejmuje koszt sprzętu (SQL uaktualnieniu serwerów), oprogramowania i administrowania. Ponadto może być konieczne uaktualnienie dostosowań lub nawet porzucenie ich. Pamiętaj o udokumentować krytyczne dostosowania przed uaktualnieniem farmy SharePoint Server.

> [!NOTE]
> Można zachować swoją farmę zakończenia pomocy technicznej dla programu SharePoint 2010, zainstalować farmę programu SharePoint Server 2016 na nowym sprzęcie (tak aby oddzielne farmy działały obok siebie), a następnie zaplanować i wykonać ręczną migrację zawartości (na przykład w celu pobrania i ponownego przekazania zawartości). Istnieją jednak potencjalne problemy z tymi ręcznymi przeniesieniami, na przykład dokumenty pochodzące z roku 2010 mające bieżące konto ostatnio zmodyfikowane z aliasem konta, które ręcznie przenosi dane. Niektóre prace, takie jak ponownetwonie witryn, podwitryn, uprawnień i struktur list, należy wykonać z wyprzedzeniem. Przed uaktualnieniem upewnij się, że twoje środowisko jest czyste. Przejmij pod uwagę dane, które można przenieść do magazynu lub które nie są już potrzebne. Może to zmniejszyć wpływ migracji. Przed uaktualnieniem i (oczywiście) przed likwidacją należy się wcześniej zweryfikować, czy istniejąca farma jest funkcjonalna.

Pamiętaj, aby przejrzeć *obsługiwane i nieobsługiwane ścieżki uaktualniania*:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

W przypadku *dostosowań* bardzo ważne jest zaplanowanie poszczególnych kroków na ścieżce migracji:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Zalety lokalne|Wady lokalnej|
|---|---|
|Pełna kontrola nad wszystkimi aspektami Farmy SharePoint (i jej SQL) dzięki sprzętowi serwera.|Za wszystkie przerwy i poprawki odpowiada Twoja firma. Możesz jednak uczestniczyć w płatnej pomocy technicznej firmy Microsoft, jeśli twój produkt nie zakończył już zakończenia pomocy technicznej.|
|Pełny zestaw funkcji lokalnego SharePoint Server z opcją połączenia Twojej farmy lokalnej z subskrypcją usługi SharePoint Online za pośrednictwem środowiska hybrydowego.|Uaktualnienia, poprawki, poprawki zabezpieczeń, uaktualnienia sprzętu i cała konserwacja programu SharePoint Server i jego farmy SQL są zarządzane lokalnie.|
|Pełny dostęp do większych opcji dostosowywania niż w SharePoint Online.|[Oferty firmy Microsoft dotyczące zgodności](/compliance/regulatory/offering-home) należy skonfigurować ręcznie lokalnie.|
|Testowanie zabezpieczeń i dostosowywanie wydajności serwera są przeprowadzane w Twojej siedzibie pod Twoją kontrolą.|Microsoft 365 funkcje dostępne dla SharePoint Online, które nie współdziałają z lokalnym SharePoint serwerem.|
|Dostawcy rozwiązań mogą pomóc w migracji danych do następnej wersji programu SharePoint Server (i nie tylko).|Witryny SharePoint Server nie używają automatycznie [certyfikatów SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), jak to widać w SharePoint Online.|
|Pełna kontrola nad konwencjami nazewnictwa, tworzeniem i przywracaniem kopii zapasowych oraz innymi opcjami odzyskiwania w SharePoint lokalnym serwera.|SharePoint serwera lokalnego jest poufny na cykl życia produktu.|

### <a name="upgrade-resources"></a>Zasoby uaktualniania

Zacznij od porównania wymagań dotyczących sprzętu i oprogramowania. Jeśli bieżące środowisko nie spełnia podstawowych wymagań, może być najpierw trzeba uaktualnić sprzęt w farmie lub na SQL serwerach. 

Możesz przenieść niektóre witryny do "zawsze zawsze zielonego" sprzętu usługi SharePoint Online. Po zakończeniu oceny postępuj zgodnie z obsługiwanymi ścieżkami uaktualniania i metodami.

- *Wymagania dotyczące sprzętu/oprogramowania dla:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Ograniczenia i limity oprogramowania dla:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Omówienie procesu uaktualniania dla:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>Tworzenie rozwiązania hybrydowego z usługą SharePoint Online SharePoint lokalnym programu SharePoint Server

Konfiguracja hybrydowa zapewnia najlepsze rozwiązanie zarówno lokalne, jak i online w przypadku niektórych potrzeb migracji. Możesz połączyć farmy programu SharePoint Server 2013, 2016 lub 2019 z usługą SharePoint Online w celu utworzenia hybrydowego środowiska [SharePoint: Dowiedz](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) się więcej o SharePoint hybrydowych.

Jeśli celem migracji jest hybrydowa farma programu SharePoint Server, należy ustalić, które witryny i użytkownicy należy przenieść w tryb online, a które muszą pozostać lokalne. Klasyfikacja zawartości SharePoint serwera jako wysokiej, średniej lub niskiej w firmie może pomóc w podjęciu tej decyzji. Być może trzeba będzie udostępniać tylko konta użytkowników w celu zalogowania się i indeksu wyszukiwania SharePoint Server z usługą SharePoint Online. Ten czynnik może być jednak jasny dopiero po jednoznacznie, gdy przyjrzysz się, jak są używane witryny. Jeśli później Twoja firma zdecyduje się na migrację całej zawartości do usługi SharePoint Online, możesz przenieść wszystkie pozostałe konta i dane w trybie online, a następnie likwidować farmę lokalną. Zarządzanie farmą SharePoint/administrowanie nimi będzie wykonywane za pośrednictwem Microsoft 365 od tej chwili.

Pamiętaj, aby zapoznać się z istniejącymi typami środowisk hybrydowych oraz ze sposobu konfigurowania połączenia między lokalną farmą usługi SharePoint a subskrypcją usługi Microsoft 365 hybrydowej.

|Opcja|Opis|
|---|---|
|[Oferty firmy Microsoft dotyczące zgodności](/compliance/regulatory/offering-home).|[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pomocy dotyczącej migracji jest ograniczona.<br/><br/> Większość uaktualnienia będzie ręcznych lub za pośrednictwem interfejsu API migracji usługi SPO opisanego w te [SharePoint Online i OneDrive Przewodnik po zawartości migracji](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Inżynierowie pomocy technicznej firmy Microsoft i pracownicy centrum danych nie mają nieograniczonego dostępu administratora do Twojej subskrypcji.|Jeśli infrastruktura sprzętowa wymaga uaktualnienia w celu obsługi nowszej wersji pakietu SharePoint lub jeśli jest wymagana farma pomocnicza, mogą wystąpić dodatkowe koszty.|
|W przypadku zadania migracji danych do usługi SharePoint Online mogą pomóc partnerzy.||
|Produkty online są aktualizowane automatycznie w całej usłudze. Funkcje mogą przestać być dostępne, ale nie ma prawdziwej zakończenia obsługi.||

Jeśli chcesz utworzyć nową witrynę sieci Microsoft 365 i w razie potrzeby ręcznie migrować dane do tej witryny, sprawdź [Microsoft 365 opcje](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Uaktualnianie SharePoint serwera lokalnego

Nie ma sposobu, aby pominąć wersje w SharePoint uaktualnień. Oznacza to, że uaktualnienia są uaktualnień posiewu:

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Przebycie całej ścieżki od wersji SharePoint 2007 do programu SharePoint Server 2016 oznacza znaczną inwestycję w czasie i obejmuje sprzęt (SQL także uaktualnienie serwerów), oprogramowanie i koszty administracyjne. W zależności od znaczeniu funkcji, należy uaktualnić dostosowania lub zrezygnować z nich.

> [!NOTE]
> Można zachować swoją farmę użytkowania programu SharePoint 2007, zainstalować farmę programu SharePoint Server 2016 na nowym sprzęcie (tak aby osobne farmy działały obok siebie), a następnie zaplanować i wykonać ręczną migrację zawartości (na przykład w celu pobrania i ponownego przekazania zawartości). Jednak przeniesienie ręczne ma pewne wady, na przykład przeniesienie dokumentów, które zastępują ostatnio zmodyfikowane konto aliasem konta, które ręcznie przenosi. Z wyprzedzeniem należy wykonać wiele zadań, takich jak ponownetwonie witryn, podwitryn, uprawnień i struktur list. W każdym przypadku rozważ, jakie dane można przenieść do magazynu lub już nie trzeba zmniejszać wpływu migracji.

Przed uaktualnieniem upewnij się, że Twoje środowisko jest czyste. Przed uaktualnieniem i z pewnością przed likwidacją należy się wcześniej zweryfikować, czy istniejąca farma działa.

Pamiętaj, aby przejrzeć *obsługiwane i nieobsługiwane ścieżki uaktualniania*:

- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Jeśli masz *dostosowania*, bardzo ważne jest zaplanowanie uaktualnienia dla każdego kroku na ścieżce migracji:

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Profesjonalista w środowisku lokalnym|Lokalna con|
|---|---|
|Pełna kontrola nad wszystkimi aspektami Twojej farmy SharePoint, od sprzętu serwera do pracy.|Za wszystkie przerwy i poprawki odpowiada Twoja firma. (Możesz jednak zaangażować się w płatną pomoc techniczną Microsoft, jeśli nie zakończył on wsparcia dla Twojego produktu).|
|Pełny zestaw funkcji lokalnego SharePoint Server z opcją połączenia Twojej farmy lokalnej z subskrypcją usługi SharePoint Online za pośrednictwem środowiska hybrydowego.|Uaktualnienie, poprawki, poprawki zabezpieczeń i cała konserwacja programu SharePoint Server zarządzana lokalnie.|
|Pełny dostęp do większych możliwości dostosowywania.|[Oferty firmy Microsoft dotyczące zgodności](/compliance/regulatory/offering-home) należy skonfigurować ręcznie lokalnie.|
|Testowanie zabezpieczeń i dostosowywanie wydajności serwera odbywa się w Twojej siedzibie pod Twoją kontrolą.|Microsoft 365 funkcje dostępne dla usługi SharePoint Online, które nie współdziałają z lokalnym SharePoint Server.|
|Partnerzy mogą pomóc w migracji danych do następnej wersji programu SharePoint Server (i nie tylko).|Witryny SharePoint Server nie używają automatycznie [certyfikatów SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), jak to widać w SharePoint Online.|
|Pełna kontrola nad konwencjami nazewnictwa, tworzeniem i przywracaniem kopii zapasowych oraz innymi opcjami odzyskiwania w SharePoint lokalnym serwera.|SharePoint serwera lokalnego jest poufny na cykl życia produktu.|

### <a name="upgrade-resources"></a>Zasoby uaktualniania

Zacznij od poznania, czy spełniasz wymagania dotyczące sprzętu i oprogramowania, a następnie postępuj zgodnie z obsługiwanymi metodami uaktualniania.

- *Wymagania dotyczące sprzętu/oprogramowania dla*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Ograniczenia i limity oprogramowania dla*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Omówienie procesu uaktualniania dla*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Tworzenie SharePoint hybrydowego między usługą SharePoint Online a środowiskiem lokalnym

Jeśli odpowiedź na Twoje potrzeby dotyczące migracji znajduje się gdzieś między kontrolką oferowaną przez lokalną a niższym kosztem utrzymania oferowanym przez usługę SharePoint Online, możesz połączyć farmy programu SharePoint Server 2013 lub 2016 z usługą SharePoint Online za pośrednictwem środowisk hybrydowych. [Dowiedz się więcej SharePoint hybrydowych](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Jeśli zdecydujesz, że hybrydowa farma programu SharePoint Server przydają się Twojej firmie, zapoznaj się z istniejącymi typami środowisk hybrydowych i sposobu konfigurowania połączenia między lokalną farmą programu SharePoint a subskrypcją usługi Microsoft 365.

Możesz utworzyć nowe środowisko Microsoft 365/testowania, które możesz skonfigurować za pomocą przewodników [laboratorium testowego](m365-enterprise-test-lab-guides.md). Po wykupieniu wersji próbnej lub zakupie subskrypcji usługi Microsoft 365 możesz utworzyć zbiory witryn, sieci Web i biblioteki dokumentów w aplikacji SharePoint Online, do których możesz przeprowadzić migrację danych. Możesz przeprowadzić migrację ręcznie, korzystając z interfejsu API migracji, lub, jeśli chcesz przeprowadzić migrację zawartości witryny Moja witryna do programu OneDrive dla Firm, za pomocą kreatora hybrydowego.

> [!NOTE]
> Aby użyć opcji hybrydowej, SharePoint program SharePoint Server 2010 musi najpierw zostać uaktualniony lokalnie do programu SharePoint Server 2013 lub 2016. SharePoint Foundation 2010 i SharePoint Foundation 2013 nie obsługują połączeń hybrydowych z usługą SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Podsumowanie opcji dla klientów Office 2010 i serwerów oraz Windows 7

Aby uzyskać wizualne podsumowanie opcji uaktualnienia, migracji i przenoszenia do chmury dla klientów i serwerów programu Office 2010 oraz systemu Windows 7, zobacz koniec plakatu pomocy [technicznej](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Zakończenie obsługi klientów i Office 2010 i serwerów oraz Windows 7.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Ten plakat przedstawia różne sposoby, które można podjąć, aby uniknąć produktów klienckich i serwerowych Office 2010 oraz zakończenia obsługi klienta i serwera programu Windows 7, z wyróżnionymi preferowanymi ścieżkami i opcjami w Microsoft 365 Enterprise.

Możesz również pobrać [ten plakat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) i wydrukować go w formacie letter, legal lub tabloid (11 x 17).

## <a name="related-articles"></a>Artykuły pokrewne

[Zasoby pomocne w uaktualnieniu serwerów i Office 2007 lub 2010](upgrade-from-office-2010-servers-and-products.md)

[Omówienie procesu uaktualniania z wersji SharePoint 2010 do SharePoint 2013](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[Najlepsze rozwiązania dotyczące uaktualniania z wersji SharePoint 2010 do SharePoint 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[Rozwiązywanie problemów z uaktualnianiem baz danych w SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[Wyszukaj dostawców rozwiązań firmy Microsoft, aby uzyskać pomoc przy uaktualnieniu](https://go.microsoft.com/fwlink/?linkid=841249)

[Zaktualizowane zasady obsługi produktów dla SharePoint 2013](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[Zaktualizowane zasady obsługi produktów dla SharePoint Server 2016](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
