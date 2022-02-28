---
title: Upload binaries aplikacji
description: Jak rozpocząć korzystanie z bazy testowej dla M365
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
ms.openlocfilehash: 200da9ca73bc666f3f11fc3fda95493d2c0954fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985286"
---
# <a name="step-3-upload-your-binaries-dependencies-and-scripts"></a>Krok 3. Upload urządzeniach binralnych, zależności i skryptach

Na tej karcie możesz przekazać pojedynczy pakiet zip zawierający pliki binarne, zależności i skrypty używane do uruchamiania pakietu testowego.

> [!NOTE]
> Rozmiar pakietu zip powinien być od co najmniej 10 MB do maksymalnie 2 GB.

## <a name="upload-package-zip-file"></a>Upload zip pakietu

:::image type="content" alt-text="Upload urządzeniach binralnych." source="Media/AddBinaries.png":::

  - Przekazane zależności mogą obejmować struktury testowe, aparaty skryptów lub dane, do których będzie można uzyskiwać dostęp w celu uruchamiania aplikacji lub przypadków testowania. Na przykład możesz przekazać plik Selenium i instalatora sterownika sieci Web, aby ułatwić uruchamianie testów opartych na przeglądarce.
  - Najlepszym rozwiązaniem jest zapewnienie modułowych działań skryptów, czyli. 
    - Skrypt `Install` wykonuje tylko operacje instalacji.
    - Skrypt `Launch` uruchamia tylko aplikację.
    - Skrypt `Close` zamyka tylko aplikację.
    - Opcjonalny skrypt `Uninstall` odinstalowuje tylko aplikację.

**Obecnie portal obsługuje tylko skrypty programu PowerShell.**


## <a name="next-steps"></a>Następne kroki 

Przejdź do następnego artykułu, aby przejść do kroku 4: **Ustawianie zadań testowych**.
> [!div class="nextstepaction"]
> [Przejdź wstecz](uploadApplication.md)
> [!div class="nextstepaction"]
> [Następny krok](testtask.md)

