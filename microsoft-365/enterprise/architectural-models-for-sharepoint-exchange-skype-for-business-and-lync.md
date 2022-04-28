---
title: Modele architektoniczne dla programów SharePoint, Exchange, Skype dla firm i Lync
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: Pobierz plakaty IT opisujące modele architektury, wdrożenia i opcje platformy dla SharePoint, Exchange, Skype dla firm i lync.
ms.openlocfilehash: 859d952fc9a2e4e9315c7fef3e56b4e59d0f60d6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096881"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modele architektoniczne dla programów SharePoint, Exchange, Skype dla firm i Lync

Na plakatach IT w tym artykule opisano modele architektury i opcje wdrażania dla SharePoint, Exchange, Skype dla firm i programu Lync. Udostępniają również informacje projektowe dotyczące wdrażania SharePoint w Microsoft Azure.
  
Korzystając z Microsoft 365, możesz udostępniać znane usługi współpracy i komunikacji za pośrednictwem chmury. Z kilkoma wyjątkami środowisko użytkownika pozostaje takie samo niezależnie od tego, czy utrzymujesz wdrożenie lokalne, czy używasz Microsoft 365. 

To ujednolicone środowisko użytkownika komplikuje decyzję o tym, gdzie umieścić każde obciążenie. Rodzi to również pytania:
  
- Jak wybrać platformę dla poszczególnych obciążeń?
    
- Czy utrzymanie dowolnej usługi w środowisku lokalnym ma sens?
    
- W jakim scenariuszu wdrożenie hybrydowe jest odpowiednie?
    
- Jak platforma Azure pasuje do obrazu?
    
- Jakie konfiguracje obciążeń serwera Office pomoc techniczna platformy Azure?
    
> [!TIP]
> Większość plakatów w tym artykule jest dostępna w wielu językach. Dostępne języki to chiński, angielski, francuski, niemiecki, włoski, japoński, koreański, portugalski, rosyjski i hiszpański. Aby pobrać plakat w jednym z tych języków, pod obrazem miniatury plakatu wybierz pozycję **Więcej języków**.
  
