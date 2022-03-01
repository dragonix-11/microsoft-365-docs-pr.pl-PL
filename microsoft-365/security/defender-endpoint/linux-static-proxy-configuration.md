---
title: Microsoft Defender for Endpoint on Linux static proxy discovery
ms.reviewer: ''
description: W tym artykule opisano, jak skonfigurować program Microsoft Defender dla punktu końcowego w systemie Linux w celu statycznego odnajdowania serwera proxy.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, installation, proxy
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
ms.openlocfilehash: 3b5061f0230a9704cb0fb9b80752c4d38954ad12
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997387"
---
# <a name="configure-microsoft-defender-for-endpoint-on-linux-for-static-proxy-discovery"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego w systemie Linux w celu odnajdowania statycznego serwera proxy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Program Microsoft Defender for Endpoint może wykryć serwer proxy przy użyciu zmiennej `HTTPS_PROXY` środowiskowej. To ustawienie należy **skonfigurować zarówno podczas** instalacji, jak i po zainstalowaniu produktu.

## <a name="installation-time-configuration"></a>Konfiguracja czasu instalacji

Podczas instalacji należy podać zmienną `HTTPS_PROXY` środowiskową do menedżera pakietu. Menedżer pakietu może odczytywać tę zmienną w dowolny z następujących sposobów:

- Zmienna `HTTPS_PROXY` jest zdefiniowana za `/etc/environment` pomocą następującego wiersza:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

- Zmienna `HTTPS_PROXY` jest zdefiniowana w konfiguracji globalnej menedżera pakietu. Na przykład w systemie Ubuntu 18.04 możesz dodać następujący wiersz do `/etc/apt/apt.conf.d/proxy.conf`:

  ```bash
  Acquire::https::Proxy "http://proxy.server:port/";
  ```

  > [!CAUTION]
  > Pamiętaj, że powyższe dwie metody mogą zdefiniować serwer proxy do użycia dla innych aplikacji w systemie. Tej metody należy używać z rozwagą lub tylko wtedy, gdy ma to być ogólnie konfiguracja globalna.

- Zmienna `HTTPS_PROXY` jest przednia do poleceń instalacji lub dezinstalacji. Na przykład w menedżerze pakietów APT zmienną należy nazwać następującą podczas instalowania programu Microsoft Defender for Endpoint:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/" apt install mdatp
  ```

  > [!NOTE]
  > Nie dodawaj sudo między definicją zmiennej środowiskowej a m. W przeciwnym razie zmienna nie zostanie rozpropagowana.

Zmienna `HTTPS_PROXY` środowiskowa może być również zdefiniowana podczas dezinstalacji.

Pamiętaj, że instalacja i dezinstalacja nie mogą się nie powieść, jeśli serwer proxy jest wymagany, ale nie skonfigurowany. Nie zostaną jednak przesłane telemetria, a operacja może potrwać znacznie dłużej z powodu limitów czasu sieci.

## <a name="post-installation-configuration"></a>Konfiguracja po instalacji

Po zakończeniu instalacji zmienna `HTTPS_PROXY` środowiskowa musi zostać zdefiniowana w pliku usługi Defender for Endpoint. Aby to zrobić, uruchom .`sudo systemctl edit --full mdatp.service`
Następnie można propagować zmienną w usłudze na jeden z dwóch sposobów:

- Odłącz linię i określ `#Environment="HTTPS_PROXY=http://address:port"` statyczny adres proxy.

- Dodawanie wiersza `EnvironmentFile=/path/to/env/file`. Ta ścieżka może wskazać `/etc/environment` plik lub plik niestandardowy, z którego trzeba dodać następujący wiersz:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

Po zmodyfikowaniu `mdatp.service`zapisz plik i uruchom ponownie usługę, aby można było zastosować zmiany za pomocą następujących poleceń:

```bash
sudo systemctl daemon-reload; sudo systemctl restart mdatp
```
