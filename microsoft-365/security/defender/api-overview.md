---
title: Omówienie interfejsów API usługi Microsoft 365 Defender
description: Dowiedz się więcej o dostępnych interfejsach API w Microsoft 365 Defender
keywords: api, apis, overview, incident, incidents, threat hunting, microsoft 365 defender
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
ms.openlocfilehash: c2a340c2ad147e32082a50e326a2e0c7e11718c2
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739610"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>Omówienie interfejsów API usługi Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Microsoft 365 Defender jest oparta na platformie gotowej do integracji.

Interfejsy API Microsoft 365 Defender umożliwiają automatyzowanie przepływów pracy na podstawie udostępnionego zdarzenia i zaawansowanych tabel wyszukiwania zagrożeń.

- **[Kolejka połączonych zdarzeń](api-incident.md)** — skoncentruj się na tym, co jest krytyczne, grupując pełny zakres ataków i wszystkie zasoby, których dotyczy problem, w ramach interfejsu API zdarzeń.

- **[Wyszukiwanie zagrożeń między produktami](api-advanced-hunting.md)** — wykorzystaj wiedzę organizacyjną zespołu ds. zabezpieczeń, aby wyszukiwać oznaki naruszenia zabezpieczeń, tworząc własne niestandardowe zapytania służące do przesiewania nieprzetworzonych danych zebranych w wielu produktach ochrony.

- **[Interfejs API przesyłania strumieniowego zdarzeń](streaming-api.md)** — wysyła zdarzenia i alerty w czasie rzeczywistym w pojedynczym strumieniu danych w miarę ich występowania.

Wraz z tymi interfejsami API specyficznymi dla Microsoft 365 Defender każdy z naszych innych produktów zabezpieczeń udostępnia [dodatkowe interfejsy API](api-articles.md), aby ułatwić korzystanie z ich unikatowych możliwości.

> [!NOTE]
> Przejście do ujednoliconego portalu nie powinno mieć wpływu na pulpity nawigacyjne usługi PowerBi oparte na interfejsach API Ochrona punktu końcowego w usłudze Microsoft Defender. Możesz kontynuować pracę z istniejącymi interfejsami API niezależnie od interaktywnego przejścia do portalu.

Obejrzyj ten krótki film wideo, aby dowiedzieć się, jak za pomocą Microsoft 365 Defender zautomatyzować przepływy pracy i zintegrować aplikacje.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4d73M?rel=0]

## <a name="learn-more"></a>Dowiedz się więcej

| **Informacje na temat uzyskiwania dostępu do interfejsów API** |
|-|
| [Dowiedz się więcej o limitach przydziału i licencjonowaniu interfejsu API](api-terms.md) |
| [Uzyskiwanie dostępu do interfejsów API Microsoft 365 Defender](api-access.md) |
| **Tworzenie aplikacji** |
| [Tworzenie aplikacji "Hello world"](api-hello-world.md) |
| [Tworzenie aplikacji w celu uzyskania dostępu do interfejsów API Microsoft 365 Defender w imieniu użytkownika](api-create-app-user-context.md) |
| [Tworzenie aplikacji w celu uzyskania dostępu do Microsoft 365 Defender bez użytkownika](api-create-app-web.md) |
| [Tworzenie aplikacji z dostępem partnerów z wieloma dzierżawami do interfejsów API Microsoft 365 Defender](api-partner-access.md) |
| **Rozwiązywanie problemów i obsługa aplikacji** |
| [Omówienie kodów błędów interfejsu API](api-error-codes.md) |
| [Zarządzanie wpisami tajnymi w aplikacjach przy użyciu usługi Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Implementowanie autoryzacji protokołu OAuth 2.0 na potrzeby logowania użytkownika](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
