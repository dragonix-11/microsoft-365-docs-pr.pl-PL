---
title: Szczegółowe właściwości w dzienniku inspekcji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- BCS160
- MET150
ms.assetid: ce004100-9e7f-443e-942b-9b04098fcfc3
description: Ten artykuł zawiera opisy dodatkowych właściwości uwzględnianych podczas eksportowania wyników do Office 365 dziennika inspekcji.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1293cdda6ae99fc64b331b7e10cf827c62504456
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2022
ms.locfileid: "63015796"
---
# <a name="detailed-properties-in-the-audit-log"></a>Szczegółowe właściwości w dzienniku inspekcji

Podczas eksportowania wyników przeszukiwania dziennika inspekcji z Centrum zgodności platformy Microsoft 365 można pobrać wszystkie wyniki spełniające kryteria wyszukiwania. W tym celu wybierz pozycję **Eksportuj wyniki Pobierz** \> **wszystkie** wyniki na stronie **Przeszukiwanie dziennika inspekcji** . Aby uzyskać więcej informacji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).
  
 W przypadku eksportowania wszystkich wyników przeszukiwania dziennika inspekcji nieprzetworzone dane z ujednoliconego dziennika inspekcji są kopiowane do pliku w formacie wartości rozdzielanych przecinkami (CSV) pobieranego na komputer lokalny. Ten plik zawiera dodatkowe informacje z każdego rekordu inspekcji w kolumnie **o nazwie Dane inspekcji**. Ta kolumna zawiera właściwość wielowymiarową dla wielu właściwości z rekordu dziennika inspekcji. Poszczególne pary **właściwości: wartości** w tej właściwości wielowymiarowej są rozdzielane przecinkami. 
  
W poniższej tabeli opisano właściwości, które są uwzględniane (w zależności od usługi, w której **występuje zdarzenie)** w kolumnie dane inspekcji o wielu właściwościach. Nazwa **Office 365, która zawiera tę** kolumnę właściwości, wskazuje usługę i typ działania (użytkownika lub administratora), który zawiera tę właściwość. Aby uzyskać bardziej szczegółowe informacje o tych właściwościach lub właściwościach, które mogą nie zostać wymienione w tym temacie, zobacz Schemat [interfejsu API działań zarządzania](/office/office-365-management-api/office-365-management-activity-api-schema).
  
> [!TIP]
> Za pomocą funkcji przekształcania JSON w dodatku Power Query w programie Excel można podzielić kolumnę **Dane** inspekcji na wiele kolumn, dzięki czemu każda właściwość ma własną kolumnę. Umożliwia to sortowanie i filtrowanie według co najmniej jednej z tych właściwości. Aby dowiedzieć się, jak to zrobić, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md). 
  
