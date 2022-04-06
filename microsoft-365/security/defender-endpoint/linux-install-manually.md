---
title: Ręczne Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux
ms.reviewer: ''
description: W tym artykule opisano Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux ręcznie z wiersza polecenia.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, instalacja, wdrażanie, dezinstalacja, szemra, ansible, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
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
ms.openlocfilehash: 4d66dad57fa7b045062a0300327b76030c33dfab
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468176"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>Ręczne Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)


W tym artykule opisano, jak ręcznie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux. Pomyślne wdrożenie wymaga wykonania wszystkich z następujących zadań:

  - [Wymagania wstępne i wymagania systemowe](#prerequisites-and-system-requirements)
  - [Konfigurowanie repozytorium oprogramowania Linux](#configure-the-linux-software-repository)
    - [R ZAO PRZYC i warianty (CentOS, Fedora, Oracle Linux i Amazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
    - [SLES i warianty](#sles-and-variants)
    - [Systemy Ubuntu i Debian](#ubuntu-and-debian-systems)
  - [Instalacja aplikacji](#application-installation)
  - [Pobierz pakiet dołączający](#download-the-onboarding-package)
  - [Konfiguracja klienta](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

Przed rozpoczęciem zobacz program [Ochrona punktu końcowego w usłudze Microsoft Defender Linux](microsoft-defender-endpoint-linux.md), aby uzyskać opis wymagań wstępnych i wymagań systemowych bieżącej wersji oprogramowania.

> [!WARNING]
> Uaktualnienie systemu operacyjnego do nowej wersji głównych po zainstalowaniu produktu wymaga ponownego zainstalowania produktu. Należy odinstalować [istniejący](linux-resources.md#uninstall) program Defender dla punktu końcowego w systemie Linux, uaktualnić system operacyjny, a następnie ponownie skonfigurować program Defender dla punktu końcowego w systemie Linux, następująco:

## <a name="configure-the-linux-software-repository"></a>Konfigurowanie repozytorium oprogramowania Linux

Program Defender dla punktu końcowego w systemie Linux można wdrożyć w jednym z następujących kanałów (oznaczonych poniżej jako *[kanał]**):* niejawni testerzy — szybkie aktualizacji, *testerzy- wolne* lub *powolni.* Każdy z tych kanałów odpowiada repozytorium oprogramowania Linux. Instrukcje dotyczące konfigurowania urządzenia do używania jednego z tych repozytoriów podano poniżej.

Wybór kanału zależy od typu i częstotliwości aktualizacji oferowanych dla Twojego urządzenia. Urządzenia w *niejawnych* programach testów — szybkie aktualizacje to pierwsze urządzenia, które otrzymują aktualizacje i nowe funkcje, a następnie niejawni testerzy — *wolne* aktualizacje, a w końcu *— prod*.

W celu wyświetlania w wersji zapoznawczej nowych funkcji i wczesnych opinii zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie do korzystania  z szybkich lub wolnych niejawnych *testerów*.

> [!WARNING]
> Przełączenie kanału po początkowej instalacji wymaga ponownego zainstalowania produktu. Aby przełączyć kanał produktu: odinstaluj istniejący pakiet, ponownie skonfiguruj urządzenie do korzystania z nowego kanału, a następnie postępuj zgodnie z instrukcjami w tym dokumencie, aby zainstalować pakiet z nowej lokalizacji.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>R ZAO PRZYC i warianty (CentOS, Fedora, Oracle Linux i Amazon Linux 2)

- Zainstaluj `yum-utils` , jeśli nie została jeszcze zainstalowana:

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > Rozkład i wersja oraz informacje o najbliższym wpisie (według głównych, a następnie mniejszych) w obszarze `https://packages.microsoft.com/config/rhel/`.

    Skorzystaj z poniższej tabeli, aby ułatwić Ci zlokalizowanie pakietu:

    <br>

    ****

    |Distro & wersji|Pakiet|
    |---|---|
    |Dla RNOG/Centos/Oracle 8.0-8.5|<https://packages.microsoft.com/config/rhel/8/[channel].repo>|
    |Dla RNOG/Centos/Oracle 7.2-7.9 & Amazon Linux 2 |<https://packages.microsoft.com/config/rhel/7/[channel].repo>|
    |Dla RNOG/Centos 6.7-6.10|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|
    |Dla Fedora 33|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |Dla Fedora 34|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    W poniższych poleceniach zastąp *elementy [version]* *i [channel]* zidentyfikowanymi informacjami:


    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > Użyj polecenia hostnamectl do identyfikowania informacji systemowych, w tym release *[version]*.

    Jeśli na przykład używasz systemu CentOS 7 i chcesz wdrożyć program Defender for Endpoint w systemie Linux z *kanału prod* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    Jeśli natomiast chcesz poznać nowe funkcje na wybranych urządzeniach, możesz wdrożyć aplikację Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux w kanale szybkich aktualizacji dla *niejawnych testerów*:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- Zainstaluj klucz publiczny usługi Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES i warianty

> [!NOTE]
> Rozkład i wersja oraz informacje o najbliższym wpisie (według głównych, a następnie mniejszych) w obszarze `https://packages.microsoft.com/config/sles/`.

   W poniższych poleceniach zastąp *[distro]* i *[version]* informacjami zidentyfikowanymi przez Ciebie:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > Użyj polecenia SPident do identyfikowania informacji związanych z systemem, w tym informacji *o wersji [wersja]*.

   Jeśli na przykład używasz systemu SLES 12 i chcesz wdrożyć w systemie Linux Ochrona punktu końcowego w usłudze Microsoft Defender z *kanału prod*:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- Zainstaluj klucz publiczny usługi Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>Systemy Ubuntu i Debian

- Zainstaluj `curl` , jeśli nie została jeszcze zainstalowana:

    ```bash
    sudo apt-get install curl
    ```

- Zainstaluj `libplist-utils` , jeśli nie została jeszcze zainstalowana:

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> Rozkład i wersja oraz informacje o najbliższym wpisie (według głównych, a następnie mniejszych) w obszarze `https://packages.microsoft.com/config/[distro]/`.

   W poniższym poleceniu zastąp *wartości [distro]* i *[version]* zidentyfikowanymi informacjami:

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > Użyj polecenia hostnamectl do identyfikowania informacji systemowych, w tym release *[version]*.

   Jeśli na przykład używasz ubuntu 18.04 i chcesz wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender Linux z *kanału prod*:

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- Zainstaluj konfigurację repozytorium:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    Jeśli na przykład wybrano *kanał prod* :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- Zainstaluj pakiet `gpg` , jeśli nie został jeszcze zainstalowany:

    ```bash
    sudo apt-get install gpg
    ```

  Jeśli `gpg` nie jest dostępna, zainstaluj .`gnupg`

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

- Aktualizowanie metadanych repozytorium:

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>Instalacja aplikacji

- R ZAO PRZYC i warianty (CentOS i Oracle Linux):

    ```bash
    sudo yum install mdatp
    ```

    > [!NOTE]
    > Jeśli na urządzeniu skonfigurowano wiele repozytoriów firmy Microsoft, możesz określić, z którego repozytorium zainstalować pakiet. W poniższym przykładzie pokazano, jak zainstalować pakiet z `production` kanału `insiders-fast` , jeśli masz również skonfigurowany kanał repozytorium na tym urządzeniu. Taka sytuacja może wystąpić, jeśli używasz wielu produktów firmy Microsoft na swoim urządzeniu. W zależności od rozkładu i wersji serwera alias repozytorium może być inny niż alias w poniższym przykładzie.

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
    > Jeśli na urządzeniu skonfigurowano wiele repozytoriów firmy Microsoft, możesz określić, z którego repozytorium zainstalować pakiet. W poniższym przykładzie pokazano, jak zainstalować pakiet z `production` kanału `insiders-fast` , jeśli masz również skonfigurowany kanał repozytorium na tym urządzeniu. Taka sytuacja może wystąpić, jeśli używasz wielu produktów firmy Microsoft na swoim urządzeniu.

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

- Ubuntu i Debian system:

    ```bash
    sudo apt-get install mdatp
    ```

    > [!NOTE]
    > Jeśli na urządzeniu skonfigurowano wiele repozytoriów firmy Microsoft, możesz określić, z którego repozytorium zainstalować pakiet. W poniższym przykładzie pokazano, jak zainstalować pakiet z `production` kanału `insiders-fast` , jeśli masz również skonfigurowany kanał repozytorium na tym urządzeniu. Taka sytuacja może wystąpić, jeśli używasz wielu produktów firmy Microsoft na swoim urządzeniu.

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

## <a name="download-the-onboarding-package"></a>Pobierz pakiet dołączający

Pobierz pakiet dołączania z witryny Microsoft 365 Defender sieci.

> [!IMPORTANT]
> Jeśli pominiesz ten krok, dowolne wykonane polecenie będzie wyświetlać komunikat ostrzegawczy z informacją, że produkt nie ma licencji. Ponadto polecenie `mdatp health` zwraca wartość .`false`

1. W portalu Microsoft 365 Defender przejdź do Ustawienia > **endpoints > Device management > Onboarding** (Dołączanie urządzeń).
2. Z pierwszego menu rozwijanego wybierz Linux **Server** jako system operacyjny. Z drugiego menu rozwijanego wybierz pozycję **Skrypt** lokalny jako metodę wdrażania.
3. Wybierz **pozycję Pobierz pakiet dołączający**. Zapisz plik jako WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux.png" alt-text="Pobieranie pakietu dołączania do portalu Microsoft 365 Defender sieci Microsoft 365 Defender" lightbox="images/portal-onboarding-linux.png":::

4. Z wiersza polecenia sprawdź, czy masz plik, i wyodrębnij zawartość archiwum:

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

1. Skopiuj MicrosoftDefenderATPOnboardingLinuxServer.py do urządzenia docelowego.

    > [!NOTE]
    > Początkowo urządzenie klienckie nie jest skojarzone z organizacją, a atrybut *orgId* jest pusty.

    ```bash
    mdatp health --field org_id
    ```

2. Uruchamianie MicrosoftDefenderATPOnboardingLinuxServer.py.

    > [!NOTE]
    > Aby uruchomić to polecenie, musisz mieć lub `python` `python3` zainstalować na urządzeniu w zależności od disto i wersji. W razie potrzeby zobacz [Instrukcje krok po kroku dotyczące instalowania języka Python w systemie Linux](https://opensource.com/article/20/4/install-python-linux).
    
    Jeśli korzystasz z systemu R UBUNTU 8.x lub Ubuntu 20.04 lub wyższej, musisz użyć .`python3`

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    W przypadku pozostałych wersji i distrosów musisz użyć `python`.
    
    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```
    
3. Sprawdź, czy urządzenie jest teraz skojarzone z Twoją organizacją, i zgłasza prawidłowy identyfikator organizacji:

    ```bash
    mdatp health --field org_id
    ```

4. Sprawdź stan kondycji produktu, uruchamiając następujące polecenie. Zwracana wartość oznacza `1` , że produkt działa zgodnie z oczekiwaniami:

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > Przy pierwszym uruchamianiu produktu są pobierane najnowsze definicje ochrony przed złośliwym kodem. W zależności od łączności sieciowej może to potrwać do kilku minut. W tym czasie powyższe polecenie zwraca wartość `false`. Stan aktualizacji definicji można sprawdzić za pomocą następującego polecenia:
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > Pamiętaj, że po zakończeniu instalacji może być konieczne skonfigurowanie serwera proxy. Zobacz [Konfigurowanie programu Defender dla punktu końcowego w systemie Linux w celu odnajdowania statycznego serwera proxy: Konfiguracja po instalacji](linux-static-proxy-configuration.md#post-installation-configuration).

5. Uruchom test wykrywania audio/wideo, aby sprawdzić, czy urządzenie jest poprawnie zainstalowane i że zgłasza do usługi. Wykonaj następujące czynności na nowo włodowym urządzeniu:

    - Upewnij się, że jest włączona ochrona w czasie rzeczywistym (jest ona oznaczana przez `1` uruchomienie następującego polecenia):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```
        
      Jeśli ta funkcja nie jest włączona, wykonaj następujące polecenie:
      
       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - Otwórz okno programu Terminal i wykonaj następujące polecenie:

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - Plik powinien zostać poddany kwarantannie przez program Defender for Endpoint w systemie Linux. Użyj następującego polecenia, aby wyświetlić listę wszystkich wykrytych zagrożeń:

        ```bash
        mdatp threat list
        ```

6. Uruchom test EDR wykrywania i zasymuluj wykrywanie, aby sprawdzić, czy urządzenie jest prawidłowo zainstalowane i podlega usłudze. Wykonaj następujące czynności na nowo włodowym urządzeniu:

    - Sprawdź, czy onboarded linux server pojawia się w Microsoft 365 Defender. Jeśli jest to pierwsze wniesienie komputera, może upłynieć do 20 minut, aż zostanie wyświetlony.

    - Pobierz i [wyodrębnij plik skryptu](https://aka.ms/LinuxDIY) na wewnecie serwera systemu Linux i uruchom następujące polecenie: `./mde_linux_edr_diy.sh`

    - Po kilku minutach należy podnieść wykrywanie w Microsoft 365 Defender.

    - Przyjrzyj się szczegółom alertu, maszynowej osi czasu i wykonaj typowe kroki badania.

## <a name="installer-script"></a>Skrypt Instalatora

Ewentualnie możesz użyć zautomatyzowanego skryptu [bash](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) instalatora dostępnego w naszym publicznym [GitHub projektu](https://github.com/microsoft/mdatp-xplat/).
Skrypt identyfikuje rozpowszechnianie i wersję, upraszcza wybór odpowiedniego repozytorium, konfiguruje urządzenie w celu pociągnięcia najnowszego pakietu oraz łączy kroki instalacji produktu i dołączania.

```bash
❯ ./mde_installer.sh --help
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

Więcej informacji znajdziesz [tutaj](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation).

## <a name="log-installation-issues"></a>Problemy z instalacją dziennika

Zobacz [Problemy z instalacją dziennika](linux-resources.md#log-installation-issues) , aby uzyskać więcej informacji na temat sposobu znalezienia automatycznie wygenerowanego dziennika, który jest tworzony przez instalatora w przypadku wystąpienia błędu.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>Jak przeprowadzić migrację z Insiders-Fast do kanału produkcyjnego

1. Odinstaluj wersję "Kanał niejawnych testerów — szybkie wersje" programu Defender dla punktu końcowego w systemie Linux.

    ```bash
    sudo yum remove mdatp
    ```

1. Wyłączanie programu Defender dla punktu końcowego w systemie Linux Insiders-Fast ponownego punktu końcowego

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > W wynikach powinien być pokazywany wynik "packages-microsoft-com-fast-prod".

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. Redeploy Ochrona punktu końcowego w usłudze Microsoft Defender Linux przy użyciu "kanału produkcyjnego".

## <a name="uninstallation"></a>Dezinstalacja

Zobacz [Odinstalowywanie](linux-resources.md#uninstall) , aby uzyskać szczegółowe informacje na temat usuwania programu Defender dla punktu końcowego w systemie Linux z urządzeń klienckich.

## <a name="see-also"></a>Zobacz też

- [Badanie problemów dotyczących kondycji agenta](health-status.md)
