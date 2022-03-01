---
title: Rozwiązywanie problemów z instalacją programu Microsoft Defender dla punktu końcowego na komputerze Mac
description: Rozwiązywanie problemów z instalacją w programie Microsoft Defender dla punktu końcowego na komputerze Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, install
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
ms.openlocfilehash: 5f56e28d472cb3fdf8dd089effcd4beac6e42374
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011417"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Rozwiązywanie problemów z instalacją programu Microsoft Defender for Endpoint w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Program Microsoft Defender for Endpoint w systemie macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="installation-failed"></a>Instalacja nie powiodła się

W przypadku instalacji ręcznej na stronie Podsumowanie kreatora instalacji jest wyświetlany komunikat "Wystąpił błąd podczas instalacji. Instalator napotkał błąd, który powodował niepowodzenie instalacji. Aby uzyskać pomoc, skontaktuj się z wydawcą oprogramowania". W przypadku wdrożeń MDM jest on również wyświetlany jako błąd instalacji ogólnej.

Chociaż użytkownikowi końcoweowi nie jest wyświetlany dokładny błąd, plik dziennika jest nadal wyświetlany z postępem instalacji w `/Library/Logs/Microsoft/mdatp/install.log`. Każda sesja instalacji jest dołączana do tego pliku dziennika. Możesz użyć tylko `sed` do wyprowadzić ostatniej sesji instalacji:

```bash
sed -n 'H; /^preinstall com.microsoft.wdav begin/h; ${g;p;}' /Library/Logs/Microsoft/mdatp/install.log
```
```Output
preinstall com.microsoft.wdav begin [2020-03-11 13:08:49 -0700] 804
INSTALLER_SECURE_TEMP=/Library/InstallerSandboxes/.PKInstallSandboxManager/CB509765-70FC-4679-866D-8A14AD3F13CC.activeSandbox/89FA879B-971B-42BF-B4EA-7F5BB7CB5695
correlation id=CB509765-70FC-4679-866D-8A14AD3F13CC
[ERROR] Downgrade from 100.88.54 to 100.87.80 is not permitted
preinstall com.microsoft.wdav end [2020-03-11 13:08:49 -0700] 804 => 1
```

W tym przykładzie rzeczywista przyczyna jest poprzedzona prefiksem `[ERROR]`.
Instalacja nie powiodła się, ponieważ starszą wersję tych wersji nie jest obsługiwana.

## <a name="mdatp-install-log-missing-or-not-updated"></a>Brakuje dziennika instalacji MDATP lub nie zaktualizowano go

W rzadkich przypadkach instalacja nie pozostawia śladów w pliku /Library/Logs/Microsoft/mdatp/install.log usługi MDATP.
Najpierw sprawdź, czy instalacja się wydarzyła. Następnie przeanalizuj możliwe błędy, zapytaniając dzienniki systemu macOS. Warto to zrobić we wdrożeniach usługi MDM, gdy nie ma interfejsu użytkownika klienta. Zalecamy używanie wąskiego okna czasowego do uruchamiania kwerendy i filtrowania według nazwy procesu rejestrowania, ponieważ będzie ona zawierała ogromną ilość informacji.

```bash
grep '^2020-03-11 13:08' /var/log/install.log
```
```Output
log show --start '2020-03-11 13:00:00' --end '2020-03-11 13:08:50' --info --debug --source --predicate 'processImagePath CONTAINS[C] "install"' --style syslog
```
