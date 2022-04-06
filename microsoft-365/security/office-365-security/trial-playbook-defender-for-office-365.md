---
title: Podręcznik wersji próbnej Office 365 Microsoft Defender
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
description: Podręcznik wersji próbnej programu Microsoft Defender Office 365 rozwiązania.
ms.openlocfilehash: b8a0fedd01a3769f2ccf8952bd9e7bce0974a2f0
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683214"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>Podręcznik wersji próbnej: Program Microsoft Defender dla Office 365

Witamy w podręczniku dla programu Microsoft Defender Office 365 wersji próbnej. Ten podręcznik pomoże Ci w jak najlepiej korzystać z 90-dniowej bezpłatnej wersji próbnej, ucząc się, jak chronić organizację za pomocą programu Defender dla Office 365. Korzystając z rekomendacji firmy Microsoft, dowiesz się, jak usługa Defender for Office 365 może ułatwić definiowanie zasad ochrony, analizowanie zagrożeń dla organizacji i reagowanie na ataki.

![Graficzna reprezentacja wszystkich składników programu Microsoft Defender dla systemu Office 365.](../../media/mdo-trial-playbook-what-is-mdo.png)

Te działania są zaleceniami od zespołu usługi Microsoft Defender w sprawie kluczowych funkcji do wypróbowania w 90-dniowej wersji próbnej.

## <a name="step-1-getting-started"></a>Krok 1. Wprowadzenie

### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Uruchom program Microsoft Defender dla Office 365 próbnej

Po zainicjowaniu wersji próbnej i ukończeniu procesu konfiguracji może upłynieć do 2 godzin, aż zmiany zajdą w życie.

Wstępnie skonfigurowane zasady zabezpieczeń w [](preset-security-policies.md) Twoim środowisku zostały automatycznie skonfigurowane. Te zasady reprezentują podstawowy profil ochrony, który jest odpowiedni dla większości użytkowników. Standardowa ochrona obejmuje:

- Sejf linki, Sejf załączniki i zasady ochrony przed wyłudzaniem informacji, które są zakresem całej dzierżawy lub podzbioru użytkowników wybranego podczas procesu konfiguracji wersji próbnej.
- Ochrona przed SharePoint, OneDrive, Office i Microsoft Teams.

