---
title: Jak zaplanować skany za pomocą programu Microsoft Defender dla punktu końcowego (Linux)
description: Dowiedz się, jak zaplanować automatyczny czas skanowania dla programu Microsoft Defender for Endpoint (Linux), aby lepiej chronić zasoby organizacji.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, scans, antivirus, microsoft defender for endpoint (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ddb02d67866e675febda59fac15e8e494188a47f
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996295"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>Planowanie skanów za pomocą programu Microsoft Defender dla punktu końcowego (Linux)

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Aby uruchomić skanowanie systemu Linux, zobacz [Obsługiwane polecenia](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).

Linux (i Unix) ma narzędzie o **nazwie crontab** (podobne do Task Scheduler), które umożliwia uruchamianie zaplanowanych zadań.

## <a name="pre-requisite"></a>Wymagania wstępne

> [!NOTE]
> Aby uzyskać listę wszystkich stref czasowych, uruchom następujące polecenie: `timedatectl list-timezones`<br>
> Przykłady stref czasowych:
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Aby ustawić zadanie cron

Użyj następujących poleceń:

### <a name="backup-crontab-entries"></a>Kopie zapasowe wpisów crontab

```bash
sudo crontab -l > /var/tmp/cron_backup_200919.dat
```

> [!NOTE]
> Gdzie 200919 ==MMDD RRMMDD

> [!TIP]
> Zrób to przed edytowaniem lub usuwaniem.

Aby edytować kartę crontab i dodać nowe zadanie jako użytkownika głównego:

```bash
sudo crontab -e
```

> [!NOTE]
> Edytor domyślny to VIM.

Mogą zostać wyświetlony:

```outbou
0 * * * * /etc/opt/microsoft/mdatp/logrorate.sh
```

Naciśnij klawisz "Wstaw"

Dodaj następujące wpisy:

```bash
CRON_TZ=America/Los_Angeles

0 2 * * sat /bin/mdatp scan quick > ~/mdatp_cron_job.log
```

> [!NOTE]
> W tym przykładzie ustawiono ją na 00 minut przed godziną 2:00. (godzina w formacie 24-godzinnym), każdy dzień miesiąca, dowolny miesiąc, w soboty. Oznacza to, że będzie uruchamiać soboty o godzinie 2:00. Pacyfik (UTC -8).

Naciśnij klawisz Esc.

Wpisz "`:wq`" bez cudzysłowów podwójnych.

> [!NOTE]
> w == write, q == quit

Aby wyświetlić zadania zron, wpisz `sudo crontab -l`

:::image type="content" source="../../media/linux-mdatp-1.png" alt-text="linux mdatp.":::

#### <a name="to-inspect-cron-job-runs"></a>Aby sprawdzić, czy zadanie cron jest uruchamiane

```bash
sudo grep mdatp /var/log/cron
```

#### <a name="to-inspect-the-mdatp_cron_joblog"></a>Aby sprawdzić plik mdatp_cron_job.log*

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Dla osób, które używają ansible, Kucha i Chłoń

Użyj następujących poleceń:

### <a name="to-set-cron-jobs-in-ansible"></a>Aby ustawić zadania w języku Ansible

```bash
cron - Manage cron.d and crontab entries

See [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html) for more information.

### To set crontabs in Chef

```bash
cron resource
```bash

```
Zobacz <https://docs.chef.io/resources/cron/> , aby uzyskać więcej informacji.

### <a name="to-set-cron-jobs-in-puppet"></a>Aby ustawić zadania cron w ciesie

```bash
Resource Type: cron
```

Zobacz <https://puppet.com/docs/puppet/5.5/types/cron.html> , aby uzyskać więcej informacji.

Automatyzowanie za pomocą pochłoń: zadania cron i zaplanowane zadania

Zobacz [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/) , aby uzyskać więcej informacji.

## <a name="additional-information"></a>Informacje dodatkowe

### <a name="to-get-help-with-crontab"></a>Aby uzyskać pomoc na karcie crontab

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>Aby uzyskać listę plików crontab bieżącego użytkownika

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>Aby uzyskać listę plików crontab innego użytkownika

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>Aby utworzyć kopię zapasową wpisów crontab

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> Zrób to przed edytowaniem lub usuwaniem.

### <a name="to-restore-crontab-entries"></a>Aby przywrócić wpisy crontab

```bash
crontab /var/tmp/cron_backup.dat
```

### <a name="to-edit-the-crontab-and-add-a-new-job-as-a-root-user"></a>Aby edytować kartę crontab i dodać nowe zadanie jako użytkownika głównego

```bash
sudo crontab -e
```

### <a name="to-edit-the-crontab-and-add-a-new-job"></a>Aby edytować kartę zadań i dodać nowe zadanie

```bash
crontab -e
```

### <a name="to-edit-other-users-crontab-entries"></a>Aby edytować wpisy crontab innego użytkownika

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>Aby usunąć wszystkie wpisy crontab

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>Aby usunąć wpisy crontab innego użytkownika

```bash
crontab -u username -r
```

### <a name="explanation"></a>Objaśnienie

+—————- minut (wartości: 0 – 59) (znaki specjalne: , - * /)  <br>
| +————- godziny (wartości: 0 – 23) (znaki specjalne: , - * /) <br>
| | +———- dnia miesiąca (wartości: 1 – 31) (znaki specjalne: , - * / L W C)  <br>
| | | +——- miesiąc (wartości: 1 – 12) (znaki specjalne: ,- * / )  <br>
| | | | + — dzień tygodnia (wartości: 0 - 6) (niedziela=0 lub 7) (znaki specjalne: , - * / L W C) <br>
| | | | |*****, które ma zostać wykonane
