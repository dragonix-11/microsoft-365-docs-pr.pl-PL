---
title: Zarządzanie grupami witryn usługi SharePoint Online przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/17/2019
audience: Admin
ms.topic: landing-page
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
description: W tym artykule znajdziesz procedury dotyczące używania programu PowerShell dla Microsoft 365 do zarządzania grupami witryn usługi SharePoint Online.
ms.openlocfilehash: 411ab477668b7956a63843d0b58b8d6d9bfc9059
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096441"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>Zarządzanie grupami witryn usługi SharePoint Online przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Mimo że możesz użyć Centrum administracyjne platformy Microsoft 365, możesz również użyć programu PowerShell do Microsoft 365 do zarządzania grupami witryn usługi SharePoint Online.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Procedury opisane w tym artykule wymagają nawiązania połączenia z usługą SharePoint Online. Aby uzyskać instrukcje, zobacz [Połączenie do programu PowerShell SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Wyświetlanie SharePoint Online za pomocą programu PowerShell dla Microsoft 365

Centrum administracyjne usługi SharePoint Online ma kilka łatwych w użyciu metod zarządzania grupami witryn. Załóżmy na przykład, że chcesz przyjrzeć się grupom i członkom grupy dla `https://litwareinc.sharepoint.com/sites/finance` witryny. Oto, co musisz zrobić:

1. W centrum administracyjnym SharePoint wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>, a następnie wybierz adres URL witryny.
2. Na stronie witryny wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**Ustawienia**</a> (znajduje się w prawym górnym rogu strony), a następnie wybierz pozycję **Uprawnienia witryny**.

A następnie powtórz proces dla następnej witryny, na którą chcesz spojrzeć.

Aby uzyskać listę grup za pomocą programu PowerShell dla Microsoft 365, możesz użyć następujących poleceń:

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

Istnieją dwa sposoby uruchamiania tego zestawu poleceń w wierszu polecenia usługi SharePoint Online Management Shell:

- Skopiuj polecenia do Notatnik (lub innego edytora tekstów), zmodyfikuj wartość zmiennej **$siteURL**, wybierz polecenia, a następnie wklej je w wierszu polecenia powłoki zarządzania usługi SharePoint Online. Gdy to zrobisz, program PowerShell zatrzyma się w wierszu **>>** polecenia. Naciśnij klawisz Enter, aby wykonać `foreach` polecenie.<br/>
- Skopiuj polecenia do Notatnik (lub innego edytora tekstu), zmodyfikuj wartość zmiennej **$siteURL**, a następnie zapisz ten plik tekstowy z nazwą i rozszerzeniem .ps1 w odpowiednim folderze. Następnie uruchom skrypt w wierszu polecenia usługi SharePoint Online Management Shell, określając jego ścieżkę i nazwę pliku. Oto przykładowe polecenie:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

W obu przypadkach powinno zostać wyświetlone coś podobnego do następującego:

![SharePoint Grupy witryn online.](../media/SPO-site-groups.png)

Są to wszystkie grupy utworzone dla witryny `https://litwareinc.sharepoint.com/sites/finance`i wszyscy użytkownicy przypisani do tych grup. Nazwy grup są żółte, aby ułatwić oddzielenie nazw grup od ich członków.

Innym przykładem jest zestaw poleceń, który wyświetla listę grup i wszystkie członkostwa w grupach dla wszystkich witryn usługi SharePoint Online.

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

[Połączenie do programu PowerShell SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Tworzenie witryn usługi SharePoint Online i dodawanie użytkowników za pomocą programu PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Zarządzanie użytkownikami i grupami usługi SharePoint Online przy użyciu programu PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
