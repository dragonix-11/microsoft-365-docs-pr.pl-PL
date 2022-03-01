---
title: Krok nr 2. Zapewnianie dostępu zdalnego do aplikacji i usług lokalnych
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Zapewnij pracownikom zdalnym dostęp do zasobów lokalnych, optymalizując dostęp do Microsoft 365 w chmurze.
ms.openlocfilehash: 11fb3e37efe67103780fc4d234837da3bc15d97f
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014844"
---
# <a name="step-2-provide-remote-access-to-on-premises-apps-and-services"></a>Krok nr 2. Zapewnianie dostępu zdalnego do aplikacji i usług lokalnych

Jeśli Twoja organizacja korzysta z rozwiązania VPN dostępnego zdalnie, zazwyczaj z serwerami VPN na brzegach Twojej sieci i klientami VPN zainstalowanymi na urządzeniach użytkowników, Twoi użytkownicy mogą korzystać z połączeń VPN w celu uzyskiwania dostępu do lokalnych aplikacji i serwerów. Może być jednak konieczne zoptymalizowanie ruchu w celu Microsoft 365 usług opartych na chmurze.

Jeśli twoi użytkownicy nie korzystają z rozwiązania VPN, możesz korzystać z serwera proxy aplikacji usługi Azure Active Directory (Azure AD) i sieci VPN usługi Azure Point-to-Site (P2S) w celu zapewnienia dostępu w zależności od tego, czy wszystkie Twoje aplikacje są oparte na sieci Web.

Oto podstawowe konfiguracje dostępu zdalnego:

- Używasz już rozwiązania VPN do dostępu zdalnego.
- Nie korzystasz z rozwiązania VPN do dostępu zdalnego i chcesz, aby Twoi pracownicy zdalni korzystali ze swoich komputerów osobistych.
- Nie używasz rozwiązania VPN z dostępem zdalnym, masz tożsamość hybrydową i potrzebujesz dostępu zdalnego tylko do lokalnych aplikacji internetowych.
- Nie korzystasz z rozwiązania VPN do dostępu zdalnego i potrzebujesz dostępu do aplikacji lokalnych, z których niektóre nie są oparte na sieci Web.

Zobacz ten schemat blokowy, aby uzyskać informacje o opcjach konfiguracji dostępu zdalnego omówinych w tym artykule.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png" alt-text="Schemat blokowy konfiguracji dostępu zdalnego." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png":::

