---
title: Zarządzanie usługą Skype dla firm Online za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: Użyj programu PowerShell dla Microsoft 365 do zarządzania Skype dla firm online, zasadami dla  użytkownika i ustawieniami spotkania.
ms.openlocfilehash: 40fc030c957fee2d31c18ea95f1939e3d9f0937b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987802"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Zarządzanie usługą Skype dla firm Online za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Skype dla firm administratorzy usługi Online są odpowiedzialni za zarządzanie zasadami. Niektóre z tych zadań można wykonywać w programie centrum administracyjne platformy Microsoft 365, ale inne można łatwiej wykonywać w programie PowerShell.

## <a name="before-you-start"></a>Przed rozpoczęciem

> [!NOTE]
> Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams PowerShell. Jeśli używasz najnowszej wersji programu Teams PowerShell, nie musisz instalować do łącznika usługi Skype dla firm Online.

Zainstaluj moduł [Teams PowerShell](/microsoftteams/teams-powershell-install).

## <a name="connect-using-admin-credentials"></a>Połączenie przy użyciu poświadczeń administratora

1. Otwórz okno Windows PowerShell wiersza polecenia i uruchom następujące polecenia:

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. W **oknie Windows PowerShell Żądanie** poświadczeń wpisz nazwę konta administratora i hasło, a następnie wybierz przycisk **OK**.

## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>Połączenie z kontem administratora z uwierzytelnianiem wieloskładnikowym

1. Otwórz okno Windows PowerShell wiersza polecenia i uruchom następujące polecenia:

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. Po wyświetleniu monitu wprowadź Skype dla firm administratora usługi Online.

3. W **oknie dialogowym Logowanie do konta** wpisz hasło administratora usługi Skype dla firm online i wybierz **pozycję Zaloguj.**

4. W **oknie dialogowym** Logowanie do konta postępuj zgodnie z instrukcjami, aby dodać informacje uwierzytelnienia, takie jak kod weryfikacyjny, a następnie wybierz pozycję **Weryfikuj**.

Więcej informacji można znaleźć w następujących artykułach:

- [Zarządzanie Skype dla firm online za pomocą programu PowerShell](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)

- [Przypisywanie zasad usługi Skype dla firm online za pomocą programu PowerShell](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Skype dla firm poleceń cmdlet programu PowerShell](/powershell/module/skype/)
