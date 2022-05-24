---
title: podręcznik wersji próbnej Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
ms.prod: m365-security
search.appverid:
- MOE150
- MET150
description: podręcznik wersji próbnej rozwiązań Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.openlocfilehash: a1adcf15bd051478e874b990a5e6b12f19d3b0c6
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648354"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>Podręcznik wersji próbnej: Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy:**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Witamy w podręczniku wersji próbnej Ochrona usługi Office 365 w usłudze Microsoft Defender. Ten podręcznik pomoże Ci w maksymalnym użyciu 90-dniowej bezpłatnej wersji próbnej, ucząc Cię, jak chronić organizację za pomocą Ochrona usługi Office 365 w usłudze Defender. Korzystając z zaleceń firmy Microsoft, dowiesz się, jak Ochrona usługi Office 365 w usłudze Defender może pomóc w definiowaniu zasad ochrony, analizie zagrożeń dla organizacji i reagowaniu na ataki.

:::image type="content" source="../../media/mdo-trial-playbook-what-is-mdo.png" alt-text="Graficzna reprezentacja wszystkich składników Ochrona usługi Office 365 w usłudze Microsoft Defender." lightbox="../../media/mdo-trial-playbook-what-is-mdo.png":::

Te akcje są zaleceniami zespołu usługi Microsoft Defender dotyczącymi kluczowych funkcji, które należy wypróbować w 90-dniowej wersji próbnej.

## <a name="step-1-getting-started"></a>Krok 1. Wprowadzenie

### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Rozpoczynanie Ochrona usługi Office 365 w usłudze Microsoft Defender wersji próbnej

Po zainicjowaniu wersji próbnej i zakończeniu procesu konfiguracji wprowadzenie zmian może potrwać do 2 godzin.

Automatycznie skonfigurowaliśmy [wstępnie skonfigurowane zasady zabezpieczeń](preset-security-policies.md) w twoim środowisku. Te zasady reprezentują profil ochrony punktu odniesienia, który jest odpowiedni dla większości użytkowników. Standardowa ochrona obejmuje:

- Sejf Linki, Sejf Załączniki i zasady ochrony przed wyłudzaniem informacji, które są ograniczone do całej dzierżawy lub podzestawu użytkowników, których można było wybrać podczas procesu konfiguracji wersji próbnej.
- ochrona załączników Sejf dla SharePoint, OneDrive i Microsoft Teams.
- ochrona linków Sejf dla obsługiwanych aplikacji Office 365.

