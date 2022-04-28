---
title: Wyszukiwanie zawartości służy do wyszukiwania zaimportowanych danych innych firm
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: ec2677ff-c4d7-4363-a9e7-22c80e015688
description: Za pomocą narzędzia content search eDiscovery wyszukaj elementy zaimportowane do skrzynek pocztowych w Microsoft 365 ze źródła danych innej firmy, tworząc zapytania.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 73967c8897ee0fd5143b8e15dfe8874fc0c85755
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095405"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>Wyszukiwanie zawartości służy do wyszukiwania danych innych firm zaimportowanych przez łącznik niestandardowego partnera

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Za pomocą narzędzia do [zbierania elektronicznych materiałów dowodowych wyszukiwania zawartości](content-search.md) w portalu zgodności usługi Microsoft Purview można wyszukiwać elementy zaimportowane do skrzynek pocztowych w Microsoft 365 ze źródła danych innej firmy. Możesz utworzyć zapytanie do wyszukiwania wszystkich zaimportowanych elementów danych innych firm lub utworzyć zapytanie w celu wyszukiwania określonych elementów danych innych firm. Ponadto można również utworzyć zasady przechowywania oparte na zapytaniach lub oparte na zapytaniach blokady zbierania elektronicznych materiałów dowodowych w celu zachowania danych innych firm.
  
Aby uzyskać więcej informacji na temat pracy z partnerem w celu zaimportowania danych innych firm oraz listy typów danych innych firm, które można zaimportować do Microsoft 365, zobacz [Praca z partnerem w celu archiwizacji danych innych firm w Office 365](work-with-partner-to-archive-third-party-data.md).

> [!IMPORTANT]
> Wskazówki zawarte w tym artykule dotyczą tylko danych innych firm, które zostały zaimportowane przez łącznik niestandardowego partnera. Ten artykuł nie dotyczy danych innych firm, które są importowane przy użyciu [łączników danych innych firm](archiving-third-party-data.md#third-party-data-connectors) w Centrum zgodności firmy Microsoft.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>Tworzenie zapytania w celu wyszukiwania wszystkich danych innych firm

Aby wyszukać (lub zatrzymać) dowolny typ danych innych firm zaimportowanych do Office 365, możesz użyć `kind:externaldata` pary właściwość-wartość komunikatu w polu słowa kluczowego dla wyszukiwania zawartości lub podczas tworzenia blokady opartej na zapytaniach. Aby na przykład wyszukać elementy zaimportowane z dowolnego źródła danych innej firmy i zawierać słowo "contoso" we właściwości Podmiot zaimportowanego elementu, należy użyć następującego zapytania: 
  
```powershell
kind:externaldata AND subject:contoso
```

Poprzedni przykład zapytania słowa kluczowego zawiera właściwość podmiotu. Aby uzyskać listę innych właściwości elementów danych innych firm, które mogą zostać uwzględnione w zapytaniu słowa kluczowego, zobacz sekcję "Więcej informacji" w [temacie Praca z partnerem w celu archiwizowania danych innych firm w Office 365](work-with-partner-to-archive-third-party-data.md#more-information).
  
Podczas tworzenia zapytań do wyszukiwania i przechowywania danych innych firm można również użyć warunków, aby zawęzić wyniki wyszukiwania. Aby uzyskać więcej informacji na temat tworzenia zapytań wyszukiwania zawartości, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>Tworzenie zapytania w celu wyszukiwania określonych typów danych innych firm

Zamiast przeszukiwać wszystkie typy danych innych firm, można tworzyć zapytania, które wyszukują tylko określony typ danych innych firm, używając następującej właściwości komunikatu *: para wartości* w polu słowa kluczowego wyszukiwania zawartości:
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

Aby na przykład wyszukać dane serwisu Facebook zawierające słowo "contoso" we właściwości Podmiot, należy użyć następującego zapytania:
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

W poniższej tabeli wymieniono typy danych innych firm, które można wyszukać, oraz wartość, która ma być używana dla właściwości komunikatu  `itemclass:` w celu wyszukiwania tego typu danych innych firm. Składnia zapytania nie uwzględnia wielkości liter. 
  
|**Typ danych innych firm**|**Wartość właściwości `itemclass:`**|
|:-----|:-----|
|CELEM  <br/> | `ipm.externaldata.AIM*` <br/> |
|Amerykański idol  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|AOL z klientem przestawnym  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|Sok jabłkowy  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|Ares  <br/> | `ipm.externaldata.Ares*` <br/> |
|Axs Encrypted  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Axs Exchange  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|Archiwum lokalne usługi Axs  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|Symbol zastępczy usługi Axs  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Podpisane przez usługę Axs  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Bazaarvoice  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|Bearshare  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|Bittorrent  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|Blackberry  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|Dzienniki połączeń BlackBerry  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|BlackBerry PIN  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry SMS  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|Bloomberg  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|Wiadomość serwisu Bloomberg  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|Bloomberg Messaging  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|Pole  <br/> | `ipm.externaldata.Box*` <br/> |
|Cisco IM &amp; Presence Server  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|Cisco Jabber  <br/> | `ipm.externaldata.Jabber*` <br/> |
|CipherCloud for Salesforce Chatter  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|Połączenie bezpośredni  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|Facebook  <br/> | `ipm.externaldata.Facebook*` <br/> |
|FastTrack  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|FXConnect  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|Flickr  <br/> | `ipm.externaldata.Flickr*` <br/> |
|Gnutella  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|Google+  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|Google Talk  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|GoToMyPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|Hopster  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|Połączenia IBM  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|Czat ICE  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|Instagram  <br/> | `ipm.externaldata.Instagram*` <br/> |
|Instant Bloomberg  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|InvestEdge  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|IRC  <br/> | `ipm.externaldata.IRC*` <br/> |
|Jive  <br/> | `ipm.externaldata.Jive*` <br/> |
|JiveApiRetention  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|JXTA  <br/> | `ipm.externaldata.JXTA*` <br/> |
|LinkedIn  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|MFTP  <br/> | `ipm.externaldata.MFTP*` <br/> |
|Microsoft UC  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|Wyrównaj do umysłu  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|Mobile Guard  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|MSN  <br/> | `ipm.externaldata.MSN*` <br/> |
|Myspace  <br/> | `ipm.externaldata.MySpace*` <br/> |
|NEONetwork  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Dokument bazowy  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Czat w usłudze Salesforce  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype dla firm  <br/> | `ipm.externaldata.Skype*` <br/> |
|Slack Enterprise Grid  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|Softether  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|Symphony  <br/> | `ipm.externaldata.Symphony*` <br/> |
|Thomson Reuters  <br/> | `ipm.externaldata.Reuters*` <br/> |
| Thomson Reuters Eikon Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|Tor  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|Czat UBS  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|Winmx  <br/> | `ipm.externaldata.WinMX*` <br/> |
|Winny  <br/> | `ipm.externaldata.Winny*` <br/> |
|Yahoo!  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|YellowJacket  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
