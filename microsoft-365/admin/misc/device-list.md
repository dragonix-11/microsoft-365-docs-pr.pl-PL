---
title: Plik CSV z listą urządzeń
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
description: Dowiedz się, jak zrobić plik CSV dla rozwiązania AutoPilot w programie Microsoft 365 dla firm.
ms.openlocfilehash: 62dbcddbdab1a08ab3b19c6616b814c421a57c04
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2021
ms.locfileid: "62996395"
---
# <a name="device-list-csv-file"></a>Plik CSV z listą urządzeń

## <a name="device-list-csv-file-format"></a>Lista urządzeń .csv formacie pliku

Do zarządzania urządzeniami i wdrażania ich Windows rozwiązania Autopilot jest potrzebny plik .csv zawierający konkretne informacje o urządzeniach.
  
Kolumny w pliku listy urządzeń muszą mieć następujące nagłówki w określonej kolejności:
  
- Kolumna A: Numer seryjny urządzenia

- Kolumna B: pozostaw puste

- Kolumna C: Skrót sprzętowy

Możesz uzyskać te informacje od producenta komputera lub użyć [skryptu programu PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo), który wygeneruje plik CSV. 

Gdy dodajesz urządzenia, musisz również dodać je do profilu. Profil służy do stosowania profilów wdrożenia z zastosowaniem rozwiązania AutoPilot do urządzenia lub grupy urządzeń.
  
## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 i zasoby dla firm](../../index.yml)
  
[Wprowadzenie do Microsoft 365 dla firm](../../admin/admin-overview/what-is-microsoft-365.md)