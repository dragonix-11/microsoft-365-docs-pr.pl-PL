---
title: Przeglądanie dzienników inspekcji
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
description: Dowiedz się, jak przeglądać dzienniki inspekcji, Microsoft 365 Lighthouse z tematem Dostawcy usług zarządzanych (MSP, Managed Service Providers).
ms.openlocfilehash: e16f6eb83d1fdc9f5aea2fdc6463959cc07e5650
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329449"
---
# <a name="review-audit-logs"></a>Przeglądanie dzienników inspekcji

Microsoft 365 Lighthouse dziennika inspekcji rejestruje akcje generujące zmianę w latarni morskiej lub innych usługach Microsoft 365 usługach. Tworzenie, edytowanie, usuwanie, przypisywanie i akcje zdalne powoduje tworzenie zdarzeń inspekcji, które można przeglądać. Domyślnie inspekcja jest włączona dla wszystkich klientów. Nie można go wyłączyć.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wyświetlać dzienniki inspekcji, musisz mieć jedno z następujących uprawnień:

- Azure Active Directory usługi Azure AD — Administrator globalny dzierżawy partnerskiej

- Rola Centrum partnerskiego Firmy Microsoft — Agent administracyjny

## <a name="review-audit-logs"></a>Przeglądanie dzienników inspekcji

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Dzienniki inspekcji**.

    > [!NOTE]
    > Wyświetlanie nowych dzienników może potrwać do godziny. Przejdź do odpowiedniej usługi, aby wyświetlić najnowsze zmiany.

2. W razie potrzeby możesz filtrować dzienniki, korzystając z następujących opcji:

    - **Zakres dat** — poprzedni miesiąc, tydzień lub dzień.
    - **Dzierżawcy** — tagi dzierżawy lub nazwy dzierżaw klientów.
    - **Aktywność** — Microsoft 365 aktywności odpowiadającej wykonanej akcji. Aby uzyskać więcej informacji, zobacz [tabelę](#activities) Działania.
    - **Zainicjowane przez** — KtoTo akcję.

3. Wybierz dziennik z listy, aby wyświetlić wszystkie szczegóły, łącznie z **treścią** Żądania.

    Aby wyeksportować dane dziennika do pliku wartości rozdzielanych przecinkami (.csv), wybierz pozycję **Eksportuj**.

## <a name="activities"></a>Działania

W poniższej tabeli wymieniono działania zarejestrowane w dziennikach inspekcji w latarniach morski. Lista może ulec zmianie w przypadku tworzenia nowych akcji. Możesz użyć działań wymienionych w dzienniku inspekcji, aby sprawdzić, które działanie zostało zainicjowane.<br><br>

| Nazwa działania | Obszar w Latarnia morska | Inicjowane działanie | Usługa, w przypadku których ma to wpływ |
|--|--|--|--|
| **stosowanie** lub **wdrażanie** | Dzierżawcy | Stosowanie planu wdrażania | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Dzierżawcy | Stosowanie tagu od klienta | Latarnia morska |
| **changeDeploymentStatus** lub **assign** | Dzierżawcy | Aktualizowanie stanu planu działań dla planu wdrażania | Latarnia morska |
| **managedTenantOperations** | Dzierżawcy | Wyświetlanie informacji o planie wdrażania | Azure AD |
| **offboardTenant** | Dzierżawcy | Dezaktywuj klienta | Latarnia morska |
| **resetTenantOnboardingStatus** | Dzierżawcy | Reagowanie klienta | Latarnia morska |
| **tenantTags** | Dzierżawcy | Tworzenie lub usuwanie tagu | Latarnia morska |
| **tenantCustomizedInformation** | Dzierżawcy | Tworzenie, aktualizowanie lub usuwanie witryny internetowej klienta lub informacji kontaktowych | Latarnia morska |
| **unassignTag** | Dzierżawcy | Usuwanie tagu z klienta | Latarnia morska |
| **sprawdź poprawność** | Dzierżawcy | Testowanie planu wdrażania | Azure AD |
| **blockUserSignin** | Użytkownicy | Blokowanie logowania | Azure AD |
| **confirmUsersComprom nieuprawnianie** | Użytkownicy | Upewnij się, że użytkownik został naruszony | Azure AD |
| **dismissUsersRisk** | Użytkownicy | Odrzucenie ryzyka użytkownika | Azure AD |
| **resetUserPassword** | Użytkownicy | Resetuj hasło | Azure AD |
| **getConditionalAccessPolicies** | Użytkownicy | Wyświetlanie zasad certyfikacji wymagających uwierzytelniania wieloskładnikowego | Azure AD |
| **getTenantIDToTenantNameMap** | Użytkownicy | Wyszukiwanie identyfikatorów | Azure AD |
| **getUsers** | Użytkownicy | Wyszukiwanie użytkowników | Azure AD |
| **getUsersWithoutMfa** | Użytkownicy | Wyświetlanie użytkowników, którzy nie są zarejestrowani w ramach uwierzytelniania MFA | Azure AD |
| **getSsprEnabledButNotRegisteredUsers** | Użytkownicy | Wyświetlanie użytkowników, którzy nie zarejestrował się dla konta SSPR | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Użytkownicy | Włączanie uwierzytelniania wieloskładnikowego (MFA) przy użyciu ustawień domyślnych zabezpieczeń | Azure AD |
|**getCompliancePolicyInfo** | Urządzenia | Wyświetlanie zasad | MEM
|**getDeviceCompliancePolicyStates** | Urządzenia | Wyświetlanie stanów zasad | MEM
|**getDeviceCompliancePolicySettingStates** | Urządzenia | Wyświetlanie niezgodnych ustawień | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | Urządzenia | Wyświetlanie niezgodnych urządzeń | MEM
|**getTenantsDeviceCompliancePolicies** | Urządzenia | Porównywanie zasad | MEM
| **restartDevice** | Urządzenia | Uruchom ponownie | MEM |
| **syncDevice** | Urządzenia | Synchronizuj | MEM |
| **rebootNow** | Zarządzanie zagrożeniami | Ponowne uruchamianie | MEM |
| **reprovision** | Windows 365 | Ponów próbę inicjowania obsługi administracyjnej | Windows 365 |
| **getDeviceUserInfo** | Zarządzanie zagrożeniami | Wyświetlanie informacji o użytkowniku urządzenia zarządzanego  | MEM |
| **getManagedDevice**, **remoteActionAudits** lub **deviceActionResults** | Zarządzanie zagrożeniami | Wyświetlanie informacji o urządzeniu zarządzanym  | MEM |
| **windowsDefenderScanFull** | Zarządzanie zagrożeniami | Pełne skanowanie | MEM |
| **windowsDefenderKan** | Zarządzanie zagrożeniami | Szybkie skanowanie | MEM |
| **windowsDefenderUpdateSignatures** | Zarządzanie zagrożeniami | Aktualizowanie oprogramowania antywirusowego | MEM |

## <a name="next-steps"></a>Następne kroki

Jeśli potrzebujesz więcej informacji, skorzystaj z interfejsu API Graph Microsoft, aby uzyskać dostęp do większej liczby zdarzeń inspekcji. Aby uzyskać więcej informacji, zobacz [Omówienie zarządzania wieloma dzierżawami przy użyciu Microsoft 365 Lighthouse API](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
