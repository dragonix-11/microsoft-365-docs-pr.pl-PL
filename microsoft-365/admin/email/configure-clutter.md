---
title: Konfigurowanie usługi mało istotne w organizacji
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
description: 'Dowiedz się, jak włączyć lub wyłączyć funkcję mało istotne dla wszystkich lub określonych użytkowników w organizacji przy użyciu programu Exchange PowerShell. '
ms.openlocfilehash: 5037e7cb6518ca90f3d12c183fcff3c838c29907
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973558"
---
# <a name="configure-clutter-for-your-organization"></a>Konfigurowanie usługi mało istotne w organizacji

> [!TIP]
> [Skoncentrowana skrzynka odbiorcza](../setup/configure-focused-inbox.md) zastąpi mało istotne. Dowiedz się więcej: [Aktualizacja focused skrzynki odbiorczej i nasze plany dotyczące mało istotne](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
Jako administrator może być musisz zarządzać funkcją mało istotne w programie Microsoft 365. Aby włączyć/wyłączyć funkcję mało istotne dla użytkowników w organizacji, musisz użyć programu Exchange PowerShell. (Osoby mogą je włączać i wyłączać, korzystając z poniższych instrukcji: Włączanie/wyłączanie funkcji usuwania jako mało istotne w [programie Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
Aby uzyskać [szczegółowe informacje na](/powershell/exchange/exchange-online-powershell) temat korzystania Exchange PowerShell, zobacz Exchange Online [PowerShell i Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Musisz mieć konto, które ma co najmniej Exchange administratora usługi oraz możliwość łączenia się z usługą Exchange Online programem PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Włączanie funkcji mało istotne przy użyciu programu Exchange PowerShell

Możesz włączyć funkcję mało istotne ręcznie dla skrzynki pocztowej, uruchamiając polecenie cmdlet [Set-Clutter](/powershell/module/exchange/set-clutter) . Możesz również wyświetlić ustawienia usługi Mało istotne dla skrzynek pocztowych w Twojej organizacji, uruchamiając polecenie cmdlet [Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Włączanie mało istotne dla jednego użytkownika o nazwie Allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Wyłączanie funkcji mało istotne przy użyciu programu Exchange PowerShell

Możesz wyłączyć funkcję mało istotne ręcznie dla skrzynki pocztowej, uruchamiając polecenie cmdlet [Set-Clutter](/powershell/module/exchange/set-clutter) . Możesz również wyświetlić ustawienia **usługi Mało istotne** dla skrzynek pocztowych w Twojej organizacji, uruchamiając polecenie cmdlet [Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Wyłącz tryb mało istotne dla jednego użytkownika o nazwie Allie Bellew:
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Jeśli zbiorczo tworzysz użytkowników za pomocą programu PowerShell, musisz uruchomić ustawienie Ustaw mało istotne [](/powershell/module/exchange/set-clutter) dla skrzynek pocztowych poszczególnych użytkowników, aby zarządzać mało istotne. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Kiedy przełącznik Oznaczanie jako mało istotne jest wyświetlany użytkownikom w aplikacji Outlook w sieci Web?
<a name="bkmk_onoff"> </a>

Jako administrator możesz ponownie włączyć funkcję mało istotne przy użyciu programu Exchange PowerShell. Gdy to zrobisz, focused skrzynka odbiorcza zostanie wyłączona i znowu będzie aktywny tryb oznaczania jako mało istotne. 
  
 **Jeśli korzystasz z usługi Outlook w sieci Web subskrypcji usługi Microsoft 365 Business Premium usługi:**
  
- Jeśli funkcja mało istotne jest obecnie włączona dla użytkownika: 
    
  - Zostaną wyświetlone ustawienia mało istotne
    
- Jeśli użytkownik ma obecnie włączoną skrzynkę odbiorczą: 
    
  - Ustawienia mało istotne nie będą wyświetlane
    
- Jeśli nie jest włączona funkcja mało istotne ani focused skrzynka odbiorcza: 
    
  - Zarówno mało istotne, jak i Focused Skrzynka odbiorcza są wyświetlane jako opcje w  polach poczty Ustawienia
    
 **Jeśli korzystasz z usługi Outlook.com:**
  
- Jeśli funkcja mało istotne jest obecnie włączona dla użytkownika: 
    
  - Zostaną wyświetlone ustawienia mało istotne
    
- Jeśli użytkownik ma obecnie włączoną skrzynkę odbiorczą: 
    
  - Ustawienia mało istotne nie będą wyświetlane
    
- Jeśli nie jest włączona funkcja mało istotne ani focused skrzynka odbiorcza: 
    
  - Zarówno mało istotne, jak i Focused Skrzynka odbiorcza są wyświetlane jako opcje w  polach poczty Ustawienia
    
- Jeśli w przeszłości włączono dla użytkownika focused skrzynkę odbiorczą:
    
  - Ustawienia mało istotne nigdy nie będą wyświetlane
    
    W przeciwnym razie, 
    
  - Zostaną wyświetlone ustawienia mało istotne
    
## <a name="related-content"></a>Zawartość pokrewna

[Używanie funkcji sortowania jako mało istotne do sortowania wiadomości o niskim priorytecie Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (artykuł)\
[Używanie funkcji mało istotne do sortowania wiadomości o niskim priorytecie w aplikacji OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (artykuł)\
[Wyłączanie opcji mało istotne w programie Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (artykuł)
