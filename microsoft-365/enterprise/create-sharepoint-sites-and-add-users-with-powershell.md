---
title: Tworzenie witryn usługi SharePoint Online i dodawanie użytkowników za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Użyj programu PowerShell, aby utworzyć nowe witryny usługi SharePoint Online, a następnie dodać użytkowników i grupy do tych witryn.'
ms.openlocfilehash: 9d99f98825d88e2d2e63f106a7b5704c773c8be1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101342"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>Tworzenie witryn usługi SharePoint Online i dodawanie użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli używasz programu PowerShell do Microsoft 365 do tworzenia witryn SharePoint Online i dodawania użytkowników, możesz szybko i wielokrotnie wykonywać zadania znacznie szybciej niż w Centrum administracyjne platformy Microsoft 365. Można również wykonywać zadania, które nie są możliwe do wykonania w Centrum administracyjne platformy Microsoft 365.

## <a name="connect-to-sharepoint-online"></a>Połączenie do SharePoint Online

Procedury opisane w tym temacie wymagają nawiązania połączenia z usługą SharePoint Online. Aby uzyskać instrukcje, zobacz [Połączenie to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>Krok 1. Tworzenie nowych zbiorów witryn przy użyciu programu PowerShell

Utwórz wiele lokacji przy użyciu programu PowerShell i pliku .csv utworzonego przy użyciu przykładowego kodu dostarczonego i Notatnik. W tej procedurze zastąpisz informacje zastępcze wyświetlane w nawiasach kwadratowych własnymi informacjami dotyczącymi lokacji i dzierżawy. Ten proces umożliwia utworzenie pojedynczego pliku i uruchomienie pojedynczego polecenia programu PowerShell, które używa tego pliku. Dzięki temu akcje podejmowane zarówno w trybie powtarzalnym, jak i przenośnym eliminują wiele, jeśli nie wszystkie, błędów, które mogą pochodzić z wpisywania długich poleceń w powłoce zarządzania usługi SharePoint Online. Procedura ta składa się z dwóch części. Najpierw utworzysz plik .csv, a następnie odwołasz się do tego pliku .csv przy użyciu programu PowerShell, który będzie używać jego zawartości do tworzenia witryn.

Polecenie cmdlet programu PowerShell importuje plik .csv i tworzy potoki do pętli wewnątrz nawiasów klamrowych, która odczytuje pierwszy wiersz pliku jako nagłówki kolumn. Następnie polecenie cmdlet programu PowerShell przechodzi przez pozostałe rekordy, tworzy nowy zbiór witryn dla każdego rekordu i przypisuje właściwości zbioru witryn zgodnie z nagłówkami kolumn.

### <a name="create-a-csv-file"></a>Tworzenie pliku .csv

> [!NOTE]
> Parametr przydziału zasobów działa tylko w lokacjach klasycznych. Jeśli używasz tego parametru w nowoczesnej witrynie, może zostać wyświetlony komunikat ostrzegawczy, że został on przestarzały.

1. Otwórz Notatnik i wklej do niego następujący blok tekstowy:

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   Gdzie *dzierżawa* jest nazwą dzierżawy, a *właściciel* to nazwa użytkownika w dzierżawie, któremu chcesz przyznać rolę administratora podstawowego zbioru witryn.

   (Możesz nacisnąć klawisze Ctrl+H, gdy używasz Notatnik, aby szybciej zastępować zbiorczo).

2. Zapisz plik na pulpicie jako **SiteCollections.csv**.

> [!TIP]
> Przed użyciem tego lub innego pliku skryptu .csv lub Windows PowerShell dobrym rozwiązaniem jest upewnienie się, że nie ma żadnych dodatkowych ani niedrukowalnych znaków. Otwórz plik w programie Word i na wstążce kliknij ikonę akapitu, aby wyświetlić znaki niedrukowujące. Nie powinno być żadnych dodatkowych znaków niedrukowalnych. Na przykład nie powinno być żadnych znaków akapitu poza ostatnim na końcu pliku.

### <a name="run-the-windows-powershell-command"></a>Uruchom polecenie Windows PowerShell

1. W wierszu Windows PowerShell wpisz lub skopiuj i wklej następujące polecenie, a następnie naciśnij klawisz Enter:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   Gdzie *MyAlias* jest równa aliasowi użytkownika.

2. Zaczekaj na ponowne wyświetlenie monitu Windows PowerShell. Może to potrwać minutę lub dwie.

3. W wierszu Windows PowerShell wpisz lub skopiuj i wklej następujące polecenie cmdlet, a następnie naciśnij klawisz Enter:

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. Zanotuj nowe zbiory witryn na liście. Korzystając z naszego przykładowego pliku CSV, zobaczysz następujące zbiory witryn: **TeamSite01**, **Blog01**, **Project01** i **Community01**

To wszystko. Utworzono wiele zbiorów witryn przy użyciu utworzonego pliku .csv i pojedynczego polecenia Windows PowerShell. Teraz możesz tworzyć i przypisywać użytkowników do tych witryn.

## <a name="step-2-add-users-and-groups"></a>Krok 2. Dodawanie użytkowników i grup

Teraz utworzysz użytkowników i dodasz ich do grupy zbiorów witryn. Następnie użyjesz pliku .csv, aby zbiorczo przekazać nowe grupy i użytkowników.

Poniższe procedury nadal korzystają z przykładowych witryn TeamSite01, Blog01, Project01 i Community01.

### <a name="create-csv-and-ps1-files"></a>Tworzenie plików .csv i .ps1

1. Otwórz Notatnik i wklej do niego następujący blok tekstowy:

   ```powershell
   Site,Group,PermissionLevels
   https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
   https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
   https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
   https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
   ```

   Gdzie *dzierżawa* jest równa nazwie dzierżawy.

2. Zapisz plik na pulpicie jako **GroupsAndPermissions.csv**.

3. Otwórz nowe wystąpienie Notatnik i wklej do niego następujący blok tekstowy:

   ```powershell
   Group,LoginName,Site
   Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
   ```

   Gdzie *dzierżawa* jest równa nazwie dzierżawy, a *nazwa użytkownika* jest równa nazwie użytkownika istniejącego użytkownika.

4. Zapisz plik na pulpicie jako **Users.csv**.

5. Otwórz nowe wystąpienie Notatnik i wklej do niego następujący blok tekstowy:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   Gdzie MyAlias jest równa nazwy użytkownika, który jest obecnie zalogowany.

6. Zapisz plik na pulpicie jako **UsersAndGroups.ps1**. Jest to prosty skrypt Windows PowerShell.

Teraz możesz uruchomić skrypt UsersAndGroup.ps1, aby dodać użytkowników i grupy do wielu zbiorów witryn.

### <a name="run-usersandgroupsps1-script"></a>Uruchamianie skryptu UsersAndGroups.ps1

1. Wróć do powłoki zarządzania SharePoint Online.

2. W wierszu Windows PowerShell wpisz lub skopiuj i wklej następujący wiersz, a następnie naciśnij klawisz Enter:

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. W wierszu potwierdzenia naciśnij **klawisz Y**.

4. W wierszu Windows PowerShell wpisz lub skopiuj i wklej następujące polecenie, a następnie naciśnij klawisz Enter:

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   Gdzie *MyAlias* jest równa twojej nazwie użytkownika.

5. Zaczekaj na powrót monitu przed przejściem dalej. Najpierw zobaczysz, że grupy są wyświetlane podczas ich tworzenia. Następnie zobaczysz, że lista grup jest powtarzana w miarę dodawania użytkowników.

## <a name="see-also"></a>Zobacz też

[Połączenie do programu PowerShell SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Zarządzanie grupami witryn usługi SharePoint Online przy użyciu programu PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
