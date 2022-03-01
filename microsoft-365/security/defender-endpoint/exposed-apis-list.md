---
title: Obsługiwana usługa Microsoft Defender dla interfejsów API punktów końcowych
ms.reviewer: ''
description: Dowiedz się więcej o konkretnych obsługiwanych jednostkach programu Microsoft Defender dla punktów końcowych, do których można tworzyć wywołania interfejsu API.
keywords: api, obsługiwane api, actor, alerts, device, user, domain, ip, file, advanced queries, advanced hunting
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
ms.openlocfilehash: 94c5698845f556936373ee4548d9aa137f03867b
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996871"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>Obsługiwana usługa Microsoft Defender dla interfejsów API punktów końcowych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>Numer URI punktu końcowego i numerowanie wersji

### <a name="endpoint-uri"></a>URI punktu końcowego

> Podstawowy URI usługi to: [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> Zapytania oparte na danych OData mają prefiks "/api". Aby na przykład pobrać alerty, można wysłać żądanie GET do [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>Versioning (Wersja)

> Interfejs API obsługuje sporządzanie wersji.
>
> Bieżąca wersja to **V1.0**.
>
> Aby użyć określonej wersji, użyj tego formatu: `https://api.securitycenter.microsoft.com/api/{Version}`. Na przykład: `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> Jeśli nie określisz żadnej wersji (np. `https://api.securitycenter.microsoft.com/api/alerts`), otrzymasz dostęp do najnowszej wersji.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Dowiedz się więcej o poszczególnych obsługiwanych jednostkach, w których można uruchamiać wywołania interfejsu API, oraz poznaj szczegóły, takie jak wartości żądań HTTP, nagłówki żądań i oczekiwane odpowiedzi.

## <a name="in-this-section"></a>W tej sekcji

Temat | Opis
:---|:---
[Zaawansowane łowiectwo](run-advanced-query-api.md) | Uruchamianie zapytań z interfejsu API.
[Metody i właściwości alertów](alerts.md) | Uruchamianie wywołań interfejsu API, takich \- jak uzyskiwanie alertów, tworzenie alertów, aktualizowanie alertów i nie tylko.
[Eksportowanie metod i właściwości oceny na urządzenie](get-assessment-methods-properties.md) | Uruchamiaj wywołania interfejsu API, aby zbierać oceny luk w zabezpieczeniach w zależności od urządzenia, takie jak: \- ocena bezpiecznej konfiguracji, ocena eksportu zasobów oprogramowania, ocena luk w oprogramowaniu eksportu lub ocena luk w zabezpieczeniach oprogramowania w przypadku eksportu.
[Metody i właściwości badania automatycznego](investigation.md) | Uruchamianie wywołań interfejsu API, takich \- jak pobierz kolekcję badania.
[Alerty dotyczące domeny](get-domain-related-alerts.md) | Uruchamianie wywołań interfejsu API, takich \- jak uzyskiwanie urządzeń związanych z domeną, statystyk dotyczących domen i nie tylko.
[Metody i właściwości plików](files.md) | Uruchamianie wywołań interfejsu API, \- takich jak uzyskiwanie informacji o plikach, alerty dotyczące plików, urządzenia powiązane z plikami i statystyki plików.
[Metody i właściwości wskaźników](ti-indicator.md) | Uruchamianie wywołania interfejsu API, na \- przykład uzyskiwanie wskaźników, tworzenie wskaźników i usuwanie wskaźników.
[Alerty dotyczące adresów IP](get-ip-related-alerts.md) | Uruchamianie połączeń interfejsu API, takich jak \- uzyskiwanie alertów dotyczących adresów IP i uzyskiwanie statystyk adresów IP.
[Metody i właściwości komputera](machine.md) | Uruchamianie wywołań interfejsu API, \- takich jak uzyskiwanie urządzeń, uzyskiwanie urządzeń według identyfikatora, informacje o zalogowanych użytkownikach, edytowanie tagów i nie tylko.
[Metody i właściwości akcji komputera](machineaction.md) | Uruchom wywołanie interfejsu API, takie \- jak Isolation, Uruchom skanowanie antywirusowe i nie tylko.
[Metody i właściwości zalecenia](recommendation.md) | Uruchamianie wywołań interfejsu API, takich \- jak get recommendation by ID.
[Metody i właściwości działań naprawczych](get-remediation-methods-properties.md) | Uruchamianie wywołania interfejsu API, na \- przykład wykonywanie wszystkich zadań naprawczych, uzyskiwanie na urządzeniach ujawnionych zadań naprawczych i uzyskiwanie jednego zadania zaradczego według identyfikatorów.
[Metody i właściwości wyników](score.md) | Uruchamiaj połączenia API, takie jak \- uzyskiwanie wyniku ekspozycji lub uzyskiwanie bezpiecznego wyniku urządzenia.
[Metody i właściwości oprogramowania](software.md) | Uruchamianie wywołań interfejsu API, takich \- jak luki w zabezpieczeniach listy przez oprogramowanie.
[Metody użytkownika](user.md) | Uruchamianie wywołań interfejsu API, takich \- jak uzyskiwanie alertów związanych z użytkownikiem i urządzeń związanych z użytkownikami.
[Metody i właściwości luk w zabezpieczeniach](vulnerability.md) | Uruchamianie wywołań interfejsu API, takich \- jak urządzenia listy w przypadku luki w zabezpieczeniach.

## <a name="see-also"></a>Zobacz też

- [Interfejsy API programu Microsoft Defender dla punktów końcowych](apis-intro.md)

- [Program Microsoft Defender for Endpoint API informacje o wersji](api-release-notes.md)
