---
title: Zarządzanie grupami zabezpieczeń za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.openlocfilehash: d07296b88e626e854c57152a079cc96e1e23e8d3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988013"
---
# <a name="manage-security-groups-with-powershell"></a>Zarządzanie grupami zabezpieczeń za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Programu PowerShell dla Microsoft 365 jako alternatywy dla centrum administracyjne platformy Microsoft 365 do zarządzania grupami zabezpieczeń. 

W tym artykule opisano tworzenie, zmienianie ustawień i usuwanie grup zabezpieczeń. 

Jeśli blok poleceń w tym artykule wymaga określenia wartości zmiennych, należy wykonać poniższe czynności.

1. Skopiuj blok polecenia do schowka i wklej go do Notatnik lub środowiska PowerShell Integrated Script Environment (ISE).
2. Wypełnij wartości zmiennych i usuń znaki "<" i ">".
3. Uruchom polecenia w oknie programu PowerShell lub w oknie programu PowerShell ISE.

Zobacz [Utrzymywanie członkostwa w grupach zabezpieczeń,](maintain-group-membership-with-microsoft-365-powershell.md) aby zarządzać członkostwem w grupach za pomocą programu PowerShell.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="list-your-groups"></a>Lista grup

Użyj tego polecenia, aby wyświetlić listę wszystkich grup.

```powershell
Get-AzureADGroup
```
Za pomocą tych poleceń można wyświetlić ustawienia określonej grupy według jej nazwy wyświetlanej.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Tworzenie nowej grupy

Użyj tego polecenia, aby utworzyć nową grupę zabezpieczeń.

```powershell
New-AzureADGroup -Description "<group purpose>" -DisplayName "<name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "<email name>"
```

### <a name="change-the-settings-on-a-group"></a>Zmienianie ustawień grupy

Wyświetl ustawienia grupy za pomocą tych poleceń.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Następnie skorzystaj z artykułu [Set-AzureADGroup](/powershell/module/azuread/set-azureadgroup) , aby dowiedzieć się, jak zmienić ustawienie.

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
Korzystając z tych poleceń, można dodać konto użytkownika według jego głównej nazwy **użytkownika (UPN)** u bieżących właścicieli grupy zabezpieczeń.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```
Korzystając z tych poleceń, można dodać konto użytkownika **według jego nazwy** wyświetlanej do bieżących właścicieli grupy zabezpieczeń.

```powershell
$userName="<Display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```
Użyj tych poleceń, aby usunąć konto użytkownika za pomocą jego **upn** na bieżących właścicieli grupy zabezpieczeń.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```

Użyj tych poleceń, aby usunąć konto użytkownika **według jego nazwy** wyświetlanej bieżącym właścicielom grupy zabezpieczeń.

```powershell
$userName="<Display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="list-your-groups"></a>Lista grup

Użyj tego polecenia, aby wyświetlić listę wszystkich grup.

```powershell
Get-MsolGroup
```
Za pomocą tych poleceń można wyświetlić ustawienia określonej grupy według jej nazwy wyświetlanej.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Tworzenie nowej grupy

Użyj tego polecenia, aby utworzyć nową grupę zabezpieczeń.

```powershell
New-MsolGroup -Description "<group purpose>" -DisplayName "<name>"
```

### <a name="change-the-settings-on-a-group"></a>Zmienianie ustawień grupy

Wyświetl ustawienia grupy za pomocą tych poleceń.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Następnie skorzystaj z artykułu [Set-MsolGroup](/powershell/module/msonline/set-msolgroup) , aby dowiedzieć się, jak zmienić ustawienie.

### <a name="remove-a-security-group"></a>Usuwanie grupy zabezpieczeń

Użyj tych poleceń, aby usunąć grupę zabezpieczeń.

```powershell
$groupName="<display name of the group>"
Remove-MsolGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)