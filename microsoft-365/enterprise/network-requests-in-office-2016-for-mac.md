---
title: Żądania sieciowe w pakiecie Office dla komputerów Mac
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: W tym artykule opisano punkty końcowe i adresy URL Office dla komputerów Mac, z którymi aplikacje próbują się skontaktować, oraz udostępniane usługi.
ms.openlocfilehash: 477225cf99ead3f5609c8082644293d4ac006603
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091132"
---
# <a name="network-requests-in-office-for-mac"></a>Żądania sieciowe w pakiecie Office dla komputerów Mac

Office dla komputerów Mac aplikacje zapewniają natywne środowisko aplikacji na platformie macOS. Każda aplikacja jest przeznaczona do pracy w różnych scenariuszach, w tym w stanach, gdy nie jest dostępny dostęp do sieci. Gdy maszyna jest połączona z siecią, aplikacje automatycznie łączą się z szeregiem usług internetowych, aby zapewnić ulepszone funkcje. W poniższych informacjach opisano punkty końcowe i adresy URL, z którymi aplikacje próbują się skontaktować, oraz podane usługi. Te informacje są przydatne podczas rozwiązywania problemów z konfiguracją sieci i ustawiania zasad dla serwerów proxy sieci. Szczegóły zawarte w tym artykule mają na celu uzupełnienie [artykułu Office 365 adresów URL i zakresów adresów](urls-and-ip-address-ranges.md), który zawiera punkty końcowe dla komputerów z systemem Microsoft Windows. O ile nie wspomniano, informacje zawarte w tym artykule dotyczą również Office 2019 r. dla komputerów Mac i Office 2016 dla komputerów Mac, które są dostępne jako jednorazowy zakup w sklepie detalicznym lub w ramach umowy licencjonowania zbiorowego. 

  
Większość tego artykułu to tabele z szczegółowymi adresami URL sieci, typami i opisami usług lub funkcji udostępnianych przez ten punkt końcowy. Każda z aplikacji Office może się różnić od użycia usługi i punktu końcowego. W poniższych tabelach zdefiniowano następujące aplikacje:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
Typ adresu URL jest zdefiniowany w następujący sposób:
  
- Temat pomocy technicznej: statyczny — adres URL jest zakodowany na stałe w aplikacji klienckiej.
    
- SS: Semi-Static — adres URL jest kodowany jako część strony internetowej lub przekierowania.
    
- CS: Config Service — adres URL jest zwracany w ramach usługi konfiguracji Office.

    
## <a name="office-for-mac-default-configuration"></a>Office dla komputerów Mac konfiguracji domyślnej

 **Instalacja i aktualizacje**
  
Następujące punkty końcowe sieci służą do pobierania programu instalacyjnego Office dla komputerów Mac z Content Delivery Network firmy Microsoft (CDN).
  
|**ADRES URL**|**Type**|**Opis**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Microsoft 365 link portalu instalacji do najnowszych pakietów instalacyjnych.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Lokalizacja pakietów instalacyjnych na Content Delivery Network.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Lokalizacja pakietów instalacyjnych na Content Delivery Network.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Punkt końcowy kontroli zarządzania dla usługi Microsoft AutoUpdate  <br/> |
   
 **Pierwsze uruchomienie aplikacji**
  
Podczas pierwszego uruchomienia aplikacja pakietu Office kontaktuje się z następującymi punktami końcowymi sieci. Te punkty końcowe zapewniają użytkownikom ulepszone funkcje Office, a adresy URL są kontaktowane niezależnie od typu licencji (w tym instalacji licencji zbiorczej).
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |Konfiguracja "Flighting" — umożliwia podświetlenie funkcji i eksperymentowanie.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test konfiguracji sieci "Flighting"  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test konfiguracji sieci "Flighting"  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Configuration Service — główna lista punktów końcowych usługi.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office pobieranie danych telemetrycznych reguł — informuje klienta o tym, jakie dane i zdarzenia mają zostać przekazane do usługi telemetrii.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |usługa telemetrii OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Telemetria Upload Raportowanie — zdarzenia "Heartbeart" i błędy występujące na kliencie są przekazywane do usługi telemetrii.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |usługa szablonów Office — udostępnia użytkownikom szablony dokumentów online.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office szablony — pliki do pobrania — Storage obrazów szablonów PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Konfiguracja sklepu dla aplikacji Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office wykaz usług integracji dokumentów (lista usług i punktów końcowych) i odnajdywanie obszaru macierzystego.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Zasoby dotyczące odnajdywania obszarów domowych w wersji 2 (15.40 lub nowszej)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Manifesty autoupdate firmy Microsoft — sprawdza, czy są dostępne aktualizacje  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Biblioteka Języka JavaScript w usłudze Microsoft Ajax  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Aplikacja Wikipedia dla Office konfiguracji i zasobów.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing mapowanie aplikacji na potrzeby konfiguracji Office i zasobów.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Osoby Graph aplikacji do konfiguracji Office i zasobów.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Co to jest nowa zawartość dla OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nowa zawartość dla OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Co nowego obrazy dla OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Usługa pomocy technicznej w aplikacji.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Usługa wykrywania konta e-mail.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |wykrywanie automatyczne Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook punkt końcowy usługi Microsoft 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Ikony Outlook dodatków.  <br/> |
   
