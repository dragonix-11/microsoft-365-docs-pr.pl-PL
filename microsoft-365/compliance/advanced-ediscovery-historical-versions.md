---
title: Konfigurowanie wersji historycznych w programie Advanced eDiscovery
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
description: Używaj wersji historycznych w programie Advanced eDiscovery do zbierania zawartości ze wszystkich wersji dokumentów przechowywanych w SharePoint i OneDrive.
ms.openlocfilehash: 5ecbb9c9216482223ce756aed5742e25a3b851a1
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028085"
---
# <a name="set-up-historical-versions-in-advanced-ediscovery-preview"></a>Konfigurowanie wersji historycznych w Advanced eDiscovery (wersja Preview)

Funkcja wersji historycznych w programie Advanced eDiscovery umożliwia menedżerom zbierania elektronicznych materiałów dowodowych w organizacji wyszukiwanie i zbieranie zawartości ze wszystkich wersji dokumentów przechowywanych w usługach SharePoint Online i OneDrive dla Firm. Następnie możesz dodać ją do zestawu recenzji do analizy i recenzji. Ułatwia to znajdowanie i przeglądanie zawartości z określonej wersji dokumentu, która może być istotny w przypadku sprawy lub śledztwa, nawet jeśli najnowsza wersja tego samego dokumentu nie zawiera odpowiednich informacji.

Aby obsługiwać funkcje wersji historycznych w programie Advanced eDiscovery, administratorzy SharePoint muszą włączyć obsługę wersji dla witryn w organizacji. Następnie, gdy użytkownicy modyfikują dokumenty w programie SharePoint lub OneDrive, niejawne wersje zwykłe są tworzone podczas zapisywania dokumentu (lub zapisywane automatycznie). SharePoint umożliwia śledzenie działań wykonywanych na elementach SharePoint (w tym dokumentach, zdarzeniach i zadaniach). Ta funkcja obsługi wersji pozostawia dziennik inspekcji, który może dostarczyć dowodów w ramach dochodzenia prawnego. Te starsze wersje dokumentu są dostępne dla organizacji, od których może być wymagane udostępnianie takich wersji, które mają poufne lub istotne treści podczas odnajdowania sądu w sądzie.

Gdy administrator zbierania elektronicznych materiałów dowodowych włączy wersje historyczne dla organizacji, a następnie aktywuje je dla określonych witryn usługi SharePoint, usługa wypychania zawartości SharePoint przeszukuje wszystkie wersje główne i pomocnicze dokumentów w aktywowanych witrynach, a następnie wysyła te wersje do indeksowania. Po zakończeniu procesu przeszukiwania i indeksowania dokumenty i ich wersje są dostępne do wyszukiwania zbierania elektronicznych materiałów dowodowych. Tak długo, jak konkretną wersję można uzyskać dostęp (na przykład za pomocą historii wersji), ta wersja będzie wykrywalna w Advanced eDiscovery kolekcji.

## <a name="set-up-historical-versions"></a>Konfigurowanie wersji historycznych

Aby włączyć wersje historyczne Advanced eDiscovery w programie Advanced eDiscovery, organizacja musi je włączyć, a następnie aktywować określone witryny tak, aby wszystkie wersje dokumentów przechowywanych w tych witrynach były indeksowane w celu wyszukiwania. Przed skonfigurowaniem Advanced eDiscovery dla wersji historycznych należy włączyć obsługę wersji w SharePoint.

### <a name="step-1-turn-on-versioning-in-sharepoint"></a>Krok 1. Włączanie wersji w aplikacji SharePoint

Pierwszym krokiem jest włączenie sporządzania wersji w aplikacji SharePoint Online w celu zachowywania wszystkich wersji dokumentu. Aby uzyskać instrukcje, [zobacz Versioning in SharePoint](/microsoft-365/community/versioning-basics-best-practices).

### <a name="step-2-turn-on-historical-versions"></a>Krok 2. Włączanie wersji historycznych

