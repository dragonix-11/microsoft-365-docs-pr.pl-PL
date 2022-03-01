---
title: Rozwiązywanie problemów z brakującymi zdarzeniami lub alertami dla programu Microsoft Defender dla punktu końcowego w systemie Linux
description: Rozwiązywanie problemów z brakującymi zdarzeniami lub alertami w programie Microsoft Defender for Endpoint w systemie Linux.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, events
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5a17f94e3d26c08c0f6e0ca358778a65189cf6a5
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011377"
---
# <a name="troubleshoot-missing-events-or-alerts-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Rozwiązywanie problemów z brakującymi zdarzeniami lub alertami dla programu Microsoft Defender dla punktu końcowego w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ten artykuł zawiera ogólne instrukcje dotyczące ograniczania brakujących zdarzeń lub alertów w Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalie informacyjnym</a>.

Po **prawidłowym zainstalowaniu programu Microsoft Defender for Endpoint** na urządzeniu w portalu  zostanie wygenerowana strona urządzenia. Możesz przejrzeć wszystkie zarejestrowane zdarzenia na karcie osi czasu na stronie urządzenia lub na stronie zaawansowanego wyszukiwania. Ta sekcja pozwala rozwiązać problem braku niektórych lub wszystkich oczekiwanych zdarzeń.
Jeśli na przykład brakuje _wszystkich zdarzeń CreatedFile_ .

## <a name="missing-network-and-login-events"></a>Brakujące zdarzenia logowania i sieci

Program Microsoft Defender for Endpoint używał `audit` struktury z systemu Linux do śledzenia aktywności sieciowej i logowania.

1. Upewnij się, że działają struktury inspekcji.

    ```bash
    service auditd status
    ```

    oczekiwany wynik:

    ```output
    ● auditd.service - Security Auditing Service
    Loaded: loaded (/usr/lib/systemd/system/auditd.service; enabled; vendor preset: enabled)
    Active: active (running) since Mon 2020-12-21 10:48:02 IST; 2 weeks 0 days ago
        Docs: man:auditd(8)
            https://github.com/linux-audit/audit-documentation
    Process: 16689 ExecStartPost=/sbin/augenrules --load (code=exited, status=1/FAILURE)
    Process: 16665 ExecStart=/sbin/auditd (code=exited, status=0/SUCCESS)
    Main PID: 16666 (auditd)
        Tasks: 25
    CGroup: /system.slice/auditd.service
            ├─16666 /sbin/auditd
            ├─16668 /sbin/audispd
            ├─16670 /usr/sbin/sedispatch
            └─16671 /opt/microsoft/mdatp/sbin/mdatp_audisp_plugin -d
    ```

2. Jeśli `auditd` przycisk jest oznaczany jako zatrzymany, uruchom go.

    ```bash
    service auditd start
    ```

**W systemach SLES** inspekcja syscall w może `auditd` być domyślnie wyłączona i może zostać uwzględnić brakujące zdarzenia.

1. Aby sprawdzić, czy inspekcja syscall nie jest wyłączona, należy wyświetlić bieżące reguły inspekcji:

    ```bash
    sudo auditctl -l
    ```

    jeśli występuje poniższy wiersz, usuń go lub edytuj, aby umożliwić programowi Microsoft Defender for Endpoint śledzenie określonych adresów SYSCALLs.

    ```output
    -a task, never
    ```

    reguły inspekcji znajdują się w .`/etc/audit/rules.d/audit.rules`

## <a name="missing-file-events"></a>Brakujące zdarzenia pliku

Zdarzenia dotyczące plików są zbierane przy użyciu struktury `fanotify` . Jeśli brakuje niektórych lub wszystkich zdarzeń pliku, upewnij się, `fanotify` że na urządzeniu jest włączona i że system plików jest [obsługiwany](microsoft-defender-endpoint-linux.md#system-requirements).

System plików na komputerze można wyświetlić w:

```bash
df -Th
```
