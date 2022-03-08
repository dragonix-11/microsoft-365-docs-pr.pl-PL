---
title: Zarządzanie SharePoint witryny usługi Online za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: W tym artykule znajdziesz procedury dotyczące korzystania z programu PowerShell na Microsoft 365 zarządzania grupami witryn SharePoint online.
ms.openlocfilehash: deef41118789a9df4353fa188c88d827909dc863
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328781"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>Zarządzanie SharePoint witryny usługi Online za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Mimo że można używać programu centrum administracyjne platformy Microsoft 365, można też zarządzać grupami witryn usługi SharePoint Online za pomocą Microsoft 365 programu PowerShell.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Procedury procedury w tym artykule wymagają nawiązania połączenia z usługą SharePoint Online. Aby uzyskać instrukcje, [Połączenie aby SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Wyświetlanie SharePoint Online za pomocą programu PowerShell dla Microsoft 365

Centrum SharePoint online ma kilka łatwych w użyciu metod zarządzania grupami witryn. Załóżmy na przykład, że chcesz zajrzeć do grup i członków grupy w `https://litwareinc.sharepoint.com/sites/finance` witrynie. Oto, co należy zrobić:

1. W centrum SharePoint wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>, a następnie wybierz adres URL witryny.
2. Na stronie witryny wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**Ustawienia**</a> (znajduje się w prawym górnym rogu strony), a następnie wybierz pozycję **Uprawnienia witryny**.

Następnie powtórz proces dla następnej witryny, którą chcesz zobaczyć.

Aby uzyskać listę grup za pomocą programu PowerShell dla programu Microsoft 365, możesz użyć następujących poleceń:

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Istnieją dwa sposoby uruchamiania tego zestawu poleceń w wierszu SharePoint powłoki zarządzania online:

- Skopiuj polecenia do Notatnik (lub innego edytora tekstu), zmodyfikuj wartość zmiennej $siteURL, zaznacz polecenia, **a** następnie wklej je do wiersza polecenia powłoki zarządzania usługi SharePoint Online. Gdy to zrobisz, program PowerShell zatrzyma się na wierszu **>>** polecenia. Naciśnij klawisz Enter, aby wykonać `foreach` polecenie.<br/>
- Skopiuj polecenia do Notatnik (lub innego edytora tekstu), zmodyfikuj wartość zmiennej **$siteURL, a** następnie zapisz ten plik tekstowy z nazwą i rozszerzeniem .ps1 w odpowiednim folderze. Następnie uruchom skrypt z wiersza polecenia SharePoint powłoki zarządzania online, określając ścieżkę i nazwę pliku. Oto przykładowe polecenie:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

W obu przypadkach powinien zostać wyświetlony podobny do tego:

![SharePoint witryny online.](../media/SPO-site-groups.png)

Są to wszystkie grupy, które zostały utworzone dla `https://litwareinc.sharepoint.com/sites/finance`witryny, i wszyscy użytkownicy przypisani do tych grup. Nazwy grup są żółte, co pomaga oddzielić nazwy grup od ich członków.

Kolejny przykład to zestaw poleceń, który zawiera listę grup i wszystkich członków grup, we wszystkich witrynach w SharePoint Online.

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```

## <a name="see-also"></a>Zobacz też

[Połączenie do SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Tworzenie SharePoint Online i dodawanie użytkowników za pomocą programu PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Zarządzanie użytkownikami SharePoint Online i grupami za pomocą programu PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
