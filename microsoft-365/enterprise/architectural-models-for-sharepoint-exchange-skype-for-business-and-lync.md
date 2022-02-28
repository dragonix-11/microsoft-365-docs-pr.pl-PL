---
title: Modele architektoniczne SharePoint, Exchange, Skype dla firm i Lync
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Pobierz plakaty IT opisujące modele architektoniczne, wdrożenie i opcje platformy dla SharePoint, Exchange, Skype dla firm i Lync.
ms.openlocfilehash: 813a143d281f85e6cbc9c0456dceaf20c674d13b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985225"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modele architektoniczne SharePoint, Exchange, Skype dla firm i Lync

Plakaty it w tym artykule opisują modele architektoniczne i opcje wdrażania SharePoint, Exchange, Skype dla firm i Lync. Zawierają one również informacje o projekcie wdrożenia SharePoint w Microsoft Azure.
  
Korzystając z Microsoft 365, możesz świadczyć znajome usługi do współpracy i komunikacji za pośrednictwem chmury. W przypadku kilku wyjątków środowisko użytkownika pozostaje bez względu na to, czy korzystasz z wdrożenia lokalnego, czy Microsoft 365. 

To ujednolicone środowisko użytkownika komplikuje decyzję o tym, gdzie należy umieścić poszczególne obciążenia pracą. Jest też związane z tym pytanie:
  
- Jak wybrać platformę dla poszczególnych obciążeń?
    
- Czy warto przechowywać dowolną usługę lokalnie?
    
- W którym scenariuszu jest odpowiednie wdrożenie hybrydowe?
    
- Jak platforma Azure mieści się w obrazie?
    
- Jakie konfiguracje obciążenia Office serwera obsługuje system Azure?
    
> [!TIP]
> Większość plakatów w tym artykule jest dostępnych w wielu językach. Dostępne języki to: chiński, angielski, francuski, niemiecki, włoski, japoński, koreański, portugalski, rosyjski i hiszpański. Aby pobrać plakat w jednym z tych języków, pod obrazem miniatury plakatu wybierz pozycję **Więcej języków**.
  
