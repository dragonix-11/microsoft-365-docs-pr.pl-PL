---
title: Wyświetlanie Microsoft 365 użytkowników za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: Dowiedz się, jak wyświetlać, wyświetlać i wyświetlać swoje Microsoft 365 konta użytkowników na różne sposoby za pomocą programu PowerShell.
ms.openlocfilehash: 5c434825da95fd7d90594b2424cab287305f7d26
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989712"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>Wyświetlanie Microsoft 365 użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Konta dzierżawy centrum administracyjne platformy Microsoft 365 wyświetlić za pomocą Microsoft 365 dzierżawy. Program PowerShell dla Microsoft 365 umożliwia to, ale oferuje też dodatkowe funkcje.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Wyświetl wszystkie konta

Aby wyświetlić pełną listę kont użytkowników, uruchom to polecenie:
  
```powershell
Get-AzureADUser
```

Informacje powinny być podobne do tych:
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>Wyświetlanie określonego konta

Aby wyświetlić określone konto użytkownika, uruchom następujące polecenie. Wprowadź nazwę konta logowania konta użytkownika, która jest również znana jako główna nazwa użytkownika (UPN). Usuń znaki "<" i ">".
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Oto przykład:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Wyświetlanie dodatkowych wartości właściwości dla określonego konta

Domyślnie polecenie cmdlet **Get-AzureADUser** wyświetla tylko właściwości *ObjectID*, *DisplayName* i *UserPrincipalName* kont.

Aby mieć bardziej selektywny wybór właściwości do wyświetlenia, użyj polecenia cmdlet **Select** w połączeniu z poleceniem cmdlet **Get-AzureADUser** . Aby połączyć te dwa polecenia cmdlet, użyj znaku "potok" ("|"), który nakazuje programowi Azure Active Directory PowerShell dla programu Graph użycie wyników jednego polecenia i wysłanie go do następnego polecenia. Oto przykładowe polecenie wyświetlace wartości *DisplayName* (Nazwa wyświetlana), *Department* (Dział) i *UsageLocation (Lokalizacja użytkowania)* dla każdego konta użytkownika:
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).
    
1.  Wyświetlanie tylko nazwy konta użytkownika, działu i lokalizacji użytkowania (**wybierz pozycję Nazwa wyświetlana, Dział, Lokalizacja użytkowania**).
  
Aby wyświetlić wszystkie właściwości określonego konta użytkownika, użyj polecenia cmdlet **Select** i symbolu wieloznacznego (*). Oto przykład:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Innym przykładem jest uruchomienie następującego polecenia w celu sprawdzenia stanu włączonego dla określonego konta użytkownika:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Wyświetlanie stanu synchronizacji konta

Konta użytkowników mają dwa źródła: 

- Windows Server Active Directory (AD), które są kontami synchronizowanych z lokalnej usługi AD z chmurą.

- Azure Active Directory (Azure AD), które są tworzone bezpośrednio w chmurze.

Aby znaleźć konta synchronizowane z lokalnego konta usługi AD, możesz użyć **następującego polecenia** . Instruuje program PowerShell, aby wszyscy użytkownicy, którzy mają atrybut *DirSyncEnabled* ustawiony na *Prawda*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

Aby znaleźć konta tylko w chmurze, możesz użyć **następującego** polecenia. Instruuje program PowerShell, aby wszyscy użytkownicy, którzy mają atrybut *DirSyncEnabled* ustawiony na *False* lub nie (*Null*).
Konto, które nigdy nie było synchronizowane z lokalnego programu AD, ma dla ustawienia *DirSyncEnabled* wartość *Null*. Dla konta, które zostało początkowo zsynchronizowane z lokalnego programu AD, ale już nie jest synchronizowane, ustawiono wartość *DirSyncEnabled* na *False*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>Wyświetlanie kont opartych na wspólnej właściwości

Aby mieć bardziej selektywny dostęp do listy kont do wyświetlenia, możesz użyć polecenia cmdlet **Where** w połączeniu z poleceniem cmdlet **Get-AzureADUser** . Aby połączyć te dwa polecenia cmdlet, użyj znaku "potok" ("|"), który nakazuje programowi Azure Active Directory PowerShell dla programu Graph użycie wyników jednego polecenia i wysłanie go do następnego polecenia. Oto przykładowe polecenie, które wyświetla tylko te konta użytkowników, które mają nieokreślone miejsce użytkowania:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

