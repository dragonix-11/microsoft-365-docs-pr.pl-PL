---
title: "Ustawienia profilu rozwiązania AutoPilot \x97 informacje"
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
f1_keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
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
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: Profile rozwiązania AutoPilot ułatwiają kontrolowanie sposobu Windows na urządzeniach użytkowników. Profile zawierają ustawienia domyślne i opcjonalne, takie jak pomiń Cortana instalacji.
ms.openlocfilehash: bacbf4faff5078fc10e2921ee176143f5ba80b2a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983914"
---
# <a name="about-autopilot-profile-settings"></a>Ustawienia profilu rozwiązania AutoPilot  informacje

## <a name="autopilot-profile-settings"></a>Ustawienia profilu rozwiązania AutoPilot

Profile rozwiązania AutoPilot mogą pomóc w kontrolowaniu sposobu Windows na urządzeniach użytkowników. Profile zawierają następujące ustawienia.
  
 **Funkcje domyślne rozwiązania AutoPilot ustawiane automatycznie (wymagane):**
  
|**Ustawienie**|**Opis**|
|:-----|:-----|
|Pomiń Cortana, OneDrive i rejestracja OEM  <br/> |Pomija instalację aplikacji dla klientów osobistych, takich Cortana aplikacji osobistych OneDrive. Użytkownik urządzenia może je zainstalować później, o ile użytkownik jest administratorem lokalnym na urządzeniu. Rejestracja oryginalnego producenta zostanie pominięta, ponieważ urządzenie będzie zarządzane przez firmę Microsoft 365 Business Premium.  <br/> |
|Logowanie się za pomocą marki firmowej  <br/> |Jeśli w firmie jest znakowanie Dodaj firmę do strony [Microsoft 365](../setup/customize-sign-in-page.md) logowania, użytkownik urządzenia będzie miał to doświadczenie podczas logowania.  <br/> |
|Automatyczne rejestrowanie w uścisku usługi MDM ze skonfigurowanymi AAD kontami.  <br/> |Tożsamość użytkownika będzie zarządzana przez firmę Azure Active Directory, a użytkownicy będą logować się Windows i Microsoft 365 przy użyciu swoich Microsoft 365 Business Premium logowania.  <br/> |
   
 **Ustawienia opcjonalne:**
  
|**Ustawienie**|**Opis**|
|:-----|:-----|
|Pomiń ustawienia prywatności (domyślnie wyłączone)  <br/> |Jeśli ta opcja jest ustawiona na wartość **Wł**., użytkownik urządzenia nie zobaczy umowy licencyjnej urządzenia i nie zobaczy Windows po pierwszym się do urządzenia.  <br/> |
|Nie zezwalaj użytkownikowi na zostanie administratorem lokalnym  <br/> |Jeśli ta opcja jest ustawiona na **Wł**., użytkownik urządzenia nie będzie mógł zainstalować żadnych aplikacji osobistych, takich jak Cortana.<br/> |
