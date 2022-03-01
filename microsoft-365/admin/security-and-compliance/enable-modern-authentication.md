---
title: Włączanie nowoczesnego uwierzytelniania dla pakietu Office 2013 na urządzeniach z systemem Windows
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7dc1c01a-090f-4971-9677-f1b192d6c910
description: Dowiedz się, jak ustawić klucze rejestru w celu włączenia nowoczesnego uwierzytelniania dla urządzeń, na Microsoft Office 2013.
ms.openlocfilehash: c5af8daa0538a1eb89521b12d1c85c310df6d012
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2021
ms.locfileid: "63005231"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Włączanie nowoczesnego uwierzytelniania dla pakietu Office 2013 na urządzeniach z systemem Windows

Aby włączyć nowoczesne uwierzytelnianie na dowolnych urządzeniach z systemem Windows, na których zainstalowano pakiet Office 2013, musisz najpierw ustawić określone klucze rejestru.
  
## <a name="enable-modern-authentication-for-office-2013-clients"></a>Włączanie nowoczesnego uwierzytelniania dla klientów pakietu Office 2013

> [!NOTE]
> Dla klientów pakietu Office 2016 nowoczesne uwierzytelnianie jest już włączone. Nie musisz ustawiać kluczy rejestru dla pakietu Office 2016. 
  
Aby włączyć nowoczesne uwierzytelnianie na dowolnych urządzeniach z systemem Windows (na przykład komputerów przenośnych i tabletów), na których zainstalowano pakiet Microsoft Office 2013, musisz ustawić poniższe klucze rejestru. Klucze należy ustawić na każdym urządzeniu, na którym chcesz włączyć nowoczesne uwierzytelnianie:
  
|**Klucz rejestru**|**Type**|**Wartość** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |
   
Po skonfigurowaniu kluczy rejestru możesz skonfigurować aplikacje urządzeń z systemem Office 2013 do korzystania z uwierzytelniania wieloskładnikowego [(MFA)](set-up-multi-factor-authentication.md) z usługą Microsoft 365. 
  
Aby zmiana została zastosowana, użytkownik, który obecnie jest zalogowany w dowolnej aplikacji klienckiej, musi się wylogować i zalogować ponownie. W przeciwnym razie usługa MRU i ustawienia mobilne będą niedostępne do czasu nawiązynia tożsamości.
  
## <a name="disable-modern-authentication-on-devices"></a>Wyłączanie nowoczesnego uwierzytelniania na urządzeniach

Aby wyłączyć nowoczesne uwierzytelnianie na danym urządzeniu, ustaw na nim następujące klucze rejestru:
  
|**Klucz rejestru**|**Type**|**Wartość**|
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL |REG_DWORD|0|
   
## <a name="related-content"></a>Zawartość pokrewna

[Zaloguj się do Office 2013 przy użyciu drugiej metody weryfikacji](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb) (artykuł)\
[Outlook hasło i nie łączy się z siecią](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled) przy użyciu nowoczesnego Office 365 uwierzytelniania (artykuł)