Następnym krokiem jest włączenie wersji historycznych w programie Advanced eDiscovery. Aby włączyć wersje historyczne dla organizacji, osoba musi być administratorem globalnym lub administratorem zbierania elektronicznych materiałów dowodowych (członkiem podgrupy Administrator zbierania elektronicznych materiałów dowodowych w grupie ról Menedżer zbierania elektronicznych materiałów dowodowych). Po włączeniu wersji historycznych zostaną one stosowane do całej organizacji.

> [!IMPORTANT]
> Po włączeniu wersji historycznych nie będzie można wyłączyć tej opcji podczas publicznej wersji zapoznawczej. Będzie można wyłączyć to wyłączenie po ogólnym zwolnieniu wersji historycznych.

1. W Centrum zgodności platformy Microsoft 365 przejdź do strony [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764), a następnie kliknij pozycję **Advanced eDiscovery ustawienia**.

   ![Wybierz Advanced eDiscovery ustawienia](..\media\HistoricalVersions1.png)

2. Na stronie **Ustawienia** wybierz kartę Historyczne wersje (wersja **zapoznawcza**), a następnie włącz przełącznik Kontrolka Historycznych **wersji dzierżawy**.

   ![Włączanie przełącznika w celu włączenia wersji historycznych](..\media\HistoricalVersions2.png)

   Zostanie wyświetlone ostrzeżenie z ostrzeżeniem, że nie będzie można wyłączyć wersji historycznych. Jak wspomniano wcześniej, nie będzie można wyłączyć wersji historycznych, dopóki funkcja nie zostanie wydana dla ogólno dostępnej wersji.

3. Kliknij **przycisk Tak** , aby włączyć wersje historyczne.

### <a name="step-3-activate-sharepoint-sites"></a>Krok 3. Aktywowanie SharePoint internetowych

Po włączeniu wersji historycznych dla organizacji ostatnim krokiem jest aktywowanie witryn SharePoint w celu obsługi wersji historycznych. Po aktywowaniu witryny (przez dodanie jej do listy witryn na karcie Wersje historyczne)  witryna jest recrowowana, a wszystkie wersje dokumentów przechowywanych w tej witrynie są indeksowane w celu wyszukiwania.

> [!NOTE]
> W trakcie publicznej wersji zapoznawczej wersji historycznych na organizację jest  limit 100 aktywacji witryn. W przypadku włączenia lub wyłączenia witryny dla wersji historycznych jest wliczane do tego limitu aktywacji. W przypadku włączenia wielu witryn każda witryna jest liczona jako jedna aktywacja. Całkowita liczba aktywacji jest wyświetlana na karcie **Wersje historyczne** .

1. Na karcie **Wersje historyczne** na stronie Advanced eDiscovery **Ustawienia** kliknij pozycję Włącz, aby aktywować witryny dla  wersji historycznych.

   ![Kliknij pozycję Włącz, aby aktywować witryny dla wersji historycznych](..\media\HistoricalVersions3.png)  

   Zostanie wyświetlona wysuuwana strona zawierająca listę wszystkich SharePoint witryny w organizacji.

2. Wybierz witrynę do aktywowania, a następnie kliknij pozycję **Włącz** , aby aktywować ją dla wersji historycznych. Za pomocą pola wyszukiwania można wyszukać określoną witrynę.

   Zostanie wyświetlone ostrzeżenie z ostrzeżeniem, że wersje dokumentów w witrynie zostaną zindeksowane, a ten proces indeksowania będzie trwać jakiś czas, zanim wersje będą gotowe do przeszukania. Ostrzeżenie zawiera również informacje o tym, że nie będzie można wyłączyć wersji historycznych dla wybranej witryny przez 30 dni.

3. Kliknij **przycisk Tak** , aby aktywować witrynę dla wersji historycznych.

   ![Aktywowana witryna i liczba aktywacji witryn są wyświetlane](..\media\HistoricalVersions4.png)  

   Witryna zostanie dodana do listy aktywowanych witryn. Dane licznika pokazujące liczbę aktywacji witryn również zostaną zaktualizowane.

4. Powtórz poprzednie kroki dla każdej witryny, którą chcesz aktywować dla wersji historycznych.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Czym różnią się wersje historyczne od opcji "zbierz wszystkie wersje" po zatwierdzeniu kolekcji roboczej do zestawu recenzji?**

