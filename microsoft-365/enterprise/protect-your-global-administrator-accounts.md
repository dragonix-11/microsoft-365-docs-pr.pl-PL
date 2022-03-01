---
title: Krok nr 2. Ochrona konta Microsoft 365 z uprawnieniami
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Ten artykuł zawiera informacje na temat ochrony dostępu z uprawnieniami do dzierżawy Microsoft 365 dzierżawy.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ff20b8dcaf203771b0c3a935b67e83eb291ec75e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013878"
---
# <a name="step-2-protect-your-microsoft-365-privileged-accounts"></a>Krok nr 2. Ochrona konta Microsoft 365 z uprawnieniami

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Naruszenia zabezpieczeń dzierżawy usługi Microsoft 365, w tym ataki chowania informacji i wyłudzania informacji, są zazwyczaj wykonywane przez naruszenie poświadczeń konta Microsoft 365 uprawnienia. Bezpieczeństwo w chmurze to partnerstwo między Tobem a firmą Microsoft:
  
- Podstawą usług firmy Microsoft w chmurze jest zaufanie i bezpieczeństwo. Firma Microsoft udostępnia funkcje i mechanizmy kontroli zabezpieczeń, które pomagają chronić dane i aplikacje.
    
- Jesteś właścicielem danych i tożsamości oraz ponosisz odpowiedzialność za ich ochronę, bezpieczeństwo zasobów lokalnych i bezpieczeństwo składników chmury, które kontrolujesz.
    
Firma Microsoft udostępnia funkcje, które pomagają chronić Twoją organizację, ale są skuteczne tylko wtedy, gdy ich używasz. Jeśli ich nie używasz, możesz być narażony na ataki. W celu ochrony Twoich kont uprzywilejowanych firma Microsoft pomoże Ci uzyskać szczegółowe instrukcje dotyczące:
  
1. Twórz dedykowane konta z uprawnieniami w chmurze i korzystaj z nich tylko wtedy, gdy jest to konieczne.
    
2. Skonfiguruj uwierzytelnianie wieloskładnikowe dla dedykowanych Microsoft 365 z uprawnieniami i użyj najsilniejszej metody uwierzytelniania pomocniczego.

3. Ochrona kont z uprawnieniami za pomocą zaleceń dotyczących tożsamości bez zaufania i dostępu do urządzeń.

## <a name="1-create-dedicated-privileged-cloud-based-user-accounts-and-use-them-only-when-necessary"></a>1. Tworzenie dedykowanych, uprzywilejowanych kont użytkowników w chmurze i korzystanie z nich tylko wtedy, gdy jest to konieczne

Zamiast korzystać ze zwykłych kont użytkowników, do których przypisano role administratora, utwórz dedykowane konta użytkowników z rolami administratorów w usłudze Azure AD. 

Od tego momentu będziesz logować się przy użyciu dedykowanych kont uprzywilejowanych tylko w przypadku zadań wymagających uprawnień administratora. Pozostałe zadania Microsoft 365 musi się odbywać przez przypisanie innych ról administracyjnych do kont użytkowników.
  
> [!NOTE]
> Wymaga to dodatkowych czynności, aby wylogować się jako codzienne konto użytkownika i zalogować się przy użyciu dedykowanego konta administratora. Jednak tę czynności należy wykonać tylko od czasu do czasu, w przypadku operacji administratora. Warto pamiętać, że odzyskanie subskrypcji Microsoft 365 w przypadku naruszenia zabezpieczeń konta administratora wymaga znacznie więcej kroków.

Musisz również utworzyć konta dostępu dla [służb ratunkowych,](/azure/active-directory/roles/security-emergency-access) aby zapobiec przypadkowemu zablokowaniu usługi Azure AD.

Możesz dodatkowo chronić swoje konta z uprawnieniami Privileged Identity Management (PIM, Azure AD Privileged Identity Management) na potrzeby przypisywania ról administratorów na żądanie. 
 
## <a name="2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-privileged-accounts"></a>2. Konfigurowanie uwierzytelniania wieloskładnikowego dla dedykowanych Microsoft 365 kont z uprawnieniami

Uwierzytelnianie wieloskładnikowe wymaga dodatkowych informacji oprócz nazwy konta i hasła. Microsoft 365 obsługuje następujące dodatkowe metody weryfikacji:
  
- Aplikacja Microsoft Authenticator aplikacji
- Rozmowa telefoniczna
- Losowo wygenerowany kod weryfikacyjny wysłany w wiadomości SMS
- Karta inteligentna (wirtualna lub fizyczna) (wymaga uwierzytelniania feder służącego do uwierzytelniania)
- Urządzenie biometryczne
- Token Oauth
- 
    
