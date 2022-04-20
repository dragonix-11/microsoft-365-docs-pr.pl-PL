---
title: Określanie priorytetów zdarzeń w Microsoft 365 Defender
description: Dowiedz się, jak filtrować zdarzenia z kolejki zdarzeń w Microsoft 365 Defender
keywords: zdarzenie, kolejka, przegląd, urządzenia, tożsamości, użytkownicy, skrzynka pocztowa, poczta e-mail, zdarzenia, analizowanie, reagowanie, klasyfikacja
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 285da473c8e8035a28ee6e64c4950e2b8fe373f5
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944420"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Określanie priorytetów zdarzeń w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Microsoft 365 Defender stosuje analizę korelacji oraz agreguje powiązane alerty i zautomatyzowane badania z różnych produktów w przypadku zdarzenia. Microsoft 365 Defender wyzwala również unikatowe alerty dotyczące działań, które można zidentyfikować tylko jako złośliwe, biorąc pod uwagę kompleksowy wgląd w Microsoft 365 Defender w całym zestawie produktów. Ten widok zapewnia analitykom zabezpieczeń szerszą historię ataków, która pomaga im lepiej zrozumieć złożone zagrożenia w całej organizacji i radzić sobie z nimi.

**Kolejka Zdarzenia** zawiera kolekcję zdarzeń, które zostały utworzone na różnych urządzeniach, użytkownikach i skrzynkach pocztowych. Ułatwia ona sortowanie zdarzeń w celu określenia priorytetów i utworzenia świadomej decyzji dotyczącej reagowania na cyberbezpieczeństwo, czyli procesu znanego jako klasyfikacja incydentów.

Do kolejki zdarzeń można przejść z poziomu **alertów & zdarzeń > incydentów** przy szybkim uruchomieniu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Sekcja Zdarzenie przedstawiająca kolejkę zdarzeń w portalu Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

W sekcji **Najnowsze zdarzenia i alerty** przedstawiono wykres liczby odebranych alertów i zdarzeń utworzonych w ciągu ostatnich 24 godzin.

Domyślnie kolejka zdarzeń w portalu Microsoft 365 Defender wyświetla zdarzenia widoczne w ciągu ostatnich sześciu miesięcy. Ostatnie zdarzenie znajduje się na górze listy, więc możesz je najpierw zobaczyć.

Kolejka zdarzeń ma dostosowywalne kolumny (wybierz pozycję **Wybierz kolumny**), które zapewniają wgląd w różne cechy zdarzenia lub jednostki, których dotyczy problem. Ułatwia to podjęcie świadomej decyzji dotyczącej priorytetyzacji zdarzeń na potrzeby analizy.

Aby szybko uzyskać dodatkowy wgląd, automatyczne nazewnictwo zdarzeń generuje nazwy zdarzeń na podstawie atrybutów alertów, takich jak liczba punktów końcowych, których dotyczy problem, użytkownicy, których dotyczy problem, źródła wykrywania lub kategorie. Dzięki temu można szybko zrozumieć zakres zdarzenia.

Na przykład: *Zdarzenie wieloetapowe w wielu punktach końcowych zgłaszanych przez wiele źródeł.*

> [!NOTE]
> Zdarzenia, które istniały przed wprowadzeniem automatycznego nazewnictwa zdarzeń, nie będą miały zmienionej nazwy.

Kolejka zdarzeń udostępnia również wiele opcji filtrowania, które po zastosowaniu umożliwiają przeprowadzenie szerokiego zakresu wszystkich istniejących zdarzeń w środowisku lub podjęcie decyzji o skoncentrowaniu się na konkretnym scenariuszu lub zagrożeniu. Zastosowanie filtrów w kolejce zdarzeń może pomóc w określeniu, które zdarzenie wymaga natychmiastowej uwagi. 

Na liście **Filtry** powyżej listy zdarzeń są wyświetlane aktualnie zastosowane filtry.

## <a name="available-filters"></a>Dostępne filtry

W domyślnej kolejce zdarzeń możesz wybrać pozycję **Filtruj** , aby wyświetlić okienko **Filtr** , z którego można określić filtrowany zestaw zdarzeń. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Okienko Filtry dla kolejki zdarzeń w portalu Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Możesz również wyświetlić okienko **Filtr** , wybierając dowolny z filtrów na liście **Filtry** powyżej listy zdarzeń.

W tej tabeli wymieniono dostępne nazwy filtrów.

