---
title: Zapewnianie dostępu do zarządzanego usługodawca zabezpieczeń (MSSP)
description: Informacje o zmianach wprowadzonych w Centrum zabezpieczeń usługi Microsoft Defender portalu Microsoft 365 Defender w programie
keywords: Wprowadzenie do portalu Microsoft 365 Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender , MDO, MDE, pojedyncze okienko szyb, portal zbiegły się, portal zabezpieczeń, portal zabezpieczeń, portal zabezpieczeń Defender
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
ms.openlocfilehash: f0148a8bfe18c7636e95ceae7b268cc70b2e58ed
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500421"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>Zapewnianie dostępu do zarządzanego usługodawca zabezpieczeń (MSSP) 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Dotyczy:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Aby zaimplementować rozwiązanie do wielodostępnego dostępu delegowanego, zrób tak:

1. Włącz [opartą na rolach kontrolę](/windows/security/threat-protection/microsoft-defender-atp/rbac) dostępu dla programu Defender dla punktu końcowego za pośrednictwem portalu Microsoft 365 Defender i połącz się z Azure Active Directory usługą Azure AD.

2. Konfigurowanie [pakietów dostępu do zarządzania na](/azure/active-directory/governance/identity-governance-overview) celu żądania dostępu i inicjowania obsługi administracyjnej.

