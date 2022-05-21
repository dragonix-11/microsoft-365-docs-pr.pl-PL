---
title: Model danych analizy użycia platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 08c5307c-4a6b-4761-8410-a6c96725760f
description: 'Dowiedz się, jak analiza użycia łączy się z interfejsem API i zapewnia miesięczny trend użycia różnych usług Microsoft 365.  '
ms.openlocfilehash: 05b8a6d9a69cc6347b4d2cdcfbdeaa26bd479cbd
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65620987"
---
# <a name="microsoft-365-usage-analytics-data-model"></a>Model danych analizy użycia platformy Microsoft 365

## <a name="data-for-the-microsoft-365-usage-analytics-tables"></a>Dane tabel analizy użycia platformy Microsoft 365

Microsoft 365 analiza użycia łączy się z interfejsem API, który uwidacznia wielowymiarowy model danych. Interfejsy API używane Microsoft 365 analizy użycia do generowania danych pochodzą z różnych, ogólnie dostępnych interfejsów API Graph. Funkcja interfejsu API analizy użycia Microsoft 365 sama w sobie nie jest ogólnie dostępna.
  
> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [Working with Microsoft 365 usage reports in Microsoft Graph (Praca z raportami użycia Microsoft 365 w usłudze Microsoft Graph](/graph/api/resources/report)). 
  
Ten interfejs API zawiera informacje o miesięcznym trendzie użycia różnych usług Microsoft 365. Aby dowiedzieć się, jakie dokładnie dane są zwracane przez interfejs API, zapoznaj się z tabelą w następnej sekcji.
  
## <a name="data-tables-returned-by-the-microsoft-365-reporting-api"></a>Tabele danych zwracane przez interfejs API raportowania Microsoft 365

|**Nazwa tabeli**|**Informacje zawarte w tabeli**|**Zakres dat**|
|:-----|:-----|:-----|
|Użycie produktu w dzierżawie  <br/> |Zawiera miesięczne sumy włączonych, aktywnych użytkowników, użytkowników przechowywanych miesiąc do miesiąca, użytkowników po raz pierwszy i skumulowanych aktywnych użytkowników.  <br/> |Zagregowane dane miesięczne dotyczące trwającego 12-miesięcznego okresu z uwzględnieniem bieżącego, niepełnego miesiąca.  <br/> |
|Działania na produkcie w dzierżawie  <br/> |Zawiera miesięczne sumy działań i liczbę aktywnych użytkowników dla różnych działań w ramach produktów.  <br/> Zobacz [definicję aktywnego użytkownika](active-user-in-usage-reports.md), aby uzyskać informacje o działaniach w obrębie produktów, które są zwracane w tej tabeli.  <br/> |Zagregowane dane miesięczne dotyczące trwającego 12-miesięcznego okresu z uwzględnieniem bieżącego, niepełnego miesiąca.  <br/> |
|Licencje pakietu Office w dzierżawie  <br/> |Dane dotyczące liczby subskrypcji pakietu Microsoft Office przypisanych do użytkowników.  <br/> |Zawiera dane stanu na koniec miesiąca dla kroczącego okresu 12 miesięcy, w tym bieżącego miesiąca częściowego.  <br/> |
|Użycie skrzynek pocztowych w dzierżawie  <br/> |Zawiera dane dotyczące skrzynki pocztowej użytkownika, łącznej liczby skrzynek pocztowych i sposobu użycia magazynu.  <br/> |Zawiera dane stanu na koniec miesiąca dla kroczącego okresu 12 miesięcy, w tym bieżącego miesiąca częściowego.  <br/> |
|Użycie klientów w dzierżawie  <br/> |Dane dotyczące liczby użytkowników aktywnie korzystających z określonych klientów/urządzeń w celu nawiązywania połączenia z usługami Exchange Online, Skype dla firm i Yammer.  <br/> |Zagregowane dane miesięczne dotyczące trwającego 12-miesięcznego okresu z uwzględnieniem bieżącego, niepełnego miesiąca.  <br/> |
|Użycie usługi SharePoint Online w dzierżawie  <br/> |Dane dotyczące witryn programu SharePoint dla witryn zespołów i grup  na przykład łączna liczba witryn, liczba dokumentów w witrynie, liczba plików według typu działania i użyte miejsce do magazynowania.  <br/> |Zawiera dane stanu na koniec miesiąca dla kroczącego okresu 12 miesięcy, w tym bieżącego miesiąca częściowego.  <br/> |
|Użycie usługi OneDrive dla Firm w dzierżawie  <br/> |Dane dotyczące kont usługi OneDrive, takie jak liczba kont, liczba dokumentów w usługach OneDrive, użyte miejsce do magazynowania, liczba plików według typu działania.  <br/> |Zawiera dane stanu na koniec miesiąca dla kroczącego okresu 12 miesięcy, w tym bieżącego miesiąca częściowego.  <br/> |
|Użycie Grupy Microsoft 365 dzierżawy  <br/> |Zawiera dane dotyczące użycia Grupy Microsoft 365, w tym skrzynki pocztowej, SharePoint i Yammer.  <br/> |Zawiera dane stanu na koniec miesiąca dla kroczącego okresu 12 miesięcy, w tym bieżącego miesiąca częściowego.  <br/> |
|Aktywacje pakietu Office w dzierżawie  <br/> |Zawiera dane dotyczące liczby aktywacji subskrypcji Office, liczby aktywacji na urządzenie (Android/iOS/Mac/PC), aktywacji według planu usługi, na przykład Aplikacje Microsoft 365 dla przedsiębiorstw, Visio, Project.  <br/> |Zawiera dane stanu na koniec miesiąca dla kroczącego okresu 12 miesięcy, w tym bieżącego miesiąca częściowego.  <br/> |
|Stan użytkowników  <br/> |Metadane dotyczące użytkowników, takie jak nazwa wyświetlana użytkownika, przypisane produkty, lokalizacja, dział, tytuł, firma. Te dane dotyczą użytkowników, którzy otrzymali licencję w ostatnim pełnym miesiącu. Każdy użytkownik jest unikatowo reprezentowany przez identyfikator użytkownika.  <br/> |Te dane dotyczą użytkowników, którym przypisano licencję podczas ostatniego pełnego miesiąca.  <br/> |
|Działania użytkowników  <br/> |Informacje dla poszczególnych poziomów użytkowników dotyczące działań wykonywanych przez licencjonowanych użytkowników.  <br/> Zobacz [definicję aktywnego użytkownika](active-user-in-usage-reports.md), aby uzyskać informacje o działaniach w obrębie produktów, które są zwracane w tej tabeli.  <br/> |Te dane dotyczą użytkowników, którzy wykonali jakieś działanie w dowolnej z usług podczas ostatniego pełnego miesiąca.  <br/> |
   
