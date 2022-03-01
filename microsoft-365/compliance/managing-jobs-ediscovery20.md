---
title: Zarządzanie zadaniami w u Advanced eDiscovery
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
description: Advanced eDiscovery zadań pomagają śledzić stan długo działających procesów związanych z wykonywaniem różnych Advanced eDiscovery zadań.
ms.openlocfilehash: 484f492ea56f6e75d3f5144dd41128c2cedfc914
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027084"
---
# <a name="manage-jobs-in-advanced-ediscovery"></a>Zarządzanie zadaniami w u Advanced eDiscovery

Poniżej znajduje się lista zadań (które są zazwyczaj długo działających procesami) śledzona na karcie Zadania w przypadku Advanced eDiscovery. Te zadania są wyzwalane przez akcje użytkownika podczas używania spraw i zarządzania nimi.

| Typ zadania           | Opis     |
| :----------------- | :----------     |
|Dodawanie danych do zestawu recenzji | Użytkownik dodał kolekcję do zestawu recenzji. To zadanie składa się z dwóch podsekcji: </br>• **Eksportowanie** — zostanie wygenerowana lista elementów w kolekcji. </br>• **Ingestion & Indeksowanie** — elementy w kolekcji zgodne z zapytaniem wyszukiwania są kopiowane do lokalizacji usługi Azure Storage (w procesie nazywanym *ingestion*), a następnie te elementy w lokalizacji usługi Azure Storage są ponownie indeksowane. Ten nowy indeks jest używany podczas wykonywania zapytań i analizowania elementów w zestawie danych. </br></br>Aby uzyskać więcej informacji, zobacz [Dodawanie wyników wyszukiwania do zestawu recenzji](add-data-to-review-set.md). |
|Dodawanie danych do innego zestawu recenzji | Użytkownik dodaje dokumenty z jednego zestawu recenzji do innego zestawu recenzji w tej samej sprawie. Aby uzyskać więcej informacji, [zobacz Dodawanie danych do zestawu recenzji z innego zestawu recenzji](add-data-to-review-set-from-another-review-set.md).|
|Dodawanie danych nie Microsoft 365 do zestawu recenzji | Użytkownik przekaże dane bez Microsoft 365 do zestawu recenzji. W trakcie tego procesu dane są również indeksowane. Na przykład pliki z lokalnego serwera plików lub komputera klienckiego są przekazywane do zestawu recenzji. Aby uzyskać więcej informacji, zobacz [Ładowanie danych Microsoft 365 do zestawu recenzji](load-non-office-365-data-into-a-review-set.md).| 
|Dodawanie danych zaradczych do zestawu recenzji | Dane z błędami przetwarzania są naprawiane i ładowane z powrotem do zestawu recenzji. Więcej informacji można znaleźć w następujących artykułach:</br>• [Rozwiązywanie problemów z błędami podczas przetwarzania danych](error-remediation-when-processing-data-in-advanced-ediscovery.md)</br>• [Rozwiązywanie problemów z błędami jedno elementu](single-item-error-remediation.md)| 
|Porównanie zestawów obciążenia | Użytkownik przegląda różnice między różnymi zestawami ładowania w zestawie recenzji. Zestaw ładowania to wystąpienie dodawania danych do zestawu recenzji. Na przykład dodanie wyników dwóch różnych wyszukiwań do tego samego zestawu recenzji oznaczałoby zestaw ładowania. |
|Konwersacja|Gdy użytkownik doda wyniki wyszukiwania do zestawu recenzji konwersacji, konwersacje za pomocą wiadomości błyskawicznych (nazywane również konwersacjami w wątkach *) w* usługach, takich jak Microsoft Teams są odtworzone w pliku PDF. To zadanie jest również wyzwalane po kliknięciu przez użytkownika przycisku **Akcja > Tworzenie plików PDF** konwersacji w zestawie recenzji. Aby uzyskać więcej informacji, zobacz [Przeglądanie konwersacji w Advanced eDiscovery](conversation-review-sets.md).
|Konwertowanie dokumentów redagowanych na format PDF|Po dodaniem adnotacji do dokumentu w zestawie recenzji i redagowania jego części użytkownik może przekonwertować dokument z redagowanych na plik PDF. Dzięki temu redagowana część nie będzie widoczna, jeśli dokument zostanie wyeksportowany do prezentacji. Aby uzyskać więcej informacji, [zobacz Wyświetlanie dokumentów w zestawie recenzji](view-documents-in-review-set.md). |
|Szacowanie wyników wyszukiwania | Gdy użytkownik utworzy i uruchomi lub ponownie uruchomi kolekcję roboczą, narzędzie wyszukiwania wyszukuje w indeksie elementy zgodne z zapytaniem wyszukiwania i przygotowuje oszacowanie, które obejmuje liczbę i całkowity rozmiar wszystkich elementów przez wyszukiwanie oraz liczbę przeszukanych źródeł danych.  Aby uzyskać więcej informacji, zobacz [Zbieranie danych dotyczących sprawy](collecting-data-for-ediscovery.md). | 
|Przygotowywanie danych do eksportu | Użytkownik eksportuje dokumenty z zestawu recenzji. Po zakończeniu procesu eksportowania mogą oni pobrać wyeksportowane dane na komputer lokalny. Aby uzyskać więcej informacji, zobacz [Eksportowanie danych o przypadku](exporting-data-ediscover20.md). | 
|Przygotowanie do rozwiązywania problemów |Gdy użytkownik wybierze plik i utworzy nowe rozwiązanie problemów w widoku Błąd na karcie Przetwarzanie sprawy, pierwszym krokiem w procesie jest przekazanie pliku, w którym wystąpił błąd przetwarzania, do lokalizacji usługi Azure Storage w chmurze firmy Microsoft. To zadanie śledzi postęp procesu przekazywania. Aby uzyskać więcej informacji na temat przepływu pracy Rozwiązywanie problemów z błędami, zobacz [Rozwiązywanie problemów podczas przetwarzania danych](error-remediation-when-processing-data-in-advanced-ediscovery.md). | 
|Przygotowywanie podglądu wyszukiwania | Gdy użytkownik utworzy i uruchomi nową kolekcję roboczą (lub ponownie uruchomi istniejącą kolekcję roboczą), narzędzie wyszukiwania przygotuje przykładowy podzbiór elementów (które pasują do zapytania wyszukiwania), których podgląd można wyświetlić. Wyświetlanie podglądu wyników wyszukiwania pomaga w określeniu skuteczności wyszukiwania.  Aby uzyskać więcej informacji, zobacz [Zbieranie danych dotyczących sprawy](collecting-data-for-ediscovery.md#view-search-results-and-statistics). | 
|Ponowne indeksowanie danych wskaźników indeksowanych | Po dodaniu do sprawy elementów przetwarzających wszystkie częściowo indeksowane elementy w wybranych źródłach danych tego użytkownika są ponownie indeksowane przez proces o nazwie Indeksowanie *zaawansowane*. To zadanie jest również wyzwalane po kliknięciu przycisku Aktualizuj indeks na  karcie Przetwarzanie sprawy i po zaktualizowaniu indeksu określonego opiekuna na stronie wysuwu właściwości wiadych. Aby uzyskać więcej informacji, [zobacz Zaawansowane indeksowanie danych do przetwarzania](indexing-custodian-data.md).
|Uruchamianie analizy | Użytkownik analizuje dane w zestawie recenzji, uruchamiając narzędzia do analizy Advanced eDiscovery, takie jak wykrywanie niemal duplikatów, analiza wątków wiadomości e-mail i analiza motywów. Aby uzyskać więcej informacji, [zobacz Analizowanie danych w zestawie recenzji](analyzing-data-in-review-set.md). | 
|Tagowanie dokumentów | To zadanie jest wyzwalane, gdy użytkownik kliknie przycisk Rozpocznij tagowanie **zadania** w **panelu Otagowanie** podczas przeglądania dokumentów w zestawie recenzji. Użytkownik może rozpocząć to zadanie po oznakowaniu dokumentów w zestawie recenzji, a następnie zbiorczo wybrać je w panelu dokumentu widoku. Aby uzyskać więcej informacji, zobacz [Oznaczanie dokumentów w zestawie recenzji](tagging-documents.md). | 
|||

## <a name="job-status"></a>Stan stanowiska

W poniższej tabeli opisano różne stany zadań.

| Stan           | Opis     |
| :----------------- | :----------     |
| Przesłaliśmy | Utworzono nowe zadanie.  Data i godzina przesłanego zadania jest wyświetlana w kolumnie **Utworzono** na **karcie** Zadania. |
| Przesyłanie nie powiodło się | Przesyłanie zadania nie powiodło się.  Należy spróbować ponownie uruchomić akcję, która wyzwoliła zadanie. |
| W toku | Zadanie jest w toku, możesz monitorować jego postęp **na karcie Zadania** . |
| Udało się | Zadanie zostało pomyślnie ukończone. Data i godzina ukończenia zadania jest wyświetlana w kolumnie Wykonane  na **karcie** Zadania. |
| Częściowy sukces | Zadanie się powiodło. Ten stan jest zazwyczaj zwracany, gdy zadanie nie znalazło żadnych częściowo zindeksowanych danych (nazywanych również danymi nieindeksowanych *) w* niektórych źródłach danych indeksowanych.  |
| Zakończone niepowodzeniem | Zadanie nie powiodło się.  Należy spróbować ponownie uruchomić akcję, która wyzwoliła zadanie. Jeśli drugie zadanie nie powiedzie się, zalecamy skontaktowanie się z pomocą techniczną firmy Microsoft i podanie informacji o pomocy technicznej z tego zadania. |
|||
