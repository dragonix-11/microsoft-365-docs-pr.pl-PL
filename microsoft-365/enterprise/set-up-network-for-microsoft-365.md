---
title: Konfigurowanie sieci na potrzeby Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Znajdź linki do artykułów zawierających informacje ułatwiające skonfigurowanie sieci na potrzeby Microsoft 365, w tym omówienie łączności sieciowej i listę punktów końcowych.
ms.openlocfilehash: 8651fa23983cddf243081248bf1e03fb067232e2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092850"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Konfigurowanie sieci na potrzeby Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Ważną częścią dołączania Microsoft 365 jest zapewnienie, że połączenia sieciowe i internetowe są skonfigurowane pod kątem zoptymalizowanego dostępu. Konfigurowanie sieci lokalnej w celu uzyskiwania dostępu do globalnie rozproszonej chmury typu oprogramowanie jako usługa (SaaS) różni się od tradycyjnej sieci zoptymalizowanej pod kątem ruchu do lokalnych centrów danych i centralnego połączenia internetowego. 

Skorzystaj z tych artykułów, aby zrozumieć kluczowe różnice i zmodyfikować urządzenia brzegowe, komputery klienckie i sieć lokalną, aby uzyskać najlepszą wydajność dla użytkowników lokalnych.

## <a name="how-microsoft-365-networking-works"></a>Jak działa sieć Microsoft 365

Zapoznaj się z tymi artykułami, aby zapoznać się z omówieniem łączności dla Microsoft 365:

- [Łączność sieciowa na platformie Microsoft 365 — omówienie](microsoft-365-networking-overview.md)
- [Zasady dotyczące łączności sieciowej na platformie Microsoft 365](microsoft-365-network-connectivity-principles.md)
- [Ocena łączności sieciowej na platformie Microsoft 365](assessing-network-connectivity.md)

Aby uzyskać porady dotyczące zwiększania wydajności, zobacz [Planowanie sieci i dostrajanie wydajności dla Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Obsługa sieci Microsoft 365 jako dostawca sprzętu sieciowego

Jeśli jesteś dostawcą sprzętu sieciowego, dołącz do [Office 365 Networking Partner Program](microsoft-365-networking-partner-program.md). Zarejestruj się w programie, aby tworzyć zasady Office 365 łączności sieciowej w swoich produktach i rozwiązaniach. 

## <a name="office-365-endpoints"></a>Punkty końcowe usługi Office 365

Punkty końcowe to zestaw docelowych adresów IP, nazw domen DNS i adresów URL dla ruchu Office 365 w Internecie. 

Aby zoptymalizować wydajność Office 365 usług opartych na chmurze, niektóre punkty końcowe wymagają specjalnej obsługi przez przeglądarki klienckie i urządzenia w sieci brzegowej. Urządzenia te obejmują zapory, urządzenia SSL Break i Inspekcja i inspekcja pakietów oraz systemy zapobiegania utracie danych.

Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie punktami końcowymi Office 365](managing-office-365-endpoints.md).

Obecnie istnieje pięć różnych chmur Office 365. Ta tabela zawiera listę punktów końcowych dla każdego z nich.

| Punkty końcowe | Opis |
|:-------|:-----|
| [Punkty końcowe na całym świecie](urls-and-ip-address-ranges.md) | Punkty końcowe dla subskrypcji Office 365 na całym świecie, które obejmują Stany Zjednoczone Government Community Cloud (GCC). |
| [Punkty końcowe DoD rządu Stanów Zjednoczonych](microsoft-365-u-s-government-dod-endpoints.md) | Punkty końcowe subskrypcji departamentu obrony Stany Zjednoczone (DoD). |
| [Punkty końcowe środowisk GCC High rządu Stanów Zjednoczonych](microsoft-365-u-s-government-gcc-high-endpoints.md) | Punkty końcowe subskrypcji Stany Zjednoczone Government Community Cloud High (GCC High). |
| [Usługa Office 365 obsługiwana przez punkty końcowe 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Punkty końcowe dla Office 365 obsługiwane przez firmę 21Vianet, która została zaprojektowana w celu zaspokojenia potrzeb Office 365 w Chinach. |
|||

Aby zautomatyzować pobieranie najnowszej listy punktów końcowych dla chmury Office 365, zobacz [Office 365 adres IP i adres URL usługi sieci Web](microsoft-365-ip-web-service.md).

Dodatkowe punkty końcowe można znaleźć w następujących artykułach:

- [Dodatkowe punkty końcowe, które nie są dostępne w usłudze sieci Web](additional-office365-ip-addresses-and-urls.md)
- [Żądania sieciowe w Office 2016 dla komputerów Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Dodatkowe tematy dotyczące sieci Microsoft 365

Zapoznaj się z tymi artykułami, aby zapoznać się ze specjalistycznymi tematami dotyczącymi sieci Microsoft 365:

- [Sieci dostarczania zawartości](content-delivery-networks.md)
- [Obsługa protokołu IPv6 w usługach Office 365](ipv6-support.md)
- [Obsługa translatora NAT za pomocą usługi Office 365](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>Usługa ExpressRoute dla Microsoft 365

Zapoznaj się z tymi artykułami, aby uzyskać informacje na temat korzystania z usługi ExpressRoute dla ruchu Office 365:

- [Usługa Azure ExpressRoute dla Office 365](azure-expressroute.md)
- [Implementowanie usługi ExpressRoute dla Office 365](implementing-expressroute.md)
- [Planowanie sieci za pomocą usługi ExpressRoute dla usługi Office 365](network-planning-with-expressroute.md)
- [Routing przy użyciu usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)
