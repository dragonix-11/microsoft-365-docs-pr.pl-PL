---
title: Zarządzanie zadaniami w środowisku zbierania elektronicznych materiałów dowodowych (Premium)
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
description: Zadania zbierania elektronicznych materiałów dowodowych (Premium) ułatwiają śledzenie stanu długotrwałych procesów związanych z wykonywaniem różnych zadań zbierania elektronicznych materiałów dowodowych (Premium).
ms.openlocfilehash: ab1b6cf45805a0d67492a5d386670f139b24f5e1
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998506"
---
# <a name="manage-jobs-in-ediscovery-premium"></a>Zarządzanie zadaniami w środowisku zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Oto lista zadań (które są zazwyczaj długotrwałymi procesami), które są śledzone na karcie **Zadania** sprawy w usłudze Microsoft Purview eDiscovery (Premium). Te zadania są wyzwalane przez akcje użytkownika podczas korzystania z przypadków i zarządzania nimi.

| Typ zadania           | Opis     |
| :----------------- | :----------     |
|Dodawanie danych do zestawu przeglądów | Użytkownik dodaje kolekcję do zestawu przeglądów. To zadanie składa się z dwóch podrzędnych zadań: </br>• **Eksportowanie** — jest generowana lista elementów w kolekcji. </br>• **Pozyskiwanie & Indeksowanie** — elementy w kolekcji zgodne z zapytaniem wyszukiwania są kopiowane do lokalizacji Storage platformy Azure (w procesie nazywanym *pozyskiwaniem*), a następnie te elementy w lokalizacji Storage platformy Azure są ponownie indeksowane. Ten nowy indeks jest używany podczas wykonywania zapytań i analizowania elementów w zestawie danych. </br></br>Aby uzyskać więcej informacji, zobacz [Dodawanie wyników wyszukiwania do zestawu przeglądów](add-data-to-review-set.md). |
|Dodawanie danych do innego zestawu przeglądów | Użytkownik dodaje dokumenty z jednego zestawu przeglądów do innego zestawu przeglądów w tym samym przypadku. Aby uzyskać więcej informacji, zobacz [Dodawanie danych do zestawu przeglądów z innego zestawu przeglądów](add-data-to-review-set-from-another-review-set.md).|
|Dodawanie danych innych niż Microsoft 365 do zestawu przeglądów | Użytkownik przekazuje dane inne niż Microsoft 365 do zestawu przeglądów. Dane są również indeksowane podczas tego procesu. Na przykład pliki z lokalnego serwera plików lub komputera klienckiego są przekazywane do zestawu przeglądów. Aby uzyskać więcej informacji, zobacz [Ładowanie danych innych niż Microsoft 365 do zestawu przeglądów](load-non-office-365-data-into-a-review-set.md).| 
|Dodawanie skorygowanych danych do zestawu przeglądów | Dane z błędami przetwarzania są korygowane i ładowane z powrotem do zestawu przeglądów. Więcej informacji można znaleźć w następujących artykułach:</br>• [Korygowanie błędów podczas przetwarzania danych](error-remediation-when-processing-data-in-advanced-ediscovery.md)</br>• [Korygowanie błędu pojedynczego elementu](single-item-error-remediation.md)| 
|Porównywanie zestawów obciążeń | Użytkownik analizuje różnice między różnymi zestawami obciążeń w zestawie przeglądów. Zestaw obciążenia to wystąpienie dodawania danych do zestawu przeglądów. Jeśli na przykład dodasz wyniki dwóch różnych wyszukiwań do tego samego zestawu przeglądów, każde z nich będzie reprezentować zestaw obciążenia. |
|Rekonstrukcja konwersacji|Gdy użytkownik dodaje wyniki wyszukiwania do zestawu przeglądów konwersacji, konwersacje wiadomości błyskawicznych (*nazywane również konwersacjami wątkowymi) w usługach* takich jak Microsoft Teams są rekonstruowane w pliku PDF. To zadanie jest również wyzwalane, gdy użytkownik kliknie pozycję **Akcja > Tworzenie plików PDF konwersacji w zestawie przeglądów** . Aby uzyskać więcej informacji, zobacz [Przeglądanie konwersacji w usłudze eDiscovery (Premium)](conversation-review-sets.md).
|Konwertowanie zredagowanych dokumentów na format PDF|Gdy użytkownik adnotuje dokument w zestawie przeglądów i zredaguje jego część, może przekonwertować zredagowany dokument na plik PDF. Dzięki temu zredagowana część nie będzie widoczna, jeśli dokument zostanie wyeksportowany do prezentacji. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dokumentów w zestawie przeglądów](view-documents-in-review-set.md). |
|Szacowanie wyników wyszukiwania | Gdy użytkownik utworzy i uruchomi lub ponownie uruchomi kolekcję roboczą, narzędzie wyszukiwania wyszukuje w indeksie elementy zgodne z zapytaniem wyszukiwania i przygotowuje oszacowanie zawierające liczbę i całkowity rozmiar wszystkich elementów w wyszukiwaniu oraz liczbę wyszukiwanych źródeł danych.  Aby uzyskać więcej informacji, zobacz [Zbieranie danych dla przypadku](collecting-data-for-ediscovery.md). | 
|Przygotowywanie danych do eksportu | Użytkownik eksportuje dokumenty z zestawu przeglądów. Po zakończeniu procesu eksportowania mogą pobrać wyeksportowane dane na komputer lokalny. Aby uzyskać więcej informacji, zobacz [Eksportowanie danych przypadków](exporting-data-ediscover20.md). | 
|Przygotowywanie do rozwiązania błędów |Gdy użytkownik wybierze plik i utworzy nowe korygowanie błędów w widoku Błąd na karcie **Przetwarzanie** przypadku, pierwszym krokiem procesu jest przekazanie pliku z błędem przetwarzania do lokalizacji usługi Azure Storage w chmurze firmy Microsoft. To zadanie śledzi postęp procesu przekazywania. Aby uzyskać więcej informacji na temat przepływu pracy korygowania błędów, zobacz [Korygowanie błędów podczas przetwarzania danych](error-remediation-when-processing-data-in-advanced-ediscovery.md). | 
|Przygotowywanie podglądu wyszukiwania | Gdy użytkownik utworzy i uruchomi nową kolekcję wersji roboczej (lub ponownie uruchomi istniejącą kolekcję roboczą), narzędzie wyszukiwania przygotuje przykładowy podzbiór elementów (zgodnych z zapytaniem wyszukiwania), które można wyświetlić w wersji zapoznawczej. Podgląd wyników wyszukiwania pomaga określić skuteczność wyszukiwania.  Aby uzyskać więcej informacji, zobacz [Zbieranie danych dla przypadku](collecting-data-for-ediscovery.md#view-search-results-and-statistics). | 
|Ponowne indeksowanie danych opiekuna | Po dodaniu opiekuna do sprawy wszystkie częściowo indeksowane elementy w wybranych źródłach danych opiekuna są ponownie indeksowane przez proces o nazwie *Zaawansowane indeksowanie*. To zadanie jest również wyzwalane po kliknięciu pozycji **Zaktualizuj indeks** na karcie **Przetwarzanie** sprawy i zaktualizowaniu indeksu dla określonego opiekuna na stronie wysuwanej właściwości opiekuna. Aby uzyskać więcej informacji, zobacz [Zaawansowane indeksowanie danych opiekuna](indexing-custodian-data.md).
|Uruchamianie analizy | Użytkownik analizuje dane w zestawie przeglądów, uruchamiając narzędzia analityczne zbierania elektronicznych materiałów dowodowych (Premium), takie jak wykrywanie niemal duplikatów, analiza wątków wiadomości e-mail i analiza motywów. Aby uzyskać więcej informacji, zobacz [Analizowanie danych w zestawie przeglądów](analyzing-data-in-review-set.md). | 
|Tagowanie dokumentów | To zadanie jest wyzwalane, gdy użytkownik kliknie pozycję **Rozpocznij tagowanie w** **panelu Tagowanie** podczas przeglądania dokumentów w zestawie przeglądów. Użytkownik może uruchomić to zadanie po otagowaniu dokumentów w zestawie przeglądów, a następnie zbiorczo wybrać je w panelu wyświetlania dokumentu. Aby uzyskać więcej informacji, zobacz [Tagowanie dokumentów w zestawie przeglądów](tagging-documents.md). | 
|||

## <a name="job-status"></a>Stan zadania

W poniższej tabeli opisano różne stany stanu zadań.

|Stan|Opis|
|---|---|
|Przekazywane|Utworzono nowe zadanie.  Data i godzina przesłania zadania są wyświetlane w kolumnie **Utworzone** na karcie **Zadania** .|
|Przesyłanie nie powiodło się|Przesłanie zadania nie powiodło się.  Należy podjąć próbę ponownego uruchomienia akcji, która wyzwoliła zadanie.|
|W toku|Zadanie jest w toku. Postęp zadania można monitorować na karcie **Zadania** .|
|Pomyślne|Zadanie zostało pomyślnie ukończone. Data i godzina ukończenia zadania są wyświetlane w kolumnie **Ukończono** na karcie **Zadania** .|
|Częściowe pomyślne|Zadanie zakończyło się pomyślnie. Ten stan jest zwykle zwracany, gdy zadanie nie znalazło żadnych częściowo zindeksowanych danych (nazywanych również *niezaindeksowanymi danymi*) w niektórych źródłach danych opiekuna.|
|Zakończone niepowodzeniem|Zadanie nie powiodło się.  Należy podjąć próbę ponownego uruchomienia akcji, która wyzwoliła zadanie. Jeśli zadanie zakończy się niepowodzeniem po raz drugi, zalecamy skontaktowanie się z pomoc techniczna firmy Microsoft i podanie informacji o pomocy technicznej z zadania.|
