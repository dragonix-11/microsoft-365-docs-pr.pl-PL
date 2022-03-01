---
title: Reagowanie na incydenty Microsoft 365 Defender
description: Badanie zdarzeń z różnych urządzeń, użytkowników i skrzynek pocztowych w portalu Microsoft 365 Defender sieci.
keywords: zdarzenia, alerty, badanie, analizowanie, odpowiedź, korelacja, ataki, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberataki
search.product: eADQiWindows 10XVcnh
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: ac908a03aad2ccbe203877250a84185cb6c8da16
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015401"
---
# <a name="incident-response-with-microsoft-365-defender"></a>Reagowanie na incydenty Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

> Chcesz doświadczyć Microsoft 365 Defender? Można go [ocenić w środowisku laboratoryjnym](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) lub [uruchomić projekt pilotażowy w środowisku produkcyjnym](m365d-pilot.md?ocid=cx-evalpilot).
>

Zdarzenie w Microsoft 365 Defender to zbiór skorelowanych alertów i skojarzonych z nimi danych, które są związane z atakiem. 

Microsoft 365 i aplikacje tworzą alerty po wykryciu podejrzanych lub złośliwych zdarzeń bądź aktywności. Poszczególne alerty zawierają cenne wskazówki dotyczące ukończonych lub trwających ataków. Jednak zazwyczaj w atakach stosowane są różne techniki wobec różnych typów obiektów, takich jak urządzenia, użytkownicy i skrzynki pocztowe. Wynikiem jest wiele alertów dla wielu obiektów w dzierżawie. 

Ponieważ wspólne alerty w celu uzyskania wglądu w ataki mogą być trudne i czasochłonne, dlatego Microsoft 365 Defender automatycznie agreguje alerty i skojarzone z nimi informacje w zdarzenie.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Skorelowanie Microsoft 365 Defender zdarzeń z jednostkami w zdarzenie." lightbox="../../media/incidents-overview/incidents.png":::

Obejrzyj to krótkie omówienie zdarzeń w czasie Microsoft 365 Defender (4 minuty).

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Grupowanie powiązanych alertów w incydentach zapewnia kompleksowy widok ataków. Możesz na przykład zobaczyć:

- Miejsce rozpoczęcia ataków.
- Jak używano taktyk.
- Jak daleko atak przeszedł w dzierżawę.
- Zakres ataków, na przykład na ile urządzeń, użytkowników i skrzynek pocztowych wpłynieło. 
- Wszystkie dane skojarzone z atakiem.

W [przypadku jej](m365d-enable.md) Microsoft 365 Defender automatyczne badanie [i rozwiązywanie](m365d-autoir.md) alertów za pośrednictwem automatyzacji i sztucznej inteligencji. Możesz również wykonać dodatkowe kroki rozwiązywania problemów w celu rozwiązania tego ataku. 

## <a name="incidents-and-alerts-in-the-microsoft-365-defender-portal"></a>Zdarzenia i alerty w portalu Microsoft 365 Defender wiadomości

Samodzielnie zarządzasz zdarzeniami **z & i alertami > zdarzeniami** podczas szybkiego uruchamiania portalu Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">zdarzeniach</a>. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Strona Zdarzenia w portalu Microsoft 365 Defender sieci Web." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Wybranie nazwy zdarzenia powoduje wyświetlenie podsumowania zdarzenia i zapewnia dostęp do kart z dodatkowymi informacjami. Oto przykład.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Przykład strony podsumowania zdarzenia w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Dodatkowe karty dla zdarzenia to:

- Alerty 

  Wszystkie alerty dotyczące zdarzenia i związane z nim informacje.

- Urządzenia

  Wszystkie urządzenia, które zostały zidentyfikowane jako część zdarzenia lub związane z nim.

- Użytkownicy

  Wszyscy użytkownicy, którzy są zidentyfikowani jako część zdarzenia lub są powiązani z nim.

- Skrzynki pocztowe

  Wszystkie skrzynki pocztowe, dla których określono, że są częścią zdarzenia lub są z nim związane.

- Badania

  Wszystkie zautomatyzowane [badania wyzwolone](m365d-autoir.md) przez alerty dotyczące zdarzenia.

