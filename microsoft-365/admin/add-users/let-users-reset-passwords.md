---
title: Zezwalanie użytkownikom na resetowanie swoich haseł
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
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5bc3f460-13cc-48c0-abd6-b80bae72d04a
description: Dowiedz się, jak ustawić zasady w Centrum administracyjne platformy Microsoft 365, aby umożliwić użytkownikom resetowanie własnych haseł przy użyciu samoobsługowego narzędzia do resetowania haseł.
ms.openlocfilehash: 2ade056638db03a0a38b7fe2bdacfe3d6d2e4530
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436696"
---
# <a name="let-users-reset-their-own-passwords"></a>Zezwalanie użytkownikom na resetowanie swoich haseł

Jako administrator Microsoft 365 możesz zezwolić użytkownikom na korzystanie z [samoobsługowego narzędzia do resetowania haseł](https://go.microsoft.com/fwlink/p/?LinkId=522677), aby nie trzeba było resetować dla nich haseł. Mniej pracy dla Ciebie!

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą ds. małych firm firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy uzyskujecie całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm w miarę rozwoju firmy — od dołączania do codziennego użytku.
 
## <a name="watch-let-users-reset-their-own-passwords"></a>Obejrzyj: Zezwalaj użytkownikom na resetowanie własnych haseł

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3AY8S]

1. W Centrum administracyjne platformy Microsoft 365 w okienku nawigacji po lewej stronie wybierz pozycję **Ustawienia** >  **Konserwuj ustawienia**, a następnie pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Zabezpieczenia & prywatność**</a>.
1. W obszarze **Zezwalaj swoim osobom na resetowanie własnych haseł** wybierz pozycję **Azure AD centrum administracyjne**.
1. W okienku nawigacji po lewej stronie wybierz pozycję **Użytkownicy**, a następnie na stronie **Użytkownicy — wszyscy użytkownicy** wybierz pozycję **Resetowanie hasła**.
1. Wybierz pozycję **Wszystkie** , aby włączyć samoobsługowe resetowanie hasła, a następnie wybierz pozycję **Zapisz**.

Jeśli ten klip wideo okazał się przydatny, poznaj [kompletną serię szkoleń dla małych firm i nowych użytkowników usługi Microsoft 365](../../business-video/index.yml).
 
## <a name="before-you-begin"></a>Przed rozpoczęciem
  
- Samoobsługowe resetowanie haseł dla użytkowników chmury jest **bezpłatne** z dowolnym płatnym planem Microsoft 365 biznesowym, edukacyjnym lub non-profit. Nie działa z Microsoft 365 wersji próbnej.

- Ta funkcja używa platformy Azure. Tę funkcję na platformie Azure automatycznie otrzymasz **bezpłatnie** po wykonaniu poniższych czynności. Jeśli nie korzystasz z innych funkcji platformy Azure, włączenie funkcji samodzielnego resetowania hasła nic nie kosztuje.

- **Jeśli korzystasz z lokalnej usługi Active Directory**, dwa powyższe punkty nie mają zastosowania. Właściwie możesz to skonfigurować, ale **wymaga to płatnej subskrypcji usługi Azure AD  wersja Premium**.

Ten artykuł jest przeznaczony dla osób, które konfigurują zasady wygasania haseł dla firmy, instytucji edukacyjnej lub organizacji niedochodowej. Aby wykonać te kroki, musisz zalogować się przy użyciu konta administratora Microsoft 365. [Co to jest konto administratora?] (Omówienie Centrum administracyjne platformy Microsoft 365](.. /admin-overview/admin-center-overview.md)

Aby wykonać te kroki, musisz być [administratorem globalnym lub administratorem haseł](about-admin-roles.md) .

## <a name="steps-let-people-reset-their-own-passwords"></a>Kroki: Zezwalaj użytkownikom na resetowanie własnych haseł

Wykonanie tych czynności spowoduje włączenie funkcji samodzielnego resetowania hasła dla wszystkich użytkowników w Twojej firmie.

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnym</a> przejdź do strony **ustawień Ustawienia** >  **Org**.

2. W górnej części strony **Ustawienia organizacji** wybierz kartę **Zabezpieczenia & prywatność** .
  
3. Wybierz pozycję **Samoobsługowe resetowanie hasła**.

4. W obszarze **Samoobsługowe resetowanie hasła** wybierz pozycję **Przejdź do Azure Portal, aby włączyć samoobsługowe resetowanie hasła**.

5. Na stronie **Właściwości** wybierz pozycję **Wszystkie** , aby włączyć ją dla wszystkich w firmie, a następnie wybierz pozycję **Zapisz**.
  
6. Gdy użytkownicy się zalogują, zostanie wyświetlony monit o wprowadzenie dodatkowych informacji kontaktowych, które pomogą im zresetować hasło w przyszłości.

## <a name="related-content"></a>Zawartość pokrewna

[Ustaw zasady wygasania haseł dla organizacji](../manage/set-password-expiration-policy.md) (artykuł)\
[Ustaw hasło użytkownika, aby nigdy nie wygasało](set-password-to-never-expire.md) (artykuł)\
[Microsoft 365 filmy szkoleniowe dla firm](../../business-video/index.yml) (strona linku)
