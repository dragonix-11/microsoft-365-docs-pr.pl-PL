---
title: Rozwiązywanie problemów z łącznością z chmurą dla programu Microsoft Defender dla punktu końcowego w systemie Linux
ms.reviewer: ''
description: Dowiedz się, jak rozwiązywać problemy z łącznością w chmurze dla programu Microsoft Defender dla punktu końcowego w systemie Linux
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, cloud, connectivity, communication
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
ms.openlocfilehash: a4c279dff6fa5a5c85a2f65144a301dde75a1615
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997231"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Rozwiązywanie problemów z łącznością z chmurą dla programu Microsoft Defender dla punktu końcowego w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="run-the-connectivity-test"></a>Uruchom test łączności

Aby sprawdzić, czy program Defender for Endpoint w systemie Linux może komunikować się z chmurą przy użyciu bieżących ustawień sieci, uruchom test łączności z wiersza polecenia:

```bash
mdatp connectivity test
```

oczekiwany wynik:

```output
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

Jeśli test łączności nie powiedzie się, sprawdź, czy urządzenie ma dostęp do Internetu [](microsoft-defender-endpoint-linux.md#network-connections) i czy któryś z punktów końcowych wymaganych przez produkt jest zablokowany przez serwer proxy lub zaporę.

Błędy z błędem zwijania 35 lub 60 wskazują odrzucenia przypinania certyfikatu. Sprawdź, czy połączenie jest w ramach inspekcji SSL lub HTTPS. Jeśli tak, dodaj usługę Microsoft Defender for Endpoint do listy zezwalań.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-transparent-proxy"></a>Procedura rozwiązywania problemów ze środowiskami bez serwera proxy lub z przezroczystym serwerem proxy

Aby sprawdzić, czy połączenie nie jest zablokowane w środowisku bez serwera proxy lub przezroczystego serwera proxy, uruchom następujące polecenie w terminalu:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Dane wyjściowe tego polecenia powinny być podobne do:

```Output
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```

## <a name="troubleshooting-steps-for-environments-with-static-proxy"></a>Procedura rozwiązywania problemów ze środowiskami ze statycznym serwerem proxy

> [!WARNING]
> Pac, WPAD i uwierzytelnione proxy nie są obsługiwane. Upewnij się, że używany jest tylko statyczny lub przezroczysty serwer proxy.
>
> Inspekcja SSL i przechwytywanie serwerów proxy nie są również obsługiwane ze względów bezpieczeństwa. Skonfiguruj wyjątek dla inspekcji SSL i serwera proxy w celu bezpośredniego przejścia danych z programu Defender for Endpoint w systemie Linux do odpowiednich adresów URL bez przecięcia. Dodanie certyfikatu odcięcia do magazynu globalnego nie umożliwi przecięcia.

Jeśli jest wymagany statyczny serwer proxy, dodaj parametr serwera proxy do powyższego polecenia, `proxy_address:port` gdzie odpowiada adresowi i portowi serwera proxy:

```bash
curl -x http://proxy_address:port -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Upewnij się, że używasz tego samego adresu i portu serwera proxy skonfigurowanego w `/lib/system/system/mdatp.service` pliku. Sprawdź konfigurację serwera proxy, jeśli występują błędy z powyższych poleceń.

Aby ustawić serwer proxy dla usługi mdatp, użyj następującego polecenia:

```bash
mdatp config proxy set --value http://address:port 
```


Po sukcesie spróbuj jeszcze jeden test łączności z wiersza polecenia:

```bash
mdatp connectivity test
```

Jeśli problem będzie nadal występował, skontaktuj się z działem obsługi klienta.

## <a name="resources"></a>Zasoby

- Aby uzyskać więcej informacji na temat konfigurowania produktu w celu używania statycznego serwera proxy, zobacz Konfigurowanie usługi [Microsoft Defender dla punktu końcowego statycznego odnajdowania serwera proxy](linux-static-proxy-configuration.md).
