---
title: Microsoft 365 współpracy między dzierżawami
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: Dowiedz się, jak współpraca Microsoft 365 działa w różnych dzierżawach i organizacjach, dzięki czemu różne organizacje mogą bezpiecznie współpracować.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 517e015a463a501ad7b9a295a80531595c650454
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100484"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Microsoft 365 współpracy między dzierżawami

Załóżmy, że dwie organizacje, Fabrikam i Contoso, mają Microsoft 365 dla dzierżawy biznesowej i chcą współpracować nad kilkoma projektami, z których niektóre działają przez ograniczony czas, a niektóre z nich są w toku. W jaki sposób firma Fabrikam i Firma Contoso mogą umożliwić swoim osobom i zespołom wydajniejszą współpracę między różnymi dzierżawami Microsoft 365 w bezpieczny sposób? Microsoft 365 w połączeniu ze współpracą B2B Azure Active Directory (Azure AD) oferuje kilka opcji. W tym artykule opisano kilka kluczowych scenariuszy, które mogą wziąć pod uwagę firmy Fabrikam i Contoso.

Microsoft 365 opcje współpracy między dzierżawami obejmują korzystanie z centralnej lokalizacji plików i konwersacji, udostępnianie kalendarzy, używanie wiadomości błyskawicznych, połączeń audio/wideo do komunikacji oraz zabezpieczanie dostępu do zasobów i aplikacji. Skorzystaj z poniższych tabel, aby wybrać rozwiązania i dowiedzieć się więcej.

## <a name="exchange-online-collaboration-options"></a>opcje współpracy Exchange Online

