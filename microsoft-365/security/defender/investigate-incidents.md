---
title: Badanie zdarzeń w Microsoft 365 Defender
description: Badanie zdarzeń związanych z urządzeniami, użytkownikami i skrzynkami pocztowymi.
keywords: zdarzenie, zdarzenia, analiza, odpowiedź, komputery, urządzenia, użytkownicy, tożsamości, poczta, wiadomość e-mail, skrzynka pocztowa, analiza, wykres, dowód
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
- incidentresponse
- m365solution-incidentresponse
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 1dd603ae4f9f694b3b17794a71d1d5cc44800584
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013263"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>Badanie zdarzeń w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Microsoft 365 Defender wszystkie związane z tym alerty, zasoby, badania i dowody z różnych urządzeń, użytkowników i skrzynek pocztowych są zes względu na zdarzenie, co daje ci pełne spojrzenie na cały obszar ataków.

W ramach zdarzenia analizuje się alerty wpływające na sieć, rozumie ich znaczenie, a także sortuje informacje, aby można było opracować skuteczny plan rozwiązywania problemów.

## <a name="initial-investigation"></a>Wstępne badanie

Przed rozpoczęciem pracy nad szczegółami sprawdź właściwości i podsumowanie zdarzenia.

Możesz rozpocząć od wybrania zdarzenia w kolumnie znacznika wyboru. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="Przykład zaznaczania zdarzenia z kolumny znacznika wyboru." lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

