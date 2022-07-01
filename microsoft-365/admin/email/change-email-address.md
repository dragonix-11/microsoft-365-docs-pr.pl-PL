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
description: Zmień adres e-mail na przyjazny adres e-mail, taki jak tom@fourthcoffee.com, kupując nazwę domeny i dodając ją do platformy Microsoft 365.
ms.openlocfilehash: 2c6085ee9c951b9afb3d44460bfd613b63375986
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602431"
---
# <a name="change-your-microsoft-365-email-address-to-use-your-custom-domain"></a>Zmienianie adresu e-mail platformy Microsoft 365 w celu korzystania z domeny niestandardowej

Zapoznaj się z [pomocą dla małych firm platformy Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) w serwisie YouTube.

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
::: moniker range="o365-worldwide"

Początkowy adres e-mail w usłudze Microsoft 365 zawiera onmicrosoft.com, na przykład tom@fourthcoffee.onmicrosoft.com. Możesz go zmienić na bardziej przyjazny adres, taki jak tomasz@fourthcoffee.com. Najpierw musisz mieć własną nazwę domeny, na przykład fourthcoffee.com. Jeśli już ją masz, to świetnie! W przeciwnym razie możesz dowiedzieć się, jak [kupić ją u rejestratora domen](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-21vianet"

Początkowy adres e-mail w Office 365 obsługiwany przez firmę 21Vianet obejmuje partner.onmschina.cn, takie jak tom@fourthcoffee.partner.onmschina.cn. Możesz zmienić go na bardziej przyjazny adres, taki jak tom@fourthcoffee.cn. Będziesz potrzebować własnej nazwy domeny, takiej jak fourthcoffee.cn najpierw. Jeśli już ją masz, to świetnie! W przeciwnym razie możesz dowiedzieć się, jak [kupić ją u rejestratora domen](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

Po zmianie adresu e-mail domeny na microsoft 365 przez zaktualizowanie rekordu MX domeny podczas instalacji wszystkie wiadomości e-mail wysyłane do tej domeny zaczną pojawiać się na platformie Microsoft 365. Przed zmianą rekordu MX upewnij się, że dodano użytkowników i utworzono skrzynki pocztowe w usłudze Microsoft 365 dla wszystkich osób, które mają adres e-mail w domenie. Nie chcesz przenosić wiadomości e-mail dla wszystkich w domenie na platformę Microsoft 365? Możesz zamiast tego wykonać kroki [pilotażu usługi Microsoft 365 z zaledwie kilkoma adresami e-mail](../misc/pilot-microsoft-365-from-my-custom-domain.md).
  
## <a name="set-up-business-email-with-a-new-domain"></a>Konfigurowanie służbowej poczty e-mail przy użyciu nowej domeny

Zapoznaj się z tym filmem i innymi osobami na naszym [kanale YouTube](https://go.microsoft.com/fwlink/?linkid=2198215).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA?autoplay=false]

Kup nową nazwę domeny dla swojego adresu e-mail i skonfiguruj adresy e-mail przy użyciu platformy Microsoft 365.

1. Kup nową nazwę domeny dla swojego adresu e-mail, podając informacje kontaktowe dla nowej nazwy domeny, wybierając formę płatności, a następnie składając zamówienie.
1. Zmień pierwszą część adresu (przed znakiem @) lub pozostaw ją w następującym miejscu. 
1. Wyloguj się z platformy Microsoft 365, a następnie zaloguj się ponownie przy użyciu nowego adresu e-mail. Adresy e-mail pracowników są aktualizowane przy użyciu nowej domeny. 

## <a name="set-up-business-email-with-an-existing-domain"></a>Konfigurowanie firmowych wiadomości e-mail przy użyciu istniejącej domeny

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu?autoplay=false]

Użyj już posiadanej nazwy domeny, niezależnie od tego, czy używasz jej dla adresu witryny internetowej, czy adresu e-mail u innego dostawcy.

1. Zaloguj się do witryny internetowej hostującej domenę. Kliknij przycisk, aby automatycznie zweryfikować lub ręcznie zaktualizować domenę. 
1. Dostosuj adres e-mail lub pozostaw go tak, jak jest.
1. Wyloguj się z platformy Microsoft 365, a następnie zaloguj się ponownie przy użyciu nowego adresu e-mail. Adresy e-mail pracowników są aktualizowane przy użyciu nowej domeny.

## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Zmień adres e-mail, aby używać domeny niestandardowej przy użyciu Centrum administracyjne platformy Microsoft 365

Aby wykonać te kroki, musisz być administratorem globalnym.

::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego pod adresem <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

2. Przejdź do strony **Domeny konfiguracji** > .

3. Na stronie **Domeny** wybierz pozycję **Dodaj domenę**.

4. Wykonaj kroki, aby potwierdzić, że jesteś właścicielem domeny. Zostanie wyświetlona instrukcja dotycząca poprawnego skonfigurowania wszystkich elementów w domenie w usłudze Microsoft 365.

5. Przejdź do pozycji **Użytkownicy** > **aktywni użytkownicy**.

6. Wybierz użytkownika, aby edytować swoją nazwę użytkownika i zmienić ją na właśnie dodaną domenę.

> [!NOTE]
> Jeśli nie używasz licencji programu Exchange, nie możesz używać domeny do wysyłania lub odbierania wiadomości e-mail z dzierżawy platformy Microsoft 365.
  
## <a name="related-content"></a>Zawartość pokrewna

[Kupowanie domeny niestandardowej przy użyciu platformy Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (artykuł)\
[Zarządzanie domenami](/admin) (strona linku)\
[Domeny — często zadawane pytania](../setup/domains-faq.yml) (artykuł)