Rozwiń poniższe sekcje, aby wyświetlić szczegółowe informacje dla każdej tabeli danych.
  
### <a name="data-table---user-state"></a>Tabela danych  Stan użytkowników

Ta tabela zawiera szczegółowe informacje na poziomie użytkownika dla wszystkich użytkowników, którzy mają przypisaną licencję w ostatnim pełnym miesiącu. Dane są pobierane z usługi Azure Active Directory.
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|Userid  <br/> |Unikatowy identyfikator użytkownika, który reprezentuje użytkownika i umożliwia łączenie się z innymi tabelami danych w zestawie danych.  <br/> |
|Timeframe  <br/> |Wartość miesiąca, którego dotyczą dane zawarte w tabeli.  <br/> |
|UPN  <br/> |Główna nazwa użytkownika, która określa użytkownika w sposób jednoznaczny w celu umożliwienia połączenia z innymi zewnętrznymi źródłami danych.  <br/> |
|Displayname  <br/> |Nazwa wyświetlana użytkownika.  <br/> |
|IDType  <br/> |Typ identyfikatora jest ustawiony na wartość 1, jeśli użytkownik jest użytkownikiem Yammer, który łączy się przy użyciu identyfikatora Yammer lub 0, jeśli łączy się z Yammer przy użyciu identyfikatora Microsoft 365.  <br/> Wartość to 1, która oznacza, że ten użytkownik łączy się z Yammer przy użyciu identyfikatora Yammer, a nie identyfikatora Microsoft 365  <br/> |
|HasLicenseEXO  <br/> |Ustaw wartość true, jeśli użytkownik ma przypisaną licencję i może używać Exchange w ostatnim dniu miesiąca.  <br/> |
|HasLicenseODB  <br/> |Ustaw wartość true, jeśli użytkownik ma przypisaną licencję i może używać OneDrive dla Firm w ostatnim dniu miesiąca.  <br/> |
|HasLicenseSPO  <br/> |Ustaw wartość true, jeśli użytkownikowi przypisano licencję i włączono możliwość korzystania z usługi SharePoint Online w ostatnim dniu miesiąca.  <br/> |
|HasLicenseYAM  <br/> |Ustaw wartość true, jeśli użytkownik ma przypisaną licencję i może używać Yammer w ostatnim dniu miesiąca.  <br/> |
|HasLicenseSFB  <br/> |Ustaw wartość true, jeśli użytkownikowi przypisano licencję i włączono możliwość korzystania z Skype for Business w ostatnim dniu miesiąca.  <br/> |
|HasLicenseTeams  <br/> |Ustaw wartość true, jeśli użytkownikowi przypisano licencję i włącz korzystanie z Microsoft Teams w ostatnim dniu miesiąca.  <br/> |
|Company  <br/> |Dane firmy przypisane do tego użytkownika w usłudze Azure Active Directory.  <br/> |
|Department  <br/> |Dane działu przypisane do tego użytkownika w usłudze Azure Active Directory.  <br/> |
|LokalizacjaCity  <br/> |Dane miasta przypisane do tego użytkownika w usłudze Azure Active Directory.  <br/> |
|LocationCountry  <br/> |Dane kraju przypisane do tego użytkownika w usłudze Azure Active Directory.  <br/> |
|LocationState  <br/> |Dane województwa przypisane do tego użytkownika w usłudze Azure Active Directory.  <br/> |
|LokalizacjaOffice  <br/> |Biuro użytkownika.  <br/> |
|Title  <br/> |Dane tytułu przypisane do tego użytkownika w usłudze Azure Active Directory.  <br/> |
|Deleted  <br/> |Prawda, jeśli użytkownik został usunięty z Microsoft 365 w ostatnim pełnym miesiącu.  <br/> |
|DeletedDate  <br/> |Data usunięcia użytkownika z Microsoft 365.  <br/> |
|YAM_State  <br/> |Stany użytkownika w systemie Yammer mogą być aktywne, usunięte lub zawieszone.  <br/> |
|YAM_ActivationDate  <br/> |Data wprowadzenia użytkownika w stan „aktywny" w usłudze Yammer.  <br/> |
|YAM_DeletionDate  <br/> |Data wprowadzenia użytkownika w stan „usunięto" w usłudze Yammer.  <br/> |
|YAM_SuspensionDate  <br/> |Data wprowadzenia użytkownika w stan „zawieszono" w usłudze Yammer.  <br/> |
   
