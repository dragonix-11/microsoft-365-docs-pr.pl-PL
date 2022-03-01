---
title: Tworzenie spraw Advanced eDiscovery w Microsoft 365 i zarządzanie nimi
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
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
description: W tym artykule opisano, jak tworzyć sprawy Advanced eDiscovery i zarządzać nimi. Pierwszym krokiem jest utworzenie sprawy i rozpoczęcie korzystania Advanced eDiscovery funkcji.
ms.openlocfilehash: f647421dcaba3d50f1cb8b7a6b1e58a792f23403
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998911"
---
# <a name="create-and-manage-an-advanced-ediscovery-case"></a>Tworzenie sprawy Advanced eDiscovery i zarządzanie nimi

Po skonfigurowaniu Advanced eDiscovery i przypisaniu uprawnień [](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions) menedżerom zbierania elektronicznych materiałów dowodowych w Twojej organizacji, które będą zarządzać sprawami, następnym krokiem jest utworzenie sprawy i zarządzanie nią.

Ten artykuł zawiera również ogólne omówienie korzystania ze spraw do zarządzania przepływem pracy Advanced eDiscovery w przypadku postępowania sądowego lub innego rodzaju dochodzenia.

## <a name="create-a-case"></a>Tworzenie sprawy

Wykonaj poniższe czynności, aby utworzyć sprawę i dodać członków. Użytkownik, który tworzy sprawę, jest automatycznie dodawany jako członek. Członkowie sprawy mogą uzyskać dostęp do sprawy w Centrum zgodności platformy Microsoft 365 i wykonywać Advanced eDiscovery zadania.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i zaloguj się przy użyciu poświadczeń dla konta użytkownika, do których przypisano uprawnienia zbierania elektronicznych materiałów dowodowych. Członkowie grupy ról Zarządzanie organizacją mogą również tworzyć Advanced eDiscovery spraw.

2. W lewym okienku nawigacji okna Centrum zgodności platformy Microsoft 365 kliknij pozycję Pokaż **wszystko, a** następnie wybierz **pozycję zbierania elektronicznych** >  materiałów dowodowychAdvanced, a następnie wybierz <a href="https://go.microsoft.com/fwlink/p/?linkid=2173764" target="_blank">**kartę** Sprawy</a>.

3. Wybierz **pozycję Utwórz sprawę**.

4. Na stronie **wysuwana nowa sprawa zbierania** elektronicznych materiałów dowodowych nadaj sprawę nazwę (wymagane), a następnie wpisz opcjonalny numer sprawy i opis. Nazwa sprawy musi być unikatowa w Twojej organizacji.

5. Kliknij **przycisk Zapisz** , aby utworzyć sprawę.

   Zostanie utworzona nowa sprawa **i Ustawienia w** nowej sprawie.

6. Na **kafelku & uprawnień** dostępu na **karcie** Ustawienia kliknij pozycję **Wybierz**.

7. Na stronie **wysuwana Zarządzanie tą sprawą** w obszarze **Zarządzanie** członkami kliknij pozycję **Dodaj** , aby dodać członków do sprawy.

8. Na liście osób zaznacz pole wyboru obok nazwisk osób, które chcesz dodać do sprawy. Jak wyjaśniono wcześniej, upewnij się, że osobom, które dodasz do sprawy, zostały przypisane odpowiednie uprawnienia zbierania elektronicznych materiałów dowodowych.

9. Po wybraniu osób, które mają być dodawać jako członków sprawy, kliknij pozycję **Dodaj**.

10. Na stronie **wysuwana Zarządzanie tą sprawą** kliknij pozycję **Zapisz** , aby zapisać nową listę członków sprawy.

11. Kliknij **kartę Narzędzia** główne, aby przejść do strony głównej sprawy.

## <a name="manage-the-workflow"></a>Zarządzanie przepływem pracy

Aby rozpocząć korzystanie z Advanced eDiscovery, oto podstawowy przepływ pracy, który jest dostosowany do typowych praktyk zbierania [elektronicznych materiałów dowodowych](advanced-ediscovery-edrm.md). W każdej z tych czynności wyróżnimy też niektóre rozszerzone funkcje Advanced eDiscovery, które można eksplorować.

![Advanced eDiscovery przepływu pracy.](../media/AeDWorkflow.png)

