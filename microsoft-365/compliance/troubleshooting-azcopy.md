---
title: Rozwiązywanie problemów z azCopy w programie Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Rozwiązywanie problemów dotyczących narzędzia Azure AzCopy podczas ładowania danych niezwiązanych Office 365 w celu korygowania błędów w Advanced eDiscovery.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 45f82482f92e740383eca774671f1abd55535675
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984601"
---
# <a name="troubleshoot-azcopy-in-advanced-ediscovery"></a>Rozwiązywanie problemów z azCopy w programie Advanced eDiscovery

Podczas ładowania danych lub dokumentów innych niż Microsoft 365 w celu korygowania błędów w programie Advanced eDiscovery interfejs użytkownika dostarcza polecenie Azure AzCopy zawierające parametry z lokalizacją przechowywania plików, które chcesz przekazać, i lokalizacją przechowywania danych platformy Azure, do której mają być przekazywane pliki. Aby przekazać dokumenty, skopiuj to polecenie, a następnie uruchom je w wierszu polecenia na komputerze lokalnym.  Na poniższym zrzucie ekranu przedstawiono przykład polecenia AzCopy:

![Upload pliki Microsoft 365 inne niż pliki.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

Zwykle po uruchomieniu działa podane polecenie. Jednak w niektórych przypadkach wyświetlane polecenie nie zostanie uruchomione pomyślnie. Oto kilka możliwych przyczyn.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>Obsługiwana wersja aplikacji AzCopy nie jest zainstalowana na komputerze lokalnym

Obecnie należy użyć programu AzCopy w wersji 8.1, aby załadować dane inne niż Microsoft 365 w programie Advanced eDiscovery. Polecenie AzCopy wyświetlane na stronie plików Upload przedstawionym  na poprzednim zrzucie ekranu zwraca błąd, jeśli nie korzystasz z programu AzCopy w wersji 8.1. Aby zainstalować tę wersję, zobacz [Przenoszenie danych za pomocą programu AzCopy w wersji 8.1](/previous-versions/azure/storage/storage-use-azcopy) na Windows.

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy nie jest zainstalowany na komputerze lokalnym lub nie jest zainstalowany w lokalizacji domyślnej

Jeśli azCopy nie jest zainstalowany lub jest zainstalowany w lokalizacji innej niż domyślna lokalizacja instalacji ( `%ProgramFiles(x86)%`czyli ), po uruchomieniu polecenia AzCopy może zostać wyświetlony następujący błąd:

> System nie może znaleźć określonej ścieżki.

Jeśli azCopy nie jest zainstalowane na komputerze lokalnym, informacje o instalacji można znaleźć w tece Przenoszenie danych za pomocą programu [AzCopy w wersji 8.1](/previous-versions/azure/storage/storage-use-azcopy) na komputerze Windows. Pamiętaj, aby zainstalować go w lokalizacji domyślnej.

Jeśli zainstalowana aplikacja AzCopy jest zainstalowana, ale jest zainstalowana w lokalizacji innej niż lokalizacja domyślna, możesz skopiować polecenie, wkleić je do pliku tekstowego, a następnie zmienić ścieżkę do lokalizacji, w której jest zainstalowana aplikacja AzCopy. Jeśli na przykład azcopy znajduje `%ProgramFiles%`się w programie , można zmienić pierwszą część polecenia z na `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`. Po wymuseniu tej zmiany skopiuj ją z pliku tekstowego, a następnie uruchom wiersz polecenia.

> [!TIP]
> Jeśli azCopy jest zainstalowany w innej lokalizacji, to domyślną lokalizację instalacji, rozważ jej odinstalowanie, a następnie ponowne zainstalowanie w lokalizacji domyślnej. Pozwoli to zapobiec temu problemowi w przyszłości.