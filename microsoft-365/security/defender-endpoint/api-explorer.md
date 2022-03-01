---
title: Eksplorator interfejsu API w programie Microsoft Defender for Endpoint
ms.reviewer: ''
description: Używanie Eksploratora API do konstruowania i używania zapytań interfejsu API, testowania i wysyłania żądań dowolnego dostępnego interfejsu API
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
ms.openlocfilehash: 6e7d0e5927a85f2f3952221c294fe2387c268546
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996248"
---
# <a name="api-explorer"></a>Eksplorator interfejsu API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint API Explorer to narzędzie, które ułatwia interakcyjne eksplorowanie różnych interfejsów API usługi Defender dla punktu końcowego.

Eksplorator API ułatwia konstruowanie i tworzenie zapytań interfejsu API, testowanie i wysyłanie żądań dowolnego dostępnego punktu końcowego interfejsu API usługi Defender. Za pomocą Eksploratora API możesz podjąć działania lub znaleźć dane, które mogą jeszcze nie być dostępne za pośrednictwem interfejsu użytkownika.

To narzędzie jest przydatne podczas tworzenia aplikacji. Pozwala on na wykonywanie zapytań interfejsu API z przestrzeganiem ustawień dostępu użytkownika, co ogranicza konieczność generowania tokenów dostępu.

Za pomocą tego narzędzia możesz również eksplorować galerię przykładowych zapytań, kopiować przykłady kodów wyników i generować informacje o debugowaniu.

Eksplorator interfejsu API umożliwia:

- Uruchamianie żądań dowolnej metody i wyświetlanie odpowiedzi w czasie rzeczywistym
- Szybkie przeglądanie przykładów interfejsu API i dowiedz się, jakie parametry obsługują
- Łatwe nakieruj interfejs API na połączenia; nie trzeba logować się poza portalem zarządzania

## <a name="access-api-explorer"></a>Eksplorator interfejsu API programu Access

Z menu nawigacji po lewej stronie wybierz pozycję **Partnerzy & Eksploratora interfejsów** \> **API INTERFEJSÓW API**.

## <a name="supported-apis"></a>Obsługiwane interfejsy API

Eksplorator interfejsów API obsługuje wszystkie interfejsy API oferowane przez usługę Defender for Endpoint.

Lista obsługiwanych interfejsów API jest dostępna w [dokumentacji interfejsów API](apis-intro.md).

## <a name="get-started-with-the-api-explorer"></a>Wprowadzenie do Eksploratora interfejsu API

1. W okienku po lewej stronie znajduje się lista przykładowych żądań, których możesz użyć.
2. Postępuj zgodnie z linkami i kliknij **pozycję Uruchom zapytanie**.

Niektóre próbki mogą wymagać określenia parametru w adresie URL, na przykład {machine-ID}.

## <a name="faq"></a>Często zadawane pytania

**Czy do korzystania z Eksploratora API muszę mieć token API?** <br>
Poświadczenia dostępu do interfejsu API nie są potrzebne. Eksplorator interfejsu API używa tokenu portalu zarządzania punktami końcowymi usługi Defender zawsze, gdy zażąda.

Poświadczenia uwierzytelniania zalogowanego użytkownika służą do sprawdzania, czy Eksplorator interfejsu API jest autoryzowany do uzyskiwania dostępu do danych w Twoim imieniu.

Określone żądania interfejsu API są ograniczone w zależności od Twoich uprawnień RBAC. Na przykład żądanie "Wskaźnik Prześlij" jest ograniczone do roli administratora zabezpieczeń.
