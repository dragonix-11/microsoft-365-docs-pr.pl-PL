---
title: Stany urządzeń
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: c3ac23c5-d4b4-4b1b-b7ce-ea759521bf8c
description: Poznaj różne stany urządzeń na liście Akcje urządzenia w administracyjnym stronie głównej usługi Microsoft 365 dla firm.
ms.openlocfilehash: 798a753f6d523a3f586ac32698cda80a127c44b5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313821"
---
# <a name="device-states"></a>Stany urządzeń

Ten artykuł dotyczy wszystkich Microsoft 365 Business Premium.

> [!NOTE]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Ta oferta oferuje dodatkowe funkcje zabezpieczeń dla urządzeń. [Dowiedz się więcej o uchcie programu Defender dla firm](../../security/defender-business/mdb-overview.md).

Urządzenia znajdujące się na liście **Akcje urządzenia** (Administrator  strona główna \> **Akcje urządzenia**) mogą mieć następujące stany.
  
![In the Device actions list, you can see the Devices states.](../../media/a621c47e-45d9-4e1a-beb9-c03254d40c1d.png)
  
|**Stan**|**Opis**|
|:-----|:-----|
|Zarządzane przez usługę Intune  <br/> |Zarządzane przez Microsoft 365 Business Premium.  <br/> |
|Oczekiwanie na wycofanie  <br/> |Microsoft 365 Business Premium przygotowuje się do usunięcia danych firmowych z urządzenia.  <br/> |
|Wycofywanie w toku  <br/> |Microsoft 365 Business Premium obecnie usuwa dane firmy z urządzenia.  <br/> |
|Wycofywanie nie powiodło się  <br/> | Akcja usuwania danych firmy nie powiodła się.  <br/> |
|Anulowano wycofywanie  <br/> |Akcja wycofywania została anulowana.  <br/> |
|Oczekiwanie na wyczyszczenie  <br/> |Trwa oczekiwanie na rozpoczęcie przywracania ustawień fabrycznych.  <br/> |
|Czyszczenie w toku  <br/> |Wywołano polecenie przywracania ustawień fabrycznych.  <br/> |
|Czyszczenie nie powiodło się  <br/> |Nie można przywrócić ustawień fabrycznych.  <br/> |
|Czyszczenie anulowane  <br/> |Czyszczenie fabryczne zostało anulowane.  <br/> |
|Zła kondycja  <br/> |Akcja jest oczekująca (lub jest w toku), ale urządzenie nie zostało zaewidencjonowane przez ponad 30 dni.  <br/> |
|Oczekiwanie na usunięcie  <br/> |Trwa oczekiwanie na akcję usuwania.  <br/> |
|Odnaleziono  <br/> |Microsoft 365 Business Premium wykrył urządzenie.  <br/> |
   

## <a name="see-also"></a>Zobacz też

[10 najlepszych sposobów zabezpieczania planów Microsoft 365 dla firm](../security-and-compliance/secure-your-business-data.md)