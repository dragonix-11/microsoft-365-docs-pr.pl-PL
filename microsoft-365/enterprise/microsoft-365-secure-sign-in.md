---
title: Krok 3. Ochrona Microsoft 365 użytkowników
f1.keywords:
- NOCSH
author: kelleyvice-msft
ms.author: kvice
manager: laurawi
ms.date: 09/30/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365initiative-coredeploy
ms.custom: ''
description: Wymagaj bezpiecznego logowania użytkowników przy użyciu uwierzytelniania wieloskładnikowego (MFA) i innych funkcji.
ms.openlocfilehash: c144b374ecc49128e11635c034f3b4b76020eafd
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015967"
---
# <a name="step-3-protect-your-microsoft-365-user-accounts"></a>Krok 3. Ochrona Microsoft 365 użytkowników

Aby zwiększyć bezpieczeństwo logowania użytkowników:

- Używanie Windows Hello dla firm
- Korzystanie Azure Active Directory hasła (Azure AD)
- Korzystanie z uwierzytelniania wieloskładnikowego
- Wdrażanie konfiguracji tożsamości i dostępu do urządzeń
- Ochrona przed naruszeniami zabezpieczeń poświadczeń za pomocą usługi Azure AD Identity Protection

## <a name="windows-hello-for-business"></a>Windows Hello dla firm

Windows Hello dla firm Windows 10 Enterprise hasło na silne uwierzytelnianie dwuskładnikowe podczas logowania się na Windows urządzeniu. Dwa czynniki to nowy typ poświadczeń użytkownika powiązany z urządzeniem i biometryczny lub numer PIN.

Aby uzyskać więcej informacji, zobacz [omówienie Windows Hello dla firm](/windows/security/identity-protection/hello-for-business/hello-overview).


## <a name="azure-ad-password-protection"></a>Ochrona hasłem w usłudze Azure AD

Usługa Azure AD Password Protection wykrywa i blokuje znane słabe hasła i ich warianty, a także może blokować dodatkowe słabe terminy specyficzne dla Twojej organizacji. Domyślne globalne listy zablokowanych haseł są automatycznie stosowane do wszystkich użytkowników w dzierżawie usługi Azure AD. Możesz zdefiniować dodatkowe wpisy na niestandardowej liście zablokowanych haseł. Gdy użytkownicy zmieniają lub resetują swoje hasła, te listy zablokowanych haseł są sprawdzane, aby wymusić stosowanie silnych haseł.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ochrony hasłem usługi Azure AD](/azure/active-directory/authentication/concept-password-ban-bad).

## <a name="mfa"></a>Uwierzytelniania wieloskładnikowego

Uwierzytelniania wieloskładnikowego wymaga, aby logowanie użytkowników podlegało dodatkowej weryfikacji poza hasłem do konta użytkownika. Nawet jeśli złośliwy użytkownik ustali hasło do konta użytkownika, musi też przed udzieleniem dostępu odpowiedzieć na dodatkową weryfikację, taką jak wiadomość SMS wysłana na smartfon.

