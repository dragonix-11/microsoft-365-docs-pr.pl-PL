---
title: Uruchom test wykrywania na urządzeniu, aby sprawdzić, czy zostało ono poprawnie zainstalowane w programie Microsoft Defender for Endpoint
description: Uruchom skrypt testu wykrywania na urządzeniu ostatnio podłączonym do usługi Microsoft Defender for Endpoint, aby sprawdzić, czy zostało ono poprawnie dodane.
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
ms.openlocfilehash: 41ba14fd2e4a9e3726e4ef4287812cf8d3ffb2d1
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011931"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>Uruchamianie testu wykrywania na nowo w urządzeniu z uruchomionym programem Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- Windows 11
- Obsługiwane Windows 10 wersji
- Windows Server 2012 R2
- System Windows Server 2016
- Windows Server, wersja 1803
- Windows Server 2019
- Windows Server 2022
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dodanie urządzenia do usługi Microsoft Defender for Endpoint w celu zarządzania jest również nazywane urządzeniami dołączania. Wnoszenie umożliwia urządzeniam zgłaszanie sygnałów o ich stanie kondycji do usługi.

Sprawdzenie, czy urządzenie zostało pomyślnie dodane do usługi, jest kluczowym etapem całego procesu wdrażania. Zapewnia, że wszystkie oczekiwane urządzenia są zarządzane. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>Weryfikowanie programu Microsoft Defender pod celu do wykrycia punktu końcowego urządzenia przy użyciu testu wykrywania programu PowerShell

Uruchom następujący skrypt programu PowerShell na nowo zainstalowanym urządzeniu, aby sprawdzić, czy urządzenie prawidłowo zgłasza się do usługi Defender for Endpoint.

1. Utwórz folder: "C:\test-MDATP-test".
2. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu i uruchom skrypt:

   1. Przejdź do **przycisku Start** i wpisz **cmd**.

   1. Kliknij prawym przyciskiem **myszy pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

      ![Okno menu Start z punktem Uruchom jako administrator.](images/run-as-admin.png)

3. Po wyświetleniu monitu skopiuj i uruchom następujące polecenie:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Okno Wiersz polecenia zostanie zamknięte automatycznie. Jeśli efekt się powiedzie, w ciągu około dziesięciu minut w portalu pojawi się nowy alert dla urządzenia.

## <a name="related-topics"></a>Tematy pokrewne

- [Urządzenia Windows urządzeniach](configure-endpoints.md)
- [Serwery wsadowe](configure-server-endpoints.md)
- [Rozwiązywanie problemów z dołączaniem do programu Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
