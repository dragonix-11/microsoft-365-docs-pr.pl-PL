---
title: Ograniczanie SharePoint witryny do lokalizacji geograficznej
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: W tym artykule dowiesz się, jak ograniczyć witryny SharePoint do określonej lokalizacji geograficznej w środowisku wielowymiarowym.
ms.openlocfilehash: 06401658afe9f6a26b1280f5931ba6b3ba761742
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983306"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Ograniczanie SharePoint witryny do lokalizacji geograficznej

W pewnych okolicznościach można wymusić, aby witryna i jej zawartość plików pozostawały w lokalizacji geograficznej, w której została utworzona, uniemożliwiając jej lokalizację geograficzną lub uniemożliwiając buforowanie zawartości plików witryny w innej lokalizacji geograficznej.

Możesz to zrobić, używając polecenia cmdlet [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) z parametrem **RestrictedToGeo** . Ten parametr ma wartość domyślną NULL, ale można go zmienić na jeden z następujących:

|Ograniczenie|Opis|
|:----------|:----------|
|NoRestriction|Witrynę można przenieść do innej lokalizacji geograficznej.|
|BlockMoveOnly|Witryny nie można przenosić do innej lokalizacji geograficznej, ale zawartość witryny może być buforowana w innych lokalizacjach geograficznych.|
|BlockFull|Witryny nie można przenosić do innej lokalizacji geograficznej, a pełna zawartość pliku nie jest buforowana w innych lokalizacjach geograficznych. Tytuły plików (zebrane z zawartości), nazwa pliku i inne właściwości pliku nadal mogą być przechowywane w pamięci podręcznej w innych lokalizacjach geograficznych.<br>Zawartość przechowywana w witrynie przed jej skonfigurowaniem do blockfull może być nadal przechowywana w pamięci podręcznej w innych lokalizacjach geograficznych.|

Należy stosować następującą składnię:

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Przykład:

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`