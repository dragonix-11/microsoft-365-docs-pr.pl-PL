---
title: Wyświetlanie kont użytkowników Microsoft 365 przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak wyświetlać, wyświetlać lub wyświetlać konta użytkowników Microsoft 365 na różne sposoby za pomocą programu PowerShell.
ms.openlocfilehash: cbbb188c50e4d163d5ef4226a83968c64e8a260c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090734"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>Wyświetlanie kont użytkowników Microsoft 365 przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Możesz użyć Centrum administracyjne platformy Microsoft 365, aby wyświetlić konta dla dzierżawy Microsoft 365. Program PowerShell dla Microsoft 365 umożliwia to, ale zapewnia również dodatkowe funkcje.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Wyświetl wszystkie konta

Aby wyświetlić pełną listę kont użytkowników, uruchom następujące polecenie:
  
```powershell
Get-AzureADUser
```

Powinny zostać wyświetlone informacje podobne do następujących:
  
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

Aby wyświetlić określone konto użytkownika, uruchom następujące polecenie. Podaj nazwę konta logowania konta użytkownika, która jest również znana jako główna nazwa użytkownika (UPN). Usuń znaki "<" i ">".
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Oto przykład:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Wyświetlanie dodatkowych wartości właściwości dla określonego konta

Domyślnie polecenie cmdlet **Get-AzureADUser** wyświetla tylko właściwości *ObjectID*, *DisplayName* i *UserPrincipalName* kont.

Aby być bardziej selektywnym względem właściwości do wyświetlenia, użyj polecenia cmdlet **Wybierz** w połączeniu z poleceniem cmdlet **Get-AzureADUser** . Aby połączyć dwa polecenia cmdlet, użyj znaku "pipe" ("|"), który informuje Azure Active Directory programu PowerShell, aby Graph pobierał wyniki jednego polecenia i wysyłał je do następnego polecenia. Oto przykładowe polecenie, które wyświetla wartości *DisplayName*, *Department* i *UsageLocation* dla każdego konta użytkownika:
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).
    
1.  Wyświetl tylko nazwę konta użytkownika, dział i **lokalizację użycia (wybierz pozycję Nazwa wyświetlana, Dział, UsageLocation**).
  
Aby wyświetlić wszystkie właściwości określonego konta użytkownika, użyj polecenia cmdlet **Wybierz** i symbolu wieloznacznego (*). Oto przykład:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

W innym przykładzie uruchom następujące polecenie, aby sprawdzić stan włączenia określonego konta użytkownika:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Wyświetlanie stanu synchronizacji konta

Konta użytkowników mają dwa źródła: 

- Windows Server Active Directory (AD), które są kontami synchronizowanymi z lokalnej usługi AD do chmury.

- konta Azure Active Directory (Azure AD), które są tworzone bezpośrednio w chmurze.

Aby znaleźć konta synchronizowane z lokalnej usługi AD, możesz użyć **następującego** polecenia. Nakazuje programowi PowerShell pobranie wszystkich użytkowników, którzy mają atrybut *DirSyncEnabled* ustawiony na *wartość True*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

Aby znaleźć konta tylko w chmurze, możesz użyć **następującego** polecenia. Nakazuje programowi PowerShell pobranie wszystkich użytkowników, którzy mają atrybut *DirSyncEnabled* ustawiony na *wartość False* lub nie ustawiono wartości (*Null*).
Konto, które nigdy nie zostało zsynchronizowane z lokalnej usługi AD, ma wartość *DirSyncEnabled* ustawioną na *wartość Null*. Konto, które zostało zsynchronizowane początkowo z lokalnej usługi AD, ale nie jest już synchronizowane, ma wartość *DirSyncEnabled* ustawioną na *wartość False*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>Wyświetlanie kont na podstawie wspólnej właściwości

