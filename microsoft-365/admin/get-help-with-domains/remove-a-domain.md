---
title: Usuwanie domeny
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: Dowiedz się, jak usunąć starą domenę z usługi Microsoft 365 przenieść użytkowników i grupy do innej domeny lub anulować subskrypcję.
ms.openlocfilehash: 875858804912ab75d0a5a0bab45c9bb1614c82ca
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011302"
---
# <a name="remove-a-domain"></a>Usuwanie domeny

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Czy usuwasz domenę, ponieważ chcesz dodać ją do innego Microsoft 365 subskrypcji? A może zamierzasz anulować subskrypcję? Możesz [zmienić plan lub subskrypcję](../../commerce/subscriptions/switch-to-a-different-plan.md) albo [anulować swoją subskrypcję](../../commerce/subscriptions/cancel-your-subscription.md).

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

### <a name="step-1-move-users-to-another-domain"></a>Krok 1: Przenoszenie użytkowników do innej domeny

#### <a name="move-users"></a>Przenoszenie użytkowników

::: moniker range="o365-worldwide"

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnego</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centrum administracyjnego</a>.

::: moniker-end

2. Wybierz **pozycję** **UżytkownicyAktywowanie** >  użytkowników.

3. Zaznacz pola obok nazw wszystkich użytkowników, których chcesz przenieść.

4. U góry strony, a następnie wybierz pozycję **Zmień domeny**.

5. W **okienku Zmienianie** domen wybierz inną domenę.

Musisz to zrobić także dla siebie, jeśli korzystasz z domeny, którą chcesz usunąć. Podczas edytowania domeny dla swojego konta musisz się wylogować i zalogować się ponownie przy użyciu nowej domeny, aby kontynuować.

#### <a name="move-yourself"></a>Przenieś się

::: moniker range="o365-worldwide"

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnego</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centrum administracyjnego</a>.

::: moniker-end

2. Przejdź do **strony Aktywni** \> **użytkownicy**, a następnie wybierz swoje konto z listy.

3. Na karcie **Konto** wybierz pozycję **Zarządzaj nazwą użytkownika**, a następnie wybierz inną domenę.

4. U góry wybierz swoją nazwę konta, a następnie wybierz pozycję **Wyloguj.**

5. Zaloguj się przy użyciu nowej domeny i tego samego hasła.

Możesz także przenieść użytkowników do innej domeny za pomocą programu PowerShell. Zobacz [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname), aby uzyskać więcej informacji. Aby ustawić domenę domyślną, użyj polecenia [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

### <a name="step-2-move-groups-to-another-domain"></a>Krok 2: Przenoszenie grup do innej domeny

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Grupy** \> grupy.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">administracyjnym</a> przejdź do strony **Grupy** > grupy.

::: moniker-end

2. Zaznacz nazwę grupy, a następnie na karcie Ogólne  w obszarze Adres e-mail **, Podstawowy** wybierz pozycję **Edytuj**.

3. Z listy rozwijanej wybierz inną domenę.

4. Wybierz **pozycję Zapisz**, a następnie **zamknij**. Powtórz tę procedurę dla wszystkich grup lub list dystrybucyjnych skojarzonych z domeną, którą chcesz usunąć.

### <a name="step-3-remove-the-old-domain"></a>Krok 3: Usuwanie starej domeny

::: moniker range="o365-worldwide"

1. W Centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domeny</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Konfigurowanie** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domen</a> .

::: moniker-end

2. Na **stronie Domeny** wybierz domenę, którą chcesz usunąć.

3. W prawym okienku wybierz pozycję **Usuń**.

4. Postępuj zgodnie z dodatkowymi monitami, a następnie wybierz **pozycję Zamknij**.

## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>Jak długo trwa usuwanie domeny?

Usuwanie domeny przez program Microsoft 365 może potrwać nawet 5 minut, jeśli nie ma do niego odwoływać się w wielu miejscach, takich jak grupy zabezpieczeń, listy dystrybucyjne, użytkownicy Microsoft 365 grupy. Jeśli jest wiele odwołań korzystających z domeny, usunięcie domeny może potrwać kilka godzin (a nawet dzień).

Jeśli masz setki lub tysiące użytkowników, użyj programu PowerShell w celu wyszukania wszystkich użytkowników, a następnie przeniesienia ich do innej domeny. W przeciwnym razie w interfejsie użytkownika może zabraknąć kilku użytkowników, a po przejściu do usuwania domeny nie będzie to możliwe i nie będzie wiadomo, dlaczego. Zobacz [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname), aby uzyskać więcej informacji. Aby ustawić domenę domyślną, użyj polecenia [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

## <a name="still-need-help"></a>Nadal potrzebujesz pomocy?

::: moniker range="o365-worldwide"

> [!NOTE]
> Nie można usunąć domeny [„.onmicrosoft.com"](../setup/domains-faq.yml) z konta. Po usunięciu domeny konta użytkowników powrócą do adresu ".onmicrosoft.com" jako podstawowy adres SMTP/userprincipalName.

Nadal nie działa? Może być konieczne ręczne usunięcie danej domeny. [Zadzwoń do nas](../../business-video/get-help-support.md), a pomożemy Ci się tym zająć!

::: moniker-end

::: moniker range="o365-21vianet"

> [!NOTE]
> Nie można usunąć domeny [".partner.onmschina.cn"](../setup/domains-faq.yml) z konta. Po usunięciu domeny konta użytkowników powrócą do adresu ".partner.onmschina.cn" jako podstawowy adres SMTP/userprincipalName.

Nadal nie działa? Może być konieczne ręczne usunięcie danej domeny. [Zadzwoń do nas](../../business-video/get-help-support.md?view=o365-21vianet&preserve-view=true), a pomożemy Ci się tym zająć!

::: moniker-end

## <a name="related-content"></a>Zawartość pokrewna

[Domeny — często](../setup/domains-faq.yml) zadawane pytania (artykuł)

[Przełączanie się do innego Microsoft 365 dla firm](../../commerce/subscriptions/switch-to-a-different-plan.md) (artykuł)

[Anulowanie subskrypcji](../../commerce/subscriptions/cancel-your-subscription.md) (artykuł)
