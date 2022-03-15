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
ms.openlocfilehash: 9ab3bb8e352a90cd4cef0c3c56496b3431e8b746
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2022
ms.locfileid: "63494460"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Włączanie nowoczesnego uwierzytelniania dla pakietu Office 2013 na urządzeniach z systemem Windows

Aby włączyć nowoczesne uwierzytelnianie na dowolnych urządzeniach z systemem Windows, na których zainstalowano pakiet Office 2013, musisz najpierw ustawić określone klucze rejestru.
  
## <a name="enable-modern-authentication-for-office-2013-clients"></a>Włączanie nowoczesnego uwierzytelniania dla klientów pakietu Office 2013

> [!NOTE]
> Dla klientów pakietu Office 2016 nowoczesne uwierzytelnianie jest już włączone. Nie musisz ustawiać kluczy rejestru dla pakietu Office 2016. 
  
Aby włączyć nowoczesne uwierzytelnianie na dowolnych urządzeniach z systemem Windows (na przykład komputerów przenośnych i tabletów), na których zainstalowano pakiet Microsoft Office 2013, musisz ustawić poniższe klucze rejestru. Klucze należy ustawić na każdym urządzeniu, na którym chcesz włączyć nowoczesne uwierzytelnianie:

<br>

****

|Klucz rejestru|Wpisać|Value|
|:---|:---:|---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|
|

Utwórz lub zmodyfikuj poniższe klucze rejestru, aby wymusić Outlook używania nowszej metody uwierzytelniania dla usług sieci Web, takich jak EWS i autodiscover. Zalecamy, aby użytkownicy wymuszali Outlook nowoczesnego uwierzytelniania.

1. Zakończ pracę programu Outlook.

2. Uruchom Edytor rejestru, korzystając z jednej z poniższych procedur, odpowiednio do wersji programu Windows:

   - **Windows 10, Windows 8.1 i Windows 8: Naciśnij** klawisze Windows + R, aby otworzyć **okno dialogowe** Uruchamianie. Wpisz *regedit.exe*, a następnie naciśnij klawisz **Enter.**
   - **Windows 7: Kliknij** **przycisk Start**, *wpiszregedit.exe* w polu wyszukiwania, a następnie naciśnij klawisz **Enter.**

3. W Edytorze rejestru znajdź i kliknij następujący podklucz rejestru:

   ```console
   HKEY_CURRENT_USER\Software\Microsoft\Exchange\
   ```

4. Jeśli *brakuje klucza AlwaysUseMSOAuthForAutoDiscover* , wpisz *alwaysUseMSOAuthForAutoDiscover*, a następnie naciśnij klawisz **Enter.**

5. Kliknij prawym przyciskiem *myszy pozycję AlwaysUseMSOAuthForAutoDiscover*, a następnie kliknij polecenie **Modyfikuj.**

6. W **polu Dane** wartości wpisz **wartość 1**, a następnie kliknij przycisk **OK.**

7. W Edytorze rejestru znajdź i kliknij następujący podklucz rejestru:

   ```console
   HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\
   ```

8. Jeśli wartości w powyższej tabeli już istnieją, zmodyfikuj je w razie potrzeby, a następnie zamknij Edytor rejestru. Jeśli tak się nie stanie, w menu Edycja wskaż polecenie **Nowy, a** następnie kliknij pozycję Wartość **DWORD** brakujących klawiszy. 

9. Jeśli na przykład brakuje klucza *EnableADAL* , wpisz *EnableADAL*, a następnie naciśnij klawisz **Enter.**

10. Kliknij prawym przyciskiem *myszy pozycję EnableADAL*, a następnie kliknij polecenie **Modyfikuj.**

11. W **polu Dane** wartości wpisz **wartość 1**, a następnie kliknij przycisk **OK.**

12. W razie potrzeby wykonaj tę samą czynności dla klucza wersji. 

13. **Zamknij Edytor rejestru.**

Po skonfigurowaniu kluczy rejestru możesz skonfigurować aplikacje urządzeń z systemem Office 2013 do korzystania z uwierzytelniania wieloskładnikowego [(MFA)](set-up-multi-factor-authentication.md) z usługą Microsoft 365. 
  
Aby zmiana została zastosowana, użytkownik, który obecnie jest zalogowany w dowolnej aplikacji klienckiej, musi się wylogować i zalogować ponownie. W przeciwnym razie usługa MRU i ustawienia mobilne będą niedostępne do czasu nawiązynia tożsamości.
  
## <a name="disable-modern-authentication-on-devices"></a>Wyłączanie nowoczesnego uwierzytelniania na urządzeniach

Aby wyłączyć nowoczesne uwierzytelnianie na danym urządzeniu, ustaw na nim następujące klucze rejestru:

<br>

****

|Klucz rejestru|Wpisać|Value|
|:---|:---:|---:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
|
   
## <a name="related-content"></a>Zawartość pokrewna

[Zaloguj się do Office 2013 przy użyciu drugiej metody weryfikacji](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb) (artykuł)\
[Outlook hasło i nie łączy się z siecią](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled) przy użyciu nowoczesnego Office 365 uwierzytelniania (artykuł)
