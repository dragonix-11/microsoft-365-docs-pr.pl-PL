---
title: Jak zaplanować aktualizację programu Microsoft Defender dla punktu końcowego (Linux)
description: Dowiedz się, jak zaplanować aktualizację programu Microsoft Defender dla punktu końcowego (Linux), aby lepiej chronić zasoby organizacji.
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
ms.openlocfilehash: f78f5e78067b3d8273d0ca9a3c7474eef66ed4fb
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996294"
---
# <a name="schedule-an-update-of-the-microsoft-defender-for-endpoint-linux"></a>Planowanie aktualizacji programu Microsoft Defender dla punktu końcowego (Linux)

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Aby uruchomić aktualizację programu Microsoft Defender dla punktu końcowego w systemie Linux, zobacz Wdrażanie aktualizacji programu [Microsoft Defender dla punktu końcowego w systemie Linux](/microsoft-365/security/defender-endpoint/linux-updates).

Linux (i Unix) ma narzędzie o **nazwie crontab** (podobne do Task Scheduler), które umożliwia uruchamianie zaplanowanych zadań.

## <a name="pre-requisite"></a>Wymagania wstępne

> [!NOTE]
> Aby uzyskać listę wszystkich stref czasowych, uruchom następujące polecenie: `timedatectl list-timezones`
>
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
sudo crontab -l > /var/tmp/cron_backup_201118.dat
```

> [!NOTE]
> Gdzie 201118 == RRMMDD

> [!TIP]
> Zrób to przed edytowaniem lub usuwaniem.

Aby edytować kartę crontab i dodać nowe zadanie jako użytkownika głównego:

```bash
sudo crontab -e
```

> [!NOTE]
> Edytor domyślny to VIM.

Mogą zostać wyświetlony:

```output
0****/etc/opt/microsoft/mdatp/logrorate.sh
```

Oraz

```output
02**sat /bin/mdatp scan quick>~/mdatp_cron_job.log
```

Zobacz [Planowanie skanów za pomocą programu Microsoft Defender dla punktu końcowego (Linux)](linux-schedule-scan-mde.md)

Naciśnij klawisz "Wstaw"

Dodaj następujące wpisy:

```bash
CRON_TZ=America/Los_Angeles
```

> #<a name="rhel-and-variants-centos-and-oracle-linux"></a>! R ZAO PRZYC i warianty (CentOS i Oracle Linux)
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo yum update mdatp >> ~/mdatp_cron_job.log
> ```

> #<a name="sles-and-variants"></a>! SLES i warianty
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo zypper update mdatp >> ~/mdatp_cron_job.log
> ```

> #<a name="ubuntu-and-debian-systems"></a>! Systemy Ubuntu i Debian
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo apt-get install --only-upgrade mdatp >> ~/mdatp_cron_job.log
> ```

> [!NOTE]
> W powyższych przykładach ustawiamy ją na 00 minut, 6 godzin (godzina w formacie 24-godzinnym), każdy dzień miesiąca, dowolny miesiąc, w niedziele. [$(data +\%d) -le 15] == Nie będzie działać, chyba że jest równe lub mniejsze niż 15 dzień (3. tydzień). Oznacza to, że będzie uruchamiany co 3. niedzielę (7) miesiąca o godzinie 6:00. Pacyfik (UTC -8).

Naciśnij klawisz Esc.

Wpisz cudzysłowy`:wq` podwójne "".

> [!NOTE]
> w == write, q == quit

Aby wyświetlić zadania zron, wpisz `sudo crontab -l`

:::image type="content" source="images/update-MDE-linux-4634577.jpg" alt-text="zaktualizuj program Defender dla punktu końcowego w systemie Linux.":::

Aby sprawdzić, czy zadanie cron jest uruchamiane:

```bash
sudo grep mdatp /var/log/cron
```

Aby sprawdzić plik mdatp_cron_job.log

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Dla osób, które używają ansible, Kucha i Chłoń

Użyj następujących poleceń:

### <a name="to-set-cron-jobs-in-ansible"></a>Aby ustawić zadania w języku Ansible

```bash
cron - Manage cron.d and crontab entries
```

Zobacz <https://docs.ansible.com/ansible/latest/modules/cron_module.html> , aby uzyskać więcej informacji.

### <a name="to-set-crontabs-in-chef"></a>Aby ustawić krzyżyki w Cycero

```bash
cron resource
```

Zobacz <https://docs.chef.io/resources/cron/> , aby uzyskać więcej informacji.

### <a name="to-set-cron-jobs-in-puppet"></a>Aby ustawić zadania cron w ciesie

Typ zasobu: cron

Zobacz <https://puppet.com/docs/puppet/5.5/types/cron.html> , aby uzyskać więcej informacji.

Automatyzowanie za pomocą pochłoń: zadania cron i zaplanowane zadania

Zobacz <https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/> , aby uzyskać więcej informacji.

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

<pre>
+—————- minute (values: 0 - 59) (special characters: , - * /)  <br>
| +————- hour (values: 0 - 23) (special characters: , - * /) <br>
| | +———- day of month (values: 1 - 31) (special characters: , - * / L W C)  <br>
| | | +——- month (values: 1 - 12) (special characters: ,- * / )  <br>
| | | | +—- day of week (values: 0 - 6) (Sunday=0 or 7) (special characters: , - * / L W C) <br>
| | | | |*****command to be executed
</pre>
