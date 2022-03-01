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
ms.openlocfilehash: c40805267320488e79c774954fd8f6bd696449fa
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "63009154"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Konfigurowanie Microsoft 365 Lighthouse zabezpieczeń portalu

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i są dostępne tylko dla partnerów spełniających [te wymagania](m365-lighthouse-requirements.md). Jeśli Twoja organizacja nie ma konta Microsoft 365 Lighthouse, zobacz Logowanie [się w celu Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Ochrona dostępu do danych klientów, gdy dostawca usług zarządzanych (MSP) delegował uprawnienia dostępu do swoich dzierżaw jest priorytetem chciwości. Microsoft 365 Lighthouse posiada zarówno wymagane, jak i opcjonalne funkcje, które pomogą Ci skonfigurować zabezpieczenia portalu Lighthouse.

## <a name="set-up-multifactor-authentication-mfa"></a>Konfigurowanie uwierzytelniania wieloskładnikowego (MFA)

Jak wspomniano we wpisie w blogu [Twoja pa$$word ma znaczenie](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> "Hasło nie ma znaczenia, ale uwierzytelniania wieloskładnikowego nie ma znaczenia. Jak wynika z naszych analiz, w przypadku używania uwierzytelniania wieloskładnikowego bezpieczeństwo Twojego konta jest większe niż 99,9%.

Gdy użytkownicy po raz pierwszy uzyskają dostęp do latarni morskiej, zostanie wyświetlony monit o skonfigurowanie uwierzytelniania wieloskładnikowego, jeśli ich konto Microsoft 365 nie ma jeszcze skonfigurowane. Użytkownicy nie będą mogli uzyskać dostępu do usługi Lighthouse do momentu ukończenia wymaganego kroku konfiguracji uwierzytelniania wieloskładnikowego. Aby dowiedzieć się więcej o metodach uwierzytelniania, zobacz [Konfigurowanie logowania Microsoft 365 do uwierzytelniania wieloskładnikowego](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-roles-to-manage-customer-tenants"></a>Konfigurowanie ról w celu zarządzania dzierżawami klientów

Dostęp do danych i ustawień dzierżawy klienta w aplikacji Lighthouse jest ograniczony do ról agenta administracyjnego i agenta pomocy technicznej w programie Cloud Solutions Provider (CSP).

Możesz sprawdzić, którzy użytkownicy w dzierżawie partnerskiej mają role agenta administracyjnego i agenta pomocy technicznej, przeglądając informacje o członkostwie w grupach zabezpieczeń na stronie [Azure AD — Wszystkie](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) grupy. Aby dowiedzieć się, jak przypisywać użytkownikom role programu CSP i inne uprawnienia, zobacz [Przypisywanie ról i uprawnień użytkownikom](/partner-center/permissions-overview). Jeśli nie masz jeszcze uprawnień dostępu delegowanego do dzierżaw klientów jako program MSP, dowiedz się, jak je uzyskać, z artykułu Uzyskiwanie uprawnień do zarządzania usługą lub subskrypcją [klienta](/partner-center/customers-revoke-admin-privileges).

W poniższej tabeli wymieniono różne strony w latarni morskiej oraz uprawnienia wymagane do wyświetlania danych dzierżawy klientów i wykonywania działań dotyczących ich danych i ustawień dla ról agenta administracyjnego i agenta pomocy technicznej.<br><br>

| Strona latarni morskiej | Uprawnienia agenta administracyjnego | Uprawnienia agenta pomocy technicznej |
|--|--|--|
| Home | <ul><li>Wyświetl wszystko</li></ul> | <ul><li>Wyświetl wszystko</li></ul> |
| Dzierżawcy | <ul><li>Wyświetl wszystko</li><li>Aktualizowanie kontaktów klientów i witryny internetowej</li><li>Wyświetlanie i stosowanie planów wdrażania</li></ul> | <ul><li>Wyświetl wszystko</li><li>Aktualizowanie kontaktów klientów i witryny internetowej</li><li>Wyświetl plany wdrażania</li></ul> |
| Użytkownicy | <ul><li>Wyświetl wszystko</li><li>Resetuj hasło</li><li>Blokowanie logowania</li><li>Włączanie uwierzytelniania wieloskładnikowego</li></ul> | <ul><li>Wyświetl wszystko</li><li>Resetuj hasło</li><li>Blokowanie logowania</li></ul> |
| Urządzenia | <ul><li>Wyświetl wszystko</li></ul> | <ul><li>Wyświetl wszystko</li></ul> |
| Zagrożenia | <ul><li>Wyświetl wszystko</li><li>Uruchamianie szybkiego skanowania</li><li>Uruchom pełne skanowanie</li><li>Ponowne uruchamianie urządzenia</li><li>Aktualizowanie oprogramowania antywirusowego</li></ul> | <ul><li>Wyświetl wszystko</li></ul> |
| Linie bazowe | <ul><li>Wyświetl wszystko</li></ul> | <ul><li>Wyświetl wszystko</li></ul> |
| Kondycja usługi | <ul><li>Wyświetl wszystko*</li></ul> | <ul><li>Wyświetl wszystko*</li></ul> |

> [!NOTE]
> Obecnie, aby można było podjąć działania oznaczone znakiem * w tabeli, użytkownicy muszą również mieć rolę usługi Azure AD w dzierżawie partnera z następującym zestawem właściwości: **microsoft.office365.serviceHealth/allEntities/allTasks**. Aby uzyskać listę ról usługi Azure AD, zobacz [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference).

Mając ogólne uprawnienia skojarzone z rolą agenta administracyjnego, zalecamy zastosowanie zasady dostępu o jak najmniejszych uprawnieniach [](/azure/active-directory/develop/secure-least-privileged-access) podczas wyznaczania użytkownika dzierżawy partnerskiej na agenta administratora a agenta pomocy technicznej. Jednym ze sposobów jest przypisanie roli agenta pomocy technicznej do wymaganych użytkowników dzierżawy partnerskiej. Dzięki temu mogą wyświetlać dane i ustawienia klientów, ale nie wprowadzać szerokich zmian. Następnie w razie potrzeby użyj funkcji zatwierdzania dostępu w czasie rzeczywistym dostępnego w usłudze Azure AD Privileged Identity Management (PIM), aby nadać użytkownikom rolę agenta administratora z zakresem czasu.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Konfigurowanie usługi Azure AD Privileged Identity Management (PIM)

MsP mogą zminimalizować liczbę osób, które mają dostęp do zabezpieczania informacji lub zasobów, przy użyciu usługi Azure AD Privileged Identity Management (PIM). Dane pim ograniczają ryzyko, że złośliwy użytkownik uzyskuje dostęp do zasobów lub autoryzowanych użytkowników w sposób niezamierzony i wpływa na zasoby poufne. Konta MSP mogą także udzielać użytkownikom dostępu z uprawnieniami tylko na czas i monitorować, co wyznaczeni użytkownicy robią z uprawnieniami dostępu.

> [!NOTE]
> Korzystanie z usługi Azure AD PIM wymaga Azure AD — wersja Premium P2 licencji usługi w dzierżawie partnera.

Poniższe kroki uacyjniają użytkowników dzierżawy partnerskiej do ról agenta administracyjnego z zakresem czasu przy użyciu usługi Azure AD PIM:

1. Utwórz grupę z przypisaną rolą zgodnie z opisem w artykule Tworzenie grupy służącej do przypisywania [ról w Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. Przejdź do [usługi Azure AD — Wszystkie](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) grupy i dodaj nową grupę jako członka grupy Agentów administratora.

3. Skonfiguruj dostęp z uprawnieniami do nowej grupy zgodnie z opisem w artykule Przypisywanie uprawnionych właścicieli i członków [do grup dostępu z uprawnieniami](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

Aby dowiedzieć się więcej, [zobacz Co to jest Privileged Identity Management?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="other-roles-and-permissions"></a>Inne role i uprawnienia

W poniższej tabeli wymieniono role dzierżawy partnerskiej i skojarzone z nimi uprawnienia.<br><br>

| Role dzierżawy partnerów | Uprawnienia w dzierżawie partnera |
|--|--|
| Administrator globalny dzierżawy partnerskiej | <ul><li>Zarejestruj się w Latarnia morska w centrum administracyjne platformy Microsoft 365.</li><li>Zaakceptuj umowę partnera podczas pierwszego uruchomienia.</li><li>Wyświetlanie dzierżaw klientów na stronie Dzierżawy.</li><li>Aktywowanie i dezaktywowanie dzierżawy.</li><li>Aktualizuj kontakty klientów i witrynę internetową.</li><li>Tworzenie, aktualizowanie i usuwanie tagów.</li><li>Przypisywanie i usuwanie tagów w dzierżawie klienta.</li></ul> |
| Administrator dzierżawy partnerskiej z co najmniej jedną dzierżawą<br> Rola usługi Azure AD przypisana z następującym zestawem właściwości:<br> **microsoft.office365.supportTickets/allEntities/allTasks**<br> (Aby uzyskać listę ról usługi Azure AD, zobacz Wbudowane role [w usłudze Azure AD](/azure/active-directory/roles/permissions-reference)). | <ul><li>Tworzenie zgłoszeń serwisowych do usługi Lighthouse.</li></ul> |


## <a name="related-content"></a>Zawartość pokrewna

[Omówienie Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (artykuł)\
[Rejestracja w Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)