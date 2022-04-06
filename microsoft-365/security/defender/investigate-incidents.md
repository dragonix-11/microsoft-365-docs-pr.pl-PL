---
title: Badanie zdarzeń w Microsoft 365 Defender
description: Badanie zdarzeń związanych z urządzeniami, użytkownikami i skrzynkami pocztowymi.
keywords: zdarzenie, incydenty, analizowanie, reagowanie, maszyny, urządzenia, użytkownicy, tożsamości, poczta, poczta e-mail, skrzynka pocztowa, badanie, wykres, dowody
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
- incidentresponse
- m365solution-incidentresponse
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 8138c07ab871ab1a6a8d89df980c914983bbb58e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666949"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>Badanie zdarzeń w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Microsoft 365 Defender agreguje wszystkie powiązane alerty, zasoby, badania i dowody z różnych urządzeń, użytkowników i skrzynek pocztowych w zdarzenia, aby umożliwić kompleksowe zapoznanie się z całym zakresem ataku.

W ramach zdarzenia analizujesz alerty wpływające na sieć, rozumiesz, co one oznaczają, i zbierasz dowody, aby można było opracować skuteczny plan korygowania.

## <a name="initial-investigation"></a>Wstępne badanie

Przed zapoznaniem się ze szczegółami przyjrzyj się właściwościom i podsumowaniu zdarzenia.

Możesz zacząć od wybrania zdarzenia z kolumny znacznika wyboru. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="Wybieranie zdarzenia w portalu Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

