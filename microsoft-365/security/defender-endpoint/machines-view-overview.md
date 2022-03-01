---
title: Wyświetlanie i organizowanie listy programu Microsoft Defender dla urządzeń końcowych
description: Informacje o dostępnych funkcjach, których można używać z listy Urządzenia, takich jak sortowanie, filtrowanie i eksportowanie listy w celu ulepszania badań.
keywords: sortuj, filtruj, eksportuj, csv, nazwa urządzenia, domena, ostatnio widziany, wewnętrzny adres IP, stan kondycji, aktywne alerty, aktywne wykrywanie złośliwego oprogramowania, kategoria zagrożeń, przeglądanie alertów, sieć, połączenie, złośliwe oprogramowanie, typ, kradzież haseł, oprogramowanie wymuszające okup, exploit, zagrożenia, ogólne złośliwe oprogramowanie, niechciane oprogramowanie
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bef6685f6bf3a998e9b37504fc5ea5e67b4f1bfd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997771"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-devices-list"></a>Wyświetlanie i organizowanie listy programu Microsoft Defender dla urządzeń końcowych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

Lista **Urządzenia zawiera** listę urządzeń w Twojej sieci, na których zostały wygenerowane alerty. Domyślnie w kolejce są wyświetlane urządzenia widziane z ostatnich 30 dni.

W skrócie zobaczysz takie informacje, jak domena, poziom ryzyka, platforma systemu operacyjnego i inne szczegóły, aby ułatwić identyfikację najbardziej ryzykownych urządzeń.

Istnieje kilka opcji do wyboru, aby dostosować widok listy urządzeń. W górnym okienku nawigacji możesz:

- Dodawanie lub usuwanie kolumn
- Eksportowanie całej listy w formacie CSV
- Wybieranie liczby elementów do pokazania na stronie
- Stosowanie filtrów

W trakcie procesu dołączania lista Urządzenia jest  stopniowo wypełniana urządzeniami, gdy zaczną raportować dane czujnika. W tym widoku możesz śledzić swoje punktu końcowe w trybie online lub pobrać pełną listę punktów końcowych jako plik CSV do analizy w trybie offline.

> [!NOTE]
> Jeśli wyeksportujesz listę urządzeń, będzie ona zawierać wszystkie urządzenia w organizacji. Pobieranie pliku może zająć dużo czasu, w zależności od tego, jak duża jest Twoja organizacja. Wyeksportowanie listy w formacie CSV powoduje wyświetlenie danych w sposób niefiltrowany. Plik CSV będzie zawierać wszystkie urządzenia w organizacji, niezależnie od filtrowania zastosowanego w samym widoku.

![Obraz listy urządzeń z listą urządzeń.](images/device-inventory.png)

## <a name="sort-and-filter-the-device-list"></a>Sortowanie i filtrowanie listy urządzeń

Aby ograniczyć listę alertów i uzyskać bardziej skoncentrowany widok, możesz zastosować następujące filtry.

### <a name="device-name"></a>Nazwa urządzenia

Wybierz nazwę urządzenia, które chcesz zbadać.

### <a name="domain"></a>Domain (Domena)

Wybierz domenę, która Cię interesuje.

### <a name="risk-level"></a>Poziom ryzyka

Poziom ryzyka odzwierciedla ogólną ocenę ryzyka urządzenia na podstawie kombinacji czynników, w tym typów i istotności aktywnych alertów na urządzeniu. Rozwiązywanie aktywnych alertów, zatwierdzanie działań naprawczych i pomijanie kolejnych alertów może obniżyć poziom ryzyka.

### <a name="exposure-level"></a>Poziom ekspozycji

Poziom ekspozycji odzwierciedla bieżącą ekspozycję na urządzenie na podstawie skumulowanego wpływu jego oczekujących zaleceń dotyczących zabezpieczeń. Możliwe poziomy są niskie, średnie i wysokie. Niska ekspozycja oznacza, że Urządzenia są mniej narażone na wykorzystywanie.

Jeśli poziom ekspozycji mówi "Brak dostępnych danych", istnieje kilka powodów, dla których może tak być:

- Urządzenie zatrzymało raportowanie przez ponad 30 dni. W takim przypadku jest ona uznawana za nieaktywną, a ekspozycja nie jest obliczana.
- System operacyjny urządzenia nie jest obsługiwany — zobacz [minimalne wymagania dotyczące programu Microsoft Defender dla punktu końcowego](minimum-requirements.md).
- Urządzenie ze przestarzałym agentem (mało prawdopodobne).

### <a name="os-platform"></a>Platforma systemu operacyjnego

Wybierz tylko platformy systemu operacyjnego, które chcesz zbadać.

### <a name="windows-versions"></a>Windows wersji

Wybierz tylko te Windows, które chcesz zbadać.

### <a name="health-state"></a>Stan kondycji

Filtruj według następujących stanów kondycji urządzenia:

- **Aktywny**: Urządzenia, które aktywnie raportują dane czujnika do usługi.
- **Nieaktywny**: Urządzenia, które przestały wysyłać sygnały przez ponad 7 dni.
- **Nieprawidłowo skonfigurowane**: Urządzenia, które zakłócają komunikację z usługą lub nie mogą wysyłać danych czujnika. Nieprawidłowo skonfigurowane urządzenia można dodatkowo sklasyfikować jako:
  - Brak danych czujnika
  - Komunikacja z ograniczoną komunikacją

  Aby uzyskać więcej informacji na temat sposobu rozwiązania problemów z nieprawidłowo skonfigurowanymi urządzeniami, zobacz Rozwiązywanie problemów [z czujnikiami o złej kondycji](fix-unhealthy-sensors.md).

### <a name="onboarding-status"></a>Stan dorównania

Stan dołączania wskazuje, czy urządzenie jest obecnie wnoszone do programu Microsoft Defender for Endpoint. Filtr można filtrować według następujących stanów:

- **Onboarded**: Punkt końcowy jest dołączany do programu Microsoft Defender for Endpoint.

- **Może zostać wnoszony**: Punkt końcowy został wykryty w sieci jako obsługiwane urządzenie, ale nie jest on obecnie wnoszony. Firma Microsoft zdecydowanie zaleca dołączanie tych urządzeń.

- **Nieobsługiwane**: Punkt końcowy został wykryty w sieci, ale nie jest obsługiwany przez program Microsoft Defender for Endpoint.

- **Za mało informacji**: System nie może ustalić możliwości obsługi urządzenia.

### <a name="last-device-update"></a>Ostatnia aktualizacja urządzenia

Filtruj widok według tego, kiedy urządzenie zostało ostatnio zaktualizowane.

### <a name="first-seen"></a>Widziane jako pierwsze

Filtruj widok według tego, kiedy urządzenie było najpierw widoczne w sieci lub kiedy zostało zgłoszone po raz pierwszy przez czujnik programu Microsoft Defender for Endpoint.

### <a name="tags"></a>Tagi

Filtruj listę według grupowania i tagów dodanych do poszczególnych urządzeń. Zobacz [Tworzenie tagów urządzeń i zarządzanie nimi](machine-tags.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Badanie urządzeń na liście programu Microsoft Defender dla urządzeń końcowych](investigate-machines.md)
