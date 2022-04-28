---
title: PerformancePoint Server 2007 r. plan zakończenia wsparcia
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
f1.keywords:
- NOCSH
description: PerformancePoint Server 2007, ProClarity i SharePoint Server 2007 osiągnęły koniec wsparcia. Przeczytaj ten artykuł, aby ułatwić planowanie uaktualnienia rozwiązania analizy biznesowej.
ms.openlocfilehash: 381faab617828d3bb30106deaaae993ed8d2b786
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096353"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>PerformancePoint Server 2007 r. plan zakończenia wsparcia

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Office serwery i aplikacje z 2007 r. osiągnęły koniec wsparcia, w tym serwery i aplikacje, których możesz używać w ramach rozwiązań analizy biznesowej. W poniższej tabeli wymieniono aplikacje analizy biznesowej, których dotyczy problem:
  
|**Aplikacje usługi Microsoft BI**|**Data zakończenia pomocy technicznej**|
|:-----|:-----|
|ProClarity Analytics Server 6.3 z dodatkiem Service Pack 3  <br/> ProClarity Desktop Professional 6.3  <br/> ProClarity SharePoint Viewer 6.3  <br/> |wtorek, 11 lipca 2017 r.  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |10 października 2017 r.  <br/> |
|PerformancePoint Server 2007 Service Pack 3  <br/> |wtorek, 9 stycznia 2018 r.  <br/> |
   
