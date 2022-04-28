---
title: Konfigurowanie wersji historycznych w usłudze eDiscovery (Premium)
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
description: Użyj wersji historycznych w usłudze eDiscovery (Premium), aby zbierać zawartość ze wszystkich wersji dokumentów przechowywanych w SharePoint i OneDrive.
ms.openlocfilehash: 2b71d79fae15b5bc8bafbf32fc189dad9b314d40
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092552"
---
# <a name="set-up-historical-versions-in-ediscovery-premium-preview"></a>Konfigurowanie wersji historycznych w usłudze eDiscovery (Premium) (wersja zapoznawcza)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Funkcja wersji historycznych w usłudze eDiscovery (Premium) umożliwia menedżerom zbierania elektronicznych materiałów dowodowych w organizacji wyszukiwanie i zbieranie zawartości ze wszystkich wersji dokumentów przechowywanych w SharePoint Online i OneDrive dla Firm. Następnie możesz dodać tę zawartość do zestawu przeglądów do analizy i przeglądu. Ułatwia to znajdowanie i przeglądanie zawartości z określonej wersji dokumentu, która może być istotna dla sprawy lub badania, nawet jeśli najnowsza wersja tego samego dokumentu nie zawiera odpowiednich informacji.

Aby obsługiwać możliwość obsługi wersji historycznych w usłudze eDiscovery (Premium), administratorzy SharePoint muszą włączyć przechowywanie wersji witryn w organizacji. Następnie, gdy użytkownicy modyfikują dokumenty w SharePoint lub OneDrive, niejawne regularne wersje są tworzone podczas zapisywania dokumentu (lub automatycznego zapisywania). SharePoint przechowywanie wersji umożliwia śledzenie działania wykonywanego na SharePoint elementach (w tym dokumentach, zdarzeniach i zadaniach). Ta możliwość przechowywania wersji pozostawia ślad inspekcji, który może dostarczyć dowodów w dochodzeniach prawnych. Te starsze wersje dokumentu są dostępne dla organizacji, która może być zobowiązana do udostępniania takich wersji, które mają poufną lub istotną zawartość podczas odnajdywania przez sąd w sprawach prawnych.

Gdy administrator zbierania elektronicznych materiałów dowodowych włącza wersje historyczne dla organizacji, a następnie aktywuje je dla określonych witryn SharePoint, usługa wypychania zawartości SharePoint przeszukiwa wszystkie główne i pomocnicze wersje dokumentów w uaktywnionych witrynach, a następnie wysyła te wersje do indeksowania. Po zakończeniu procesu przeszukiwania i indeksowania dokumenty i ich wersje są dostępne do wyszukiwania zbierania elektronicznych materiałów dowodowych. Jeśli dostęp do określonej wersji będzie możliwy (według historii wersji), ta wersja będzie odnajdywalna w wyszukiwaniu kolekcji zbierania elektronicznych materiałów dowodowych (Premium).

## <a name="set-up-historical-versions"></a>Konfiguruj wersje historyczne

Aby włączyć wersje historyczne w usłudze eDiscovery (Premium), organizacja musi ją włączyć, a następnie aktywować określone witryny, aby wszystkie wersje dokumentów przechowywanych w tych witrynach były indeksowane do wyszukiwania. Przed skonfigurowanie funkcji eDiscovery (Premium) dla wersji historycznych należy włączyć obsługę wersji w SharePoint.

### <a name="step-1-turn-on-versioning-in-sharepoint"></a>Krok 1. Włączanie obsługi wersji w SharePoint

Pierwszym krokiem jest włączenie obsługi wersji w usłudze SharePoint Online, aby wszystkie wersje dokumentu zostały zachowane. Aby uzyskać instrukcje, zobacz [Versioning in SharePoint (Przechowywanie wersji w SharePoint](/microsoft-365/community/versioning-basics-best-practices)).

### <a name="step-2-turn-on-historical-versions"></a>Krok 2. Włączanie wersji historycznych

