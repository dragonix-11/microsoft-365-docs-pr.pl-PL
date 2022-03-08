---
title: Rozwiązywanie problemów z łącznością z chmurą dla programu Microsoft Defender dla punktu końcowego w systemie macOS
description: W tym temacie opisano, jak rozwiązywać problemy z łącznością w chmurze dla programu Microsoft Defender dla punktu końcowego w systemie macOS
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 677737f530e35ed52a2a1f3fe7a8d6f18c26e7b6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326570"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Rozwiązywanie problemów z łącznością z chmurą dla programu Microsoft Defender dla punktu końcowego w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platforma** dla systemu macOS

W tym temacie opisano, jak rozwiązywać problemy z łącznością w chmurze dla programu Microsoft Defender dla punktu końcowego w systemie macOS.

## <a name="run-the-connectivity-test"></a>Uruchom test łączności
Aby sprawdzić, czy program Defender dla punktu końcowego na komputerze Mac może komunikować się z chmurą przy użyciu bieżących ustawień sieci, uruchom test łączności z wiersza polecenia:

```Bash
mdatp connectivity test
```

oczekiwany wynik:
```Bash
Testing connection with https://cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://eu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://wu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://x.cp.wd.microsoft.com/api/report ... [OK]
Testing connection with https://winatp-gw-cus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-eus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-weu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-neu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-ukw.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-uks.microsoft.com/test ... [OK]
Testing connection with https://eu-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://us-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://uk-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://v20.events.data.microsoft.com/ping ... [OK]
```

Jeśli test łączności nie powiedzie się, sprawdź, czy urządzenie ma dostęp do Internetu [](microsoft-defender-endpoint-mac.md#network-connections) i czy któryś z punktów końcowych wymaganych przez produkt jest zablokowany przez serwer proxy lub zaporę.

Błędy z błędem zwijania 35 lub 60 oznaczają odrzucenia przypinania certyfikatów, co wskazuje potencjalny problem ze inspekcją SSL lub HTTPS. Zobacz poniższe instrukcje dotyczące konfiguracji inspekcji SSL.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-proxy-autoconfig-pac-or-with-web-proxy-autodiscovery-protocol-wpad"></a>Rozwiązywanie problemów ze środowiskami bez serwera proxy lub za pomocą automatycznego konfigurowania serwera proxy (PAC) lub z protokołem WPAD (Web Proxy Autodiscovery Protocol)
Skorzystaj z poniższej procedury, aby sprawdzić, czy połączenie nie jest zablokowane w środowisku bez serwera proxy, za pomocą automatycznego konfiguracji serwera proxy (PAC) lub z protokołem WPAD (Web Proxy Autodiscovery Protocol).

Jeśli ruch anonimowy jest blokowany przez serwer proxy lub zaporę, upewnij się, że ruch anonimowy jest dozwolony we wcześniej wymienionych adresach URL.

> [!WARNING]
> Uwierzytelnione proxy nie są obsługiwane. Upewnij się, że używany jest tylko PAC, WPAD lub statyczny serwer proxy. Inspekcja SSL i przechwytywanie serwerów proxy nie są również obsługiwane ze względów bezpieczeństwa. Skonfiguruj wyjątek dla inspekcji SSL i serwera proxy, aby bezpośrednio przekazać dane z programu Microsoft Defender dla punktu końcowego w systemie macOS do odpowiednich adresów URL bez przecięcia. Dodanie certyfikatu odcięcia do magazynu globalnego nie umożliwi przecięcia.
Aby sprawdzić, czy połączenie nie jest zablokowane: W przeglądarce, takiej jak program Microsoft Edge dla komputerów Mac lub Safari, otwórz https://x.cp.wd.microsoft.com/api/report oraz https://cdn.x.cp.wd.microsoft.com/ping.

Opcjonalnie w programie Terminal uruchom następujące polecenie:

```Bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping' 
```

Dane wyjściowe tego polecenia powinny być podobne do:
```bash
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```
