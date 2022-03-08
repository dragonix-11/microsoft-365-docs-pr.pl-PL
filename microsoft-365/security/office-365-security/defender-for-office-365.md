---
title: Program Microsoft Defender dla Office 365 — CSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.assetid: e100fe7c-f2a1-4b7d-9e08-622330b83653
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- intro-overview
description: Usługa Microsoft Defender dla Office 365 obejmuje załączniki Sejf, linki Sejf, zaawansowane narzędzia do ochrony przed wyłudzaniem informacji, narzędzia do raportowania i funkcje analizy zagrożeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f78194541db8221aad1243966ddee6b6dc071d7d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317055"
---
# <a name="microsoft-defender-for-office-365"></a>Usługa Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych korzystających z programu [Microsoft Defender dla Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Jeśli korzystasz z usługi Outlook.com, Microsoft 365 Family lub Microsoft 365 Personal i szukasz informacji na temat linków programu Sejf lub załączników programu Sejf w programie Outlook, zobacz Zaawansowane zabezpieczenia usługi [Outlook.com dla Microsoft 365 subskrybenci](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Program Microsoft Defender for Office 365 chroni organizację przed złośliwymi zagrożeniami, które mogą być ze strony wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy. Program Defender for Office 365 oferuje:

- **[Zasady ochrony przed zagrożeniami](#configure-microsoft-defender-for-office-365-policies)**: Zdefiniuj zasady ochrony przed zagrożeniami, aby ustawić odpowiedni poziom ochrony dla organizacji.

- **[Raporty](#view-microsoft-defender-for-office-365-reports)**: Wyświetlaj raporty w czasie rzeczywistym, aby monitorować program Defender Office 365 wydajności w organizacji.

- **[Możliwości analizy zagrożeń i reagowania](#use-threat-investigation-and-response-capabilities)** na nie: Używaj narzędzi wiodących do badania, zrozumienia, symulowania i zapobiegania zagrożeniam.

- **[Funkcje automatycznego badania i reagowania](office-365-air.md)**: Oszczędzaj czas i wysiłku podczas badań i ograniczania zagrożeń.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>Interakcyjny przewodnik po programie Microsoft Defender dla Office 365

W tym interakcyjny przewodniku dowiesz się, jak chronić organizację za pomocą programu Microsoft Defender dla Office 365. Zobaczysz, jak może pomóc w definiowaniu Office 365 ochrony, analizowaniu zagrożeń dla organizacji i reagowaniu na ataki.

[Zapoznaj się z interakcyjny przewodnik](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>Wprowadzenie

Jeśli jesteś nowym użytkownikem programu Microsoft Defender dla usługi Office 365 lub uczysz się jak *najlepiej, możesz* skorzystać z poniesienia konfiguracji początkowej usługi Defender dla programu Office 365 na fragmenty, zbadać i wyświetlać raporty przy użyciu tego artykułu jako odwołania. Oto logiczne wczesne fragmenty konfiguracji:

- Skonfiguruj wszystko, co *ma w nazwie "anti*".
  - ochrona przed złośliwym oprogramowaniem
  - ochrona przed wyłudzaniem informacji
  - ochrona przed spamem
- Skonfiguruj wszystko tak, aby *wszystko w nazwie* było "bezpieczne".
  - Bezpieczne linki
  - Sejf załączników
- Obrona obciążeń pracą (np. SharePoint online, OneDrive i Teams)
- Ochrona za pomocą automatycznego przeczyszczania o zerowej godzinie (ZAP).

Aby uczyć się przez ten sposób, [kliknij ten link](protect-against-threats.md).

> [!NOTE]
> Program Microsoft Defender dla Office 365 jest dostępny w dwóch różnych typach planów. Możesz sprawdzić, czy masz **plan 1** , jeśli masz wykrywanie w czasie rzeczywistym, a plan **2**, jeśli masz Eksploratora zagrożeń. Plan, który masz wpływ na narzędzia, które zobaczysz, więc masz pewność, że wiesz o planie w momencie jego nauki.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender dla Office 365 Plan 1 i Plan 2

W poniższej tabeli podsumowano dane zawarte w poszczególnych planach.

****

|Defender dla Office 365 Plan 1|Defender for Office 365 Plan 2|
|---|---|
|Funkcje konfiguracji, ochrony i wykrywania: <ul><li>[Sejf załączników](safe-attachments.md)</li><li>[Bezpieczne linki](safe-links.md)</li><li>[Sejf załączników do SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Ochrona przed wyłudzaniem informacji w programie Defender dla Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Wykrywanie w czasie rzeczywistym](threat-explorer.md)</li></ul>|Funkcje usługi Defender Office 365 Plan 1 <p> --- plus --- <p> Funkcje automatyzacji, badań, rozwiązywania problemów i edukacji: <ul><li>[Śledzenie zagrożeń](threat-trackers.md)</li><li>[Eksplorator zagrożeń](threat-explorer.md)</li><li>[Zautomatyzowane badanie i odpowiedź](office-365-air.md)</li><li>[Szkolenie z symeny ataków](attack-simulation-training.md)</li><li>[Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania w Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Badanie zdarzeń w Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Badanie alertów w programie Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|


- Usługa Microsoft Defender dla Office 365 Plan 2 jest zawarta Office 365 E5, Office 365 A5 i Microsoft 365 E5.

- Program Microsoft Defender dla Office 365 Plan 1 jest dołączony do Microsoft 365 Business Premium.

- Program Microsoft Defender dla Office 365 Plan 1 i Defender dla systemu Office 365 Plan 2 są dostępne jako dodatek dla niektórych subskrypcji. Aby dowiedzieć się więcej, oto kolejny link Dostępność funkcji w programie [Microsoft Defender dla Office 365 planów](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funkcja [Sejf dokumenty](safe-docs.md) jest dostępna tylko dla użytkowników z licencjami usługi Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5 (nieujętą do programu Microsoft Defender dla Office 365 planów).

- Jeśli Twoja bieżąca subskrypcja nie zawiera programu Microsoft Defender dla usługi Office 365 i [chcesz, skontaktuj](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) się ze sprzedażą, aby rozpocząć okres próbny i dowiedz się, jak usługa Microsoft Defender dla usługi Office 365 może działać w Twojej organizacji.

- Program Microsoft Defender dla Office 365 P2 ma dostęp do integracji usługi **Microsoft 365 Defender**, co umożliwia efektywne wykrywanie, przeglądanie i reagowanie na zdarzenia i alerty oraz reagowanie na nie.

## <a name="configure-microsoft-defender-for-office-365-policies"></a>Konfigurowanie programu Microsoft Defender na Office 365 danych

Za pomocą usługi Microsoft Defender Office 365 zespół zabezpieczeń Twojej organizacji może skonfigurować ochronę, definiując zasady w portalu  \>  \> <https://security.microsoft.com> Microsoft 365 Defender pod adresem Zasady współpracy poczty e-mail & i zasady ochrony przed zagrożeniami **&.** Możesz też przejść bezpośrednio do strony **Zasady zagrożeń** , używając narzędzia <https://security.microsoft.com/threatpolicy>.

Dowiedz się więcej, oglądając [ten klip wideo](https://www.youtube.com/watch?v=vivvTmWJ_3c).

> [!TIP]
> Aby uzyskać szybką listę zasad do zdefiniowania, zobacz [Ochrona przed zagrożeniami](protect-against-threats.md).

## <a name="defender-for-office-365-policies"></a>Zasady dotyczące Office 365 Defender

Zasady zdefiniowane dla organizacji określają zachowanie i poziom ochrony dla wstępnie zdefiniowanych zagrożeń. Opcje zasad są bardzo elastyczne. Na przykład zespół zabezpieczeń organizacji może ustawić poziom ochrony przed zagrożeniami dla użytkownika, organizacji, adresata i domeny. Należy regularnie przeglądać zasady, ponieważ codziennie pojawiają się nowe zagrożenia i wyzwania.

- **[Sejf załączników](safe-attachments.md)**: Zapewnia ochronę przez zero dni w celu zabezpieczenia systemu wiadomości, sprawdzając załączniki wiadomości e-mail w celu ich zabezpieczenia w przypadku złośliwej zawartości. Kieruje wszystkie wiadomości i załączniki, które nie mają podpisu wirusa/złośliwego oprogramowania, do specjalnego środowiska, a następnie wykrywa złośliwe intencje za pomocą technik uczenia maszynowego i analizy. Jeśli nie zostanie znalezione podejrzane działanie, wiadomość jest przesyłana dalej do skrzynki pocztowej. Aby dowiedzieć się więcej, [zobacz Konfigurowanie Sejf załączników](set-up-safe-attachments-policies.md).

- **[Sejf linków](safe-links.md)**. Zapewnia weryfikację adresów URL po kliknięciu, na przykład w wiadomościach e-mail i Office plikach. Ochrona jest na bieżąco i obowiązuje w całym środowisku obsługi wiadomości Office wiadomości. Linki są skanowane przy każdym kliknięciu: bezpieczne linki pozostają dostępne, a złośliwe linki są dynamicznie blokowane. Aby dowiedzieć się więcej, [zobacz Konfigurowanie Sejf linków](set-up-safe-links-policies.md).

- Sejf załączniki do SharePoint **[, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)**: Chroni organizację, gdy użytkownicy współpracują i udostępniają pliki, przez identyfikowanie i blokowanie złośliwych plików w witrynach zespołowych i bibliotekach dokumentów. Aby dowiedzieć się więcej, zobacz [Włączanie programu Defender Office 365 dla SharePoint, OneDrive i Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

- **[Ochrona przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)** w programie Defender Office 365: Wykrywa próby personifikacji użytkowników oraz domen wewnętrznych lub niestandardowych. Stosowane są modele uczenia maszynowego i zaawansowane algorytmy wykrywania personifikacji, aby uniknąć ataków wyłudzających informacje. Aby dowiedzieć się więcej, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>Wyświetlanie raportów programu Microsoft Defender Office 365 aplikacji

Usługa Microsoft Defender for Office 365 zawiera [raporty służące](view-reports-for-mdo.md) do monitorowania usługi Defender pod Office 365. Dostęp do raportów można uzyskać w portalu Microsoft 365 Defender  \>  \> <https://security.microsoft.com> pod adresem Raporty dotyczące poczty e-mail & raportów dotyczących współpracy poczty e-mail **& współpracy**. Możesz też przejść bezpośrednio do strony Raporty e-mail **i dotyczące współpracy za** pomocą usługi <https://security.microsoft.com/securityreports>.

Raporty są aktualizowane w czasie rzeczywistym, dzięki użyciu najnowszych informacji. Te raporty zawierają również zalecenia i ostrzegają o bliskich zagrożeniach. Wstępnie zdefiniowane raporty są następujące:

- [Eksplorator zagrożeń (lub wykrywanie w czasie rzeczywistym)](threat-explorer.md)
- [Raport o stanie ochrony przed zagrożeniami](view-reports-for-mdo.md#threat-protection-status-report)
- ... i kilka innych.

## <a name="use-threat-investigation-and-response-capabilities"></a>Używanie funkcji analizy zagrożeń i reakcji

Usługa Microsoft Defender for Office 365 Plan 2 zawiera najlepsze w swojej klasie narzędzia do badania zagrożeń [](office-365-ti.md) i reagowania, które umożliwiają zespołowi zabezpieczeń Twojej organizacji przewidywanie, zrozumienie i zapobieganie złośliwym atakom.

- **[Śledzenie zagrożeń zapewnia](threat-trackers.md)** najnowszą analizę kwestii związanych z istotnej aktywnością. Możesz na przykład wyświetlić informacje o najnowszym złośliwym oprogramowaniu i podjąć działania zaradcze, zanim stanie się ono rzeczywistym zagrożeniem dla organizacji. Dostępne są między innymi [następujące monitory](threat-trackers.md#noteworthy-trackers) warte [uwagi, śledzenie](threat-trackers.md#trending-trackers) trendów, [śledzone](threat-trackers.md#tracked-queries) zapytania i [zapisane zapytania](threat-trackers.md#saved-queries).

- **[Eksplorator zagrożeń (](threat-explorer.md)** czyli wykrywanie w czasie rzeczywistym) (nazywany również Eksploratorem) to raport w czasie rzeczywistym, który umożliwia identyfikowanie i analizowanie najnowszych zagrożeń. Eksploratora można skonfigurować do pokazywania danych okresów niestandardowych.

- **[Szkolenie symulacyjne dotyczące](attack-simulation-training.md)** ataków pozwala na uruchamianie realistycznych scenariuszy ataków w twojej organizacji w celu identyfikowania luk w zabezpieczeniach. Dostępne są przykłady bieżących typów ataków, takich jak ataki poświadczeń wyłudzających informacje oraz ataki haseł na hasłach.

## <a name="save-time-with-automated-investigation-and-response"></a>Oszczędzanie czasu dzięki zautomatyzowanemu śledztwu i odpowiedzi

(**NOWOŚĆ!**) Gdy badasz potencjalne cyberataki, czas jest istotą. Im szybciej będziesz identyfikować zagrożenia i je zminimalizować, tym lepsza będzie Twoja organizacja. [Funkcje automatycznego badania](office-365-air.md) i odpowiedzi (AIR) obejmują zestaw podręczników zabezpieczeń, które mogą być uruchamiane automatycznie, na przykład po wyzwoleniu alertu, lub ręcznie, na przykład z widoku w Eksploratorze. Program AIR może zaoszczędzić czas i nakład pracy zespołowej związanej z zabezpieczeniami, aby skutecznie i skutecznie chronić zagrożenia. Aby dowiedzieć się więcej, zobacz [AIR in Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>Uprawnienia wymagane do korzystania z programu Microsoft Defender Office 365 funkcji

Aby uzyskać dostęp do usługi Microsoft Defender Office 365 funkcji, musisz mieć przypisaną odpowiednią rolę. W poniższej tabeli podano kilka przykładów:

<br>

****

|Rola lub grupa ról|Zasoby, aby dowiedzieć się więcej|
|---|---|
|administrator globalny (Zarządzanie organizacją)|Tę rolę możesz przypisać w Azure Active Directory lub w Microsoft 365 Defender portalu. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).|
|Administrator zabezpieczeń|Tę rolę możesz przypisać w Azure Active Directory lub w Microsoft 365 Defender portalu. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).|
|Zarządzanie organizacją w Exchange Online|[Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo) <p> [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)|
|Wyszukiwanie i przeczyszczanie|Ta rola jest dostępna tylko w portalu Microsoft 365 Defender lub portalu Centrum zgodności platformy Microsoft 365. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender oraz](permissions-microsoft-365-security-center.md) [Uprawnienia w Centrum zgodności platformy Microsoft 365](../../compliance/microsoft-365-compliance-center-permissions.md).|
|||

## <a name="get-microsoft-defender-for-office-365"></a>Uzyskaj program Microsoft Defender dla Office 365

Usługa Microsoft Defender for Office 365 jest zawarta w niektórych subskrypcjach, takich jak Microsoft 365 E5, Office 365 E5, Office 365 A5 i Microsoft 365 Business Premium. Jeśli Twoja subskrypcja nie zawiera programu Defender for Office 365, możesz kupić usługę Defender dla usługi Office 365 Plan 1 lub Defender dla usługi Office 365 Plan 2 jako dodatek do niektórych subskrypcji. Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Usługa Microsoft Defender Office 365 dostępność](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) dla listy subskrypcji, które zawierają usługę Defender dla Office 365 planów.

- [Dostępność funkcji w programie Microsoft Defender Office 365 dla](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) planów planów usługi Microsoft Defender na listę funkcji zawartych w planach 1 i 2.

- [Uzyskaj odpowiedni program Microsoft Defender dla Office 365](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content), aby porównać plany i kupić usługę Defender dla Office 365.

- [Rozpocznij bezpłatny okres próbny](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>Nowe funkcje programu Microsoft Defender dla Office 365

Nowe funkcje są stale dodawane do programu Microsoft Defender Office 365 stale. Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Microsoft 365 zawiera](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365) listę nowych funkcji w zakresie opracowywania i wdrażania.

- [Opis usługi Microsoft Defender for Office 365 zawiera](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) opis funkcji i dostępności w usłudze Defender dla Office 365 planów.

## <a name="see-also"></a>Zobacz też

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [Zautomatyzowane badanie i odpowiedź (AIR) w programie Microsoft 365 Defender](../defender/m365d-autoir.md)
