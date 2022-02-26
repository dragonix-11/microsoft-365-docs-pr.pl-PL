---
title: Dodawanie lub usuwanie administratora geolokalizacji
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Musisz skonfigurować osobnych administratorów dla poszczególnych lokalizacji geograficznych? Dowiedz się, jak dodać lub usunąć administratora geolokalizacji w Microsoft 365 wielu lokalizacji geograficznych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e661e42759fe0b035bfe97c33165f78316973403
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973785"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a>Dodawanie lub usuwanie administratora geolokalizacji w Microsoft 365 wielu lokalizacji geograficznych

Dla każdej lokalizacji geograficznej posiadanych w dzierżawie możesz skonfigurować osobnych administratorów. Ci administratorzy będą mieli dostęp do ustawień usługi SharePoint Online i OneDrive, które są specyficzne dla ich lokalizacji geograficznej.

Niektóre usługi , takie jak magazyn terminów, są administrowane z lokalizacji centralnej i replikowane do lokalizacji satelitarnych. Administrator geolokalizacji lokalizacji centralnej ma do nich dostęp, natomiast administratorzy geolokalizacji lokalizacji satelitarnych ich nie mają.

Administratorzy globalni i administratorzy usługi SharePoint Online nadal mają dostęp do ustawień w lokalizacji centralnej i we wszystkich lokalizacjach satelitarnych.

## <a name="configuring-geo-administrators"></a>Konfigurowanie administratorów lokalizacji geograficznej

Konfigurowanie administratorów geograficznych wymaga SharePoint PowerShell online.

Usługa [Połączenie-SPOService](/powershell/module/sharepoint-online/Connect-SPOService) umożliwia połączenie się z centrum administracyjnym lokalizacji geograficznej, w którym chcesz dodać administratora geolokalizacji. (Na przykład: Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Aby wyświetlić istniejących administratorów geograficznych lokalizacji, uruchom `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Dodawanie użytkownika jako administratora geolokalizacji

Aby dodać użytkownika jako administratora geolokalizacji, uruchom `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Aby usunąć użytkownika jako administratora geolokalizacji lokalizacji, uruchom  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Dodawanie grupy jako administratora geolokalizacji

Możesz dodać grupę zabezpieczeń lub grupę zabezpieczeń z obsługą poczty jako administratora geolokalizacji. (Grupy dystrybucyjne i grupy Microsoft 365 nie są obsługiwane).

Aby dodać grupę jako administratora geolokalizacji, uruchom `Add-SPOGeoAdministrator -GroupAlias <alias>`

Aby usunąć grupę jako administrator lokalizacji geograficznej, uruchom `Remove-SPOGeoAdministrator -GroupAlias <alias>`

Pamiętaj, że nie wszystkie grupy zabezpieczeń mają alias grupy. Jeśli chcesz dodać grupę zabezpieczeń, która nie ma aliasu, uruchom pozycję [Get-MsolGroup](/powershell/module/msonline/get-msolgroup) , aby pobrać listę grup, znajdź identyfikator ObjectID tej grupy zabezpieczeń, a następnie uruchom ją:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Aby usunąć grupę przy użyciu identyfikatorów ObjectID, uruchom `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="related-topics"></a>Tematy pokrewne

[Add-SPOGeoAdministrator](/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Ustawianie aliasu (MailNickName) dla grupy zabezpieczeń](/powershell/module/azuread/set-azureadgroup)