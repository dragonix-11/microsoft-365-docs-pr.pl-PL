---
title: Tworzenie przypadków zbierania elektronicznych materiałów dowodowych (Premium) i zarządzanie nimi na platformie Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: W tym artykule opisano sposób tworzenia przypadków Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) i zarządzania nimi. Pierwszym krokiem jest utworzenie sprawy i rozpoczęcie korzystania z funkcji i funkcji zbierania elektronicznych materiałów dowodowych (Premium).
ms.openlocfilehash: b8577a8d44cb6860cd595d3f2f13c731c290ba12
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630372"
---
# <a name="create-and-manage-an-ediscovery-premium-case"></a>Tworzenie sprawy zbierania elektronicznych materiałów dowodowych (Premium) i zarządzanie nią

Po skonfigurowaniu Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium) i [przypisaniu uprawnień do menedżerów zbierania elektronicznych materiałów dowodowych](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions) w organizacji, które będą zarządzać sprawami, następnym krokiem jest utworzenie sprawy i zarządzanie nią.

Ten artykuł zawiera również ogólne omówienie przypadków użycia do zarządzania przepływem pracy zbierania elektronicznych materiałów dowodowych (Premium) w przypadku sprawy prawnej lub innych typów dochodzeń.

## <a name="create-a-case"></a>Tworzenie sprawy

Wykonaj poniższe kroki, aby utworzyć przypadek i dodać członków. Użytkownik tworzący sprawę jest automatycznie dodawany jako członek. Członkowie sprawy mogą uzyskać dostęp do sprawy w portal zgodności Microsoft Purview i wykonywać zadania zbierania elektronicznych materiałów dowodowych (Premium).

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności</a> i zaloguj się przy użyciu poświadczeń konta użytkownika, do których przypisano uprawnienia zbierania elektronicznych materiałów dowodowych. Członkowie grupy ról Zarządzanie organizacją mogą również tworzyć przypadki zbierania elektronicznych materiałów dowodowych (Premium).

2. W okienku nawigacji po lewej stronie portalu zgodności kliknij pozycję **Pokaż wszystko**, a następnie wybierz pozycję **eDiscovery** > **Advanced**, a następnie wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2173764" target="_blank">kartę **Sprawy**</a>.

3. Wybierz **pozycję Utwórz przypadek**.

4. Na stronie wysuwanej **Nowy przypadek zbierania elektronicznych** materiałów dowodowych podaj nazwę sprawy (wymagane), a następnie wpisz opcjonalny numer i opis sprawy. Nazwa sprawy musi być unikatowa w organizacji.

5. Kliknij przycisk **Zapisz** , aby utworzyć przypadek.

   Zostanie utworzony nowy przypadek i zostanie wyświetlona karta **Ustawienia** w nowym przypadku.

6. Na kafelku **Uprawnienia & dostępu** na karcie **Ustawienia** kliknij pozycję **Wybierz**.

7. Na **zarządzać tym przypadku** wysuwany w obszarze **Zarządzanie członkami**, kliknij przycisk **Dodaj** , aby dodać członków do sprawy.

8. Na liście osób zaznacz pole wyboru obok nazw osób, które chcesz dodać do sprawy. Jak wyjaśniono wcześniej, upewnij się, że osobom dodanym do sprawy przypisano odpowiednie uprawnienia do zbierania elektronicznych materiałów dowodowych.

9. Po wybraniu osób, które mają zostać dodane jako członkowie sprawy, kliknij przycisk **Dodaj**.

10. Na stronie **Manage this case flyout (Zarządzanie tym przypadkiem** ) kliknij pozycję **Zapisz** , aby zapisać nową listę członków sprawy.

11. Kliknij kartę **Narzędzia** główne, aby przejść do strony głównej sprawy.

## <a name="manage-the-workflow"></a>Zarządzanie przepływem pracy

Aby rozpocząć korzystanie z eDiscovery (Premium), oto podstawowy przepływ pracy, który jest zgodny z [typowymi praktykami zbierania elektronicznych materiałów dowodowych](advanced-ediscovery-edrm.md). W każdym z tych kroków wyróżnimy również niektóre rozszerzone funkcje zbierania elektronicznych materiałów dowodowych (Premium), które można eksplorować.

![Przepływ pracy zbierania elektronicznych materiałów dowodowych (Premium).](../media/AeDWorkflow.png)

