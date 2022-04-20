---
title: Eksportuj dokumenty z zestawu do przeglądu
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
description: Dowiedz się, jak wybierać i eksportować zawartość z zestawu przeglądów zbierania elektronicznych materiałów dowodowych (Premium) dla prezentacji lub przeglądów zewnętrznych.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: f0366843cab17092f3690992aa0cff5205414f86
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948732"
---
# <a name="export-documents-from-a-review-set-in-ediscovery-premium"></a>Eksportowanie dokumentów z zestawu przeglądów w usłudze eDiscovery (Premium)

Eksportowanie umożliwia użytkownikom dostosowywanie zawartości dołączonej do pakietu pobierania podczas eksportowania dokumentu z zestawu przeglądów w usłudze eDiscovery (Premium).

Aby wyeksportować dokumenty z zestawu przeglądów:

1. W portalu zgodności usługi Microsoft Purview otwórz przypadek zbierania elektronicznych materiałów dowodowych (Premium), wybierz kartę **Zestawy przeglądów**, a następnie wybierz zestaw przeglądów, który chcesz wyeksportować.

2. W zestawie przeglądów kliknij pozycję **ActionExport** > .

   Narzędzie Eksportuj wyświetla stronę wysuwaną z ustawieniami umożliwiającymi skonfigurowanie eksportu. Niektóre opcje są wybierane domyślnie, ale można je zmienić. Opisy opcji eksportu, które można skonfigurować, można znaleźć w poniższej sekcji.

   ![Opcje konfiguracji eksportowania elementów z zestawu przeglądów.](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

3. Po skonfigurowaniu eksportu kliknij pozycję **Eksportuj** , aby rozpocząć proces eksportowania. W zależności od opcji wybranej w sekcji **Opcje wyjściowe** możesz uzyskać dostęp do plików eksportu, pobierając je bezpośrednio lub na koncie usługi Azure Storage organizacji.

> [!NOTE]
> Zadania eksportu są zachowywane przez całe życie sprawy. Należy jednak pobrać zawartość z zadania eksportu w ciągu 30 dni od zakończenia zadania eksportu.

## <a name="export-options"></a>Opcje eksportu

Użyj następujących opcji, aby skonfigurować eksport. Nie wszystkie opcje są dozwolone w przypadku niektórych opcji wyjściowych, w szczególności eksportowanie plików tekstowych i zredagowanych plików PDF nie jest dozwolone podczas eksportowania do formatu PST.

- **Nazwa eksportu**: nazwa zadania eksportu. Zostanie on użyty do nazwania plików ZIP, które zostaną pobrane.

- **Opis**: Pole z bezpłatnym tekstem umożliwiające dodanie opisu.

- **Eksportowanie tych dokumentów**

  - Tylko wybrane dokumenty: ta opcja eksportuje tylko aktualnie wybrane dokumenty. Ta opcja jest dostępna tylko wtedy, gdy elementy są zaznaczone w zestawie przeglądów.
  
  - Wszystkie filtrowane dokumenty: ta opcja eksportuje dokumenty w aktywnym filtrze. Ta opcja jest dostępna tylko wtedy, gdy filtr jest stosowany do zestawu przeglądów.
  
  - Wszystkie dokumenty w zestawie przeglądów: ta opcja eksportuje wszystkie dokumenty w zestawie przeglądów.

- **Opcje wyjściowe**: wyeksportowana zawartość jest dostępna do pobrania bezpośrednio za pośrednictwem przeglądarki internetowej lub może zostać wysłana na konto usługi Azure Storage. Dwie pierwsze opcje umożliwiają bezpośrednie pobieranie.
  
  - Tylko raporty: tworzone są tylko pliki podsumowania i ładowania.
  
  - Luźne pliki i adresy PST (wiadomość e-mail jest dodawana do pstów, gdy jest to możliwe): pliki są eksportowane w formacie podobnym do oryginalnej struktury katalogów widocznej dla użytkowników w ich aplikacjach natywnych.  Aby uzyskać więcej informacji, zobacz sekcję [Loose files and PST export structure (Luźne pliki i struktura eksportu PST](#loose-files-and-pst-export-structure) ).
  
  - Skondensowana struktura katalogów: pliki są eksportowane i uwzględniane w pobieraniu.
  
  - Skondensowana struktura katalogów wyeksportowana do konta usługi Azure Storage: pliki są eksportowane na konto usługi Azure Storage organizacji. Aby skorzystać z tej opcji, musisz podać adres URL kontenera na koncie usługi Azure Storage w celu wyeksportowania plików. Musisz również podać token sygnatury dostępu współdzielonego dla konta usługi Azure Storage. Aby uzyskać więcej informacji, zobacz [Eksportowanie dokumentów w przeglądzie ustawionym na konto usługi Azure Storage](download-export-jobs.md).

- **Obejmują**
  
  - Tagi: po wybraniu tagowania informacje są uwzględniane w pliku ładowania.
  
  - Pliki tekstowe: Ta opcja obejmuje wyodrębnione wersje tekstowe plików natywnych w eksporcie.
  
  - Zastąp zredagowane elementy natywne przekonwertowanymi plikami PDF: w przypadku wygenerowania zredagowanych plików PDF podczas przeglądu te pliki są dostępne do eksportowania. Możesz wyeksportować tylko pliki natywne, które zostały zredagowane (nie wybierając tej opcji) lub wybrać tę opcję, aby wyeksportować pliki PDF zawierające rzeczywiste redakcje.

  - Pliki PDF konwersacji zamiast pojedynczych wiadomości czatu: zaznacz to pole wyboru, aby wyeksportować konwersacje na czacie w pliku PDF. Wszystkie wiadomości czatu z tej samej konwersacji są eksportowane w tym samym pliku PDF. Jeśli to pole wyboru pozostanie niezaznaczone, każdy unikatowy komunikat w konwersacji na czacie zostanie wyeksportowany jako element autonomiczny. Plik jest eksportowany w tym samym formacie, w jakim został zapisany, jak w skrzynce pocztowej. W przypadku określonej konwersacji otrzymujesz wiele plików msg.

W poniższych sekcjach opisano strukturę folderów dla luźnych plików i skondensowanych opcji struktury katalogów. Eksporty są partycjonowane do plików ZIP o maksymalnym rozmiarze nieskompresowanego zawartości 75 GB. Jeśli rozmiar eksportu jest mniejszy niż 75 GB, eksport będzie składać się z pliku podsumowania i pojedynczego pliku ZIP. W przypadku eksportów większych niż 75 GB nieskompresowanych danych zostanie utworzonych wiele plików ZIP. Po pobraniu pliki ZIP mogą zostać nieskompresowane w jednej lokalizacji, aby ponownie utworzyć pełny eksport.

### <a name="loose-files-and-pst-export-structure"></a>Luźne pliki i struktura eksportu PST

Jeśli wybierzesz tę opcję eksportu, wyeksportowana zawartość zostanie zorganizowana w następującej strukturze:

- Summary.csv: zawiera podsumowanie zawartości wyeksportowane z zestawu przeglądów

- Folder główny: ten folder o nazwie [Nazwa eksportu] x z.zip i zostanie powtórzony dla każdej partycji pliku ZIP. Folder główny zawiera następujące elementy:
  
  - Export_load_file_x z.csv: plik metadanych.
  
  - Ostrzeżenia i błędy x z.csv: ten plik zawiera informacje o błędach napotkanych podczas próby wyeksportowania z zestawu przeglądów.
  
  - Exchange: ten folder zawiera całą zawartość z Exchange przechowywaną w plikach PST. Zredagowanych plików PDF nie można dołączyć do tej opcji. Jeśli załącznik zostanie wybrany w zestawie przeglądów, nadrzędna wiadomość e-mail zostanie wyeksportowana z dołączonym załącznikiem.
  
    Folder Exchange może również zawierać podfolder o nazwie mailboxname_loosefiles.zip, który zawiera następujące elementy:

    - Komunikaty chronione przez usługę Information Rights Management (IRM), które zostały zdekodowane.
    - Komunikaty korygowane przez błąd.
    - Nowoczesne załączniki lub linki przywoływane w komunikatach.
    - Zaszyfrowane elementy (które nie są uwzględnione w plikach PST w folderze Exchange).
  
  - SharePoint: ten folder zawiera całą zawartość natywną z SharePoint w natywnym formacie pliku. Zredagowanych plików PDF nie można dołączyć do tej opcji.

### <a name="condensed-directory-structure"></a>Skondensowana struktura katalogów

- Summary.csv: zawiera podsumowanie zawartości wyeksportowane z zestawu przeglądów

- Folder główny: ten folder o nazwie [Nazwa eksportu] x z.zip i zostanie powtórzony dla każdej partycji pliku ZIP.
  
  - Export_load_file_x z.csv: plik metadanych, a także lokalizacja każdego pliku przechowywanego w pliku ZIP.
  
  - Ostrzeżenia i błędy x z.csv: ten plik zawiera informacje o błędach napotkanych podczas próby wyeksportowania z zestawu przeglądów.

  - NativeFiles: ten folder zawiera wszystkie pliki natywne, które zostały wyeksportowane. Pliki natywne są zastępowane zredagowanymi plikami PDF, jeśli *wybrano opcję Zamień zredagowane natywne na przekonwertowane pliki PDF* .
  
  - Error_files: ten folder zawiera pliki, w których wystąpił błąd wyodrębniania lub innego przetwarzania. Pliki zostaną umieszczone w oddzielnych folderach— ExtractionError lub ProcessingError. Te pliki są wymienione w pliku ładowania.

  - Extracted_text_files: Ten folder zawiera wszystkie wyodrębnione pliki tekstowe, które zostały wygenerowane podczas przetwarzania.

### <a name="condensed-directory-structure-exported-to-your-azure-storage-account"></a>Skondensowana struktura katalogów wyeksportowana na konto usługi Azure Storage

Ta opcja używa tej samej ogólnej struktury co *skrócona struktura katalogów*, jednak zawartość nie jest spakowana i dane są zapisywane na koncie usługi Azure Storage. Ta opcja jest zwykle używana podczas pracy z dostawcą zbierania elektronicznych materiałów dowodowych innych firm. Aby uzyskać szczegółowe informacje na temat korzystania z tej opcji, zobacz [Eksportowanie dokumentów w przeglądzie ustawionym na konto usługi Azure Storage](download-export-jobs.md).
