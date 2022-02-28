---
title: Wyłączanie synchronizacji katalogów dla Microsoft 365
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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: W tym artykule znajdziesz informacje dotyczące używania programu PowerShell do wyłączenia synchronizacji katalogów dla Microsoft 365.
ms.openlocfilehash: 83a3d66493994800a71a1910332a5eb2cdb003cd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988397"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Wyłączanie synchronizacji katalogów dla Microsoft 365
Za pomocą programu PowerShell można wyłączyć synchronizację katalogów i przekonwertować synchronizowanych użytkowników na użytkowników korzystających tylko z chmury. Nie zaleca się jednak wyłączenia synchronizacji katalogów jako kroku rozwiązywania problemów. Jeśli potrzebujesz pomocy dotyczącej rozwiązywania problemów z synchronizacją katalogów, [zobacz artykuł Rozwiązywanie](fix-problems-with-directory-synchronization.md) problemów z synchronizacją Microsoft 365 katalogów. 
  
[W razie potrzeby skontaktuj](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) się z pomocą techniczną dla produktów biznesowych.
  
## <a name="turn-off-directory-synchronization"></a>Wyłączanie synchronizacji katalogów  
Aby wyłączyć synchronizację katalogów:
  
1. Najpierw zainstaluj wymagane oprogramowanie i połącz się ze swoją Microsoft 365 subskrypcją. Aby uzyskać instrukcje, [Połączenie się z modułem Microsoft Azure Active Directory dla Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Użyj [set-MsolDirSyncEnabled,](/previous-versions/azure/dn194097(v=azure.100)) aby wyłączyć synchronizację katalogów: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>W przypadku użycia tego polecenia musisz odczekać 72 godziny, zanim będzie można ponownie włączyć synchronizację katalogów.
>
