---
title: Izolacja i Access Control w Microsoft 365
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
f1.keywords:
- NOCSH
description: 'Podsumowanie: Wyjaśnienie izolacji i kontroli dostępu w różnych aplikacjach Microsoft 365.'
ms.openlocfilehash: dbb5ceb8b0e1e4ef6bb80ba2c3c771fc6d6cac5b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099394"
---
# <a name="isolation-and-access-control-in-microsoft-365"></a>Izolacja i Access Control w Microsoft 365

Azure Active Directory (Azure AD) i Microsoft 365 używają wysoce złożonego modelu danych, który obejmuje dziesiątki usług, setki jednostek, tysiące relacji i dziesiątki tysięcy atrybutów. Na wysokim poziomie usługa Azure AD i katalogi usług to kontenery dzierżaw i adresatów, które są synchronizowane przy użyciu protokołów replikacji opartej na stanie. Oprócz informacji o katalogu przechowywanych w usłudze Azure AD każde obciążenie usługi ma własną infrastrukturę usług katalogowych.
 
![Microsoft 365 synchronizację danych dzierżawy.](../media/office-365-isolation-tenant-data-sync.png)

W tym modelu nie ma jednego źródła danych katalogu. Określone systemy posiadają pojedyncze elementy danych, ale żaden pojedynczy system nie przechowuje wszystkich danych. usługi Microsoft 365 współpracują z usługą Azure AD w tym modelu danych. Usługa Azure AD to "system prawdy" dla udostępnionych danych, który jest zwykle małymi i statycznymi danymi używanymi przez każdą usługę. Model federacyjny używany w Microsoft 365 i usłudze Azure AD udostępnia udostępniony widok danych.

Microsoft 365 używa magazynu fizycznego i magazynu w chmurze platformy Azure. Exchange Online (w tym Exchange Online Protection) i Skype dla firm używać własnego magazynu na potrzeby danych klientów. SharePoint Online korzysta zarówno z magazynu SQL Server, jak i usługi Azure Storage, stąd potrzeba dodatkowej izolacji danych klientów na poziomie magazynu.

## <a name="exchange-online"></a>Exchange Online

Exchange Online przechowuje dane klientów w skrzynkach pocztowych. Skrzynki pocztowe są hostowane w bazach danych extensible Storage Engine (ESE) nazywanych bazami danych skrzynek pocztowych. Obejmuje to skrzynki pocztowe użytkowników, połączone skrzynki pocztowe, udostępnione skrzynki pocztowe i skrzynki pocztowe folderów publicznych. Skrzynki pocztowe użytkowników obejmują zapisaną zawartość Skype dla firm, taką jak historie konwersacji.

Zawartość skrzynki pocztowej użytkownika obejmuje:

- Wiadomości e-mail i załączniki wiadomości e-mail
- Informacje o kalendarzu i wolnych/zajętych
- Kontakty
- Zadania
- Uwagi
- Grupy
- Dane wnioskowania

Każda baza danych skrzynek pocztowych w Exchange Online zawiera skrzynki pocztowe z wielu dzierżaw. Kod autoryzacji zabezpiecza każdą skrzynkę pocztową, w tym w ramach dzierżawy. Domyślnie tylko przypisany użytkownik ma dostęp do skrzynki pocztowej. Lista kontroli dostępu (ACL), która zabezpiecza skrzynkę pocztową, zawiera tożsamość uwierzytelnioną przez usługę Azure AD na poziomie dzierżawy. Skrzynki pocztowe dla każdej dzierżawy są ograniczone do tożsamości uwierzytelnionych względem dostawcy uwierzytelniania dzierżawy, który obejmuje tylko użytkowników z tej dzierżawy. Zawartość w dzierżawie A w żaden sposób nie może zostać uzyskana przez użytkowników w dzierżawie B, chyba że zostanie jawnie zatwierdzona przez dzierżawę A.

## <a name="skype-for-business"></a>Skype dla firm

Skype dla firm przechowuje dane w różnych miejscach:

