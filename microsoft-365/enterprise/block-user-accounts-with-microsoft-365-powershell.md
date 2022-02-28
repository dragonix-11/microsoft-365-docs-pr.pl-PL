---
title: Blokowanie Microsoft 365 użytkowników za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Jak za pomocą programu PowerShell blokować i odblokowywać dostęp do Microsoft 365 konta.
ms.openlocfilehash: 0ecfdfb8f99175ce5312769593c7637a7d1ae25b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985090"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>Blokowanie Microsoft 365 użytkowników za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Zablokowanie dostępu do konta Microsoft 365 uniemożliwia innym osobom logowanie się i uzyskiwanie dostępu do usług i danych w Microsoft 365 organizacji. Za pomocą programu PowerShell możesz zablokować dostęp do pojedynczych lub wielu kont użytkowników.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="block-access-to-individual-user-accounts"></a>Blokowanie dostępu do kont poszczególnych użytkowników

Aby zablokować konto indywidualnego użytkownika, użyj następującej składni:

```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Parametr *-ObjectID* w poleceniach cmdlet **Set-AzureAD** przyjmuje nazwę logowania konta,znaną także jako główna nazwa użytkownika lub identyfikator obiektu konta.

W tym przykładzie dostęp do konta użytkownika jest *fabricec@litwareinc.com*.

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

Aby sprawdzić stan zablokowanego konta użytkownika, użyj następującego polecenia:

```powershell
Get-AzureADUser  -ObjectID <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-multiple-user-accounts"></a>Blokowanie wielu kont użytkowników

Aby zablokować dostęp do wielu kont użytkowników, utwórz plik tekstowy zawierający jedną nazwę logowania konta w każdym wierszu w ten sposób:

  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

W przykładowym pliku tekstowym w następujących poleceniach *jest C:\Moje Documents\Accounts.txt*. Zastąp tę nazwę pliku ścieżką i nazwą pliku tekstowego.

Aby zablokować dostęp do kont wymienionych w pliku tekstowym, uruchom następujące polecenie:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $false}
```

Aby odblokować konta wymienione w pliku tekstowym, uruchom następujące polecenie:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $true}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="block-individual-user-accounts"></a>Blokowanie kont poszczególnych użytkowników

Aby zablokować dostęp do konta pojedynczego użytkownika, użyj następującej składni:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet, których *nazwa zawiera Msol*. Musisz uruchomić te polecenia cmdlet z Windows PowerShell.

Ten przykład blokuje dostęp do konta *użytkownika fabricec\@ litwareinc.com*.

```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Aby odblokować konto użytkownika, uruchom następujące polecenie:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

Aby sprawdzić stan zablokowanego konta użytkownika, uruchom następujące polecenie:

```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-for-multiple-user-accounts"></a>Blokowanie dostępu dla wielu kont użytkowników

Najpierw utwórz plik tekstowy, który zawiera jedno konto w każdym wierszu w ten sposób:

```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

W przykładowym pliku tekstowym w następujących poleceniach *jest C:\Moje Documents\Accounts.txt*. Zastąp tę nazwę pliku ścieżką i nazwą pliku tekstowego.

Aby zablokować dostęp do kont wymienionych w pliku tekstowym, uruchom następujące polecenie:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Aby odblokować konta wymienione w pliku tekstowym, uruchom następujące polecenie:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)
