---
title: Rozwiązywanie problemów z odpowiedziami na żywo w programie Microsoft Defender for Endpoint
description: Rozwiązywanie problemów, które mogą wystąpić podczas korzystania z funkcji odpowiedzi na żywo w programie Microsoft Defender for Endpoint
keywords: rozwiązywanie problemów z odpowiedzią na żywo, na żywo, odpowiedzią, zablokowaniem, plikiem
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 4a3bab27a4e2efd6b196167754303f35d5553de6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997827"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-live-response-issues"></a>Rozwiązywanie problemów z odpowiedziami na żywo w programie Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Ta strona zawiera szczegółowe kroki rozwiązywania problemów z odpowiedziami na żywo.

## <a name="file-cannot-be-accessed-during-live-response-sessions"></a>Podczas sesji odpowiedzi na żywo nie można uzyskać dostępu do pliku

Jeśli podczas próby podjęcia działania w sesji odpowiedzi na żywo występuje komunikat o błędzie informujący, że nie można uzyskać dostępu do pliku, musisz wykonać poniższe czynności, aby rozwiązać ten problem.

1. Skopiuj poniższy fragment kodu skryptu i zapisz go jako plik PS1:

    ```powershell
    $copied_file_path=$args[0]
    $action=Copy-Item $copied_file_path -Destination $env:TEMP -PassThru -ErrorAction silentlyContinue

    if ($action){
         Write-Host "You copied the file specified in $copied_file_path to $env:TEMP Succesfully"
    }

    else{
        Write-Output "Error occoured while trying to copy a file, details:"
        Write-Output  $error[0].exception.message

    }
    ```

2. Dodaj skrypt do biblioteki odpowiedzi na żywo.
3. Uruchom skrypt z jednym parametrem: ścieżką pliku do skopiowania.
4. Przejdź do folderu TEMP.
5. Uruchom akcję, którą chcesz podjąć na skopiowanym pliku.

## <a name="slow-live-response-sessions-or-delays-during-initial-connections"></a>Wolne sesje odpowiedzi na żywo lub opóźnienia podczas początkowych połączeń

W odpowiedzi na żywo usługa Defender korzysta z zarejestrowania czujnika punktu końcowego w usłudze WNS w sieci Windows. Jeśli masz problemy z łącznością w odpowiedzi na żywo, potwierdź następujące szczegóły:

1. `notify.windows.com` nie jest blokowane w Twoim środowisku. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień serwera proxy urządzenia i łączności internetowej](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).
2. Usługa WpnService (Windows systemu powiadomień wypychanych) nie jest wyłączona.

Zapoznaj się z poniższymi artykułami, aby w pełni poznać wymagania i zachowania usługi WpnService:

- [Omówienie Windows usług powiadomień wypychanych (WNS)](/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)
- [Enterprise zapory sieciowej i serwera proxy do obsługi ruchu WNS](/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)
- [Zakresy publicznych adresów IP usługi powiadomień wypychanych (MPNS) firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=44535)