> [!NOTE]
> Usługa konfiguracji Office działa jako usługa automatycznego odnajdywania dla wszystkich klientów Microsoft Office, a nie tylko dla komputerów Mac. Punkty końcowe zwracane w odpowiedzi są częściowo statyczne w tej zmianie jest bardzo rzadko, ale nadal możliwe. 
  
 **Logowanie**
  
Podczas logowania się do magazynu w chmurze kontaktują się następujące punkty końcowe sieci. W zależności od typu konta można skontaktować się z różnymi usługami. Przykład:
  
- **MSA: Konto Microsoft** — zwykle używane w scenariuszach konsumenckich i detalicznych 
    
- **OrgID: Konto organizacji** — zwykle używane w scenariuszach komercyjnych 
    
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |usługa autoryzacji Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |usługa logowania Microsoft 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft Account Login Service (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Pomocnik usługi logowania konta Microsoft (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Microsoft 365 znakowanie logowania (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Lokalizator dokumentów i miejsc Storage  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Ostatnio używana usługa dokumentów (MRU)  <br/> |
   
> [!NOTE]
> W przypadku licencji opartych na subskrypcji i sprzedaży detalicznej logowanie zarówno aktywuje produkt, jak i umożliwia dostęp do zasobów w chmurze, takich jak OneDrive. W przypadku instalacji licencji zbiorczej użytkownicy nadal są monitni o zalogowanie się (domyślnie), ale jest to wymagane tylko w celu uzyskania dostępu do zasobów w chmurze, ponieważ produkt jest już aktywowany. 
  
 **Aktywacja produktu**
  
Następujące punkty końcowe sieci dotyczą aktywacji subskrypcji Microsoft 365 i licencji detalicznej. W szczególności nie dotyczy to instalacji licencji zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |usługa licencjonowania Office  <br/> |
   
 **Co nowego**
  
Następujące punkty końcowe sieci dotyczą tylko subskrypcji Microsoft 365.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Co to jest nowa zawartość strony JSON.  <br/> |
   
 **Poszukiwanie**
  
Następujące punkty końcowe sieci dotyczą tylko subskrypcji Microsoft 365.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Usługa sieci Web dla badaczy  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Zawartość statyczna badacza  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Dostawca zawartości dla badaczy  <br/> |
   
 **Inteligentne wyszukiwanie**
  
Następujące punkty końcowe sieci dotyczą zarówno subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |usługa sieci Web Szczegółowe informacje  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |Biblioteka JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Obsługa biblioteki JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |dostawca zawartości Szczegółowe informacje  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |dostawca zawartości Szczegółowe informacje  <br/> |
   
 **Projektant programu PowerPoint**
  
Następujące punkty końcowe sieci dotyczą tylko subskrypcji Microsoft 365.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Usługa internetowa projektanta PowerPoint  <br/> |
   
 **Szybki start programu PowerPoint**
  
Następujące punkty końcowe sieci dotyczą tylko subskrypcji Microsoft 365.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint usługi internetowej Szybki start  <br/> |
   
 **Wyślij uśmiech/marszczyć brwi**
  
Następujące punkty końcowe sieci dotyczą zarówno subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Wyślij usługę uśmiechu  <br/> |
   
 **Skontaktuj się z pomocą techniczną**
  
Następujące punkty końcowe sieci dotyczą zarówno subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Skontaktuj się z pomocą techniczną  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Usługa pomocy technicznej w aplikacji  <br/> |
   
 **Zapisz jako plik PDF**
  
Następujące punkty końcowe sieci dotyczą zarówno subskrypcji Microsoft 365, jak i aktywacji licencji detalicznej/zbiorczej.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Usługa konwersji dokumentów programu Word (PDF)  <br/> |
   
 **Office Apps (dodatki)**
  
Następujące punkty końcowe sieci mają zastosowanie zarówno do aktywacji subskrypcji Microsoft 365, jak i licencji detalicznej/zbiorczej, gdy dodatki aplikacji Office są zaufane.
  
|**ADRES URL**|**Aplikacje**|**Type**|**Opis**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |konfiguracja magazynu aplikacja pakietu Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Zasoby aplikacji Wikipedii  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Mapowanie zasobów aplikacji  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Osoby Graph zasoby aplikacji  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |usługa przekierowania Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |biblioteki języka JavaScript Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Usługa telemetrii i raportowania dla aplikacji Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Biblioteka Języka JavaScript w usłudze Microsoft Ajax  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Biblioteka Języka JavaScript w usłudze Microsoft Ajax  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |biblioteki języka JavaScript Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Zasoby pomocy technicznej  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Zasoby pomocy technicznej  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Zasoby pomocy technicznej  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |Biblioteka Języka JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Raportowanie błędów  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Zasoby czcionek  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Usługa telemetrii  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Raportowanie telemetrii  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |biblioteka zasobów Microsoft Store  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Zasoby strony Wikipedii  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Zasoby multimediów w Wikipedii  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Ramka piaskownicy Wikipedii  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Szablony mapowania  <br/> |
   
 **Bezpieczne linki**
  
Następujący punkt końcowy sieci ma zastosowanie do wszystkich aplikacji Office tylko dla subskrypcji Microsoft 365.
  
|**ADRES URL**|**Type**|**Opis**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Usługa Microsoft Sejf Link  <br/> |
   
 **Raportowanie awarii**
  
Następujący punkt końcowy sieci ma zastosowanie do wszystkich aplikacji Office dla aktywacji subskrypcji Microsoft 365 i licencji detalicznej/zbiorczej. W przypadku nieoczekiwanego awarii procesu raport jest generowany i wysyłany do usługi Watson.
  
|**ADRES URL**|**Type**|**Opis**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Usługa Raportowanie błędów firmy Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |usługa Szczegółowe informacje współpracy Office  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Opcje zmniejszania liczby żądań sieciowych i ruchu

Domyślna konfiguracja Office dla komputerów Mac zapewnia najlepsze środowisko użytkownika, zarówno pod względem funkcjonalności, jak i aktualności maszyny. W niektórych scenariuszach można uniemożliwić aplikacjom kontaktowanie się z punktami końcowymi sieci. W tej sekcji omówiono opcje, aby to zrobić.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Wyłączanie Sign-In i Office Add-Ins w chmurze
  
Klienci korzystający z licencji zbiorczych mogą mieć ścisłe zasady dotyczące zapisywania dokumentów w magazynie opartym na chmurze. Następujące preferencje dla aplikacji można ustawić, aby wyłączyć logowanie MSA/OrgID i dostęp do Office dodatków.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Jeśli użytkownicy spróbują uzyskać dostęp do funkcji Sign-In, zobaczy błąd, że połączenie sieciowe nie istnieje. Ponieważ ta preferencja blokuje również aktywację produktu online, powinna być używana tylko w przypadku instalacji licencji zbiorczej. W szczególności użycie tej preferencji uniemożliwi aplikacjom Office uzyskiwanie dostępu do następujących punktów końcowych:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Wszystkie punkty końcowe wymienione w sekcji "Zaloguj się" powyżej.
    
- Wszystkie punkty końcowe wymienione w sekcji "Inteligentne wyszukiwanie" powyżej.
    
- Wszystkie punkty końcowe wymienione w sekcji "Aktywacja produktu" powyżej.
    
- Wszystkie punkty końcowe wymienione w sekcji "aplikacje Office (nazywane dodatkami)" powyżej.
    
Aby ponownie ustanowić pełną funkcjonalność dla użytkownika, ustaw preferencję "2" lub usuń ją.
  
> [!NOTE]
> Ta preferencja wymaga Office dla komputerów Mac kompilacji 15.25 [160726] lub nowszej. 
  
### <a name="telemetry"></a>Telemetria 
  
Office dla komputerów Mac wysyła informacje telemetryczne z powrotem do firmy Microsoft w regularnych odstępach czasu. Dane są przekazywane do punktu końcowego "Nexus". Dane telemetryczne ułatwiają zespołowi inżynieryjnemu ocenę kondycji i wszelkich nieoczekiwanych zachowań każdego aplikacja pakietu Office. Istnieją dwie kategorie danych telemetrycznych:
  
- **Puls** zawiera informacje o wersji i licencji. Te dane są wysyłane natychmiast po uruchomieniu aplikacji. 
    
- **Użycie** zawiera informacje o sposobie używania aplikacji i błędach nieśmiertelnych. Te dane są wysyłane co 60 minut. 
    
Firma Microsoft bardzo poważnie traktuje Twoją prywatność. Informacje o zasadach zbierania danych firmy Microsoft można przeczytać pod adresem [https://privacy.microsoft.com](https://privacy.microsoft.com). Aby uniemożliwić aplikacjom wysyłanie danych telemetrycznych "Użycie", można **dostosować preferencję SendAllTelemetryEnabled** . Preferencja dotyczy aplikacji i można ją ustawić za pośrednictwem profilów konfiguracji systemu macOS lub ręcznie z poziomu terminalu: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Dane telemetryczne pulsu są zawsze wysyłane i nie można ich wyłączyć.
  
### <a name="crash-reporting"></a>Raportowanie awarii
  
W przypadku wystąpienia błędu aplikacji krytycznej aplikacja nieoczekiwanie zakończy działanie i przekaże raport o awarii do usługi "Watson". Raport o awarii składa się ze stosu wywołań, który jest listą kroków, które aplikacja przetwarzała przed awarią. Te kroki pomagają zespołowi inżynieryjnemu zidentyfikować dokładną funkcję, która uległa awarii i dlaczego.
  
W niektórych przypadkach zawartość dokumentu spowoduje awarię aplikacji. Jeśli aplikacja zidentyfikuje dokument jako przyczynę, zapyta użytkownika, czy można również wysłać dokument wraz ze stosem wywołań. Użytkownicy mogą dokonać świadomego wyboru tego pytania. Administratorzy IT mogą mieć ścisłe wymagania dotyczące przesyłania dokumentów i podejmować decyzje w imieniu użytkownika, aby nigdy nie wysyłać dokumentów. Można ustawić następujące preferencje, aby uniemożliwić wysyłanie dokumentów i pominąć monit do użytkownika:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Jeśli **właściwość SendAllTelemetryEnabled** ma wartość **FALSE**, wszystkie raportowanie awarii dla tego procesu jest wyłączone. Aby włączyć raportowanie awarii bez wysyłania danych telemetrycznych użycia, można ustawić następujące preferencje: ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Aktualizacje
  
Firma Microsoft wydaje Office dla komputerów Mac aktualizacje w regularnych odstępach czasu (zazwyczaj raz w miesiącu). Zdecydowanie zachęcamy użytkowników i administratorów IT do zapewnienia aktualności maszyn w celu zapewnienia zainstalowania najnowszych poprawek zabezpieczeń. W przypadkach, gdy administratorzy IT chcą ściśle kontrolować aktualizacje maszyn i zarządzać nimi, można ustawić następujące preferencje, aby zapobiec automatycznemu wykrywaniu i oferowaniu aktualizacji produktów przez proces autoupdate:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blokowanie żądań za pomocą zapory/serwera proxy
  
Jeśli organizacja blokuje żądania adresów URL za pośrednictwem zapory lub serwera proxy, należy skonfigurować adresy URL wymienione w tym dokumencie jako dozwolone lub zablokować je z odpowiedzią 40X (np. 403 lub 404). Odpowiedź 40X umożliwi aplikacjom Office bezproblemowe zaakceptowanie niemożności uzyskania dostępu do zasobu i zapewni szybsze środowisko użytkownika, niż po prostu upuszczenie połączenia, co z kolei spowoduje ponowienie próby przez klienta.
  
Jeśli serwer proxy wymaga uwierzytelniania, do klienta zostanie zwrócona odpowiedź 407. Aby uzyskać najlepsze środowisko, upewnij się, że używasz Office dla komputerów Mac kompilacji w wersji 15.27 lub nowszej, ponieważ zawierają one konkretne poprawki do pracy z serwerami NTLM i Kerberos.
  
  
## <a name="see-also"></a>Zobacz też

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

