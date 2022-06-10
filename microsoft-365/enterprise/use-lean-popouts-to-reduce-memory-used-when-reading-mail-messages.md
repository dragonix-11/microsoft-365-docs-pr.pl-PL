---
title: Używanie wyskakujące okienka lean w celu zmniejszenia ilości pamięci używanej podczas odczytywania wiadomości e-mail
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Ten artykuł zawiera informacje dotyczące używania wyskakujące okienka lean w celu zwiększenia wydajności pobierania komunikatów w Outlook w sieci Web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9636fd3beafd169358c4b50cafdc4ac0f9494994
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012687"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Używanie wyskakujące okienka lean w celu zmniejszenia ilości pamięci używanej podczas odczytywania wiadomości e-mail

Ten artykuł zawiera informacje dotyczące poprawy wydajności pobierania komunikatów w Outlook w sieci Web. Ten artykuł jest częścią [planowania sieci i dostrajania wydajności dla projektu Office 365](./network-planning-and-performance.md).
  
Jako **administrator aplikacji** Office 365, **administrator globalny** lub **administrator użytkowników** można skonfigurować Outlook w sieci Web do dostarczania _wyskakujące chude wyskakujące_, mniejsze, mniej pamięci wersji niektórych wiadomości e-mail w Microsoft Edge lub Internet Explorer. Gdy wyskakujące okienka pochylenia są skonfigurowane dla Outlook w sieci Web, ładowane są renderowane składniki po stronie serwera, które optymalizujące wydajność.
  
> [!NOTE]
> Od marca 2018 r. wyskakujące okienka lean nie są dostępne dla komunikatów określających ograniczenia praw użytkowania, takie jak Rights Management informacji (IRM).
  
Te funkcje będą nadal działać w oknie głównym, ale nie są dostępne w wyskakującym okienku lean:
  
- dodatki Outlook
  
- obecność Skype dla firm
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Aby skonfigurować wyskakujące okienka lean dla wszystkich użytkowników w organizacji Office 365
  
1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Uruchom polecenie cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) z parametrem LeanPopoutEnabled w następujący sposób:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Aby na przykład włączyć wyskakujące okienka lean dla wszystkich użytkowników w organizacji:
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Aby wyłączyć wyskakujące okienka lean dla wszystkich użytkowników w organizacji:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