Następnym krokiem jest włączenie wersji historycznych w usłudze eDiscovery (Premium). Aby włączyć wersje historyczne dla organizacji, osoba musi być administratorem globalnym lub administratorem zbierania elektronicznych materiałów dowodowych (członkiem podgrupy administratora zbierania elektronicznych materiałów dowodowych w grupie ról Menedżera zbierania elektronicznych materiałów dowodowych). Po włączeniu wersji historycznych będą one stosowane do całej organizacji.

> [!IMPORTANT]
> Po włączeniu wersji historycznych nie będzie można wyłączyć ich w publicznej wersji zapoznawczej. Będzie można go wyłączyć po wydaniu wersji historycznych w celu zapewnienia ogólnej dostępności.

1. W portalu zgodności usługi Microsoft Purview przejdź do obszaru [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764)a następnie kliknij pozycję **Ustawienia zbierania elektronicznych materiałów dowodowych (Premium**).

   ![Wybierz ustawienia zbierania elektronicznych materiałów dowodowych (Premium)](..\media\HistoricalVersions1.png)

2. Na stronie **Ustawienia** wybierz kartę **Wersje historyczne (wersja zapoznawcza**), a następnie przełącz przełącznik **Dzierżawa wersji historycznych** na włączony.

   ![Włącz przełącznik, aby włączyć wersje historyczne](..\media\HistoricalVersions2.png)

   Zostanie wyświetlone ostrzeżenie informujące o tym, że nie będzie można wyłączyć wersji historycznych. Jak wspomniano wcześniej, nie będzie można wyłączyć wersji historycznych, dopóki funkcja nie zostanie wydana w celu zapewnienia ogólnej dostępności.

3. Kliknij przycisk **Tak** , aby włączyć wersje historyczne.

### <a name="step-3-activate-sharepoint-sites"></a>Krok 3. Aktywowanie witryn SharePoint

Po włączeniu wersji historycznych dla organizacji ostatnim krokiem jest aktywowanie SharePoint witryn do obsługi wersji historycznych. Po aktywowaniu witryny (przez dodanie jej do listy witryn na **karcie Wersje historyczne** ) witryna jest ponownie przeszukowana, a wszystkie wersje dokumentów przechowywanych w tej witrynie są indeksowane do wyszukiwania.

> [!NOTE]
> Istnieje limit 100 aktywacji witryn na organizację podczas publicznej wersji zapoznawczej wersji historycznych. Aktywacja jest liczona do tego limitu za każdym razem, gdy włączasz lub wyłączasz witrynę dla wersji historycznych. Jeśli włączysz wiele witryn, każda witryna zostanie zliczona jako pojedyncza aktywacja. Łączna liczba aktywacji jest wyświetlana na **karcie Wersje historyczne** .

1. Na karcie **Wersje historyczne** na stronie **Ustawienia** eDiscovery (Premium) kliknij przycisk **Włącz**, aby aktywować witryny dla wersji historycznych.

   ![Kliknij przycisk Włącz, aby aktywować witryny dla wersji historycznych](..\media\HistoricalVersions3.png)  

   Zostanie wyświetlona strona wysuwana zawierająca listę wszystkich witryn SharePoint w organizacji.

2. Wybierz witrynę do aktywowania, a następnie kliknij przycisk **Włącz** , aby aktywować ją dla wersji historycznych. Możesz użyć pola wyszukiwania, aby wyszukać określoną witrynę.

   Zostanie wyświetlone ostrzeżenie informujące, że wersje dokumentów w witrynie zostaną zindeksowane, a ten proces indeksowania zajmie trochę czasu, zanim wersje będą gotowe do wyszukiwania. Ostrzeżenie oznacza również, że nie będzie można wyłączyć wersji historycznych dla wybranej witryny przez 30 dni.

3. Kliknij przycisk **Tak** , aby aktywować witrynę dla wersji historycznych.

   ![Zostanie wyświetlona aktywowana witryna i liczba aktywacji witryny](..\media\HistoricalVersions4.png)  

   Witryna zostanie dodana do listy aktywowanych witryn. Aktualizowany jest również licznik pokazujący liczbę aktywacji witryny.

4. Powtórz poprzednie kroki dla każdej witryny, którą chcesz aktywować dla wersji historycznych.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Czym różnią się wersje historyczne od opcji "zbieranie wszystkich wersji" podczas zatwierdzania kolekcji roboczej w zestawie przeglądów?**

