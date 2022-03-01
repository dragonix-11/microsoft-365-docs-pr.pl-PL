---
title: Jak zaplanować skanowania za pomocą programu Microsoft Defender dla punktu końcowego w systemie macOS
description: Dowiedz się, jak zaplanować automatyczny czas skanowania dla programu Microsoft Defender for Endpoint w systemie macOS, aby lepiej chronić zasoby organizacji.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, skany, oprogramowanie antywirusowe
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
ms.openlocfilehash: 629db5fc343d100913d631f59a680fc9160713ed
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011369"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Planowanie skanowania za pomocą programu Microsoft Defender for Endpoint w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Mimo że za pomocą programu Microsoft Defender for Endpoint możesz w dowolnym momencie rozpocząć skanowanie przed zagrożeniami, twoje przedsiębiorstwo może korzystać z zaplanowanych lub zaplanowanych skanów w czasie. Można na przykład zaplanować uruchomienie skanowania na początku każdego dnia roboczego lub tygodnia. 

## <a name="schedule-a-scan-with-launchd"></a>Planowanie skanowania z *uruchomiony*

Możesz utworzyć harmonogram skanowania, używając *launchd* daemon na urządzeniu z systemem macOS.

Aby uzyskać więcej informacji na *temat użytego tutaj formatu pliku plist* , zobacz [Informacje o](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) plikach listy właściwości informacji w oficjalnej witrynie dewelopera firmy Apple.

### <a name="schedule-a-quick-scan"></a>Planowanie szybkiego skanowania

Poniższy kod przedstawia schemat, który jest potrzebny do zaplanowania szybkiego skanowania. 

1. Otwórz edytor tekstów i użyj tego przykładu jako przewodnika dla własnego zaplanowanego pliku skanowania.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedquickscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan quick</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>0</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Zapisz plik jako *com.microsoft.wdav.schedquickpage.plist*.

### <a name="schedule-a-full-scan"></a>Planowanie pełnego skanowania

1. Otwórz edytor tekstów i użyj tego przykładu do pełnego skanowania.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedfullscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan full</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>50</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Zapisz plik jako *com.microsoft.wdav.schedfullscan.plist*.
 
### <a name="load-your-file"></a>Ładowanie pliku

1. Otwórz **program Terminal**.
2. Wprowadź następujące polecenia, aby załadować plik:

    ```bash
    launchctl load /Library/LaunchDaemons/<your file name.plist>
    launchctl start <your file name>
    ```

3. Zaplanowane skanowanie zostanie uruchomione w dniu, godzinie i częstotliwości zdefiniowanej na liście p. W poprzednich przykładach skanowanie jest uruchamiane w każdy piątek o godzinie 2:50. 

    - Wartość `Weekday` argumentu używa `StartCalendarInterval` liczby całkowitej wskazującej piąty dzień tygodnia lub piątek. Ten zakres należy do przedziału od 0 do 7, a 7 oznacza niedzielę.
    - Wartość `Day` argumentu używa `StartCalendarInterval` liczby całkowitej do wskazania trzeciego dnia miesiąca. Zakres należy do przedziału od 1 do 31.
    - Wartość `Hour` argumentu używa `StartCalendarInterval` liczby całkowitej wskazującej drugą godzinę dnia. Zakres należy do przedziału od 0 do 24.
    Wartość `Minute` argumentu używa `StartCalendarInterval` liczby całkowitej do wskazania pięćdziesięciu minut godziny. Zakres należy do przedziału od 0 do 59.
    
    
 > [!IMPORTANT]
 > Agenty wykonane po *uruchomieniu* nie będą działać w zaplanowanym czasie, gdy urządzenie przesłoni. Będą one uruchamiane po wznowieniu działania urządzenia z trybu uśpienia.
 >
 > Jeśli urządzenie jest wyłączone, skanowanie zostanie uruchomione podczas następnego zaplanowanego czasu skanowania.

## <a name="schedule-a-scan-with-intune"></a>Planowanie skanowania za pomocą usługi Intune

Możesz również planować skanowania za pomocą Microsoft Intune. Skrypt [runMDATPQuickScan.sh](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP#runmdatpquickscansh) powłoki dostępny w skryptach dla programu [Microsoft Defender dla](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP) punktu końcowego będzie utrwalony, gdy urządzenie zostanie przywrócone z trybu uśpienia. 

Zobacz [Używanie skryptów powłoki na urządzeniach z systemem macOS w usłudze Intune](/mem/intune/apps/macos-shell-scripts) , aby uzyskać bardziej szczegółowe instrukcje dotyczące używania tego skryptu w przedsiębiorstwie.
