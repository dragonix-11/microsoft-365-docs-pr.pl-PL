---
title: Uzyskiwanie dostępu do Microsoft 365 Defender API
description: Dowiedz się, jak uzyskać dostęp do interfejsów API Microsoft 365 Defender API
keywords: access, api, kontekst aplikacji, kontekst użytkownika, aplikacja aad, token dostępu
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
ms.openlocfilehash: a8406c0ec27c238615b25f60b988efbb50a8d7d7
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013702"
---
# <a name="access-the-microsoft-365-defender-apis"></a>Uzyskiwanie dostępu do Microsoft 365 Defender API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Microsoft 365 Defender udostępnia większość danych i akcji za pośrednictwem zestawu interfejsów API programistycznych. Te interfejsy API ułatwiają automatyzowanie przepływów pracy i pełne wykorzystanie Microsoft 365 Defender możliwości firmy.

Aby korzystać z interfejsów API, musisz wykonać następujące czynności:

- Tworzenie Azure Active Directory aplikacji
- Uzyskiwanie tokenu dostępu przy użyciu tej aplikacji
- Używanie tokenu w celu uzyskania dostępu do Microsoft 365 Defender API

> [!NOTE]
> Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji protokołu OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Po zakończeniu tych czynności możesz uzyskać dostęp do interfejsu API Microsoft 365 Defender przy użyciu określonego kontekstu.

## <a name="application-context-recommended"></a>Kontekst aplikacji (zalecane)

Użyj tego kontekstu w przypadku aplikacji uruchamianych bez zalogowania się użytkownika, takich jak usługi w tle lub daemony.

1. Utwórz Azure Active Directory sieci Web.
2. Przypisz odpowiednie uprawnienia do aplikacji.
3. Utwórz klucz dla aplikacji.
4. Uzyskaj token zabezpieczający przy użyciu aplikacji i jej klucza.
5. Użyj tokenu, aby uzyskać dostęp do Microsoft 365 Defender API.

Aby uzyskać więcej informacji, **[zobacz Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender dostępu bez użytkownika](api-create-app-web.md)**.

## <a name="user-context"></a>Kontekst użytkownika

W tym kontekście można wykonywać akcje w imieniu jednego użytkownika.

1. Utwórz natywny Azure Active Directory aplikacji.
2. Przypisywanie żądanych uprawnień do aplikacji.
3. Uzyskaj token zabezpieczający przy użyciu poświadczeń użytkownika dla aplikacji.
4. Użyj tokenu, aby uzyskać dostęp do Microsoft 365 Defender API.

Aby uzyskać więcej informacji, **[zobacz Tworzenie aplikacji w celu uzyskania Microsoft 365 Defender interfejsów API w imieniu użytkownika](api-create-app-user-context.md)**.

## <a name="partner-context"></a>Kontekst partnera

Użyj tego kontekstu, jeśli chcesz udostępnić aplikację wielu użytkownikom w wielu [dzierżawach](/azure/active-directory/develop/single-and-multi-tenant-apps).

1. Utwórz Azure Active Directory wielodostępną aplikację.
2. Przypisywanie żądanych uprawnień do aplikacji.
3. Uzyskaj [zgodę administratora](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) dla aplikacji od każdej dzierżawy.
4. Uzyskaj token zabezpieczający przy użyciu poświadczeń użytkownika na podstawie identyfikatora dzierżawy klienta.
5. Użyj tokenu, aby uzyskać dostęp do Microsoft 365 Defender API.

Aby uzyskać więcej informacji, **[zobacz Tworzenie aplikacji z dostępem partnera do Microsoft 365 Defender API](api-partner-access.md)**.

## <a name="related-articles"></a>Artykuły pokrewne

- [Microsoft 365 Defender interfejsów API — omówienie](api-overview.md)
- [Autoryzacja protokołu OAuth 2.0 do logowania użytkownika i dostępu do interfejsu API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Zarządzanie sekretami aplikacji serwera za pomocą magazynu kluczy platformy Azure](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Tworzenie aplikacji "Witaj świecie", która uzyskuje dostęp do Microsoft 365 API](api-hello-world.md)
