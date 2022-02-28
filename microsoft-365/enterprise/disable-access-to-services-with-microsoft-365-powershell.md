---
title: Wyłączanie dostępu do usług Microsoft 365 za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Z tego artykułu dowiesz się, jak za pomocą programu PowerShell wyłączyć użytkownikom dostęp Microsoft 365 usługach firmy Microsoft.
ms.openlocfilehash: bce02c40bf6ca99d74b8747fb0c5eb5c0b485888
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985485"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>Wyłączanie dostępu do usług Microsoft 365 za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Po przypisaniu Microsoft 365 użytkownika z planu licencjonowania usługi Microsoft 365 są dostępne dla użytkownika z tej licencji. Możesz jednak kontrolować, do Microsoft 365 do których użytkownik może uzyskać dostęp. Na przykład, nawet jeśli licencja zezwala na dostęp do usługi SharePoint Online, możesz wyłączyć dostęp do niej. Za pomocą programu PowerShell możesz wyłączyć dostęp do dowolnej liczby usług w określonym planie licencjonowania:

- Pojedyncze konto.
- Grupa kont.
- Wszystkie konta w organizacji.

>[!Note]
>Istnieją Microsoft 365 usługi, które mogą uniemożliwiać wyłączenie określonej usługi, gdy inne usługi są od nich zależne.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Następnie użyj tego polecenia, aby wyświetlić dostępne plany licencjonowania, znane również jako AccountSkuIds:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z **nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z Windows PowerShell.
>

Aby uzyskać więcej informacji, [zobacz Wyświetlanie licencji i usług za pomocą programu PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).
    
Aby wyświetlić wyniki procedur przed i po nich w tym temacie, zobacz Wyświetlanie szczegółów licencji konta i usługi za [pomocą programu PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
Dostępny jest skrypt programu PowerShell automatyzujący procedury opisane w tym temacie. W szczególności skrypt umożliwia wyświetlanie i wyłączanie usług w Twojej organizacji Microsoft 365, w tym aplikacji Sway. Aby uzyskać więcej informacji, zobacz [Wyłączanie dostępu do aplikacji Sway za pomocą programu PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Wyłączanie określonych Microsoft 365 usługi dla określonych użytkowników w określonym planie licencjonowania
  
Aby wyłączyć określony zestaw usług Microsoft 365 dla użytkowników w określonym planie licencjonowania, wykonaj następujące czynności:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Krok 1. Określ niepożądane usługi w planie licencjonowania, stosując następującą składnię:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

Poniższy przykład tworzy obiekt **LicenseOptions**, który wyłącza usługi Office i SharePoint Online w planie `litwareinc:ENTERPRISEPACK` licencjonowania o nazwie (Office 365 Enterprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>Krok 2. Użyj **obiektu LicenseOptions z** kroku 1 na jednym lub większej liczby użytkowników.
    
Aby utworzyć nowe konto z wyłączonymi usługami, użyj następującej składni:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

W poniższym przykładzie allie Bellew tworzy nowe konto, które przypisuje licencję i wyłącza usługi opisane w kroku 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Aby uzyskać więcej informacji na temat tworzenia kont użytkowników w programie PowerShell dla komputerów Microsoft 365, zobacz [Tworzenie kont użytkowników za pomocą programu PowerShell](create-user-accounts-with-microsoft-365-powershell.md).
    
Aby wyłączyć usługi dla istniejącego licencjonowanego użytkownika, użyj następującej składni:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

W tym przykładzie usługi dla użytkownika są BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

Aby wyłączyć usługi opisane w kroku 1 dla wszystkich istniejących licencjonowanych użytkowników, określ nazwę planu usługi Microsoft 365 na ekranie polecenia cmdlet **Get-MsolAccountSku** (na przykład **litwareinc:ENTERPRISEPACK**), a następnie uruchom następujące polecenia:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 Jeśli używasz polecenia **cmdlet Get-MsolUser** bez użycia _parametru All_ , zwracanych jest tylko pierwszych 500 kont użytkowników.

Aby wyłączyć usługi dla grupy istniejących użytkowników, należy użyć jednej z następujących metod identyfikacji użytkowników:
    
**Metoda 1. Filtrowanie kont na podstawie istniejącego atrybutu konta** 

W tym celu użyj następującej składni:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

W poniższym przykładzie wyłączyno usługi dla użytkowników w dziale sprzedaży w Stanach Zjednoczonych.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Metoda 2. Korzystanie z listy określonych kont** 

W tym celu wykonaj następujące czynności:
    
1. Utwórz plik tekstowy zawierający jedno konto w każdym wierszu w ten sposób:
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   W tym przykładzie plik tekstowy to C:\\Moje dokumenty\\Accounts.txt.
    
2. Uruchom następujące polecenie:
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

Jeśli chcesz wyłączyć dostęp do usług dla wielu planów licencjonowania, powtórz powyższe instrukcje dla każdego planu licencjonowania, upewniając się, że:

- Do kont użytkowników przypisano plan licencjonowania.
- Usługi do wyłączenia są dostępne w planie licencjonowania.

Aby wyłączyć Microsoft 365 dla użytkowników podczas przypisywania ich do planu licencjonowania, zobacz Wyłączanie dostępu do usług [podczas przypisywania licencji użytkowników](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>Przypisywanie wszystkich usług w planie licencjonowania do konta użytkownika

W przypadku kont użytkowników z wyłączonymi usługami możesz włączyć wszystkie usługi w określonym planie licencjonowania za pomocą tych poleceń:

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>Temat pokrewny

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
