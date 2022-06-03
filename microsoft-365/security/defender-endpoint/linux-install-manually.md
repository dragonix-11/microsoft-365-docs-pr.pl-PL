---
title: Ręczne wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux
ms.reviewer: ''
description: Opisuje sposób ręcznego wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux z poziomu wiersza polecenia.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
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
ms.openlocfilehash: a9d16cb82354bcb44e817de3207cb49de66dbf91
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873055"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>Ręczne wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)


W tym artykule opisano sposób ręcznego wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux. Pomyślne wdrożenie wymaga wykonania wszystkich następujących zadań:

  - [Wymagania wstępne i wymagania systemowe](#prerequisites-and-system-requirements)
  - [Konfigurowanie repozytorium oprogramowania systemu Linux](#configure-the-linux-software-repository)
    - [RHEL i warianty (CentOS, Fedora, Oracle Linux i Amazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
    - [SLES i warianty](#sles-and-variants)
    - [Systemy Ubuntu i Debian](#ubuntu-and-debian-systems)
  - [Instalacja aplikacji](#application-installation)
  - [Pobieranie pakietu dołączania](#download-the-onboarding-package)
  - [Konfiguracja klienta](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

Przed rozpoczęciem zapoznaj się z [artykułem Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](microsoft-defender-endpoint-linux.md), aby zapoznać się z opisem wymagań wstępnych i wymagań systemowych dotyczących bieżącej wersji oprogramowania.

> [!WARNING]
> Uaktualnienie systemu operacyjnego do nowej wersji głównej po zainstalowaniu produktu wymaga ponownej instalacji produktu. Należy [odinstalować](linux-resources.md#uninstall) istniejącą usługę Defender for Endpoint w systemie Linux, uaktualnić system operacyjny, a następnie ponownie skonfigurować usługę Defender dla punktu końcowego w systemie Linux, wykonując poniższe kroki.

## <a name="configure-the-linux-software-repository"></a>Konfigurowanie repozytorium oprogramowania systemu Linux

Usługę Defender for Endpoint w systemie Linux można wdrożyć z jednego z następujących kanałów (oznaczonego poniżej jako *[channel]*): *insiders-fast*, *insiders-slow* lub *prod*. Każdy z tych kanałów odpowiada repozytorium oprogramowania systemu Linux. Poniżej przedstawiono instrukcje dotyczące konfigurowania urządzenia do korzystania z jednego z tych repozytoriów.

Wybór kanału określa typ i częstotliwość aktualizacji oferowanych urządzeniu. Urządzenia w *insiders-fast* są pierwszymi, które otrzymują aktualizacje i nowe funkcje, a następnie *wewnętrznych powolny* i ostatnio przez *prod*.

Aby zapoznać się z nowymi funkcjami i przekazać wczesną opinię, zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie tak, aby *korzystały z funkcji insiders-fast* lub *insiders-slow*.

> [!WARNING]
> Przełączenie kanału po początkowej instalacji wymaga ponownej instalacji produktu. Aby przełączyć kanał produktu: odinstaluj istniejący pakiet, skonfiguruj ponownie urządzenie do korzystania z nowego kanału i wykonaj kroki opisane w tym dokumencie, aby zainstalować pakiet z nowej lokalizacji.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>RHEL i warianty (CentOS, Fedora, Oracle Linux i Amazon Linux 2)

- Zainstaluj `yum-utils` , jeśli nie jest jeszcze zainstalowany:

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > Twoja dystrybucja i wersja oraz zidentyfikuj najbliższy wpis (według głównych, a następnie pomocniczych) dla niego w obszarze `https://packages.microsoft.com/config/rhel/`.

    Skorzystaj z poniższej tabeli, aby ułatwić ci znalezienie pakietu:

    <br>

    ****

    |Wersja & dystrybucji|Pakiet|
    |---|---|
    |Dla RHEL/Centos/Oracle 8.0-8.5|<https://packages.microsoft.com/config/rhel/8/[channel].repo>|
    |Dla RHEL/Centos/Oracle 7.2-7.9 & Amazon Linux 2 |</azure/cognitive-services/speech-service/how-to-configure-rhel-centos-7>|
    <!--|Dla RHEL/Centos 6.7-6.10|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|-->
    |Dla fedory 33|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |Dla fedory 34|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    W następujących poleceniach zastąp ciąg *[version]* i *[channel]* zidentyfikowanymi informacjami:


    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > Użyj polecenia hostnamectl, aby zidentyfikować informacje związane z systemem, w tym wydanie *[wersja]*.

    Jeśli na przykład używasz systemu CentOS 7 i chcesz wdrożyć usługę Defender for Endpoint w systemie Linux z kanału *prod* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    Jeśli chcesz eksplorować nowe funkcje na wybranych urządzeniach, możesz wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux na kanale *insiders-fast*:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- Zainstaluj klucz publiczny usługi Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES i warianty

> [!NOTE]
> Twoja dystrybucja i wersja oraz zidentyfikuj najbliższy wpis (według głównych, a następnie pomocniczych) dla niego w obszarze `https://packages.microsoft.com/config/sles/`.

   W następujących poleceniach zastąp *ciąg [dystrybucja]* i *[wersja]* zidentyfikowanymi informacjami:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > Użyj polecenia SPident, aby zidentyfikować informacje związane z systemem, w tym wydanie *[wersja]*.

   Jeśli na przykład używasz protokołu SLES 12 i chcesz wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux z kanału *prod*:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- Zainstaluj klucz publiczny usługi Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>Systemy Ubuntu i Debian

- Zainstaluj `curl` , jeśli nie jest jeszcze zainstalowany:

    ```bash
    sudo apt-get install curl
    ```

- Zainstaluj `libplist-utils` , jeśli nie jest jeszcze zainstalowany:

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> Twoja dystrybucja i wersja oraz zidentyfikuj najbliższy wpis (według głównych, a następnie pomocniczych) dla niego w obszarze `https://packages.microsoft.com/config/[distro]/`.

   W poniższym poleceniu zastąp *ciąg [dystrybucja]* i *[wersja]* zidentyfikowanymi informacjami:

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > Użyj polecenia hostnamectl, aby zidentyfikować informacje związane z systemem, w tym wydanie *[wersja]*.

   Jeśli na przykład używasz systemu Ubuntu 18.04 i chcesz wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux z kanału *prod*:

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- Zainstaluj konfigurację repozytorium:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    Jeśli na przykład wybrano kanał *prod* :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- Zainstaluj pakiet, `gpg` jeśli nie został jeszcze zainstalowany:

    ```bash
    sudo apt-get install gpg
    ```

  Jeśli `gpg` program jest niedostępny, zainstaluj program `gnupg`.

    ```bash
    sudo apt-get install gnupg
    ```

- Zainstaluj klucz publiczny usługi Microsoft GPG:

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

- Zainstaluj sterownik https, jeśli jeszcze go nie ma:

    ```bash
    sudo apt-get install apt-transport-https
    ```

- Zaktualizuj metadane repozytorium:

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>Instalacja aplikacji

- RHEL i warianty (CentOS i Oracle Linux):

    ```bash
    sudo yum install mdatp
    ```

    > [!NOTE]
    > Jeśli na urządzeniu skonfigurowano wiele repozytoriów firmy Microsoft, możesz określić, z którego repozytorium zainstalować pakiet. W poniższym przykładzie pokazano, jak zainstalować pakiet z kanału `production` , jeśli na tym urządzeniu skonfigurowano również `insiders-fast` kanał repozytorium. Taka sytuacja może wystąpić, jeśli na urządzeniu jest używanych wiele produktów firmy Microsoft. W zależności od dystrybucji i wersji serwera alias repozytorium może być inny niż w poniższym przykładzie.

    ```bash
    # list all repositories
    yum repolist
    ```

    ```Output
    ...
    packages-microsoft-com-prod               packages-microsoft-com-prod        316
    packages-microsoft-com-prod-insiders-fast packages-microsoft-com-prod-ins      2
    ...
    ```

    ```bash
    # install the package from the production repository
    sudo yum --enablerepo=packages-microsoft-com-prod install mdatp
    ```

- SLES i warianty:

    ```bash
    sudo zypper install mdatp
    ```

    > [!NOTE]
    > Jeśli na urządzeniu skonfigurowano wiele repozytoriów firmy Microsoft, możesz określić, z którego repozytorium zainstalować pakiet. W poniższym przykładzie pokazano, jak zainstalować pakiet z kanału `production` , jeśli na tym urządzeniu skonfigurowano również `insiders-fast` kanał repozytorium. Taka sytuacja może wystąpić, jeśli na urządzeniu jest używanych wiele produktów firmy Microsoft.

    ```bash
    zypper repos
    ```

    ```Output
    ...
    #  | Alias | Name | ...
    XX | packages-microsoft-com-insiders-fast | microsoft-insiders-fast | ...
    XX | packages-microsoft-com-prod | microsoft-prod | ...
    ...

    ```

    ```bash
    sudo zypper install packages-microsoft-com-prod:mdatp
    ```

- System Ubuntu i Debian:

    ```bash
    sudo apt-get install mdatp
    ```

    > [!NOTE]
    > Jeśli na urządzeniu skonfigurowano wiele repozytoriów firmy Microsoft, możesz określić, z którego repozytorium zainstalować pakiet. W poniższym przykładzie pokazano, jak zainstalować pakiet z kanału `production` , jeśli na tym urządzeniu skonfigurowano również `insiders-fast` kanał repozytorium. Taka sytuacja może wystąpić, jeśli na urządzeniu jest używanych wiele produktów firmy Microsoft.

    ```bash
    cat /etc/apt/sources.list.d/*
    ```

    ```Output
    deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod insiders-fast main
    deb [arch=amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod bionic main
    ```

    ```bash
    sudo apt -t bionic install mdatp
    ```

## <a name="download-the-onboarding-package"></a>Pobieranie pakietu dołączania

Pobierz pakiet dołączania z portalu Microsoft 365 Defender.

> [!IMPORTANT]
> Jeśli ten krok zostanie pominięty, każde wykonane polecenie wyświetli komunikat ostrzegawczy wskazujący, że produkt jest nielicencjonowany. `mdatp health` Również polecenie zwraca wartość `false`.

1. W portalu Microsoft 365 Defender przejdź do **obszaru Ustawienia > Punkty końcowe > Zarządzanie urządzeniami > dołączanie**.
2. W pierwszym menu rozwijanym wybierz pozycję **Linux Server** jako system operacyjny. W drugim menu rozwijanym wybierz pozycję **Skrypt lokalny** jako metodę wdrażania.
3. Wybierz pozycję **Pobierz pakiet dołączania**. Zapisz plik jako WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux.png" alt-text="Pobieranie pakietu dołączania w portalu Microsoft 365 Defender" lightbox="images/portal-onboarding-linux.png":::

4. W wierszu polecenia sprawdź, czy masz plik, i wyodrębnij zawartość archiwum:

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  5752 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

## <a name="client-configuration"></a>Konfiguracja klienta

1. Skopiuj MicrosoftDefenderATPOnboardingLinuxServer.py na urządzenie docelowe.

    > [!NOTE]
    > Początkowo urządzenie klienckie nie jest skojarzone z organizacją, a atrybut *orgId* jest pusty.

    ```bash
    mdatp health --field org_id
    ```

2. Uruchom MicrosoftDefenderATPOnboardingLinuxServer.py.

    > [!NOTE]
    > Aby uruchomić to polecenie, musisz mieć `python`  lub `python3` zainstalować na urządzeniu w zależności od wersji i disto. W razie potrzeby zobacz [Instrukcje krok po kroku dotyczące instalowania języka Python w systemie Linux](https://opensource.com/article/20/4/install-python-linux).
    
    Jeśli używasz systemu RHEL 8.x lub Ubuntu 20.04 lub nowszego, musisz użyć polecenia `python3`.

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    W pozostałych dystrybucjach i wersjach należy użyć polecenia `python`.
    
    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```
    
3. Sprawdź, czy urządzenie jest teraz skojarzone z Twoją organizacją i zgłosi prawidłowy identyfikator organizacji:

    ```bash
    mdatp health --field org_id
    ```

4. Sprawdź stan kondycji produktu, uruchamiając następujące polecenie. Zwracana wartość `1` oznacza, że produkt działa zgodnie z oczekiwaniami:

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > Gdy produkt zostanie uruchomiony po raz pierwszy, pobierze najnowsze definicje ochrony przed złośliwym kodem. Może to potrwać do kilku minut w zależności od łączności sieciowej. W tym czasie powyższe polecenie zwraca wartość `false`. Stan aktualizacji definicji można sprawdzić za pomocą następującego polecenia:
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > Należy pamiętać, że po zakończeniu instalacji początkowej może być konieczne skonfigurowanie serwera proxy. Zobacz [Konfigurowanie usługi Defender dla punktu końcowego w systemie Linux w celu odnajdywania statycznego serwera proxy: konfiguracja po instalacji](linux-static-proxy-configuration.md#post-installation-configuration).

5. Uruchom test wykrywania av, aby sprawdzić, czy urządzenie jest prawidłowo dołączone i raportuje do usługi. Wykonaj następujące kroki na nowo dołączonym urządzeniu:

    - Upewnij się, że ochrona w czasie rzeczywistym jest włączona (oznaczona wynikiem uruchomienia następującego `1` polecenia):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```
        
      Jeśli nie jest włączona, wykonaj następujące polecenie:
      
       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - Otwórz okno Terminal i wykonaj następujące polecenie:

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - Plik powinien zostać poddany kwarantannie przez usługę Defender for Endpoint w systemie Linux. Użyj następującego polecenia, aby wyświetlić listę wszystkich wykrytych zagrożeń:

        ```bash
        mdatp threat list
        ```

6. Uruchom test wykrywania EDR i symuluj wykrywanie, aby sprawdzić, czy urządzenie jest prawidłowo dołączone i raportuje do usługi. Wykonaj następujące kroki na nowo dołączonym urządzeniu:

    - Sprawdź, czy dołączony serwer z systemem Linux jest wyświetlany w Microsoft 365 Defender. Jeśli jest to pierwsze dołączenie maszyny, jej wyświetlenie może potrwać do 20 minut.

    - Pobierz i wyodrębnij [plik skryptu](https://aka.ms/LinuxDIY) na dołączony serwer z systemem Linux i uruchom następujące polecenie: `./mde_linux_edr_diy.sh`

    - Po kilku minutach należy podnieść wykrywanie w Microsoft 365 Defender.

    - Przyjrzyj się szczegółom alertu, osi czasu maszyny i wykonaj typowe kroki badania.

## <a name="installer-script"></a>Skrypt instalatora

Alternatywnie możesz użyć zautomatyzowanego [skryptu bash instalatora](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) udostępnionego w naszym [publicznym repozytorium GitHub](https://github.com/microsoft/mdatp-xplat/).
Skrypt identyfikuje dystrybucję i wersję, upraszcza wybór odpowiedniego repozytorium, konfiguruje urządzenie do ściągania najnowszego pakietu i łączy kroki instalacji produktu i dołączania.

```bash
> ./mde_installer.sh --help
usage: basename ./mde_installer.sh [OPTIONS]
Options:
-c|--channel      specify the channel from which you want to install. Default: insiders-fast
-i|--install      install the product
-r|--remove       remove the product
-u|--upgrade      upgrade the existing product
-o|--onboard      onboard/offboard the product with <onboarding_script>
-p|--passive-mode set EPP to passive mode
-t|--tag          set a tag by declaring <name> and <value>. ex: -t GROUP Coders
-m|--min_req      enforce minimum requirements
-w|--clean        remove repo from package manager for a specific channel
-v|--version      print out script version
-h|--help         display help
```

Przeczytaj więcej [tutaj](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation).

## <a name="log-installation-issues"></a>Problemy z instalacją dziennika

Zobacz [Problemy z instalacją dziennika](linux-resources.md#log-installation-issues) , aby uzyskać więcej informacji na temat znajdowania automatycznie wygenerowanego dziennika utworzonego przez instalatora w przypadku wystąpienia błędu.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>Jak przeprowadzić migrację z Insiders-Fast do kanału produkcyjnego

1. Odinstaluj wersję "Insiders-Fast channel" usługi Defender for Endpoint w systemie Linux.

    ```bash
    sudo yum remove mdatp
    ```

1. Wyłączanie repozytorium Defender for Endpoint w systemie Linux Insiders-Fast

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > Dane wyjściowe powinny zawierać ciąg "packages-microsoft-com-fast-prod".

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. Ponowne wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux przy użyciu "kanału produkcyjnego".

## <a name="uninstallation"></a>Dezinstalacji

Zobacz [Odinstalowywanie](linux-resources.md#uninstall) , aby uzyskać szczegółowe informacje na temat usuwania usługi Defender for Endpoint w systemie Linux z urządzeń klienckich.

## <a name="see-also"></a>Zobacz też

- [Badaj problemy z kondycją agenta](health-status.md)
