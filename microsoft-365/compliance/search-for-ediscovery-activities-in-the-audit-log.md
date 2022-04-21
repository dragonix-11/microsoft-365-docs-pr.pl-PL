---
title: Wyszukaj działania zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 67cc7f42-a53d-4751-b929-6005c80798f7
description: Dowiedz się, jakie zdarzenia są rejestrowane, gdy użytkownicy z przypisanymi uprawnieniami do zbierania elektronicznych materiałów dowodowych wykonują zadania wyszukiwania zawartości, zbierania elektronicznych materiałów dowodowych (Standard) i zbierania elektronicznych materiałów dowodowych (Premium) w portalu zgodności usługi Microsoft Purview.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1e21fcff71d050e09a60a6708678d46f2b894bdc
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995871"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>Wyszukaj działania zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W dzienniku inspekcji są rejestrowane działania związane z wyszukiwaniem zawartości i zbierania elektronicznych materiałów dowodowych (w przypadku funkcji zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Standard) i eDiscovery (Premium) w usłudze Microsoft Purview lub przy użyciu odpowiednich poleceń cmdlet programu PowerShell. Zdarzenia są rejestrowane, gdy administratorzy lub menedżerowie zbierania elektronicznych materiałów dowodowych (lub dowolne przypisane przez użytkownika uprawnienia do zbierania elektronicznych materiałów dowodowych) wykonują następujące zadania wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych (standardowa) w portalu zgodności:
  
- Tworzenie spraw podstawowych i zbierania elektronicznych materiałów dowodowych (Premium) i zarządzanie nimi

- Tworzenie, uruchamianie i edytowanie wyszukiwań zawartości

- Wykonywanie akcji wyszukiwania, takich jak wyświetlanie podglądu, eksportowanie i usuwanie wyników wyszukiwania

- Zarządzanie opiekunami i zestawy przeglądów w zakresie zbierania elektronicznych materiałów dowodowych (Premium)

- Konfigurowanie filtrowania uprawnień dla wyszukiwania zawartości

- Zarządzanie rolą administratora zbierania elektronicznych materiałów dowodowych
  
Aby uzyskać więcej informacji na temat przeszukiwania dziennika inspekcji, wymaganych uprawnień i eksportowania wyników wyszukiwania, zobacz [Przeszukiwanie dziennika inspekcji w portalu zgodności](search-the-audit-log-in-security-and-compliance.md).
  
## <a name="how-to-search-for-and-view-ediscovery-activities"></a>Jak wyszukiwać i wyświetlać działania zbierania elektronicznych materiałów dowodowych

Obecnie należy wykonać kilka konkretnych czynności, aby wyświetlić działania zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji. W tym artykule wyjaśniono, jak to zrobić.
  
1. Przejdź do witryny <https://compliance.microsoft.com> i zaloguj się przy użyciu konta służbowego.

2. W okienku nawigacji po lewej stronie portalu zgodności kliknij pozycję **Inspekcja**.

3. Na liście rozwijanej **Działania** w obszarze **działania zbierania elektronicznych** materiałów dowodowych lub **działań zbierania elektronicznych materiałów dowodowych (Premium)** kliknij co najmniej jedno działanie, aby wyszukać.

    > [!NOTE]
    > Lista rozwijana **Działania** zawiera również grupę działań o nazwie **działania cmdlet zbierania elektronicznych** materiałów dowodowych, które będą zwracać rekordy z dziennika inspekcji poleceń cmdlet.
  
4. Wybierz zakres dat i godzin, aby wyświetlić zdarzenia zbierania elektronicznych materiałów dowodowych, które wystąpiły w tym okresie.

5. W polu **Użytkownicy** wybierz co najmniej jednego użytkownika, aby wyświetlić wyniki wyszukiwania. Pozostaw to pole puste, aby zwrócić wpisy dla wszystkich użytkowników.

6. Kliknij pozycję **Wyszukaj** , aby uruchomić wyszukiwanie przy użyciu kryteriów wyszukiwania.

7. Po wyświetleniu wyników wyszukiwania możesz kliknąć pozycję **Filtruj wyniki** , aby filtrować lub sortować wynikowe rekordy działań. Niestety, nie można użyć filtrowania, aby jawnie wykluczyć niektóre działania. 

8. Aby wyświetlić szczegółowe informacje o działaniu, kliknij rekord działania na liście wyników wyszukiwania. 

    Zostanie wyświetlona strona wysuwanych **szczegółów** zawierająca szczegółowe właściwości z rekordu zdarzenia. Aby wyświetlić dodatkowe szczegóły, kliknij pozycję **Więcej informacji**. Opis tych właściwości można znaleźć w sekcji [Szczegółowe właściwości działań zbierania elektronicznych materiałów dowodowych](#detailed-properties-for-ediscovery-activities) .

9. W razie potrzeby możesz wyeksportować wyniki wyszukiwania dziennika inspekcji do pliku CSV, a następnie użyć funkcji Excel Power Query, aby sformatować i odfiltrować te rekordy. Aby uzyskać więcej informacji, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md).

## <a name="ediscovery-activities"></a>Działania zbierania elektronicznych materiałów dowodowych