W przypadku połączeń dostępu zdalnego możesz również połączyć użytkowników [](https://support.microsoft.com/help/4028379/windows-10-how-to-use-remote-desktop) z komputerem lokalnym za pomocą pulpitu zdalnego. Na przykład pracownik zdalny może używać pulpitu zdalnego do łączenia się z komputerem w swoim biurze ze swojego Windows, iOS lub Android. Po najechu na połączenie zdalne mogą oni z niego korzystać tak, jakby byli przed nim.

## <a name="optimize-performance-for-remote-access-vpn-clients-to-microsoft-365-cloud-services"></a>Optymalizowanie wydajności pod kątem klientów sieci VPN z dostępem zdalnym Microsoft 365 usług w chmurze

Jeśli twoi pracownicy zdalni uzyskają dostęp zdalny do sieci organizacji za pomocą tradycyjnego klienta VPN, upewnij się, że klient sieci VPN podzielił wsparcie techniczne.

Bez rozdzielania rozdzielania cały ruch w pracy zdalnej jest przesyłany przez połączenie VPN, gdzie musi być przesyłany dalej do urządzeń brzegowych organizacji, przetwarzany, a następnie wysyłany w Internecie.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png" alt-text="Ruch sieciowy z klientów sieci VPN bez konieczności wytłaniania." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png":::

Microsoft 365 ruchu musi odbywać się trasą pośrednią przez Twoją organizację, która może być przesyłana dalej do punktu wejścia sieciowego firmy Microsoft, daleko od fizycznej lokalizacji klienta VPN. Ta ścieżka pośrednia powoduje dodanie opóźnienia do ruchu sieciowego i zmniejszenie ogólnej wydajności.

Dzięki rozdzielaniu rozdzielanym możesz skonfigurować klienta SIECI VPN tak, aby określone typy ruchu nie były wysyłane przez połączenie VPN do sieci organizacji.

Aby zoptymalizować dostęp do Microsoft 365 w chmurze, skonfiguruj rozdzielanych klientów SIECI VPN w celu wykluczenia ruchu w kategorii Optymalizuj Microsoft 365  punktów końcowych przez połączenie VPN. Aby uzyskać więcej informacji, [zobacz Office 365 kategorii punktów końcowych](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). Zobacz [tę listę](../enterprise/urls-and-ip-address-ranges.md) punktów końcowych kategorii Optymalizowanie.

Oto wynikowy przepływ ruchu, w którym większość ruchu do połączeń Microsoft 365 w chmurze pomija połączenie VPN.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png" alt-text="Ruch sieciowy z klientów sieci VPN z korkami." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png":::

Dzięki temu klient VPN może wysyłać i odbierać ważne wiadomości Microsoft 365 ruchu związanego z usługami w chmurze bezpośrednio przez Internet i do najbliższego punktu wejścia do sieci firmy Microsoft.

Aby uzyskać więcej informacji i wskazówki, zobacz [Optymalizowanie Office 365 sieci zdalnej](../enterprise/microsoft-365-vpn-split-tunnel.md) dla użytkowników zdalnych korzystających z rozdzielania sieci VPN.

## <a name="deploy-remote-access-when-all-your-apps-are-web-apps-and-you-have-hybrid-identity"></a>Wdrażanie dostępu zdalnego, gdy wszystkie aplikacje są aplikacjami sieci Web i masz tożsamość hybrydową

Jeśli Twoi pracownicy zdalni nie używają tradycyjnego klienta VPN, a Twoje lokalne konta użytkowników i grupy są synchronizowane z usługą Azure AD, możesz użyć serwera proxy aplikacji Azure AD w celu zapewnienia bezpiecznego dostępu zdalnego aplikacjom internetowym hostowanych na serwerach lokalnych. Aplikacje oparte na sieci Web obejmują SharePoint Serwera, Outlook sieci Web lub inne aplikacje biznesowe oparte na sieci Web.

Poniżej znajdują się składniki serwera proxy aplikacji Azure AD.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png" alt-text="Składniki serwera proxy aplikacji Azure AD." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png":::

Aby uzyskać więcej informacji, zobacz omówienie [serwera proxy aplikacji Azure AD](/azure/active-directory/manage-apps/application-proxy).

> [!NOTE]
> Serwer proxy aplikacji Azure AD nie jest uwzględniony w Microsoft 365 subskrypcji usługi Azure AD. Za użycie należy zapłacić za pomocą osobnej subskrypcji platformy Azure.

## <a name="deploy-remote-access-when-not-all-your-apps-are-web-apps"></a>Wdrażanie dostępu zdalnego, gdy nie wszystkie aplikacje są aplikacjami sieci Web

Jeśli Twoi pracownicy zdalni nie korzystają z tradycyjnego klienta VPN i masz aplikacje, które nie są oparte na sieci Web, możesz korzystać z sieci VPN typu "punkt-do witryny" platformy Azure.

Połączenie VPN P2S tworzy bezpieczne połączenie z urządzeniem pracownika zdalnego do twojej sieci organizacji za pośrednictwem sieci wirtualnej Azure.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png" alt-text="Składniki usługi Azure P2S VPN." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png":::

Aby uzyskać więcej informacji, zobacz omówienie [połączenia VPN w p2S](/azure/vpn-gateway/point-to-site-about).

> [!NOTE]
> Usługa Azure P2S VPN nie jest zawarta w Microsoft 365 subskrypcji usługi. Za użycie należy zapłacić za pomocą osobnej subskrypcji platformy Azure.

## <a name="deploy-windows-365-to-provide-remote-access-for-remote-workers-using-personal-devices"></a>Wdrażanie usługi Windows 365 w celu zapewnienia dostępu zdalnego pracownikom zdalnym przy użyciu urządzeń osobistych

Aby wspierać pracowników zdalnych, którzy mogą korzystać tylko z osobistych i niewykonanych urządzeń, użyj usługi Windows 365 do tworzenia i przydzielania pulpitów wirtualnych do użytku z domu użytkownikom. W przypadku lokalnego połączenia sieciowego (OPNC) komputery Windows 365 w chmurze mogą działać tak samo jak komputery połączone z siecią organizacji.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-365.png" alt-text="Składniki Windows 365." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-365.png":::

Aby uzyskać więcej informacji, zobacz [omówienie Windows 365](/windows-365/overview).

> [!NOTE]
> Windows 365 nie jest uwzględnione w Microsoft 365 subskrypcji usługi. Za użycie należy zapłacić za pomocą osobnej subskrypcji.

## <a name="protect-your-remote-desktop-services-connections-with-the-remote-desktop-services-gateway"></a>Ochrona połączeń usług pulpitu zdalnego za pomocą bramy usług pulpitu zdalnego

Jeśli używasz usług pulpitu zdalnego (RDS) w celu umożliwienia pracownikom łączenia się z komputerami opartymi na Windows w Twojej sieci lokalnej, użyj bramy usług Pulpit zdalny Microsoft Services w sieci brzegowej. Brama szyfruje ruch za pomocą zabezpieczeń TLS (Transport Layer Security) i zapobiega bezpośredniemu dostępowi rds na komputerze lokalnym hostującym usługi RDS.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png" alt-text="Połączenia usług pulpitu zdalnego z bramą usług pulpitu zdalnego." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png":::

Aby [uzyskać więcej informacji,](https://www.microsoft.com/security/blog/2020/04/16/security-guidance-remote-desktop-adoption/) zobacz ten artykuł.

## <a name="admin-technical-resources-for-remote-access"></a>Zasoby techniczne dla administratorów dotyczące dostępu zdalnego

- [Jak szybko zoptymalizować ruch Office 365 dla zdalnych pracowników & zmniejszenie obciążenia infrastruktury](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571)
- [Optymalizowanie Office 365 dla użytkowników zdalnych przy użyciu rozdzielania sieci VPN](../enterprise/microsoft-365-vpn-split-tunnel.md)

## <a name="results-of-step-2"></a>Wyniki kroku 2

Po wdrożeniu rozwiązania dostępu zdalnego dla pracowników zdalnych:

| Konfiguracja dostępu zdalnego | Wyniki |
|:-------|:-----|
| Połączenie VPN z dostępem zdalnym jest już dostępne | Skonfigurowano klienta sieci VPN z dostępem zdalnym do rozdzielania i dla kategorii Optymalizuj Microsoft 365 końcowych. |
| Nie ma rozwiązania VPN do dostępu zdalnego i potrzebujesz dostępu zdalnego tylko do lokalnych aplikacji internetowych | Skonfigurowano serwer proxy aplikacji Azure. |
| Nie ma rozwiązania VPN do dostępu zdalnego i potrzebujesz dostępu do aplikacji lokalnych, z których niektóre nie są oparte na sieci Web | Skonfigurowano sieć VPN azure P2S. |
| Pracownicy zdalni używający swoich urządzeń osobistych z domu | Skonfigurowano usługę Windows 365. |
| Pracownicy zdalni korzystający z połączeń RDS z systemami lokalnymi | W sieci brzegowej wdrożono bramę usług pulpitu zdalnego. |
|||

## <a name="next-step"></a>Następny krok

[![Krok 3. Wdrażanie Microsoft 365 usług zabezpieczeń i zgodności.](../media/empower-people-to-work-remotely/remote-workers-step-grid-3.png)](empower-people-to-work-remotely-security-compliance.md)

Przejdź do [kroku 3, aby](empower-people-to-work-remotely-security-compliance.md) wdrożyć Microsoft 365 zabezpieczeń i zgodności w celu ochrony aplikacji, danych i urządzeń.
