---
title: Żądania sieciowe w programie Office dla komputerów Mac
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: W tym artykule opisano, z którymi punktami końcowymi i adresami URL Office dla komputerów Mac są próbami sięgać aplikacje, oraz dostarczane przez nie usługi.
ms.openlocfilehash: 37071b0aaf9e6f172d99a10cb4a1506f1627ef03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984377"
---
# <a name="network-requests-in-office-for-mac"></a>Żądania sieciowe w programie Office dla komputerów Mac

Office dla komputerów Mac zapewniają natywne środowisko aplikacji na platformie macOS. Każda aplikacja została zaprojektowana do działania w różnych scenariuszach, w tym w stanach, w których nie ma dostępu do sieci. Gdy komputer jest połączony z siecią, aplikacje automatycznie łączą się z szeregami usług internetowych w celu zapewnienia rozszerzonych funkcji. Poniżej opisano, z którymi punktami końcowymi i adresami URL aplikacja próbuje się uzyskać, oraz dostarczane przez nie usługi. Te informacje są przydatne podczas rozwiązywania problemów z konfiguracją sieci i ustawiania zasad dla sieciowych serwerów proxy. Szczegółowe informacje w tym artykule są uzupełnieniem artykułu adres [URL](urls-and-ip-address-ranges.md) Office 365 zakresów adresów URL, który zawiera punkty końcowe dla komputerów z systemem Microsoft Windows. O ile nie zaznaczono, informacje zawarte w tym artykule dotyczą również programów Office 2019 dla komputerów Mac i Office 2016 dla komputerów Mac, które są dostępne w ramach zakupów detalicznych i w ramach umowy licencjonowania zbiorowego. 

  
Większość tego artykułu zawiera tabele z adresami URL sieci, typem i opisem usługi lub funkcji udostępnianej przez ten punkt końcowy. Każda z tych Office może różnić się w zakresie usługi i użycia punktu końcowego. W poniższych tabelach są zdefiniowane następujące aplikacje:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
Typ adresu URL jest zdefiniowany w następujący sposób:
  
- ST: Statyczny — adres URL jest mocno kodowany w aplikacji klienckiej.
    
- SS: Semi-Static — adres URL jest zakodowany jako część strony internetowej lub przekierowania.
    
- CS: Usługa konfiguracji — adres URL jest zwracany jako część usługi Office konfiguracji.

    
## <a name="office-for-mac-default-configuration"></a>Office dla komputerów Mac konfiguracji domyślnej

 **Instalacja i aktualizacje**
  
Następujące punkty końcowe sieci są używane do pobierania programu Office dla komputerów Mac sieciowego z witryny Microsoft Content Delivery Network (CDN).
  
|**ADRES URL**|**Type**|**Opis**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Microsoft 365 do usługi przesyłania dalej portalu instalacji do najnowszych pakietów instalacyjnych.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SZ  <br/> |Lokalizacja pakietów instalacyjnych na Content Delivery Network.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SZ  <br/> |Lokalizacja pakietów instalacyjnych na Content Delivery Network.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Punkt końcowy kontroli zarządzania dla programu Microsoft AutoUpdate  <br/> |
   
 **Uruchamianie aplikacji po raz pierwszy**
  
Podczas pierwszego uruchomienia aplikacji sieciowej następuje kontakt z następującymi punktami końcowymi aplikacja pakietu Office. Te punkty końcowe zapewniają użytkownikom ulepszone Office, a kontakt z adresami URL jest możliwy niezależnie od typu licencji (w tym instalacji w licencjonowaniu licencjonowanym).
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |Konfiguracja "flightingu" — pozwala na eksperymentowanie i zasypanie funkcji.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test konfiguracji sieci "dystrybucji testowej"  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test konfiguracji sieci "dystrybucji testowej"  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office konfiguracji — główna lista punktów końcowych usługi.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office telemetrii reguł — informuje klienta o tym, jakie dane i zdarzenia należy przekazać do usługi telemetrii.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote telemetrii  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office raportowania Upload telemetrii — "Heartbeart" i zdarzenia błędów występujące na kliencie są przekazywane do usługi telemetrii.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office szablonów — udostępnia użytkownikom szablony dokumentów w trybie online.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office pobierania szablonów — Storage obrazów szablonów PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Konfiguracja sklepu dla Office aplikacji.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office wykaz usług Integration Services dokumentu (lista usług i punktów końcowych) i odnajdowanie realiów domowych.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Zasoby dla odnajdowania realiów domowych w wersji 2 (15.40 i nowsze)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Manifesty programu Microsoft AutoUpdate — sprawdza, czy są dostępne aktualizacje  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SZ  <br/> |Biblioteka JavaScript programu Microsoft Ajax  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SZ  <br/> |Aplikacja Wikipedia dla Office i zasobów.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SZ  <br/> |Bing mapy dla Office i zasobów.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SZ  <br/> |People Graph app for Office configuration and resources.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Zawartość Co nowego dla OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nowa zawartość dla OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SZ  <br/> |Obrazy "Co nowego" dla OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Usługa pomocy technicznej w aplikacji.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Usługa wykrywania konta e-mail.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook wykrywania automatycznego  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook punkt końcowy usługi Microsoft 365 usługi.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Ikony Outlook dodatków.  <br/> |
   
