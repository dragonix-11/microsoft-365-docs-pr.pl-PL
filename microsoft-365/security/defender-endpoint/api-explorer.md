---
title: Eksplorator interfejsu API w Ochrona punktu końcowego w usłudze Microsoft Defender
ms.reviewer: ''
description: Tworzenie i wykonywanie zapytań interfejsu API, testowanie i wysyłanie żądań dla dowolnego dostępnego interfejsu API za pomocą Eksploratora interfejsu API
keywords: api, explorer, send, request, get, post,
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
ms.topic: conceptual
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 5d3d81f878e201cd00e7286bd045caa5fb3e1625
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486800"
---
# <a name="api-explorer"></a>Eksplorator interfejsu API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

Eksplorator interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender to narzędzie, które ułatwia interaktywne eksplorowanie różnych interfejsów API usługi Defender for Endpoint.

Eksplorator interfejsu API ułatwia tworzenie i wykonywanie zapytań interfejsu API, testowanie i wysyłanie żądań dla dowolnego dostępnego punktu końcowego interfejsu API usługi Defender for Endpoint. Użyj Eksploratora interfejsu API, aby wykonywać akcje lub znajdować dane, które mogą nie być jeszcze dostępne za pośrednictwem interfejsu użytkownika.

Narzędzie jest przydatne podczas tworzenia aplikacji. Umożliwia wykonywanie zapytań interfejsu API, które respektują ustawienia dostępu użytkowników, co zmniejsza konieczność generowania tokenów dostępu.

Możesz również użyć narzędzia do eksplorowania galerii przykładowych zapytań, kopiowania przykładów kodu wynikowego i generowania informacji debugowania.

Za pomocą Eksploratora interfejsu API możesz:

- Uruchom żądania dla dowolnej metody i zobacz odpowiedzi w czasie rzeczywistym.
- Szybko przejrzyj przykłady interfejsu API i dowiedz się, jakie parametry obsługują.
- Łatwe wykonywanie wywołań interfejsu API; nie trzeba uwierzytelniać się poza logowaniem do portalu zarządzania.

## <a name="access-api-explorer"></a>Eksplorator interfejsu API dostępu

Z menu nawigacji po lewej stronie wybierz pozycję **Partnerzy &** **[Eksplorator interfejsów API](https://security.microsoft.com/interoperability/api-explorer)** interfejsów \> API.

## <a name="supported-apis"></a>Obsługiwane interfejsy API

Eksplorator interfejsów API obsługuje wszystkie interfejsy API oferowane przez usługę Defender for Endpoint.

Lista obsługiwanych interfejsów API jest dostępna w [dokumentacji interfejsów API](apis-intro.md).

## <a name="get-started-with-the-api-explorer"></a>Wprowadzenie do Eksploratora interfejsu API

1. W okienku po lewej stronie znajduje się lista przykładowych żądań, których można użyć.
2. Postępuj zgodnie z linkami i kliknij pozycję **Uruchom zapytanie**.

Niektóre przykłady mogą wymagać określenia parametru w adresie URL, na przykład {machine- ID}.

## <a name="faq"></a>Często zadawane pytania

**Czy muszę mieć token interfejsu API, aby korzystać z Eksploratora interfejsu API?** <br>
Poświadczenia umożliwiające dostęp do interfejsu API nie są potrzebne. Eksplorator interfejsu API używa tokenu portalu zarządzania punktami końcowymi usługi Defender za każdym razem, gdy wysyła żądanie.

Poświadczenie uwierzytelniania zalogowanego użytkownika służy do sprawdzania, czy Eksplorator interfejsu API ma autoryzację dostępu do danych w Twoim imieniu.

Określone żądania interfejsu API są ograniczone w zależności od uprawnień RBAC. Na przykład żądanie "Prześlij wskaźnik" jest ograniczone do roli administratora zabezpieczeń.
