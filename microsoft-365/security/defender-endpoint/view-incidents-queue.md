---
title: Wyświetlanie i organizowanie kolejki Zdarzenia
ms.reviewer: ''
description: Zapoznaj się z listą zdarzeń i dowiedz się, jak stosować filtry w celu ograniczenia listy i uzyskania bardziej szczegółowego widoku.
keywords: wyświetlanie, organizowanie, zdarzenia, agregowanie, badania, kolejkowanie, ttp
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d57097d255b9f64782320dbd380f90b7a98573cb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "63007881"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-incidents-queue"></a>Wyświetlanie i organizowanie kolejki zdarzenia punktu końcowego programu Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

W **kolejce Zdarzenia** jest pokazany zbiór zdarzeń oflagowanych na urządzeniach w Twojej sieci. Ułatwia on sortowanie zdarzeń w celu priorytetyzowanie i tworzenie świadomych decyzji dotyczących reakcji osób, które zechcą na nie odtworzyć.

Domyślnie w kolejce są wyświetlane zdarzenia z ostatnich 30 dni, a najnowsze zdarzenie jest wyświetlane u góry listy, co pomaga najpierw zobaczyć najnowsze zdarzenia.

Istnieje kilka opcji, które można wybrać, aby dostosować widok kolejki Zdarzenia. 

W górnym okienku nawigacji możesz:
- Dostosowywanie kolumn w celu dodania lub usunięcia kolumn 
- Modyfikowanie liczby elementów do wyświetlenia na stronie
- Wybieranie elementów do pokazania na stronie
- Wybierz wsadowe zdarzenia do przypisania 
- Nawigowanie między stronami
- Stosowanie filtrów

![Obraz kolejki zdarzeń.](images/atp-incident-queue.png)

## <a name="sort-and-filter-the-incidents-queue"></a>Sortowanie i filtrowanie kolejki zdarzeń
Aby ograniczyć listę zdarzeń i uzyskać bardziej skoncentrowany widok, możesz zastosować następujące filtry.

### <a name="severity"></a>Ważność

Ważność zdarzenia | Opis
:---|:---
High (Wysoki) </br>(Czerwony) | Zagrożenia często są skojarzone z zaawansowanymi trwałymi zagrożeniami (MZ). Te zdarzenia oznaczają duże ryzyko ze względu na poważne szkody, które mogą one spowodować na urządzeniach.
Średni </br>(Orange) | Zagrożenia rzadko obserwowane w organizacji, takie jak anomalalna zmiana rejestru, wykonywanie podejrzanych plików i obserwowane zachowania typowe dla etapów ataków.
Niska </br>(Żółty) | Zagrożenia związane z rozpowszechnionym złośliwym oprogramowaniem i narzędziami do łamania informacji, które nie muszą oznaczać zaawansowanego zagrożenia skierowanego do organizacji.
Informacyjne </br>(Szary) | Zdarzenia informacyjne mogą nie być uznawane za niebezpieczne dla sieci, ale warto śledzić je.

## <a name="assigned-to"></a>Przypisane do
Możesz filtrować listę, wybierając pozycję przypisaną do wszystkich lub osób przypisanych do Ciebie.

### <a name="category"></a>Kategoria
Zdarzenia są kategoryzowane na podstawie opisu etapu, w którym znajduje się łańcuch kill-chain. Ten widok ułatwia analitykowi zagrożeń ustalenie priorytetu, pilności i odpowiadającej mu strategii reagowania na wdrożenie na podstawie kontekstu.

### <a name="status"></a>Stan
Możesz ograniczyć listę wyświetlanych zdarzeń na podstawie ich stanu, aby sprawdzić, które z nich są aktywne lub rozwiązane.

### <a name="data-sensitivity"></a>Czułość danych
Filtr ten umożliwia pokazanie zdarzeń zawierających etykiety wrażliwości.

## <a name="incident-naming"></a>Nazewnictwo zdarzeń

Aby w skrócie zrozumieć zakres zdarzenia, nazwy zdarzeń są generowane automatycznie na podstawie atrybutów alertów, takich jak liczba punktów końcowych, których dotyczy problem, użytkownicy, źródła wykrywania lub kategorie.

Przykład: *Wieloetapowe zdarzenie dotyczące wielu punktów końcowych zgłoszonych przez wiele źródeł.*

> [!NOTE]
> Zdarzenia, które istniały przed rozpoczęciem automatycznego nazewnictwa zdarzeń, zachowają swoje imię i nazwisko.


## <a name="see-also"></a>Zobacz też
- [Kolejka zdarzeń](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Zarządzanie zdarzeniami](manage-incidents.md)
- [Badanie zdarzeń](investigate-incidents.md)

