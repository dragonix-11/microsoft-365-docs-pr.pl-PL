---
title: Konfigurowanie Microsoft 365 Lighthouse zabezpieczeń portalu
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Aby uzyskać informacje na temat dostawców usług zarządzanych (MSP) korzystających Microsoft 365 Lighthouse, dowiedz się, jak skonfigurować zabezpieczenia portalu.
ms.openlocfilehash: 8f8ec851d2ce6795565530e120f3704128336ea2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323125"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Konfigurowanie Microsoft 365 Lighthouse zabezpieczeń portalu

Ochrona dostępu do danych klientów, gdy dostawca usług zarządzanych (MSP) delegował uprawnienia dostępu do swoich dzierżaw jest priorytetem chciwości. Microsoft 365 Lighthouse posiada zarówno wymagane, jak i opcjonalne funkcje, które pomogą Ci skonfigurować zabezpieczenia portalu Lighthouse. Aby uzyskać dostęp do usługi Lighthouse, musisz skonfigurować określone role z włączonym uwierzytelnianiem wieloskładnikowym (MFA). Opcjonalnie możesz skonfigurować usługę Azure AD Privileged Identity Management (PIM) i dostęp warunkowy.

## <a name="set-up-multifactor-authentication-mfa"></a>Konfigurowanie uwierzytelniania wieloskładnikowego (MFA)

Jak wspomniano we wpisie w blogu [Twoja pa$$word ma znaczenie](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> "Hasło nie ma znaczenia, ale uwierzytelniania wieloskładnikowego nie ma znaczenia. Jak wynika z naszych analiz, w przypadku używania uwierzytelniania wieloskładnikowego bezpieczeństwo Twojego konta jest większe niż 99,9%.

Gdy użytkownicy po raz pierwszy uzyskają dostęp do latarni morskiej, zostanie wyświetlony monit o skonfigurowanie uwierzytelniania wieloskładnikowego, jeśli ich konto Microsoft 365 nie ma jeszcze skonfigurowane. Użytkownicy nie będą mogli uzyskać dostępu do usługi Lighthouse do momentu ukończenia wymaganego kroku konfiguracji uwierzytelniania wieloskładnikowego. Aby dowiedzieć się więcej o metodach uwierzytelniania, zobacz [Konfigurowanie logowania Microsoft 365 do uwierzytelniania wieloskładnikowego](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>Konfigurowanie kontroli dostępu opartej na rolach

Kontrola dostępu oparta na rolach udziela dostępu do zasobów lub informacji na podstawie ról użytkowników. Dostęp do danych i ustawień dzierżawy klienta w aplikacji Lighthouse jest ograniczony do konkretnych ról w programie Dostawca rozwiązań w chmurze (CSP). Aby skonfigurować role RBAC w latarni lighthouse, zalecamy stosowanie szczegółowych uprawnień administratora delegowanego (GDAP, Granular Delegated Admin Privileges) w celu implementowania szczegółowych przypisań dla użytkowników.

Aby rozpocząć pracę z GDAP, zobacz [Konfigurowanie ról w celu zarządzania dzierżawami klientów](m365-lighthouse-set-up-roles.md).

Technikom MSP można też uzyskać dostęp do latarni morskiej przy użyciu ról agenta administratora lub agenta pomocy technicznej za pośrednictwem delegowanego uprawnienia administratora.

W przypadku działań związanych z dzierżawą innych niż klient w latarni morskiej (takich jak dołączanie, dezaktywowanie/ponowne aktywowanie klienta, zarządzanie tagami i przeglądanie dzienników) technikom usługi MSP musi być przypisana rola w dzierżawie partnera. W poprzednim artykule link zawierał szczegóły dotyczące takich ról i ich uprawnień w latarni morskiej.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Konfigurowanie usługi Azure AD Privileged Identity Management (PIM)

MsP mogą zminimalizować liczbę osób, które mają dostęp do roli o wysokim poziomie uprawnień, aby zabezpieczyć informacje lub zasoby przy użyciu funkcji numer telefonu. Dane pim ograniczają ryzyko, że złośliwy użytkownik uzyskuje dostęp do zasobów lub autoryzowanych użytkowników w sposób niezamierzony i wpływa na zasoby poufne. MsP mogą także udzielać użytkownikom tylko na bieżąco ról o wysokich uprawnieniach w celu uzyskiwania dostępu do zasobów, wprowadzać szerokie zmiany i monitorować, co wyznaczeni użytkownicy robią z ich uprawnieniami. 

> [!NOTE]
> Korzystanie z usługi Azure AD PIM wymaga Azure AD — wersja Premium P2 licencji usługi w dzierżawie partnera.

Poniższe kroki uacyjniają użytkowników dzierżawy partnerskiej do zakresu wyższych ról uprawnień przy użyciu usługi pim:

1. Utwórz grupę z przypisaną rolą zgodnie z opisem w artykule Tworzenie grupy służącej do przypisywania [ról w Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. Przejdź do usługi [Azure AD](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) — Wszystkie grupy i dodaj nową grupę jako członka grupy zabezpieczeń dla ról o wysokich uprawnieniach (na przykład do grupy zabezpieczeń agentów administratora dap lub podobnie odpowiedniej grupy zabezpieczeń dla ról GDAP).

3. Skonfiguruj dostęp z uprawnieniami do nowej grupy zgodnie z opisem w artykule Przypisywanie uprawnionych właścicieli i członków [do grup dostępu z uprawnieniami](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

Aby dowiedzieć się więcej na temat danych pim, zobacz [Co to jest Privileged Identity Management?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>Konfigurowanie dostępu warunkowego usługi Azure AD opartego na czynnikach ryzyka

MsP mogą używać dostępu warunkowego opartego na czynnikach ryzyka w celu upewnienia się, że członkowie ich personelu udowadniają swoją tożsamość za pomocą uwierzytelniania wieloskładnikowego i przez zmianę hasła po wykryciu jako ryzykowny użytkownik (z wyciekami poświadczeń lub za pomocą analizy zagrożeń w usłudze Azure AD). Użytkownicy muszą również zalogować się z znanej lokalizacji lub zarejestrowanego urządzenia po wykryciu ich jako ryzykownych danych logowania. Innymi ryzykownym zachowaniem jest zalogowanie się przy użyciu złośliwego lub anonimowego adresu IP albo zwykłego lub niemożliwego miejsca podróży, użycie anomalicznego tokenu, użycie hasła od hasła lub inne nietypowe zachowanie związane z logowaniem. W zależności od poziomu ryzyka użytkownika, msp mogą również zablokować dostęp podczas logowania. Aby dowiedzieć się więcej o czynnikach ryzyka, zobacz [Co to jest ryzyko?](/azure/active-directory/identity-protection/concept-identity-protection-risks) 

> [!NOTE]
> Dostęp warunkowy wymaga Azure AD — wersja Premium P2 licencji w dzierżawie partnera. Aby skonfigurować dostęp warunkowy, [zobacz Konfigurowanie dostępu Azure Active Directory warunkowego](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>Zawartość pokrewna

[Uprawnienia resetowania hasła](/azure/active-directory/roles/permissions-reference#password-reset-permissions) (artykuł)\
[Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artykuł)\
[Omówienie Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (artykuł)\
[Rejestracja w Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)