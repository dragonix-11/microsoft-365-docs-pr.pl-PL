---
title: Wdrażanie aktualizacji dla programu Microsoft Defender dla punktu końcowego na komputerze Mac
description: Kontrolowanie aktualizacji programu Microsoft Defender dla punktu końcowego na komputerze Mac w środowiskach przedsiębiorstwa.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, updates, deploy
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
ms.openlocfilehash: ceff362daeb2054b6037ea0eecbeafbb9dbed4f3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019238"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>Wdrażanie aktualizacji programu Microsoft Defender dla punktu końcowego w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Program Microsoft Defender for Endpoint w systemie macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Firma Microsoft regularnie publikuje aktualizacje oprogramowania w celu zwiększenia wydajności, zabezpieczeń i dostarczania nowych funkcji.

Aby zaktualizować program Microsoft Defender for Endpoint w systemie macOS, używany jest program o nazwie Microsoft AutoUpdate (MAU). Domyślnie program MAU automatycznie sprawdza aktualizacje codziennie, ale możesz zmienić to ustawienie na cotygodniowe, miesięczne lub ręczne.

![Zrzut ekranu: mau.](images/MDATP-34-MAU.png)

Jeśli zdecydujesz się wdrożyć aktualizacje za pomocą narzędzi do dystrybucji oprogramowania, musisz skonfigurować program MAU tak, aby ręcznie sprawdzał aktualizacje oprogramowania. Preferencje można wdrożyć, aby skonfigurować sposób i czas, w którym program MAU sprawdza aktualizacje dla komputerów Mac w organizacji.

## <a name="use-msupdate"></a>Użyj programu msupdate

Program MAU zawiera narzędzie wiersza polecenia, nazywane *msupdate*, zaprojektowane dla administratorów IT, aby mieli bardziej dokładną kontrolę nad stosowanymi aktualizacjami. Instrukcje dotyczące korzystania z tego narzędzia można znaleźć w tece Aktualizowanie [Office dla komputerów Mac przy użyciu programu msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate).

W programie MAU identyfikator aplikacji Microsoft Defender for Endpoint w systemie macOS to *WDAV00*. Aby pobrać i zainstalować najnowsze aktualizacje programu Microsoft Defender dla punktu końcowego w systemie macOS, wykonaj następujące polecenie w oknie programu Terminal:

```dos
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>Ustawianie preferencji programu Microsoft AutoUpdate

W tej sekcji opisano najczęściej używane preferencje, za pomocą których można skonfigurować aplikację mau. Te ustawienia można wdrożyć jako profil konfiguracji za pośrednictwem konsoli zarządzania, z których korzysta twój przedsiębiorstwo. Przykład profilu konfiguracji przedstawiono w poniższych sekcjach.

### <a name="set-the-channel-name"></a>Ustawianie nazwy kanału

Kanał ten określa typ i częstotliwość aktualizacji oferowanych za pośrednictwem programu MAU. Urządzenia w `Beta` mogą wypróbować nowe funkcje przed urządzeniami w i `Preview` `Current`.

Kanał `Current` zawiera najbardziej stabilną wersję produktu.

> [!IMPORTANT]
> Przed programem Microsoft AutoUpdate w wersji 4.29 kanały miały inne nazwy:
>
> - `Beta` otrzymał nazwę `InsiderFast` (niejawny program testów z szybkimi niejawnym programem testów)
> - `Preview` został nazwany `External` (Niejawny program testów : wolne informacje)
> - `Current` nazwano `Production`

> [!TIP]
> Aby móc wyświetlić podgląd nowych funkcji i przekazać wczesne opinie, zalecamy skonfigurowanie na niektórych urządzeniach w przedsiębiorstwie ustawień `Beta` lub `Preview`.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|ChannelName|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|Beta <p> Wersja zapoznawcza <p> Bieżący|
|||

> [!WARNING]
> To ustawienie zmienia kanał dla wszystkich aplikacji zaktualizowanych za pomocą programu Microsoft AutoUpdate. Aby zmienić kanał tylko dla programu Microsoft Defender dla punktu końcowego w systemie macOS, `[channel-name]` wykonaj następujące polecenie po zamianie na odpowiedni kanał:
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>Ustawianie częstotliwości sprawdzania aktualizacji

Zmień, jak często ma być wyszukiwane aktualizacje.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|UpdateCheckFrequency|
|**Typ danych**|Liczba całkowita|
|**Wartość domyślna**|720 (minuty)|
|**Komentowanie**|Ta wartość jest ustawiana w minutach.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>Zmienianie sposobu interakcji użytkownika mau z aktualizacjami

Zmienianie sposobu wyszukiwania aktualizacji przez programu MAU.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|HowToCheck|
|**Typ danych**|Ciąg|
|**Dopuszczalne wartości**|Ręcznie <p> AutomaticCheck <p> AutomaticDownload|
|**Komentowanie**|Pamiętaj, że jeśli to możliwe, pobieranie i instalowanie w trybie dyskretnym odbywa się przy automatycznym pobieraniu.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>Zmienianie ustawienia, czy jest włączony przycisk Sprawdź aktualizacje

Określenie, czy użytkownicy lokalni będą mogli klikać opcję "Sprawdź aktualizacje" w interfejsie użytkownika programu Microsoft AutoUpdate.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|EnableCheckForUpdatesButton|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|True (domyślne) <p> False (Fałsz|
|||

### <a name="disable-insider-checkbox"></a>Wyłącz pole wyboru Niejawny program testów

Ma wartość True (Prawda), aby "Dołącz do Office niejawnego programu testów..." niedostępne/wyszasowane dla użytkowników.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|DisableInsiderCheckbox|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|Fałsz (domyślnie) <p> True (Prawda)|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>Ograniczanie telemetrii wysyłanej z usługi MAU

Ustaw wartość False (Fałsz), aby wysyłać minimalne dane pulsu, bez użycia aplikacji i bez szczegółów środowiska.

<br>

****

|Sekcja|Value|
|---|---|
|**Domain (Domena)**|`com.microsoft.autoupdate2`|
|**Klucz**|SendAllTelemetryEnabled|
|**Typ danych**|Wartość logiczna|
|**Dopuszczalne wartości**|True (domyślne) <p> False (Fałsz|
|||

## <a name="example-configuration-profile"></a>Przykładowy profil konfiguracji

Poniższy profil konfiguracji służy do:

- Umieść urządzenie w kanale produkcji
- Automatyczne pobieranie i instalowanie aktualizacji
- Włączanie przycisku "Sprawdź aktualizacje" w interfejsie użytkownika
- Zezwalaj użytkownikom na urządzeniu na zarejestrowanie się w kanałach niejawnego programu testów

> [!WARNING]
> Poniżej przedstawiono konfigurację przykładową i nie należy jej używać w środowisku produkcyjnym bez odpowiedniego przeglądu ustawień i dostosowania konfiguracji.

> [!TIP]
> Aby móc wyświetlić podgląd nowych funkcji i przekazać wczesne opinie, zalecamy skonfigurowanie na niektórych urządzeniach w przedsiębiorstwie ustawień `Beta` lub `Preview`.

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

Aby skonfigurować jednostkę MAU, możesz wdrożyć ten profil konfiguracji za pomocą narzędzia do zarządzania, z których korzysta twój przedsiębiorstwo:

- Z usługi JAMF przekaż ten profil konfiguracji i ustaw domenę preferencji na *com.microsoft.autoupdate2*.
- Z usługi Intune przekaż ten profil konfiguracji i ustaw nazwę niestandardowego profilu konfiguracji na *com.microsoft.autoupdate2*.

## <a name="resources"></a>Zasoby

- [odwołanie do msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate)
