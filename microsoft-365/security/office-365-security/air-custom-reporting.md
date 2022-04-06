---
title: Niestandardowe rozwiązania do raportowania z automatycznym badaniem i odpowiedzią
keywords: SIEM, API, AIR, autoIR, Microsoft Defender for Endpoint, zautomatyzowane badanie, integracja, raport niestandardowy
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
description: Dowiedz się, jak zintegrować zautomatyzowane badania i odpowiedzi z niestandardowym lub innym rozwiązaniem do raportowania.
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3ff4317fc195a175a2b622c13ea4683a5e010b1c
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680714"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>Niestandardowe lub inne rozwiązania do raportowania dla programu Microsoft Defender dla Office 365

Usługa [Microsoft Defender dla Office 365](defender-for-office-365.md) umożliwia uzyskiwanie szczegółowych [informacji o zautomatyzowanych badaniach](air-view-investigation-results.md). Jednak niektóre organizacje również korzystają z rozwiązania do raportowania niestandardowego lub innego. Jeśli Twoja organizacja chce zintegrować informacje [o zautomatyzowanych](office-365-air.md) badaniach z takim rozwiązaniem, możesz użyć interfejsu API działań zarządzania Office 365 zarządzaniem.

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Usługa [Microsoft Defender dla Office 365](defender-for-office-365.md) umożliwia uzyskiwanie szczegółowych [informacji o zautomatyzowanych badaniach](air-view-investigation-results.md). Jednak niektóre organizacje również korzystają z rozwiązania do raportowania niestandardowego lub innego. Jeśli Twoja organizacja chce zintegrować informacje o zautomatyzowanych badaniach z takim rozwiązaniem, możesz użyć interfejsu API działań zarządzania Office 365 zarządzaniem.

|Zasób|Opis|
|:---|:---|
|[Office 365 interfejsów API zarządzania](/office/office-365-management-api/office-365-management-apis-overview)|Interfejs API Office 365 zarządzania zawiera informacje o różnych działaniach i zdarzeniach dotyczących użytkowników, administratorów, systemu oraz zdarzeń z aplikacji Microsoft 365 i Azure Active Directory aktywności.|
|[Wprowadzenie do interfejsów API Office 365 zarządzania](/office/office-365-management-api/get-started-with-office-365-management-apis)|Interfejs API Office 365 zarządzania używa usługi Azure AD do świadczenia usług uwierzytelniania dla Twojej aplikacji na Microsoft 365 danych. Wykonaj czynności opisane w tym artykule, aby skonfigurować tę procedurę.|
|[Office 365 interfejsu API działań zarządzania](/office/office-365-management-api/office-365-management-activity-api-reference)|Za pomocą interfejsu API działań zarządzania Office 365 możesz pobierać informacje o akcjach i zdarzeniach użytkownika, administratora, systemu oraz zasad z dzienników aktywności usługi Microsoft 365 i Azure AD. Przeczytaj ten artykuł, aby dowiedzieć się więcej o tym, jak to działa.|
|[Office 365 schemat interfejsu API działań zarządzania](/office/office-365-management-api/office-365-management-activity-api-schema)|Zapoznaj się z omówieniem schematu [Common](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) i usługi [Defender for Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) oraz analizy zagrożeń i schematu reakcji, aby uzyskać informacje o konkretnych typach danych dostępnych za pośrednictwem interfejsu API działań zarządzania Office 365.|

## <a name="see-also"></a>Zobacz też

- [Usługa Microsoft Defender dla Office 365](defender-for-office-365.md)
- [Zautomatyzowane badanie i reagowanie w Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