1. **[Dodaj do sprawy także](add-custodians-to-case.md) źródła danych, [które nie są](non-custodial-data-sources.md) odimowywne**. Pierwszym krokiem po utworzeniu sprawy jest dodanie osób- opiekunów. Jest *to osoba* , która ma kontrolę administracyjną nad dokumentem lub plikiem elektronicznym, która może być istotny w danej sprawie. Ponadto można dodawać źródła danych, które nie są skojarzone z określonym użytkownikiem, ale mogą być istotne dla danej sprawy.

   Oto niektóre zdarzenia, które mogą się zdarzyć (lub które można wykonać) podczas dodawania osób do sprawy:

   - Dane w skrzynce pocztowej usługi Exchange użytkownika, koncie programu OneDrive i wszystkich grupach Microsoft Teams lub Yammer, których jest członkiem, mogą zostać "oznaczone" jako dane częściowe w tym przypadku.
  
   - Dane pochłoną się ponownie (przez proces o nazwie *Indeksowanie zaawansowane*). Ułatwia to optymalizację wyszukiwania w następnym kroku.
  
   - Możesz umieścić w tym miejscu dane, które nie są już odłogiem. Zachowuje to dane, które mogą być istotne dla danej sprawy w trakcie badania.
  
   - Z innymi źródłami danych można skojarzyć opiekuna (na przykład witrynę programu SharePoint lub grupę programu Microsoft 365 z opiekunem), aby można było ponownie zindeksowane dane, umieścić je w posiadaniu i wyszukiwać, podobnie jak dane w skrzynce pocztowej użytkownika lub koncie OneDrive.

   - Przepływ pracy [komunikacji w](managing-custodian-communications.md) programie Advanced eDiscovery do wysyłania powiadomień o wstrzymaniu ze względu na prawo do osób odbieranych.

2. **[Zbierz odpowiednią zawartość ze źródeł danych](create-draft-collection.md)**. Po dodaniu do sprawy materiałów do przechowywania danych i źródeł danych, które nie są zbędne, użyj wbudowanego narzędzia do zbierania danych, aby wyszukać w tych źródłach danych zawartość, która może być istotny w danej sytuacji. Za pomocą słów kluczowych, właściwości i warunków można [](building-search-queries.md) tworzyć zapytania wyszukiwania zwracające wyniki wyszukiwania z danymi, które najprawdopodobniej są istotne dla danej sprawy. Możesz również:

   - Wyświetl [statystyki kolekcji](collection-statistics-reports.md) , które mogą pomóc uściślić kolekcję w celu zawężenia wyników.

   - Wyświetl podgląd próbki kolekcji, aby szybko sprawdzić, czy odpowiednie dane są znalezione.

   - Popraw zapytanie i ponownie uruchomić kolekcję.

3. **[Zatwierdzanie kolekcji do zestawu recenzji](commit-draft-collection.md)**. Po skonfigurowaniu i zweryfikowaniu, że wyszukiwanie zwraca żądane dane, następnym krokiem jest dodanie wyników wyszukiwania do zestawu recenzji. Podczas dodawania danych do zestawu recenzji elementy są kopiowane z ich oryginalnej lokalizacji do bezpiecznej lokalizacji Storage Azure. Ponowne indeksowanie danych zapewnia dokładne i szybkie wyszukiwanie podczas przeglądania i analizowania elementów w zestawie recenzji. Do zestawu recenzji można również dodawać Office 365 [inne niż dane](load-non-office-365-data-into-a-review-set.md).

   Istnieje również specjalny rodzaj zestawu recenzji, do który możesz dodawać dane, nazywany *zestawem recenzji konwersacji*. Te typy zestawów recenzji zapewniają możliwości rekonstruowania, przeglądania i eksportowania konwersacji z wątkami, takich jak konwersacje Microsoft Teams. Aby uzyskać więcej informacji, zobacz [Przeglądanie konwersacji w Advanced eDiscovery](conversation-review-sets.md).

