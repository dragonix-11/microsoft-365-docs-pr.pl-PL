---
title: Reagowanie na zdarzenia za pomocą Microsoft 365 Defender
description: Badanie zdarzeń widocznych na różnych urządzeniach, użytkownikach i skrzynkach pocztowych w portalu Microsoft 365 Defender.
keywords: zdarzenia, alerty, badanie, analizowanie, reagowanie, korelacja, atak, maszyny, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, e-mail, 365, microsoft, m365, reagowanie na zdarzenia, cyberatak
search.product: eADQiWindows 10XVcnh
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 15b540f9993e8f2163f464379aca9496bec4cca7
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665387"
---
# <a name="incident-response-with-microsoft-365-defender"></a>Reagowanie na zdarzenia za pomocą Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

> Chcesz doświadczyć Microsoft 365 Defender? Można [go ocenić w środowisku laboratoryjnym](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) lub [uruchomić projekt pilotażowy w środowisku produkcyjnym](m365d-pilot.md?ocid=cx-evalpilot).
>

Zdarzenie w Microsoft 365 Defender to kolekcja skorelowanych alertów i skojarzonych danych, które składają się na historię ataku.

Microsoft 365 usługi i aplikacje tworzą alerty w przypadku wykrycia podejrzanego lub złośliwego zdarzenia lub działania. Poszczególne alerty dostarczają cennych wskazówek dotyczących zakończonego lub trwającego ataku. Jednak ataki zwykle stosują różne techniki względem różnych typów jednostek, takich jak urządzenia, użytkownicy i skrzynki pocztowe. Wynikiem jest wiele alertów dla wielu jednostek w dzierżawie.

Ponieważ łączenie poszczególnych alertów w celu uzyskania wglądu w atak może być trudne i czasochłonne, Microsoft 365 Defender automatycznie agreguje alerty i skojarzone z nimi informacje w zdarzeniu.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Jak Microsoft 365 Defender skoreluje zdarzenia z jednostek w zdarzeniu." lightbox="../../media/incidents-overview/incidents.png":::

Obejrzyj ten krótki przegląd zdarzeń w Microsoft 365 Defender (4 minuty).

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Grupowanie powiązanych alertów w zdarzeniu zapewnia kompleksowy wgląd w atak. Możesz na przykład zobaczyć:

- Gdzie rozpoczął się atak.
- Jakiej taktyki użyto.
- Jak daleko atak przeszedł do dzierżawy.
- Zakres ataku, taki jak liczba urządzeń, użytkowników i skrzynek pocztowych, które zostały naruszone.
- Wszystkie dane skojarzone z atakiem.

Jeśli [ta opcja jest włączona](m365d-enable.md), Microsoft 365 Defender może [automatycznie badać i rozwiązywać](m365d-autoir.md) alerty za pośrednictwem automatyzacji i sztucznej inteligencji. Możesz również wykonać dodatkowe kroki korygowania, aby rozwiązać problem z atakiem.

## <a name="incidents-and-alerts-in-the-microsoft-365-defender-portal"></a>Zdarzenia i alerty w portalu Microsoft 365 Defender

Zdarzeniami można zarządzać z poziomu **alertów & incydentów > zdarzeń** przy szybkim uruchomieniu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Strona Zdarzenia w portalu Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Wybranie nazwy zdarzenia powoduje wyświetlenie podsumowania zdarzenia i zapewnia dostęp do kart z dodatkowymi informacjami. Oto przykład.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Strona Podsumowanie zdarzenia w portalu Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Dodatkowe karty dotyczące zdarzenia to:

- Alerty

  Wszystkie alerty związane ze zdarzeniem i ich informacjami.

- Urządzeń

  Wszystkie urządzenia, które zostały zidentyfikowane jako część zdarzenia lub są z nimi powiązane.

- Użytkownicy

  Wszyscy użytkownicy, którzy zostali zidentyfikowani jako część zdarzenia lub są z nimi powiązani.

- Skrzynek pocztowych

  Wszystkie skrzynki pocztowe, które zostały zidentyfikowane jako należące do zdarzenia lub związane z tym zdarzeniem.

- Dochodzenia

  Wszystkie [zautomatyzowane badania](m365d-autoir.md) wyzwalane przez alerty w zdarzeniu.

