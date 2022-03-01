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
description: Dowiedz się, jak administrator może ustawić zasady wygasania haseł dla Twojej firmy, szkoły lub organizacji niedochodowej w centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: 9ba871a166169a0125b68808c124b10802424dfd
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011319"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Określanie zasad wygasania haseł w organizacji

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ten artykuł jest przeznaczony dla osób, które konfigurują zasady wygasania haseł dla firmy, instytucji edukacyjnej lub organizacji niedochodowej. Aby wykonać te czynności, musisz zalogować się przy użyciu Microsoft 365 administratora. [Co to jest konto administratora?](/microsoft-365/admin/add-users/about-admin-roles).

Jako administrator możesz ustawić wygasanie haseł użytkowników po upływie określonej liczby dni lub skonfigurować je tak, aby nigdy nie wygasały. Domyślnie hasła nigdy nie wygasają w danej organizacji.

Z bieżących badań zdecydowanie wynika, że obowiązkowe zmiany hasła przynoszą więcej szkód niż pożytku. Skłaniają użytkowników do wybierania słabszych haseł, ponownego ich wykorzystywania lub aktualizowania starych haseł w sposób umożliwiający łatwe ich odgadnięcie przez hakerów. Zalecamy włączenie [uwierzytelniania wieloskładnikowego](../security-and-compliance/set-up-multi-factor-authentication.md). Aby dowiedzieć się więcej o zasadach dotyczących haseł, zobacz Zalecenia [dotyczące zasad dotyczących haseł](../misc/password-policy-recommendations.md).

Aby wykonać te [czynności, musisz](../add-users/about-admin-roles.md) być administratorem globalnym.

Jeśli jesteś użytkownikiem, nie masz uprawnień do konfigurowania hasła tak, aby nigdy nie wygasło. Zwróć się o wykonanie procedury opisanej w tym artykule do pracownika pomocy technicznej w miejscu pracy lub na uczelni.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="set-password-expiration-policy"></a>Ustawianie zasad wygasania hasła

Postępuj zgodnie z poniższą instrukcją, jeśli chcesz, aby hasła użytkowników wygasały po upływie określonego czasu.

1. W centrum administracyjne platformy Microsoft 365 przejdź do karty Prywatność & <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**zabezpieczeń** w</a> obszarze **Ustawienia Ustawienia**.

    Jeśli nie jesteś administratorem globalnym, nie zobaczysz opcji Zabezpieczenia i prywatność.
  
1. Wybierz pozycję **Ustawianie zasad wygasania hasła**.
  
1. Jeśli nie chcesz, aby użytkownicy zmieniali hasła, wyczyść pole wyboru obok pozycji Ustaw wygasanie haseł użytkowników po **upływie kilku dni**.

1. Określ, jak często hasła powinny wygasać. Wybierz liczbę dni z przedziału od 14 do 730.
  
1. W drugim polu wpisz, kiedy użytkownicy będą powiadamiani o wygaśnięciu hasła, a następnie wybierz opcję **Zapisz**. Wybierz liczbę dni z przedziału od 1 do 30.

> [!IMPORTANT]
> Powiadomienia o wygaśnięciu hasła nie są już obsługiwane w Office sieci Web ani [w centrum administracyjnym](https://portal.office.com).
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Istotne kwestie dotyczące funkcji wygasania haseł, o których warto wiedzieć
  
Osoby, które używają tylko aplikacji Outlook, nie muszą resetować swoich haseł Microsoft 365 do momentu ich wygaśnięcia w pamięci podręcznej. Moment ten może nadejść kilka dni po rzeczywistej dacie wygaśnięcia. Obecnie nie ma obejścia tego błędu na poziomie administratora.

## <a name="prevent-last-password-from-being-used-again"></a>Zapobieganie ponownemu używaniu ostatniego hasła

Jeśli chcesz uniemożliwić użytkownikom ponowne stosowanie haseł, możesz to zrobić, wymuszając historię haseł w lokalnej usłudze Active Directory (AD). Zobacz [Tworzenie niestandardowych zasad haseł](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

W usłudze Azure AD nie można ponownie użyć ostatniego hasła, gdy użytkownik zmieni hasło. Zasady dotyczące haseł są stosowane do wszystkich kont użytkowników, które są tworzone i zarządzane bezpośrednio w usłudze Azure AD. Tych zasad haseł nie można modyfikować. Zobacz [Zasady dotyczące haseł usługi Azure AD](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Synchronizowanie skrótów haseł użytkowników z lokalnej usługi Active Directory z usługą Azure AD (Microsoft 365)

W tym artykule opisano ustawianie zasad wygasania haseł tylko do kont użytkowników w chmurze (Azure AD). Nie dotyczy on użytkowników tożsamości hybrydowej, którzy używają synchronizacji skrótów haseł, uwierzytelniania pass-through ani federacji lokalnej, na przykład usług ADFS.
  
Aby dowiedzieć się, jak synchronizować skróty haseł użytkowników z lokalnego katalogu AD z usługą Azure AD, zobacz [Implementowanie synchronizacji skrótów haseł za pomocą synchronizacji w narzędziu Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>Zasady dotyczące haseł i ograniczenia konta w Azure Active Directory

W usłudze Azure Active Directory możesz ustawić więcej zasad i ograniczeń dotyczących haseł. Aby uzyskać [więcej informacji, zobacz](/azure/active-directory/authentication/concept-sspr-policy) Zasady dotyczące haseł i ograniczenia Azure Active Directory konta.

## <a name="update-password-policy"></a>Aktualizowanie zasad haseł

Polecenie Set-MsolPasswordPolicy aktualizuje zasady dotyczące haseł określonej domeny lub dzierżawy i wskazuje czas, przez który hasło jest prawidłowe, zanim zostanie zmienione.

Aby dowiedzieć się, jak zaktualizować zasady dotyczące haseł dla określonej domeny lub [dzierżawy, zobacz Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>Zawartość pokrewna

[Umożliwianie użytkownikom resetowania swoich haseł](../add-users/let-users-reset-passwords.md) (artykuł)/

[Resetowanie haseł](../add-users/reset-passwords.md) (artykuł)
