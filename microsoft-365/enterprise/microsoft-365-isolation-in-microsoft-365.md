---
title: Izolacji i kontroli dostępu w Microsoft 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
description: 'Podsumowanie: objaśnienie izolacji i kontroli dostępu w różnych aplikacjach systemu Microsoft 365.'
ms.openlocfilehash: 65845a8d6c8e6be578e997fa1455aa280c787897
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019357"
---
# <a name="isolation-and-access-control-in-microsoft-365"></a>Izolacji i kontroli dostępu w Microsoft 365

Azure Active Directory (Azure AD) i usługi Microsoft 365 korzystają z bardzo złożonego modelu danych, który zawiera dziesiątki usług, setki jednostek, tysiące relacji i dziesiątki tysięcy atrybutów. Na wysokim poziomie usługa Azure AD i katalogi usług to kontenery dzierżaw i adresatów synchronizowane przy użyciu protokołów replikacji opartych na stanie. Oprócz informacji katalogowych w usłudze Azure AD każde z obciążeń usług ma własną infrastrukturę usług katalogowych.
 
![Microsoft 365 danych dzierżawy.](../media/office-365-isolation-tenant-data-sync.png)

W tym modelu nie ma jednego źródła danych katalogu. Poszczególne systemy są właścicielami pojedynczych danych, ale żaden pojedynczy system nie przechowuje wszystkich danych. Microsoft 365 współpracują z usługami Azure AD w tym modelu danych. Usługa Azure AD to "system prawdy" dla danych udostępnionych, który zazwyczaj jest małymi i statycznych danymi używanymi przez każdą usługę. Model federowany używany w usługach Microsoft 365 i Azure AD zapewnia udostępniony widok danych.

Microsoft 365 korzysta zarówno z magazynu fizycznego, jak i z magazynu w chmurze platformy Azure. Exchange Online (w tym Exchange Online Protection) i Skype dla firm używać własnej przestrzeni dyskowej na potrzeby danych klientów. SharePoint online używa zarówno magazynu SQL Server, jak i platformy Azure Storage, co oznacza konieczność dodatkowej izolacji danych klienta na poziomie magazynu.

## <a name="exchange-online"></a>Exchange Online

Exchange Online danych klientów w skrzynkach pocztowych. Skrzynki pocztowe są hostowane w bazach danych aparatu Storage (ESE), nazywanych bazami danych skrzynek pocztowych. Dotyczy to skrzynek pocztowych użytkowników, połączonych skrzynek pocztowych, udostępnionych skrzynek pocztowych i skrzynek pocztowych folderów publicznych. Skrzynki pocztowe użytkowników zawierają zapisane Skype dla firm, takie jak historia konwersacji.

Zawartość skrzynki pocztowej użytkownika obejmuje:

- Załączniki wiadomości e-mail i wiadomości e-mail
- Informacje o kalendarzu i informacje o wolnym/zajętym
- Kontakty
- Zadania
- Uwagi
- Grupy
- Dane wnioskowania

Każda baza danych skrzynek pocztowych w Exchange Online zawiera skrzynki pocztowe z wielu dzierżaw. Kod autoryzacji zabezpiecza każdą skrzynkę pocztową, w tym w ramach autoryzacji. Domyślnie tylko przypisany użytkownik ma dostęp do skrzynki pocztowej. Lista kontroli dostępu (ACL), która zabezpiecza skrzynkę pocztową, zawiera tożsamość uwierzytelnioną przez usługę Azure AD na poziomie dzierżawy. Skrzynki pocztowe w poszczególnych dzierżawach są ograniczone do tożsamości uwierzytelnionych u dostawcy uwierzytelniania dzierżawy, który obejmuje tylko użytkowników z tej dzierżawy. Zawartość w dzierżawie A nie może być w jakikolwiek sposób uzyskiwana przez użytkowników w dzierżawie B, chyba że zostanie jawnie zatwierdzona przez dzierżawę A.

## <a name="skype-for-business"></a>Skype dla firm

Skype dla firm przechowuje dane w różnych miejscach:

- Informacje o użytkowniku i koncie, które obejmują punkty końcowe połączenia, identyfikatory dzierżawy, plany wybierania numerów, ustawienia mobilne, stan obecności, listy kontaktów itp., są przechowywane na serwerach usługi Skype dla firm Active Directory oraz na różnych serwerach Skype dla firm danych. Listy kontaktów są przechowywane w skrzynce Exchange Online pocztowej użytkownika, jeśli dla użytkownika włączono oba produkty, lub na serwerach Skype dla firm, jeśli ten użytkownik nie jest. Skype dla firm danych nie są podzielone na dzierżawy, ale ochrona danych przez wiele dzierżaw jest wymuszana za pośrednictwem kontroli dostępu opartej na rolach (RBAC, Role based Access Control).
- Zawartość spotkań i przekazane dane są przechowywane w udziałach systemu plików rozproszonych (DFS, Distributed File System). Tę zawartość można również zarchiwizować w Exchange Online włączona. Udziały usługi DFS nie są podzielone na dzierżawy. zawartość jest zabezpieczona przy użyciu ACL, a wielonajętowa jest wymuszana za pośrednictwem RBAC.
- Rekordy szczegółowe połączeń, które są historią działań, taką jak historia połączeń, sesje wiadomości błyskawicznych, udostępnianie aplikacji, historia wiadomości błyskawicznych itp., mogą być również przechowywane w programie Exchange Online, ale większość rekordów szczegółów połączeń jest tymczasowo przechowywana na serwerach rekordu szczegółów połączeń. Zawartość nie jest podzielona na dzierżawę, ale wielu dzierżaw jest wymuszana za pośrednictwem RBAC.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online dostępnych jest kilka niezależnych mechanizmów izolacji danych. Obiekty są przechowywane w bazach danych aplikacji jako kod abstrakcyjny. Gdy na przykład użytkownik przekaże plik do usługi SharePoint Online, plik jest dezasembowany, przekształcany w kod aplikacji i przechowywany w wielu tabelach w wielu bazach danych.

Jeśli użytkownik może uzyskać bezpośredni dostęp do magazynu zawierającego dane, nie można zinterpretować zawartości przez człowieka ani żadnego systemu innego niż SharePoint Online. Mechanizmy te obejmują kontrolę dostępu zabezpieczeń i właściwości. Wszystkie SharePoint online są zabezpieczone kodem autoryzacji i zasadami RBAC, w tym w ramach pożyczki. Lista kontroli dostępu ( ACL), która zabezpiecza zasób, zawiera tożsamość uwierzytelnioną na poziomie dzierżawy. SharePoint danych online dla dzierżawy są ograniczone do tożsamości uwierzytelnionych przez dostawcę uwierzytelniania dzierżawy.

Oprócz acl, właściwość na poziomie dzierżawy określająca dostawcę uwierzytelniania (czyli usługę Azure AD specyficzną dla dzierżawy) jest zapisywana raz i nie można jej zmienić po jej skonfigurowaniu. Po skonfigurowaniu właściwości dzierżawy dostawcy uwierzytelniania dla dzierżawy nie można jej zmienić przy użyciu żadnych interfejsów API ujawnionych dla dzierżawy.

Dla każdej *dzierżawy jest* używany unikatowy identyfikator subskrypcji. Wszystkie witryny klientów są własnością dzierżawy i mają unikatowe identyfikatory *subskrypcji* . Właściwość *SubscriptionId* w witrynie jest zapisywana raz i jest stała. Po przypisaniu do dzierżawy witryny nie można przenieść do innej dzierżawy. *SubscriptionId* to klucz używany do utworzenia zakresu zabezpieczeń dla dostawcy uwierzytelniania i jest powiązany z dzierżawą.

SharePoint Online korzysta SQL Server magazynu Storage Azure Storage do przechowywania metadanych zawartości. Klucz partycji magazynu zawartości to *SiteId* in SQL. Podczas uruchamiania zapytania SQL, w SharePoint Online jest używany element *SiteId* zweryfikowany jako część sprawdzania *subscriptionId na* poziomie dzierżawy.

SharePoint Online przechowuje zaszyfrowaną zawartość plików w Microsoft Azure blob. Każda farma usługi SharePoint Online ma własne konto usługi Microsoft Azure, a wszystkie obiekty blob zapisane na platformie Azure są szyfrowane osobno za pomocą klucza przechowywanego w sklepie SQL zawartości. Klucz szyfrowania chroniony w kodzie przez warstwę autoryzacji i nie jest ujawniony bezpośrednio użytkownikowi końcoweowi. SharePoint w trybie online jest dostępne monitorowanie w czasie rzeczywistym, które wykrywa, kiedy żądanie HTTP odczytuje lub zapisuje dane dla więcej niż jednej dzierżawy. Tożsamość żądania *, subscriptionId jest* śledzona na stronie *SubscriptionId* dostępnego zasobu. Żądania dostępu do zasobów większej liczby dzierżaw nie powinny być nigdy zdarzane użytkownikom końcowych. Jedynym wyjątkiem są żądania usługi w środowisku wielodostępnym. Na przykład przeszukiwarka wyszukiwania ściąga zmiany zawartości dla całej bazy danych jednocześnie. Zazwyczaj obejmuje to wykonywanie zapytań na witrynach więcej niż jednej dzierżawy w jednym z żądań usługi, odbywa się to ze względu na wydajność.

