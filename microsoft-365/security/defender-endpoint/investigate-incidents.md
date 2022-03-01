---
title: Badanie zdarzeń w programie Microsoft Defender dla punktu końcowego
description: Wyświetlanie skojarzonych alertów, zarządzanie zdarzeniem i wyświetlanie metadanych alertów w celu dalszego zbadania zdarzenia
keywords: badanie, zdarzenie, alerty, metadane, ryzyko, źródło wykrywania, urządzenia, których dotyczy problem, wzorce, korelacja
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2a297813fbde94499f2d239627be6c33c153e8b0
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011282"
---
# <a name="investigate-incidents-in-microsoft-defender-for-endpoint"></a>Badanie zdarzeń w programie Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Badanie zdarzeń mających wpływ na sieć, zrozumienie ich znaczenie oraz sortowanie dowodów w celu ich rozwiązania.

Podczas zbadania zdarzenia zobaczysz:

- Szczegóły zdarzenia
- Komentarze i akcje dotyczące incydentów
- Karty (alerty, urządzenia, badania, dowody, wykres)

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUV]

## <a name="analyze-incident-details"></a>Analizowanie szczegółów zdarzenia

Kliknij zdarzenie, aby wyświetlić **okienko Zdarzenie**. Wybierz **pozycję Otwórz stronę zdarzenia** , aby wyświetlić szczegóły zdarzenia i powiązane informacje (alerty, urządzenia, badania, dowody, wykres).

![Obraz szczegółów zdarzenia1.](images/atp-incident-details.png)

### <a name="alerts"></a>Alerty

Możesz zbadać alerty i zobaczyć, jak powiązywają się ze sobą w przypadku zdarzenia. Alerty są pogrupowane w zdarzenia z następujących powodów:

- Zautomatyzowane badanie — zautomatyzowane badanie wyzwoliło alert połączony podczas badania pierwotnego alertu
- Cechy pliku — pliki skojarzone z alertem mają podobne cechy
- Ręczne skojarzenie — użytkownik ręcznie powiązył alerty
- Godzina proxy — alerty zostały wyzwolone na tym samym urządzeniu w określonym czasie
- Ten sam plik — pliki skojarzone z alertem są dokładnie takie same
- Ten sam adres URL — adres URL, który wyzwolył alert, jest dokładnie taki sam

![Obraz karty Alerty ze stroną ze szczegółami zdarzenia pokazującą przyczyny, dla których alerty zostały połączone w tym zdarzeniu.](images/atp-incidents-alerts-reason.png)

Możesz także zarządzać alertami i oglądać metadane alertów razem z innymi informacjami. Aby uzyskać więcej informacji, zobacz [Badanie alertów](investigate-alerts.md).

### <a name="devices"></a>Urządzenia

Możesz również zbadać urządzenia, które są częścią danego zdarzenia lub są z nim związane. Aby uzyskać więcej informacji, zobacz [Badanie urządzeń](investigate-machines.md).

![Obraz karty Urządzenia na stronie szczegółów zdarzenia.](images/atp-incident-device-tab.png)

### <a name="investigations"></a>Badania

Wybierz **pozycję Badania** , aby wyświetlić wszystkie automatyczne badania uruchomione przez system w odpowiedzi na alerty o incydentach.

![Obraz karty Badania na stronie szczegółów zdarzenia.](images/atp-incident-investigations-tab.png)

## <a name="going-through-the-evidence"></a>Jak się tego dosyć

Program Microsoft Defender for Endpoint automatycznie bada wszystkie zdarzenia obsługiwane przez zdarzenia oraz podejrzane jednostki w alertach, udostępniając Ci automatycznie odpowiedzialność i informacje na temat ważnych plików, procesów, usług i nie tylko.

Wszystkie analizowane jednostki zostaną oznaczone jako zainfekowane, usunięte lub podejrzane.

![Obraz karty dowodów na stronie szczegółów zdarzenia.](images/atp-incident-evidence-tab.png)

## <a name="visualizing-associated-cybersecurity-threats"></a>Wizualizowanie skojarzonych zagrożeń bezpieczeństwa bezpieczeństwa

Program Microsoft Defender for Endpoint agreguje informacje o zagrożeniach w zdarzenie, dzięki czemu można zobaczyć wzorce i korelacje pochodzące z różnych punktów danych. Takie korelacje możesz wyświetlić na wykresie zdarzeń.

### <a name="incident-graph"></a>Wykres zdarzeń

Ten **Graph** historię ataków na bezpieczeństwo. Możesz na przykład wskazać, jaki był punkt wejścia, który wskaźnik naruszenia bezpieczeństwa lub aktywności został obserwowany na którym urządzeniu. itd.

![Obraz wykresu zdarzenia.](images/atp-incident-graph-tab.png)

Możesz kliknąć kółka na wykresie zdarzeń, aby wyświetlić szczegóły złośliwych plików, skojarzonych z nimi wykrycia plików, ile wystąpień pojawiło się na całym świecie, czy zostały one obserwowane w organizacji, jeśli tak, ilu wystąpień.

![Obraz ze szczegółami zdarzenia.](images/atp-incident-graph-details.png)

## <a name="related-topics"></a>Tematy pokrewne

- [Kolejka zdarzeń](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Badanie zdarzeń w programie Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/investigate-incidents)
- [Zarządzanie zdarzeniami programu Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/manage-incidents)
