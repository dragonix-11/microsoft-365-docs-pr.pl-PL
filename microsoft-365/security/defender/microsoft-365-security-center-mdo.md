---
title: Ochrona usługi Office 365 w usłudze Microsoft Defender w usłudze Microsoft 365 Defender
description: Zapoznaj się ze zmianami wprowadzonymi w Centrum & zgodności w Microsoft 365 Defender.
keywords: Microsoft 365, Wprowadzenie do Microsoft 365 Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender, MDO, MDE, pojedyncze okienko szyb, nowy portal zabezpieczeń, nowy portal zabezpieczeń Defender
ms.date: 02/21/2021
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.prod: m365-security
ms.technology: m365d
ms.openlocfilehash: a42805ea9b803818bd538e24a3fa626a00dac348
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499842"
---
# <a name="microsoft-defender-for-office-365-in-microsoft-365-defender"></a>Ochrona usługi Office 365 w usłudze Microsoft Defender w usłudze Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365)

## <a name="quick-reference"></a>Podręczny przewodnik

W poniższej tabeli wymieniono zmiany w nawigacji między Centrum zabezpieczeń i & zgodności a Microsoft 365 Defender.

<br>

****

|[Centrum & zabezpieczeń](https://protection.office.com)|[Microsoft 365 Defender](https://security.microsoft.com)|[Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)|[Exchange administracyjne](https://admin.exchange.microsoft.com)|
|---|---|---|---|
|Alerty|<ul><li>[Zasady alertów](https://security.microsoft.com/alertpolicies)</li><li>[Alerty o & zdarzeniach](https://security.microsoft.com/alerts)</li></ul>|[Strona Alerty](https://compliance.microsoft.com/homepage)||
|Klasyfikacja||Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|Ochrona przed utratą danych||Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|Zarządzanie rekordami||Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|Zarządzanie informacjami||Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|Zarządzanie zagrożeniami|[Współpraca za & e-mail](https://security.microsoft.com/homepage)|||
|Uprawnienia|[Uprawnienia & ról](https://security.microsoft.com/emailandcollabpermissions)|Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|Przepływ poczty e-mail|||Zobacz [Exchange administracyjne](https://admin.exchange.microsoft.com/#/)|
|Prywatność danych||Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|Wyszukiwanie|[Inspekcja](https://security.microsoft.com/auditlogsearch?viewid=Async%20Search)|Wyszukiwanie (wyszukiwanie zawartości)||
|Raporty|[Raport](https://security.microsoft.com/emailandcollabreport)|||
|Zapewnianie ochrony usługi||Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|Nadzór||Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|zbierania elektronicznych materiałów dowodowych||Zobacz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/homepage)||
|||||

[Microsoft 365 Defender](./microsoft-365-defender.md) łączy <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> funkcje zabezpieczeń istniejących portali zabezpieczeń firmy Microsoft, w tym Centrum zabezpieczeń & zgodności. To ulepszone centrum pomaga zespołom zabezpieczeń chronić ich organizację przed zagrożeniami w bardziej efektywny sposób.

Jeśli znasz Centrum zgodności & zabezpieczeń (protection.office.com), w tym artykule opisano niektóre zmiany i ulepszenia w Microsoft 365 Defender.

Dowiedz się więcej o zaletach: [Omówienie funkcji Microsoft 365 Defender](microsoft-365-defender.md)

Jeśli szukasz elementów związanych ze zgodnością, odwiedź witrynę <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365.</a>

## <a name="new-and-improved-capabilities"></a>Nowe i ulepszone funkcje

Pasek nawigacji po lewej stronie (pasek Szybkie uruchamianie) będzie wyglądać znajomo. W tej aplikacji jest jednak kilka nowych i zaktualizowanych elementów Defender dla Chmury.

Ujednolicone rozwiązanie Microsoft 365 Defender umożliwia łączenie sygnałów zagrożeń i określanie pełnego zakresu i wpływu zagrożenia oraz jego wpływu na organizację.

:::image type="content" source="../../media/M365-defender-converge-experience.png" alt-text="Środowisko Microsoft 365 Defender zbieżne" lightbox="../../media/M365-defender-converge-experience.png":::

Ochrona usługi Office 365 w usłudze Defender chroni organizację przed złośliwymi zagrożeniami, które mogą być publikowane przez wiadomości e-mail, linki (adresy URL) i narzędzia do współpracy.

:::image type="content" source="../../media/Defender-for-O365.png" alt-text="Portal Ochrona usługi Office 365 w usłudze Defender użytkowników" lightbox="../../media/Defender-for-O365.png":::

### <a name="incidents-and-alerts"></a>Zdarzenia i alerty

Łączy zarządzanie zdarzeniami i alertami w wiadomościach e-mail, urządzeniach i tożsamościach. Alerty są teraz dostępne w węźle Badanie i zapewniają szerszy widok ataków. Strona alertu udostępnia pełny kontekst dla alertu, łącząc sygnały ataków w celu skonstruowania szczegółowej historii. Wcześniej alerty były specyficzne dla różnych obciążeń pracą. Nowe, ujednolicone środowisko zapewnia teraz spójny widok alertów dla różnych obciążeń. Możesz szybko przeprowadzić triage, zbadać i podjąć skuteczne działania.

- [Dowiedz się więcej o badaniach](incidents-overview.md)
- [Dowiedz się więcej o zarządzaniu alertami](/windows/security/threat-protection/microsoft-defender-atp/review-alerts)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Pasek szybkie uruchamianie alertów i akcji w portalu Microsoft 365 Defender wiadomości" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>Goniące

Aktywne wyszukiwanie zagrożeń, złośliwego oprogramowania i złośliwych działań w punktach końcowych, Office 365 skrzynkach pocztowych i nie tylko przy użyciu [zaawansowanych zapytań wyszukiwania](advanced-hunting-overview.md). Za pomocą tych zaawansowanych zapytań można lokalizować i przeglądać wskaźniki zagrożeń i jednostki zarówno dla znanych, jak i potencjalnych zagrożeń.

[Niestandardowe reguły wykrywania](/windows/security/threat-protection/microsoft-defender-atp/custom-detection-rules) można utworzyć na pomocą zaawansowanych zapytań wyszukiwania, aby aktywnie obserwować zdarzenia, które mogą być chwycone przez naruszenie działań i nieprawidłowo skonfigurowane urządzenia.

Oto przykład [zaawansowanego wyszukiwania](advanced-hunting-example.md) w Ochrona usługi Office 365 w usłudze Microsoft Defender.

### <a name="action-center"></a>Centrum akcji

Centrum akcji pokazuje badania utworzone na podstawie zautomatyzowanych możliwości badania i odpowiedzi. Ten zautomatyzowany, samoobsługowy program Microsoft 365 Defender pomaga zespołom zabezpieczeń, automatycznie odpowiadając na określone zdarzenia.

Dowiedz się więcej o [Centrum akcji](m365d-action-center.md).

#### <a name="threat-analytics"></a>Analiza zagrożeń

Uzyskaj analizę zagrożeń od ekspertów od specjalistów ds. zabezpieczeń firmy Microsoft. Analiza zagrożeń pomaga zespołom zabezpieczeń zwiększyć efektywność w przypadku wyłaniających się zagrożeń. Analiza zagrożeń obejmuje:

- Wykrywanie i środki zaradcze związane z pocztą e-mail Ochrona usługi Office 365 w usłudze Microsoft Defender. Jest to dodatek do danych punktu końcowego, które są już dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender.
- Widok zdarzeń związanych z zagrożeniami.
- Ulepszone środowisko do szybkiego identyfikowania i używania informacji z możliwością działania w raportach.

Do analizy zagrożeń możesz uzyskać dostęp z lewego górnego paska nawigacyjnego w programie Microsoft 365 Defender lub z dedykowanej karty pulpitu nawigacyjnego, która pokazuje najważniejsze zagrożenia dla organizacji.

Dowiedz się więcej na temat śledzenia wyłaniających się zagrożeń i reagowania na [nie za pomocą analizy zagrożeń](./threat-analytics.md).

### <a name="email--collaboration"></a>Współpraca za & e-mail

Śledź i badaj zagrożenia dotyczące poczty e-mail użytkowników, śledź kampanie i nie tylko. Jeśli używasz Centrum zgodności z zabezpieczeniami &, to będzie znane.

:::image type="content" source="../../media/converge-3-email-and-collab-new.png" alt-text="Menu szybkiego uruchamiania wiadomości e-mail & Collab (lub MSDO) w lewym okienku nawigacji w Microsoft 365 Defender nawigacji" lightbox="../../media/converge-3-email-and-collab-new.png":::

#### <a name="email-entity-page"></a>Strona jednostki e-mail

Strona [encji E-mail](../office-365-security/mdo-email-entity-page.md) *ujednolicono* informacje e-mail, które były w przeszłości rozproszone na różnych stronach lub w różnych widokach. Badanie wiadomości e-mail pod celu zbadania zagrożeń i *trendów jest scentralizowane*. Informacje nagłówka i podgląd wiadomości e-mail są dostępne za pośrednictwem tej samej strony poczty e-mail oraz innych przydatnych informacji związanych z pocztą e-mail. Stan detonacji złośliwych plików załączników i adresów URL można też znaleźć na karcie tej samej strony. Strona jednostki poczty e-mail umożliwia zespołom administratorów i operacji zabezpieczeń szybkie zrozumienie zagrożeń e-mail i ich stanu, a następnie szybkie określenie obsługi.

### <a name="access-and-reports"></a>Program Access i raporty

Wyświetlaj raporty, zmieniaj ustawienia i modyfikuj role użytkowników.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Menu Szybkie uruchamianie dla uprawnień Microsoft 365 Defender i raportowania w lewym okienku nawigacji w Microsoft 365 Defender nawigacji" lightbox="../../media/converge-4-access-and-reporting-new.png":::

> [!NOTE]
> DKIM (DomainKeys Identified Mail) zapewnia, że docelowe systemy poczty e-mail zaufają wiadomościom wychodzącym z Twojej domeny niestandardowej.
> W Ochrona usługi Office 365 w usłudze Defender użytkowników możesz teraz zarządzać klawiszami *DKIM* i obracać je za pośrednictwem programu Microsoft 365 Defender: <https://security.microsoft.com/threatpolicy>lub  \>  \>  \> \> przejść do sekcji **DKIM** Reguły zasad zagrożeń & reguły zasad ochrony przed zagrożeniami.
>
> Aby uzyskać więcej informacji, zobacz [Używanie funkcji DKIM do sprawdzania poprawności wychodzących](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email) wiadomości e-mail wysłanych z domeny niestandardowej.

## <a name="whats-changed"></a>Co się zmieniło

Ta tabela zawiera krótkie informacje na temat zarządzania zagrożeniami, w przypadku których między Centrum zabezpieczeń i zgodnością a & Microsoft 365 Defender zgodnością nastąpiła zmiana. Kliknij linki, aby dowiedzieć się więcej o tych obszarach.

<br>

****

|Obszar|Opis zmiany|
|---|---|
|[Badanie](../office-365-security/office-365-air.md#changes-are-coming-soon-in-your-microsoft-365-defender-portal)|Łączy funkcje AIR w programach [Ochrona usługi Office 365 w usłudze Defender](/microsoft-365/security/office-365-security/defender-for-office-365) [i Defender for Endpoint](../defender-endpoint/automated-investigations.md). Dzięki tym aktualizacjom i ulepszeniom Twój zespół operacyjny ds. zabezpieczeń będzie mógł wyświetlać szczegółowe informacje o zautomatyzowanych badaniach i działaniach naprawczych w ramach poczty e-mail, zawartości współpracy, kont użytkowników i urządzeń w jednym miejscu.|
|[Kolejka alertów](../../compliance/alert-policies.md)|Okienko **wysuwu alertów** Widoku w Centrum & zabezpieczeń zawiera teraz linki do Microsoft 365 Defender. Kliknij link **Otwórz stronę alertu** i Microsoft 365 Defender otwierane. Dostęp do strony **Wyświetlanie alertów można** uzyskać, klikając dowolny alert Office 365 w kolejce alertów.|
|[Szkolenie z symeny ataków](../office-365-security/attack-simulation-training-insights.md)|Korzystanie ze szkolenia z użyciem symezyjnej ataków do uruchamiania realistycznych scenariuszy ataków w organizacji. Takie symulowane ataki mogą pomóc w przeszkolić pracowników przed rzeczywistymi atakami, które mają wpływ na organizację. Szkolenie symulacyjne dotyczące ataków obejmuje więcej opcji, rozszerzone raporty i ulepszone przepływy szkoleniowe, które ułatwiają korzystanie z tych symulacyjnych i szkoleniowych scenariuszy ataków i zarządzanie nimi.|
|

Nie ma zmian w tych obszarach:

- [Eksplorator](../office-365-security/threat-explorer.md)
- [Zasady & reguł](../../compliance/alert-policies.md)
- [Kampania](../office-365-security/campaigns.md)
- [Materiały](../office-365-security/admin-submission.md)
- [Przegląd](./m365d-action-center.md)
- [Śledzenie zagrożeń](../office-365-security/threat-trackers.md)

Sprawdź też **sekcję Informacje pokrewne** u dołu tego artykułu.

> [!IMPORTANT]
> Portal <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender łączy</a> funkcje zabezpieczeń w systemach <https://securitycenter.windows.com>, i <https://protection.office.com>. To, co zostanie wyświetlony, będzie jednak zależne od Twojej subskrypcji. Jeśli na przykład masz tylko plan Ochrona usługi Office 365 w usłudze Microsoft Defender 1 lub 2 w ramach subskrypcji autonomicznych, nie zobaczysz funkcji Zabezpieczenia punktów końcowych i Usługi Defender dla usługi Office Plan 1 nie będą widziały elementów takich jak Analiza zagrożeń.

> [!TIP]
> Wszystkie Exchange Online Protection (EOP) zostaną uwzględnione w programie Microsoft 365 Defender, ponieważ EOP jest podstawowym elementem Ochrona usługi Office 365 w usłudze Defender.

## <a name="microsoft-365-defender-home-page"></a>Microsoft 365 Defender strona główna

Na stronie głównej portalu są zawarte ważne informacje podsumowujące dotyczące stanu zabezpieczeń Microsoft 365 sieci.

Korzystając z **przewodnika z przewodnikiem** , możesz skorzystać z krótkiego przewodnika po stronach punktów końcowych lub wiadomości e-mail & współpracy. Pamiętaj, że to, co zostanie tutaj wyświetlony, zależy od tego, czy masz licencję usługi Ochrona usługi Office 365 w usłudze Defender i/lub Defender dla punktu końcowego.

Znajduje się również link do Centrum zabezpieczeń & zgodności w celu porównania. Ostatni link znajduje się na stronie Co **nowego** , która opisuje najnowsze aktualizacje.

## <a name="related-information"></a>Informacje pokrewne

- [Przekierowywanie centrum & zgodności w celu Microsoft 365 Defender](microsoft-365-security-mdo-redirection.md)
- [Centrum akcji](./m365d-action-center.md)
- [Alerty dotyczące & poczty e-mail](../../compliance/alert-policies.md#default-alert-policies)
- [Niestandardowe reguły wykrywania](/microsoft-365/security/defender-endpoint/custom-detection-rules)
- [Tworzenie symulacyjnej próby wyłudzania](../office-365-security/attack-simulation-training.md) informacji [i tworzenie ładu na szkolenia dla osób](../office-365-security/attack-simulation-training-payloads.md)
