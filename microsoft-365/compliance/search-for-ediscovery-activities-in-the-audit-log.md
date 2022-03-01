---
title: Wyszukiwanie działań zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji
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
description: Dowiedz się, jakie zdarzenia są rejestrowane, gdy użytkownicy z przypisanymi uprawnieniami zbierania elektronicznych materiałów dowodowych wykonują przeszukiwanie zawartości, podstawowe zbierania elektronicznych materiałów dowodowych i Advanced eDiscovery zadania w Centrum zgodności platformy Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: eb1a6f1ee0ff9c84f4dbfc7f42427ae9dda499de
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021161"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>Wyszukiwanie działań zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji

W dzienniku inspekcji są rejestrowane działania związane z wyszukiwaniem zawartości i zbierania elektronicznych materiałów dowodowych (w przypadku zbierania elektronicznych materiałów dowodowych i zbierania elektronicznych materiałów dowodowych Advanced eDiscovery) wykonywane w programie Centrum zgodności platformy Microsoft 365 lub przez uruchamianie odpowiednich poleceń cmdlet programu PowerShell. Zdarzenia są rejestrowane, gdy administratorzy lub menedżerowie zbierania elektronicznych materiałów dowodowych (lub dowolnego użytkownika z przypisanymi uprawnieniami zbierania elektronicznych materiałów dowodowych) wykonują następujące zadania związane z wyszukiwaniem zawartości i podstawowymi zadaniami zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365:
  
- Tworzenie podstawowych spraw i zarządzanie nimi Advanced eDiscovery przypadku

- Tworzenie, uruchamianie i edytowanie wyszukiwań zawartości

- Wykonywanie akcji wyszukiwania, takich jak wyświetlanie podglądu, eksportowanie i usuwanie wyników wyszukiwania

- Zarządzanie projektami i zestawami rerecenzentów w Advanced eDiscovery

- Konfigurowanie filtrowania uprawnień dla wyszukiwania zawartości

- Zarządzanie rolą administratora zbierania elektronicznych materiałów dowodowych
  
Aby uzyskać więcej informacji na temat przeszukiwania dziennika inspekcji, wymaganych uprawnień i eksportowania wyników wyszukiwania, zobacz Przeszukiwanie dziennika [inspekcji w](search-the-audit-log-in-security-and-compliance.md) Centrum zgodności platformy Microsoft 365.
  
## <a name="how-to-search-for-and-view-ediscovery-activities"></a>Jak wyszukiwać i wyświetlać działania zbierania elektronicznych materiałów dowodowych

Obecnie musisz wykonać kilka określonych czynności, aby wyświetlić działania zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji. W tym artykule wyjaśniono, jak to zrobić.
  
1. Przejdź do <https://compliance.microsoft.com> konta służbowego lub szkolnego i zaloguj się.

2. W lewym okienku nawigacji okna Centrum zgodności platformy Microsoft 365 pozycję **Inspekcja**.

3. Na liście **rozwijanej** Działania w obszarze Działania zbierania elektronicznych materiałów dowodowych **lub Advanced eDiscovery działań** kliknij co najmniej jedno działania do wyszukania.

    > [!NOTE]
    > Lista **rozwijana** Działania zawiera również grupę działań o nazwach działań **polecenia cmdlet** zbierania elektronicznych materiałów dowodowych, które zwrócą rekordy z dziennika inspekcji polecenia cmdlet.
  
4. Wybierz zakres dat i godzin, aby wyświetlić zdarzenia zbierania elektronicznych materiałów dowodowych, które wystąpiły w tym okresie.

5. W **polu Użytkownicy** wybierz co najmniej jednego użytkownika, dla których chcesz wyświetlić wyniki wyszukiwania. Jeśli pozostawisz to pole puste, zostaną zwrócone wpisy dotyczące wszystkich użytkowników.

6. Kliknij **przycisk** Wyszukaj, aby uruchomić wyszukiwanie z użyciem kryteriów wyszukiwania.

7. Po wyświetlaniu wyników wyszukiwania możesz kliknąć pozycję Filtruj wyniki, aby filtrować lub sortować uzyskane rekordy aktywności. Niestety, za pomocą filtrowania nie można jawnie wykluczać określonych działań. 

8. Aby wyświetlić szczegóły dotyczące działania, kliknij rekord działania na liście wyników wyszukiwania. 

    Zostanie **wyświetlona** strona wysuwana Szczegóły zawierająca szczegółowe właściwości rekordu zdarzenia. Aby wyświetlić dodatkowe szczegóły, kliknij **pozycję Więcej informacji**. Opis tych właściwości można znaleźć w sekcji Szczegółowe właściwości działań zbierania elektronicznych materiałów [dowodowych](#detailed-properties-for-ediscovery-activities) .

9. W razie potrzeby możesz wyeksportować wyniki przeszukiwania dziennika inspekcji do pliku CSV, a następnie użyć funkcji Excel Power Query do formatowania i filtrowania tych rekordów. Aby uzyskać więcej informacji, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md).

## <a name="ediscovery-activities"></a>Działania zbierania elektronicznych materiałów dowodowych

W poniższej tabeli opisano działania związane z wyszukiwaniem zawartości i podstawowymi działaniami zbierania elektronicznych materiałów dowodowych rejestrowane w przypadku, gdy administrator lub menedżer zbierania elektronicznych materiałów dowodowych wykonuje działania związane z zbierania elektronicznych materiałów dowodowych przy użyciu Centrum zgodności platformy Microsoft 365. Niektóre działania wykonywane w Advanced eDiscovery mogą być zwracane podczas wyszukiwania działań na tej liście.
  
