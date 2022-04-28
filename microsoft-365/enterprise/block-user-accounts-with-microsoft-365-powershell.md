---
title: Blokowanie kont użytkowników Microsoft 365 przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/16/2020
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
- seo-marvel-apr2020
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Jak zablokować i odblokować dostęp do kont Microsoft 365 przy użyciu programu PowerShell.
ms.openlocfilehash: ffeac03f9f48e6531443a8f90a3d5fd3506172fe
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091616"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>Blokowanie kont użytkowników Microsoft 365 przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Gdy blokujesz dostęp do konta Microsoft 365, uniemożliwiasz każdemu użytkownikowi logowanie się i uzyskiwanie dostępu do usług i danych w organizacji Microsoft 365. Za pomocą programu PowerShell można zablokować dostęp do kont użytkowników indywidualnych lub wielu użytkowników.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="block-access-to-individual-user-accounts"></a>Blokowanie dostępu do poszczególnych kont użytkowników

Użyj następującej składni, aby zablokować konto użytkownika:

```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Parametr *-ObjectID* w poleceniu cmdlet **Set-AzureAD** akceptuje nazwę logowania konta, znaną również jako główna nazwa użytkownika, lub identyfikator obiektu konta.

Ten przykład blokuje dostęp do *fabricec@litwareinc.com* konta użytkownika.

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Aby odblokować to konto użytkownika, uruchom następujące polecenie:

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Aby wyświetlić nazwę UPN konta użytkownika na podstawie nazwy wyświetlanej użytkownika, użyj następujących poleceń:

```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

W tym przykładzie jest wyświetlana nazwa UPN konta użytkownika  *Caleb Sills*.

```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Aby zablokować konto na podstawie nazwy wyświetlanej użytkownika, użyj następujących poleceń:

```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

Aby sprawdzić zablokowany stan konta użytkownika, użyj następującego polecenia:

```powershell
Get-AzureADUser  -ObjectID <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-multiple-user-accounts"></a>Blokowanie wielu kont użytkowników

Aby zablokować dostęp dla wielu kont użytkowników, utwórz plik tekstowy zawierający jedną nazwę logowania do konta w każdym wierszu w następujący sposób:

  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

W poniższych poleceniach przykładowy plik tekstowy to *C:\My Documents\Accounts.txt*. Zastąp tę nazwę pliku ścieżką i nazwą pliku tekstowego.

Aby zablokować dostęp do kont wymienionych w pliku tekstowym, uruchom następujące polecenie:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $false}
```

Aby odblokować konta wymienione w pliku tekstowym, uruchom następujące polecenie:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $true}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="block-individual-user-accounts"></a>Blokuj indywidualne konta użytkowników

Użyj następującej składni, aby zablokować dostęp do pojedynczego konta użytkownika:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet, które mają nazwę *msol*. Musisz uruchomić te polecenia cmdlet z Windows PowerShell.

Ten przykład blokuje dostęp do sieci *szkieletowej\@* konta użytkownika litwareinc.com.

```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Aby odblokować konto użytkownika, uruchom następujące polecenie:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

Aby sprawdzić zablokowany stan konta użytkownika, uruchom następujące polecenie:

```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-for-multiple-user-accounts"></a>Blokowanie dostępu dla wielu kont użytkowników

Najpierw utwórz plik tekstowy zawierający jedno konto w każdym wierszu w następujący sposób:

```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

W poniższych poleceniach przykładowy plik tekstowy to *C:\My Documents\Accounts.txt*. Zastąp tę nazwę pliku ścieżką i nazwą pliku tekstowego.

Aby zablokować dostęp do kont wymienionych w pliku tekstowym, uruchom następujące polecenie:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Aby odblokować konta wymienione w pliku tekstowym, uruchom następujące polecenie:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie za pomocą programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