| Nazwa filtru | Opis |
|:-------|:-----|
| Stan | Wybierz pozycję **Nowy**, **W toku** lub **Rozwiązano**. |
| Ważności | Ważność zdarzenia wskazuje na jego wpływ na zasoby. Im większa ważność, tym większy wpływ i zwykle wymaga natychmiastowej uwagi. Wybierz pozycję **Wysoki**, **Średni**, **Niski** lub **Informacyjny**. |
| Przypisanie zdarzenia | Wybierz przypisanego użytkownika lub użytkowników. |
| Wiele źródeł usług  | Określ, czy filtr jest przeznaczony dla więcej niż jednego źródła usługi. |
| Źródła usług  | Określ zdarzenia zawierające alerty z: Zarządzanie aplikacjami, Microsoft 365 Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender, Microsoft Defender for Identity, Microsoft Defender for Cloud Apps. |
| Tagi | Wybierz jedną lub wiele nazw tagów z listy. |
| Wiele kategorii  | Określ, czy filtr jest przeznaczony dla więcej niż jednej kategorii. |
| Kategorie | Wybierz kategorie, aby skoncentrować się na określonych taktykach, technikach lub widocznych składnikach ataku. |
| Podmioty | Określ nazwę zasobu, takiego jak użytkownik, urządzenie, skrzynka pocztowa lub nazwa aplikacji. |
| Poufność danych | Niektóre ataki koncentrują się na celowaniu w celu eksfiltrowania poufnych lub cennych danych. Stosując filtr dla określonych etykiet poufności, można szybko określić, czy informacje poufne zostały potencjalnie naruszone i nadać priorytet tym incydentom. <br><br> Ten filtr wyświetla informacje tylko po zastosowaniu [etykiet poufności z usługi Microsoft Purview Information Protection](../../compliance/sensitivity-labels.md). |
| Grupy urządzeń | Określ nazwę [grupy urządzeń](/windows/security/threat-protection/microsoft-defender-atp/machine-groups) . |
| Platforma systemu operacyjnego | Określ systemy operacyjne urządzeń. |
| Klasyfikacji | Określ zestaw klasyfikacji powiązanych alertów. |
| Stan zautomatyzowanego badania | Określ stan zautomatyzowanego badania.  |
| Skojarzone zagrożenie | Określ nazwane zagrożenie.  |
| Aktorów | Określ nazwanego aktora zagrożeń.  |
|||

Filtr domyślny to wyświetlanie wszystkich alertów i zdarzeń o stanie **Nowy** i **W toku** oraz o ważności **Niski**, **Średni** lub **Wysoki**.

Możesz szybko usunąć filtr, wybierając znak **X** w nazwie filtru na liście **Filtry** . 

## <a name="save-custom-filters-as-urls"></a>Zapisywanie filtrów niestandardowych jako adresów URL

Po skonfigurowaniu przydatnego filtru w kolejce zdarzeń możesz dodać do zakładki adres URL karty przeglądarki lub w inny sposób zapisać go jako link na stronie sieci Web, dokumencie programu Word lub wybranym miejscu. Zapewni to dostęp jednym kliknięciem do kluczowych widoków kolejki zdarzeń, takich jak:

- Nowe zdarzenia
- Zdarzenia o wysokiej ważności
- Nieprzypisane zdarzenia
- Zdarzenia o wysokiej ważności, nieprzypisane
- Zdarzenia przypisane do mnie
- Zdarzenia przypisane do mnie i dla Ochrona punktu końcowego w usłudze Microsoft Defender
- Zdarzenia z określonym tagiem lub tagami
- Zdarzenia z określoną kategorią zagrożeń
- Incydenty z określonym powiązanym zagrożeniem
- Incydenty z określonym aktorem

Po skompilowaniu i zapisaniu listy przydatnych widoków filtrów jako adresów URL można go użyć do szybkiego przetwarzania i określania priorytetów zdarzeń w kolejce oraz [zarządzania](manage-incidents.md) nimi w celu późniejszego przypisania i analizy.

## <a name="search-for-incidents"></a>Wyszukiwanie zdarzeń

W polu **Wyszukaj nazwę lub identyfikator** powyżej listy zdarzeń możesz wpisać identyfikator zdarzenia lub nazwę zdarzenia. Po wybraniu zdarzenia z listy wyników wyszukiwania portal Microsoft 365 Defender otwiera nową kartę z właściwościami zdarzenia, z której można rozpocząć [badanie](investigate-incidents.md).

## <a name="search-for-impacted-assets"></a>Wyszukiwanie zasobów, których dotyczy problem

Możesz nazwać element zawartości&mdash; jako nazwę użytkownika, urządzenia, skrzynki pocztowej lub aplikacji&mdash; i znaleźć wszystkie powiązane zdarzenia. 

## <a name="specify-a-time-range"></a>Określanie zakresu czasu

Domyślna lista zdarzeń dotyczy zdarzeń, które miały miejsce w ciągu ostatnich sześciu miesięcy. Możesz określić nowy zakres czasu z listy rozwijanej obok ikony kalendarza, wybierając następujące opcje:

 - 1 dzień
 - 3 dni
 - 1 tydzień
 - 30 dni
 - 30 dni
 - 6 miesięcy
 - Zakres niestandardowy, w którym można określić daty i godziny

## <a name="next-steps"></a>Następne kroki

Po określeniu, które zdarzenie wymaga najwyższego priorytetu, wybierz go i:

- [Zarządzaj właściwościami](manage-incidents.md) zdarzenia dla tagów, przypisania, natychmiastowego rozwiązania zdarzeń fałszywie dodatnich i komentarzy.
- Rozpocznij [badania](investigate-incidents.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie zdarzeń](incidents-overview.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
- [Badanie zdarzeń](investigate-incidents.md)