- Dowód i odpowiedź

  Wszystkie obsługiwane zdarzenia i podejrzane jednostki w alertach o zdarzeniu.

- Graph (wersja zapoznawcza)

  Wizualna reprezentacja ataków, która łączy różne podejrzane jednostki, które są częścią ataków, z ich powiązanymi zasobami, takimi jak użytkownicy, urządzenia i skrzynki pocztowe.

Oto relacja między zdarzeniem i jego danymi a kartami zdarzenia w portalu Microsoft 365 Defender w.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Relacja zdarzenia i jego danych z kartami zdarzenia w portalu Microsoft 365 Defender zdarzenia." lightbox="../../media/incidents-overview/incidents-security-center.png":::

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>Przykładowy przepływ pracy reagowania na zdarzenia dla Microsoft 365 Defender

Oto przykładowy przepływ pracy do odpowiadania na zdarzenia w aplikacji Microsoft 365 z portalem Microsoft 365 Defender zadań.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Przykład przepływu pracy reagowania na incydenty dla Microsoft 365." lightbox="../../media/incidents-overview/incidents-example-workflow.png":::

Na bieżąco określ zdarzenia o najwyższym priorytecie do analizy i rozwiązania w kolejce zdarzeń i przygotuj je do reakcji. Jest to kombinacja:

- [Triagowanie w](incident-queue.md) celu określenia zdarzeń o najwyższym priorytecie za pomocą filtrowania i sortowania kolejki zdarzeń.
- [Zarządzanie](manage-incidents.md) zdarzeniami przez zmodyfikowanie ich tytułu, przypisanie ich do analityka oraz dodanie tagów i komentarzy.

Rozważ następujące kroki dla własnego przepływu pracy reagowania na incydenty:

1. W przypadku każdego zdarzenia rozpocznij [atak oraz analiza i analiza alertów](investigate-incidents.md):
 
   1. Wyświetl podsumowanie zdarzenia, aby zrozumieć jego zakres i ważność oraz jednostki, których dotyczy karta Podsumowanie i **Graph (Wersja** zapoznawcza).

   1. Rozpocznij analizowanie alertów, aby zrozumieć ich pochodzenie, zakres i ważność, za pomocą karty **Alerty** .

   1. W razie potrzeby zbieraj informacje na temat urządzeń, użytkowników i skrzynek pocztowych, których to ma wpływ, za pomocą kart **Urządzenia****, Użytkownicy** i **Skrzynki pocztowe**.

   1. Zobacz, Microsoft 365 Defender [automatycznie rozwiązano niektóre alerty](m365d-autoir.md) za pomocą **karty Badania**.
   
   1. W razie potrzeby użyj informacji z zestawu danych dotyczących zdarzenia, aby uzyskać więcej informacji na karcie **Dowód i** odpowiedź.

2. Po analizie lub w jej trakcie wykonuj zawieranie w celu zmniejszenia jakiegokolwiek dodatkowego wpływu ataków i ataku zagrożenia bezpieczeństwa.

3. W jak najbłędszej możliwej sprawie odzyskaj zasoby dzierżawy po ataku, przywracając zasoby dzierżawy do stanu, w którym były przed zdarzeniem.

