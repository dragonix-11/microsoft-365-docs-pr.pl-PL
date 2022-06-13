---
title: Przeglądanie dzienników inspekcji w Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: vivkuma
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się, jak przeglądać dzienniki inspekcji.
ms.openlocfilehash: a357d6d4383fb967b09d1ce3dc1be68d7fd2ca4f
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017515"
---
# <a name="review-audit-logs-in-microsoft-365-lighthouse"></a>Przeglądanie dzienników inspekcji w Microsoft 365 Lighthouse

Microsoft 365 Lighthouse dzienniki inspekcji rejestrują akcje, które generują zmianę w usłudze Lighthouse lub innych usługach Microsoft 365. Wszystkie akcje tworzenia, edytowania, usuwania, przypisywania i zdalnego tworzenia zdarzeń inspekcji, które można przeglądać. Domyślnie inspekcja jest włączona dla wszystkich klientów. Nie można go wyłączyć.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wyświetlić dzienniki inspekcji, musisz mieć jedno z następujących uprawnień:

- rola Azure Active Directory (Azure AD) — administrator globalny dzierżawy partnera

- Rola Centrum partnerskiego firmy Microsoft — agent administracyjny

## <a name="review-audit-logs"></a>Przeglądanie dzienników inspekcji

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Dzienniki inspekcji**.

    > [!NOTE]
    > Wyświetlenie nowych dzienników może potrwać do 1 godziny. Przejdź do odpowiedniej usługi, aby wyświetlić najnowsze zmiany.

2. W razie potrzeby przefiltruj dzienniki przy użyciu następujących opcji:

    - **Zakres dat** — poprzedni miesiąc, tydzień lub dzień.
    - **Dzierżawy** — tagi dzierżawy lub nazwy dzierżawy klienta.
    - **Działanie** — Microsoft 365 typ działania odpowiadający wykonanej akcji. Aby uzyskać więcej informacji, zobacz tabelę [Działania](#activities) .
    - **Zainicjowane przez** — KtoTo zainicjowało akcję.

3. Wybierz dziennik z listy, aby wyświetlić pełne szczegóły, w tym treść **żądania** .

    Aby wyeksportować dane dziennika do pliku wartości rozdzielanych przecinkami (.csv), wybierz pozycję **Eksportuj**.

## <a name="activities"></a>Działania

W poniższej tabeli wymieniono działania przechwycone w dziennikach inspekcji usługi Lighthouse. Lista może ulec zmianie w miarę tworzenia nowych akcji. Możesz użyć działania wymienionego w dzienniku inspekcji, aby zobaczyć, która akcja została zainicjowana.<br><br>

| Nazwa działania | Obszar w latarni morskiej | Zainicjowano akcję | Wpływ na usługę |
|--|--|--|--|
| **zastosuj** lub **wdróż** | Najemców | Stosowanie planu wdrożenia | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Najemców | Stosowanie tagu od klienta | Lighthouse |
| **changeDeploymentStatus** lub **przypisz** | Najemców | Aktualizowanie stanu planu akcji dla planu wdrożenia | Lighthouse |
| **managedTenantOperations** | Najemców | Wyświetlanie informacji o planie wdrożenia | Azure AD |
| **offboardTenant** | Najemców | Inaktywowanie klienta | Lighthouse |
| **resetTenantOnboardingStatus** | Najemców | Reaktywny klient | Lighthouse |
| **tenantTags** | Najemców | Tworzenie lub usuwanie tagu | Lighthouse |
| **tenantCustomizedInformation** | Najemców | Tworzenie, aktualizowanie lub usuwanie witryny internetowej klienta lub informacji kontaktowych | Lighthouse |
| **unassignTag** | Najemców | Usuwanie tagu z klienta | Lighthouse |
| **Sprawdzania poprawności** | Najemców | Testowanie planu wdrożenia | Azure AD |
| **blockUserSignin** | Użytkownicy | Blokuj logowanie | Azure AD |
| **confirmUsersCompromised** | Użytkownicy | Potwierdzanie naruszenia zabezpieczeń użytkownika | Azure AD |
| **dismissUsersRisk** | Użytkownicy | Odrzucanie ryzyka użytkownika | Azure AD |
| **resetUserPassword** | Użytkownicy | Resetuj hasło | Azure AD |
| **getConditionalAccessPolicies** | Użytkownicy | Wyświetlanie zasad urzędu certyfikacji wymagających uwierzytelniania wieloskładnikowego | Azure AD |
| **getTenantIDToTenantNameMap** | Użytkownicy | Wyszukiwanie identyfikatorów | Azure AD |
| **getUsers** | Użytkownicy | Wyszukaj użytkowników | Azure AD |
| **getUsersWithoutMfa** | Użytkownicy | Wyświetlanie użytkowników, którzy nie są zarejestrowani w usłudze MFA | Azure AD |
| **getSsprEnabledButNotRegisteredUsers** | Użytkownicy | Wyświetlanie użytkowników, którzy nie są zarejestrowani na potrzeby samoobsługowego resetowania hasła | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Użytkownicy | Włączanie uwierzytelniania wieloskładnikowego (MFA) z wartościami domyślnymi zabezpieczeń | Azure AD |
|**getCompliancePolicyInfo** | Urządzeń | Wyświetlanie zasad | MEM
|**getDeviceCompliancePolicyStates** | Urządzeń | Wyświetlanie stanów zasad | MEM
|**getDeviceCompliancePolicySettingStates** | Urządzeń | Wyświetlanie niezgodnych ustawień | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | Urządzeń | Wyświetlanie niezgodnych urządzeń | MEM
|**getTenantsDeviceCompliancePolicies** | Urządzeń | Porównanie zasad | MEM
| **restartDevice** | Urządzeń | Uruchom ponownie | MEM |
| **syncDevice** | Urządzeń | Synchronizuj | MEM |
| **rebootNow** | Zarządzanie zagrożeniami | Ponownie obuwać | MEM |
| **ponowne aprowizowanie** | Windows 365 | Ponów próbę aprowizacji | Windows 365 |
| **getDeviceUserInfo** | Zarządzanie zagrożeniami | Wyświetlanie informacji o użytkowniku urządzenia zarządzanego  | MEM |
| **getManagedDevice**, **remoteActionAudits** lub **deviceActionResults** | Zarządzanie zagrożeniami | Wyświetlanie informacji o urządzeniu zarządzanym  | MEM |
| **windowsDefenderScanFull** | Zarządzanie zagrożeniami | Pełne skanowanie | MEM |
| **windowsDefenderScan** | Zarządzanie zagrożeniami | Szybkie skanowanie | MEM |
| **windowsDefenderUpdateSignatures** | Zarządzanie zagrożeniami | Aktualizowanie programu antywirusowego | MEM |

## <a name="next-steps"></a>Następne kroki

W razie potrzeby użyj usługi Microsoft interfejs Graph API, aby uzyskać dostęp do większej liczby zdarzeń inspekcji. Aby uzyskać więcej informacji, zobacz [Omówienie zarządzania wieloma dzierżawami przy użyciu interfejsu API Microsoft 365 Lighthouse](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)\
[Wyświetlanie ról Azure Active Directory w Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (artykuł)