---
title: Wymagania wstępne dotyczące implementowania zasad dostępu do tożsamości i urządzeń — Microsoft 365 dla | przedsiębiorstwa Microsoft Docs
description: W tym artykule opisano wymagania wstępne, które należy spełnić, aby używać Zero Trust zasad i konfiguracji dostępu do tożsamości oraz urządzeń.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 2c2902e7e61428d9c60423f83ed637d6d22a0570
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131245"
---
# <a name="prerequisite-work-for-implementing-zero-trust-identity-and-device-access-policies"></a>Wymagania wstępne dotyczące implementowania zasad Zero Trust tożsamości i dostępu do urządzeń

W tym artykule opisano wymagania wstępne, które administratorzy muszą spełnić, aby korzystać z zalecanych Zero Trust zasad dostępu do tożsamości i urządzeń oraz korzystać z dostępu warunkowego. Omówiono w nim również zalecane wartości domyślne dotyczące konfigurowania platform klienckich dla najlepszego środowiska logowania jednokrotnego.

## <a name="prerequisites"></a>Wymagania wstępne

Przed użyciem Zero Trust zasad dostępu do tożsamości i urządzeń, które są zalecane, organizacja musi spełnić wymagania wstępne. Wymagania są różne dla różnych modeli tożsamości i uwierzytelniania wymienionych na liście:

- Tylko w chmurze
- Uwierzytelnianie hybrydowe z uwierzytelnianiem synchronizacji skrótów haseł (PHS)
- Hybrydowe z uwierzytelnianiem przekazywanym (PTA)
- Federacyjnych

W poniższej tabeli szczegółowo opisano funkcje wymagań wstępnych i ich konfigurację, które mają zastosowanie do wszystkich modeli tożsamości, z wyjątkiem sytuacji, w których zostały zanotowane.

