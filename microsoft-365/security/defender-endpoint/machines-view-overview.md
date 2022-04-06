---
title: Spis urządzeń
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
ms.openlocfilehash: a9753cdc818aefdf33411bd237327310dfc512ab
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474756"
---
# <a name="device-inventory"></a>Spis urządzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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

:::image type="content" source="images/device-inventory.png" alt-text="Lista urządzeń" lightbox="images/device-inventory.png":::

## <a name="sort-and-filter-the-device-list"></a>Sortowanie i filtrowanie listy urządzeń

Aby ograniczyć listę alertów i uzyskać bardziej skoncentrowany widok, możesz zastosować następujące filtry.

### <a name="device-name"></a>Nazwa urządzenia

W trakcie Ochrona punktu końcowego w usłudze Microsoft Defender wnoszeniu urządzenia do aplikacji MDE są stopniowo wypełniane w spisie urządzeń, gdy zaczną zgłaszać dane czujnika. Poniżej przedstawiono spis urządzeń wypełniony urządzeniami wykrytymi w Twojej sieci w ramach procesu odnajdowania urządzeń. Spis urządzeń zawiera trzy karty, które listy urządzeń są dostępne według:

- **Komputery i urządzenia przenośne**: Enterprise końcowe (stacje robocze, serwery i urządzenia przenośne)
- **Urządzenia sieciowe**: urządzenia, takie jak routery i przełączniki
- **Urządzenia IoT**: urządzenia, takie jak drukarki i kamery

## <a name="navigate-to-the-device-inventory-page"></a>Przejdź do strony spisu urządzeń

Aby uzyskać dostęp do strony spisu urządzeń, wybierz **pozycję Spis** urządzeń z menu nawigacji **Punkty** końcowe w portalu Microsoft 365 Defender [sieci Web](/defender/microsoft-365-security-center-mde).

## <a name="device-inventory-overview"></a>Omówienie spisu urządzeń

Zostanie otwarty spis urządzeń na **karcie Komputery i** urządzenia przenośne. W skrócie możesz zobaczyć takie informacje, jak nazwa urządzenia, domena, poziom ryzyka, poziom ekspozycji, platforma systemu operacyjnego, stan dołączania, stan kondycji czujnika i inne szczegóły, aby ułatwić identyfikację najbardziej ryzykownych urządzeń.

Kolumna **Stan dołączania umożliwia sortowanie** i filtrowanie według wykrytych urządzeń oraz urządzeń już Ochrona punktu końcowego w usłudze Microsoft Defender.

![Obraz listy urządzeń z listą urządzeń.](images/device-inventory.png)

Na **kartach Urządzenia** sieciowe **i Urządzenia IoT** są również dostępne informacje, takie jak dostawca, model i typ urządzenia:

![Obraz listy urządzeń sieciowych.](images/device-inventory-networkdevices.png)

U góry karty spisu poszczególnych urządzeń jest widać łączną liczbę urządzeń, liczbę urządzeń, które nie zostały jeszcze naniesone, oraz liczbę urządzeń zidentyfikowanych jako większe ryzyko dla Twojej organizacji. Te informacje ułatwiają określanie priorytetów urządzeń w zakresie ulepszeń dotyczących zabezpieczeń.

Karta **Liczba nowo wykrytych** urządzeń dla urządzeń sieciowych i urządzeń IoT zawiera liczbę nowych wykrytych urządzeń w ciągu ostatnich 7 dni, wymienionych w bieżącym widoku.

![Obraz nowej liczby wykrytych urządzeń.](images/new-discovered-devices.png)

## <a name="explore-the-device-inventory"></a>Przejrzyj spis urządzeń

Istnieje kilka opcji, które możesz wybrać, aby dostosować widok spisu urządzeń. W górnym obszarze nawigacji dla każdej karty możesz:

- Wyszukiwanie urządzenia według nazwy
- Wyszukiwanie urządzenia według ostatnio używanego adresu IP lub prefiksu adresu IP
- Dodawanie lub usuwanie kolumn
- Eksportowanie całej listy w formacie CSV do analizy w trybie offline
- Zaznaczanie zakresu dat do wyświetlenia
- Stosowanie filtrów

