---
title: Używaj wysuwu wysuwu, aby zmniejszyć zużycie pamięci podczas czytania wiadomości e-mail
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: Ten artykuł zawiera informacje dotyczące korzystania z wysuwu materiałów informacyjnych w celu zwiększenia wydajności pobierania wiadomości w Outlook w sieci Web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aaacacc0c1db418181690a5a4691bd251180d97c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985082"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Używaj wysuwu wysuwu, aby zmniejszyć zużycie pamięci podczas czytania wiadomości e-mail

Ten artykuł zawiera informacje dotyczące poprawy wydajności pobierania wiadomości w programie Outlook w sieci Web. Ten artykuł jest częścią planowania [sieci i dostosowywania wydajności dla Office 365](./network-planning-and-performance.md) projektu.
  
Jako administrator aplikacji pakietu **Office 365, administrator** globalny lub administrator użytkownika możesz skonfigurować usługę Outlook w sieci Web **tak, aby** dostarczała nieuchowe wyskakujące okienka _, mniejsza_ i wymagała mniej pamięci wersję niektórych wiadomości e-mail w programie Microsoft Edge lub Internet Explorer. Gdy dla wysuwu są skonfigurowane wysuwu Outlook w sieci Web, renderowane składniki po stronie serwera są ładowane, aby zoptymalizować wydajność.
  
> [!NOTE]
> Od marca 2018 r. nie są dostępne podręczne podręczne informacje dla wiadomości określających ograniczenia praw użytkowania, takie jak zarządzanie prawami do informacji (IRM).
  
Te funkcje będą nadal działać w oknie głównym, ale nie są dostępne w niechcnych okienkach:
  
- Outlook dodatki
  
- Skype dla firm obecności
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Aby skonfigurować podręczne okienka dla wszystkich użytkowników w Office 365 organizacji
  
1. [Połączenie do Exchange Online przy użyciu zdalnej pracy z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Uruchom polecenie [cmdlet Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) z parametrem LeanPopoutEnabled w następujący sposób:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Aby na przykład włączyć funkcję wysuwu danych dla wszystkich użytkowników w organizacji:
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Aby wyłączyć funkcję wysuwu wysuwu danych dla wszystkich użytkowników w organizacji:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
