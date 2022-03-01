---
title: Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie
ms.reviewer: ''
description: W tym artykule opisano, jak zainstalować program Microsoft Defender for Endpoint w systemie Linux i jak z nich korzystać.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, installation, deploy, dezinstalacja, 8, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.openlocfilehash: ebc5c0bfad32da316368c5c440fed23df28e9e17
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011340"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

W tym temacie opisano, jak zainstalować, skonfigurować, zaktualizować i używać programu Microsoft Defender dla punktu końcowego w systemie Linux.

> [!CAUTION]
> Uruchamianie innych produktów ochrony punktów końcowych innych firm wraz z programem Microsoft Defender for Endpoint dla systemu Linux może prowadzić do problemów z wydajnością i nieprzewidywalnych efektów ubocznych. Jeśli ochrona punktu końcowego firmy innym niż Microsoft jest bezwzględnym wymaganiem w Twoim środowisku, nadal możesz bezpiecznie korzystać z usługi Defender for Endpoint w systemie Linux EDR po skonfigurowaniu funkcji oprogramowania antywirusowego do uruchamiania w trybie [pasywnym](linux-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Jak zainstalować program Microsoft Defender for Endpoint w systemie Linux

### <a name="prerequisites"></a>Wymagania wstępne

- Dostęp do portalu Microsoft 365 Defender sieci Microsoft 365 Defender
- Rozpowszechnianie Linuksa przy użyciu [menedżera systemu systemd](https://systemd.io/)
- Środowisko początkujących w systemie Linux i skryptach BASH
- Uprawnienia administracyjne na urządzeniu (w przypadku wdrożenia ręcznego)

> [!NOTE]
> Program Microsoft Defender dla punktu końcowego w systemie Linux jest niezależny od [agenta OMS](/azure/azure-monitor/agents/agents-overview#log-analytics-agent). Program Microsoft Defender for Endpoint korzysta z własnej, niezależnej potoku telemetrii.


### <a name="installation-instructions"></a>Instrukcje instalacji

Istnieje kilka metod i narzędzi wdrożeniowych, których można użyć do zainstalowania i skonfigurowania programu Microsoft Defender dla punktu końcowego w systemie Linux.

Na ogół należy wykonać następujące czynności:

- Upewnij się, że masz subskrypcję programu Microsoft Defender for Endpoint.
- Wdrażanie programu Microsoft Defender dla punktu końcowego w systemie Linux przy użyciu jednej z następujących metod wdrażania:
  - Narzędzie wiersza polecenia:
    - [Wdrażanie ręczne](linux-install-manually.md)
  - Narzędzia do zarządzania przez inne firmy:
    - [Wdrażanie za pomocą narzędzia do zarządzania konfiguracją konfiguracją konfiguracją w u klientach](linux-install-with-puppet.md)
    - [Wdrażanie przy użyciu narzędzia do zarządzania konfiguracją w sposób ansible](linux-install-with-ansible.md)
    - [Wdrażanie przy użyciu narzędzia do zarządzania konfiguracją oprogramowania](linux-deploy-defender-for-endpoint-with-chef.md)

Jeśli wystąpią jakiekolwiek błędy instalacji, zobacz Rozwiązywanie problemów z instalacją w programie [Microsoft Defender for Endpoint dla systemu Linux](linux-support-install.md).

> [!NOTE]
> Instalowanie programu Microsoft Defender for Endpoint w innej lokalizacji niż ścieżka instalacji domyślnej nie jest obsługiwane. 

### <a name="system-requirements"></a>Wymagania systemowe

- Obsługiwane dystrybucje serwera Linux i wersje x64 (AMD64/EM64T):

  - Red Hat Enterprise Linux w wersji 6.7 lub wyższej
  - System Red Hat Enterprise Linux w wersji 7.2 lub wyższej
  - Red Hat Enterprise Linux 8.x
  - CentOS 6.7 lub wyższa 
  - CentOS 7.2 lub wyższa
  - Ubuntu 16.04 LTS lub wyższa wersja LTS
  - Debian 9 lub wyższy
  - SUSE Linux Enterprise Server 12 lub wyższa wersja
  - Oracle Linux 7.2 lub wyższa wersja
  - Amazon Linux 2
  - Fedora 33 lub wyższa

    > [!NOTE]
    > Dystrybucje i wersje, których nie wymieniono jawnie, są nieobsługiwane (nawet jeśli pochodzą z oficjalnie obsługiwanych dystrybucji).

- Lista obsługiwanych wersji kernelu
  - Red Hat Enterprise Linux 6 i CentOS 6:
    - Dla 6.7: 2.6.32-573.*
    - Dla 6.8: 2.6.32-642.*
    - Dla 6.9: 2.6.32-696.*
    - Dla 6.10: 2.6.32.754.2.1.el6.x86_64 na 2.6.32-754.41.2:
    
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
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64


    > [!NOTE]
    > Po zwolnieniu nowej wersji pakietu pomoc techniczna dla dwóch poprzednich wersji zostanie ograniczona tylko do pomocy technicznej. Wersje starsze niż wymienione w tej sekcji są dostępne tylko dla pomocy technicznej przy uaktualnieniu.

  - Dla pozostałych obsługiwanych rozkładów wymagana jest minimalna wersja kernelu: 3.10.0-327

- Mechanizm dostawcy zdarzeń
  - Red Hat Enterprise Linux 6 i CentOS 6: `Talpa` rozwiązanie oparte na module kernel
  - Pozostałe obsługiwane rozkłady: `Fanotify`
    - Opcja `fanotify` kernel musi być włączona

      > [!CAUTION]
      > Uruchamianie programu Defender dla punktu końcowego w systemie `fanotify`Linux obok innych opartych na rozwiązaniach zabezpieczeń nie jest obsługiwane. Może to prowadzić do nieprzewidywalnych wyników, łącznie z zawieszeniem systemu operacyjnego.

- Miejsce na dysku: 1 GB

- /opt/microsoft/mdatp/sbin/wdavdaemon wymaga uprawnienia wykonywalnego. Aby uzyskać więcej informacji, zobacz "Upewnij się, że daemon ma uprawnienia wykonywalne" w tece Rozwiązywanie problemów z instalacją programu [Microsoft Defender dla punktu końcowego w systemie Linux](/microsoft-365/security/defender-endpoint/linux-support-install).

- Podstawowe funkcje: co najmniej 2, 4 preferowane

- Pamięć: co najmniej 1 GB, 4 preferowane

    > [!NOTE]
    > Upewnij się, że masz wolne miejsce na dysku w /var.

- Rozwiązanie to obecnie zapewnia ochronę w czasie rzeczywistym dla następujących typów systemu plików:

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

Po włączeniu usługi może być konieczne skonfigurowanie sieci lub zapory w celu umożliwienia połączeń wychodzących między usługą a punktami końcowymi.

- Musi być włączona framework inspekcji (`auditd`).

  > [!NOTE]
  > Zdarzenia systemowe przechwytywane przez reguły `/etc/audit/rules.d/` `audit.log`dodawane do będą dodawane do (y) i mogą mieć wpływ na inspekcję hosta i zbieranie danych nadrzędnych. Zdarzenia dodane przez program Microsoft Defender for Endpoint dla systemu Linux zostaną otagowane za pomocą klucza `mdatp` .

### <a name="configuring-exclusions"></a>Konfigurowanie wykluczeń

Podczas dodawania wykluczeń Program antywirusowy Microsoft Defender warto pamiętać o typowych błędach wykluczeń, które mogą [Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>Połączenia sieciowe

Poniższy arkusz kalkulacyjny zawiera listę usług i skojarzonych z nimi adresów URL, z których sieć musi nawiązać połączenie. Upewnij się, że nie ma żadnych reguł zapory ani filtrowania sieci, które uniemożliwiłyby dostęp do tych adresów URL. Jeśli tak, może być konieczne utworzenie reguły *zezwalania* specjalnie dla nich.

<br>

****


|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|Lista adresów URL punktu końcowego programu Microsoft Defender dla klientów komercyjnych | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Lista adresów URL programu Microsoft Defender dla punktów końcowych dla klientów GCC/DoD| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|


> [!NOTE]
> Aby uzyskać bardziej konkretną listę adresów URL, zobacz [Konfigurowanie ustawień łączności internetowej i serwera proxy](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

Usługa Defender for Endpoint może wykryć serwer proxy przy użyciu następujących metod odnajdowania:

- Przezroczysty serwer proxy
- Ręczna statyczna konfiguracja serwera proxy

Jeśli ruch anonimowy jest blokowany przez serwer proxy lub zaporę, upewnij się, że ruch anonimowy jest dozwolony we wcześniej wymienionych adresach URL. W przypadku przezroczystych serwerów proxy dodatkowa konfiguracja usługi Defender dla punktu końcowego nie jest potrzebna. W przypadku statycznego serwera proxy wykonaj czynności opisane w [ręcznej konfiguracji statycznego serwera proxy](linux-static-proxy-configuration.md).

> [!WARNING]
> Pac, WPAD i uwierzytelnione proxy nie są obsługiwane. Upewnij się, że używany jest tylko statyczny lub przezroczysty serwer proxy.
>
> Inspekcja SSL i przechwytywanie serwerów proxy nie są również obsługiwane ze względów bezpieczeństwa. Skonfiguruj wyjątek dla inspekcji SSL i serwera proxy w celu bezpośredniego przejścia danych z programu Defender for Endpoint w systemie Linux do odpowiednich adresów URL bez przecięcia. Dodanie certyfikatu odcięcia do magazynu globalnego nie umożliwi przecięcia.

Aby uzyskać instrukcje rozwiązywania problemów, zobacz [Rozwiązywanie problemów z łącznością z chmurą dla programu Microsoft Defender dla punktu końcowego w systemie Linux](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Jak zaktualizować program Microsoft Defender dla punktu końcowego w systemie Linux

Firma Microsoft regularnie publikuje aktualizacje oprogramowania w celu zwiększenia wydajności, zabezpieczeń i dostarczania nowych funkcji. Aby zaktualizować program Microsoft Defender dla punktu końcowego w systemie Linux, zobacz Wdrażanie aktualizacji programu [Microsoft Defender dla punktu końcowego w systemie Linux](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Konfigurowanie ochrony punktu końcowego w usłudze Microsoft Defender na Linuxie

Wskazówki dotyczące konfigurowania produktu w środowiskach przedsiębiorstwa można uzyskać w tece Ustawianie preferencji programu [Microsoft Defender dla punktu końcowego w systemie Linux](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>Typowe aplikacje do programu Microsoft Defender for Endpoint mogą mieć wpływ

Duże obciążenia pracą we/wy z określonych aplikacji mogą doświadczać problemów z wydajnością, jeśli zainstalowano program Microsoft Defender for Endpoint. Należą do nich aplikacje dla deweloperów scenariuszy, takich jak Jenkins i Jira, oraz obciążenia baz danych, takie jak OracleDB i Postgres. Jeśli występuje spadek wydajności, rozważ ustawienie wykluczeń dla zaufanych aplikacji, uwzględniając typowe błędy [wykluczeń, Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) pamiętać. Aby uzyskać dodatkowe wskazówki, rozważ konsultowanie dokumentacji dotyczącej wykluczeń oprogramowania antywirusowego z aplikacji innych firm.

## <a name="resources"></a>Zasoby

- Aby uzyskać więcej informacji na temat rejestrowania, odinstalowywania lub innych tematów, zobacz [Zasoby](linux-resources.md).
