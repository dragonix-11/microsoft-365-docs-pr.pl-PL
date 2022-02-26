---
title: Uzyskiwanie dostępu do Microsoft 365 Defender klienta programu MSSP
description: Uzyskiwanie dostępu do Microsoft 365 Defender klienta programu MSSP
keywords: zarządzane zabezpieczenia usługodawca, mssp, konfigurowanie, integracja
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 5a359938dbee85ea64b5f46804761410cae1f48e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62973804"
---
# <a name="access-the-microsoft-365-defender-mssp-customer-portal"></a>Uzyskiwanie dostępu do Microsoft 365 Defender klienta programu MSSP

**Dotyczy:**
- [ Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [ Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Te kroki są kierowane do programu MSSP.

Domyślnie klienci korzystający z programu MSSP mają Microsoft 365 Defender dzierżawę, korzystając z następującego adresu URL: `https://securitycenter.windows.com/`.

Jednak w celu uzyskania dostępu do portalu klientów programu MSSP należy użyć adresu URL specyficznego dla dzierżawy w następującym formacie: `https://securitycenter.windows.com?tid=customer_tenant_id`

Na ogół mssp należy dodać do każdego klienta MSSP w usłudze Azure AD, która będzie zarządzać.

Aby uzyskać identyfikator dzierżawy klienta programu MSSP, a następnie użyć tego identyfikatora w celu uzyskania dostępu do adresu URL dzierżawy, należy wykonać następujące czynności:

1. Jako program MSSP zaloguj się do usługi Azure AD przy użyciu poświadczeń.

2. Przełączanie katalogu do dzierżawy klienta MSSP.

3. Wybierz **Azure Active Directory > Właściwości**. Identyfikator dzierżawy znajdziesz w polu Identyfikator katalogu.

4. Aby uzyskać dostęp do portalu klientów programu MSSP, zastąp wartość `customer_tenant_id` w następującym adresie URL: `https://securitycenter.windows.com/?tid=customer_tenant_id`.

## <a name="related-topics"></a>Tematy pokrewne

- [Udzielanie dostępu do portalu przez program MSSP](grant-mssp-access.md)
- [Konfigurowanie powiadomień alertów](configure-mssp-notifications.md)
- [Pobieranie alertów z dzierżawy klienta](fetch-alerts-mssp.md)
