---
title: Integracja serwera SIEM z usługami i aplikacjami Microsoft 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 11/18/2019
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom:
- Ent_Solutions
- SIEM
- seo-marvel-apr2020
description: Zapoznaj się z omówieniem integracji serwera usługi Security Information and Event Management (SIEM) z usługami i aplikacjami w chmurze Microsoft 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 978319cca91322c7eb737d89cbfc167574f14093
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731422"
---
# <a name="security-information-and-event-management-siem-server-integration-with-microsoft-365-services-and-applications"></a>Integracja serwera usługi Security Information and Event Management (SIEM) z usługami i aplikacjami Microsoft 365

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="summary"></a>Podsumowanie

Czy Twoja organizacja korzysta z serwera SIEM (Security Information and Event Management) lub planuje go pobrać? Być może zastanawiasz się, jak integruje się z Microsoft 365 lub Office 365. Ten artykuł zawiera listę zasobów, których można użyć do integracji serwera SIEM z usługami i aplikacjami Microsoft 365.

> [!TIP]
> Jeśli nie masz jeszcze serwera SIEM i eksplorujesz swoje opcje, rozważ **[usługę Microsoft Sentinel](/azure/sentinel/overview)**.

## <a name="do-i-need-a-siem-server"></a>Czy potrzebuję serwera SIEM?

To, czy potrzebujesz serwera SIEM, zależy od wielu czynników, takich jak wymagania dotyczące zabezpieczeń organizacji i miejsce, w którym znajdują się dane. Microsoft 365 obejmuje szeroką gamę funkcji zabezpieczeń, które spełniają potrzeby wielu organizacji w zakresie zabezpieczeń bez dodatkowych serwerów, takich jak serwer SIEM. Niektóre organizacje mają specjalne okoliczności, które wymagają użycia serwera SIEM. Oto kilka przykładów:

- *Firma Fabrikam* ma lokalną zawartość i aplikacje, a niektóre w chmurze (mają wdrożenie chmury hybrydowej). Aby uzyskać raporty zabezpieczeń dla całej zawartości i aplikacji, firma Fabrikam zaimplementowała serwer SIEM.
- *Firma Contoso* to organizacja usług finansowych, która ma szczególnie rygorystyczne wymagania dotyczące zabezpieczeń. Dodali serwer SIEM do swojego środowiska, aby skorzystać z dodatkowej ochrony, jakiej potrzebują.

## <a name="siem-server-integration-with-microsoft-365"></a>Integracja serwera SIEM z Microsoft 365

Serwer SIEM może odbierać dane z wielu różnych usług i aplikacji Microsoft 365. W poniższej tabeli wymieniono kilka usług i aplikacji Microsoft 365 oraz dane wejściowe i zasoby serwera SIEM, aby dowiedzieć się więcej.

<br/><br/>

|usługa Microsoft 365 lub aplikacja|Dane wejściowe/metody serwera SIEM|Zasoby, aby dowiedzieć się więcej|
|---|---|---|
|[Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md)|Dzienniki inspekcji|[Integracja rozwiązania SIEM z Ochrona usługi Office 365 w usłudze Microsoft Defender](siem-integration-with-office-365-ti.md)|
|[Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)|Punkt końcowy HTTPS hostowany na platformie Azure <p> REST API|[Ściąganie alertów do narzędzi SIEM](../defender-endpoint/configure-siem.md)|
|[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)|Integracja dzienników|[Integracja rozwiązania SIEM z Microsoft Defender for Cloud Apps](/cloud-app-security/siem)|

> [!TIP]
> Zapoznaj się z usługą [Microsoft Sentinel](/azure/sentinel/overview). Usługa Microsoft Sentinel zawiera łączniki dla rozwiązań firmy Microsoft. Te łączniki są dostępne "po wyjętej wersji" i zapewniają integrację w czasie rzeczywistym. Usługi Microsoft Sentinel można używać z rozwiązaniami Microsoft 365 Defender i usługami Microsoft 365, w tym z usługami Office 365, Azure AD, Microsoft Defender for Identity, Microsoft Defender for Cloud Apps i nie tylko.

### <a name="audit-logging-must-be-turned-on"></a>Rejestrowanie inspekcji musi być włączone

Przed skonfigurowaniem integracji serwera SIEM upewnij się, że rejestrowanie inspekcji jest włączone.

- Aby uzyskać informacje o SharePoint Online, OneDrive dla Firm i Azure Active Directory, zobacz [Włączanie lub wyłączanie inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).
- Aby uzyskać Exchange Online, zobacz [Zarządzanie inspekcją skrzynek pocztowych](../../compliance/enable-mailbox-auditing.md).

## <a name="more-resources"></a>Więcej zasobów

[Integrowanie rozwiązań zabezpieczeń w Microsoft Defender dla Chmury](/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)

[Integrowanie alertów Graph interfejs API Zabezpieczenia firmy Microsoft z rozwiązaniem SIEM](/graph/security-integration)
