---
title: Tożsamość i dostęp do urządzeń w środowisku Microsoft 365 testowym
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Utwórz środowisko Microsoft 365, aby przetestować tożsamość i dostęp do urządzenia.
ms.openlocfilehash: 488bd22b555ab30a27e0d9c8ef662af1b6945da9
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015958"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>Tożsamość i dostęp do urządzeń w środowisku Microsoft 365 testowym

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

[Konfiguracje tożsamości i](../security/office-365-security/microsoft-365-policies-configurations.md) dostępu do urządzeń są zestawem zalecanych konfiguracji i zasad dostępu warunkowego w celu ochrony dostępu do wszystkich usług zintegrowanych z usługą Azure Active Directory (Azure AD).

Aby utworzyć środowisko testowe, w którym są dostępne typowe konfiguracje tożsamości i dostępu do urządzeń:

1. Skonfiguruj środowisko testowe przy użyciu wstępnie wymaganej funkcji tożsamości i zabezpieczeń na podstawie wybranego modelu tożsamości i metody uwierzytelniania:

  - [Tylko w chmurze](cloud-only-prereqs-m365-test-environment.md)
  - [Synchronizacja skrótów haseł (PHS)](phs-prereqs-m365-test-environment.md)
  - [Uwierzytelnianie pass-through (PTA)](pta-prereqs-m365-test-environment.md)

2. Użyj [wspólnych zasad dostępu do tożsamości](../security/office-365-security/identity-access-policies.md) i urządzeń, aby skonfigurować zasady na podstawie wymagań wstępnych skonfigurowanych dla środowiska testowego oraz eksplorować i weryfikować ochronę tożsamości i urządzeń.

## <a name="see-also"></a>Zobacz też

[Dodatkowe przewodniki laboratorium testowego dotyczące tożsamości](m365-enterprise-test-lab-guides.md#identity)

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)
