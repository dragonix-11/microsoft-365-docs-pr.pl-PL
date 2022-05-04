---
title: Konfigurowanie zabezpieczeń portalu Microsoft 365 Lighthouse
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się, jak skonfigurować zabezpieczenia portalu.
ms.openlocfilehash: 60e0d2f1ba61e5def3979358f338da0846914543
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188685"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Konfigurowanie zabezpieczeń portalu Microsoft 365 Lighthouse

Ochrona dostępu do danych klientów, gdy dostawca usług zarządzanych (MSP) delegował uprawnienia dostępu do swoich dzierżaw, jest priorytetem cyberbezpieczeństwa. Microsoft 365 Lighthouse oferuje zarówno wymagane, jak i opcjonalne funkcje ułatwiające konfigurowanie zabezpieczeń portalu usługi Lighthouse. Przed uzyskaniem dostępu do usługi Lighthouse należy skonfigurować określone role z włączonym uwierzytelnianiem wieloskładnikowym (MFA). Opcjonalnie można skonfigurować Azure AD Privileged Identity Management (PIM) i dostęp warunkowy.

## <a name="set-up-multifactor-authentication-mfa"></a>Konfigurowanie uwierzytelniania wieloskładnikowego (MFA)

Jak wspomniano we wpisie w blogu [Twoja $word Pa$, nie ma znaczenia](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> "Hasło nie ma znaczenia, ale uwierzytelnianie wieloskładnikowe to robi. Na podstawie naszych badań twoje konto jest o ponad 99,9% mniej narażone na naruszenie zabezpieczeń w przypadku korzystania z uwierzytelniania wieloskładnikowego"

Gdy użytkownicy uzyskują dostęp do usługi Lighthouse po raz pierwszy, zostanie wyświetlony monit o skonfigurowanie uwierzytelniania wieloskładnikowego, jeśli ich konto Microsoft 365 nie zostało jeszcze skonfigurowane. Użytkownicy nie będą mogli uzyskać dostępu do usługi Lighthouse, dopóki nie zostanie ukończony wymagany krok konfiguracji uwierzytelniania wieloskładnikowego. Aby dowiedzieć się więcej na temat metod uwierzytelniania, zobacz [Konfigurowanie Microsoft 365 logowania na potrzeby uwierzytelniania wieloskładnikowego](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>Konfigurowanie kontroli dostępu opartej na rolach

Kontrola dostępu oparta na rolach (RBAC) udziela dostępu do zasobów lub informacji na podstawie ról użytkowników. Dostęp do danych i ustawień dzierżawy klienta w aplikacji Lighthouse jest ograniczony do określonych ról z programu Dostawca rozwiązań w chmurze (CSP). Aby skonfigurować role RBAC w usłudze Lighthouse, zalecamy użycie szczegółowych uprawnień administratora delegowanego (GDAP) w celu zaimplementowania szczegółowych przypisań dla użytkowników. Uprawnienia administratora delegowanego (DAP) są nadal wymagane do pomyślnego dołączenia dzierżawy, ale klienci korzystający tylko z protokołu GDAP wkrótce będą mogli dołączyć bez zależności od języka DAP. Uprawnienia GDAP mają pierwszeństwo, gdy dap i GDAP współistnieją dla klienta.

Aby skonfigurować relację GDAP, zobacz [Uzyskiwanie szczegółowych uprawnień administratora do zarządzania usługą klienta](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). Aby uzyskać więcej informacji na temat ról, które zalecamy używać usługi Lighthouse, zobacz [Omówienie uprawnień w Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

Technicy MSP mogą również uzyskiwać dostęp do usługi Lighthouse przy użyciu ról agenta administracyjnego lub agenta pomocy technicznej za pośrednictwem uprawnień administratora delegowanego (DAP).

W przypadku akcji niezwiązanych z dzierżawą klienta w usłudze Lighthouse (na przykład dołączania, dezaktywowania/ponownego aktywowania klienta, zarządzania tagami, przeglądania dzienników) technicy MSP muszą mieć przypisaną rolę w dzierżawie partnera. Aby uzyskać więcej informacji na temat ról dzierżawy partnera, zobacz [Omówienie uprawnień w Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Konfigurowanie Azure AD Privileged Identity Management (PIM)

Dostawcy oprogramowania mogą zminimalizować liczbę osób, które mają dostęp do ról o wysokim poziomie uprawnień w celu zabezpieczenia informacji lub zasobów przy użyciu usługi PIM. Usługa PIM zmniejsza prawdopodobieństwo, że złośliwa osoba uzyska dostęp do zasobów lub autoryzowani użytkownicy przypadkowo wpłyną na poufny zasób. Dostawcy usług zarządzania mogą również przyznawać użytkownikom role just in time o wysokim poziomie uprawnień, aby uzyskiwać dostęp do zasobów, wprowadzać szerokie zmiany i monitorować, co wyznaczoni użytkownicy robią ze swoim uprzywilejowanym dostępem.

> [!NOTE]
> Użycie Azure AD PIM wymaga licencji Azure AD — wersja Premium P2 w dzierżawie partnera.

Poniższe kroki umożliwiają podniesienie poziomu uprawnień użytkowników dzierżawy partnera do ról wyższych uprawnień o określonym zakresie czasu przy użyciu usługi PIM:

1. Utwórz grupę z możliwością przypisywania ról zgodnie z [opisem w artykule Tworzenie grupy do przypisywania ról w Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. Przejdź do [Azure AD — wszystkie grupy](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) i dodaj nową grupę jako członka grupy zabezpieczeń dla ról o wysokich uprawnieniach (na przykład grupy zabezpieczeń agentów administracyjnych dla języka DAP lub podobnie odpowiedniej grupy zabezpieczeń dla ról GDAP).

3. Skonfiguruj uprzywilejowany dostęp do nowej grupy zgodnie z opisem w artykule [Przypisywanie uprawnionych właścicieli i członków dla uprzywilejowanych grup dostępu](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

Aby dowiedzieć się więcej na temat usługi PIM, zobacz [Co to jest Privileged Identity Management?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>Konfigurowanie dostępu warunkowego Azure AD opartego na ryzyku

Dostawcy usług mogą korzystać z dostępu warunkowego opartego na ryzyku, aby upewnić się, że ich pracownicy udowodnili swoją tożsamość przy użyciu uwierzytelniania wieloskładnikowego i zmieniając hasło po wykryciu jako ryzykowny użytkownik (z wyciekiem poświadczeń lub według Azure AD analizy zagrożeń). Użytkownicy muszą również zalogować się ze znanej lokalizacji lub zarejestrowanego urządzenia, gdy zostanie wykryte ryzykowne logowanie. Inne ryzykowne zachowania obejmują logowanie się ze złośliwego lub anonimowego adresu IP lub z nietypowej lub niemożliwej lokalizacji podróży, użycie nietypowego tokenu, użycie hasła z sprayu hasła lub inne nietypowe zachowanie logowania. W zależności od poziomu ryzyka użytkownika dostawcy usług mogą również zablokować dostęp podczas logowania. Aby dowiedzieć się więcej na temat zagrożeń, zobacz [Co to jest ryzyko?](/azure/active-directory/identity-protection/concept-identity-protection-risks)

> [!NOTE]
> Dostęp warunkowy wymaga licencji Azure AD — wersja Premium P2 w dzierżawie partnera. Aby skonfigurować dostęp warunkowy, zobacz [Konfigurowanie dostępu warunkowego Azure Active Directory](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>Zawartość pokrewna

[Uprawnienia do resetowania haseł](/azure/active-directory/roles/permissions-reference#password-reset-permissions) (artykuł)\
[Omówienie uprawnień w Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md) (artykuł)\
[Wyświetl role Azure Active Directory w Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (artykuł)\
[Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artykuł)\
[Omówienie Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (artykuł)\
[Zarejestruj się, aby Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)