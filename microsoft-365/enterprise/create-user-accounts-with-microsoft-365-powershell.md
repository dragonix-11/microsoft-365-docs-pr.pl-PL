---
title: Tworzenie kont użytkowników platformy Microsoft 365 przy użyciu programu PowerShell
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
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Jak używać programu PowerShell do tworzenia indywidualnych lub wielu kont użytkowników platformy Microsoft 365.
ms.openlocfilehash: 9f96c5a96e014055622deb34c37cb8523f0041f8
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930246"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>Tworzenie kont użytkowników platformy Microsoft 365 przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno platformy Microsoft 365 Enterprise, jak i usługi Office 365 Enterprise.*

Program PowerShell dla platformy Microsoft 365 umożliwia wydajne tworzenie kont użytkowników, w tym wielu kont.

Podczas tworzenia kont użytkowników w programie PowerShell niektóre właściwości konta są zawsze wymagane. Inne właściwości nie są wymagane, ale są ważne. Zobacz poniższą tabelę.
  
|**Nazwa właściwości**|**Wymagany?**|**Opis**|
|:-----|:-----|:-----|
|**Displayname** <br/> |Tak  <br/> |Jest to nazwa wyświetlana używana w usługach Platformy Microsoft 365. Na przykład *Caleb Sills*. <br/> |
|**Userprincipalname** <br/> |Tak  <br/> |Jest to nazwa konta używana do logowania się do usług platformy Microsoft 365. Na przykład *CalebS\@contoso.onmicrosoft.com*.  <br/> |
|**Imię** <br/> |Nie  <br/> ||
|**Nazwisko** <br/> |Nie  <br/> ||
|**LicenseAssignment** <br/> |Nie  <br/> |Jest to plan licencjonowania (znany również jako [plan licencji lub jednostka SKU](/azure/active-directory/enterprise-users/licensing-service-plan-reference)), z którego dostępna licencja jest przypisywana do konta użytkownika. Licencja definiuje usługi platformy Microsoft 365, które są dostępne dla konta. Nie musisz przypisywać licencji użytkownikowi podczas tworzenia konta, ale konto musi mieć licencję na dostęp do usług platformy Microsoft 365. Po utworzeniu konta użytkownika masz 30 dni na licencję. |
|**Password (hasło)** <br/> |Nie  <br/> | Jeśli nie określisz hasła, losowe hasło zostanie przypisane do konta użytkownika, a hasło będzie widoczne w wynikach polecenia. W przypadku określenia hasła musi ono zawierać od 8 do 16 znaków tekstowych ASCII następujących typów: małe litery, wielkie litery, cyfry i symbole.<br/> |
|**UsageLocation** <br/> |Nie  <br/> |Jest to prawidłowy kod kraju ISO 3166-1 alfa-2. Na przykład *stany USA* dla Stanów Zjednoczonych i *FR* dla Francji. Należy podać tę wartość, ponieważ niektóre usługi platformy Microsoft 365 nie są dostępne w niektórych krajach. Nie można przypisać licencji do konta użytkownika, chyba że konto ma skonfigurowaną tę wartość. Aby uzyskać więcej informacji, zobacz [About license restrictions (Informacje o ograniczeniach licencji](https://go.microsoft.com/fwlink/p/?LinkId=691730)).<br/> |

>[!Note]
>[Dowiedz się, jak tworzyć konta użytkowników](../admin/add-users/add-users.md) przy użyciu centrum administracyjnego platformy Microsoft 365.
> 
> Aby uzyskać listę dodatkowych zasobów, zobacz [Zarządzanie użytkownikami i grupami](/admin).
>   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory PowerShell for Graph

Najpierw [połącz się z dzierżawą platformy Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Po nawiązaniu połączenia użyj następującej składni, aby utworzyć indywidualne konto:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

W tym przykładzie utworzono konto użytkownika z USA *, Caleba Sillsa*:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Korzystanie z modułu usługi Microsoft Azure Active Directory dla programu Windows PowerShell

Najpierw [połącz się z dzierżawą platformy Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Tworzenie indywidualnego konta użytkownika

Aby utworzyć indywidualne konto, użyj następującej składni:
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu usługi Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet, które mają nazwę *Msol* . Uruchom te polecenia cmdlet z programu Windows PowerShell.
>

Aby wyświetlić listę dostępnych [nazw planów licencjonowania](/azure/active-directory/enterprise-users/licensing-service-plan-reference), użyj następującego polecenia:

````powershell
Get-MsolAccountSku
````

W tym przykładzie utworzono konto użytkownika z USA *Caleba Sillsa* i przypisano licencję z `contoso:ENTERPRISEPACK` planu licencjonowania (Office 365 Enterprise E3).
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Tworzenie wielu kont użytkowników

1. Utwórz plik wartości rozdzielanej przecinkami (CSV), który zawiera wymagane informacje o koncie użytkownika. Przykład:

     ```powershell
     UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
     ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
     LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
     ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
     ```

   >[!NOTE]
   >Nazwy kolumn i ich kolejność w pierwszym wierszu pliku CSV są dowolne. Upewnij się jednak, że kolejność danych w pozostałej części pliku jest zgodna z kolejnością nazw kolumn. Użyj nazw kolumn dla wartości parametrów w poleceniu programu PowerShell dla platformy Microsoft 365.
    
2. Należy stosować następującą składnię:
    
    ```powershell
     Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
    ```

   Ten przykład tworzy konta użytkowników z pliku *C:\My Documents\NewAccounts.csv* i rejestruje wyniki w pliku o nazwie *C:\My Documents\NewAccountResults.csv*.
    
    ```powershell
    Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
    ```

3. Przejrzyj plik wyjściowy, aby wyświetlić wyniki. Nie określiliśmy haseł, więc losowe hasła wygenerowane przez platformę Microsoft 365 są widoczne w pliku wyjściowym.
    
## <a name="see-also"></a>Zobacz też

[Zarządzanie kontami, licencjami i grupami użytkowników platformy Microsoft 365 przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla platformy Microsoft 365](getting-started-with-microsoft-365-powershell.md)
