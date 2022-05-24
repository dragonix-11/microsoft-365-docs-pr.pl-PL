---
title: Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie
ms.reviewer: ''
description: Opis sposobu instalowania i używania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 825605f932b3732ba27af7ec95160f34959356b0
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648332"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

W tym temacie opisano sposób instalowania, konfigurowania, aktualizowania i używania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux.

> [!CAUTION]
> Uruchamianie innych produktów ochrony punktów końcowych innych firm wraz z Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux może prowadzić do problemów z wydajnością i nieprzewidywalnych skutków ubocznych. Jeśli ochrona punktów końcowych innych niż Microsoft jest absolutnym wymaganiem w twoim środowisku, nadal możesz bezpiecznie korzystać z funkcji usługi Defender for Endpoint w systemie Linux EDR po skonfigurowaniu funkcji antywirusowej do uruchamiania w [trybie pasywnym](linux-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Jak zainstalować Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

Ochrona punktu końcowego w usłudze Microsoft Defender dla systemu Linux obejmuje funkcje ochrony przed złośliwym kodem i wykrywanie i reagowanie w punktach końcowych (EDR). 


### <a name="prerequisites"></a>Wymagania wstępne

- Dostęp do portalu Microsoft 365 Defender
- Dystrybucja systemu Linux przy użyciu [systemowego](https://systemd.io/) menedżera systemu

  >[!NOTE]
  >Dystrybucja systemu Linux przy użyciu menedżera systemu z wyjątkiem systemu RHEL/CentOS 6.x obsługuje zarówno systemV, jak i upstart.

- Środowisko dla początkujących w zakresie skryptów bash i systemu Linux
- Uprawnienia administracyjne na urządzeniu (w przypadku wdrożenia ręcznego)

> [!NOTE]
> Ochrona punktu końcowego w usłudze Microsoft Defender agent systemu Linux jest niezależny od [agenta pakietu OMS](/azure/azure-monitor/agents/agents-overview#log-analytics-agent). Ochrona punktu końcowego w usłudze Microsoft Defender opiera się na własnym niezależnym potoku telemetrii.


### <a name="installation-instructions"></a>Instrukcje instalacji

Istnieje kilka metod i narzędzi wdrażania, których można użyć do instalowania i konfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux.

Ogólnie rzecz biorąc, należy wykonać następujące kroki:

- Upewnij się, że masz subskrypcję Ochrona punktu końcowego w usłudze Microsoft Defender.
- Wdróż Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux przy użyciu jednej z następujących metod wdrażania:
  - Narzędzie wiersza polecenia:
    - [Wdrażanie ręczne](linux-install-manually.md)
  - Narzędzia do zarządzania innych firm:
    - [Wdrażanie przy użyciu narzędzia do zarządzania konfiguracją platformy Puppet](linux-install-with-puppet.md)
    - [Wdrażanie przy użyciu narzędzia do zarządzania konfiguracją rozwiązania Ansible](linux-install-with-ansible.md)
    - [Wdrażanie przy użyciu narzędzia do zarządzania konfiguracją programu Chef](linux-deploy-defender-for-endpoint-with-chef.md)

Jeśli wystąpią błędy instalacji, zapoznaj się [z tematem Rozwiązywanie problemów z błędami instalacji w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-support-install.md).

> [!NOTE]
> Instalowanie Ochrona punktu końcowego w usłudze Microsoft Defender nie jest obsługiwane w żadnej innej lokalizacji niż domyślna ścieżka instalacji. 

### <a name="system-requirements"></a>Wymagania systemowe

- Obsługiwane dystrybucje serwerów z systemem Linux i x64 (AMD64/EM64T) i wersje x86_64:

  - Red Hat Enterprise Linux 6.7 lub nowszy
  - Red Hat Enterprise Linux 7.2 lub nowszy
  - Red Hat Enterprise Linux 8.x
  - CentOS 6.7 lub nowszy 
  - CentOS 7.2 lub nowszy
  - Ubuntu 16.04 LTS lub nowszy LTS
  - Debian 9 lub nowszy
  - SUSE Linux Enterprise Server 12 lub nowszy
  - Oracle Linux 7.2 lub nowszy
  - Oracle Linux 8.x
  - Amazon Linux 2
  - Fedora 33 lub nowsza

    > [!NOTE]
    > Dystrybucje i wersja, które nie są jawnie wymienione, są nieobsługiwane (nawet jeśli pochodzą z oficjalnie obsługiwanych dystrybucji).

- Lista obsługiwanych wersji jądra
  - Minimalna wersja jądra 3.10.0-327 (dla wszystkich obsługiwanych dystrybucji systemu Linux wymienionych powyżej z wyjątkiem systemu Red Hat Enterprise Linux 6 i CentOS 6)
  - Opcja `fanotify` jądra musi być włączona
  - Red Hat Enterprise Linux 6 i CentOS 6:
    - Dla wersji 6.7: 2.6.32-573.*
    - Dla wersji 6.8: 2.6.32-642.*
    - Dla wersji 6.9: 2.6.32-696.* (z wyjątkiem 2.6.32-696.el6.x86_64)
    - W przypadku wersji 6.10: 2.6.32.754.2.1.el6.x86_64 do 2.6.32-754.43.1:
    
       - 2.6.32-754.10.1.el6.x86_64
       - 2.6.32-754.11.1.el6.x86_64
       - 2.6.32-754.12.1.el6.x86_64
       - 2.6.32-754.14.2.el6.x86_64
       - 2.6.32-754.15.3.el6.x86_64
       - 2.6.32-754.17.1.el6.x86_64
       - 2.6.32-754.18.2.el6.x86_64
       - 2.6.32-754.2.1.el6.x86_64
       - 2.6.32-754.22.1.el6.x86_64
       - 2.6.32-754.23.1.el6.x86_64
       - 2.6.32-754.24.2.el6.x86_64
       - 2.6.32-754.24.3.el6.x86_64
       - 2.6.32-754.25.1.el6.x86_64
       - 2.6.32-754.27.1.el6.x86_64
       - 2.6.32-754.28.1.el6.x86_64
       - 2.6.32-754.29.1.el6.x86_64
       - 2.6.32-754.29.2.el6.x86_64
       - 2.6.32-754.3.5.el6.x86_64
       - 2.6.32-754.30.2.el6.x86_64
       - 2.6.32-754.33.1.el6.x86_64
       - 2.6.32-754.35.1.el6.x86_64
       - 2.6.32-754.39.1.el6.x86_64
       - 2.6.32-754.41.2.el6.x86_64
       - 2.6.32-754.43.1.el6.x86_64
       - 2.6.32-754.47.1.el6.x86_64
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64

 > [!NOTE]
 > Po wydaniu nowej wersji pakietu obsługa dwóch poprzednich wersji jest ograniczona tylko do pomocy technicznej. Wersje starsze niż wymienione w tej sekcji są udostępniane tylko do obsługi uaktualnień technicznych.


  > [!CAUTION]
  > Uruchamianie usługi Defender for Endpoint w systemie Linux obok innych rozwiązań zabezpieczeń opartych na systemie `fanotify`nie jest obsługiwane. Może to prowadzić do nieprzewidywalnych wyników, w tym zawieszenia systemu operacyjnego.

- Miejsce na dysku: 1 GB

- /opt/microsoft/mdatp/sbin/wdavdaemon wymaga uprawnień wykonywalnych. Aby uzyskać więcej informacji, zobacz "Upewnij się, że demon ma uprawnienie do wykonywalnego" w [temacie Rozwiązywanie problemów z instalacją Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](/microsoft-365/security/defender-endpoint/linux-support-install).

- Rdzenie: 2 minimum, 4 preferowane

- Pamięć: minimum 1 GB, 4 preferowane

    > [!NOTE]
    > Upewnij się, że masz wolne miejsce na dysku w /var.

- Rozwiązanie zapewnia obecnie ochronę w czasie rzeczywistym dla następujących typów systemów plików:

  - `btrfs`
  - `ecryptfs`
  - `ext2`
  - `ext3`
  - `ext4`
  - `fuse`
  - `fuseblk`
  - `jfs`
  - `nfs`
  - `overlay`
  - `ramfs`
  - `reiserfs`
  - `tmpfs`
  - `udf`
  - `vfat`
  - `xfs`

Po włączeniu usługi może być konieczne skonfigurowanie sieci lub zapory w celu zezwolenia na połączenia wychodzące między nią a punktami końcowymi.

- Należy włączyć platformę inspekcji (`auditd`).

  > [!NOTE]
  > Zdarzenia systemowe przechwycone przez reguły dodane do `/etc/audit/rules.d/` zostaną dodane do `audit.log`elementów i mogą mieć wpływ na inspekcję hosta i zbieranie nadrzędne. Zdarzenia dodane przez Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux zostaną oznaczone kluczem`mdatp`.

### <a name="configuring-exclusions"></a>Konfigurowanie wykluczeń

Podczas dodawania wykluczeń do Program antywirusowy Microsoft Defender należy pamiętać o [typowych błędach wykluczania dla Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>Połączenia sieciowe

Poniższy arkusz kalkulacyjny do pobrania zawiera listę usług i skojarzonych z nimi adresów URL, z którymi sieć musi mieć możliwość nawiązania połączenia. Upewnij się, że nie ma reguł filtrowania zapory ani sieci, które odmawiałyby dostępu do tych adresów URL. Jeśli tak, może być konieczne utworzenie reguły *zezwalania* specjalnie dla nich.

<br>

****

|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów komercyjnych| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender gov/GCC/doD | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów Gov/GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

> [!NOTE]
> Aby uzyskać bardziej szczegółową listę adresów URL, zobacz [Konfigurowanie ustawień serwera proxy i łączności internetowej](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

Usługa Defender for Endpoint może odnajdywać serwer proxy przy użyciu następujących metod odnajdywania:

- Przezroczysty serwer proxy
- Ręczna konfiguracja statycznego serwera proxy

Jeśli serwer proxy lub zapora blokuje ruch anonimowy, upewnij się, że ruch anonimowy jest dozwolony we wcześniej wymienionych adresach URL. W przypadku przezroczystych serwerów proxy nie jest wymagana dodatkowa konfiguracja usługi Defender for Endpoint. W przypadku statycznego serwera proxy wykonaj kroki opisane w [temacie Ręczna konfiguracja statycznego serwera proxy](linux-static-proxy-configuration.md).

> [!WARNING]
> Serwery proxy PAC, WPAD i uwierzytelnione nie są obsługiwane. Upewnij się, że jest używany tylko statyczny serwer proxy lub przezroczysty serwer proxy.
>
> Inspekcja protokołu SSL i przechwytywanie serwerów proxy również nie są obsługiwane ze względów bezpieczeństwa. Skonfiguruj wyjątek inspekcji protokołu SSL i serwera proxy w celu bezpośredniego przekazywania danych z usługi Defender for Endpoint w systemie Linux do odpowiednich adresów URL bez przechwytywania. Dodanie certyfikatu przechwytywania do magazynu globalnego nie pozwoli na przechwycenie.

Aby uzyskać instrukcje rozwiązywania problemów, zobacz [Rozwiązywanie problemów z łącznością w chmurze dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Jak zaktualizować Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

Firma Microsoft regularnie publikuje aktualizacje oprogramowania w celu zwiększenia wydajności, bezpieczeństwa i dostarczania nowych funkcji. Aby zaktualizować Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux, zobacz [Wdrażanie aktualizacji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Konfigurowanie ochrony punktu końcowego w usłudze Microsoft Defender na Linuxie

Wskazówki dotyczące konfigurowania produktu w środowiskach przedsiębiorstwa są dostępne w [temacie Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>Typowe aplikacje do Ochrona punktu końcowego w usłudze Microsoft Defender mogą mieć wpływ

Wysokie obciążenia we/wy z niektórych aplikacji mogą występować problemy z wydajnością podczas instalowania Ochrona punktu końcowego w usłudze Microsoft Defender. Obejmują one aplikacje dla scenariuszy deweloperskich, takich jak Jenkins i Jira, oraz obciążenia baz danych, takie jak OracleDB i Postgres. Jeśli występuje spadek wydajności, rozważ ustawienie wykluczeń dla zaufanych aplikacji, pamiętając [o typowych błędach wykluczania dla Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus). Aby uzyskać dodatkowe wskazówki, rozważ zapoznanie się z dokumentacją dotyczącą wykluczeń oprogramowania antywirusowego z aplikacji innych firm.

## <a name="resources"></a>Zasoby

- Aby uzyskać więcej informacji na temat rejestrowania, odinstalowywania lub innych tematów, zobacz [Zasoby](linux-resources.md).
