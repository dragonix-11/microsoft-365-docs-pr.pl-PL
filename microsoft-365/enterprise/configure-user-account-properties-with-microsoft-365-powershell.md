---
title: Konfigurowanie Microsoft 365 właściwości konta użytkownika przy użyciu programu PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- admindeeplinkMAC
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Użyj programu PowerShell do Microsoft 365, aby skonfigurować właściwości poszczególnych lub wielu kont użytkowników w dzierżawie Microsoft 365.
ms.openlocfilehash: 3a1aa77a6af3995d7cd4d072b6b6c6047bf89942
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091352"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Konfigurowanie Microsoft 365 właściwości konta użytkownika przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Za pomocą <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> można skonfigurować właściwości dla kont użytkowników dzierżawy Microsoft 365. W programie PowerShell można również to zrobić, a także inne rzeczy, których nie można wykonać w centrum administracyjnym.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Aby skonfigurować właściwości kont użytkowników w module Azure Active Directory programu PowerShell dla Graph, użyj polecenia cmdlet [**Set-AzureADUser**](/powershell/module/azuread/set-azureaduser) i określ właściwości do ustawienia lub zmiany.

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>Zmienianie właściwości określonego konta użytkownika

Należy zidentyfikować konto za pomocą parametru *-ObjectID* i ustawić lub zmienić określone właściwości przy użyciu dodatkowych parametrów. Oto lista najpopularniejszych parametrów:
  
- -Dział "\<department name>"

- -DisplayName "\<full user name>"

- -FacsimilieTelephoneNumber "\<fax number>"

- -GivenName "\<user first name>"

- -Nazwisko "\<user last name>"

- -Mobile "\<mobile phone number>"

- -JobTitle "\<job title>"

- -PreferredLanguage "\<language>"

- -StreetAddress "\<street address>"

- -City "\<city name>"

- -State "\<state name>"

- -PostalCode "\<postal code>"

- -Country "\<country name>"

- -TelephoneNumber "\<office phone number>"

- -UsageLocation "\<2-character country or region code>"

    Jest to dwuliterowy kod kraju lub regionu ISO 3166-1 alfa-2 (A2).

Aby uzyskać dodatkowe parametry, zobacz [Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> Przed przypisaniem licencji do konta użytkownika należy przypisać lokalizację użycia.

Aby wyświetlić główną nazwę użytkownika dla kont użytkowników, uruchom następujące polecenie.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).

1. Posortuj listę nazw głównych użytkowników alfabetycznie (**Sortuj nazwę UserPrincipalName**) i wyślij ją do następnego polecenia (**|**).

1. Wyświetl tylko właściwość Główna nazwa użytkownika dla każdego konta (**wybierz pozycję UserPrincipalName**).

1. Wyświetlaj je po jednym ekranie (**więcej**).

Aby wyświetlić główną nazwę użytkownika dla konta na podstawie jego nazwy wyświetlanej (imię i nazwisko), uruchom następujące polecenia. Wypełnij zmienną *$userName* i usuń \< and > znaki:
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

W tym przykładzie jest wyświetlana główna nazwa użytkownika konta użytkownika o nazwie wyświetlanej *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Przy użyciu zmiennej *$upn* można wprowadzać zmiany w poszczególnych kontach na podstawie ich nazwy wyświetlanej. Oto przykład, który ustawia lokalizację użycia *Belindy Newman* na Francję. Określa jednak jej nazwę wyświetlaną, a nie główną nazwę użytkownika:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Zmienianie właściwości dla wszystkich kont użytkowników

Aby zmienić właściwości dla wszystkich użytkowników, możesz użyć kombinacji poleceń cmdlet **Get-AzureADUser** i **Set-AzureADUser** . Poniższy przykład zmienia lokalizację użycia dla wszystkich użytkowników na *Francję*:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).

1. Ustaw lokalizację użytkownika na Francja (**Set-AzureADUser -UsageLocation "FR").**

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Zmienianie właściwości określonego zestawu kont użytkowników

Aby zmienić właściwości określonego zestawu kont użytkowników, możesz użyć kombinacji poleceń cmdlet **Get-AzureADUser**, **Where** i **Set-AzureADUser** . Poniższy przykład zmienia lokalizację użycia dla wszystkich użytkowników w dziale księgowości na *Francję*:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).

