---
title: Włączanie SharePoint Multi-Geo lokalizacji geograficznej satelitarnej
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
description: Ten artykuł zawiera informacje dla administratorów globalnych SharePoint administratorów o włączaniu SharePoint Multi-Geo lokalizacji geolokalizacji satelitarnych.
ms.openlocfilehash: b542c1ee77c7b4ca7a6179bac5ce5eaa1090606a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330443"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>Włączanie SharePoint Multi-Geo lokalizacji geograficznej satelitarnej

Ten artykuł jest dla administratorów globalnych lub administratorów programu SharePoint, którzy tworzyli lokalizację satelitarnej **usługi SharePoint Multi-Geo** Multi-Geo, zanim funkcje SharePoint Multi-Geo stały się ogólnie dostępne w dniu 27 marca 2019 r. i nie włączono usługi SharePoint Multi-Geo w ich lokalizacjach geograficznych satelitarnych. 

>[!Note]
>Jeśli po **27 marca 2019** r. dodano nową lokalizację geograficzną, nie trzeba wykonywać tych instrukcji, ponieważ nowa lokalizacja geograficzna będzie już włączona dla usług OneDrive i SharePoint Multi-Geo.

Te instrukcje pozwalają włączyć SharePoint lokalizacji satelitarnej, dzięki czemu użytkownicy korzystający z lokalizacji satelitarnej multi-Geo mogą korzystać zarówno z usług OneDrive, jak i SharePoint Multi-Geo usługi O365. 

>[!IMPORTANT]
>Pamiętaj, że jest to jednokierunkowe włączenie. Po skonfigurowaniu trybu usługi SPO nie będzie można przywrócić dzierżawy do trybu OneDrive trybu wielolokalizacji bez eskalacji dzięki pomocy technicznej. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>Aby ustawić lokalizację geograficzną w tryb usługi SPO

Aby ustawić lokalizację geograficzną w trybie usługi SPO, połącz się z lokalizacją geograficzną, którą chcesz ustawić w trybie usługi SPO:

1.    Otwieranie SharePoint zarządzania w trybie online 
2.    Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential
3.    Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience.](../media/Set-SPO-MultiGeo.jpg)
4.    Ta operacja trwa zwykle około godziny, podczas wykonywania różnych operacji publikowania w usłudze i ponownego oznaczania dzierżawy. Po co najmniej 1 godzinie wykonaj operację Get-SPOMultiGeoExperience.  Dzięki temu można sprawdzić, czy ta lokalizacja geograficzna jest w trybie usługi SPO.</br></br>
![Set-SPOMultiGeoExperience.](../media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>Niektóre pamięci podręczne w usłudze są aktualizowane co 24 godziny, dlatego może się okazać, że przez okres do 24 godzin geolokalizacji satelitarnej mogą okresowo działać tak, jakby nadal działało w trybie ODB. Nie powoduje to żadnych problemów technicznych. 
 
Dodatkowe informacje dotyczące SharePoint Multi-Geo można [znaleźć w aka.ms/sharepointmultigeo](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)


