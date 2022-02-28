---
title: Konfigurowanie Microsoft 365 konta użytkownika za pomocą programu PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- admindeeplinkMAC
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Za pomocą programu PowerShell Microsoft 365 do konfigurowania właściwości pojedynczych lub wielu kont użytkowników w Microsoft 365 dzierżawie.
ms.openlocfilehash: 01b17837e4babc31d385be66f9387129baf87da1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984456"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Konfigurowanie Microsoft 365 konta użytkownika za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Za pomocą <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">tego centrum administracyjne platformy Microsoft 365 do</a> skonfigurowania właściwości kont użytkowników w Microsoft 365 dzierżawie. W programie PowerShell możesz również to zrobić oraz wykonać inne czynności, których nie możesz wykonać w centrum administracyjnym.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Aby skonfigurować właściwości kont użytkowników w module Azure Active Directory PowerShell dla programu Graph, użyj polecenia cmdlet [**Set-AzureADUser**](/powershell/module/azuread/set-azureaduser) i określ właściwości do ustawienia lub zmiany.

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>Zmienianie właściwości konkretnego konta użytkownika

Możesz określić konto za pomocą *parametru -ObjectID* i ustawić lub zmienić określone właściwości przy użyciu dodatkowych parametrów. Poniżej podano listę najbardziej typowych parametrów:
  
- -Dział "\<department name>"

- -DisplayName "\<full user name>"

- -FacsimilieTelephoneNumber "\<fax number>"

- -GivenName "\<user first name>"

- -Surname "\<user last name>"

- — Urządzenie przenośne "\<mobile phone number>"

- -JobTitle "\<job title>"

- -PreferredLanguage "\<language>"

- -StreetAddress "\<street address>"

- — Miasto "\<city name>"

- -Województwo "\<state name>"

- -PostalCode "\<postal code>"

- -Country "\<country name>"

- -TelephoneNumber "\<office phone number>"

- -UsageLocation "\<2-character country or region code>"

    Jest to dwuliterowy kod kraju lub regionu ISO 3166-1 alfa-2 (A2).

Aby uzyskać dodatkowe parametry, [zobacz Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> Aby przypisać licencje do konta użytkownika, musisz przypisać lokalizację użycia.

Aby wyświetlić główną nazwę użytkownika dla kont użytkowników, uruchom następujące polecenie.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).

1. Posortuj listę głównych nazw użytkowników alfabetycznie (**sortuj nazwę UserPrincipalName**) i wyślij ją do następnego polecenia (**|**).

1. Wyświetlanie tylko właściwości User Principal Name (Główna nazwa użytkownika) dla każdego konta (**Select UserPrincipalName**).

1. Wyświetlanie ich po jednym ekranie na raz (**więcej**).

Aby wyświetlić główną nazwę użytkownika dla konta na podstawie jego nazwy wyświetlanej (imię i nazwisko), uruchom następujące polecenia. Wypełnij *zmienną $userName* i usuń \< and > znaki:
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

W tym przykładzie jest wyświetlana główna nazwa użytkownika dla konta użytkownika, które ma nazwę wyświetlaną *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Używając zmiennej *$upn* , możesz wprowadzać zmiany do poszczególnych kont na podstawie ich nazwy wyświetlanej. Oto przykład, który ustawia lokalizację użytkowania *Belindy Newman* we Francji. Jednak zamiast nazwy głównej użytkownika jest określana jej nazwa wyświetlana:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Zmienianie właściwości wszystkich kont użytkowników

Aby zmienić właściwości dla wszystkich użytkowników, możesz użyć kombinacji polecenia cmdlet **Get-AzureADUser** i **Set-AzureADUser** . W poniższym przykładzie zmiana lokalizacji użytkowania dla wszystkich użytkowników *na Francja:*
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje o kontach użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).

1. Ustaw lokalizację użytkownika we Francji (**Set-AzureADUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Zmienianie właściwości określonego zestawu kont użytkowników

Aby zmienić właściwości określonego zestawu kont użytkowników, możesz użyć kombinacji poleceniech **cmdlet Get-AzureADUser**, **Where** i **Set-AzureADUser** . W poniższym przykładzie zmiana lokalizacji użytkowania wszystkich użytkowników w dziale księgowym *na Francja:*
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje na temat kont użytkowników (**Get-AzureADUser**) i wyślij je do następnego polecenia (**|**).

1.  Znajdź wszystkie konta użytkowników, dla których właściwość *Department* (Dział) jest ustawiona na "Accounting" (**Gdzie {$_). Department -eq "Accounting"}**), a następnie wyślij wynikowe informacje do następnego polecenia (**|**).