### <a name="data-table---user-activity"></a>Tabela danych  Działania użytkowników

Ta tabela zawiera dane dotyczące każdego użytkownika, który wykonał jakiekolwiek działania w którejkolwiek usłudze w poprzednim miesiącu.
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|Userid  <br/> |Unikatowy identyfikator użytkownika, który reprezentuje użytkownika i umożliwia łączenie się z innymi tabelami danych w zestawie danych.  <br/> |
|IDType  <br/> |Typ identyfikatora jest ustawiony na wartość 1, jeśli użytkownik jest użytkownikiem Yammer, który łączy się przy użyciu identyfikatora Yammer lub 0, jeśli łączy się z Yammer przy użyciu identyfikatora Microsoft 365.  <br/> Wartość to 1, która oznacza, że ten użytkownik łączy się z Yammer przy użyciu identyfikatora Yammer, a nie identyfikatora Microsoft 365  <br/> |
|Timeframe  <br/> |Wartość miesiąca, którego dotyczą dane przedstawione w tej tabeli.  <br/> |
|EXO_EmailSent  <br/> |Liczba wysłanych wiadomości e-mail.  <br/> |
|EXO_EmailReceived  <br/> |Liczba otrzymanych wiadomości e-mail.  <br/> |
|EXO_EmailRead  <br/> |Liczba działań odczytu wiadomości e-mail wykonywanych przez użytkownika, może to być wielokrotne odczytywanie przeczytanej wiadomości e-mail lub odebrana wcześniej wiadomość e-mail.  <br/> |
|EXO_AppointmentCreated  <br/> |Liczba utworzonych spotkań.  <br/> |
|EXO_MeetingAccepted  <br/> |Liczba zaakceptowanych spotkań.  <br/> |
|EXO_MeetingCancelled  <br/> |Liczba odwołanych spotkań.  <br/> |
|EXO_MeetingDeclined  <br/> |Liczba odrzuconych spotkań.  <br/> |
|EXO_MeetingSent  <br/> |Liczba wysłanych spotkań.  <br/> |
|ODB_FileViewedModified  <br/> |Liczba plików, na których użytkownik wykonywał działania w dowolnej usłudze OneDrive dla Firm (może to być np. tworzenie, aktualizowanie, usuwanie, wyświetlanie lub pobieranie).  <br/> |
|ODB_FileSynched  <br/> |Liczba plików zsynchronizowanych przez danego użytkownika w dowolnej usłudze OneDrive dla Firm.  <br/> |
|ODB_FileSharedInternally  <br/> |Liczba plików udostępnionych wewnętrznie przez tego użytkownika z dowolnego OneDrive dla Firm lub użytkowników w grupach (które mogą obejmować użytkowników zewnętrznych).  <br/> |
|ODB_FileSharedExternally  <br/> |Liczba plików udostępnionych zewnętrznie przez danego użytkownika w dowolnej usłudze OneDrive dla Firm.  <br/> |
|ODB_AccessedByOwner  <br/> |Liczba witryn, z którymi użytkownik wchodził w interakcję, znajdujących się na własnych OneDrive dla Firm.  <br/> |
|ODB_AccessedByOthers  <br/> |Liczba witryn, z którymi ten użytkownik wchodził w interakcję, które znajdują się w OneDrive dla Firm innego użytkownika.  <br/> |
|SPO_GroupFileViewedModified  <br/> |Liczba plików, z których użytkownik wchodził w interakcję w dowolnej witrynie grupy.  <br/> |
|SPO_GroupFileSynched  <br/> |Liczba plików zsynchronizowanych przez danego użytkownika w dowolnej witrynie grupy.  <br/> |
|SPO_GroupFileSharedInternally  <br/> |Liczba plików udostępnionych użytkownikom w organizacji lub użytkownikom w grupach (które mogą obejmować użytkowników zewnętrznych).  <br/> |
|SPO_GroupFileSharedExternally  <br/> |Liczba plików udostępnionych zewnętrznie przez danego użytkownika w dowolnej witrynie grupy.  <br/> |
|SPO_GroupAccessedByOwner  <br/> |Liczba witryn, z którymi użytkownik wchodził w interakcję, znajdujących się w należącej do nich witrynie grupy.  <br/> |
|SPO_GroupAccessedByOthers  <br/> |Liczba witryn, z którymi użytkownik wchodził w interakcję, znajdujących się w witrynie grupy, której właścicielem jest inny użytkownik.  <br/> |
|SPO_OtherFileViewedModified  <br/> |Liczba plików, na których dany użytkownik wykonywał działania w innej witrynie.  <br/> |
|SPO_OtherFileSynched  <br/> |Liczba plików zsynchronizowanych przez danego użytkownika z dowolnej witryny.  <br/> |
|SPO_OtherFileSharedInternally  <br/> |Liczba plików udostępnionych wewnętrznie przez tego użytkownika z dowolnej innej witryny lub użytkowników w grupach (które mogą obejmować użytkowników zewnętrznych). <br/> |
|SPO_OtherFileSharedExternally  <br/> |Liczba plików udostępnionych zewnętrznie z dowolnej witryny.  <br/> |
|SPO_OtherAccessedByOwner  <br/> |Liczba witryn, na których użytkownik wykonywał działania, znajdujących się w witrynie, której jest właścicielem.  <br/> |
|SPO_OtherAccessedByOthers  <br/> |Liczba witryn, na których użytkownik wykonywał działania, znajdujących się w witrynie, której właścicielem jest inny użytkownik.  <br/> |
|SPO_TeamFileViewedModified  <br/> |Liczba plików, na których użytkownik wykonywał działania w dowolnej witrynie zespołu.  <br/> |
|SPO_TeamFileSynched  <br/> |Liczba plików zsynchronizowanych przez danego użytkownika w dowolnej witrynie zespołu.  <br/> |
|SPO_TeamFileSharedInternally  <br/> |Liczba plików udostępnionych wewnętrznie przez tego użytkownika z dowolnej witryny zespołu lub użytkowników w grupach (które mogą obejmować użytkowników zewnętrznych).  <br/> |
|SPO_TeamFileSharedExternally  <br/> |Liczba plików udostępnionych zewnętrznie przez danego użytkownika w dowolnej witrynie zespołu.  <br/> |
|SPO_TeamAccessedByOwner  <br/> |Liczba witryn, z którymi użytkownik wchodził w interakcję, znajdujących się w witrynie zespołu, której jest właścicielem.  <br/> |
|SPO_TeamAccessedByOthers  <br/> |Liczba witryn, z którymi użytkownik wchodził w interakcję, znajdujących się w witrynie zespołu, której właścicielem jest inny użytkownik.  <br/> |
|Teams_ChatMessages  <br/> |Liczba wysłanych wiadomości czatu.  <br/> |
|Teams_ChannelMessage  <br/> |Liczba wiadomości opublikowanych w kanałach.  <br/> |
|Teams_CallParticipate  <br/> |Liczba połączeń, w których użytkownik uczestniczył.  <br/> |
|Teams_MeetingParticipate  <br/> |Liczba spotkań, do których użytkownik dołączył.  <br/> |
|Teams_HasOtherAction  <br/> |Wartość logiczna, jeśli użytkownik wykonał jakieś inne działania w usłudze Microsoft Teams.  <br/> |
|YAM_MessagePost  <br/> |Liczba Yammer komunikatów opublikowanych przez tego użytkownika.  <br/> |
|YAM_MessageLiked  <br/> |Liczba Yammer komunikatów, które podobały się temu użytkownikowi.  <br/> |
|YAM_MessageRead  <br/> |Liczba komunikatów Yammer odczytanych przez tego użytkownika.  <br/> |
|SFB_P2PSummary  <br/> |Liczba sesji równorzędnych, w których uczestniczył dany użytkownik.  <br/> |
|SFB_ConfOrgSummary  <br/> |Liczba sesji konferencji zorganizowanych przez tego użytkownika.  <br/> |
|SFB_ConfPartSummary  <br/> |Liczba sesji konferencji, w których uczestniczył dany użytkownik.  <br/> |

