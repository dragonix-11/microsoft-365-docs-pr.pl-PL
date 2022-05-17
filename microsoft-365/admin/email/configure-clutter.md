---
title: Konfigurowanie zaśmiecania dla organizacji
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
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 832276bd-d024-47b6-a80a-a6b884907a5b
description: 'Dowiedz się, jak włączyć lub wyłączyć funkcję Bałagan dla wszystkich lub określonych użytkowników w organizacji przy użyciu programu Exchange programu PowerShell. '
ms.openlocfilehash: 64c11b2a8bbce3747727c458a4427f5c0e1b135b
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437200"
---
# <a name="configure-microsoft-365-clutter-for-your-organization"></a>Konfigurowanie Microsoft 365 Clutter dla organizacji

> [!TIP]
> [Skoncentrowana skrzynka odbiorcza](../setup/configure-focused-inbox.md) zastąpi element Clutter. Dowiedz się więcej: [Aktualizacja ukierunkowanej skrzynki odbiorczej i nasze plany dotyczące zaśmiecania](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
Jako administrator może być konieczne zarządzanie funkcją Bałagan w Microsoft 365. Aby włączyć/wyłączyć funkcję Bałagan dla użytkowników w organizacji, należy użyć Exchange programu PowerShell. (Użytkownicy mogą go włączyć/wyłączyć, korzystając z następujących instrukcji: [Wyłącz/włącz bałagan w Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
Zapoznaj się [z tematem Używanie programu PowerShell z Exchange Online](/powershell/exchange/exchange-online-powershell) i [Połączenie do Exchange Online programu PowerShell, aby](/powershell/exchange/connect-to-exchange-online-powershell) uzyskać szczegółowe informacje na temat korzystania z programu Exchange PowerShell. Musisz mieć konto, które ma co najmniej rolę administratora usługi Exchange i możliwość nawiązywania połączenia z Exchange Online za pomocą programu PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Włączanie funkcji Bałagan przy użyciu programu Exchange PowerShell

Możesz włączyć funkcję Bałagan ręcznie dla skrzynki pocztowej, uruchamiając polecenie cmdlet [Set-Clutter](/powershell/module/exchange/set-clutter) . Możesz również wyświetlić ustawienia bałaganu dla skrzynek pocztowych w organizacji, uruchamiając polecenie cmdlet [Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Włącz usługę Clutter dla jednego użytkownika o nazwie Allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Wyłączanie zaśmiecania przy użyciu programu Exchange PowerShell

Dla skrzynki pocztowej można ręcznie wyłączyć funkcję Bałagan, uruchamiając polecenie cmdlet [Set-Clutter](/powershell/module/exchange/set-clutter) . Możesz również wyświetlić ustawienia **bałaganu** dla skrzynek pocztowych w organizacji, uruchamiając polecenie cmdlet [Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Wyłącz element Clutter dla jednego użytkownika o nazwie Allie Bellew:
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Jeśli używasz programu PowerShell do zbiorczego tworzenia użytkowników, musisz uruchomić polecenie [Set-Clutter](/powershell/module/exchange/set-clutter) w skrzynce pocztowej każdego użytkownika, aby zarządzać elementem Clutter. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Kiedy przełącznik włączania/wyłączania bałaganu jest wyświetlany użytkownikom w Outlook w sieci Web?
<a name="bkmk_onoff"> </a>

Jako administrator możesz ponownie włączyć funkcję Clutter przy użyciu Exchange programu PowerShell. Gdy to zrobisz, skoncentrowana skrzynka odbiorcza zostanie wyłączona, a element Clutter będzie ponownie aktywny. 
  
 **Jeśli używasz Outlook w sieci Web z subskrypcją Microsoft 365 Business Premium:**
  
- Jeśli użytkownik ma obecnie włączoną funkcję Bałagan: 
    
  - Zostaną wyświetlone ustawienia bałaganu
    
- Jeśli użytkownik ma obecnie włączoną ukierunkowaną skrzynkę odbiorczą: 
    
  - Ustawienia zaśmiecania nie będą wyświetlane
    
- Jeśli nie włączono żadnej zaśmieconej lub skoncentrowanej skrzynki odbiorczej: 
    
  - W Ustawienia Poczty użytkownika są wyświetlane zarówno elementy Clutter, jak i Focused Inbox
    
 **Jeśli używasz witryny Outlook.com:**
  
- Jeśli użytkownik ma obecnie włączoną funkcję Bałagan: 
    
  - Zostaną wyświetlone ustawienia bałaganu
    
- Jeśli użytkownik ma obecnie włączoną ukierunkowaną skrzynkę odbiorczą: 
    
  - Ustawienia zaśmiecania nie będą wyświetlane
    
- Jeśli nie włączono żadnej zaśmieconej lub skoncentrowanej skrzynki odbiorczej: 
    
  - W Ustawienia Poczty użytkownika są wyświetlane zarówno elementy Clutter, jak i Focused Inbox
    
- Jeśli w pewnym momencie w przeszłości włączono dla użytkownika usługę Focused Inbox:
    
  - Ustawienia bałaganu nigdy nie będą wyświetlane
    
    Inaczej 
    
  - Zostaną wyświetlone ustawienia bałaganu
    
## <a name="related-content"></a>Zawartość pokrewna

[Sortowanie komunikatów o niskim priorytecie w Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (artykuł)\
[Sortowanie komunikatów o niskim priorytecie w usłudze OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (artykuł)\
[Wyłączanie funkcji Bałagan w Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (artykuł)