- Informacje o użytkowniku i koncie, w tym punkty końcowe połączenia, identyfikatory dzierżawy, plany wybierania numerów, ustawienia roamingu, stan obecności, listy kontaktów itp., są przechowywane na serwerach Skype dla firm usługi Active Directory i na różnych serwerach Skype dla firm baz danych. Listy kontaktów są przechowywane w skrzynce pocztowej Exchange Online użytkownika, jeśli użytkownik jest włączony dla obu produktów lub na serwerach Skype dla firm, jeśli użytkownik nie jest. Skype dla firm serwery baz danych nie są partycjonowane dla dzierżawy, ale izolacja danych z wieloma dzierżawami jest wymuszana za pośrednictwem kontroli dostępu opartej na rolach (RBAC).
- Zawartość spotkania i przekazane dane są przechowywane w udziałach rozproszonego systemu plików (DFS). Tę zawartość można również zarchiwizować w Exchange Online, jeśli jest włączona. Udziały systemu plików DFS nie są partycjonowane dla dzierżawy. zawartość jest zabezpieczona listami ACL, a wielodostępność jest wymuszana za pośrednictwem kontroli dostępu opartej na rolach.
- Rekordy szczegółów wywołań, które są historią działań, takimi jak historia wywołań, sesje wiadomości błyskawicznych, udostępnianie aplikacji, historia wiadomości błyskawicznych itp., mogą być również przechowywane w Exchange Online, ale większość rekordów szczegółów wywołań jest tymczasowo przechowywana na serwerach rekordów szczegółów wywołań (CDR). Zawartość nie jest partycjonowana na dzierżawę, ale wiele dzierżaw jest wymuszana za pośrednictwem kontroli dostępu opartej na rolach.

## <a name="sharepoint-online"></a>SharePoint Online

usługa SharePoint Online ma kilka niezależnych mechanizmów zapewniających izolację danych. Przechowuje obiekty jako abstrakcyjny kod w bazach danych aplikacji. Na przykład gdy użytkownik przekazuje plik do usługi SharePoint Online, plik jest demontowany, tłumaczony na kod aplikacji i przechowywany w wielu tabelach w wielu bazach danych.

Jeśli użytkownik może uzyskać bezpośredni dostęp do magazynu zawierającego dane, zawartość nie jest interpretowana dla człowieka ani żadnego systemu innego niż SharePoint Online. Mechanizmy te obejmują kontrolę dostępu do zabezpieczeń i właściwości. Wszystkie zasoby SharePoint Online są zabezpieczone przez kod autoryzacji i zasady RBAC, w tym w ramach dzierżawy. Lista kontroli dostępu (ACL), która zabezpiecza zasób, zawiera tożsamość uwierzytelnioną na poziomie dzierżawy. SharePoint Dane online dla dzierżawy są ograniczone do tożsamości uwierzytelnionych przez dostawcę uwierzytelniania dla dzierżawy.

Oprócz list ACL właściwość na poziomie dzierżawy określająca dostawcę uwierzytelniania (czyli usługę Azure AD specyficzną dla dzierżawy) jest zapisywana raz i nie można jej zmienić po ustawieniu. Po ustawieniu właściwości dzierżawy dostawcy uwierzytelniania dla dzierżawy nie można jej zmienić przy użyciu interfejsów API uwidocznianych dla dzierżawy.

Unikatowy *identyfikator SubscriptionId* jest używany dla każdej dzierżawy. Wszystkie witryny klienta są własnością dzierżawy i mają przypisany identyfikator *SubscriptionId* unikatowy dla dzierżawy. *Właściwość SubscriptionId* w witrynie jest zapisywana raz i trwale. Po przypisaniu do dzierżawy nie można przenieść witryny do innej dzierżawy. *SubscriptionId* jest kluczem używanym do tworzenia zakresu zabezpieczeń dla dostawcy uwierzytelniania i jest powiązany z dzierżawą.

usługa SharePoint Online używa SQL Server i usługi Azure Storage do przechowywania metadanych zawartości. Klucz partycji magazynu zawartości to *SiteId* w SQL. Podczas uruchamiania zapytania SQL usługa SharePoint Online używa identyfikatora *SiteId* zweryfikowanego w ramach sprawdzania *identyfikatora SubscriptionId na poziomie dzierżawy*.

SharePoint Online przechowuje zaszyfrowaną zawartość plików w Microsoft Azure obiektach blob. Każda farma SharePoint Online ma własne konto Microsoft Azure, a wszystkie obiekty blob zapisane na platformie Azure są szyfrowane indywidualnie przy użyciu klucza przechowywanego w magazynie zawartości SQL. Klucz szyfrowania chroniony w kodzie przez warstwę autoryzacji i nie jest uwidoczniany bezpośrednio użytkownikowi końcowemu. SharePoint Online ma monitorowanie w czasie rzeczywistym w celu wykrywania, kiedy żądanie HTTP odczytuje lub zapisuje dane dla więcej niż jednej dzierżawy. Identyfikator *subskrypcji* tożsamości żądania jest śledzony względem *identyfikatora subskrypcji* dostępnego zasobu. Żądania dostępu do zasobów więcej niż jednej dzierżawy nigdy nie powinny być wykonywane przez użytkowników końcowych. Żądania obsługi w środowisku wielodostępnym są jedynym wyjątkiem. Na przykład przeszukiwarka wyszukiwania pobiera zmiany zawartości dla całej bazy danych jednocześnie. Zwykle wiąże się to z wykonywaniem zapytań dotyczących lokacji więcej niż jednej dzierżawy w ramach pojedynczego żądania obsługi, co jest wykonywane ze względów wydajności.

