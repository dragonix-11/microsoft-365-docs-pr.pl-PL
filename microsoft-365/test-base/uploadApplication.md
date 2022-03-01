---
title: Upload swoją paczkę
description: Jak przekazać aplikację, pliki binarne i zależności do bazy testowej
search.appverid: MET150
author: mansipatel-usl
ms.author: rshastri
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 99b25757b3f7b0b3d4fcd43f97bab2ac303de6fa
ms.sourcegitcommit: b1a2b09edbcfcc62ff3f1ecf5bd8adb1afa344c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2021
ms.locfileid: "63018974"
---
# <a name="step-2-uploading-a-package"></a>Krok 2. Przekazanie pakietu

Na stronie Test Base portal (Portal testowy) przejdź do Upload **opcji** nowego pakietu na lewym pasku nawigacyjnym, jak pokazano poniżej:

:::image type="content" alt-text="Upload nową paczkę." source="Media/Upload-New-Package.png" lightbox="Media/Upload-New-Package.png":::

Po dojechu do tej aplikacji wykonaj poniższe czynności, aby przekazać nowy pakiet.

## <a name="enter-details-for-your-package"></a>Wprowadź szczegóły paczki

Na karcie Szczegóły testu wpisz nazwę, wersję i inne szczegóły pakietu zgodnie z żądaniem.

**Testowanie gotowego rozwiązania i** **funkcjonalności** można przetestować za pośrednictwem tego pulpitu nawigacyjnego.

Poniższe kroki zapewniają przewodnik dotyczący wypełniania szczegółów pakietu:

1. W polu wprowadź nazwę, która ma zostać nadana pakietowi `Package name` .

    > [!NOTE]
    > Wprowadzona kombinacja nazwy pakietu i wersji musi być unikatowa w twojej organizacji. Jest on sprawdzany za pomocą znacznika wyboru, jak pokazano poniżej.

    - Jeśli zdecydujesz się użyć ponownie nazwy pakietu, numer wersji musi być unikatowy (to jest nigdy nie używany z wpływem na pakiet o tej konkretnej nazwie).

    - Jeśli kombinacja nazwy pakietu + wersja nie przejdzie kontroli unikatowości, zostanie wyświetlony komunikat o błędzie z komunikatem "Pakiet z tą wersją pakietu *już istnieje"*.

    :::image type="content" alt-text="Obraz instrukcji przekazywania pakietu." source="Media/Instructions.png":::

2. Wprowadź wersję w polu "Wersja pakietu".

    :::image type="content" alt-text="Wersja pakietu." source="Media/ApplicationVersion.png":::

3. Wybierz typ testu, który chcesz uruchomić dla tego pakietu.

    Test **typu "Out-of-Box" (OOB)** wykonuje *instalację*, *uruchamianie*, *zamykanie* i *odinstalowywanie* pakietu. Po zakończeniu instalacji procedura uruchamiania i zamykania jest powtarzana 30 razy, zanim zostanie uruchomione pojedyncze odinstalowanie.

    Ten test OOB udostępnia usterekzowany telemetrię dla Twojego pakietu w celu porównania Windows kompilacji.

    Test **funkcjonalny może** wykonać przekazany skrypty testów na Twoim pakiecie. Skrypty są uruchamiane w sekwencji przekazywania, a niepowodzenie w określonym skrypcie zatrzyma wykonywanie kolejnych skryptów.

    > [!NOTE]
    > **Wszystkie** skrypty są uruchamiane najwyżej przez 80 minut.

4. Wybierz typ aktualizacji systemu operacyjnego.

    - "Aktualizacje zabezpieczeń" umożliwiają przetestowanie Pakietu pod kątem przyrostowych Windows comiesięcznych aktualizacji zabezpieczeń.
    - "Aktualizacje funkcji" umożliwiają przetestowanie Twojego pakietu Windows przed ich wydaniem dwurocznych aktualizacji funkcji z niejawnego programu testów pakietu Windows niejawnego programu testów.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Typ aktualizacji systemu operacyjnego." source="Media/OSUpdateType.png":::

5. Wybierz wersje systemu operacyjnego w testach aktualizacji zabezpieczeń.

    Z listy rozwijanej wielokrotnego wyboru wybierz wersje systemu operacyjnego Windows na których twój pakiet zostanie zainstalowany.

    - Aby przetestować pakiet tylko pod Windows systemami operacyjnymi klienta, wybierz z listy menu odpowiednie Windows o wersjach systemu operacyjnego klienta.
    - Aby przetestować pakiet tylko pod Windows systemami operacyjnymi programu Windows Server, wybierz z listy menu odpowiednie wersje systemu operacyjnego Windows Server.
    - Aby przetestować pakiet pod Windows systemami operacyjnymi client i Windows Server, wybierz z listy menu wszystkie odpowiednie systemy operacyjne.

    > [!NOTE]
    > Jeśli wybierzesz opcję przetestowania pakietu zarówno w przypadku systemu operacyjnego serwera, jak i systemu operacyjnego klienta, upewnij się, że pakiet jest zgodny i może być uruchamiany w obu systemach operacyjnych.

    :::image type="content" alt-text="Wybieranie wersji systemu operacyjnego." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Wybierz opcje testów aktualizacji funkcji:

    - Wybierz opcję "Wybierz kanał niejawnego programu testów" i `Windows Insider Program Channel` wybierz kompilację, pod kątem których powinny być testowane Twoje pakiety.

      Obecnie korzystamy z kompilacji testowych w kanale beta niejawnego programu testów.

    - Przy opcji "Wybierz plan bazowy systemu operacyjnego dla szczegółowych informacji" wybierz wersję systemu Windows, która ma być używana jako plan bazowy podczas porównywania wyników testu.

    > [!NOTE]
    > Obecnie NIE obsługujemy testowania aktualizacji funkcji dla systemu operacyjnego serwera
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Testowanie aktualizacji funkcji." source="Media/FeatureUpdate.png":::

7. Strona Ukończone szczegóły testu powinna wyglądać tak:

    :::image type="content" alt-text="Wyświetlanie szczegółów testu." source="Media/TestDetails.png":::

## <a name="next-steps"></a>Następne kroki

W następnym artykule o mowa przekazywanie danych binralnych do naszej usługi.

> [!div class="nextstepaction"]
> [Następny krok](binaries.md)

<!---
Add button for next page
-->
