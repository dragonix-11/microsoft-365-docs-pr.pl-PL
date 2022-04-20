---
title: Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu Microsoft Intune
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
description: Dowiedz się, jak dołączać i dołączać urządzenia z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu Microsoft Intune
ms.openlocfilehash: 99a407b2b0c8d6a506cd138078b3f35cf9e5a232
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952979"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-intune"></a>Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu Intune

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Możesz użyć Intune, aby dołączyć urządzenia z systemem macOS do rozwiązań usługi Microsoft Purview.

> [!IMPORTANT]
> Użyj tej procedury, jeśli ***na*** urządzeniach z systemem macOS nie wdrożono Ochrona punktu końcowego w usłudze Microsoft Defender (MDE)

**Dotyczy:**

- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, że [urządzenia z systemem macOS są dołączone do Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) i są zarejestrowane w [aplikacji Portal firmy](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Upewnij się, że masz dostęp do [centrum Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home).
- Obsługuje to system macOS w wersji Catalina 10.15 lub nowszej.
- Utwórz grupy użytkowników, do których mają zostać przypisane aktualizacje konfiguracji.
- Instalowanie przeglądarki v95+ Edge na urządzeniach z systemem macOS 


## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Dołączanie urządzeń z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu Microsoft Intune

Dołączanie urządzenia z systemem macOS do rozwiązań zgodności jest procesem sześciofazowym.

1. [Tworzenie profilów konfiguracji systemu](#create-system-configuration-profiles)
1. [Pobieranie pakietu dołączania urządzenia](#get-the-device-onboarding-package)
1. [Wdrażanie pakietu dołączania](#deploy-the-onboarding-package)
1. [Włączanie rozszerzenia systemu](#enable-system-extension)
1. [Pobieranie pakietu instalacyjnego](#get-the-installation-package)
1. [Wdrażanie pakietu instalacyjnego](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>Tworzenie profilów konfiguracji systemu

1. Te pliki będą potrzebne do tej procedury.

|plik wymagany do |Źródła |
|---------|---------|
|Dołączanie pakietu    |pobrane z **pakietu dołączania** portalu zgodności, nazwy pliku *DeviceComplianceOnboarding.xml* |
|Dostępności |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
pełny dostęp do dysku     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Plik sieciowy| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|Rozszerzenia systemu |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|Preferencja zarządzania urządzeniami przenośnymi     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|Preferencja MAU|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Pakiet instalacyjny     |pobrany z portalu zgodności **Pakiet instalacyjny**, nazwa *\*pliku wdav.pkg*\* |

> [!TIP]
> Pliki *mobileconfig* można pobrać pojedynczo lub w [jednym połączonym pliku](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , który zawiera:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - rozszerzenia systemowe
>
>Jeśli którykolwiek z tych pojedynczych plików zostanie zaktualizowany, konieczne będzie ponowne pobranie połączonego pliku lub pojedynczego zaktualizowanego pliku indywidualnie.

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

2. Otwórz **Microsoft Endpoint Manager** **centerDevicesProfile** >  >  **konfiguracji**.

1. Wybierz: **Utwórz profil** 

1. Wybierz:
    1. **Platforma = macOS**
    1. **Typ profilu = Szablony**
    1. **Nazwa szablonu = Niestandardowa**

1. Wybierz **pozycję Utwórz**

1. W tym przykładzie wybierz nazwę profilu, na przykład *AccessibilityformacOS* . Wybierz przycisk **Dalej**.

1. Wybierz plik **accessibility.mobileconfig** pobrany w kroku 1 jako plik profilu konfiguracji.

1. Wybierz **pozycję Dalej**

1. Na **karcie Przypisania** dodaj grupę, do którą chcesz wdrożyć te konfiguracje, i wybierz pozycję **Dalej**.

1. Przejrzyj ustawienia i wybierz pozycję **Utwórz** , aby wdrożyć konfigurację.

1. Powtórz kroki 3–11, aby utworzyć profile dla:
    1. **plik fulldisk.mobileconfig**
    1. **plikcom.microsoft.autoupdate2.xml**
    1. Plik **com.microsoft.wdav.xml** preferencji MDE
        1. ustaw aparat `passive mode` = `true` antywirusowy lub .`false` Użyj polecenia `true`, jeśli wdrażasz tylko DLP. Użyj `false` wartości lub nie przypisz jej w przypadku wdrażania DLP i Ochrona punktu końcowego w usłudze Microsoft Defender (MDE).
    1. **netfilter.mobileconfig**
 
1. Otwórz **pozycję** **UrządzeniaProfile** >  konfiguracji. Powinny zostać tam wyświetlone utworzone profile.

1. Na stronie **Profile konfiguracji wybierz właśnie** utworzony profil, w tym *przykładzie AccessibilityformacOS* i wybierz pozycję **Stan urządzenia** , aby wyświetlić listę urządzeń i stan wdrożenia profilu konfiguracji.

### <a name="get-the-device-onboarding-package"></a>Pobieranie pakietu dołączania urządzenia

1. W **centrum zgodności** otwórz **Ustawienia** >  **Device Onboarding** i wybierz pozycję **Dołączanie**.
 
1. W **obszarze Wybierz system operacyjny, aby rozpocząć proces dołączania** wybierz pozycję **macOS**.
 
1. W obszarze **Metoda wdrażania** wybierz pozycję **Mobile Zarządzanie urządzeniami/Microsoft Intune**.
 
1. Wybierz pozycję **Pobierz pakiet dołączania**. Zawiera on kod dołączania w pliku *DeviceComplianceOnboarding.xml* .

### <a name="deploy-the-onboarding-package"></a>Wdrażanie pakietu dołączania

1. Otwórz **Microsoft Endpoint Manager** **centerDevicesProfile** >  >  **konfiguracji**.

1. Wybierz: **Utwórz profil**. 

1. Wybierz:
    1. **Platforma = macOS**
    1. **Typ profilu = Szablony**
    1. **Nazwa szablonu = Niestandardowa**

1. Wybierz **pozycję Utwórz**

1. W tym przykładzie wybierz nazwę profilu, na przykład *OnboardingPackage* . Wybierz przycisk **Dalej**.

1. Wybierz plik *DeviceComplianceOnboarding.xml* jako plik profilu konfiguracji.

1. Wybierz **pozycję Dalej**

1. Na **karcie Przypisania** dodaj grupę, do którą chcesz wdrożyć te konfiguracje, i wybierz pozycję **Dalej**.

1. Przejrzyj ustawienia i wybierz pozycję **Utwórz** , aby wdrożyć konfigurację.

### <a name="enable-system-extension"></a>Włączanie rozszerzenia systemu

1. W **centrum Microsoft Endpoint Manager** wybierz pozycję **Utwórz profil** w obszarze **Profile konfiguracji**

1. Wybierz:
    1. **Platforma = macOS**
    1. **Typ profilu = Szablony**
    1. **Nazwa szablonu = Rozszerzenia**

1. Wybierz **pozycję Utwórz**

1. Na **karcie Podstawy** nadaj nowemu profilowi nazwę.

1. Na karcie **Ustawienia konfiguracji** rozwiń węzeł **Rozszerzenia systemu**.

1. W obszarze **Identyfikator pakietu** i **identyfikator zespołu** ustaw te wartości

|Identyfikator pakietu  |Identyfikator zespołu  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. Na **karcie Przypisania** dodaj grupę, do którą chcesz wdrożyć te konfiguracje, i wybierz pozycję **Dalej**.

1. Wybierz pozycję **Dalej** , aby wdrożyć konfigurację.

### <a name="get-the-installation-package"></a>Pobieranie pakietu instalacyjnego

1. W **centrum zgodności** otwórz **Ustawienia** >  **Device Onboarding** i wybierz pozycję **Dołączanie**.
 
1. W obszarze **Wybierz system operacyjny, aby rozpocząć proces dołączania** wybierz system **macOS**
 
1. W obszarze **Metoda wdrażania** wybierz pozycję **Mobile Zarządzanie urządzeniami/Microsoft Intune**
 
1. Wybierz pozycję **Pobierz pakiet instalacyjny**. Spowoduje to podanie pliku *wdav.pkg* .

> [!IMPORTANT]
> Przed wdrożeniem pliku *wdav.pkg.* pakiet za pośrednictwem Intune, należy go sformatować przy użyciu *narzędzi opakowującego aplikacje Intune dla komputerów Mac* w formacie *wdav.pkg.intunemac*.
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>Wdrażanie pakietu instalacyjnego programu Microsoft DLP

1. Postępuj zgodnie z procedurami w temacie [Jak dodać aplikacje biznesowe dla systemu macOS do Microsoft Intune](/mem/intune/apps/lob-apps-macos), aby przekonwertować plik *wdav.pkg* na odpowiedni format i wdrożyć go za pośrednictwem Intune.

## <a name="offboard-macos-devices-using-intune"></a>Odłączanie urządzeń z systemem macOS przy użyciu Intune

> [!NOTE]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołanie do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie sześć miesięcy.

2. W **centrum Microsoft Endpoint Manager** otwórz pozycję **UrządzeniaProfile** >  konfiguracji, w tym miejscu powinny zostać wyświetlone utworzone profile.

1. Na stronie **Profile konfiguracji** wybierz profil *wdav.pkg.intunemac* .

1. Wybierz pozycję **Stan urządzenia** , aby wyświetlić listę urządzeń i stan wdrożenia profilu konfiguracji

1. **Otwieranie właściwości** i **przypisań**

1. Usuń grupę z przypisania. Spowoduje to odinstalowanie pakietu *wdav.pkg.intunemac* i odłączanie urządzenia z systemem macOS z rozwiązań zgodności.