1. **[Dodaj opiekunów](add-custodians-to-case.md) i [źródła danych bez opieki](non-custodial-data-sources.md) do sprawy**. Pierwszym krokiem po utworzeniu sprawy jest dodanie opiekunów. *Opiekun to* osoba mająca kontrolę administracyjną nad dokumentem lub elektroniczną dokumentacją, która może być istotna dla sprawy. Ponadto można dodawać źródła danych, które nie są skojarzone z określonym użytkownikiem, ale mogą być istotne dla danego przypadku.

   Oto kilka rzeczy, które się zdarzają (lub które można zrobić) po dodaniu opiekunów do sprawy:

   - Dane w skrzynce pocztowej programu Exchange opiekuna, koncie usługi OneDrive i dowolnych grupach usługi Microsoft Teams lub Yammer, do których należy opiekun, mogą być w tym przypadku "oznaczone" jako dane powiernicze.
  
   - Dane opiekuna są ponownie indeksowane (przez proces o nazwie *Zaawansowane indeksowanie*). Pomaga to zoptymalizować wyszukiwanie w następnym kroku.
  
   - Możesz wstrzymać dane opiekuna. Pozwala to zachować dane, które mogą być istotne dla sprawy podczas badania.
  
   - Inne źródła danych można skojarzyć z opiekunem (na przykład można skojarzyć witrynę programu SharePoint lub grupę platformy Microsoft 365 z opiekunem), aby te dane mogły zostać ponownie wyeksportowane, wstrzymane i przeszukane, podobnie jak dane w skrzynce pocztowej opiekuna lub na koncie usługi OneDrive.

   - Przepływ [pracy komunikacji](managing-custodian-communications.md) w usłudze eDiscovery (Premium) umożliwia wysłanie powiadomienia o blokadzie prawnej do opiekunów.

2. **[Zbierz odpowiednią zawartość ze źródeł danych](create-draft-collection.md)**. Po dodaniu opiekunów i źródeł danych bez nadzoru do sprawy użyj wbudowanego narzędzia kolekcji, aby wyszukać w tych źródłach danych zawartość, która może być istotna dla danego przypadku. Słowa kluczowe, właściwości i warunki umożliwiają [tworzenie zapytań wyszukiwania zwracających](building-search-queries.md) wyniki wyszukiwania z danymi, które najprawdopodobniej są istotne dla danego przypadku. Możesz również:

   - Wyświetl [statystyki kolekcji](collection-statistics-reports.md) , które mogą ułatwić uściślanie kolekcji w celu zawężenia wyników.

   - Wyświetl podgląd przykładu kolekcji, aby szybko sprawdzić, czy znaleziono odpowiednie dane.

   - Popraw zapytanie i uruchom ponownie kolekcję.

3. **[Zatwierdzanie kolekcji do zestawu przeglądów](commit-draft-collection.md)**. Po skonfigurowaniu i zweryfikowaniu, że wyszukiwanie zwraca żądane dane, następnym krokiem jest dodanie wyników wyszukiwania do zestawu przeglądów. Po dodaniu danych do zestawu przeglądów elementy są kopiowane z ich oryginalnej lokalizacji do bezpiecznej lokalizacji usługi Azure Storage. Dane są ponownie analizowane, aby zoptymalizować je pod kątem dokładnych i szybkich wyszukiwań podczas przeglądania i analizowania elementów w zestawie przeglądów. Ponadto możesz również [dodać dane inne niż Office 365 do zestawu przeglądów](load-non-office-365-data-into-a-review-set.md).

   Istnieje również specjalny rodzaj zestawu przeglądów, do których można dodawać dane, nazywany *zestawem przeglądów konwersacji*. Te typy zestawów przeglądów zapewniają możliwości rekonstrukcji konwersacji w celu rekonstruowania, przeglądania i eksportowania wątkowych konwersacji, takich jak te w usłudze Microsoft Teams. Aby uzyskać więcej informacji, zobacz [Przeglądanie konwersacji w usłudze eDiscovery (Premium)](conversation-review-sets.md).