> [!NOTE]
> Teams_HasOtherAction oznacza, że użytkownik jest uważany za aktywnego, ale ma zero wartości dla wiadomości czatu, połączeń 1:1, komunikatów kanału, łącznej liczby spotkań i zorganizowanych spotkań.
   
### <a name="data-table---tenant-product-usage"></a>Tabela danych  Użycie produktu w dzierżawie

Ta tabela zawiera dane wdrażania z miesiąca na miesiąc w zakresie włączania, aktywnego, zwracania i po raz pierwszy użytkowników dla każdego produktu w ramach Microsoft 365. Wartości Microsoft 365 reprezentują aktywne użycie w każdym z produktów.
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|Product  <br/> |Nazwy produktów, dla których podsumowano informacje o użyciu. Microsoft 365 wartość w kolumnie produktu reprezentuje działanie w dowolnym produkcie  <br/> |
|Timeframe  <br/> |Wartość miesiąca. Jeden wiersz na produkt na miesiąc dla ostatnich 12 miesięcy z uwzględnieniem bieżącego, niepełnego miesiąca.  <br/> |
|EnabledUsers  <br/> |Liczba użytkowników włączonych do korzystania z produktu dla wartości przedziału czasowego, jeśli użytkownik został włączony przez część miesiąca, nadal są liczone.  <br/> |
|ActiveUsers  <br/> |Liczba użytkowników, którzy wykonali zamierzone działanie w produkcie dla wartości przedziału czasowego.  <br/> Użytkownik jest liczony jako aktywny dla produktu w danym miesiącu, jeśli wykonał jedno z kluczowych działań w danym produkcie. Kluczowe działania są dostępne w tabeli **Działania na produkcie w dzierżawie**.  <br/> |
|CumulativeActiveUsers  <br/> |Liczba użytkowników, którzy mogą korzystać z produktu i zrobili to co najmniej raz w okresie od rozpoczęcia zbierania danych w nowym systemie użycia do miesiąca określonego wartością Timeframe.  <br/> |
|MoMReturningUsers  <br/> |Liczba użytkowników, którzy są aktywni w miesiącu określonym wartością Timeframe, a także w poprzednim miesiącu.  <br/> |
|FirstTimeUsers  <br/> |Liczba użytkowników, którzy stali się aktywni po raz pierwszy w miesiącu określonym wartością Timeframe od czasu rozpoczęcia zbierania danych w nowym systemie użycia.  <br/> Użytkownik jest liczony jako nowy w danym miesiącu, jeśli jego aktywność została wykryta po raz pierwszy od momentu rozpoczęcia zbierania danych w nowym systemie raportowania. Po zliczeniu jako użytkownik po raz pierwszy, nawet jeśli ten użytkownik ma dużą lukę w swojej aktywności, nigdy nie będzie ponownie liczony jako użytkownik po raz pierwszy  <br/> |
|Content Date  <br/> |Jeśli wartość Timeframe pokazuje bieżący miesiąc, ta wartość będzie reprezentować ostatnią datę w tym miesiącu, dla której są dostępne dane.  <br/> Jeśli wartość Timeframe pokazuje poprzedni miesiąc, ta wartość będzie reprezentować ostatnią datę dla tego miesiąca.  <br/> |
   
