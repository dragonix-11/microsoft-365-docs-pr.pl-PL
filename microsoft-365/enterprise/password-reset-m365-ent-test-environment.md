---
title: Resetowanie hasła w środowisku Microsoft 365 testowym
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Podsumowanie: Skonfiguruj i przetestuj resetowanie hasła w Microsoft 365 testowym.'
ms.openlocfilehash: 9aa55f42ca295577bf3b1c81ee54b1160adf3d27
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986411"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>Resetowanie hasła w środowisku Microsoft 365 testowym

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

Azure Active Directory (Azure AD) funkcja samodzielnego resetowania hasła (SSPR) pozwala użytkownikom resetować i odblokowywać swoje hasła lub konta.

W tym artykule opisano, jak konfigurować i testować resetowanie hasła w środowisku testowania Microsoft 365 sieci.

Konfigurowanie zasad SSPR obejmuje trzy fazy:
- [Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku testowania Microsoft 365 hasła](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Etap 2. Włączanie funkcji zapisu hasła](#phase-2-enable-password-writeback)
- [Etap 3. Konfigurowanie i testowanie resetowania hasła](#phase-3-configure-and-test-password-reset)
    
![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Etap 1. Konfigurowanie synchronizacji skrótów haseł w środowisku testowania Microsoft 365 hasła

Najpierw postępuj zgodnie z instrukcjami [dotyczącymi synchronizacji skrótów haseł](password-hash-sync-m365-ent-test-environment.md). 

Wynikowa konfiguracja wygląda następująco:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowania skrótów haseł.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z:
  
- Subskrypcja Microsoft 365 E5 próbna lub płatna.
- Uproszczony intranet organizacji połączony z Internetem składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w aplikacji APP1 w celu zsynchronizowania domeny TESTLAB Usługi domenowe w usłudze Active Directory (AD DS) z dzierżawą usługi Azure AD subskrypcji usługi Microsoft 365 usługi.

## <a name="phase-2-enable-password-writeback"></a>Etap 2. Włączanie funkcji zapisu hasła

Postępuj zgodnie z instrukcjami [z fazy 2 przewodnika laboratorium testowego zapisu hasła](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

Aby funkcja resetowania hasła umożliwiała resetowanie hasła, funkcja zapisu hasła musi być włączona.
  
## <a name="phase-3-configure-and-test-password-reset"></a>Etap 3. Konfigurowanie i testowanie resetowania hasła

Na tym etapie skonfiguruj resetowanie hasła w dzierżawie usługi Azure AD za pośrednictwem członkostwa w grupach, a następnie sprawdź, czy działa.

Najpierw włącz resetowanie hasła dla kont w konkretnej grupie usługi Azure AD.

1. W prywatnym wystąpieniu przeglądarki otwórz pozycję [https://portal.azure.com](https://portal.azure.com), a następnie zaloguj się przy użyciu poświadczeń konta administratora globalnego.
2. W portalu Azure wybierz pozycję **Azure Active Directory** >  **GroupsNew** >  **group**.
3. Ustaw **typ grupy na** Wartość **zabezpieczeń**, **Nazwę grupy** na **PWReset**, a dla **typu Członkostwo** na **Wartość przypisana**.
4. Wybierz **pozycję Członkowie**, znajdź i wybierz **pozycję Użytkownik 3**, wybierz **pozycję Wybierz**, a następnie wybierz pozycję **Utwórz**.
5. Zamknij okienko **Grupy** .
6. W okienku Azure Active Directory nawigacji wybierz pozycję **Resetowanie** hasła.
7. W **okienku Password reset-Properties (Właściwości** resetowania hasła) w obszarze opcji **Self Service Password Reset Enabled** (Samodzielne resetowanie hasła włączone) wybierz pozycję **Selected (Zaznaczone**).
8. Wybierz **pozycję Wybierz** grupę, wybierz grupę **PWReset**, a następnie wybierz **pozycję** **ZaznaczZazamów** > .
9. Zamknij prywatne wystąpienie przeglądarki.

Następnie przetestuj resetowanie hasła dla konta użytkownika 3.

1. Otwórz nowe wystąpienie przeglądarki prywatnej i przejdź do strony [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
1. Zaloguj się przy użyciu poświadczeń konta Użytkownika 3.
1. W **większej liczby wymaganych informacji** wybierz pozycję **Dalej**. 
1. W **ekranie Nie utrac dostępu** do swojego konta ustaw numer telefonu uwierzytelniania na swój numer telefonu komórkowego i adres e-mail uwierzytelnienia na służbowe lub osobiste konto e-mail.
1. Po zweryfikowaniu obu opcji wybierz **pozycję Wygląda dobrze**, a następnie zamknij prywatne wystąpienie przeglądarki.
1. W nowym prywatnym wystąpieniu przeglądarki przejdź do .[https://aka.ms/sspr](https://aka.ms/sspr)
1. Wprowadź nazwę konta Użytkownik 3, wprowadź znaki z captcha, a następnie wybierz przycisk **Dalej**.
1. Aby **uzyskać weryfikację w kroku 1**, wybierz pozycję Wyślij **mój alternatywny adres e-mail pocztą e-mail**, a następnie wybierz pozycję Wyślij wiadomość **e-mail**. Po otrzymaniu wiadomości e-mail wprowadź kod weryfikacyjny, a następnie wybierz pozycję **Dalej**.
1. W **wrócić do swojego konta** wprowadź nowe hasło dla konta Użytkownika 3, a następnie wybierz pozycję **Zakończ**. Zanotuj zmienione hasło do konta użytkownika 3 i przechowuj je w bezpiecznym miejscu.
1. Na osobnej karcie tej samej [https://admin.microsoft.com](https://admin.microsoft.com)przeglądarki przejdź do przycisku , a następnie zaloguj się przy użyciu nazwy konta Użytkownika 3 i jego nowego hasła. Powinna zostać wyświetlony Microsoft Office **strona główna**.

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)