---
title: Krok 1. Uniemożliwianie byłym pracownikom logowania się i blokowania dostępu do usług Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Administratorzy globalni mogą zablokować byłym pracownikom możliwość logowania się i blokowania dostępu do usług Microsoft 365.
ms.openlocfilehash: eec436a182f5e065f445167dea38fe99390ca105
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436652"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>Krok 1. Uniemożliwianie byłym pracownikom logowania się i blokowania dostępu do usług Microsoft 365

Jeśli musisz natychmiast uniemożliwić użytkownikowi dostęp do logowania, musisz zresetować jego hasło. W tym kroku wymuś wylogowanie użytkownika z Microsoft 365.

> [!NOTE]
> Musisz być administratorem globalnym, aby zainicjować wylogowanie dla innych administratorów. W przypadku użytkowników niebędących administratorami możesz użyć administratora użytkownika lub administratora pomocy technicznej, aby wykonać tę akcję. [Dowiedz się więcej o rolach administratora](about-admin-roles.md)

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.
2. Zaznacz pole obok nazwy użytkownika, a następnie wybierz pozycję **Resetuj hasło**.
3. Wprowadź nowe hasło, a następnie wybierz pozycję **Resetuj**. (Nie wysyłaj ich do nich).
4. Wybierz nazwę użytkownika, aby przejść do okienka jego właściwości, a następnie na karcie **Konto** wybierz pozycję **Wyloguj się ze wszystkich sesji**.

W ciągu godziny lub po opuszczeniu bieżącej strony Microsoft 365, na której się znajdują, zostanie wyświetlony monit o ponowne zalogowanie się. Token dostępu jest dobry przez godzinę, więc oś czasu zależy od tego, ile czasu pozostało do tego tokenu i czy nawigują poza bieżącą stronę internetową.
  
> [!IMPORTANT]
> Jeśli użytkownik jest w Outlook w sieci Web, po prostu klikając w swojej skrzynce pocztowej, może nie zostać wyrzucony natychmiast. Po wybraniu innego kafelka, takiego jak OneDrive lub odświeżeniu przeglądarki, wylogowanie zostanie zainicjowane.
  
Aby natychmiast wylogować użytkownika za pomocą programu PowerShell, zobacz polecenie cmdlet [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) .
  
Aby uzyskać więcej informacji o czasie, jaki zajmuje usunięcie kogoś z poczty e-mail, zobacz [Co należy wiedzieć o zamykaniu sesji poczty e-mail pracownika](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Blokowanie dostępu byłego pracownika do usług Microsoft 365

> [!IMPORTANT]
 > Zablokowanie konta może potrwać do 24 godzin. Jeśli musisz natychmiast uniemożliwić użytkownikowi dostęp do logowania, wykonaj powyższe kroki i zresetuj jego hasło.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.
2. Wybierz nazwę pracownika, który chcesz zablokować, a następnie w obszarze nazwa użytkownika wybierz symbol **Blokuj tego użytkownika**.
3. Wybierz **pozycję Blokuj logowanie użytkownika**, a następnie wybierz pozycję **Zapisz**.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Blokowanie byłemu pracownikowi dostępu do poczty e-mail (usługa Exchange Online)

Jeśli masz wiadomość e-mail w ramach subskrypcji Microsoft 365, zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego Exchange</a> i wykonaj te kroki, aby zablokować byłym pracownikom dostęp do poczty e-mail.
  
1. Przejdź do centrum administracyjnego Exchange > **Skrzynki pocztowe adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank"></a>
1. Wybierz skrzynkę pocztową użytkownika z listy, a następnie w *okienku Szczegóły* (po prawej stronie) wybierz pozycję **Zarządzaj ustawieniami aplikacji poczty e-mail** w obszarze **Aplikacje poczty e-mail**. **Wyłącz** suwak dla wszystkich opcji; **Urządzenia przenośne (Exchange ActiveSync),** **Outlook w sieci Web**, **Outlook desktop (MAPI),** **Exchange usługi internetowe**, **POP3** i **IMAP**.
1. Wybierz **Zapisz**.

## <a name="related-content"></a>Zawartość pokrewna

[centrum administracyjne Exchange w Exchange Online](/exchange/exchange-admin-center) (artykuł)\

[Przywracanie użytkownika](restore-user.md) (artykuł)
