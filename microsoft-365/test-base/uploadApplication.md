---
title: Przekazywanie pakietu
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
ms.openlocfilehash: cd0d463e234c439d8b57576375fd6a91e512f753
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995291"
---
# <a name="upload-your-test-base-package-zip"></a>Przekaż pakiet usługi Test Base (zip) 

Na stronie Portal bazy testów przejdź do opcji **Nowy pakiet** na lewym pasku nawigacyjnym, a następnie kliknij pozycję **Starsze środowisko przekazywania** , aby włączyć środowisko przekazywania zip, jak pokazano poniżej:

:::image type="content" alt-text="Upload nowy pakiet." source="Media/testapplication01.png" lightbox="Media/testapplication01.png":::

:::image type="content" alt-text="Zastosuj operację." source="Media/testapplication21.png" lightbox="Media/testapplication21.png":::

W tym miejscu wykonaj poniższe kroki, aby przekazać nowy pakiet.

## <a name="enter-details-for-your-package"></a>Wprowadź szczegóły pakietu

Na karcie Szczegóły testu wpisz nazwę, wersję i inne szczegóły pakietu zgodnie z żądaniem.

**Testowanie gotowe do użycia** i **funkcjonalne** można wykonać za pośrednictwem tego pulpitu nawigacyjnego.

Poniższe kroki zawierają przewodnik po sposobie wypełniania szczegółów pakietu:

1. Wprowadź nazwę, która ma zostać nadana pakietowi `Package name` w polu.

    > [!NOTE]
    > Wprowadzona kombinacja nazwy pakietu i wersji musi być unikatowa w organizacji. Jest to weryfikowane przez znacznik wyboru, jak pokazano poniżej.

    - Jeśli zdecydujesz się ponownie użyć nazwy pakietu, numer wersji musi być unikatowy (czyli nigdy nie był używany z pakietem o tej konkretnej nazwie).

    - Jeśli kombinacja nazwy pakietu i wersji nie przejdzie sprawdzania unikatowości, zostanie wyświetlony komunikat o błędzie z komunikatem *"Pakiet z tą wersją pakietu już istnieje"*.

    :::image type="content" alt-text="Obraz przedstawiający przekazywanie instrukcji dotyczących pakietu." source="Media/Instructions.png":::

2. Wprowadź wersję w polu "Wersja pakietu".

    :::image type="content" alt-text="Wersja pakietu." source="Media/ApplicationVersion.png":::

3. Wybierz typ testu, który chcesz uruchomić w tym pakiecie.

    Test **out-of-box (OOB)** wykonuje *instalację*, *uruchamianie*, *zamykanie* i *odinstalowywanie* pakietu. Po zainstalowaniu procedura zamykania uruchamiania jest powtarzana 30 razy przed uruchomieniem pojedynczego odinstalowywania.

    Ten test OOB zapewnia ustandaryzowane dane telemetryczne w pakiecie do porównania między Windows kompilacjami.

    **Test funkcjonalny** umożliwia wykonanie przekazanych skryptów testowych w pakiecie. Skrypty są uruchamiane w sekwencji przekazywania, a niepowodzenie w określonym skryptzie spowoduje zatrzymanie wykonywania kolejnych skryptów.

    > [!NOTE]
    > **Wszystkie** skrypty są uruchamiane najwyżej przez 80 minut.

4. Wybierz typ aktualizacji systemu operacyjnego.

    - "Aktualizacje zabezpieczeń" umożliwiają testowanie pakietu pod kątem przyrostowych zmian Windows miesięcznych aktualizacji zabezpieczeń w wersji wstępnej.
    - "Aktualizacje funkcji" umożliwiają testowanie pakietu pod kątem Windows kompilacji corocznych aktualizacji funkcji w wersji wstępnej z programu Windows Insider Program.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Typ aktualizacji systemu operacyjnego." source="Media/OSUpdateType.png":::

5. Wybierz wersje systemu operacyjnego dla testów aktualizacji zabezpieczeń.

    Na liście rozwijanej Wielokrotne wybieranie wybierz wersje systemu operacyjnego Windows pakiet zostanie zainstalowany.

    - Aby przetestować pakiet tylko w systemach operacyjnych Windows Client, wybierz odpowiednią Windows wersje systemu operacyjnego klienta z listy menu.
    - Aby przetestować pakiet tylko w systemach operacyjnych Windows Server, wybierz odpowiednie wersje systemu operacyjnego serwera Windows z listy menu.
    - Aby przetestować pakiet w systemach operacyjnych Windows Client i Windows Server, wybierz z listy menu wszystkie odpowiednie systemy operacyjne.

    > [!NOTE]
    > Jeśli wybierzesz opcję testowania pakietu zarówno w systemach operacyjnych serwera, jak i klienta, upewnij się, że pakiet jest zgodny i może działać w obu systemach operacyjnych

    :::image type="content" alt-text="Wybieranie wersji systemu operacyjnego." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Wybierz opcje testów aktualizacji funkcji:

    - Z opcją "Wybierz kanał niejawnych testów" wybierz `Windows Insider Program Channel` kompilację , pod którą pakiety powinny być testowane.

      Obecnie używamy kompilacji, które zostały uruchomione w kanale testerów wersji beta.

    - Z opcją "Wybierz punkt odniesienia systemu operacyjnego dla szczegółowych informacji" wybierz wersję systemu operacyjnego Windows, która ma być używana jako punkt odniesienia podczas porównywania wyników testu.

    > [!NOTE]
    > Obecnie nie obsługujemy testowania aktualizacji funkcji dla systemów operacyjnych serwera
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Testowanie aktualizacji funkcji." source="Media/FeatureUpdate.png":::

7. Ukończona strona Szczegóły testu powinna wyglądać następująco:

    :::image type="content" alt-text="Wyświetlanie szczegółów testu." source="Media/TestDetails.png":::

## <a name="next-steps"></a>Następne kroki

W następnym artykule opisano przekazywanie plików binarnych do naszej usługi.

> [!div class="nextstepaction"]
> [Następny krok](binaries.md)

<!---
Add button for next page
-->