Daj nam znać, co myślisz! Wyślij do nas wiadomość e-mail na [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Użyj następujących linków, aby uzyskać potrzebne plakaty:
  
- **Modele architektury**: użyj tych zasobów, aby określić idealną platformę i konfigurację dla SharePoint 2016 i Skype dla firm 2015.
    
  - [Modele architektury microsoft SharePoint 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [bazy danych SharePoint Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Modele architektury microsoft Skype dla firm 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Platforma**: użyj tych zasobów, aby określić idealną platformę i konfigurację dla SharePoint 2013, Exchange 2013 i Lync 2013.
    
  - [opcje platformy SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [opcje platformy Exchange 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Opcje platformy programu Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 na platformie Azure**: użyj tych plakatów IT do projektowania i konfigurowania obciążeń SharePoint Server 2013 w usługach infrastruktury platformy Azure.
    
  - [Witryny internetowe na platformie Azure przy użyciu programu SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Przykład projektu: witryny internetowe na platformie Azure dla SharePoint 2013 r.](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [SharePoint odzyskiwania po awarii na platformie Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Plakaty modeli architektonicznych

Plakaty IT dla SharePoint 2016 i Skype dla firm 2015 r. umożliwiają porównanie metod wdrażania w formacie łatwym do wydrukowania. Na plakatach są wyświetlane wszystkie opcje konfiguracji lub platformy. Udostępniają one następujące informacje dla każdej opcji:
  
- **Omówienie**: krótkie podsumowanie platformy, w tym diagram koncepcyjny.
    
- **Najlepsze dla**: Typowe scenariusze, które idealnie nadają się do platformy.
    
- **Wymagania licencyjne**: licencje potrzebne do wdrożenia.
    
- **Zadania związane z architekturą**: decyzje, które należy podjąć jako architekt.
    
- **Zadania lub obowiązki specjalistów IT**: codzienne obowiązki, które personel IT musi zaplanować.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>modele architektury Microsoft SharePoint Server 2016

|Element|Opis|
|---|---|
|[![Miniatura plakatu modeli architektonicznych SharePoint Server 2016.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)\| [](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=52650)    |Ten plakat IT zawiera opis konfiguracji SharePoint Online, Azure i SharePoint lokalnych, o których muszą wiedzieć osoby podejmujące decyzje biznesowe i architekci rozwiązań. <br/><br/> - **SharePoint Online (SaaS)**: korzystanie z SharePoint za pośrednictwem modelu subskrypcji oprogramowania jako usługi (SaaS). <br/> - **SharePoint hybrydowe**: przenieś witryny i aplikacje SharePoint do chmury we własnym tempie. <br/> - **SharePoint na platformie Azure (IaaS)**: rozszerzanie środowiska lokalnego na platformę Azure i wdrażanie tam serwerów SharePoint 2016. (Ten model jest zalecany w przypadku środowisk wysokiej dostępności lub odzyskiwania po awarii oraz środowisk deweloperskich/testowych). <br/> - **SharePoint lokalnie**: planowanie, wdrażanie, konserwacja i dostosowywanie środowiska SharePoint w obsługiwanym centrum danych.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>bazy danych SharePoint Server 2016

|Element|Opis|
|---|---|
|[![Miniatura plakatu bazy danych SharePoint Server 2016.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)\| [](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=55041)    |Ten plakat IT to krótkie odwołanie do baz danych SharePoint Server 2016. Zostaną wyświetlone szczegółowe informacje dotyczące każdej bazy danych: <br/><br/> - Rozmiar <br/> — Wskazówki dotyczące skalowania <br/> - Wzorce we/wy <br/> - Wymagania <br/><br/>  Na pierwszej stronie przedstawiono SharePoint systemowe bazy danych i aplikacje usług, które mają wiele baz danych. Na drugiej stronie przedstawiono wszystkie aplikacje usług, które mają pojedyncze bazy danych. <br/><br/>  Aby uzyskać więcej informacji, zobacz [Typy i opisy baz danych w programie SharePoint Server 2016](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modele architektury microsoft Skype dla firm 2015

|Element|Opis|
|---|---|
|[![Miniatura plakatu modeli architektury Skype dla firm.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)\| [](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=55022)    |Ten plakat zawiera opis usługi Skype dla firm Online, lokalnej, hybrydowej i prywatnej wymiany oddziałów w chmurze (PBX). Opisano w nim również integrację z konfiguracjami Exchange i SharePoint, o których muszą wiedzieć osoby podejmujące decyzje biznesowe i architekci rozwiązań. <br/><br/> Plakat jest przeznaczony dla specjalistów IT w celu podniesienia świadomości podstawowych modeli architektonicznych, za pośrednictwem których można korzystać Skype dla firm Online i Skype dla firm lokalnie. <br/><br/>Zacznij od konfiguracji, która najlepiej odpowiada potrzebom i planom organizacji. W razie potrzeby rozważ i użyj innych konfiguracji. Na przykład warto rozważyć integrację z Exchange i SharePoint lub rozwiązaniem, które korzysta z oferty PBX w chmurze firmy Microsoft.|
   
## <a name="platform-options-posters"></a>Plakaty opcji platformy

Plakaty IT dla SharePoint 2013, Exchange 2013 i Lync 2013 umożliwiają szybkie porównanie metod wdrażania. Każdy plakat zawiera listę wszystkich konfiguracji lub opcji platformy. Zawiera następujące informacje dla każdej opcji:
  
- **Omówienie**: krótkie podsumowanie platformy, w tym diagram koncepcyjny.
    
- **Najlepsze dla**: Typowe scenariusze, które idealnie nadają się do platformy.
    
- **Wymagania licencyjne**: licencje potrzebne do wdrożenia.
    
- **Zadania związane z architekturą**: decyzje, które należy podjąć jako architekt.
    
- **Zadania lub obowiązki specjalistów IT**: codzienne obowiązki, które personel IT musi zaplanować.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>opcje platformy SharePoint 2013

|Element|Opis|
|---|---|
|[![Miniatura plakatu opcje platformy SharePoint 2013.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)\| [](https://go.microsoft.com/fwlink/p/?LinkId=324593)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=40332)    |W przypadku osób podejmujących decyzje biznesowe i architektów ten plakat przedstawia opcje platformy dla SharePoint 2013 r., SharePoint w Microsoft 365, w środowisku hybrydowym lokalnym z wdrożeniami Microsoft 365, azure i wdrożeniami lokalnymi. Zawiera omówienie każdej architektury, zaleceń, wymagań licencyjnych oraz list zadań architekta i specjalistów IT dla każdej platformy. Plakat przedstawia kilka rozwiązań SharePoint na platformie Azure.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>opcje platformy Exchange 2013

|Element|Opis|
|---|---|
|[![Miniatura plakatu opcje platformy Exchange.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)\| [](https://go.microsoft.com/fwlink/p/?LinkID=398742)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=42676)    |W przypadku osób podejmujących decyzje biznesowe i architektów ten plakat opisuje opcje platformy dla Exchange 2013 roku. Klienci mogą wybierać spośród Exchange Online za pomocą Microsoft 365, Exchange hybrydowych, Exchange Server lokalnych i hostowanych Exchange. Plakat zawiera szczegóły każdej opcji architektury, w tym idealne scenariusze dla każdej z nich, wymagania licencyjne i obowiązki specjalistów IT.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Opcje platformy programu Lync 2013

|Element|Opis|
|---|---|
|[![Miniatura plakatu Opcje platformy programu Lync 2013.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)\| [](https://go.microsoft.com/fwlink/p/?LinkID=391839)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=41677)    |W przypadku osób podejmujących decyzje biznesowe i architektów ten plakat zawiera opis opcji platformy dla programu Lync 2013. Klienci mogą wybierać z usługi Lync Online za pomocą Microsoft 365, hybrydowego programu Lync, lokalnego programu Lync Server i hostowanego programu Lync. Plakat IT zawiera szczegóły każdej opcji architektury, w tym idealne scenariusze dla każdej z nich, wymagania licencyjne i obowiązki specjalistów IT.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>SharePoint na plakatach rozwiązań platformy Azure

Plakaty IT dla SharePoint na platformie Azure pokazują rozwiązania oparte na platformie Azure korzystające z programu SharePoint Server 2013.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Witryny internetowe w Microsoft Azure przy użyciu programu SharePoint Server 2013

|Element|Opis|
|---|---|
|[![Obraz przedstawiający witryny internetowe na platformie Azure przy użyciu plakatu SharePoint Server 2013.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392551)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=41992)    |Ten plakat przedstawia kluczowe działania projektowe i zalecaną architekturę witryn internetowych na platformie Azure.  <br/><br/> Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:  <br/><br/> - [Witryny internetowe na platformie Azure przy użyciu programu SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architektury platformy Azure dla SharePoint 2013 r.](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>Witryny internetowe na platformie Azure dla SharePoint 2013 r.

|Element|Opis|
|---|---|
|[![Obraz przedstawiający witryny internetowe w Microsoft Azure dla plakatu SharePoint Server 2013.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392548)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=41991)    |Użyj tego przykładu projektu jako punktu wyjścia dla własnej architektury witryny internetowej na platformie Azure przy użyciu programu SharePoint Server 2013. <br/><br/> Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:  <br/><br/> - [Witryny internetowe na platformie Azure przy użyciu programu SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architektury platformy Azure dla SharePoint 2013 r.](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint odzyskiwanie po awarii do Microsoft Azure

|Element|Opis|
|---|---|
|[![Obraz przedstawiający plakat SharePoint procesu odzyskiwania po awarii na platformie Azure.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392554)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=41993)    |Ten plakat IT przedstawia zasady architektury środowiska odzyskiwania po awarii na platformie Azure. <br/><br/> Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:  <br/><br/> - [odzyskiwanie po awarii SharePoint Server 2013 na platformie Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Architektury platformy Azure dla SharePoint 2013 r.](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>Zobacz też

- [Centrum rozwiązań i architektury platformy Microsoft 365](../solutions/index.yml)
  
- [Modele architektury chmury firmy Microsoft](../solutions/cloud-architecture-models.md)
  
- [przewodniki laboratorium testowego Microsoft 365](m365-enterprise-test-lab-guides.md)
  
- [Rozwiązania hybrydowe](hybrid-solutions.md)