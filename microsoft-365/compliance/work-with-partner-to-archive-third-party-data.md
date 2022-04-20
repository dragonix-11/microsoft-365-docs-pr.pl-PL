---
title: Współpraca z partnerem w celu archiwizowania danych innych firm
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
description: Dowiedz się, jak skonfigurować łącznik niestandardowy do importowania danych innych firm ze źródeł danych, takich jak Salesforce Chatter, Yahoo Messenger lub Yammer.
ms.openlocfilehash: 72159d88cdeb8c573f1a71342ca7cbd015099568
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944508"
---
# <a name="work-with-a-partner-to-archive-third-party-data"></a>Współpraca z partnerem w celu archiwizowania danych innych firm

Możesz współpracować z partnerem firmy Microsoft, aby zaimportować i zarchiwizować dane ze źródła danych innej firmy, aby Microsoft 365. Partner może zapewnić łącznik niestandardowy, który jest skonfigurowany do wyodrębniania elementów ze źródła danych innych firm (regularnie), a następnie importowania tych elementów. Łącznik partnera konwertuje zawartość elementu ze źródła danych na format wiadomości e-mail, a następnie przechowuje elementy w skrzynkach pocztowych. Po zaimportowaniu danych innych firm można zastosować do tych danych funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, In-Place archiwizowanie, inspekcja i zasady przechowywania Microsoft 365.

> [!IMPORTANT]
> Rozwiązania [do zgodności z komunikacją](communication-compliance.md) w Microsoft 365 nie można zastosować do danych innych firm zaimportowanych przez łączniki partnerów wymienione w tym artykule.

Oto omówienie procesu i czynności niezbędnych do współpracy z partnerem firmy Microsoft w celu zaimportowania danych innych firm.

