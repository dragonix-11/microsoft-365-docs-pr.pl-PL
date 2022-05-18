---
title: Określanie zasad wygasania haseł w organizacji
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 0f54736f-eb22-414c-8273-498a0918678f
description: Dowiedz się, jak administrator może ustawić zasady wygasania haseł dla twojej firmy, szkoły lub organizacji non-profit w Centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: b7f7691d0c1c0e6177d5414bc7802b62bb07a3b3
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468783"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Określanie zasad wygasania haseł w organizacji

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ten artykuł jest przeznaczony dla osób, które konfigurują zasady wygasania haseł dla firmy, instytucji edukacyjnej lub organizacji niedochodowej. Aby wykonać te kroki, musisz zalogować się przy użyciu konta administratora Microsoft 365. [Co to jest konto administratora?](/microsoft-365/admin/add-users/about-admin-roles).

Jako administrator możesz ustawić wygasanie haseł użytkowników po upływie określonej liczby dni lub skonfigurować je tak, aby nigdy nie wygasały. Domyślnie hasła są ustawiane tak, aby nigdy nie wygasały w organizacji.

Z bieżących badań zdecydowanie wynika, że obowiązkowe zmiany hasła przynoszą więcej szkód niż pożytku. Skłaniają użytkowników do wybierania słabszych haseł, ponownego ich wykorzystywania lub aktualizowania starych haseł w sposób umożliwiający łatwe ich odgadnięcie przez hakerów. Zalecamy włączenie [uwierzytelniania wieloskładnikowego](../security-and-compliance/set-up-multi-factor-authentication.md). Aby dowiedzieć się więcej na temat zasad haseł, zapoznaj się z [zaleceniami dotyczącymi zasad haseł](../misc/password-policy-recommendations.md).

Aby wykonać te kroki, musisz być [administratorem globalnym](../add-users/about-admin-roles.md) .

Jeśli jesteś użytkownikiem, nie masz uprawnień do konfigurowania hasła tak, aby nigdy nie wygasło. Zwróć się o wykonanie procedury opisanej w tym artykule do pracownika pomocy technicznej w miejscu pracy lub na uczelni.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą ds. małych firm firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy uzyskujecie całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm w miarę rozwoju firmy — od dołączania do codziennego użytku.

## <a name="set-password-expiration-policy"></a>Ustawianie zasad wygasania hasła

Postępuj zgodnie z poniższą instrukcją, jeśli chcesz, aby hasła użytkowników wygasały po upływie określonego czasu.

1. W Centrum administracyjne platformy Microsoft 365 przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">karty **Prywatność & zabezpieczeń**</a>.

    Jeśli nie jesteś administratorem globalnym ani administratorem zabezpieczeń, nie zobaczysz opcji Ochrona & prywatności.
  
1. Wybierz pozycję **Ustawianie zasad wygasania hasła**.
  
1. Jeśli nie chcesz, aby użytkownicy musieli zmieniać hasła, usuń zaznaczenie pola wyboru obok pozycji **Ustaw hasła, aby nigdy nie wygasały**.

1. Określ, jak często hasła powinny wygasać. Wybierz liczbę dni z przedziału od 14 do 730.
 
> [!IMPORTANT]
> Powiadomienia o wygaśnięciu hasła nie są już obsługiwane w Office aplikacji internetowych ani [w centrum administracyjnym](https://portal.office.com).
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Istotne kwestie dotyczące funkcji wygasania haseł, o których warto wiedzieć
  
Osoby korzystające tylko z aplikacji Outlook nie będą zmuszone do zresetowania Microsoft 365 hasła do momentu wygaśnięcia go w pamięci podręcznej. Moment ten może nadejść kilka dni po rzeczywistej dacie wygaśnięcia. Obecnie nie ma obejścia tego błędu na poziomie administratora.

## <a name="prevent-last-password-from-being-used-again"></a>Zapobieganie ponownemu używaniu ostatniego hasła

Jeśli chcesz uniemożliwić użytkownikom odtwarzanie starych haseł, możesz to zrobić, wymuszając historię haseł w usłudze lokalna usługa Active Directory (AD). Zobacz [Tworzenie niestandardowych zasad haseł](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

W Azure AD ostatniego hasła nie można użyć ponownie, gdy użytkownik zmieni hasło. Zasady haseł są stosowane do wszystkich kont użytkowników, które są tworzone i zarządzane bezpośrednio w Azure AD. Nie można modyfikować tych zasad haseł. Zobacz [Azure AD zasad haseł](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Synchronizowanie skrótów haseł użytkowników z lokalna usługa Active Directory do Azure AD (Microsoft 365)

W tym artykule opisano ustawianie zasad wygasania haseł tylko do kont użytkowników w chmurze (Azure AD). Nie dotyczy użytkowników tożsamości hybrydowej, którzy używają synchronizacji skrótów haseł, uwierzytelniania przekazywanego lub federacji lokalnej, takiej jak usługi ADFS.
  
Aby dowiedzieć się, jak synchronizować skróty haseł użytkowników z lokalnego katalogu AD z usługą Azure AD, zobacz [Implementowanie synchronizacji skrótów haseł za pomocą synchronizacji w narzędziu Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>Zasady haseł i ograniczenia kont w Azure Active Directory

Więcej zasad i ograniczeń haseł można ustawić w usłudze Azure Active Directory. Aby uzyskać więcej informacji, zapoznaj się z [tematem Zasady haseł i ograniczenia kont w Azure Active Directory](/azure/active-directory/authentication/concept-sspr-policy).

## <a name="update-password-policy"></a>Aktualizowanie zasad haseł

Polecenie cmdlet Set-MsolPasswordPolicy aktualizuje zasady haseł określonej domeny lub dzierżawy i wskazuje czas, przez jaki hasło pozostaje prawidłowe przed jego zmianą.

Aby dowiedzieć się, jak zaktualizować zasady haseł dla określonej domeny lub dzierżawy, zobacz [Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>Zawartość pokrewna

[Zezwalaj użytkownikom na resetowanie własnych haseł](../add-users/let-users-reset-passwords.md) (artykuł)/

[Resetowanie haseł](../add-users/reset-passwords.md) (artykuł)
