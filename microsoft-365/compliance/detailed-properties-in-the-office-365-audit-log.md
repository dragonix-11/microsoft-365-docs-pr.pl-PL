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
description: Ten artykuł zawiera opisy dodatkowych właściwości uwzględnionych podczas eksportowania wyników dla rekordu dziennika inspekcji Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2342a64deaa2787e534a09b3d874ed3795d82ea8
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996223"
---
# <a name="detailed-properties-in-the-audit-log"></a>Szczegółowe właściwości w dzienniku inspekcji

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Podczas eksportowania wyników wyszukiwania dziennika inspekcji z portalu zgodności usługi Microsoft Purview możesz pobrać wszystkie wyniki spełniające kryteria wyszukiwania. Aby to zrobić, wybierz pozycję **Eksportuj wyniki** \> **Pobierz wszystkie wyniki** na stronie **przeszukiwania dziennika inspekcji** . Aby uzyskać więcej informacji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).
  
 Podczas eksportowania wszystkich wyników wyszukiwania dziennika inspekcji nieprzetworzone dane z ujednoliconego dziennika inspekcji są kopiowane do pliku wartości rozdzielanej przecinkami (CSV), który jest pobierany na komputer lokalny. Ten plik zawiera dodatkowe informacje z każdego rekordu inspekcji w kolumnie o nazwie **AuditData**. Ta kolumna zawiera właściwość wielowartościową dla wielu właściwości z rekordu dziennika inspekcji. Każda z **właściwości: pary wartości** w tej właściwości wielowartościowej są oddzielone przecinkami. 
  
W poniższej tabeli opisano właściwości, które są uwzględniane (w zależności od usługi, w której występuje zdarzenie) w wielowłaściwej kolumnie **AuditData** . **Usługa Office 365, która ma tę** kolumnę właściwości, wskazuje usługę i typ działania (użytkownika lub administratora), który zawiera właściwość. Aby uzyskać bardziej szczegółowe informacje na temat tych właściwości lub właściwości, które mogą nie być wymienione w tym temacie, zobacz [Schemat interfejsu API działania zarządzania](/office/office-365-management-api/office-365-management-activity-api-schema).
  
> [!TIP]
> Za pomocą funkcji przekształcania JSON w Power Query w Excel można podzielić kolumnę **AuditData** na wiele kolumn, aby każda właściwość zawierała własną kolumnę. Umożliwia to sortowanie i filtrowanie co najmniej jednej z tych właściwości. Aby dowiedzieć się, jak to zrobić, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md). 
  
