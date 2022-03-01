---
title: Archiwizowanie danych innych firm we współpracy z partnerem
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Dowiedz się, jak skonfigurować łącznik niestandardowy do importowania danych innych firm ze źródeł danych, takich jak Czat usługi Salesforce, Yahoo Messenger lub Yammer.
ms.openlocfilehash: 53c6cae76327c7a8fb8ca89de464ad8a63e75d6a
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017769"
---
# <a name="work-with-a-partner-to-archive-third-party-data"></a>Archiwizowanie danych innych firm we współpracy z partnerem

We współpracy z partnerem firmy Microsoft możesz importować i archiwizować dane ze źródła danych innej firmy w celu Microsoft 365. Partner może udostępnić Ci łącznik niestandardowy skonfigurowany w celu regularnego wyodrębniania elementów ze źródła danych innej firmy, a następnie zaimportować te elementy. Łącznik partnera konwertuje zawartość elementu ze źródła danych na format wiadomości e-mail, a następnie przechowuje te elementy w skrzynkach pocztowych. Po zaimportowaniu danych innych firm możesz zastosować do tych danych funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, In-Place archiwizacja, inspekcja i Microsoft 365 przechowywania.

> [!IMPORTANT]
> Rozwiązania [zgodności komunikacji](communication-compliance.md) w p Microsoft 365 nie można zastosować do danych innych firm zaimportowanych za pomocą łączników partnerów wymienionych w tym artykule.

Oto omówienie tego procesu i czynności niezbędnych do współpracy z partnerem firmy Microsoft w celu zaimportowania danych innych firm.

