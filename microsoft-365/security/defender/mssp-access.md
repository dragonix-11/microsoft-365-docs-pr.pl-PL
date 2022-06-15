---
title: Zapewnianie dostępu do zarządzanego dostawcy usług zabezpieczeń (MSSP)
description: Dowiedz się więcej o zmianach z Centrum zabezpieczeń usługi Microsoft Defender do portalu Microsoft 365 Defender
keywords: Wprowadzenie do portalu Microsoft 365 Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender , MDO, MDE, pojedyncze okienko szkła, portal konwergentny, portal zabezpieczeń, portal zabezpieczeń usługi Defender
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
manager: dansimp
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.openlocfilehash: 4eccd4d6140810bae4caef5e194082aeb3054217
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102377"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>Zapewnianie dostępu do zarządzanego dostawcy usług zabezpieczeń (MSSP) 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Dotyczy:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Aby zaimplementować rozwiązanie dostępu delegowanego z wieloma dzierżawami, wykonaj następujące kroki:

1. Włącz [kontrolę dostępu opartą na rolach](/microsoft-365/security/defender-endpoint/rbac) dla usługi Defender for Endpoint za pośrednictwem portalu Microsoft 365 Defender i połącz się z grupami Azure Active Directory (Azure AD).

2. Skonfiguruj [zarządzanie uprawnieniami dla użytkowników zewnętrznych](/azure/active-directory/governance/entitlement-management-external-users) w ramach Azure AD Identity Governance, aby umożliwić żądania dostępu i aprowizację.

3. Zarządzanie żądaniami dostępu i inspekcjami w [usłudze Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>Włączanie kontroli dostępu opartej na rolach w Ochrona punktu końcowego w usłudze Microsoft Defender w portalu Microsoft 365 Defender

1. **Tworzenie grup dostępu dla zasobów MSSP w usłudze Customer AAD: Groups**

    Te grupy zostaną połączone z rolami utworzonymi w usłudze Defender for Endpoint w portalu Microsoft 365 Defender. W tym celu w dzierżawie usługi AD klienta utwórz trzy grupy. W naszym przykładowym podejściu utworzymy następujące grupy:

    - Analityk warstwy 1
    - Analityk warstwy 2
    - Osoby zatwierdzające analityków MSSP  

2. Utwórz role usługi Defender for Endpoint dla odpowiednich poziomów dostępu w usłudze Customer Defender for Endpoint w Microsoft 365 Defender ról i grup portalu.

    Aby włączyć kontrolę dostępu opartą na rolach w portalu Microsoft 365 Defender klienta, uzyskaj dostęp do **ról > punktów końcowych & grup > ról** przy użyciu konta użytkownika z uprawnieniami administratora globalnego lub administratora zabezpieczeń.

    :::image type="content" source="../../media/mssp-access.png" alt-text="Szczegóły dostępu mssp w portalu Microsoft 365 Defender" lightbox="../../media/mssp-access.png":::

    Następnie utwórz role RBAC w celu spełnienia potrzeb warstwy SOC programu MSSP. Połącz te role z utworzonymi grupami użytkowników za pomocą polecenia "Przypisane grupy użytkowników".

    Dwie możliwe role:

    - **Analitycy warstwy 1** <br>
      Wykonaj wszystkie akcje z wyjątkiem odpowiedzi na żywo i zarządzaj ustawieniami zabezpieczeń.

    - **Analitycy warstwy 2** <br>
      Możliwości warstwy 1 z dodatkiem do [odpowiedzi na żywo](/microsoft-365/security/defender-endpoint/live-response).

    Aby uzyskać więcej informacji, zobacz [Zarządzanie dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](/microsoft-365/security/defender-endpoint/rbac).

## <a name="configure-governance-access-packages"></a>Konfigurowanie pakietów dostępu do ładu

1. **Dodawanie programu MSSP jako połączonej organizacji w usłudze Customer AAD: Identity Governance**

    Dodanie dostawcy MSSP jako połączonej organizacji umożliwi dostawcy mssp żądania i aprowizowanie dostępu. 

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do usługi Identity Governance: Połączona organizacja. Dodaj nową organizację i wyszukaj dzierżawę analityka MSSP za pośrednictwem identyfikatora dzierżawy lub domeny. Zalecamy utworzenie oddzielnej dzierżawy usługi AD dla analityków MSSP.

2. **Tworzenie wykazu zasobów w usłudze Customer AAD: Identity Governance**

    Wykazy zasobów to logiczna kolekcja pakietów dostępu utworzona w dzierżawie usługi AD klienta.

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do usługi Identity Governance: Catalogs i dodaj **nowy wykaz**. W naszym przykładzie będziemy nazywać go **MSSP Accesses**.

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="Nowy wykaz w portalu Microsoft 365 Defender" lightbox="../../media/goverance-catalog.png":::


    Więcej informacji można znaleźć [w temacie Tworzenie wykazu zasobów](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Tworzenie pakietów dostępu dla zasobów MSSP Customer AAD: Identity Governance**

    Pakiety dostępu to kolekcja praw i dostępu, które żądający zostanie udzielony po zatwierdzeniu. 

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do usługi Identity Governance: Access Packages i dodaj **nowy pakiet dostępu**. Utwórz pakiet dostępu dla osób zatwierdzających mssp i każdej warstwy analityka. Na przykład następująca konfiguracja analityka warstwy 1 tworzy pakiet dostępu, który:

    - Wymaga, aby członek grupy usług AD **administratorów analityków MSSP** autoryzował nowe żądania
    - Ma coroczne przeglądy dostępu, w których analitycy SOC mogą zażądać rozszerzenia dostępu
    - Może być żądany tylko przez użytkowników w dzierżawie MSSP SOC
    - Automatyczne uzyskiwanie dostępu wygasa po 365 dniach

    :::image type="content" source="../../media/new-access-package.png" alt-text="Szczegóły nowego pakietu dostępu w portalu Microsoft 365 Defender" lightbox="../../media/new-access-package.png":::

    Aby uzyskać więcej informacji, zobacz [Tworzenie nowego pakietu dostępu](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Podaj link żądania dostępu do zasobów MSSP z usługi Customer AAD: Identity Governance**

    Link portalu Mój dostęp jest używany przez analityków MSSP SOC do żądania dostępu za pośrednictwem utworzonych pakietów dostępu. Link jest trwały, co oznacza, że ten sam link może być używany w czasie dla nowych analityków. Żądanie analityka przechodzi do kolejki w celu zatwierdzenia przez **osoby zatwierdzające analityka MSSP**.

    :::image type="content" source="../../media/access-properties.png" alt-text="Właściwości dostępu w portalu Microsoft 365 Defender" lightbox="../../media/access-properties.png":::

    Link znajduje się na stronie przeglądu każdego pakietu dostępu.

## <a name="manage-access"></a>Zarządzanie dostępem

1. Przejrzyj i autoryzuj żądania dostępu w aplikacji Customer i/lub MSSP myaccess.

    Żądania dostępu są zarządzane w kliencie Mój dostęp przez członków grupy Osób zatwierdzających analityków MSSP.

    Aby to zrobić, uzyskaj dostęp do aplikacji myaccess klienta przy użyciu: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Przykład: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Zatwierdzanie lub odrzucanie żądań w sekcji **Zatwierdzenia** interfejsu użytkownika.

     W tym momencie aprowizowano dostęp analityków i każdy analityk powinien mieć dostęp do portalu Microsoft 365 Defender klienta:

    `https://security.microsoft.com/?tid=<CustomerTenantId>` z przypisanymi uprawnieniami i rolami.
