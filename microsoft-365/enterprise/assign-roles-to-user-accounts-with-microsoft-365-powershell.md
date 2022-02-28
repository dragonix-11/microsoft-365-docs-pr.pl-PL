---
title: Przypisywanie ról do Microsoft 365 użytkowników za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule dowiesz się, jak szybko i łatwo używać programu PowerShell do Microsoft 365 przypisywania ról administratorów do kont użytkowników.
ms.openlocfilehash: 0b0fc0a5da1a6b84d4f13f95ace4846e367ae111
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985049"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>Przypisywanie ról administratora do Microsoft 365 użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Możesz łatwo przypisywać role do kont użytkowników przy użyciu programu PowerShell dla komputerów Microsoft 365.

>[!Note]
>Dowiedz się, jak [przypisywać role administratora](../admin/add-users/assign-admin-roles.md) do kont użytkowników centrum administracyjne platformy Microsoft 365.
>
>Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw użyj administratora dc usługi **Azure AD**, administratora **aplikacji** w chmurze lub konta  administratora globalnego, aby połączyć się ze [swoją Microsoft 365 dzierżawą](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](/microsoft-365/admin/add-users/about-admin-roles?).

Następnie zidentyfikuj nazwę logowania konta użytkownika, które chcesz dodać do roli (przykład: fredsm\@ contoso.com). Ta nazwa jest również znana jako główna nazwa użytkownika (UPN).

Następnie określ nazwę roli. Zobacz [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference).

>[!Note]
>Zwróć uwagę na notatki w tym artykule. Niektóre nazwy ról w programie PowerShell Azure Active Directory (Azure AD). Na przykład rola *administratora SharePoint* w programie centrum administracyjne platformy Microsoft 365 to *SharePoint usługi w* programie PowerShell usługi Azure AD.
>

Następnie wypełnij pola logowania i nazw ról i uruchom następujące polecenia:
  
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

Oto przykład ukończonego zestawu poleceń, który przypisuje rolę administratora SharePoint do konta *belindan\@ contoso.com*:
  
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

Najpierw użyj konta administratora globalnego, aby [połączyć się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="for-a-single-role-change"></a>W przypadku jednej zmiany roli

Najczęściej spotykane sposoby określania konta użytkownika to użycie jego nazwy wyświetlanej lub nazwy e-mail, nazywanej również nazwą logowania lub główną nazwą użytkownika (UPN).

#### <a name="display-names-of-user-accounts"></a>Nazwy wyświetlane kont użytkowników

Jeśli masz już uprawnienia do pracy z wyświetlanymi nazwami kont użytkowników, określ następujące informacje:
  
- Konto użytkownika, które chcesz skonfigurować
    
    Aby określić konto użytkownika, należy określić jego nazwę wyświetlaną. Aby uzyskać pełną listę kont, użyj tego polecenia:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    To polecenie zawiera listę Nazwa wyświetlana kont użytkowników posortowanych według nazwy wyświetlanej po jednym ekranie na raz. Za pomocą polecenia cmdlet **Where** można odfiltrować listę do mniejszego zestawu. Zobacz poniższy przykład.

   >[!Note]
   >Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z *nazwą Msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    To polecenie zawiera listę tylko kont użytkowników, dla których nazwa wyświetlana zaczyna się od "Jan".
    
- Rola, którą chcesz przypisać
    
    Aby wyświetlić listę dostępnych ról administratora, które można przypisać do kont użytkowników, użyj tego polecenia:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Po określeniu nazwy wyświetlanej konta i nazwy roli przypisz tę rolę do konta za pomocą tych poleceń:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Wklej polecenia do Notatnik. Dla *$dispName i* *$roleName* zastąp tekst opisu ich wartościami. Usuń znaki \< and > , ale zachowaj cudzysłowy. Wklej zmodyfikowane wiersze do okna Microsoft Azure Active Directory Moduł Windows PowerShell, aby je uruchomić. Ewentualnie można użyć środowiska Windows PowerShell Script Environment (ISE).
  
Oto przykład ukończonego zestawu poleceń:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Nazwy logowania kont użytkowników

Jeśli masz już uprawnienia do pracy z nazwami logowania lub nazwami UPN kont użytkowników, sprawdź następujące informacje:
  
- UpN konta użytkownika
    
    Jeśli nie znasz upn, użyj tego polecenia:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    To polecenie zawiera listę u góry nazwy użytkownika (UPN) dla kont użytkowników posortowanych według nazwy UPN po jednym ekranie na raz. Do filtrowania **listy możesz** użyć polecenia cmdlet Where. Oto przykład:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    To polecenie zawiera listę tylko kont użytkowników, dla których nazwa wyświetlana zaczyna się od "Jan".
    
- Rola, którą chcesz przypisać
    
    Aby wyświetlić listę dostępnych ról, które można przypisać do kont użytkowników, użyj tego polecenia:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Po przypisaniu głównej nazwy użytkownika do konta i nazwy roli użyj tych poleceń, aby przypisać tę rolę do konta:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Skopiuj polecenia i wklej je do Notatnik. Dla **$upnName** **i $roleName** zmiennych. Zastąp tekst opisu wartościami. Usuń znaki \< and > , ale zachowaj cudzysłowy. Wklej zmodyfikowane wiersze do Microsoft Azure Active Directory Moduł dla Windows PowerShell, aby je uruchomić. Ewentualnie możesz użyć funkcji Windows PowerShell ISE.
  
Oto przykład ukończonego zestawu poleceń:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Wiele zmian ról

W przypadku wielu zmian ról należy ustalić następujące informacje:
  
- Konta użytkowników, które chcesz skonfigurować. Za pomocą metod poprzednich sekcji można zebrać zestaw nazw wyświetlanych lub nazw UPN.
    
- Role, które chcesz przypisać do każdego konta użytkownika. Aby wyświetlić listę dostępnych ról, które można przypisać do kont użytkowników, użyj tego polecenia:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Następnie utwórz plik tekstowy wartości rozdzielanych przecinkami (CSV), który zawiera pola nazwy wyświetlanej lub głównej nazwy użytkownika i nazwy roli. Możesz to zrobić łatwo w Microsoft Excel.

Oto przykład nazw wyświetlanych:
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

Następnie wprowadź lokalizację pliku CSV i uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

Oto przykład dla upnów:
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

Następnie wprowadź lokalizację pliku CSV i uruchom wynikowe polecenia w wierszu polecenia programu PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
