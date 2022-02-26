---
title: Microsoft 365 między dzierżawami
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się Microsoft 365 jak działa współpraca między dzierżawami i organizacjami, pozwalając na bezpieczną współpracę w różnych organizacjach.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9cb91b6bcaac212eeaf0ef4051f466751d8dbbd9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973512"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Microsoft 365 między dzierżawami

Załóżmy, że dwie organizacje — Fabrikam i Contoso — każda z nich ma dzierżawę usługi Microsoft 365 dla firm i chcą współpracować nad kilkoma projektami, z których część jest uruchamiana przez ograniczony czas, a inne są trwające. W jaki sposób firmy Fabrikam i Contoso mogą umożliwić ich osobom i zespołom efektywnnszą współpracę w ramach Microsoft 365 dzierżaw w bezpieczny sposób? Microsoft 365 w połączeniu z współpracą B2B usługi Azure Active Directory (Azure AD) oferuje kilka opcji. W tym artykule opisano kilka kluczowych scenariuszy, które mogą rozważyć firmy Fabrikam i Contoso.

Microsoft 365 między dzierżawami obejmują korzystanie z centralnej lokalizacji plików i konwersacji, udostępnianie kalendarzy, korzystanie z wiadomości błyskawicznych, połączenia audio/wideo w celu komunikacji oraz zabezpieczanie dostępu do zasobów i aplikacji. Skorzystaj z poniższych tabel, aby wybrać rozwiązania i dowiedzieć się więcej.

## <a name="exchange-online-collaboration-options"></a>Exchange Online opcji współpracy

