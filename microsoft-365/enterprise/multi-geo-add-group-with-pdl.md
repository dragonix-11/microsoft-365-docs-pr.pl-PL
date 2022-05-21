---
title: Tworzenie grupy Microsoft 365 z określoną preferowaną lokalizacją danych
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
description: Dowiedz się, jak utworzyć grupę Microsoft 365 z określoną preferowaną lokalizacją danych w środowisku z wieloma lokalizacjami geograficznymi.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 162f499a783c23ec45ec75610833c61978beaafb
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623381"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Tworzenie grupy Microsoft 365 z określoną preferowaną lokalizacją danych

Gdy użytkownicy w środowisku z wieloma obszarami geograficznymi tworzą grupę Microsoft 365, preferowana lokalizacja danych grupy (PDL) jest automatycznie ustawiana na lokalizację użytkownika. Administratorzy globalni, SharePoint i Exchange mogą tworzyć grupy w dowolnym wybranym regionie. 

Jeśli musisz utworzyć grupę z określonym plikiem PDL, możesz to zrobić za pomocą <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnego SharePoint</a> lub za pośrednictwem polecenia cmdlet programu Microsoft PowerShell Exchange Online New-UnifiedGroup. W takim przypadku zarówno skrzynka pocztowa grupy, jak i witryna SharePoint skojarzona z grupą zostaną aprowizowane w określonym pliku PDL.

Aby utworzyć grupę Microsoft 365 przy użyciu określonego pliku PDL, przejdź do <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnego SharePoint</a> w lokalizacji geograficznej, w której chcesz utworzyć witrynę grupy.

Przykład:

Jeśli chcesz utworzyć witrynę grupy w swojej lokalizacji w Australii, możesz przejść do https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Wybierz pozycję **+ Utwórz**.
2. Postępuj zgodnie z procesem, aby utworzyć witrynę grupy.

Witryna grupy zostanie aprowizowana w lokalizacji geograficznej odpowiadającej centrum administracyjnemu SharePoint, z którego zainicjowano żądanie utworzenia witryny. 

Korzystanie z programu Exchange PowerShell 

Połączenie Exchange Online programu PowerShell i przekazać parametr *-MailBoxRegion* przy użyciu kodu lokalizacji geograficznej.

Przykład: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Zrzut ekranu przedstawiający New-UnifiedGroup polecenia cmdlet programu PowerShell ze składnią.](../media/multi-geo-new-group-with-pdl-powershell.png)

> [!Note]
> SharePoint aprowizowanie lokacji grupy jest na żądanie. Witryna zostanie aprowizowana przy pierwszej próbie uzyskania dostępu do niej przez właściciela lub członka grupy.

## <a name="geo-location-codes"></a>Kody lokalizacji geograficznej

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Tematy pokrewne

[Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[Tworzenie grup z określoną preferowaną lokalizacją danych przy użyciu interfejs Graph API](/graph/api/group-post-groups)