To polecenie instruuje Azure Active Directory programu PowerShell dla Graph:
  
1. Uzyskaj wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).
    
1. Znajdź wszystkie konta użytkowników, które mają nieokreślone miejsce użytkowania (**gdzie {$\_. UsageLocation -eq $Null}**). Wewnątrz nawiasów klamrowych polecenie nakazuje programowi PowerShell odnalezienie tylko zestawu kont, dla których właściwość user userlocation (**$\_Lokalizacja użytkowania użytkownika). Lokalizacja użytkowania**) nie jest określona (**-eq $Null**).
    
Właściwość **UsageLocation (Lokalizacja** użytkowania) jest tylko jedną z wielu właściwości skojarzonych z kontem użytkownika. Aby wyświetlić wszystkie właściwości określonego konta użytkownika, użyj polecenia cmdlet **Select** i symbolu wieloznacznego (*). Oto przykład:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Na przykład **nazwa właściwości** konta użytkownika to Miasto. Aby wyświetlić listę wszystkich kont użytkowników zamieszkałych w Londynie, możesz użyć następującego polecenia:
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Składnia polecenia cmdlet **Where** w tych przykładach to **Where {$\_.** [nazwa właściwości konta użytkownika] [operator porównania] [wartość] **}**.> [operator porównania] to **-eq** dla równości, **-ne** dla nie równa się, **-lt** dla mniejszego niż, **-gt** dla większe niż i inne.  [wartość] jest zazwyczaj ciągiem (sekwencją liter, cyfr i innymi znakami), wartością liczbową $Null nieokreślonym. Aby uzyskać więcej informacji, zobacz [Gdzie](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Wyświetl wszystkie konta

Aby wyświetlić pełną listę kont użytkowników, uruchom to polecenie:
  
```powershell
Get-MsolUser
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z *nazwą Msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
>

Informacje powinny być podobne do tych:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Polecenie **cmdlet Get-MsolUser** ma również zestaw parametrów do filtrowania wyświetlanego zestawu kont użytkowników. Aby na przykład wyświetlić listę nielicencjonowanych użytkowników (użytkowników, którzy dodano do usługi Microsoft 365 ale nie mają jeszcze licencji na używanie żadnych usług), uruchom to polecenie:
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Informacje powinny być podobne do tych:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Aby uzyskać informacje o dodatkowych parametrach do filtrowania wyświetlanego zestawu kont użytkowników, zobacz [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Wyświetlanie określonego konta

Aby wyświetlić określone konto użytkownika, uruchom następujące polecenie. Wprowadź nazwę logowania dla konta użytkownika, które jest również nazywane główną nazwą użytkownika (UPN). Usuń znaki "<" i ">".
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Wyświetlanie kont opartych na wspólnej właściwości

Aby mieć bardziej selektywny dostęp do listy kont do wyświetlenia, możesz użyć polecenia cmdlet **Where** w połączeniu z poleceniem cmdlet **Get-MsolUser** . Aby połączyć te dwa polecenia cmdlet, użyj znaku "potok" ("|"), który nakazuje programowi PowerShell użycie wyników jednego polecenia i wysłanie go do następnego polecenia. Oto przykład, w którym są wyświetlane tylko te konta użytkowników, które mają nieokreślone miejsce użytkowania:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje o kontach użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).
    
1. Znajdź wszystkie konta użytkowników, które mają nieokreślone miejsce użytkowania (**gdzie {$\_. UsageLocation -eq $Null}**). Wewnątrz nawiasów klamrowych polecenie nakazuje programowi PowerShell znalezienie tylko zestawu kont, dla których właściwość userlocation użytkowania (**$\_. Lokalizacja użytkowania**) nie jest określona (**-eq $Null**).
    
Informacje powinny być podobne do tych:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

Właściwość *UsageLocation (Lokalizacja* użytkowania) jest tylko jedną z wielu właściwości skojarzonych z kontem użytkownika. Aby wyświetlić wszystkie właściwości kont użytkowników, użyj polecenia cmdlet **Select** i symbolu wieloznacznego (*) w celu wyświetlenia ich wszystkich dla określonego konta użytkownika. Oto przykład:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Na przykład *nazwa właściwości* konta użytkownika to Miasto. Aby wyświetlić listę wszystkich kont użytkowników użytkowników zamieszkałych w Londynie, możesz użyć następującego polecenia:
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Składnia polecenia cmdlet **Where** w tych przykładach to **Where {$\_.** [nazwa właściwości konta użytkownika] [operator porównania] [wartość] **}**.  [operator porównania] to **-eq** dla równa się, **-ne** dla nie równa się, **-lt** dla mniejszego niż, **-gt** dla wartości większe niż i inne.  [wartość] jest zazwyczaj ciągiem (sekwencją liter, cyfr i innymi znakami), wartością liczbową $Null nieokreślonym. Aby uzyskać więcej informacji, zobacz [Gdzie](/powershell/module/microsoft.powershell.core/where-object).
  
Aby sprawdzić stan zablokowanego konta użytkownika, użyj następującego polecenia:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Wyświetlanie dodatkowych wartości właściwości dla kont

Domyślnie polecenie cmdlet **Get-MsolUser** wyświetla następujące trzy właściwości kont użytkowników:
  
- UserPrincipalName (Nazwa użytkownika)

- DisplayName (Nazwa wyświetlana)

- isLicensed

Jeśli potrzebujesz dodatkowych właściwości, takich jak dział, w którym użytkownik pracuje, oraz kraj/region, w którym korzysta z usług firmy Microsoft 365, możesz uruchomić polecenie **Get-MsolUser** w połączeniu z poleceniem cmdlet **Select** (Wybierz), aby określić listę właściwości konta użytkownika. Oto przykład:
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje o kontach użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).
    
1. Wyświetlanie tylko nazwy konta użytkownika, działu i lokalizacji użytkowania (**wybierz pozycję Nazwa wyświetlana, Dział, Lokalizacja użytkowania**).
    
Informacje powinny być podobne do tych:
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

Polecenie cmdlet **Select** umożliwia wybranie właściwości do wyświetlenia. Aby wyświetlić wszystkie właściwości określonego konta użytkownika, użyj symbolu wieloznacznego (*). Oto przykład:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Aby mieć bardziej selektywny dostęp do listy kont do wyświetlenia, możesz również użyć polecenia cmdlet **Where** . Oto przykładowe polecenie, które wyświetla tylko te konta użytkowników, które mają nieokreślone miejsce użytkowania:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje o kontach użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).
    
1. Znajdź wszystkie konta użytkowników, które mają nieokreślone miejsce użytkowania (**gdzie {$\_. UsageLocation -eq $Null}**), a następnie wyślij wynikowe informacje do następnego polecenia (**|**). Wewnątrz nawiasów klamrowych polecenie nakazuje programowi PowerShell odnalezienie tylko zestawu kont, dla których właściwość user userlocation (**$\_Lokalizacja użytkowania użytkownika). Lokalizacja użytkowania**) nie jest określona (**-eq $Null**).
    
1. Wyświetlanie tylko nazwy konta użytkownika, działu i lokalizacji użytkowania (**wybierz pozycję Nazwa wyświetlana, Dział, Lokalizacja użytkowania**).
    
Informacje powinny być podobne do tych:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Jeśli używasz synchronizacji katalogów do tworzenia użytkowników usługi Microsoft 365 i zarządzania nimi, możesz wyświetlić konto lokalne, z którego został Microsoft 365 użytkownik. W poniższym przykładzie przyjęto założenie, że:

- Usługa Azure AD Połączenie skonfigurowana do używania domyślnej kotwicy źródłowej identyfikatorów ObjectGUID. (Aby uzyskać więcej informacji na temat konfigurowania zakotwiczenia źródła, zobacz Temat narzędzia [Azure AD Połączenie: pojęcia projektowe](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- Zainstalowano Usługi domenowe w usłudze Active Directory dla programu PowerShell (zobacz Narzędzia [RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
