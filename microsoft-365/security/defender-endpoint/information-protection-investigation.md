---
title: Określanie priorytetów reakcji na zdarzenia przy użyciu etykiet wrażliwości
description: Dowiedz się, jak za pomocą etykiet wrażliwości określać priorytety i badać zdarzenia
keywords: informacje, ochrona, dane, utrata, zapobieganie, etykiety, zapobieganie, zdarzenie, badanie, badanie
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
ms.openlocfilehash: 465c149e3ad82384b574b43c66da917a46e4a2ce
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474162"
---
# <a name="use-sensitivity-labels-to-prioritize-incident-response"></a>Określanie priorytetów reakcji na zdarzenia przy użyciu etykiet wrażliwości

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Typowy zaawansowany, trwały cykl życia zagrożeń obejmuje eksekwację danych. W przypadku zdarzeń dotyczących zabezpieczeń ważne jest, aby mieć możliwość ustalania priorytetów w przypadkach, gdy poufne pliki mogą stanowić zagrożenie dla danych firmowych i informacji.

Program Defender for Endpoint ułatwia ustalanie priorytetów zdarzeń zabezpieczających o wiele prostsze dzięki użyciu etykiet wrażliwości. Etykiety poufności szybko identyfikują zdarzenia, które mogą obejmować urządzenia z informacjami poufnymi, takimi jak informacje poufne.

## <a name="investigate-incidents-that-involve-sensitive-data"></a>Badanie zdarzeń dotyczących danych poufnych

Dowiedz się, jak używać etykiet wrażliwości danych w celu ustalania priorytetów analizy zdarzeń.

> [!NOTE]
> Etykiety są wykrywane w Windows 10, wersja 1809 lub nowszym, a Windows 11.

1. W Microsoft 365 Defender wiadomości wybierz pozycję **Zdarzenia i & Alerty** \> **o zdarzeniach**.

2. Przewiń w prawo, aby wyświetlić **kolumnę Czułość** danych. Ta kolumna zawiera etykiety wrażliwości obserwowane na urządzeniach w związku z zdarzeniami, ze wskazaniem, czy zdarzenia mogą dotyczyć poufnych plików.

   :::image type="content" source="images/data-sensitivity-column.png" alt-text="Opcja Wysoce poufne w kolumnie poufności danych" lightbox="images/data-sensitivity-column.png":::

    Możesz również filtrować według wrażliwości **na dane**

    :::image type="content" source="images/data-sensitivity-filter.png" alt-text="Filtr wrażliwości danych" lightbox="images/data-sensitivity-filter.png":::

3. Otwórz stronę zdarzenia w celu dalszego zbadania.

   :::image type="content" source="images/incident-page.png" alt-text="Szczegóły strony zdarzenia" lightbox="images/incident-page.png":::

4. Wybierz **kartę Urządzenia,** aby zidentyfikować urządzenia przechowujące pliki za pomocą etykiet wrażliwości.

   :::image type="content" source="images/investigate-devices-tab.png" alt-text="Karta Urządzenie" lightbox="images/investigate-devices-tab.png":::

5. Wybierz urządzenia przechowujące poufne dane i przeszukaj oś czasu, aby określić, których plików może to wpłynąć, a następnie podjąć odpowiednie działania w celu zapewnienia ochrony danych.

   Zdarzenia wyświetlane na osi czasu urządzenia można zawęzić, wyszukując etykiety wrażliwości danych. Spowoduje to pokazanie tylko zdarzeń skojarzonych z plikami o nazwie etykiety.

   :::image type="content" source="images/machine-timeline-labels.png" alt-text="Oś czasu urządzenia z zawęższymi wynikami wyszukiwania na podstawie etykiety" lightbox="images/machine-timeline-labels.png":::

> [!TIP]
> Te punkty danych są również widoczne dzięki "DeviceFileEvents" w zaawansowanym chłoniu, dzięki czemu zaawansowane zapytania i planowanie wykrywania mogą uwzględniać etykiety wrażliwości i stan ochrony plików.
