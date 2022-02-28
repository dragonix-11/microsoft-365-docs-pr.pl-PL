---
title: Tworzenie Microsoft 365 użytkowników za pomocą programu PowerShell
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
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Jak za pomocą programu PowerShell tworzyć pojedyncze lub wiele Microsoft 365 kont użytkowników.
ms.openlocfilehash: 7396e98e597491910b639e5a0d0c57b8f685bc02
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985456"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>Tworzenie Microsoft 365 użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Za pomocą programu PowerShell Microsoft 365 wydajnie tworzyć konta użytkowników, w tym wiele kont.

Podczas tworzenia kont użytkowników w programie PowerShell zawsze są wymagane pewne właściwości konta. Inne właściwości nie są wymagane, ale są ważne. Zobacz następującą tabelę.
  
|**Nazwa właściwości**|**Wymagany?**|**Opis**|
|:-----|:-----|:-----|
|**DisplayName (Nazwa wyświetlana)** <br/> |Tak  <br/> |Jest to nazwa wyświetlana, która jest używana w Microsoft 365 usługach. Na przykład *Caleb Sills*. <br/> |
|**UserPrincipalName (Nazwa użytkownika)** <br/> |Tak  <br/> |Jest to nazwa konta, która jest używana do logowania się do Microsoft 365 usług. Na przykład *CalebS\@ contoso.onmicrosoft.com*.  <br/> |
|**Imię** <br/> |Nie  <br/> ||
|**Nazwisko** <br/> |Nie  <br/> ||
|**LicenseAssignment** <br/> |Nie  <br/> |Jest to plan licencjonowania (nazywany również planem licencji lub licencją SKU), z którego do konta użytkownika jest przypisana dostępna licencja. Licencja określa Microsoft 365 usług dostępnych dla tego konta. Podczas tworzenia konta nie trzeba przypisywać licencji do użytkownika, ale konto musi mieć licencję na dostęp do Microsoft 365 usług. Masz 30 dni na licencję konta użytkownika po jego utworzeniu. |
|**Password (hasło)** <br/> |Nie  <br/> | Jeśli hasło nie zostanie określone, do konta użytkownika zostanie przypisane losowe hasło, które będzie widoczne w wynikach polecenia. Hasło musi mieć od 8 do 16 znaków ascii następujących typów: małe litery, wielkie litery, cyfry i symbole.<br/> |
|**Lokalizacja użytkowania** <br/> |Nie  <br/> |Jest to prawidłowy kod kierunkowy kraju ISO 3166-1 alfa-2. Na przykład *STANY ZJEDNOCZONE* , a *FR* dla Francji. Warto podać tę wartość, ponieważ niektóre Microsoft 365 są niedostępne w niektórych krajach. Nie można przypisać licencji do konta użytkownika, jeśli dla konta nie skonfigurowano tej wartości. Aby uzyskać więcej informacji, zobacz [Informacje o ograniczeniach licencyjnych](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |

>[!Note]
>[Dowiedz się, jak tworzyć konta użytkowników](../admin/add-users/add-users.md) przy użyciu centrum administracyjne platformy Microsoft 365.
> 
> Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Po nawiązania połączenia utwórz pojedyncze konto przy użyciu następującej składni:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

W tym przykładzie jest konto użytkownika *Caleb Sills* w Usa:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Tworzenie indywidualnego konta użytkownika

Aby utworzyć pojedyncze konto, użyj następującej składni:
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet, których *nazwa zawiera Msol*. Uruchom te polecenia cmdlet z Windows PowerShell.
>

Aby wyświetlić listę dostępnych nazw planów licencjonowania, użyj tego polecenia:

````powershell
Get-MsolAccountSku
````

W tym przykładzie jest dzielone konto użytkownika *Caleb Sills* w Usa i `contoso:ENTERPRISEPACK` przypisywana jest licencja z planu licencjonowania (Office 365 Enterprise E3).
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Tworzenie wielu kont użytkowników

1. Utwórz plik wartości rozdzielanych przecinkami (CSV) zawierający wymagane informacje o koncie użytkownika. Przykład:

     ```powershell
     UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
     ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
     LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
     ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
     ```

   >[!NOTE]
   >Nazwy kolumn i ich kolejność w pierwszym wierszu pliku CSV są dowolne. Upewnij się jednak, że kolejność danych w pozostałej części pliku jest zgodnie z kolejnością nazw kolumn. Następnie użyj nazw kolumn dla wartości parametrów w programie PowerShell dla Microsoft 365 wiersza.
    
2. Należy stosować następującą składnię:
    
    ```powershell
     Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
    ```

   W tym przykładzie są tworzyne konta użytkowników z pliku *C:\Moje Documents\NewAccounts.csv* i dzienniki wyników w pliku o *nazwie C:\Moje Documents\NewAccountResults.csv*.
    
    ```powershell
    Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
    ```

3. Przejrzyj plik wyjściowy, aby wyświetlić wyniki. Nie określiliśmy haseł, więc losowe hasła, które Microsoft 365 generowane, są widoczne w pliku wyjściowym.
    
## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)