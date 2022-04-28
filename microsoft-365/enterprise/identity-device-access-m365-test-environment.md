---
title: Tożsamość i dostęp urządzeń dla środowiska testowego Microsoft 365
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Tworzenie środowiska Microsoft 365 w celu przetestowania tożsamości i dostępu do urządzenia.
ms.openlocfilehash: 09c7bf9ecb6aaadc89cedfd881e66a5fd19f28d7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091220"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>Tożsamość i dostęp urządzeń dla środowiska testowego Microsoft 365

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

[Konfiguracje tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md) to zestaw zalecanych konfiguracji i zasad dostępu warunkowego w celu ochrony dostępu do wszystkich usług zintegrowanych z usługą Azure Active Directory (Azure AD).

Aby utworzyć środowisko testowe z typowymi konfiguracjami tożsamości i dostępu do urządzeń:

1. Skonfiguruj środowisko testowe przy użyciu funkcji tożsamości wymagań wstępnych i zabezpieczeń na podstawie wybranego modelu tożsamości i metody uwierzytelniania:

  - [Tylko w chmurze](cloud-only-prereqs-m365-test-environment.md)
  - [Synchronizacja skrótów haseł (PHS)](phs-prereqs-m365-test-environment.md)
  - [Uwierzytelnianie przekazywane (PTA)](pta-prereqs-m365-test-environment.md)

2. Użyj [typowych zasad dostępu do tożsamości i urządzeń](../security/office-365-security/identity-access-policies.md) , aby skonfigurować zasady bazujące na wymaganiach wstępnych skonfigurowanych dla środowiska testowego oraz eksplorować i weryfikować ochronę tożsamości i urządzeń.

## <a name="see-also"></a>Zobacz też

[Dodatkowe przewodniki laboratorium testów tożsamości](m365-enterprise-test-lab-guides.md#identity)

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)
