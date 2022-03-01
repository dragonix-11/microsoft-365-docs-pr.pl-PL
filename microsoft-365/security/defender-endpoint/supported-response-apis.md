---
title: Obsługiwane interfejsy API odpowiedzi programu Microsoft Defender dla punktów końcowych
description: Dowiedz się więcej o określonych wywołaniach interfejsu API programu Microsoft Defender dla punktów końcowych związanych z odpowiedziami.
keywords: response apis, graph api, supported api, actor, alerts, device, user, domain, ip, file
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
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
ms.openlocfilehash: dcf73669ab780ec23cbd5551039dc8c74f0502ef
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997880"
---
# <a name="supported-microsoft-defender-for-endpoint-query-apis"></a>Obsługiwane interfejsy API zapytań programu Microsoft Defender dla punktów końcowych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> [!TIP]
> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-supported-response-apis-abovefoldlink)

Dowiedz się więcej na temat obsługiwanych wywołań interfejsu API związanych z odpowiedziami, które można uruchamiać, oraz szczegółowych informacji, takich jak wymagane nagłówki żądań i oczekiwana odpowiedź z połączeń.

## <a name="in-this-section"></a>W tej sekcji

<br>

****

|Temat|Opis|
|---|---|
|Zbierz pakiet badania|Uruchom ten interfejs API, aby zebrać pakiet badania z urządzenia.|
|Wyizoluj urządzenie|Uruchom ten interfejs API, aby odizolować urządzenie z sieci.|
|Niezamówianie urządzenia|Usuń urządzenie z izolacji.|
|Ograniczanie wykonywania kodu|Uruchom ten interfejs API, aby prowadzić ataki przez zatrzymanie złośliwych procesów. Możesz również zablokować urządzenie i uniemożliwić uruchamianie kolejnych prób potencjalnie złośliwych programów.|
|Unrestrict code execution|Uruchom to ustawienie, aby odwrócić ograniczenie zasad aplikacji po sprawdzeniu, że naruszone urządzenie zostało usunięte.|
|Uruchom skanowanie antywirusowe|Zdalnie zainicjuj skanowanie antywirusowe, aby pomóc w zidentyfikowaniu i naprawieniu złośliwego oprogramowania, które może być obecne na naruszonym urządzeniu.|
|Zatrzymywanie i poddaj kwarantannie plik|Uruchom to wywołanie, aby zatrzymać uruchamianie procesów, poddaj kwarantannie pliki i usuń trwale, takie jak klucze rejestru.|
|Przykład żądania|Uruchom to wywołanie, aby poprosić o próbkę pliku z określonego urządzenia. Plik zostanie zebrany z urządzenia i przekazany do bezpiecznego magazynu.|
|Blokowanie pliku|Uruchom ten interfejs API, aby zapobiec dalszemu rozpowszechnianiu ataków w organizacji, poprzez zablokowanie potencjalnie złośliwych plików lub potencjalnego złośliwego oprogramowania.|
|Odblokowywanie pliku|Zezwalaj na uruchamianie pliku w organizacji przy użyciu Program antywirusowy Microsoft Defender.|
|Uzyskiwanie URI SAS pakietu|Uruchom ten interfejs API, aby uzyskać interfejs URI, który umożliwia pobieranie pakietu badania.|
|Uzyskaj obiekt MachineAction|Uruchom ten interfejs API, aby pobrać obiekt MachineAction.|
|Pobierz kolekcję MachineActions|Uruchom to, aby pobrać kolekcję akcji komputera.|
|Pobierz kolekcję FileActions|Uruchom ten interfejs API, aby pobrać kolekcję FileActions.|
|Obiekt Get FileMachineAction|Uruchom ten interfejs API, aby uzyskać obiekt FileMachineAction.|
|Pobierz kolekcję FileMachineActions|Uruchom ten interfejs API, aby pobrać kolekcję FileMachineAction.|
|
