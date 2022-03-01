---
title: Wyłączanie wymagań dotyczących silnych haseł dla użytkowników
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
search.appverid:
- BCS160
- MET150
- MOE150
description: Dowiedz się, jak ustawić dla użytkowników silne wymagania dotyczące haseł, używając funkcji Windows PowerShell.
ms.openlocfilehash: 5932f01c2f17a72f4f6a20a6457d263bed7dd85e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017864"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>Wyłączanie wymagań dotyczących silnych haseł dla użytkowników

W tym artykule wyjaśniono, jak wyłączyć użytkownikom silne wymagania dotyczące haseł. Wymagania dotyczące silnych haseł są domyślnie włączone w Twojej organizacji usługi Microsoft 365 firm. Twoja organizacja może mieć wymagania dotyczące wyłączania silnych haseł. Wykonaj poniższe czynności, aby wyłączyć wymagania dotyczące silnych haseł. Musisz wykonać te czynności przy użyciu programu PowerShell.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ten artykuł jest dla osób, które zarządzają zasadami haseł dla firmy, szkoły lub organizacji niedochodowej. Aby wykonać te czynności, musisz zalogować się przy użyciu Microsoft 365 administratora. [Co to jest konto administratora?] (Omówienie centrum administracyjne platformy Microsoft 365](.. /admin-overview/admin-center-overview.md) Aby wykonać te czynności, musisz być [administratorem globalnym lub administratorem](about-admin-roles.md) haseł.

Musisz także nawiązać połączenie z programem Microsoft 365 Za pomocą programu PowerShell.

## <a name="set-strong-passwords"></a>Ustawianie silnych haseł

1. [Połączenie do Microsoft 365 za pomocą programu PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. Za pomocą programu PowerShell można wyłączyć wymagania dotyczące silnych haseł dla wszystkich użytkowników za pomocą następującego polecenia:

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> Nazwa użytkownikaPrincipalName musi mieć format logowania typu internetowego, w którym po nazwie użytkownika musi znajdować się znak "@" i nazwa domeny. Na przykład: user@contoso.com.

## <a name="related-content"></a>Zawartość pokrewna

[Jak nawiązać połączenie z siecią Microsoft 365 programie PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[Więcej informacji na temat poleceń MsolUser programu PowerShell](/powershell/azure/active-directory/install-adv2)

[Więcej informacji na temat zasad dotyczących haseł](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
