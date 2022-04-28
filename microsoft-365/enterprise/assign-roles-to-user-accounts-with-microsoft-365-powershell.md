---
title: Przypisywanie ról do Microsoft 365 kont użytkowników przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/23/2020
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: W tym artykule dowiesz się, jak szybko i łatwo używać programu PowerShell do Microsoft 365 przypisywania ról administratora do kont użytkowników.
ms.openlocfilehash: 8ac98920dd3d2d0487905b001434d73274463f9a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097453"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>Przypisywanie ról administratora do Microsoft 365 kont użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Role można łatwo przypisywać do kont użytkowników przy użyciu programu PowerShell na potrzeby Microsoft 365.

>[!Note]
>Dowiedz się, jak [przypisywać role administratora](../admin/add-users/assign-admin-roles.md) do kont użytkowników przy użyciu Centrum administracyjne platformy Microsoft 365.
>
>Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw użyj **administratora kontrolera domeny usługi Azure AD**, **administratora aplikacji w chmurze** lub konta **administratora globalnego**, [aby nawiązać połączenie z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](/microsoft-365/admin/add-users/about-admin-roles?).

Następnie zidentyfikuj nazwę logowania konta użytkownika, które chcesz dodać do roli (na przykład fredsm\@ contoso.com). Jest to również nazywane główną nazwą użytkownika (UPN).

Następnie określ nazwę roli. Zobacz [Role wbudowane usługi Azure AD](/azure/active-directory/roles/permissions-reference).

>[!Note]
>Zwróć uwagę na notatki w tym artykule. Niektóre nazwy ról różnią się w przypadku programu PowerShell Azure Active Directory (Azure AD). Na przykład rolą *administratora SharePoint* w Centrum administracyjne platformy Microsoft 365 jest *administrator usługi SharePoint* w programie Azure AD PowerShell.
>

Następnie wypełnij nazwy logowania i ról, a następnie uruchom następujące polecenia:
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<admin role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Oto przykład ukończonego zestawu poleceń, który przypisuje rolę administratora usługi SharePoint do konta *belindan\@ contoso.com*:
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Aby wyświetlić listę nazw użytkowników dla określonej roli administratora, użyj tych poleceń.

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw użyj konta administratora globalnego, aby [nawiązać połączenie z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="for-a-single-role-change"></a>W przypadku zmiany pojedynczej roli

Najczęstszym sposobem określenia konta użytkownika jest użycie jego nazwy wyświetlanej lub nazwy e-mail, która jest również znana jako nazwa logowania lub główna nazwa użytkownika (UPN).

#### <a name="display-names-of-user-accounts"></a>Wyświetlanie nazw kont użytkowników

Jeśli pracujesz z nazwami wyświetlanymi kont użytkowników, określ następujące informacje:
  
- Konto użytkownika, które chcesz skonfigurować
    
    Aby określić konto użytkownika, należy określić jego nazwę wyświetlaną. Aby uzyskać pełną listę kont, użyj następującego polecenia:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    To polecenie wyświetla listę nazwy wyświetlanej kont użytkowników posortowanych według nazwy wyświetlanej po jednym ekranie naraz. Listę można filtrować do mniejszego zestawu przy użyciu polecenia cmdlet **Where** . Zobacz poniższy przykład.

   >[!Note]
   >Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą *msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    To polecenie wyświetla tylko konta użytkowników, dla których nazwa wyświetlana zaczyna się od "John".
    
- Rola, którą chcesz przypisać
    
    Aby wyświetlić listę dostępnych ról administratora, które można przypisać do kont użytkowników, użyj tego polecenia:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Po określeniu nazwy wyświetlanej konta i nazwy roli użyj tych poleceń, aby przypisać rolę do konta:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Wklej polecenia do Notatnik. W przypadku *zmiennych $dispName* i *$roleName* zastąp tekst opisu wartościami. Usuń znaki, \< and > ale zachowaj cudzysłów. Wklej zmodyfikowane wiersze w oknie Microsoft Azure Active Directory Module for Windows PowerShell, aby je uruchomić. Alternatywnie można użyć Windows PowerShell zintegrowanego środowiska skryptów (ISE).
  
Oto przykład ukończonego zestawu poleceń:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Nazwy logowania kont użytkowników

Jeśli pracujesz z nazwami logowania lub nazwami UPN kont użytkowników, określ następujące informacje:
  
- Nazwa UPN konta użytkownika
    
    Jeśli nie znasz nazwy UPN, użyj tego polecenia:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    To polecenie wyświetla nazwę UPN kont użytkowników posortowane według nazwy UPN, po jednym ekranie naraz. Aby odfiltrować listę, możesz użyć polecenia cmdlet **Where** . Oto przykład:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    To polecenie wyświetla tylko konta użytkowników, dla których nazwa wyświetlana zaczyna się od "John".
    
- Rola, którą chcesz przypisać
    
    Aby wyświetlić listę dostępnych ról, które można przypisać do kont użytkowników, użyj tego polecenia:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Po utworzeniu nazwy UPN konta i nazwy roli użyj tych poleceń, aby przypisać rolę do konta:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Skopiuj polecenia i wklej je do Notatnik. Dla **zmiennych $upnName** i **$roleName** . Zastąp tekst opisu wartościami. Usuń znaki, \< and > ale zachowaj cudzysłów. Wklej zmodyfikowane wiersze do modułu Microsoft Azure Active Directory, aby Windows PowerShell okno, aby je uruchomić. Alternatywnie można użyć Windows PowerShell ISE.
  
Oto przykład ukończonego zestawu poleceń:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Zmiany wielu ról

W przypadku wielu zmian roli określ następujące informacje:
  
- Które konta użytkowników chcesz skonfigurować. Metody z poprzedniej sekcji umożliwiają zebranie zestawu nazw wyświetlanych lub nazw UPN.
    
- Jakie role chcesz przypisać do każdego konta użytkownika. Aby wyświetlić listę dostępnych ról, które można przypisać do kont użytkowników, użyj tego polecenia:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Następnie utwórz plik tekstowy wartości rozdzielanej przecinkami (CSV), który ma nazwę wyświetlaną lub nazwę UPN i pola nazwy roli. Można to zrobić łatwo w Microsoft Excel.

Oto przykład dla nazw wyświetlanych:
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

Następnie wypełnij lokalizację pliku CSV i uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

Oto przykład dla nazw UPN:
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

Następnie wypełnij lokalizację pliku CSV i uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Wprowadzenie za pomocą programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