> [!NOTE]
> Działania zbierania elektronicznych materiałów dowodowych opisane w tej sekcji zapewniają podobne informacje do działań dotyczących polecenia cmdlet zbierania elektronicznych materiałów dowodowych opisanych w następnej sekcji. Zalecamy korzystanie z działań zbierania elektronicznych materiałów dowodowych opisanych w tej sekcji, ponieważ będą one wyświetlane w wynikach przeszukiwania dziennika inspekcji w ciągu 30 minut. Może upłynieć do 24 godzin, aż działania związane z poleceniami cmdlet zbierania elektronicznych materiałów dowodowych będą widoczne w wynikach przeszukiwania dziennika inspekcji.
  
|**Przyjazna nazwa**|**Operacja**|**Odpowiednie polecenie cmdlet**|**Opis**|
|:-----|:-----|:-----|:-----|
|Dodano członka do sprawy zbierania elektronicznych materiałów dowodowych  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |Użytkownik został dodany jako członek sprawy zbierania elektronicznych materiałów dowodowych. Jako członek sprawy użytkownik może wykonywać różne zadania związane ze sprawą w zależności od tego, czy mu przypisano niezbędne uprawnienia.  <br/> |
|Zmieniono wyszukiwanie zawartości  <br/> |SearchUpdated  <br/> |Set-ComplianceSearch  <br/> |Wyszukiwanie istniejącej zawartości zostało zmienione. Zmiany mogą obejmować dodawanie lub usuwanie lokalizacji zawartości lub edytowanie zapytania wyszukiwania.  <br/> |
|Zmieniono członkostwo administratora zbierania elektronicznych materiałów dowodowych  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |Zmieniono listę administratorów zbierania elektronicznych materiałów dowodowych w organizacji. To działanie jest rejestrowane, gdy lista administratorów zbierania elektronicznych materiałów dowodowych zostanie zastąpiona grupą nowych użytkowników. Jeśli dodano lub usunięto jednego użytkownika, zostanie zarejestrowana operacja CaseAdminAdded.  <br/> |
|Zmieniono sprawę zbierania elektronicznych materiałów dowodowych  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |Zmieniono sprawę zbierania elektronicznych materiałów dowodowych. Zmiany obejmują zamknięcie otwartej sprawy lub ponowne otwarcie zamkniętej sprawy.  <br/> |
|Zmieniono członkostwo w przypadku zbierania elektronicznych materiałów dowodowych  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |Zmieniono listę członkostwa w przypadku sprawy zbierania elektronicznych materiałów dowodowych. To działanie jest rejestrowane w przypadku zastąpienia wszystkich członków grupą nowych użytkowników. Jeśli dodano lub usunięto pojedynczego członka, zostanie zarejestrowana operacja CaseMemberAdded lub CaseMemberRemoved.  <br/> |
|Zmieniono filtr uprawnień wyszukiwania  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |Zmieniono filtr uprawnień wyszukiwania.  <br/> |
|Zmieniono kwerendę wyszukiwania dla sprawy zbierania elektronicznych materiałów dowodowych  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |Zmieniono hold oparte na kwerendach skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych. Możliwe zmiany obejmują edytowanie zapytania lub zakresu dat w przypadku hold'a opartego na kwerendzie.  <br/> |
|Pobrany element podglądu przeszukiwania zawartości  <br/> |PreviewItemDownloaded  <br/> |Nie dotyczy  <br/> |Użytkownik pobrał element na swój komputer lokalny (klikając link Pobierz **oryginalny** element) podczas wyświetlania podglądu wyników wyszukiwania.  <br/> |
|Na liście znajduje się element podglądu przeszukiwania zawartości  <br/> |PreviewItemListed  <br/> |Nie dotyczy  <br/> |Użytkownik kliknął pozycję **Podgląd** wyników wyszukiwania, aby wyświetlić stronę wyników wyszukiwania podglądu, która zawiera maksymalnie 1000 elementów z wyników wyszukiwania.  <br/> |
|Wyświetlony element podglądu przeszukiwania zawartości  <br/> |PreviewItemRendered  <br/> |Nie dotyczy  <br/> |Menedżer zbierania elektronicznych materiałów dowodowych wyświetlał element, klikając go podczas wyświetlania podglądu wyników wyszukiwania.  <br/> |
|Utworzono wyszukiwanie zawartości  <br/> |SearchCreated  <br/> |New-ComplianceSearch  <br/> |Utworzono nowe wyszukiwanie zawartości.  <br/> |
|Utworzono administratora zbierania elektronicznych materiałów dowodowych  <br/> |CaseAdminAdded  <br/> |Add-eDiscoveryCaseAdmin  <br/> |Dodano użytkownika jako administratora zbierania elektronicznych materiałów dowodowych w organizacji.  <br/> |
|Utworzono sprawę zbierania elektronicznych materiałów dowodowych  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |Utworzono sprawę zbierania elektronicznych materiałów dowodowych. Po utworzeniu sprawy wystarczy nadać jej nazwę. Inne zadania związane ze sprawami, takie jak dodawanie członków, tworzenie blokady i tworzenie przeszukiwań zawartości związanych ze sprawą, skutkować zarejestrowanymi dodatkowymi zdarzeniami.  <br/> |
|Utworzono filtr uprawnień wyszukiwania  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |Utworzono filtr uprawnień wyszukiwania.  <br/> |
|Utworzono zapytanie wyszukiwania dla sprawy zbierania elektronicznych materiałów dowodowych  <br/> |HoldCreated  <br/> |New-CaseHoldRule  <br/> |Utworzono hold oparte na kwerendach skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych.  <br/> |
|Wyszukiwanie usuniętej zawartości  <br/> |SearchRemoved  <br/> |Remove-ComplianceSearch  <br/> |Usunięto istniejące wyszukiwanie zawartości.  <br/> |
|Usunięto administratora zbierania elektronicznych materiałów dowodowych  <br/> |CaseAdminRemoved  <br/> |Remove-eDiscoveryCaseAdmin  <br/> |Administrator zbierania elektronicznych materiałów dowodowych został usunięty z Twojej organizacji.  <br/> |
|Usunięto sprawę zbierania elektronicznych materiałów dowodowych  <br/> |CaseRemoved  <br/> |Remove-ComplianceCase  <br/> |Usunięto sprawę zbierania elektronicznych materiałów dowodowych. Aby można było usunąć sprawę, należy usunąć wszelkie wstrzymanie skojarzone ze sprawą.  <br/> |
|Usunięto filtr uprawnień wyszukiwania  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |Usunięto filtr uprawnień wyszukiwania.  <br/> |
|Usunięto zapytanie wyszukiwania dla sprawy zbierania elektronicznych materiałów dowodowych  <br/> |HoldRemoved  <br/> |Remove-CaseHoldRule  <br/> |Usunięto hold oparte na kwerendach skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych. Usuwanie zapytania z wstrzymywania często jest wynikiem usunięcia hold. Po usunięciu zapytania wstrzymywania lub kwerendy wstrzymywania są zwalniane lokalizacje zawartości, które zostały zawieszone.  <br/> |
|Pobrany eksport wyszukiwania zawartości  <br/> |SearchExportDownloaded  <br/> |Nie dotyczy  <br/> |Użytkownik pobrał wyniki wyszukiwania zawartości na komputer lokalny. Zanim **będzie można pobrać wyniki** wyszukiwania, należy zainicjować rozpoczęte eksportowanie działań wyszukiwania zawartości.  <br/> |
|Podgląd wyników wyszukiwania zawartości  <br/> |SearchPreviewed  <br/> |Nie dotyczy  <br/> |Użytkownik przeglądał wyniki wyszukiwania zawartości.  <br/> |
|Purged results of content search  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |Użytkownik przeczyścił wyniki przeszukiwania zawartości, uruchamiając polecenie **New-ComplianceSearchAction -Purge** .  <br/> |
|Usunięto analizę wyszukiwania zawartości  <br/> |RemovedSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |Usunięto akcję przygotowania wyszukiwania zawartości (w celu przygotowania wyników Advanced eDiscovery). Jeśli akcja przygotowywania miała miejsce za mniej niż dwa tygodnie, wyniki wyszukiwania przygotowane na Advanced eDiscovery zostały usunięte z Microsoft Azure przechowywania. Jeśli akcja przygotowawczy była starsza niż 2 tygodnie, to zdarzenie wskazuje, że usunięto tylko odpowiadającą jej akcję przygotowawczych.  <br/> |
|Usunięto eksportowanie przeszukiwania zawartości  <br/> |RemovedSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |Usunięto akcję eksportowania przeszukiwania zawartości. Jeśli akcja eksportowania miała mniej niż dwa tygodnie, wyniki wyszukiwania przekazane do Microsoft Azure magazynu zostały usunięte. Jeśli akcja eksportowania była starsza niż 2 tygodnie, to zdarzenie wskazuje, że usunięto tylko odpowiadającą jej akcję eksportowania.  <br/> |
|Usunięto członka ze sprawy zbierania elektronicznych materiałów dowodowych  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |Użytkownik został usunięty jako członek sprawy zbierania elektronicznych materiałów dowodowych.  <br/> |
|Usunięto wyniki podglądu wyszukiwania zawartości  <br/> |RemovedSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |Usunięto akcję podglądu przeszukiwania zawartości.  <br/> |
|Usunięto akcję przeczyszczania wykonaną podczas przeszukiwania zawartości  <br/> |RemovedSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |Usunięto akcję przeczyszczania przeszukiwania zawartości.  <br/> |
|Usunięto raport wyszukiwania  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |Usunięto akcję raportu eksportu wyszukiwania zawartości.  <br/> |
|Rozpoczęto analizę wyszukiwania zawartości  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |Wyniki przeszukiwania zawartości zostały przygotowane do analizy w programie Advanced eDiscovery.  <br/> |
|Rozpoczęto wyszukiwanie zawartości  <br/> |SearchStarted  <br/> |Start-ComplianceSearch  <br/> |Rozpoczęto wyszukiwanie zawartości. Wyszukiwanie zawartości jest tworzone lub zmieniane za pomocą Centrum zgodności platformy Microsoft 365 jest automatycznie rozpoczynane.<br/> |
|Rozpoczęto eksportowanie wyszukiwania zawartości  <br/> |SearchExported  <br/> |New-ComplianceSearchAction  <br/> |Użytkownik wyeksportował wyniki wyszukiwania zawartości.  <br/> |
|Rozpoczęto eksportowanie raportu  <br/> |SearchReport  <br/> |New-ComplianceSearchAction  <br/> |Użytkownik wyeksportował raport przeszukiwania zawartości.  <br/> |
|Zatrzymano wyszukiwanie zawartości  <br/> |SearchStopped  <br/> |Stop-ComplianceSearch  <br/> |Użytkownik zatrzymał wyszukiwanie zawartości.  <br/> |
|(brak)|CaseViewed|Get-ComplianceCase|Użytkownik przeglądał podstawową sprawę zbierania elektronicznych materiałów dowodowych w Centrum zgodności. Rekord inspekcji dla tego zdarzenia zawiera nazwę przeglądanego przypadku. |
|(brak)|SearchViewed|Get-ComplianceSearch|Użytkownik przeglądał wyszukiwanie zawartości w Centrum zgodności, korzystając z funkcji wyszukiwania na karcie Wyszukiwania w podstawowej  sprawie zbierania elektronicznych materiałów dowodowych lub korzystając z tej funkcji na stronie **Wyszukiwanie** zawartości. Rekord inspekcji dla tego zdarzenia zawiera tożsamość przeglądanego wyszukiwania.|
|(brak)|ViewedSearchExported|Get-ComplianceSearchAction -Export|Użytkownik przeglądał eksport przeszukiwania zawartości w Centrum zgodności, korzystając z karty Eksportowanie na **stronie Przeszukiwanie** zawartości. To działanie jest rejestrowane również w przypadku wyświetlenia przez użytkownika eksportu skojarzonego z podstawową sprawą zbierania elektronicznych materiałów dowodowych.|
|(brak)|ViewedSearchPreviewed|Get-ComplianceSearchAction —Podgląd|Użytkownik przeglądał wyniki wyszukiwania zawartości w centrum zgodności. To działanie jest również rejestrowane, gdy użytkownik wyświetla podgląd wyników wyszukiwania skojarzonego z podstawową sprawą zbierania elektronicznych materiałów dowodowych.|
|||||
  
