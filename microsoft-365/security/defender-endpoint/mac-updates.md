---
title: Wdrażanie aktualizacji dla Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac
description: Kontroluj aktualizacje dla Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac w środowiskach przedsiębiorstwa.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, aktualizacje, wdrażanie
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4612c7ca68ab0b55fa2a2f28821cb5baef6ff6e9
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669347"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>Wdrażanie aktualizacji dla Ochrona punktu końcowego w usłudze Microsoft Defender na macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Usługa ochrony punktu końcowego w usłudze Microsoft Defender w systemie macOS](microsoft-defender-endpoint-mac.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Firma Microsoft regularnie publikuje aktualizacje oprogramowania w celu zwiększenia wydajności, bezpieczeństwa i dostarczania nowych funkcji.

Aby zaktualizować Ochrona punktu końcowego w usłudze Microsoft Defender na macOS, jest używany program o nazwie Microsoft AutoUpdate (MAU). Domyślnie usługa MAU automatycznie sprawdza dostępność aktualizacji codziennie, ale można ją zmienić na co tydzień, co miesiąc lub ręcznie.

:::image type="content" source="images/MDATP-34-MAU.png" alt-text="MAU" lightbox="images/MDATP-34-MAU.png":::

Jeśli zdecydujesz się wdrożyć aktualizacje przy użyciu narzędzi dystrybucji oprogramowania, skonfiguruj narzędzie MAU do ręcznego sprawdzania dostępności aktualizacji oprogramowania. Możesz wdrożyć preferencje, aby skonfigurować sposób i czas sprawdzania aktualizacji dla komputerów Mac w organizacji przez program MAU.

## <a name="use-msupdate"></a>Korzystanie z biblioteki msupdate

Mau zawiera narzędzie wiersza polecenia o nazwie *msupdate*, które jest przeznaczone dla administratorów IT, dzięki czemu mają precyzyjniejszą kontrolę nad zastosowaniem aktualizacji. Instrukcje dotyczące korzystania z tego narzędzia można znaleźć w [temacie Update Office dla komputerów Mac przy użyciu polecenia msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate).

W programie MAU identyfikatorem aplikacji dla Ochrona punktu końcowego w usłudze Microsoft Defender na macOS jest *WDAV00*. Aby pobrać i zainstalować najnowsze aktualizacje dla Ochrona punktu końcowego w usłudze Microsoft Defender na macOS, wykonaj następujące polecenie w oknie terminalu:

```dos
cd /Library/Application\ Support/Microsoft/MAU2.0/Microsoft\ AutoUpdate.app/Contents/MacOS
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>Ustawianie preferencji dla usługi Microsoft AutoUpdate

W tej sekcji opisano najbardziej typowe preferencje, których można użyć do skonfigurowania jednostki MAU. Te ustawienia można wdrożyć jako profil konfiguracji za pośrednictwem konsoli zarządzania używanej przez przedsiębiorstwo. Przykład profilu konfiguracji przedstawiono w poniższych sekcjach.

### <a name="set-the-channel-name"></a>Ustawianie nazwy kanału

Kanał określa typ i częstotliwość aktualizacji oferowanych za pośrednictwem jednostki MAU. Urządzenia w programie `Beta` mogą wypróbować nowe funkcje przed urządzeniami w systemach `Preview` i `Current`.

Kanał `Current` zawiera najbardziej stabilną wersję produktu.

> [!IMPORTANT]
> Przed programem Microsoft AutoUpdate w wersji 4.29 kanały miały różne nazwy:
>
> - `Beta` został nazwany `InsiderFast` (Insider Fast)
> - `Preview` został nazwany `External` (Insider Slow)
> - `Current` został nazwany `Production`

> [!TIP]
> Aby wyświetlić podgląd nowych funkcji i przekazać wczesną opinię, zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie do `Beta` lub `Preview`.

<br>

****

|Sekcji|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|Channelname|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|Beta <p> Wersja zapoznawcza <p> Bieżącego|
|||

> [!WARNING]
> To ustawienie zmienia kanał dla wszystkich aplikacji, które są aktualizowane za pośrednictwem usługi Microsoft AutoUpdate. Aby zmienić kanał tylko dla Ochrona punktu końcowego w usłudze Microsoft Defender na macOS, wykonaj następujące polecenie po zastąpieniu `[channel-name]` go odpowiednim kanałem:
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>Ustawianie częstotliwości sprawdzania aktualizacji

Zmień częstotliwość wyszukiwania aktualizacji przez jednostki MAU.

<br>

****

|Sekcji|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|UpdateCheckFrequency|
|**Typ danych**|Liczba całkowita|
|**Wartość domyślna**|720 (minuty)|
|**Komentowanie**|Ta wartość jest ustawiana w minutach.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>Zmienianie sposobu interakcji mau z aktualizacjami

Zmień sposób wyszukiwania aktualizacji przez jednostki MAU.

<br>

****

|Sekcji|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|HowToCheck|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|Ręcznie <p> Automatyczne sprawdzanie <p> AutomaticDownload|
|**Komentowanie**|Pamiętaj, że funkcja AutomaticDownload wykona pobieranie i zainstalowanie w trybie dyskretnym, jeśli jest to możliwe.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>Zmienianie, czy przycisk "Sprawdź aktualizacje" jest włączony

Zmień, czy użytkownicy lokalni będą mogli kliknąć opcję "Sprawdź aktualizacje" w interfejsie użytkownika microsoft AutoUpdate.

<br>

****

|Sekcji|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|EnableCheckForUpdatesButton|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|True (wartość domyślna) <p> False|
|||

### <a name="disable-insider-checkbox"></a>Wyłącz pole wyboru Insider (Niejawny tester)

Ustaw wartość true na wartość "Dołącz do programu Office Insider Program..." pole wyboru jest niedostępne/wyszarzone dla użytkowników.

<br>

****

|Sekcji|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|DisableInsiderCheckbox|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|False (wartość domyślna) <p> True|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>Ograniczanie danych telemetrycznych wysyłanych z jednostki MAU

Ustaw wartość false, aby wysyłać minimalne dane pulsu, brak użycia aplikacji i brak szczegółów środowiska.

<br>

****

|Sekcji|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|SendAllTelemetryEnabled|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|True (wartość domyślna) <p> False|
|||

## <a name="example-configuration-profile"></a>Przykładowy profil konfiguracji

Do tego celu jest używany następujący profil konfiguracji:

- Umieść urządzenie w kanale produkcyjnym
- Automatyczne pobieranie i instalowanie aktualizacji
- Włącz przycisk "Sprawdź aktualizacje" w interfejsie użytkownika
- Zezwalanie użytkownikom na urządzeniu na rejestrację w kanałach niejawnych testerów

> [!WARNING]
> Poniższa konfiguracja jest przykładową konfiguracją i nie powinna być używana w środowisku produkcyjnym bez odpowiedniego przeglądu ustawień i dostosowywania konfiguracji.

> [!TIP]
> Aby wyświetlić podgląd nowych funkcji i przekazać wczesną opinię, zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie do `Beta` lub `Preview`.

### <a name="jamf"></a>JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
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
</plist>
```

### <a name="intune"></a>Intune

```XML
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

Aby skonfigurować jednostkę MAU, możesz wdrożyć ten profil konfiguracji za pomocą narzędzia do zarządzania używanego przez przedsiębiorstwo:

- W narzędziu JAMF przekaż ten profil konfiguracji i ustaw domenę preferencji na *com.microsoft.autoupdate2*.
- Z Intune przekaż ten profil konfiguracji i ustaw niestandardową nazwę profilu konfiguracji na *com.microsoft.autoupdate2*.

## <a name="resources"></a>Zasoby

- [dokumentacja msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate)
