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
description: Zaloguj się do konta administratora Microsoft 365, aby ustawić niektóre hasła użytkowników, które nigdy nie wygasną przy użyciu programu Azure AD programu PowerShell.
ms.openlocfilehash: a8357e3c72ea4bcd30234492b30e75eff8cb123a
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010195"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Konfigurowanie hasła konkretnego użytkownika, aby nigdy nie wygasało

W tym artykule wyjaśniono, jak ustawić hasło dla poszczególnych użytkowników, aby nie wygasał. Te kroki należy wykonać przy użyciu programu PowerShell.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ten artykuł jest przeznaczony dla osób, które konfigurują zasady wygasania haseł dla firmy, instytucji edukacyjnej lub organizacji niedochodowej. Aby wykonać te kroki, musisz zalogować się przy użyciu konta administratora Microsoft 365. Zobacz [Omówienie Centrum administracyjne platformy Microsoft 365](/microsoft-365/admin/admin-overview/admin-center-overview).

Aby wykonać te kroki, musisz być [administratorem globalnym lub administratorem haseł](about-admin-roles.md) .

Administrator globalny usługi w chmurze firmy Microsoft może użyć [Azure Active Directory programu PowerShell dla Graph](/powershell/azure/active-directory/install-adv2), aby ustawić hasła, które nie wygasają dla określonych użytkowników. Możesz również użyć poleceń cmdlet [usługi AzureAD](/powershell/module/Azuread) , aby usunąć konfigurację, która nigdy nie wygasa, lub zobaczyć, które hasła użytkowników mają nigdy nie wygasać.

Ten przewodnik dotyczy innych dostawców, takich jak Intune i Microsoft 365, którzy również korzystają z Azure AD dla usług tożsamości i katalogów. Wygaśnięcie hasła to jedyna część zasad, którą można zmienić.

## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Jak sprawdzić zasady wygasania pod kątem hasła

Aby uzyskać więcej informacji na temat polecenia Get-AzureADUser w module AzureAD, zobacz artykuł referencyjny [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser).

Uruchom jedno z następujących poleceń:

- Aby sprawdzić, czy hasło pojedynczego użytkownika nigdy nie wygasa, uruchom następujące polecenie cmdlet przy użyciu nazwy UPN (na przykład *user@contoso.onmicrosoft.com*) lub identyfikatora użytkownika, który chcesz sprawdzić:

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

- Aby uzyskać raport wszystkich użytkowników z passwordNeverExpires w języku Html na pulpicie bieżącego użytkownika o nazwie  **ReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- Aby uzyskać raport wszystkich użytkowników z passwordNeverExpires w csv na pulpicie bieżącego użytkownika o nazwie **ReportPasswordNeverExpires.csv**

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

- Aby ustawić hasła wszystkich użytkowników w organizacji, aby nigdy nie wygasały, uruchom następujące polecenie cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Konta użytkowników skonfigurowane przy użyciu parametru `-PasswordPolicies DisablePasswordExpiration` nadal starzeją się na podstawie atrybutu `pwdLastSet` . Na podstawie atrybutu `pwdLastSet` , jeśli zmienisz wygaśnięcie na `-PasswordPolicies None`, wszystkie hasła, które mają pwdLastSet starsze niż 90 dni, wymagają od użytkownika zmiany ich przy następnym zalogowaniu. Ta zmiana może mieć wpływ na dużą liczbę użytkowników.

### <a name="set-a-password-to-expire"></a>Ustawianie wygaśnięcia hasła

Uruchom jedno z następujących poleceń:

- Aby ustawić hasło jednego użytkownika w celu wygaśnięcia hasła, uruchom następujące polecenie cmdlet przy użyciu nazwy UPN lub identyfikatora użytkownika użytkownika:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Aby ustawić hasła wszystkich użytkowników w organizacji tak, aby wygasały, użyj następującego polecenia cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>Zawartość pokrewna

[Zezwalaj użytkownikom na resetowanie własnych haseł](../add-users/let-users-reset-passwords.md) (artykuł)\
[Resetowanie haseł](../add-users/reset-passwords.md) (artykuł)\
[Ustawianie zasad wygasania haseł dla organizacji](../manage/set-password-expiration-policy.md) (artykuł)