## <a name="advanced-ediscovery-activities"></a>Advanced eDiscovery działania

W poniższej tabeli opisano Advanced eDiscovery rejestrowane w dzienniku inspekcji. Te działania mogą ułatwić śledzenie postępu aktywności w Advanced eDiscovery przypadku.

|**Przyjazna nazwa**|**Operacja**|**Opis**|
|:-----|:-----|:-----|
|Dodano dane do innego zestawu recenzji|AddWorkingSetQueryToWorkingSet|Do innego zestawu recenzji dodano dokumenty z jednego zestawu recenzji.|
|Dodano dane do przejrzenia zestawu|AddQueryToWorkingSet|Użytkownik dodał wyniki wyszukiwania z przeszukiwania zawartości skojarzonego z Advanced eDiscovery przypadku recenzji.|
|Dodano dane Microsoft 365 do przejrzenia zestawu|AddNonOffice365DataToWorkingSet|Do zestawu Microsoft 365 dodano dane inne niż te.|
|Dodano dokumenty zaradcze, aby przejrzeć zestaw|AddRemediatedData|Użytkownik przekaże dokumenty, w których wystąpiły błędy indeksowania naprawione w zestawie recenzji.|
|Analizowane dane w zestawie recenzji|RunAlgo|Użytkownik uruchomił analizę dokumentów w zestawie recenzji.|
|Dokument z adnotacjami w zestawie recenzji|AdnotacjaDokument|Użytkownik dodał adnotację do dokumentu w zestawie recenzji. Adnotacja obejmuje redagowanie zawartości w dokumencie.|
|Porównanie zestawów obciążenia|LoadComparisonJob|Użytkownik porównał dwa różne zestawy ładowania w zestawie recenzji. Zestaw ładowania jest wtedy, gdy do zestawu recenzji są dodawane dane z przeszukiwania zawartości skojarzonego ze sprawą.|
|Przekonwertowane dokumenty redagowane na format PDF|BurnJob|Użytkownik przekonwertował wszystkie dokumenty redagowane w zestawie recenzji na pliki PDF.|
|Utworzono zestaw recenzji|CreateWorkingSet|Użytkownik utworzył zestaw recenzji.|
|Utworzono wyszukiwanie zestawu recenzji|CreateWorkingSetSearch|Użytkownik utworzył zapytanie wyszukiwania, które przeszukuje dokumenty w zestawie recenzji.|
|Utworzono tag|CreateTag|Użytkownik utworzył grupę tagów w zestawie recenzji. Grupa tagów może zawierać co najmniej jeden tag podrzędny. Te tagi są następnie używane do oznaczania dokumentów w zestawie recenzji.|
|Usunięto wyszukiwanie zestawu recenzji|DeleteWorkingSetSearch|Użytkownik usunął zapytanie wyszukiwania w zestawie recenzji.|
|Usunięto tag|DeleteTag|Użytkownik usunął tag lub grupę tagów w zestawie recenzji.|
|Pobrano dokument|DownloadDocument|Użytkownik pobrał dokument z zestawu recenzji.|
|Edytowano tag|UpdateTag|Użytkownik zmienił tag w zestawie recenzji.|
|Wyeksportowano dokumenty z zestawu recenzji|ExportJob|Dokumenty wyeksportowane przez użytkownika z zestawu recenzji.|
|Zmodyfikowano ustawienie sprawy|UpdateCaseSettings|Użytkownik zmodyfikował ustawienia dotyczące sprawy. Ustawienia sprawy obejmują informacje o przypadku, uprawnienia dostępu i ustawienia, które kontrolują zachowanie wyszukiwania i analizy.|
|Zmodyfikowano wyszukiwanie zestawu recenzji|UpdateWorkingSetSearch|Użytkownik edytował zapytanie wyszukiwania w zestawie recenzji.|
|Wyszukiwanie zestawu podglądu recenzji|PreviewWorkingSetSearch|Użytkownik przeglądał wyniki zapytania wyszukiwania w zestawie recenzji.|
|Dokumenty o błędach usunięte|ErrorRemediationJob|Użytkownik naprawi pliki zawierające błędy indeksowania.|
|Dokument oznakowany|TagFiles|Oznaczanie dokumentu w zestawie recenzji przez użytkownika.|
|Oznakowane wyniki kwerendy|TagJob|Oznacza wszystkie dokumenty zgodne z kryteriami zapytania wyszukiwania w zestawie recenzji.|
|Widok dokumentu w zestawie recenzji|ViewDocument|Użytkownik przeglądał dokument w zestawie recenzji.|
|||