Obejrzyj ten klip wideo, aby dowiedzieć się więcej: Ochrona przed złośliwymi linkami za pomocą linków Sejf w programie [Microsoft Defender dla Office 365 — YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

### <a name="enable-users-to-report-suspicious-content"></a>Umożliwianie użytkownikom zgłaszania podejrzanej zawartości

Usługa Defender for Office 365 umożliwia użytkownikom zgłaszanie wiadomości do ich zespołów zabezpieczeń i umożliwia administratorom przesyłanie wiadomości do firmy Microsoft w celu analizy.

- [Wdymuj dodatek Wiadomość raportu lub dodatek Wyłudzanie informacji raportu](enable-the-report-message-add-in.md).
- Ustanawianie przepływu pracy w [celu zgłaszania wyników fałszywie dodatnich i ujemnych](report-false-positives-and-false-negatives.md).
- Korzystanie z [portalu Przesyłanie.](admin-submission.md)

Obejrzyj ten klip wideo, aby dowiedzieć się więcej: Dowiedz się, jak za pomocą portalu Przesyłanie przesyłać wiadomości do analizy [— YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

### <a name="review-reports-to-understand-the-threat-landscape"></a>Przeglądanie raportów w celu zrozumienia zagrożeń

Skorzystaj z funkcji raportowania w programie Defender Office 365, aby uzyskać więcej szczegółowych informacji o środowisku.

- Opis zagrożeń otrzymanych w wiadomości e-mail i narzędziach do współpracy dzięki [raportowi o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
- Zobacz, gdzie są blokowane zagrożenia za pomocą [raportu o stanie przepływu poczty](view-email-security-reports.md#mailflow-status-report).
- [Przejrzyj linki](view-reports-for-mdo.md#url-protection-report) , które były przeglądane przez użytkowników lub blokowane przez system.

![Wyślij & e-mail do raportów o współpracy w Microsoft 365 Defender wiadomościach e-mail.](../../media/mdo-trial-playbook-reporting.png)

## <a name="step-2-intermediate-steps"></a>Krok 2. Kroki pośrednie

### <a name="prioritize-focus-on-your-most-targeted-users"></a>Ustawianie priorytetu na użytkownikach, do których jest najczęściej kierowana

Chroń najbardziej docelowych i najbardziej widocznych użytkowników za pomocą usługi Priority Account Protection w programie Defender Office 365, który ułatwia priorytetyzowanie przepływów pracy w celu zapewnienia bezpieczeństwa tym użytkownikom.

- Identyfikowanie najbardziej docelowych lub najbardziej widocznych użytkowników.
- [Oznacz tych użytkowników jako](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) konta priorytetowe.
- Monitoruj zagrożenia, dla których mają być najważniejsze konta w portalu.

Obejrzyj ten klip wideo, aby dowiedzieć się więcej: Ochrona kont priorytetowych w [programie Microsoft Defender dla komputerów Office 365 — YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

![Alerty w Microsoft 365 Defender wiadomości.](../../media/mdo-trial-playbook-alerts.png)

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>Unikanie kosztownych naruszeń przez zapobieganie naruszeniu zabezpieczeń użytkowników

Otrzymuj alerty o potencjalnym złamaniu zabezpieczeń i automatycznie ograniczaj wpływ tych zagrożeń, aby uniemożliwić atakującym uzyskiwanie dostępu do Twojego środowiska.

- Przejrzyj [naruszone alerty użytkowników](address-compromised-users-quickly.md#compromised-user-alerts).
- [Badanie i odpowiadanie](address-compromised-users-quickly.md) na naruszonych użytkowników.

![Badanie naruszonych użytkowników.](../../media/mdo-trial-playbook-investigation.png)

Obejrzyj ten klip wideo, aby dowiedzieć się więcej: Wykrywanie naruszenia bezpieczeństwa w programie [Microsoft Defender dla Office 365 — YouTube](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

### <a name="use-threat-explorer-to-investigate-malicious-email"></a>Badanie złośliwych wiadomości e-mail za pomocą Eksploratora zagrożeń

Program Defender for Office 365 umożliwia badanie działań, które nałoży na osoby w organizacji ryzyko i podejmie działania w celu ochrony organizacji. Możesz to zrobić przy użyciu [Eksploratora zagrożeń lub (wykrywanie w czasie rzeczywistym).](threat-explorer.md)

- [Znajdowanie podejrzanych dostarczonych wiadomości](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered) e-mail: Znajdowanie i usuwanie wiadomości, identyfikowanie adresu IP złośliwego nadawcy wiadomości e-mail lub rozpoczynanie zdarzenia w celu dalszego badania.
- [Sprawdź akcję i lokalizację](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location) dostarczenia: To sprawdzanie pozwala sprawdzić lokalizację problemowych wiadomości e-mail.
- [Wyświetl oś czasu wiadomości e-mail](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): Po prostu poluj na służby bezpieczeństwa.

### <a name="see-campaigns-targeting-your-organization"></a>Zobacz kampanie ukierunkowane na organizację

Zobacz większy obraz dzięki widokom kampanii w programie Defender for Office 365, który zawiera widok kampanii w ramach ataków przeznaczonych na Twoją organizację oraz ich wpływ na Twoich użytkowników.

- [Identyfikowanie kampanii kampanii](campaigns.md#what-is-a-campaign) skierowanej do użytkowników.
- [Wizualizowanie](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) zakresu ataków.
- [Śledź interakcje użytkowników](campaigns.md#campaign-details) z tymi wiadomościami.

![Szczegóły kampanii w Microsoft 365 Defender portalu internetowym.](../../media/mdo-trial-playbook-campaign-details.png)

Obejrzyj ten klip wideo, aby dowiedzieć się więcej: Widoki kampanii w [programie Microsoft Defender dla Office 365 — YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

### <a name="use-automation-to-remediate-risks"></a>Rozwiązywanie problemów za pomocą automatyzacji

Efektywne reagowanie przy użyciu funkcji automatycznego badania i odpowiedzi (AIR) w celu przeglądania zagrożeń, określania priorytetów i reagowania na nie.

- [Dowiedz się więcej](automated-investigation-response-office.md) o podręcznikach do nauki.
- [Wyświetlanie szczegółów i wyników](email-analysis-investigations.md) badania.
- Wyeliminuj [zagrożenia, akceptując działania naprawcze](air-remediation-actions.md).

![Badanie wyników.](../../media/mdo-trial-playbook-investigation-results.png)

## <a name="step-3-advanced-content"></a>Krok 3. Zawartość zaawansowana

### <a name="dive-deep-into-data-with-query-based-hunting"></a>Zanurz się w dane za pomocą wyszukiwania opartego na zapytaniach

Korzystaj z zaawansowanego wyszukiwania, aby tworzyć niestandardowe reguły wykrywania, aktywnie sprawdzać zdarzenia w środowisku i znajdować wskaźniki zagrożeń. Eksplorowanie nieprzetworzonych danych w środowisku.

- [Tworzenie reguł wykrywania niestandardowego](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- [Uzyskiwanie dostępu do zapytań](../defender/advanced-hunting-shared-queries.md) udostępnionych utworzonych przez inne osoby.

Obejrzyj ten klip wideo, aby dowiedzieć się więcej: [Schłoń w Microsoft 365 Defender - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>Szkolenie użytkowników w celu dostrzegowania zagrożeń przez symulowanie ataków

Zapewnij użytkownikom odpowiednią wiedzę w celu identyfikowania zagrożeń i zgłaszania podejrzanych wiadomości za pomocą szkolenia symezyjną ataków w programie Defender for Office 365.

- [Symulowanie realistycznych](attack-simulation-training.md) zagrożeń w celu zidentyfikowania użytkowników, którzy mogą być podatni na zagrożenia.
- [Przypisywanie szkoleń](attack-simulation-training.md#assign-training) użytkownikom na podstawie wyników symulacyjnych.
- [Śledzenie postępu](attack-simulation-training-insights.md) organizacji w czasie symulacyjnej i ukończonej szkoleń.

![Szczegółowe informacje szkoleniowe dotyczące symeny ataków w portalu Microsoft 365 Defender danych.](../../media/mdo-trial-playbook-attack-simulation-training-results.png)

## <a name="additional-resources"></a>Dodatkowe materiały

- **Interakcyjny przewodnik**: Nie rozznajomiasz się z programem Defender dla Office 365? Przejrzyj [interakcyjny przewodnik,](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) aby dowiedzieć się, jak rozpocząć pracę.
- **Dokumenty firmy Microsoft**: Uzyskaj szczegółowe informacje o tym, jak działa Office 365 Defender for Office 365 i jak najlepiej wdrożyć go dla swojej organizacji. Odwiedź [witrynę Dokumenty](overview.md).
- **Dostępne funkcje**: Aby uzyskać pełną listę funkcji zabezpieczeń poczty e Office 365 e-mail wymienionych według warstwy produktu, zobacz [Macierz funkcji](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **Dlaczego usługa Defender dla Office 365**: Usługa [Defender for Office 365 Datasheet](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) pokazuje 10 najlepszych powodów, dla których klienci wybierają firmę Microsoft.
