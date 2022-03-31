---
title: Zarządzanie użytkownikami SharePoint Online i grupami za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Z tego artykułu dowiesz się, jak za pomocą programu PowerShell dla Microsoft 365 zarządzać SharePoint użytkownikami, grupami i witrynami online.
ms.openlocfilehash: e2166753b1be56c19011a1fc7e20d1584a5d3004
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681199"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>Zarządzanie użytkownikami SharePoint Online i grupami za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli jesteś administratorem usługi SharePoint Online, który pracuje z dużymi listami kont lub grup użytkowników i chce łatwiej zarządzać nimi, możesz użyć programu PowerShell dla systemu Microsoft 365.

Przed rozpoczęciem procedury w tym artykule wymagają nawiązania połączenia z usługą SharePoint Online. Aby uzyskać instrukcje, [Połączenie do SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>Uzyskiwanie listy witryn, grup i użytkowników

Zanim zaczniemy zarządzać użytkownikami i grupami, musisz uzyskać listy twoich witryn, grup i użytkowników. Następnie możesz użyć tych informacji do pracy z przykładem w tym artykule.

Uzyskaj listę witryn w dzierżawie za pomocą tego polecenia:

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

Polecenie cmdlet `Set-SPOUser` umożliwia dodanie użytkownika do listy administratorów zbioru witryn w zbiorze witryn.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

Aby użyć tych poleceń, zamień wszystkie cudzysłowy, w tym znaki < i >, na poprawne nazwy.

Na przykład za pomocą tego zestawu poleceń do listy administratorów zbioru witryn w zbiorze witryn ContosoTest w dzierżawie Contoso jest dodano nazwę użytkownika Contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

Te polecenia można skopiować i wkleić do programu Notatnik, zmienić wartości zmiennych dla systemów $tenant, $site i $user na rzeczywiste wartości ze środowiska, a następnie wkleić je do okna powłoki zarządzania usługi SharePoint Online, aby je uruchomić.

## <a name="add-a-user-to-other-site-collection-groups"></a>Dodawanie użytkownika do innych grup zbioru witryn

W tym zadaniu użyjemy `Add-SPOUser` polecenia cmdlet, aby dodać użytkownika do grupy SharePoint w zbiorze witryn.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

Na przykład dodajmy Glen Rife (user name glenr) do grupy Audytorzy w zbiorze witryn ContosoTest w dzierżawie contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Tworzenie grupy zbioru witryn

Polecenie cmdlet `New-SPOSiteGroup` umożliwia utworzenie nowej grupy SharePoint i dodanie jej do zbioru witryn.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

Właściwości grupy, takie jak poziomy uprawnień, można później zaktualizować przy użyciu polecenia `Set-SPOSiteGroup` cmdlet.

Na przykład dodajmy grupę Audytorzy z uprawnieniami Tylko wyświetlanie do zbioru witryn contosotest w dzierżawie firmy Contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Usuwanie użytkowników z grupy

Czasami trzeba usunąć użytkownika z witryny, a nawet wszystkich witryn. Być może pracownik przechodzi z jednego dzielenia do drugiego lub opuszcza firmę. W interfejsie użytkownika można to zrobić z łatwością dla jednego pracownika, ale nie da się tego łatwo zrobić, gdy trzeba przenieść pełne podziały z jednej witryny do drugiej.

Za pomocą powłoki zarządzania SharePoint online i plików CSV jest to jednak szybkie i łatwe. W tym zadaniu za pomocą funkcji Windows PowerShell usunąć użytkownika z grupy zabezpieczeń zbioru witryn. Następnie użyjesz pliku CSV i usuniesz wielu użytkowników z różnych witryn.

Będziemy używać polecenia cmdlet "Remove-SPOUser" do usunięcia pojedynczego Microsoft 365 z grupy zbioru witryn w celu zobaczenia składni poleceń. Składnia wygląda następująco:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Na przykład usuńmy wojciecha Overby z grupy audytorów zbioru witryn Contosotest w dzierżawie firmy Contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Załóżmy, że chcemy usunąć Wojciecha ze wszystkich grup, w których obecnie się znajduje. Oto jak możemy to zrobić:

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> To tylko przykład. Nie należy uruchamiać tego polecenia, chyba że naprawdę trzeba usunąć użytkownika ze wszystkich grup, na przykład gdy użytkownik odejdzie z firmy.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatyzowanie zarządzania dużymi listami użytkowników i grup

Aby dodać dużą liczbę kont do witryn SharePoint i nadać im uprawnienia, możesz użyć poleceń programu centrum administracyjne platformy Microsoft 365, poszczególnych poleceń programu PowerShell lub programu PowerShell i pliku CSV. Z tych opcji najszybszym sposobem na zautomatyzowanie tego zadania jest plik CSV.

Podstawowym procesem jest utworzenie pliku CSV, który zawiera nagłówki (kolumny) odpowiadające parametrom, których skrypt Windows PowerShell potrzebuje. Możesz łatwo utworzyć taką listę w programie Excel a następnie wyeksportować ją jako plik CSV. Następnie możesz użyć skryptu Windows PowerShell iterować rekordy (wiersze) w pliku CSV, dodając użytkowników do grup i grup do witryn.

Na przykład utworzymy plik CSV definiujący grupę zbiorów witryn, grup i uprawnień. Następnie utworzymy plik CSV, aby wypełnić grupy użytkownikami. Na koniec utworzymy i uruchamiamy skrypt Windows PowerShell, który tworzy i wypełnia grupy.

Pierwszy plik CSV spowoduje dodanie co najmniej jednej grupy do jednego lub większej liczby zbiorów witryn i będzie mieć tę strukturę:

Nagłówek:

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

Drugi plik CSV spowoduje dodanie jednego lub większej liczby użytkowników do jednej lub większej liczby grup i będzie mieć tę strukturę:

Nagłówek:

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

W następnym kroku należy zapisać na dysku dwa pliki CSV. Oto przykładowe polecenia, które używają zarówno plików CSV, jak i do dodawania uprawnień i członkostwa w grupach:

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Skrypt zaim importuje zawartość pliku CSV i używa wartości w kolumnach do wypełnienia parametrów poleceń **New-SPOSiteGroup** i **Add-SPOUser** . W naszym przykładzie zapisujemy ten plik w folderze O365Admin na dysku C, ale możesz go zapisać w dowolnym miejscu.

Teraz przy użyciu tego samego pliku CSV usuńmy wiele osób z kilku grup w różnych witrynach. Oto przykładowe polecenie:

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Generowanie raportów użytkowników

Możesz uzyskać raport dla kilku witryn i wyświetlić użytkowników tych witryn, ich poziom uprawnień i inne właściwości. Składnia wygląda następująco:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Spowoduje to pobrać dane z tych trzech witryn i zapisać je w pliku tekstowym na dysku lokalnym. Parametr —Dołącz spowoduje dodanie nowej zawartości do istniejącego pliku.

Na przykład uruchommy raport w witrynach Test Contoso, TeamSite01 i Project01 dzierżawy Contoso1:

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Musieliśmy zmienić tylko **zmienną $site** . **Zmienna $tenant** zachowuje wartość za pośrednictwem wszystkich trzech uruchamianych poleceń.

Co jednak zrobić w przypadku każdej witryny? Możesz to zrobić bez konieczności wpisywania wszystkich tych witryn internetowych, używając tego polecenia:

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Ten raport jest dość prosty i można dodać kod, aby utworzyć bardziej szczegółowe raporty lub raporty, które zawierają bardziej szczegółowe informacje. Jednak to powinno dać Ci pomysł, jak zarządzać użytkownikami w środowisku usługi SharePoint Online SharePoint Przy użyciu powłoki zarządzania online.

## <a name="see-also"></a>Zobacz też

[Połączenie do SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Zarządzanie usługą SharePoint Online za pomocą programu PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