1.  Znajdź wszystkie konta użytkowników, których właściwość *Dział* ma ustawioną wartość "Księgowość" (**gdzie {$_. Dział -eq "Księgowość"}**) i wyślij wynikowe informacje do następnego polecenia (**|**).

1. Ustaw lokalizację użytkownika na Francja (**Set-AzureADUser -UsageLocation "FR").**

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Aby skonfigurować właściwości kont użytkowników przy użyciu modułu Microsoft Azure Active Directory dla Windows PowerShell, użyj polecenia cmdlet **Set-MsolUser** i określ właściwości do ustawienia lub zmiany.

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą *msol*. Uruchom te polecenia cmdlet z Windows PowerShell.

### <a name="change-properties-for-a-specific-user-account"></a>Zmienianie właściwości określonego konta użytkownika

Aby skonfigurować właściwości dla określonego konta użytkownika, użyj polecenia cmdlet [**Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) i określ właściwości do ustawienia lub zmiany. 

Należy zidentyfikować konto za pomocą parametru *-UserPrincipalName* i ustawić lub zmienić określone właściwości przy użyciu dodatkowych parametrów. Oto lista najpopularniejszych parametrów.
  
- -City "\<city name>"

- -Country "\<country name>"

- -Dział "\<department name>"

- -DisplayName "\<full user name>"

- -Faks "\<fax number>"

- -FirstName "\<user first name>"

- -LastName "\<user last name>"

- -MobilePhone "\<mobile phone number>"

- -Office "\<office location>"

- -PhoneNumber "\<office phone number>"

- -PostalCode "\<postal code>"

- -PreferredLanguage "\<language>"

- -State "\<state name>"

- -StreetAddress "\<street address>"

- -Tytuł "\<title name>"

- -UsageLocation "\<2-character country or region code>"

    Jest to dwuliterowy kod kraju lub regionu ISO 3166-1 alfa-2 (A2).

Aby uzyskać dodatkowe parametry, zobacz [Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

Aby wyświetlić główne nazwy użytkowników wszystkich użytkowników, uruchom następujące polecenie:
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje dotyczące kont użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).

1. Posortuj listę nazw głównych użytkowników alfabetycznie (**Sortuj nazwę UserPrincipalName**) i wyślij ją do następnego polecenia (**|**).

1. Wyświetl tylko właściwość Główna nazwa użytkownika dla każdego konta (**wybierz pozycję UserPrincipalName**).

1. Wyświetlaj je po jednym ekranie (**więcej**).

Aby wyświetlić główną nazwę użytkownika dla konta na podstawie jego nazwy wyświetlanej (imię i nazwisko), uruchom następujące polecenia. Wypełnij zmienną *$userName* i usuń \< and > znaki.
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

W tym przykładzie jest wyświetlana główna nazwa użytkownika o nazwie Caleb Sills:
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Przy użyciu zmiennej *$upn* można wprowadzać zmiany w poszczególnych kontach na podstawie ich nazwy wyświetlanej. Oto przykład, który ustawia lokalizację użycia *Belindy Newman* na *Francję*, ale określa jej nazwę wyświetlaną, a nie główną nazwę użytkownika:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Zmienianie właściwości dla wszystkich kont użytkowników

Aby zmienić właściwości dla wszystkich użytkowników, użyj kombinacji poleceń cmdlet **Get-MsolUser** i **Set-MsolUser** . Poniższy przykład zmienia lokalizację użycia dla wszystkich użytkowników na *Francję*:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje dotyczące kont użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).

1. Ustaw lokalizację użytkownika na Francja (**Set-MsolUser -UsageLocation "FR").**

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Zmienianie właściwości określonego zestawu kont użytkowników

Aby zmienić właściwości określonego zestawu kont użytkowników, można użyć kombinacji poleceń cmdlet **Get-MsolUser**, **Where** i **Set-MsolUser** . Poniższy przykład zmienia lokalizację użycia dla wszystkich użytkowników w dziale księgowości na *Francję*:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

To polecenie instruuje program PowerShell, aby:
  
1. Pobierz wszystkie informacje dotyczące kont użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).

1. Znajdź wszystkie konta użytkowników, których właściwość *Dział* ma ustawioną wartość "Księgowość" (**gdzie {$_. Dział -eq "Księgowość"}**) i wyślij wynikowe informacje do następnego polecenia (**|**).

1. Ustaw lokalizację użytkownika na Francja (**Set-MsolUser -UsageLocation "FR").**

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie za pomocą programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