| Cel udostępniania | Działanie administracyjne | How-to information (Informacje edytowe) |
|:-----|:-----|:-----|
|Udostępnianie kalendarzy innej organizacji Microsoft 365 organizacji |Administratorzy mogą skonfigurować różne poziomy dostępu do kalendarza w programie Exchange Online, aby umożliwić firmom współpracę z innymi firmami i umożliwić użytkownikom udostępnianie harmonogramów (informacji o wolnym/zajętym) innym osobom. | <ul><li>[Udostępnianie](/exchange/sharing/sharing) </li><li> [Relacje między organizacjami](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [Tworzenie relacji między organizacjami](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [Modyfikowanie relacji między organizacjami](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [Usuwanie relacji między organizacjami](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [Udostępnianie kalendarzy użytkownikom zewnętrznym](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|Sterowanie udostępnianiem kalendarzy przez użytkowników osobom spoza organizacji | Administratorzy stosują zasady udostępniania do skrzynek pocztowych użytkowników, aby kontrolować, komu można je udostępniać, oraz jaki jest poziom dostępu |  <ul><li> [Zasady udostępniania](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [Tworzenie zasad udostępniania](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [Stosowanie zasad udostępniania do skrzynek pocztowych](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [Modyfikowanie, wyłączanie lub usuwanie zasad udostępniania](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|Konfigurowanie bezpiecznych kanałów poczty e-mail i kontrolowanie przepływu poczty e-mail z organizacjami partnerskimi | Administratorzy tworzą łączniki, aby zastosować zabezpieczenia do wymiany poczty z organizacją partnerską lub usługodawca. Łączniki wymuszają szyfrowanie za pośrednictwem protokołu TLS (Transport Layer Security), a także dopuszczając ograniczenia dotyczące nazw domen lub zakresów adresów IP, z których partnerzy wysyłają wiadomości e-mail. |  <ul><li> [Jak Exchange Online TLS do zabezpieczania połączeń e-mail](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [Konfigurowanie przepływu poczty e-mail przy użyciu łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [Domeny zdalne](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [Konfigurowanie łącznika do bezpiecznego przepływu poczty e-mail z organizacją partnerską](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [Najlepsze rozwiązania dotyczące przepływu poczty e-mail (omówienie)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint online i OneDrive dla Firm opcje współpracy

| Cele w tym dzieleniu się | Działanie administracyjne | How-to information (Informacje edytowe) |
|:-----|:-----|:-----|
|Udostępnianie witryn i dokumentów użytkownikom zewnętrznym | Administratorzy konfigurują udostępnianie w dzierżawie lub na poziomie zbioru witryn dla uwierzytelnionego konta Microsoft, uwierzytelnionego konta służbowego lub kont gości |  <ul><li> [Zarządzanie udostępnianiem zewnętrznym w środowisku usługi SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [Ograniczanie udostępniania zawartości SharePoint i OneDrive według domeny](/sharepoint/restricted-domains-sharing) </li><li> [Używanie SharePoint Online jako rozwiązania ekstranetowego B2B (Business-to-Business)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|Śledzenie i kontrolowanie udostępniania zewnętrznego dla użytkowników końcowych | OneDrive dla Firm i użytkownicy SharePoint online konfigurują udostępnianie witryn i dokumentów oraz ustanawiają powiadomienia w celu śledzenia udostępniania |  <ul><li> [Konfigurowanie powiadomień dotyczących udostępniania zewnętrznego dla OneDrive dla Firm](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [Udostępnianie SharePoint lub folderów](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>Skype dla firm opcji współpracy

| Cel udostępniania | Działanie administracyjne | How-to information (Informacje edytowe) |
|:-----|:-----|:-----|
|Skype dla firm online — wiadomości błyskawiczne, połączenia i informacje o obecności z innymi Skype dla firm użytkownikami | Administratorzy mogą umożliwić użytkownikom usługi Skype dla firm online wiadomości błyskawiczne, na przykład połączenia audio/wideo i wyświetlanie informacji o obecności z użytkownikami z innej Microsoft 365 dzierżawy. | [Zezwalanie użytkownikom na kontaktowanie się z zewnętrznymi użytkownikami programu Skype dla firm](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype dla firm online — wiadomości błyskawiczne, połączenia i informacje o obecności Skype użytkownikach indywidualnych | Administratorzy mogą umożliwić użytkownikom usługi Skype dla firm online wiadomości błyskawiczne, dzwonienie i wyświetlanie informacji o obecności Skype użytkowników indywidualnych. | [Umożliwianie Skype dla firm użytkownikom dodawania Skype kontaktów](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>Opcje współpracy między użytkownikami przy użyciu usługi Azure AD

| Cel udostępniania | Działanie administracyjne | How-to information (Informacje edytowe) |
|:-----|:-----|:-----|
|Współpraca między firmami przy użyciu usługi Azure AD — udostępnianie zawartości przez dodawanie użytkowników zewnętrznych do grupy w katalogu organizacji | Administrator dc usługi **Azure AD****, administrator** **zabezpieczeń, administrator** **użytkowników, administrator** aplikacji w chmurze lub  administrator globalny dla jednej dzierżawy usługi Microsoft 365 może zaprosić osoby z innej dzierżawy usługi Microsoft 365 do dołączenia do ich katalogu, dodać tych użytkowników zewnętrznych do grupy i udzielić im dostępu do zawartości, takiej jak witryny i biblioteki usługi SharePoint dla tej grupy. |  <ul><li> [Co to jest wersja zapoznawcza współpracy B2B usługi Azure AD?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [B2B usługi Azure AD: nowe aktualizacje ułatwiają sortowanie między firmami](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [Udostępnianie zewnętrzne i współpraca Azure Active Directory B2B](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [Azure Active Directory interfejsu API współpracy B2B i dostosowywania](/azure/active-directory/active-directory-b2b-api) </li><li> [Pokaz usług Azure AD i tożsamości: Współpraca między firmami w usłudze Azure AD](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>Microsoft 365 opcji współpracy

| Cel udostępniania | Działanie administracyjne | How-to information (Informacje edytowe) |
|:-----|:-----|:-----|
|Microsoft 365 grupy — poczta e-mail, kalendarz, OneNote i pliki udostępnione w centralnym miejscu | Grupy są obsługiwane w planach Business Essentials, Business Premium, Education oraz Enterprise E1, E3 i E5. Osoby w jednej Microsoft 365 dzierżawie mogą utworzyć grupę i zaprosić osoby z innej Microsoft 365 dzierżawy jako użytkowników-gości. Dotyczy również programu Dynamics CRM. |  <ul><li> [Informacje o Microsoft 365 grup](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Dostęp dla gości w Microsoft 365 grupy](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [Wdrażanie Microsoft 365 grup](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>Yammer opcji współpracy

| Cel udostępniania | Działanie administracyjne | How-to information (Informacje edytowe) |
|:-----|:-----|:-----|
|Yammer — współpraca za pośrednictwem sieci społecznościowej przedsiębiorstwa | O ile możliwość tworzenia grup zewnętrznych nie została wyłączona przez administratora usługi Yammer, użytkownicy mogą tworzyć grupy zewnętrzne do współpracy w programie Yammer za pośrednictwem konwersacji, polubienia i obserwowania wpisów, udostępniania plików i czatu online. | [Tworzenie grup zewnętrznych i zarządzanie nimi w usłudze Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>Teams opcji współpracy

|Cel udostępniania|Działanie administracyjne|How-to information (Informacje edytowe)|
|:-----|:-----|:-----|
|Współpraca w Teams z użytkownikami  zewnętrznymi w organizacji | Administrator **użytkownika lub** administrator globalny **zapraszający** Microsoft 365 musi włączyć współpracę zewnętrzną w Teams. Administratorzy globalni i właściciele  zespołu będą teraz mogli zaprosić do współpracy wszystkie osoby z adresem e-mail Teams.  <br/> Administratorzy mogą również zarządzać gośćmi już obecni w dzierżawie i edytować je. |  <ul><li> [Autoryzuj dostęp gościa](/microsoftteams/teams-dependencies) </li><li> [Włączanie lub wyłączanie dostępu gościa w Teams](/microsoftteams/set-up-guests) </li><li> [Sterowanie dostępem gości za pomocą programu PowerShell](/microsoftteams/guest-access-powershell) </li><li> [Lista kontrolna dostępu gościa](/microsoftteams/guest-access-checklist) </li><li> [Wyświetlanie użytkowników gości](/microsoftteams/view-guests) </li><li> [Edytowanie informacji o gościu](/microsoftteams/edit-guests-information) </li></ul> |
|Właściciele zespołów mogą zapraszać gości i zarządzać ich możliwościami współpracy w ramach zespołów.  |Właściciele zespołów mają dodatkową kontrolę nad tym, co goście mogą robić w ich zespołach. |  <ul><li> [Dodawanie gości](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [Dodawanie gościa do zespołu](/microsoftteams/add-guests) </li><li> [Zarządzanie dostępem gości w aplikacji Teams](/microsoftteams/manage-guests) </li><li> [Wyświetlanie członków zespołu lub kanału](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|Goście z innych dzierżaw mogą wyświetlać zawartość w programie Teams i współpracować z innymi członkami | Brak. | [Środowisko dostępu gościa](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>Power BI opcji współpracy

| Cel udostępniania | Działanie administracyjne | How-to information (Informacje edytowe) |
|:-----|:-----|:-----|
|Power BI umożliwia zewnętrznym użytkownikom-gościom korzystanie z zawartości udostępnianej im za pomocą linków. Dzięki temu użytkownicy w organizacji mogą bezpiecznie rozpowszechniać zawartość w różnych organizacjach.<br/> | Administrator Power BI może kontrolować, czy użytkownicy mogą zapraszać użytkowników zewnętrznych do wyświetlania zawartości w organizacji.| [Rozpowszechnianie Power BI zawartości dla zewnętrznych gości za pomocą usługi Azure AD B2B](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Punkty, o których należy wiedzieć w Microsoft 365 współpracy między dzierżawami

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Udostępnianie kont użytkowników, licencji, subskrypcji i miejsca do magazynowania

Każda organizacja obsługuje własne konta użytkowników, tożsamości, grupy zabezpieczeń, subskrypcje, licencje i magazyn. Osoby korzystają z funkcji współpracy w p Microsoft 365 z zasadami udostępniania i ustawieniami zabezpieczeń, aby zapewnić dostęp do potrzebnych informacji przy zachowaniu kontroli zasobów firmy.

- **Konta użytkowników:** Kont nie można udostępniać ani duplikować między dzierżawami lub partycjami w lokalnym środowisku Usługi domenowe w usłudze Active Directory.

- **Subskrypcje &amp; licencji.** W programie Microsoft 365 licencje z planów licencjonowania (nazywanych również jednostkami SKU lub planami Microsoft 365) zapewniają użytkownikom dostęp do usług Microsoft 365 zdefiniowanych dla tych planów.

- **Storage:** W Microsoft 365 licencjonowania ograniczenia i limity oprogramowania dla usługi SharePoint Online są zarządzane oddzielnie od limitów magazynowania skrzynek pocztowych. Limity miejsca do magazynowania skrzynki pocztowej są ustawiane i zarządzane przy użyciu Exchange Online. W obu scenariuszach nie można udostępniać magazynu dla różnych dzierżaw.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Czy przestrzenie nazw domen mogą być Microsoft 365 dzierżawami?

L.p. Nazwy domen organizacji, takie jak fabrikam.com lub tailspintoys.com, można skojarzyć i używać tylko z jedną Microsoft 365 dzierżawy. Każda dzierżawa musi mieć własną przestrzeń nazw. Przestrzeni nazw UPN, SMTP i SIP nie można udostępniać w różnych dzierżawach.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>Co ze składnikami hybrydowymi i Microsoft 365 współpracę w ramach dzierżawy?

Lokalnych składników hybrydowych, takich jak organizacja Exchange i usługa Azure AD Połączenie, nie można podzielić między wiele dzierżaw.
