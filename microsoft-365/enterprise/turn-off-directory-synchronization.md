---
title: Wyłącz synchronizację katalogów dla Microsoft 365
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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: W tym artykule znajdziesz informacje dotyczące używania programu PowerShell do wyłączania synchronizacji katalogów dla Microsoft 365.
ms.openlocfilehash: 5082f89032c17e549f11f8397126f6d059937c48
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077348"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Wyłącz synchronizację katalogów dla Microsoft 365
Za pomocą programu PowerShell można wyłączyć synchronizację katalogów i przekonwertować synchronizowanych użytkowników na tylko w chmurze. Nie zaleca się jednak wyłączania synchronizacji katalogów w ramach kroku rozwiązywania problemów. Jeśli potrzebujesz pomocy w rozwiązywaniu problemów z synchronizacją katalogów, zobacz artykuł [Rozwiązywanie problemów z synchronizacją katalogów dla Microsoft 365](fix-problems-with-directory-synchronization.md). 
  
W razie potrzeby [skontaktuj się z pomocą techniczną](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) dotyczącą produktów biznesowych.
  
## <a name="turn-off-directory-synchronization"></a>Wyłączanie synchronizacji katalogów  
Aby wyłączyć synchronizację katalogów:
  
1. Najpierw zainstaluj wymagane oprogramowanie i połącz się z subskrypcją Microsoft 365. Aby uzyskać instrukcje, zobacz [Połączenie z modułem Microsoft Azure Active Directory dla Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Użyj [polecenia Set-MsolDirSyncEnabled](/previous-versions/azure/dn194097(v=azure.100)) , aby wyłączyć synchronizację katalogów: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Jeśli używasz tego polecenia, musisz poczekać 72 godziny, zanim będzie można ponownie włączyć synchronizację katalogów.
>
