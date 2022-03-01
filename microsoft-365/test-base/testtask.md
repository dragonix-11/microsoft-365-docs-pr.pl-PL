---
title: Ustawianie zadań testowych
description: Ustawianie zadań testowych
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 8255cadfa77dec222527c79caf4d8737abfe2b8c
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016015"
---
# <a name="step-4-the-tasks-tab"></a>Krok 4. Karta Zadania

Na karcie zadania powinny być dostępne ścieżki do skryptów testowych, które znajdują się w folderze zip przekazanym na karcie binaries.

  - **Out of Box Test Scripts:** Wpisz względne ścieżki instalacji, uruchamiania, zamykania i odinstalowywania skryptów. Możesz także wybrać dodatkowe ustawienia dla skryptu instalacji.
  - **Skrypty testowania funkcjonalności:** Wpisz ścieżkę względną do każdego przekazanego skryptu testu funkcjonalnego. Za pomocą tego przycisku można dodać dodatkowe skrypty testów ```Add Script``` funkcjonalnych. Potrzebujesz co najmniej jednego (1) skryptu i możesz dodać maksymalnie osiem (8) skryptów testów funkcjonalnych. 
  
    Skrypty są uruchamiane w podanej kolejności. Błąd w określonym skryptze zatrzymuje wykonywanie kolejnych skryptów.
    Możesz także wybrać dodatkowe ustawienia dla każdego skryptu.

## <a name="set-script-path"></a>Ustawianie ścieżki skryptu

![Obraz zadania testowego.](Media/testtask.png)

Przykład sposobu zapewnienia ścieżki względnej w strukturze folderów znajduje się poniżej:

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1** byłaby. _ScriptX.ps1_ jako ścieżkę względną.
  - **Script.ps1** jako _ścieżkę względną script.ps1folder1/_ folder.


## <a name="next-steps"></a>Następne kroki

Wyświetlanie szczegółów karty Opcje testowania w następnym artykule 
> [!div class="nextstepaction"]
> [Następny krok](testoptions.md)