Obecnie tylko najnowsza wersja dokumentów jest indeksowana w celu wyszukiwania. Oznacza to, że po uruchomieniu kolekcji roboczej są przeszukiwane tylko najnowsze wersje dokumentów. Jeśli dokument pasuje do zapytania słów kluczowych dla kolekcji, jest zwracany w wynikach kolekcji. Jeśli jednak najnowsza wersja dokumentu nie pasuje do zapytania wyszukiwania, dokument nie zostanie zwrócony, jeśli starsze wersje dokumentu zawierają słowo kluczowe. Aby zminimalizować tę sytuację, Advanced eDiscovery umożliwia zbieranie wszystkich wersji dokumentu po zatwierdzeniu kolekcji [do zestawu recenzji](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set). Oznacza to, że każda starsza wersja, która może zawierać słowo kluczowe, zostanie dodana do zestawu recenzji.

Wersje historyczne różnią się i są bardziej efektywne niż "gromadzenie wszystkich wersji", ponieważ po aktywowaniu witryny wszystkie wersje dokumentu (a nie tylko ostatnia wersja) są indeksowane w celu wyszukania. Jeśli starsza wersja dokumentu zawiera słowo kluczowe dopasowania do zapytania wyszukiwania, zostanie zwrócone przez kolekcję.

**Czy jeśli dla witryny włączono wersje historyczne, to czy ma to wpływ na jej wydajność?**

L.p. Po włączeniu wersji historycznych dla witryny jej wydajność będzie taka sama jak przed jej obsługą. Procesy przeszukiwania i indeksowania, które są wykonywane w witrynie po jej włączeniu, będą wykonywane w wolniejszym tempie i będą wykonywane poza szczytem. Włączenie wersji historycznych witryny rozpocznie proces wypełniania wstecz, który znajduje wszystkie wersje dokumentów w witrynie, a następnie wysyła te wersje do indeksu. W zależności od liczby wersji dokumentu dla witryny ten proces wypełniania automatycznego może mieć wpływ na kondycję usługi. Ten potencjalny wpływ został zminimalizowany w następujący sposób:

- Staramy się, aby te wersje były przetwarzane w godzinach poza szczytem.

- Przetwarzamy wersje dokumentów w kolejkach o najniższym priorytecie, co umożliwia delegowanie większości zasobów usługi do zmian użytkowników.

**Jak długo muszę czekać na aktywowanie witryny, aż wszystkie historyczne wersje dokumentów w tej witrynie zostaną zindeksowane i będą dostępne do wyszukiwania zbierania elektronicznych materiałów dowodowych?**

Na podstawie liczby dokumentów w witrynie i średniej liczby wersji każdego dokumentu próbujemy oszacować łączną liczbę plików w witrynie. Na jej podstawie szacowany czas indeksowania może być następujący:

`Number of versions / (Processing rate of 100,000 files per day ) + .5 days = Total number of days to process a site`

Pół dnia jest dodawane jako bufor, ponieważ indeksowanie wersji w witrynie jest zoptymalizowane pod kątem pracy poza godzinami szczytu.

Jeśli na przykład łączna liczba dokumentów i wszystkich wersji witryny wynosi 150 000, przetwarzanie witryny dla wersji historycznych zajmie co najmniej dwa dni:

`150,000 files/100,000 files per day + .5 days = 2 days`

**Dlaczego nie zaleca się częstego aktywowania lub dezaktywowania witryn dla wersji historycznych?**

Po dezaktywowaniu wcześniej aktywowanej witryny jest wyzwalany proces oczyszczania. Ten proces może zająć trochę czasu. Jeśli ta sama witryna zostanie ponownie aktywowana, należy ponownie uruchomić proces ponownego wypełniania w celu ponownego wypełnienia witryny. Zarówno procesy oczyszczania, jak i wypełniania pracą z powrotem są procesami wymagania czasu i ilości zasobów. Dlatego zalecamy dokładne rozważenie i zaplanowanie witryn, które mają zostać aktywowane dla wersji historycznej, aby uniknąć wielokrotnego aktywowania i dezaktywowania wersji historycznych witryny.
