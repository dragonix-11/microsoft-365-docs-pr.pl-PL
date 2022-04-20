---
title: Ochrona usługi Office 365 w usłudze Microsoft Defender — CSH
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
description: Ochrona usługi Office 365 w usłudze Microsoft Defender obejmuje załączniki Sejf, linki Sejf, zaawansowane narzędzia chroniące przed wyłudzaniem informacji, narzędzia do raportowania i możliwości analizy zagrożeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a181f8ef6bb7ca018fb9ddf0f0adc4fe565b73e1
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941550"
---
# <a name="microsoft-defender-for-office-365"></a>Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych, którzy [mają Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Jeśli używasz witryny Outlook.com, Microsoft 365 Family lub Microsoft 365 Personal i szukasz informacji na temat linków Sejf lub załączników Sejf w Outlook, zobacz [Zaawansowane zabezpieczenia Outlook.com dla Microsoft 365 subskrybentów](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Ochrona usługi Office 365 w usłudze Microsoft Defender chroni organizację przed złośliwymi zagrożeniami związanymi z wiadomościami e-mail, linkami (adresami URL) i narzędziami do współpracy. Ochrona usługi Office 365 w usłudze Defender obejmuje:

- **[Zasady ochrony przed zagrożeniami](#configure-microsoft-defender-for-office-365-policies)**: zdefiniuj zasady ochrony przed zagrożeniami, aby ustawić odpowiedni poziom ochrony organizacji.

- **[Raporty](#view-microsoft-defender-for-office-365-reports)**: wyświetlanie raportów w czasie rzeczywistym w celu monitorowania wydajności Ochrona usługi Office 365 w usłudze Defender w organizacji.

- **[Możliwości badania zagrożeń i reagowania na](#use-threat-investigation-and-response-capabilities)** nie: użyj wiodących narzędzi do badania, zrozumienia, symulowania i zapobiegania zagrożeniom.

- **[Funkcje zautomatyzowanego badania i reagowania](office-365-air.md)**: oszczędzaj czas i nakład pracy na badanie i ograniczanie zagrożeń.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>Interaktywny przewodnik po Ochrona usługi Office 365 w usłudze Microsoft Defender

W tym interaktywnym przewodniku dowiesz się, jak chronić organizację za pomocą Ochrona usługi Office 365 w usłudze Microsoft Defender. Dowiesz się, jak Ochrona usługi Office 365 w usłudze Defender mogą pomóc w definiowaniu zasad ochrony, analizie zagrożeń dla organizacji i reagowaniu na ataki.

[Zapoznaj się z interaktywnym przewodnikiem](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>Wprowadzenie

Jeśli dopiero Ochrona usługi Office 365 w usłudze Microsoft Defender lub uczysz się *najlepiej, możesz* skorzystać z podzielenia początkowej konfiguracji Ochrona usługi Office 365 w usłudze Defender na fragmenty, badania i wyświetlanie raportów przy użyciu tego artykułu jako odwołania. Oto logiczne wczesne fragmenty konfiguracji:

- Skonfiguruj wszystkie elementy z nazwą "*anti*".
  - ochrona przed złośliwym oprogramowaniem
  - ochrona przed wyłudzaniem informacji
  - anty-spam
- Skonfiguruj wszystko z wartością "*safe*" w nazwie.
  - Bezpieczne linki
  - załączniki Sejf
- Bronić obciążeń (np. SharePoint Online, OneDrive i Teams)
- Ochrona przy użyciu automatycznego przeczyszczania o wartości zero godzin (ZAP).

Aby dowiedzieć się, jak to zrobić, [kliknij ten link](protect-against-threats.md).

> [!NOTE]
> Ochrona usługi Office 365 w usłudze Microsoft Defender jest dostępny w dwóch różnych typach planów. Jeśli masz Eksploratora zagrożeń, możesz sprawdzić, czy masz **plan 1** , czy masz "wykrywanie w czasie rzeczywistym" i **plan 2**. Plan, który masz, ma wpływ na narzędzia, które zobaczysz, więc upewnij się, że masz świadomość swojego planu w miarę nauki.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2

W poniższej tabeli przedstawiono podsumowanie elementów uwzględnionych w każdym planie.

|Ochrona usługi Office 365 w usłudze Defender plan 1|Ochrona usługi Office 365 w usłudze Defender plan 2|
|---|---|
|Możliwości konfiguracji, ochrony i wykrywania: <ul><li>[załączniki Sejf](safe-attachments.md)</li><li>[Bezpieczne linki](safe-links.md)</li><li>[Bezpieczne załączniki dla programu SharePoint, usługi OneDrive i aplikacji Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Ochrona przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Wykrywanie w czasie rzeczywistym](threat-explorer.md)</li></ul>|Ochrona usługi Office 365 w usłudze Defender plan 1 — możliwości <p> --- plus --- <p> Możliwości automatyzacji, badania, korygowania i edukacji: <ul><li>[Moduły śledzące zagrożenia](threat-trackers.md)</li><li>[Eksplorator zagrożeń](threat-explorer.md)</li><li>[Zautomatyzowane badanie i reagowanie](office-365-air.md)</li><li>[Trenowanie symulacji ataków](attack-simulation-training.md)</li><li>[Proaktywne wyszukiwanie zagrożeń dzięki zaawansowanym polowaniom w Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Badanie zdarzeń w Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Badanie alertów w Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 jest uwzględniony w Office 365 E5, Office 365 A5 i Microsoft 365 E5.

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 jest uwzględniony w Microsoft 365 Business Premium.

- Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 1 i Ochrona usługi Office 365 w usłudze Defender Plan 2 są dostępne jako dodatek dla niektórych subskrypcji. Aby dowiedzieć się więcej, oto kolejny link [Dostępność funkcji w planach Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funkcja [dokumenty Sejf](safe-docs.md) jest dostępna tylko dla użytkowników z licencjami Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5 (nieobjętymi Ochrona usługi Office 365 w usłudze Microsoft Defender planów).

- Jeśli bieżąca subskrypcja nie zawiera Ochrona usługi Office 365 w usłudze Microsoft Defender i chcesz, [skontaktuj się ze sprzedażą, aby rozpocząć wersję próbną](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html), i dowiedz się, jak Ochrona usługi Office 365 w usłudze Microsoft Defender mogą działać w organizacji.

- Ochrona usługi Office 365 w usłudze Microsoft Defender klienci P2 mają dostęp do **integracji Microsoft 365 Defender** w celu wydajnego wykrywania, przeglądania i reagowania na zdarzenia i alerty.

## <a name="configure-microsoft-defender-for-office-365-policies"></a>Konfigurowanie zasad Ochrona usługi Office 365 w usłudze Microsoft Defender

Dzięki Ochrona usługi Office 365 w usłudze Microsoft Defender zespół ds. zabezpieczeń organizacji może skonfigurować ochronę, definiując zasady w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com> Email & collaboration **Policies & rules** Threat policies (Zasady **współpracy** \> & poczty e-mail & **zasad**\> zagrożeń). Możesz też przejść bezpośrednio do strony **Zasady zagrożeń** przy użyciu polecenia <https://security.microsoft.com/threatpolicy>.

Dowiedz się więcej, oglądając [ten film wideo](https://www.youtube.com/watch?v=vivvTmWJ_3c).

> [!TIP]
> Aby uzyskać szybką listę zasad do zdefiniowania, zobacz [Ochrona przed zagrożeniami](protect-against-threats.md).

## <a name="defender-for-office-365-policies"></a>zasady Ochrona usługi Office 365 w usłudze Defender

Zasady zdefiniowane dla organizacji określają poziom zachowania i ochrony wstępnie zdefiniowanych zagrożeń. Opcje zasad są niezwykle elastyczne. Na przykład zespół ds. zabezpieczeń organizacji może ustawić szczegółową ochronę przed zagrożeniami na poziomie użytkownika, organizacji, adresata i domeny. Ważne jest regularne przeglądanie zasad, ponieważ codziennie pojawiają się nowe zagrożenia i wyzwania.

- **[Sejf załączników](safe-attachments.md)**: zapewnia ochronę bez dni w celu ochrony systemu obsługi komunikatów przez sprawdzanie załączników wiadomości e-mail pod kątem złośliwej zawartości. Kieruje wszystkie komunikaty i załączniki, które nie mają sygnatury wirusa/złośliwego oprogramowania, do specjalnego środowiska, a następnie używa technik uczenia maszynowego i analizy do wykrywania złośliwych intencji. Jeśli nie zostanie znalezione podejrzane działanie, wiadomość zostanie przekazana do skrzynki pocztowej. Aby dowiedzieć się więcej, zobacz [Konfigurowanie zasad Sejf załączników](set-up-safe-attachments-policies.md).

- **[Sejf Linki](safe-links.md)**: zapewnia weryfikację adresów URL po kliknięciu, na przykład w wiadomościach e-mail i plikach Office. Ochrona jest w toku i ma zastosowanie w środowisku komunikatów i Office. Linki są skanowane dla każdego kliknięcia: bezpieczne linki pozostają dostępne, a złośliwe linki są dynamicznie blokowane. Aby dowiedzieć się więcej, zobacz [Konfigurowanie zasad linków Sejf](set-up-safe-links-policies.md).

- **[Sejf Załączniki dla SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)**: chroni organizację, gdy użytkownicy współpracują i udostępniają pliki, identyfikując i blokując złośliwe pliki w witrynach zespołu i bibliotekach dokumentów. Aby dowiedzieć się więcej, zobacz [Włączanie Ochrona usługi Office 365 w usłudze Defender dla SharePoint, OneDrive i Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

- **[Ochrona przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)**: wykrywa próby personifikacji użytkowników i domen wewnętrznych lub niestandardowych. Stosuje modele uczenia maszynowego i zaawansowane algorytmy wykrywania personifikacji, aby zapobiec atakom wyłudzającym informacje. Aby dowiedzieć się więcej, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>Wyświetlanie raportów Ochrona usługi Office 365 w usłudze Microsoft Defender

Ochrona usługi Office 365 w usłudze Microsoft Defender obejmuje [raporty](view-reports-for-mdo.md) do monitorowania Ochrona usługi Office 365 w usłudze Defender. Dostęp do raportów można uzyskać w portalu usługiMicrosoft 365 Defender pod adresem <https://security.microsoft.com> Reports **Email & collaboration** Email & collaboration reports (**Raporty** \> dotyczące współpracy \> & **e-mail & raporty współpracy**). Możesz też przejść bezpośrednio do strony **Raporty dotyczące poczty e-mail i współpracy** przy użyciu polecenia <https://security.microsoft.com/securityreports>.

Raporty są aktualizowane w czasie rzeczywistym, zapewniając najnowsze szczegółowe informacje. Te raporty zawierają również zalecenia i powiadamiają o zbliżających się zagrożeniach. Wstępnie zdefiniowane raporty obejmują następujące elementy:

- [Eksplorator zagrożeń (lub wykrywanie w czasie rzeczywistym)](threat-explorer.md)
- [Raport o stanie ochrony przed zagrożeniami](view-reports-for-mdo.md#threat-protection-status-report)
- ... i kilka innych.

## <a name="use-threat-investigation-and-response-capabilities"></a>Korzystanie z możliwości badania zagrożeń i reagowania na nie

Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 zawiera najlepsze w swojej klasie [narzędzia do badania zagrożeń i reagowania na](office-365-ti.md) nie, które umożliwiają zespołowi ds. zabezpieczeń organizacji przewidywanie, zrozumienie i zapobieganie złośliwym atakom.

- **[Monitory zagrożeń](threat-trackers.md)** zapewniają najnowsze informacje wywiadowcze na temat występujących problemów z cyberbezpieczeństwem. Możesz na przykład wyświetlić informacje o najnowszym złośliwym oprogramowaniu i podjąć środki zaradcze, zanim stanie się ono rzeczywistym zagrożeniem dla organizacji. Dostępne [trackery obejmują godne uwagi trackery](threat-trackers.md#noteworthy-trackers), [śledzenie trendów](threat-trackers.md#trending-trackers), [śledzone zapytania](threat-trackers.md#tracked-queries) i [zapisane zapytania](threat-trackers.md#saved-queries).

- **[Eksplorator zagrożeń (lub wykrywanie w czasie rzeczywistym)](threat-explorer.md)** (nazywany również Eksploratorem) to raport w czasie rzeczywistym, który umożliwia identyfikowanie i analizowanie ostatnich zagrożeń. Eksplorator można skonfigurować tak, aby pokazywał dane dla okresów niestandardowych.

- **[Trenowanie symulacji ataków](attack-simulation-training.md)** umożliwia uruchamianie realistycznych scenariuszy ataków w organizacji w celu zidentyfikowania luk w zabezpieczeniach. Dostępne są symulacje bieżących typów ataków, w tym zbieranie poświadczeń wyłudzania informacji włóczni i ataki na załączniki oraz atak z użyciem sprayu haseł i ataków siłowych haseł.

## <a name="save-time-with-automated-investigation-and-response"></a>Oszczędzaj czas dzięki zautomatyzowanemu badaniu i reagowaniu

(**NOWY!**) Podczas badania potencjalnego cyberataku czas jest najważniejszy. Im szybciej będzie można identyfikować i eliminować zagrożenia, tym lepiej będzie w twojej organizacji. [Funkcje zautomatyzowanego badania i reagowania](office-365-air.md) (AIR) obejmują zestaw podręczników zabezpieczeń, które mogą być uruchamiane automatycznie, na przykład po wyzwoleniu alertu lub ręcznie, na przykład z widoku w Eksploratorze. Usługa AIR może zaoszczędzić czas i nakład pracy zespołu ds. operacji zabezpieczeń w efektywnym i wydajnym ograniczaniu zagrożeń. Aby dowiedzieć się więcej, zobacz [AIR w Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>Uprawnienia wymagane do korzystania z funkcji Ochrona usługi Office 365 w usłudze Microsoft Defender

Aby uzyskać dostęp do Ochrona usługi Office 365 w usłudze Microsoft Defender funkcji, musisz mieć przypisaną odpowiednią rolę. Poniższa tabela zawiera kilka przykładów:

|Rola lub grupa ról|Zasoby, aby dowiedzieć się więcej|
|---|---|
|administrator globalny (zarządzanie organizacją)|Tę rolę można przypisać w Azure Active Directory lub w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|Administrator zabezpieczeń|Tę rolę można przypisać w Azure Active Directory lub w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|Zarządzanie organizacją w Exchange Online|[Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo) <p> [Exchange Online programu PowerShell](/powershell/exchange/exchange-online-powershell)|
|Wyszukiwanie i przeczyszczanie|Ta rola jest dostępna tylko w portalu Microsoft 365 Defender lub portalu zgodności usługi Microsoft Purview. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md) i [uprawnienia w portalu zgodności usługi Microsoft Purview](../../compliance/microsoft-365-compliance-center-permissions.md).|
|||

## <a name="get-microsoft-defender-for-office-365"></a>Pobieranie Ochrona usługi Office 365 w usłudze Microsoft Defender

Ochrona usługi Office 365 w usłudze Microsoft Defender jest uwzględniony w niektórych subskrypcjach, takich jak Microsoft 365 E5, Office 365 E5, Office 365 A5 i Microsoft 365 Business Premium. Jeśli Twoja subskrypcja nie obejmuje Ochrona usługi Office 365 w usłudze Defender, możesz kupić Ochrona usługi Office 365 w usłudze Defender plan 1 lub Ochrona usługi Office 365 w usłudze Defender plan 2 jako do niektórych subskrypcji. Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Ochrona usługi Office 365 w usłudze Microsoft Defender dostępność](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) dla listy subskrypcji, które obejmują plany Ochrona usługi Office 365 w usłudze Defender.

- [Dostępność funkcji w planach Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) dla listy funkcji uwzględnionych w planach 1 i 2.

- [Uzyskaj odpowiednie Ochrona usługi Office 365 w usłudze Microsoft Defender](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content), aby porównać plany i Ochrona usługi Office 365 w usłudze Defender zakupu.

- [Rozpoczynanie bezpłatnej wersji próbnej](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>Nowe funkcje w Ochrona usługi Office 365 w usłudze Microsoft Defender

Nowe funkcje są stale dodawane do Ochrona usługi Office 365 w usłudze Microsoft Defender. Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Microsoft 365 Plan działania](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365) zawiera listę nowych funkcji w programie i wdrażanym.

- [Opis usługi Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) opisuje funkcje i dostępność w planach Ochrona usługi Office 365 w usłudze Defender.

## <a name="see-also"></a>Zobacz też

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [Zautomatyzowane badanie i reagowanie (AIR) w Microsoft 365 Defender](../defender/m365d-autoir.md)
