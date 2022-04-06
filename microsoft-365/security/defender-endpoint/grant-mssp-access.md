---
title: Udzielanie dostępu do zarządzanego usługodawca zabezpieczeń (MSSP)
description: Kroki niezbędne do skonfigurowania integracji programu MSSP z programem Ochrona punktu końcowego w usłudze Microsoft Defender
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
ms.openlocfilehash: c8a96f3dba51de09a7237279b4053b9f4ed9b4a7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470488"
---
# <a name="grant-managed-security-service-provider-mssp-access-preview"></a>Udzielanie dostępu do zarządzanego usługodawca zabezpieczeń (MSSP) (w wersji Preview)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Aby zaimplementować rozwiązanie do wielodostępnego dostępu delegowanego, zrób tak:

1. Włącz [opartą na rolach kontrolę dostępu w](rbac.md) usłudze Defender dla punktu końcowego i połącz się z grupami usługi Active Directory (AD).

2. Konfigurowanie [pakietów dostępu do zarządzania na](/azure/active-directory/governance/identity-governance-overview) celu żądania dostępu i inicjowania obsługi administracyjnej.

3. Zarządzaj żądaniami dostępu i inspekcjami w [programie Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint"></a>Włączanie kontroli dostępu opartej na rolach w programie Ochrona punktu końcowego w usłudze Microsoft Defender

1. **Tworzenie grup dostępu dla zasobów MSSP w grupie AAD: Grupy**

    Te grupy zostaną połączone z rolami, które tworzysz w programie Defender dla punktu końcowego. W tym celu w dzierżawie usługi AD klienta utwórz trzy grupy. W naszym przykładzie tworzymy następujące grupy:

    - Analityk warstwy 1
    - Analityk warstwy 2
    - Osoby zatwierdzające analityków MSSP

2. Utwórz usługę Defender dla ról punktu końcowego dla odpowiednich poziomów dostępu w programie Customer Defender for Endpoint.

    Aby włączyć RBAC w portalu Microsoft 365 Defender klientów, uzyskaj dostęp do Ustawienia > > **Role** i "Włączanie ról" z konta użytkownika z uprawnieniami administratora globalnego lub administratora zabezpieczeń.

    :::image type="content" source="images/mssp-access.png" alt-text="Dostęp do programu MSSP" lightbox="images/mssp-access.png":::

    Następnie utwórz role RBAC, aby spełnić wymagania warstwy SOC programu MSSP. Połącz te role z utworzonymi grupami użytkowników za pomocą linku "Przypisane grupy użytkowników".

    Dwie możliwe role:

    - **Analitycy poziomu 1**

      Wykonywanie wszystkich akcji z wyjątkiem reakcji na żywo i zarządzania ustawieniami zabezpieczeń.

    - **Analitycy warstwy 2**

      Funkcje warstwy 1 z możliwością [reagowania na żywo](live-response.md)

    Aby uzyskać więcej informacji, [zobacz Używanie kontroli dostępu opartej na rolach](rbac.md).

## <a name="configure-governance-access-packages"></a>Konfigurowanie pakietów dostępu do zarządzania

1. **Dodawanie programu MSSP jako połączonej organizacji w aplikacji customer AAD: Identity Governance**

    Dodanie programu MSSP jako połączonej organizacji umożliwi programowi MSSP żądanie i uzyskanie dostępu do obsługi administracyjnej.

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do zarządzania tożsamościami: połączona organizacja. Dodaj nową organizację i wyszukaj dzierżawę analityka programu MSSP za pomocą identyfikatora dzierżawy lub domeny. Sugerujemy utworzenie oddzielnej dzierżawy usługi AD dla analityków PROGRAMU MSSP.

2. **Tworzenie wykazu zasobów w aplikacji Klient AAD: Zarządzanie tożsamościami**

    Wykazy zasobów są logicznym zbiorem pakietów dostępu utworzonym w dzierżawie usługi AD klienta.

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do zarządzania tożsamościami: wykazami i dodaj **nowy wykaz**. W naszym przykładzie będziemy to nazywać **"Accesses MSSP"**.

    :::image type="content" source="images/goverance-catalog.png" alt-text="Strona nowego wykazu" lightbox="images/goverance-catalog.png":::

    Aby uzyskać więcej informacji, [zobacz Tworzenie katalogu zasobów](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Tworzenie pakietów dostępu dla zasobów programu MSSP dla klientów i AAD: Zarządzanie tożsamościami**

    Pakiety programu Access to zbiór praw i dostępu, które żąda który zostanie przyznany po zatwierdzeniu.

    W tym celu w dzierżawie usługi AD klienta uzyskaj dostęp do zarządzania tożsamościami: pakiety programu Access i dodaj **nowy pakiet dostępu**. Utwórz pakiet dostępu dla osób zatwierdzających mssp i każdej warstwy analityków. Na przykład następująca konfiguracja analityka warstwy 1 tworzy pakiet dostępu, który:

    - Wymaga od członka grupy AD osób zatwierdzających **analityków MSSP** w celu autoryzowania nowych żądań
    - Ma coroczne recenzje dostępu, w których analitycy SOC mogą zażądać rozszerzenia dostępu.
    - Użytkownicy mogą zażądać tylko w dzierżawie SOC programu MSSP
    - Automatyczne wygasanie programu Access po 365 dniach

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/new-access-package.png" alt-text="Strona Nowy pakiet dostępu" lightbox="images/new-access-package.png":::

    Aby uzyskać więcej informacji, [zobacz Tworzenie nowego pakietu dostępu](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Udostępnij łącze żądania dostępu do zasobów programu MSSP z zasobów klientów i AAD: Zarządzanie tożsamościami**

    Link Mój portal programu Access jest używany przez analityków SOC programu MSSP do żądania dostępu za pośrednictwem utworzonych pakietów dostępu. Link jest trwałe, co oznacza, że z czasem ten sam link może być używany dla nowych analityków. Żądanie analityka trafia do kolejki w celu zatwierdzenia przez osoby zatwierdzające analityka **MSSP**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/access-properties.png" alt-text="Strona Właściwości" lightbox="images/access-properties.png":::

    Link znajduje się na stronie przeglądu każdego pakietu dostępu.

## <a name="manage-access"></a>Zarządzanie dostępem

1. Przejrzyj i autoryzuj żądania dostępu w  mojego dostępu klienta i/lub MSSP.

    Żądania dostępu są zarządzane przez klienta Mój dostęp przez członków grupy Osoby zatwierdzające analityków MSSP.

    Aby to zrobić, uzyskaj dostęp do funkcji mój dostęp klienta, używając: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Przykład: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Zatwierdź lub odmów żądania **Zatwierdzenia** sekcji interfejsu użytkownika.

    W tym momencie dostęp analityka został inicjowania obsługi i każdy analityk powinien mieć dostęp do portalu Microsoft 365 Defender klienta:`https://security.microsoft.com/?tid=<CustomerTenantId>`

## <a name="related-topics"></a>Tematy pokrewne

- [Uzyskiwanie dostępu do portalu klientów programu MSSP](access-mssp-portal.md)
- [Konfigurowanie powiadomień alertów](configure-mssp-notifications.md)
- [Pobieranie alertów z dzierżawy klienta](fetch-alerts-mssp.md)
