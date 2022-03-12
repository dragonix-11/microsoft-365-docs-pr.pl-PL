---
title: Eksportowanie dokumentów z zestawu recenzji
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
ms.assetid: ''
description: Dowiedz się, jak zaznaczać i eksportować zawartość z zestawu Advanced eDiscovery dla prezentacji lub recenzji zewnętrznych.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 61de8fed9c5bcb00daf3a8273f3ebfc86fe75a35
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449460"
---
# <a name="export-documents-from-a-review-set-in-advanced-ediscovery"></a>Eksportowanie dokumentów z zestawu recenzji w programie Advanced eDiscovery

Eksportowanie umożliwia użytkownikom dostosowywanie zawartości zawartej w pakiecie pobierania podczas eksportowania dokumentu z zestawu recenzji w pakiecie Advanced eDiscovery.

Aby wyeksportować dokumenty z zestawu recenzji:

1. W Centrum zgodności platformy Microsoft 365 otwórz sprawę Advanced eDiscovery, wybierz kartę Zestawy recenzji, a następnie wybierz  zestaw recenzji, który chcesz wyeksportować.

2. W zestawie recenzji kliknij pozycję **ActionExport** > .

   Narzędzie Eksportowanie wyświetli stronę wysuwu z ustawieniami, aby skonfigurować eksportowanie. Niektóre opcje są domyślnie zaznaczone, ale można je zmienić. Opisy opcji eksportu, które można skonfigurować, można znaleźć w poniższej sekcji.

   ![Opcje konfiguracji eksportowania elementów z zestawu recenzji.](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

3. Po skonfigurowaniu eksportu kliknij pozycję **Eksportuj** , aby rozpocząć proces eksportowania. W zależności od opcji wybranej w sekcji  Opcje danych wyjściowych możesz uzyskać dostęp do wyeksportowanych plików, pobierając je bezpośrednio lub na koncie usługi Azure Storage Twojej organizacji.

> [!NOTE]
> Zadania eksportowania są zachowywane przez czas życia sprawy. Jednak musisz pobrać zawartość z zadania eksportu w ciągu 30 dni od ukończenia zadania eksportowania.

## <a name="export-options"></a>Opcje eksportowania

Skonfiguruj eksportowanie za pomocą następujących opcji. Nie wszystkie opcje są dozwolone dla niektórych opcji wyjściowych, w szczególności w przypadku eksportowania plików tekstowych i redagowanych plików PDF nie są dozwolone podczas eksportowania do formatu PST.

- **Nazwa eksportu**: nazwa zadania eksportu. Zostanie on użyty do nazwania plików ZIP, które zostaną pobrane.

- **Opis**: pole tekstowe bezpłatne, w przypadku których możesz dodać opis.

- **Eksportowanie tych dokumentów**

  - Tylko wybrane dokumenty: ta opcja powoduje wyeksportowanie tylko obecnie zaznaczonych dokumentów. Ta opcja jest dostępna tylko po wybraniu elementów w zestawie recenzji.
  
  - Wszystkie filtrowane dokumenty: ta opcja powoduje wyeksportowanie dokumentów z aktywnego filtru. Ta opcja jest dostępna tylko po zastosowaniu filtru do zestawu recenzji.
  
  - Wszystkie dokumenty w zestawie recenzji: ta opcja powoduje wyeksportowanie wszystkich dokumentów z zestawu recenzji.

- **Opcje wyjściowe**: Wyeksportowana zawartość jest dostępna do pobrania bezpośrednio za pośrednictwem przeglądarki sieci Web lub może zostać wysłana na konto usługi Azure Storage. Pierwsze dwie opcje umożliwiają pobieranie bezpośrednie.
  
  - Tylko raporty: Tworzony jest tylko plik podsumowania i ładowania.
  
  - Pliki luźne i pliki PST (jeśli to możliwe) są dodawane do plików PST: pliki są eksportowane w formacie podobnym do oryginalnej struktury katalogów widocznej dla użytkowników w ich natywnych aplikacjach.  Aby uzyskać więcej informacji, zobacz sekcję [Luźne pliki i struktura eksportu PST](#loose-files-and-pst-export-structure) .
  
  - Skondensowana struktura katalogu: pliki są eksportowane i uwzględniane w pliku do pobrania.
  
  - Skondensowana struktura katalogu wyeksportowana do Twojego konta usługi Azure Storage: Pliki są eksportowane do konta usługi Azure Storage Twojej organizacji. W przypadku tej opcji musisz podać adres URL kontenera na koncie usługi Azure Storage, aby wyeksportować pliki. Musisz również udostępnić token SAS (Shared Access Signature) dla swojego konta Storage Azure. Aby uzyskać więcej informacji, zobacz [Eksportowanie dokumentów w ramach zestawu recenzji do konta Storage Azure](download-export-jobs.md).

- **Uwzględnij**
  
  - Tagi: Jeśli ta opcja jest zaznaczona, informacje o tagowaniu są uwzględniane w pliku ładowania.
  
  - Pliki tekstowe: Ta opcja uwzględnia wyodrębnione wersje tekstowe plików natywnych w eksporcie.
  
  - Zastępowanie redagowanych natywnych plików przekonwertowanych plikami PDF: Jeśli podczas przeglądania zostaną wygenerowane redagowane pliki PDF, te pliki będą dostępne do wyeksportowania. Możesz wybrać eksportowanie tylko plików natywnych, które zostały redagowane (nie zaznaczając tej opcji) lub możesz wybrać tę opcję, aby wyeksportować pliki PDF zawierające rzeczywiste ponowne działania.

  - Pliki PDF konwersacji zamiast pojedynczych wiadomości czatu: Zaznacz to pole wyboru, aby wyeksportować konwersacje na czacie w pliku PDF. Wszystkie wiadomości czatu z tej samej konwersacji są eksportowane do tego samego pliku PDF. Jeśli pozostawisz to pole wyboru niezaznaczane, każda unikatowa wiadomość w konwersacji na czacie jest eksportowana jako autonomiczny element. Plik jest eksportowany w tym samym formacie, w który został zapisany, co w skrzynce pocztowej. W przypadku określonej konwersacji otrzymujesz wiele plików msg.

W poniższych sekcjach opisano strukturę folderów w przypadku luźnych plików oraz skondensowane opcje struktury katalogu. Eksporty są podzielone na pliki ZIP o maksymalnym rozmiarze nieskompresowanych treści 75 GB. Jeśli rozmiar eksportu jest mniejszy niż 75 GB, eksport będzie się składał z pliku podsumowania i jednego pliku ZIP. W przypadku eksportów większych niż 75 GB nieskompresowanych danych zostanie utworzonych wiele plików ZIP. Po pobraniu pliki ZIP można dekompresować w jednej lokalizacji w celu ponownego odtworzenia pełnego eksportu.

### <a name="loose-files-and-pst-export-structure"></a>Luźne pliki i struktura eksportu pst

Jeśli wybierzesz tę opcję eksportu, wyeksportowana zawartość będzie zorganizowana w następującej strukturze:

- Summary.csv: Zawiera podsumowanie zawartości wyeksportowanych z zestawu recenzji

- Folder główny: ten folder o nazwie [Export Name] x z z.zip i będzie powtarzany dla każdej partycji pliku ZIP. Folder główny zawiera następujące elementy:
  
  - Export_load_file_x pliku z.csv: plik metadanych.
  
  - Ostrzeżenia i błędy x z.csv: Ten plik zawiera informacje o błędach napotkanych podczas próby wyeksportowania z zestawu recenzji.
  
  - Exchange: Ten folder zawiera całą zawartość z plików Exchange przechowywanych w plikach PST. Tej opcji nie można dołączona do redagowanych plików PDF. Jeśli w zestawie recenzji wybrano załącznik, nadrzędna wiadomość e-mail zostanie wyeksportowana z dołączonym załącznikiem.
  
    Folder Exchange może również zawierać podfolder o nazwie mailboxname_loosefiles.zip zawierający następujące elementy:

    - Wiadomości chronione za pomocą usługi Zarządzanie prawami do informacji (IRM) w dekodowanych wiadomościach.
    - Komunikaty o błędach usunięte.
    - Nowoczesne załączniki lub linki, do których odwołują się wiadomości.
    - Zaszyfrowane elementy (które nie są zawarte w plikach PST w Exchange folderze).
  
  - SharePoint: Ten folder zawiera całą natywną zawartość z SharePoint w natywnym formacie pliku. Tej opcji nie można dołączona do redagowanych plików PDF.

### <a name="condensed-directory-structure"></a>Skondensowana struktura katalogu

- Summary.csv: Zawiera podsumowanie zawartości wyeksportowanych z zestawu recenzji

- Folder główny: ten folder o nazwie [Export Name] x z z.zip i będzie powtarzany dla każdej partycji pliku ZIP.
  
  - Export_load_file_x z z.csv: Plik metadanych, a także lokalizację każdego pliku, który jest przechowywany w pliku ZIP.
  
  - Ostrzeżenia i błędy x z.csv: Ten plik zawiera informacje o błędach napotkanych podczas próby wyeksportowania z zestawu recenzji.

  - NativeFiles: Ten folder zawiera wszystkie wyeksportowane pliki natywne. Pliki natywne są zamieniane na pliki PDF redacted, jeśli wybrano opcję Zamień *redacted natives na przekonwertowane pliki PDF* .
  
  - Error_files: Ten folder zawiera pliki, w przypadku których wystąpił błąd wyodrębniania lub przetwarzania. Pliki zostaną umieszczone w osobnych folderach: ExtractionError lub ProcessingError. Te pliki są wymienione w pliku ładowania.

  - Extracted_text_files: Ten folder zawiera wszystkie wyodrębnione pliki tekstowe, które zostały wygenerowane podczas przetwarzania.

### <a name="condensed-directory-structure-exported-to-your-azure-storage-account"></a>Skondensowana struktura katalogu wyeksportowana do Twojego konta Storage Azure

Ta opcja ma taką samą ogólną strukturę jak struktura katalogu zagęszczanego *, jednak* zawartość nie jest zeszkowana, a dane są zapisywane na Twoim koncie usługi Azure Storage konta. Ta opcja jest zazwyczaj używana podczas pracy z innym dostawcą zbierania elektronicznych materiałów dowodowych. Aby uzyskać szczegółowe informacje na temat korzystania z tej opcji, zobacz Eksportowanie dokumentów [w zestawie recenzji do konta usługi Azure Storage konta](download-export-jobs.md).