3. Zarządzaj żądaniami dostępu i inspekcjami w [programie Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>Włączanie kontroli dostępu opartej na rolach w Ochrona punktu końcowego w usłudze Microsoft Defender w Microsoft 365 Defender sieci Microsoft 365 Defender.

1. **Tworzenie grup dostępu dla zasobów MSSP w grupie AAD: Grupy**

    Te grupy zostaną połączone z rolami tworzonymi w programie Defender dla punktu końcowego w Microsoft 365 Defender sieci Web. W tym celu w dzierżawie usługi AD klienta utwórz trzy grupy. W naszym przykładzie tworzymy następujące grupy:

    - Analityk warstwy 1
    - Analityk warstwy 2
    - Osoby zatwierdzające analityków MSSP  

2. Utwórz usługę Defender dla ról punktu końcowego dla odpowiednich poziomów dostępu w programie Customer Defender for Endpoint w Microsoft 365 Defender ról i grup portalu.

    Aby włączyć RBAC w portalu Microsoft 365 Defender klientów, uzyskaj dostęp do ról > punktów końcowych & grup **> Role** z kontem użytkownika z uprawnieniami administratora globalnego lub administratora zabezpieczeń.

    :::image type="content" source="../../media/mssp-access.png" alt-text="Szczegóły dostępu do programu MSSP w portalu Microsoft 365 Defender sieci" lightbox="../../media/mssp-access.png":::

    Następnie utwórz role RBAC, aby spełnić wymagania warstwy SOC programu MSSP. Połącz te role z utworzonymi grupami użytkowników za pomocą linku "Przypisane grupy użytkowników".

    Dwie możliwe role:

    - **Analitycy poziomu 1** <br>
      Wykonywanie wszystkich akcji z wyjątkiem reakcji na żywo i zarządzania ustawieniami zabezpieczeń.

    - **Analitycy warstwy 2** <br>
      Funkcje warstwy 1 z możliwością [reagowania na żywo](/windows/security/threat-protection/microsoft-defender-atp/live-response)

    Aby uzyskać więcej informacji, [zobacz Używanie kontroli dostępu opartej na rolach](/windows/security/threat-protection/microsoft-defender-atp/rbac).

## <a name="configure-governance-access-packages"></a>Konfigurowanie pakietów dostępu do zarządzania

1. **Dodawanie programu MSSP jako połączonej organizacji w aplikacji customer AAD: Identity Governance**

    Dodanie programu MSSP jako połączonej organizacji umożliwi programowi MSSP żądanie i uzyskanie dostępu do obsługi administracyjnej. 

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do zarządzania tożsamościami: połączona organizacja. Dodaj nową organizację i wyszukaj dzierżawę analityka programu MSSP za pomocą identyfikatora dzierżawy lub domeny. Sugerujemy utworzenie oddzielnej dzierżawy usługi AD dla analityków PROGRAMU MSSP.

2. **Tworzenie wykazu zasobów w aplikacji Klient AAD: Zarządzanie tożsamościami**

    Wykazy zasobów są logicznym zbiorem pakietów dostępu utworzonym w dzierżawie usługi AD klienta.

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do zarządzania tożsamościami: wykazami i dodaj **nowy wykaz**. W naszym przykładzie będziemy to nazywać **"Accesses MSSP"**.

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="Nowy wykaz w portalu Microsoft 365 Defender sieci Microsoft 365 Defender" lightbox="../../media/goverance-catalog.png":::


    Aby uzyskać więcej informacji, [zobacz Tworzenie katalogu zasobów](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Tworzenie pakietów dostępu dla zasobów programu MSSP dla klientów i AAD: Zarządzanie tożsamościami**

    Pakiety programu Access to zbiór praw i dostępu, które żąda który zostanie przyznany po zatwierdzeniu. 

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do zarządzania tożsamościami: pakiety programu Access i dodaj **nowy pakiet dostępu**. Utwórz pakiet dostępu dla osób zatwierdzających mssp i każdej warstwy analityków. Na przykład następująca konfiguracja analityka warstwy 1 tworzy pakiet dostępu, który:

    - Wymaga od członka grupy AD osób zatwierdzających **analityków MSSP** w celu autoryzowania nowych żądań
    - Ma coroczne recenzje dostępu, w których analitycy SOC mogą zażądać rozszerzenia dostępu.
    - Użytkownicy mogą zażądać tylko w dzierżawie SOC programu MSSP
    - Automatyczne wygasanie programu Access po 365 dniach

    :::image type="content" source="../../media/new-access-package.png" alt-text="Szczegóły nowego pakietu dostępu w portalu Microsoft 365 Defender dostępu" lightbox="../../media/new-access-package.png":::

    Aby uzyskać więcej informacji, [zobacz Tworzenie nowego pakietu dostępu](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Udostępnij łącze żądania dostępu do zasobów programu MSSP z zasobów klientów i AAD: Zarządzanie tożsamościami**

    Link Mój portal programu Access jest używany przez analityków SOC programu MSSP do żądania dostępu za pośrednictwem utworzonych pakietów dostępu. Link jest trwałe, co oznacza, że z czasem ten sam link może być używany dla nowych analityków. Żądanie analityka trafia do kolejki w celu zatwierdzenia przez osoby zatwierdzające analityka **MSSP**.

    :::image type="content" source="../../media/access-properties.png" alt-text="Właściwości dostępu w portalu Microsoft 365 Defender sieci Microsoft 365 Defender." lightbox="../../media/access-properties.png":::

    Link znajduje się na stronie przeglądu każdego pakietu dostępu.

## <a name="manage-access"></a>Zarządzanie dostępem

1. Przejrzyj i autoryzuj żądania dostępu w  mojego dostępu klienta i/lub MSSP.

    Żądania dostępu są zarządzane przez klienta Mój dostęp przez członków grupy Osoby zatwierdzające analityków MSSP.

    Aby to zrobić, uzyskaj dostęp do funkcji mój dostęp klienta, używając: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Przykład: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Zatwierdź lub odmów żądania **Zatwierdzenia** sekcji interfejsu użytkownika.

     W tym momencie dostęp analityka został inicjowania obsługi i każdy analityk powinien mieć dostęp do portalu Microsoft 365 Defender klienta:

    `https://security.microsoft.com/?tid=<CustomerTenantId>` z przypisanymi uprawnieniami i rolami.

> [!IMPORTANT]
> Delegowany dostęp do Ochrona punktu końcowego w usłudze Microsoft Defender w portalu Microsoft 365 Defender obecnie umożliwia dostęp do jednej dzierżawy w jednym oknie przeglądarki.
