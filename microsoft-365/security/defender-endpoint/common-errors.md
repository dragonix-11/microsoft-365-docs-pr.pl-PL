---
title: Typowe błędy interfejsu API programu Microsoft Defender dla punktów końcowych
description: Lista typowych błędów interfejsu API programu Microsoft Defender dla punktów końcowych z opisami.
keywords: Interfejsy API, interfejsy API programu Microsoft Defender dla punktów końcowych, błędy, rozwiązywanie problemów
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: d960091409a71fd23e52a098ae3d8164c7df5aef
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996238"
---
# <a name="common-rest-api-error-codes"></a>Typowe kody błędów interfejsu API usługi REST



[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


* Kody błędów wymienione w poniższej tabeli mogą być zwracane przez operację na dowolnym interfejsie API programu Microsoft Defender dla punktów końcowych.
* Oprócz kodu błędu każda odpowiedź na błąd zawiera komunikat o błędzie, który może pomóc rozwiązać problem.
* Wiadomość jest tekstem bezpłatnym, który można zmienić.
* W dolnej części strony znajdują się przykłady odpowiedzi.

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kod błędu|Kod stanu HTTP|Komunikat
---|---|---
BadRequest|BadRequest (400)|Komunikat o błędzie "Ogólne żądanie złej obsługi".
ODataError|BadRequest (400)|Nieprawidłowe zapytanie URI OData (określono konkretny błąd).
InvalidInput|BadRequest (400)|Nieprawidłowe dane wejściowe {the invalid input}.
InvalidRequestBody|BadRequest (400)|Nieprawidłowa treść żądania.
InvalidHashValue|BadRequest (400)|Wartość skrótu {the invalid hash} jest nieprawidłowa.
InvalidDomainName|BadRequest (400)|Nazwa domeny {the invalid domain} jest nieprawidłowa.
InvalidIpAddress|BadRequest (400)|Adres IP {the invalid IP} jest nieprawidłowy.
InvalidUrl|BadRequest (400)|Adres URL {the invalid URL} jest nieprawidłowy.
MaximumBatchSizeExceeded|BadRequest (400)|Przekroczono maksymalny rozmiar partii. Otrzymano: {batch size received}, allowed: {batch size allowed}.
MissingRequiredParameter|BadRequest (400)|Brakuje parametru {the missing parameter}.
OsPlatformNotSupported|BadRequest (400)|Ta akcja nie jest obsługiwana przez platformę systemu operacyjnego {klienta platformy systemu operacyjnego}.
ClientVersionNotSupported|BadRequest (400)|Żądana akcja} jest obsługiwana w wersji klienta {supported client version} i powyższych.
Bez autoryzacji|Bez autoryzacji (401)|Nagłówek autoryzacji bez autoryzacji (nieprawidłowy lub wygasły).
Dostęp zabroniony|Dostęp zabroniony (403)|Dostęp zabroniony (ważny token, ale niewystarczające uprawnienie do akcji).
DisabledFeature|Dostęp zabroniony (403)|Funkcja dzierżawy nie jest włączona.
DisallowedOperation|Dostęp zabroniony (403)|{the disalloweed operation and the reason}.
NotFound|Nie znaleziono (404)|Komunikat o błędzie Ogólne, nie znaleziono.
ResourceNotFound|Nie znaleziono (404)|Nie znaleziono zasobu {żądanego zasobu}.
InternalServerError|Wewnętrzny błąd serwera (500)|(Brak komunikatu o błędzie, ponów operację)
TooManyRequests|Zbyt wiele żądań (429)|Odpowiedź będzie oznaczać osiągnięcie limitu przydziału zarówno przez liczbę żądań, jak i przez procesor.

## <a name="body-parameters-are-case-sensitive"></a>W parametrach treści jest zróżnicowana wielkość liter

W parametrach treści w tej chwili jest w nich wróżniana wielkość liter.

Jeśli występują **błędy InvalidRequestBody** lub **MissingRequiredParameters** , może to być spowodowane przez nieprawidłową literę parametru lub małe litery.

Przejrzyj stronę dokumentacji interfejsu API i sprawdź, czy przesłane parametry są zgodne z odpowiednim przykładem.

## <a name="correlation-request-id"></a>Identyfikator żądania korelacji

Każda odpowiedź o błędzie zawiera unikatowy parametr identyfikatora do śledzenia.

Nazwa właściwości tego parametru to "target".

Podczas kontaktowania się z nami w sprawie błędu dołączenie tego identyfikatora pomoże znaleźć jego główną przyczynę.

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
