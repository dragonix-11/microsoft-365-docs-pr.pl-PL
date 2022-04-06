---
title: Microsoft 365 Defender zaawansowanego interfejsu API wyszukiwania
description: Dowiedz się, jak uruchamiać zaawansowane zapytania myśliwskie przy Microsoft 365 Defender zaawansowanego interfejsu API łowiectwo
keywords: Zaawansowane łowiectwo, interfejsy API, api, M365 Defender, Microsoft 365 Defender
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
ms.openlocfilehash: 05957fcf7cf2b3b03fbc757fc8b21e67156b285a
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500832"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>Microsoft 365 Defender zaawansowanego interfejsu API łowiectwo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

[Zaawansowane szukanie](advanced-hunting-overview.md) jest narzędziem do szukania zagrożeń, [](advanced-hunting-query-language.md) które używa specjalnie skonstruowanych zapytań, aby sprawdzać dane dotyczące wydarzeń z ostatnich 30 dni w Microsoft 365 Defender. Za pomocą zaawansowanych zapytań wyszukiwania możesz sprawdzać nietypowe działania, wykrywać możliwe zagrożenia, a nawet odpowiadać na ataki. Zaawansowany interfejs API wyszukiwania umożliwia programowe wykonywanie zapytań dotyczących danych dotyczących zdarzeń.

## <a name="quotas-and-resource-allocation"></a>Przydziały i alokacja zasobów

Poniższe warunki odnoszą się do wszystkich zapytań.

1. Kwerendy eksplorowały i zwracają dane z ostatnich 30 dni.
2. Wyniki mogą zwrócić do 100 000 wierszy.
3. Możesz wykonać do 45 rozmów na minutę na dzierżawcę.
4. Zapytania są blokowane, jeśli dzierżawa osiągnęła 100% do czasu kolejnego 15-minutowego cyklu.
5. Jeśli jedno żądanie będzie trwać dłużej niż 10 minut, zostanie u niego urósłowy błąd i zostanie zwrócony błąd.
6. Kod `429` odpowiedzi HTTP oznacza, że osiągnięto przydział według liczby wysłanych żądań lub przydziału czasu bieżącego. Przeczytaj treść odpowiedzi, aby zrozumieć osiągnięty limit. 

> [!NOTE]
> Wszystkie przydziały wymienione powyżej (na przykład 15 połączeń na min) są według rozmiaru dzierżawy. Te przydziały są minimalne.

## <a name="permissions"></a>Uprawnienia

Jedno z następujących uprawnień jest wymagane do wywołania zaawansowanego interfejsu API wyszukiwania. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Uzyskiwanie dostępu do [interfejsów API Microsoft 365 Defender Ochrony](api-access.md)

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
-|-|-
Aplikacja | AdvancedQuery.Read.All| Uruchamianie zapytań zaawansowanych
Delegowane (konto służbowe) | AdvancedQuery.Read | Uruchamianie zapytań zaawansowanych

>[!Note]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
>- Użytkownik musi mieć rolę AD "Wyświetlanie danych"
>- W zależności od ustawień grupy urządzeń użytkownik musi mieć dostęp do urządzenia.

## <a name="http-request"></a>Żądanie HTTP

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>Żądaj nagłówków

Nagłówek | Value
-|-
Autoryzacja | Bearer {token} **Uwaga: wymagana**
Typ zawartości | application/json

## <a name="request-body"></a>Treść wniosku

W treści żądania należy podać obiekt JSON o następujących parametrach:

Parametr | Wpisać | Opis
-|-|-
Zapytanie | Tekst | Kwerenda do uruchomienia. **Uwaga: wymagane**

## <a name="response"></a>Odpowiedź

Jeśli ta metoda powiedzie się, ta metoda zwróci wyniki `200 OK`, a obiekt _QueryResponse_ w treści odpowiedzi.

Obiekt odpowiedzi zawiera trzy właściwości najwyższego poziomu:

1. Statystyka — słownik statystyki wydajności zapytania.
2. Schemat — schemat odpowiedzi, lista par Name-Type poszczególnych kolumn.
3. Wyniki — lista zaawansowanych wydarzeń chłoniowych.

## <a name="example"></a>Przykład

W poniższym przykładzie użytkownik wysyła poniższe zapytanie i odbiera obiekt odpowiedzi interfejsu API zawierający `Stats`, `Schema`i `Results`.

### <a name="query"></a>Zapytanie

```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

### <a name="response-object"></a>Obiekt Response

```json
{
    "Stats": {
        "ExecutionTime": 4.621215,
        "resource_usage": {
            "cache": {
                "memory": {
                    "hits": 773461,
                    "misses": 4481,
                    "total": 777942
                },
                "disk": {
                    "hits": 994,
                    "misses": 197,
                    "total": 1191
                }
            },
            "cpu": {
                "user": "00:00:19.0468750",
                "kernel": "00:00:00.0156250",
                "total cpu": "00:00:19.0625000"
            },
            "memory": {
                "peak_per_node": 236822432
            }
        },
        "dataset_statistics": [
            {
                "table_row_count": 2,
                "table_size": 102
            }
        ]
    },
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-08-30T06:38:35.7664356Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        },
        {
            "Timestamp": "2020-08-30T06:38:30.5163363Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        }
    ]
}
```

## <a name="related-articles"></a>Artykuły pokrewne

- [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md)
- [Informacje o limitach i licencjonowaniu interfejsu API](api-terms.md)
- [Opis kodów błędów](api-error-codes.md)
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
