---
title: Włączanie nowoczesnego uwierzytelniania dla Office 2013 na Windows urządzeniach
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
ms.openlocfilehash: 468658c3b346c7923937ff9595699a20306ed6a9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754182"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Włączanie nowoczesnego uwierzytelniania dla Office 2013 na Windows urządzeniach

Microsoft Office 2013 na komputerach Windows Microsoft obsługuje nowoczesne uwierzytelnianie. Jednak aby je włączyć, musisz skonfigurować następujące klucze rejestru:

|Klucz rejestru|Wpisać|Value|
|:---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

> [!NOTE]
> Nowoczesne uwierzytelnianie jest już włączone w Office 2016 lub nowszym. Nie musisz ustawiać tych kluczy rejestru dla nowszych wersji programu Office.

## <a name="enable-modern-authentication-for-office-2013-clients"></a>Włączanie nowoczesnego uwierzytelniania dla klientów pakietu Office 2013

1. Zamknij program Outlook.

2. Skopiuj i wklej następujący tekst w Notatnik:

   ```text
   Windows Registry Editor Version 5.00

   [HKEY_CURRENT_USER\Software\Microsoft\Exchange]
   "AlwaysUseMSOAuthForAutoDiscover"=dword:00000001

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
   "EnableADAL"=dword:00000001
   "Version"=dword:00000001
   ```

3. Zapisz plik z rozszerzeniem reg zamiast .txt w łatwej do znalezienia lokalizacji. Na przykład `C:\Data\Office2013_Enable_ModernAuth.reg`.

4. Otwórz Eksploratora plików (dawniej znanego jako Windows), przejdź do lokalizacji właśnie zapisanego pliku reg, a następnie kliknij go dwukrotnie.

5. W **wyświetlonym oknie dialogowym** Kontrola konta użytkownika kliknij przycisk **Tak** , aby zezwolić aplikacji na zmiany na urządzeniu.

6. W **wyświetlonym oknie dialogowym** z ostrzeżeniem Edytor rejestru kliknij przycisk **Tak** , aby zaakceptować zmiany.

Po skonfigurowaniu kluczy rejestru możesz skonfigurować aplikacje pakietu Office 2013 do używania uwierzytelniania wieloskładnikowego (MFA) z usługą Microsoft 365. Aby uzyskać więcej informacji, [zobacz Konfigurowanie uwierzytelniania wieloskładnikowego](set-up-multi-factor-authentication.md).

Jeśli jesteś obecnie zalogowany do dowolnej aplikacji klienckiej Office, musisz się wylogować i zalogować ponownie, aby zmiana została w związku z tym wylogowywana. W przeciwnym razie usługa MRU i ustawienia mobilne będą niedostępne do czasu nawiązynia tożsamości.

## <a name="disable-modern-authentication-on-devices"></a>Wyłączanie nowoczesnego uwierzytelniania na urządzeniach

Procedura wyłączania nowoczesnego uwierzytelniania na urządzeniu jest bardzo podobna, ale wymaganych jest mniej kluczy rejestru i trzeba ustawić dla nich wartość 0.

|Klucz rejestru|Wpisać|Value|
|---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|

```text
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Exchange]
"AlwaysUseMSOAuthForAutoDiscover"=dword:00000000

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
"EnableADAL"=dword:00000000
```

## <a name="related-content"></a>Zawartość pokrewna

[Logowanie do pakietu Office 2013 przy użyciu drugiej metody weryfikacji](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)

[Outlook monituje o hasło i nie łączy się z siecią przy użyciu nowoczesnego uwierzytelniania Office 365](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled)