- Dowody i odpowiedź

  Wszystkie obsługiwane zdarzenia i podejrzane jednostki w alertach zdarzenia.

- Graph (wersja zapoznawcza)

  Wizualna reprezentacja ataku łącząca różne podejrzane jednostki, które są częścią ataku, z powiązanymi zasobami, takimi jak użytkownicy, urządzenia i skrzynki pocztowe.

Oto relacja między zdarzeniem i jego danymi oraz karty zdarzenia w portalu Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Relacja zdarzenia i jego danych z kartami zdarzenia w portalu Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-security-center.png":::

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>Przykładowy przepływ pracy reagowania na zdarzenia dla Microsoft 365 Defender

Oto przykładowy przepływ pracy umożliwiający reagowanie na zdarzenia w Microsoft 365 za pomocą portalu Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Przykład przepływu pracy reagowania na zdarzenia dla portalu Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-example-workflow.png":::

Na bieżąco zidentyfikuj zdarzenia o najwyższym priorytecie do analizy i rozwiązania w kolejce zdarzeń i przygotuj je do odpowiedzi. Jest to kombinacja następujących elementów:

- [Klasyfikowanie](incident-queue.md) do określania zdarzeń o najwyższym priorytecie poprzez filtrowanie i sortowanie kolejki zdarzeń.
- [Zarządzanie zdarzeniami](manage-incidents.md) przez modyfikowanie ich tytułu, przypisywanie ich do analityka oraz dodawanie tagów i komentarzy.

Rozważ następujące kroki dla własnego przepływu pracy reagowania na zdarzenia:

1. Dla każdego incydentu rozpocznij [badanie i analizę ataków i alertów](investigate-incidents.md):

   1. Wyświetl podsumowanie zdarzenia, aby zrozumieć jego zakres i ważność oraz wpływ jednostek na karty **Podsumowanie** i **Graph** (wersja zapoznawcza).

   1. Rozpocznij analizowanie alertów w celu zrozumienia ich pochodzenia, zakresu i ważności za pomocą karty **Alerty** .

   1. W razie potrzeby zbierz informacje o urządzeniach, użytkownikach i skrzynkach pocztowych, korzystając z kart **Urządzenia**, **Użytkownicy** i **Skrzynki pocztowe** .

   1. Zobacz, jak Microsoft 365 Defender [automatycznie rozwiązało niektóre alerty](m365d-autoir.md) za pomocą karty **Badania**.

   1. W razie potrzeby użyj informacji w zestawie danych dla zdarzenia, aby uzyskać więcej informacji na karcie **Dowody i odpowiedź** .

2. Po lub w trakcie analizy wykonaj hermetyzację w celu zmniejszenia dodatkowego wpływu ataku i wyeliminowania zagrożenia bezpieczeństwa.

3. Jak najwięcej, odzyskaj sprawę po ataku, przywracając zasoby dzierżawy do stanu, w jakim znajdowały się przed incydentem.