1. Ustaw lokalizację użytkownika we Francji (**Set-AzureADUser -UsageLocation "FR"**).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Aby skonfigurować właściwości kont użytkowników za pomocą modułu Microsoft Azure Active Directory dla systemu Windows PowerShell, użyj polecenia cmdlet **Set-MsolUser** i określ właściwości do ustawienia lub zmiany.

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z *nazwą Msol*. Uruchom te polecenia cmdlet z Windows PowerShell.

### <a name="change-properties-for-a-specific-user-account"></a>Zmienianie właściwości konkretnego konta użytkownika

Aby skonfigurować właściwości dla określonego konta użytkownika, użyj polecenia cmdlet [**Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) i określ właściwości do ustawienia lub zmiany. 

Możesz zidentyfikować konto za pomocą *parametru -UserPrincipalName* i ustawić lub zmienić określone właściwości, używając dodatkowych parametrów. Oto lista najbardziej typowych parametrów.
  
- — Miasto "\<city name>"

- -Country "\<country name>"

- -Dział "\<department name>"

- -DisplayName "\<full user name>"

- -Faks "\<fax number>"

- -FirstName "\<user first name>"

- -LastName "\<user last name>"

- -MobilePhone "\<mobile phone number>"

- — Office "\<office location>"

- -Numer_telefonu "\<office phone number>"

- -PostalCode "\<postal code>"

- -PreferredLanguage "\<language>"

- -Województwo "\<state name>"

- -StreetAddress "\<street address>"

- - Tytuł "\<title name>"

- -UsageLocation "\<2-character country or region code>"

    Jest to dwuliterowy kod kraju lub regionu ISO 3166-1 alfa-2 (A2).

Aby uzyskać dodatkowe parametry, [zobacz Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

Aby wyświetlić główne nazwy użytkowników wszystkich użytkowników, uruchom następujące polecenie:
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje dotyczące kont użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).

1. Posortuj listę głównych nazw użytkowników alfabetycznie (**sortuj nazwę UserPrincipalName**) i wyślij ją do następnego polecenia (**|**).

1. Wyświetlanie tylko właściwości User Principal Name (Główna nazwa użytkownika) dla każdego konta (**Select UserPrincipalName**).

1. Wyświetlanie ich po jednym ekranie na raz (**więcej**).

Aby wyświetlić główną nazwę użytkownika dla konta na podstawie jego nazwy wyświetlanej (imię i nazwisko), uruchom następujące polecenia. Wypełnij *zmienną $userName* i usuń \< and > znaki.
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

W tym przykładzie jest wyświetlana główna nazwa użytkownika o nazwie Caleb Sills:
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Używając zmiennej *$upn* , możesz wprowadzać zmiany do poszczególnych kont na podstawie ich nazwy wyświetlanej. Oto przykład, w którym lokalizacja użytkowania *Belindy Newman* jest ustawiana we *Francji, ale* jest określana jej nazwa wyświetlana, a nie główna nazwa użytkownika:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Zmienianie właściwości wszystkich kont użytkowników

Aby zmienić właściwości dla wszystkich użytkowników, użyj kombinacji polecenia cmdlet **Get-MsolUser** i **Set-MsolUser** . W poniższym przykładzie zmiana lokalizacji użytkowania dla wszystkich użytkowników *na Francja:*
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje dotyczące kont użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).

1. Ustaw lokalizację użytkownika we Francji (**Set-MsolUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Zmienianie właściwości określonego zestawu kont użytkowników

Aby zmienić właściwości określonego zestawu kont użytkowników, możesz użyć kombinacji poleceniech **cmdlet Get-MsolUser**, **Where** i **Set-MsolUser** . W poniższym przykładzie zmiana lokalizacji użytkowania wszystkich użytkowników w dziale księgowym *na Francja:*
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

To polecenie nakazuje programowi PowerShell:
  
1. Uzyskaj wszystkie informacje dotyczące kont użytkowników (**Get-MsolUser**) i wyślij je do następnego polecenia (**|**).

1. Znajdź wszystkie konta użytkowników, dla których właściwość *Department (* Dział) jest ustawiona na "Accounting" (**Gdzie {$_). Department -eq "Accounting"}**) i wyślij wynikowe informacje do następnego polecenia (**|**).

1. Ustaw lokalizację użytkownika we Francji (**Set-MsolUser -UsageLocation "FR"**).

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
