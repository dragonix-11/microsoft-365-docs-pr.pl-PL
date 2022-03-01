---
title: Rozwiązywanie problemów z instalacją programu Microsoft Defender dla punktu końcowego w systemie Linux
ms.reviewer: ''
description: Rozwiązywanie problemów z instalacją programu Microsoft Defender dla punktu końcowego w systemie Linux
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, installation
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
ms.openlocfilehash: a0b2a571be5f78818279a343d253709e05814908
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011375"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Rozwiązywanie problemów z instalacją programu Microsoft Defender dla punktu końcowego w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="verify-that-the-installation-succeeded"></a>Sprawdzanie, czy instalacja zakończyła się pomyślnie

Błąd podczas instalacji może, ale nie może spowodować wystąpienia istotnego komunikatu o błędzie przez menedżera pakietu. Aby sprawdzić, czy instalacja się powiedzie, uzyskaj i sprawdź dzienniki instalacji przy użyciu:

```bash
 sudo journalctl --no-pager|grep 'microsoft-mdatp' > installation.log
```

```bash
 grep 'postinstall end' installation.log
```

```Output
 microsoft-mdatp-installer[102243]: postinstall end [2020-03-26 07:04:43OURCE +0000] 102216
```

Dane wyjściowe poprzedniego polecenia z prawidłową datą i godziną instalacji wskazują sukces.

Sprawdź też [konfigurację klienta](linux-install-manually.md#client-configuration) , aby sprawdzić kondycję produktu i wykryć plik tekstowy EICAR.

## <a name="make-sure-you-have-the-correct-package"></a>Upewnij się, że masz poprawny pakiet

Sprawdź, czy instalowany pakiet jest taki jak dystrybucja i wersja hosta.

<br>

****

|pakiet|rozkład|
|---|---|
|mdatp-rtp8. Linux.x86_64.rpm|Oracle, RNOG i CentOS 8.x|
|mdatp-sles12. Linux.x86_64.rpm|SUSE Linux Enterprise Server 12.x|
|mdatp-sles15. Linux.x86_64.rpm|SUSE Linux Enterprise Server 15.x|
|mdatp. Linux.x86_64.rpm|Oracle, R BIBLIOTECE i CentOS 7.x|
|mdatp. Linux.x86_64.deb|Debian i Ubuntu 16.04, 18.04 i 20.04|
|

W [przypadku ręcznego](linux-install-manually.md) wdrożenia upewnij się, że została wybrana właściwa wersja i distro.

## <a name="installation-failed"></a>Instalacja nie powiodła się

Sprawdź, czy usługa Defender for Endpoint jest uruchomiona:

```bash
service mdatp status
```

```Output
 ● mdatp.service - Microsoft Defender for Endpoint
   Loaded: loaded (/lib/systemd/system/mdatp.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-03-26 10:37:30 IST; 23h ago
 Main PID: 1966 (wdavdaemon)
    Tasks: 105 (limit: 4915)
   CGroup: /system.slice/mdatp.service
           ├─1966 /opt/microsoft/mdatp/sbin/wdavdaemon
           ├─1967 /opt/microsoft/mdatp/sbin/wdavdaemon
           └─1968 /opt/microsoft/mdatp/sbin/wdavdaemon
 ```

## <a name="steps-to-troubleshoot-if-the-mdatp-service-isnt-running"></a>Procedura rozwiązywania problemów z nieuprawnianą usługą MDATP

1. Sprawdź, czy użytkownik "mdatp" istnieje:

    ```bash
    id "mdatp"
    ```

    Jeśli nie ma żadnych danych wyjściowych, uruchom

    ```bash
    sudo useradd --system --no-create-home --user-group --shell /usr/sbin/nologin mdatp
    ```

2. Spróbuj w włączanie i ponowne uruchamianie usługi przy użyciu:

    ```bash
    sudo service mdatp start
    ```

    ```bash
    sudo service mdatp restart
    ```

3. Jeśli po uruchomieniu poprzedniego polecenia nie zostanie odnaleziony plik mdatp.service, uruchom polecenie:

    ```bash
    sudo cp /opt/microsoft/mdatp/conf/mdatp.service <systemd_path> 
    ```

    gdzie `<systemd_path>` jest `/lib/systemd/system` dla dystrybucji Ubuntu i Debian oraz /usr/lib/systemd/system' dla R ubuntu, CentOS, Oracle i SLES. Następnie ponownie uruchomić krok 2.

4. Jeśli powyższe czynności nie zadziałają, sprawdź, czy zainstalowano program SELinux i w trybie wymuszania. Jeśli tak, spróbuj ją zmienić na tryb permisywny (najlepiej) lub wyłączony. Można to zrobić przez ustawienie `SELINUX` w pliku parametru wartości "permisive" lub "disabled" `/etc/selinux/config` (wyłączone), a następnie ponowne uruchomienie. Aby uzyskać więcej szczegółowych informacji, zajrzyj do man-page of selinux.
Teraz spróbuj ponownie uruchomić usługę MDATP, korzystając z kroku 2. Natychmiast przywróć zmianę konfiguracji ze względów bezpieczeństwa po jej wypróbowaniu i ponownym uruchomieniu.

5. Jeśli `/opt` katalog jest linkiem symbolicznym, utwórz link bind dla `/opt/microsoft`.

6. Upewnij się, że daemon ma wykonywalne uprawnienia.

    ```bash
    ls -l /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    ```Output
    -rwxr-xr-x 2 root root 15502160 Mar  3 04:47 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    Jeśli daemon nie ma uprawnień wykonywalnych, udostępnij go jako wykonywalny przy użyciu:

    ```bash
    sudo chmod 0755 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    i ponownie spróbuj wykonać krok 2.

7. Upewnij się, że system plików zawierający plik wdavdaemon nie jest montowany z wartością "noexec".

## <a name="if-the-defender-for-endpoint-service-is-running-but-the-eicar-text-file-detection-doesnt-work"></a>Jeśli usługa Defender for Endpoint jest uruchomiona, ale wykrywanie pliku tekstowego EICAR nie działa

1. Sprawdź typ systemu plików przy użyciu:

    ```bash
    findmnt -T <path_of_EICAR_file>
    ```

    Tutaj wymieniono obecnie obsługiwane systemy plików dla działań przy [dostępie](microsoft-defender-endpoint-linux.md#system-requirements). Pliki spoza tych systemów plików nie będą skanowane.

## <a name="command-line-tool-mdatp-isnt-working"></a>Narzędzie wiersza polecenia "mdatp" nie działa

1. Jeśli uruchomienie narzędzia wiersza polecenia powoduje `mdatp` błąd `command not found`, uruchom następujące polecenie:

    ```bash
    sudo ln -sf /opt/microsoft/mdatp/sbin/wdavdaemonclient /usr/bin/mdatp
    ```

    i spróbuj ponownie.

    Jeśli żaden z powyższych kroków nie pomoże, zbierz dzienniki diagnostyczne:

    ```bash
    sudo mdatp diagnostic create
    ```

    ```Output
    Diagnostic file created: <path to file>
    ```

    Ścieżka do pliku zip zawierającego dzienniki zostanie wyświetlona jako wynik. Za pomocą tych dzienników możesz się z działem pomocy technicznej  mamy do ręki.