### <a name="data-table---tenant-product-activity"></a>Tabela danych  Działania na produkcie w dzierżawie

Ta tabela zawiera miesięczne sumy aktywności i liczbę aktywnych użytkowników dla różnych działań w ramach produktów.
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|Timeframe  <br/> |Wartość miesiąca. Jeden wiersz na produkt na miesiąc dla ostatnich 12 miesięcy z uwzględnieniem bieżącego, niepełnego miesiąca.  <br/> |
|Product  <br/> |Nazwa produktu w Microsoft 365, dla którego są dostępne dane użycia.  <br/> |
|Activity  <br/> |Nazwa działania w produkcie, które jest używane do pokazania aktywnego użycia produktu.  <br/> |
|ActivityCount  <br/> |Jest to całkowita liczba działań obliczana dla każdej czynności wykonywanej w ramach produktu przez wszystkich aktywnych użytkowników.  <br/> **Uwaga:** w przypadku działań w usługach SharePoint Online i OneDrive dla Firm ta wartość oznacza liczbę odrębnych dokumentów, na których użytkownicy przeprowadzali interakcje.  <br/> |
|ActiveUserCount  <br/> |Liczba użytkowników, którzy wykonywali działania w obrębie produktu.  <br/> |
|TotalDurationInMinute  <br/> |Czas trwania w minutach liczony dla wszystkich aktywnych użytkowników, którzy korzystali z sesji audio lub wideo w ramach odpowiedniego działania w programie Skype dla firm.  <br/> |
|Content Date  <br/> |Jeśli wartość Timeframe pokazuje bieżący miesiąc, ta wartość będzie reprezentować ostatnią datę w tym miesiącu, dla której są dostępne dane.  <br/> Jeśli wartość Timeframe pokazuje poprzedni miesiąc, ta wartość będzie reprezentować ostatnią datę dla tego miesiąca.  <br/> |
   
### <a name="data-table---tenant-mailbox-usage"></a>Tabela danych  Użycie skrzynek pocztowych w dzierżawie

Ta tabela składa się z danych podsumowania dla wszystkich licencjonowanych Exchange Online użytkowników, którzy mają skrzynkę pocztową użytkownika. Zawiera ona stan na koniec miesiąca dla wszystkich skrzynek pocztowych użytkowników. Dane w tej tabeli nie są dodawane przez wiele miesięcy. Dane z ostatniego miesiąca w tej tabeli reprezentują najnowszy stan.
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|TotalMailboxes  <br/> |Liczba skrzynek pocztowych użytkownika dla subskrypcji Microsoft 365.  <br/> |
|IssueWarningQuota  <br/> |Całkowity limit przydziału dla ostrzeżenia dla wszystkich skrzynek pocztowych wszystkich użytkowników.  <br/> |
|ProhibitSendQuota  <br/> |Łączny limit przydziału dla zablokowania wysyłania dla wszystkich skrzynek pocztowych użytkowników.  <br/> |
|ProhibitSendReceiveQuota  <br/> |Łączny limit przydziału dla zablokowania wysyłania i odbierania dla wszystkich skrzynek pocztowych użytkowników.  <br/> |
|TotalItemBytes  <br/> |Ilość używanego miejsca do magazynowania (w bajtach) dla wszystkich skrzynek pocztowych użytkowników.  <br/> |
|Skrzynki pocztoweNoWarning  <br/> |Liczba skrzynek pocztowych użytkowników, dla których nie przekroczono limitu miejsca do magazynowania wywołującego ostrzeżenie.  <br/> |
|Skrzynki pocztoweIssueWarning  <br/> |Liczba skrzynek pocztowych użytkowników, dla których wyświetlono ostrzeżenie dotyczące przydziału miejsca do magazynowania.  <br/> |
|Skrzynki pocztoweExceedSendQuota  <br/> |Liczba skrzynek pocztowych użytkowników, dla których przekroczono przydział wysyłania.  <br/> |
|Skrzynki pocztoweExceedSendReceiveQuota  <br/> |Liczba skrzynek pocztowych użytkownika, które przekroczyły limit przydziału wysyłania/odbierania.  <br/> |
|Usunięte skrzynki pocztowe  <br/> |Liczba skrzynek pocztowych użytkowników, które zostały usunięte w określonym przedziale czasu.  <br/> |
|Timeframe  <br/> |Wartość miesiąca.  <br/> |
|Content Date  <br/> |Jeśli wartość Timeframe pokazuje bieżący miesiąc, ta wartość będzie reprezentować ostatnią datę w tym miesiącu, dla której są dostępne dane.  <br/> Jeśli wartość Timeframe pokazuje poprzedni miesiąc, ta wartość będzie reprezentować ostatnią datę dla tego miesiąca.  <br/> |
   