Obecnie tylko najnowsza wersja dokumentów jest indeksowana do wyszukiwania. Oznacza to, że po uruchomieniu kolekcji roboczej przeszukiwane są tylko najnowsze wersje dokumentów. Jeśli dokument jest zgodny z zapytaniem słowa kluczowego dla kolekcji, jest zwracany w wynikach kolekcji. Jeśli jednak najnowsza wersja dokumentu nie jest zgodna z zapytaniem wyszukiwania, dokument nie zostanie zwrócony, jeśli starsze wersje dokumentu zawierają słowo kluczowe. Aby rozwiązać tę sytuację, funkcja zbierania elektronicznych materiałów dowodowych (Premium) umożliwia zbieranie wszystkich wersji dokumentu podczas [zatwierdzania kolekcji w zestawie przeglądów](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set). Oznacza to, że każda starsza wersja, która może zawierać słowo kluczowe, zostanie dodana do zestawu przeglądów.

Wersje historyczne są inne i bardziej wydajne niż "zbieranie wszystkich wersji", ponieważ po aktywowaniu witryny wszystkie wersje dokumentu (a nie tylko ostatnia wersja) są indeksowane do wyszukiwania. W rezultacie, jeśli starsza wersja dokumentu zawiera słowo kluczowe pasujące do zapytania wyszukiwania, zostanie zwrócone przez kolekcję.

**Czy włączenie wersji historycznych witryny ma wpływ na wydajność witryny?**

L.p. Po włączeniu wersji historycznych dla lokacji wydajność witryny będzie taka sama jak przed włączeniem lokacji. Procesy przeszukiwania i indeksowania wykonywane w lokacji po jej włączeniu będą wykonywane wolniej i będą wykonywane poza godzinami szczytu. Włączenie wersji historycznych witryny spowoduje rozpoczęcie procesu wypełniania, który znajduje wszystkie wersje dokumentów w witrynie, a następnie wysyła te wersje do indeksu. W zależności od liczby wersji dokumentów dla witryny ten proces wypełniania może mieć wpływ na kondycję usługi. Ten potencjalny wpływ został złagodzony w następujący sposób:

- Dokładamy wszelkich starań, aby przetworzyć te wersje poza godzinami szczytu.

- Przetwarzamy wersje dokumentów w kolejkach o najniższym priorytecie, co umożliwia delegowanie większości zasobów usługi do zmian użytkowników.

**Jak długo muszę czekać po aktywowaniu witryny, aż wszystkie historyczne wersje dokumentów w tej witrynie zostaną zindeksowane i będą dostępne do wyszukiwania zbierania elektronicznych materiałów dowodowych?**

Na podstawie liczby dokumentów dla witryny i średniej liczby wersji na dokument próbujemy oszacować całkowitą liczbę plików na witrynę. Na tej podstawie oszacowanie, jak długo może potrwać indeksowanie, jest następujące:

`Number of versions / (Processing rate of 100,000 files per day ) + .5 days = Total number of days to process a site`

Pół dnia jest dodawany jako bufor, ponieważ indeksowanie wersji w lokacji jest zoptymalizowane pod kątem uruchamiania poza godzinami szczytu.

Jeśli na przykład łączna liczba dokumentów i wszystkie wersje witryny to 150 000, przetworzenie witryny pod kątem wersji historycznych potrwa co najmniej dwa dni:

`150,000 files/100,000 files per day + .5 days = 2 days`

**Dlaczego nie zaleca się częstego aktywowania lub dezaktywowania witryn dla wersji historycznych?**

Po dezaktywowaniu wcześniej aktywowanej witryny zostanie wyzwolony proces oczyszczania. Ukończenie tego procesu zajmie trochę czasu. Jeśli ta sama lokacja zostanie ponownie aktywowana, należy ponownie uruchomić proces ponownego wypełniania lokacji. Zarówno procesy oczyszczania, jak i wypełniania kopii zapasowych są czasochłonne i intensywnie obciążają zasoby. Dlatego zalecamy dokładne rozważenie i zaplanowanie witryn, które chcesz aktywować dla wersji historycznej, aby uniknąć wielokrotnego aktywowania i dezaktywowania wersji historycznych witryny.
