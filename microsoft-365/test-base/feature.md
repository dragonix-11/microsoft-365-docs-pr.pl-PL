---
title: Sprawdzanie poprawności aktualizacji funkcji
description: Szczegółowe informacje na temat przekazywania aplikacji do sprawdzania poprawności aktualizacji funkcji
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
ms.openlocfilehash: f6e7cfffb92f64d92a4ad68d93d1d51dccc0f4bb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988350"
---
# <a name="windows-feature-update-validation"></a>Windows sprawdzania poprawności aktualizacji funkcji

Potrzebujesz szczegółowych informacji o tym, jak będą działać Twoje aplikacje w następnej wersji programu Windows 10 lub Windows 11 — bez utrzymywania środowiska w celu weryfikacji nowych Windows funkcji? 

Chcesz uruchomić testy poprawności dla kompilacji niejawnego programu testów Windows w naszym środowisku platformy Azure?

**Sprawdzanie poprawności aktualizacji** funkcji w bazie testowej dla M365 może pomóc Ci osiągnąć wszystko to i nie tylko!

Zapoznaj się z poniższym konspektem krok po kroku, aby dowiedzieć się, jak uzyskać dostęp do tej nowej funkcji w bazie testowej dla usługi M365.

Aby rozpocząć pracę w ```Feature update validation``` bazie testowej dla M365, przekaż aplikacje (i powiązane pliki) za pośrednictwem portalu samoobsługowego. 

Poniżej wyróżnione są czynności, które należy wykonać podczas wypełniania szczegółów **testu**:

1. Wybierz **pozycję Aktualizacja funkcji** jako typ aktualizacji systemu operacyjnego:

![Typ systemu operacyjnego sprawdzania poprawności aktualizacji funkcji.](Media/Feature-update-validation-01.png)

2. Wybierz kanał niejawnego programu Windows, dla którego chcesz zweryfikować aplikację.  

![Sprawdzanie poprawności aktualizacji funkcji. Wybieranie kanału beta niejawnego programu testów.](Media/Feature-update-validation-02.png)

3. Wybierz wersję podstawową pakietu Windows 10 lub Windows 11 jako plan bazowy testu (i wynikowe wnioski!) i podaj inne szczegóły wymagane do pomyślnego dochowania paczki.

![Sprawdzanie poprawności aktualizacji funkcji z wydaną Windows 10 i Windows 11.](Media/Feature-update-validation-03.png)

4. Aby wyświetlić wyniki sprawdzania poprawności aplikacji dla wersji Windows 10 aktualizacji funkcji, odwiedź stronę ```Feature Updates Test Results```.

![Sprawdzanie poprawności aktualizacji funkcji umożliwia szybkie przeglądanie wyników.](Media/Feature-update-validation-04.png)


## <a name="next-steps"></a>Następne kroki

Przejść do następnego artykułu, aby rozpocząć opis analizy regresji pamięci.
> [!div class="nextstepaction"]
> [Następny krok](memory.md)

<!---
Add button for next page
-->
