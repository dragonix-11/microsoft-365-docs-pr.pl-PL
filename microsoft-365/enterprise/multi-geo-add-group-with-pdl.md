---
title: Tworzenie grupy platformy Microsoft 365 z określoną preferowaną lokalizacją danych
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: Dowiedz się, jak utworzyć grupę platformy Microsoft 365 z określoną preferowaną lokalizacją danych w środowisku z wieloma lokalizacjami geograficznymi.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: ff9b6ae6949ab1e6af1ee102abfcf2cb132fed9f
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940717"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Tworzenie grupy platformy Microsoft 365 z określoną preferowaną lokalizacją danych

Gdy użytkownicy w środowisku z wieloma lokalizacjami geograficznymi tworzą grupę platformy Microsoft 365, preferowana lokalizacja danych grupy (PDL) jest automatycznie ustawiana na lokalizację użytkownika. Administratorzy globalni, programu SharePoint i programu Exchange mogą tworzyć grupy w dowolnym wybranym regionie. 

Jeśli musisz utworzyć grupę z określonym plikiem PDL, możesz to zrobić za pomocą <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnego programu SharePoint</a> lub za pośrednictwem polecenia cmdlet programu Microsoft PowerShell usługi Exchange Online New-UnifiedGroup. W takim przypadku zarówno skrzynka pocztowa grupy, jak i witryna programu SharePoint skojarzona z grupą zostaną aprowizowane w określonym pliku PDL.

Aby utworzyć grupę platformy Microsoft 365 z określonym plikiem PDL, przejdź do <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnego programu SharePoint</a> w lokalizacji geograficznej, w której chcesz utworzyć witrynę grupy.

Przykład:

Jeśli chcesz utworzyć witrynę grupy w swojej lokalizacji w Australii, możesz przejść do `https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement`

1. Wybierz pozycję **+ Utwórz**.
2. Postępuj zgodnie z procesem, aby utworzyć witrynę grupy.

Witryna grupy zostanie zainicjowana w lokalizacji geograficznej odpowiadającej centrum administracyjnemu programu SharePoint, z którego zainicjowano żądanie utworzenia witryny. 

Korzystanie z programu Exchange PowerShell 

Połącz się z programem PowerShell usługi Exchange Online i przekaż parametr *-MailBoxRegion* przy użyciu kodu lokalizacji geograficznej.

Przykład: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Zrzut ekranu przedstawiający New-UnifiedGroup polecenia cmdlet programu PowerShell ze składnią.](../media/multi-geo-new-group-with-pdl-powershell.png)

> [!Note]
> Aprowizowanie witryny grupy programu SharePoint odbywa się na żądanie. Witryna zostanie aprowizowana przy pierwszej próbie uzyskania dostępu do niej przez właściciela lub członka grupy.

## <a name="geo-location-codes"></a>Kody lokalizacji geograficznej

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Tematy pokrewne

[Nawiązywanie połączenia z programem PowerShell usługi Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell)

[Tworzenie grup z określoną preferowaną lokalizacją danych przy użyciu interfejsu API programu Graph](/graph/api/group-post-groups)