> [!NOTE]
> Usługa Office konfiguracji działa jako usługa wykrywania automatycznego dla wszystkich klientów Microsoft Office, nie tylko dla komputerów Mac. Punkty końcowe zwracane w odpowiedzi są półstatyczne w tym przypadku, że zmiana jest bardzo rzadko, ale nadal możliwa. 
  
 **Logowanie**
  
Podczas logowania się do magazynu opartego na chmurze następuje kontakt z następującymi punktami końcowymi sieci. W zależności od typu konta może być kontakt z różnymi usługami. Przykład:
  
- **MSA: Konto Microsoft —** zwykle używane w scenariuszach detalicznych i indywidualnych 
    
- **OrgID: Konto organizacji —** zwykle używane w scenariuszach komercyjnych 
    
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows usługi autoryzacji  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 365 logowania (identyfikator organizacji)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Usługa logowania do konta Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Pomocnik usługi logowania do konta Microsoft (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SZ  <br/> |Microsoft 365 znakowania logowania (Identyfikator organizacji)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Document and Places Storage Locator  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Usługa dokumentów Ostatnio używane (MRU)  <br/> |
   
> [!NOTE]
> W przypadku licencji detalicznych i opartych na subskrypcji logowanie się zarówno aktywuje produkt, jak i umożliwia dostęp do zasobów chmurowych, takich jak OneDrive. W przypadku instalacji w licencji volume License użytkownicy nadal są monitowali o zalogowanie się (domyślnie), ale jest to wymagane tylko w celu uzyskania dostępu do zasobów w chmurze, ponieważ produkt został już aktywowany. 
  
 **Aktywacja produktu**
  
Poniższe punkty końcowe sieci dotyczą aktywacji Microsoft 365 subskrypcji i licencji detalicznej. W szczególności NIE dotyczy to instalacji w licencjonowaniu volume license.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office usługi licencjonowania  <br/> |
   
 **Zawartość Co nowego**
  
Poniższe punkty końcowe sieci dotyczą tylko Microsoft 365 subskrypcji.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SZ  <br/> |Zawartość strony JSON Co nowego.  <br/> |
   
 **Poszukiwanie**
  
Poniższe punkty końcowe sieci dotyczą tylko Microsoft 365 subskrypcji.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Usługa internetowa researchera  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Zawartość statyczna badacza  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Dostawca zawartości (Researcher Content Provider)  <br/> |
   
 **Inteligentne wyszukiwanie**
  
Poniższe punkty końcowe sieci dotyczą zarówno aktywacji subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Szczegółowe informacje sieci Web  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |Biblioteka JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Obsługa biblioteki kodu JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Szczegółowe informacje zawartości  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Szczegółowe informacje zawartości  <br/> |
   
 **Projektant programu PowerPoint**
  
Poniższe punkty końcowe sieci dotyczą tylko Microsoft 365 subskrypcji.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint usługi sieci Web Projektanta  <br/> |
   
 **Szybki start programu PowerPoint**
  
Poniższe punkty końcowe sieci dotyczą tylko Microsoft 365 subskrypcji.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint usługi sieci Web Szybki start  <br/> |
   
 **Wyślij uśmiech/pomówienie**
  
Poniższe punkty końcowe sieci dotyczą zarówno aktywacji subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Usługa Wyślij uśmiech  <br/> |
   
 **Skontaktuj się z pomocą techniczną**
  
Poniższe punkty końcowe sieci dotyczą zarówno aktywacji subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Skontaktuj się z pomocą techniczną  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Usługa pomocy technicznej w aplikacji  <br/> |
   
 **Zapisywanie w formacie PDF**
  
Poniższe punkty końcowe sieci dotyczą zarówno aktywacji subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Usługa konwersji dokumentów programu Word (PDF)  <br/> |
   
 **Office (dodatki)**
  
Poniższe punkty końcowe sieci dotyczą zarówno aktywacji subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej, gdy dodatki Office aplikacji są zaufane.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |aplikacja pakietu Office konfiguracji magazynu  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SZ  <br/> |Zasoby aplikacji Wikipedia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SZ  <br/> |Bing zasobów aplikacji Mapy  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SZ  <br/> |Zasoby Graph osób  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SZ  <br/> |Office przekierowywania  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SZ  <br/> |Office bibliotek języka JavaScript  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SZ  <br/> |Usługa raportowania i telemetrii Office aplikacji  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SZ  <br/> |Biblioteka JavaScript programu Microsoft Ajax  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SZ  <br/> |Biblioteka JavaScript programu Microsoft Ajax  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SZ  <br/> |Office bibliotek języka JavaScript  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SZ  <br/> |Zasoby pomocy technicznej  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SZ  <br/> |Zasoby pomocy technicznej  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SZ  <br/> |Zasoby pomocy technicznej  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SZ  <br/> |Biblioteka kodu JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SZ  <br/> |Raportowanie błędów  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SZ  <br/> |Zasoby czcionek  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SZ  <br/> |Usługa telemetrii  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SZ  <br/> |Raportowanie telemetrii  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SZ  <br/> |Microsoft Store zawartości  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SZ  <br/> |Zasoby strony Wikipedia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SZ  <br/> |Zasoby multimedialne Wikipedia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SZ  <br/> |Ramka piaskownicy aplikacji Wikipedia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SZ  <br/> |Szablony map  <br/> |
   
 **Bezpieczne linki**
  
Poniższy punkt końcowy sieci dotyczy wszystkich aplikacji Office tylko dla Microsoft 365 subskrypcji.
  
|**ADRES URL**|**Type**|**Opis**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Usługa Microsoft Sejf Link  <br/> |
   
 **Raportowanie awarii**
  
Poniższy punkt końcowy sieci dotyczy wszystkich aplikacji Office zarówno w przypadku aktywacji subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej. Gdy proces nieoczekiwanie ulega awarii, jest generowany raport, który jest wysyłany do usługi Watson.
  
|**ADRES URL**|**Type**|**Opis**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Usługa raportowania błędów firmie Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office Collaborative Szczegółowe informacje Service  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Opcje ograniczania ruchu i żądań sieciowych

Domyślna konfiguracja programu Office dla komputerów Mac zapewnia najlepsze środowisko użytkownika zarówno pod względem funkcji, jak i utrzymywania komputera na bieżąco. W niektórych scenariuszach możesz chcieć uniemożliwić aplikacjom kontaktowanie się z punktami końcowymi sieci. W tej sekcji omówiono dostępne opcje.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Wyłączanie funkcji cloud Sign-In i Office Add-Ins
  
Klienci korzystający z licencji licencjonowania woluminowego mogą mieć ścisłe zasady dotyczące zapisywania dokumentów w chmurze. Następującą preferencję dla aplikacji można skonfigurować tak, aby wyłączyć logowanie MSA/orgID oraz dostęp do Office dodatków.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Jeśli użytkownicy spróbują uzyskać dostęp do Sign-In sieci, zobaczą komunikat o błędzie, że nie ma połączenia sieciowego. Ponieważ ta preferencja blokuje również aktywację produktów w trybie online, powinna być używana tylko w przypadku instalacji w licencji zbiorczej. Zastosowanie tej preferencji uniemożliwi aplikacjom Office uzyskanie dostępu do następujących punktów końcowych:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Wszystkie punkty końcowe wymienione w sekcji "Logowanie" powyżej.
    
- Wszystkie punkty końcowe wymienione w sekcji "Inteligentne odnośniki" powyżej.
    
- Wszystkie punkty końcowe wymienione w sekcji "Aktywacja produktu" powyżej.
    
- Wszystkie punkty końcowe wymienione w sekcji "Office Apps (czyli dodatki)" powyżej.
    
Aby ponownie ustanowić pełną funkcjonalność dla użytkownika, ustaw dla niego preferencję "2" lub usuń ją.
  
> [!NOTE]
> Ta preferencja wymaga Office dla komputerów Mac kompilacji 15.25 [160726] lub nowszej. 
  
### <a name="telemetry"></a>Telemetria 
  
Office dla komputerów Mac wysyła informacje telemetryczne do firmy Microsoft w regularnych odstępach czasu. Dane są przekazywane do punktu końcowego "Nexus". Dane telemetryczne pomagają zespołowi inżynierów oceniać kondycję i wszelkie nieoczekiwane zachowania każdego aplikacja pakietu Office. Istnieją dwie kategorie telemetrii:
  
- **Puls zawiera** informacje o wersji i licencji. Te dane są wysyłane natychmiast po uruchomieniu aplikacji. 
    
- **Użycie** zawiera informacje dotyczące sposobu używania aplikacji oraz błędów nie krytycznego. Te dane są wysyłane co 60 minut. 
    
Firma Microsoft bardzo poważnie podejmuje swoją prywatność. Informacje o zasadach zbierania danych przez firmę Microsoft można znaleźć na stronie [https://privacy.microsoft.com](https://privacy.microsoft.com). Aby uniemożliwić aplikacjom wysyłanie telemetrii "Użycie", można dostosować preferencję **SendAllTelemetryEnabled** . Ta preferencja jest dla  per-aplikacji i można ją ustawić za pośrednictwem profilów konfiguracji systemu macOS lub ręcznie z terminalu: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Telemetria Puls jest wysyłana zawsze i nie można jej wyłączyć.
  
### <a name="crash-reporting"></a>Raportowanie awarii
  
W razie wystąpienia błędu krytycznego aplikacja nieoczekiwanie zakończy działanie i przekaże raport o awarii do usługi "Watson". Raport o awarii składa się ze stosu wywołań, który jest listą kroków przetwarzanych przez aplikację, które prowadzą do awarii. Te kroki ułatwiają zespołowi inżynierów ustalenie, która dokładnie funkcja zawiodła i dlaczego.
  
W niektórych przypadkach zawartość dokumentu powoduje awarię aplikacji. Jeśli aplikacja zidentyfikuje dokument jako przyczynę, zapyta użytkownika, czy wraz ze stosem wywołań może również wysłać dokument. Użytkownicy mogą podjąć świadomą decyzję w tej kwestii. Administratorzy IT mogą mieć ścisłe wymagania dotyczące przekazywania dokumentów i podjąć w imieniu użytkownika decyzję, że dokumenty nigdy nie będą wysyłane. Aby uniemożliwić wysyłanie dokumentów i pominąć monit dla użytkownika, można ustawić następującą preferencję:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Jeśli **dla ustawienia SendAllTelemetryEnabled** ustawiono wartość **FALSE**, całe raportowanie awarii dla tego procesu jest wyłączone. Aby włączyć raportowanie awarii bez wysyłania telemetrii użycia, można ustawić następującą preferencję: ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Aktualizacje
  
Firma Microsoft wydaje Office dla komputerów Mac w regularnych odstępach czasu (zwykle raz na miesiąc). Zdecydowanie zaleca się, aby użytkownicy i administratorzy IT dbali o aktualizację komputerów w celu zapewnienia, że są zainstalowane najnowsze poprawki zabezpieczeń. W przypadkach, gdy administratorzy IT chcą ściśle kontrolować aktualizacje komputera i zarządzać nimi, można ustawić następującą preferencję, aby uniemożliwić procesowi AutoUpdate automatyczne wykrywanie i oferowanie aktualizacji produktu:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blokowanie żądań za pomocą zapory/serwera proxy
  
Jeśli Twoja organizacja blokuje żądania adresów URL za pośrednictwem zapory lub serwera proxy, skonfiguruj adresy URL wymienione w tym dokumencie jako dozwolone lub zablokowane z odpowiedzią 40X (np. 403 lub 404). Odpowiedź 40X pozwoli aplikacjom programu Office bez problemów zaakceptować brak dostępu do zasobu i zapewni szybsze środowisko użytkownika niż po prostu upuszczenie połączenia, co z kolei spowoduje, że klient spróbuje ponownie.
  
Jeśli serwer proxy wymaga uwierzytelniania, do klienta zostanie zwrócona odpowiedź 407. Aby uzyskać najlepsze środowisko pracy, upewnij się, że używasz kompilacji Office dla komputerów Mac 15.27 lub nowszej, ponieważ zawierają one konkretne poprawki dotyczące pracy z serwerami NTLM i Kerberos.
  
  
## <a name="see-also"></a>Zobacz też

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