Daj nam znać, co o tym sądzisz! Wyślij nam wiadomość e-mail [na adres cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Użyj poniższych linków, aby pobrać potrzebne plakaty:
  
- **Modele architektoniczne**. Użyj tych zasobów, aby określić idealną platformę i konfigurację dla SharePoint 2016 i Skype dla firm 2015.
    
  - [Modele SharePoint architektury firmy Microsoft SharePoint 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint danych programu SharePoint Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Modele Skype dla firm architektury firmy Microsoft Skype dla firm 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Platforma**. Skorzystaj z tych zasobów, aby określić idealną platformę i konfigurację dla oprogramowania SharePoint 2013, Exchange 2013 i Lync 2013.
    
  - [opcje SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [opcje Exchange 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Opcje platformy programu Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013** na platformie Azure: Za pomocą tych plakatów it można projektować i konfigurować obciążenia pracą programu SharePoint Server 2013 w usługach infrastruktury platformy Azure.
    
  - [Witryny internetowe na platformie Azure przy SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Przykład projektu: witryny internetowe na platformie Azure dla SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [SharePoint odzyskiwania po awarii do platformy Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Plakaty modeli architektonicznych

Plakaty it dla SharePoint 2016 i Skype dla firm 2015 zapewniają sposób porównywania metod wdrażania w formacie łatwym do wydrukowania. Plakaty zawiera listę wszystkich opcji konfiguracji lub platformy. Zapewniają następujące informacje dla każdej z opcji:
  
- **Omówienie**: krótkie podsumowanie platformy, w tym diagram koncepcyjny.
    
- **Najlepsze rozwiązanie**: Typowe scenariusze, które najlepiej nadają się do działania platformy.
    
- **Wymagania licencyjne**: licencje potrzebne do wdrożenia.
    
- **Zadania związane z architekturą**. Decyzje, które należy podjąć jako architekt.
    
- **Zadania lub obowiązki pracowników it**: dzienny zakres obowiązków, na który musi zaplanować twój personel IT.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>Microsoft SharePoint Server architektoniczne z roku 2016

|Element|Opis|
|---|---|
|[![Miniatura plakatu SharePoint modeli architektonicznych programu SharePoint Server 2016.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)\| [](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=52650)    |Ten plakat IT zawiera opis SharePoint usługi Online, platformy Azure i oprogramowania SharePoint konfiguracji lokalnych, o których muszą wiedzieć twórcy procesów biznesowych i architektów rozwiązań. <br/><br/> - **SharePoint Online (SaaS)**: SharePoint za pośrednictwem modelu subskrypcji oprogramowanie jako usługa (SaaS). <br/> - **SharePoint hybrydowe**: Przenieś witryny SharePoint aplikacje do chmury we własnym tempie. <br/> - **SharePoint Azure (IaaS)**: Rozszerzanie środowiska lokalnego na platformę Azure i wdrażanie serwerów SharePoint 2016. (Ten model jest zalecany w przypadku środowisk o wysokiej dostępności lub odzyskiwania po awarii oraz środowisk deweloperskich/testowych). <br/> - **SharePoint lokalnie**: planowanie, wdrażanie, obsługa i dostosowywanie środowiska SharePoint w utrzymywanym centrum danych.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint danych programu SharePoint Server 2016

|Element|Opis|
|---|---|
|[![Miniatura plakatu bazy SharePoint Server 2016.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)\| [](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=55041)    |Ten plakat IT zawiera podręczną informacje na temat baz danych SharePoint Server 2016. Zobaczysz szczegółowe informacje dotyczące każdej bazy danych: <br/><br/> — Rozmiar <br/> — wskazówki dotyczące skalowania <br/> - Wzorce we/Wy <br/> — Wymagania <br/><br/>  Na pierwszej stronie przedstawiono bazy danych SharePoint systemowych i aplikacje usług, które mają wiele baz danych. Na drugiej stronie przedstawiono wszystkie aplikacje usług, które mają pojedyncze bazy danych. <br/><br/>  Aby uzyskać więcej informacji, zobacz [Typy i opisy baz danych w programie SharePoint Server 2016](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modele Skype dla firm architektury firmy Microsoft 2015

|Element|Opis|
|---|---|
|[![Miniatura plakatu Skype dla firm modeli architektonicznych.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)\| [](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=55022)    |Ten plakat zawiera opis Skype dla firm PBX w trybie online, lokalnym, hybrydowym i w chmurze. Opisano w nim także integrację Exchange i konfiguracji SharePoint firmowych, o których muszą wiedzieć twórcy rozwiązań biznesowych i architektzy rozwiązań. <br/><br/> Plakat jest przeznaczony dla informatyków w celu zwiększenia wiedzy na temat podstawowych modeli architektonicznych, dzięki którym można Skype dla firm online i Skype dla firm lokalnym. <br/><br/>Zacznij od konfiguracji, która najlepiej odpowiada potrzebom i planom Twojej organizacji. Rozważ inne konfiguracje i używaj ich zgodnie z potrzebami. Na przykład warto rozważyć integrację z systemami Exchange i SharePoint lub rozwiązanie, które skorzysta z oferty usługi PBX firmy Microsoft w chmurze.|
   
## <a name="platform-options-posters"></a>Plakaty z opcjami platformy

Plakaty it dla systemów SharePoint 2013, Exchange 2013 i Lync 2013 zapewniają szybki sposób porównywania metod wdrażania. Każdy plakat zawiera listę wszystkich konfiguracji lub opcji platformy. Dla każdej z tych opcji są podane następujące informacje:
  
- **Omówienie**: krótkie podsumowanie platformy, w tym diagram koncepcyjny.
    
- **Najlepsze rozwiązanie**: Typowe scenariusze, które najlepiej nadają się do działania platformy.
    
- **Wymagania licencyjne**: licencje potrzebne do wdrożenia.
    
- **Zadania związane z architekturą**. Decyzje, które należy podjąć jako architekt.
    
- **Zadania lub obowiązki pracowników it**: dzienny zakres obowiązków, na który musi zaplanować twój personel IT.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>opcje SharePoint 2013

|Element|Opis|
|---|---|
|[![Miniatura obrazu plakatu SharePoint Opcje platformy 2013.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)\| [](https://go.microsoft.com/fwlink/p/?LinkId=324593)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=40332)    |Ten plakat dla osób decyzyjnych i architektów biznesowych przedstawia opcje platformy dla usług SharePoint 2013 i SharePoint w programie Microsoft 365 — lokalnego wdrożenia hybrydowego z wdrożeniami Microsoft 365, Azure i tylko lokalnymi. Zawiera omówienie każdej architektury, zaleceń, wymagań licencyjnych oraz list zadań architektów i profesjonalistów it dla poszczególnych platform. Ten plakat wyróżnia kilka SharePoint rozwiązania na platformie Azure.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>opcje Exchange 2013

|Element|Opis|
|---|---|
|[![Miniatura obrazu plakatu Exchange Opcje platformy.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)\| [](https://go.microsoft.com/fwlink/p/?LinkID=398742)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=42676)    |Dla osób decyzyjnych i architektów biznesowych ten plakat zawiera opis opcji platformy dla Exchange 2013. Klienci mogą wybierać spośród Exchange Online z Microsoft 365, hybrydowym Exchange, Exchange Server lokalnym i hostowaną Exchange. Plakat zawiera szczegółowe informacje na temat poszczególnych opcji architektury, w tym idealne scenariusze dla poszczególnych opcji, wymagania licencyjne i obowiązki profesjonalnych it.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Opcje platformy programu Lync 2013

|Element|Opis|
|---|---|
|[![Miniatura obrazu plakatu Opcje platformy programu Lync 2013.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)\| [](https://go.microsoft.com/fwlink/p/?LinkID=391839)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=41677)    |Dla twórców i architektów biznesowych ten plakat zawiera opis opcji platformy dla programu Lync 2013. Klienci mogą wybierać z usługi Lync Online Microsoft 365, hybrydowym programem Lync, lokalnym programem Lync Server i hostowaną usługą Lync. Plakat IT zawiera szczegóły poszczególnych opcji architektury, w tym idealne scenariusze dla poszczególnych opcji, wymagania licencyjne i obowiązki pro it.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>SharePoint na plakatach rozwiązań platformy Azure

Plakaty IT dla SharePoint platformie Azure pokazują oparte na platformie Azure rozwiązania, które korzystają z SharePoint Server 2013.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Witryny internetowe w programie Microsoft Azure SharePoint Server 2013

|Element|Opis|
|---|---|
|[![Obraz witryn internetowych na platformie Azure używających plakatu SharePoint Server 2013.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392551)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=41992)    |Ten plakat zawiera opis kluczowych działań projektowych i zalecanej architektury dla witryn internetowych na platformie Azure.  <br/><br/> Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:  <br/><br/> - [Witryny internetowe na platformie Azure przy SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architekturę platformy Azure dla SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>Witryny internetowe na platformie Azure SharePoint 2013

|Element|Opis|
|---|---|
|[![Obraz witryn internetowych w programie Microsoft Azure plakat SharePoint Server 2013.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392548)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=41991)    |Skorzystaj z tego przykładu projektu jako punktu wyjścia dla własnej architektury witryny internetowej na platformie Azure przy użyciu programu SharePoint Server 2013. <br/><br/> Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:  <br/><br/> - [Witryny internetowe na platformie Azure przy SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architekturę platformy Azure dla SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint odzyskiwania po awarii Microsoft Azure

|Element|Opis|
|---|---|
|[![Obraz plakatu dla procesu odzyskiwania po awarii SharePoint na platformie Azure.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392554)\| Visio [więcej języków](https://www.microsoft.com/download/details.aspx?id=41993)    |Ten plakat IT przedstawia zasady architektury środowiska odzyskiwania po awarii na platformie Azure. <br/><br/> Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:  <br/><br/> - [SharePoint odzyskiwania po awarii serwera 2013 na platformie Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Architekturę platformy Azure dla SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>Zobacz też

- [Microsoft 365 rozwiązania i architektury](../solutions/index.yml)
  
- [Modele architektury chmury firmy Microsoft](../solutions/cloud-architecture-models.md)
  
- [Microsoft 365 laboratorium testowego](m365-enterprise-test-lab-guides.md)
  
- [Rozwiązania hybrydowe](hybrid-solutions.md)