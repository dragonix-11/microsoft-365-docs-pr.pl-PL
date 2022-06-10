---
title: Wyłączanie silnych wymagań dotyczących haseł dla użytkowników
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
description: Jeśli jesteś administratorem, który zarządza zasadami haseł dla firmy, szkoły lub organizacji non-profit, możesz ustawić silne wymagania dotyczące haseł przy użyciu Azure AD programu PowerShell.
ms.openlocfilehash: e98c9a3f7b31cbb53d4c853487f4908a6dec72d5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010261"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>Wyłączanie silnych wymagań dotyczących haseł dla użytkowników

W tym artykule wyjaśniono, jak wyłączyć wymagania dotyczące silnych haseł dla użytkowników. Wymagania dotyczące silnych haseł są domyślnie włączone w Microsoft 365 dla organizacji biznesowej. Organizacja może mieć wymagania dotyczące wyłączania silnych haseł. Wykonaj poniższe kroki, aby wyłączyć wymagania dotyczące silnych haseł. Te kroki należy wykonać przy użyciu programu PowerShell.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ten artykuł dotyczy osób, które zarządzają zasadami haseł dla firmy, szkoły lub organizacji non-profit. Aby wykonać te kroki, musisz zalogować się przy użyciu konta administratora Microsoft 365. [Co to jest konto administratora?] (Omówienie Centrum administracyjne platformy Microsoft 365](.. /admin-overview/admin-center-overview.md) Aby wykonać te kroki, musisz być [administratorem globalnym lub administratorem haseł](about-admin-roles.md).

Należy również nawiązać połączenie z Microsoft 365 za pomocą programu PowerShell.

## <a name="set-strong-passwords"></a>Ustawianie silnych haseł

1. [Połączenie do Microsoft 365 za pomocą programu PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. Za pomocą programu PowerShell można wyłączyć silne wymagania dotyczące haseł dla wszystkich użytkowników za pomocą następującego polecenia:

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> Nazwa userPrincipalName musi być w formacie logowania w stylu internetowym, w którym po nazwie użytkownika następuje znak at (@) i nazwa domeny. Na przykład: user@contoso.com.

## <a name="related-content"></a>Zawartość pokrewna

[Jak nawiązać połączenie z Microsoft 365 za pomocą programu PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[Więcej informacji na temat poleceń msolUser programu PowerShell](/powershell/azure/active-directory/install-adv2)

[Więcej informacji na temat zasad haseł](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