## <a name="ediscovery-cmdlet-activities"></a>Działania polecenia cmdlet zbierania elektronicznych materiałów dowodowych

W poniższej tabeli wymieniono rekordy dziennika inspekcji polecenia cmdlet rejestrowane wtedy, gdy administrator lub użytkownik wykonuje działanie związane z zbierania elektronicznych materiałów dowodowych przy użyciu Centrum zgodności lub uruchamiając odpowiednie polecenie cmdlet w programie PowerShell w centrum zabezpieczeń & zgodności. Szczegółowe informacje w rekordzie dziennika inspekcji różnią się w przypadku działań dotyczących polecenia cmdlet wymienionych w tej tabeli i działań dotyczących zbierania elektronicznych materiałów dowodowych opisanych w poprzedniej sekcji.
  
Jak wspomniano wcześniej, może upłynieć do 24 godzin, aż działania związane z poleceniami cmdlet zbierania elektronicznych materiałów dowodowych pojawią się w wynikach przeszukiwania dziennika inspekcji.
  
> [!TIP]
> Polecenia cmdlet w kolumnie **Operation** w poniższej tabeli są połączone z odpowiadającym mu tematem pomocy polecenia cmdlet w witrynie TechNet. Przejdź do tematu pomocy polecenia cmdlet, aby uzyskać opis dostępnych parametrów dla każdego polecenia cmdlet. Parametr i wartość parametru, które były używane z poleceniem cmdlet, są uwzględniane we wpisie dziennika inspekcji dla każdego rejestrowanego działania cmdlet zbierania elektronicznych materiałów dowodowych. 
  
