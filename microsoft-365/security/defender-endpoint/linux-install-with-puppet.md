---
title: Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux za pomocą platformy Puppet
ms.reviewer: ''
description: Opis sposobu wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux przy użyciu platformy Puppet.
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
ms.openlocfilehash: 5ec3eb5d12933b33f4af7d5af96b4ab54fda4604
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663803"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux za pomocą platformy Puppet

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

W tym artykule opisano sposób wdrażania usługi Defender for Endpoint w systemie Linux przy użyciu platformy Puppet. Pomyślne wdrożenie wymaga wykonania wszystkich następujących zadań:

- [Pobieranie pakietu dołączania](#download-the-onboarding-package)
- [Tworzenie manifestu platformy Puppet](#create-a-puppet-manifest)
- [Wdrożenie](#deployment)
- [Sprawdzanie stanu dołączania](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

 Opis wymagań wstępnych i wymagań systemowych dotyczących bieżącej wersji oprogramowania można znaleźć [na stronie głównej usługi Defender for Endpoint w systemie Linux](microsoft-defender-endpoint-linux.md).

Ponadto w przypadku wdrażania platformy Puppet musisz znać zadania administracyjne platformy Puppet, skonfigurować platformę Puppet i wiedzieć, jak wdrażać pakiety. Platforma Puppet ma wiele sposobów wykonania tego samego zadania. W tych instrukcjach założono dostępność obsługiwanych modułów Puppet, takich jak *apt* , aby ułatwić wdrożenie pakietu. Twoja organizacja może używać innego przepływu pracy. Aby uzyskać szczegółowe informacje, zapoznaj się z [dokumentacją platformy Puppet](https://puppet.com/docs) .

## <a name="download-the-onboarding-package"></a>Pobieranie pakietu dołączania

Pobierz pakiet dołączania z portalu Microsoft 365 Defender:

1. W portalu Microsoft 365 Defender przejdź do **obszaru Ustawienia > Punkty końcowe > Zarządzanie urządzeniami > dołączanie**.
2. W pierwszym menu rozwijanym wybierz pozycję **Linux Server** jako system operacyjny. W drugim menu rozwijanym wybierz **preferowane narzędzie do zarządzania konfiguracją systemu Linux** jako metodę wdrażania.
3. Wybierz pozycję **Pobierz pakiet dołączania**. Zapisz plik jako WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Opcja pobrania dołączony pakiet" lightbox="images/portal-onboarding-linux-2.png":::

4. W wierszu polecenia sprawdź, czy masz plik. 

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

5. Wyodrębnij zawartość archiwum.

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-a-puppet-manifest"></a>Tworzenie manifestu platformy Puppet

Należy utworzyć manifest platformy Puppet do wdrażania usługi Defender for Endpoint w systemie Linux na urządzeniach zarządzanych przez serwer Puppet. W tym przykładzie użyto modułów *apt* i *yumrepo* dostępnych z platformy puppetlabs i przyjęto założenie, że moduły zostały zainstalowane na serwerze Puppet.

Utwórz foldery *install_mdatp/files* i *install_mdatp/manifesty* w folderze modules instalacji puppet. Ten folder zazwyczaj znajduje się w *folderze /etc/puppetlabs/code/environments/production/modules na serwerze* Puppet. Skopiuj utworzony powyżej plik mdatp_onboard.json do folderu *install_mdatp/files* . Tworzenie *pliku init.pp* plik zawierający instrukcje wdrażania:

```bash
pwd
```

```Output
/etc/puppetlabs/code/environments/production/modules
```

```bash
tree install_mdatp
```

```Output
install_mdatp
├── files
│   └── mdatp_onboard.json
└── manifests
    └── init.pp
```

### <a name="contents-of-install_mdatpmanifestsinitpp"></a>Zawartość `install_mdatp/manifests/init.pp`

Usługę Defender for Endpoint w systemie Linux można wdrożyć z jednego z następujących kanałów (oznaczonego poniżej jako *[channel]*): *insiders-fast*, *insiders-slow* lub *prod*. Każdy z tych kanałów odpowiada repozytorium oprogramowania systemu Linux.

Wybór kanału określa typ i częstotliwość aktualizacji oferowanych urządzeniu. Urządzenia w *insiders-fast* są pierwszymi, które otrzymują aktualizacje i nowe funkcje, a następnie *wewnętrznych powolny* i ostatnio przez *prod*.

Aby zapoznać się z nowymi funkcjami i przekazać wczesną opinię, zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie tak, aby *korzystały z funkcji insiders-fast* lub *insiders-slow*.

> [!WARNING]
> Przełączenie kanału po początkowej instalacji wymaga ponownej instalacji produktu. Aby przełączyć kanał produktu: odinstaluj istniejący pakiet, skonfiguruj ponownie urządzenie do korzystania z nowego kanału i wykonaj kroki opisane w tym dokumencie, aby zainstalować pakiet z nowej lokalizacji.

Zanotuj dystrybucję i wersję oraz zidentyfikuj najbliższy wpis w obszarze `https://packages.microsoft.com/config/[distro]/`.

W poniższych poleceniach zastąp *ciąg [dystrybucja]* i *[wersja]* zidentyfikowanymi informacjami:

> [!NOTE]
> W przypadku systemów RedHat, Oracle Linux, Amazon Linux 2 i CentOS 8 zastąp *ciąg [dystrybucja]* ciągiem "rhel".

```puppet
# Puppet manifest to install Microsoft Defender for Endpoint on Linux.
# @param channel The release channel based on your environment, insider-fast or prod.
# @param distro The Linux distribution in lowercase. In case of RedHat, Oracle Linux, Amazon Linux 2, and CentOS 8, the distro variable should be 'rhel'.
# @param version The Linux distribution release number, e.g. 7.4.

class install_mdatp (
$channel = 'insiders-fast',
$distro = undef,
$version = undef
){
    case $::osfamily {
        'Debian' : {
            apt::source { 'microsoftpackages' :
                location => "https://packages.microsoft.com/${distro}/${version}/prod",
                release  => $channel,
                repos    => 'main',
                key      => {
                    'id'     => 'BC528686B50D79E339D3721CEB3E94ADBE1229CF',
                    'server' => 'keyserver.ubuntu.com',
                },
            }
        }
        'RedHat' : {
            yumrepo { 'microsoftpackages' :
                baseurl  => "https://packages.microsoft.com/${distro}/${version}/${channel}",
                descr    => "packages-microsoft-com-prod-${channel}",
                enabled  => 1,
                gpgcheck => 1,
                gpgkey   => 'https://packages.microsoft.com/keys/microsoft.asc'
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }

    case $::osfamily {
        /(Debian|RedHat)/: {
            file { ['/etc/opt', '/etc/opt/microsoft', '/etc/opt/microsoft/mdatp']:
                ensure => directory,
                owner  => root,
                group  => root,
                mode   => '0755'
            }

            file { '/etc/opt/microsoft/mdatp/mdatp_onboard.json':
                source  => 'puppet:///modules/install_mdatp/mdatp_onboard.json',
                owner   => root,
                group   => root,
                mode    => '0600',
                require => File['/etc/opt/microsoft/mdatp']
            }

            package { 'mdatp':
                ensure  => 'installed',
                require => File['/etc/opt/microsoft/mdatp/mdatp_onboard.json']
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }
}
```

## <a name="deployment"></a>Wdrożenie

Uwzględnij powyższy manifest w pliku site.pp Plik:

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```

```Output
node "default" {
    include install_mdatp
}
```

Zarejestrowane urządzenia agenta okresowo sondują serwer Puppet Server i instalują nowe profile konfiguracji i zasady natychmiast po ich wykryciu.

## <a name="monitor-puppet-deployment"></a>Monitorowanie wdrożenia platformy Puppet

Na urządzeniu agenta możesz również sprawdzić stan dołączania, uruchamiając następujące polecenie:

```bash
mdatp health
```

```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **licencja**: Potwierdza to, że urządzenie jest powiązane z Twoją organizacją.

- **orgId**: jest to identyfikator organizacji usługi Defender for Endpoint.

## <a name="check-onboarding-status"></a>Sprawdzanie stanu dołączania

Możesz sprawdzić, czy urządzenia zostały prawidłowo dołączone, tworząc skrypt. Na przykład następujący skrypt sprawdza zarejestrowane urządzenia pod kątem stanu dołączania:

```bash
mdatp health --field healthy
```

Powyższe polecenie jest drukowane `1` , jeśli produkt jest dołączony i działa zgodnie z oczekiwaniami.

> [!IMPORTANT]
> Gdy produkt zostanie uruchomiony po raz pierwszy, pobierze najnowsze definicje ochrony przed złośliwym kodem. W zależności od połączenia internetowego może to potrwać do kilku minut. W tym czasie powyższe polecenie zwraca wartość `0`.

Jeśli produkt nie jest w dobrej kondycji, kod zakończenia (który można sprawdzić za pomocą `echo $?`) wskazuje problem:

- 1, jeśli urządzenie nie zostało jeszcze dołączone.
- 3, jeśli nie można nawiązać połączenia z demonem.

## <a name="log-installation-issues"></a>Problemy z instalacją dziennika

 Aby uzyskać więcej informacji na temat znajdowania automatycznie wygenerowanego dziennika utworzonego przez instalatora w przypadku wystąpienia błędu, zobacz [Problemy z instalacją dziennika](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>Uaktualnienia systemu operacyjnego

Podczas uaktualniania systemu operacyjnego do nowej wersji głównej należy najpierw odinstalować usługę Defender for Endpoint w systemie Linux, zainstalować uaktualnienie, a na koniec ponownie skonfigurować usługę Defender dla punktu końcowego w systemie Linux na urządzeniu.

## <a name="uninstallation"></a>Dezinstalacji

Utwórz moduł *remove_mdatp* podobny do *install_mdatp* z następującą zawartością w *pliku init.pp* Plik:

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
