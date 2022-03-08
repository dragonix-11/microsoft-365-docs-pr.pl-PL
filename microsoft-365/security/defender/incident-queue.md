---
title: Określanie priorytetów zdarzeń w Microsoft 365 Defender
description: Dowiedz się, jak filtrować zdarzenia z kolejki zdarzeń w Microsoft 365 Defender
keywords: zdarzenie, kolejka, przegląd, urządzenia, tożsamości, użytkownicy, skrzynka pocztowa, wiadomość e-mail, zdarzenia, analiza, odpowiedź, triage
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
ms.openlocfilehash: 38bfde92a2988cd8bdbca770402af96a4b9c5134
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321835"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Określanie priorytetów zdarzeń w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Microsoft 365 Defender analizy korelacji i agreguje powiązane alerty oraz zautomatyzowane badania z różnych produktów w zdarzenie. Microsoft 365 Defender także wyzwala unikatowe alerty dotyczące działań, które można zidentyfikować wyłącznie jako złośliwe przy całej widoczności Microsoft 365 Defender dla całego pakietu produktów. Ten widok udostępnia analitykom zabezpieczeń szerszą historię ataków, która ułatwia im lepsze zrozumienie złożonych zagrożeń w organizacji i zajmowanie się nimi.

**Kolejka Zdarzenia** zawiera kolekcję zdarzeń utworzonych na różnych urządzeniach, użytkownikach i skrzynkach pocztowych. Ułatwia on sortowanie w ramach zdarzeń w celu priorytetyzowania i tworzenia świadomych decyzji dotyczących reakcji osób, które są nazywane procesem sortowania zdarzeń.

Do kolejki zdarzeń możesz uzyskać dostęp z menu **Zdarzenia & alerty > zdarzenia** na pasku Szybkie uruchamianie portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender zdarzenia.</a> Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Przykład kolejki zdarzeń." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Sekcja **Najnowsze zdarzenia i** alerty zawiera wykres liczby otrzymywanych alertów i zdarzeń utworzonych w ciągu ostatnich 24 godzin.

Domyślnie w kolejce zdarzeń w portalu Microsoft 365 Defender są wyświetlane zdarzenia widziane w ciągu ostatnich sześciu miesięcy. Najnowsze zdarzenie znajduje się na początku listy, więc jest ono najpierw widać.

Kolejka zdarzeń ma dostosowywalne kolumny (wybierz pozycję Wybierz kolumny **), które** zapewniają wgląd w różne cechy zdarzenia lub jednostek, na które ma wpływ zdarzenie. Ułatwia to podejmowanie przejętnych decyzji dotyczących priorytetów zdarzeń w analizie.

Aby mieć dodatkową widoczność, automatyczne nazewnictwo zdarzeń generuje nazwy zdarzeń na podstawie atrybutów alertów, takich jak liczba punktów końcowych, których dotyczy problem, użytkownicy, źródła wykrywania lub kategorie. Umożliwia to szybkie zrozumienie zakresu zdarzenia.

Przykład: *Wieloetapowe zdarzenie dotyczące wielu punktów końcowych zgłoszonych przez wiele źródeł.*

> [!NOTE]
> Nazwy zdarzeń, które istniały przed rozpoczęciem automatycznego nazewnictwa zdarzeń, nie będą się zmieniać.

Kolejka zdarzeń udostępnia również wiele opcji filtrowania, które po zastosowaniu umożliwiają wykonanie szerokiej obsługi wszystkich istniejących zdarzeń w środowisku lub skupienie się na konkretnym scenariuszu lub zagrożeń. Stosowanie filtrów w kolejce zdarzeń może ułatwić ustalenie, które zdarzenie wymaga natychmiastowej uwagi. 

Lista **Filtry** nad listą zdarzeń zawiera aktualnie zastosowane filtry.

## <a name="available-filters"></a>Dostępne filtry

W domyślnej kolejce zdarzeń możesz wybrać pozycję **Filtruj**,  aby wyświetlić okienko filtru, w którym możesz określić filtrowany zestaw zdarzeń. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Przykład okienka filtrów dla kolejki zdarzeń." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Okienko filtru **można też** wyświetlić, wybierając dowolny filtr na liście Filtry nad listą zdarzeń.

W poniższej tabeli wymieniono dostępne nazwy filtrów.

