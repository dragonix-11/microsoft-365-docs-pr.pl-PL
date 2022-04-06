---
title: Uruchom test wykrywania na urządzeniu, aby sprawdzić, czy zostało ono poprawnie Ochrona punktu końcowego w usłudze Microsoft Defender
description: Uruchom skrypt testu wykrywania na urządzeniu ostatnio podłączonym do usługi Ochrona punktu końcowego w usłudze Microsoft Defender, aby sprawdzić, czy zostało ono poprawnie dodane.
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1d8459633d00d759fda1584e0084cd8ed4e12633
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477264"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>Uruchamianie testu wykrywania na nowo włodowym Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- Windows 11
- Obsługiwane Windows 10 wersji
- Windows Server 2012 R2
- System Windows Server 2016
- Windows Server, wersja 1803
- Windows Server 2019
- Windows Server 2022
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Po dodaniu urządzenia do usługi Ochrona punktu końcowego w usłudze Microsoft Defender do zarządzania jest to również nazywane urządzeniami dołączania. Wnoszenie umożliwia urządzeniam zgłaszanie sygnałów o ich stanie kondycji do usługi.

Sprawdzenie, czy urządzenie zostało pomyślnie dodane do usługi, jest kluczowym etapem całego procesu wdrażania. Zapewnia, że wszystkie oczekiwane urządzenia są zarządzane. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>Weryfikowanie Ochrona punktu końcowego w usłudze Microsoft Defender dołączania urządzenia przy użyciu testu wykrywania programu PowerShell

Uruchom następujący skrypt programu PowerShell na nowo zainstalowanym urządzeniu, aby sprawdzić, czy urządzenie prawidłowo zgłasza się do usługi Defender for Endpoint.

1. Utwórz folder: "C:\test-MDATP-test".
2. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu i uruchom skrypt:

   1. Przejdź do **przycisku Start** i wpisz **cmd**.

   1. Kliknij prawym przyciskiem **myszy pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

      :::image type="content" source="images/run-as-admin.png" alt-text="The menu Start pointing to Run as administrator" lightbox="images/run-as-admin.png":::
    
3. Po wyświetleniu monitu skopiuj i uruchom następujące polecenie:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Okno Wiersz polecenia zostanie zamknięte automatycznie. Jeśli efekt się powiedzie, w ciągu około dziesięciu minut w portalu pojawi się nowy alert dla urządzenia.

## <a name="related-topics"></a>Tematy pokrewne

- [Urządzenia Windows urządzeniach](configure-endpoints.md)
- [Serwery wsadowe](configure-server-endpoints.md)
- [Rozwiązywanie Ochrona punktu końcowego w usłudze Microsoft Defender problemów z dołączaniem](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
