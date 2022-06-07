---
title: Krok nr 2. Ochrona kont uprzywilejowanych platformy Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- m365initiative-coredeploy
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Ten artykuł zawiera informacje o ochronie uprzywilejowanego dostępu do dzierżawy platformy Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3da8a6279d122a056a168485145c171f9d3d7f5f
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930202"
---
# <a name="step-2-protect-your-microsoft-365-privileged-accounts"></a>Krok nr 2. Ochrona kont uprzywilejowanych platformy Microsoft 365

*Ten artykuł dotyczy zarówno platformy Microsoft 365 Enterprise, jak i usługi Office 365 Enterprise.*

Naruszenia zabezpieczeń dzierżawy platformy Microsoft 365, w tym zbieranie informacji i ataki wyłudzające informacje, są zazwyczaj wykonywane przez naruszenie poświadczeń uprzywilejowanego konta platformy Microsoft 365. Zabezpieczenia w chmurze to partnerstwo między Tobą a firmą Microsoft:
  
- Usługi w chmurze firmy Microsoft są oparte na fundamencie zaufania i bezpieczeństwa. Firma Microsoft zapewnia mechanizmy kontroli zabezpieczeń i możliwości ułatwiające ochronę danych i aplikacji.
    
- Jesteś właścicielem danych i tożsamości oraz ponosisz odpowiedzialność za ich ochronę, bezpieczeństwo zasobów lokalnych i bezpieczeństwo składników chmury, które kontrolujesz.
    
Firma Microsoft oferuje możliwości ochrony organizacji, ale są one skuteczne tylko wtedy, gdy z nich korzystasz. Jeśli ich nie używasz, możesz być narażony na ataki. Aby chronić konta uprzywilejowane, firma Microsoft jest tutaj, aby ułatwić ci szczegółowe instrukcje dotyczące:
  
1. Utwórz dedykowane, uprzywilejowane konta oparte na chmurze i używaj ich tylko w razie potrzeby.
    
2. Skonfiguruj uwierzytelnianie wieloskładnikowe (MFA) dla dedykowanych kont uprzywilejowanych platformy Microsoft 365 i użyj najsilniejszej formy uwierzytelniania pomocniczego.

3. Ochrona kont uprzywilejowanych przy użyciu tożsamości zero zaufania i zaleceń dotyczących dostępu do urządzeń.

> [!NOTE]
> Aby zabezpieczyć uprzywilejowane role, zapoznaj się z [artykułem Najlepsze rozwiązania dotyczące ról usługi Azure AD](/azure/active-directory/roles/best-practices) w celu zabezpieczenia uprzywilejowanego dostępu do dzierżawy.

## <a name="1-create-dedicated-privileged-cloud-based-user-accounts-and-use-them-only-when-necessary"></a>1. Tworzenie dedykowanych, uprzywilejowanych kont użytkowników opartych na chmurze i używanie ich tylko w razie potrzeby

Zamiast korzystać z codziennych kont użytkowników, do których przypisano role administratora, utwórz dedykowane konta użytkowników, które mają role administratora w usłudze Azure AD. 

Od tego momentu logujesz się przy użyciu dedykowanych kont uprzywilejowanych tylko w przypadku zadań wymagających uprawnień administratora. Całą inną administrację platformy Microsoft 365 należy wykonać, przypisując inne role administracyjne do kont użytkowników.
  
> [!NOTE]
> Wymaga to dodatkowych kroków, aby wylogować się jako codzienne konto użytkownika i zalogować się przy użyciu dedykowanego konta administratora. Należy to jednak robić sporadycznie tylko w przypadku operacji administratora. Należy wziąć pod uwagę, że odzyskanie subskrypcji platformy Microsoft 365 po naruszeniu konta administratora wymaga o wiele więcej kroków.

Należy również utworzyć [konta dostępu awaryjnego](/azure/active-directory/roles/security-emergency-access) , aby zapobiec przypadkowemu zablokowaniu usługi Azure AD.

Możesz dodatkowo chronić konta uprzywilejowane przy użyciu usługi Azure AD Privileged Identity Management (PIM) na potrzeby przypisywania ról administratora na żądanie w ramach just in time. 
 
## <a name="2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-privileged-accounts"></a>2. Konfigurowanie uwierzytelniania wieloskładnikowego dla dedykowanych kont uprzywilejowanych platformy Microsoft 365

Uwierzytelnianie wieloskładnikowe (MFA) wymaga dodatkowych informacji poza nazwą konta i hasłem. Platforma Microsoft 365 obsługuje następujące dodatkowe metody weryfikacji:
  
