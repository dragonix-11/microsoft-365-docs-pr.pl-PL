---
title: Resetowanie hasła dla środowiska testowego Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Konfigurowanie i testowanie resetowania hasła dla środowiska testowego Microsoft 365.'
ms.openlocfilehash: 4e68372aee44887641d626c3e3667adbdedd5a1e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095625"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>Resetowanie hasła dla środowiska testowego Microsoft 365

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

samoobsługowe resetowanie haseł (SSPR) Azure Active Directory (Azure AD) umożliwia użytkownikom resetowanie lub odblokowywanie haseł lub kont.

W tym artykule opisano sposób konfigurowania i testowania resetowania haseł w środowisku testowym Microsoft 365.

Konfigurowanie samoobsługowego resetowania hasła obejmuje trzy fazy:
- [Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Faza 2. Włączanie zapisywania zwrotnego haseł](#phase-2-enable-password-writeback)
- [Faza 3. Konfigurowanie i testowanie resetowania hasła](#phase-3-configure-and-test-password-reset)
    
![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Faza 1. Konfigurowanie synchronizacji skrótów haseł dla środowiska testowego Microsoft 365

Najpierw postępuj zgodnie z instrukcjami [synchronizacji skrótów haseł](password-hash-sync-m365-ent-test-environment.md). 

Wynikowe konfiguracje wyglądają następująco:
  
![Symulowane przedsiębiorstwo ze środowiskiem testowym synchronizacji skrótów haseł.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Ta konfiguracja składa się z następujących elementów:
  
- Subskrypcja Microsoft 365 E5 wersji próbnej lub płatnej.
- Uproszczony intranet organizacji połączony z Internetem, składający się z maszyn wirtualnych DC1, APP1 i CLIENT1 w podsieci sieci wirtualnej platformy Azure.
- Usługa Azure AD Połączenie działa w usłudze APP1, aby zsynchronizować domenę Active Directory Domain Services TESTLAB (AD DS) z dzierżawą usługi Azure AD subskrypcji Microsoft 365.

## <a name="phase-2-enable-password-writeback"></a>Faza 2. Włączanie zapisywania zwrotnego haseł

Postępuj zgodnie z instrukcjami w [sekcji Faza 2 przewodnika laboratorium testowego zapisywania zwrotnego haseł](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

Aby używać resetowania hasła, musisz mieć włączoną funkcję zapisywania zwrotnego haseł.
  
## <a name="phase-3-configure-and-test-password-reset"></a>Faza 3. Konfigurowanie i testowanie resetowania hasła

W tej fazie skonfiguruj resetowanie hasła w dzierżawie usługi Azure AD za pomocą członkostwa w grupie, a następnie sprawdź, czy działa.

Najpierw włącz resetowanie hasła dla kont w określonej grupie usługi Azure AD.

1. W prywatnym wystąpieniu przeglądarki otwórz polecenie [https://portal.azure.com](https://portal.azure.com), a następnie zaloguj się przy użyciu poświadczeń konta administratora globalnego.
2. W Azure Portal wybierz pozycję **Azure Active Directory** >  **GroupsNowa** >  **grupa**.
3. Ustaw **typ grupy** na **wartość Zabezpieczenia**, **Nazwa grupy** na **PWReset**, a **typ członkostwa** na **Przypisano**.
4. Wybierz pozycję **Członkowie**, znajdź i wybierz pozycję **Użytkownik 3**, wybierz pozycję **Wybierz**, a następnie wybierz pozycję **Utwórz**.
5. Zamknij okienko **Grupy** .
6. W okienku Azure Active Directory wybierz pozycję **Resetowanie hasła** w obszarze nawigacji po lewej stronie.
7. W okienku **Resetowanie hasła-Właściwości** w obszarze opcji **Samoobsługowe resetowanie hasła włączone** wybierz pozycję **Wybrane**.
8. Wybierz **pozycję Wybierz grupę**, wybierz grupę **PWReset**, a następnie wybierz pozycję **WybierzZapisz** > .
9. Zamknij wystąpienie przeglądarki prywatnej.

Następnie przetestuj resetowanie hasła dla konta użytkownika 3.

1. Otwórz nowe wystąpienie przeglądarki prywatnej i przejdź do obszaru [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
1. Zaloguj się przy użyciu poświadczeń konta użytkownika 3.
1. W **obszarze Więcej wymaganych informacji** wybierz pozycję **Dalej**. 
1. W **obszarze Nie trac dostępu do konta** ustaw numer telefonu uwierzytelniania na numer telefonu komórkowego i adres e-mail uwierzytelniania na służbowe lub osobiste konto e-mail.
1. Po zweryfikowaniu obu tych elementów wybierz pozycję **Wygląda dobrze**, a następnie zamknij prywatne wystąpienie przeglądarki.
1. W nowym wystąpieniu przeglądarki prywatnej przejdź do pozycji [https://aka.ms/sspr](https://aka.ms/sspr).
1. Wprowadź nazwę konta Użytkownika 3, wprowadź znaki z captcha, a następnie wybierz przycisk **Dalej**.
1. W **kroku 1 weryfikacji** wybierz pozycję **Wyślij wiadomość e-mail do mojej alternatywnej wiadomości e-mail**, a następnie wybierz pozycję **Poczta e-mail**. Po otrzymaniu wiadomości e-mail wprowadź kod weryfikacyjny, a następnie wybierz pozycję **Dalej**.
1. W **obszarze Wróć do konta** wprowadź nowe hasło dla konta Użytkownika 3, a następnie wybierz pozycję **Zakończ**. Zanotuj zmienione hasło konta użytkownika 3 i zapisz je w bezpiecznej lokalizacji.
1. Na osobnej karcie tej samej przeglądarki przejdź do [https://admin.microsoft.com](https://admin.microsoft.com)pozycji , a następnie zaloguj się przy użyciu nazwy konta użytkownika 3 i nowego hasła. Powinna zostać wyświetlona strona **główna Microsoft Office**.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)