## <a name="teams"></a>Teams

Dane Teams przechowywane w różny sposób, w zależności od typu zawartości. 

Zapoznaj się z sesją [konferencji Ignite na temat Microsoft Teams architektury,](https://channel9.msdn.com/Events/Ignite/Microsoft-Ignite-Orlando-2017/BRK3071) aby uzyskać szczegółową dyskusję.

### <a name="core-teams-customer-data"></a>Podstawowe Teams klientów

Jeśli obsługa Twojej dzierżawy jest aprowizowana w Australii, Kanadzie, Unii Europejskiej, Francji, Niemczech, Indiach, Japonii, Południowej Afryki, Szwajcarii (z Liechtensteinem), Zjednoczonych Emiratach Arabskich, Zjednoczonym Królestwie lub Stanach Zjednoczonych, firma Microsoft przechowuje następujące dane klientów tylko w tym miejscu:

- Teams czaty, konwersacje zespołu i kanału, obrazy, wiadomości poczty głosowej i kontakty.
- SharePoint zawartości witryny online i plików przechowywanych w tej witrynie.
- Pliki przekazane do OneDrive służbowego lub szkolnego.

#### <a name="chat-channel-messages-team-structure"></a>Czat, wiadomości kanałów, struktura zespołu

Każdy zespół w programie Teams jest Microsoft 365 przez grupę usługi i jej witrynę sieci SharePoint oraz Exchange skrzynkę pocztową. Czaty prywatne (w tym czaty grupowe), wiadomości wysłane w ramach konwersacji w kanale oraz struktura zespołów i kanałów są przechowywane w usłudze czatu działającej na platformie Azure. Dane są również przechowywane w ukrytym folderze w skrzynkach pocztowych użytkowników i grup w celu włączenia funkcji ochrony informacji.

#### <a name="voicemail-and-contacts"></a>Poczta głosowa i kontakty

Wiadomości poczty głosowej są przechowywane w Exchange. Kontakty są przechowywane w Exchange danych w chmurze. Exchange i magazyn Exchange w chmurze już zapewniają dane przechowywane w każdym z lokalizacji geograficznych centrum danych na całym świecie. W przypadku wszystkich zespołów poczta głosowa i kontakty są przechowywane w kraju dla Australii, Kanady, Francji, Niemiec, Indii, Japonii, Zjednoczonych Emiratów Arabskich, Zjednoczonego Królestwa, Południowej Afryki, Korei Południowej, Szwajcarii (która obejmuje Liechtenstein) i Stanów Zjednoczonych. We wszystkich innych krajach pliki są przechowywane w Usa, Europie lub Asia-Pacific lokalizacji na podstawie koligacji dzierżawy.

#### <a name="images-and-media"></a>Obrazy i multimedia

Multimedia używane w czatach (oprócz plików GIF Giphy, które nie są przechowywane, ale są linkiem do oryginalnego adresu URL usługi Giphy, Giphy jest usługą niebędącą od firmy Microsoft) są przechowywane w usłudze multimediów opartej na platformie Azure, która jest wdrożona w tych samych lokalizacjach, co usługa czatu.

#### <a name="files"></a>Pliki

Pliki (w tym OneNote wiki) które ktoś udostępnia w kanale są przechowywane w witrynie zespołu SharePoint zespołu. Pliki udostępnione w prywatnym czacie albo na czacie podczas spotkania lub połączenia są przekazywane i przechowywane w OneDrive konta służbowego użytkownika, który udostępnił plik. Exchange, SharePoint i OneDrive już podać dane przechowywania w każdym z lokalizacji geograficznych centrum danych na całym świecie. W przypadku obecnych klientów wszystkie pliki, notesy programu OneNote, zawartość stron typu wiki Teams i skrzynki pocztowe w ramach usługi Teams są już przechowywane w lokalizacji na podstawie koligacji dzierżawy. Pliki są przechowywane w kraju dla Australii, Kanady, Francji, Niemiec, Indii, Japonii, Zjednoczonych Emiratów Arabskich, Zjednoczonego Królestwa, Południowej Afryki, Korei Południowej i Szwajcarii (w tym Liechtensteinu). W przypadku wszystkich pozostałych krajów pliki są przechowywane w Usa, Europie lub regionie Azji i Pacyfiku w zależności od koligacji dzierżawy.
