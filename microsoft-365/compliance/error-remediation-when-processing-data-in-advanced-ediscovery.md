---
title: Korygowanie błędów podczas przetwarzania danych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Dowiedz się, jak za pomocą korygowania błędów rozwiązywać problemy z danymi w usłudze eDiscovery (Premium), które mogą uniemożliwić prawidłowe przetwarzanie zawartości.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: e119458281a81ab41f8034ce76e65a5946536204
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093114"
---
# <a name="error-remediation-when-processing-data"></a>Korygowanie błędów podczas przetwarzania danych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Korygowanie błędów umożliwia administratorom zbierania elektronicznych materiałów dowodowych rozwiązywanie problemów z danymi, które uniemożliwiają prawidłowe przetwarzanie zawartości w usłudze Microsoft Purview eDiscovery (Premium). Na przykład nie można przetwarzać plików chronionych hasłem, ponieważ pliki są zablokowane lub szyfrowane. Korzystając z korygowania błędów, administratorzy zbierania elektronicznych materiałów dowodowych mogą pobierać pliki z takimi błędami, usuwać ochronę haseł, a następnie przekazywać skorygowane pliki.

Użyj następującego przepływu pracy, aby korygować pliki z błędami w przypadkach zbierania elektronicznych materiałów dowodowych (Premium).

## <a name="create-an-error-remediation-session-to-remediate-files-with-processing-errors"></a>Tworzenie sesji korygowania błędów w celu skorygowania plików z błędami przetwarzania

> [!NOTE]
> Jeśli kreator korygowania błędów zostanie zamknięty w dowolnym momencie podczas poniższej procedury, możesz powrócić do sesji korygowania błędów na karcie **Przetwarzanie** , wybierając pozycję **Korygowania** w menu rozwijanym **Widok** .

1. Na karcie **Przetwarzanie** w przypadku zbierania elektronicznych materiałów dowodowych (Premium) wybierz pozycję **Błędy** w menu rozwijanym **Widok**, a następnie wybierz zestaw przeglądów lub cały przypadek z menu rozwijanego **Zakres**. W tej sekcji są wyświetlane wszystkie błędy z przypadku lub błędu z określonego zestawu przeglądów.

   ![Błąd podczas korygowania.](../media/8c2faf1a-834b-44fc-b418-6a18aed8b81a.png)

2. Wybierz błędy, które chcesz skorygować, klikając przycisk radiowy obok typu błędu lub typu pliku.  W poniższym przykładzie korygujemy plik chroniony hasłem.

3. Kliknij pozycję **Nowe korygowanie błędów**.

    Przepływ pracy korygowania błędów rozpoczyna się od etapu przygotowania, w którym pliki z błędami są kopiowane do lokalizacji Storage platformy Azure dostarczonej przez firmę Microsoft, aby można było je pobrać na komputer lokalny w celu skorygowania.

    ![Przygotowywanie korygowania błędów.](../media/390572ec-7012-47c4-a6b6-4cbb5649e8a8.png)

4. Po zakończeniu przygotowywania kliknij przycisk **Dalej: Pobierz pliki** , aby kontynuować pobieranie.

    ![Pobierz pliki.](../media/6ac04b09-8e13-414a-9e24-7c75ba586363.png)

5. Aby pobrać pliki, określ **ścieżkę docelową do pobrania**. Jest to ścieżka do folderu nadrzędnego na komputerze lokalnym, na którym zostanie pobrany plik.  Ścieżka domyślna %USERPROFILE%\Downloads\errors wskazuje folder pobierania zalogowanego użytkownika. W razie potrzeby możesz zmienić tę ścieżkę. Jeśli ją zmienisz, zalecamy użycie lokalnej ścieżki pliku w celu osiągnięcia najlepszej wydajności. Nie używaj ścieżki sieci zdalnej. Na przykład można użyć ścieżki **C:\Korygowanie**.

   Ścieżka do folderu nadrzędnego jest automatycznie dodawana do polecenia AzCopy (jako wartość **/Dest** parametru).

6. Skopiuj wstępnie zdefiniowane polecenie, klikając pozycję **Kopiuj do schowka**. Otwórz wiersz polecenia Windows, wklej polecenie AzCopy, a następnie naciśnij **klawisz Enter**.

    ![Przygotuj się do korygowania błędów.](../media/f364ab4d-31c5-4375-b69f-650f694a2f69.png)

    > [!NOTE]
    > Aby pomyślnie użyć polecenia udostępnionego na stronie **Pobieranie plików** , należy użyć narzędzia AzCopy w wersji 8.1. Aby przekazać pliki w kroku 10, należy również użyć narzędzia AzCopy w wersji 8.1. Aby zainstalować tę wersję narzędzia AzCopy, zobacz [Transfer data with the AzCopy v8.1 on Windows (Przesyłanie danych za pomocą narzędzia AzCopy w wersji 8.1 na Windows](/previous-versions/azure/storage/storage-use-azcopy)). Jeśli podane polecenie narzędzia AzCopy nie powiedzie się, zobacz [Rozwiązywanie problemów z narzędziem AzCopy w sekcji eDiscovery (Premium)](troubleshooting-azcopy.md).

    Wybrane pliki są pobierane do lokalizacji określonej w kroku 5. W folderze nadrzędnym (na przykład **C:\Remediation**) zostanie automatycznie utworzona następująca struktura podfolderu:

    `<Parent folder>\Subfolder 1\Subfolder 2\<file>`

    - *Podfolder 1* ma nazwę z identyfikatorem przypadku lub zestawem przeglądów, w zależności od zakresu wybranego w kroku 1.

    - *Podfolder 2* ma nazwę z identyfikatorem pliku pobranego pliku

    - Pobrany plik znajduje się w *podfoldecie 2* i ma również nazwę z identyfikatorem pliku.

    Oto przykład ścieżki folderu i nazwy pliku błędu, które są tworzone podczas pobierania elementów do folderu nadrzędnego **C:\Remediation** :

    `C:\Remediation\232f8b7e-089c-4781-88c6-210da0615d32\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938.docx`

    Jeśli zostanie pobranych wiele plików, każdy z nich zostanie pobrany do podfolderu o nazwie z identyfikatorem pliku.

    > [!IMPORTANT]
    > Podczas przekazywania plików w kroku 9 i kroku 10 skorygowane pliki muszą mieć tę samą nazwę pliku i znajdować się w tej samej strukturze podfolderów. Nazwy podfolderów i plików są używane do skojarzenia skorygowanego pliku z oryginalnym plikiem błędu. Jeśli struktura folderów lub nazwy plików zostaną zmienione, zostanie wyświetlony następujący błąd: `Cannot apply Error Remediation to the current Workingset`. Aby zapobiec wszelkim problemom, zalecamy przechowywanie skorygowanych plików w tym samym folderze nadrzędnym i strukturze podfolderów.

