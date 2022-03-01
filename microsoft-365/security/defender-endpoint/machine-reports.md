---
title: Raport kondycji i zgodności urządzeń w programie Microsoft Defender for Endpoint
description: Śledzenie wykrywania stanu kondycji urządzenia, stanu oprogramowania antywirusowego, platformy systemu operacyjnego i Windows 10 za pomocą raportu kondycji i zgodności urządzeń
keywords: stan kondycji, oprogramowanie antywirusowe, platforma systemu operacyjnego, wersja systemu Windows 10, wersja, kondycja, zgodność, stan
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
ms.openlocfilehash: eaa9d05fd62127949e6a0b40de8d42a79c446d4d
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996738"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>Raport kondycji i zgodności urządzeń w programie Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Raport o stanie urządzeń zawiera szczegółowe informacje o urządzeniach w Organizacji. Raport zawiera popularne informacje pokazujące stan kondycji czujnika, stan oprogramowania antywirusowego, platformy systemu operacyjnego i Windows 10 (i Windows 11).

Pulpit nawigacyjny ma strukturę dwóch sekcji:

:::image type="content" alt-text="Obraz raportu urządzenia." source="images/device-reports.png" lightbox="images/device-reports.png":::


<br>

****

|Sekcja|Opis|
|---|---|
|1|Trendy w urządzeniach|
|2|Podsumowanie urządzenia (bieżący dzień)|
|||

## <a name="device-trends"></a>Trendy w urządzeniach

Domyślnie trendy dotyczące urządzeń wyświetlają informacje o urządzeniu z 30-dniowego okresu kończącego się na ostatni cały dzień. Aby uzyskać lepszą perspektywę trendów występujących w organizacji, możesz dostosować okres raportowania, dostosowując pokazywany okres. Aby dostosować przedział czasu, wybierz zakres czasu z listy rozwijanej:

- 30 dni
- Trzy miesiące
- Sześć miesięcy
- Niestandardowe

> [!NOTE]
> Filtry te są stosowane tylko w sekcji trendów urządzeń. Nie ma to wpływu na sekcję podsumowania urządzenia.

## <a name="device-summary"></a>Podsumowanie urządzeń

Mimo że trendy dotyczące urządzeń wskazują popularne informacje o urządzeniach, w podsumowaniu urządzenia są wyświetlane informacje dotyczące urządzeń w zakresie od bieżącego dnia.

> [!NOTE]
> Dane odzwierciedlone w sekcji podsumowania są objęte zakresem 180 dni przed datą bieżącą. Jeśli na przykład dzisiejszą datą jest 27 marca 2019 r., dane w sekcji podsumowania będą odzwierciedlać liczby od 28 września 2018 r. do 27 marca 2019 r.
>
> Filtr zastosowany w sekcji trendów nie jest stosowany w sekcji podsumowania.

Sekcja trendów urządzeń umożliwia przechodzenie do szczegółów listy urządzeń z zastosowanym do niej filtrem. Na przykład kliknięcie paska Nieaktywny na karcie Stan kondycji czujnika spowoduje wyświetlanie listy urządzeń z wynikami wskazującymi tylko te urządzenia, których stan czujnika jest nieaktywny.

## <a name="device-attributes"></a>Atrybuty urządzenia

Raport składa się z kart, na których są wyświetlane następujące atrybuty urządzenia:

- **Stan kondycji**: wyświetla informacje o stanie czujnika na urządzeniach, udostępniając zagregowany widok urządzeń, które są aktywne, mają problemy z komunikacją, są nieaktywne lub nie są widoczne żadne dane czujnika.
- **Stan oprogramowania antywirusowego Windows 10 urządzeniach**: pokazuje liczbę urządzeń i stan Program antywirusowy Microsoft Defender.
- **Platformy systemu operacyjnego**: pokazuje rozpowszechnianie platform systemu operacyjnego istnieje w organizacji.
- **Windows 10 wersji**: pokazuje rozpowszechnianie Windows 10 urządzeniach i ich wersjach w organizacji.

## <a name="filter-data"></a>Filtrowanie danych

Użyj podanych filtrów, aby dołączyć lub wykluczyć urządzenia z określonymi atrybutami.

Możesz wybrać wiele filtrów do zastosowania w atrybutach urządzenia.

> [!NOTE]
> Filtry te są stosowane **do** wszystkich kart w raporcie.

Aby na przykład wyświetlić dane dotyczące urządzeń Windows 10 z stanem kondycji czujnika Aktywne:

1. W **obszarze Filtry > stan kondycji czujnika > Aktywne**.
2. Następnie wybierz **platformy systemu operacyjnego > Windows 10**.
3. Wybierz **pozycję Zastosuj**.

## <a name="related-topic"></a>Temat pokrewny

- [Raport ochrony przed zagrożeniami](threat-protection-reports.md)