4. **Przeglądanie i analizowanie danych w zestawie przeglądów**. Teraz, gdy dane są w zestawie przeglądów, możesz użyć szerokiej gamy narzędzi i możliwości, aby wyświetlać i analizować dane przypadków w celu zmniejszenia zestawu danych do tego, co jest najbardziej istotne dla badanego przypadku. Poniżej przedstawiono listę niektórych narzędzi i możliwości, których można użyć podczas tego procesu.

   - [Wyświetlanie dokumentów](view-documents-in-review-set.md). Obejmuje to wyświetlanie metadanych dla każdego dokumentu w zestawie przeglądów i wyświetlanie dokumentu w jego natywnej wersji lub wersji tekstowej.

   - [Tworzenie zapytań i filtrów](review-set-search.md). Zapytania wyszukiwania można tworzyć przy użyciu różnych kryteriów wyszukiwania (w tym możliwości przeszukiwania wszystkich [właściwości metadanych pliku](document-metadata-fields-in-advanced-ediscovery.md) w celu dalszego uściślenia i usunięcia danych sprawy do tego, co jest najbardziej istotne dla danego przypadku. Możesz również użyć filtrów zestawu przeglądów, aby szybko zastosować inne warunki do wyników zapytania wyszukiwania w celu dalszego uściślenia tych wyników. 

   - [Tworzenie tagów i korzystanie z nich](tagging-documents.md). Tagi można zastosować do dokumentów w zestawie przeglądów, aby określić, które elementy reagują (lub nie reagują na przypadek), a następnie używać tych tagów podczas tworzenia zapytań wyszukiwania w celu uwzględnienia lub wykluczenia otagowanych dokumentów. Możesz również otagować, aby określić, które dokumenty mają zostać wyeksportowane.

   - [Adnotowanie i redagowanie dokumentów](view-documents-in-review-set.md#annotate-view). Narzędzie adnotacji w recenzji umożliwia dodawanie adnotacji do dokumentów i redagowanie zawartości w dokumentach jako produktu roboczego. Podczas przeglądu generujemy wersję dokumentu z adnotowanymi lub zredagowanymi dokumentami w formacie PDF, aby zmniejszyć ryzyko eksportowania niezredagowanej wersji natywnej dokumentu.

   - [Analizowanie danych przypadków](analyzing-data-in-review-set.md). Funkcja analizy w usłudze eDiscovery (Premium) jest zaawansowana. Po uruchomieniu analizy danych w zestawie przeglądów przeprowadzamy analizy, takie jak wykrywanie niemal duplikatów, wątki wiadomości e-mail i motywy, które mogą pomóc zmniejszyć liczbę dokumentów, które należy przejrzeć. Generujemy również raporty analizy, które podsumowują wynik uruchamiania analizy. Jak wcześniej wyjaśniono, uruchomienie analizy uruchamia również [model wykrywania uprawnień klienta-adwokata](attorney-privilege-detection.md#use-the-attorney-client-privilege-detection-model).

5. **Eksportowanie i pobieranie danych przypadków**. Ostatnim krokiem po zebraniu, przejrzeniu i przeanalizowaniu danych przypadków jest wyeksportowanie ich z zbierania elektronicznych materiałów dowodowych (Premium) do przeglądu zewnętrznego lub do przeglądu przez osoby spoza zespołu dochodzeniowego. Eksportowanie danych jest procesem dwuetapowym. Pierwszym krokiem jest [wyeksportowanie](export-documents-from-review-set.md) danych z zestawu przeglądów i skopiowanie ich do innej lokalizacji usługi Azure Storage (udostępnionej przez firmę Microsoft lub jednej zarządzanej przez organizację). Następnie użyjesz Eksplorator usługi Azure Storage, aby [pobrać](download-export-jobs.md) dane na komputer lokalny. Oprócz wyeksportowanych plików danych zawiera on również raport eksportu, raport podsumowania i raport o błędach.

## <a name="ediscovery-premium-architecture"></a>Architektura zbierania elektronicznych materiałów dowodowych (Premium)

Oto diagram architektury przedstawiający kompleksowy przepływ pracy zbierania elektronicznych materiałów dowodowych (Premium) w środowisku z jednym obszarem geograficznym i w środowisku z wieloma lokalizacjami geograficznymi oraz kompleksowy przepływ danych zgodny z [modelem referencyjnym odnajdywania elektronicznego](overview-ediscovery-20.md#ediscovery-premium-alignment-with-the-electronic-discovery-reference-model).

[![Plakat modelu: Architektura zbierania elektronicznych materiałów dowodowych (Premium) na platformie Microsoft 365.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Wyświetl jako obraz](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Pobieranie jako pliku PDF](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Pobieranie jako pliku programu Visio](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)
