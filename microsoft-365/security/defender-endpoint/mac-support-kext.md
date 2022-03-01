---
title: Rozwiązywanie problemów z rozszerzeniem kernel w programie Microsoft Defender for Endpoint w systemie macOS
description: Rozwiązywanie problemów związanych z rozszerzeniem kernel w programie Microsoft Defender for Endpoint w systemie macOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, kernel, extension
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
ms.openlocfilehash: ba52d9587a2ac530eabeacf8c72336751a1a17d7
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63026628"
---
# <a name="troubleshoot-kernel-extension-issues-in-microsoft-defender-for-endpoint-on-macos"></a>Rozwiązywanie problemów z rozszerzeniem kernel w programie Microsoft Defender for Endpoint w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Program Microsoft Defender for Endpoint w systemie macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ten artykuł zawiera informacje na temat rozwiązywania problemów z rozszerzeniem kernel zainstalowanym jako część programu Microsoft Defender for Endpoint w systemie macOS.

Od wersji macOS High Sierra (10.13) system macOS wymaga jawnego zatwierdzenia wszystkich rozszerzeń kernelu, zanim będą one mogły działać na urządzeniu.

Jeśli nie zatwierdzisz rozszerzenia kernel podczas wdrażania/instalacji programu Microsoft Defender for Endpoint w systemie macOS, aplikacja wyświetli baner z monitem o włączenie tej funkcji:

   ![RTP disabled screenshot (Wyłączony rTP).](images/mdatp-32-main-app-fix.png)

Możesz również uruchomić .```mdatp health``` Raportuje on, czy jest włączona ochrona w czasie rzeczywistym, ale nie jest dostępna. Oznacza to, że rozszerzenie kernelu nie jest zatwierdzone do uruchomienia na urządzeniu.

```bash
mdatp health
```
```Output
...
real_time_protection_enabled                : false
real_time_protection_available              : true
...
```

Poniższe sekcje zawierają wskazówki dotyczące sposobu rozwiązania tego problemu w zależności od metody użytej do wdrożenia programu Microsoft Defender for Endpoint w systemie macOS.

## <a name="managed-deployment"></a>Wdrożenie zarządzane

Zobacz instrukcje odpowiadające narzędziu do zarządzania użytego do wdrożenia produktu:

- [Wdrażanie oparte na programie JAMF](mac-install-with-jamf.md)
- [Microsoft Intune oparte na programie](mac-install-with-intune.md#create-system-configuration-profiles)

## <a name="manual-deployment"></a>Wdrażanie ręczne

Jeśli od zainstalowania produktu minęło mniej niż 30 minut,  \> przejdź do tematu Preferencje systemowe Security **& Privacy** (Preferencje systemowe) i przejdź  do tematu Zezwalaj na oprogramowanie systemowe od deweloperów "Microsoft Corporation".

Jeśli nie widzisz tego monitu, oznacza to, że minęło co najmniej 30 minut, a rozszerzenie kernel nadal nie zostało zatwierdzone do uruchomienia na urządzeniu:

![Okno Zabezpieczeń i prywatności po wyświetleniu monitu o wygaśnięcie zrzutu ekranu.](images/mdatp-33-securityprivacysettings-noprompt.png)

W takim przypadku należy wykonać poniższe czynności, aby ponownie uruchomić przepływ zatwierdzania.

1. W programie Terminal spróbuj zainstalować sterownik. Następująca operacja nie powiedzie się, ponieważ rozszerzenie kernel nie zostało zatwierdzone do uruchomienia na urządzeniu. Wyzwoli jednak ponownie przepływ zatwierdzania.

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    ```Output
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Diagnostics for /Library/Extensions/wdavkext.kext:
    ```

2. Otwórz **menu Zabezpieczenia** \> **i & Preferencje** systemowe. (Zamknij go najpierw, jeśli jest otwarty).

3. **Zezwalaj** na oprogramowanie systemowe od deweloperów "Microsoft Corporation"

4. W programie Terminal zainstaluj ponownie sterownik. Tym razem operacja zakończy się powodzeniem:

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    Transparent powinien zniknąć z aplikacji Defender i powinien teraz oznaczać, ```mdatp health``` że ochrona w czasie rzeczywistym jest włączona i dostępna:

    ```bash
    mdatp health
    ```

    ```Output
    ...
    real_time_protection_enabled                : true
    real_time_protection_available              : true
    ...
    ```