|**Przyjazna nazwa**|**Operacja (polecenie cmdlet)**|**Opis**|
|:-----|:-----|:-----|
|Utworzono wstrzymaj w przypadku zbierania elektronicznych materiałów dowodowych  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |Utworzono wstrzymanie dla sprawy zbierania elektronicznych materiałów dowodowych. Można utworzyć wstrzymanie z określeniem źródła zawartości lub bez niego. Jeśli źródła zawartości zostaną określone, zostaną zidentyfikowane we wpisie dziennika inspekcji.  <br/> |
|Usunięto wstrzymanie ze sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |Usunięto hold skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych. Usunięcie wstrzymywania zwalnia wszystkie lokalizacje zawartości z tego miejsca. Usunięcie tej trzymania powoduje również usunięcie reguł holdu sprawy skojarzonych z hold (zobacz **Remove-CaseHoldRule** poniżej).  <br/> |
|Zmieniono hold w przypadku zbierania elektronicznych materiałów dowodowych  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |Zmieniono hold skojarzone z zbierania elektronicznych materiałów dowodowych. Możliwe zmiany obejmują dodawanie lub usuwanie lokalizacji zawartości lub wyłączanie (wyłączanie) zawieszonego miejsca.  <br/> |
|Utworzono zapytanie wyszukiwania dla sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule) <br/> |Utworzono hold oparte na kwerendach skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych.  <br/> |
|Usunięto zapytanie wyszukiwania dla sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-CaseHoldRule](/powershell/module/exchange/remove-caseholdrule) <br/> |Usunięto hold oparte na kwerendach skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych. Usuwanie zapytania z wstrzymywania często jest wynikiem usunięcia hold. Po usunięciu zapytania wstrzymywania lub kwerendy wstrzymywania są zwalniane lokalizacje zawartości, które zostały zawieszone.  <br/> |
|Zmieniono kwerendę wyszukiwania dla sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Set-CaseHoldRule](/powershell/module/exchange/set-caseholdrule) <br/> |Zmieniono hold oparte na kwerendach skojarzone ze sprawą zbierania elektronicznych materiałów dowodowych. Możliwe zmiany obejmują edytowanie zapytania lub zakresu dat w przypadku hold'a opartego na kwerendzie.  <br/> |
|Utworzono sprawę zbierania elektronicznych materiałów dowodowych  <br/> |[New-ComplianceCase](/powershell/module/exchange/new-compliancecase) <br/> |Utworzono sprawę zbierania elektronicznych materiałów dowodowych. Po utworzeniu sprawy wystarczy nadać jej nazwę. Inne zadania związane ze sprawami, takie jak dodawanie członków, tworzenie blokady i tworzenie przeszukiwań zawartości związanych ze sprawą, skutkować zarejestrowanymi dodatkowymi zdarzeniami.  <br/> |
|Usunięto sprawę zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-ComplianceCase](/powershell/module/exchange/remove-compliancecase) <br/> |Usunięto sprawę zbierania elektronicznych materiałów dowodowych. Aby można było usunąć sprawę, należy usunąć wszelkie wstrzymanie skojarzone ze sprawą.  <br/> |
|Zmieniono sprawę zbierania elektronicznych materiałów dowodowych  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |Zmieniono sprawę zbierania elektronicznych materiałów dowodowych. Zmiany obejmują zamknięcie otwartej sprawy lub ponowne otwarcie zamkniętej sprawy.  <br/> |
|Dodano członka do sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |Użytkownik został dodany jako członek sprawy zbierania elektronicznych materiałów dowodowych. Jako członek sprawy użytkownik może wykonywać różne zadania związane ze sprawą w zależności od tego, czy mu przypisano niezbędne uprawnienia.  <br/> |
|Usunięto członka ze sprawy zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |Użytkownik został usunięty jako członek sprawy zbierania elektronicznych materiałów dowodowych.  <br/> |
|Zmieniono członkostwo w przypadku zbierania elektronicznych materiałów dowodowych  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |Zmieniono listę członkostwa w przypadku sprawy zbierania elektronicznych materiałów dowodowych. To działanie jest rejestrowane w przypadku zastąpienia wszystkich członków grupą nowych użytkowników. Jeśli dodasz lub usuniesz pojedynczego członka, zostanie zarejestrowana operacja **Add-ComplianceCaseMember** lub **Remove-ComplianceCaseMember** .  <br/> |
|Utworzono wyszukiwanie zawartości  <br/> |[Wyszukiwanie nowych zgodności](/powershell/module/exchange/new-compliancesearch) <br/> |Utworzono nowe wyszukiwanie zawartości.  <br/> |
|Wyszukiwanie usuniętej zawartości  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |Usunięto istniejące wyszukiwanie zawartości.  <br/> |
|Zmieniono wyszukiwanie zawartości  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |Wyszukiwanie istniejącej zawartości zostało zmienione. Zmiany te mogą obejmować dodawanie lub usuwanie lokalizacji zawartości, które są przeszukiwane i edytowane przez zapytanie wyszukiwania.  <br/> |
|Rozpoczęto wyszukiwanie zawartości  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |Rozpoczęto wyszukiwanie zawartości. Wyszukiwanie jest automatycznie rozpoczynane podczas tworzenia lub zmieniania wyszukiwania zawartości przy użyciu graficznego interfejsu użytkownika centrum zgodności. Jeśli utworzysz lub zmienisz wyszukiwanie za pomocą polecenia cmdlet **New-ComplianceSearch** lub **Set-ComplianceSearch** , musisz uruchomić polecenie cmdlet **Start-ComplianceSearch** , aby rozpocząć wyszukiwanie.  <br/> |
|Zatrzymano wyszukiwanie zawartości  <br/> |[Stop-ComplianceSearch](/powershell/module/exchange/stop-compliancesearch) <br/> |Wyszukiwanie zawartości, które zostało uruchomione, zostało zatrzymane.  <br/> |
|Utworzono akcję wyszukiwania zawartości  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |Utworzono akcję wyszukiwania zawartości. Akcje przeszukiwania zawartości obejmują wyświetlanie podglądu wyników wyszukiwania, eksportowanie wyników wyszukiwania, przygotowywanie wyników wyszukiwania do analizy w programie Advanced eDiscovery oraz trwałe usuwanie elementów, które spełniają kryteria wyszukiwania przeszukiwania zawartości.  <br/> |
|Akcja wyszukiwania usuniętej zawartości  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |Usunięto akcję wyszukiwania zawartości.  <br/> |
|Utworzono filtr uprawnień wyszukiwania  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |Utworzono filtr uprawnień wyszukiwania.  <br/> |
|Usunięto filtr uprawnień wyszukiwania  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |Usunięto filtr uprawnień wyszukiwania.  <br/> |
|Zmieniono filtr uprawnień wyszukiwania  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |Zmieniono filtr uprawnień wyszukiwania.  <br/> |
|Utworzono administratora zbierania elektronicznych materiałów dowodowych  <br/> |[Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |Użytkownik został dodany jako administrator zbierania elektronicznych materiałów dowodowych w Twojej organizacji.  <br/> |
|Usunięto administratora zbierania elektronicznych materiałów dowodowych  <br/> |[Remove-eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |Administrator zbierania elektronicznych materiałów dowodowych został usunięty z Twojej organizacji.  <br/> |
|Zmieniono członkostwo administratora zbierania elektronicznych materiałów dowodowych  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |Zmieniono listę administratorów zbierania elektronicznych materiałów dowodowych w organizacji. To działanie jest rejestrowane, gdy lista administratorów zbierania elektronicznych materiałów dowodowych zostanie zastąpiona grupą nowych użytkowników. Jeśli dodano lub usunięto pojedynczego użytkownika, zostanie zarejestrowana operacja **Add-eDiscoveryCaseAdmin** lub **Remove-eDiscoveryCaseAdmin** .  <br/> |
|(brak)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|To działanie jest rejestrowane, gdy użytkownik wyświetla listę podstawowych zbierania elektronicznych materiałów dowodowych lub spraw Advanced eDiscovery e-mail. To działanie jest również rejestrowane, gdy użytkownik może wyświetlenia określonej sprawy w podstawowym zbierania elektronicznych materiałów dowodowych. Gdy użytkownik wyświetla określoną sprawę, rekord inspekcji zawiera tożsamość dotyczącej właśnie tej sprawy. Jeśli użytkownik wyświetlał tylko listę spraw, rekord inspekcji nie zawiera tożsamości sprawy.|
|(brak)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|To działanie jest rejestrowane, gdy użytkownik wyświetla listę przeszukiwań zawartości lub wyszukiwań skojarzonych z podstawową sprawą zbierania elektronicznych materiałów dowodowych. To działanie jest również rejestrowane, gdy użytkownik wyświetly określone wyszukiwanie zawartości lub konkretne wyszukiwanie skojarzone z podstawową sprawą zbierania elektronicznych materiałów dowodowych. Gdy użytkownik wyświetla określone wyszukiwanie, rekord inspekcji zawiera tożsamość przeglądanych wyszukiwań. Jeśli użytkownik wyświetlał tylko listę wyszukiwań, rekord inspekcji nie zawiera tożsamości wyszukiwania.
|(brak)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|To działanie jest rejestrowane, gdy użytkownik wyświetlał listę akcji wyszukiwania dotyczących zgodności (takich jak operacje eksportowania, podglądów lub przeczyszczania) lub akcji skojarzonych z podstawową sprawą zbierania elektronicznych materiałów dowodowych. To działanie jest również rejestrowane, gdy użytkownik zobaczy określoną akcję wyszukiwania zgodności (na przykład eksport) lub widoki określonej akcji skojarzonej z podstawową sprawą zbierania elektronicznych materiałów dowodowych. Gdy użytkownik wyświetla akcję wyszukiwania, rekord inspekcji zawiera tożsamość przeglądanych akcji wyszukiwania. Jeśli użytkownik wyświetlał tylko listę akcji, rekord inspekcji nie zawiera tożsamości akcji.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>Szczegółowe właściwości działań zbierania elektronicznych materiałów dowodowych

W poniższej tabeli opisano właściwości, które są zawarte na stronie wysuwu dla działań zbierania elektronicznych materiałów dowodowych wymienionych w wynikach wyszukiwania. Te właściwości są także uwzględniane w pliku CSV podczas eksportowania wyników przeszukiwania dziennika inspekcji. Rekord dziennika inspekcji dla działania zbierania elektronicznych materiałów dowodowych nie będzie zawierał wszystkich szczegółowych właściwości wymienionych poniżej.
  
> [!TIP]
> Podczas eksportowania wyników wyszukiwania plik CSV zawiera kolumnę **o nazwie AudtiData**, która zawiera szczegółowe właściwości opisane w poniższej tabeli we właściwości wielowymiarowej. Za pomocą funkcji Power Query w programie Excel można podzielić tę kolumnę na wiele kolumn, dzięki czemu każda właściwość będzie mieć własną kolumnę. Pozwoli to sortować i filtrować według co najmniej jednej z tych właściwości. Aby uzyskać więcej informacji, zobacz sekcję "Eksportowanie wyników wyszukiwania do pliku" w [sekcji Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file). 
  
|**Właściwość**|**Opis**|
|:-----|:-----|
|Sprawa  <br/> |Tożsamość (GUID) sprawy zbierania elektronicznych materiałów dowodowych, która została utworzona, zmieniona lub usunięta.  <br/> |
|ClientApplication  <br/> |Działania polecenia cmdlet zbierania elektronicznych materiałów dowodowych mają dla tej właściwości wartość **EMC** . Oznacza to, że działanie zostało wykonane przy użyciu graficznego interfejsu użytkownika centrum zgodności lub uruchomienia polecenia cmdlet w programie PowerShell.  <br/> |
|ClientIP (ClientIP)  <br/> |Adres IP urządzenia używanego w czasie rejestrowanego działania. Adres IP jest wyświetlany w formacie adresu IPv4 lub IPv6.  <br/> |
|ClientRequestId  <br/> | W przypadku działań zbierania elektronicznych materiałów dowodowych ta właściwość jest zwykle pusta.  <br/> |
|CmdletVersion  <br/> |Numer kompilacji wersji centrum zgodności działającego w organizacji.  <br/> |
|CreationTime  <br/> |Data i godzina zakończenia działania zbierania elektronicznych materiałów dowodowych w uniwersalnym czasie koordynowanej (UTC).  <br/> |
|EffectiveOrganization  <br/> |Nazwa organizacji platformy Microsoft 365.  <br/> |
|ExchangeLocations  <br/> |Skrzynki Exchange Online, które są uwzględnione w wyszukiwaniu zawartości lub umieszczone w wstrzymywaniu w przypadku zbierania elektronicznych materiałów dowodowych.  <br/> |
|Wykluczenia  <br/> |Lokalizacje skrzynki pocztowej lub witryny wykluczone z wyszukiwania zawartości lub zarchiwi w przypadku sprawy zbierania elektronicznych materiałów dowodowych.  <br/> |
|ExtendedProperties (Właściwości rozszerzone)  <br/> |Dodatkowe właściwości z przeszukiwania zawartości, akcji wyszukiwania zawartości lub wstrzymywania w przypadku zbierania elektronicznych materiałów dowodowych, takie jak identyfikator GUID obiektu i odpowiadające im parametry polecenia cmdlet i polecenia cmdlet, które były używane podczas działania.  <br/> |
|Identyfikator  <br/> |Identyfikator wpisu w raporcie. Identyfikator jednoznacznie określa wpis dziennika inspekcji.  <br/> |
|NonPIIParameters  <br/> |Lista parametrów (bez żadnych wartości) użytych z poleceniem cmdlet wskazanym we właściwości Operation. Parametry wymienione w tej właściwości są takie same jak parametry wymienione we właściwości Parameters.  <br/> |
|ObjectId  <br/> |Identyfikator GUID lub nazwa obiektu (na przykład Przeszukiwanie zawartości lub Podstawowa sprawa zbierania elektronicznych materiałów dowodowych), który został utworzony, do którego uzyskał dostęp, został zmieniony lub usunięty przez działanie wymienione we właściwości Operation. Ten obiekt jest także identyfikowany w kolumnie Element w wynikach przeszukiwania dziennika inspekcji.  <br/> |
|ObjectType  <br/> |Typ obiektu zbierania elektronicznych materiałów dowodowych, który użytkownik utworzył, usunął lub zmodyfikował; na przykład akcja wyszukiwania zawartości (podgląd, eksport lub przeczyszczanie), sprawa zbierania elektronicznych materiałów dowodowych lub przeszukiwanie zawartości.  <br/> |
|Operacja  <br/> |Nazwa operacji odpowiadającej wykonanemu działaniu zbierania elektronicznych materiałów dowodowych.  <br/> |
|OrganizationId  <br/> |Identyfikator GUID organizacji Microsoft 365 organizacji.  <br/> |
|Parametry  <br/> |Nazwa i wartość parametrów użytych z odpowiadającym mu poleceniem cmdlet.  <br/> |
|PublicFolderLocations  <br/> |Lokalizacje folderów publicznych w Exchange Online, które są uwzględniane podczas przeszukiwania zawartości lub umieszczane w wstrzymywaniu w przypadku zbierania elektronicznych materiałów dowodowych.  <br/> |
|Zapytanie  <br/> |Zapytanie wyszukiwania skojarzone z działaniem, na przykład wyszukiwanie zawartości lub hold oparte na kwerendzie.  <br/> |
|RecordType (Typ rekordu)  <br/> |Typ operacji wskazywanej przez rekord. Wartość **18 wskazuje** zdarzenie związane z działaniem wymienionym w sekcji [działania polecenia cmdlet](#ediscovery-cmdlet-activities) zbierania elektronicznych materiałów dowodowych. Wartość **24** oznacza zdarzenie związane z działaniem wymienionym w sekcji Jak wyszukiwać i wyświetlać działania zbierania [elektronicznych materiałów](#how-to-search-for-and-view-ediscovery-activities) dowodowych.  <br/> |
|ResultStatus (Statystyka wyników)  <br/> |Wskazuje, czy akcja (określona we właściwości Operation) powiodła się, czy nie.  <br/> |
|SecurityComplianceCenterEventType (Typotypu rozwiązania SecurityComplianceCenter)  <br/> |Oznacza, że działanie było zdarzeniem centrum zgodności. Dla wszystkich działań zbierania elektronicznych materiałów dowodowych ta właściwość będzie mieć wartość **0** .  <br/> |
|SharePointLocations  <br/> |Witryny SharePoint Online, które są uwzględnione w wyszukiwaniu zawartości lub umieszczone w akwedycie sprawy zbierania elektronicznych materiałów dowodowych.  <br/> |
|StartTime  <br/> |Data i godzina rozpoczęcia działania zbierania elektronicznych materiałów dowodowych w uniwersalnym czasie koordynowanych (UTC).  <br/> |
|UserId  <br/> |Użytkownik, który wykonał działanie (wskazane przez właściwość Operation), w wyniku którego zarejestrowano rekord. Dziennik inspekcji zawiera również rekordy dotyczące działań zbierania elektronicznych materiałów dowodowych wykonywanych przez konta systemowe (takie jak NT AUTHORITY\SYSTEM).  <br/> |
|UserKey (Klucz użytkownika)  <br/> |Alternatywny identyfikator użytkownika wskazanego przez właściwość UserId. W przypadku działań zbierania elektronicznych materiałów dowodowych wartość tej właściwości jest zwykle taka sama jak właściwość UserId.  <br/> |
|UserServicePlan  <br/> |Subskrypcja używana przez Twoją organizację. W przypadku działań zbierania elektronicznych materiałów dowodowych ta właściwość jest zwykle pusta.  <br/> |
|UserType (Typ użytkownika)  <br/> |Typ użytkownika, który wykonał operację. Następujące wartości wskazują typ użytkownika.  <br/> 0 Zwykły użytkownik. 2 Administrator w organizacji. 3 Administrator centrum danych firmy Microsoft lub konto systemowe centrum danych. 4 Konto systemowe. 5 Aplikacja. 6 Podmiot zabezpieczeń usługi. |
|Wersja  <br/> |Numer wersji zarejestrowanego działania (wskazanego przez właściwość Operation).  <br/> |
|Obciążenie pracą  <br/> |Usługa, w której wystąpiło działanie. W przypadku działań zbierania elektronicznych materiałów dowodowych wartością jest **SecurityComplianceCenter**.  <br/> |