W poniższej tabeli opisano działania wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa), które są rejestrowane, gdy administrator lub menedżer zbierania elektronicznych materiałów dowodowych wykonuje działanie związane zbierania elektronicznych materiałów dowodowych przy użyciu portalu zgodności. Niektóre działania wykonywane w ramach zbierania elektronicznych materiałów dowodowych (Premium) mogą być zwracane podczas wyszukiwania działań na tej liście.
  
> [!NOTE]
> Działania zbierania elektronicznych materiałów dowodowych opisane w tej sekcji zawierają podobne informacje do działań cmdlet zbierania elektronicznych materiałów dowodowych opisanych w następnej sekcji. Zalecamy użycie działań zbierania elektronicznych materiałów dowodowych opisanych w tej sekcji, ponieważ będą one wyświetlane w wynikach wyszukiwania dziennika inspekcji w ciągu 30 minut. Wyświetlanie działań cmdlet zbierania elektronicznych materiałów dowodowych w wynikach wyszukiwania dziennika inspekcji może potrwać do 24 godzin.
  
|**Przyjazna nazwa**|**Operacja**|**Odpowiednie polecenie cmdlet**|**Opis**|
|:-----|:-----|:-----|:-----|
|Dodano element członkowski do sprawy zbierania elektronicznych materiałów dowodowych  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |Użytkownik został dodany jako członek sprawy zbierania elektronicznych materiałów dowodowych. Jako członek sprawy użytkownik może wykonywać różne zadania związane z wielkością liter w zależności od tego, czy przypisano im niezbędne uprawnienia.  <br/> |
|Zmienione wyszukiwanie zawartości  <br/> |SearchUpdated  <br/> |Set-ComplianceSearch  <br/> |Istniejące wyszukiwanie zawartości zostało zmienione. Zmiany mogą obejmować dodawanie lub usuwanie lokalizacji zawartości lub edytowanie zapytania wyszukiwania.  <br/> |
|Zmieniono członkostwo administratora zbierania elektronicznych materiałów dowodowych  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |Lista administratorów zbierania elektronicznych materiałów dowodowych w organizacji została zmieniona. To działanie jest rejestrowane, gdy lista administratorów zbierania elektronicznych materiałów dowodowych zostanie zastąpiona grupą nowych użytkowników. Jeśli jeden użytkownik zostanie dodany lub usunięty, zostanie zarejestrowana operacja CaseAdminAdded.  <br/> |
|Zmieniono przypadek zbierania elektronicznych materiałów dowodowych  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |Przypadek zbierania elektronicznych materiałów dowodowych został zmieniony. Zmiany obejmują zamknięcie otwartego przypadku lub ponowne otwarcie zamkniętego przypadku.  <br/> |
|Zmieniono członkostwo w przypadku zbierania elektronicznych materiałów dowodowych  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |Lista członkostwa w sprawie zbierania elektronicznych materiałów dowodowych została zmieniona. To działanie jest rejestrowane, gdy wszyscy członkowie zostaną zastąpieni grupą nowych użytkowników. W przypadku dodania lub usunięcia pojedynczego elementu członkowskiego zarejestrowana jest operacja CaseMemberAdded lub CaseMemberRemoved.  <br/> |
|Zmieniony filtr uprawnień wyszukiwania  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |Filtr uprawnień wyszukiwania został zmieniony.  <br/> |
|Zmieniono zapytanie wyszukiwania dla blokady sprawy zbierania elektronicznych materiałów dowodowych  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |Zmieniono blokadę opartą na zapytaniach skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych. Możliwe zmiany obejmują edytowanie zapytania lub zakresu dat dla blokady opartej na zapytaniach.  <br/> |
|Pobrano element podglądu wyszukiwania zawartości  <br/> |PreviewItemDownloaded  <br/> |nd.  <br/> |Użytkownik pobrał element na swój komputer lokalny (klikając link **Pobierz oryginalny element** ) podczas podglądu wyników wyszukiwania.  <br/> |
|Element podglądu wyszukiwania zawartości na liście  <br/> |PreviewItemListed  <br/> |nd.  <br/> |Użytkownik kliknął pozycję **Podgląd wyników wyszukiwania** , aby wyświetlić stronę wyników wyszukiwania w wersji zapoznawczej, która wyświetla maksymalnie 1000 elementów z wyników wyszukiwania.  <br/> |
|Wyświetlony element podglądu wyszukiwania zawartości  <br/> |PreviewItemRendered  <br/> |nd.  <br/> |Menedżer zbierania elektronicznych materiałów dowodowych wyświetlił element, klikając go podczas wyświetlania podglądu wyników wyszukiwania.  <br/> |
|Utworzone wyszukiwanie zawartości  <br/> |SearchCreated  <br/> |New-ComplianceSearch  <br/> |Utworzono nowe wyszukiwanie zawartości.  <br/> |
|Utworzony administrator zbierania elektronicznych materiałów dowodowych  <br/> |CaseAdminAdded  <br/> |Add-eDiscoveryCaseAdmin  <br/> |Użytkownik został dodany jako administrator zbierania elektronicznych materiałów dowodowych w organizacji.  <br/> |
|Utworzono przypadek zbierania elektronicznych materiałów dowodowych  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |Utworzono przypadek zbierania elektronicznych materiałów dowodowych. Po utworzeniu sprawy wystarczy nadać mu nazwę. Inne zadania związane z wielkością liter, takie jak dodawanie członków, tworzenie blokad i tworzenie wyszukiwań zawartości skojarzonych ze sprawą, powodują rejestrowanie dodatkowych zdarzeń.  <br/> |
|Utworzony filtr uprawnień wyszukiwania  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |Utworzono filtr uprawnień wyszukiwania.  <br/> |
|Utworzono zapytanie wyszukiwania dla blokady sprawy zbierania elektronicznych materiałów dowodowych  <br/> |HoldCreated  <br/> |New-CaseHoldRule  <br/> |Utworzono blokadę opartą na zapytaniach skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych.  <br/> |
|Wyszukiwanie usuniętej zawartości  <br/> |WyszukiwanieRemoved  <br/> |Remove-ComplianceSearch  <br/> |Istniejące wyszukiwanie zawartości zostało usunięte.  <br/> |
|Usunięty administrator zbierania elektronicznych materiałów dowodowych  <br/> |CaseAdminRemoved  <br/> |Remove-eDiscoveryCaseAdmin  <br/> |Administrator zbierania elektronicznych materiałów dowodowych został usunięty z twojej organizacji.  <br/> |
|Usunięto przypadek zbierania elektronicznych materiałów dowodowych  <br/> |CaseRemoved  <br/> |Remove-ComplianceCase  <br/> |Usunięto przypadek zbierania elektronicznych materiałów dowodowych. Przed usunięciem sprawy należy usunąć wszystkie blokady skojarzone ze sprawą.  <br/> |
|Filtr usuniętych uprawnień wyszukiwania  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |Usunięto filtr uprawnień wyszukiwania.  <br/> |
|Usunięto zapytanie wyszukiwania dla blokady sprawy zbierania elektronicznych materiałów dowodowych  <br/> |HoldRemoved  <br/> |Remove-CaseHoldRule  <br/> |Usunięto blokadę opartą na zapytaniach skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych. Usunięcie zapytania z blokady jest często wynikiem usunięcia blokady. Po usunięciu blokady lub blokady zostaną zwolnione lokalizacje zawartości, które zostały wstrzymane.  <br/> |
|Pobrany eksport wyszukiwania zawartości  <br/> |SearchExportDownloaded  <br/> |nd.  <br/> |Użytkownik pobrał wyniki wyszukiwania zawartości na komputerze lokalnym. Przed pobraniem wyników wyszukiwania należy zainicjować rozpoczęty **eksport działania wyszukiwania zawartości** .  <br/> |
|Podgląd wyników wyszukiwania zawartości  <br/> |SearchPreviewed  <br/> |nd.  <br/> |Użytkownik wyświetlił podgląd wyników wyszukiwania zawartości.  <br/> |
|Przeczyszczane wyniki wyszukiwania zawartości  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |Użytkownik oczyścił wyniki wyszukiwania zawartości, uruchamiając polecenie **New-ComplianceSearchAction -Purge** .  <br/> |
|Usunięto analizę wyszukiwania zawartości  <br/> |RemovedSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |Usunięto akcję przygotowywania wyszukiwania zawartości (w celu przygotowania wyników wyszukiwania do zbierania elektronicznych materiałów dowodowych (Premium)). Jeśli akcja przygotowania miała mniej niż dwa tygodnie, wyniki wyszukiwania przygotowane do zbierania elektronicznych materiałów dowodowych (Premium) zostały usunięte z obszaru przechowywania Microsoft Azure. Jeśli akcja przygotowania była starsza niż 2 tygodnie, to zdarzenie wskazuje, że usunięto tylko odpowiednią akcję przygotowania.  <br/> |
|Usunięto eksport wyszukiwania zawartości  <br/> |RemovedSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |Akcja eksportowania wyszukiwania zawartości została usunięta. Jeśli akcja eksportu miała mniej niż dwa tygodnie, wyniki wyszukiwania przekazane do Microsoft Azure obszaru magazynowania zostały usunięte. Jeśli akcja eksportu była starsza niż 2 tygodnie, to zdarzenie wskazuje, że usunięto tylko odpowiednią akcję eksportu.  <br/> |
|Usunięto element członkowski ze sprawy zbierania elektronicznych materiałów dowodowych  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |Użytkownik został usunięty jako członek sprawy zbierania elektronicznych materiałów dowodowych.  <br/> |
|Usunięto wyniki wyszukiwania zawartości w wersji zapoznawczej  <br/> |RemovedSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |Akcja wyszukiwania zawartości w wersji zapoznawczej została usunięta.  <br/> |
|Usunięto akcję przeczyszczania wykonywaną podczas wyszukiwania zawartości  <br/> |RemovedSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |Usunięto akcję przeczyszczania wyszukiwania zawartości.  <br/> |
|Usunięto raport wyszukiwania  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |Usunięto akcję eksportowania raportu wyszukiwania zawartości.  <br/> |
|Rozpoczęto analizę wyszukiwania zawartości  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |Wyniki wyszukiwania zawartości zostały przygotowane do analizy w eDiscovery (Premium).  <br/> |
|Rozpoczęte wyszukiwanie zawartości  <br/> |WyszukiwanieStarted  <br/> |Start-ComplianceSearch  <br/> |Rozpoczęto wyszukiwanie zawartości. Podczas tworzenia lub zmieniania wyszukiwania zawartości przy użyciu portalu zgodności wyszukiwanie jest uruchamiane automatycznie.<br/> |
|Rozpoczęto eksportowanie wyszukiwania zawartości  <br/> |SearchExported  <br/> |New-ComplianceSearchAction  <br/> |Użytkownik wyeksportował wyniki wyszukiwania zawartości.  <br/> |
|Rozpoczęto eksportowanie raportu  <br/> |SearchReport  <br/> |New-ComplianceSearchAction  <br/> |Użytkownik wyeksportował raport wyszukiwania zawartości.  <br/> |
|Zatrzymano wyszukiwanie zawartości  <br/> |SearchStopped  <br/> |Stop-ComplianceSearch  <br/> |Użytkownik zatrzymał wyszukiwanie zawartości.  <br/> |
|(brak)|CaseViewed|Get-ComplianceCase|Użytkownik wyświetlił przypadek zbierania elektronicznych elektronicznych materiałów dowodowych (Standard) w centrum zgodności. Rekord inspekcji dla tego zdarzenia zawiera nazwę sprawy, która została wyświetlona. |
|(brak)|SearchViewed|Get-ComplianceSearch|Użytkownik wyświetlił wyszukiwanie zawartości w centrum zgodności, uzyskując dostęp do wyszukiwania na karcie **Wyszukiwania** w przypadku zbierania elektronicznych materiałów dowodowych (Standardowa) lub uzyskując do niego dostęp na stronie **wyszukiwania zawartości** . Rekord inspekcji dla tego zdarzenia zawiera tożsamość wyświetlonego wyszukiwania.|
|(brak)|ViewedSearchExported|Get-ComplianceSearchAction -Export|Użytkownik wyświetlił eksport wyszukiwania zawartości w centrum zgodności, uzyskując dostęp do eksportu na karcie **Eksporty** na stronie **wyszukiwania zawartości** . To działanie jest również rejestrowane, gdy użytkownik wyświetli eksport skojarzony ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa).|
|(brak)|ViewedSearchPreviewed|Get-ComplianceSearchAction —wersja zapoznawcza|Użytkownik wyświetlił podgląd wyników wyszukiwania zawartości w Centrum zgodności. To działanie jest również rejestrowane, gdy użytkownik wyświetla podgląd wyników wyszukiwania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa).|
|||||
  
