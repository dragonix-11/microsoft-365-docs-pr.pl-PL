---
title: Możliwości reagowania & badania zagrożeń — plan 2 Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/09/2019
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 32405da5-bee1-4a4b-82e5-8399df94c512
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się więcej o możliwościach badania zagrożeń i reagowania na nie w planie Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c972a42730f4d21b73227a8b8a9900223109d590
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972040"
---
# <a name="threat-investigation-and-response"></a>Badanie zagrożeń i reagowanie na nie

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)

Możliwości badania zagrożeń i reagowania na nie w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) pomagają analitykom zabezpieczeń i administratorom chronić Microsoft 365 organizacji dla użytkowników biznesowych, wykonując następujące czynności:

- Ułatwianie identyfikowania, monitorowania i zrozumienia cyberataków.
- Pomaga szybko rozwiązywać problemy z zagrożeniami w Exchange Online, SharePoint Online, OneDrive dla Firm i Microsoft Teams.
- Zapewnianie szczegółowych informacji i wiedzy ułatwiających operacjom zabezpieczeń zapobieganie cyberatakom na ich organizację.
- Stosowanie [zautomatyzowanego badania i reagowania w Office 365](automated-investigation-response-office.md) w przypadku krytycznych zagrożeń opartych na wiadomościach e-mail.

Możliwości badania zagrożeń i reagowania na nie zapewniają wglądu w zagrożenia i powiązane akcje reagowania, które są dostępne w portalu Microsoft 365 Defender. Te szczegółowe informacje mogą pomóc zespołowi ds. zabezpieczeń organizacji chronić użytkowników przed atakami opartymi na wiadomościach e-mail lub plikach. Funkcje te ułatwiają monitorowanie sygnałów i zbieranie danych z wielu źródeł, takich jak aktywność użytkownika, uwierzytelnianie, poczta e-mail, komputery z naruszeniem zabezpieczeń i zdarzenia zabezpieczeń. Osoby podejmujące decyzje biznesowe i zespół ds. operacji zabezpieczeń mogą wykorzystać te informacje do zrozumienia zagrożeń dla organizacji i reagowania na nie oraz ochrony własności intelektualnej.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>Zapoznaj się z narzędziami do badania zagrożeń i reagowania na nie

Możliwości badania zagrożeń i reagowania na nie w portalu Microsoft 365 Defender są <https://security.microsoft.com> zestawem narzędzi i przepływów pracy reagowania, które obejmują:

