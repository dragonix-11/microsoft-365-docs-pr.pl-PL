---
title: Zarządzanie użytkownikami i grupami usługi SharePoint Online przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
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
description: W tym artykule dowiesz się, jak używać programu PowerShell do Microsoft 365 do zarządzania użytkownikami, grupami i witrynami usługi SharePoint Online.
ms.openlocfilehash: 78c829e476c63e435d9543b3a4175cdbbccb76e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100682"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>Zarządzanie użytkownikami i grupami usługi SharePoint Online przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli jesteś administratorem usługi SharePoint Online, który współpracuje z dużymi listami kont użytkowników lub grup i chce łatwiej nimi zarządzać, możesz użyć programu PowerShell do Microsoft 365.

Przed rozpoczęciem procedury opisane w tym artykule wymagają nawiązania połączenia z usługą SharePoint Online. Aby uzyskać instrukcje, zobacz [Połączenie to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>Pobieranie listy witryn, grup i użytkowników

Zanim zaczniemy zarządzać użytkownikami i grupami, musisz uzyskać listy witryn, grup i użytkowników. Następnie możesz użyć tych informacji, aby zapoznać się z przykładem w tym artykule.

Pobierz listę witryn w dzierżawie za pomocą tego polecenia:

```powershell
Get-SPOSite
```

Pobierz listę grup w dzierżawie za pomocą tego polecenia:

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

Pobierz listę użytkowników w dzierżawie za pomocą tego polecenia:

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Dodawanie użytkownika do grupy Administratorzy zbioru witryn

Polecenie cmdlet służy `Set-SPOUser` do dodawania użytkownika do listy administratorów zbioru witryn w zbiorze witryn.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

Aby użyć tych poleceń, zastąp wszystkie elementy w cudzysłowie, w tym znaki < i >, prawidłowymi nazwami.

Na przykład ten zestaw poleceń dodaje opal Castillo (nazwa użytkownika opalc) do listy administratorów zbioru witryn w zbiorze witryn ContosoTest w dzierżawie firmy Contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

Możesz skopiować i wkleić te polecenia do Notatnik, zmienić wartości zmiennych dla $tenant, $site i $user na rzeczywiste wartości ze środowiska, a następnie wkleić je w oknie powłoki zarządzania usługi SharePoint Online, aby je uruchomić.

## <a name="add-a-user-to-other-site-collection-groups"></a>Dodawanie użytkownika do innych grup zbiorów witryn

W tym zadaniu użyjemy `Add-SPOUser` polecenia cmdlet, aby dodać użytkownika do grupy SharePoint w zbiorze witryn.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

Na przykład dodajmy Glen Rife (nazwa użytkownika glenr) do grupy Audytorzy w zbiorze witryn ContosoTest w dzierżawie contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Tworzenie grupy zbioru witryn

Polecenie cmdlet służy `New-SPOSiteGroup` do tworzenia nowej grupy SharePoint i dodawania jej do zbioru witryn.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

Właściwości grupy, takie jak poziomy uprawnień, można później zaktualizować przy użyciu `Set-SPOSiteGroup` polecenia cmdlet.

Na przykład dodajmy grupę Audytorzy z uprawnieniami Tylko widok do zbioru witryn contosotest w dzierżawie contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Usuwanie użytkowników z grupy

Czasami trzeba usunąć użytkownika z witryny, a nawet wszystkich witryn. Być może pracownik przenosi się z jednego działu do drugiego lub opuszcza firmę. Możesz to zrobić dla jednego pracownika łatwo w interfejsie użytkownika, ale nie jest to łatwe, gdy trzeba przenieść pełny podział z jednej witryny do innej.

Jednak przy użyciu SharePoint plików powłoki zarządzania online i plików CSV jest to szybkie i łatwe. W tym zadaniu użyjesz Windows PowerShell, aby usunąć użytkownika z grupy zabezpieczeń zbioru witryn. Następnie użyjesz pliku CSV i usuniesz wielu użytkowników z różnych witryn.

Użyjemy polecenia cmdlet "Remove-SPOUser", aby usunąć pojedynczego użytkownika Microsoft 365 z grupy zbioru witryn, aby zobaczyć składnię polecenia. Oto jak wygląda składnia:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Na przykład usuńmy Bobby'ego Overby'ego z grupy Audytorzy zbioru witryn w zbiorze witryn contosotest w dzierżawie contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Załóżmy, że chcieliśmy usunąć Bobby'ego ze wszystkich grup, w których obecnie się znajduje. Oto jak to zrobić:

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> To tylko przykład. Nie należy uruchamiać tego polecenia, chyba że naprawdę trzeba usunąć użytkownika z każdej grupy, na przykład jeśli użytkownik opuści firmę.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatyzowanie zarządzania dużymi listami użytkowników i grup

Aby dodać dużą liczbę kont do SharePoint lokacji i nadać im uprawnienia, możesz użyć Centrum administracyjne platformy Microsoft 365, poszczególnych poleceń programu PowerShell lub programu PowerShell i pliku CSV. Spośród tych opcji plik CSV jest najszybszym sposobem automatyzacji tego zadania.

Podstawowym procesem jest utworzenie pliku CSV zawierającego nagłówki (kolumny) odpowiadające parametrom, których potrzebuje skrypt Windows PowerShell. Możesz łatwo utworzyć taką listę w Excel, a następnie wyeksportować ją jako plik CSV. Następnie użyjesz skryptu Windows PowerShell, aby iterować rekordy (wiersze) w pliku CSV, dodając użytkowników do grup i grup do witryn.

Na przykład utwórzmy plik CSV, aby zdefiniować grupę zbiorów witryn, grup i uprawnień. Następnie utworzymy plik CSV, aby wypełnić grupy użytkownikami. Na koniec utworzymy i uruchomimy skrypt Windows PowerShell, który tworzy i wypełnia grupy.

Pierwszy plik CSV doda co najmniej jedną grupę do co najmniej jednego zbioru witryn i będzie miał następującą strukturę:

Nagłówka:

```powershell
Site,Group,PermissionLevels
```

Element:

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

Oto przykładowy plik:

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

Drugi plik CSV doda co najmniej jednego użytkownika do co najmniej jednej grupy i będzie miał następującą strukturę:

Nagłówka:

```powershell
Group,LoginName,Site
```

Element:

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

Oto przykładowy plik:

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

W następnym kroku na dysku muszą być zapisane dwa pliki CSV. Oto przykładowe polecenia, które używają zarówno plików CSV, jak i do dodawania uprawnień i członkostwa w grupie:

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Skrypt importuje zawartość pliku CSV i używa wartości w kolumnach, aby wypełnić parametry poleceń **New-SPOSiteGroup** i **Add-SPOUser** . W naszym przykładzie zapisujemy ten plik w folderze O365Admin na dysku C, ale można go zapisać w dowolnym miejscu.

Teraz usuńmy grupę osób dla kilku grup w różnych witrynach przy użyciu tego samego pliku CSV. Oto przykładowe polecenie:

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Generowanie raportów użytkowników

Możesz pobrać raport dla kilku witryn i wyświetlić użytkowników dla tych witryn, ich poziomu uprawnień i innych właściwości. Tak wygląda składnia:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Spowoduje to przechwycenie danych dla tych trzech witryn i zapisanie ich w pliku tekstowym na dysku lokalnym. Parametr — dołączanie spowoduje dodanie nowej zawartości do istniejącego pliku.

Na przykład uruchomimy raport w witrynach ContosoTest, TeamSite01 i Project01 dla dzierżawy contoso1:

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Musieliśmy zmienić tylko **zmienną $site** . Zmienna **$tenant** zachowuje swoją wartość przez wszystkie trzy uruchomienia polecenia.

Co jednak zrobić, jeśli chcesz to zrobić dla każdej witryny? Można to zrobić bez konieczności wpisywania wszystkich tych witryn internetowych za pomocą następującego polecenia:

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Ten raport jest dość prosty i można dodać więcej kodu w celu utworzenia bardziej szczegółowych raportów lub raportów zawierających bardziej szczegółowe informacje. Powinno to jednak dać wyobrażenie o tym, jak używać powłoki zarządzania SharePoint Online do zarządzania użytkownikami w środowisku SharePoint Online.

## <a name="see-also"></a>Zobacz też

[Połączenie do programu PowerShell SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Zarządzanie SharePoint Online przy użyciu programu PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
