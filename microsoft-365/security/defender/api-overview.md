---
title: Omówienie Microsoft 365 Defender API
description: Informacje o dostępnych interfejsach API w programie Microsoft 365 Defender
keywords: api, api, overview, incident, incidents, threat hunting, microsoft 365 defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: ec4a497fd0ee428fbc664ae064ec95f74fcdce85
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010392"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>Omówienie Microsoft 365 Defender API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Microsoft 365 Defender jest zbudowana na platformie gotowej do integracji.

Użyj interfejsów API Microsoft 365 Defender, aby zautomatyzować przepływy pracy na podstawie udostępnionych zdarzeń i zaawansowanych tabel chłoń.

- **[Kolejka połączonych zdarzeń](api-incident.md)** — skoncentruj się na tym, co najważniejsze, grupując pełny zakres ataków i wszystkie zasoby, na które wpływa ten wpływ, przy użyciu interfejsu API zdarzenia.

- **[Poszukiwania zagrożeń między](api-advanced-hunting.md)** produktami — korzystaj z wiedzy organizacyjnej zespołu zabezpieczeń, aby poszukać znaków naruszenia bezpieczeństwa, tworząc własne zapytania niestandardowe w celu przesieszczenia nieprzetworzonych danych zebranych w wielu produktach ochrony.

- **[Interfejs API przesyłania strumieniowego zdarzeń](streaming-api.md)** — wysyłaj zdarzenia i alerty w czasie rzeczywistym w pojedynczym strumieniu danych w momencie ich wystąpienia.

Wraz z tymi Microsoft 365 Defender API, wszystkie nasze inne produkty zabezpieczające udostępniają dodatkowe interfejsy [API](api-articles.md), aby ułatwić Ci skorzystanie z ich unikatowych możliwości.

> [!NOTE]
> Przejście na ujednolicony portal nie powinno mieć wpływu na pulpity nawigacyjne usługi PowerBi oparte na interfejsach API programu Microsoft Defender dla punktów końcowych. Możesz nadal pracować z istniejącymi interfejsami API niezależnie od przejścia portalu interakcyjnego.

## <a name="learn-more"></a>Dowiedz się więcej

| **Opis sposobu uzyskiwania dostępu do interfejsów API** |
|-|
| [Informacje o przydziałach i licencjonowaniu interfejsu API](api-terms.md) |
| [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md) |
| **Tworzenie aplikacji** |
| [Tworzenie aplikacji "Witaj świecie"](api-hello-world.md) |
| [Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender interfejsów API w imieniu użytkownika](api-create-app-user-context.md) |
| [Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender dostępu bez użytkownika](api-create-app-web.md) |
| [Tworzenie aplikacji z dostępem partnera z wieloma dzierżawami do Microsoft 365 Defender API](api-partner-access.md) |
| **Rozwiązywanie problemów i obsługa aplikacji** |
| [Opis kodów błędów interfejsu API](api-error-codes.md) |
| [Zarządzanie tajemnicami w aplikacjach za pomocą magazynu kluczy platformy Azure](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Implementowanie autoryzacji protokołu OAuth 2.0 do logowania użytkownika](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