## <a name="ediscovery-premium-activities"></a>Działania zbierania elektronicznych materiałów dowodowych (Premium)

W poniższej tabeli opisano działania zbierania elektronicznych materiałów dowodowych (Premium) zarejestrowane w dzienniku inspekcji. Te działania mogą służyć do śledzenia postępu działania w przypadku zbierania elektronicznych materiałów dowodowych (Premium).

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:-----|:-----|:-----|
|Dodano dane do innego zestawu przeglądów|AddWorkingSetQueryToWorkingSet|Użytkownik dodał dokumenty z jednego zestawu przeglądów do innego zestawu przeglądów.|
|Dodano dane do zestawu przeglądów|AddQueryToWorkingSet|Użytkownik dodał wyniki wyszukiwania z wyszukiwania zawartości skojarzonego z przypadkiem zbierania elektronicznych materiałów dowodowych (Premium) do zestawu przeglądów.|
|Dodano dane inne niż Microsoft 365 do zestawu przeglądów|AddNonOffice365DataToWorkingSet|Użytkownik dodał dane inne niż Microsoft 365 do zestawu przeglądów.|
|Dodano skorygowane dokumenty do zestawu przeglądów|AddRemediatedData|Użytkownik przekazuje dokumenty z błędami indeksowania, które zostały naprawione w zestawie przeglądów.|
|Analizowane dane w zestawie przeglądów|RunAlgo|Użytkownik przeprowadził analizę dokumentów w zestawie przeglądów.|
|Dokument z adnotacji w zestawie przeglądów|AdnotacjeDocument|Użytkownik adnotował dokument w zestawie przeglądów. Adnotacja obejmuje redagowanie zawartości w dokumencie.|
|Porównywane zestawy obciążeń|LoadComparisonJob|Użytkownik porównał dwa różne zestawy obciążeń w zestawie przeglądów. Zestaw obciążenia jest wtedy, gdy dane z wyszukiwania zawartości skojarzonego ze sprawą są dodawane do zestawu przeglądów.|
|Przekonwertowane zredagowane dokumenty na format PDF|BurnJob|Użytkownik przekonwertował wszystkie zredagowane dokumenty w zestawie przeglądów na pliki PDF.|
|Utworzony zestaw przeglądów|CreateWorkingSet|Użytkownik utworzył zestaw przeglądów.|
|Utworzono wyszukiwanie zestawu przeglądów|CreateWorkingSetSearch|Użytkownik utworzył zapytanie wyszukiwania, które wyszukuje dokumenty w zestawie przeglądów.|
|Utworzony tag|CreateTag|Użytkownik utworzył grupę tagów w zestawie przeglądów. Grupa tagów może zawierać co najmniej jeden tag podrzędny. Tagi te są następnie używane do oznaczania dokumentów w zestawie przeglądów.|
|Usunięto wyszukiwanie zestawu przeglądów|DeleteWorkingSetSearch|Użytkownik usunął zapytanie wyszukiwania w zestawie przeglądów.|
|Usunięty tag|DeleteTag|Użytkownik usunął tag lub grupę tagów w zestawie przeglądów.|
|Pobrany dokument|PobierzDocument|Użytkownik pobrał dokument z zestawu przeglądów.|
|Edytowany tag|UpdateTag|Użytkownik zmienił tag w zestawie przeglądów.|
|Wyeksportowane dokumenty z zestawu przeglądów|ExportJob|Użytkownik wyeksportował dokumenty z zestawu przeglądów.|
|Zmodyfikowane ustawienie przypadku|UpdateCaseSettings|Użytkownik zmodyfikował ustawienia dla sprawy. Ustawienia przypadku obejmują informacje o przypadku, uprawnienia dostępu i ustawienia kontrolujące zachowanie wyszukiwania i analizy.|
|Zmodyfikowane wyszukiwanie zestawu przeglądów|UpdateWorkingSetSearch|Użytkownik edytował zapytanie wyszukiwania w zestawie przeglądów.|
|Wyszukiwanie zestawu przeglądów w wersji zapoznawczej|PreviewWorkingSetSearch|Użytkownik wyświetlił podgląd wyników zapytania wyszukiwania w zestawie przeglądów.|
|Skorygowane dokumenty o błędach|ErrorRemediationJob|Użytkownik naprawia pliki zawierające błędy indeksowania.|
|Oznakowany dokument|TagFiles|Użytkownik taguje dokument w zestawie przeglądów.|
|Otagowane wyniki zapytania|TagJob|Użytkownik taguje wszystkie dokumenty zgodne z kryteriami zapytania wyszukiwania w zestawie przeglądów.|
|Wyświetlony dokument w zestawie przeglądów|ViewDocument|Użytkownik wyświetlił dokument w zestawie przeglądów.|
|||

