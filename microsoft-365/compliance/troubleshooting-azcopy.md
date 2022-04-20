---
title: Rozwiązywanie problemów z narzędziem AzCopy w usłudze eDiscovery (Premium)
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
description: Rozwiązywanie problemów z błędami narzędzia Azure AzCopy podczas ładowania danych innych niż Office 365 w celu korygowania błędów w usłudze eDiscovery (Premium).
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: ed9910df4da310034320ea030c8b5da1c5918e52
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943496"
---
# <a name="troubleshoot-azcopy-in-ediscovery-premium"></a>Rozwiązywanie problemów z narzędziem AzCopy w usłudze eDiscovery (Premium)

Podczas ładowania danych lub dokumentów innych niż Microsoft 365 w celu korygowania błędów w usłudze Microsoft Purview eDiscovery (Premium) interfejs użytkownika udostępnia polecenie azure AzCopy zawierające parametry z lokalizacją przechowywania plików, które chcesz przekazać, oraz lokalizację magazynu platformy Azure, do której zostaną przekazane pliki. Aby przekazać dokumenty, skopiuj to polecenie, a następnie uruchom je w wierszu polecenia na komputerze lokalnym.  Poniższy zrzut ekranu przedstawia przykład polecenia narzędzia AzCopy:

![Upload pliki inne niż Microsoft 365.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

Zwykle podane polecenie działa podczas jego uruchamiania. Jednak mogą wystąpić przypadki, gdy wyświetlane polecenie nie zostanie pomyślnie uruchomione. Oto kilka możliwych powodów.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>Obsługiwana wersja narzędzia AzCopy nie jest zainstalowana na komputerze lokalnym

W tej chwili należy użyć narzędzia AzCopy w wersji 8.1, aby załadować dane inne niż Microsoft 365 w usłudze eDiscovery (Premium). Polecenie AzCopy wyświetlane na stronie **Upload files** wyświetlanej na poprzednim zrzucie ekranu zwraca błąd, jeśli nie używasz narzędzia AzCopy w wersji 8.1. Aby zainstalować tę wersję, zobacz [Transfer data with the AzCopy v8.1 on Windows (Przesyłanie danych za pomocą narzędzia AzCopy w wersji 8.1 na Windows](/previous-versions/azure/storage/storage-use-azcopy)).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>Narzędzie AzCopy nie jest zainstalowane na komputerze lokalnym lub nie jest zainstalowane w lokalizacji domyślnej

Jeśli narzędzie AzCopy nie jest zainstalowane lub jest zainstalowane w lokalizacji innej niż domyślna lokalizacja instalacji (czyli `%ProgramFiles(x86)%`), podczas uruchamiania polecenia AzCopy może zostać wyświetlony następujący błąd:

> System nie może odnaleźć określonej ścieżki.

Jeśli narzędzie AzCopy nie jest zainstalowane na komputerze lokalnym, informacje o instalacji można znaleźć w temacie [Transfer data with the AzCopy v8.1 on Windows (Przesyłanie danych za pomocą narzędzia AzCopy v8.1 na Windows](/previous-versions/azure/storage/storage-use-azcopy)). Pamiętaj, aby zainstalować go w lokalizacji domyślnej.

Jeśli narzędzie AzCopy jest zainstalowane, ale jest zainstalowane w lokalizacji innej niż lokalizacja domyślna, możesz skopiować polecenie, wkleić je do pliku tekstowego, a następnie zmienić ścieżkę do lokalizacji, w której zainstalowano narzędzie AzCopy. Jeśli na przykład narzędzie Azcopy znajduje się w `%ProgramFiles%`programie , możesz zmienić pierwszą część polecenia z `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` na `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`. Po wprowadzeniu tej zmiany skopiuj ją z pliku tekstowego, a następnie uruchom wiersz polecenia.

> [!TIP]
> Jeśli narzędzie AzCopy jest zainstalowane w lokalizacji innej niż domyślna lokalizacja instalacji, rozważ odinstalowanie go, a następnie ponowne zainstalowanie go w lokalizacji domyślnej. Pomoże to zapobiec temu problemowi w przyszłości.