|**Właściwość**|**Opis**|**usługa Microsoft 365, która ma tę właściwość**|
|:-----|:-----|:-----|
|Aktor|Konto użytkownika lub usługi, które wykonało akcję.|Azure Active Directory|
|AddOnName|Nazwa dodatku, który został dodany, usunięty lub zaktualizowany w zespole. Typ dodatków w Microsoft Teams to bot, łącznik lub karta.|Microsoft Teams|
|AddOnType|Typ dodatku, który został dodany, usunięty lub zaktualizowany w zespole. Następujące wartości wskazują typ dodatku.  <br/> **1** — wskazuje bota.<br/> **2** — wskazuje łącznik.<br/> **3** — wskazuje kartę.|Microsoft Teams|
|AzureActiveDirectoryEventType|Typ zdarzenia Azure Active Directory. Następujące wartości wskazują typ zdarzenia.  <br/> **0** — wskazuje zdarzenie logowania do konta.<br/> **1** — wskazuje zdarzenie zabezpieczeń aplikacji platformy Azure.|Azure Active Directory|
|ChannelGuid|Identyfikator kanału Microsoft Teams. Zespół, w których znajduje się kanał, jest identyfikowany przez właściwości **TeamName** i **TeamGuid** .|Microsoft Teams|
|Channelname|Nazwa kanału Microsoft Teams. Zespół, w których znajduje się kanał, jest identyfikowany przez właściwości **TeamName** i **TeamGuid** .|Microsoft Teams|
|Klient|Urządzenie klienckie, system operacyjny urządzenia i przeglądarka urządzenia używane na potrzeby zdarzenia logowania (na przykład Nokia Lumia 920; Windows Phone 8; IE Mobile 11).|Azure Active Directory|
|ClientInfoString|Informacje o kliencie poczty e-mail, który został użyty do wykonania operacji, takie jak wersja przeglądarki, wersja Outlook i informacje o urządzeniu przenośnym|Exchange (działanie skrzynki pocztowej)|
|ClientIP|Adres IP urządzenia, które było używane podczas rejestrowania działania. Adres IP jest wyświetlany w formacie adresu IPv4 lub IPv6.<br/><br/> W przypadku niektórych usług wartością wyświetlaną w tej właściwości może być adres IP zaufanej aplikacji (na przykład Office w sieci Web aplikacji) wywołujący do usługi w imieniu użytkownika, a nie adres IP urządzenia używanego przez osobę, która wykonała działanie. <br/><br/>Ponadto w przypadku działania administratora (lub działania wykonywanego przez konto systemowe) dla zdarzeń związanych z Azure Active Directory adres IP nie jest rejestrowany, a wartość właściwości ClientIP to `null`. |Azure Active Directory, Exchange, SharePoint|
|CreationTime|Data i godzina w uniwersalnym czasie koordynowanym (UTC), kiedy użytkownik wykonał działanie.|Wszystkie|
|DestinationFileExtension|Rozszerzenie pliku skopiowanego lub przeniesionego. Ta właściwość jest wyświetlana tylko dla działań użytkownika FileCopied i FileMoved.|SharePoint|
|Destinationfilename|Nazwa pliku jest kopiowana lub przenoszona. Ta właściwość jest wyświetlana tylko dla akcji FileCopied i FileMoved.|SharePoint|
|DestinationRelativeUrl|Adres URL folderu docelowego, w którym plik jest kopiowany lub przenoszony. Kombinacja wartości właściwości **SiteURL**, **DestinationRelativeURL** i **DestinationFileName** jest taka sama jak wartość właściwości **ObjectID** , która jest pełną nazwą ścieżki skopiowanego pliku. Ta właściwość jest wyświetlana tylko dla działań użytkownika FileCopied i FileMoved.|SharePoint|
|Eventsource|Określa, że zdarzenie miało miejsce w SharePoint. Możliwe wartości to **SharePoint** i **ObjectModel**.|SharePoint|
|ExternalAccess|W przypadku Exchange działania administratora określa, czy polecenie cmdlet było uruchamiane przez użytkownika w organizacji, przez personel centrum danych firmy Microsoft, konto usługi centrum danych, czy przez administratora delegowanego. Wartość **False** wskazuje, że polecenie cmdlet zostało uruchomione przez kogoś w organizacji. Wartość **True** wskazuje, że polecenie cmdlet zostało uruchomione przez personel centrum danych, konto usługi centrum danych lub administratora delegowanego.  <br/> W przypadku Exchange działania skrzynki pocztowej określa, czy do skrzynki pocztowej uzyskiwał dostęp użytkownik spoza organizacji.|Exchange|
|Extendedproperties|Właściwości rozszerzone zdarzenia Azure Active Directory.|Azure Active Directory|
|ID|Identyfikator wpisu raportu. Identyfikator jednoznacznie identyfikuje wpis raportu.|Wszystkie|
|InternalLogonType|Zarezerwowane do użytku wewnętrznego.|Exchange (działanie skrzynki pocztowej)|
|Itemtype|Typ obiektu, do których uzyskano dostęp lub został zmodyfikowany. Możliwe wartości to **Plik**, **Folder**, **Sieć Web**, **Witryna**, **Dzierżawa** i **DocumentLibrary**.|SharePoint|
|Loginstatus|Identyfikuje błędy logowania, które mogły wystąpić.|Azure Active Directory|
|LogonType|Typ dostępu do skrzynki pocztowej. Następujące wartości wskazują typ użytkownika, który uzyskał dostęp do skrzynki pocztowej.  <br/><br/> **0** — wskazuje właściciela skrzynki pocztowej.<br/> **1** — wskazuje administratora.<br/> **2** — wskazuje delegata. <br/>**3** — wskazuje usługę transportu w centrum danych firmy Microsoft.<br/> **4** — wskazuje konto usługi w centrum danych firmy Microsoft. <br/>**6** — wskazuje administratora delegowanego.|Exchange (działanie skrzynki pocztowej)|
|Skrzynka pocztowaGuid|Identyfikator GUID Exchange skrzynki pocztowej, do których uzyskano dostęp.|Exchange (działanie skrzynki pocztowej)|
|MailboxOwnerUPN|Adres e-mail osoby, która jest właścicielem skrzynki pocztowej, do której uzyskano dostęp.|Exchange (działanie skrzynki pocztowej)|
|Członków|Wyświetla listę użytkowników, którzy zostali dodana lub usunięta z zespołu. Następujące wartości wskazują typ roli przypisany do użytkownika.  <br/><br/> **1** — wskazuje rolę Właściciela.<br/> **2** — wskazuje rolę członka.<br/> **3** — wskazuje rolę gościa. <br/><br/>Właściwość Członkowie zawiera również nazwę organizacji i adres e-mail członka.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|Właściwość jest uwzględniana w przypadku zdarzeń administratora, takich jak dodawanie użytkownika jako członka witryny lub grupy administratorów zbioru witryn. Właściwość zawiera nazwę właściwości, która została zmodyfikowana (na przykład grupa Administrator witryny) nową wartość zmodyfikowanej właściwości (na przykład użytkownika, który został dodany jako administrator witryny, oraz poprzednią wartość zmodyfikowanego obiektu.|Wszystkie (działanie administratora)|
|Objectid|W przypadku rejestrowania inspekcji Exchange administratora nazwa obiektu, który został zmodyfikowany przez polecenie cmdlet.  <br/> W przypadku działania SharePoint pełna nazwa ścieżki adresu URL pliku lub folderu, do którego uzyskuje dostęp użytkownik.  <br/> W przypadku działania usługi Azure AD nazwa konta użytkownika, które zostało zmodyfikowane.|Wszystkie|
|Operacja|Nazwa działania użytkownika lub administratora. Wartość tej właściwości odpowiada wartości wybranej na liście rozwijanej **Działania** . Jeśli wybrano **opcję Pokaż wyniki dla wszystkich działań** , raport będzie zawierał wpisy dla wszystkich działań użytkownika i administratora dla wszystkich usług. Opis operacji/działań, które są rejestrowane w dzienniku inspekcji, można znaleźć na karcie **Inspekcja działań** w [obszarze Wyszukaj dziennik inspekcji w Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> W przypadku Exchange działania administratora ta właściwość identyfikuje nazwę uruchomionego polecenia cmdlet.|Wszystkie|
|Identyfikator organizacji|Identyfikator GUID organizacji.|Wszystkie|
|Ścieżka|Nazwa folderu skrzynki pocztowej, w którym znajduje się wiadomość, do której uzyskano dostęp. Ta właściwość identyfikuje również folder, do którego jest tworzony komunikat lub do którego jest kopiowany/przenoszony.|Exchange (działanie skrzynki pocztowej)|
|Parametry|W przypadku Exchange działania administratora nazwa i wartość wszystkich parametrów, które zostały użyte z poleceniem cmdlet zidentyfikowanym we właściwości Operacja.|Exchange (działanie administratora)|
|Typ rekordu|Typ operacji wskazany przez rekord. Ta właściwość wskazuje usługę lub funkcję, w której została wyzwolona operacja. Aby uzyskać listę typów rekordów i odpowiadającą im wartość ENUM (która jest wartością wyświetlaną we właściwości **RecordType** w rekordzie inspekcji), zobacz [Typ rekordu dziennika inspekcji](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).| 
|ResultStatus|Wskazuje, czy akcja (określona we właściwości **Operacja** ) zakończyła się pomyślnie, czy nie.  <br/> W przypadku Exchange działania administratora wartość to **Prawda** (pomyślne) lub **False** (niepowodzenie).|Wszystkie  <br/>|
|SecurityComplianceCenterEventType|Wskazuje, że działanie było zdarzeniem portalu zgodności. Wszystkie działania centrum zgodności będą miały wartość **0** dla tej właściwości.|Centrum zgodności & zabezpieczeń|
|Typ udostępniania|Typ uprawnień do udostępniania przypisanych użytkownikowi, którym został udostępniony zasób. Ten użytkownik jest identyfikowany we właściwości **UserSharedWith** .|SharePoint|
|Witryny|Identyfikator GUID witryny, w której znajduje się plik lub folder, do którego ma dostęp użytkownik.|SharePoint|
|SiteUrl|Adres URL witryny, w której znajduje się plik lub folder, do którego uzyskuje dostęp użytkownik.|SharePoint|
|SourceFileExtension|Rozszerzenie pliku, do których był uzyskiwany dostęp użytkownik. Ta właściwość jest pusta, jeśli obiekt, do których uzyskano dostęp, jest folderem.|SharePoint|
|SourceFileName|Nazwa pliku lub folderu, do którego uzyskuje dostęp użytkownik.|SharePoint|
|SourceRelativeUrl|Adres URL folderu zawierającego plik, do który jest uzyskiwany przez użytkownika. Kombinacja wartości właściwości **SiteURL**, **SourceRelativeURL** i **SourceFileName** jest taka sama jak wartość właściwości **ObjectID** , która jest pełną nazwą ścieżki dla pliku, do którego uzyskuje dostęp użytkownik.|SharePoint|
|Temat|Wiersz tematu wiadomości, do której uzyskano dostęp.|Exchange (działanie skrzynki pocztowej)|
|TabType| Typ karty dodany, usunięty lub zaktualizowany w zespole. Możliwe wartości dla tej właściwości to:  <br/><br/> **Excel pinezka** — karta Excel.  <br/> **Rozszerzenie** — wszystkie aplikacje innych firm i innych firm; takich jak Class Schedule, VSTS i Forms.  <br/> **Uwagi** — karta OneNote.  <br/> **Pdfpin** — karta PDF.  <br/> **Powerbi** — karta Power BI.  <br/> **Powerpointpin** — karta PowerPoint.  <br/> **Sharepointfiles** — karta SharePoint.  <br/> **Strona internetowa** — przypięta karta witryny internetowej.  <br/> **Karta wiki** — karta typu wiki.  <br/> **Wordpin** — karta Programu Word.|Microsoft Teams|
|Target (Element docelowy)|Użytkownik, na który została wykonana akcja (zidentyfikowana we właściwości **Operacja** ). Jeśli na przykład użytkownik-gość zostanie dodany do SharePoint lub zespołu firmy Microsoft, ten użytkownik zostanie wymieniony w tej właściwości.|Azure Active Directory|
|TeamGuid|Identyfikator zespołu w Microsoft Teams.|Microsoft Teams|
|Teamname|Nazwa zespołu w Microsoft Teams.|Microsoft Teams|
|Useragent|Informacje o przeglądarce użytkownika. Te informacje są dostarczane przez przeglądarkę.|SharePoint|
|Domena użytkownika|Informacje o tożsamości dotyczące organizacji dzierżawy użytkownika (aktora), który wykonał akcję.|Azure Active Directory|
|Userid|Użytkownik, który wykonał akcję (określoną we właściwości **Operacja** ), która spowodowała zarejestrowanie rekordu. Rekordy inspekcji dla działań wykonywanych przez konta systemowe (takie jak SHAREPOINT\system lub NT AUTHORITY\SYSTEM) są również zawarte w dzienniku inspekcji. Inną wspólną wartością właściwości UserId jest app@sharepoint. Oznacza to, że "użytkownik", który wykonał działanie, był aplikacją, która ma uprawnienia niezbędne w SharePoint do wykonywania akcji w całej organizacji (takich jak przeszukiwanie witryny SharePoint lub konta OneDrive) w imieniu użytkownika, administratora lub usługi. <br/><br/>Więcej informacji można znaleźć w następujących artykułach:<br/> [Użytkownik appsharepoint\@ w rekordach inspekcji](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records)<br/> lub <br/>[Konta systemowe w Exchange rekordy inspekcji skrzynki pocztowej](search-the-audit-log-in-security-and-compliance.md#system-accounts-in-exchange-mailbox-audit-records). |Wszystkie|
|UserKey|Alternatywny identyfikator użytkownika zidentyfikowanego we właściwości **UserID** . Na przykład ta właściwość jest wypełniana unikatowym identyfikatorem paszportu (PUID) dla zdarzeń wykonywanych przez użytkowników w SharePoint. Ta właściwość może również określać tę samą wartość co właściwość **UserID** dla zdarzeń występujących w innych usługach i zdarzeniach wykonywanych przez konta systemowe.|Wszystkie|
|UserSharedWith|Użytkownik, którym został udostępniony zasób. Ta właściwość jest uwzględniana, jeśli wartość właściwości **Operation** to **SharingSet**. Ten użytkownik jest również wymieniony w kolumnie **Udostępnione dla** w raporcie.|SharePoint|
|Usertype|Typ użytkownika, który wykonał operację. Następujące wartości wskazują typ użytkownika. <br/> <br/> **0** — zwykły użytkownik. <br/>**2** — Administrator w organizacji Microsoft 365.<sup> 1</sup> <br/>**3** — Administrator centrum danych firmy Microsoft lub konto systemu centrum danych. <br/>**4** — Konto systemowe. <br/>**5** — Aplikacja. <br/>**6** — jednostka usługi.<br/>**7** — zasady niestandardowe.<br/>**8** — Zasady systemowe.|Wszystkie|
|Wersja|Wskazuje numer wersji działania (identyfikowanego przez właściwość **Operation** ), które jest rejestrowane.|Wszystkie|
|Obciążenia|Usługa Microsoft 365, w której wystąpiło działanie.|Wszystkie|
||||

> [!NOTE]
><sup>1</sup> W przypadku zdarzeń związanych z Azure Active Directory wartość dla administratora nie jest używana w rekordzie inspekcji. Rekordy inspekcji działań wykonywanych przez administratorów wskazują, że działanie wykonał zwykły użytkownik (na przykład **UserType: 0**). Właściwość **UserID** zidentyfikuje osobę (zwykłego użytkownika lub administratora), która wykonała działanie.
