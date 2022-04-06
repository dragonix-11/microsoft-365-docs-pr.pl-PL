---
title: Konfigurowanie sieci pod Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: landing-page
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: Znajdź linki do artykułów z informacjami pomocnych w skonfigurowaniu sieci na Microsoft 365, w tym omówienie łączności sieciowej i listę punktów końcowych.
ms.openlocfilehash: c6dbc4362648b3695c23f363c0e6925ead97bacb
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680847"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Konfigurowanie sieci pod Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Ważną częścią dołączania do Microsoft 365 jest skonfigurowanie połączeń sieciowych i internetowych pod kątem zoptymalizowanego dostępu. Konfigurowanie sieci lokalnej w celu uzyskiwania dostępu do globalnie rozproszonej chmury typu Oprogramowanie jako usługa (SaaS, Software-as-a-Service) różni się od tradycyjnej sieci zoptymalizowanej pod kątem ruchu do lokalnych centrów danych i centralnego połączenia internetowego. 

Skorzystaj z tych artykułów, aby zrozumieć najważniejsze różnice i zmodyfikować urządzenia brzegowe, komputery klienckie i sieć lokalną, aby uzyskać najlepszą wydajność dla użytkowników lokalnych.

## <a name="how-microsoft-365-networking-works"></a>Jak działa Microsoft 365 sieci

W tych artykułach o przeglądzie łączności w Microsoft 365:

- [Microsoft 365 łączności sieciowej](microsoft-365-networking-overview.md)
- [Microsoft 365 dotyczących łączności sieciowej](microsoft-365-network-connectivity-principles.md)
- [Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)

Aby uzyskać porady dotyczące zwiększania wydajności, zobacz [Planowanie sieci i dostosowywanie wydajności w celu zwiększenia Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Obsługa Microsoft 365 sieci jako dostawca sprzętu sieciowego

Jeśli jesteś dostawcą sprzętu sieciowego, dołącz do [Office 365 Networking Partner Program.](microsoft-365-networking-partner-program.md) Zarejestruj się w programie, aby Office 365 zasady łączności sieciowej w swoich produktach i rozwiązaniach. 

## <a name="office-365-endpoints"></a>Office 365 punktami końcowymi

Punkty końcowe to zestaw docelowych adresów IP, nazw domen DNS i adresów URL dla Office 365 ruchu w Internecie. 

Aby zoptymalizować wydajność Office 365 usług opartych na chmurze, niektóre punkty końcowe wymagają specjalnej obsługi przez przeglądarki klienckie i urządzenia w Twojej sieci brzegowej. Do tych urządzeń należą zapory, urządzenia do obsługi przerw SSL i inspekcji pakietów oraz systemy ochrony przed utratą danych.

Aby [uzyskać szczegółowe Office 365 zobacz Zarządzanie punktami](managing-office-365-endpoints.md) końcowymi usługi.

Obecnie istnieje pięć różnych Office 365 chmur. W poniższej tabeli znajdziesz listę punktów końcowych dla każdego z nich.

| Punkty końcowe | Opis |
|:-------|:-----|
| [Punkty końcowe na całym świecie](urls-and-ip-address-ranges.md) | Punkty końcowe dla subskrypcji usługi Office 365 na świecie, które obejmują stany zjednoczone Government Community Cloud (GCC). |
| [Punkty końcowe amerykańskiego dod](microsoft-365-u-s-government-dod-endpoints.md) | Punkty końcowe subskrypcji DoD (United States Department of Defense). |
| [Rząd Stanów Zjednoczonych GCC punkty końcowe o wysokiej jakości](microsoft-365-u-s-government-gcc-high-endpoints.md) | Punkty końcowe dla subskrypcji High (Government Community Cloud High) dla Stanów Zjednoczonych (GCC High). |
| [Office 365 obsługiwane przez punkty końcowe usługi 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Punkty końcowe dla usługi Office 365 obsługiwanej przez firmę 21Vianet, która została zaprojektowana w celu zaspokojenia potrzeb firmy Office 365 w Chinach. |
|||

Aby zautomatyzować uzyskiwanie najnowszej listy punktów końcowych dla chmury usługi Office 365, zobacz Office 365 [adresu IP i usługi sieci Web adresu URL](microsoft-365-ip-web-service.md).

Aby uzyskać dodatkowe punkty końcowe, zobacz następujące artykuły:

- [Dodatkowe punkty końcowe, które nie są dostępne w usłudze sieci Web](additional-office365-ip-addresses-and-urls.md)
- [Żądania sieciowe w programie Office 2016 dla komputerów Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Dodatkowe tematy dotyczące sieci Microsoft 365 sieci

W tych artykułach znajdziesz tematy specjalistyczne w Microsoft 365 sieci:

- [Sieci dostarczania zawartości](content-delivery-networks.md)
- [Obsługa protokołu IPv6 w Office 365 usługach internetowych](ipv6-support.md)
- [Obsługa NAT z Office 365](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute dla Microsoft 365

Zapoznaj się z tymi artykułami, aby uzyskać informacje na temat użycia Office 365 ExpressRoute:

- [Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
- [Implementowanie expressroute dla Office 365](implementing-expressroute.md)
- [Planowanie sieci z usługą ExpressRoute dla sieci Office 365](network-planning-with-expressroute.md)
- [Routing za pomocą usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)
