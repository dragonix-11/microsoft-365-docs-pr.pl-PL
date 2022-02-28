---
title: Eksportowanie dokumentów do konta usługi Azure Storage Twojej organizacji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
ms.custom: seo-marvel-mar2020
description: Wyeksportuj dokumenty w zestawie recenzji do konta usługi Azure Storage, a następnie użyj programu Eksplorator usługi Azure Storage, aby pobrać je na komputer lokalny.
ms.openlocfilehash: 8f3110ef386fd5c5d8adc641aa223435caf0da67
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988030"
---
# <a name="export-documents-in-a-review-set-to-an-azure-storage-account"></a>Eksportowanie dokumentów w zestawie recenzji do konta usługi Azure Storage

Podczas eksportowania dokumentów z zestawu recenzji w przypadku Advanced eDiscovery przypadku możesz wyeksportować je do konta usługi Azure Storage zarządzanego przez Twoją organizację. W przypadku użycia tej opcji dokumenty są przekazywane do usługi Azure Storage lokalizacji. Po wyeksportowaniu dokumentów możesz uzyskać do nich dostęp (i pobrać je na komputer lokalny lub do innej lokalizacji), korzystając z Eksplorator usługi Azure Storage. Ten artykuł zawiera instrukcje dotyczące eksportowania dokumentów na konto usługi Azure Storage oraz używania programu Eksplorator usługi Azure Storage do łączenia się z lokalizacją usługi Azure Storage w celu pobrania wyeksportowanych dokumentów. Aby uzyskać więcej informacji na Eksplorator usługi Azure Storage, zobacz [Używanie Eksplorator usługi Azure Storage](/azure/storage/blobs/storage-quickstart-blobs-storage-explorer).

## <a name="before-you-export-documents-from-a-review-set"></a>Przed wyeksportowaniem dokumentów z zestawu recenzji

- Aby wyeksportować dokumenty z zestawu recenzji, musisz podać token SAS (Shared Access Signature) dla konta usługi Azure Storage oraz adres URL określonego kontenera na koncie magazynu. Pamiętaj, aby były pod ręką (na przykład skopiowane do pliku tekstowego) podczas wykonywania kroku 2

  - **Token SAS**: Upewnij się, że token SAS jest dla Twojego konta usługi Azure Storage (a nie dla kontenera). Możesz wygenerować token SAS dla Twojego konta w usłudze Azure Storage. W tym celu przejdź do konta usługi Azure Storage i wybierz pozycję Udostępnij podpis dostępu  w obszarze **Ustawienia ustawień magazynu** na dysku magazynu. Użyj ustawień domyślnych i zezwalaj na wszystkie typy zasobów podczas generowania tokenu SAS.

  - **Container URL** (Adres URL kontenera): musisz utworzyć kontener, aby przekazać do tego zestawu dokumentów recenzji, a następnie uzyskać kopię adresu URL kontenera. na przykład `https://ediscoverydata.blob.core.windows.net/exportdata`. Aby uzyskać adres URL, przejdź do kontenera w usłudze Azure Storage i wybierz pozycję Właściwości w  sekcji **Ustawienia sekcji w** obszarze kontenerów blade.