## <a name="teams"></a>Teams

Dane Teams są przechowywane inaczej, w zależności od typu zawartości. 

Zapoznaj się z [sesją ignite breakout dotyczącą architektury Microsoft Teams](https://channel9.msdn.com/Events/Ignite/Microsoft-Ignite-Orlando-2017/BRK3071), aby zapoznać się z dogłębną dyskusją.

### <a name="core-teams-customer-data"></a>Podstawowe dane Teams klienta

Jeśli dzierżawa jest aprowizowana w Australii, Kanadzie, Unii Europejskiej, Francji, Niemczech, Indiach, Japonii, RPA, Korei Południowej, Szwajcarii (w tym Liechtensteinie), Zjednoczonych Emiratach Arabskich, Wielkiej Brytanii lub Stany Zjednoczone, firma Microsoft przechowuje następujące dane klientów w spoczynku tylko w tej lokalizacji:

- Teams czaty, konwersacje zespołowe i kanałowe, obrazy, wiadomości poczty głosowej i kontakty.
- SharePoint zawartość witryny online i pliki przechowywane w tej witrynie.
- Pliki przekazane do OneDrive do pracy lub szkoły.

#### <a name="chat-channel-messages-team-structure"></a>Czat, komunikaty kanałów, struktura zespołu

Każdy zespół w Teams jest wspierany przez grupę Microsoft 365 oraz jej witrynę SharePoint i skrzynkę pocztową Exchange. Prywatne czaty (w tym czaty grupowe), wiadomości wysyłane w ramach konwersacji w kanale oraz struktura zespołów i kanałów są przechowywane w usłudze czatu działającej na platformie Azure. Dane są również przechowywane w ukrytym folderze w skrzynkach pocztowych użytkownika i grupy w celu włączenia funkcji Information Protection.

#### <a name="voicemail-and-contacts"></a>Poczta głosowa i kontakty

Poczta głosowa jest przechowywana w Exchange. Kontakty są przechowywane w Exchange opartym na chmurze magazynie danych. Exchange i magazyn w chmurze oparty na Exchange zapewniają już miejsce przechowywania danych w każdym z obszarów geograficznych światowego centrum danych. Dla wszystkich zespołów poczta głosowa i kontakty są przechowywane w kraju dla Australii, Kanady, Francji, Niemiec, Indii, Japonii, Zjednoczonych Emiratów Arabskich, Wielkiej Brytanii, RPA, Korei Południowej, Szwajcarii (w tym Liechtensteinu) i Stany Zjednoczone. W przypadku wszystkich innych krajów pliki są przechowywane w lokalizacji USA, Europa lub Asia-Pacific na podstawie koligacji dzierżawy.

#### <a name="images-and-media"></a>Obrazy i nośniki

Nośnik używany w czatach (z wyjątkiem plików GIF giphy, które nie są przechowywane, ale są linkiem referencyjnym do oryginalnego adresu URL usługi Giphy, Giphy jest usługą inną niż Microsoft) jest przechowywany w usłudze multimedialnej opartej na platformie Azure, która jest wdrażana w tych samych lokalizacjach co usługa czatu.

#### <a name="files"></a>Pliki

Pliki (w tym OneNote i wiki), które ktoś udostępnia w kanale, są przechowywane w witrynie SharePoint zespołu. Pliki udostępnione w ramach czatu prywatnego lub czatu podczas spotkania lub połączenia są przekazywane i przechowywane na OneDrive konta służbowego użytkownika, który udostępnia plik. Exchange, SharePoint i OneDrive już zapewniają miejsce przechowywania danych w każdym z obszarów geograficznych światowego centrum danych. W przypadku istniejących klientów wszystkie pliki, notesy OneNote, Teams zawartość typu wiki i skrzynki pocztowe, które są częścią środowiska Teams, są już przechowywane w lokalizacji na podstawie koligacji dzierżawy. Pliki są przechowywane w kraju dla Australii, Kanady, Francji, Niemiec, Indii, Japonii, Zjednoczonych Emiratów Arabskich, Wielkiej Brytanii, RPA, Korei Południowej i Szwajcarii (w tym Liechtensteinu). We wszystkich innych krajach pliki są przechowywane w lokalizacji USA, Europa lub Azja i Pacyfik na podstawie koligacji dzierżawy.