Aby być bardziej selektywnym względem listy kont do wyświetlenia, możesz użyć polecenia cmdlet **Where** w połączeniu z poleceniem cmdlet **Get-AzureADUser** . Aby połączyć dwa polecenia cmdlet, użyj znaku "pipe" ("|"), który informuje Azure Active Directory programu PowerShell, aby Graph pobierał wyniki jednego polecenia i wysyłał je do następnego polecenia. Oto przykładowe polecenie, które wyświetla tylko te konta użytkowników, które mają nieokreśloną lokalizację użycia:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

To polecenie instruuje Azure Active Directory programu PowerShell, aby Graph:
  
1. Pobierz wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).
    
1. Znajdź wszystkie konta użytkowników, które mają nieokreśloną lokalizację użycia (**gdzie {$\_). UsageLocation -eq $Null}**). Wewnątrz nawiasów klamrowych polecenie instruuje program PowerShell, aby odnalazł tylko zestaw kont, dla których właściwość konta użytkownika UsageLocation (**$\_. UsageLocation**) nie jest określony (**-eq $Null**).
    
**Właściwość UsageLocation** jest tylko jedną z wielu właściwości skojarzonych z kontem użytkownika. Aby wyświetlić wszystkie właściwości określonego konta użytkownika, użyj polecenia cmdlet **Wybierz** i symbolu wieloznacznego (*). Oto przykład:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Na przykład **city** to nazwa właściwości konta użytkownika. Aby wyświetlić listę wszystkich kont użytkowników mieszkających w Londynie, możesz użyć następującego polecenia:
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Składnia polecenia cmdlet **Where** w tych przykładach to **Where {$\_.** [nazwa właściwości konta użytkownika] [operator porównania] [wartość] **}**.> [operator porównania] to **-eq** dla równości, **-ne** dla nie równa się, **-lt** dla mniejszej niż, **-gt** dla większej niż i innych.  [value] jest zwykle ciągiem (sekwencją liter, cyfr i innych znaków), wartością liczbową lub **$Null** dla nieokreślonych. Aby uzyskać więcej informacji, zobacz [Gdzie](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Wyświetl wszystkie konta

Aby wyświetlić pełną listę kont użytkowników, uruchom następujące polecenie:
  
```powershell
Get-MsolUser
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą *msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
>

Powinny zostać wyświetlone informacje podobne do następujących:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Polecenie cmdlet **Get-MsolUser** ma również zestaw parametrów do filtrowania wyświetlonego zestawu kont użytkowników. Na przykład dla listy nielicencjonowanych użytkowników (użytkowników, którzy zostali dodaowani do Microsoft 365 ale nie mają jeszcze licencji na korzystanie z żadnej z tych usług), uruchom następujące polecenie:
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Powinny zostać wyświetlone informacje podobne do następujących:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Aby uzyskać informacje o dodatkowych parametrach do filtrowania zestawu wyświetlanych kont użytkowników, zobacz [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Wyświetlanie określonego konta

Aby wyświetlić określone konto użytkownika, uruchom następujące polecenie. Podaj nazwę logowania konta użytkownika, które jest również nazywane główną nazwą użytkownika (UPN). Usuń znaki "<" i ">".
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Wyświetlanie kont na podstawie wspólnej właściwości

Aby być bardziej selektywnym względem listy kont do wyświetlenia, możesz użyć polecenia cmdlet **Where** w połączeniu z poleceniem cmdlet **Get-MsolUser** . Aby połączyć dwa polecenia cmdlet, użyj znaku "pipe" ("|"), który nakazuje programowi PowerShell wykonanie wyników jednego polecenia i wysłanie go do następnego polecenia. Oto przykład przedstawiający tylko te konta użytkowników, które mają nieokreśloną lokalizację użycia:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje na temat kont użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).
    
1. Znajdź wszystkie konta użytkowników, które mają nieokreśloną lokalizację użycia (**gdzie {$\_). UsageLocation -eq $Null}**). Wewnątrz nawiasów klamrowych polecenie instruuje program PowerShell, aby odnalazł tylko zestaw kont, dla których właściwość konta użytkownika UsageLocation (**$\_. UsageLocation**) nie jest określony (**-eq $Null**).
    
Powinny zostać wyświetlone informacje podobne do następujących:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

*Właściwość UsageLocation* jest tylko jedną z wielu właściwości skojarzonych z kontem użytkownika. Aby wyświetlić wszystkie właściwości kont użytkowników, użyj polecenia cmdlet **Wybierz** i symbolu wieloznacznego (*), aby wyświetlić je wszystkie dla określonego konta użytkownika. Oto przykład:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Na przykład *city* to nazwa właściwości konta użytkownika. Możesz użyć następującego polecenia, aby wyświetlić listę wszystkich kont użytkowników dla użytkowników mieszkających w Londynie:
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Składnia polecenia cmdlet **Where** w tych przykładach to **Where {$\_.** [nazwa właściwości konta użytkownika] [operator porównania] [wartość] **}**.  [operator porównania] jest **-eq** dla równości, **-ne** dla nie równa, **-lt** dla mniej niż, **-gt** dla większe niż i inne.  [value] jest zwykle ciągiem (sekwencją liter, cyfr i innych znaków), wartością liczbową lub **$Null** dla nieokreślonych. Aby uzyskać więcej informacji, zobacz [Gdzie](/powershell/module/microsoft.powershell.core/where-object).
  
Aby sprawdzić zablokowany stan konta użytkownika, użyj następującego polecenia:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Wyświetlanie dodatkowych wartości właściwości dla kont

Domyślnie polecenie cmdlet **Get-MsolUser** wyświetla te trzy właściwości kont użytkowników:
  
- Userprincipalname

- Displayname

- isLicensed

Jeśli potrzebujesz dodatkowych właściwości, takich jak dział, w którym pracuje użytkownik, oraz kraj/region, w którym korzysta z usług Microsoft 365, możesz uruchomić polecenie **Get-MsolUser w połączeniu** z poleceniem cmdlet **Wybierz**, aby określić listę właściwości konta użytkownika. Oto przykład:
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje o kontach użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).
    
1. Wyświetl tylko nazwę konta użytkownika, dział i **lokalizację użycia (wybierz pozycję Nazwa wyświetlana, Dział, UsageLocation**).
    
Powinny zostać wyświetlone informacje podobne do następujących:
  
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

Polecenie cmdlet **Wybierz** umożliwia wybranie właściwości do wyświetlenia. Aby wyświetlić wszystkie właściwości określonego konta użytkownika, użyj symbolu wieloznacznego (*). Oto przykład:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Aby być bardziej selektywnym względem listy kont do wyświetlenia, możesz również użyć polecenia cmdlet **Where** . Oto przykładowe polecenie, które wyświetla tylko te konta użytkowników, które mają nieokreśloną lokalizację użycia:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje o kontach użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).
    
1. Znajdź wszystkie konta użytkowników, które mają nieokreśloną lokalizację użycia (**gdzie {$\_). UsageLocation -eq $Null}**) i wyślij wynikowe informacje do następnego polecenia (**|**). Wewnątrz nawiasów klamrowych polecenie instruuje program PowerShell, aby odnalazł tylko zestaw kont, dla których właściwość konta użytkownika UsageLocation (**$\_. UsageLocation**) nie jest określony (**-eq $Null**).
    
1. Wyświetl tylko nazwę konta użytkownika, dział i **lokalizację użycia (wybierz pozycję Nazwa wyświetlana, Dział, UsageLocation**).
    
Powinny zostać wyświetlone informacje podobne do następujących:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Jeśli używasz synchronizacji katalogów do tworzenia Microsoft 365 użytkowników i zarządzania nimi, możesz wyświetlić konto lokalne, z którego został wyświetlony Microsoft 365 użytkownik. W poniższym przykładzie przyjęto założenie, że:

- Usługa Azure AD Połączenie jest skonfigurowana do używania domyślnej kotwicy źródłowej identyfikatora ObjectGUID. (Aby uzyskać więcej informacji na temat konfigurowania kotwicy źródła, zobacz [Azure AD Połączenie: Pojęcia dotyczące projektowania](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- Zainstalowano moduł Active Directory Domain Services programu PowerShell (zobacz [narzędzia RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie za pomocą programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