>[!Note]
>W organizacjach, które muszą spełniać standardy National Institute of Standards and Technology (NIST), dostęp do dodatkowych metod weryfikacji na podstawie wiadomości sms lub połączeń telefonicznych jest ograniczony. Kliknij [tutaj,](https://pages.nist.gov/800-63-FAQ/#q-b01) aby uzyskać szczegółowe informacje.
>

Jeśli korzystasz z kont użytkowników przechowywanych tylko w chmurze (model tożsamości tylko w chmurze), skonfiguruj uwierzytelniania [MFA](/office365/admin/security-and-compliance/set-up-multi-factor-authentication) w celu skonfigurowania uwierzytelniania wieloskładnikowego przy użyciu połączenia telefonicznego lub wiadomości tekstowej z kodem weryfikacyjnym wysyłanym na smartfon dla każdego dedykowanego konta z uprawnieniami.
    
W przypadku większych organizacji korzystających z modelu Microsoft 365 hybrydowego masz więcej opcji weryfikacji. Jeśli masz już infrastrukturę zabezpieczeń skonfigurowaną do silniejszej metody uwierzytelniania pomocniczego, skonfiguruj uwierzytelnianie [MFA](../admin/security-and-compliance/set-up-multi-factor-authentication.md) i skonfiguruj dla każdego dedykowanego konta z odpowiednimi uprawnieniami odpowiednią metodę weryfikacji.
  
Jeśli infrastruktura zabezpieczeń odpowiedniej silniejszej metody weryfikacji na potrzeby uwierzytelniania wieloskładnikowego programu Microsoft 365 nie została jeszcze skonfigurowana i działa, zdecydowanie zalecamy skonfigurowanie dedykowanych kont z uprawnieniami do uwierzytelniania wieloskładnikowego przy użyciu aplikacji Microsoft Authenticator, połączenia telefonicznego lub wiadomości tekstowej z kodem weryfikacyjnym wysyłanej na smartfon jako tymczasowego zabezpieczenia na dedykowanych kontach. Nie pozostawiaj dedykowanych kont z uprawnieniami bez dodatkowej ochrony zapewnionej przez uwierzytelniania wieloskładnikowego.
  
Aby uzyskać więcej informacji, zobacz [Uwierzytelniania wieloskładnikowego dla Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md).
  
## <a name="3-protect-administrator-accounts-with-zero-trust-identity-and-device-access-recommendations"></a>3. Ochrona kont administratora za pomocą zaleceń dotyczących tożsamości i dostępu do urządzeń przy użyciu zerowego zaufania

Aby zapewnić bezpieczeństwo i produktywność pracowników, firma Microsoft udostępnia zestaw zaleceń dotyczących tożsamości [i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md). W celu zachowania tożsamości używaj zaleceń i ustawień poszczególnych artykułów:

- [Wymagania wstępne](../security/office-365-security/identity-access-prerequisites.md)
- [Typowe zasady dostępu do urządzeń i tożsamości](../security/office-365-security/identity-access-policies.md)

## <a name="additional-protections-for-enterprise-organizations"></a>Dodatkowa ochrona dla przedsiębiorstw

Za pomocą tych dodatkowych metod upewnij się, że Twoje konto privileged i konfiguracja, która jest z nim konfigurowana, są jak najbezpieczniej.
  
### <a name="privileged-access-workstation"></a>Stacja robocza z dostępem z uprawnieniami

Aby zapewnić, że wykonywanie zadań o wysokim poziomie uprawnień jest jak najbezpieczniej, użyj stacji roboczej programu Access z uprawnieniami (PAW). Komputer dedykowany jest używany tylko do poufnych zadań konfiguracyjnych, takich jak konfiguracja Microsoft 365 wymagające konta uprzywilejowanych. Ten komputer nie jest używany codziennie do przeglądania Internetu ani do poczty e-mail, dlatego jest lepiej chroniony przed atakami i zagrożeniami internetowymi.
  
Aby uzyskać instrukcje dotyczące sposobu skonfigurowania zestawu pauzy, zobacz [https://aka.ms/cyberpaw](/security/compass/privileged-access-devices).

Aby włączyć usługę Azure PIM dla kont administratora i dzierżawcy usługi Azure AD, zobacz kroki [konfigurowania usługi zarządzania pim](/azure/active-directory/active-directory-privileged-identity-management-configure).

Aby opracowywać kompleksowy plan dotyczący bezpiecznego dostępu uprzywilejowanych przed cyberatakami, zobacz Zabezpieczanie dostępu z uprawnieniami dla wdrożeń hybrydowych i [chmurowych w usłudze Azure AD](/azure/active-directory/admin-roles-best-practices).

### <a name="azure-ad-privileged-identity-management"></a>Usługa Azure AD Privileged Identity Management

Zamiast trwale przypisywać swoje konta z uprawnieniami do roli administratora, możesz włączyć funkcję zarządzania usługą Azure AD PIM na żądanie, przypisanie roli administratora tylko na czas, gdy będzie to konieczne.
  
Konta administratorów są od trwałych administratorów do uprawnionych administratorów. Rola administratora jest nieaktywna, dopóki ktoś jej nie potrzebuje. Następnie należy ukończyć proces aktywacji w celu dodania roli administratora do konta uprawnień przez ustalony czas. Gdy upłynie termin, program PIM usuwa rolę administratora z konta uprawnień.
  
Korzystanie z funkcji pim i ten proces znacznie skraca czas, przez który Twoje konta uprzywilejowany są narażone na ataki i używanie ich przez złośliwych użytkowników.

Program PIM jest dostępny w p Azure Active Directory — wersja Premium P2, który jest dołączony do Microsoft 365 E5. Możesz również kupić indywidualne licencje Azure Active Directory — wersja Premium P2 dla kont administratora.
  
Więcej informacji można znaleźć w następujących artykułach:

- [Usługa Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).
- [Zabezpieczanie dostępu z uprawnieniami dla wdrożeń hybrydowych i chmurowych w usłudze Azure AD](/azure/active-directory/roles/security-planning)
  

### <a name="privileged-access-management"></a>Zarządzanie dostępem z uprawnieniami

Zarządzanie dostępem z uprawnieniami jest włączane przez konfigurowanie zasad określających dostęp na czas dla działań opartych na zadaniach w dzierżawie. Pomaga chronić organizację przed naruszeniem zabezpieczeń, które mogą korzystać z istniejących uprzywilejowanych kont administratora z dostępem na pozycji do poufnych danych lub dostępem do krytycznych ustawień konfiguracji. Możesz na przykład skonfigurować zasady zarządzania dostępem z uprawnieniami, które wymagają jawnego zatwierdzenia dostępu do ustawień skrzynki pocztowej organizacji i zmiany ich w dzierżawie.

W tym kroku włączysz zarządzanie dostępem uprzywilejowanym w dzierżawie i skonfigurujesz zasady dostępu uprzywilejowanych, które zapewniają dodatkowe zabezpieczenia dostępu opartego na zadaniach do danych i ustawień konfiguracji dla organizacji. Istnieją trzy podstawowe kroki rozpoczynania pracy z dostępem z uprawnieniami w organizacji:

- Tworzenie grupy osoby zatwierdzającej
- Włączanie dostępu z uprawnieniami
- Tworzenie zasad zatwierdzania

Zarządzanie dostępem uprzywilejowanym umożliwia organizacji działanie przy użyciu uprawnień o zerowej pozycji i zapewnianie warstwy ochrony przed luki w zabezpieczeniach wynikających z takiego dostępu administracyjnego na takim miejscu. Dostęp z uprawnieniami wymaga zatwierdzenia w celu wykonania dowolnego zadania, które ma zdefiniowane zasady zatwierdzania. Użytkownicy potrzebujący wykonywania zadań zawartych w zasadach zatwierdzania muszą zażądać zatwierdzenia dostępu i uzyskać do niego dostęp.

Aby włączyć zarządzanie dostępem z uprawnieniami, zobacz [Konfigurowanie zarządzania dostępem z uprawnieniami](/office365/securitycompliance/privileged-access-management-configuration).

Aby uzyskać więcej informacji, zobacz [Zarządzanie dostępem z uprawnieniami](/office365/securitycompliance/privileged-access-management-overview).

### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>Oprogramowanie do zarządzania informacjami o zabezpieczeniach i zdarzeniami na Microsoft 365 zdarzeń

Oprogramowanie SIEM uruchamiane na serwerze wykonuje w czasie rzeczywistym analizę alertów zabezpieczeń i zdarzeń utworzonych przez aplikacje i sprzęt sieciowy. Aby umożliwić serwerowi SIEM dołączanie alertów i zdarzeń zabezpieczeń Microsoft 365 do funkcji analizy i raportowania, zintegruj usługę Azure AD z usługą OKR. Zobacz [Wprowadzenie do Azure Log Integration](/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Następny krok

[![Ochrona kont Microsoft 365 użytkowników](../media/deploy-identity-solution-overview/microsoft-365-secure-sign-in.png)](microsoft-365-secure-sign-in.md)

Przejdź do [kroku 3,](microsoft-365-secure-sign-in.md) aby zabezpieczyć konta użytkowników.