Aby uzyskać więcej informacji, zobacz [Zasoby ułatwiające uaktualnienie z serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Co oznacza *koniec wsparcia* ?

Podobnie jak większość produktów firmy Microsoft, PerformancePoint Server 2007 z dodatkiem SP3, oprogramowanie ProClarity i SharePoint Server 2007 z dodatkiem SP3, mają cykl życia pomocy technicznej, podczas którego firma Microsoft udostępnia nowe funkcje, poprawki usterek i aktualizacje zabezpieczeń. Cykl życia produktu zazwyczaj trwa 10 lat od początkowego wydania produktu. Koniec tego cyklu życia jest znany jako koniec wsparcia dla produktu. Ponieważ program ProClarity, PerformancePoint Server i SharePoint Server 2007 osiągnęły koniec wsparcia, firma Microsoft nie zapewnia już:
  
- Pomoc techniczna dotycząca problemów, które mogą wystąpić.
    
- Poprawki błędów w przypadku wykrytych problemów, które mogą mieć wpływ na stabilność i użyteczność serwerów.
    
- Poprawki zabezpieczeń wykrytych luk w zabezpieczeniach, które mogą narazić serwery lub aplikacje na naruszenia zabezpieczeń.
    
- Aktualizacje stref czasowych.
    
Instalacja programu ProClarity, SharePoint Server 2007 SP3 i PerformancePoint Server 2007 z dodatkiem SP3 będzie nadal działać, mimo że obsługa została zakończona. Jednak zdecydowanie zalecamy jak najszybszą migrację z tych aplikacji.
  
## <a name="what-are-my-options"></a>Jakie są moje opcje?

Od 2007 r. w aplikacjach usługi Microsoft BI wprowadzono wiele zmian i masz kilka opcji do rozważenia, jak podsumowano w poniższej tabeli.
  
|**Jeśli używasz tego ...**|**Zapoznaj się z tymi opcjami...**|**I pamiętaj o tym ...**|
|:-----|:-----|:-----|
| monitorowanie PerformancePoint Server 2007 r.&amp; Możliwości analizy, w tym:<br/>— Serwer monitorowania programu PerformancePoint <br/>— Projektant pulpitu nawigacyjnego programu PerformancePoint<br/>— Podgląd pulpitu nawigacyjnego dla SharePoint Services (używany do renderowania pulpitów nawigacyjnych programu PerformancePoint, kart wyników i raportów)<br/> |**Excel z Excel w przeglądarce** (w chmurze lub lokalnie). Aby zapoznać się z omówieniem, zobacz [Możliwości analizy biznesowej w Excel i Microsoft 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx).<br/><br/> **Power BI** (w chmurze lub lokalnie). Aby zapoznać się z omówieniem, zobacz [Co to jest Power BI?](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Server Reporting Services** (lokalnie). Aby zapoznać się z omówieniem, zobacz [SQL Server Reporting Services (SSRS): Tworzenie, wdrażanie i zarządzanie raportami mobilnymi i podzielonymi na strony](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports). <br/><br/> **Usługi programu PerformancePoint** (lokalnie). Aby zapoznać się z omówieniem, zobacz [Co nowego w Usługi programu PerformancePoint (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14)). <br/> |Excel jest dostępna jako rozwiązanie online (oparte na chmurze) lub lokalne. Wiele potrzeb dotyczących raportowania i pulpitu nawigacyjnego można spełnić w Excel.  <br/><br/> Power BI jest dostępna jako rozwiązanie online lub lokalne. Power BI nie jest uwzględniona w Microsoft 365. Ale możesz zacząć korzystać z Power BI za darmo. Później, w zależności od użycia danych i potrzeb biznesowych, możesz przeprowadzić uaktualnienie do Power BI Pro przy użyciu Microsoft 365 E5.<br/> <br/> Usługi Reporting Services i Usługi programu PerformancePoint są rozwiązaniami lokalnymi. <br/><br/> Usługi programu PerformancePoint jest dostępna w SharePoint Server 2010, SharePoint Server 2013 i SharePoint Server 2016. <br/> <br/> Niektóre funkcje i typy raportów, które były dostępne w PerformancePoint Server 2007 r., nie są dostępne w Excel, Power BI, usługach Reporting Services lub Usługi programu PerformancePoint. Przejrzyj dostępne funkcje, aby określić najlepsze rozwiązanie dla Twoich potrzeb biznesowych. <br/> |
| Oprogramowanie ProClarity, w tym:<br/>- ProClarity Desktop Professional<br/> — Serwer usługi ProClarity Analytics<br/>- ProClarity SharePoint Viewer<br/> |**Skontaktuj się z partnerem firmy Microsoft,** aby zidentyfikować rozwiązanie, które najlepiej spełnia Twoje potrzeby. Odwiedź [Centrum partnerskie firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249). <br/><br/> Możesz również rozważyć użycie Excel z Excel w przeglądarce, Power BI, SQL Server Reporting Services lub Usługi programu PerformancePoint.  <br/> |Kilka, ale nie wszystkie funkcje oprogramowania ProClarity są dostępne w innych ofertach firmy Microsoft, w tym Excel, Power BI, Reporting Services i Usługi programu PerformancePoint.  <br/> |
|wskaźniki KPI serwera SharePoint Server 2007 (nazywane również wskaźnikami KPI moss)  <br/> |**Excel z Usługi programu Excel**. Aby zapoznać się z omówieniem, zobacz [Business intelligence in Excel and Usługi programu Excel (SharePoint Server 2013) (Analiza biznesowa w Excel i Usługi programu Excel (SharePoint Server 2013).](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx). <br/> |Kluczowe wskaźniki wydajności moss utworzone przy użyciu programu SharePoint Server 2007 mogą być używane w systemach SharePoint Server 2010, SharePoint Server 2013 i SharePoint Server 2016. Nie można jednak tworzyć nowych wskaźników KPI moss.  <br/> |
|Excel 2007 r.  <br/> |**Excel** (w chmurze lub lokalnie). Aby zapoznać się z omówieniem, zobacz [Możliwości analizy biznesowej w Excel i Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx). <br/><br/> **Power BI** (w chmurze lub lokalnie). Aby zapoznać się z omówieniem, zobacz [Co to jest Power BI?](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |Zarówno Excel, jak i Power BI oferują organizacji rozwiązania oparte na chmurze i lokalne, z obsługą wielu różnych źródeł danych.  <br/> |
   
### <a name="help-selecting-a-solution"></a>Pomoc dotycząca wybierania rozwiązania

Przy tak wielu dostępnych opcjach analizy biznesowej może wydawać się przytłaczające określenie, która opcja jest najlepsza. Mamy dostępny przewodnik online, aby pomóc. Zobacz [Wybieranie narzędzi analizy biznesowej firmy Microsoft do analizy i raportowania](/sql/reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting).
  
### <a name="what-if-i-dont-upgrade-now"></a>Co zrobić, jeśli nie uaktualniam teraz?

Możesz wybrać, aby nie uaktualniać natychmiast. Istniejące serwery i aplikacje będą nadal działać. Nie otrzymasz jednak żadnych dalszych aktualizacji, w tym aktualizacji zabezpieczeń, ponieważ pomoc techniczna została zakończona. A jeśli coś pójdzie nie tak z aplikacjami serwera, nie będziesz w stanie uzyskać pomocy technicznej firmy Microsoft.
  
## <a name="how-do-i-plan-my-upgrade"></a>Jak mogę zaplanować uaktualnienie?

Po zapoznaniu się z opcjami uaktualniania następnym krokiem jest przygotowanie planu uaktualnienia. Poniższe sekcje zawierają informacje i dodatkowe zasoby, które pomogą. Masz cztery główne opcje, w tym dwie, które działają zarówno w chmurze, jak i lokalnie, oraz dwie, które są tylko lokalne:
  
|**Opcja**|**W chmurze czy lokalnie?**|
|:-----|:-----|
|[Excel z serwerem SharePoint (lokalnie)](#excel-with-sharepoint-server-on-premises) <br/> |Zarówno  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or-on-premises)<br/> |Zarówno  <br/> |
|[Reporting Services](#use-reporting-services-on-premises) <br/> |Tylko lokalnie  <br/> |
|[Usługi programu PerformancePoint](#use-performancepoint-services-on-premises) <br/> |Tylko lokalnie  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>Używanie Excel (w chmurze lub lokalnie)

Za pomocą Excel, który jest również znany jako *Usługi programu Excel* w SharePoint Server, można wyświetlać i używać skoroszytów w oknie przeglądarki, nawet jeśli Excel nie jest zainstalowany na komputerze. Za pomocą Excel można tworzyć raporty, karty wyników i pulpity nawigacyjne. Następnie udostępnij skoroszyty innym osobom, które mogą używać Excel w przeglądarce, niezależnie od tego, czy korzystają z usługi SharePoint Online w ramach lokalnego serwera Microsoft 365 czy SharePoint Server. Możesz użyć danych przechowywanych lokalnie lub w chmurze, co umożliwia korzystanie z wielu różnych źródeł danych.
  
W poniższej tabeli porównaliśmy kluczowe zalety używania Excel z Microsoft 365 do używania Excel z serwerem SharePoint. Poniżej przedstawiono więcej informacji.
  
|**Excel z Microsoft 365 (w chmurze)**|**Excel z serwerem SharePoint (lokalnie)**|
|:-----|:-----|
|**Otrzymujesz najnowszą, największą wersję Excel**. Dzięki Microsoft 365 otrzymujesz najnowszą wersję Excel, która obejmuje zaawansowane nowe typy wykresów, możliwość szybkiego i łatwego tworzenia wykresów i tabel oraz obsługę większej liczby źródeł danych. <br/> <br/> **Konfiguracja jest znacznie prostsza**. Excel jest dołączony do Microsoft 365 dla firm, więc nie ma ciężkich podnoszenia z Twojej strony. Zarejestruj się i zaloguj się, a będziesz działać szybciej i wydajniej niż w przypadku uaktualniania serwerów lokalnych. <br/> <br/> **Użytkownicy mają wszędzie dostęp do swoich skoroszytów**. Użytkownicy mogą bezpiecznie wyświetlać skoroszyty z dowolnego miejsca, korzystając z komputera, smartfona i tabletu. <br/> <br/> **To nie tylko!** Zobacz [Możliwości analizy biznesowej w Excel i Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx). <br/> |**Zarządzasz ustawieniami globalnymi**. Jako administrator SharePoint możesz określić ustawienia globalne, takie jak zabezpieczenia, równoważenie obciążenia, zarządzanie sesjami, buforowanie skoroszytu i połączenia danych zewnętrznych. <br/> <br/> **Możesz użyć Usługi programu Excel z Usługi programu PerformancePoint**. W ramach instalacji programu SharePoint Server można skonfigurować Usługi programu Excel i Usługi programu PerformancePoint oraz uwzględnić raporty Usługi programu Excel w pulpitach nawigacyjnych programu PerformancePoint. <br/> <br/> **To nie tylko!** Zobacz [Business intelligence in Excel and Usługi programu Excel (SharePoint Server 2013) (Analiza biznesowa w Excel i Usługi programu Excel (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx). <br/> |
   
#### <a name="excel-with-microsoft-365-in-the-cloud"></a>Excel z Microsoft 365 (w chmurze)

Jeśli przejdziesz do Microsoft 365, będziesz mieć najbardziej aktualne usługi i aplikacje, w tym Excel 2016. Usługi programu PerformancePoint nie jest dostępna w Microsoft 365, więc zastąpisz zawartość pulpitu nawigacyjnego programu PerformancePoint Excel skoroszytami lub innymi raportami. Dobrą wiadomością jest to, że Excel 2016 ma wiele nowych typów wykresów i łatwiej niż kiedykolwiek wcześniej tworzyć imponujące pulpity nawigacyjne w Excel. Nowe funkcje są dodawane regularnie. Aby dowiedzieć się więcej, zobacz [What's New in Excel 2016 for Windows (Co nowego w Excel 2016 dla Windows](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx)).
  
Ponadto jeśli kupisz 50 lub więcej miejsc Microsoft 365, zespół Microsoft FastTrack może ci pomóc w skonfigurowaniu. Aby dowiedzieć się więcej, odwiedź [stronę FastTrack](https://www.microsoft.com/fasttrack/microsoft-365).
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel z serwerem SharePoint (lokalnie)

W przypadku uaktualnienia do nowszej wersji SharePoint można użyć Excel z Usługi programu Excel lub w przeglądarce w następujący sposób:
  
- Usługi programu Excel w programie SharePoint Server 2010
    
- Usługi programu Excel na serwerze SharePoint Server 2013
    
- Excel, która jest częścią Office Online Server, zainstalowana oddzielnie od SharePoint Server 2016
    
Możesz również skonfigurować Usługi programu PerformancePoint w nowej wersji serwera SharePoint Server i użyć go razem z Excel.
  
Aby dowiedzieć się więcej na temat opcji uaktualniania SharePoint, zobacz [plan zakończenia pomocy technicznej programu SharePoint Server 2007](sharepoint-2007-end-of-support.md).
  
Aby dowiedzieć się więcej o Usługi programu Excel, zobacz [omówienie Usługi programu Excel (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee424405(v=office.14)).
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>Korzystanie z Power BI (w chmurze lub lokalnie)

Power BI to zestaw narzędzi do analizy biznesowej do analizowania danych i udostępniania szczegółowych informacji. Dzięki Power BI możesz tworzyć interaktywne raporty i pulpity nawigacyjne za pomocą lokalnych lub online źródeł danych. Użytkownicy mogą wyświetlać raporty i pulpity nawigacyjne oraz korzystać z nich na swoich komputerach lub urządzeniach przenośnych.
  
Power BI nie należy do Microsoft 365 ani serwera SharePoint. Jest to oddzielna oferta obejmująca Power BI Desktop, bramy Power BI i usługa Power BI. Power BI integruje się również z usługą SharePoint Online. Możesz rozpocząć pracę z Power BI bezpłatnie. Na podstawie użycia danych i potrzeb biznesowych możesz później przeprowadzić uaktualnienie do Power BI Pro przy użyciu Microsoft 365 E5. Aby dowiedzieć się więcej, zobacz [Co to jest Power BI?](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>Korzystanie z usług Reporting Services (lokalnie)

SQL Server Reporting Services zapewnia niezawodne rozwiązanie do raportowania. Usługi Reporting Services można skonfigurować w trybie natywnym lub w trybie zintegrowanym SharePoint. Możesz użyć kilku różnych narzędzi do tworzenia raportów, w tym Projektant raportów, Report Builder i Power View. W najnowszej wersji SQL Server możesz również użyć SQL Server Mobile Report Publisher, aby dostarczać raporty skalowane do dowolnego rozmiaru ekranu. Dzięki temu użytkownicy mogą korzystać z raportów na swoich urządzeniach przenośnych. Aby dowiedzieć się więcej, zobacz [SQL Server Reporting Services (SSRS): Tworzenie i wdrażanie raportów mobilnych i raportów podzielonych na strony oraz zarządzanie nimi](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports).
  
### <a name="use-performancepoint-services-on-premises"></a>Korzystanie z Usługi programu PerformancePoint (lokalnie)

PerformancePoint Server 2007 roku został sprzedany oddzielnie od SharePoint Server 2007. Począwszy od SharePoint Server 2010, Usługi programu PerformancePoint jest aplikacją usługi w programie SharePoint Server. Dlatego nie musisz kupować oddzielnych licencji serwera ani sprzętu, aby korzystać z Usługi programu PerformancePoint.
  
Aby przejść z PerformancePoint Server 2007 r. do Usługi programu PerformancePoint, przejdź do nowszej wersji serwera SharePoint Server i skonfiguruj Usługi programu PerformancePoint. Wersja przeniesionego serwera SharePoint określa, czy można zaimportować istniejącą zawartość pulpitu nawigacyjnego z PerformancePoint Server 2007 r. do Usługi programu PerformancePoint.
  
- W przypadku uaktualnienia do programu SharePoint Server 2010 możesz zaimportować zawartość pulpitu nawigacyjnego programu PerformancePoint z PerformancePoint Server 2007 r. do Usługi programu PerformancePoint w programie SharePoint Server 2010. Aby dowiedzieć się więcej, zobacz [Import Wizard: PerformancePoint Server 2007 content to SharePoint Server 2010 (Kreator importowania: zawartość PerformancePoint Server 2007 do serwera SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/ee681485(v=office.14))).
    
- Jeśli przejdziesz na serwer SharePoint Server 2013 lub SharePoint Server 2016, najprawdopodobniej musisz utworzyć nową zawartość pulpitu nawigacyjnego (źródła danych, raporty, karty wyników i strony pulpitu nawigacyjnego).
    
Aby rozpocząć pracę z planem uaktualniania Usługi programu PerformancePoint, zobacz następujące zasoby:
  
- [SharePoint Server 2007 — plan pomocy technicznej](sharepoint-2007-end-of-support.md)
    
- Jeśli wiesz, do której wersji SharePoint się przenosisz, zobacz odpowiedni artykuł dotyczący Usługi programu PerformancePoint:
    
  - [Planowanie Usługi programu PerformancePoint (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee681486(v=office.14))
    
  - [Usługi programu PerformancePoint w programie SharePoint Server 2013 — omówienie](/sharepoint/administration/performancepoint-services-overview)
    
  - [Usługi programu PerformancePoint w programie SharePoint Server 2016 — omówienie](/sharepoint/administration/performancepoint-services-overview)
    
Po uaktualnieniu do Usługi programu PerformancePoint otrzymujesz kilka nowych funkcji i ulepszeń. Usługi programu PerformancePoint oferuje ulepszone karty wyników; nowe wizualizacje, takie jak raport Drzewo dekompozycji i Szczegóły kluczowego wskaźnika wydajności; więcej typów wykresów, lepsze możliwości filtrowania analizy czasowej i ulepszona zgodność ułatwień dostępu. Aby dowiedzieć się więcej, zobacz [Co nowego w Usługi programu PerformancePoint (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14)).
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>Gdzie mogę uzyskać pomoc dotyczącą uaktualnienia?

Niezależnie od tego, czy uaktualniasz środowisko lokalne, czy przechodzisz do Microsoft 365, zalecamy współpracę z partnerem firmy Microsoft. Wykwalifikowany partner może pomóc w określeniu rozwiązania, które najlepiej spełnia Twoje potrzeby biznesowe i pomaga w wdrożeniu. Odwiedź [Centrum partnerskie firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) i użyj filtrów wyszukiwania, aby znaleźć dostawcę rozwiązań.
  
## <a name="related-topics"></a>Tematy pokrewne

[Zasoby ułatwiające uaktualnienie z serwerów i klientów Office 2007](upgrade-from-office-2007-servers-and-products.md)