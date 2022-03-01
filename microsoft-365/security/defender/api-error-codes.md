---
title: Typowe Microsoft 365 Defender błędów interfejsu API usługi REST
description: Informacje na temat typowych kodów błędów Microsoft 365 Defender API REST
keywords: api, error, codes, common errors, Microsoft 365 Defender, api error codes
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
ms.openlocfilehash: 499ab1722b2754e893361784f7ff1ce257ceb58b
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013663"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>Typowe Microsoft 365 Defender błędów interfejsu API usługi REST

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Kody błędów mogą być zwracane przez operację na dowolnym z Microsoft 365 Defender API. Każda odpowiedź na błąd będzie zawierać komunikat o błędzie, który może pomóc rozwiązać problem. Kolumna komunikatu o błędzie w sekcji tabeli zawiera kilka przykładowych komunikatów. Zawartość rzeczywistych wiadomości będzie się różnić w zależności od czynników, które wyzwoliły odpowiedź. Zmienna zawartość jest wskazywana w tabeli nawiasami kątowym.

## <a name="error-codes"></a>Kody błędów

Kod błędu | Kod stanu HTTP | Komunikat
-|-|-
BadRequest | BadRequest (400) | Komunikat o błędzie "Ogólne żądanie złej obsługi".
ODataError | BadRequest (400) | Nieprawidłowe zapytanie URI danych \<the specific error is specified\>OData.
InvalidInput | BadRequest (400) | Nieprawidłowe dane wejściowe \<the invalid input\>.
InvalidRequestBody | BadRequest (400) | Nieprawidłowa treść żądania.
InvalidHashValue | BadRequest (400) | Wartość skrótu \<the invalid hash\> jest nieprawidłowa.
InvalidDomainName | BadRequest (400) | Nazwa domeny jest \<the invalid domain\> nieprawidłowa.
InvalidIpAddress | BadRequest (400) | \<the invalid IP\> Adres IP jest nieprawidłowy.
InvalidUrl | BadRequest (400) | Adres URL \<the invalid URL\> jest nieprawidłowy.
MaximumBatchSizeExceeded | BadRequest (400) | Przekroczono maksymalny rozmiar partii. Otrzymano: \<batch size received\>, dozwolone: {batch size allowed}.
MissingRequiredParameter | BadRequest (400) | Brakuje \<the missing parameter\> parametru.
OsPlatformNotSupported | BadRequest (400) | Ta akcja nie \<the client OS Platform\> jest obsługiwana przez platformę systemu operacyjnego.
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> jest obsługiwane w wersji klienta i \<supported client version\> wyżej.
Bez autoryzacji | Bez autoryzacji (401) | Bez autoryzacji <br /><br />*Uwaga: Zwykle jest to spowodowane nieprawidłowym lub wygasłym nagłówkiem autoryzacji.*
Dostęp zabroniony | Dostęp zabroniony (403) | Dostęp zabroniony <br /><br />*Uwaga: Prawidłowy token, ale niewystarczające uprawnienia do tej akcji*.
DisabledFeature | Dostęp zabroniony (403) | Funkcja dzierżawy nie jest włączona.
DisallowedOperation | Dostęp zabroniony (403) | \<the disallowed operation and the reason\>.
NotFound | Nie znaleziono (404) | Komunikat o błędzie Ogólne, nie znaleziono.
ResourceNotFound | Nie znaleziono (404) | Nie \<the requested resource\> znaleziono zasobu.
InternalServerError | Wewnętrzny błąd serwera (500) | *Uwaga: Brak komunikatu o błędzie, ponów operację lub skontaktuj się z firmą [Microsoft](../../admin/get-help-support.md) , jeśli nie zostanie rozwiązany*

## <a name="examples"></a>Przykłady

```json
{
    "error": {
        "code": "ResourceNotFound",
        "message": "Machine 123123123 was not found",
        "target": "43f4cb08-8fac-4b65-9db1-745c2ae65f3a"
    }
}
```

```json
{
    "error": {
        "code": "InvalidRequestBody",
        "message": "Request body is incorrect",
        "target": "1fa66c0f-18bd-4133-b378-36d76f3a2ba0"
    }
}
```

## <a name="body-parameters"></a>Parametry treści

> [!IMPORTANT]
> W parametrach treści jest zróżnicowa wielkość liter.

Błąd *InvalidRequestBody* lub *MissingRequiredParameters* może być spowodowany literówkami. Przejrzyj dokumentację interfejsu API i sprawdź, czy przesłane parametry pasują do odpowiedniego przykładu.

## <a name="tracking-id"></a>Identyfikator śledzenia

Każda odpowiedź o błędzie zawiera unikatowy parametr identyfikatora do śledzenia. Nazwa właściwości tego parametru jest *wartością docelową*. W przypadku skontaktowania się z nami w sprawie błędu dołączenie tego identyfikatora pomoże nam znaleźć główną przyczynę problemu.

## <a name="related-articles"></a>Artykuły pokrewne

- [Microsoft 365 Defender interfejsów API — omówienie](api-overview.md)
- [Obsługiwane Microsoft 365 Defender API](api-supported.md)
- [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md)
- [Informacje o limitach i licencjonowaniu interfejsu API](api-terms.md)
