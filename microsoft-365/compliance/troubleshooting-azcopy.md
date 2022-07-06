---
title: Rozwiązywanie problemów z narzędziem AzCopy w usłudze eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Rozwiązywanie problemów z błędami narzędzia Azure AzCopy podczas ładowania danych innych niż Office 365 w celu korygowania błędów w usłudze eDiscovery (Premium).
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 3a74dd5f2a341e9a99cbfc82cfb12900bae42491
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641147"
---
# <a name="troubleshoot-azcopy-in-ediscovery-premium"></a>Rozwiązywanie problemów z narzędziem AzCopy w usłudze eDiscovery (Premium)

Podczas ładowania danych lub dokumentów innych niż microsoft 365 na potrzeby korygowania błędów w Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) interfejs użytkownika dostarcza polecenie azure AzCopy zawierające parametry z lokalizacją, w której są przechowywane pliki, które chcesz przekazać, oraz lokalizację magazynu platformy Azure, do której zostaną przekazane pliki. Aby przekazać dokumenty, skopiuj to polecenie, a następnie uruchom je w wierszu polecenia na komputerze lokalnym.  Poniższy zrzut ekranu przedstawia przykład polecenia narzędzia AzCopy:

![Przekazywanie plików innych niż Microsoft 365.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

Zwykle podane polecenie działa podczas jego uruchamiania. Jednak mogą wystąpić przypadki, gdy wyświetlane polecenie nie zostanie pomyślnie uruchomione. Oto kilka możliwych powodów.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>Obsługiwana wersja narzędzia AzCopy nie jest zainstalowana na komputerze lokalnym

W tej chwili należy użyć narzędzia AzCopy w wersji 8.1, aby załadować dane spoza platformy Microsoft 365 w środowisku eDiscovery (Premium). Polecenie AzCopy wyświetlane na stronie **Przekazywanie plików** pokazane na poprzednim zrzucie ekranu zwraca błąd, jeśli nie używasz narzędzia AzCopy w wersji 8.1. Aby zainstalować tę wersję, zobacz [Transferowanie danych za pomocą narzędzia AzCopy w wersji 8.1 w systemie Windows](/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>Narzędzie AzCopy nie jest zainstalowane na komputerze lokalnym lub nie jest zainstalowane w lokalizacji domyślnej

Jeśli narzędzie AzCopy nie jest zainstalowane lub jest zainstalowane w lokalizacji innej niż domyślna lokalizacja instalacji (czyli `%ProgramFiles(x86)%`), podczas uruchamiania polecenia AzCopy może zostać wyświetlony następujący błąd:

> System nie może odnaleźć określonej ścieżki.

Jeśli narzędzie AzCopy nie jest zainstalowane na komputerze lokalnym, informacje o instalacji można znaleźć w [temacie Transfer data with the AzCopy v8.1 on Windows (Przesyłanie danych za pomocą narzędzia AzCopy v8.1 w systemie Windows](/previous-versions/azure/storage/storage-use-azcopy)). Pamiętaj, aby zainstalować go w lokalizacji domyślnej.

Jeśli narzędzie AzCopy jest zainstalowane, ale jest zainstalowane w lokalizacji innej niż lokalizacja domyślna, możesz skopiować polecenie, wkleić je do pliku tekstowego, a następnie zmienić ścieżkę do lokalizacji, w której zainstalowano narzędzie AzCopy. Jeśli na przykład narzędzie Azcopy znajduje się w `%ProgramFiles%`programie , możesz zmienić pierwszą część polecenia z `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` na `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`. Po wprowadzeniu tej zmiany skopiuj ją z pliku tekstowego, a następnie uruchom wiersz polecenia.

> [!TIP]
> Jeśli narzędzie AzCopy jest zainstalowane w lokalizacji innej niż domyślna lokalizacja instalacji, rozważ odinstalowanie go, a następnie ponowne zainstalowanie go w lokalizacji domyślnej. Pomoże to zapobiec temu problemowi w przyszłości.