---
title: Zarządzanie Skype dla firm Online przy użyciu programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Użyj programu PowerShell dla Microsoft 365, aby zarządzać zasadami usługi Skype dla firm Online, zasadami poszczególnych użytkowników i ustawieniami spotkania.
ms.openlocfilehash: 1c3a3e06d3fa607765382176a8c291fab2c69636
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097673"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Zarządzanie Skype dla firm Online przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Skype dla firm Administratorzy usługi Online są odpowiedzialni za zarządzanie zasadami. Chociaż niektóre z tych zadań można wykonać w Centrum administracyjne platformy Microsoft 365, inne są łatwiejsze do wykonania w programie PowerShell.

## <a name="before-you-start"></a>Przed rozpoczęciem

> [!NOTE]
> Skype dla firm Online Connector jest obecnie częścią najnowszego modułu Teams programu PowerShell. Jeśli używasz najnowszej Teams publicznej wersji programu **PowerShell**, nie musisz instalować łącznika usługi Skype dla firm Online.

> [!NOTE]
> Skype dla firm Administratorzy online mogą zarządzać zasadami aplikacji **Teams** i **Skype dla firm Online** za pośrednictwem programu PowerShell.

Zainstaluj [moduł Teams programu PowerShell](/microsoftteams/teams-powershell-install).

## <a name="connect-using-admin-credentials"></a>Połączenie przy użyciu poświadczeń administratora

1. Otwórz okno wiersza polecenia Windows PowerShell i uruchom następujące polecenia:

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. W oknie dialogowym **Windows PowerShell Żądanie poświadczeń** wpisz nazwę konta administratora i hasło, a następnie wybierz przycisk **OK**.

## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>Połączenie przy użyciu konta administratora z uwierzytelnianiem wieloskładnikowym

1. Otwórz okno wiersza polecenia Windows PowerShell i uruchom następujące polecenia:

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. Po wyświetleniu monitu wprowadź nazwę konta administratora usługi Skype dla firm Online.

3. W oknie dialogowym **Logowanie do konta** wpisz hasło administratora usługi Skype dla firm Online i wybierz pozycję **Zaloguj** się.

4. W oknie dialogowym **Logowanie się do konta postępuj** zgodnie z instrukcjami, aby dodać informacje uwierzytelniania, takie jak kod weryfikacyjny, a następnie wybierz pozycję **Weryfikuj**.

Więcej informacji można znaleźć w następujących artykułach:

- [Zarządzanie zasadami usługi Skype dla firm Online przy użyciu programu PowerShell](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)

- [Przypisywanie zasad Skype dla firm Online dla poszczególnych użytkowników za pomocą programu PowerShell](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)

## <a name="see-also"></a>Zobacz też

[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Wprowadzenie za pomocą programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Skype dla firm odwołania do poleceń cmdlet programu PowerShell](/powershell/module/skype/)