### <a name="data-table---tenant-client-usage"></a>Tabela danych  Użycie klientów w dzierżawie

Ta tabela zawiera dane podsumowania z miesiąca na miesiąc dotyczące klientów używanych przez użytkowników do nawiązywania połączenia z Exchange Online, Skype dla firm i Yammer. W tej tabeli nie ma jeszcze danych użycia klienta dla SharePoint Online i OneDrive dla Firm.
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|Product  <br/> |Nazwa produktu w Microsoft 365, dla którego są dostępne dane użycia klienta.  <br/> |
|Clientid  <br/> |Nazwa każdego urządzenia używanego do łączenia się z produktem.  <br/> |
|UserCount  <br/> |Liczba użytkowników, którzy skorzystali z każdego z klientów, dla każdego produktu.  <br/> |
|Timeframe  <br/> |Wartość miesiąca.  <br/> |
|Content Date  <br/> |Jeśli wartość Timeframe pokazuje bieżący miesiąc, ta wartość będzie reprezentować ostatnią datę w tym miesiącu, dla której są dostępne dane.  <br/> Jeśli wartość Timeframe pokazuje poprzedni miesiąc, ta wartość będzie reprezentować ostatnią datę dla tego miesiąca.  <br/> |
   
### <a name="data-table---tenant-sharepoint-online-usage"></a>Tabela danych  Użycie usługi SharePoint Online w dzierżawie

