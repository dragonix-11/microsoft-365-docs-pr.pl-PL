---
title: Wyświetlanie błędów synchronizacji katalogów w programie Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Dowiedz się, jak wyświetlić błędy synchronizacji katalogów i możliwe poprawki w centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: 2b832cff65aad0ae7327f440a565e12c7cba66f4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986642"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Wyświetlanie błędów synchronizacji katalogów w programie Microsoft 365

Błędy synchronizacji katalogów można <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">wyświetlić w centrum administracyjne platformy Microsoft 365</a>. Wyświetlane są tylko błędy obiektów użytkownika. Aby wyświetlić błędy w programie PowerShell, zobacz [Identyfikowanie obiektów za pomocą usługi DirSyncProvisioningErrors](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Wyświetlanie błędów synchronizacji katalogów w centrum administracyjne platformy Microsoft 365

Aby wyświetlić błędy w centrum administracyjne platformy Microsoft 365:
  
1. Zaloguj się [do centrum administracyjne platformy Microsoft 365 przy](https://admin.microsoft.com) użyciu konta administratora globalnego. 
    
2. Na stronie **głównej** zobaczysz kartę **Zarządzanie użytkownikami** . 
    
    ![Karta Zarządzanie użytkownikami w centrum administracyjne platformy Microsoft 365.](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. Na karcie wybierz pozycję **Błędy** synchronizacji w obszarze usługi **Azure AD Połączenie**, aby wyświetlić błędy na **stronie Błędy synchronizacji** katalogów.   
    
    ![Przykład strony Błędy synchronizacji katalogów.](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Wybierz dowolny z błędów, aby wyświetlić okienko szczegółów z informacjami o błędzie i poradami dotyczącymi sposobu jego rozwiązania.

   ![Przykładowe szczegóły błędu synchronizacji katalogów.](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Aby rozwiązać wszystkie zidentyfikowane problemy, zobacz rozwiązywanie problemów z [synchronizacją Microsoft 365](fix-problems-with-directory-synchronization.md) katalogów.