## <a name="ediscovery-cmdlet-activities"></a>Działania poleceń cmdlet zbierania elektronicznych materiałów dowodowych

W poniższej tabeli wymieniono rekordy dziennika inspekcji poleceń cmdlet, które są rejestrowane, gdy administrator lub użytkownik wykonuje działanie związane zbierania elektronicznych materiałów dowodowych przy użyciu centrum zgodności lub uruchamiając odpowiednie polecenie cmdlet w programie PowerShell Security & Compliance Center. Szczegółowe informacje w rekordzie dziennika inspekcji różnią się w przypadku działań poleceń cmdlet wymienionych w tej tabeli i działań zbierania elektronicznych materiałów dowodowych opisanych w poprzedniej sekcji.
  
Jak wspomniano wcześniej, może upłynąć do 24 godzin, aby działania poleceń cmdlet zbierania elektronicznych materiałów dowodowych były wyświetlane w wynikach wyszukiwania dziennika inspekcji.
  
> [!TIP]
> Polecenia cmdlet w kolumnie **Operacja** w poniższej tabeli są połączone z odpowiednim tematem pomocy polecenia cmdlet w witrynie TechNet. Przejdź do tematu pomocy polecenia cmdlet, aby uzyskać opis dostępnych parametrów dla każdego polecenia cmdlet. Parametr i wartość parametru, które były używane z poleceniem cmdlet, są uwzględniane we wpisie dziennika inspekcji dla każdego zarejestrowanego działania polecenia cmdlet zbierania elektronicznych materiałów dowodowych. 
  