4. [Rozwiąż](manage-incidents.md#resolve-an-incident) zdarzenie i pokłoń trochę czasu na naukę, która ma miejsce po zdarzeniu, aby:

   - Zrozumienie typu ataków i jego wpływu.
   - Zbadaj ataki w [narzędziu Analiza](threat-analytics.md) zagrożeń i społeczności zabezpieczeń w celu wykrywania trendu ataków na zabezpieczenia.
   - Odwołaj przepływ pracy użyty do rozwiązania zdarzenia i zaktualizuj standardowe przepływy pracy, procesy, zasady i podręczniki zgodnie z potrzebami.
   - Określ, czy konieczne są zmiany w konfiguracji zabezpieczeń, i je implementuj.

Jeśli jesteś nowym użytkownikiem analizy zabezpieczeń, zapoznaj się [](incidents-overview.md) z wprowadzeniem do reagowania na pierwsze zdarzenie, aby uzyskać dodatkowe informacje i przejść przez przykładowe zdarzenie.

Aby uzyskać więcej informacji na temat reakcji na incydenty w produktach firmy Microsoft, zobacz [ten artykuł](/security/compass/incident-response-overview).

## <a name="example-security-operations-for-microsoft-365-defender"></a>Przykładowe operacje zabezpieczeń na Microsoft 365 Defender

Oto przykład operacji zabezpieczeń (SecOps) dla Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Przykład operacji zabezpieczeń na Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-example-operations.png":::

Codzienne zadania mogą obejmować:

- [Zarządzanie](manage-incidents.md) zdarzeniami
- Przeglądanie [zautomatyzowanych akcji badania i odpowiedzi (AIR)](m365d-action-center.md) w Centrum akcji
- Przeglądanie najnowszej [analizy zagrożeń](threat-analytics.md)
- [Reagowanie](investigate-incidents.md) na zdarzenia

Zadania miesięczne mogą obejmować:

- Przeglądanie [ustawień air](m365d-configure-auto-investigation-response.md)
- Przeglądanie [bezpiecznego wyniku i](microsoft-secure-score-improvement-actions.md) [zagrożenia & zarządzania lukami w zabezpieczeniach](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Raportowanie w Twoim łańcuchu zarządzania zabezpieczeniami IT

Zadania kwartalne mogą obejmować raport i krótki raport dla głównego inspektora ds. zabezpieczeń informacji (CISO).

Zadania coroczne mogą obejmować przeprowadzanie istotnych ćwiczeń związanych z naruszeniem zabezpieczeń w celu przetestowania personelu, systemów i procesów. 

Za pomocą zadań dziennych, miesięcznych, kwartalnych i rocznych można aktualizować lub uściślić procesy, zasady i konfiguracje zabezpieczeń.

Zobacz [ Integrowanie Microsoft 365 Defender z operacjami zabezpieczeń,](integrate-microsoft-365-defender-secops.md) aby uzyskać więcej szczegółowych informacji.

### <a name="secops-resources-across-microsoft-products"></a>Zasoby usługi SecOps w produktach firmy Microsoft

Aby uzyskać więcej informacji na temat usługi SecOps w produktach firmy Microsoft, zobacz następujące zasoby:

- [Możliwości](/security/compass/security-operations-capabilities)
- [Najważniejsze wskazówki](/security/compass/security-operations)
- [Klipy wideo i slajdy](/security/compass/security-operations-videos-and-decks)


## <a name="get-incident-notifications-by-email"></a>Powiadomienia o incydentach za pośrednictwem poczty e-mail

Możesz skonfigurować powiadamianie Microsoft 365 Defender e-mail o nowych zdarzeniach lub aktualizacjach istniejących zdarzeń. Możesz otrzymywać powiadomienia na podstawie:

- Ważność zdarzenia.
- Grupa Urządzenia.
- Tylko w pierwszej aktualizacji na zdarzenie.

Powiadomienie e-mail zawiera między innymi ważne informacje o zdarzeniu, takie jak nazwa zdarzenia, ważność i kategorie. Możesz również przejść bezpośrednio do zdarzenia i od razu rozpocząć analizę. Aby uzyskać więcej informacji, zobacz [Badanie zdarzeń](investigate-incidents.md).

Możesz dodawać lub usuwać adresatów w powiadomieniach e-mail. Nowi adresaci są powiadamiani o incydentach po ich dodaniu. 

>[!NOTE]
>Do skonfigurowania **ustawień powiadomień e-mail** jest konieczne uprawnienie Zarządzanie ustawieniami zabezpieczeń. Jeśli wybrano podstawowe zarządzanie uprawnieniami, użytkownicy z rolami administratora zabezpieczeń lub administratora globalnego mogą konfigurować powiadomienia e-mail. <br> <br>
Podobnie, jeśli organizacja używa kontroli dostępu opartej na rolach (RBAC, role based access control), możesz tylko tworzyć, edytować, usuwać i odbierać powiadomienia w oparciu o grupy urządzeń, które możesz zarządzać.

### <a name="create-a-rule-for-email-notifications"></a>Tworzenie reguły dotyczącej powiadomień e-mail

Wykonaj poniższe czynności, aby utworzyć nową regułę i dostosować ustawienia powiadomień e-mail.

1. W okienku nawigacji wybierz pozycję Ustawienia > Microsoft 365 Defender > **e-mail o zdarzeniu**.
2. Wybierz **pozycję Dodaj element**.
3. Na stronie **Podstawy** wpisz nazwę reguły i opis, a następnie wybierz pozycję **Dalej**.
4. Na stronie **Ustawienia powiadomień** skonfiguruj:
    - **Ważność alertu** — wybierz ważność alertu, które powodują uruchomienie powiadomienia o zdarzeniu. Jeśli na przykład chcesz zostać poinformowany tylko o zdarzeniach o wysokim poziomie ważności, wybierz pozycję **Wysoka**.
    - **Zakres grupy urządzeń** — możesz określić wszystkie grupy urządzeń lub wybrać je z listy grup urządzeń w dzierżawie.
    - **Powiadamianie tylko przy pierwszym wystąpieniu zdarzenia** — wybierz, czy chcesz, aby powiadomienie było tylko przy pierwszym alercie, który jest taki, jak w przypadku innych zaznaczeń. Późniejsze aktualizacje i alerty dotyczące zdarzenia nie będą wysyłać dodatkowych powiadomień.
    - **Uwzględnij nazwę organizacji w wiadomości** e-mail — wybierz, czy nazwa organizacji ma być wyświetlana w powiadomieniu e-mail.
    - **Dołącz link do portalu specyficznego** dla dzierżawy — wybierz, czy chcesz dodać link z identyfikatorem dzierżawy w powiadomieniu e-mail o uzyskiwaniu dostępu do określonej Microsoft 365 dzierżawy.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Ustawienia powiadomień dotyczących powiadomień e-mail o incydentach." lightbox="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png":::

5. Wybierz pozycję **Dalej**. Na stronie **Adresaci** dodaj adresy e-mail, na które będą wysyłane powiadomienia o incydentach. Wybierz **pozycję Dodaj** po wpisaniu każdego nowego adresu e-mail. Aby przetestować powiadomienia i upewnić się, że adresaci otrzymają je w skrzynkach odbiorczych, wybierz pozycję **Wyślij testową wiadomość e-mail**. 
6. Wybierz pozycję **Dalej**. Na **stronie Recenzja** reguły przejrzyj ustawienia reguły, a następnie wybierz pozycję **Utwórz regułę**. W zależności od ustawień adresaci zaczną otrzymywać powiadomienia o incydentach za pośrednictwem poczty e-mail.

Aby edytować istniejącą regułę, wybierz ją z listy reguł. W okienku z nazwą reguły wybierz pozycję Edytuj  regułę i zmień ustawienia na stronach **Podstawowe** informacje, Ustawienia **powiadomień** **i Adresaci**.

Aby usunąć regułę, wybierz ją z listy reguł. W okienku z nazwą reguły wybierz pozycję **Usuń**.


## <a name="training-for-security-analysts"></a>Szkolenie dla analityków zabezpieczeń

Skorzystaj z tego modułu szkoleniowego firmy Microsoft Dowiedz się, jak za Microsoft 365 Defender zarządzać zdarzeniami i alertami.

|Szkolenie:|Badanie zdarzeń z Microsoft 365 Defender|
|---|---|
|![Badanie zdarzeń za pomocą Microsoft 365 Defender szkolenia.](../../media/incidents-overview/m365-defender-address-security-investigation.svg)| Microsoft 365 Defender zunifikuje dane o zagrożeniach z wielu usług i łączy je w zdarzenia i alerty przy jej połączeniu ze względu na technologię AI. Dowiedz się, jak zminimalizować czas między zdarzeniem a jego zarządzaniem na wypadek późniejszej odpowiedzi i rozwiązania problemu. <p> 27 min – 6 jednostek |

> [!div class="nextstepaction"]
> [Rozpoczynanie >](/learn/modules/defender-investigate-incidents/)

## <a name="next-steps"></a>Następne kroki

Skorzystaj z wymienionych czynności w zależności od poziomu doświadczenia lub roli w zespole zabezpieczeń.

### <a name="experience-level"></a>Poziom doświadczenia

Skorzystaj z tej tabeli, aby uzyskać poziom doświadczenia w analizie zabezpieczeń i reagowaniu na incydenty.

| Poziom | Kroki |
|:-------|:-----|
| **Nowy** | <ol><li> Zapoznaj się [z instruktażem](first-incident-overview.md) Odpowiadanie na pierwsze zdarzenie, aby zapoznać się z przewodnikiem po typowym procesie analizy, rozwiązywania problemów i przeglądu po incydentach w portalu Microsoft 365 Defender za pomocą przykładowego ataku. </li><li> Zobacz, które zdarzenia powinny [być priorytetyzowane](incident-queue.md) na podstawie istotności i innych czynników. </li><li> [Zarządzanie zdarzeniami](manage-incidents.md), które obejmują zmienianie nazw, przypisywanie, klasyfikowanie oraz dodawanie tagów i komentarzy na podstawie przepływu pracy zarządzania zdarzeniami.</li></ol> |
| **Wystąpił** | <ol><li> Rozpoczynanie pracy z kolejką zdarzeń **ze strony Zdarzenia** w portalu Microsoft 365 Defender sieci Web. W tym miejscu można wykonywać następujące czynności: </li> <ul><li> Zobacz, które zdarzenia powinny [być priorytetyzowane](incident-queue.md) na podstawie istotności i innych czynników. </li><li> [Zarządzanie zdarzeniami](manage-incidents.md), które obejmują zmienianie nazw, przypisywanie, klasyfikowanie oraz dodawanie tagów i komentarzy na podstawie przepływu pracy zarządzania zdarzeniami. </li><li> [Wykonuj](investigate-incidents.md) badania zdarzeń. </li></ul> </li><li> Śledzenie wyłaniających się zagrożeń i reagowanie na nie za pomocą [analizy zagrożeń](threat-analytics.md). </li><li>  Aktywne wyszukiwanie zagrożeń za pomocą [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md). </li><li> W tych [podręcznikach do reagowania](/security/compass/incident-response-playbooks) na incydenty znajdziesz szczegółowe wskazówki dotyczące prób wyłudzania informacji, haseł i wyrażania zgody na aplikacje. </li></ol> |


### <a name="security-team-role"></a>Rola zespołu zabezpieczeń

Postępuj zgodnie z tą tabelą w zależności od roli zespołu zabezpieczeń.

| Rola | Kroki |
|:-------|:-----|
| Odpowiadanie na incydenty (warstwa 1) | Rozpoczynanie pracy z kolejką zdarzeń **ze strony Zdarzenia** w portalu Microsoft 365 Defender sieci Web. W tym miejscu można wykonywać następujące czynności: <ul><li> Zobacz, które zdarzenia powinny [być priorytetyzowane](incident-queue.md) na podstawie istotności i innych czynników. </li><li> [Zarządzanie zdarzeniami](manage-incidents.md), które obejmują zmienianie nazw, przypisywanie, klasyfikowanie oraz dodawanie tagów i komentarzy na podstawie przepływu pracy zarządzania zdarzeniami. </li></ul> |
| Security szybki lub analityk (warstwa 2) | <ol><li> [Przejmij](investigate-incidents.md) badania nad zdarzeniami **na stronie** Zdarzenia w Microsoft 365 Defender sieci Web. </li><li> W tych [podręcznikach do reagowania](/security/compass/incident-response-playbooks) na incydenty znajdziesz szczegółowe wskazówki dotyczące prób wyłudzania informacji, haseł i wyrażania zgody na aplikacje. </li></ol> |
| Zaawansowani analitycy zabezpieczeń lub zaawansowani analitycy zagrożeń (warstwa 3) | <ol><li>[Przejmij](investigate-incidents.md) badania nad zdarzeniami **na stronie** Zdarzenia w Microsoft 365 Defender sieci Web. </li><li> Śledzenie wyłaniających się zagrożeń i reagowanie na nie za pomocą [analizy zagrożeń](threat-analytics.md). </li><li> Aktywne wyszukiwanie zagrożeń za pomocą [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md). </li><li> W tych [podręcznikach do reagowania](/security/compass/incident-response-playbooks) na incydenty znajdziesz szczegółowe wskazówki dotyczące prób wyłudzania informacji, haseł i wyrażania zgody na aplikacje. |
| Menedżer SOC | Zobacz, jak [zintegrować Microsoft 365 Defender z Centrum operacji zabezpieczeń (SOC).](integrate-microsoft-365-defender-secops.md) |