Gdy to zrobisz, zostanie otwarte okienko podsumowania z kluczowymi informacjami o zdarzeniu, takimi jak ważność, do kogo jest przypisane, oraz [miTRE ATT&CK&trade;](https://attack.mitre.org/) kategorii dla zdarzenia. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="Przykład okienka podsumowania dla zdarzenia." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

W tym miejscu możesz wybrać pozycję **Otwórz stronę zdarzenia**. Zostanie otwarta strona główna zdarzenia, na której znajdziesz więcej informacji podsumowujących oraz karty alertów, urządzeń, użytkowników, badań i dowodów.

Możesz również otworzyć stronę główną zdarzenia, wybierając nazwę zdarzenia w kolejce zdarzenia.

## <a name="summary"></a>Podsumowanie

Strona **Podsumowanie** pozwala w skrócie spojrzeć na najważniejsze informacje na temat zdarzenia.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Przykład strony podsumowania zdarzenia w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Informacje w tych sekcjach są uporządkowane.

| Sekcja | Opis |
|:-------|:-----|
| Alerty i kategorie | Wizualny i numeryczny widok postępu zaawansowania ataków na łańcuch killów. Podobnie jak w przypadku innych produktów zabezpieczeń firmy Microsoft, Microsoft 365 Defender jest ona dostosowana do struktury [MITRE ATT&CK&trade;](https://attack.mitre.org/). Oś czasu alertów zawiera chronologiczną kolejność, w jakiej wystąpiły alerty, oraz ich stan i nazwisko. |
| Zakres |  Wyświetla liczbę urządzeń, użytkowników i skrzynek pocztowych, których to wpływ, oraz wyświetla jednostki w kolejności poziomu ryzyka i priorytetu badania. |
| Dowód | Wyświetla liczbę obiektów, których dotyczy zdarzenie. |
| Informacje o zdarzeniu | Wyświetla właściwości zdarzenia, takie jak tagi, stan i ważność. |
|||

Strona Podsumowanie **umożliwia** ocenę względnej ważności zdarzenia i szybki dostęp do skojarzonych alertów i jednostek, na które ma wpływ zdarzenie.

## <a name="alerts"></a>Alerty

Na karcie **Alerty** możesz wyświetlić kolejkę alertów dla alertów dotyczących zdarzenia i innych informacji o nich, takich jak:

- Ważność.
- Jednostki, które uczestniczyły w alercie.
- Źródło alertów (Microsoft Defender for Identity, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Defender for Cloud Apps i Zarządzanie aplikacjami).
- Powód, dla którego łączyli się ze sobą.

Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="Przykład strony Alerty dla zdarzenia." lightbox="../../media/investigate-incidents/incident-alerts.png":::

Domyślnie alerty są uporządkowane chronologicznie, aby można było zobaczyć, jak z czasem przebiegł atak. Po wybraniu alertu w ramach zdarzenia program Microsoft 365 Defender informacje o alertach specyficzne dla kontekstu ogólnego zdarzenia. 

Możesz zobaczyć zdarzenia alertu, które inne wyzwalane alerty spowodowały bieżący alert, a także wszystkie jednostki i działania, których dotyczy atak, w tym urządzenia, pliki, użytkowników i skrzynki pocztowe.

Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="Przykład strony ze szczegółami alertu w obrębie zdarzenia." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

Strona alertu o zdarzeniu zawiera następujące sekcje:

- Alert, który zawiera:

   - Co się stało

   - Wykonane działania

   - Zdarzenia pokrewne

- Właściwości alertów w prawym okienku (stan, szczegóły, opis i inne)

Nie każdy alert będzie zawierał wszystkie podsekcji wymienione w sekcji **Alert** .

Dowiedz się, jak używać kolejki alertów i stron alertów w celu [zbadania alertów](investigate-alerts.md).

## <a name="devices"></a>Urządzenia

Karta **Urządzenia** zawiera listę wszystkich urządzeń związanych z zdarzeniem. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="Przykład strony Urządzenia dla zdarzenia." lightbox="../../media/investigate-incidents/incident-devices.png":::

Możesz zaznaczyć znacznik wyboru dla urządzenia, aby wyświetlić szczegółowe informacje o urządzeniu, dane katalogu, aktywne alerty i zalogowani użytkownicy. Wybierz nazwę urządzenia, aby wyświetlić szczegóły dotyczące urządzenia w spisie urządzeń programu Microsoft Defender for Endpoint. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="Przykład strony urządzeń dla programu Microsoft Defender for Endpoint." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

Na stronie urządzenia możesz zebrać dodatkowe informacje o urządzeniu, takie jak wszystkie związane z nim alerty, oś czasu i zalecenia dotyczące zabezpieczeń. Na przykład na karcie Oś  czasu możesz przewijać maszynną oś czasu i wyświetlać wszystkie zdarzenia i zachowania obserwowane na komputerze w kolejności chronologicznej z podniesionym alertami.

> [!TIP]
> Możesz wykonać skanowanie na żądanie na stronie urządzenia. W portalu Microsoft 365 Defender wybierz pozycję **Punkty końcowe > spis urządzeń**. Wybierz urządzenie z alertami, a następnie uruchom skanowanie antywirusowe. Akcje, takie jak skany antywirusowe, są śledzone i są widoczne na **stronie spisu** urządzeń. Aby dowiedzieć się więcej, zobacz [Uruchamianie skanowania Program antywirusowy Microsoft Defender na urządzeniach](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>Użytkownicy

Na **karcie** Użytkownicy jest wymieniona lista wszystkich użytkowników, którzy zidentyfikowani są częścią zdarzenia lub są powiązani z nim. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Przykład strony Użytkownicy dla zdarzenia." lightbox="../../media/investigate-incidents/incident-users.png":::

Możesz zaznaczyć znacznik wyboru dla użytkownika, aby wyświetlić szczegóły zagrożenia konta użytkownika, jego ekspozycji i informacji kontaktowych. Wybierz nazwę użytkownika, aby wyświetlić dodatkowe szczegóły konta użytkownika.

Dowiedz się, jak wyświetlać dodatkowe informacje o użytkownikach i zarządzać użytkownikami zdarzenia w celu [zbadania użytkowników](investigate-users.md).


## <a name="mailboxes"></a>Skrzynki pocztowe

Karta **Skrzynki** pocztowe zawiera listę wszystkich skrzynek pocztowych, które zostały zidentyfikowane jako część zdarzenia lub które są związane z nim. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="Przykład strony Skrzynki pocztowe dla zdarzenia." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

Możesz zaznaczyć znacznik wyboru skrzynki pocztowej, aby wyświetlić listę aktywnych alertów. Wybierz nazwę skrzynki pocztowej, aby wyświetlić dodatkowe szczegóły skrzynki pocztowej na stronie Eksploratora dla programu Microsoft Defender dla Office 365.

## <a name="investigations"></a>Badania

Karta **Badania zawiera** listę [wszystkich zautomatyzowanych](m365d-autoir.md) badań wyzwalanych przez alerty dotyczące tego zdarzenia. Automatyczne badania będą wykonywać akcje naprawcze lub poczekać na zatwierdzenie akcji przez analityków w zależności od tego, jak skonfigurowano automatyczne badania do uruchamiania w programie Microsoft Defender dla endpoint i Defender dla systemu Office 365.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="Przykład strony Badania zdarzenia." lightbox="../../media/investigate-incidents/incident-investigations.png":::

Wybierz badanie, aby przejść do jego strony szczegółów, aby uzyskać pełne informacje na temat stanu badania i rozwiązywania problemów. Jeśli w ramach badania istnieją akcje oczekujące na zatwierdzenie, zostaną one wyświetlone na karcie Historia akcji **oczekujących** . Działania w ramach rozwiązywania problemów.

Jest też karta Wykres **badania** , która pokazuje:

- Połączenie alertów z zasobami w organizacji, których to wpływa.
- Jednostki powiązane z alertami, które są częścią historii ataków.
- Alerty dotyczące zdarzenia.

Wykres badania ułatwia szybkie zrozumienie pełnego zakresu ataków przez połączenie różnych podejrzanych jednostek, które są częścią ataków, z powiązanymi zasobami, takimi jak użytkownicy, urządzenia i skrzynki pocztowe. 

Aby uzyskać więcej informacji, zobacz [Automatyczne badanie i odpowiedź w programie Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>Dowód i odpowiedź

Karta **Dowód i odpowiedź** zawiera wszystkie obsługiwane zdarzenia i podejrzane jednostki w alertach dotyczących zdarzenia. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="Przykład strony dowodów i odpowiedzi dotyczącej zdarzenia." lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender automatycznie bada wszystkie zdarzenia obsługiwane przez zdarzenia oraz podejrzane jednostki w alertach, udostępniając Ci informacje o ważnych wiadomościach e-mail, plikach, procesach, usługach, adresach IP i innych elementach. Ułatwia to szybkie wykrywanie i blokowanie potencjalnych zagrożeń związanych z tym zdarzeniem.

Każdy z analizowanych obiektów jest oznaczony werdyktem (Złośliwy, Podejrzany, Oczyść) i stanem rozwiązywania problemów. Ułatwia to zrozumienie stanu rozwiązywania problemów w całym zdarzeniu i czynności, jakie można podjąć.

## <a name="graph-preview"></a>Graph (wersja zapoznawcza)

Karta **Graph** zawiera informacje o pełnym zakresie ataków, o tym, jak z czasem przebiegają ataki w Sieci, gdzie się rozpoczęło i jak daleko poszli atakujący. Łączy ona różne podejrzane jednostki, które są częścią ataków, z powiązanymi zasobami, takimi jak użytkownicy, urządzenia i skrzynki pocztowe. 

Na **Graph** zaawansowanej możesz:

1. Odtwarzaj alerty i węzły na wykresie w czasie, gdy występowały, aby zrozumieć chronologicznie atak.


   :::image type="content" source="../../media/investigate-incidents/incident-graph-play.gif" alt-text="Przykład odtwarzania alertów i węzłów na Graph głównej":::
 

2. Otwórz okienko encji, aby przejrzeć szczegóły encji i działać na działaniach naprawczych, takich jak usuwanie pliku lub odizolowanie urządzenia.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-entity-pane.png" alt-text="Przykład okienka encji na Graph głównej" lightbox="../../media/investigate-incidents/incident-graph-entity-pane.png":::

3. Wyróżnianie alertów na podstawie jednostki, z którą są powiązane.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-alert.png" alt-text="Przykład wyróżnienia alertu na Graph głównej" lightbox="../../media/investigate-incidents/incident-graph-alert.png":::

## <a name="next-steps"></a>Następne kroki

W razie potrzeby:

- [Badanie alertów o zdarzeniu](investigate-alerts.md)
- [Badanie użytkowników zdarzenia](investigate-users.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Określanie priorytetów zdarzeń](incident-queue.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