|Konfiguracja|Wyjątki|Licencjonowanie|
|---|:---:|---|
|[Skonfiguruj język PHS](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  Należy włączyć tę funkcję, aby wykrywać wyciekły poświadczenia i działać na nich w przypadku dostępu warunkowego opartego na ryzyku. **Uwaga:** Jest to wymagane niezależnie od tego, czy organizacja korzysta z uwierzytelniania federacyjnego.|Tylko w chmurze|Microsoft 365 E3 lub E5|
|[Włącz bezproblemowe logowanie jednokrotne](/azure/active-directory/connect/active-directory-aadconnect-sso) , aby automatycznie logować użytkowników, gdy znajdują się na urządzeniach organizacji połączonych z siecią organizacji.|Tylko w chmurze i federacyjne|Microsoft 365 E3 lub E5|
|[Skonfiguruj nazwane lokalizacje](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations). Azure AD Identity Protection zbiera i analizuje wszystkie dostępne dane sesji w celu wygenerowania oceny ryzyka. Zalecamy określenie zakresów publicznych adresów IP organizacji dla sieci w konfiguracji Azure AD nazwanych lokalizacji. Ruch pochodzący z tych zakresów otrzymuje obniżoną ocenę ryzyka, a ruch spoza środowiska organizacji otrzymuje wyższy wynik ryzyka.||Microsoft 365 E3 lub E5|
|[Zarejestruj wszystkich użytkowników na potrzeby samoobsługowego resetowania haseł (SSPR) i uwierzytelniania wieloskładnikowego (MFA).](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged) Zalecamy zarejestrowanie użytkowników w celu Azure AD uwierzytelniania wieloskładnikowego z wyprzedzeniem. Azure AD usługa Identity Protection korzysta z uwierzytelniania wieloskładnikowego Azure AD w celu przeprowadzenia dodatkowej weryfikacji zabezpieczeń. Ponadto w celu zapewnienia najlepszego środowiska logowania zalecamy użytkownikom zainstalowanie [aplikacji Microsoft Authenticator](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) i aplikacji Microsoft Portal firmy na swoich urządzeniach. Można je zainstalować ze sklepu z aplikacjami dla każdej platformy.||Microsoft 365 E3 lub E5|
|[Włącz automatyczną rejestrację urządzeń przyłączonych do domeny Windows komputerów](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). Dostęp warunkowy zapewni, że urządzenia łączące się z aplikacjami są przyłączone do domeny lub są zgodne. Aby obsługiwać tę funkcję na komputerach Windows, urządzenie musi być zarejestrowane w Azure AD.  W tym artykule omówiono sposób konfigurowania automatycznej rejestracji urządzeń.|Tylko w chmurze|Microsoft 365 E3 lub E5|
|**Przygotuj zespół pomocy technicznej**. Utwórz plan dla użytkowników, którzy nie mogą ukończyć uwierzytelniania wieloskładnikowego. Może to być dodanie ich do grupy wykluczeń zasad lub zarejestrowanie dla nich nowych informacji uwierzytelniania wieloskładnikowego. Przed wprowadzeniem jednej z tych zmian wrażliwych na zabezpieczenia należy upewnić się, że rzeczywisty użytkownik wykonuje żądanie. Wymaganie od menedżerów użytkowników pomocy w zatwierdzaniu jest skutecznym krokiem.||Microsoft 365 E3 lub E5|
|[Skonfiguruj zapisywanie zwrotne haseł w lokalnej usłudze AD](/azure/active-directory/active-directory-passwords-getting-started). Zapisywanie zwrotne haseł umożliwia Azure AD wymaganie od użytkowników zmiany haseł lokalnych po wykryciu naruszenia zabezpieczeń konta wysokiego ryzyka. Tę funkcję można włączyć przy użyciu Azure AD Połączenie na jeden z dwóch sposobów: włącz **funkcję zapisywania zwrotnego haseł** na opcjonalnym ekranie funkcji konfiguracji Azure AD Połączenie lub włącz ją za pośrednictwem Windows PowerShell.|Tylko w chmurze|Microsoft 365 E3 lub E5|
|[Skonfiguruj ochronę haseł Azure AD](/azure/active-directory/authentication/concept-password-ban-bad). Azure AD ochrona haseł wykrywa i blokuje znane słabe hasła i ich warianty, a także może blokować dodatkowe słabe terminy specyficzne dla twojej organizacji. Domyślne globalne listy zakazanych haseł są automatycznie stosowane do wszystkich użytkowników w dzierżawie Azure AD. Dodatkowe wpisy można zdefiniować na niestandardowej liście zakazanych haseł. Gdy użytkownicy zmieniają lub resetują swoje hasła, te listy zakazanych haseł są sprawdzane w celu wymuszenia użycia silnych haseł.||Microsoft 365 E3 lub E5|
|[Włącz usługę Azure Active Directory Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection). Azure AD Identity Protection umożliwia wykrywanie potencjalnych luk w zabezpieczeniach wpływających na tożsamości organizacji oraz konfigurowanie zautomatyzowanych zasad korygowania na poziomie niskiego, średniego i wysokiego ryzyka logowania oraz ryzyka dla użytkowników.||Microsoft 365 E5 lub Microsoft 365 E3 z dodatkiem E5 Security|
|**Włącz nowoczesne uwierzytelnianie** dla [Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) i [dla usługi Skype dla firm Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). Nowoczesne uwierzytelnianie jest warunkiem wstępnym korzystania z uwierzytelniania wieloskładnikowego. Nowoczesne uwierzytelnianie jest domyślnie włączone dla klientów Office 2016 i 2019, SharePoint i OneDrive dla Firm.||Microsoft 365 E3 lub E5|
|[Włącz ciągłą ocenę dostępu](microsoft-365-continuous-access-evaluation.md) dla Azure AD. Ciągła ocena dostępu proaktywnie przerywa aktywne sesje użytkowników i wymusza zmiany zasad dzierżawy niemal w czasie rzeczywistym.||Microsoft 365 E3 lub E5|

## <a name="recommended-client-configurations"></a>Zalecane konfiguracje klienta

W tej sekcji opisano domyślne konfiguracje klienta platformy, które zalecamy, aby zapewnić użytkownikom najlepsze środowisko logowania jednokrotnego, a także wymagania techniczne dotyczące dostępu warunkowego.

### <a name="windows-devices"></a>urządzenia Windows

Zalecamy Windows 11 lub Windows 10 (wersja 2004 lub nowsza), ponieważ platforma Azure została zaprojektowana tak, aby zapewnić bezproblemowe środowisko logowania jednokrotnego dla środowiska lokalnego i Azure AD. Urządzenia służbowe powinny być skonfigurowane do bezpośredniego dołączania do Azure AD lub jeśli organizacja korzysta z lokalnego przyłączania do domeny usługi AD, te urządzenia powinny być [skonfigurowane do automatycznego i dyskretnego rejestrowania w Azure AD](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

W przypadku urządzeń Windows BYOD użytkownicy mogą używać funkcji **Dodaj konto służbowe**. Należy pamiętać, że użytkownicy przeglądarki Google Chrome na urządzeniach Windows 11 lub Windows 10 muszą [zainstalować rozszerzenie](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog), aby uzyskać takie samo bezproblemowe logowanie jak Microsoft Edge użytkowników. Ponadto jeśli organizacja ma przyłączone do domeny urządzenia Windows 8 lub 8.1, możesz zainstalować program Microsoft Workplace Join dla komputerów innych niż Windows 10. [Pobierz pakiet, aby zarejestrować](https://www.microsoft.com/download/details.aspx?id=53554) urządzenia w Azure AD.

### <a name="ios-devices"></a>Urządzenia z systemem iOS

Zalecamy zainstalowanie [aplikacji Microsoft Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) na urządzeniach użytkowników przed wdrożeniem zasad dostępu warunkowego lub uwierzytelniania wieloskładnikowego. Co najmniej należy zainstalować aplikację, gdy użytkownicy zostaną poproszeni o zarejestrowanie urządzenia w Azure AD przez dodanie konta służbowego lub zainstalowanie aplikacji portalu firmy Intune w celu zarejestrowania urządzenia w zarządzaniu. Zależy to od skonfigurowanych zasad dostępu warunkowego.

### <a name="android-devices"></a>Urządzenia z systemem Android

Zalecamy użytkownikom zainstalowanie [aplikacji Intune — Portal firmy](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) i [aplikacji Microsoft Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) przed wdrożeniem zasad dostępu warunkowego lub gdy jest to wymagane podczas niektórych prób uwierzytelniania. Po zainstalowaniu aplikacji użytkownicy mogą zostać poproszeni o zarejestrowanie się w Azure AD lub zarejestrowanie urządzenia przy użyciu Intune. Zależy to od skonfigurowanych zasad dostępu warunkowego.

Zalecamy również, aby urządzenia należące do organizacji były ustandaryzowane na maszynach OEM i wersjach, które obsługują system Android for Work lub Samsung Knox, aby zezwalać na konta poczty, być zarządzane i chronione przez zasady zarządzania urządzeniami przenośnymi Intune.

### <a name="recommended-email-clients"></a>Zalecani klienci poczty e-mail

Następujący klienci poczty e-mail obsługują nowoczesne uwierzytelnianie i dostęp warunkowy.

|Platforma|Klient|Wersja/uwagi|
|---|---|---|
|**Windows**|Outlook|2019, 2016, 2013 <p> [Włączanie nowoczesnego uwierzytelniania](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [Wymagane aktualizacje](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook dla systemu iOS|[Najnowsza](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook dla systemu Android|[Najnowsza](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**macOS**|Outlook|2019 i 2016|
|**Linux**|Nieobsługiwane||

### <a name="recommended-client-platforms-when-securing-documents"></a>Zalecane platformy klienckie podczas zabezpieczania dokumentów

Po zastosowaniu zasad bezpiecznych dokumentów zaleca się następujących klientów.

|Platforma|Word/Excel/PowerPoint|OneNote|aplikacja OneDrive|aplikacja SharePoint|[Klient synchronizacji OneDrive](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 11 lub Windows 10|Obsługiwane|Obsługiwane|nd.|nd.|Obsługiwane|
|Windows 8.1|Obsługiwane|Obsługiwane|nd.|nd.|Obsługiwane|
|Android|Obsługiwane|Obsługiwane|Obsługiwane|Obsługiwane|nd.|
|iOS|Obsługiwane|Obsługiwane|Obsługiwane|Obsługiwane|nd.|
|macOS|Obsługiwane|Obsługiwane|nd.|nd.|Nieobsługiwane|
|Linux|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|

### <a name="microsoft-365-client-support"></a>obsługa klienta Microsoft 365

Aby uzyskać więcej informacji na temat obsługi klienta w Microsoft 365, zobacz następujące artykuły:

- [obsługa aplikacji klienckich Microsoft 365 — dostęp warunkowy](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [obsługa aplikacji klienckich Microsoft 365 — uwierzytelnianie wieloskładnikowe](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>Ochrona kont administratorów

W przypadku Microsoft 365 E3 lub E5 lub z oddzielnymi licencjami Azure AD — wersja Premium P1 lub P2 możesz wymagać uwierzytelniania wieloskładnikowego dla kont administratorów z ręcznie utworzonymi zasadami dostępu warunkowego. Aby uzyskać szczegółowe informacje, zobacz [Dostęp warunkowy: Wymagaj uwierzytelniania wieloskładnikowego dla administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) .

W przypadku wersji Microsoft 365 lub Office 365, które nie obsługują dostępu warunkowego, można włączyć [ustawienia domyślne zabezpieczeń](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), aby wymagać uwierzytelniania wieloskładnikowego dla wszystkich kont.

Oto kilka dodatkowych zaleceń:

- Użyj [Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-getting-started), aby zmniejszyć liczbę trwałych kont administracyjnych.
- [Zarządzanie dostępem uprzywilejowanym umożliwia](../../compliance/privileged-access-management-overview.md) ochronę organizacji przed naruszeniami, które mogą korzystać z istniejących kont administratorów uprzywilejowanych z dostępem do poufnych danych lub dostępem do krytycznych ustawień konfiguracji.
- Tworzenie i używanie oddzielnych kont przypisanych [Microsoft 365 ról administratora](../../admin/add-users/about-admin-roles.md) *tylko do celów administracyjnych*. Administratorzy powinni mieć własne konto użytkownika do regularnego użytku nieadministracyjnym i używać konta administracyjnego tylko wtedy, gdy jest to konieczne do wykonania zadania skojarzonego z ich rolą lub funkcją zadania.
- Postępuj zgodnie z [najlepszymi rozwiązaniami](/azure/active-directory/admin-roles-best-practices) dotyczącymi zabezpieczania uprzywilejowanych kont w Azure AD.

## <a name="next-step"></a>Następny krok

[![Krok 2. Konfigurowanie typowych zasad Zero Trust tożsamości i dostępu do dostępu warunkowego.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png#lightbox)](identity-access-policies.md)

[Konfigurowanie typowych zasad tożsamości Zero Trust i dostępu urządzeń](identity-access-policies.md)
