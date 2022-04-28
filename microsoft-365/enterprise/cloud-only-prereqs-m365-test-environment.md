---
title: Wymagania wstępne dotyczące tożsamości i dostępu do urządzeń tylko w chmurze w środowisku testowym Microsoft 365
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
description: Utwórz środowisko Microsoft 365, aby przetestować dostęp do tożsamości i urządzeń z wymaganiami wstępnymi dotyczącymi uwierzytelniania tylko w chmurze.
ms.openlocfilehash: 88138600e516412b74c38234647147197742f2de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097519"
---
# <a name="identity-and-device-access-prerequisites-for-cloud-only-in-your-microsoft-365-test-environment"></a>Wymagania wstępne dotyczące tożsamości i dostępu do urządzeń tylko w chmurze w środowisku testowym Microsoft 365

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

[Konfiguracje tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md) to zestaw zalecanych konfiguracji i zasad dostępu warunkowego w celu ochrony dostępu do wszystkich usług zintegrowanych z usługą Azure Active Directory (Azure AD).

W tym artykule opisano sposób konfigurowania środowiska testowego Microsoft 365, które spełnia wymagania [konfiguracji tylko wymagań wstępnych](../security/office-365-security/identity-access-prerequisites.md#prerequisites) dotyczących tożsamości i dostępu do urządzeń.

Istnieje osiem faz konfigurowania tego środowiska testowego:

1. Tworzenie uproszczonego środowiska testowego
2. Konfigurowanie nazwanych lokalizacji
3. Konfigurowanie samoobsługowego resetowania hasła
4. Konfigurowanie uwierzytelniania wieloskładnikowego
5. Włączanie automatycznej rejestracji urządzeń na komputerach Windows przyłączonych do domeny
6. Konfigurowanie ochrony hasłem w usłudze Azure AD 
7. Włączanie usługi Azure AD Identity Protection
8. Włączanie nowoczesnego uwierzytelniania dla Exchange Online i Skype dla firm Online

## <a name="phase-1-build-out-your-lightweight-microsoft-365-test-environment"></a>Faza 1. Tworzenie uproszczonego środowiska testowego Microsoft 365

Postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
Oto wynikowej konfiguracji.

![Uproszczone środowisko testowe platformy Microsoft 3656 Enterprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)
 
## <a name="phase-2-configure-named-locations"></a>Faza 2. Konfigurowanie nazwanych lokalizacji

Najpierw określ publiczne adresy IP lub zakresy adresów używane przez organizację.

Następnie postępuj zgodnie z instrukcjami w temacie [Konfigurowanie nazwanych lokalizacji w Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations), aby dodać adresy lub zakresy adresów jako nazwane lokalizacje. 

## <a name="phase-3-configure-self-service-password-reset"></a>Faza 3. Konfigurowanie samoobsługowego resetowania hasła

Postępuj zgodnie z instrukcjami w [fazie 3 przewodnika laboratorium testowego resetowania haseł](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Podczas włączania resetowania haseł dla kont w określonej grupie usługi Azure AD dodaj te konta do grupy **Resetowanie hasła** :

- Użytkownik 2
- Użytkownik 3
- Użytkownik 4
- Użytkownik 5

Przetestuj resetowanie hasła tylko dla konta użytkownika 2.

## <a name="phase-4-configure-multi-factor-authentication"></a>Faza 4. Konfigurowanie uwierzytelniania wieloskładnikowego

Postępuj zgodnie z instrukcjami w [fazie 2 przewodnika laboratorium testowego uwierzytelniania wieloskładnikowego](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) dla następujących kont użytkowników:

- Użytkownik 2
- Użytkownik 3
- Użytkownik 4
- Użytkownik 5

Przetestuj uwierzytelnianie wieloskładnikowe tylko dla konta użytkownika 2.

## <a name="phase-5-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Faza 5. Włączanie automatycznej rejestracji urządzeń przyłączonych do domeny Windows komputerów 

Postępuj zgodnie z [tymi instrukcjami](/azure/active-directory/devices/hybrid-azuread-join-plan), aby włączyć automatyczną rejestrację urządzeń przyłączonych do domeny Windows komputerach.

## <a name="phase-6-configure-azure-ad-password-protection"></a>Faza 6. Konfigurowanie ochrony hasłem w usłudze Azure AD 

Postępuj zgodnie [z tymi instrukcjami,](/azure/active-directory/authentication/concept-password-ban-bad) aby zablokować znane słabe hasła i ich warianty.

## <a name="phase-7-enable-azure-ad-identity-protection"></a>Faza 7. Włączanie usługi Azure AD Identity Protection

Postępuj zgodnie z instrukcjami w [sekcji Faza 2 przewodnika laboratorium testowego usługi Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-8-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Faza 8. Włączanie nowoczesnego uwierzytelniania dla Exchange Online i Skype dla firm Online

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

Rezultatem jest środowisko testowe, które spełnia wymagania [konfiguracji wymagań wstępnych tylko w chmurze](../security/office-365-security/identity-access-prerequisites.md#prerequisites) dotyczącej tożsamości i dostępu do urządzeń. 

## <a name="next-step"></a>Następny krok

Użyj [typowych zasad dostępu do tożsamości i urządzeń](../security/office-365-security/identity-access-policies.md) , aby skonfigurować zasady, które bazują na wymaganiach wstępnych i chronią tożsamości i urządzenia.

## <a name="see-also"></a>Zobacz też

[Dodatkowe przewodniki laboratorium testów tożsamości](m365-enterprise-test-lab-guides.md#identity)

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)
