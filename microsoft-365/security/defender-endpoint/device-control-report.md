---
title: Ochrona danych organizacji za pomocą kontrolki urządzenia
description: Monitoruj bezpieczeństwo danych organizacji za pośrednictwem raportów dotyczących sterowania urządzeniami.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: deniseb
author: denisebmsft
ms.reviewer: dansimp
ms.topic: article
manager: dansimp
audience: ITPro
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 8a31ce05ed6986159d9f6e4c489e6f7707cfecc4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465294"
---
# <a name="device-control-report"></a>Raport sterowania urządzeniami

**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ochrona punktu końcowego w usłudze Microsoft Defender sterowanie urządzeniem chroni przed utratą danych, monitorując i kontrolując użycie multimediów przez urządzenia w Twojej organizacji, takie jak korzystanie z wymiennych urządzeń magazynujących i dysków USB.

Raport sterowania urządzeniami umożliwia wyświetlanie zdarzeń związanych ze zużyciem multimediów, takich jak:

- **Inspekcja zdarzeń:** Przedstawia liczbę zdarzeń inspekcji, które mają miejsce po połączeniu multimediów zewnętrznych.
- **Zdarzenia zasad:** Pokazuje liczbę zdarzeń zasad, które występują po wyzwoleniu zasad sterowania urządzeniem.

> [!NOTE]
> Zdarzenie inspekcji do śledzenia użycia multimediów jest domyślnie włączone dla urządzeń włączonych do Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="understanding-the-audit-events"></a>Opis zdarzeń inspekcji

Zdarzenia inspekcji to między innymi:

- **Wykonuj i odinstaluj dysk USB:** Inspekcja zdarzeń generowanych, gdy dysk USB jest montowany lub nieukońowany.
- **PnP:** Plug and Play inspekcji są generowane po podłączeniu magazynu wymiennych, drukarki Bluetooth nośnika multimedialnego.
- **Kontrolka dostępu do magazynu wymiennych:** Zdarzenia są generowane, gdy są wyzwalane zasady kontroli dostępu magazynu wymiennych. Może to być inspekcja, blokowanie lub zezwalanie.

## <a name="monitor-device-control-security"></a>Monitorowanie zabezpieczeń sterowania urządzeniem

Kontrola urządzeń w Ochrona punktu końcowego w usłudze Microsoft Defender umożliwia administratorom zabezpieczeń narzędzia, które umożliwiają im śledzenie zabezpieczeń urządzeń organizacji za pomocą raportów. Raport sterowania urządzeniami można znaleźć w portalu Microsoft 365 Defender w raportach w > **ochrony urządzeń**.

Na karcie Ochrona urządzenia na pulpicie **nawigacyjnym** Raporty jest pokazana liczba zdarzeń inspekcji wygenerowanych według typu nośnika w ciągu ostatnich 180 dni.

> [!div class="mx-imgBorder"]
> ![DeviceControlReportCard](https://user-images.githubusercontent.com/81826151/138504137-e9a7673e-e988-48cd-820d-2625ec6df352.png)

Przycisk **Wyświetl szczegóły** umożliwia wyświetlenie większej liczby danych dotyczących użycia multimediów na **stronie raportu sterowania urządzeniami** .

Strona udostępnia pulpit nawigacyjny z zagregowaną liczbą zdarzeń według typu i listą zdarzeń. Administratorzy mogą filtrować według zakresu czasu, nazwy klasy multimediów i identyfikatora urządzenia.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="Strona Szczegóły raportu sterowania urządzeniami w portalu Microsoft 365 Defender urządzenia" lightbox="images/Detaileddevicecontrolreport.png":::

Po wybraniu zdarzenia zostanie wyświetlone wysuwne okno, które zawiera więcej informacji:

- **Szczegóły ogólne:** Data, tryb akcji, zasady i dostęp do tego zdarzenia.
- **Informacje o multimediach:** Informacje o multimediach obejmują nazwę multimediów, nazwę klasy, identyfikator GUID klasy, identyfikator urządzenia, identyfikator dostawcy, numer seryjny i typ autobusu.
- **Szczegóły lokalizacji:** Nazwa urządzenia, identyfikator użytkownika i identyfikator urządzenia MDATP.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="The Filter on Device Control Report page" lightbox="images/devicecontrolreportfilter.png":::

Aby wyświetlić aktywność w czasie rzeczywistym dla tego nośnika w całej organizacji, wybierz przycisk **Otwórz zaawansowane** wyszukiwania. Obejmuje to osadzone, wstępnie zdefiniowane zapytanie.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="The Query on Device Control Report page" lightbox="images/Devicecontrolreportquery.png":::

Aby sprawdzić zabezpieczenia urządzenia, wybierz przycisk **Otwórz stronę urządzenia** w wysuwanych oknach. Ten przycisk powoduje otwarcie strony jednostki urządzenia.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="Strona jednostki urządzenia" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>Zgłaszanie opóźnień

Raport sterowania urządzeniami może mieć 12-godzinne opóźnienie od czasu wystąpienia połączenia multimedialnego do czasu odzwierciedlania zdarzenia na karcie lub na liście domen.