[Krok 1. Znajdowanie partnera danych innej firmy](#step-1-find-a-third-party-data-partner)

[Krok 2. Tworzenie i konfigurowanie skrzynki pocztowej danych innej firmy](#step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365)

[Krok 3. Konfigurowanie skrzynek pocztowych użytkowników na dane innych firm](#step-3-configure-user-mailboxes-for-third-party-data)

[Krok 4. Podanie partnerowi informacji](#step-4-provide-your-partner-with-information)

[Krok 5. Zarejestruj łącznik danych innej firmy w programie Azure Active Directory](#step-5-register-the-third-party-data-connector-in-azure-active-directory)

## <a name="how-the-third-party-data-import-process-works"></a>Jak działa proces importowania danych innych firm

Na poniższej ilustracji i opisie przedstawiono działanie procesu importowania danych innych firm podczas współpracy z partnerem.

![Jak działa proces importowania danych innych firm.](../media/5d4cf8e9-b4cc-4547-90c8-d12d04a9f0e7.png)

1. Klient współpracuje ze swoim partnerem w celu skonfigurowania łącznika, który wyodrębnia elementy ze źródła danych innej firmy, a następnie importuje je do Microsoft 365.

2. Łącznik partnera łączy się ze źródłami danych innych firm za pośrednictwem interfejsu API innej firmy (według harmonogramu lub zgodnie z konfiguracją) i wyodrębnia elementy ze źródła danych. Łącznik partnera konwertuje zawartość elementu na format wiadomości e-mail. Zobacz [sekcję Więcej](#more-information) informacji, aby uzyskać opis schematu formatu wiadomości.

3. Łącznik partnera łączy się z usługą platformy Azure Microsoft 365 przy użyciu Exchange sieci Web (EWS) za pośrednictwem dobrze znanego punktu końcowego.

4. Elementy są importowane do skrzynki pocztowej określonego użytkownika lub do "wychwytliwej" skrzynki pocztowej danych innych firm. To, czy element został zaimportowany do skrzynki pocztowej określonego użytkownika, czy do skrzynki pocztowej danych innej firmy, jest oparte na następujących kryteriach:

   1. **Elementy, które mają identyfikator użytkownika odpowiadający kontu użytkownika:** Jeśli łącznik partnera może zamapować identyfikator użytkownika elementu w źródle danych innej firmy na określony identyfikator użytkownika w programie Microsoft 365, ten element jest kopiowany do folderu przeczyszczania **w folderze** Elementy do odzyskania użytkownika. Użytkownicy nie mogą uzyskać dostępu do elementów w folderze przeczyszczania. Za pomocą narzędzi zbierania elektronicznych materiałów dowodowych można jednak wyszukiwać elementy w folderze przeczyszczania.

   1. **Elementy, które nie mają identyfikatora użytkownika odpowiadającego kontu użytkownika:** Jeśli łącznik partnera nie może zamapować identyfikatora użytkownika elementu na określony identyfikator użytkownika, jest on kopiowany **do folderu** Skrzynka odbiorcza w skrzynce odbiorczej innej firmy. Importowanie elementów do skrzynki odbiorczej umożliwia Ci lub innej osobie w organizacji logowanie się do skrzynki pocztowej innej firmy w celu wyświetlania tych elementów i zarządzania nimi oraz do wyświetlania, czy w konfiguracji łącznika partnera należy coś dopasować.

## <a name="step-1-find-a-third-party-data-partner"></a>Krok 1. Znajdowanie partnera danych innej firmy

Kluczowym elementem archiwizacji danych innych firm w programie Microsoft 365 jest znajdowanie partnera firmy Microsoft, który konkruje się w przechwytywaniu danych ze źródła danych innej firmy i importowaniu ich do usługi Microsoft 365. Po zaimportowaniu danych można je zarchiwizować i zachować wraz z innymi danymi firmy Microsoft w Twojej organizacji, takimi jak wiadomości e-mail Exchange i dokumenty z usług SharePoint i OneDrive dla Firm. Partner tworzy łącznik, który wyodrębnia dane z zewnętrznych źródeł danych organizacji (takich jak blackBerry, Facebook, Google+, Thomson Reuters, Twitter i YouTube) i przekazuje te dane do interfejsu API programu Microsoft 365, który importuje elementy do skrzynek pocztowych programu Exchange jako wiadomości e-mail.

W poniższych sekcjach przedstawiono partnerów firmy Microsoft (oraz inne źródła danych, które obsługują), którzy uczestniczą w programie do archiwizacji danych innych firm w programie Microsoft 365.

[17a-4 LLC.](#17a-4-llc)

[ArchiveSocial](#archivesocial)

[Veritas](#veritas)

[OpenText](#opentext)

[Jak to zdać](#smarsh)

[Verba](#verba)

### <a name="17a-4-llc"></a>17a-4 LLC.

[17a-4 LLC](https://www.17a-4.com) obsługuje następujące źródła danych innych firm:

- BlackBerry

- Bloomberg Data Strumienie

- Cisco Jabber

- FactSet

- HipChat

- InvestEdge

- LivePerson

- Dane w programie MessageLabs Strumienie

- OpenText

- Oracle/ATG "click-to-call" Pomoc na żywo

- Pivot IM Z.O.Y

- Microsoft SharePoint

- MindAlign

- Sitrion One (Newsgator)

- Skype dla firm (Lync/OCS)

- Skype dla firm Online (Lync Online)

- SQL danych

- Squawker

- Thomson Reuters Eikon Messenger

### <a name="archivesocial"></a>ArchiveSocial

[ArchiwumSocial](https://www.archivesocial.com) obsługuje następujące źródła danych innych firm:

- Facebook

- Flickr

- Aby to zda

- LinkedIn

- Pinterest

- Twitter

- YouTube

- Vimeo

### <a name="veritas"></a>Veritas

[Firma Veritas](https://www.globanet.com) obsługuje następujące źródła danych innych firm:

- AOL z klientem przestawny

- Dzienniki połączeń BlackBerry (5, 10, 12)

- BlackBerry Messenger (w wersji 5, 10, w wersji 12)

- Numer PIN urządzenia BlackBerry (w wersji 5, 10, w wersji 12)

- BlackBerry SMS (v5, w wersji 10, w wersji 12)

- Bloomberg Chat

- Bloomberg Mail

- Box

- CipherCloud for Salesforce Chatter

- Cisco IM &amp; Presence Server (10, 10.5.1 SU1, 11.0, 11.5 SU2)

- Cisco Webex Teams

- Citrix Workspace &amp; ShareFile

- CrowdCompass

- Niestandardowe rozdzielane pliki tekstowe

- Niestandardowe pliki XML

- Facebook (strony)

- Factset

- FXConnect

- ICE Chat/YellowJacket

- Jive

- Macgregor XIP

- Microsoft Exchange Server

- Microsoft OneDrive dla firm

- Microsoft Teams

- Microsoft Yammer

- Mobile Guard

- Pivot

- Czat usługi Salesforce

- Skype dla firm Online

- Skype dla firm, wersje 2007 R2–2016 (lokalnie)

- Zapas czasu Enterprise siatki

- Nago

- Thomson Reuters Eikon

- Thomson Reuters Messenger

- Thomson Reuters Dealings 3000 / FX Trading

- Twitter

- Czat UBS

- YouTube

### <a name="opentext"></a>OpenText

[OpenText](https://www.opentext.com/what-we-do/products/opentext-product-offerings-catalog/rebranded-products/daegis) obsługuje następujące źródła danych innych firm:

- Axs Encrypted

- Osie Exchange

- Lokalne archiwum osi

- Axs PlaceHolder

- Podpisane osie

- Bloomberg

- Thomson Reuters

### <a name="smarsh"></a>Jak to zdać

[Tensh](https://www.smarsh.com) obsługuje następujące źródła danych innych firm:

- AIM

- Idol amerykański

- Apple Juice

- AOL z klientem przestawny

- Ares

- Bazaar Voice

- Bear Share

- Bit Potok

- Dzienniki połączeń BlackBerry (5, 10, 12)

- BlackBerry Messenger (w wersji 5, 10, w wersji 12)

- Numer PIN urządzenia BlackBerry (w wersji 5, 10, w wersji 12)

- BlackBerry SMS (v5, w wersji 10, w wersji 12)

- Bloomberg Mail

- CellTrust

- Importowanie czatu

- Zasady i rejestrowanie na czacie w czasie rzeczywistym

- Czat

- Cisco IM &amp; Presence Server (v9.0.1, v9.1, v9.1.1 SU1, v10, 10.5.1 SU1)

- Cisco Unified Presence Server (8.6.3, 8.6.4, 8.6.5)

- Importowanie współpracy

- Rejestrowanie współpracy w czasie rzeczywistym

- Bezpośredni Połączenie

- Facebook

- FactSet

- FastTrack

- Historyjka

- Google+

- GoToMyPC

- Hopster

- HubConnex

- IBM Connections (3.0.1, 4.0, 4.5, 4.5 CR3, v5)

- IBM Connections Chat Cloud

- IBM Connections Social Cloud

- IBM SameTime Advanced 8.5.2 IFR1

- IBM SameTime Communicate 9.0

- IBM SameTime Community (v8.0.2, 8.5.1 IFR2, v8.5.2 IFR1, v9.1)

- IBM SameTime Complete 9.0

- IBM SameTime Conference 9.0

- IBM SameTime Meeting 8.5.2 IFR1

- ICE/YellowJacket

- Importowanie wiadomości błyskawicznych

- Zasady i rejestrowanie w czasie rzeczywistym wiadomości błyskawicznych

- Indii Messenger

- Instant Bloomberg

- IRC

- Jive

- Rejestrowanie w czasie rzeczywistym Jive 6 (v6, v7)

- Importowanie pliku Jive

- JXTA

- LinkedIn

- Microsoft Lync (2010, 2013)

- MFTP

- Microsoft Lync 2013 Voice

- Microsoft SharePoint (2010, 2013)

- Microsoft Office SharePoint Online

- Microsoft UC (Unified Communications)

- MindAlign

- Mobile Guard

- MSN

- Mój obszar

- NEONetwork

- Microsoft 365 dedykowany dla programu Lync

- Microsoft 365 udostępnione wiadomości błyskawiczne

- Pinterest

- Pivot

- QQ

- Skype dla firm 2015

- SoftEther

- Nago

- Thomson Reuters Eikon

- Thomson Reuters Messenger

- Tor

- TTT

- Twitter

- WinMX

- Winny

- Yahoo

- Yammer

- YouTube


### <a name="verba"></a>Verba

[Program Verba](https://www.verba.com) obsługuje następujące źródła danych innych firm:

- Avaya Aura Video

- Avaya Aura Voice

- Avtec Radio

- Przedz./Telex Radio

- BroadSoft Video

- BroadSoft Voice

- Centile Voice

- Cisco Jabber IM

- Cisco UC Video

- Cisco UC Voice

- Cisco UCCX/UCCE Video

- Cisco UCCX/UCCE Voice

- ESChat Radio

- Ekspert ds. kontaktu Geoman

- IP Trade Voice

- Luware LUCS Contact Center

- Microsoft UC (Unified Communications)

- Mitel MiContact Center for Lync (prairieFyre)

- Klip wideo: sterownik obramowania sesji pakietu Oracle/ Acme

- Głos kontrolera granicznego sesji pakietu Oracle/Acme

- Singtel Mobile Voice

- SIPREC Video

-  SIPREC Voice

- Skype dla firm / Wiadomości błyskawiczne w programie Lync

- Skype dla firm / Wideo w programie Lync

- Skype dla firm / Lync Voice

- Speakerbus Voice

- Standardowa karta wideo SIP/H.323

- Standard SIP/H.323 Voice

- Truphone Voice

- TwistedPair Radio

- Windows ekran komputera stacjonarnego

## <a name="step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365"></a>Krok 2. Tworzenie i konfigurowanie skrzynki pocztowej danych innej firmy w programie Microsoft 365

Poniżej o procedurach tworzenia i konfigurowania skrzynki pocztowej danych innej firmy na celu zaimportowania danych do Microsoft 365. Jak wyjaśniono wcześniej, elementy są importowane do tej skrzynki pocztowej, jeśli łącznik partnera nie może zamapować identyfikatora użytkownika elementu na konto użytkownika.

 **Wykonywanie tych zadań w centrum administracyjne platformy Microsoft 365**

1. Utwórz konto użytkownika i przypisz mu licencję Exchange Online Plan 2. Zobacz [Dodawanie użytkowników do Microsoft 365](../admin/add-users/add-users.md). Aby można było umieścić skrzynkę pocztową w archiwum w chmurze lub włączyć archiwalne skrzynki pocztowe z przydziałem magazynowania do 1,5 TB, wymagana jest licencja Planu 2.

2. Dodaj konto użytkownika skrzynki pocztowej danych innej firmy do roli administratora usługi **Exchange** w programie Microsoft 365; zobacz Przypisywanie ról administratora w [programie Microsoft 365](../admin/add-users/assign-admin-roles.md).

    > [!TIP]
    > Zapisz poświadczenia dla tego konta użytkownika. Musisz je udostępnić partnerowi zgodnie z opisem w kroku 4.

 **Wykonywanie tych zadań w centrum Exchange administracyjnego**

1. Ukrywanie skrzynki pocztowej danych innych firm w książce adresowej i innych listach adresów w organizacji. zobacz [Zarządzanie skrzynkami pocztowymi użytkowników](/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes). Ewentualnie możesz uruchomić następujące polecenie programu PowerShell:

    ```powershell
    Set-Mailbox -Identity <identity of third-party data mailbox> -HiddenFromAddressListsEnabled $true
    ```

2. Przypisz **uprawnienia Pełny** dostęp do skrzynki pocztowej danych innej firmy, aby administratorzy lub administratorzy zgodności mogą otwierać skrzynkę pocztową danych innych firm w kliencie stacjonarnym programu Outlook. Zobacz Zarządzanie uprawnieniami [adresatów](https://go.microsoft.com/fwlink/p/?LinkId=692104).

3. Włącz następujące funkcje związane ze zgodnością dla skrzynki pocztowej danych innych firm:

    - Włączanie archiwaowej skrzynki pocztowej. zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md) i [Włączanie automatycznego rozwijania archiwizacji](enable-autoexpanding-archiving.md). Pozwala to na wolne miejsce w podstawowej skrzynce pocztowej przez skonfigurowanie zasad archiwizacji, które przesuną elementy danych innych firm do archiwaowej skrzynki pocztowej. Zapewnia to do 1,5 TB przestrzeni dyskowej na dane innych firm.

    - Umieść skrzynkę pocztową danych innej firmy w  postępowaniem sądowym. W Centrum zabezpieczeń i zgodności Microsoft 365 zasady przechowywania. Umieszczenie tej skrzynki pocztowej w posiadaniu przechowuje elementy danych innych firm (przez czas nieograniczony lub przez określony czas) i zapobiega ich przeczyszczeniu ze skrzynki pocztowej. Zobacz jeden z następujących tematów:

      - [Umieść skrzynkę pocztową w  hold](./create-a-litigation-hold.md)

      - [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md)

    - Włączanie rejestrowania inspekcji skrzynki pocztowej dla właściciela, pełnomocnika i administratora do skrzynki pocztowej danych innej firmy. zobacz [Włączanie inspekcji skrzynki pocztowej](enable-mailbox-auditing.md). Umożliwia to inspekcję wszystkich działań wykonywanych przez każdego użytkownika, który ma dostęp do skrzynki pocztowej danych innej firmy.

## <a name="step-3-configure-user-mailboxes-for-third-party-data"></a>Krok 3. Konfigurowanie skrzynek pocztowych użytkowników na dane innych firm

Następnym krokiem jest skonfigurowanie skrzynek pocztowych użytkowników do obsługi danych innych firm. Możesz wykonać te zadania, korzystając Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">administracyjnego</a> lub odpowiednich Windows PowerShell cmdlet.

1. Włączyć archiwalne skrzynki pocztowe dla każdego użytkownika; zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md) i [Włączanie automatycznego rozwijania archiwizacji](enable-autoexpanding-archiving.md).

2. Umieść skrzynki pocztowe użytkowników w związku z postępowaniem sądowym lub zastosuj Microsoft 365 przechowywania. Zobacz jeden z następujących tematów:

    - [Umieść skrzynkę pocztową w  hold](./create-a-litigation-hold.md)

    - [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md)

    Jak wspomniano wcześniej, po zawieszaeniu skrzynek pocztowych można ustawić czas trwania przechowywania elementów ze źródła danych innej firmy lub określić czas nieograniczony przechowywania elementów.

## <a name="step-4-provide-your-partner-with-information"></a>Krok 4. Podanie partnerowi informacji

Ostatnim krokiem jest dostarczenie partnerowi poniższych informacji, aby on może skonfigurować łącznik w celu łączenia się z Twoją organizacją w celu importowania danych do skrzynek pocztowych użytkowników i skrzynek pocztowych danych innych firm.

- Punkt końcowy używany do łączenia się z usługą Azure w programie Microsoft 365:

    ```http
    https://office365ingestionsvc.gble1.protection.outlook.com/service/ThirdPartyIngestionService.svc
    ```

- Poświadczenia logowania (Microsoft 365 identyfikatora użytkownika i hasła) skrzynki pocztowej danych innej firmy utworzonej w kroku 2. Te poświadczenia są wymagane, aby łącznik partnera może uzyskać dostęp do skrzynek pocztowych użytkowników i innych skrzynek pocztowych danych oraz importować do nich elementy.

## <a name="step-5-register-the-third-party-data-connector-in-azure-active-directory"></a>Krok 5. Zarejestruj łącznik danych innej firmy w programie Azure Active Directory

Począwszy od 30 września 2018 r., usługa Azure w usłudze Microsoft 365 zacznie używać nowoczesnego uwierzytelniania w usłudze Exchange Online do uwierzytelniania łączników danych innych firm, które próbują połączyć się z Twoją organizacją w celu zaimportowania danych. Przyczyną tej zmiany jest to, że nowoczesne uwierzytelnianie zapewnia większe bezpieczeństwo niż bieżąca metoda, która opierała się na liście zezwalań dla łączników innych firm, które używają poprzednio opisanego punktu końcowego do łączenia się z usługą Azure.

Aby umożliwić łącznikowi danych innej firmy nawiązywanie połączenia z usługą Microsoft 365 przy użyciu nowej metody nowoczesnego uwierzytelniania, administrator w Twojej organizacji musi wyrazić zgodę na zarejestrowanie łącznika jako zaufanej aplikacji usługi w usłudze Azure Active Directory. W tym celu zaakceptowanie żądania uprawnień w celu zezwolenia łącznikowi na dostęp do danych organizacji w aplikacji Azure Active Directory. Po zaakceptowaniu tego żądania łącznik danych innej firmy jest dodawany jako aplikacja przedsiębiorstwa do usługi Azure Active Directory i reprezentowany jako podmiot zabezpieczeń usługi. Aby uzyskać więcej informacji na temat procesu wyrażania zgody, zobacz  [Zgoda administratora dzierżawy](/skype-sdk/trusted-application-api/docs/tenantadminconsent).

Oto procedura uzyskiwania dostępu do i akceptowania żądania zarejestrowania łącznika:

1. Przejdź do [tej strony](https://login.microsoftonline.com/common/oauth2/authorize?client_id=8dfbc50b-2111-4d03-9b4d-dd0d00aae7a2&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) i zaloguj się przy użyciu poświadczeń administratora globalnego.

   Zostanie wyświetlone poniższe okno dialogowe. Możesz rozwinąć daczki, aby sprawdzić uprawnienia, które zostaną przypisane do łącznika.

   ![Zostanie wyświetlone okno dialogowe żądania uprawnień.](../media/O365-ThirdPartyDataConnector-OptIn1.png)

2. Kliknij **przycisk Zaakceptuj**.

Po zaakceptowaniu żądania zostanie wyświetlony [Portal Azure](https://portal.azure.com) . Aby wyświetlić listę aplikacji dla organizacji, **kliknij pozycję** >  Azure Active Directory **Enterprise aplikacji**. Łącznik Microsoft 365 danych innych firm jest wymieniony na Enterprise **bladej aplikacji**.

> [!IMPORTANT]
> Po 30 września 2018 r. dane innych firm nie będą już importowane do skrzynek pocztowych w Twojej organizacji, jeśli nie zarejestrujesz łącznika danych innej firmy w programie Azure Active Directory. Należy zauważyć, że istniejące łączniki danych innych firm (utworzone przed 30 września 2018 r.) muszą również zostać zarejestrowane w programie Azure Active Directory zgodnie z procedurą podaną w kroku 5.

### <a name="revoking-consent-for-a-third-party-data-connector"></a>Cofanie zgody na łącznik danych innej firmy

Gdy organizacja zgonie się na żądanie uprawnień w celu zarejestrowania łącznika danych innej firmy w programie Azure Active Directory, organizacja może w dowolnym momencie cofnąć tę zgodę. Jednak odwołanie zgody dla łącznika oznacza, że dane z zewnętrznego źródła danych nie będą już importowane do Microsoft 365.

Aby odwołać zgodę dla łącznika danych innej firmy, możesz usunąć odpowiednią aplikację (przez usunięcie odpowiedniego podmiotu zabezpieczeń usługi) z usługi Azure Active Directory przy użyciu narzędzia **blade aplikacji Enterprise** w Portalu Azure lub przy użyciu polecenia [Remove-MsolServicePrincipal](/powershell/module/msonline/remove-msolserviceprincipal) w programie Microsoft 365 PowerShell. Możesz również użyć polecenia cmdlet [Remove-AzureADServicePrincipal](/powershell/module/azuread/remove-azureadserviceprincipal) w programie Azure Active Directory PowerShell.

## <a name="more-information"></a>Więcej informacji

- Jak wyjaśniono wcześniej, elementy ze źródeł danych innych firm są importowane do Exchange pocztowych jako wiadomości e-mail. Łącznik partnera zaim importuje element przy użyciu schematu wymaganego przez interfejs API Microsoft 365 API. W poniższej tabeli opisano właściwości wiadomości elementu ze źródła danych innej firmy po zaimportowaniu go do skrzynki pocztowej Exchange jako wiadomości e-mail. W tabeli znajduje się również informacja, czy właściwość wiadomości jest obowiązkowa. Obowiązkowe właściwości muszą zostać wypełnione. Jeśli brakuje obowiązkowej właściwości elementu, nie zostanie on zaimportowany do Microsoft 365. W procesie importowania jest zwracany komunikat o błędzie wyjaśniający, dlaczego nie zaimportowano elementu i której właściwości brakuje.<br/><br/>

    |**Właściwość message**|**Obowiązkowy?**|**Opis**|**Wartość przykładowa**|
    |:-----|:-----|:-----|:-----|
    |**FROM** <br/> |Tak  <br/> |Użytkownik, który pierwotnie utworzył lub wysłał element w innym źródle danych. Łącznik partnera próbuje zamapować identyfikator użytkownika z elementu źródłowego (na przykład uchwytu serwisu Twitter) na konto użytkownika dla wszystkich uczestników (użytkowników w polach FROM i TO). Kopia wiadomości zostanie zaimportowana do skrzynki pocztowej każdego uczestnika. Jeśli żadnego z uczestników tego elementu nie można zamapować na konto użytkownika, element zostanie zaimportowany do archiwalnej skrzynki pocztowej innej firmy w programie Microsoft 365.  <br/> <br/> Uczestnik, który jest identyfikowany jako nadawca elementu, musi mieć aktywną skrzynkę pocztową w organizacji, do których jest importowany. Jeśli nadawca nie ma aktywnej skrzynki pocztowej, jest zwracany następujący błąd:<br/><br/>  `One or more messages in the Request failed to be delivered to either From or Sender email address. You will need to resend your entire Request. Error: The request failed. The remote server returned an error: (401) Unauthorized.`  | `bob@contoso.com` <br/> |
    |**TO** <br/> |Tak  <br/> |Użytkownik, który otrzymał element, jeśli dotyczy elementu w źródle danych.  <br/> | `bob@contoso.com` <br/> |
    |**TEMAT** <br/> |Nie  <br/> |Temat elementu źródłowego.  <br/> | `"Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/> |
    |**DATE** <br/> |Tak  <br/> |Data pierwotnie utworzonego lub opublikowanego elementu w źródle danych klienta. Może to być na przykład data przesłania wiadomości w serwisie Twitter w serwisie Twitter.  <br/> | `01 NOV 2015` <br/> |
    |**BODY (TREŚĆ)** <br/> |Nie  <br/> |Treść wiadomości lub wpisu. W przypadku niektórych źródeł danych zawartość tej właściwości może być taka sama jak **zawartość właściwości SUBJECT** . W trakcie procesu importowania łącznik partnera próbuje zachować pełną wierność ze źródła zawartości, jak to tylko możliwe. Jeśli możliwe pliki, grafika lub inna zawartość z treści elementu źródłowego jest uwzględniana w tej właściwości. W przeciwnym razie zawartość elementu źródłowego jest uwzględniana we właściwości **ZAŁĄCZNIK** . Zawartość tej właściwości zależy od łącznika partnera i możliwości platformy źródłowej.  <br/> | `Author: bob@contoso.com` <br/>  `Date: 10 DEC 2014` <br/>  `Tweet: "Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/>  `Date: 01 NOV 2015` <br/> |
    |**ZAŁĄCZNIK** <br/> |Nie  <br/> |Jeśli element w źródle danych (na przykład tweet w serwisie Twitter lub konwersacja za pomocą wiadomości błyskawicznych) ma dołączony plik lub obrazy, partner w programie Connect najpierw spróbuje dołączyć załączniki we właściwości **BODY** . Jeśli nie jest to możliwe, zostanie on dodany do właściwości ** ZAŁĄCZNIK **. Inne przykłady załączników to polubień w serwisie Facebook, metadanych ze źródła zawartości oraz odpowiedzi na wiadomość lub wpis.  <br/> | `image.gif` <br/> |
    |**MESSAGECLASS** <br/> |Tak  <br/> | Jest to właściwość wielowymiarowa, która jest tworzona i wypełniana przez łącznik partnera. Format tej właściwości to  `IPM.NOTE.Source.Event`. (Ta właściwość musi zaczynać się od  `IPM.NOTE`. Ten format jest podobny do formatu klasy  `IPM.NOTE.X` wiadomości). Ta właściwość zawiera następujące informacje:  <br/><br/>`Source`: wskazuje źródło danych innej firmy. na przykład Twitter, Facebook lub BlackBerry.  <br/> <br/>  `Event`— wskazuje typ działania wykonanego w źródle danych innej firmy, w przypadku których te elementy zostały wyprodukowana; na przykład tweet w serwisie Twitter lub wpis w serwisie Facebook. Zdarzenia są specyficzne dla źródła danych.  <br/> <br/>  Jedną z tych właściwości jest filtrowanie określonych elementów na podstawie źródła danych, z którego pochodził element lub na podstawie typu zdarzenia. Na przykład podczas wyszukiwania zbierania elektronicznych materiałów dowodowych możesz utworzyć zapytanie wyszukiwania w celu znalezienia wszystkich tweetów opublikowanych przez określonego użytkownika.  <br/> | `IPM.NOTE.Twitter.Tweet` <br/> |

- Gdy elementy zostaną pomyślnie zaimportowane do skrzynek Microsoft 365 w programie identyfikator unikatowy, w ramach odpowiedzi HTTP jest zwracana identyfikator unikatowy adresata. Ten identyfikator, nazywany  `x-IngestionCorrelationID`, może być używany przez partnerów do dalszych celów rozwiązywania problemów w celu śledzenia wszystkich elementów. Zalecane jest przechwytywanie tych informacji przez partnerów i rejestrowanie ich odpowiednio na ich końcu. Oto przykład odpowiedzi HTTP pokazującej ten identyfikator:

    ```http
    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Server: Microsoft-IIS/8.5
    x-IngestionCorrelationID: 1ec7667d-f097-47fe-a9a2-bc7ab0a7552b
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 02 Feb 2016 22:55:33 GMT
    ```

- Za pomocą narzędzia Wyszukiwanie zawartości w Centrum zabezpieczeń i zgodności możesz wyszukiwać elementy zaimportowane do skrzynek pocztowych z zewnętrznego źródła danych. Aby wyszukać konkretnie te zaimportowane elementy, w polu słowa kluczowego przeszukiwania zawartości możesz użyć następujących par właściwości-wartość komunikatu.

  - **`kind:externaldata`**: Ta para wartość właściwości pozwala przeszukiwać wszystkie typy danych innych firm. Aby na przykład wyszukać elementy zaimportowane ze źródła danych innej firmy i zawierające wyraz "contoso" we właściwości Temat importowanego elementu, użyj zapytania słowa kluczowego  `kind:externaldata AND subject:contoso`.

  - **`itemclass:ipm.externaldata.<third-party data type>`**: Tej pary wartość właściwości należy używać tylko do wyszukiwania danych typu danych innych firm. Aby na przykład przeszukiwać tylko dane serwisu Facebook, które zawierają wyraz "contoso" we właściwości Temat, użyj zapytania słowa kluczowego  `itemclass:ipm.externaldata.Facebook* AND subject:contoso`.

  Aby uzyskać pełną listę `itemclass` wartości, których można użyć dla typów danych innych firm dla tej właściwości, zobacz Używanie wyszukiwania zawartości do wyszukiwania danych innych firm, które zaimportowano do [Microsoft 365](use-content-search-to-search-third-party-data-that-was-imported.md).

   Aby uzyskać więcej informacji na temat korzystania z wyszukiwania zawartości i tworzenia zapytań wyszukiwania słów kluczowych, zobacz:

  - [Przeszukiwanie zawartości](content-search.md)

  - [Zapytania słów kluczowych i warunki wyszukiwania dla przeszukiwania zawartości](keyword-queries-and-search-conditions.md)