---
title: Zarządzanie grupami zabezpieczeń przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
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
- O365ITProTrain
description: Dowiedz się, jak zarządzać grupami zabezpieczeń za pomocą programu PowerShell.
ms.openlocfilehash: c1ae74e60eb00e74efe5ad881e9ce3c0ebb3cf12
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099416"
---
# <a name="manage-security-groups-with-powershell"></a>Zarządzanie grupami zabezpieczeń przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Program PowerShell umożliwia Microsoft 365 jako alternatywa dla Centrum administracyjne platformy Microsoft 365 do zarządzania grupami zabezpieczeń. 

W tym artykule opisano wyświetlanie listy, tworzenie, zmienianie ustawień i usuwanie grup zabezpieczeń. 

Jeśli blok poleceń w tym artykule wymaga określenia wartości zmiennych, wykonaj te kroki.

1. Skopiuj blok poleceń do schowka i wklej go do Notatnik lub zintegrowanego środowiska skryptów programu PowerShell (ISE).
2. Wypełnij wartości zmiennej i usuń znaki "<" i ">".
3. Uruchom polecenia w oknie programu PowerShell lub programie PowerShell ISE.

Zobacz [Utrzymywanie członkostwa w grupach zabezpieczeń](maintain-group-membership-with-microsoft-365-powershell.md) , aby zarządzać członkostwem w grupach przy użyciu programu PowerShell.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="list-your-groups"></a>Wyświetlanie listy grup

Użyj tego polecenia, aby wyświetlić listę wszystkich grup.

```powershell
Get-AzureADGroup
```
Użyj tych poleceń, aby wyświetlić ustawienia określonej grupy według jej nazwy wyświetlanej.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Tworzenie nowej grupy

Użyj tego polecenia, aby utworzyć nową grupę zabezpieczeń.

```powershell
New-AzureADGroup -Description "<group purpose>" -DisplayName "<name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "<email name>"
```

### <a name="change-the-settings-on-a-group"></a>Zmienianie ustawień w grupie

Wyświetl ustawienia grupy przy użyciu tych poleceń.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Następnie użyj artykułu [Set-AzureADGroup](/powershell/module/azuread/set-azureadgroup) , aby określić sposób zmiany ustawienia.

### <a name="remove-a-security-group"></a>Usuwanie grupy zabezpieczeń

Użyj tych poleceń, aby usunąć grupę zabezpieczeń.

```powershell
$groupName="<display name of the group>"
Remove-AzureADGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

### <a name="manage-the-owners-of-a-security-group"></a>Zarządzanie właścicielami grupy zabezpieczeń

Użyj tych poleceń, aby wyświetlić bieżących właścicieli grupy zabezpieczeń.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```
Użyj tych poleceń, aby dodać konto użytkownika według **głównej nazwy użytkownika (UPN)** do bieżących właścicieli grupy zabezpieczeń.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```
Użyj tych poleceń, aby dodać konto użytkownika według **jego nazwy wyświetlanej** do bieżących właścicieli grupy zabezpieczeń.

```powershell
$userName="<Display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```
Użyj tych poleceń, aby usunąć konto użytkownika za pomocą nazwy **UPN** dla bieżących właścicieli grupy zabezpieczeń.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```

Użyj tych poleceń, aby usunąć konto użytkownika według **jego nazwy wyświetlanej** bieżącym właścicielom grupy zabezpieczeń.

```powershell
$userName="<Display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="list-your-groups"></a>Wyświetlanie listy grup

Użyj tego polecenia, aby wyświetlić listę wszystkich grup.

```powershell
Get-MsolGroup
```
Użyj tych poleceń, aby wyświetlić ustawienia określonej grupy według jej nazwy wyświetlanej.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Tworzenie nowej grupy

Użyj tego polecenia, aby utworzyć nową grupę zabezpieczeń.

```powershell
New-MsolGroup -Description "<group purpose>" -DisplayName "<name>"
```

### <a name="change-the-settings-on-a-group"></a>Zmienianie ustawień w grupie

Wyświetl ustawienia grupy przy użyciu tych poleceń.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Następnie użyj artykułu [Set-MsolGroup](/powershell/module/msonline/set-msolgroup) , aby określić sposób zmiany ustawienia.

### <a name="remove-a-security-group"></a>Usuwanie grupy zabezpieczeń

Użyj tych poleceń, aby usunąć grupę zabezpieczeń.

```powershell
$groupName="<display name of the group>"
Remove-MsolGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)