| Cel udostępniania | Akcja administracyjna | Informacje z instrukcjami |
|:-----|:-----|:-----|
|Udostępnianie kalendarzy innej organizacji Microsoft 365 |Administratorzy mogą skonfigurować różne poziomy dostępu do kalendarza w Exchange Online, aby umożliwić firmom współpracę z innymi firmami i umożliwić użytkownikom udostępnianie harmonogramów (informacji wolnych/zajętych) innym osobom. | <ul><li>[Udostępnianie](/exchange/sharing/sharing) </li><li> [Relacje organizacji](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [Tworzenie relacji organizacji](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [Modyfikowanie relacji organizacji](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [Usuwanie relacji organizacji](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [Udostępnianie kalendarzy użytkownikom zewnętrznym](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|Kontrolowanie sposobu udostępniania kalendarzy przez użytkowników osobom spoza organizacji | Administratorzy stosują zasady udostępniania do skrzynek pocztowych użytkowników, aby kontrolować, komu można je udostępniać, oraz poziom udzielonego dostępu |  <ul><li> [Zasady udostępniania](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [Tworzenie zasad udostępniania](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [Stosowanie zasad udostępniania do skrzynek pocztowych](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [Modyfikowanie, wyłączanie lub usuwanie zasad udostępniania](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|Konfigurowanie bezpiecznych kanałów poczty e-mail i kontrolowanie przepływu poczty za pomocą organizacji partnerskich | Administratorzy tworzą łączniki w celu zastosowania zabezpieczeń do wymiany poczty z organizacją partnera lub dostawcą usług. Łączniki wymuszają szyfrowanie za pośrednictwem zabezpieczeń warstwy transportu (TLS), a także zezwalają na ograniczenia dotyczące nazw domen lub zakresów adresów IP, z których partnerzy wysyłają wiadomości e-mail. |  <ul><li> [Jak Exchange Online używa protokołu TLS do zabezpieczania połączeń poczty e-mail](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [Konfigurowanie przepływu poczty przy użyciu łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [Domeny zdalne](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [Konfigurowanie łącznika na potrzeby bezpiecznego przepływu poczty w organizacji partnerskiej](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [Najlepsze rozwiązania dotyczące przepływu poczty (omówienie)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>opcje współpracy SharePoint Online i OneDrive dla Firm

| Udostępnianie celów | Akcja administracyjna | Informacje z instrukcjami |
|:-----|:-----|:-----|
|Udostępnianie witryn i dokumentów użytkownikom zewnętrznym | Administratorzy konfigurują udostępnianie na poziomie dzierżawy lub zbioru witryn dla konta Microsoft uwierzytelnionego, uwierzytelnionego konta służbowego lub kont gościa |  <ul><li> [Zarządzanie udostępnianiem zewnętrznym dla środowiska usługi SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [Ograniczanie udostępniania zawartości SharePoint i OneDrive według domeny](/sharepoint/restricted-domains-sharing) </li><li> [Korzystanie z usługi SharePoint Online jako rozwiązania ekstranetu typu "business-to-business" (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|Śledzenie i kontrolowanie udostępniania zewnętrznego dla użytkowników końcowych | OneDrive dla Firm właścicieli plików i użytkowników końcowych usługi SharePoint Online konfiguruje udostępnianie witryn i dokumentów oraz ustanawia powiadomienia w celu śledzenia udostępniania |  <ul><li> [Konfigurowanie powiadomień dotyczących udostępniania zewnętrznego dla OneDrive dla Firm](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [Udostępnianie plików lub folderów SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>opcje współpracy Skype dla firm

| Cel udostępniania | Akcja administracyjna | Informacje z instrukcjami |
|:-----|:-----|:-----|
|Skype dla firm Online — wiadomości błyskawiczne, wywołania i obecność u innych użytkowników Skype dla firm | Administratorzy mogą włączyć swoich użytkowników usługi Skype dla firm Online do wiadomości błyskawicznych, nawiązywać połączenia audio/wideo i wyświetlać obecność użytkowników w innej dzierżawie Microsoft 365. | [Zezwalanie użytkownikom na kontaktowanie się z zewnętrznymi użytkownikami programu Skype dla firm](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype dla firm Online — wiadomości błyskawiczne, wywołania i obecność u użytkowników Skype (konsumentów) | Administratorzy mogą włączyć użytkowników usługi Skype dla firm Online do wiadomości błyskawicznych, nawiązywać połączenia i wyświetlać obecność użytkowników Skype (konsumentów). | [Zezwalaj Skype dla firm użytkownikom na dodawanie kontaktów Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>Opcje B2B Collaboration usługi Azure AD

| Cel udostępniania | Akcja administracyjna | Informacje z instrukcjami |
|:-----|:-----|:-----|
|Współpraca B2B w usłudze Azure AD — udostępnianie zawartości przez dodanie użytkowników zewnętrznych do grupy w katalogu organizacji | **Administrator kontrolera domeny usługi Azure AD**, **administrator zabezpieczeń**, **administrator użytkowników**, **administrator aplikacji w chmurze** lub **administrator globalny** dla jednej dzierżawy Microsoft 365 może zaprosić osoby w innej dzierżawie Microsoft 365 do dołączenia do katalogu, dodać tych użytkowników zewnętrznych do grupy i udzielić dostępu do zawartości, takiej jak SharePoint witryn i bibliotek dla grupy. |  <ul><li> [Co to jest wersja zapoznawcza współpracy B2B usługi Azure AD?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B: nowe aktualizacje ułatwiają kolab między firmami](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [Udostępnianie zewnętrzne i współpraca Azure Active Directory B2B](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [Azure Active Directory interfejsu API współpracy B2B i dostosowywania](/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD and Identity Show: Azure AD B2B Collaboration (Business to Business to Business)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>opcje współpracy Microsoft 365

| Cel udostępniania | Akcja administracyjna | Informacje z instrukcjami |
|:-----|:-----|:-----|
|Grupy Microsoft 365 — poczta e-mail, kalendarz, OneNote i pliki udostępnione w centralnym miejscu | Grupy są obsługiwane w planach Business Essentials, Business Premium, Education i Enterprise E1, E3 i E5. Osoby w jednej dzierżawie Microsoft 365 mogą utworzyć grupę i zaprosić osoby w innej dzierżawie Microsoft 365 jako użytkowników-gości. Dotyczy również usługi Dynamics CRM. |  <ul><li> [Dowiedz się więcej o grupach Microsoft 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Dostęp gościa w Grupy Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [Wdrażanie Grupy Microsoft 365](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>opcje współpracy Yammer

| Cel udostępniania | Akcja administracyjna | Informacje z instrukcjami |
|:-----|:-----|:-----|
|Yammer — współpraca za pośrednictwem mediów społecznościowych przedsiębiorstwa | Chyba że możliwość tworzenia grup zewnętrznych jest wyłączona przez administratora Yammer, użytkownicy mogą tworzyć grupy zewnętrzne do współpracy w Yammer poprzez konwersacje, możliwość polubiania i obserwowania wpisów, udostępniania plików i czatowania online. | [Tworzenie grup zewnętrznych i zarządzanie nimi w usłudze Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>opcje współpracy Teams

|Cel udostępniania|Akcja administracyjna|Informacje z instrukcjami|
|:-----|:-----|:-----|
|Współpraca w Teams z użytkownikami zewnętrznymi w organizacji | **Administrator użytkownika** lub **administrator globalny** dla dzierżawy zapraszania Microsoft 365 musi włączyć współpracę zewnętrzną w Teams. Administratorzy globalni i właściciele zespołów będą teraz mogli zapraszać każdego, kto ma adres e-mail, do współpracy w Teams.  <br/> Administratorzy mogą również zarządzać gośćmi już obecnymi w dzierżawie i edytować je. |  <ul><li> [Autoryzowanie dostępu gościa](/microsoftteams/teams-dependencies) </li><li> [Włączanie lub wyłączanie dostępu gościa w Teams](/microsoftteams/set-up-guests) </li><li> [Kontrolowanie dostępu gościa za pomocą programu PowerShell](/microsoftteams/guest-access-powershell) </li><li> [Lista kontrolna dostępu gościa](/microsoftteams/guest-access-checklist) </li><li> [Wyświetlanie użytkowników-gości](/microsoftteams/view-guests) </li><li> [Edytowanie informacji o użytkowniku-gościu](/microsoftteams/edit-guests-information) </li></ul> |
|Właściciele zespołów mogą zapraszać gości i zarządzać tym, jak współpracują w ramach swoich zespołów.  |Właściciele zespołów mają dodatkową kontrolę nad tym, co goście mogą robić w swoich zespołach. |  <ul><li> [Dodaj gości](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [Dodawanie gościa do zespołu](/microsoftteams/add-guests) </li><li> [Zarządzanie dostępem gościa w Teams](/microsoftteams/manage-guests) </li><li> [Zobacz, kto jest w zespole lub w kanale](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|Goście z innych dzierżaw mogą wyświetlać zawartość w Teams i współpracować z innymi członkami | Brak. | [Środowisko dostępu gościa](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>opcje współpracy Power BI

| Cel udostępniania | Akcja administracyjna | Informacje z instrukcjami |
|:-----|:-----|:-----|
|Power BI umożliwia zewnętrznym użytkownikom-gościom korzystanie z udostępnionej im zawartości za pośrednictwem linków. Dzięki temu użytkownicy w organizacji mogą bezpiecznie rozpowszechniać zawartość w różnych organizacjach.<br/> | Administrator Power BI może kontrolować, czy użytkownicy mogą zapraszać użytkowników zewnętrznych do wyświetlania zawartości w organizacji.| [Dystrybuowanie zawartości Power BI do zewnętrznych użytkowników-gości przy użyciu usługi Azure AD B2B](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Punkty, które należy pamiętać o Microsoft 365 współpracy między dzierżawami

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Udostępnianie kont użytkowników, licencji, subskrypcji i magazynu

Każda organizacja przechowuje własne konta użytkowników, tożsamości, grupy zabezpieczeń, subskrypcje, licencje i magazyn. Użytkownicy korzystają z funkcji współpracy w Microsoft 365 wraz z zasadami udostępniania i ustawieniami zabezpieczeń, aby zapewnić dostęp do potrzebnych informacji przy zachowaniu kontroli nad zasobami firmy.

- **Konta użytkowników:** Nie można udostępniać ani duplikować kont między dzierżawami lub partycjami w usługach lokalna usługa Active Directory Domain Services.

- **Subskrypcje &amp; licencji:** w Microsoft 365 licencje z planów licencjonowania (nazywane również jednostkami SKU lub planami Microsoft 365) zapewniają użytkownikom dostęp do usług Microsoft 365 zdefiniowanych dla tych planów.

- **Storage:** W planach licencjonowania Microsoft 365 granice oprogramowania i limity dla usługi SharePoint Online są zarządzane niezależnie od limitów magazynu skrzynek pocztowych. Limity magazynu skrzynek pocztowych są konfigurowane i zarządzane przy użyciu Exchange Online. W obu scenariuszach nie można udostępniać magazynu między dzierżawami.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Czy możemy udostępniać przestrzenie nazw domeny w dzierżawach Microsoft 365?

L.p. Nazwy domen organizacji, takie jak fabrikam.com lub tailspintoys.com, mogą być skojarzone i używane tylko z jedną dzierżawą Microsoft 365. Każda dzierżawa musi mieć własną przestrzeń nazw. Przestrzenie nazw UPN, SMTP i SIP nie mogą być współużytkowane między dzierżawami.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>A co ze składnikami hybrydowymi i Microsoft 365 współpracy między dzierżawami?

Lokalnych składników hybrydowych, takich jak organizacja Exchange i usługa Azure AD Połączenie, nie można podzielić między wiele dzierżaw.