7. Po pobraniu plików można je skorygować za pomocą odpowiedniego narzędzia. W przypadku plików chronionych hasłem można użyć kilku narzędzi do łamania haseł. Jeśli znasz hasła do plików, możesz je otworzyć i usunąć ochronę haseł.

8. Wróć do eDiscovery (Premium) i kreatora korygowania błędów, a następnie kliknij przycisk **Dalej: Upload plików**.  Spowoduje to przejście do następnej strony, na której można teraz przekazać pliki.

    ![pliki Upload.](../media/af3d8617-1bab-4ecd-8de0-22e53acba240.png)

9. Określ folder nadrzędny, w którym znajdują się skorygowane pliki w polu tekstowym **Ścieżka do lokalizacji plików** . Ponownie folder nadrzędny musi mieć taką samą strukturę podfolderów, która została utworzona podczas pobierania plików.

    Ścieżka do folderu nadrzędnego jest automatycznie dodawana do polecenia AzCopy (jako wartość **/Source** parametru).

10. Skopiuj wstępnie zdefiniowane polecenie, klikając pozycję **Kopiuj do schowka**. Otwórz wiersz polecenia Windows, wklej polecenie AzCopy, a następnie naciśnij **klawisz Enter**. przekazywanie plików.

    ![Wyniki pomyślnego przekazania skorygowanych plików w narzędziu Azcopy.](../media/ff2ff691-629f-4065-9b37-5333f937daf6.png)

11. Po uruchomieniu polecenia AzCopy kliknij przycisk **Dalej: Przetwarzanie plików**.

    Po zakończeniu przetwarzania możesz przejść do zestawu przeglądów i wyświetlić skorygowane pliki.

## <a name="remediating-errors-in-container-files"></a>Korygowanie błędów w plikach kontenerów

W sytuacjach, gdy zawartość pliku kontenera (takiego jak plik .zip) nie może zostać wyodrębniona przez funkcję zbierania elektronicznych materiałów dowodowych (Premium), można pobrać kontenery i rozszerzyć zawartość do tego samego folderu, w którym znajduje się oryginalny kontener. Rozwinięte pliki zostaną przypisane do kontenera nadrzędnego tak, jakby zostały pierwotnie rozwinięte przez funkcję zbierania elektronicznych materiałów dowodowych (Premium). Proces działa zgodnie z powyższym opisem, z wyjątkiem przekazywania pojedynczego pliku jako pliku zastępczego.  Podczas przekazywania skorygowanych plików nie dołączaj oryginalnego pliku kontenera.

## <a name="remediating-errors-by-uploading-the-extracted-text"></a>Korygowanie błędów przez przekazanie wyodrębnionego tekstu

Czasami nie można skorygować pliku do formatu natywnego, który może interpretować eDiscovery (Premium). Można jednak zastąpić oryginalny plik plikiem tekstowym zawierającym oryginalny tekst pliku natywnego (w procesie nazywanym *nakładką tekstową*). W tym celu wykonaj kroki opisane w tym artykule, ale zamiast korygować oryginalny plik w formacie natywnym, należy utworzyć plik tekstowy zawierający wyodrębniony tekst z oryginalnego pliku, a następnie przekazać plik tekstowy przy użyciu oryginalnej nazwy pliku dołączonej do sufiksu .txt. Na przykład plik jest pobierany podczas korygowania błędów o nazwie 335850cc-6602-4af0-acfa-1d14d9128ca2.abc. Otwórz plik w aplikacji natywnej, skopiuj tekst, a następnie wklej go do nowego pliku o nazwie 335850cc-6602-4af0-acfa-1d14d9128ca2.abc.txt. W takim przypadku należy usunąć oryginalny plik w formacie natywnym ze skorygowanej lokalizacji pliku na komputerze lokalnym przed przekazaniem skorygowanego pliku tekstowego do usługi eDiscovery (Premium).

## <a name="what-happens-when-files-are-remediated"></a>Co się stanie, gdy pliki zostaną skorygowane

Po przekazaniu skorygowanych plików oryginalne metadane są zachowywane z wyjątkiem następujących pól:

- ExtractedTextSize
- HasText
- IsErrorRemediate
- LoadId
- ProcessingErrorMessage
- ProcessingStatus
- Tekst
- Wordcount
- Identyfikator zestawu roboczego

Aby uzyskać definicję wszystkich pól metadanych w usłudze eDiscovery (Premium), zobacz [Pola metadanych dokumentu](document-metadata-fields-in-advanced-ediscovery.md).