---
title: Wyświetlanie błędów synchronizacji katalogów w Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak wyświetlać błędy synchronizacji katalogów i możliwe poprawki w Centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: 1aa6a9208c9ae3091c2490a003eaabb841b78dc5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096507"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Wyświetlanie błędów synchronizacji katalogów w Microsoft 365

W Centrum administracyjne platformy Microsoft 365 można wyświetlić błędy synchronizacji <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">katalogów</a>. Wyświetlane są tylko błędy obiektu Użytkownika. Aby wyświetlić błędy w programie PowerShell, zobacz [Identyfikowanie obiektów za pomocą narzędzia DirSyncProvisioningErrors](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Wyświetl błędy synchronizacji katalogów w Centrum administracyjne platformy Microsoft 365

Aby wyświetlić błędy w Centrum administracyjne platformy Microsoft 365:
  
1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu konta administratora globalnego. 
    
2. Na stronie **głównej** zostanie wyświetlona karta **Zarządzanie użytkownikami** . 
    
    ![Karta Zarządzania użytkownikami w Centrum administracyjne platformy Microsoft 365.](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. Na karcie wybierz pozycję **Synchronizuj błędy** w obszarze **Połączenie usługi Azure AD**, aby wyświetlić błędy na stronie **Błędy synchronizacji katalogów**.   
    
    ![Przykład strony błędów synchronizacji katalogu.](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Wybierz dowolny z błędów, aby wyświetlić okienko szczegółów z informacjami o błędzie i wskazówkami dotyczącymi sposobu jego rozwiązania.

   ![Przykład szczegółów błędu synchronizacji katalogu.](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Po wyświetleniu zobacz [Rozwiązywanie problemów z synchronizacją katalogów dla Microsoft 365](fix-problems-with-directory-synchronization.md) w celu rozwiązania wszelkich zidentyfikowanych problemów.