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
ms.openlocfilehash: 23c21eae9ad149aea5442c0c8a00f716f3d22506
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099482"
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



## <a name="upload-your-binaries-dependencies-and-scripts"></a>Upload plików binarnych, zależności i skryptów

Na tej karcie przekażesz pojedynczy pakiet zip zawierający pliki binarne, zależności i skrypty używane do uruchamiania pakietu testów.

> [!NOTE]
> Rozmiar pakietu zip powinien wynosić od co najmniej 10 MB do maksymalnie 2 GB.

**plik zip pakietu Upload**

:::image type="content" alt-text="Upload plików binarnych." source="Media/AddBinaries.png":::

  - Przekazane zależności mogą obejmować platformy testowe, aparaty skryptów lub dane, które będą dostępne do uruchamiania aplikacji lub przypadków testowych. Na przykład możesz przekazać narzędzie Selenium i instalator sterownika internetowego, aby ułatwić uruchamianie testów opartych na przeglądarce.
  - Najlepszym rozwiązaniem jest zapewnienie, że działania skryptu są przechowywane modułowe, tj. 
    - Skrypt `Install` wykonuje tylko operacje instalacji.
    - Skrypt `Launch` uruchamia tylko aplikację.
    - Skrypt `Close` zamyka tylko aplikację.
    - Opcjonalny `Uninstall` skrypt odinstalowuje tylko aplikację.

**Obecnie portal obsługuje tylko skrypty programu PowerShell.**



## <a name="the-tasks-tab"></a>Karta Zadania

Na karcie Zadania powinny zostać wyświetlone ścieżki do skryptów testowych, które znajdują się w folderze zip przekazanym na karcie pliki binarne.

  - **Skrypty testowe out of box:** Wpisz względne ścieżki do skryptów instalacji, uruchamiania, zamykania i odinstalowywania. Możesz również wybrać dodatkowe ustawienia skryptu instalacji.
  - **Skrypty testów funkcjonalnych:** Wpisz ścieżkę względną do każdego przekazanego skryptu testu funkcjonalnego. Dodatkowe skrypty testów funkcjonalnych można dodać za pomocą przycisku ```Add Script``` . Potrzebujesz co najmniej jednego skryptu (1) i możesz dodać do ośmiu (8) skryptów testów funkcjonalnych. 
  
    Skrypty są uruchamiane w sekwencji, w jakiej są wyświetlane. Błąd w określonym skryptzie uniemożliwia wykonywanie kolejnych skryptów.
    Masz również możliwość wybrania dodatkowych ustawień dla każdego dostarczonego skryptu.

**Ustawianie ścieżki skryptu**

:::image type="content" alt-text="Obraz zadania testowego." source="Media/testtask.png":::

Poniżej przedstawiono przykład sposobu podawania ścieżki względnej w strukturze folderów:

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1** . _ScriptX.ps1_ jako ścieżkę względną.
  - **Script.ps1** będzie mieć _folder1/script.ps1_ jako ścieżkę względną.



## <a name="choose-your-test-options"></a>Wybierz opcje testu. 

Karta jest dostępna ```Test Options``` dla użytkowników, którzy chcą wykonać testy funkcjonalne, aby wskazać, kiedy poprawka Windows Update powinna zostać zastosowana w sekwencji wykonywania skryptów testów funkcjonalnych.

:::image type="content" alt-text="Obraz przedstawiający opcje testowania. Testy out-of-box lub funkcjonalne." source="Media/testoptions.png":::

Wybierz pozycję _**Przejrzyj**_ , aby przejść do następnej karty i przejrzeć wybrane opcje testu.



## <a name="review-your-selections-to-create-your-package"></a>Przejrzyj wybrane opcje, aby utworzyć pakiet.

1. Na tej karcie usługa wyświetla szczegóły testu i uruchamia szybkie sprawdzanie kompletności.

    Komunikat **walidacji zakończony niepowodzeniem** lub **Weryfikacja** pokazuje, czy można przejść do następnych kroków, czy nie.

2. Przejrzyj szczegóły testu i jeśli są spełnione, kliknij przycisk **Utwórz** .

    :::image type="content" alt-text="Wyświetl walidację." source="Media/validation.png" lightbox="Media/validation.png":::

3. Spowoduje to dołączenie pakietu do środowiska Bazy testów. Jeśli pakiet zostanie pomyślnie utworzony, zostanie wyzwolony zautomatyzowany test sprawdzający, czy pakiet można pomyślnie wykonać na platformie Azure.

    :::image type="content" alt-text="Pomyślny wynik." source="Media/successful.png":::

    > [!NOTE]
    > Otrzymasz powiadomienie z Azure Portal, aby powiadomić Cię o powodzeniu lub niepowodzeniu weryfikacji pakietu.
    >
    > Należy pamiętać, że proces może potrwać do 24 godzin, dlatego prawdopodobnie przekroczą limit czasu strony internetowej, jeśli nie jesteś na niej aktywny, dlatego powiadomienie nie poinformuje Cię o zakończeniu tego przebiegu na żądanie.

    - W takim przypadku możesz wyświetlić stan pakietu na karcie **Zarządzanie pakietami** .

      :::image type="content" alt-text="Obraz do zarządzania pakietami." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - W przypadku pomyślnych testów ich wyniki można wyświetlić za pośrednictwem stron **Podsumowanie testu**, **Wyniki aktualizacji zabezpieczeń** i **Wyniki aktualizacji funkcji** w zaplanowanych odstępach czasu, często rozpoczynających się kilka dni po przekazaniu.
  
    - Testy zakończone niepowodzeniem wymagają przekazania nowego pakietu. 

      **Dzienniki testów** można pobrać w celu dalszej analizy ze stron **wyników aktualizacji zabezpieczeń** i wyników **aktualizacji funkcji**.

    - Jeśli wystąpią powtarzające się błędy testu, skontaktuj się z testbasepreview@microsoft.com ze szczegółowymi informacjami o błędzie.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z naszymi wytycznymi dotyczącymi zawartości, korzystając z poniższego linku.

> [!div class="nextstepaction"]
> [Następny krok](contentguideline.md)
