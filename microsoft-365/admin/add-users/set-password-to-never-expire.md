---
title: Konfigurowanie hasła konkretnego użytkownika, aby nigdy nie wygasało
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: Zaloguj się do konta Microsoft 365, aby ustawić niektóre hasła użytkowników tak, aby nigdy nie wygasały przy użyciu konta Windows PowerShell.
ms.openlocfilehash: f0eff70b2b95c7e318f8a7e52777d4b684dbd8bf
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021237"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Konfigurowanie hasła konkretnego użytkownika, aby nigdy nie wygasało

W tym artykule wyjaśniono, jak ustawić hasło dla pojedynczego użytkownika, aby nie wygasło. Musisz wykonać te czynności przy użyciu programu PowerShell.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ten artykuł jest przeznaczony dla osób, które konfigurują zasady wygasania haseł dla firmy, instytucji edukacyjnej lub organizacji niedochodowej. Aby wykonać te czynności, musisz zalogować się przy użyciu Microsoft 365 administratora. Zobacz [Omówienie centrum administracyjne platformy Microsoft 365](/microsoft-365/admin/admin-overview/admin-center-overview?view=o365-worldwide).

Aby wykonać te [czynności, musisz być administratorem globalnym lub administratorem](about-admin-roles.md) hasła.

Administrator globalny usługi firmy Microsoft w chmurze może za pomocą programu [Azure Active Directory PowerShell](/powershell/azure/active-directory/install-adv2) dla systemu Graph ustawić hasła, które nie wygasają dla określonych użytkowników. Za pomocą polecenia cmdlet usługi [AzureAD](/powershell/module/Azuread) możesz również usunąć konfigurację, która nigdy nie wygasa, lub sprawdzić, które hasła użytkowników są tak ustawione, aby nigdy nie wygasały.

Ten przewodnik dotyczy innych dostawców, takich jak intune czy Microsoft 365, którzy także korzystają z usługi Azure AD w celu korzystania z usług tożsamości i katalogów. Wygaśnięcie hasła to jedyna część zasad, które można zmienić.


## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Jak sprawdzić zasady wygasania hasła

Aby uzyskać więcej informacji na Get-AzureADUser w module AzureAD, zobacz artykuł referencyjny [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser).

Uruchom jedno z następujących poleceń:

- Aby sprawdzić, czy hasło pojedynczego użytkownika nie jest tak ustawione, aby nigdy nie wygasło, uruchom następujące polecenie cmdlet, używając nazwy UPN (na przykład *user@contoso.onmicrosoft.com*) lub identyfikatora użytkownika, którego chcesz sprawdzić:

    ```powershell
    Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

    Przykład:

    ```powershell
    Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

- Aby wyświetlić ustawienie **Hasło nigdy nie wygasa** dla wszystkich użytkowników, uruchom następujące polecenie cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- Aby uzyskać raport o wszystkich użytkownikach korzystających z hasłaNeverExpires w języku Html na pulpicie bieżącego użytkownika z nazwą  **ReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- Aby uzyskać raport o wszystkich użytkownikach korzystających z hasłaNeverExpires w formacie CSV na pulpicie bieżącego użytkownika z nazwą **ReportPasswordNeverExpires.csv**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv

## Set a password to never expire

Run one of the following commands:

- To set the password of one user to never expire, run the following cmdlet by using the UPN or the user ID of the user:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration
    ```

- Aby ustawić hasła wszystkich użytkowników w organizacji tak, aby nigdy nie wygasały, uruchom następujące polecenie cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Konta użytkowników skonfigurowane z parametrem nadal `-PasswordPolicies DisablePasswordExpiration` mają wiek na podstawie tego `pwdLastSet` atrybutu. W zależności od `pwdLastSet` atrybutu po `-PasswordPolicies None`zmianie daty wygaśnięcia na , wszystkie hasła o wartości pwdLastSet starszej niż 90 dni wymagają, aby użytkownik zmienił je przy następnym logować się. Ta zmiana może mieć wpływ na dużą liczbę użytkowników.

### <a name="set-a-password-to-expire"></a>Ustawianie hasła do wygaśnięcia

Uruchom jedno z następujących poleceń:

- Aby ustawić hasło jednego użytkownika tak, aby hasło wygasło, uruchom następujące polecenie cmdlet przy użyciu nazwy UPN lub identyfikatora użytkownika:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Aby ustawić hasła wszystkich użytkowników w organizacji tak, aby wygasały, użyj następującego polecenia cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>Zawartość pokrewna

[Umożliwianie użytkownikom resetowania swoich haseł](../add-users/let-users-reset-passwords.md) (artykuł)\
[Resetowanie haseł](../add-users/reset-passwords.md) (artykuł)\
[Ustawianie zasad wygasania haseł dla organizacji](../manage/set-password-expiration-policy.md) (artykuł)
