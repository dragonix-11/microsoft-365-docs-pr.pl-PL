---
title: Na urządzeniach z systemem macOS można korzystać z Microsoft 365 zgodności przy Microsoft Intune (wersja zapoznawcza)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Dowiedz się, jak korzystać z urządzeń z systemem macOS w nowych Microsoft 365 zgodności przy Microsoft Intune (wersja zapoznawcza)
ms.openlocfilehash: 5f8dd27490992e15d53dfc10311ce7b23b99683a
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526516"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview"></a>Wdychaj i wydojaj urządzenia z systemem macOS Microsoft 365 rozwiązania zgodności przy użyciu usługi Intune (wersja preview)

Intune umożliwia dołączanie urządzeń z systemem macOS do Microsoft 365 zgodności.

> [!IMPORTANT]
> Skorzystaj z tej ***procedury, jeśli*** na urządzeniach z systemem macOS nie wdrożono programu Microsoft Defender for Endpoint (MDE)

**Dotyczy:**

- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, [że urządzenia z systemem macOS są podłączone do usługi Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) i zarejestrowane w Portal firmy [aplikacji](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Upewnij się, że masz dostęp do centrum [Microsoft Endpoint Manager sieci.](https://endpoint.microsoft.com/#home)
- To obsługuje system macOS w wersji Catalina w wersji 10.15 i w wersji wyższej.
- Utwórz grupy użytkowników, do których chcesz przypisać aktualizacje konfiguracji.
- Instalowanie przeglądarki Edge w wersji 95+ na urządzeniach z systemem macOS 


## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>Na urządzeniach z systemem macOS można Microsoft 365 rozwiązania do zgodności przy użyciu Microsoft Intune

Proces dołączania urządzenia z systemem macOS do rozwiązań zgodności jest procesem 6-fazowym.

1. [Tworzenie profilów konfiguracji systemu](#create-system-configuration-profiles)
1. [Pobierz pakiet dołączania urządzenia](#get-the-device-onboarding-package)
1. [Wdrażanie pakietu wdrażania](#deploy-the-onboarding-package)
1. [Włącz rozszerzenie systemu](#enable-system-extension)
1. [Uzyskaj pakiet instalacyjny](#get-the-installation-package)
1. [Wdrażanie pakietu instalacyjnego](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>Tworzenie profilów konfiguracji systemu

1. Te pliki będą potrzebne do tej procedury.

|wymagany dla |źródło |
|---------|---------|
|Pakiet dołączający    |pobrane z pakietu **dołączania portalu** zgodności, nazwa *plikuDeviceComplianceOnboarding.xml* |
|ułatwienia dostępu |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
pełny dostęp do dysku     |[fullconfig.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Network filer| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|Rozszerzenia systemu |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|Preferencja MDE     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|Preferencja użytkownika mau|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Pakiet instalacyjny     |pobrane z pakietu instalacyjnego portalu **zgodności**, nazwa pliku *\*wdav.pkg*\* |

> [!TIP]
> Możesz pobrać pliki *.mobileconfig* pojedynczo lub w [jednym połączonym pliku](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , który zawiera:
> - accessibility.mobileconfig
> - fullconfig.mobileconfig
> - netfilter.mobileconfig
> - rozszerzenia systemowe
>
>Jeśli którykolwiek z tych pojedynczych plików zostanie zaktualizowany, konieczne będzie pobranie ponownie połączonego pliku lub pojedynczego aktualizowanego pliku.

<!--2. Copy this code and save it in a file named `com.microsoft.autoupdate2.xml`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>B762FF60-6ACB-4A72-9E72-459D00C936F3</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.autoupdate2</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft AutoUpdate settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft AutoUpdate configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
            <key>PayloadUUID</key>
            <string>5A6F350A-CC2C-440B-A074-68E3F34EBAE9</string>
            <key>PayloadType</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadOrganization</key>
            <string>Microsoft</string>
            <key>PayloadIdentifier</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft AutoUpdate configuration settings</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>ChannelName</key>
            <string>Production</string>
            <key>HowToCheck</key>
            <string>AutomaticDownload</string>
            <key>EnableCheckForUpdatesButton</key>
            <true/>
            <key>DisableInsiderCheckbox</key>
            <false/>
            <key>SendAllTelemetryEnabled</key>
            <true/>
            </dict>
        </array>
    </dict>
</plist>
```
-->

2. Otwórz centrum **Microsoft Endpoint Manager** >  **UrządnianiaKonfiguracja** >  **profilów**.

1. Wybierz: **Utwórz profil** 

1. Wybierz pozycję:
    1. **Platforma = macOS**
    1. **Typ profilu = Szablony**
    1. **Nazwa szablonu = Niestandardowe**

1. Wybierz pozycję **Create (Utwórz)**

1. W tym przykładzie wybierz nazwę profilu, na przykład *AccessibilityformacOS* . Wybierz przycisk **Dalej**.

1. Wybierz plik **accessibility.mobileconfig** pobrany w kroku 1 jako plik profilu konfiguracji.

1. Wybierz przycisk **Dalej**

1. Na **karcie Zadania dodaj** grupę, w której chcesz wdrożyć te konfiguracje, i wybierz pozycję **Dalej**.

1. Przejrzyj ustawienia i wybierz pozycję **Utwórz,** aby wdrożyć konfigurację.

1. Powtórz kroki od 3 do 11 w celu utworzenia profilów dla:
    1. **fullconfig.mobileconfig** file
    1. **com.microsoft.autoupdate2.xml** pliku
    1. Preferencje MDE **com.microsoft.wdav.xml** pliku
        1. ustaw aparat antywirusowy `passive mode` = `true` lub `false`. Użyj, `true`jeśli wdrażasz tylko DLP. Użyj `false` wartości lub nie przypisz jej, jeśli wdrażasz funkcję DLP i program Microsoft Defender for Endpoint (MDE).
    1. **netfilter.mobileconfig**
 
1. Otwórz **profile** **DevicesConfiguration** > , powinny być tam dostępne utworzone profile.

1. Na **stronie Profile konfiguracji** wybierz utworzony profil, w tym przykładzie *AccessibilityformacOS* i wybierz pozycję Stan urządzenia, aby  wyświetlić listę urządzeń i stan wdrożenia profilu konfiguracji.

### <a name="get-the-device-onboarding-package"></a>Pobierz pakiet dołączania urządzenia

1. W **Centrum zgodności otwórz** **Ustawienia** >  **Dołączanie i** wybierz pozycję **Dołączanie**.
 
1. W **przypadku opcji Wybierz system operacyjny, aby rozpocząć proces dołączania** , wybierz **pozycję macOS**.
 
1. W **przypadku metody wdrażania** **wybierz pozycję Zarządzanie urządzeniami przenośnymi/Microsoft Intune**.
 
1. Wybierz **pozycję Pobierz pakiet dołączający**. Kod dołączania znajduje *się wDeviceComplianceOnboarding.xml* pliku.

### <a name="deploy-the-onboarding-package"></a>Wdrażanie pakietu wdrażania

1. Otwórz centrum **Microsoft Endpoint Manager** >  **UrządnianiaKonfiguracja** >  **profilów**.

1. Wybierz pozycję: **Utwórz profil**. 

1. Wybierz pozycję:
    1. **Platforma = macOS**
    1. **Typ profilu = Szablony**
    1. **Nazwa szablonu = Niestandardowe**

1. Wybierz pozycję **Create (Utwórz)**

1. W tym przykładzie wybierz nazwę profilu, taką jak *OnboardingPackage* . Wybierz przycisk **Dalej**.

1. Wybierz plik *DeviceComplianceOnboarding.xml* jako plik profilu konfiguracji.

1. Wybierz przycisk **Dalej**

1. Na **karcie Zadania dodaj** grupę, w której chcesz wdrożyć te konfiguracje, i wybierz pozycję **Dalej**.

1. Przejrzyj ustawienia i wybierz pozycję **Utwórz,** aby wdrożyć konfigurację.

### <a name="enable-system-extension"></a>Włącz rozszerzenie systemu

1. W centrum **Microsoft Endpoint Manager w** obszarze **Profile** konfiguracji wybierz pozycję **Utwórz profil**

1. Wybierz pozycję:
    1. **Platforma = macOS**
    1. **Typ profilu = Szablony**
    1. **Nazwa szablonu = Rozszerzenia**

1. Wybierz pozycję **Create (Utwórz)**

1. Na karcie **Podstawy** nadaj temu noweowi profilowi nazwę.

1. Na karcie **Ustawienia konfiguracji** rozwiń **pozycję Rozszerzenia systemowe**.

1. W **obszarze Identyfikator pakietu** i **Identyfikator zespołu** ustaw te wartości.

|Identyfikator pakietu  |Identyfikator zespołu  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. Na **karcie Zadania dodaj** grupę, w której chcesz wdrożyć te konfiguracje, i wybierz pozycję **Dalej**.

1. Wybierz **pozycję Dalej** , aby wdrożyć konfigurację.

### <a name="get-the-installation-package"></a>Uzyskaj pakiet instalacyjny

1. W **Centrum zgodności otwórz** **Ustawienia** >  **Dołączanie i** wybierz pozycję **Dołączanie**.
 
1. Aby **rozpocząć proces dołączania do aplikacji Wybierz system operacyjny** , wybierz **macOS**
 
1. W **przypadku metody wdrażania** **wybierz pozycję Zarządzanie urządzeniami przenośnymi/Microsoft Intune**
 
1. Wybierz **pozycję Pobierz pakiet instalacyjny**. Spowoduje to nadanie *pliku wdav.pkg* .

> [!IMPORTANT]
> Przed wdrożeniem *wdav.pkg.* za pośrednictwem usługi Intune, należy ją ponownie sformatować za pomocą narzędzi do zawijania aplikacji *Intune dla komputerów Mac* do formatu *wdav.pkg.intunemac* .
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>Wdrażanie pakietu instalacyjnego DLP firmy Microsoft

1. Postępuj zgodnie z procedurami w temacie Jak dodać aplikacje biznesowe [macOS (LOB)](/mem/intune/apps/lob-apps-macos) do programu Microsoft Intune, aby przekonwertować *plik wdav.pkg* na odpowiedni format i wdrożyć go za pośrednictwem usługi Intune.

## <a name="offboard-macos-devices-using-intune"></a>Urządzenia z systemem macOS w usłudze Intune

> [!NOTE]
> Wynoszenie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie sześć miesięcy.

2. W **Microsoft Endpoint Manager Otwórz** **urządzeniaKonfiguracja** >  profile powinny być tam dostępne utworzone profile.

1. Na **stronie Profile konfiguracji** wybierz profil *wdav.pkg.intunemac* .

1. Wybierz **pozycję Stan** urządzenia, aby wyświetlić listę urządzeń i stan wdrożenia profilu konfiguracji

1. Otwórz **okno Właściwości** **i przydziały**

1. Usuń grupę z zadania. Spowoduje to odinstalowanie *pakietu wdav.pkg.intunemac* i odinstalowanie urządzenia macOS z rozwiązań zgodności.