4. **Przeglądanie i analizowanie danych w zestawie recenzji**. Teraz, gdy dane są w zestawie recenzji, możesz użyć wielu różnych narzędzi i możliwości do wyświetlania i analizowania danych sprawy w celu ograniczenia zestawu danych do tego, co jest najbardziej istotne dla sprawy, której badasz. Poniżej znajdziesz listę niektórych narzędzi i możliwości, których można używać w ramach tego procesu.

   - [Wyświetlanie dokumentów](view-documents-in-review-set.md). Obejmuje to wyświetlanie metadanych dla każdego dokumentu w zestawie recenzji oraz wyświetlanie dokumentu w jego natywnej wersji lub w wersji tekstowej.

   - [Tworzenie zapytań i filtrów](review-set-search.md). Zapytania wyszukiwania tworzy się przy użyciu różnych kryteriów wyszukiwania (w tym możliwości przeszukiwania [](document-metadata-fields-in-advanced-ediscovery.md) wszystkich właściwości metadanych pliku w celu uściślenia i zwątowania danych dotyczących sprawy do tego, co jest najważniejsze. Możesz również użyć filtrów zestawu recenzji, aby szybko zastosować inne warunki do wyników zapytania wyszukiwania, aby jeszcze bardziej uściślić te wyniki. 

   - [Tworzenie i używanie tagów](tagging-documents.md). Tagi można stosować do dokumentów w zestawie recenzji, aby określić, które z nich są reagują (lub nie reagują na nie), a następnie używać tych tagów podczas tworzenia zapytań wyszukiwania, aby uwzględnić lub wykluczyć oznakowane dokumenty. Możesz również otagować dokumenty, aby określić, które dokumenty mają zostać wyeksportowane.

   - [Donosz adnotacje do dokumentów i redaguj je](view-documents-in-review-set.md#annotate-view). Do dodawania adnotacji do dokumentów i redagowania zawartości w dokumentach jako produktu służbowego można używać narzędzia adnotacji w recenzji. Podczas przeglądania jest generowana wersja PDF dokumentu z adnotacjami lub redagowana, aby zmniejszyć ryzyko eksportowania nieoznaczonej natywnej wersji dokumentu.

   - [Analizowanie danych dotyczących sprawy](analyzing-data-in-review-set.md). Funkcje analizy w p Advanced eDiscovery są bardzo zaawansowane. Po uruchomieniu analizy danych w zestawie recenzji przeprowadzamy analizę, taką jak niemal zduplikowane wykrywanie, wątkowanie wiadomości e-mail i motywy, które mogą zmniejszyć liczbę dokumentów do przejrzenia. Generujemy również raporty analizy, które podsumowują wyniki uruchomionej analizy. Jak wyjaśniono wcześniej, uruchomienie analizy uruchamia również [model wykrywania uprawnień klienta-obsługi klienta](attorney-privilege-detection.md#use-the-attorney-client-privilege-detection-model).

5. **Eksportowanie i pobieranie danych sprawy**. Ostatnim krokiem po zgromadzeniu, przejrzeniu i przeanalizowaniu danych sprawy jest wyeksportowanie ich z usługi Advanced eDiscovery do przeglądu zewnętrznego lub do przeglądu przez osoby spoza zespołu badania. Eksportowanie danych jest procesem dwuetapowym. Pierwszym krokiem jest [wyeksportowanie](export-documents-from-review-set.md) danych z zestawu recenzji i skopiowanie ich do innej lokalizacji usługi Azure Storage (udostępnianej przez firmę Microsoft lub zarządzanej przez Twoją organizację). Następnie za pomocą Eksplorator usługi Azure Storage [pobrać](download-export-jobs.md) dane na komputer lokalny. Oprócz wyeksportowanych plików danych pakiet eksportu zawiera również raport eksportu, raport podsumowujący i raport o błędach.

## <a name="advanced-ediscovery-architecture"></a>Advanced eDiscovery architekturze

Oto diagram architektury przedstawiający uniwersalny przepływ pracy programu Advanced eDiscovery w środowisku jednolokalowym i w środowisku wielolokalowym oraz przepływ danych, który jest wyrównany do modelu EDT ([Electronic Discovery Reference Model](overview-ediscovery-20.md#advanced-ediscovery-alignment-with-the-electronic-discovery-reference-model)).

[![Plakat modelu: architektura Advanced eDiscovery w Microsoft 365.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Wyświetl jako obraz](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Pobierz jako plik PDF](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Pobierz jako plik Visio pliku](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)