- Aplikacja Microsoft Authenticator
- Rozmowa telefoniczna
- Losowo wygenerowany kod weryfikacyjny wysyłany za pośrednictwem wiadomości SMS
- Karta inteligentna (wirtualna lub fizyczna) (wymaga uwierzytelniania federacyjnego)
- Urządzenie biometryczne
- Token Oauth
    
>[!Note]
>W przypadku organizacji, które muszą przestrzegać standardów NIST (National Institute of Standards and Technology), korzystanie z dodatkowych metod weryfikacji opartych na rozmowach telefonicznych lub wiadomościach SMS jest ograniczone. Kliknij [tutaj](https://pages.nist.gov/800-63-FAQ/#q-b01) , aby uzyskać szczegółowe informacje.
>

Jeśli jesteś małą firmą korzystającą z kont użytkowników przechowywanych tylko w chmurze (model tożsamości tylko w chmurze), [skonfiguruj uwierzytelnianie wieloskładnikowe](/office365/admin/security-and-compliance/set-up-multi-factor-authentication) w celu skonfigurowania uwierzytelniania wieloskładnikowego przy użyciu połączenia telefonicznego lub kodu weryfikacyjnego wiadomości SMS wysłanego na telefon inteligentny dla każdego dedykowanego konta uprzywilejowanego.
    
Jeśli jesteś większą organizacją korzystającą z hybrydowego modelu tożsamości platformy Microsoft 365, masz więcej opcji weryfikacji. Jeśli masz już infrastrukturę zabezpieczeń dla silniejszej metody uwierzytelniania pomocniczego, [skonfiguruj](../admin/security-and-compliance/set-up-multi-factor-authentication.md) uwierzytelnianie wieloskładnikowe i skonfiguruj każde dedykowane konto uprzywilejowane dla odpowiedniej metody weryfikacji.
  
Jeśli infrastruktura zabezpieczeń dla żądanej silniejszej metody weryfikacji nie jest w miejscu i działa dla usługi Microsoft 365 MFA, zdecydowanie zalecamy skonfigurowanie dedykowanych uprzywilejowanych kont przy użyciu uwierzytelniania wieloskładnikowego przy użyciu aplikacji Microsoft Authenticator, połączenia telefonicznego lub kodu weryfikacyjnego wiadomości SMS wysłanego do telefonu inteligentnego dla uprzywilejowanych kont jako tymczasowego środka bezpieczeństwa. Nie pozostawiaj dedykowanych kont uprzywilejowanych bez dodatkowej ochrony zapewnianej przez usługę MFA.
  
Aby uzyskać więcej informacji, zobacz [MFA for Microsoft 365 (Uwierzytelnianie wieloskładnikowe dla platformy Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)).
  
## <a name="3-protect-administrator-accounts-with-zero-trust-identity-and-device-access-recommendations"></a>3. Ochrona kont administratorów przy użyciu tożsamości zero zaufania i zaleceń dotyczących dostępu do urządzeń

Aby zapewnić bezpieczną i produktywną siłę roboczą, firma Microsoft udostępnia zestaw zaleceń dotyczących [tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md). W przypadku tożsamości użyj zaleceń i ustawień w następujących artykułach:

- [Wymagania wstępne](../security/office-365-security/identity-access-prerequisites.md)
- [Wspólne zasady tożsamości i dostępu do urządzeń](../security/office-365-security/identity-access-policies.md)

## <a name="additional-protections-for-enterprise-organizations"></a>Dodatkowe zabezpieczenia dla organizacji korporacyjnych

Użyj tych dodatkowych metod, aby upewnić się, że konto uprzywilejowane i konfiguracja, która jest wykonywana przy jego użyciu, są możliwie najbezpieczniejsze.
  
### <a name="privileged-access-workstation"></a>Stacja robocza z dostępem uprzywilejowanym

Aby zapewnić, że wykonywanie zadań o wysokim poziomie uprawnień jest możliwie najbezpieczniejsze, użyj stacji roboczej z uprzywilejowanym dostępem (PAW). Paw to dedykowany komputer, który jest używany tylko do poufnych zadań konfiguracji, takich jak konfiguracja platformy Microsoft 365, która wymaga konta uprzywilejowanego. Ponieważ ten komputer nie jest używany codziennie do przeglądania Internetu lub poczty e-mail, jest lepiej chroniony przed atakami i zagrożeniami internetowymi.
  
Aby uzyskać instrukcje dotyczące konfigurowania stacji roboczej z dostępem typu PAW, zobacz [https://aka.ms/cyberpaw](/security/compass/privileged-access-devices).

Aby włączyć usługę Azure PIM dla kont dzierżawy i administratora usługi Azure AD, zobacz [kroki konfigurowania usługi PIM](/azure/active-directory/active-directory-privileged-identity-management-configure).

Aby opracować kompleksowy plan zabezpieczania uprzywilejowanego dostępu przed cyberagresjami, zobacz [Zabezpieczanie uprzywilejowanego dostępu do wdrożeń hybrydowych i w chmurze w usłudze Azure AD](/azure/active-directory/admin-roles-best-practices).

### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

Zamiast stałego przypisywania kont uprzywilejowanych do roli administratora, możesz użyć usługi Azure AD PIM, aby w razie potrzeby włączyć przypisanie roli administratora na żądanie i just in time.
  
Konta administratorów przechodzą od stałych administratorów do uprawnionych administratorów. Rola administratora jest nieaktywna, dopóki ktoś jej nie potrzebuje. Następnie ukończysz proces aktywacji, aby dodać rolę administratora do konta uprzywilejowanego przez wstępnie określony czas. Gdy czas wygaśnie, usługa PIM usunie rolę administratora z konta uprzywilejowanego.
  
Użycie usługi PIM i tego procesu znacznie skraca czas, przez który uprzywilejowane konta są narażone na ataki i użycie przez złośliwych użytkowników.

Usługa PIM jest dostępna w usłudze Azure Active Directory Premium P2, która jest dołączona do platformy Microsoft 365 E5. Alternatywnie możesz kupić indywidualne licencje usługi Azure Active Directory Premium P2 dla kont administratorów.
  
Więcej informacji można znaleźć w następujących artykułach:

- [Usługa Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).
- [Zabezpieczanie uprzywilejowanego dostępu do wdrożeń hybrydowych i w chmurze w usłudze Azure AD](/azure/active-directory/roles/security-planning)
  

### <a name="privileged-access-management"></a>Privileged Access Management

Zarządzanie dostępem uprzywilejowanym jest włączone przez skonfigurowanie zasad określających dostęp just in time dla działań opartych na zadaniach w dzierżawie. Może pomóc w ochronie organizacji przed naruszeniami, które mogą korzystać z istniejących kont administratorów uprzywilejowanych mających stały dostęp do poufnych danych lub dostęp do krytycznych ustawień konfiguracji. Można na przykład skonfigurować zasady zarządzania dostępem uprzywilejowanym, które wymagają jawnego zatwierdzenia dostępu i zmiany ustawień skrzynki pocztowej organizacji w dzierżawie.

W tym kroku włączysz zarządzanie dostępem uprzywilejowanym w dzierżawie i skonfigurujesz zasady dostępu uprzywilejowanego, które zapewniają dodatkowe zabezpieczenia dostępu opartego na zadaniach do danych i ustawień konfiguracji organizacji. Aby rozpocząć pracę z uprzywilejowanym dostępem w organizacji, należy wykonać trzy podstawowe kroki:

- Tworzenie grupy osoby zatwierdzającej
- Włączanie dostępu uprzywilejowanego
- Tworzenie zasad zatwierdzania

Zarządzanie dostępem uprzywilejowanym umożliwia organizacji działanie bez stałych uprawnień i zapewnianie warstwy ochrony przed lukami w zabezpieczeniach wynikającymi z takiego stałego dostępu administracyjnego. Dostęp uprzywilejowany wymaga zatwierdzeń do wykonywania każdego zadania, które ma zdefiniowane skojarzone zasady zatwierdzania. Użytkownicy, którzy muszą wykonywać zadania zawarte w zasadach zatwierdzania, muszą zażądać zatwierdzenia dostępu i otrzymać je.

Aby włączyć zarządzanie dostępem uprzywilejowanym, zobacz [Konfigurowanie zarządzania dostępem uprzywilejowanym](/office365/securitycompliance/privileged-access-management-configuration).

Aby uzyskać więcej informacji, zobacz [Privileged access management (Zarządzanie dostępem uprzywilejowanym).](/office365/securitycompliance/privileged-access-management-overview)

### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>Oprogramowanie do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM) na potrzeby rejestrowania na platformie Microsoft 365

Oprogramowanie SIEM uruchamiane na serwerze wykonuje w czasie rzeczywistym analizę alertów zabezpieczeń i zdarzeń utworzonych przez aplikacje i sprzęt sieciowy. Aby umożliwić serwerowi SIEM uwzględnianie alertów zabezpieczeń i zdarzeń platformy Microsoft 365 w jego funkcjach analizy i raportowania, zintegruj usługę Azure AD z systemem SEIM. Zobacz [Wprowadzenie do integracji z dziennikiem platformy Azure](/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Następny krok

[![Ochrona kont użytkowników platformy Microsoft 365](../media/deploy-identity-solution-overview/microsoft-365-secure-sign-in.png)](microsoft-365-secure-sign-in.md)

Kontynuuj [krok 3](microsoft-365-secure-sign-in.md) , aby zabezpieczyć konta użytkowników.
