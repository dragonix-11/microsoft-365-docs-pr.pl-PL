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
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: fafb48af3aa0c38146073a0682323496bc0431e2
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015392"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Określanie priorytetów zdarzeń w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Microsoft 365 Defender analizy korelacji i agreguje powiązane alerty oraz zautomatyzowane badania z różnych produktów w zdarzenie. Microsoft 365 Defender także wyzwala unikatowe alerty dotyczące działań, które można zidentyfikować wyłącznie jako złośliwe przy całej widoczności Microsoft 365 Defender dla całego pakietu produktów. Ten widok udostępnia analitykom zabezpieczeń szerszą historię ataków, która ułatwia im lepsze zrozumienie złożonych zagrożeń w organizacji i zajmowanie się nimi.

**Kolejka Zdarzenia** zawiera kolekcję zdarzeń utworzonych na różnych urządzeniach, użytkownikach i skrzynkach pocztowych. Ułatwia on sortowanie zdarzeń w celu priorytetyzowanie i tworzenie świadomych decyzji dotyczących reakcji osób, które zechcą na nie odtworzyć. Ta nazywane jest również trygoną zdarzeń.

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

## <a name="available-filters"></a>Dostępne filtry

W domyślnej kolejce zdarzeń możesz wybrać pozycję  Filtry, aby wyświetlić okienko Filtry, w którym możesz wyświetlić filtrowany zestaw zdarzeń. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Przykład okienka filtrów dla kolejki zdarzeń." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Filtr domyślny to wyświetlanie wszystkich alertów i zdarzeń w stanie **Nowy** **i W toku** .

W poniższej tabeli wymieniono dostępne nazwy filtrów.

| Nazwa filtru | Opis |
|:-------|:-----|
| Stan | Wybierz **pozycję Nowy**, **W toku** lub **Rozpoznano**. |
| Ważność | Istotność zdarzenia jest często podysycana wpływem tego zdarzenia na twoje zasoby. Im wyższa ważność, tym większy wpływ i zazwyczaj wymaga natychmiastowej uwagi. Wybierz **pozycję** Wysoki, **Średni**, **Niski** **lub Informacyjne**. |
| Przypisanie zdarzenia | Wybierz pozycję Przypisane do wszystkich, Przypisane do mnie lub Nieprzypisane. |
| Wiele źródeł usługi  | Określ, czy filtr ma być filtrowany dla więcej niż jednego źródła usługi. |
| Źródła usług  | Filtruj, aby zobaczyć tylko zdarzenia zawierające alerty od: Zarządzanie aplikacjami, Microsoft 365 Defender, Microsoft Defender dla programu Office 365, Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Defender for Cloud Apps. |
| Tagi | Wybierz jedną lub wiele nazw tagów z listy. |
| Wiele kategorii  | Określ, czy filtr ma być dla więcej niż jednej kategorii. |
| Kategorie | Wybieraj kategorie, aby skoncentrować się na konkretnych taktykach, technikach lub elementach ataków. |
| Platforma systemu operacyjnego | Ogranicz widok kolejki zdarzeń według systemu operacyjnego. |
| Klasyfikacja | Filtrowanie zdarzeń na podstawie klasyfikacji określonych alertów pokrewnych. Wybierz **pozycję Prawda alertu**, **Alerty fałsz** lub **Nie ustawiono**. |
| Stan badania | Filtrowanie zdarzeń według stanu automatycznego badania.  |
| Skojarzone zagrożenie | Filtrowanie zdarzeń według nazwanego zagrożenia.  |
| Szybki | Filtrowanie zdarzeń według nazwanego podmiotu zagrożenia.  |
| Czułość danych | Niektóre ataki koncentrują się na określaniu docelowych grup odbiorców w celu eksfiltrowania poufnych lub wartościowych danych. Stosując filtr w celu ustalenia, czy w zdarzeniu biorą udział poufne dane, można szybko ustalić, czy informacje poufne zostały potencjalnie naruszone, i ustalić priorytety związane z tymi zdarzeniami. <br><br>Ten filtr jest dostępny tylko wtedy, Microsoft Information Protection jest włączony.|
|||

## <a name="save-defined-filters-as-urls"></a>Zapisywanie zdefiniowanych filtrów jako adresów URL

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

## <a name="next-steps"></a>Następne kroki

Po  określeniu, które zdarzenie wymaga najwyższego priorytetu, zaznacz je i wybierz pozycję:

- [Zarządzanie](manage-incidents.md) właściwościami zdarzenia w przypadku znaczników, przypisania, natychmiastowego rozwiązania w przypadku incydentów fałszywie dodatnich i komentarzy.
- Rozpocznij [badania](investigate-incidents.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie zdarzeń](incidents-overview.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
- [Badanie zdarzeń](investigate-incidents.md)
