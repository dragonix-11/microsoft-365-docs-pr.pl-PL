---
title: Obsługa członkostwa w grupach zabezpieczeń za pomocą programu PowerShell
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Dowiedz się, jak za pomocą programu PowerShell utrzymać członkostwo w Microsoft 365 grupach.
ms.openlocfilehash: 3637fb7d2e68091c43e624e9b6780d032c1930bc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988387"
---
# <a name="maintain-security-group-membership-with-powershell"></a>Obsługa członkostwa w grupach zabezpieczeń za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Programu PowerShell dla Microsoft 365 można używać jako alternatywy dla centrum administracyjne platformy Microsoft 365 w celu utrzymania członkostwa w grupach zabezpieczeń w Microsoft 365. 

>[!Note]
>[Dowiedz się, jak utrzymać Microsoft 365 grupy](../admin/create-groups/add-or-remove-members-from-groups.md) przy użyciu centrum administracyjne platformy Microsoft 365. Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych
Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Dodawanie lub usuwanie kont użytkowników jako członków grupy

Aby dodać konto użytkownika za pomocą głównej nazwy **użytkownika, wprowadź** główną nazwę użytkownika (UPN) konta użytkownika (na przykład belindan@contoso.com) i nazwę wyświetlaną grupy zabezpieczeń, usuwając znaki "<" i ">", a następnie uruchom te polecenia w oknie programu PowerShell lub w środowisku zintegrowanego skryptu programu PowerShell (ISE).

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Aby dodać konto użytkownika według jego nazwy wyświetlanej, wprowadź nazwę wyświetlaną konta użytkownika (na przykład Belinda Newman) oraz nazwę wyświetlaną grupy, **a** następnie uruchom te polecenia w oknie programu PowerShell lub w oknie środowiska PowerShell isE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Aby usunąć konto użytkownika za pomocą jego upn, wprowadź nazwę **UPN** konta użytkownika (na przykład: belindan@contoso.com) i nazwę wyświetlaną grupy, a następnie uruchom te polecenia w oknie programu PowerShell lub w oknie programu PowerShell isE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby** usunąć konto użytkownika według jego nazwy wyświetlanej, wprowadź nazwę wyświetlaną konta użytkownika (na przykład Belinda Newman) oraz nazwę wyświetlaną grupy, a następnie uruchom te polecenia w oknie programu PowerShell lub w oknie środowiska PowerShell isE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Dodawanie lub usuwanie grup jako członków grupy

Grupy zabezpieczeń mogą zawierać inne grupy jako członków. Microsoft 365 grupy, jednak nie mogą. Ta sekcja zawiera polecenia programu PowerShell służące do dodawania lub usuwania grup tylko dla grupy zabezpieczeń.

Aby dodać grupę według jej nazwy wyświetlanej **, wpisz** nazwę wyświetlaną grupy, która ma być dodawania, oraz nazwę wyświetlaną grupy, która będzie zawierać grupę członków, i uruchom te polecenia w oknie programu PowerShell lub w oknie programu PowerShell lub w oknie środowiska PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby** usunąć grupę według jej nazwy wyświetlanej, wpisz nazwę wyświetlaną grupy, która ma być usuwana, oraz nazwę wyświetlaną grupy, która będzie zawierać grupę członków, i uruchom te polecenia w oknie programu PowerShell lub w oknie programu PowerShell lub w oknie programu PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Dodawanie lub usuwanie kont użytkowników jako członków grupy

Aby dodać konto użytkownika według jego głównej nazwy **użytkownika, wprowadź** główną nazwę użytkownika (UPN) konta użytkownika (na przykład: belindan@contoso.com) i nazwę wyświetlaną grupy, usuwając znaki "<" i ">", a następnie uruchom te polecenia w oknie programu PowerShell lub w oknie programu PowerShell lub w oknie ISE programu PowerShell.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Aby dodać konto użytkownika według jego nazwy wyświetlanej, wprowadź nazwę wyświetlaną konta użytkownika (na przykład Belinda Newman) oraz nazwę wyświetlaną grupy, **a** następnie uruchom te polecenia w oknie programu PowerShell lub w oknie środowiska PowerShell isE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Aby usunąć konto użytkownika za pomocą jego upn, wprowadź nazwę **UPN** konta użytkownika (na przykład: belindan@contoso.com) i nazwę wyświetlaną grupy, a następnie uruchom te polecenia w oknie programu PowerShell lub w oknie programu PowerShell isE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby** usunąć konto użytkownika według jego nazwy wyświetlanej, wprowadź nazwę wyświetlaną konta użytkownika (na przykład Belinda Newman) oraz nazwę wyświetlaną grupy, a następnie uruchom te polecenia w oknie programu PowerShell lub w oknie środowiska PowerShell isE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Dodawanie lub usuwanie grup jako członków grupy

Grupy zabezpieczeń mogą zawierać inne grupy jako członków. Microsoft 365 grupy, jednak nie mogą. Ta sekcja zawiera polecenia programu PowerShell służące do dodawania lub usuwania grup tylko dla grupy zabezpieczeń.

Aby dodać grupę według jej nazwy wyświetlanej **, wpisz** nazwę wyświetlaną grupy, która ma być dodawania, oraz nazwę wyświetlaną grupy, która będzie zawierać grupę członków, i uruchom te polecenia w oknie programu PowerShell lub w oknie programu PowerShell lub w oknie środowiska PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**Aby** usunąć grupę według jej nazwy wyświetlanej, wpisz nazwę wyświetlaną grupy, która ma być usuwana, oraz nazwę wyświetlaną grupy, która będzie zawierać grupę członków, i uruchom te polecenia w oknie programu PowerShell lub w oknie programu PowerShell lub w oknie programu PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)