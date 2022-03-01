---
title: Przykłady zasad sterowania urządzeniami dla jamf
description: Dowiedz się, jak używać zasad sterowania urządzeniami, używając przykładów, których można używać z usługą JAMF.
keywords: microsoft, defender, endpoint, Microsoft Defender for Endpoint, mac, device, control, usb, wymiennych, nośniki, jamf
ms.prod: m365-security
ms.mktglfcycl: security
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
ms.openlocfilehash: 74925625f6d004c1901756cde75310b345dd5747
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011371"
---
# <a name="examples-of-device-control-policies-for-jamf"></a>Przykłady zasad sterowania urządzeniami dla jamf

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ten dokument zawiera przykłady zasad sterowania urządzeniami, które można dostosować dla swojej organizacji. Te przykłady mają zastosowanie, jeśli do zarządzania urządzeniami w przedsiębiorstwie używasz usługi JAMF.

## <a name="restrict-access-to-all-removable-media"></a>Ograniczanie dostępu do wszystkich nośników wymiennych

W poniższym przykładzie dostęp do wszystkich nośników wymiennych jest ograniczany. Zwróć uwagę `none` na uprawnienia, które są stosowane na najwyższym poziomie zasad, co oznacza, że wszystkie operacje na plikach będą zabronione.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>none</string>
            </array>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="set-all-removable-media-to-be-read-only"></a>Ustawianie wszystkich nośników wymiennych jako tylko do odczytu

W poniższym przykładzie wszystkie nośniki wymienne są konfigurowane jako tylko do odczytu. Zwróć uwagę `read` na uprawnienia stosowane na najwyższym poziomie zasad, co oznacza, że wszystkie operacje zapisu i wykonywania będą niedozwolone.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>read</string>
            </array>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="disallow-program-execution-from-removable-media"></a>Nie zezwalaj na wykonywanie programu na nośniku wymiennym

W poniższym przykładzie pokazano, jak można niedozwolone jest wykonywanie programu z nośników wymiennych. Zwróć uwagę `read` na `write` uprawnienia, które są stosowane na najwyższym poziomie zasad.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>read</string>
                <string>write</string>
            </array>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="restrict-all-devices-from-specific-vendors"></a>Ograniczanie wszystkich urządzeń od określonych dostawców

W poniższym przykładzie wszystkie urządzenia od określonych dostawców (w tym przypadku są oznaczone jako `fff0` i `4525`). Wszystkie inne urządzenia będą nieograniczone, ponieważ uprawnienia zdefiniowane na najwyższym poziomie zasad będą zawierały wszystkie możliwe uprawnienia (odczyt, zapis i wykonywanie).

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>read</string>
                <string>write</string>
                <string>execute</string>
            </array>
            <key>vendors</key>
            <dict>
                <key>fff0</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>none</string>
                    </array>
                </dict>
                <key>4525</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>none</string>
                    </array>
                </dict>
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="restrict-specific-devices-identified-by-vendor-id-product-id-and-serial-number"></a>Ograniczanie określonych urządzeń zidentyfikowanych za pomocą identyfikatora dostawcy, identyfikatora produktu i numeru seryjnego

W poniższym przykładzie ograniczenie dostępu do dwóch określonych urządzeń oznaczonych identyfikatorem `fff0`dostawcy , identyfikatorem produktu `1000`i numerami seryjnymi `04ZSSMHI2O7WBVOA` oraz `04ZSSMHI2O7WBVOB`. Na wszystkich pozostałych poziomach zasad uprawnienia obejmują wszystkie możliwe wartości (odczyt, zapis i wykonywanie), co oznacza, że wszystkie inne urządzenia będą nieograniczone.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>read</string>
                <string>write</string>
                <string>execute</string>
            </array>
            <key>vendors</key>
            <dict>
                <key>fff0</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>read</string>
                        <string>write</string>
                        <string>execute</string>
                    </array>
                    <key>products</key>
                    <dict>
                        <key>1000</key>
                        <dict>
                            <key>permission</key>
                            <array>
                                <string>read</string>
                                <string>write</string>
                                <string>execute</string>
                            </array>
                            <key>serialNumbers</key>
                            <dict>
                                <key>04ZSSMHI2O7WBVOA</key>
                                <array>
                                  <string>none</string>
                                </array>
                                <key>04ZSSMHI2O7WBVOB</key>
                                <array>
                                  <string>none</string>
                                </array>
                            </dict>
                        </dict>
                    </dict>
                </dict>
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie sterowania urządzeniami dla systemu macOS](mac-device-control-overview.md)