- Pobierz i zainstaluj Eksplorator usługi Azure Storage. Aby uzyskać instrukcje, [Eksplorator usługi Azure Storage narzędzie](https://go.microsoft.com/fwlink/p/?LinkId=544842). Za pomocą tego narzędzia możesz połączyć się z kontenerem na koncie usługi Azure Storage i pobrać dokumenty wyeksportowane w kroku 1.

## <a name="step-1-export-the-documents-from-a-review-set"></a>Krok 1. Eksportowanie dokumentów z zestawu recenzji

Pierwszym krokiem jest utworzenie zadania eksportu w celu wyeksportowania dokumentów z zestawu recenzji. Aby uzyskać bardziej szczegółowe instrukcje dotyczące wszystkich opcji eksportu, zobacz [Eksportowanie dokumentów z zestawu recenzji](export-documents-from-review-set.md). W poniższej procedurze wyróżniliśmy ustawienia eksportowania dokumentów na konto usługi Azure Storage Twojej organizacji.

1. W Centrum zgodności platformy Microsoft 365 otwórz sprawę Advanced eDiscovery, wybierz kartę Zestawy recenzji, a następnie wybierz  zestaw recenzji, który chcesz wyeksportować.

2. W zestawie recenzji kliknij pozycję **ActionExport** > .

3. Na stronie **wysuwu** opcji eksportu wpisz nazwę (wymagany) i opis (opcjonalnie) dla eksportu.

4. Skonfiguruj ustawienia w sekcjach dokumentów, metadanych, zawartości i opcji. Aby uzyskać więcej informacji o tych ustawieniach, zobacz [Eksportowanie dokumentów z zestawu recenzji](export-documents-from-review-set.md).

5. W sekcji **Opcje danych wyjściowych** wybierz skondensowana struktura katalogu wyeksportowana do twojego konta usługi **Azure Storage konta**.

6. Wklej adres URL kontenera i token SAS dla Twojego konta magazynu w odpowiadających im polach.

   ![Wklej adres URL połączenia i token SAS w odpowiadających im polach.](../media/AzureStorageOutputOptions.png)

7. Kliknij **pozycję Eksportuj** , aby utworzyć zadanie eksportu.

## <a name="step-2-obtain-the-sas-url-from-the-export-job"></a>Krok 2. Uzyskiwanie adresu URL SAS z zadania eksportowania

Następnym krokiem jest uzyskanie adresu URL SAS wygenerowanego po utworzeniu zadania eksportu w kroku 1. Za pomocą adresu URL SAS możesz połączyć się z kontenerem na Twoim koncie usługi Azure Storage, do konta, do których wyeksportowano dokumenty zestawu recenzji.

1. Na stronie **Advanced eDiscovery** przejdź do sprawy, a następnie kliknij **kartę Eksporty**.

2. Na karcie **Eksporty** kliknij zadanie eksportu, które chcesz pobrać. Jest to zadanie eksportu utworzone w kroku 1.

3. Na stronie wysuwu w **obszarze Lokalizacje** skopiuj wyświetlany adres URL SAS. W razie potrzeby możesz zapisać go w pliku tekstowym, aby uzyskać do niego dostęp w kroku 3.

   ![Skopiuj adres URL SAS wyświetlany w obszarze Lokalizacje.](../media/eDiscoExportJob.png)

   > [!TIP]
   > Adres URL SAS wyświetlany w zadaniu eksportu to zsuń adres URL kontenera i token SAS dla Twojego konta Storage Azure. Możesz skopiować go z zadania eksportu lub utworzyć samodzielnie, łącząc adres URL i token SAS.

## <a name="step-3-connect-to-the-azure-storage-container"></a>Krok 3. Połączenie do kontenera usługi Azure Storage usługi

Ostatnim krokiem jest użycie interfejsu Eksplorator usługi Azure Storage i adresu URL SAS w celu nawiązania połączenia z kontenerem na koncie usługi Azure Storage i pobrania wyeksportowanych dokumentów na komputer lokalny.

1. Uruchom Eksplorator usługi Azure Storage, który został pobrany i zainstalowany.

2. Kliknij **ikonę Otwórz Połączenie dialogowe**.

   ![Kliknij ikonę Dodaj konto.](../media/AzureStorageConnect.png)

3. Na stronie **Połączenie do usługi Azure Storage** kliknij pozycję **Kontener obiektów blob**.

4. Na stronie **Wybieranie metody uwierzytelniania** wybierz opcję Podpis dostępu udostępnionego **(SAS),** a następnie kliknij przycisk **Dalej**.

5. Na stronie **Wprowadź informacje o połączeniu** wklej adres URL SAS (uzyskany w zadaniu eksportowania w kroku 2) w polu **Adres URL SAS kontenera obiektów blob** .

    ![Wklej adres URL SAS w polu URI.](../media/AzureStorageConnect3.png)

    Zwróć uwagę, że nazwa kontenera jest wyświetlana w polu **Nazwa wyświetlana** . Tę nazwę można edytować.

6. Kliknij **przycisk Dalej**, aby wyświetlić **stronę podsumowania**, a następnie kliknij przycisk **Połączenie**.

    Zostanie **otwarty węzeł Kontenery obiektów** blob (**w Storage Kont** > **(dołączone** \> kontenery).

    ![Eksportowanie zadań w węźle Kontenery obiektów blob.](../media/AzureStorageConnect5.png)

    Zawiera ona kontener o nazwie z nazwą wyświetlaną z kroku 5. Ten kontener zawiera folder dla każdego zadania eksportu pobranego do kontenera na twoim koncie usługi Azure Storage poczty. Te foldery mają identyfikator odpowiadający identyfikatorowi zadania eksportu. Te identyfikatory eksportu (i nazwę eksportu) możesz znaleźć w obszarze Informacje o pomocy technicznej na wysuwanych informacjach dla każdego  zadania eksportu dane przygotowywanie wymienione na karcie Zadania w  Advanced eDiscovery przypadku.

7. Kliknij dwukrotnie folder zadania eksportu, aby go otworzyć.

   Zostanie wyświetlona lista folderów i raportów eksportu.

    ![Folder eksportu zawiera wyeksportowane pliki i raporty eksportu.](../media/AzureStorageConnect6.png)

8. Aby wyeksportować całą zawartość z zadania eksportu, kliknij strzałkę  w górę w celu powrotu do folderu zadania eksportu, a następnie kliknij pozycję **Pobierz**.

9. Określ lokalizację, do której chcesz pobrać wyeksportowane pliki, a następnie kliknij pozycję Wybierz folder.

    Proces Eksplorator usługi Azure Storage proces pobierania. Stan pobierania eksportowanych elementów jest wyświetlany w **okienku Działania** . Po zakończeniu pobierania zostanie wyświetlony komunikat.

> [!NOTE]
> Zamiast pobierać całe zadanie eksportu w programie Eksplorator usługi Azure Storage, możesz wybrać określone elementy do pobrania i wyświetlenia.

## <a name="more-information"></a>Więcej informacji

- Folder zadania eksportu zawiera następujące elementy. Rzeczywiste elementy w folderze eksportu są określane przez opcje eksportu skonfigurowane podczas tworzenia zadania eksportu. Aby uzyskać więcej informacji o tych opcjach, zobacz [Eksportowanie dokumentów z zestawu recenzji](export-documents-from-review-set.md).

  - Export_load_file.csv: Ten plik CSV to szczegółowy raport eksportu zawierający informacje o każdym wyeksportowanych dokumentach. Plik składa się z kolumny dla każdej właściwości metadanych dokumentu. Aby uzyskać listę i opis metadanych zawartych w tym raporcie, zobacz kolumnę Nazwa eksportowanego  pola w tabeli w polach metadanych dokumentu w [Advanced eDiscovery.](document-metadata-fields-in-advanced-ediscovery.md)

  - Summary.txt: plik tekstowy zawierający podsumowanie eksportu, w tym statystykę eksportowania.

  - Extracted_text_files: Ten folder zawiera wersję pliku tekstowego każdego wyeksportowanego dokumentu.

  - NativeFiles: Ten folder zawiera natywną wersję pliku każdego wyeksportowanego dokumentu.

  - Error_files: Ten folder zawiera następujące elementy, jeśli zadanie eksportu zawiera pliki błędów:

    - ExtractionError.csv: Ten plik CSV zawiera dostępne metadane dla plików, które nie zostały poprawnie wyodrębnione z ich elementu nadrzędnego.

    - ProcessingError: Ten folder zawiera dokumenty z błędami przetwarzania. Ta zawartość znajduje się na poziomie elementu, co oznacza, że jeśli w załączniku wystąpił błąd przetwarzania, dokument zawierający ten załącznik również zostanie uwzględniony w tym folderze.