[Krok 1. Znajdowanie partnera danych innej firmy](#step-1-find-a-third-party-data-partner)

[Krok 2. Tworzenie i konfigurowanie skrzynki pocztowej danych innej firmy](#step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365)

[Krok 3. Konfigurowanie skrzynek pocztowych użytkowników dla danych innych firm](#step-3-configure-user-mailboxes-for-third-party-data)

[Krok 4. Podawanie partnerowi informacji](#step-4-provide-your-partner-with-information)

[Krok 5. Rejestrowanie łącznika danych innej firmy w Azure Active Directory](#step-5-register-the-third-party-data-connector-in-azure-active-directory)

## <a name="how-the-third-party-data-import-process-works"></a>Jak działa proces importowania danych innych firm

Poniższa ilustracja i opis wyjaśniają, jak działa proces importowania danych innych firm podczas pracy z partnerem.

![Jak działa proces importowania danych innych firm.](../media/5d4cf8e9-b4cc-4547-90c8-d12d04a9f0e7.png)

1. Klient współpracuje z wybranym partnerem, aby skonfigurować łącznik, który wyodrębni elementy ze źródła danych innej firmy, a następnie zaimportuje te elementy do Microsoft 365.

2. Łącznik partnera łączy się ze źródłami danych innych firm za pośrednictwem interfejsu API innej firmy (zgodnie z harmonogramem lub zgodnie z konfiguracją) i wyodrębnia elementy ze źródła danych. Łącznik partnera konwertuje zawartość elementu na format wiadomości e-mail. Zobacz sekcję [Więcej informacji](#more-information) , aby uzyskać opis schematu formatu wiadomości.

3. Łącznik partnerski łączy się z usługą platformy Azure w Microsoft 365 przy użyciu usługi Exchange Web Service (EWS) za pośrednictwem dobrze znanego punktu końcowego.

4. Elementy są importowane do skrzynki pocztowej określonego użytkownika lub do skrzynki pocztowej danych "catch-all" innej firmy. To, czy element jest importowany do określonej skrzynki pocztowej użytkownika, czy do skrzynki pocztowej danych innej firmy, jest oparte na następujących kryteriach:

   1. **Elementy, które mają identyfikator użytkownika odpowiadający kontu użytkownika:** Jeśli łącznik partnera może mapować identyfikator użytkownika elementu w źródle danych innej firmy na określony identyfikator użytkownika w Microsoft 365, element jest kopiowany do folderu **Przeczyszczanie** w folderze Elementy możliwe do odzyskania użytkownika. Użytkownicy nie mogą uzyskać dostępu do elementów w folderze Przeczyszczanie. Można jednak użyć narzędzi zbierania elektronicznych materiałów dowodowych do wyszukiwania elementów w folderze Przeczyszczanie.

   1. **Elementy, które nie mają identyfikatora użytkownika odpowiadającego kontu użytkownika:** Jeśli łącznik partnera nie może zamapować identyfikatora użytkownika elementu na określony identyfikator użytkownika, element zostanie skopiowany do folderu **Skrzynka odbiorcza** skrzynki pocztowej danych innej firmy. Importowanie elementów do skrzynki odbiorczej umożliwia Tobie lub innej osobie w organizacji zalogowanie się do skrzynki pocztowej innej firmy w celu wyświetlenia tych elementów i zarządzania nimi oraz sprawdzenie, czy w konfiguracji łącznika partnera należy wprowadzić jakiekolwiek zmiany.

## <a name="step-1-find-a-third-party-data-partner"></a>Krok 1. Znajdowanie partnera danych innej firmy

Kluczowym składnikiem archiwizacji danych innych firm w Microsoft 365 jest znalezienie i współpraca z partnerem firmy Microsoft, który specjalizuje się w przechwytywaniu danych ze źródła danych innych firm i importowaniu ich do Microsoft 365. Po zaimportowaniu danych można je archiwizować i zachowywać wraz z innymi danymi firmy Microsoft organizacji, takimi jak poczta e-mail z Exchange i dokumentów z SharePoint i OneDrive dla Firm. Partner tworzy łącznik, który wyodrębnia dane ze źródeł danych innych firm (takich jak BlackBerry, Facebook, Google+, Thomson Reuters, Twitter i YouTube) i przekazuje te dane do interfejsu API Microsoft 365, który importuje elementy do Exchange skrzynek pocztowych jako wiadomości e-mail.

W poniższych sekcjach wymieniono partnerów firmy Microsoft (i obsługiwane przez nich źródła danych innych firm), którzy uczestniczą w programie archiwizacji danych innych firm w Microsoft 365.

[17a-4 LLC](#17a-4-llc)

[ArchiveSocial](#archivesocial)

[Veritas](#veritas)

[Opentext](#opentext)

[Smarsh](#smarsh)

[Verba](#verba)

### <a name="17a-4-llc"></a>17a-4 LLC

[17a-4 LLC](https://www.17a-4.com) obsługuje następujące źródła danych innych firm:

- Blackberry

- Bloomberg Data Strumienie

- Cisco Jabber

- FactSet

- HipChat

- InvestEdge

- LivePerson

- MessageLabs Data Strumienie

- Opentext

- Oracle/ATG — "kliknij, aby zadzwonić" — Pomoc na żywo

- Imtrader przestawny

- Microsoft SharePoint

- MindAlign

- Sitrion One (Newsgator)

- Skype dla firm (Lync/OCS)

- Skype dla firm Online (Lync Online)

- bazy danych SQL

- Squawker

- Thomson Reuters Eikon Messenger

### <a name="archivesocial"></a>ArchiveSocial

[Aplikacja ArchiveSocial](https://www.archivesocial.com) obsługuje następujące źródła danych innych firm:

- Facebook

- Flickr

- Instagram

- LinkedIn

- Pinterest

- Twitter

- YouTube

- Vimeo

### <a name="veritas"></a>Veritas

[Usługa Veritas](https://www.globanet.com) obsługuje następujące źródła danych innych firm:

- AOL z klientem przestawnym

- Dzienniki połączeń BlackBerry (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- Bloomberg Chat

- Bloomberg Mail

- Pole

- CipherCloud for Salesforce Chatter

- Cisco IM &amp; Presence Server (v10, v10.5.1 SU1, v11.0, v11.5 SU2)

- Cisco Webex Teams

- Plik sharefile obszaru roboczego &amp; Citrix

- CrowdCompass

- Pliki tekstowe rozdzielane niestandardowo

- Niestandardowe pliki XML

- Facebook (strony)

- Zestaw faktów

- FXConnect

- ICE Chat/YellowJacket

- Jive

- Macgregor XIP

- Microsoft Exchange Server

- Microsoft OneDrive dla Firm

- Microsoft Teams

- Microsoft Yammer

- Mobile Guard

- Dokument bazowy

- Czat w usłudze Salesforce

- Skype dla firm Online

- Skype dla firm, wersje 2007 R2 – 2016 (lokalnie)

- Slack Enterprise Grid

- Symphony

- Thomson Reuters Eikon

- Thomson Reuters Messenger

- Thomson Reuters Dealings 3000 / FX Trading

- Twitter

- Czat UBS

- YouTube

### <a name="opentext"></a>Opentext

[Program OpenText](https://www.opentext.com/what-we-do/products/opentext-product-offerings-catalog/rebranded-products/daegis) obsługuje następujące źródła danych innych firm:

- Axs Encrypted

- Axs Exchange

- Archiwum lokalne usługi Axs

- Symbol zastępczy usługi Axs

- Podpisane przez usługę Axs

- Bloomberg

- Thomson Reuters

### <a name="smarsh"></a>Smarsh

[Program Smarsh](https://www.smarsh.com) obsługuje następujące źródła danych innych firm:

- CELEM

- Amerykański idol

- Sok jabłkowy

- AOL z klientem przestawnym

- Ares

- Bazar Voice

- Bear Share

- Bit Torrent

- Dzienniki połączeń BlackBerry (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- Bloomberg Mail

- CellTrust

- Importowanie czatu

- Rejestrowanie i zasady czatu w czasie rzeczywistym

- Gadać

- Cisco IM &amp; Presence Server (v9.0.1, v9.1, v9.1.1 SU1, v10, v10.5.1 SU1)

- Cisco Unified Presence Server (wersja 8.6.3, wersja 8.6.4, wersja 8.6.5)

- Importowanie współpracy

- Rejestrowanie współpracy w czasie rzeczywistym

- Połączenie bezpośredni

- Facebook

- FactSet

- FastTrack

- Gnutella

- Google+

- GoToMyPC

- Hopster

- HubConnex

- Połączenia IBM (v3.0.1, v4.0, v4.5, v4.5 CR3, v5)

- IBM Connections Chat Cloud

- Chmura społecznościowa połączeń IBM

- IBM SameTime Advanced 8.5.2 IFR1

- IBM SameTime Communicate 9.0

- IBM SameTime Community (v8.0.2, v8.5.1 IFR2, v8.5.2 IFR1, v9.1)

- IBM SameTime Complete 9.0

- IBM SameTime Conference 9.0

- IBM SameTime Meeting 8.5.2 IFR1

- ICE/YellowJacket

- Importowanie wiadomości błyskawicznych

- Rejestrowanie i zasady w czasie rzeczywistym wiadomości błyskawicznych

- Indii Messenger

- Instant Bloomberg

- IRC

- Jive

- Rejestrowanie Jive 6 w czasie rzeczywistym (wersja 6, wersja 7)

- Jive Import

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

- Moje miejsce

- NEONetwork

- Microsoft 365 dedykowany program Lync

- Microsoft 365 udostępnionej wiadomości błyskawicznej

- Pinterest

- Dokument bazowy

- QQ

- Skype dla firm 2015

- Softether

- Symphony

- Thomson Reuters Eikon

- Thomson Reuters Messenger

- Tor

- TTT

- Twitter

- Winmx

- Winny

- Yahoo

- Yammer

- YouTube


### <a name="verba"></a>Verba

[Verba](https://www.verba.com) obsługuje następujące źródła danych innych firm:

- Avaya Aura Wideo

- Avaya Aura Voice

- Avtec Radio

- Bosch/Telex Radio

- BroadSoft Video

- BroadSoft Voice

- Głos centyla

- Cisco Jabber — wiadomości błyskawiczne

- Wideo Cisco UC

- Cisco UC Voice

- Cisco UCCX/UCCE Wideo

- Cisco UCCX/UCCE Voice

- ESChat Radio

- Geoman Contact Expert

- IP Trade Voice

- Luware LUCS Contact Center

- Microsoft UC (Unified Communications)

- Mitel MiContact Center for Lync (prairieFyre)

- Wideo kontrolera obramowania sesji pakietów Oracle/Acme

- Głos kontrolera obramowania sesji pakietów Oracle/Acme

- Singtel Mobile Voice

- Wideo SIPREC

-  SIPREC Voice

- Skype dla firm / Lync IM

- Skype dla firm / Lync Wideo

- Skype dla firm /Lync Voice

- Speakerbus Voice

- Wideo w standardzie SIP/H.323

- Standardowa SIP/H.323 Voice

- Truphone Voice

- TwistedPair Radio

- ekran komputera stacjonarnego Windows

## <a name="step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365"></a>Krok 2. Tworzenie i konfigurowanie skrzynki pocztowej danych innej firmy w Microsoft 365

Poniżej przedstawiono kroki tworzenia i konfigurowania skrzynki pocztowej danych innych firm na potrzeby importowania danych do Microsoft 365. Jak wyjaśniono wcześniej, elementy są importowane do tej skrzynki pocztowej, jeśli łącznik partnera nie może zamapować identyfikatora użytkownika elementu na konto użytkownika.

 **Wykonaj te zadania w Centrum administracyjne platformy Microsoft 365**

1. Utwórz konto użytkownika i przypisz mu licencję Exchange Online Plan 2. Zobacz [Dodawanie użytkowników do Microsoft 365](../admin/add-users/add-users.md). Licencja planu 2 jest wymagana do umieszczenia skrzynki pocztowej w blokadzie postępowania sądowego lub włączenia archiwum skrzynki pocztowej z limitem przydziału magazynu do 1,5 TB.

2. Dodaj konto użytkownika skrzynki pocztowej danych innej firmy do roli administratora **Exchange administratora** w Microsoft 365. Zobacz [Przypisywanie ról administratora w Microsoft 365](../admin/add-users/assign-admin-roles.md).

    > [!TIP]
    > Zapisz poświadczenia dla tego konta użytkownika. Należy je udostępnić partnerowi zgodnie z opisem w kroku 4.

 **Wykonaj te zadania w centrum administracyjnym Exchange**

1. Ukryj skrzynkę pocztową danych innych firm przed książką adresową i innymi listami adresów w organizacji; Zobacz [Zarządzanie skrzynkami pocztowymi użytkowników](/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes). Alternatywnie możesz uruchomić następujące polecenie programu PowerShell:

    ```powershell
    Set-Mailbox -Identity <identity of third-party data mailbox> -HiddenFromAddressListsEnabled $true
    ```

2. Przypisz **uprawnienie FullAccess** do skrzynki pocztowej danych innych firm, aby administratorzy lub funkcjonariusze zgodności mogli otworzyć skrzynkę pocztową danych innej firmy w kliencie stacjonarnym Outlook. Zobacz [Zarządzanie uprawnieniami adresatów](https://go.microsoft.com/fwlink/p/?LinkId=692104).

3. Włącz następujące funkcje związane ze zgodnością dla skrzynki pocztowej danych innych firm:

    - Włącz skrzynkę pocztową archiwum; Zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md) i [Włączanie automatycznego rozszerzania archiwizacji](enable-autoexpanding-archiving.md). Dzięki temu można zwolnić miejsce do magazynowania w podstawowej skrzynce pocztowej, konfigurując zasady archiwum, które przenosi elementy danych innych firm do skrzynki pocztowej archiwum. Zapewnia to maksymalnie 1,5 TB miejsca do magazynowania danych innych firm.

    - Umieść skrzynkę pocztową danych innych firm w blokadzie postępowania sądowego. Można również zastosować zasady przechowywania Microsoft 365 w centrum zabezpieczeń i zgodności. Umieszczenie tej skrzynki pocztowej w blokadzie zachowuje elementy danych innych firm (na czas nieokreślony lub przez określony czas) i uniemożliwia ich przeczyszczanie ze skrzynki pocztowej. Zobacz jeden z następujących tematów:

      - [Umieszczanie skrzynki pocztowej w blokadzie postępowania sądowego](./create-a-litigation-hold.md)

      - [Dowiedz się więcej o zasadach przechowywania i etykietach przechowywania](retention.md)

    - Włącz rejestrowanie inspekcji skrzynki pocztowej dla właściciela, pełnomocnika i administratora dostępu do skrzynki pocztowej danych innych firm; Zobacz [Włączanie inspekcji skrzynek pocztowych](enable-mailbox-auditing.md). Umożliwia to przeprowadzanie inspekcji wszystkich działań wykonywanych przez każdego użytkownika, który ma dostęp do skrzynki pocztowej danych innej firmy.

## <a name="step-3-configure-user-mailboxes-for-third-party-data"></a>Krok 3. Konfigurowanie skrzynek pocztowych użytkowników dla danych innych firm

Następnym krokiem jest skonfigurowanie skrzynek pocztowych użytkowników w celu obsługi danych innych firm. Wykonaj te zadania przy użyciu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange</a> lub przy użyciu odpowiednich poleceń cmdlet Windows PowerShell.

1. Włącz skrzynkę pocztową archiwum dla każdego użytkownika; Zobacz [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md) i [Włączanie automatycznego rozszerzania archiwizacji](enable-autoexpanding-archiving.md).

2. Umieść skrzynki pocztowe użytkowników w blokadzie postępowania sądowego lub zastosuj zasady przechowywania Microsoft 365; zobacz jeden z następujących tematów:

    - [Umieszczanie skrzynki pocztowej w blokadzie postępowania sądowego](./create-a-litigation-hold.md)

    - [Dowiedz się więcej o zasadach przechowywania i etykietach przechowywania](retention.md)

    Jak wspomniano wcześniej, po umieszczeniu skrzynek pocztowych w stanie wstrzymania można ustawić czas przechowywania elementów ze źródła danych innej firmy lub zdecydować się na przechowywanie elementów na czas nieokreślony.

## <a name="step-4-provide-your-partner-with-information"></a>Krok 4. Podawanie partnerowi informacji

Ostatnim krokiem jest dostarczenie partnerowi następujących informacji, aby mógł skonfigurować łącznik w celu nawiązania połączenia z organizacją w celu zaimportowania danych do skrzynek pocztowych użytkowników i do skrzynki pocztowej danych innych firm.

- Punkt końcowy używany do nawiązywania połączenia z usługą platformy Azure w Microsoft 365:

    ```http
    https://office365ingestionsvc.gble1.protection.outlook.com/service/ThirdPartyIngestionService.svc
    ```

- Poświadczenia logowania (Microsoft 365 identyfikator użytkownika i hasło) skrzynki pocztowej danych innej firmy utworzonej w kroku 2. Te poświadczenia są wymagane, aby łącznik partnera mógł uzyskiwać dostęp do elementów i importować je do skrzynek pocztowych użytkowników i do skrzynki pocztowej danych innych firm.

## <a name="step-5-register-the-third-party-data-connector-in-azure-active-directory"></a>Krok 5. Rejestrowanie łącznika danych innej firmy w Azure Active Directory

Od 30 września 2018 r. usługa platformy Azure w Microsoft 365 zacznie używać nowoczesnego uwierzytelniania w Exchange Online do uwierzytelniania łączników danych innych firm, które próbują nawiązać połączenie z organizacją w celu zaimportowania danych. Przyczyną tej zmiany jest to, że nowoczesne uwierzytelnianie zapewnia większe bezpieczeństwo niż bieżąca metoda oparta na liście dozwolonych łączników innych firm, które używają wcześniej opisanego punktu końcowego do nawiązywania połączenia z usługą platformy Azure.

Aby umożliwić łącznikowi danych innej firmy nawiązywanie połączenia z Microsoft 365 przy użyciu nowej nowoczesnej metody uwierzytelniania, administrator w organizacji musi wyrazić zgodę na zarejestrowanie łącznika jako zaufanej aplikacji usługi w Azure Active Directory. Odbywa się to przez zaakceptowanie żądania uprawnień, aby umożliwić łącznikowi dostęp do danych organizacji w Azure Active Directory. Po zaakceptowaniu tego żądania łącznik danych innej firmy jest dodawany jako aplikacja dla przedsiębiorstw do Azure Active Directory i reprezentowany jako jednostka usługi. Aby uzyskać więcej informacji na temat procesu wyrażania zgody, zobacz  [Zgoda administratora dzierżawy](/skype-sdk/trusted-application-api/docs/tenantadminconsent).

Poniżej przedstawiono kroki uzyskiwania dostępu do łącznika i akceptowania żądania zarejestrowania łącznika:

1. Przejdź do [tej strony](https://login.microsoftonline.com/common/oauth2/authorize?client_id=8dfbc50b-2111-4d03-9b4d-dd0d00aae7a2&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) i zaloguj się przy użyciu poświadczeń administratora globalnego.

   Zostanie wyświetlone następujące okno dialogowe. Możesz rozwinąć daszki, aby przejrzeć uprawnienia, które zostaną przypisane do łącznika.

   ![Zostanie wyświetlone okno dialogowe żądania uprawnień.](../media/O365-ThirdPartyDataConnector-OptIn1.png)

2. Kliknij pozycję **Zaakceptuj**.

Po zaakceptowaniu żądania zostanie wyświetlony [Azure Portal](https://portal.azure.com). Aby wyświetlić listę aplikacji dla organizacji, kliknij pozycję **Azure Active Directory** >  **Enterprise aplikacje**. Łącznik danych Microsoft 365 innej firmy znajduje się w bloku **aplikacji Enterprise**.

> [!IMPORTANT]
> Po 30 września 2018 r. dane innych firm nie będą już importowane do skrzynek pocztowych w organizacji, jeśli nie zarejestrujesz łącznika danych innej firmy w Azure Active Directory. Należy pamiętać, że istniejące łączniki danych innych firm (utworzone przed 30 września 2018 r.) również muszą zostać zarejestrowane w Azure Active Directory, wykonując procedurę opisaną w kroku 5.

### <a name="revoking-consent-for-a-third-party-data-connector"></a>Odwoływanie zgody dla łącznika danych innej firmy

Po wyrażeniu zgody organizacji na żądanie uprawnień w celu zarejestrowania łącznika danych innej firmy w Azure Active Directory organizacja może w dowolnym momencie odwołać tę zgodę. Jednak odwołanie zgody dla łącznika oznacza, że dane ze źródła danych innej firmy nie będą już importowane do Microsoft 365.

Aby odwołać zgodę na łącznik danych innej firmy, możesz usunąć aplikację (usuwając odpowiednią jednostkę usługi) z Azure Active Directory przy użyciu bloku **aplikacji Enterprise** w Azure Portal lub przy użyciu polecenia [Remove-MsolServicePrincipal](/powershell/module/msonline/remove-msolserviceprincipal) w Microsoft 365 Powershell. Możesz również użyć polecenia cmdlet [Remove-AzureADServicePrincipal](/powershell/module/azuread/remove-azureadserviceprincipal) w programie Azure Active Directory programu PowerShell.

## <a name="more-information"></a>Więcej informacji

- Jak wyjaśniono wcześniej, elementy ze źródeł danych innych firm są importowane do Exchange skrzynek pocztowych jako wiadomości e-mail. Łącznik partnera importuje element przy użyciu schematu wymaganego przez interfejs API Microsoft 365. W poniższej tabeli opisano właściwości wiadomości elementu ze źródła danych innej firmy po jego zaimportowaniu do skrzynki pocztowej Exchange jako wiadomość e-mail. Tabela wskazuje również, czy właściwość komunikatu jest obowiązkowa. Właściwości obowiązkowe muszą być wypełnione. Jeśli w elemencie brakuje właściwości obowiązkowej, nie zostanie on zaimportowany do Microsoft 365. Proces importowania zwraca komunikat o błędzie wyjaśniający, dlaczego element nie został zaimportowany i której właściwości brakuje.<br/><br/>

    |**Właściwość message**|**Obowiązkowe?**|**Opis**|**Przykładowa wartość**|
    |:-----|:-----|:-----|:-----|
    |**Z** <br/> |Tak  <br/> |Użytkownik, który pierwotnie utworzył lub wysłał element w źródle danych innej firmy. Łącznik partnera próbuje zamapować identyfikator użytkownika z elementu źródłowego (na przykład dojścia twitterowego) na konto użytkownika dla wszystkich uczestników (użytkowników w polach OD i DO). Kopia wiadomości zostanie zaimportowana do skrzynki pocztowej każdego uczestnika. Jeśli żaden z uczestników z elementu nie może zostać zamapowany na konto użytkownika, element zostanie zaimportowany do skrzynki pocztowej archiwizacji innej firmy w Microsoft 365.  <br/> <br/> Uczestnik zidentyfikowany jako nadawca elementu musi mieć aktywną skrzynkę pocztową w organizacji, do którą jest importowany element. Jeśli nadawca nie ma aktywnej skrzynki pocztowej, zwracany jest następujący błąd:<br/><br/>  `One or more messages in the Request failed to be delivered to either From or Sender email address. You will need to resend your entire Request. Error: The request failed. The remote server returned an error: (401) Unauthorized.`  | `bob@contoso.com` <br/> |
    |**DO** <br/> |Tak  <br/> |Użytkownik, który otrzymał element, jeśli ma zastosowanie do elementu w źródle danych.  <br/> | `bob@contoso.com` <br/> |
    |**TEMAT** <br/> |Nie  <br/> |Temat z elementu źródłowego.  <br/> | `"Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/> |
    |**DATA** <br/> |Tak  <br/> |Data utworzenia lub opublikowania elementu w źródle danych klienta. Na przykład ta data, kiedy wiadomość w serwisie Twitter została opublikowana na Twitterze.  <br/> | `01 NOV 2015` <br/> |
    |**CIAŁA** <br/> |Nie  <br/> |Zawartość wiadomości lub wpisu. W przypadku niektórych źródeł danych zawartość tej właściwości może być taka sama jak zawartość właściwości **SUBJECT** . Podczas procesu importowania łącznik partnera stara się zachować pełną wierność ze źródła zawartości, jak to możliwe. Jeśli możliwe pliki, grafika lub inna zawartość z treści elementu źródłowego są zawarte w tej właściwości. W przeciwnym razie zawartość elementu źródłowego jest uwzględniana we właściwości **ATTACHMENT** . Zawartość tej właściwości zależy od łącznika partnera i możliwości platformy źródłowej.  <br/> | `Author: bob@contoso.com` <br/>  `Date: 10 DEC 2014` <br/>  `Tweet: "Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/>  `Date: 01 NOV 2015` <br/> |
    |**ZAŁĄCZNIK** <br/> |Nie  <br/> |Jeśli element w źródle danych (na przykład tweet w usłudze Twitter lub konwersacja w wiadomościach błyskawicznych) ma dołączony plik lub dołącz obrazy, partner connect najpierw podejmie próbę uwzględnienia załączników we właściwości **BODY** . Jeśli nie jest to możliwe, zostanie on dodany do właściwości ** ZAŁĄCZNIK **. Inne przykłady załączników obejmują polubienia w serwisie Facebook, metadane ze źródła zawartości oraz odpowiedzi na wiadomość lub wpis.  <br/> | `image.gif` <br/> |
    |**MESSAGECLASS** <br/> |Tak  <br/> | Jest to właściwość wielowartościowa, która jest tworzona i wypełniana przez łącznik partnera. Format tej właściwości to  `IPM.NOTE.Source.Event`. (Ta właściwość musi zaczynać się od  `IPM.NOTE`. Ten format jest podobny do formatu  `IPM.NOTE.X` klasy message). Ta właściwość zawiera następujące informacje:  <br/><br/>`Source`: wskazuje źródło danych innej firmy; na przykład Twitter, Facebook lub BlackBerry.  <br/> <br/>  `Event`: wskazuje typ działania, które zostało wykonane w źródle danych innej firmy, które wygenerowało elementy; na przykład tweet w serwisie Twitter lub wpis w serwisie Facebook. Zdarzenia są specyficzne dla źródła danych.  <br/> <br/>  Jednym z celów tej właściwości jest filtrowanie określonych elementów na podstawie źródła danych, z którego pochodzi element, lub na podstawie typu zdarzenia. Na przykład w wyszukiwaniu zbierania elektronicznych materiałów dowodowych można utworzyć zapytanie wyszukiwania, aby znaleźć wszystkie tweety, które zostały opublikowane przez określonego użytkownika.  <br/> | `IPM.NOTE.Twitter.Tweet` <br/> |

- Po pomyślnym zaimportowaniu elementów do skrzynek pocztowych w Microsoft 365 unikatowy identyfikator jest zwracany do obiektu wywołującego w ramach odpowiedzi HTTP. Ten identyfikator o nazwie  `x-IngestionCorrelationID`, może być używany do kolejnych celów rozwiązywania problemów przez partnerów w celu kompleksowego śledzenia elementów. Zaleca się, aby partnerzy przechwycili te informacje i zarejestrowali je odpowiednio na końcu. Oto przykład odpowiedzi HTTP pokazującej ten identyfikator:

    ```http
    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Server: Microsoft-IIS/8.5
    x-IngestionCorrelationID: 1ec7667d-f097-47fe-a9a2-bc7ab0a7552b
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 02 Feb 2016 22:55:33 GMT
    ```

- Za pomocą narzędzia wyszukiwanie zawartości w centrum zabezpieczeń i zgodności można wyszukiwać elementy, które zostały zaimportowane do skrzynek pocztowych ze źródła danych innej firmy. Aby wyszukać te zaimportowane elementy, możesz użyć następujących par właściwości-wartości komunikatu w polu słowa kluczowego dla wyszukiwania zawartości.

  - **`kind:externaldata`**: użyj tej pary właściwości-wartości, aby wyszukać wszystkie typy danych innych firm. Aby na przykład wyszukać elementy, które zostały zaimportowane ze źródła danych innej firmy i zawierały słowo "contoso" we właściwości Podmiot zaimportowanego elementu, należy użyć zapytania  `kind:externaldata AND subject:contoso`kluczowego .

  - **`itemclass:ipm.externaldata.<third-party data type>`**: użyj tej pary właściwości-wartości, aby wyszukać tylko określony typ danych innych firm. Na przykład aby wyszukać tylko dane serwisu Facebook zawierające słowo "contoso" we właściwości Podmiot, należy użyć zapytania  `itemclass:ipm.externaldata.Facebook* AND subject:contoso`słowa kluczowego .

  Aby uzyskać pełną listę wartości używanych dla typów danych innych firm dla `itemclass` właściwości, zobacz [Używanie wyszukiwania zawartości do wyszukiwania danych innych firm, które zostały zaimportowane do Microsoft 365](use-content-search-to-search-third-party-data-that-was-imported.md).

   Aby uzyskać więcej informacji na temat korzystania z wyszukiwania zawartości i tworzenia zapytań wyszukiwania słów kluczowych, zobacz:

  - [Wyszukiwanie zawartości](content-search.md)

  - [Zapytania słów kluczowych i warunki wyszukiwania dla wyszukiwania zawartości](keyword-queries-and-search-conditions.md)