4. [Rozwiąż](manage-incidents.md#resolve-an-incident) zdarzenie i poświęć czas na uczenie się po zdarzeniu:

   - Informacje o typie ataku i jego wpływie.
   - Zbadaj atak w usłudze [Threat Analytics](threat-analytics.md) i społeczności zabezpieczeń pod kątem trendu ataku na zabezpieczenia.
   - Przypomnij sobie przepływ pracy używany do rozwiązania zdarzenia i zaktualizowania standardowych przepływów pracy, procesów, zasad i podręczników w razie potrzeby.
   - Określ, czy potrzebne są zmiany w konfiguracji zabezpieczeń i zaimplementuj je.

Jeśli jesteś nowym użytkownikiem analizy zabezpieczeń, zapoznaj się z [wprowadzeniem do reagowania na pierwsze zdarzenie, aby](incidents-overview.md) uzyskać dodatkowe informacje i przejść przez przykładowe zdarzenie.

Aby uzyskać więcej informacji na temat reagowania na zdarzenia w produktach firmy Microsoft, zobacz [ten artykuł](/security/compass/incident-response-overview).

## <a name="example-security-operations-for-microsoft-365-defender"></a>Przykładowe operacje zabezpieczeń dla Microsoft 365 Defender

Oto przykład operacji zabezpieczeń (SecOps) dla Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Przykład operacji zabezpieczeń dla Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-example-operations.png":::

Codzienne zadania mogą obejmować:

- [Zarządzanie zdarzeniami](manage-incidents.md)
- Przeglądanie [zautomatyzowanych akcji badania i reagowania (AIR)](m365d-action-center.md) w centrum akcji
- Przeglądanie najnowszej analizy [zagrożeń](threat-analytics.md)
- [Reagowanie na](investigate-incidents.md) zdarzenia

Zadania miesięczne mogą obejmować:

- Przeglądanie [ustawień air](m365d-configure-auto-investigation-response.md)
- Przegląd [wskaźnika bezpieczeństwa](microsoft-secure-score-improvement-actions.md) i [zarządzania lukami w zabezpieczeniach & zagrożeń](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Raportowanie do łańcucha zarządzania zabezpieczeniami IT

Zadania kwartalne mogą obejmować raport i informacje o wynikach zabezpieczeń dla dyrektora ds. zabezpieczeń informacji (CISO).

Zadania roczne mogą obejmować przeprowadzenie poważnego zdarzenia lub naruszenia zabezpieczeń w celu przetestowania personelu, systemów i procesów.

Codzienne, miesięczne, kwartalne i roczne zadania mogą służyć do aktualizowania lub uściślania procesów, zasad i konfiguracji zabezpieczeń.

Aby uzyskać więcej informacji, zobacz [Integrowanie Microsoft 365 Defender z operacjami zabezpieczeń](integrate-microsoft-365-defender-secops.md).

### <a name="secops-resources-across-microsoft-products"></a>Zasoby usługi SecOps w produktach firmy Microsoft

Aby uzyskać więcej informacji o usłudze SecOps w produktach firmy Microsoft, zobacz następujące zasoby:

- [Możliwości](/security/compass/security-operations-capabilities)
- [Najważniejsze wskazówki](/security/compass/security-operations)
- [Klipy wideo i slajdy](/security/compass/security-operations-videos-and-decks)

## <a name="get-incident-notifications-by-email"></a>Pobieranie powiadomień o zdarzeniach pocztą e-mail

Możesz skonfigurować Microsoft 365 Defender, aby powiadomić pracowników pocztą e-mail o nowych zdarzeniach lub aktualizacjach istniejących zdarzeń. Możesz wybrać opcję otrzymywania powiadomień na podstawie:

- Ważność zdarzenia.
- Grupa urządzeń.
- Tylko przy pierwszej aktualizacji na zdarzenie.

Powiadomienie e-mail zawiera między innymi ważne informacje o zdarzeniu, takie jak nazwa zdarzenia, ważność i kategorie. Możesz również przejść bezpośrednio do zdarzenia i od razu rozpocząć analizę. Aby uzyskać więcej informacji, zobacz [Badanie zdarzeń](investigate-incidents.md).

W powiadomieniach e-mail możesz dodawać lub usuwać adresatów. Nowi adresaci otrzymują powiadomienia o zdarzeniach po ich dodaniu.

> [!NOTE]
> Aby skonfigurować ustawienia powiadomień e-mail, potrzebne jest uprawnienie **Zarządzanie ustawieniami zabezpieczeń** . Jeśli wybrano użycie podstawowego zarządzania uprawnieniami, użytkownicy z rolami administratora zabezpieczeń lub administratora globalnego mogą konfigurować powiadomienia e-mail. <br> <br>
Podobnie, jeśli organizacja korzysta z kontroli dostępu opartej na rolach (RBAC), możesz tworzyć, edytować, usuwać i odbierać powiadomienia na podstawie grup urządzeń, które mogą być zarządzane.

### <a name="create-a-rule-for-email-notifications"></a>Tworzenie reguły dla powiadomień e-mail

Wykonaj następujące kroki, aby utworzyć nową regułę i dostosować ustawienia powiadomień e-mail.

1. W okienku nawigacji wybierz pozycję **Ustawienia > Microsoft 365 Defender > Powiadomienia e-mail o zdarzeniach**.
2. Wybierz pozycję **Dodaj element**.
3. Na stronie **Podstawy wpisz nazwę reguły** i opis, a następnie wybierz pozycję **Dalej**.
4. Na stronie **Ustawienia powiadomień** skonfiguruj:
    - **Ważność alertu** — wybierz ważność alertów, które będą wyzwalać powiadomienie o zdarzeniu. Jeśli na przykład chcesz mieć tylko informacje o zdarzeniach o wysokiej ważności, wybierz pozycję **Wysoki**.
    - **Zakres grupy urządzeń** — możesz określić wszystkie grupy urządzeń lub wybrać z listy grup urządzeń w dzierżawie.
    - **Powiadamiaj tylko o pierwszym wystąpieniu na zdarzenie** — wybierz, czy chcesz otrzymywać powiadomienie tylko w pierwszym alercie, który pasuje do innych wybranych opcji. Późniejsze aktualizacje lub alerty związane ze zdarzeniem nie będą wysyłać dodatkowych powiadomień.
    - **Dołącz nazwę organizacji do wiadomości e-mail** — wybierz, czy nazwa organizacji ma być wyświetlana w powiadomieniu e-mail.
    - **Dołącz link portalu specyficzny dla dzierżawy** — wybierz, czy chcesz dodać link z identyfikatorem dzierżawy w powiadomieniu e-mail w celu uzyskania dostępu do określonej dzierżawy Microsoft 365.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Strona Ustawienia powiadomień dla powiadomień e-mail o zdarzeniach w portalu Microsoft 365 Defender." lightbox="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png":::

5. Wybierz pozycję **Dalej**. Na stronie **Adresaci** dodaj adresy e-mail, które będą otrzymywać powiadomienia o zdarzeniu. Wybierz pozycję **Dodaj** po wpisaniu każdego nowego adresu e-mail. Aby przetestować powiadomienia i upewnić się, że adresaci otrzymają je w skrzynkach odbiorczych, wybierz pozycję **Wyślij testowy adres e-mail**.
6. Wybierz pozycję **Dalej**. Na stronie **Przejrzyj regułę** przejrzyj ustawienia reguły, a następnie wybierz pozycję **Utwórz regułę**. Adresaci zaczną otrzymywać powiadomienia o zdarzeniach za pośrednictwem poczty e-mail na podstawie ustawień.

Aby edytować istniejącą regułę, wybierz ją z listy reguł. W okienku o nazwie reguły wybierz pozycję **Edytuj regułę** i wprowadź zmiany na stronach **Podstawy**, **Ustawienia powiadomień** i **Adresaci** .

Aby usunąć regułę, wybierz ją z listy reguł. W okienku o nazwie reguły wybierz pozycję **Usuń**.

## <a name="training-for-security-analysts"></a>Szkolenia dla analityków zabezpieczeń

Skorzystaj z tego modułu szkoleniowego z usługi Microsoft Learn, aby dowiedzieć się, jak używać Microsoft 365 Defender do zarządzania zdarzeniami i alertami.

|Szkolenia:|Badanie zdarzeń za pomocą Microsoft 365 Defender|
|---|---|
|![Badanie zdarzeń za pomocą ikony trenowania Microsoft 365 Defender.](../../media/incidents-overview/m365-defender-address-security-investigation.svg)| Microsoft 365 Defender ujednolica dane zagrożeń z wielu usług i używa sztucznej inteligencji do łączenia ich w zdarzenia i alerty. Dowiedz się, jak zminimalizować czas między zdarzeniem a jego zarządzaniem w celu późniejszego reagowania i rozwiązywania problemów. <p> 27 min — 6 jednostek |

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/defender-investigate-incidents/)

## <a name="next-steps"></a>Następne kroki

Wykonaj wymienione kroki na podstawie poziomu doświadczenia lub roli w zespole ds. zabezpieczeń.

### <a name="experience-level"></a>Poziom doświadczenia

Postępuj zgodnie z tą tabelą, aby uzyskać poziom doświadczenia w zakresie analizy zabezpieczeń i reagowania na zdarzenia.

| Poziom | Kroki |
|:-------|:-----|
| **Nowy** | <ol><li> Zapoznaj [się z przewodnikiem Reagowanie na pierwsze zdarzenie](first-incident-overview.md), aby zapoznać się z przewodnikiem po typowym procesie analizy, korygowania i przeglądu po zdarzeniu w portalu Microsoft 365 Defender z przykładem ataku. </li><li> Sprawdź, które zdarzenia powinny być [traktowane priorytetowo](incident-queue.md) na podstawie ważności i innych czynników. </li><li> [Zarządzanie zdarzeniami](manage-incidents.md), w tym zmienianie nazw, przypisywanie, klasyfikowanie i dodawanie tagów i komentarzy na podstawie przepływu pracy zarządzania zdarzeniami.</li></ol> |
| **Doświadczonych** | <ol><li> Wprowadzenie z kolejką zdarzeń na stronie **Zdarzenia** w portalu Microsoft 365 Defender. W tym miejscu można wykonywać następujące czynności: </li> <ul><li> Sprawdź, które zdarzenia powinny być [traktowane priorytetowo](incident-queue.md) na podstawie ważności i innych czynników. </li><li> [Zarządzanie zdarzeniami](manage-incidents.md), w tym zmienianie nazw, przypisywanie, klasyfikowanie i dodawanie tagów i komentarzy na podstawie przepływu pracy zarządzania zdarzeniami. </li><li> [Przeprowadzanie badań](investigate-incidents.md) zdarzeń. </li></ul> </li><li> Śledzenie pojawiających się zagrożeń i reagowanie na nie przy użyciu [analizy zagrożeń](threat-analytics.md). </li><li>  Proaktywne wyszukiwanie zagrożeń przy [użyciu zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md). </li><li> Zobacz te [podręczniki reagowania na zdarzenia, aby](/security/compass/incident-response-playbooks) uzyskać szczegółowe wskazówki dotyczące wyłudzania informacji, sprayu haseł i ataków udzielania zgody aplikacji. </li></ol> |

### <a name="security-team-role"></a>Rola zespołu ds. zabezpieczeń

Postępuj zgodnie z tą tabelą w oparciu o rolę zespołu ds. zabezpieczeń.

| Rola | Kroki |
|---|---|
| Osoba reagująca na zdarzenia (warstwa 1) | Wprowadzenie z kolejką zdarzeń na stronie **Zdarzenia** w portalu Microsoft 365 Defender. W tym miejscu można wykonywać następujące czynności: <ul><li> Sprawdź, które zdarzenia powinny być [traktowane priorytetowo](incident-queue.md) na podstawie ważności i innych czynników. </li><li> [Zarządzanie zdarzeniami](manage-incidents.md), w tym zmienianie nazw, przypisywanie, klasyfikowanie i dodawanie tagów i komentarzy na podstawie przepływu pracy zarządzania zdarzeniami. </li></ul> |
| Badacz zabezpieczeń lub analityk (warstwa 2) | <ol><li> [Przeprowadź badania](investigate-incidents.md) zdarzeń na stronie **Zdarzenia** w portalu Microsoft 365 Defender. </li><li> Zobacz te [podręczniki reagowania na zdarzenia, aby](/security/compass/incident-response-playbooks) uzyskać szczegółowe wskazówki dotyczące wyłudzania informacji, sprayu haseł i ataków udzielania zgody aplikacji. </li></ol> |
| Zaawansowany analityk zabezpieczeń lub łowca zagrożeń (warstwa 3) | <ol><li>[Przeprowadź badania](investigate-incidents.md) zdarzeń na stronie **Zdarzenia** w portalu Microsoft 365 Defender. </li><li> Śledzenie pojawiających się zagrożeń i reagowanie na nie przy użyciu [analizy zagrożeń](threat-analytics.md). </li><li> Proaktywne wyszukiwanie zagrożeń przy [użyciu zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md). </li><li> Zobacz te [podręczniki reagowania na zdarzenia, aby](/security/compass/incident-response-playbooks) uzyskać szczegółowe wskazówki dotyczące wyłudzania informacji, sprayu haseł i ataków udzielania zgody aplikacji. |
| Menedżer SOC | Zobacz, jak [zintegrować Microsoft 365 Defender z centrum operacji zabezpieczeń (SOC).](integrate-microsoft-365-defender-secops.md) |
