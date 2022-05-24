---
title: Niestandardowe rozwiązania do raportowania z automatycznym badaniem i odpowiedzią
keywords: SIEM, API, AIR, autoIR, Ochrona punktu końcowego w usłudze Microsoft Defender, zautomatyzowane badanie, integracja, raport niestandardowy
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Dowiedz się, jak zintegrować zautomatyzowane badanie i reagowanie z niestandardowym lub zewnętrznym rozwiązaniem do raportowania.
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f21ed51cc9e89c2d60c924df377f109c6e29eec6
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647892"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>Niestandardowe lub zewnętrzne rozwiązania do raportowania dla Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dzięki [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) uzyskasz [szczegółowe informacje o zautomatyzowanych badaniach](air-view-investigation-results.md). Jednak niektóre organizacje korzystają również z niestandardowego lub zewnętrznego rozwiązania do raportowania. Jeśli Twoja organizacja chce zintegrować informacje o [zautomatyzowanych badaniach](office-365-air.md) z takim rozwiązaniem, możesz użyć interfejsu API działania zarządzania Office 365.

Dzięki [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) uzyskasz [szczegółowe informacje o zautomatyzowanych badaniach](air-view-investigation-results.md). Jednak niektóre organizacje korzystają również z niestandardowego lub zewnętrznego rozwiązania do raportowania. Jeśli Twoja organizacja chce zintegrować informacje o zautomatyzowanych badaniach z takim rozwiązaniem, możesz użyć interfejsu API działania zarządzania Office 365.

|Zasób|Opis|
|:---|:---|
|[Omówienie interfejsów API zarządzania Office 365](/office/office-365-management-api/office-365-management-apis-overview)|Interfejs API działania zarządzania Office 365 zawiera informacje o różnych akcjach i zdarzeniach dotyczących użytkowników, administratorów, systemów i zasad z dzienników aktywności Microsoft 365 i Azure Active Directory.|
|[Wprowadzenie z interfejsami API zarządzania Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis)|Interfejs API zarządzania Office 365 używa Azure AD do udostępniania usług uwierzytelniania dla aplikacji w celu uzyskania dostępu do danych Microsoft 365. Wykonaj kroki opisane w tym artykule, aby to skonfigurować.|
|[Dokumentacja dotycząca interfejsu API działań związanych z zarządzaniem w usłudze Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)|Interfejs API działania zarządzania Office 365 umożliwia pobieranie informacji o akcjach i zdarzeniach dotyczących użytkowników, administratorów, systemów i zasad oraz z dzienników aktywności Microsoft 365 i Azure AD. Przeczytaj ten artykuł, aby dowiedzieć się więcej o tym, jak to działa.|
|[Schemat interfejsu API działań związanych z zarządzaniem w usłudze Office 365](/office/office-365-management-api/office-365-management-activity-api-schema)|Zapoznaj się z omówieniem [wspólnego schematu](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) oraz [schematu Ochrona usługi Office 365 w usłudze Defender i badania zagrożeń oraz schematu reagowania na nie](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema), aby dowiedzieć się więcej o określonych rodzajach danych dostępnych za pośrednictwem interfejsu API działania zarządzania Office 365.|

## <a name="see-also"></a>Zobacz też

- [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md)
- [Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
