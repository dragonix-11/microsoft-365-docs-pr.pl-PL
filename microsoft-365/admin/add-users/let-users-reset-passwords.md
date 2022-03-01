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
description: Dowiedz się, jak skonfigurować zasady umożliwiające użytkownikom samodzielne resetowanie haseł za pomocą narzędzia do samodzielnego resetowania hasła.
ms.openlocfilehash: e72d4815be5486f8f7df362b5b93cae988b7df63
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011304"
---
# <a name="let-users-reset-their-own-passwords"></a>Zezwalanie użytkownikom na resetowanie swoich haseł

Jako administrator Microsoft 365, możesz pozwolić użytkownikom na korzystanie z narzędzia do samodzielnego resetowania hasła, aby nie trzeba było resetować haseł za nich.[](https://go.microsoft.com/fwlink/p/?LinkId=522677) Mniej pracy dla Ciebie!

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.
 
## <a name="watch-let-users-reset-their-own-passwords"></a>Obejrzyj: umożliwianie użytkownikom resetowania swoich haseł

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3AY8S]

1. W okienku centrum administracyjne platformy Microsoft 365 w lewym okienku nawigacji  >  wybierz pozycję Ustawienia Ustawienia **Org**, a następnie pozycję Zabezpieczenia <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**i & prywatności**</a>.
1. W **obszarze Umożliwianie osobom resetowania swoich haseł wybierz** pozycję **Centrum administracyjne usługiAzure AD**.
1. W lewym okienku nawigacji **wybierz pozycję Użytkownicy**, a następnie na stronie Użytkownicy **— wszyscy** użytkownicy wybierz pozycję **Resetowanie hasła**.
1. Wybierz **pozycję Wszystkie** , aby włączyć funkcję samodzielnego resetowania hasła, a następnie wybierz pozycję **Zapisz**.

Jeśli ten klip wideo okazał się przydatny, poznaj [kompletną serię szkoleń dla małych firm i nowych użytkowników usługi Microsoft 365](../../business-video/index.yml).
 
## <a name="before-you-begin"></a>Przed rozpoczęciem
  
- Każdy plan płatny dla firm, Microsoft 365 dla firm,  edukacji i organizacji niedochodowych umożliwia bezpłatne samodzielne resetowanie haseł dla użytkowników chmury. Nie działa to w przypadku Microsoft 365 próbnej.

- Ta funkcja używa platformy Azure. Tę funkcję na platformie Azure automatycznie otrzymasz **bezpłatnie** po wykonaniu poniższych czynności. Jeśli nie korzystasz z innych funkcji platformy Azure, włączenie funkcji samodzielnego resetowania hasła nic nie kosztuje.

- **Jeśli korzystasz z lokalnej usługi Active Directory**, dwa powyższe punkty nie mają zastosowania. Właściwie możesz to skonfigurować, ale **wymaga to płatnej subskrypcji usługi Azure AD  wersja Premium**.

Ten artykuł jest przeznaczony dla osób, które konfigurują zasady wygasania haseł dla firmy, instytucji edukacyjnej lub organizacji niedochodowej. Aby wykonać te czynności, musisz zalogować się przy użyciu Microsoft 365 administratora. [Co to jest konto administratora?] (Omówienie centrum administracyjne platformy Microsoft 365](.. /admin-overview/admin-center-overview.md)

Aby wykonać te [czynności, musisz być administratorem globalnym lub administratorem](about-admin-roles.md) hasła.

## <a name="steps-let-people-reset-their-own-passwords"></a>Kroki: umożliwianie resetowania haseł

Wykonanie tych czynności spowoduje włączenie funkcji samodzielnego resetowania hasła dla wszystkich użytkowników w Twojej firmie.

1. W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">administracyjnym</a> przejdź **do strony Ustawienia** >  **Org ustawienia**.

2. W górnej części strony **ustawień organizacji** wybierz **kartę Zabezpieczenia i & prywatności** .
  
3. Wybierz **pozycję Samodzielne resetowanie hasła**.

4. W **obszarze Samodzielne resetowanie hasła** wybierz pozycję **Przejdź do portalu Azure Portal, aby włączyć samodzielne resetowanie hasła**.

5. Na stronie **Właściwości** wybierz **pozycję Wszystkie,** aby włączyć tę funkcję dla wszystkich osób w firmie, a następnie wybierz pozycję **Zapisz**.
  
6. Gdy użytkownicy się zalogują, zostanie wyświetlony monit o wprowadzenie dodatkowych informacji kontaktowych, które pomogą im zresetować hasło w przyszłości.

## <a name="related-content"></a>Zawartość pokrewna

[Ustawianie zasad wygasania haseł dla organizacji](../manage/set-password-expiration-policy.md) (artykuł)\
[Ustawianie hasła pojedynczego użytkownika tak, aby nigdy nie wygasło](set-password-to-never-expire.md) (artykuł)\
[Microsoft 365 szkoleniowe klipy wideo dla firm](../../business-video/index.yml) (strona linku)