Gdy to zrobisz, zostanie otwarte okienko podsumowania z kluczowymi informacjami o zdarzeniu, takimi jak ważność, do której został przypisany, oraz kategoriami [MITRE ATT&CK&trade;](https://attack.mitre.org/) dla zdarzenia. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="Okienko zawierające szczegóły podsumowania zdarzenia w portalu Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

W tym miejscu możesz wybrać pozycję **Otwórz stronę zdarzenia**. Spowoduje to otwarcie strony głównej zdarzenia, na której znajdziesz więcej informacji podsumowania i kart dotyczących alertów, urządzeń, użytkowników, badań i dowodów.

Możesz również otworzyć stronę główną zdarzenia, wybierając nazwę zdarzenia z kolejki zdarzeń.

## <a name="summary"></a>Podsumowanie

Na stronie **Podsumowanie przedstawiono** migawkę najważniejszych elementów, które należy zauważyć na temat zdarzenia.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Podsumowanie informacji o zdarzeniu w portalu Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Informacje są zorganizowane w tych sekcjach.

| Sekcji | Opis |
|:-------|:-----|
| Alerty i kategorie | Wizualny i liczbowy widok zaawansowanego ataku na łańcuch zabijania. Podobnie jak w przypadku innych produktów zabezpieczeń firmy Microsoft, Microsoft 365 Defender jest dopasowana do struktury [MITRE ATT&CK&trade;](https://attack.mitre.org/). Oś czasu alertów przedstawia kolejność chronologiczną, w której wystąpiły alerty, oraz ich stan i nazwę. |
| Zakres |  Wyświetla liczbę urządzeń, użytkowników i skrzynek pocztowych, których dotyczy problem, oraz wyświetla listę jednostek w kolejności poziomu ryzyka i priorytetu badania. |
| Dowody | Przedstawia liczbę jednostek, których dotyczy zdarzenie. |
| Informacje o zdarzeniu | Wyświetla właściwości zdarzenia, takie jak tagi, stan i ważność. |
|||

Użyj strony **Podsumowanie** , aby ocenić względne znaczenie zdarzenia i szybko uzyskać dostęp do skojarzonych alertów i jednostek, których dotyczy problem.

## <a name="alerts"></a>Alerty

Na **karcie Alerty** możesz wyświetlić kolejkę alertów dla alertów związanych z incydentem i inne informacje o nich, takie jak:

- Ważności.
- Jednostki, które brały udział w alercie.
- Źródło alertów (Microsoft Defender for Identity, Ochrona punktu końcowego w usłudze Microsoft Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Defender dla Chmury Apps i dodatku ładu aplikacji).
- Powód, dla którego byli ze sobą powiązani.

Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="Okienko Alerty dotyczące zdarzenia w portalu Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-alerts.png":::

Domyślnie alerty są uporządkowane chronologicznie, aby umożliwić sprawdzenie, jak atak rozgrywał się w czasie. Po wybraniu alertu w ramach zdarzenia Microsoft 365 Defender wyświetla informacje o alertach specyficzne dla kontekstu ogólnego zdarzenia. 

Możesz zobaczyć zdarzenia alertu, które inne wyzwolone alerty spowodowały bieżący alert, oraz wszystkie jednostki i działania, których dotyczy atak, w tym urządzenia, pliki, użytkownicy i skrzynki pocztowe.

Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="Szczegóły alertu w obrębie zdarzenia w portalu Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

Strona alertu o zdarzeniu zawiera następujące sekcje:

- Historia alertu, która obejmuje:

   - Co się stało

   - Podjęte działania

   - Zdarzenia pokrewne

- Właściwości alertu w okienku po prawej stronie (stan, szczegóły, opis i inne)

Nie każdy alert będzie miał wszystkie wymienione podsekcje w sekcji **Historia alertu** .

Dowiedz się, jak używać kolejki alertów i stron [alertów w ramach badania alertów](investigate-alerts.md).

## <a name="devices"></a>Urządzeń

Na karcie **Urządzenia** są wyświetlane wszystkie urządzenia związane ze zdarzeniem. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="Strona Urządzenia zdarzenia w portalu Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-devices.png":::

Możesz wybrać znacznik wyboru dla urządzenia, aby wyświetlić szczegóły urządzenia, danych katalogu, aktywnych alertów i zalogowanych użytkowników. Wybierz nazwę urządzenia, aby wyświetlić szczegóły urządzenia w spisie urządzeń usługi Defender for Endpoint. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="Strona Dotycząca opcji Spis urządzeń w Ochrona punktu końcowego w usłudze Microsoft Defender." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

Na stronie urządzenia możesz zebrać dodatkowe informacje o urządzeniu, takie jak wszystkie jego alerty, oś czasu i zalecenia dotyczące zabezpieczeń. Na przykład na karcie **Oś czasu** możesz przewijać oś czasu maszyny i wyświetlać wszystkie zdarzenia i zachowania obserwowane na maszynie w kolejności chronologicznej, przeplatane z wywołanymi alertami.

> [!TIP]
> Skany na żądanie można wykonywać na stronie urządzenia. W portalu Microsoft 365 Defender wybierz pozycję **Punkty końcowe > Spis urządzeń**. Wybierz urządzenie z alertami, a następnie uruchom skanowanie antywirusowe. Akcje, takie jak skanowanie antywirusowe, są śledzone i widoczne na stronie **Spis urządzeń** . Aby dowiedzieć się więcej, zobacz [Uruchamianie skanowania programu antywirusowego Defender na urządzeniach](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>Użytkownicy

Karta **Użytkownicy** zawiera listę wszystkich użytkowników, którzy zostali zidentyfikowani jako część zdarzenia lub powiązani z tym zdarzeniem. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Strona Użytkownicy w portalu Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-users.png":::

Możesz wybrać znacznik wyboru dla użytkownika, aby wyświetlić szczegóły zagrożenia, narażenia i informacji kontaktowych konta użytkownika. Wybierz nazwę użytkownika, aby wyświetlić dodatkowe szczegóły konta użytkownika.

Dowiedz się, jak wyświetlać dodatkowe informacje o użytkownikach i zarządzać użytkownikami zdarzenia w [celu zbadania użytkowników](investigate-users.md).


## <a name="mailboxes"></a>Skrzynek pocztowych

Karta **Skrzynki pocztowe** zawiera listę wszystkich skrzynek pocztowych, które zostały zidentyfikowane jako należące do zdarzenia lub związane z tym zdarzeniem. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="Strona Skrzynki pocztowe zdarzenia w portalu Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

Możesz wybrać znacznik wyboru dla skrzynki pocztowej, aby wyświetlić listę aktywnych alertów. Wybierz nazwę skrzynki pocztowej, aby wyświetlić dodatkowe szczegóły skrzynki pocztowej na stronie Eksplorator, aby Ochrona usługi Office 365 w usłudze Defender.

## <a name="investigations"></a>Dochodzenia

Na **karcie Badania** są wyświetlane wszystkie [zautomatyzowane badania](m365d-autoir.md) wyzwalane przez alerty w tym zdarzeniu. Zautomatyzowane badania będą wykonywać akcje korygowania lub czekać na zatwierdzenie przez analityka akcji, w zależności od tego, jak skonfigurowano automatyczne badania do uruchamiania w usłudze Defender for Endpoint i Ochrona usługi Office 365 w usłudze Defender.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="Strona Badania dotyczące zdarzenia w portalu Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-investigations.png":::

Wybierz badanie, aby przejść do jego strony szczegółów, aby uzyskać pełne informacje na temat stanu badania i korygowania. Jeśli w ramach badania oczekują jakiekolwiek akcje oczekujące na zatwierdzenie, zostaną one wyświetlone na karcie **Historia oczekujących akcji** . Podejmij działania w ramach korygowania incydentów.

Istnieje również karta **Wykres badania** , która pokazuje:

- Połączenie alertów z zasobami, których dotyczy problem w organizacji.
- Które jednostki są powiązane z alertami i jak są częścią historii ataku.
- Alerty dotyczące zdarzenia.

Wykres badania pomaga szybko zrozumieć pełny zakres ataku, łącząc różne podejrzane jednostki, które są częścią ataku, z powiązanymi zasobami, takimi jak użytkownicy, urządzenia i skrzynki pocztowe. 

Aby uzyskać więcej informacji, zobacz [Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>Dowody i odpowiedź

Karta **Dowody i odpowiedź** pokazuje wszystkie obsługiwane zdarzenia i podejrzane jednostki w alertach w zdarzeniu. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="Strona Dowody i reagowanie na zdarzenie w portalu Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender automatycznie bada wszystkie zdarzenia obsługiwane przez zdarzenia i podejrzane jednostki w alertach, udostępniając informacje o ważnych wiadomościach e-mail, plikach, procesach, usługach, adresach IP i innych. Pomaga to szybko wykrywać i blokować potencjalne zagrożenia w zdarzeniu.

Każda z analizowanych jednostek jest oznaczona werdyktem (Złośliwy, Podejrzany, Czysty) i stanem korygowania. Ułatwia to zrozumienie stanu korygowania całego incydentu i możliwości wykonania kolejnych kroków.

## <a name="graph-preview"></a>Graph (wersja zapoznawcza)

Na karcie **Graph** przedstawiono pełny zakres ataku, sposób rozprzestrzeniania się ataku przez sieć w czasie, miejsce jego rozpoczęcia i jak daleko posunęli się atakujący. Łączy różne podejrzane jednostki, które są częścią ataku, z powiązanymi zasobami, takimi jak użytkownicy, urządzenia i skrzynki pocztowe. 

Na karcie **Graph** możesz:

1. Odtwórz alerty i węzły na wykresie, ponieważ wystąpiły one wraz z upływem czasu, aby zrozumieć chronologię ataku.


   :::image type="content" source="../../media/investigate-incidents/incident-graph-play.gif" alt-text="Odtwarzanie alertów i węzłów na stronie Graph":::
 

2. Otwórz okienko jednostki, co umożliwia przeglądanie szczegółów jednostki i wykonywanie działań korygujących, takich jak usuwanie pliku lub izolowanie urządzenia.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-entity-pane.png" alt-text="Okienko jednostki na stronie Graph w portalu Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-graph-entity-pane.png":::

3. Wyróżnij alerty na podstawie jednostki, z którą są one powiązane.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-alert.png" alt-text="Wyróżnienie alertu na stronie Graph" lightbox="../../media/investigate-incidents/incident-graph-alert.png":::

## <a name="next-steps"></a>Następne kroki

W razie potrzeby:

- [Badanie alertów zdarzenia](investigate-alerts.md)
- [Badanie użytkowników zdarzenia](investigate-users.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Określanie priorytetów zdarzeń](incident-queue.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