![Poprawne hasło i dodatkowa weryfikacja skutkują pomyślnym zalogowaniem się.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

Pierwszym krokiem w używaniu uwierzytelniania MFA jest wymaganie go dla [wszystkich kont administratora](protect-your-global-administrator-accounts.md), nazywanych również kontami z uprawnieniami. Poza tym pierwszym krokiem firma Microsoft zaleca uwierzytelniania MFA dla wszystkich użytkowników.

Uwierzytelniania wieloskładnikowego można wymagać na trzy sposoby w zależności od Microsoft 365 mfa.

| Planowanie | Zalecenie |
|---------|---------|
|Wszystkie Microsoft 365 (bez Azure AD — wersja Premium P1 licencji P2)     |[Włącz domyślne ustawienia zabezpieczeń w usłudze Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Wartości domyślne zabezpieczeń w usłudze Azure AD obejmują uwierzytelniania wieloskładnikowe dla użytkowników i administratorów.   |
|Microsoft 365 E3 (obejmuje Azure AD — wersja Premium P1 licencji)     | Użyj typowych [zasad dostępu warunkowego,](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) aby skonfigurować następujące zasady: <br>- [Wymaganie uwierzytelniania wieloskładnikowego dla administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Wymaganie uwierzytelniania WIELOSKŁADNIKOWEGO dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Blokowanie starszego uwierzytelniania](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (obejmuje Azure AD — wersja Premium P2 licencji)     | Korzystając z usługi Azure AD Identity Protection, zacznij implementować zalecany przez firmę Microsoft zestaw dostępu warunkowego i powiązanych zasad, tworząc te dwie zasady:<br> - [Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest średnie lub wysokie](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk) <br>- [Zmiana hasła przez użytkowników o wysokim poziomie ryzyka](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user)       |
| | |

### <a name="security-defaults"></a>Domyślne ustawienia zabezpieczeń

Wartości domyślne zabezpieczeń to nowa funkcja dla subskrypcji Microsoft 365 i Office 365 wersji próbnej utworzonych po 21 października 2019 r. Te subskrypcje mają włączone ustawienia domyślne zabezpieczeń, co wymaga, aby wszyscy użytkownicy korzystali ***z uwierzytelniania WIELOSKŁADNIKOWEGO Microsoft Authenticator aplikacji***.
 
Użytkownicy mają 14 dni na zarejestrowanie się w celu uwierzytelniania wieloskładnikowego za pomocą aplikacji Microsoft Authenticator na swoich telefonach inteligentnych, która rozpoczyna się od pierwszego logowania po włączeniu ustawień domyślnych zabezpieczeń. Po upływie 14 dni użytkownik nie będzie mógł się zalogować do czasu ukończenia rejestracji uwierzytelniania MFA.

Domyślne ustawienia zabezpieczeń zapewniają, że wszystkie organizacje mają podstawowy poziom zabezpieczeń dla domyślnie włączonego logowania użytkownika. Ustawienia domyślne zabezpieczeń można wyłączyć na rzecz uwierzytelniania wieloskładnikowego za pomocą zasad dostępu warunkowego lub dla poszczególnych kont.

Aby uzyskać więcej informacji, zobacz [omówienie domyślnych ustawień zabezpieczeń](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Zasady dostępu warunkowego

Zasady dostępu warunkowego to zestaw reguł określających warunki, na podstawie których sprawdzane są logowania i do których jest udzielany dostęp. Można na przykład utworzyć zasady dostępu warunkowego o treści:

- Jeśli nazwa konta użytkownika jest członkiem grupy użytkowników z przypisanymi rolami administratora Exchange, użytkownika, hasła, zabezpieczeń, administratora systemu **SharePoint, administratora** **Exchange, administratora** SharePoint lub administratora globalnego, przed zezwoleniem na dostęp należy wymagać  uwierzytelniania wieloskładnikowego.

Te zasady pozwalają na wymaganie uwierzytelniania MFA opartego na członkostwie w grupach zamiast próby skonfigurowania poszczególnych kont użytkowników do uwierzytelniania MFA, gdy są one przypisane do tych ról administratora lub nieprzypisane do nich.

Możesz również użyć zasad dostępu warunkowego, aby uzyskać bardziej zaawansowane możliwości, takie jak wymaganie, aby logowanie było wykonywane ze zgodnego urządzenia, takiego jak komputer przenośny z systemem Windows 10.

Dostęp warunkowy wymaga Azure AD — wersja Premium P1 licencji, które są zawarte w Microsoft 365 E3 i E5.

Aby uzyskać więcej informacji, zobacz [Omówienie dostępu warunkowego](/azure/active-directory/conditional-access/overview).

### <a name="using-these-methods-together"></a>Wspólne korzystanie z tych metod

Należy pamiętać o następujących kwestiach:

- Nie można włączyć ustawień domyślnych zabezpieczeń, jeśli włączono jakiekolwiek zasady dostępu warunkowego.
- Nie można włączyć żadnych zasad dostępu warunkowego, jeśli włączono ustawienia domyślne zabezpieczeń.

Jeśli są włączone domyślne ustawienia zabezpieczeń, wszyscy nowi użytkownicy są monitni o rejestrację uwierzytelniania MFA i korzystanie z Microsoft Authenticator usługi. 

W poniższej tabeli przedstawiono wyniki włączania uwierzytelniania MFA z ustawieniami domyślnymi zabezpieczeń i zasadami dostępu warunkowego.

| Metoda | Włączone | Wyłączone | Dodatkowa metoda uwierzytelniania |
|:-------|:-----|:-------|:-------|
| **Domyślne ustawienia zabezpieczeń**  | Nie można używać zasad dostępu warunkowego | Można używać zasad dostępu warunkowego | Microsoft Authenticator aplikacji |
| **Zasady dostępu warunkowego** | Jeśli są włączone, nie można włączyć domyślnych ustawień zabezpieczeń | Jeśli wszystkie są wyłączone, możesz włączyć ustawienia domyślne zabezpieczeń  | Użytkownik określa podczas rejestracji uwierzytelniania MFA  |
||||

## <a name="zero-trust-identity-and-device-access-configurations"></a>Konfiguracje zerowym zaufaniem tożsamości i dostępu do urządzeń

Ustawienia i zasady zerowego zaufania w zakresie tożsamości i dostępu do urządzeń to zalecane wstępnie wymagane funkcje i ich ustawienia w połączeniu z zasadami dostępu warunkowego, usługi Intune i usługi Azure AD Identity Protection, które określają, czy dane żądanie dostępu powinno zostać udzielone i na jakich warunkach. Określenie to jest oparte na koncie użytkownika logowania, używanego urządzenia, aplikacji używanej przez użytkownika do uzyskiwania dostępu, lokalizacji, z której jest dokonywane żądanie dostępu, oraz oceny ryzyka związanego z żądaniem. Funkcja ta pomaga zapewnić, że tylko zatwierdzeni użytkownicy i urządzenia mogą uzyskać dostęp do krytycznych zasobów.

>[!Note]
>Usługa Azure AD Identity Protection wymaga Azure AD — wersja Premium P2 licencji, które są zawarte w Microsoft 365 E5.
>

Zasady dostępu do urządzenia i tożsamości są zdefiniowane jako używane w trzech warstwach: 

- Ochrona według planu bazowego to minimalny poziom zabezpieczeń tożsamości i urządzeń, które mają dostęp do Twoich aplikacji i danych.
- Ochrona po poufnej stronie zapewnia dodatkową ochronę dla określonych danych. Tożsamości i urządzenia podlegają wyższym poziomom wymagań dotyczących zabezpieczeń i kondycji urządzenia.
- Ochrona środowisk o ściśle uregulowanych lub sklasyfikowanych danych dotyczy zazwyczaj małych ilości danych, które są wysoce klasyfikowane, zawierają tajemnice handlowe lub podlegają przepisom dotyczącym danych. Tożsamości i urządzenia podlegają znacznie wyższym poziomom wymagań dotyczących zabezpieczeń i kondycji urządzenia. 

Te warstwy i odpowiadające im konfiguracje zapewniają spójny poziom ochrony danych, tożsamości i urządzeń.

Firma Microsoft zdecydowanie zaleca skonfigurowanie i stosowanie zasad dostępu do urządzeń i tożsamości bez zaufania w Twojej organizacji, w tym określonych ustawień dla usług Microsoft Teams, Exchange Online i SharePoint. Aby uzyskać więcej informacji, zobacz [Konfiguracje dostępu do urządzeń i tożsamości bez zaufania](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

W tej sekcji dowiesz się, jak skonfigurować zasady chroniące przed złamaniem poświadczeń, gdy atakujący określi nazwę konta użytkownika i hasło w celu uzyskania dostępu do usług i danych w chmurze organizacji. Usługa Azure AD Identity Protection udostępnia wiele sposobów ochrony przed naruszeniem poświadczeń użytkownika przez atakującego.

Dzięki usłudze Azure AD Identity Protection możesz:

|Funkcja|Opis|
|:---------|:---------|
| Określanie i adresuj potencjalne luki w tożsamościach organizacji | Usługa Azure AD używa uczenia maszynowego do wykrywania anomalii i podejrzanych działań, takich jak logowania i działania po zalogowaniu się. Korzystając z tych danych, usługa Azure AD Identity Protection generuje raporty i alerty, które ułatwiają ocenę problemów i podjęcia działań.|
|Wykrywaj podejrzane działania związane z tożsamościami Twojej organizacji i odpowiadaj na nie automatycznie|Możesz skonfigurować zasady oparte na czynnikach ryzyka, które będą automatycznie odpowiadać na wykryte problemy po osiągnięciu określonego poziomu ryzyka. Te zasady, oprócz innych kontrolek dostępu warunkowego zapewnianych przez usługi Azure AD i Microsoft Intune, mogą automatycznie blokować dostęp lub podjąć działania korygujące, takie jak resetowanie hasła i wymaganie uwierzytelniania wieloskładnikowego usługi Azure AD dla kolejnych logowania. |
| Badanie podejrzanych zdarzeń i rozwiązywanie ich za pomocą działań administracyjnych | Zdarzenia związane z zagrożeniami można zbadać, korzystając z informacji dotyczących zdarzenia związanego z zabezpieczeniami. Dostępne są podstawowe przepływy pracy służące do śledzenia badań i inicjowania działań naprawczych, takich jak resetowanie hasła. |
|||

Zobacz [więcej informacji na temat usługi Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

Zapoznaj się [z krokami włączania usługi Azure AD Identity Protection](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies).

## <a name="admin-technical-resources-for-mfa-and-secure-sign-ins"></a>Zasoby techniczne dla uwierzytelniania wieloskładnikowego i bezpiecznego logowania

- [Uwierzytelniania wieloskładnikowego dla Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)
- [Wdrażanie tożsamości dla usługi Microsoft 365](deploy-identity-solution-overview.md)
- [Filmy szkoleniowe na platformie Azure Academy w usłudze Azure AD](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)
- [Konfigurowanie zasad rejestracji usługi Azure AD Multi-Factor Authentication](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)
- [Konfiguracje tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md)

## <a name="next-step"></a>Następny krok

![Wdrażanie modelu tożsamości](../media/deploy-identity-solution-overview/deploy-identity-solution-identity-infrastructure.png)

Przejdź do kroku 4, aby wdrożyć infrastrukturę tożsamości na podstawie wybranego modelu tożsamości:

- [Tożsamość tylko w chmurze](cloud-only-identities.md)
- [Tożsamość hybrydowa](prepare-for-directory-synchronization.md)
