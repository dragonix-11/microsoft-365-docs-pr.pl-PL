---
title: PerformancePoint Server 2007 r. przewodnik po zakończeniu pomocy technicznej
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: PerformancePoint Server 2007, ProClarity i SharePoint Server 2007 zakończyły wsparcie techniczne. Przeczytaj ten artykuł, aby ułatwić zaplanowanie uaktualnienia rozwiązania do usługi bi.
ms.openlocfilehash: f4e0662109cc5bdbdfbf922086715a0de4d91c37
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983797"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>PerformancePoint Server 2007 r. przewodnik po zakończeniu pomocy technicznej

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Office 2007 serwery i aplikacje zakończyły wsparcie techniczne, w tym serwery i aplikacje, z których być może korzystasz w ramach rozwiązań analizy biznesowej. W poniższej tabeli wymieniono aplikacje usługi bi, których to dotyczy:
  
|**Aplikacje usługi Microsoft BI**|**Data zakończenia pomocy technicznej**|
|:-----|:-----|
|ProClarity Analytics Server 6.3 z dodatkiem Service Pack 3  <br/> ProClarity Desktop Professional 6.3  <br/> ProClarity SharePoint Viewer 6.3  <br/> |11 lipca 2017 r.  <br/> |
|SharePoint Server 2007 z dodatkiem Service Pack 3  <br/> |10 października 2017 r.  <br/> |
|PerformancePoint Server 2007 z dodatkiem Service Pack 3  <br/> |9 stycznia 2018 r.  <br/> |
   
