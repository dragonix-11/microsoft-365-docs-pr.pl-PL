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
ms.openlocfilehash: cb546a7e4130509d7acd0021b3cb78df23c1819f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474477"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Zarządzanie usługą Skype dla firm Online za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Skype dla firm administratorzy usługi Online są odpowiedzialni za zarządzanie zasadami. Niektóre z tych zadań można wykonywać w programie Centrum administracyjne platformy Microsoft 365, ale inne można łatwiej wykonywać w programie PowerShell.

## <a name="before-you-start"></a>Przed rozpoczęciem

> [!NOTE]
> Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams PowerShell. Jeśli korzystasz z najnowszej wersji programu **Teams PowerShell**, nie musisz instalować do łącznika usługi Skype dla firm Online.

> [!NOTE]
> Skype dla firm administratorzy online mogą zarządzać zarówno zasadami aplikacji usługi **Teams**, **jak i Skype dla firm online** za pomocą programu PowerShell.

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

[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie z programem PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Skype dla firm poleceń cmdlet programu PowerShell](/powershell/module/skype/)
