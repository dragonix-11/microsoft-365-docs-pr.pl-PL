---
title: Utrzymywanie członkostwa w grupach zabezpieczeń przy użyciu programu PowerShell
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Dowiedz się, jak zachować członkostwo w grupach Microsoft 365 przy użyciu programu PowerShell.
ms.openlocfilehash: 48720d5f3922598feec5a64eaa2c2532e17248ad
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095691"
---
# <a name="maintain-security-group-membership-with-powershell"></a>Utrzymywanie członkostwa w grupach zabezpieczeń przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Program PowerShell może służyć do Microsoft 365 jako alternatywy dla Centrum administracyjne platformy Microsoft 365 w celu utrzymania członkostwa w grupach zabezpieczeń w Microsoft 365. 

>[!Note]
>[Dowiedz się, jak zachować członkostwo w grupach Microsoft 365](../admin/create-groups/add-or-remove-members-from-groups.md) przy użyciu Centrum administracyjne platformy Microsoft 365. Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph
Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Dodawanie lub usuwanie kont użytkowników jako członków grupy

**Aby dodać konto użytkownika według nazwy UPN**, wypełnij nazwę główną użytkownika (UPN) konta użytkownika (np. belindan@contoso.com) i nazwę wyświetlaną grupy zabezpieczeń, usuwając znaki "<" i ">", a następnie uruchom te polecenia w oknie programu PowerShell lub zintegrowanym środowisku skryptowym programu PowerShell (ISE).

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby dodać konto użytkownika według jego nazwy wyświetlanej**, wypełnij nazwę wyświetlaną konta użytkownika (na przykład Belinda Newman) i nazwę wyświetlaną grupy i uruchom te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby usunąć konto użytkownika według nazwy UPN**, wypełnij nazwę UPN konta użytkownika (na przykład belindan@contoso.com) i nazwę wyświetlaną grupy i uruchom te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby usunąć konto użytkownika według jego nazwy wyświetlanej**, wypełnij nazwę wyświetlaną konta użytkownika (na przykład Belinda Newman) i nazwę wyświetlaną grupy i uruchom te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Dodawanie lub usuwanie grup jako członków grupy

Grupy zabezpieczeń mogą zawierać inne grupy jako elementy członkowskie. nie można jednak Microsoft 365 grup. Ta sekcja zawiera polecenia programu PowerShell umożliwiające dodawanie lub usuwanie grup tylko dla grupy zabezpieczeń.

**Aby dodać grupę według jej nazwy wyświetlanej**, podaj nazwę wyświetlaną grupy, którą chcesz dodać, oraz nazwę wyświetlaną grupy, która będzie zawierać grupę składową i uruchamiać te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby usunąć grupę według jej nazwy wyświetlanej**, podaj nazwę wyświetlaną grupy, którą zamierzasz usunąć, oraz nazwę wyświetlaną grupy, która będzie zawierać grupę składową i uruchamiać te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Dodawanie lub usuwanie kont użytkowników jako członków grupy

**Aby dodać konto użytkownika według nazwy UPN**, wypełnij nazwę główną użytkownika (UPN) konta użytkownika (np. belindan@contoso.com) i nazwę wyświetlaną grupy, usuwając znaki "<" i ">", a następnie uruchom te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby dodać konto użytkownika według jego nazwy wyświetlanej**, wypełnij nazwę wyświetlaną konta użytkownika (na przykład Belinda Newman) i nazwę wyświetlaną grupy i uruchom te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby usunąć konto użytkownika według nazwy UPN**, wypełnij nazwę UPN konta użytkownika (na przykład belindan@contoso.com) i nazwę wyświetlaną grupy i uruchom te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Aby usunąć konto użytkownika według jego nazwy wyświetlanej**, wypełnij nazwę wyświetlaną konta użytkownika (na przykład Belinda Newman) i nazwę wyświetlaną grupy i uruchom te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Dodawanie lub usuwanie grup jako członków grupy

Grupy zabezpieczeń mogą zawierać inne grupy jako elementy członkowskie. nie można jednak Microsoft 365 grup. Ta sekcja zawiera polecenia programu PowerShell umożliwiające dodawanie lub usuwanie grup tylko dla grupy zabezpieczeń.

**Aby dodać grupę według jej nazwy wyświetlanej**, podaj nazwę wyświetlaną grupy, którą chcesz dodać, oraz nazwę wyświetlaną grupy, która będzie zawierać grupę składową i uruchamiać te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**Aby usunąć grupę według jej nazwy wyświetlanej**, podaj nazwę wyświetlaną grupy, którą zamierzasz usunąć, oraz nazwę wyświetlaną grupy, która będzie zawierać grupę składową i uruchamiać te polecenia w oknie programu PowerShell lub programie PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)