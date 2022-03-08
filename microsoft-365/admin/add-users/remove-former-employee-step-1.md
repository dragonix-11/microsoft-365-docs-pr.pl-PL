---
title: Krok 1. Uniemożliwianie byłemu pracownikowi logowania się i blokowanie dostępu do Microsoft 365 usług
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
description: Zablokuj byłemu pracownikowi logowanie się i zablokuj dostęp do Microsoft 365 internetowych.
ms.openlocfilehash: abd6a6f47952b5af190b08f1ecae337840eaa312
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315963"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>Krok 1. Uniemożliwianie byłemu pracownikowi logowania się i blokowanie dostępu do Microsoft 365 usług

Jeśli chcesz od razu uniemożliwić użytkownikowi dostęp do logowania się, zresetuj jego hasło. W tym kroku wymusz wylogowanie użytkownika z Microsoft 365.

> [!NOTE]
> Aby zainicjować wylogowywę dla innych administratorów, musisz być administratorem globalnym. W przypadku użytkowników niebędących administratorami tę akcję może wykonać administrator użytkownika lub administrator pomocy technicznej. [Dowiedz się więcej o rolach administratorów](about-admin-roles.md)

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.
2. Zaznacz pole obok nazwy użytkownika, a następnie wybierz pozycję **Resetuj hasło**.
3. Wprowadź nowe hasło, a następnie wybierz pozycję **Resetuj**. (Nie wysyłaj ich do nich).
4. Wybierz nazwę użytkownika, aby przejść do jego okienka właściwości, a następnie na **karcie** Konto wybierz pozycję **Wyloguj się ze wszystkich sesji**.

W ciągu godziny — lub po opuszczeniu bieżącej Microsoft 365, na których się znajduje — zostanie wyświetlony monit o ponowne zalogowanie się. Token dostępu jest dobry przez godzinę, więc czas na osi czasu zależy od tego, ile czasu pozostało w tym tokenie i czy przechodzi poza bieżącą stronę sieci Web.
  
> [!IMPORTANT]
> Jeśli użytkownik znajduje się w Outlook w sieci Web, po prostu klikając w swojej skrzynce pocztowej, może nie zostać wyrzucony natychmiast. Gdy tylko wybierze inny kafelek, na przykład OneDrive lub odświeży przeglądarkę, zostanie zainicjowane wylogowywanie.
  
Aby natychmiast wylogować użytkownika za pomocą programu PowerShell, zobacz polecenie cmdlet [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) .
  
Aby uzyskać więcej informacji o czasie, jaki zajmuje usunięcie kogoś z poczty e-mail, zobacz [Co należy wiedzieć o zamykaniu sesji poczty e-mail pracownika](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Blokowanie byłemu pracownikowi dostępu do Microsoft 365 usług firmy

> [!IMPORTANT]
 > Zablokowanie konta może potrwać do 24 godzin. Jeśli chcesz od razu uniemożliwić użytkownikowi dostęp do logowania, wykonaj powyższe czynności i zresetuj jego hasło.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.
2. Wybierz imię i nazwisko pracownika, którego chcesz zablokować, a następnie pod imieniem i nazwiskiem użytkownika wybierz symbol blokowania **tego użytkownika**.
3. Wybierz **pozycję Zablokuj użytkownikom logowanie**, a następnie wybierz pozycję **Zapisz**.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Blokowanie byłemu pracownikowi dostępu do poczty e-mail (usługa Exchange Online)

Jeśli w ramach subskrypcji usługi Microsoft 365 masz pocztę e-mail, zaloguj się do centrum administracyjnego programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> i wykonaj poniższe czynności, aby zablokować byłemu pracownikowi dostęp do jego poczty e-mail.
  
1. Przejdź do centrum Exchange i > **adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank"></a>
1. Wybierz skrzynkę pocztową użytkownika z listy, a następnie w okienku *szczegółów (po* prawej stronie) wybierz pozycję Zarządzaj ustawieniami aplikacji poczty e-mail **w obszarze** **Aplikacje poczty e-mail**. Wyłącz **suwak** dla wszystkich opcji. **Aplikacje mobilne (Exchange ActiveSync)****, Outlook w sieci Web**, **Outlook (MAPI)** oraz usługi Exchange sieci **Web**, **POP3** **i IMAP**.
1. Wybierz **Zapisz**.

## <a name="related-content"></a>Zawartość pokrewna

[Exchange administracyjnego w programie Exchange Online](/exchange/exchange-admin-center) (artykuł)\

[Przywracanie użytkownika](restore-user.md) (artykuł)
