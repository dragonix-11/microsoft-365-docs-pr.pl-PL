---
title: Dostęp do grup Microsoft 365, Teams i SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się więcej o dostępie do Microsoft 365 grup, Teams i SharePoint.
ms.openlocfilehash: e01326093476f341c6c4c75448efbdf8c745779f
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63004970"
---
# <a name="governing-access-in-microsoft-365-groups-teams-and-sharepoint"></a>Dostęp do grup Microsoft 365, Teams i SharePoint

Istnieje wiele kontrolek umożliwiających sterowanie dostępem użytkowników do zasobów w grupach, zespołach i SharePoint. Przejrzyj te opcje i rozważ ich mapowanie na potrzeby Twojej firmy, czułość danych i zakres osób, z którymi twoi użytkownicy muszą współpracować.

W poniższej tabeli przedstawiono podręczną tabelę z kontrolkami dostępu dostępnymi w programie Microsoft 365. Dalsze informacje podano w poniższych sekcjach.

|Kategoria|Opis|Odwołanie|
|:-------|:----------|:--------|
|Członkostwo|||
||Odnajdowanie prywatnych zespołów|[Zarządzanie odnajdowanie prywatnych zespołów w Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)|
||Dynamiczne członkostwo w grupach na podstawie reguł|[Tworzenie lub aktualizowanie grupy dynamicznej w programie Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)|
||Kontrolowanie, kto może udostępniać pliki, foldery i witryny.|[Konfigurowanie żądań dostępu i zarządzanie nimi](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)|
|Dostęp warunkowy|||
||Uwierzytelnianie wieloskładnikowe|[Uwierzytelnianie wieloskładnikowe usługi Azure AD](/azure/active-directory/authentication/concept-mfa-howitworks)|
||Kontrola dostępu do urządzenia zależy od grupy, zespołu lub wrażliwości witryny.|[Używanie etykiet wrażliwości w celu ochrony zawartości Microsoft Teams, grup Microsoft 365 i SharePoint internetowych](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Ograniczanie dostępu do witryny dla urządzeń niezawiązyanych.|[Kontrolowanie SharePoint dostępu z urządzeń niezamanektowych](/sharepoint/control-access-from-unmanaged-devices)|
||Kontrolowanie dostępu do witryny na podstawie lokalizacji|[Kontrolowanie dostępu do SharePoint i OneDrive danych na podstawie lokalizacji sieciowej](/sharepoint/control-access-based-on-network-location)|
|Dostęp dla gości|||
||Zezwalanie lub blokowanie SharePoint z określonych domen.|[Ograniczanie udostępniania zawartości SharePoint i OneDrive według domeny](/sharepoint/restricted-domains-sharing)|
||Zezwalanie na członkostwo w zespołach lub grupach z określonych domen lub blokowanie ich.|[Zezwalanie na zaproszenia do B2B z określonych organizacji lub blokowanie ich](/azure/active-directory/b2b/allow-deny-list)|
||Uniemożliwianie udostępniania anonimowego.|[Wyłączanie linków Każdy](./share-limit-accidental-exposure.md#turn-off-anyone-links)|
||Kontrolowanie uprawnień dla linków z dostępem anonimowym.|[Ustawianie uprawnień do łączenia dla linków Każdy](./best-practices-anonymous-sharing.md#set-link-permissions)|
||Kontrolowanie wygasania linków udostępniania anonimowego.|[Ustawianie daty wygaśnięcia dla linków Każdy](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)|
||Domyślnie steruj typem linku udostępniania wyświetlanego użytkownikom.|[Zmiana domyślnego typu linku dla witryny](/sharepoint/change-default-sharing-link)|
||Ograniczanie udostępniania zewnętrznego do określonych osób.|[Ograniczanie udostępniania zewnętrznego do określonych grup zabezpieczeń](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)|
||Kontrola dostępu gościa do grupy, zespołu lub witryny na podstawie wrażliwości informacji.|[Używanie etykiet wrażliwości w celu ochrony zawartości Microsoft Teams, grup Microsoft 365 i SharePoint internetowych](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Wyłącz opcje udostępniania.|[Ograniczanie udostępniania w Microsoft 365](./microsoft-365-limit-sharing.md)|
|Zarządzanie użytkownikami|||
||Regularne przeglądanie członkostwa w zespołach i grupach.|[Co to są recenzje dostępu do usługi Azure AD?](/azure/active-directory/governance/access-reviews-overview)|
||Automatyzowanie zarządzania dostępem do grup i zespołów.|[Co to jest zarządzanie uprawnieniami do usługi Azure AD?](/azure/active-directory/governance/entitlement-management-overview)|
||Zezwalaj innym osobom na tworzenie kanałów prywatnych w Teams.|[Zarządzanie cyklem życia kanałów prywatnych w Microsoft Teams](/MicrosoftTeams/private-channels-life-cycle-management)|

## <a name="membership"></a>Członkostwo

Członkostwo w zespołach i grupach jest kontrolowane przez właścicieli. Członkowie mogą zapraszać inne osoby, ale zaproszenia są wysyłane do właścicieli w celu zatwierdzenia. Zespoły i grupy publiczne mogą być odnajdowane przez wszystkie osoby w organizacji, ale możesz kontrolować, czy prywatne zespoły i grupy mogą być wykrywalne:

- [Zarządzanie odnajdowanie prywatnych zespołów w Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)

Możesz dynamicznie zarządzać członkostwem w grupie lub zespole na podstawie niektórych kryteriów, takich jak dział. W takim przypadku członkowie i właściciele nie mogą zapraszać osób do zespołu. W grupach dynamicznych są używane metadane Azure Active Directory, aby kontrolować, kto jest członkiem grupy. Upewnij się, że używasz metadanych, są pełne i aktualne, ponieważ nieprawidłowe metadane mogą prowadzić do tego, że użytkownicy nie będą już grupować lub są do nich dodawana niepoprawni.

- [Tworzenie lub aktualizowanie grupy dynamicznej w programie Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

SharePoint witryny oferują możliwość dodawania właścicieli, członków i odwiedzających niezależnie od członkostwa w grupie lub zespole. W zależności od wymagań możesz ograniczyć liczbę osób, które mogą zapraszać osoby do witryny. Ponadto w zależności od wrażliwości informacji w danej witrynie możesz ograniczyć liczbę osób, które mogą udostępniać pliki i foldery. Te ograniczenia są konfigurowane przez zespół, grupę lub właściciela witryny:

- [Konfigurowanie żądań dostępu i zarządzanie nimi](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)


## <a name="conditional-access"></a>Dostęp warunkowy

Dzięki Microsoft 365 możesz wymagać uwierzytelniania wieloskładnikowego zarówno dla osób w organizacji, jak i poza nią. Istnieje wiele opcji dostępnych w sytuacji, gdy jest wyświetlany monit o uwierzytelnienie drugiego czynnika. Zdecydowanie zalecamy wdrożenie uwierzytelniania wieloskładnikowego w organizacji:

- [Uwierzytelnianie wieloskładnikowe usługi Azure AD](/azure/active-directory/authentication/concept-mfa-howitworks)

Jeśli w niektórych grupach i zespołach masz informacje poufne, możesz wymusić zasady zarządzania urządzeniami na podstawie etykiety wrażliwości grupy lub zespołu. Dostęp można całkowicie zablokować na urządzeniach niezawiązyanych lub zezwolić na ograniczony dostęp tylko w sieci Web:

- [Używanie etykiet wrażliwości w celu ochrony zawartości Microsoft Teams, grup Microsoft 365 i SharePoint internetowych](../compliance/sensitivity-labels-teams-groups-sites.md)

W SharePoint można ograniczyć dostęp do witryn z określonych lokalizacji sieciowych.

- [Kontrolowanie dostępu do SharePoint i OneDrive danych na podstawie lokalizacji sieciowej](/sharepoint/control-access-based-on-network-location)


Dodatkowe zasoby:

- [Planowanie wdrożenia dostępu warunkowego](/azure/active-directory/conditional-access/plan-conditional-access)

- [Microsoft Intune omówienie](/mem/intune/fundamentals/what-is-intune)

- [Kontrolowanie SharePoint dostępu z urządzeń niezamanektowych](/sharepoint/control-access-from-unmanaged-devices)


## <a name="guest-access"></a>Dostęp dla gości

Możesz ograniczyć gości na podstawie domeny ich adresów e-mail. SharePoint oferuje ustawienia ograniczeń dotyczących domeny dla całej organizacji i witryny. Grupy i Teams używają list zezwalania na domeny lub list zablokowanych w usłudze Azure AD. Oba ustawienia należy skonfigurować, aby uniknąć niechcianego udostępniania, oraz zapewnić spójne środowisko użytkownika:

- [Ograniczanie udostępniania zawartości SharePoint i OneDrive według domeny](/sharepoint/restricted-domains-sharing)

- [Zezwalanie na zaproszenia do B2B z określonych organizacji lub blokowanie ich](/azure/active-directory/b2b/allow-deny-list)

Microsoft 365 umożliwia anonimowe udostępnianie plików i folderów przy użyciu *linków Każdy* udostępnia. *Każdy* link może być przesyłany dalej, a każda osoba mająca link może uzyskać dostęp do udostępnionego elementu. W zależności od wrażliwości danych rozważ możliwość ustawienia sposobu używania  linków Każdy — łącznie z wyłączeniem ich całkowicie, ograniczeniem uprawnień do łączenia tylko do odczytu lub ustawieniem dla nich czasu wygaśnięcia:

- [Wyłączanie linków Każdy](./share-limit-accidental-exposure.md#turn-off-anyone-links)

- [Ustawianie uprawnień do łączenia dla linków Każdy](./best-practices-anonymous-sharing.md#set-link-permissions)

- [Ustawianie daty wygaśnięcia dla linków Każdy](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)

Podczas udostępniania plików lub folderów użytkownicy mają do wyboru kilka typów linków. Aby zmniejszyć ryzyko przypadkowego nieodpowiedniego udostępniania, możesz zmienić domyślny typ linku prezentowany użytkownikom, którzy go udostępniają. Na przykład zmiana ustawienia domyślnego z  linków Każdy na linki Każdy, które zezwalają na dostęp anonimowy, na linki Osoby w organizacji może zmniejszyć ryzyko niechcianego udostępniania informacji poufnych:

- [Zmiana domyślnego typu linku dla witryny](/sharepoint/change-default-sharing-link)

Jeśli Twoja organizacja ma poufne dane, które trzeba udostępnić gościom, ale martwi Cię nieodpowiednie udostępnianie, możesz ograniczyć udostępnianie zewnętrzne plików i folderów do członków określonych grup zabezpieczeń. W ten sposób możesz ograniczyć udostępnianie zewnętrzne do określonej grupy osób lub wymagać od użytkowników przećwęć szkolenia dotyczące odpowiedniego udostępniania zewnętrznego przed dodaniem ich do grupy zabezpieczeń:

- [Ograniczanie udostępniania zewnętrznego do określonych grup zabezpieczeń](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)

Grupy i Teams mają ustawienia na poziomie organizacji, które umożliwiają lub odmawiają dostępu gościa. Możesz ograniczyć dostęp gości do określonych zespołów lub grup przy użyciu programu [Microsoft PowerShell](per-group-guest-access.md), jednak zalecamy, aby to zrobić za pomocą etykiety wrażliwości. Etykiety wrażliwości umożliwiają automatyczne zezwalanie na dostęp gościa lub odmawianie go na podstawie zastosowanej etykiety:

- [Używanie etykiet wrażliwości w celu ochrony zawartości Microsoft Teams, grup Microsoft 365 i SharePoint internetowych](../compliance/sensitivity-labels-teams-groups-sites.md)

W środowisku, w którym często zapraszasz gości do grup i zespołów, rozważ skonfigurowanie regularnie planowanych recenzji dostępu gości. Właściciele mogą zostać proszeni o przejrzenie gości w ich grupach i zespołach oraz zatwierdzenie lub zablokowanie dostępu.

- [Konfigurowanie recenzji dostępu gościa](/microsoft-365/solutions/create-secure-guest-sharing-environment#set-up-guest-access-reviews)

Microsoft 365 udostępnia wiele różnych metod udostępniania informacji. Jeśli masz informacje poufne i chcesz ograniczyć sposób ich udostępniania, zapoznaj się z opcjami ograniczenia udostępniania:

- [Ograniczanie udostępniania w Microsoft 365](./microsoft-365-limit-sharing.md)

Dodatkowe zasoby:

- [Konfigurowanie bezpiecznej współpracy za pomocą Microsoft 365](./setup-secure-collaboration-with-teams.md)

- [Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytanych użytkownikom](./best-practices-anonymous-sharing.md)

- [Ograniczanie przypadkowego udostępnienia plików osobom spoza organizacji](./share-limit-accidental-exposure.md)

- [Tworzenie bezpiecznego środowiska udostępniania gości](./create-secure-guest-sharing-environment.md)

- [Włącz współpracę zewnętrzną B2B i zarządzaj tym, kto może zapraszać gości](/azure/active-directory/b2b/delegate-invitations)

## <a name="user-management"></a>Zarządzanie użytkownikami

W związku z rozwojem grup i zespołów w organizacji dobrym rozwiązaniem jest regularne przeglądanie informacji o członkostwie w zespołach i grupach. Może to być szczególnie przydatne w przypadku zespołów i grup o zmieniającym się członkostwie, zawierających informacje poufne lub zawierających gości. Rozważ skonfigurowanie recenzji dostępu dla tych zespołów i grup:

- [Co to są recenzje dostępu do usługi Azure AD?](/azure/active-directory/governance/access-reviews-overview)

Wiele organizacji ściśle współpracuje z innymi organizacjami lub kluczowymi dostawcami, z którymi współpracują. Zarządzanie użytkownikami i dostęp do zasobów może być trudnym zadaniem w przypadku takich scenariuszy. Rozważ zautomatyzowanie niektórych zadań zarządzania użytkownikami, a nawet przejście niektórych z nich do organizacji partnerskiej:

- [Co to jest zarządzanie uprawnieniami do usługi Azure AD?](/azure/active-directory/governance/entitlement-management-overview)

Kanały prywatne w Teams umożliwiają dostęp do ograniczonych konwersacji i udostępniania plików między podzbiorami członków zespołu. W zależności od konkretnych potrzeb biznesowych możesz zechcieć zezwolić na tę funkcję lub zablokować tę funkcję.

- [Kanały prywatne w Microsoft Teams](/MicrosoftTeams/private-channels)

- [Zarządzanie cyklem życia kanałów prywatnych w Microsoft Teams](/MicrosoftTeams/private-channels-life-cycle-management)

Dodatkowe zasoby:

- [Azure Active Directory zarządzanie tożsamością](/azure/active-directory/governance)

## <a name="related-topics"></a>Tematy pokrewne

[Zalecenia dotyczące planowania zarządzania współpracą](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Tworzenie planu zarządzania współpracą](collaboration-governance-first.md)

[Zabezpieczenia i zgodność z przepisami w Microsoft Teams](/microsoftteams/security-compliance-overview)

[Zarządzanie ustawieniami udostępniania w SharePoint](/sharepoint/turn-external-sharing-on-or-off)

[Tworzenie sieci zewnętrznej w aplikacji i zarządzanie Yammer](/yammer/work-with-external-users/create-and-manage-an-external-network)

[Konfigurowanie Teams z trzema poziomami ochrony](./configure-teams-three-tiers-protection.md)