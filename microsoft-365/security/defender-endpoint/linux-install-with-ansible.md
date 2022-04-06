---
title: Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux za pomocą urządzenia Ansible
ms.reviewer: ''
description: W tym artykule opisano, Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux przy użyciu narzędzia Ansible.
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
ms.openlocfilehash: 57f0687fce422f26b76fc8b98a06ce0566f90f60
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476076"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-ansible"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux za pomocą urządzenia Ansible

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

W tym artykule opisano sposób wdrażania programu Defender dla punktu końcowego w systemie Linux przy użyciu narzędzia Ansible. Pomyślne wdrożenie wymaga wykonania wszystkich z następujących zadań:

- [Pobierz pakiet dołączający](#download-the-onboarding-package)
- [Tworzenie plików ANsible YAML](#create-ansible-yaml-files)
- [Wdrożenie](#deployment)
- [Informacje](#references)

## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

Przed rozpoczęciem zapoznaj się z główną stroną programu [Defender for Endpoint w systemie Linux](microsoft-defender-endpoint-linux.md) , aby uzyskać opis wymagań wstępnych i wymagań systemowych bieżącej wersji oprogramowania.

Ponadto w przypadku wdrażania w programie Ansible musisz znać zadania administracyjne z możliwością ansible, mieć skonfigurowane w programie Ansible oraz dowiedzieć się, jak wdrażać podręczniki i zadania. W aplikacji Ansible jest wiele sposobów wykonania tego samego zadania. W poniższych instrukcjach założono, że są dostępne obsługiwane moduły ansible, takie jak *m* i *unarchive* , aby ułatwić wdrożenie pakietu. Twoja organizacja może używać innego przepływu pracy. Szczegółowe informacje można [znaleźć w dokumentacji aplikacji Ansible](https://docs.ansible.com/) .

- Ansible musi być zainstalowany na co najmniej jednym komputerze (Ansible nazywa to węzeł kontrolki).
- Należy skonfigurować usługę SSH dla konta administratora między węzłem kontrolki a wszystkimi węzłami zarządzanymi (urządzeniami, na których będzie zainstalowany program Defender for Endpoint), i zaleca się skonfigurowanie uwierzytelniania kluczem publicznym.
- Następujące oprogramowanie musi być zainstalowane we wszystkich węzłach zarządzanych:
  - zwijanie
  - python-apt

- Wszystkie węzły zarządzane muszą być wymienione w następującym formacie w `/etc/ansible/hosts` odpowiednim pliku:

    ```bash
    [servers]
    host1 ansible_ssh_host=10.171.134.39
    host2 ansible_ssh_host=51.143.50.51
    ```

- Test ping:

    ```bash
    ansible -m ping all
    ```

## <a name="download-the-onboarding-package"></a>Pobierz pakiet dołączający

Pobierz pakiet dołączający z portalu Microsoft 365 Defender sieci:

1. W Microsoft 365 Defender sieci Web przejdź do Ustawienia > **punkty końcowe > zarządzanie urządzeniami > dołączanie**.
2. Z pierwszego menu rozwijanego wybierz Linux **Server** jako system operacyjny. Z drugiego menu rozwijanego wybierz preferowaną metodę wdrażania narzędzie do zarządzania **konfiguracją systemu Linux** .
3. Wybierz **pozycję Pobierz pakiet dołączający**. Zapisz plik jako WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Opcja Pobierz pakiet dołączający" lightbox="images/portal-onboarding-linux-2.png":::

4. W wierszu polecenia sprawdź, czy masz plik. Wyodrębnianie zawartości archiwum:

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-ansible-yaml-files"></a>Tworzenie plików ANsible YAML

Tworzenie podzadań lub plików ról współtworzy podręcznik lub zadanie.

- Tworzenie zadania dołączania: `onboarding_setup.yml`

    ```bash
    - name: Create MDATP directories
      file:
        path: /etc/opt/microsoft/mdatp/
        recurse: true
        state: directory
        mode: 0755
        owner: root
        group: root

    - name: Register mdatp_onboard.json
      stat:
        path: /etc/opt/microsoft/mdatp/mdatp_onboard.json
      register: mdatp_onboard

    - name: Extract WindowsDefenderATPOnboardingPackage.zip into /etc/opt/microsoft/mdatp
      unarchive:
        src: WindowsDefenderATPOnboardingPackage.zip
        dest: /etc/opt/microsoft/mdatp
        mode: 0600
        owner: root
        group: root
      when: not mdatp_onboard.stat.exists
    ```

- Dodaj repozytorium i klucz usługi Defender for Endpoint: `add_apt_repo.yml`

    Program Defender dla punktu końcowego w systemie Linux można wdrożyć w jednym z następujących kanałów (oznaczonych poniżej jako *[kanał]**):* niejawni testerzy — szybkie aktualizacji, *testerzy- wolne* lub *powolni.* Każdy z tych kanałów odpowiada repozytorium oprogramowania Linux.

    Wybór kanału zależy od typu i częstotliwości aktualizacji oferowanych dla Twojego urządzenia. Urządzenia w *niejawnych* programach testów — szybkie aktualizacje to pierwsze urządzenia, które otrzymują aktualizacje i nowe funkcje, a następnie niejawni testerzy — *wolne* aktualizacje, a w końcu *— prod*.

    W celu wyświetlania w wersji zapoznawczej nowych funkcji i wczesnych opinii zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie do korzystania  z szybkich lub wolnych niejawnych *testerów*.

    > [!WARNING]
    > Przełączenie kanału po początkowej instalacji wymaga ponownego zainstalowania produktu. Aby przełączyć kanał produktu: odinstaluj istniejący pakiet, ponownie skonfiguruj urządzenie do korzystania z nowego kanału, a następnie postępuj zgodnie z instrukcjami w tym dokumencie, aby zainstalować pakiet z nowej lokalizacji.

    Zanotuj swój rozkład i wersję oraz określ najbliższy wpis w obszarze `https://packages.microsoft.com/config/[distro]/`.

    W poniższych poleceniach zastąp *[distro]* i *[version]* informacjami zidentyfikowanymi przez Ciebie.

    > [!NOTE]
    > W przypadku Oracle Linux i Amazon Linux 2 zastąp *[distro]* literą "r" .

  ```bash
  - name: Add Microsoft APT key
    apt_key:
      url: https://packages.microsoft.com/keys/microsoft.asc
      state: present
    when: ansible_os_family == "Debian"

  - name: Add Microsoft apt repository for MDATP
    apt_repository:
      repo: deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/[distro]/[version]/prod [codename] main
      update_cache: yes
      state: present
      filename: microsoft-[channel]
    when: ansible_os_family == "Debian"

  - name: Add Microsoft DNF/YUM key
    rpm_key:
      state: present
      key: https://packages.microsoft.com/keys/microsoft.asc
    when: ansible_os_family == "RedHat"

  - name: Add  Microsoft yum repository for MDATP
    yum_repository:
      name: packages-microsoft-[channel]
      description: Microsoft Defender for Endpoint
      file: microsoft-[channel]
      baseurl: https://packages.microsoft.com/[distro]/[version]/[channel]/ 
      gpgcheck: yes
      enabled: Yes
    when: ansible_os_family == "RedHat"
  ```

- Utwórz pliki ANsible install i uninstall YAML.

    - W przypadku rozkładów opartych na zdolnościach należy użyć następującego pliku YAML:

        ```bash
        cat install_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_apt_repo.yml
            - name: Install MDATP
              apt:
                name: mdatp
                state: latest
                update_cache: yes
        ```

        ```bash
        cat uninstall_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              apt:
                name: mdatp
                state: absent
        ```

    - W przypadku dystrybucyjnych opartych na pliku dnf należy użyć następującego pliku YAML:

        ```bash
        cat install_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_yum_repo.yml
            - name: Install MDATP
              dnf:
                name: mdatp
                state: latest
                enablerepo: packages-microsoft-[channel]
        ```

        ```bash
        cat uninstall_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              dnf:
                name: mdatp
                state: absent
        ```

## <a name="deployment"></a>Wdrożenie

Teraz uruchom pliki zadań w odpowiednim katalogu `/etc/ansible/playbooks/` lub w odpowiednim katalogu.

- Instalacja:

    ```bash
    ansible-playbook /etc/ansible/playbooks/install_mdatp.yml -i /etc/ansible/hosts
    ```

> [!IMPORTANT]
> Przy pierwszym uruchamianiu produktu są pobierane najnowsze definicje ochrony przed złośliwym kodem. W zależności od połączenia internetowego może to potrwać do kilku minut.

- Sprawdzanie poprawności/konfiguracja:

    ```bash
    ansible -m shell -a 'mdatp connectivity test' all
    ```
    ```bash
    ansible -m shell -a 'mdatp health' all
    ```

- Dezinstalacja:

    ```bash
    ansible-playbook /etc/ansible/playbooks/uninstall_mdatp.yml -i /etc/ansible/hosts
    ```

## <a name="log-installation-issues"></a>Problemy z instalacją dziennika

Zobacz [Problemy z instalacją dziennika](linux-resources.md#log-installation-issues) , aby uzyskać więcej informacji na temat sposobu znalezienia automatycznie wygenerowanego dziennika, który jest tworzony przez instalatora w przypadku wystąpienia błędu.

## <a name="operating-system-upgrades"></a>Uaktualnienia systemu operacyjnego

Podczas uaktualniania systemu operacyjnego do nowej wersji głównych należy najpierw odinstalować program Defender for Endpoint dla systemu Linux, zainstalować uaktualnienie, a na koniec ponownie skonfigurować program Defender dla punktu końcowego w systemie Linux na urządzeniu.

## <a name="references"></a>Informacje

- [Dodawanie lub usuwanie repozytoriów YUM](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/yum_repository_module.html)

- [Zarządzanie pakietami za pomocą menedżera pakietów dnf](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)

- [Dodawanie i usuwanie repozytoriów APT](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_repository_module.html)

- [Zarządzanie pakietami apt-packages](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)

## <a name="see-also"></a>Zobacz też
- [Badanie problemów dotyczących kondycji agenta](health-status.md)
