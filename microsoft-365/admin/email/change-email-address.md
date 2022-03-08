---
title: Zmienianie adresów e-mail w celu używania domeny niestandardowej
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: f4d8cae9-6d06-4c4b-b4e5-6581fd05ea82
description: Zmień swój adres e-mail na przyjazny adres e-mail, na tom@fourthcoffee.com, kupując nazwę domeny i dodając ją do Microsoft 365.
ms.openlocfilehash: 4630b3df4719611440e92801235fde20d7bd95f4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316425"
---
# <a name="change-your-email-address-to-use-your-custom-domain"></a>Zmienianie adresów e-mail w celu używania domeny niestandardowej

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
::: moniker range="o365-worldwide"

Twój początkowy adres e-mail w Microsoft 365 zawiera wartość onmicrosoft.com, na przykład tom@fourthcoffee.onmicrosoft.com. Możesz go zmienić na bardziej przyjazny adres, taki jak tomasz@fourthcoffee.com. Najpierw musisz mieć własną nazwę domeny, na przykład fourthcoffee.com. Jeśli już ją masz, to świetnie! W przeciwnym razie możesz dowiedzieć się, jak [kupić ją u rejestratora domen](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-21vianet"

Twój początkowy adres e-mail w Office 365 obsługiwanej przez firmę 21Vianet obejmuje partner.onmschina.cn, takie jak tom@fourthcoffee.partner.onmschina.cn. Możesz go zmienić na bardziej przyjazny adres, na przykład tom@fourthcoffee.cn. Najpierw musisz mieć własną nazwę domeny, na przykład fourthcoffee.cn domeny. Jeśli już ją masz, to świetnie! W przeciwnym razie możesz dowiedzieć się, jak [kupić ją u rejestratora domen](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

Gdy zmienisz adres e-mail domeny, aby przychodził do usługi Microsoft 365, przez zaktualizowanie rekordu MX domeny podczas konfiguracji WSZYSTKIE wiadomości e-mail wysyłane do tej domeny zaczną przychodzić do Microsoft 365. Przed zmianą rekordu MX upewnij się, że dodano użytkowników i utworzono skrzynki pocztowe Microsoft 365 dla wszystkich osób korzystających z poczty e-mail w tej domenie. Nie chcesz przenosić poczty e-mail wszystkich osób w domenie do Microsoft 365? Zamiast tego możesz wykonać [kroki pilotażowe Microsoft 365 tylko z kilkoma adresami e-mail](../misc/pilot-microsoft-365-from-my-custom-domain.md).
  
## <a name="set-up-business-email-with-a-new-domain"></a>Konfigurowanie firmowej poczty e-mail z nową domeną

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA?autoplay=false]

Kup nową nazwę domeny dla swojego adresu e-mail i skonfiguruj adresy e-mail za pomocą Microsoft 365.

1. Kup nową nazwę domeny dla swojego adresu e-mail, podając swoje informacje kontaktowe dla nowej nazwy domeny, wybierając metodę płatności, a następnie składając zamówienie.
1. Zmień pierwszą część adresu (przed znakiem @ ) lub pozostaw ją bez zmian. 
1. Wyloguj się Microsoft 365, a następnie zaloguj się ponownie przy użyciu nowego adresu e-mail. Adresy e-mail pracowników są aktualizowane o nową domenę. 

## <a name="set-up-business-email-with-an-existing-domain"></a>Konfigurowanie firmowej poczty e-mail z istniejącą domeną

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu?autoplay=false]

Użyj nazwy domeny, która już należy do Ciebie, niezależnie od tego, czy używasz jej na przykład adresu witryny internetowej, czy adresu e-mail u innego dostawcy.

1. Zaloguj się do witryny internetowej hostowej Twoją domenę. Kliknij przycisk, aby sprawdzić automatycznie lub ręcznie zaktualizować domenę. 
1. Dostosuj adres e-mail lub pozostaw go bez niego.
1. Wyloguj się Microsoft 365, a następnie zaloguj się ponownie przy użyciu nowego adresu e-mail. Adresy e-mail pracowników są aktualizowane o nową domenę.

## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Zmienianie adresu e-mail w celu używania domeny niestandardowej przy użyciu centrum administracyjne platformy Microsoft 365

Aby wykonać te czynności, musisz być administratorem globalnym.

::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

2. Przejdź do **strony** **SetupDomains** > .

3. Na stronie **Domeny** wybierz pozycję **Dodaj domenę**.

4. Postępuj zgodnie z instrukcjami, aby potwierdzić, że jesteś właścicielem domeny. Otrzymasz  przewodnik po tym, jak wszystko poprawnie skonfigurować w twojej domenie w Microsoft 365.

5. Przejdź do **usersActive** >  **users (Aktywuj użytkowników**).

6. Wybierz użytkownika, aby edytować jego nazwę użytkownika i zmienić go na właśnie dodaną domenę.

> [!NOTE]
> Jeśli nie używasz licencji usługi Exchange, nie możesz używać tej domeny do wysyłania i odbierania wiadomości e-mail z Microsoft 365 dzierżawy.
  
## <a name="related-content"></a>Zawartość pokrewna

[Kupowanie domeny niestandardowej przy Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (artykuł)\
[Zarządzanie domenami](/admin) (strona linku)\
[Domeny — często](../setup/domains-faq.yml) zadawane pytania (artykuł)