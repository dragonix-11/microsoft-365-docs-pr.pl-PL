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
description: Dowiedz się, jak utworzyć Microsoft 365 z określoną preferowaną lokalizacją danych w środowisku wielolokalizacji.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6ce4ed337b07206e6508a5955edc2c264586df4b
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995954"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Tworzenie grupy Microsoft 365 z określoną preferowaną lokalizacją danych

Gdy użytkownicy w środowisku z wieloma lokalizacjami geograficznymi tworzą grupę usługi Microsoft 365, preferowana lokalizacja danych grupy (PDL) jest automatycznie ustawiana na preferowaną lokalizację danych użytkownika. Administratorzy globalni, SharePoint i Exchange mogą tworzyć grupy w dowolnym wybranej przez nich regionie. 

Jeśli chcesz utworzyć grupę o określonej wersji pliku PDL, możesz to zrobić z centrum administracyjnego programu SharePoint lub za pomocą polecenia cmdlet programu Exchange Online New-UnifiedGroup Microsoft PowerShell. W takim przypadku zarówno skrzynka pocztowa grupy, jak i witryna SharePoint skojarzona z grupą zostaną zapewnienia obsługi administracyjnej w określonym pliku PDL.

Aby utworzyć grupę Microsoft 365 o  określony plik PDL, przejdź do centrum administracyjnego usługi SharePoint w lokalizacji geograficznej, w której chcesz utworzyć witrynę grupy.

Przykład:

Jeśli chcesz utworzyć witrynę grupy w lokalizacji Australii, możesz przejść do pozycji https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Wybierz **pozycję + Utwórz**.
2. Postępuj zgodnie z procesem tworzenia witryny grupy.

Witryna grupy będzie inicjowana w lokalizacji geograficznej odpowiadającej centrum administracyjnego usługi SharePoint, z którego zainicjowano żądanie utworzenia witryny. 

Używanie Exchange PowerShell 

Połączenie aby Exchange Online PowerShell i przekazać parametr *-MailBoxRegion* kodem lokalizacji geograficznej.

Przykład: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Zrzut ekranu przedstawiający New-UnifiedGroup cmdlet programu PowerShell ze składnią.](../media/multi-geo-new-group-with-pdl-powershell.png)

Pamiętaj, SharePoint obsługi administracyjnej witryny grupy jest na żądanie. Witryna zostanie aprowowana przy pierwszej próbie uzyskania dostępu przez właściciela lub członka grupy.

## <a name="geo-location-codes"></a>Kody lokalizacji geograficznej

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Tematy pokrewne

[Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[Tworzenie grup z określoną preferowaną lokalizacją danych przy użyciu Graph API](/graph/api/group-post-groups)