| Nazwa filtru | Opis |
|:-------|:-----|
| Stan | Wybierz **pozycję Nowy**, **W toku** lub **Rozpoznano**. |
| Ważność | Istotność zdarzenia jest często podysycana wpływem tego zdarzenia na twoje zasoby. Im wyższa ważność, tym większy wpływ i zazwyczaj wymaga natychmiastowej uwagi. Wybierz **pozycję** Wysoki, **Średni**, **Niski** **lub Informacyjne**. |
| Przypisanie zdarzenia | Zaznacz przypisanego użytkownika lub użytkowników. |
| Wiele źródeł usługi  | Określ, czy filtr ma być filtrowany dla więcej niż jednego źródła usługi. |
| Źródła usług  | Określ zdarzenia zawierające alerty od: Zarządzanie aplikacjami, Microsoft 365 Defender, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Defender for Cloud Apps. |
| Tagi | Wybierz jedną lub wiele nazw tagów z listy. |
| Wiele kategorii  | Określ, czy filtr ma być dla więcej niż jednej kategorii. |
| Kategorie | Wybieraj kategorie, aby skoncentrować się na konkretnych taktykach, technikach lub elementach ataków. |
| Jednostki | Określ nazwę zasobu, na przykład nazwę użytkownika, urządzenia, skrzynki pocztowej lub aplikacji. |
| Czułość danych | Niektóre ataki koncentrują się na określaniu docelowych grup odbiorców w celu eksfiltrowania poufnych lub wartościowych danych. Stosując filtr dla określonych etykiet wrażliwości, możesz szybko ustalić, czy informacje poufne zostały naruszone, i ustalić priorytet odpowiedzi na te zdarzenia. <br><br> Ten filtr jest dostępny tylko wtedy, Microsoft Information Protection jest włączony. |
| Grupy urządzeń | Określ [nazwę grupy](/windows/security/threat-protection/microsoft-defender-atp/machine-groups) urządzeń. |
| Platforma systemu operacyjnego | Określ systemy operacyjne urządzeń. |
| Klasyfikacja | Określ zestaw klasyfikacji powiązanych alertów. |
| Stan zautomatyzowanego badania | Określ stan zautomatyzowanego badania.  |
| Skojarzone zagrożenie | Określenie nazwanego zagrożenia.  |
| Szybki | Określ nazwany podmiot zagrożenia.  |
|||

Filtr domyślny to wyświetlanie wszystkich alertów i zdarzeń o stanie Nowy i W toku  oraz o  poziomie ważności **Niski,** **Średni** lub **Wysoki**.

Filtr można szybko usunąć, wybierając **znak X** w nazwie filtru na **liście** Filtry. 

## <a name="save-custom-filters-as-urls"></a>Zapisywanie filtrów niestandardowych jako adresów URL

Po skonfigurowaniu przydatnego filtru w kolejce zdarzeń można dodać do zakładek adres URL karty przeglądarki lub zapisać go w inny sposób jako link na stronie internetowej, w dokumencie programu Word lub w wybranej przez ciebie miejscu. Zapewni ci to dostęp jednym kliknięciem do kluczowych widoków kolejki zdarzeń, takich jak:

- Nowe zdarzenia
- Zdarzenia o wysokim poziomie ważności
- Nieprzypisane zdarzenia
- Zdarzenia o wysokim poziomie ważności, nieprzypisane
- Przypisane mi zdarzenia
- Zdarzenia przypisane do mnie i programu Microsoft Defender dla punktu końcowego
- Zdarzenia z określonym tagiem lub znacznikiem
- Zdarzenia z określoną kategorią zagrożeń
- Zdarzenia z określonymi zagrożeniami
- Zdarzenia z określonym aktorem

Po skompilowaniu i przechowywaniu listy użytecznych widoków filtru jako adresów URL można jej używać do szybkiego przetwarzania i ustalania priorytetów zdarzeń w kolejce i zarządzania nimi na podstawie kolejnych zadań i analiz.[](manage-incidents.md)

## <a name="search-for-incidents"></a>Wyszukiwanie zdarzeń

W **polu Wyszukaj nazwę lub identyfikator** nad listą zdarzeń możesz wpisać identyfikator zdarzenia lub nazwę zdarzenia. Po wybraniu zdarzenia z listy wyników wyszukiwania w portalu Microsoft 365 Defender zostanie otwarta nowa karta z właściwościami zdarzenia, z której możesz rozpocząć [badanie](investigate-incidents.md).

## <a name="search-for-impacted-assets"></a>Wyszukiwanie zasobów, których to wpływa

Elementowi zawartości&mdash; można na przykład nazwać użytkownika, urządzenie,&mdash; skrzynkę pocztową lub nazwę aplikacji oraz znaleźć wszystkie powiązane zdarzenia. 

## <a name="specify-a-time-range"></a>Określanie zakresu czasu

Domyślna lista zdarzeń jest dla zdarzeń, które wystąpiły w ciągu ostatnich sześciu miesięcy. Możesz określić nowy zakres czasu w polu listy rozwijanej obok ikony kalendarza, wybierając pozycję:

 - 1 dzień
 - 3 dni
 - 1 tydzień
 - 30 dni
 - 30 dni
 - 6 miesięcy
 - Zakres niestandardowy, w którym można określić daty i godziny

## <a name="next-steps"></a>Następne kroki

Po  określeniu, które zdarzenie wymaga najwyższego priorytetu, zaznacz je i wybierz pozycję:

- [Zarządzanie](manage-incidents.md) właściwościami zdarzenia w przypadku znaczników, przypisania, natychmiastowego rozwiązania w przypadku incydentów fałszywie dodatnich i komentarzy.
- Rozpocznij [badania](investigate-incidents.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie zdarzeń](incidents-overview.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
- [Badanie zdarzeń](investigate-incidents.md)