|**Przyjazna nazwa**|**Operacja (polecenie cmdlet)**|**Opis**|
|:-----|:-----|:-----|
|Utworzono blokadę w przypadku zbierania elektronicznych materiałów dowodowych  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |Utworzono blokadę dla sprawy zbierania elektronicznych materiałów dowodowych. Blokadę można utworzyć przy użyciu lub bez określania źródła zawartości. Jeśli zostaną określone źródła zawartości, zostaną one zidentyfikowane we wpisie dziennika inspekcji.  <br/> |
|Usunięto blokadę ze sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |Usunięto blokadę skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych. Usunięcie blokady powoduje zwolnienie wszystkich lokalizacji zawartości z blokady. Usunięcie blokady powoduje również usunięcie reguł blokady sprawy skojarzonych z blokadą (zobacz **Remove-CaseHoldRule** poniżej).  <br/> |
|Zmieniono blokadę w przypadku zbierania elektronicznych materiałów dowodowych  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |Wstrzymanie skojarzone zbierania elektronicznych materiałów dowodowych zostało zmienione. Możliwe zmiany obejmują dodawanie lub usuwanie lokalizacji zawartości lub wyłączanie (wyłączanie) blokady.  <br/> |
|Utworzono zapytanie wyszukiwania dla blokady sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule) <br/> |Utworzono blokadę opartą na zapytaniach skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych.  <br/> |
|Usunięto zapytanie wyszukiwania dla blokady sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-CaseHoldRule](/powershell/module/exchange/remove-caseholdrule) <br/> |Usunięto blokadę opartą na zapytaniach skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych. Usunięcie zapytania z blokady jest często wynikiem usunięcia blokady. Po usunięciu blokady lub blokady zostaną zwolnione lokalizacje zawartości, które zostały wstrzymane.  <br/> |
|Zmieniono zapytanie wyszukiwania dla blokady sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Set-CaseHoldRule](/powershell/module/exchange/set-caseholdrule) <br/> |Zmieniono blokadę opartą na zapytaniach skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych. Możliwe zmiany obejmują edytowanie zapytania lub zakresu dat dla blokady opartej na zapytaniach.  <br/> |
|Utworzono przypadek zbierania elektronicznych materiałów dowodowych  <br/> |[New-ComplianceCase](/powershell/module/exchange/new-compliancecase) <br/> |Utworzono przypadek zbierania elektronicznych materiałów dowodowych. Po utworzeniu sprawy wystarczy nadać mu nazwę. Inne zadania związane z wielkością liter, takie jak dodawanie członków, tworzenie blokad i tworzenie wyszukiwań zawartości skojarzonych ze sprawą, powodują rejestrowanie dodatkowych zdarzeń.  <br/> |
|Usunięto przypadek zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-ComplianceCase](/powershell/module/exchange/remove-compliancecase) <br/> |Usunięto przypadek zbierania elektronicznych materiałów dowodowych. Przed usunięciem sprawy należy usunąć wszystkie blokady skojarzone ze sprawą.  <br/> |
|Zmieniono przypadek zbierania elektronicznych materiałów dowodowych  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |Przypadek zbierania elektronicznych materiałów dowodowych został zmieniony. Zmiany obejmują zamknięcie otwartego przypadku lub ponowne otwarcie zamkniętego przypadku.  <br/> |
|Dodano element członkowski do sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |Użytkownik został dodany jako członek sprawy zbierania elektronicznych materiałów dowodowych. Jako członek sprawy użytkownik może wykonywać różne zadania związane z wielkością liter w zależności od tego, czy przypisano im niezbędne uprawnienia.  <br/> |
|Usunięto element członkowski ze sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |Użytkownik został usunięty jako członek sprawy zbierania elektronicznych materiałów dowodowych.  <br/> |
|Zmieniono członkostwo w przypadku zbierania elektronicznych materiałów dowodowych  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |Lista członkostwa w sprawie zbierania elektronicznych materiałów dowodowych została zmieniona. To działanie jest rejestrowane, gdy wszyscy członkowie zostaną zastąpieni grupą nowych użytkowników. Jeśli pojedynczy element członkowski zostanie dodany lub usunięty, zostanie zarejestrowana operacja **Add-ComplianceCaseMember** lub **Remove-ComplianceCaseMember** .  <br/> |
|Utworzone wyszukiwanie zawartości  <br/> |[New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) <br/> |Utworzono nowe wyszukiwanie zawartości.  <br/> |
|Wyszukiwanie usuniętej zawartości  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |Istniejące wyszukiwanie zawartości zostało usunięte.  <br/> |
|Zmienione wyszukiwanie zawartości  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |Istniejące wyszukiwanie zawartości zostało zmienione. Zmiany mogą obejmować dodawanie lub usuwanie lokalizacji zawartości, które są przeszukiwane, i edytowanie zapytania wyszukiwania.  <br/> |
|Rozpoczęte wyszukiwanie zawartości  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |Rozpoczęto wyszukiwanie zawartości. Podczas tworzenia lub zmieniania wyszukiwania zawartości przy użyciu graficznego interfejsu użytkownika centrum zgodności wyszukiwanie jest uruchamiane automatycznie. Jeśli utworzysz lub zmienisz wyszukiwanie przy użyciu polecenia cmdlet **New-ComplianceSearch** lub **Set-ComplianceSearch** , musisz uruchomić polecenie cmdlet **Start-ComplianceSearch** , aby rozpocząć wyszukiwanie.  <br/> |
|Zatrzymano wyszukiwanie zawartości  <br/> |[Stop-ComplianceSearch](/powershell/module/exchange/stop-compliancesearch) <br/> |Uruchomione wyszukiwanie zawartości zostało zatrzymane.  <br/> |
|Akcja wyszukiwania zawartości utworzonej  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |Utworzono akcję wyszukiwania zawartości. Akcje wyszukiwania zawartości obejmują wyświetlanie podglądu wyników wyszukiwania, eksportowanie wyników wyszukiwania, przygotowywanie wyników wyszukiwania do analizy w funkcji zbierania elektronicznych materiałów dowodowych (Premium) oraz trwałe usuwanie elementów zgodnych z kryteriami wyszukiwania w wyszukiwaniu zawartości.  <br/> |
|Akcja wyszukiwania usuniętej zawartości  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |Akcja wyszukiwania zawartości została usunięta.  <br/> |
|Utworzony filtr uprawnień wyszukiwania  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |Utworzono filtr uprawnień wyszukiwania.  <br/> |
|Filtr usuniętych uprawnień wyszukiwania  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |Usunięto filtr uprawnień wyszukiwania.  <br/> |
|Zmieniony filtr uprawnień wyszukiwania  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |Filtr uprawnień wyszukiwania został zmieniony.  <br/> |
|Utworzony administrator zbierania elektronicznych materiałów dowodowych  <br/> |[Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |Użytkownik został dodany jako administrator zbierania elektronicznych materiałów dowodowych w organizacji.  <br/> |
|Usunięty administrator zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |Administrator zbierania elektronicznych materiałów dowodowych został usunięty z twojej organizacji.  <br/> |
|Zmieniono członkostwo administratora zbierania elektronicznych materiałów dowodowych  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |Lista administratorów zbierania elektronicznych materiałów dowodowych w organizacji została zmieniona. To działanie jest rejestrowane, gdy lista administratorów zbierania elektronicznych materiałów dowodowych zostanie zastąpiona grupą nowych użytkowników. Jeśli jeden użytkownik zostanie dodany lub usunięty, zostanie zarejestrowana operacja **Add-eDiscoveryCaseAdmin** lub **Remove-eDiscoveryCaseAdmin** .  <br/> |
|(brak)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|To działanie jest rejestrowane, gdy użytkownik wyświetlił listę przypadków zbierania elektronicznych materiałów dowodowych (Standard) lub eDiscovery (Premium). To działanie jest również rejestrowane, gdy użytkownik wyświetli określony przypadek w środowisku zbierania elektronicznych materiałów dowodowych (Standard). Gdy użytkownik wyświetli konkretny przypadek, rekord inspekcji zawiera tożsamość wyświetlonego przypadku. Jeśli użytkownik wyświetlił tylko listę przypadków, rekord inspekcji nie zawiera tożsamości sprawy.|
|(brak)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|To działanie jest rejestrowane, gdy użytkownik wyświetlił listę wyszukiwań zawartości lub wyszukiwań skojarzonych ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa). To działanie jest również rejestrowane, gdy użytkownik wyświetla określone wyszukiwanie zawartości lub wyświetla określone wyszukiwanie skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa). Gdy użytkownik wyświetli określone wyszukiwanie, rekord inspekcji zawiera tożsamość wyświetlonego wyszukiwania. Jeśli użytkownik wyświetlił tylko listę wyszukiwań, rekord inspekcji nie zawiera tożsamości wyszukiwania.
|(brak)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|To działanie jest rejestrowane, gdy użytkownik wyświetlił listę akcji wyszukiwania zgodności (takich jak eksporty, podglądy lub przeczyszczanie) lub akcji skojarzonych ze sprawą zbierania elektronicznych materiałów dowodowych (standardowa). To działanie jest również rejestrowane, gdy użytkownik wyświetla określoną akcję wyszukiwania zgodności (na przykład eksport) lub wyświetla określoną akcję skojarzoną ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa). Gdy użytkownik wyświetla akcję wyszukiwania, rekord inspekcji zawiera tożsamość wyświetlonej akcji wyszukiwania. Jeśli użytkownik wyświetlił tylko listę akcji, rekord inspekcji nie zawiera tożsamości akcji.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>Szczegółowe właściwości działań zbierania elektronicznych materiałów dowodowych

