---
title: Wdrażanie oprogramowania Ochrona punktu końcowego w usłudze Microsoft Defender Linux za pomocą systemu Linux
ms.reviewer: ''
description: W tym artykule opisano, jak Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux przy użyciu owej aktualizacji.
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
ms.openlocfilehash: adf58b3009c3feaafde389b91ddc64b441d49f40
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476014"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>Wdrażanie oprogramowania Ochrona punktu końcowego w usłudze Microsoft Defender Linux za pomocą systemu Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

W tym artykule opisano sposób wdrażania programu Defender dla punktu końcowego w systemie Linux przy użyciu technologii 8. Pomyślne wdrożenie wymaga wykonania wszystkich z następujących zadań:

- [Pobierz pakiet dołączający](#download-the-onboarding-package)
- [Utwórz manifest manifestu w kiecie](#create-a-puppet-manifest)
- [Wdrożenie](#deployment)
- [Sprawdź stan dołączania](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

 Opis wymagań wstępnych i wymagań systemowych dla bieżącej wersji oprogramowania można znaleźć na stronie głównej programu [Defender for Endpoint w systemie Linux](microsoft-defender-endpoint-linux.md).

Ponadto w przypadku wdrożenia z zadaniami kondyscyjną należy zapoznać się z zadaniami administracyjnymi, mieć skonfigurowane ustawienia Szybka i dowiedzieć się, jak wdrażać pakiety. Można wykonać to samo zadanie na wiele sposobów. W poniższych instrukcjach założono, że są dostępne obsługiwane moduły na przykład *apt* , aby ułatwić wdrożenie pakietu. Twoja organizacja może używać innego przepływu pracy. Aby uzyskać szczegółowe informacje [, zapoznaj się z dokumentacją](https://puppet.com/docs) treści.

## <a name="download-the-onboarding-package"></a>Pobierz pakiet dołączający

Pobierz pakiet dołączający z portalu Microsoft 365 Defender sieci:

1. W Microsoft 365 Defender sieci Web przejdź do Ustawienia > **punkty końcowe > zarządzanie urządzeniami > dołączanie**.
2. Z pierwszego menu rozwijanego wybierz Linux **Server** jako system operacyjny. Z drugiego menu rozwijanego wybierz preferowaną metodę wdrażania narzędzie do zarządzania **konfiguracją systemu Linux** .
3. Wybierz **pozycję Pobierz pakiet dołączający**. Zapisz plik jako WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Opcja pobrania pakietu onboarded" lightbox="images/portal-onboarding-linux-2.png":::

4. W wierszu polecenia sprawdź, czy masz plik. 

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
5. Wyodrębnianie zawartości archiwum.
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-a-puppet-manifest"></a>Tworzenie manifestu manifestu manifestu w celu utworzenia pliku manifestu

Musisz utworzyć manifest w celu wdrożenia programu Defender dla punktu końcowego w systemie Linux na urządzeniach zarządzanych przez serwer szosowy. W tym przykładzie korzysta się z modułów *mi* *i yumrepo* dostępnych w programieLabs oraz założono, że moduły zostały zainstalowane na serwerze Szyb.

Utwórz foldery *install_mdatp/plików* *i pliki install_mdatp/manifestów* w folderze modułów instalacji Folder. Ten folder zwykle znajduje się w *katalogu /etc/ftplabs/code/environments/production/modules* na serwerze Szybki. Skopiuj utworzony mdatp_onboard.json do folderu install_mdatp */pliki* . Tworzenie *init.pp* zawierający instrukcje dotyczące wdrażania:

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

Program Defender dla punktu końcowego w systemie Linux można wdrożyć w jednym z następujących kanałów (oznaczonych poniżej jako *[kanał]**):* niejawni testerzy — szybkie aktualizacji, *testerzy- wolne* lub *powolni.* Każdy z tych kanałów odpowiada repozytorium oprogramowania Linux.

Wybór kanału zależy od typu i częstotliwości aktualizacji oferowanych dla Twojego urządzenia. Urządzenia w *niejawnych* programach testów — szybkie aktualizacje to pierwsze urządzenia, które otrzymują aktualizacje i nowe funkcje, a następnie niejawni testerzy — *wolne* aktualizacje, a w końcu *— prod*.

W celu wyświetlania w wersji zapoznawczej nowych funkcji i wczesnych opinii zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie do korzystania  z szybkich lub wolnych niejawnych *testerów*.

> [!WARNING]
> Przełączenie kanału po początkowej instalacji wymaga ponownego zainstalowania produktu. Aby przełączyć kanał produktu: odinstaluj istniejący pakiet, ponownie skonfiguruj urządzenie do korzystania z nowego kanału, a następnie postępuj zgodnie z instrukcjami w tym dokumencie, aby zainstalować pakiet z nowej lokalizacji.

Zanotuj swój rozkład i wersję oraz określ najbliższy wpis w obszarze `https://packages.microsoft.com/config/[distro]/`.

W poniższych poleceniach zastąp *wartości [distro]* i *[version]* zidentyfikowanymi informacjami:

> [!NOTE]
> W przypadku redhat, Oracle Linux, Amazon Linux 2 i CentOS 8, zastąp *[distro]* na 'rnog'.

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
                location => "https://packages.microsoft.com/config/${distro}/${version}/prod",
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
                baseurl  => "https://packages.microsoft.com/config/${distro}/${version}/${channel}",
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

Dołącz powyższy manifest do swojej witryny.pp w tym pliku:

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```
```Output
node "default" {
    include install_mdatp
}
```

Urządzenia zarejestrowanego agenta okresowo ankietują serwer Proxy i instalują nowe profile konfiguracji i zasady zaraz po ich wykryciu.

## <a name="monitor-puppet-deployment"></a>Monitorowanie wdrożenia z działaniami w celu monitorowania danych

Na urządzeniu agenta możesz także sprawdzić stan dołączania, uruchamiając program:

```bash
mdatp health
```
```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **licencjonowane**: Potwierdzi to, że urządzenie jest powiązane z Twoją organizacją.

- **orgId**: Jest to identyfikator organizacji usługi Defender for Endpoint.

## <a name="check-onboarding-status"></a>Sprawdź stan dołączania

Możesz sprawdzić, czy urządzenia zostały poprawnie zainstalowane, tworząc skrypt. Na przykład poniższy skrypt sprawdza stan dołączania zarejestrowanych urządzeń:

```bash
mdatp health --field healthy
```

Powyższe polecenie jest drukowane, `1` jeśli produkt jest wnoszony i działa zgodnie z oczekiwaniami.

> [!IMPORTANT]
> Przy pierwszym uruchamianiu produktu są pobierane najnowsze definicje ochrony przed złośliwym kodem. W zależności od połączenia internetowego może to potrwać do kilku minut. W tym czasie powyższe polecenie zwraca wartość `0`.

Jeśli produkt nie jest w dobrej kondycji, kod wyjścia (który `echo $?`można sprawdzić przez ) wskazuje problem:

- 1, jeśli urządzenie nie zostało jeszcze naniesone.
- 3, jeśli nie można nawiązać połączenia z daemonem.

## <a name="log-installation-issues"></a>Problemy z instalacją dziennika

 Aby uzyskać więcej informacji na temat sposobu znalezienia automatycznie wygenerowanego dziennika, który jest tworzony przez instalatora w przypadku wystąpienia błędu, zobacz Problemy z [instalacją dziennika](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>Uaktualnienia systemu operacyjnego

Podczas uaktualniania systemu operacyjnego do nowej wersji głównych należy najpierw odinstalować program Defender for Endpoint dla systemu Linux, zainstalować uaktualnienie, a na koniec ponownie skonfigurować program Defender dla punktu końcowego w systemie Linux na urządzeniu.

## <a name="uninstallation"></a>Dezinstalacja

Tworzenie modułu *podobnego remove_mdatp* do *install_mdatp* z następującą zawartością w *init.pp* w tym pliku:

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