Obejrzyj ten film wideo, aby dowiedzieć się więcej: [Ochrona przed złośliwymi linkami za pomocą linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender — YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

### <a name="enable-users-to-report-suspicious-content"></a>Umożliwianie użytkownikom zgłaszania podejrzanych treści

Ochrona usługi Office 365 w usłudze Defender umożliwia użytkownikom zgłaszanie komunikatów do swoich zespołów ds. zabezpieczeń i umożliwia administratorom przesyłanie komunikatów do firmy Microsoft w celu analizy.

- Wdróż [dodatek Komunikat raportu lub dodatek Wyłudzanie informacji o raporcie](enable-the-report-message-add-in.md).
- Ustanawianie przepływu pracy w celu [raportowania wyników fałszywie dodatnich i fałszywie ujemnych](report-false-positives-and-false-negatives.md).
- Użyj [portalu Przesłane](admin-submission.md).

Obejrzyj ten film wideo, aby dowiedzieć się więcej: [Dowiedz się, jak przesyłać wiadomości do analizy za pomocą portalu Przesyłania — YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

### <a name="review-reports-to-understand-the-threat-landscape"></a>Przeglądanie raportów w celu zrozumienia krajobrazu zagrożeń

Skorzystaj z możliwości raportowania w Ochrona usługi Office 365 w usłudze Defender, aby uzyskać więcej szczegółów na temat środowiska.

- Omówienie zagrożeń odebranych w narzędziach do poczty e-mail i współpracy za pomocą [raportu o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
- Zobacz, gdzie zagrożenia są blokowane w [raporcie o stanie przepływu poczty](view-email-security-reports.md#mailflow-status-report).
- [Przejrzyj linki](view-reports-for-mdo.md#url-protection-report) , które zostały wyświetlone przez użytkowników lub zablokowane przez system.

:::image type="content" source="../../media/mdo-trial-playbook-reporting.png" alt-text="Raporty dotyczące współpracy & poczty e-mail w portalu Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-reporting.png":::

## <a name="step-2-intermediate-steps"></a>Krok 2. Kroki pośrednie

### <a name="prioritize-focus-on-your-most-targeted-users"></a>Określanie priorytetów na najbardziej docelowych użytkownikach

Chroń najbardziej docelowych i najbardziej widocznych użytkowników za pomocą usługi Priority Account Protection w Ochrona usługi Office 365 w usłudze Defender, co ułatwia określenie priorytetów przepływu pracy w celu zapewnienia bezpieczeństwa tych użytkowników.

- Zidentyfikuj najbardziej docelowych lub najbardziej widocznych użytkowników.
- [Otaguj tych użytkowników](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) jako konta priorytetowe.
- Śledzenie zagrożeń dla konta priorytetowego w portalu.

Obejrzyj ten film wideo, aby dowiedzieć się więcej: [Ochrona kont priorytetowych w Ochrona usługi Office 365 w usłudze Microsoft Defender — YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

:::image type="content" source="../../media/mdo-trial-playbook-alerts.png" alt-text="Alerty w portalu Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-alerts.png":::

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>Unikaj kosztownych naruszeń, zapobiegając naruszeniom bezpieczeństwa użytkowników

Otrzymywanie alertów o potencjalnych naruszeniach zabezpieczeń i automatyczne ograniczanie wpływu tych zagrożeń, aby zapobiec uzyskaniu przez osoby atakujące głębszego dostępu do środowiska.

- Przejrzyj [alerty użytkowników, których zabezpieczenia zostały naruszone](address-compromised-users-quickly.md#compromised-user-alerts).
- [Badanie i reagowanie na](address-compromised-users-quickly.md) naruszonym użytkownikom.

:::image type="content" source="../../media/mdo-trial-playbook-investigation.png" alt-text="Badanie użytkowników, którzy naruszyli bezpieczeństwo." lightbox="../../media/mdo-trial-playbook-investigation.png":::

Obejrzyj ten film wideo, aby dowiedzieć się więcej: [Wykrywanie naruszeń zabezpieczeń i reagowanie na nie w Ochrona usługi Office 365 w usłudze Microsoft Defender — YouTube](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

### <a name="use-threat-explorer-to-investigate-malicious-email"></a>Badanie złośliwych wiadomości e-mail za pomocą Eksploratora zagrożeń

Ochrona usługi Office 365 w usłudze Defender umożliwia badanie działań, które narażają osoby w organizacji na niebezpieczeństwo, oraz podjęcie działań w celu ochrony organizacji. Można to zrobić za pomocą [Eksploratora zagrożeń](threat-explorer.md).

- [Znajdź dostarczoną podejrzaną wiadomość e-mail](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered): znajdź i usuń wiadomości, zidentyfikuj adres IP złośliwego nadawcy wiadomości e-mail lub rozpocznij zdarzenie w celu dalszego zbadania.
- [Sprawdź akcję dostarczania i lokalizację](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): to sprawdzenie informuje o lokalizacji wiadomości e-mail z problemami.
- [Wyświetl oś czasu wiadomości e-mail](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): po prostu wyszukaj dla swojego zespołu ds. operacji zabezpieczeń.

### <a name="see-campaigns-targeting-your-organization"></a>Wyświetlanie kampanii skierowanych do organizacji

Zobacz szerszy obraz widoków kampanii w Ochrona usługi Office 365 w usłudze Defender, co daje wgląd w kampanie ataków wymierzone w organizację i ich wpływ na użytkowników.

- [Identyfikowanie kampanii](campaigns.md#what-is-a-campaign) skierowanych do użytkowników.
- [Wizualizowanie zakresu](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) ataku.
- [Śledzenie interakcji użytkownika](campaigns.md#campaign-details) z tymi komunikatami.

  :::image type="content" source="../../media/mdo-trial-playbook-campaign-details.png" alt-text="Szczegóły kampanii w portalu Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-campaign-details.png":::

Obejrzyj ten film wideo, aby dowiedzieć się więcej: [Wyświetlenia kampanii w Ochrona usługi Office 365 w usłudze Microsoft Defender — YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

### <a name="use-automation-to-remediate-risks"></a>Korygowanie ryzyka przy użyciu automatyzacji

Efektywne reagowanie przy użyciu zautomatyzowanego badania i reagowania (AIR) do przeglądania, określania priorytetów i reagowania na zagrożenia.

- [Dowiedz się więcej](automated-investigation-response-office.md) o podręcznikach badania.
- [Wyświetl szczegóły i wyniki](email-analysis-investigations.md) badania.
- Eliminowanie zagrożeń przez [zatwierdzenie akcji korygowania](air-remediation-actions.md).

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="Wyniki badania." lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

## <a name="step-3-advanced-content"></a>Krok 3. Zawartość zaawansowana

### <a name="dive-deep-into-data-with-query-based-hunting"></a>Szczegółowe informacje o danych z wyszukiwaniem zagrożeń opartym na zapytaniach

Użyj zaawansowanego wyszukiwania zagrożeń do pisania niestandardowych reguł wykrywania, proaktywnego sprawdzania zdarzeń w środowisku i lokalizowania wskaźników zagrożeń. Eksplorowanie danych pierwotnych w środowisku.

- [Kompilowanie niestandardowych reguł wykrywania](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- [Uzyskiwanie dostępu do udostępnionych zapytań utworzonych](../defender/advanced-hunting-shared-queries.md) przez inne osoby.

Obejrzyj ten film wideo, aby dowiedzieć się więcej: [Wyszukiwanie zagrożeń przy użyciu Microsoft 365 Defender — YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>Szkolenie użytkowników do wykrywania zagrożeń przez symulowanie ataków

Wyposaż użytkowników w odpowiednią wiedzę, aby identyfikować zagrożenia i zgłaszać podejrzane komunikaty, korzystając z trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Defender.

- [Symulowanie realistycznych zagrożeń](attack-simulation-training.md) w celu zidentyfikowania narażonych użytkowników.
- [Przypisywanie szkoleń](attack-simulation-training.md#assign-training) do użytkowników na podstawie wyników symulacji.
- [Śledź postęp](attack-simulation-training-insights.md) organizacji w symulacjach i ukończeniu szkoleń.

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="Szczegółowe informacje na temat symulacji ataków w portalu Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="additional-resources"></a>Dodatkowe materiały

- **Przewodnik interaktywny**: Nie znasz Ochrona usługi Office 365 w usłudze Defender? Zapoznaj się z [interaktywnym przewodnikiem](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) , aby dowiedzieć się, jak rozpocząć pracę.
- **Dokumentacja firmy Microsoft**: uzyskaj szczegółowe informacje o tym, jak działa Ochrona usługi Office 365 w usłudze Defender i jak najlepiej zaimplementować ją w organizacji. Odwiedź stronę [Docs](overview.md).
- **Co zawiera**: Aby uzyskać pełną listę funkcji zabezpieczeń Office 365 poczty e-mail wymienionych w warstwie produktu, zobacz [Macierz funkcji](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **Dlaczego Ochrona usługi Office 365 w usłudze Defender**: w [arkuszu danych Ochrona usługi Office 365 w usłudze Defender](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) przedstawiono 10 najważniejszych powodów, dla których klienci wybierają firmę Microsoft.