> [!NOTE]
> Jeśli wyeksportujesz listę urządzeń, będzie ona zawierać wszystkie urządzenia w organizacji. Pobieranie pliku może zająć dużo czasu, w zależności od tego, jak duża jest Twoja organizacja. Wyeksportowanie listy w formacie CSV powoduje wyświetlenie danych w sposób niefiltrowany. Plik CSV będzie zawierać wszystkie urządzenia w organizacji, niezależnie od filtrowania zastosowanego w samym widoku.

Możesz użyć funkcji sortowania i filtrowania dostępnych na poszczególnych kartach spisu urządzeń, aby uzyskać bardziej skoncentrowany widok oraz ułatwić ocenę urządzeń i zarządzanie nimi w organizacji.

Liczba w górnej części każdej karty zostanie zaktualizowana na podstawie bieżącego widoku.

## <a name="use-filters-to-customize-the-device-inventory-views"></a>Dostosowywanie widoków spisu urządzeń za pomocą filtrów

Filtr | Opis
:---|:---
**Poziom ryzyka** </br> | Poziom ryzyka odzwierciedla ogólną ocenę ryzyka urządzenia na podstawie kombinacji czynników, w tym typów i istotności aktywnych alertów na urządzeniu. Rozwiązywanie aktywnych alertów, zatwierdzanie działań naprawczych i pomijanie kolejnych alertów może obniżyć poziom ryzyka.
**Poziom ekspozycji** </br> | Poziom ekspozycji odzwierciedla bieżącą ekspozycję na urządzenie na podstawie skumulowanego wpływu jego oczekujących zaleceń dotyczących zabezpieczeń. Możliwe poziomy są niskie, średnie i wysokie. Niska ekspozycja oznacza, że Urządzenia są mniej narażone na wykorzystywanie. </br> </br> Jeśli poziom ekspozycji mówi "Brak dostępnych danych", istnieje kilka powodów, dla których może tak być:</br>— Urządzenie zatrzymało raportowanie przez ponad 30 dni. W takim przypadku jest ona uznawana za nieaktywną, a ekspozycja nie jest obliczana.</br>- System operacyjny urządzenia nie jest obsługiwany — zobacz [minimalne wymagania dotyczące systemu Ochrona punktu końcowego w usłudze Microsoft Defender](https://microsoft-my.sharepoint.com/personal/siosulli_microsoft_com/Documents/Security%20Posture/TVM/minimum-requirements.md).</br>— Urządzenie ze przestarzałym agentem (mało prawdopodobne).
**Tagi** </br> | Filtruj listę według grupowania i tagów dodanych do poszczególnych urządzeń. Zobacz [Tworzenie tagów urządzeń i zarządzanie nimi](machine-tags.md).
**Wartość urządzenia**</br> | Filtruj listę według tego, czy urządzenie zostało oznaczone jako wysokie lub niskie.
**Stan wykluczenia** </br> | Przefiltruj listę według tego, czy urządzenie zostało wykluczone. Aby uzyskać więcej informacji, zobacz [Wyklucz urządzenia](exclude-devices.md).
**Platforma systemu operacyjnego** </br>| Filtrowanie według platform systemu operacyjnego, które chcesz zbadać </br></br>(_Tylko komputery i urządzenia przenośne oraz urządzenia IoT_)
**Widziane jako pierwsze** </br> | Filtruj widok według tego, kiedy urządzenie było najpierw widoczne w sieci lub kiedy zostało zgłoszone po raz pierwszy przez Ochrona punktu końcowego w usłudze Microsoft Defender sieci.</br></br>(_Tylko komputery i urządzenia przenośne oraz urządzenia IoT_)
**Wersje systemu Windows** </br> | Filtruj według Windows, które chcesz zbadać.</br></br> (_Tylko komputery i urządzenia przenośne_)
**Stan kondycji czujnika** </br> | Filtruj według następujących stanów kondycji czujnika, aby urządzenia podłączone do Ochrona punktu końcowego w usłudze Microsoft Defender:</br> - **Aktywny**: Urządzenia, które aktywnie raportują dane czujnika do usługi.</br> - **Nieaktywny**: Urządzenia, które przestały wysyłać sygnały przez ponad 7 dni. </br> - **Nieprawidłowo skonfigurowane**: Urządzenia, które zakłócają komunikację z usługą lub nie mogą wysyłać danych czujnika. </br> Nieprawidłowo skonfigurowane urządzenia można dodatkowo sklasyfikować jako: </br>  - Brak danych czujnika </br>  - Komunikacja z ograniczoną komunikacją </br>  Aby uzyskać więcej informacji na temat sposobu rozwiązania problemów z nieprawidłowo skonfigurowanymi urządzeniami, zobacz Rozwiązywanie problemów [z czujnikiami o złej kondycji](https://microsoft-my.sharepoint.com/personal/siosulli_microsoft_com/Documents/Security%20Posture/TVM/fix-unhealthy-sensors.md).</br></br> (_Tylko komputery i urządzenia przenośne_)
**Stan dorównania** </br> | Stan dołączania wskazuje, czy urządzenie jest obecnie Ochrona punktu końcowego w usłudze Microsoft Defender lub nie. Filtr można filtrować według następujących stanów: </br> - **Onboarded**: Punkt końcowy jest dołączany do Ochrona punktu końcowego w usłudze Microsoft Defender.  </br> - **Może zostać wnoszony**: Punkt końcowy został wykryty w sieci jako obsługiwane urządzenie, ale nie jest on obecnie wnoszony. Firma Microsoft zdecydowanie zaleca dołączanie tych urządzeń. </br> - **Nieobsługiwane**: Punkt końcowy został wykryty w sieci, ale nie jest obsługiwany przez Ochrona punktu końcowego w usłudze Microsoft Defender. </br> - **Za mało informacji**: System nie może ustalić możliwości obsługi urządzenia.</br></br> (_Tylko komputery i urządzenia przenośne_)
**Stan oprogramowania antywirusowego** </br> | Filtruj widok według tego, czy stan oprogramowania antywirusowego jest wyłączony, nie jest aktualizowany czy nieznany.</br></br> (_Tylko komputery i urządzenia przenośne_)
**Grupa** </br> | Filtruj listę według grupy, która cię interesuje. </br></br> (_Tylko komputery i urządzenia przenośne_)
**Zarządzane przez** </br> | Zarządzane przez wskazuje, jak urządzenie jest zarządzane. Możesz filtrować według:</br>— Ochrona punktu końcowego w usłudze Microsoft Defender </br> — Zarządzanie urządzeniami przenośnymi (MDM) </br>— Nieznany: Może to być spowodowane tym, że uruchomiona Windows, program SCCM jest w miejscu lub inna firma MDM.</br></br> (_Tylko komputery i urządzenia przenośne_)
**Typ urządzenia** </br> | Filtruj według typu urządzenia, które chcesz zbadać.</br></br> (_Tylko urządzenia IoT_)

## <a name="use-columns-to-customize-the-device-inventory-views"></a>Dostosowywanie widoków spisu urządzeń za pomocą kolumn

Możesz dodawać lub usuwać kolumny z widoku i sortować pozycje, klikając dostępny nagłówek kolumny.

Na karcie **Komputer i urządzenia przenośne** wybierz pozycję **Dostosuj kolumny** , aby wyświetlić dostępne kolumny. Wartości domyślne są zaznaczone na poniższej ilustracji:

![Obraz komputerów i urządzeń przenośnych](images/computerandmobilescolumns.png)

Na karcie **Urządzenia sieciowe** wybierz pozycję **Dostosuj kolumny** , aby wyświetlić dostępne kolumny. Wartości domyślne są zaznaczone na poniższej ilustracji:

![Obraz kolumn urządzenia sieciowego](images/networkdevicescolumns.png)

Na karcie **Urządzenia z systemem IoT** wybierz pozycję **Dostosuj kolumny** , aby wyświetlić dostępne kolumny. Wartości domyślne są zaznaczone na poniższej ilustracji:

![Obraz kolumn urządzenia IoT](images/iotdevicescolumns.png)

## <a name="related-articles"></a>Artykuły pokrewne

[Badanie urządzeń na liście Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia](investigate-machines.md)