Ta tabela składa się z danych podsumowania dla poszczególnych miesięcy dotyczących użycia lub aktywności witryn usługi SharePoint Online. Te dane obejmują tylko witryny zespołów i witryny grup. Stan końca miesiąca witryny usługi SharePoint Online jest reprezentowany w tej kolumnie, na przykład jeśli użytkownik utworzył pięć dokumentów i użył 10 MB do całkowitego magazynu, a następnie usunął niektóre pliki i dodał więcej plików, aby na koniec miesiąca stan dla plików wynosi łącznie siedem, które używają pięciu MB magazynu,  wartość reprezentowana w tej tabeli to stan końca miesiąca. Ta tabela jest ukryta, co pozwala uniknąć podwójnego zliczania agregacji, i jest używana jako źródło w celu utworzenia dwóch tabel referencyjnych.
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|Typ witryny  <br/> |Wartość typu witryny (dowolna/zespołu/grupy) („dowolna" oznacza którykolwiek z tych 2 typów).  <br/> |
|TotalSites  <br/> |Liczba witryn, które istniały na koniec określonego przedziału czasu.  <br/> |
|DocumentCount  <br/> |Całkowita liczba dokumentów, które istniały w witrynie na koniec określonego przedziału czasu.  <br/> |
|Diplansed  <br/> |Całkowite użyte miejsce do magazynowania zsumowane dla wszystkich witryn na koniec określonego przedziału czasu.  <br/> |
|Activitytype  <br/> |Liczba witryn, w których zarejestrowano różnego typu działania na plikach (dowolne/aktywne pliki/pliki udostępnione ZEW/WEW /pliki zsynchronizowane).  <br/> Reprezentuje dowolne z wykonanych działań dotyczących plików.  <br/> |
|SitesWithOwnerActivities  <br/> |Liczba aktywnych witryn, w których właściciele witryn wykonali określone działanie na plikach w swoich witrynach. Właściciel witryny można pobrać z polecenia programu PowerShell **get-sposite**. Jest to osoba odpowiedzialna za witrynę.   <br/> |
|SitesWithNonOwnerActivities  <br/> |Liczba aktywnych witryn zsumowanych w danym miesiącu, w których użytkownicy inni niż właściciele witryn wykonali określone działanie na plikach w witrynach. Właściciel witryny można pobrać z polecenia programu PowerShell **get-sposite**. Jest to osoba odpowiedzialna za witrynę. <br/> |
|ActivityTotalSites  <br/> |Liczba witryn, w których zarejestrowano dowolne działanie w określonym przedziale czasowym. Jeśli w witrynie zarejestrowano działanie wcześniej w przedziale czasu, a następnie usunięto tę witrynę przed końcem przedziału czasu, to nadal zostanie ona uwzględniona w sumie aktywnych witryn dla danego przedziału czasu.  <br/> |
|Timeframe  <br/> |Ta kolumna zawiera wartości daty. Używana jako relacja jeden do wielu dla tabeli Kalendarz.  <br/> |
|Content Date  <br/> |Jeśli wartość Timeframe pokazuje bieżący miesiąc, ta wartość będzie reprezentować ostatnią datę w tym miesiącu, dla której są dostępne dane.  <br/> Jeśli wartość Timeframe pokazuje poprzedni miesiąc, ta wartość będzie reprezentować ostatnią datę dla tego miesiąca.  <br/> |
   
### <a name="data-table---tenant-onedrive-usage"></a>Tabela danych  Użycie usługi OneDrive w dzierżawie

Ta tabela zawiera dane dotyczące kont usługi OneDrive, takie jak liczba kont, liczba dokumentów na kontach usługi OneDrive, użyte miejsce do magazynowania i liczba plików według typu działania. W tej tabeli przedstawiono stan kont usługi OneDrive dla Firm na koniec miesiąca. Jeśli na przykład użytkownik utworzył pięć dokumentów, które używały 10 MB miejsca do magazynowania, a następnie usunął kilka i dodał więcej plików, aby na koniec miesiąca miał siedem plików korzystających z pięciu MB magazynu, wartość końca miesiąca jest reprezentowana w tej tabeli pod koniec miesiąca.
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|Typ witryny  <br/> |Wartość wynosi „OneDrive".  <br/> |
|TotalSites  <br/> |Liczba kont usługi OneDrive dla Firm, które istniały na końcu określonego przedziału czasu.  <br/> |
|DocumentCount  <br/> |Całkowita liczba dokumentów, które istniały na wszystkich kontach usługi OneDrive dla Firm na koniec określonego przedziału czasu.  <br/> |
|Diplansed  <br/> |Łączna ilość używanego magazynu zsumowana na całym koncie OneDrive na końcu przedziału czasu.  <br/> |
|Activitytype  <br/> |Liczba kont, dla których zarejestrowano różnego typu działania na plikach (dowolne/aktywne pliki/pliki udostępnione ZEW/WEW /pliki zsynchronizowane).  <br/> Typ dowolny oznacza, że wykonano dowolne działanie na pliku.  <br/> |
|SitesWithOwnerActivities  <br/> |Liczba aktywnych kont usługi OneDrive dla Firm, na których właściciele kont wykonali określone działanie na plikach na własnych kontach.  <br/> |
|SitesWithNonOwnerActivities  <br/> |Liczba kont usługi OneDrive dla Firm, na których działanie na plikach zostało wykonane przez użytkowników innych niż właściciel konta.  <br/> |
|ActivityTotalSites  <br/> |Liczba kont usługi OneDrive dla Firm, na których zarejestrowano dowolne działanie na pliku podczas określonego przedziału czasu. Jeśli na koncie usługi OneDrive dla Firm zarejestrowano działanie wcześniej w przedziale czasu, a następnie usunięto to konto przed końcem przedziału czasu, to nadal zostanie ono uwzględniona w sumie aktywnych kont usługi OneDrive dla Firm dla danego przedziału czasu.  <br/> |
|Timeframe  <br/> |Ta kolumna zawiera wartości daty. Używana jako relacja jeden do wielu dla tabeli Kalendarz.  <br/> |
|Content Date  <br/> |Jeśli wartość Timeframe pokazuje bieżący miesiąc, ta wartość będzie reprezentować ostatnią datę w tym miesiącu, dla której są dostępne dane.  <br/> Jeśli wartość Timeframe pokazuje poprzedni miesiąc, ta wartość będzie reprezentować ostatnią datę dla tego miesiąca.  <br/> |
   
### <a name="data-table---tenant-microsoft-365-groups-usage"></a>Tabela danych — użycie Grupy Microsoft 365 dzierżawy

Ta tabela zawiera dane dotyczące sposobu użycia Grupy Microsoft 365 w całej organizacji.
  
****

|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|Ramach czasowych  <br/> |Wartość miesiąca. Jeden wiersz na produkt na miesiąc dla ostatnich 12 miesięcy z uwzględnieniem bieżącego, niepełnego miesiąca.  <br/> |
|Grouptype  <br/> |Typ grupy (prywatna/publiczna/dowolna).  <br/> |
|TotalGroups  <br/> |Liczba grup dla każdego typu grupy.  <br/> |
|ActiveGroups  <br/> |Liczba aktywnych grup.  <br/> |
|MBX_TotalGroups  <br/> |Liczba grup ze skrzynką pocztową.  <br/> |
|MBX_ActiveGroups  <br/> |Liczba aktywnych grup ze skrzynką pocztową.  <br/> |
|MBX_TotalActivities  <br/> |Liczba działań dotyczących skrzynki pocztowej.  <br/> |
|MBX_TotalItems  <br/> |Liczba elementów skrzynki pocztowej.  <br/> |
|MBX_StorageUsed  <br/> |Ilość miejsca użytego w skrzynce pocztowej.  <br/> |
|SPO_TotalGroups  <br/> |Liczba grup programu SharePoint.  <br/> |
|SPO_ActiveGroups  <br/> |Liczba aktywnych grup programu SharePoint.  <br/> |
|SPO_FileAccessedActiveGroups  <br/> |Liczba grup SharePoint, które mają dostęp do plików.  <br/> |
|SPO_FileSyncedActiveGroups  <br/> |Liczba grup SharePoint, które mają działania synchronizowane z plikami.  <br/> |
|SPO_FileSharedInternallyActiveGroups  <br/> |Liczba grup SharePoint, które mają działania udostępnione wewnętrznie lub grupom (które mogą obejmować użytkowników zewnętrznych).  <br/> |
|SPO_FileSharedExternallyActiveGroups  <br/> |Liczba grup programu SharePoint z działaniami zewnętrznego udostępniania.  <br/> |
|SPO_TotalActivities  <br/> |Liczba działań programu SharePoint.  <br/> |
|SPO_FileAccessedActivities  <br/> |Liczba działań dostępu do plików programu SharePoint.  <br/> |
|SPO_FileSyncedActivities  <br/> |Liczba działań synchronizacji plików programu SharePoint.  <br/> |
|SPO_FileSharedInternallyActivities  <br/> |Liczba SharePoint działań udostępnionych plików wewnętrznie lub grup (które mogą obejmować elementy członkowskie zewnętrzne).  <br/> |
|SPO_FileSharedExternallyActivities  <br/> |Liczba działań zewnętrznego udostępniania plików programu SharePoint.  <br/> |
|SPO_TotalFiles  <br/> |Liczba plików programu SharePoint.  <br/> |
|SPO_ActiveFiles  <br/> |Liczba aktywnych plików programu SharePoint.  <br/> |
|SPO_StorageUsed  <br/> |Ilość miejsca do magazynowania użytego w programie SharePoint.  <br/> |
|YAM_TotalGroups  <br/> |Liczba grup usługi Yammer.  <br/> |
|YAM_ActiveGroups  <br/> |Liczba aktywnych grup usługi Yammer.  <br/> |
|YAM_LikedActiveGroups  <br/> |Liczba grup usługi Yammer z działaniami polubienia.  <br/> |
|YAM_PostedActiveGroups  <br/> |Liczba grup usługi Yammer z działaniami opublikowania.  <br/> |
|YAM_ReadActiveGroups  <br/> |Liczba grup usługi Yammer z działaniami przeczytania.  <br/> |
|YAM_TotalActivities  <br/> |Liczba działań usługi Yammer.  <br/> |
|YAM_LikedActivities  <br/> |Liczba działań polubienia w usłudze Yammer.  <br/> |
|YAM_PostedActivties  <br/> |Liczba działań opublikowania w usłudze Yammer.  <br/> |
|YAM_ReadActivites  <br/> |Liczba działań przeczytania w usłudze Yammer.  <br/> |

### <a name="data-table---tenant-office-licenses"></a>Tabela danych — licencje Office dzierżawy

Ta tabela zawiera dane podsumowania z miesiąca na miesiąc dotyczące przypisania licencji dla użytkowników. 
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|LicenseName  <br/> |Nazwa licencji.  <br/> |
|AssignedCount  <br/> |Liczba przypisanych licencji.  <br/> |
|Timeframe  <br/> |Wartość miesiąca.  <br/> |

### <a name="data-table---tenant-office-activation"></a>Tabela danych  Aktywacje pakietu Office w dzierżawie

Tabela zawiera dane dotyczące liczby Office aktywacji subskrypcji w planach usług, na przykład Aplikacje Microsoft 365 dla przedsiębiorstw, Visio, Project. Udostępnia również dane dotyczące liczby aktywacji na urządzenie (Android/iOS/Mac/PC).
  
|**Nazwa kolumny**|**Opis kolumny**|
|:-----|:-----|
|ServicePlanName  <br/> |Lista wartości nazwy planu usługi i liczb aktywacji według urządzeń, jak przedstawiono w poniższych kolumnach.  <br/> |
|TotalEnabled  <br/> |Liczba włączonych użytkowników według nazwy planu usługi do końca określonego przedziału czasu.  <br/> |
|TotalActivatedUsers  <br/> |Liczba użytkowników, którzy aktywowali poszczególne plany usługi do końca określonego przedziału czasu.  <br/> |
|AndroidCount  <br/> |Liczba aktywacji według planu usługi dla urządzeń z systemem Android do końca określonego przedziału czasu.  <br/> |
|iOSCount  <br/> |Liczba aktywacji według planu usługi dla urządzeń z systemem iOS do końca określonego przedziału czasu.  <br/> |
|MacCount  <br/> |Liczba aktywacji według planu usługi dla komputerów Mac do końca określonego przedziału czasu.  <br/> |
|PcCount  <br/> |Liczba aktywacji według planu usługi dla komputerów PC do końca określonego przedziału czasu.  <br/> |
|WinRtCount  <br/> |Liczba aktywacji według planu usługi dla urządzeń z systemem Windows Mobile do końca określonego przedziału czasu.  <br/> |
|Timeframe  <br/> |Ta kolumna zawiera wartości daty. Używana jako relacja jeden do wielu dla tabeli Kalendarz.  <br/> |
|Content Date  <br/> |Jeśli wartość Timeframe pokazuje bieżący miesiąc, ta wartość będzie reprezentować ostatnią datę w tym miesiącu, dla której są dostępne dane.  <br/> Jeśli wartość Timeframe pokazuje poprzedni miesiąc, ta wartość będzie reprezentować ostatnią datę dla tego miesiąca.  <br/> |
