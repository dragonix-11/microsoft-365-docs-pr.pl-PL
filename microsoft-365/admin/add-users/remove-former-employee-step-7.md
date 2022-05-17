---
title: Krok 7. Usuwanie konta użytkownika byłego pracownika
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
search.appverid:
- BCS160
- MET150
- MOE150
description: Po zapisaniu wszystkich danych użytkownika byłego pracownika i uzyskaniu do nich dostępu możesz usunąć konto byłego pracownika w Centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: d6e53dd8d14add9383e3eff9d3c1d90a5087ec45
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436278"
---
# <a name="step-7---delete-a-former-employees-user-account"></a>Krok 7. Usuwanie konta użytkownika byłego pracownika

Po zapisaniu i uzyskaniu dostępu do wszystkich danych użytkownika byłego pracownika można usunąć konto byłego pracownika.

> [!IMPORTANT]
> Nie usuwaj konta, jeśli zostało skonfigurowane przesyłanie dalej poczty e-mail lub konto zostało przekonwertowane na udostępnioną skrzynkę pocztową. Konto jest niezbędne zarówno w przypadku przesyłania dalej poczty, jak i udostępnionej skrzynki pocztowej.

1. W centrum administracyjnym przejdź do strony **Użytkownicy** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktywni użytkownicy</a>.
2. Wybierz nazwę pracownika, który chcesz usunąć.
3. W obszarze nazwa użytkownika wybierz pozycję **Usuń użytkownika**. Wybierz odpowiednie opcje dla tego użytkownika, a następnie wybierz pozycję **Usuń użytkownika**. Jeśli masz już dostęp innego użytkownika do poczty e-mail tego użytkownika i OneDrive, nie musisz tego robić ponownie tutaj.

Po usunięciu użytkownika jego konto staje się nieaktywne na około 30 dni. Przed upływem tego czasu można przywrócić konto  później zostanie ono trwale usunięte.

## <a name="watch-delete-a-former-employees-user-account"></a>Obejrzyj: Usuwanie konta użytkownika byłego pracownika

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR]

Jeśli ten klip wideo okazał się przydatny, poznaj [kompletną serię szkoleń dla małych firm i nowych użytkowników usługi Microsoft 365](../../business-video/index.yml).

## <a name="does-your-organization-use-active-directory"></a>Czy Twoja organizacja korzysta z usługi Active Directory?

Jeśli organizacja synchronizuje konta użytkowników z Microsoft 365 z lokalnego środowiska usługi Active Directory, należy usunąć i przywrócić te konta użytkowników w lokalnej usłudze Active Directory. Nie można tego robić w usłudze Office 365.

Aby dowiedzieć się, jak usunąć i przywrócić konto użytkownika w usłudze Active Directory, zobacz [Usuwanie konta użytkownika](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).
  
Jeśli używasz Azure Active Directory, zobacz polecenie cmdlet [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) programu PowerShell.
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>Co należy wiedzieć o zamykaniu sesji poczty e-mail pracownika

Poniżej przedstawiono informacje o tym, jak usunąć pracownika z poczty e-mail (Exchange).

<br>

****

|Co możesz zrobić|Jak to zrobić|
|:-----|:-----|
|Zamknięcie sesji (na przykład aplikacji Outlook w sieci Web, programu Outlook, programu Exchange Active Sync itp.) i wymuszenie otwarcia nowej sesji|Resetuj hasło|
|Zamknięcie sesji i zablokowanie dostępu do przyszłych sesji (dla wszystkich protokołów)|Wyłącz konto. Na przykład (w centrum administracyjnym Exchange lub przy użyciu programu PowerShell): <p>  `Set-Mailbox user@contoso.com -AccountDisabled:$true`|
|Zamknięcie sesji dla konkretnego protokołu (na przykład ActiveSync)|Wyłącz protokół. Na przykład (w centrum administracyjnym Exchange lub przy użyciu programu PowerShell): <p>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false`|
|

Powyższe operacje można wykonać w trzech miejscach:
  
<br>

****

|Jeśli zamykasz sesję tutaj|Zajmuje to tyle czasu|
|---|---|
|W centrum administracyjnym programu Exchange lub przy użyciu programu PowerShell|Oczekiwane opóźnienie mieści się w 30 minutach|
|W centrum administracyjnym usługi Azure Active Directory|Oczekiwane opóźnienie wynosi 60 minut|
|W środowisku lokalnym|Oczekiwane opóźnienie wynosi co najmniej 3 godziny|
|

### <a name="how-to-get-fastest-response-for-account-termination"></a>Jak uzyskać najszybszą reakcję na zamknięcie konta

**Najszybsza**. Użyj centrum administracyjnego programu Exchange (użyj programu PowerShell) lub centrum administracyjnego usługi Azure Active Directory. Synchronizowanie zmian za pomocą narzędzia DirSync w środowisku lokalnym może potrwać kilka godzin.
  
**Najszybsza dla użytkownika obecnego lokalnie i w centrum danych programu Exchange**. Zamknij sesję przy użyciu centrum administracyjnego usługi Azure Active Directory/centrum administracyjnego programu Exchange i wprowadź zmiany również w środowisku lokalnym. W przeciwnym razie zmiany w centrum administracyjnym usługi Azure Active Directory/centrum administracyjnym programu Exchange zostaną zastąpione przez narzędzie DirSync.
  
## <a name="related-content"></a>Zawartość pokrewna

[Przywracanie użytkownika](restore-user.md) (artykuł)

[Resetowanie haseł](reset-passwords.md) (artykuł)
