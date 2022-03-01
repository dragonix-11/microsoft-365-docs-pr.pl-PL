---
title: Wymagania wstępne dostępu do tożsamości i urządzeń dla uwierzytelniania przechodzą w Microsoft 365 testowego
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Utwórz środowisko Microsoft 365, aby przetestować tożsamość i dostęp do urządzenia zgodnie z wymaganiami wstępnymi uwierzytelniania pass-through.
ms.openlocfilehash: 662cf1aa45c2d297600baf63bd3970f31d437f95
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015953"
---
# <a name="identity-and-device-access-prerequisites-for-pass-through-authentication-in-your-microsoft-365-test-environment"></a>Wymagania wstępne dostępu do tożsamości i urządzeń dla uwierzytelniania przechodzą w Microsoft 365 testowego

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

[Konfiguracje tożsamości](../security/office-365-security/microsoft-365-policies-configurations.md) i dostępu do urządzeń są zestawem konfiguracji i zasad dostępu warunkowego w celu ochrony dostępu do wszystkich usług w usłudze Microsoft 365 dla przedsiębiorstw, które są zintegrowane z usługą Azure Active Directory (Azure AD).

W tym artykule opisano sposób konfigurowania środowiska Microsoft 365 testowego, które spełnia wymagania konfiguracji wymagań wstępnych uwierzytelniania [pass-through](../security/office-365-security/identity-access-prerequisites.md#prerequisites) na potrzeby dostępu do urządzenia i tożsamości.

Aby skonfigurować to środowisko testowe, należy skonfigurować dziesięć faz:

1. Stwórz symulowane przedsiębiorstwo przy użyciu uwierzytelniania Microsoft 365 testowego
2. Konfigurowanie bezproblemowego logowania pojedynczego w usłudze Azure AD
3. Konfigurowanie nazwanych lokalizacji
4. Konfigurowanie zapisu hasła
5. Konfigurowanie samodzielnego resetowania hasła
6. Konfigurowanie uwierzytelniania wieloskładnikowego
7. Włączanie automatycznej rejestracji urządzeń dla komputerów Windows przyłączony do domeny
8. Konfigurowanie ochrony hasłem usługi Azure AD 
9. Włączanie usługi Azure AD Identity Protection
10. Włączanie nowoczesnego uwierzytelniania dla usług Exchange Online i Skype dla firm Online

## <a name="phase-1-build-out-your-simulated-enterprise-with-pass-through-authentication-microsoft-365-test-environment"></a>Etap 1. Tworzenie symulowanego przedsiębiorstwa przy użyciu uwierzytelniania Microsoft 365 testowego

Postępuj zgodnie z instrukcjami [podanymi w tece Uwierzytelnianie przekaż](pass-through-auth-m365-ent-test-environment.md).

Oto wynikowa konfiguracja.

![Symulowane przedsiębiorstwo ze środowiskiem testowym uwierzytelniania przekazać.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>Etap 2. Konfigurowanie bezproblemowego logowania pojedynczego w usłudze Azure AD

Postępuj zgodnie z instrukcjami z fazy 2 przewodnika laboratorium testowego bezproblemowego logowania się [pojedynczego w usłudze Azure AD](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## <a name="phase-3-configure-named-locations"></a>Etap 3. Konfigurowanie nazwanych lokalizacji

Najpierw określ publiczne adresy IP lub zakresy adresów używane przez Twoją organizację.

Następnie wykonaj instrukcje z [tematu Konfigurowanie nazwanych lokalizacji w programie Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations), aby dodać adresy lub zakresy adresów jako nazwane lokalizacje. 

## <a name="phase-4-configure-password-writeback"></a>Etap 4. Konfigurowanie zapisu hasła

Postępuj zgodnie z instrukcjami [z fazy 2 przewodnika laboratorium testowego zapisu hasła](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## <a name="phase-5-configure-self-service-password-reset"></a>Etap 5. Konfigurowanie samodzielnego resetowania hasła

Postępuj zgodnie z instrukcjami [z fazy 3 przewodnika laboratorium testowego resetowania hasła](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Po włączeniu resetowania hasła dla kont w konkretnej grupie usługi Azure AD dodaj następujące konta do **grupy Resetowanie** hasła:

- Użytkownik 2
- Użytkownik 3
- Użytkownik 4
- Użytkownik 5

Przetestuj resetowanie hasła tylko dla konta użytkownika 2.

## <a name="phase-6-configure-multi-factor-authentication"></a>Etap 6. Konfigurowanie uwierzytelniania wieloskładnikowego

Wykonaj instrukcje [z fazy 2 przewodnika laboratorium testowego dotyczącego](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) uwierzytelniania wieloskładnikowego dla następujących kont użytkowników:

- Użytkownik 2
- Użytkownik 3
- Użytkownik 4
- Użytkownik 5

Przetestuj uwierzytelnianie wieloskładnikowe tylko dla konta użytkownika 2.

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Etap 7. Włączanie automatycznej rejestracji urządzeń dla komputerów Windows przyłączony do domeny 

Wykonaj [poniższe instrukcje](/azure/active-directory/devices/hybrid-azuread-join-plan), aby włączyć automatyczną rejestrację urządzeń przyłącznych do domeny Windows komputerach.

## <a name="phase-8-configure-azure-ad-password-protection"></a>Etap 8. Konfigurowanie ochrony hasłem usługi Azure AD 

Wykonaj [poniższe instrukcje,](/azure/active-directory/authentication/concept-password-ban-bad) aby zablokować znane słabe hasła i ich warianty.

## <a name="phase-9-enable-azure-ad-identity-protection"></a>Etap 9. Włączanie usługi Azure AD Identity Protection

Postępuj zgodnie z instrukcjami [z fazy 2 przewodnika laboratorium testowego usługi Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Etap 10. Włączanie nowoczesnego uwierzytelniania dla usług Exchange Online i Skype dla firm Online

Aby Exchange Online, wykonaj [poniższe instrukcje](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later). 

Dla Skype dla firm Online:

1. Połączenie do [usługi Skype dla firm Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. Uruchom to polecenie.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. Sprawdź, czy zmiana powiodła się za pomocą tego polecenia.

  ```powershell
  Get-CsOAuthConfiguration
  ```

Wynikiem jest środowisko testowe, które spełnia wymagania konfiguracji wymagań wstępnych uwierzytelniania [pass-through](../security/office-365-security/identity-access-prerequisites.md#prerequisites) dla tożsamości i dostępu do urządzenia. 

## <a name="next-step"></a>Następny krok

Użyj [wspólnych zasad dostępu do tożsamości i](../security/office-365-security/identity-access-policies.md) urządzeń, aby skonfigurować zasady na podstawie wymagań wstępnych oraz chronić tożsamości i urządzenia.

## <a name="see-also"></a>Zobacz też

[Dodatkowe przewodniki laboratorium testowego dotyczące tożsamości](m365-enterprise-test-lab-guides.md#identity)

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)
