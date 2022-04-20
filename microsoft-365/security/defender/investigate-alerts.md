---
title: Badanie alertów w Microsoft 365 Defender
description: Zbadaj alerty widoczne na różnych urządzeniach, użytkownikach i skrzynkach pocztowych.
keywords: zdarzenia, alerty, badanie, analizowanie, reagowanie, korelacja, atak, maszyny, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
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
ms.technology: m365d
ms.openlocfilehash: fd043ae1ebabcb8162ed96b973c9392bae5fd2a1
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944442"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Badanie alertów w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

>[!Note]
>W tym artykule opisano alerty zabezpieczeń w Microsoft 365 Defender. Można jednak używać alertów aktywności do wysyłania powiadomień e-mail do siebie lub innych administratorów, gdy użytkownicy wykonują określone działania w Microsoft 365. Aby uzyskać więcej informacji, zobacz [Tworzenie alertów dotyczących działań — Microsoft Purview | Microsoft Docs](../../compliance/create-activity-alerts.md).

Alerty są podstawą wszystkich zdarzeń i wskazują wystąpienie złośliwych lub podejrzanych zdarzeń w środowisku. Alerty są zazwyczaj częścią szerszego ataku i dostarczają wskazówek dotyczących zdarzenia.

W Microsoft 365 Defender powiązane alerty są agregowane razem w celu utworzenia [zdarzeń](incidents-overview.md). Incydenty zawsze zapewniają szerszy kontekst ataku, jednak analizowanie alertów może być przydatne, gdy wymagana jest dokładniejsza analiza.

