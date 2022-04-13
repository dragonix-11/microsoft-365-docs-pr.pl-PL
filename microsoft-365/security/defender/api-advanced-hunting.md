---
title: Microsoft 365 Defender zaawansowany interfejs API wyszukiwania zagrożeń
description: Dowiedz się, jak uruchamiać zaawansowane zapytania dotyczące wyszukiwania zagrożeń przy użyciu zaawansowanego interfejsu API wyszukiwania zagrożeń w Microsoft 365 Defender
keywords: Zaawansowane wyszukiwanie zagrożeń, interfejsy API, api, M365 Defender, Microsoft 365 Defender
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
ms.openlocfilehash: d01cdacc40b58eb940b2773606221b4fdbe18728
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823195"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>Microsoft 365 Defender zaawansowany interfejs API wyszukiwania zagrożeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

[Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md) to narzędzie do wyszukiwania zagrożeń, które używa [specjalnie skonstruowanych zapytań](advanced-hunting-query-language.md) do badania danych zdarzeń z ostatnich 30 dni w Microsoft 365 Defender. Zaawansowane zapytania dotyczące wyszukiwania zagrożeń umożliwiają inspekcję nietypowych działań, wykrywanie możliwych zagrożeń, a nawet reagowanie na ataki. Zaawansowany interfejs API wyszukiwania zagrożeń umożliwia programowe wykonywanie zapytań dotyczących danych zdarzeń.

## <a name="quotas-and-resource-allocation"></a>Przydziały i alokacja zasobów

Poniższe warunki odnoszą się do wszystkich zapytań.

1. Zapytania eksplorują i zwracają dane z ostatnich 30 dni.
2. Wyniki mogą zwracać do 100 000 wierszy.
3. Możesz wykonywać maksymalnie 45 wywołań na minutę na dzierżawę.
4. Zapytania są blokowane, jeśli dzierżawa osiągnęła 100% aż do następnego 15-minutowego cyklu.
5. Jeśli pojedyncze żądanie jest uruchamiane dłużej niż 10 minut, upłynął limit czasu i zwróci błąd.
6. Kod `429` odpowiedzi HTTP wskazuje, że osiągnięto limit przydziału, liczbę wysłanych żądań lub przydzielony czas wykonywania. Przeczytaj treść odpowiedzi, aby zrozumieć osiągnięty limit. 

> [!NOTE]
> Wszystkie limity przydziału wymienione powyżej (na przykład 15 wywołań na minutę) są na rozmiar dzierżawy. Te limity przydziału są minimalne.

## <a name="permissions"></a>Uprawnienia

Do wywołania zaawansowanego interfejsu API wyszukiwania zagrożeń jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Uzyskiwanie dostępu do interfejsów API Microsoft 365 Defender Protection](api-access.md)

Typ uprawnień | Uprawnienia | Nazwa wyświetlana uprawnień
-|-|-
Aplikacja | AdvancedHunting.Read.All| Uruchamianie zaawansowanych zapytań
Delegowane (konto służbowe) | AdvancedHunting.Read | Uruchamianie zaawansowanych zapytań

>[!Note]
> Podczas uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
>- Użytkownik musi mieć rolę usługi AD "Wyświetl dane"
>- Użytkownik musi mieć dostęp do urządzenia na podstawie ustawień grupy urządzeń.

## <a name="http-request"></a>Żądanie HTTP

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>Nagłówki żądań

Nagłówek | Value
-|-
Autoryzacji | Nośnik {token} **Uwaga: wymagane**
Typ zawartości | application/json

## <a name="request-body"></a>Treść żądania

W treści żądania podaj obiekt JSON z następującymi parametrami:

Parametr | Wpisać | Opis
-|-|-
Kwerendy | Tekst | Zapytanie do uruchomienia. **Uwaga: wymagane**

## <a name="response"></a>Odpowiedzi

Jeśli to się powiedzie, ta metoda zwróci `200 OK`obiekt _, i QueryResponse_ w treści odpowiedzi.

Obiekt odpowiedzi zawiera trzy właściwości najwyższego poziomu:

1. Statystyki — słownik statystyk wydajności zapytań.
2. Schemat — schemat odpowiedzi, lista par Name-Type dla każdej kolumny.
3. Wyniki — lista zaawansowanych zdarzeń wyszukiwania zagrożeń.

## <a name="example"></a>Przykład

W poniższym przykładzie użytkownik wysyła poniższe zapytanie i odbiera obiekt odpowiedzi interfejsu API zawierający `Stats`, `Schema`i `Results`.

### <a name="query"></a>Kwerendy

```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

### <a name="response-object"></a>Obiekt odpowiedzi

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

- [Uzyskiwanie dostępu do interfejsów API Microsoft 365 Defender](api-access.md)
- [Dowiedz się więcej o limitach interfejsu API i licencjonowaniu](api-terms.md)
- [Omówienie kodów błędów](api-error-codes.md)
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