- [Explorer](#explorer)
- [Zdarzenia](#incidents)
- [Trenowanie symulacji ataków](attack-simulation-training.md)
- [Zautomatyzowane badanie i reagowanie](automated-investigation-response-office.md)

### <a name="explorer"></a>Explorer

Użyj [Eksploratora (i wykrywania w czasie rzeczywistym),](threat-explorer.md) aby analizować zagrożenia, wyświetlać liczbę ataków w czasie i analizować dane według rodzin zagrożeń, infrastruktury atakującej i innych. Eksplorator (nazywany również Eksploratorem zagrożeń) to miejsce początkowe dla przepływu pracy badania każdego analityka zabezpieczeń.

:::image type="content" source="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png" alt-text="Strona Eksplorator zagrożeń" lightbox="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png":::

Aby wyświetlić ten raport i użyć go w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do **Eksploratora** współpracy \> **& poczty e-mail**. Aby przejść bezpośrednio do strony **Eksploratora** , użyj polecenia <https://security.microsoft.com/threatexplorer>.

## <a name="office-365-threat-intelligence-connection"></a>połączenie analizy zagrożeń Office 365

Ta funkcja jest dostępna tylko wtedy, gdy masz aktywną subskrypcję Office 365 E5 lub dodatek analizy zagrożeń. Aby uzyskać więcej informacji, zobacz stronę produktu Office 365 Enterprise E5.

Po włączeniu tej funkcji będzie można włączyć dane z Ochrona usługi Office 365 w usłudze Microsoft Defender do Microsoft 365 Defender, aby przeprowadzić kompleksowe badanie zabezpieczeń w skrzynkach pocztowych Office 365 i Windows Urządzeń.

> [!NOTE]
> Aby włączyć tę funkcję, musisz mieć odpowiednią licencję.

Aby uzyskać kontekstową integrację urządzeń w usłudze Office 365 Threat Intelligence, musisz włączyć ustawienia usługi Defender for Endpoint na pulpicie nawigacyjnym Security & Compliance.

### <a name="incidents"></a>Zdarzenia

Użyj listy Zdarzenia (jest to również nazywane badaniami), aby wyświetlić listę zdarzeń związanych z zabezpieczeniami lotów. Zdarzenia służą do śledzenia zagrożeń, takich jak podejrzane wiadomości e-mail, oraz do dalszego badania i korygowania.

:::image type="content" source="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png" alt-text="Lista bieżących zdarzeń związanych z zagrożeniami w Office 365" lightbox="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png":::

Aby wyświetlić listę bieżących zdarzeń dla organizacji w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do **obszaru Zdarzenia & alerty** \> **Zdarzenia**. Aby przejść bezpośrednio do strony **Zdarzenia** , użyj polecenia <https://security.microsoft.com/incidents>.

:::image type="content" source="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png" alt-text="Strona Przeglądanie w Centrum zgodności & zabezpieczeń" lightbox="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png":::

### <a name="attack-simulation-training"></a>Trenowanie symulacji ataków

Użyj szkolenia symulacji ataków, aby skonfigurować i uruchomić realistyczne cyberataki w organizacji oraz zidentyfikować osoby znajdujące się w trudnej sytuacji, zanim prawdziwy cyberatak wpłynie na Twoją firmę. Aby dowiedzieć się więcej, zobacz [Symulowanie ataku wyłudzania informacji](attack-simulation-training.md).

Aby wyświetlić tę funkcję i korzystać z niej w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do **obszaru Email & collaborationAttack simulation training (Poczta e-mail & współpraca** > **) Szkolenie symulacji ataków**. Aby przejść bezpośrednio do strony **trenowania symulacji ataków** , użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=overview>.

### <a name="automated-investigation-and-response"></a>Zautomatyzowane badanie i reagowanie

Użyj funkcji zautomatyzowanego badania i reagowania (AIR), aby zaoszczędzić czas i nakład pracy korelujący zawartość, urządzenia i osoby zagrożone zagrożeniami w organizacji. Procesy AIR mogą rozpoczynać się za każdym razem, gdy niektóre alerty są wyzwalane lub gdy są uruchamiane przez zespół ds. operacji zabezpieczeń. Aby dowiedzieć się więcej, zobacz [zautomatyzowane badanie i reagowanie w Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>Widżety analizy zagrożeń

W ramach oferty Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2 analitycy zabezpieczeń mogą przejrzeć szczegóły dotyczące znanego zagrożenia. Jest to przydatne w celu określenia, czy istnieją dodatkowe środki zapobiegawcze/kroki, które można podjąć w celu zapewnienia bezpieczeństwa użytkownikom.

:::image type="content" source="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png" alt-text="Okienko Trendy zabezpieczeń z informacjami o ostatnich zagrożeniach" lightbox="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png":::

## <a name="how-do-we-get-these-capabilities"></a>Jak uzyskać te możliwości?

Microsoft 365 możliwości badania zagrożeń i reagowania na nie są uwzględnione w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2, który jest uwzględniony w Enterprise E5 lub jako dodatek do niektórych subskrypcji. Aby dowiedzieć się więcej, zobacz [Ochrona usługi Office 365 w usłudze Defender Plan 1 i Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="required-roles-and-permissions"></a>Wymagane role i uprawnienia

Ochrona usługi Office 365 w usłudze Microsoft Defender używa kontroli dostępu opartej na rolach. Uprawnienia są przypisywane za pośrednictwem niektórych ról w Azure Active Directory, Centrum administracyjne platformy Microsoft 365 lub portalu Microsoft 365 Defender.

> [!TIP]
> Chociaż niektóre role, takie jak Administrator zabezpieczeń, można przypisać w portalu Microsoft 365 Defender, należy rozważyć użycie Centrum administracyjne platformy Microsoft 365 lub Azure Active Directory zamiast tego. Aby uzyskać informacje o rolach, grupach ról i uprawnieniach, zobacz następujące zasoby:
>
> - [Uprawnienia w portalu usługi Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
> - [Wbudowane role usługi Azure AD](/azure/active-directory/roles/permissions-reference)

|Działanie|Role i uprawnienia|
|---|---|
|Użyj pulpitu nawigacyjnego zarządzania lukami w zabezpieczeniach & (lub nowego [pulpitu nawigacyjnego zabezpieczeń)](security-dashboard.md) <p> Wyświetlanie informacji o ostatnich lub bieżących zagrożeniach|Jedna z następujących czynności: <ul><li>**Administrator globalny**</li><li>**Administrator zabezpieczeń**</li><li>**Czytelnik zabezpieczeń**</li></ul> <p> Te role można przypisać w Azure Active Directory (<https://portal.azure.com>) lub Centrum administracyjne platformy Microsoft 365 (<https://admin.microsoft.com>).|
|[Analizowanie zagrożeń przy użyciu Eksploratora (i wykrywania w czasie rzeczywistym)](threat-explorer.md)|Jedna z następujących czynności: <ul><li>**Administrator globalny**</li><li>**Administrator zabezpieczeń**</li><li>**Czytelnik zabezpieczeń**</li></ul> <p> Te role można przypisać w Azure Active Directory (<https://portal.azure.com>) lub Centrum administracyjne platformy Microsoft 365 (<https://admin.microsoft.com>).|
|Wyświetlanie zdarzeń (nazywanych również badaniami) <p> Dodawanie wiadomości e-mail do zdarzenia|Jedna z następujących czynności: <ul><li>**Administrator globalny**</li><li>**Administrator zabezpieczeń**</li><li>**Czytelnik zabezpieczeń**</li></ul> <p> Te role można przypisać w Azure Active Directory (<https://portal.azure.com>) lub Centrum administracyjne platformy Microsoft 365 (<https://admin.microsoft.com>).|
|Wyzwalanie akcji poczty e-mail w zdarzeniu <p> Znajdowanie i usuwanie podejrzanych wiadomości e-mail|Jedna z następujących czynności: <ul><li>**Administrator globalny**</li><li>**Administrator zabezpieczeń** oraz rola **Wyszukiwania i przeczyszczania**</li></ul> <p> Role **administratora globalnego** i **administratora zabezpieczeń** można przypisać w Azure Active Directory (<https://portal.azure.com>) lub Centrum administracyjne platformy Microsoft 365 (<https://admin.microsoft.com>). <p> Rola **Wyszukaj i przeczyszczanie** musi zostać przypisana do **ról współpracy & poczty e-mail** w portalu usługi Microsoft 36 Defender (<https://security.microsoft.com>).|
|Integracja planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2 z Ochrona punktu końcowego w usłudze Microsoft Defender <p> Integrowanie Ochrona usługi Office 365 w usłudze Microsoft Defender planu 2 z serwerem SIEM|Rola **administratora globalnego** lub **administratora zabezpieczeń** przypisana w Azure Active Directory (<https://portal.azure.com>) lub Centrum administracyjne platformy Microsoft 365 (<https://admin.microsoft.com>). <p> --- **Plus** --- <p> Odpowiednia rola przypisana w dodatkowych aplikacjach (takich jak [Centrum zabezpieczeń usługi Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/user-roles) lub serwer SIEM).|

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o monitorach zagrożeń — nowe i godne uwagi](threat-trackers.md)
- [Znajdowanie i badanie dostarczonej złośliwej wiadomości e-mail (Office 365 badanie zagrożeń i reagowanie)](investigate-malicious-email-that-was-delivered.md)
- [Integrowanie Office 365 badania zagrożeń i reagowania na nie z Ochrona punktu końcowego w usłudze Microsoft Defender](integrate-office-365-ti-with-mde.md)
- [Symulowanie ataku wyłudzania informacji](attack-simulation-training.md)