**W kolejce Alerty** jest wyświetlany bieżący zestaw alertów. Do kolejki alertów można dostać się z poziomu **alertów & zdarzeń > alertów podczas** szybkiego uruchamiania [portalu Microsoft 365 Defender](https://go.microsoft.com/fwlink/p/?linkid=2077139).

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Sekcja Alerty w portalu Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png":::

Alerty z różnych rozwiązań zabezpieczeń firmy Microsoft, takich jak Ochrona punktu końcowego w usłudze Microsoft Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender i Microsoft 365 Defender zostaną wyświetlone tutaj.

Domyślnie kolejka alertów w portalu Microsoft 365 Defender wyświetla nowe i w toku alerty z ostatnich 30 dni. Najnowszy alert znajduje się w górnej części listy, więc możesz go najpierw zobaczyć. 

W domyślnej kolejce alertów możesz wybrać pozycję **Filtr** , aby wyświetlić okienko **Filtr** , z którego można określić podzestaw alertów. Oto przykład.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Sekcja Filtry w portalu Microsoft 365 Defender." lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png":::

Alerty można filtrować zgodnie z następującymi kryteriami:

- Ważności
- Stan
- Źródła usług
- Jednostki (zasoby, których dotyczy problem)
- Stan zautomatyzowanego badania

## <a name="required-roles-for-defender-for-office-365-alerts"></a>Wymagane role dla alertów Ochrona usługi Office 365 w usłudze Defender

Aby uzyskać dostęp do alertów Ochrona usługi Office 365 w usłudze Microsoft Defender, musisz mieć dowolną z następujących ról:

- W przypadku ról globalnych Azure Active Directory (Azure AD):

   - Administrator globalny

   - Administrator zabezpieczeń

   - Operator zabezpieczeń

   - Czytelnik globalny

   - Czytelnik zabezpieczeń

- grupy ról & zgodności Office 365 zabezpieczeń

   - Administrator zgodności

   - Zarządzanie organizacją 

- [Rola niestandardowa](custom-roles.md)

## <a name="analyze-an-alert"></a>Analizowanie alertu

Aby wyświetlić główną stronę alertu, wybierz nazwę alertu. Oto przykład.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Szczegóły alertu w portalu Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png":::

Możesz również wybrać akcję **Otwórz główną stronę alertu** w okienku **Zarządzanie alertami** .

Strona alertu składa się z następujących sekcji: 

- Historia alertów, czyli łańcuch zdarzeń i alertów związanych z tym alertem w kolejności chronologicznej
- Szczegóły podsumowania

Na stronie alertu możesz wybrać wielokropek (**...**) obok dowolnej jednostki, aby wyświetlić dostępne akcje, takie jak łączenie alertu z innym incydentem. Lista dostępnych akcji zależy od typu alertu.

### <a name="alert-sources"></a>Źródła alertów

Microsoft 365 Defender alerty mogą pochodzić z rozwiązań takich jak Ochrona punktu końcowego w usłudze Microsoft Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Microsoft Defender for Cloud Apps i dodatku ładu aplikacji dla Microsoft Defender for Cloud Apps. Możesz zauważyć alerty z przedpłaconymi znakami w alercie. Poniższa tabela zawiera wskazówki ułatwiające zrozumienie mapowania źródeł alertów na podstawie wstępnie utworzonego znaku alertu.

> [!NOTE]
> - Przedpłacone identyfikatory GUID są specyficzne tylko dla ujednoliconych środowisk, takich jak ujednolicona kolejka alertów, strona ujednoliconych alertów, ujednolicone badanie i ujednolicone zdarzenie.
> - Znak przedprodukowany nie zmienia identyfikatora GUID alertu. Jedyną zmianą identyfikatora GUID jest składnik przedprodukowany.

| Źródło alertu | Znak przedprodukowany |
| :---|:--- |
| Ochrona usługi Office 365 w usłudze Microsoft Defender | `fa{GUID}` <br> Przykład: `fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Ochrona punktu końcowego w usłudze Microsoft Defender | `da` lub `ed` dla alertów wykrywania niestandardowego <br> |
| Microsoft Defender for Identity | `aa{GUID}` <br> Przykład: `aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Cloud Apps |`ca{GUID}` <br> Przykład: `ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>Analizowanie zasobów, których dotyczy problem

Sekcja **Podjęte akcje** zawiera listę elementów zawartości, których dotyczy problem, takich jak skrzynki pocztowe, urządzenia i użytkownicy, których dotyczy ten alert. 

Możesz również wybrać pozycję **Widok w centrum akcji**, aby wyświetlić kartę **Historia** **centrum akcji** w portalu Microsoft 365 Defender. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Śledzenie roli alertu w historii alertu

W scenariuszu alertu zostaną wyświetlone wszystkie zasoby lub jednostki związane z alertem w widoku drzewa procesów. Alert w tytule jest tym, który koncentruje się po pierwszym wylądowaniu na stronie wybranego alertu. Zasoby w wątku alertu można rozszerzać i klikać. Zapewniają one dodatkowe informacje i przyspieszają reagowanie, umożliwiając podjęcie akcji bezpośrednio w kontekście strony alertu. 

> [!NOTE]
> Sekcja dotycząca alertów może zawierać więcej niż jeden alert z dodatkowymi alertami dotyczącymi tego samego drzewa wykonywania wyświetlanymi przed wybranym alertem lub po nim.

### <a name="view-more-alert-information-on-the-details-page"></a>Wyświetl więcej informacji o alertach na stronie szczegółów

Na stronie szczegółów są wyświetlane szczegóły wybranego alertu ze szczegółami i powiązanymi z nim akcjami. Jeśli wybierzesz dowolne zasoby lub jednostki, których dotyczy problem w wątku alertu, strona szczegółów zmieni się, aby podać informacje kontekstowe i akcje dla wybranego obiektu.

Po wybraniu interesującej jednostki strona szczegółów zmienia się, aby wyświetlić informacje o wybranym typie jednostki, informacje historyczne, gdy są dostępne, oraz opcje podejmowania działań na tej jednostce bezpośrednio ze strony alertu.

## <a name="manage-alerts"></a>Zarządzaj alertami

Aby zarządzać alertem, wybierz pozycję **Zarządzaj alertem** w sekcji szczegóły podsumowania na stronie alertu. W przypadku pojedynczego alertu oto przykład okienka **Zarządzanie alertami** .

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Sekcja Zarządzanie alertami w portalu Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png":::

Okienko **Zarządzanie alertami** umożliwia wyświetlanie lub określanie:

- Stan alertu (Nowy, Rozwiązany, W toku).
- Konto użytkownika, do których przypisano alert.
- Klasyfikacja alertu:

   - **Nie ustawiono** (wartość domyślna).

   - **Wartość prawdziwie dodatnia** z typem zagrożenia. Użyj tej klasyfikacji dla alertów, które dokładnie wskazują rzeczywiste zagrożenie. Określenie typu zagrożenia ułatwia zespołowi ds. zabezpieczeń wyświetlanie wzorców zagrożeń i działanie w celu obrony organizacji przed nimi.

   - **Działanie informacyjne, oczekiwane** z typem działania. Użyj opcji w tej kategorii, aby sklasyfikować alerty dla testów zabezpieczeń, działania czerwonego zespołu i oczekiwanego nietypowego zachowania zaufanych aplikacji i użytkowników.

   - **Wynik fałszywie dodatni** dla typów alertów, które zostały utworzone nawet wtedy, gdy nie ma złośliwego działania. Klasyfikowanie alertów jako fałszywie dodatnich pomaga Microsoft 365 Defender poprawić jego jakość wykrywania.

- Komentarz do alertu.

> [!NOTE]
> Jednym ze sposobów zarządzania alertami jest użycie tagów. Możliwość tagowania dla Ochrona usługi Office 365 w usłudze Microsoft Defender jest wdrażana przyrostowo i jest obecnie dostępna w wersji zapoznawczej. <br>
> Obecnie zmodyfikowane nazwy tagów są stosowane tylko do alertów utworzonych *po* aktualizacji. Alerty, które zostały wygenerowane przed modyfikacją, nie będą odzwierciedlać zaktualizowanej nazwy tagu. 

Aby zarządzać *zestawem alertów podobnym do określonego alertu*, wybierz pozycję **Wyświetl podobne alerty** w polu **INSIGHT** w sekcji szczegóły podsumowania na stronie alertu.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" alt-text="Zarządzanie alertem w portalu Microsoft 365 Defender":::

W okienku **Zarządzanie alertami** można następnie sklasyfikować wszystkie powiązane alerty w tym samym czasie. Oto przykład.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" alt-text="Zarządzanie powiązanymi alertami w portalu Microsoft 365 Defender":::

Jeśli podobne alerty zostały już sklasyfikowane w przeszłości, możesz zaoszczędzić czas, korzystając z zaleceń Microsoft 365 Defender, aby dowiedzieć się, jak zostały rozwiązane inne alerty. W sekcji szczegóły podsumowania wybierz pozycję **Rekomendacje**.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" alt-text="Przykład wybierania zaleceń dla alertu":::

Karta **Rekomendacje** zawiera akcje następnego kroku i porady dotyczące badania, korygowania i zapobiegania. Oto przykład.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" alt-text="Przykład zaleceń dotyczących alertów":::

## <a name="resolve-an-alert"></a>Rozwiązywanie alertu

Po zakończeniu analizowania alertu i jego rozwiązaniu przejdź do okienka **Zarządzanie alertami** dla alertu lub podobnych alertów i oznacz stan jako **Rozwiązany** , a następnie zaklasyfikuj go jako **wynik prawdziwie dodatni** z typem zagrożenia, działaniem **informacyjnym, oczekiwanym** z typem działania lub **wynikiem fałszywie dodatnim**.

Klasyfikowanie alertów pomaga Microsoft 365 Defender poprawić jego jakość wykrywania.

## <a name="use-power-automate-to-triage-alerts"></a>Klasyfikowanie alertów przy użyciu Power Automate

Zespoły nowoczesnych operacji zabezpieczeń (SecOps) wymagają automatyzacji, aby efektywnie działać. Aby skupić się na wyszukiwaniu i badaniu rzeczywistych zagrożeń, zespoły SecOps używają Power Automate do klasyfikowania listy alertów i eliminowania tych, które nie są zagrożeniami.  

### <a name="criteria-for-resolving-alerts"></a>Kryteria rozwiązywania alertów

- Użytkownik ma włączony komunikat poza biurem

- Użytkownik nie jest oznaczony jako wysokiego ryzyka

Jeśli obie te wartości są prawdziwe, usługa SecOps oznacza alert jako legalną podróż i rozwiązuje ten problem. Powiadomienie jest publikowane w Microsoft Teams po rozwiązaniu alertu.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>Połączenie Power Automate do Microsoft Defender for Cloud Apps

Aby utworzyć automatyzację, musisz mieć token interfejsu API, aby można było nawiązać połączenie Power Automate z Microsoft Defender for Cloud Apps.

1. Kliknij **pozycję Ustawienia**, wybierz pozycję **Rozszerzenia zabezpieczeń**, a następnie kliknij pozycję **Dodaj token** na **karcie Tokeny interfejsu API**.

2. Podaj nazwę tokenu, a następnie kliknij pozycję **Generuj**. Zapisz token, ponieważ będzie on potrzebny później.

### <a name="create-an-automated-flow"></a>Tworzenie zautomatyzowanego przepływu

Aby zapoznać się ze szczegółowym procesem krok po kroku, zobacz wideo [tutaj](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn).

W tym filmie wideo opisano również sposób łączenia usługi Power Automate z usługą Defender dla Chmury Apps.

## <a name="next-steps"></a>Następne kroki

W razie potrzeby w przypadku zdarzeń w procesie kontynuuj [badanie](investigate-incidents.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
- [Badanie zdarzeń](investigate-incidents.md)
