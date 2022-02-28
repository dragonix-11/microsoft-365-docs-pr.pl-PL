---
title: Przeszukiwanie zawartości za pomocą wyszukiwania zaimportowanych danych innych firm
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Narzędzie zbierania elektronicznych materiałów dowodowych przeszukiwania zawartości umożliwia wyszukiwanie elementów zaimportowanych do skrzynek pocztowych w programie Microsoft 365 ze źródła danych innej firmy przez tworzenie zapytań.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 068a6e3164154129ba9148b41138d50c518042ed
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988022"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>Przeszukiwanie zawartości w celu wyszukiwania danych innych firm zaimportowanych przez niestandardowy łącznik partnera

Za pomocą narzędzia [zbierania](content-search.md) elektronicznych materiałów dowodowych przeszukiwania zawartości w aplikacji Centrum zgodności platformy Microsoft 365 wyszukiwać elementy zaimportowane do skrzynek pocztowych w programie Microsoft 365 ze źródła danych innej firmy. Możesz utworzyć zapytanie, aby przeszukać wszystkie zaimportowane elementy danych innych firm, lub zapytanie wyszukuje określone elementy danych innych firm. Ponadto możesz utworzyć oparte na kwerendach zasady przechowywania lub oparte na kwerendach przechowywanie zbierania elektronicznych materiałów dowodowych w celu zachowania danych innych firm.
  
Aby uzyskać więcej informacji na temat współpracy z partnerem w celu importowania danych innych firm oraz listy typów danych innych firm, które można zaimportować do programu Microsoft 365, zobacz Współpraca z [partnerem](work-with-partner-to-archive-third-party-data.md) w celu archiwizowania danych innych firm w programie Office 365.

> [!IMPORTANT]
> Wskazówki w tym artykule dotyczą tylko danych innych firm, które zaimportowano przez niestandardowy łącznik partnera. Ten artykuł nie dotyczy danych innych firm, które są importowane za pomocą łączników danych innych [firm w Centrum](archiving-third-party-data.md#third-party-data-connectors) zgodności firmy Microsoft.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>Tworzenie kwerendy wyszukącej wszystkie dane innych firm

Aby wyszukać (lub umieścić w miejscu wstrzymywania) dowolny typ danych innych firm zaimportowanych do programu Office 365, `kind:externaldata` możesz użyć pary wartość właściwości wiadomości w polu słowa kluczowego do przeszukiwania zawartości lub podczas tworzenia hold'a opartego na kwerendzie. Aby na przykład wyszukać elementy zaimportowane z dowolnego źródła danych innej firmy i zawierające wyraz "contoso" we właściwości Temat importowanego elementu, można użyć następującego zapytania: 
  
```powershell
kind:externaldata AND subject:contoso
```

Poprzedni przykład zapytania słów kluczowych zawiera właściwość subject. Aby uzyskać listę innych właściwości elementów danych innych firm, które mogą być zawarte w zapytaniu słowa kluczowego, zobacz sekcję "Więcej informacji" w tece Współpraca z partnerem w celu archiwizowania danych innych firm w [programie Office 365](work-with-partner-to-archive-third-party-data.md#more-information).
  
Podczas tworzenia zapytań do wyszukiwania i przechowywania danych innych firm możesz także zawęzić wyniki wyszukiwania za pomocą warunków. Aby uzyskać więcej informacji na temat tworzenia zapytań przeszukiwania zawartości, zobacz Zapytania [słów kluczowych i warunki wyszukiwania dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>Tworzenie kwerendy w celu wyszukiwania określonych typów danych innych firm

Zamiast przeszukiwać wszystkie typy danych innych firm, możesz tworzyć zapytania, które wyszukują tylko określony typ danych innych firm, używając następującej właściwości komunikatu *: para* wartości w polu słowa kluczowego dla wyszukiwania zawartości:
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

Aby na przykład przeszukać dane serwisu Facebook zawierające wyraz "contoso" we właściwości Temat, użyj następującego zapytania:
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

W poniższej tabeli wymieniono typy danych innych firm, które można wyszukiwać,  `itemclass:` oraz wartość właściwości wiadomości, która umożliwia wyszukiwanie danych tego typu. W składni zapytania nie jest rozróżniana wielkość liter. 
  
|**Typ danych innej firmy**|**Wartość właściwości `itemclass:`**|
|:-----|:-----|
|AIM  <br/> | `ipm.externaldata.AIM*` <br/> |
|Idol amerykański  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|AOL z klientem przestawny  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|Apple Juice  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|Ares  <br/> | `ipm.externaldata.Ares*` <br/> |
|Axs Encrypted  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Osie Exchange  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|Lokalne archiwum osi  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|Symbol zastępczy osi  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Podpisane osie  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Bazaarvoice  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|Bearshare  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|Bit Jaka jest  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|Blackberry  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|Dzienniki połączeń BlackBerry  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|BlackBerry PIN  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry SMS  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|Bloomberg  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|Wiadomość bloomberga  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|Bloomberg Messaging  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|Box  <br/> | `ipm.externaldata.Box*` <br/> |
|Cisco IM &amp; Presence Server  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|Cisco Jabber  <br/> | `ipm.externaldata.Jabber*` <br/> |
|CipherCloud for Salesforce Chatter  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|Bezpośredni Połączenie  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|Facebook  <br/> | `ipm.externaldata.Facebook*` <br/> |
|FastTrack  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|FXConnect  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|Flickr  <br/> | `ipm.externaldata.Flickr*` <br/> |
|Historyjka  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|Google+  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|Google Talk  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|GoToMyPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|Hopster  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|IBM Connections  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|ICE Chat  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|Aby to zda  <br/> | `ipm.externaldata.Instagram*` <br/> |
|Instant Bloomberg  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|InvestEdge  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|IRC  <br/> | `ipm.externaldata.IRC*` <br/> |
|Jive  <br/> | `ipm.externaldata.Jive*` <br/> |
|JiveApiRetention  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|JXTA  <br/> | `ipm.externaldata.JXTA*` <br/> |
|LinkedIn  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|MFTP  <br/> | `ipm.externaldata.MFTP*` <br/> |
|Microsoft UC  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|Mind Align  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|Mobile Guard  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|MSN  <br/> | `ipm.externaldata.MSN*` <br/> |
|MySpace  <br/> | `ipm.externaldata.MySpace*` <br/> |
|NEONetwork  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Pivot  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Czat usługi Salesforce  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype dla firm  <br/> | `ipm.externaldata.Skype*` <br/> |
|Zapas czasu Enterprise siatki  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|SoftEther  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|Nago  <br/> | `ipm.externaldata.Symphony*` <br/> |
|Thomson Reuters  <br/> | `ipm.externaldata.Reuters*` <br/> |
| Thomson Reuters Eikon Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|Tor  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|Czat UBS  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|WinMX  <br/> | `ipm.externaldata.WinMX*` <br/> |
|Winny  <br/> | `ipm.externaldata.Winny*` <br/> |
|Yahoo!  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|YellowJacket  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
