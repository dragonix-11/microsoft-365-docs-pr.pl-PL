---
title: Rozwiązywanie problemów z programem Microsoft Defender for Endpoint w systemie Linux R ENDPOINT6
ms.reviewer: ''
description: Rozwiązywanie problemów z łącznością z chmurą dla programu Microsoft Defender dla punktu końcowego w systemie Linux
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, cloud, connectivity, communication
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 43a60d12883dc639c4ee5b831d305010cef58533
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997772"
---
# <a name="troubleshoot-issues-for-microsoft-defender-for-endpoint-on-linux-rhel6"></a>Rozwiązywanie problemów z programem Microsoft Defender for Endpoint w systemie Linux R ENDPOINT6

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Ten artykuł zawiera wskazówki dotyczące rozwiązywania problemów z programem Microsoft Defender dla systemu Linux w systemie Red Hat Linux 6 (R 6) lub wyższym. 

Po zainstalowaniu pakietu (mdatp_XXX.XX.XX.x86_64.rpm) należy podjąć działania w celu sprawdzenia, czy instalacja powiodła się. 


## <a name="check-the-service-health"></a>Sprawdzanie kondycji usługi

Aby sprawdzić kondycję usługi, użyj następującego polecenia:

```bash
mdatp health 
```

## <a name="verify-that-the-service-is-running"></a>Sprawdzanie, czy usługa jest uruchomiona

Aby sprawdzić, czy usługa jest uruchomiona, użyj następującego polecenia:

```bash
service mdatp status 
```

Oczekiwane dane wyjściowe: `mdatp start/running, process 4517`

## <a name="verify-the-distribution-and-kernel-version"></a>Sprawdzanie wersji rozkładu i kernelu
Wersje rozkładu i kernela powinny się znaleźć na liście obsługiwanych.

Użyj następującego polecenia, aby pobrać wersję dystrybucyjną:

```bash
cat /etc/redhat-release (or /etc/system-release) 
```

Użyj następującego polecenia, aby pobrać wersję kernelu:

```bash
uname -r
```
## <a name="check-if-mdatp-audisp-process-is-running"></a>Sprawdzanie, czy proces mdatp jeśli nie jest uruchomiony 
Oczekiwanym wynikami jest to, że proces jest uruchomiony.

Aby to sprawdzić, użyj następującego polecenia:

```bash
pidof mdatp_audisp_plugin 
```

## <a name="check-talpa-modules"></a>Sprawdzanie modułów TALPA
Powinno być załadowanych dziewięć modułów. 

Aby to sprawdzić, użyj następującego polecenia:

```bash
lsmod | grep talpa
```

Oczekiwane dane wyjściowe: Włączone

```bash
talpa_pedconnector       878  0 

talpa_pedevice          5189  2 talpa_pedconnector 

talpa_vfshook          32300  1 

talpa_vcdevice          4947  1 

talpa_syscall           9127  0 

talpa_core             90699  4 talpa_vfshook,talpa_vcdevice,talpa_syscall 

talpa_linux            29424  5 talpa_vfshook,talpa_vcdevice,talpa_syscall,talpa_core 

talpa_syscallhookprobe      882  0 

talpa_syscallhook      14987  2 talpa_vfshook,talpa_syscallhookprobe 
```


```bash
lsmod | grep talpa | wc -l 
```

Oczekiwany wynik: 9

## <a name="check-talpa-status"></a>Sprawdzanie stanu TALPA

```bash
cat /proc/sys/talpa/interceptors/VFSHookInterceptor/status 
```

Debugowanie plików dziennika (oprócz pakietu "utwórz diagnostyczne mdatp") 

```bash
/var/log/audit/audit.log 

/var/log/messages 

semanage fcontext -l > selinux.log 
```
 

Wydajność i pamięć 

```bash
top -p <wdavdaemon pid>      

pmap -x <wdavdaemon pid> 
```

Gdzie `<wdavdaemon pid>` można znaleźć za pomocą `pidof wdavdaemon`.