Aby uzyskać więcej informacji, zobacz Zasoby pomocne przy uaktualnieniu z Office i klientów programu [Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Co oznacza *zakończenie obsługi* ?

Jak większość produktów firmy Microsoft, program PerformancePoint Server 2007 z dodatkiem SP3, oprogramowanie ProClarity i program SharePoint Server 2007 z dodatkiem SP3, mają cykl pomocy technicznej, w trakcie którego firma Microsoft udostępnia nowe funkcje, poprawki i aktualizacje zabezpieczeń. Cykl życia produktu zazwyczaj trwa 10 lat od początkowego wydania produktu. Koniec tego cyklu życia znany jest jako koniec wsparcia technicznego produktu. Po zakończeniu obsługi programu ProClarity, PerformancePoint Server i SharePoint Server 2007 firma Microsoft nie zapewnia już:
  
- pomoc techniczną w zakresie mogącego wystąpić problemów;
    
- Poprawki błędów dotyczące wykrytych problemów, które mogą mieć wpływ na stabilność i użyteczność serwerów.
    
- Poprawki zabezpieczeń dotyczące wykrytych luk, które mogą na narażenie serwerów lub aplikacji na naruszenie bezpieczeństwa.
    
- Aktualizacje stref czasowych.
    
Instalacje proClarity, SharePoint Server 2007 z dodatkiem SP3 i PerformancePoint Server 2007 z dodatkiem SP3 będą nadal działać, nawet jeśli pomoc techniczna została zakończona. Zdecydowanie jednak zalecamy możliwie jak najszybciej migrację z tych aplikacji.
  
## <a name="what-are-my-options"></a>Jakie są moje opcje?

Od 2007 r. w aplikacjach usługi Microsoft BI w aplikacjach do obsługi biznesowych zaszły liczne zmiany, a do rozważenia jest kilka opcji, które można podsumować w poniższej tabeli.
  
|**Jeśli używasz tego urządzenia...**|**Zapoznaj się z tymi opcjami...**|**I miej to na uwadze...**|
|:-----|:-----|:-----|
| PerformancePoint Server 2007 &amp; Funkcje analizy, w tym:<br/>- Serwer monitorowania programu PerformancePoint <br/>- Projektant pulpitu nawigacyjnego programu PerformancePoint<br/>- Podgląd pulpitu nawigacyjnego dla SharePoint Services (używany do renderowania pulpitów nawigacyjnych, kart wyników i raportów programu PerformancePoint)<br/> |**Excel pomocą Excel w przeglądarce** (w chmurze lub lokalnie). Aby uzyskać omówienie, zobacz [Funkcje usługi bi w Excel i Microsoft 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx).<br/><br/> **Power BI** (w chmurze lub lokalnie). Aby uzyskać omówienie, [zobacz Co to jest Power BI?](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Server Reporting Services** (lokalnie). Aby uzyskać omówienie, zobacz [SQL Server Reporting Services (SSRS): Tworzenie i wdrażanie](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports) raportów mobilnych i podzielonych na strony oraz zarządzanie nimi. <br/><br/> **Usługi programu PerformancePoint** (lokalnie). Aby uzyskać omówienie, zobacz [Co nowego w programie Usługi programu PerformancePoint (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14)). <br/> |Excel jest dostępna jako rozwiązanie online (chmurowe) lub lokalne. Wiele potrzeb w zakresie raportowania i pulpitu nawigacyjnego można spełnić Excel.  <br/><br/> Power BI jest dostępna jako rozwiązanie lokalne lub online. Power BI nie jest uwzględniane w Microsoft 365. Możesz jednak zacząć bezpłatnie Power BI aplikacji. Później, w zależności od użycia danych i potrzeb biznesowych, możesz uaktualnić usługę do Power BI Pro z Microsoft 365 E5.<br/> <br/> Usługi Reporting Services Usługi programu PerformancePoint są rozwiązaniami lokalnymi. <br/><br/> Usługi programu PerformancePoint jest dostępna w SharePoint Server 2010, SharePoint Server 2013 i SharePoint Server 2016. <br/> <br/> Niektóre funkcje i typy raportów, które były dostępne w programie PerformancePoint Server 2007, nie są dostępne w programach Excel, Power BI, Reporting Services i Usługi programu PerformancePoint. Przejrzyj dostępne funkcje, aby ustalić najlepsze rozwiązanie do twoich potrzeb biznesowych. <br/> |
| Oprogramowanie ProClarity, w tym:<br/>- ProClarity Desktop Professional<br/> - ProClarity Analytics Server<br/>- ProClarity SharePoint Viewer<br/> |**We współpracy z partnerem firmy Microsoft** określ rozwiązanie najlepiej spełniające Twoje potrzeby. Odwiedź [Centrum partnerów firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249). <br/><br/> Możesz także rozważyć używanie aplikacji Excel z Excel przeglądarki, aplikacji Power BI, SQL Server Reporting Services lub Usługi programu PerformancePoint.  <br/> |Kilka, ale nie wszystkie funkcje oprogramowania ProClarity są dostępne w innych ofertach firmy Microsoft, w tym Excel, Power BI, Reporting Services i Usługi programu PerformancePoint.  <br/> |
|SharePoint KPI programu SharePoint Server 2007 (zwanych także wskaźnikami KPI programu MOSS)  <br/> |**Excel z Usługi programu Excel**. Aby uzyskać omówienie, zobacz [Funkcje analizy biznesowej w programach Excel i Usługi programu Excel (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx). <br/> |Wskaźników KPI programu MOSS utworzonych przy użyciu programu SharePoint Server 2007 można używać w programach SharePoint Server 2010, SharePoint Server 2013 i SharePoint Server 2016. Nie można jednak tworzyć nowych wskaźników KPI mosS.  <br/> |
|Excel 2007  <br/> |**Excel** (w chmurze lub lokalnie). Aby uzyskać omówienie, zobacz Funkcje [usługi bi w Excel i Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx). <br/><br/> **Power BI** (w chmurze lub lokalnie). Aby uzyskać omówienie, [zobacz Co to jest Power BI?](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |Zarówno Excel, jak i Power BI Twojej organizacji oferują rozwiązania chmurowe i lokalne, które zapewniają obsługę wielu różnych źródeł danych.  <br/> |
   
### <a name="help-selecting-a-solution"></a>Pomoc w wyborze rozwiązania

Ponieważ jest dostępnych tak wiele opcji do wyboru, określenie najlepszej z nich może wydawać się przytłaczające. Aby Ci pomóc, mamy dostępny przewodnik online. Zobacz [Wybieranie narzędzi analizy biznesowej firmy Microsoft do analizy i raportowania](/sql/reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting).
  
### <a name="what-if-i-dont-upgrade-now"></a>Co zrobić, jeśli nie uaktualnię teraz?

Możesz nie uaktualniać od razu. Istniejące serwery i aplikacje będą nadal działać. Nie będziesz jednak otrzymywać dalszych aktualizacji, w tym aktualizacji zabezpieczeń, ponieważ zakończono pomoc techniczną. A jeśli coś poszło nie tak z aplikacjami serwera, nie będzie można uzyskać pomocy technicznej od firmy Microsoft.
  
## <a name="how-do-i-plan-my-upgrade"></a>Jak zaplanować uaktualnienie?

Kolejnym krokiem po poznaniu opcji uaktualnienia jest przygotowanie planu uaktualnienia. W poniższych sekcjach zajmą się informacjami i dodatkowymi zasobami, które mogą ci pomóc. Masz cztery główne opcje, w tym dwie, które działają zarówno w chmurze, jak i lokalnie, i dwie, które są tylko lokalne:
  
|**Opcja**|**W chmurze czy lokalnie?**|
|:-----|:-----|
|[Excel z SharePoint (lokalnie)](#excel-with-sharepoint-server-on-premises) <br/> |Oba  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or-on-premises)<br/> |Oba  <br/> |
|[Reporting Services](#use-reporting-services-on-premises) <br/> |Tylko lokalnie  <br/> |
|[Usługi programu PerformancePoint](#use-performancepoint-services-on-premises) <br/> |Tylko lokalnie  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>Używanie Excel (w chmurze lub lokalnie)

W programie Excel, który w programie SharePoint *Usługi programu Excel* Server jest również znany jako Usługi programu Excel, można wyświetlać skoroszyty i używać ich w oknie przeglądarki, nawet jeśli program Excel nie jest zainstalowany na komputerze. Za pomocą Excel można tworzyć raporty, karty wyników i pulpity nawigacyjne. Następnie udostępnij skoroszyty innym osobom, które mogą korzystać z programu Excel w przeglądarce, niezależnie od tego, czy używają usługi SharePoint Online w ramach usługi Microsoft 365, czy programu SharePoint Server lokalnie. Możesz korzystać z danych przechowywanych lokalnie lub w chmurze, co umożliwia korzystanie z wielu różnych źródeł danych.
  
W poniższej tabeli porównano najważniejsze zalety korzystania Excel z Microsoft 365 z Excel z programem SharePoint Server. Poniżej po następuje więcej informacji.
  
|**Excel z Microsoft 365 (w chmurze)**|**Excel z SharePoint (lokalnie)**|
|:-----|:-----|
|**Masz dostęp do najnowszej i największej wersji Excel**. Dzięki Microsoft 365 masz najnowszą wersję programu Excel, która zawiera nowe zaawansowane typy wykresów, możliwość szybkiego i łatwego tworzenia wykresów oraz tabel oraz obsługę większej liczby źródeł danych. <br/> <br/> **Konfiguracja jest znacznie uproszczona**. Excel jest dołączony do Microsoft 365 dla firm, dzięki czemu nie masz ciężkiej pracy. Zarejestruj się i zaloguj się, a wszystko będzie działać szybciej i wydajniej niż w przypadku uaktualniania serwerów lokalnych. <br/> <br/> **Skoroszyty są dostępne wszędzie**. Skoroszyty można bezpiecznie wyświetlać z miejsca, w którym się znajdują, przy użyciu komputera, smartfonu i tabletu. <br/> <br/> **To nie wszystko!** Zobacz [Funkcje usługi bi w Excel i Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx). <br/> |**Zarządzasz ustawieniami globalnymi**. Jako administrator SharePoint możesz określić ustawienia globalne, takie jak zabezpieczenia, równoważenie obciążenia, zarządzanie sesjami, buforowanie skoroszytów i połączenia danych zewnętrznych. <br/> <br/> **Możesz używać Usługi programu Excel z Usługi programu PerformancePoint**. Można konfigurować Usługi programu Excel i Usługi programu PerformancePoint w ramach instalacji programu SharePoint Server oraz uwzględniać raporty Usługi programu Excel pulpitów nawigacyjnych programu PerformancePoint. <br/> <br/> **To nie wszystko!** Zobacz [Funkcje analizy biznesowej w Excel i Usługi programu Excel (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx). <br/> |
   
#### <a name="excel-with-microsoft-365-in-the-cloud"></a>Excel z Microsoft 365 (w chmurze)

Po przejście do Microsoft 365 będziesz mieć najnowsze usługi i aplikacje, w tym usługi Excel 2016. Usługi programu PerformancePoint nie jest dostępna w programie Microsoft 365, dlatego chcesz zastąpić zawartość pulpitu nawigacyjnego programu PerformancePoint zawartością pulpitu nawigacyjnego programu PerformancePoint Excel skoroszytami lub innymi raportami. Dobra wiadomość jest taka, że Excel 2016 zawiera wiele nowych typów wykresów, a tworzenie imponujących pulpitów nawigacyjnych w programie Excel jest łatwiejsze Excel. Nowe funkcje są regularnie dodawane. Aby dowiedzieć się więcej, [zobacz Co nowego w programie Excel 2016 dla Windows](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx).
  
Ponadto jeśli zakupisz co najmniej 50 stanowisk Microsoft 365, zespół FastTrack Microsoft FastTrack pomoże Ci w skonfigurowaniu tej usługi. Aby dowiedzieć się więcej, odwiedź [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365).
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel z SharePoint (lokalnie)

W przypadku uaktualnienia do nowszej wersji pakietu SharePoint można używać programu Excel z programem Usługi programu Excel lub przeglądarką w następujący sposób:
  
- Usługi programu Excel programie SharePoint Server 2010
    
- Usługi programu Excel w SharePoint Server 2013
    
- Excel, która jest częścią Office Online Server, instalowana niezależnie od programu SharePoint Server 2016
    
Możesz skonfigurować Usługi programu PerformancePoint w nowej wersji programu SharePoint Server i używać go razem z Excel.
  
Aby dowiedzieć się więcej o dostępnych SharePoint uaktualniania, zobacz SharePoint Zakończenie pomocy technicznej dla programu [Server 2007 Przewodnik po zakończeniu pomocy technicznej](sharepoint-2007-end-of-support.md).
  
Aby dowiedzieć się więcej o Usługi programu Excel, zobacz [Usługi programu Excel omówienie (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee424405(v=office.14)).
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>Używanie Power BI (w chmurze lub lokalnie)

Power BI to pakiet narzędzi do analizy biznesowej do analizowania danych i udostępniania szczegółowych informacji. Za Power BI możesz tworzyć interakcyjne raporty i pulpity nawigacyjne przy użyciu źródeł danych lokalnych lub online. Inne osoby mogą wyświetlać Twoje raporty i pulpity nawigacyjne oraz korzystać z nich na swoich komputerach lub urządzeniach przenośnych.
  
Power BI nie jest częścią programu Microsoft 365 ani SharePoint Server. Jest to osobna oferta, która obejmuje Power BI Desktop, Power BI bram i usługę Power BI bramy. Power BI można również zintegrować z usługą SharePoint Online. Możesz rozpocząć pracę z Power BI bezpłatnie. W zależności od wykorzystania danych i potrzeb biznesowych możesz później uaktualnić usługę do Power BI Pro z Microsoft 365 E5. Aby dowiedzieć się więcej, [zobacz Co to jest Power BI?](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>Korzystanie z usług Reporting Services (lokalnie)

SQL Server Reporting Services udostępnia zaawansowane rozwiązanie do raportowania. Usługi Reporting Services można skonfigurować w trybie natywnym SharePoint trybie zintegrowanym. Do tworzenia raportów można używać kilku różnych narzędzi, takich jak Report Designer, Report Builder i Power View. Najnowsza wersja aplikacji SQL Server umożliwia też dostarczanie raportów w aplikacji raport SQL Server mobile report Publisher do dowolnego rozmiaru ekranu. Umożliwi to użytkownikom dostęp do raportów na urządzeniach przenośnych. Aby dowiedzieć się więcej, [zobacz SQL Server Reporting Services (SSRS): Tworzenie i wdrażanie](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports) raportów mobilnych i podzielonych na strony oraz zarządzanie nimi.
  
### <a name="use-performancepoint-services-on-premises"></a>Użyj Usługi programu PerformancePoint (lokalnie)

PerformancePoint Server 2007 był sprzedawany niezależnie od SharePoint Server 2007. Począwszy od SharePoint Server 2010, Usługi programu PerformancePoint jest aplikacją usługi w SharePoint Server. Zatem nie musisz kupować osobnych licencji serwera ani sprzętu, aby używać Usługi programu PerformancePoint.
  
Aby przejść z PerformancePoint Server 2007 do Usługi programu PerformancePoint, należy przejść do najnowszej wersji programu SharePoint Server i skonfigurować Usługi programu PerformancePoint. Wersja programu SharePoint, która jest przesunana w celu określenia, czy można zaimportować istniejącą zawartość pulpitu nawigacyjnego z programu PerformancePoint Server 2007 do Usługi programu PerformancePoint.
  
- W przypadku uaktualnienia do programu SharePoint Server 2010 można zaimportować zawartość pulpitu nawigacyjnego programu PerformancePoint z programu PerformancePoint Server 2007 do programu Usługi programu PerformancePoint w programie SharePoint Server 2010. Aby dowiedzieć się więcej, zobacz [Kreator importu: PerformancePoint Server 2007 do SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/ee681485(v=office.14)).
    
- Po przejście do programu SharePoint Server 2013 lub SharePoint Server 2016 będzie prawdopodobnie konieczne utworzenie nowej zawartości pulpitu nawigacyjnego (źródeł danych, raportów, kart wyników i stron pulpitu nawigacyjnego).
    
Aby rozpocząć pracę nad planem Usługi programu PerformancePoint, zobacz następujące zasoby:
  
- [SharePoint dotyczące zakończenia pomocy technicznej dla programu SharePoint Server 2007 Przewodnik](sharepoint-2007-end-of-support.md)
    
- Jeśli wiesz, do której wersji SharePoint się przenosisz, zobacz odpowiedni artykuł dla Usługi programu PerformancePoint:
    
  - [Planowanie na Usługi programu PerformancePoint (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee681486(v=office.14))
    
  - [Usługi programu PerformancePoint programu SharePoint Server 2013 — omówienie](/sharepoint/administration/performancepoint-services-overview)
    
  - [Usługi programu PerformancePoint programu SharePoint Server 2016 — omówienie](/sharepoint/administration/performancepoint-services-overview)
    
Po uaktualnieniu do Usługi programu PerformancePoint otrzymasz kilka nowych funkcji i ulepszeń. Usługi programu PerformancePoint oferuje ulepszone karty wyników, nowe wizualizacje, takie jak raport drzewa dekompozycji i szczegóły wskaźnika KPI, więcej typów wykresów, lepsze możliwości filtrowania analizy czasowej oraz lepszą zgodność z ułatwieniami dostępu. Aby dowiedzieć się więcej, zobacz Co [nowego w programie Usługi programu PerformancePoint (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14)).
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>Gdzie mogę uzyskać pomoc przy uaktualnieniu?

Niezależnie od tego, czy uaktualnisz system lokalnie, czy przechodzisz do programu Microsoft 365, zalecamy współpracę z partnerem firmy Microsoft. Kwalifikowany partner pomoże Ci w zidentyfikowaniu rozwiązania najlepiej spełniającego Twoje potrzeby biznesowe i pomocy przy wdrażaniu. Przejdź do [Centrum partnerskiego firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) i użyj filtrów wyszukiwania, aby znaleźć dostawcę rozwiązań.
  
## <a name="related-topics"></a>Tematy pokrewne

[Zasoby pomocne w uaktualnieniu serwerów i klientów programu Office 2007](upgrade-from-office-2007-servers-and-products.md)