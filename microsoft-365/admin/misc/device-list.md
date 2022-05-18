---
title: Plik CSV listy urządzeń
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- MSB365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 932e3676-2491-49f0-9177-d893d2f5276e
ROBOTS: NOINDEX
description: Dowiedz się, jak utworzyć plik CSV dla rozwiązania AutoPilot w Microsoft 365 dla firm.
ms.openlocfilehash: af695448e31ea93d36b36a8831702acb84a92410
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469563"
---
# <a name="windows-autopilot-device-list-csv-file"></a>plik CSV listy urządzeń rozwiązania Windows Autopilot

## <a name="device-list-csv-file-format"></a>Format pliku .csv listy urządzeń

Aby zarządzać urządzeniami i wdrażać je za pośrednictwem rozwiązania Windows Autopilot, potrzebny jest plik .csv zawierający konkretne informacje o urządzeniach.
  
Kolumny w pliku listy urządzeń muszą mieć następujące nagłówki w określonej kolejności:
  
- Kolumna A: Numer seryjny urządzenia

- Kolumna B: pozostaw puste

- Kolumna C: Skrót sprzętowy

Możesz uzyskać te informacje od producenta komputera lub użyć [skryptu programu PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo), który wygeneruje plik CSV. 

Podczas dodawania urządzeń należy również dodać je do profilu. Profil służy do stosowania profilów wdrażania rozwiązania AutoPilot do urządzenia lub grupy urządzeń.
  
## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 dokumentacji i zasobów biznesowych](../../index.yml)
  
[Wprowadzenie z Microsoft 365 dla firm](../../admin/admin-overview/what-is-microsoft-365.md)