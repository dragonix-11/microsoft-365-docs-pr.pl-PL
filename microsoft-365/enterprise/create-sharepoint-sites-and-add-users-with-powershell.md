---
title: Tworzenie SharePoint Online i dodawanie użytkowników za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Podsumowanie: Za pomocą programu PowerShell możesz tworzyć SharePoint witryny online, a następnie dodawać do nich użytkowników i grupy.'
ms.openlocfilehash: 76411621c0c313a31e4c92417b4472d6fd34ddac
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977633"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>Tworzenie SharePoint Online i dodawanie użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Gdy używasz programu PowerShell dla programu Microsoft 365 do tworzenia witryn usługi SharePoint Online i dodawania użytkowników, możesz szybko i wielokrotnie wykonywać zadania znacznie szybciej niż w aplikacji centrum administracyjne platformy Microsoft 365. Można również wykonywać zadania, których nie można wykonać w centrum administracyjne platformy Microsoft 365.

## <a name="connect-to-sharepoint-online"></a>Połączenie do usługi SharePoint Online

Procedury w tym temacie wymagają nawiązania połączenia z usługą SharePoint Online. Aby uzyskać instrukcje, [Połączenie do SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>Krok 1. Tworzenie nowych zbiorów witryn przy użyciu programu PowerShell

Za pomocą programu PowerShell i pliku .csv utwórz wiele witryn, używając podanego i Notatnik. W tej procedurze zastąpisz informacje zastępcze wyświetlane w nawiasach kwadratowych własnymi informacjami o witrynie i dzierżawie. Ten proces umożliwia utworzenie jednego pliku i uruchomienie pojedynczego polecenia programu PowerShell, które używa tego pliku. Dzięki temu akcje wykonane zarówno powtarzalne, jak i przenośne, oraz eliminuje wiele (o ile nie wszystkie) błędy, które mogą wynikać z wpisywania długich poleceń w SharePoint powłoki zarządzania online. Ta procedura ma dwa elementy. Najpierw utworzysz plik .csv, a następnie odwołzesz się do tego pliku przy .csv PowerShell, który użyje jego zawartości do tworzenia witryn.

Polecenie cmdlet programu PowerShell importuje plik .csv i potoki, do pętli wewnątrz nawiasów klamrowych, która odczytuje pierwszy wiersz pliku jako nagłówki kolumn. Następnie polecenie cmdlet programu PowerShell tworzy iteracyjne w pozostałych rekordach, tworzy nowy zbiór witryn dla każdego rekordu i przypisuje właściwości zbioru witryn zgodnie z nagłówkami kolumn.

### <a name="create-a-csv-file"></a>Tworzenie .csv pliku

> [!NOTE]
> Parametr przydziału zasobów działa tylko w witrynach klasycznych. Jeśli używasz tego parametru w nowoczesnej witrynie, może zostać wyświetlony komunikat ostrzegawczy z ostrzeżeniem, że został on przestarzały.

1. Otwórz Notatnik i wklej do niego następujący blok tekstu:

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   Gdzie *dzierżawa* to nazwa Twojej dzierżawy, a  właściciel to nazwa użytkownika w Twojej dzierżawie, któremu chcesz przyznać rolę podstawowego administratora zbioru witryn.

   (Gdy użyjemy klawiszy Ctrl+H, Notatnik szybko zamienić zbiorczo).

2. Zapisz plik na pulpicie jako **SiteCollections.csv**.

> [!TIP]
> Przed użyciem tego lub dowolnego innego pliku skryptu programu .csv lub Windows PowerShell warto upewnić się, że nie ma żadnych niepotrzebnych ani niedrukowych znaków. Otwórz plik w programie Word i na wstążce kliknij ikonę akapitu, aby wyświetlić znaki niedrukujące. Nie powinno być dodatkowych znaków niedrukowany. Na przykład na końcu pliku nie powinny być znaczniki akapitu za znacznikiem akapitu.

### <a name="run-the-windows-powershell-command"></a>Uruchamianie Windows PowerShell wiersza

1. W wierszu Windows PowerShell wpisz lub skopiuj i wklej następujące polecenie, a następnie naciśnij klawisz Enter:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   Gdzie *Wartości MyAlias* są równe aliasowi użytkownika.

2. Poczekaj, aż Windows PowerShell monit o ponowne pojawienie się. Może to potrwać minutę lub dwie.

3. W wierszu Windows PowerShell wpisz lub skopiuj i wklej następujące polecenie cmdlet, a następnie naciśnij klawisz Enter:

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. Zwróć uwagę na nowe zbiory witryn na liście. W przykładowym pliku CSV zobaczysz następujące zbiory witryn: **TeamSite01**, **Blog01**, **Project01** i **Community01**.

To wszystko. Utworzono wiele zbiorów witryn przy użyciu utworzonego .csv pliku i jednego Windows PowerShell polecenia. Teraz możesz tworzyć i przypisywać użytkowników do tych witryn.

## <a name="step-2-add-users-and-groups"></a>Krok 2. Dodawanie użytkowników i grup

Teraz utworzysz użytkowników i dodasz ich do grupy zbioru witryn. Następnie użyjemy pliku .csv w celu zbiorczego przekazania nowych grup i użytkowników.

Poniższe procedury kontynuują korzystanie z przykładowych witryn TeamSite01, Blog01, Project01 i Community01.

### <a name="create-csv-and-ps1-files"></a>Tworzenie .csv i .ps1 plików

1. Otwórz Notatnik i wklej do niego następujący blok tekstu:

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

   Gdzie *dzierżawa* jest równa nazwie Twojej dzierżawy.

2. Zapisz plik na pulpicie jako **plikGroupsAndPermissions.csv**.

3. Otwórz nowe wystąpienie tekstu Notatnik i wklej do niego następujący blok tekstu:

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

   Tam *, gdzie dzierżawa* jest równa twojej nazwie dzierżawy, a *nazwa* użytkownika to nazwa użytkownika istniejącego użytkownika.

4. Zapisz plik na pulpicie jako **plikUsers.csv**.

5. Otwórz nowe wystąpienie tekstu Notatnik i wklej do niego następujący blok tekstu:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   Gdzie MyAlias jest równa nazwie użytkownika, który jest obecnie zalogowany.

6. Zapisz plik na pulpicie jako **plikUsersAndGroups.ps1**. Jest to prosty Windows PowerShell skryptu.

Teraz możesz uruchomić skrypt skryptów UsersAndGroup.ps1 dodawania użytkowników i grup do wielu zbiorów witryn.

### <a name="run-usersandgroupsps1-script"></a>Uruchamianie UsersAndGroups.ps1 skryptu

1. Powróć do SharePoint zarządzania usługi Online.

2. W wierszu Windows PowerShell wpisz lub skopiuj i wklej następujący wiersz, a następnie naciśnij klawisz Enter:

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. W wierszu potwierdzenia naciśnij klawisz **Y**.

4. Po wyświetleniu Windows PowerShell wpisz lub skopiuj i wklej następujące polecenie, a następnie naciśnij klawisz Enter:

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   Gdzie *MyAlias* równa się Twojej nazwie użytkownika.

5. Przed przejściem dalej poczekaj, aż zostanie wyświetlony monit o powrót. Grupy będą najpierw wyświetlane podczas ich tworzenia. Następnie lista grup będzie powtarzana po dodaniu użytkowników.

## <a name="see-also"></a>Zobacz też

[Połączenie do SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Zarządzanie SharePoint witryny usługi Online za pomocą programu PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
