---
title: Wymagania wstępne dotyczące tożsamości i dostępu urządzeń do synchronizacji skrótów haseł w środowisku testowym Microsoft 365
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Utwórz środowisko Microsoft 365, aby przetestować dostęp do tożsamości i urządzeń przy użyciu wymagań wstępnych dotyczących uwierzytelniania synchronizacji skrótów haseł.
ms.openlocfilehash: af357a477ea0aa66881b546d6cefbd517e453e80
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100374"
---
# <a name="identity-and-device-access-prerequisites-for-password-hash-synchronization-in-your-microsoft-365-test-environment"></a>Wymagania wstępne dotyczące tożsamości i dostępu urządzeń do synchronizacji skrótów haseł w środowisku testowym Microsoft 365

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

[Konfiguracje tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md) to zestaw konfiguracji i zasad dostępu warunkowego w celu ochrony dostępu do wszystkich usług w Microsoft 365 dla przedsiębiorstw zintegrowanych z usługą Azure Active Directory (Azure AD).

W tym artykule opisano sposób konfigurowania środowiska testowego Microsoft 365 spełniającego wymagania [hybrydowe z wymaganiami wstępnymi uwierzytelniania synchronizacji skrótów haseł](../security/office-365-security/identity-access-prerequisites.md#prerequisites) dla tożsamości i dostępu do urządzeń.

Istnieje dziesięć faz konfigurowania tego środowiska testowego:

1. Tworzenie symulowanego przedsiębiorstwa ze środowiskiem testowym synchronizacji skrótów haseł
2. Konfigurowanie bezproblemowego logowania jednokrotnego w usłudze Azure AD
3. Konfigurowanie nazwanych lokalizacji
4. Konfigurowanie zapisywania zwrotnego haseł
5. Konfigurowanie samoobsługowego resetowania hasła dla wszystkich kont użytkowników
6. Konfigurowanie uwierzytelniania wieloskładnikowego dla wszystkich kont użytkowników
7. Włączanie automatycznej rejestracji urządzeń na komputerach Windows przyłączonych do domeny
8. Konfigurowanie ochrony hasłem w usłudze Azure AD 
9. Włączanie usługi Azure AD Identity Protection
10. Włączanie nowoczesnego uwierzytelniania dla Exchange Online i Skype dla firm Online

## <a name="phase-1-build-out-your-simulated-enterprise-with-password-hash-sync-microsoft-365-test-environment"></a>Faza 1. Tworzenie symulowanego przedsiębiorstwa przy użyciu synchronizacji skrótów haseł Microsoft 365 środowisku testowym

Postępuj zgodnie z instrukcjami w [przewodniku laboratorium testowego synchronizacji skrótów haseł](password-hash-sync-m365-ent-test-environment.md) .
Oto wynikowej konfiguracji.

![Symulowane przedsiębiorstwo ze środowiskiem testowym synchronizacji skrótów haseł.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>Faza 2. Konfigurowanie bezproblemowego logowania jednokrotnego w usłudze Azure AD

Postępuj zgodnie z instrukcjami w [fazie 2 przewodnika laboratorium testowego bezproblemowego logowania jednokrotnego usługi Azure AD](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## <a name="phase-3-configure-named-locations"></a>Faza 3. Konfigurowanie nazwanych lokalizacji

Najpierw określ publiczne adresy IP lub zakresy adresów używane przez organizację.

Następnie postępuj zgodnie z instrukcjami w temacie [Konfigurowanie nazwanych lokalizacji w Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations), aby dodać adresy lub zakresy adresów jako nazwane lokalizacje. 

## <a name="phase-4-configure-password-writeback"></a>Faza 4. Konfigurowanie zapisywania zwrotnego haseł

Postępuj zgodnie z instrukcjami w [sekcji Faza 2 przewodnika laboratorium testowego zapisywania zwrotnego haseł](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## <a name="phase-5-configure-self-service-password-reset"></a>Faza 5. Konfigurowanie samoobsługowego resetowania hasła

Postępuj zgodnie z instrukcjami w [fazie 3 przewodnika laboratorium testowego resetowania haseł](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Podczas włączania resetowania haseł dla kont w określonej grupie usługi Azure AD dodaj te konta do grupy **Resetowanie hasła** :

- Użytkownik 2
- Użytkownik 3
- Użytkownik 4
- Użytkownik 5

Przetestuj resetowanie hasła tylko dla konta użytkownika 2.

## <a name="phase-6-configure-multi-factor-authentication"></a>Faza 6. Konfigurowanie uwierzytelniania wieloskładnikowego

Postępuj zgodnie z instrukcjami w [fazie 2 przewodnika laboratorium testowego uwierzytelniania wieloskładnikowego](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) dla następujących kont użytkowników:

- Użytkownik 2
- Użytkownik 3
- Użytkownik 4
- Użytkownik 5

Przetestuj uwierzytelnianie wieloskładnikowe tylko dla konta użytkownika 2.

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Faza 7. Włączanie automatycznej rejestracji urządzeń przyłączonych do domeny Windows komputerów 

Postępuj zgodnie z [tymi instrukcjami](/azure/active-directory/devices/hybrid-azuread-join-plan), aby włączyć automatyczną rejestrację urządzeń przyłączonych do domeny Windows komputerach.

## <a name="phase-8-configure-azure-ad-password-protection"></a>Faza 8. Konfigurowanie ochrony hasłem w usłudze Azure AD 

Postępuj zgodnie [z tymi instrukcjami,](/azure/active-directory/authentication/concept-password-ban-bad) aby zablokować znane słabe hasła i ich warianty.

## <a name="phase-9-enable-azure-ad-identity-protection"></a>Faza 9. Włączanie usługi Azure AD Identity Protection

Postępuj zgodnie z instrukcjami w [sekcji Faza 2 przewodnika laboratorium testowego usługi Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Faza 10. Włączanie nowoczesnego uwierzytelniania dla Exchange Online i Skype dla firm Online

Aby uzyskać Exchange Online, postępuj zgodnie z [tymi instrukcjami](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later). 

W przypadku usługi Skype dla firm Online:

1. Połączenie do [Skype dla firm Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. Uruchom to polecenie.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. Sprawdź, czy zmiana zakończyła się pomyślnie za pomocą tego polecenia.

  ```powershell
  Get-CsOAuthConfiguration
  ```

Rezultatem jest środowisko testowe, które spełnia wymagania [usługi Active Directory z konfiguracją wymagań wstępnych synchronizacji skrótów haseł](../security/office-365-security/identity-access-prerequisites.md#prerequisites) dla tożsamości i dostępu do urządzenia. 

## <a name="next-step"></a>Następny krok

Użyj [typowych zasad dostępu do tożsamości i urządzeń](../security/office-365-security/identity-access-policies.md) , aby skonfigurować zasady, które bazują na wymaganiach wstępnych i chronią tożsamości i urządzenia.

## <a name="see-also"></a>Zobacz też

[Dodatkowe przewodniki laboratorium testów tożsamości](m365-enterprise-test-lab-guides.md#identity)

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)
