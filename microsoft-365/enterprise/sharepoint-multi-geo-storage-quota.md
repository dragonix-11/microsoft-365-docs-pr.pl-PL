---
title: SharePoint przydziałów magazynowania w środowiskach wielowymiarowych
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
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Dowiedz się SharePoint przydziałów magazynowania w środowiskach wielowymiarowych i o tym, jak administrator usługi SharePoint Online może zarządzać przydziałami.
ms.openlocfilehash: d1e47c206f1353093ba8bebf9db03ab7142d6da9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984449"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>SharePoint przydziałów magazynowania w środowiskach wielowymiarowych

Domyślnie wszystkie lokalizacje geograficzne środowiska wielowymiarowego mają współużytowany przydział magazynowania dzierżawy.

Przy użyciu SharePoint przydziału magazynowania geolokalizacji możesz zarządzać przydziałem magazynowania dla każdej lokalizacji geograficznej. Przydzielanie przydziału miejsca do magazynowania dla lokalizacji geograficznej staje się maksymalną ilością miejsca do magazynowania dostępną dla tej lokalizacji geograficznej i odejmowana od dostępnego przydziału miejsca do magazynowania dzierżawy. Pozostały dostępny przydział miejsca do magazynowania dzierżawy jest następnie współużytowany w skonfigurowanych lokalizacjach geograficznych, dla których nie przydzielono określonego przydziału magazynowania.

Przydział SharePoint miejsca do magazynowania dla dowolnej lokalizacji geograficznej może zostać przydzielony przez administratora usługi SharePoint online przez połączenie z lokalizacją centralną. Administratorzy geolokalizacji lokalizacji satelitarnych mogą wyświetlać przydział magazynowania, ale nie mogą go przydzielić.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>Konfigurowanie przydziału miejsca do magazynowania dla lokalizacji geograficznej

Użyj modułu [Microsoft Office SharePoint Online i połącz](https://www.microsoft.com/download/details.aspx?id=35588) się z centralną lokalizacją, aby przydzielić przydział magazynowania dla lokalizacji geograficznej.

Aby przydzielić Storage przydziału dla lokalizacji, uruchom polecenie cmdlet:

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>
```

Aby wyświetlić Storage dla bieżącej lokalizacji geograficznej, uruchom:

```powershell
Get-SPOGeoStorageQuota
```

![Zrzut ekranu przedstawiający okno programu PowerShell Get-SPOGeoStorageQuota polecenie cmdlet.](../media/multi-geo-storage-quota.png)

Aby wyświetlić Storage dla wszystkich lokalizacji geograficznych, uruchom:

```powershell
Get-SPOGeoStorageQuota -AllLocations
```

Aby usunąć przydział miejsca do magazynowania przydzielony dla lokalizacji geograficznej, ustaw:`StorageQuota value = 0`

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0
```