|**Właściwość**|**Opis**|**Microsoft 365 usługi, która ma tę właściwość**|
|:-----|:-----|:-----|
|Actor|Użytkownik lub konto usługi, które wykonało akcję.|Azure Active Directory|
|AddOnName|Nazwa dodatku, który został dodany, usunięty lub zaktualizowany w zespole. Typem dodatków w programie Microsoft Teams jest bot, łącznik lub karta.|Microsoft Teams|
|AddOnType|Typ dodatku, który został dodany, usunięty lub zaktualizowany w zespole. Następujące wartości wskazują typ dodatku.  <br/> **1** . Wskazuje bota.<br/> **2** — wskazuje łącznik.<br/> **3** — wskazuje kartę.|Microsoft Teams|
|AzureActiveDirectoryEventType (TypsventType usługi AzureActiveDirectoryEventType)|Typ zdarzenia Azure Active Directory. Następujące wartości wskazują typ zdarzenia.  <br/> **0** — oznacza zdarzenie logowania konta.<br/> **1** . Oznacza zdarzenie zabezpieczeń aplikacji platformy Azure.|Azure Active Directory|
|ChannelGuid|Identyfikator kanału Microsoft Teams. Zespół, w którym znajduje się kanał, jest oznaczony **właściwościami TeamName** i **TeamGuid** .|Microsoft Teams|
|ChannelName|Nazwa kanału Microsoft Teams. Zespół, w którym znajduje się kanał, jest oznaczony **właściwościami TeamName** i **TeamGuid** .|Microsoft Teams|
|Klient|Urządzenie klienckie, system operacyjny urządzenia i przeglądarka urządzeń użyte podczas zdarzenia logowania (na przykład Nokia Lumia 920; Windows Phone 8; IE Mobile 11).|Azure Active Directory|
|ClientInfoString|Informacje o kliencie poczty e-mail użytym do wykonania operacji, takie jak wersja przeglądarki, Outlook i informacje o urządzeniu przenośnym|Exchange (aktywność skrzynki pocztowej)|
|ClientIP (ClientIP)|Adres IP urządzenia używanego w czasie rejestrowanego działania. Adres IP jest wyświetlany w formacie adresu IPv4 lub IPv6.<br/><br/> W przypadku niektórych usług wartością wyświetlaną w tej właściwości może być adres IP zaufanej aplikacji (na przykład aplikacji Office w sieci Web) dzwoniących do usługi w imieniu użytkownika, a nie adres IP urządzenia używanego przez osobę, która wykonała dane działanie. <br/><br/>Ponadto w przypadku działań administratora (lub działań wykonywanych przez konto systemowe) związanych ze zdarzeniami Azure Active Directory adres IP nie jest rejestrowany, a wartość właściwości ClientIP to `null`. |Azure Active Directory, Exchange, SharePoint|
|CreationTime|Data i godzina wykonania działania przez użytkownika w uniwersalnym czasie koordynowaym (UTC).|Wszystkie|
|DestinationFileExtension (Extension pliku docelowego)|Rozszerzenie pliku, który został skopiowany lub przeniesiony. Ta właściwość jest wyświetlana tylko w przypadku działań użytkownika FileCopied i FileMoved.|SharePoint|
|DestinationFileName (Nazwa pliku docelowego)|Nazwa pliku, który został skopiowany lub przeniesiony. Ta właściwość jest wyświetlana tylko w przypadku akcji FileCopied i FileMoved.|SharePoint|
|DestinationRelativeUrl (DocelowyrelativeUrl)|Adres URL folderu docelowego, do którego został skopiowany lub przeniesiony plik. Kombinacja wartości właściwości **SiteURL**, **DestinationRelativeURL** i **DestinationFileName** jest taka sama jak wartość właściwości **ObjectID** i wskazuje pełną nazwę i ścieżkę skopiowanego pliku. Ta właściwość jest wyświetlana tylko w przypadku działań użytkownika FileCopied i FileMoved.|SharePoint|
|EventSource|Wskazuje, że zdarzenie wystąpiło w SharePoint. Dopuszczalne wartości to **SharePoint** **ObjectModel**.|SharePoint|
|ExternalAccess (Dostęp zewnętrzny)|Na Exchange administratora określa, czy polecenie cmdlet zostało uruchomione przez użytkownika w organizacji, przez pracowników centrum danych firmy Microsoft lub konto usługi centrum danych, czy przez administratora delegowanego. Wartość **False oznacza** , że polecenie cmdlet zostało uruchomione przez osobę z Twojej organizacji. Wartość **Prawda oznacza** , że polecenie cmdlet zostało uruchomione przez pracowników centrum danych, konto usługi centrum danych lub administratora delegowanego.  <br/> Na Exchange skrzynki pocztowej określa, czy użytkownik spoza organizacji uzyskał do niej dostęp.|Exchange|
|ExtendedProperties (Właściwości rozszerzone)|Właściwości rozszerzone dla zdarzenia Azure Active Directory.|Azure Active Directory|
|Identyfikator|Identyfikator wpisu w raporcie. Identyfikator jednoznacznie określa wpis w raporcie.|Wszystkie|
|InternalLogonType (Wewnętrzny typlogonu)|Zarezerwowane do użytku wewnętrznego.|Exchange (aktywność skrzynki pocztowej)|
|ItemType (Typ elementu)|Typ obiektu, do którego uzyskano dostęp lub który został zmodyfikowany. Dopuszczalne wartości to **: Plik**, **Folder**, **Sieć Web**, **Witryna**, **Dzierżawa** i **Biblioteki Dokumentów**.|SharePoint|
|LoginStatus (Statystyka logowania)|Identyfikuje błędy logowania, które mogły wystąpić.|Azure Active Directory|
|LogonType (Typ logowania)|Typ dostępu do skrzynki pocztowej. Następujące wartości wskazują typ użytkownika, który uzyskał dostęp do skrzynki pocztowej.  <br/><br/> **0** — wskazuje właściciela skrzynki pocztowej.<br/> **1** . Wskazuje administratora.<br/> **2** — wskazuje pełnomocnika. <br/>**3** . Wskazuje usługę transportu w centrum danych firmy Microsoft.<br/> **4** . Wskazuje konto usługi w centrum danych firmy Microsoft. <br/>**6** . Wskazuje administratora delegowanego.|Exchange (aktywność skrzynki pocztowej)|
|MailboxGuid|Identyfikator EXCHANGE guid skrzynki pocztowej, do której uzyskano dostęp.|Exchange (aktywność skrzynki pocztowej)|
|MailboxOwnerUPN (Właściciel Skrzynki pocztowej)|Adres e-mail osoby, do której uzyskano dostęp do skrzynki pocztowej.|Exchange (aktywność skrzynki pocztowej)|
|Członkowie|Lista użytkowników dodanych lub usuniętych z zespołu. Następujące wartości wskazują typ roli przypisany do użytkownika.  <br/><br/> **1** — wskazuje rolę Właściciel.<br/> **2** — wskazuje rolę Członek.<br/> **3** — rola Gość. <br/><br/>Właściwość Członkowie zawiera również nazwę organizacji i adres e-mail członka.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|Właściwość jest uwzględniana w przypadku zdarzeń administratora, takich jak dodanie użytkownika jako członka witryny lub grupy administratorów zbioru witryn. Zawiera nazwę zmodyfikowanej właściwości (na przykład grupa Administrator witryny), nową wartość zmodyfikowanej właściwości (na przykład nazwę użytkownika dodanego jako administrator witryny) oraz poprzednią wartość zmodyfikowanego obiektu.|Wszystkie (działania administratorów)|
|ObjectId|Na Exchange inspekcji administratora jest to nazwa obiektu zmodyfikowanego przez polecenie cmdlet.  <br/> Na SharePoint działania, pełny adres URL pliku lub folderu, do którego uzyskał dostęp użytkownik.  <br/> W przypadku działań usługi Azure AD jest to nazwa zmodyfikowanego konta użytkownika.|Wszystkie|
|Operacja|Nazwa działania użytkownika lub administratora. Wartość tej właściwości odpowiada wartości wybranej z listy **rozwijanej** Działania. Jeśli **zaznaczono opcję Pokaż wyniki dla wszystkich** działań, raport będzie zawierał wpisy dotyczące wszystkich działań użytkowników i administratorów we wszystkich usługach. Aby uzyskać opis działań/operacji rejestrowanych w dzienniku inspekcji, zobacz kartę Rejestrowane działania w obszarze  Przeszukiwanie dziennika inspekcji w [Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> W Exchange administratorów ta właściwość określa nazwę uruchomionego polecenia cmdlet.|Wszystkie|
|OrganizationId|Identyfikator GUID organizacji.|Wszystkie|
|Ścieżka|Nazwa folderu skrzynki pocztowej zawierającego wiadomość, do której uzyskano dostęp. Ta właściwość określa również folder, w którym utworzono wiadomość, lub do którego została skopiowana/przeniesiona.|Exchange (aktywność skrzynki pocztowej)|
|Parametry|Na Exchange administratorów nazwa i wartość dla wszystkich parametrów użytych z poleceniem cmdlet wskazanym we właściwości Operation.|Exchange (działania administratorów)|
|RecordType (Typ rekordu)|Typ operacji wskazywanej przez rekord. Ta właściwość wskazuje usługę lub funkcję, w przypadku których operacja została wyzwolona. Aby uzyskać listę typów rekordów i odpowiadającą im wartość WYLIM (która jest wartością wyświetlaną we właściwości **RecordType** (Typ Rekordu) w rekordzie inspekcji), zobacz Typ rekordu [dziennika inspekcji](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).| 
|ResultStatus (Statystyka wyników)|Wskazuje, czy akcja (określona we właściwości **Operation** ) powiodła się, czy nie.  <br/> W Exchange administratora wartość to **Prawda** (pomyślnie) lub **Fałsz** (niepowodzenie).|Wszystkie  <br/>|
|SecurityComplianceCenterEventType (Typotypu rozwiązania SecurityComplianceCenter)|Oznacza, że działanie było zdarzeniem Centrum zgodności platformy Microsoft 365 zdarzenia. W przypadku wszystkich działań w Centrum zgodności ta właściwość będzie mieć wartość **0** .|Centrum & zabezpieczeń|
|SharingType|Typ uprawnień udostępniania przypisanych do użytkownika, mu udostępniono zasób. Ten użytkownik jest identyfikowany we właściwości **UserSharedWith** .|SharePoint|
|Witryna|Identyfikator GUID witryny zawierającej plik lub folder, do którego uzyskał dostęp użytkownik.|SharePoint|
|SiteUrl|Adres URL witryny zawierającej plik lub folder, do którego uzyskał dostęp użytkownik.|SharePoint|
|SourceFileExtension (Extension pliku źródłowego)|Rozszerzenie pliku, do którego uzyskał dostęp użytkownik. Jeśli obiektem, do którego uzyskano dostęp, jest folder, ta właściwość jest pusta.|SharePoint|
|SourceFileName (Nazwa pliku źródłowego)|Nazwa pliku lub folderu, do którego uzyskał dostęp użytkownik.|SharePoint|
|SourceRelativeUrl|Adres URL folderu zawierającego plik, do którego uzyskał dostęp użytkownik. Kombinacja wartości właściwości **SiteURL**, **SourceRelativeURL** i **SourceFileName** jest taka sama jak wartość właściwości **ObjectID** i wskazuje pełną nazwę i ścieżkę pliku, do którego uzyskał dostęp użytkownik.|SharePoint|
|Temat|Wiersz tematu wiadomości, do której uzyskano dostęp.|Exchange (aktywność skrzynki pocztowej)|
|TabType| Typ karty dodany, usunięty lub zaktualizowany w zespole. Możliwe wartości tej właściwości są takie:  <br/><br/> **Excel —** karta Excel.  <br/> **Rozszerzenie** — wszystkie aplikacje innych firm i innych firm. takie jak Plan zajęć, VSTS i Forms.  <br/> **Notatki** — OneNote karcie.  <br/> **Pdfpin** — karta PDF.  <br/> **Powerbi** — karta Power BI zaawansowane.  <br/> **Powerpointpin** — karta PowerPoint zaawansowanej.  <br/> **SharePointfiles** — karta SharePoint plikach.  <br/> **Strona sieci** Web — przypięta karta witryny sieci Web.  <br/> **Wiki-tab** — karta typu wiki.  <br/> **Wordpin** — karta Word.|Microsoft Teams|
|Target (Element docelowy)|Użytkownik, dla których wykonano dane działanie (wskazane przez właściwość **Operation** ). Na przykład jeśli gość został dodany do SharePoint lub do zespołu Microsoft, ten użytkownik zostałby wymieniony w tej właściwości.|Azure Active Directory|
|TeamGuid|Identyfikator zespołu w Microsoft Teams.|Microsoft Teams|
|TeamName|Nazwa zespołu w Microsoft Teams.|Microsoft Teams|
|UserAgent (Agent użytkownika)|Informacje o przeglądarce użytkownika. Te informacje są udostępniane przez przeglądarkę.|SharePoint|
|UserDomain (Domena użytkownika)|Informacje dotyczące tożsamości organizacji dzierżawy użytkownika, który wykonał działanie (działanie).|Azure Active Directory|
|UserId|Użytkownik, który wykonał działanie (wskazane przez właściwość **Operation** ), w wyniku którego zarejestrowano rekord. Dziennik inspekcji zawiera również rekordy inspekcji dotyczące działań wykonywanych przez konta systemowe (takie jak SHAREPOINT\system lub NT AUTHORITY\SYSTEM). Inną wspólną wartością właściwości UserId jest app@sharepoint. Oznacza to, że "użytkownik", który wykonał dane działanie, był aplikacją mającą uprawnienia wymagane w programie SharePoint do wykonywania akcji dla całej organizacji (takich jak wyszukiwanie w witrynie programu SharePoint lub na koncie programu OneDrive) w imieniu użytkownika, administratora lub usługi. <br/><br/>Więcej informacji można znaleźć w następujących artykułach:<br/> [Użytkownik programu AppSharePoint\@ w rekordach inspekcji](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records)<br/> lub <br/>[Konta systemowe w Exchange inspekcji skrzynki pocztowej](search-the-audit-log-in-security-and-compliance.md#system-accounts-in-exchange-mailbox-audit-records). |Wszystkie|
|UserKey (Klucz użytkownika)|Alternatywny identyfikator użytkownika wskazanego przez właściwość **UserID** . Na przykład w przypadku wydarzeń wykonywanych przez użytkowników w programie SharePoint ta właściwość jest wypełniona identyfikatorem PUID. Ta właściwość może także określać tę samą wartość co właściwość **UserID** w przypadku zdarzeń w innych usługach i zdarzeń wykonywanych przez konta systemowe.|Wszystkie|
|UserSharedWith|Użytkownik, dla których udostępniono zasób. Ta właściwość jest uwzględniana, jeśli wartość właściwości **Operation** to **SharingSet**. Ten użytkownik jest również wymieniony w kolumnie **Udostępnione** dla w raporcie.|SharePoint|
|UserType (Typ użytkownika)|Typ użytkownika, który wykonał operację. Następujące wartości wskazują typ użytkownika. <br/> <br/> **0** — zwykły użytkownik. <br/>**2** — Administrator w Twojej Microsoft 365 organizacji.<sup> 1</sup> <br/>**3** . Administrator centrum danych firmy Microsoft lub konto systemowe centrum danych. <br/>**4** . Konto systemowe. <br/>**5** . Aplikacja. <br/>**6** . Podmiot zabezpieczeń usługi.<br/>**7** . Zasady niestandardowe.<br/>**8** . Zasady systemowe.|Wszystkie|
|Wersja|Numer wersji zarejestrowanego działania (wskazanego przez właściwość **Operation** ).|Wszystkie|
|Obciążenie pracą|Usługa Microsoft 365, w której miało miejsce działanie.|Wszystkie|
||||

> [!NOTE]
><sup>1</sup> W Azure Active Directory związanych z zdarzeniami związanymi z inspekcją wartość dla administratora nie jest używana w rekordzie inspekcji. Rekordy inspekcji działań wykonywanych przez administratorów wskazują, że zwykły użytkownik (na przykład **UserType: 0**) wykonał dane działanie. Właściwość **UserID** określa osobę (zwykłego użytkownika lub administratora), która wykonała dane działanie.