W poniższej tabeli opisano właściwości, które znajdują się na stronie wysuwanej dla działania zbierania elektronicznych materiałów dowodowych wymienionego w wynikach wyszukiwania. Te właściwości są również zawarte w pliku CSV podczas eksportowania wyników wyszukiwania dziennika inspekcji. Rekord dziennika inspekcji dla działania zbierania elektronicznych materiałów dowodowych nie będzie zawierać wszystkich szczegółowych właściwości wymienionych poniżej.
  
> [!TIP]
> Podczas eksportowania wyników wyszukiwania plik CSV zawiera kolumnę o nazwie **AudtiData**, która zawiera szczegółowe właściwości opisane w poniższej tabeli we właściwości wielowartościowej. Możesz użyć funkcji Power Query w Excel, aby podzielić tę kolumnę na wiele kolumn, aby każda właściwość miała własną kolumnę. Umożliwi to sortowanie i filtrowanie co najmniej jednej z tych właściwości. Aby uzyskać więcej informacji, zobacz sekcję "Eksportowanie wyników wyszukiwania do pliku" w [temacie Wyszukaj dziennik inspekcji](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file). 
  
|**Właściwość**|**Opis**|
|:-----|:-----|
|Przypadku  <br/> |Tożsamość (GUID) przypadku zbierania elektronicznych materiałów dowodowych, która została utworzona, zmieniona lub usunięta.  <br/> |
|ClientApplication  <br/> |Działania poleceń cmdlet zbierania elektronicznych materiałów dowodowych mają wartość **EMC** dla tej właściwości. Oznacza to, że działanie zostało wykonane przy użyciu graficznego interfejsu użytkownika centrum zgodności lub uruchomienia polecenia cmdlet w programie PowerShell.  <br/> |
|ClientIP  <br/> |Adres IP urządzenia, które było używane podczas rejestrowania działania. Adres IP jest wyświetlany w formacie adresu IPv4 lub IPv6.  <br/> |
|ClientRequestId  <br/> | W przypadku działań zbierania elektronicznych materiałów dowodowych ta właściwość jest zwykle pusta.  <br/> |
|CmdletVersion  <br/> |Numer kompilacji dla wersji centrum zgodności działającego w organizacji.  <br/> |
|CreationTime  <br/> |Data i godzina w uniwersalnym czasie koordynowanym (UTC) po zakończeniu działania zbierania elektronicznych materiałów dowodowych.  <br/> |
|EffectiveOrganization  <br/> |Nazwa organizacji platformy Microsoft 365.  <br/> |
|ExchangeLocations  <br/> |Skrzynki pocztowe Exchange Online dołączone do wyszukiwania zawartości lub wstrzymane w przypadku zbierania elektronicznych materiałów dowodowych.  <br/> |
|Wykluczenia  <br/> |Skrzynka pocztowa lub lokalizacje witryn, które są wykluczone z wyszukiwania zawartości lub blokady w przypadku zbierania elektronicznych materiałów dowodowych.  <br/> |
|Extendedproperties  <br/> |Dodatkowe właściwości wyszukiwania zawartości, akcja wyszukiwania zawartości lub blokada w przypadku zbierania elektronicznych materiałów dowodowych, takie jak identyfikator GUID obiektu oraz odpowiednie parametry polecenia cmdlet i polecenia cmdlet, które były używane podczas wykonywania działania.  <br/> |
|Identyfikator  <br/> |Identyfikator wpisu raportu. Identyfikator jednoznacznie identyfikuje wpis dziennika inspekcji.  <br/> |
|NonPIIParameters  <br/> |Lista parametrów (bez żadnych wartości), które zostały użyte z poleceniem cmdlet zidentyfikowanym we właściwości Operation. Parametry wymienione w tej właściwości są takie same jak parametry wymienione we właściwości Parameters.  <br/> |
|Objectid  <br/> |Identyfikator GUID lub nazwa obiektu (na przykład wyszukiwanie zawartości lub przypadek zbierania elektronicznych materiałów dowodowych (Standardowa), który został utworzony, uzyskiwany, zmieniony lub usunięty przez działanie wymienione we właściwości Operacja. Ten obiekt jest również identyfikowany w kolumnie Element w wynikach wyszukiwania dziennika inspekcji.  <br/> |
|Objecttype  <br/> |Typ obiektu zbierania elektronicznych materiałów dowodowych, który użytkownik utworzył, usunął lub zmodyfikował; na przykład akcja wyszukiwania zawartości (wersja zapoznawcza, eksport lub przeczyszczenie), przypadek zbierania elektronicznych materiałów dowodowych lub wyszukiwanie zawartości.  <br/> |
|Operacja  <br/> |Nazwa operacji odpowiadającej wykonanemu działaniu zbierania elektronicznych materiałów dowodowych.  <br/> |
|Identyfikator organizacji  <br/> |Identyfikator GUID organizacji Microsoft 365.  <br/> |
|Parametry  <br/> |Nazwa i wartość parametrów, które zostały użyte z odpowiednim poleceniem cmdlet.  <br/> |
|PublicFolderLocations  <br/> |Lokalizacje folderów publicznych w Exchange Online, które są uwzględnione w wyszukiwaniu zawartości lub umieszczane w blokadzie w przypadku zbierania elektronicznych materiałów dowodowych.  <br/> |
|Kwerendy  <br/> |Zapytanie wyszukiwania skojarzone z działaniem, takie jak wyszukiwanie zawartości lub blokada oparta na zapytaniach.  <br/> |
|Typ rekordu  <br/> |Typ operacji wskazany przez rekord. Wartość **18** wskazuje zdarzenie związane z działaniem wymienionym w sekcji [Działania cmdlet zbierania elektronicznych](#ediscovery-cmdlet-activities) materiałów dowodowych. Wartość **24** wskazuje zdarzenie związane z działaniem wymienionym w sekcji [Jak wyszukiwać i wyświetlać działania zbierania elektronicznych materiałów dowodowych](#how-to-search-for-and-view-ediscovery-activities) .  <br/> |
|ResultStatus  <br/> |Wskazuje, czy akcja (określona we właściwości Operacja) zakończyła się pomyślnie, czy nie.  <br/> |
|SecurityComplianceCenterEventType  <br/> |Wskazuje, że działanie było zdarzeniem centrum zgodności. Wszystkie działania zbierania elektronicznych materiałów dowodowych będą miały wartość **0** dla tej właściwości.  <br/> |
|SharepointLocations  <br/> |Witryny SharePoint Online, które są uwzględnione w wyszukiwaniu zawartości lub wstrzymane w przypadku zbierania elektronicznych materiałów dowodowych.  <br/> |
|Starttime  <br/> |Data i godzina w uniwersalnym czasie koordynowanym (UTC) rozpoczęcia działania zbierania elektronicznych materiałów dowodowych.  <br/> |
|Userid  <br/> |Użytkownik, który wykonał działanie (określone we właściwości Operation), które spowodowało zarejestrowanie rekordu. Rekordy dotyczące działań zbierania elektronicznych materiałów dowodowych wykonywanych przez konta systemowe (takie jak NT AUTHORITY\SYSTEM) są również uwzględniane w dzienniku inspekcji.  <br/> |
|UserKey  <br/> |Alternatywny identyfikator użytkownika zidentyfikowanego we właściwości UserId. W przypadku działań zbierania elektronicznych materiałów dowodowych wartość tej właściwości jest zwykle taka sama jak właściwość UserId.  <br/> |
|UserServicePlan  <br/> |Subskrypcja używana przez organizację. W przypadku działań zbierania elektronicznych materiałów dowodowych ta właściwość jest zwykle pusta.  <br/> |
|Usertype  <br/> |Typ użytkownika, który wykonał operację. Następujące wartości wskazują typ użytkownika.  <br/> 0 Zwykły użytkownik. 2 Administrator w organizacji. 3 Konto administratora centrum danych firmy Microsoft lub systemu centrum danych. 4 Konto systemowe. 5 Aplikacja. 6 Jednostka usługi. |
|Wersja  <br/> |Wskazuje numer wersji działania (identyfikowanego przez właściwość Operation), które jest rejestrowane.  <br/> |
|Obciążenia  <br/> |Usługa, w której wystąpiło działanie. W przypadku działań zbierania elektronicznych materiałów dowodowych wartość to **SecurityComplianceCenter**.  <br/> |
