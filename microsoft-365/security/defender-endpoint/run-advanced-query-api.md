---
title: Zaawansowany interfejs API łowiectwo
ms.reviewer: ''
description: Dowiedz się, jak używać zaawansowanego interfejsu API wyszukiwania do uruchamiania zaawansowanych zapytań w programie Microsoft Defender for Endpoint. Zapoznaj się z ograniczeniami i zobacz przykład.
keywords: api, obsługiwane api, zaawansowane wyszukiwania, zapytanie
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
ms.openlocfilehash: 2e5898c0227128c099c7f0fe1ca99a6d9c8001ef
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996870"
---
# <a name="advanced-hunting-api"></a>Zaawansowany interfejs API łowiectwo

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="limitations"></a>Ograniczenia

1. Kwerendę można uruchomić tylko na danych z ostatnich 30 dni.

2. Wyniki będą zawierać maksymalnie 100 000 wierszy.

3. Liczba wykonywania jest ograniczona dla dzierżawy:
   - Wywołania interfejsu API: Maksymalnie 45 połączeń na minutę, do 1500 połączeń na godzinę.
   - Czas wykonywania: 10 minut czasu bieżącego co godzinę i 3 godziny pracy dziennie.

4. Maksymalny czas wykonywania jednego żądania to 10 minut.

5. 429 odpowiedzi będzie oznaczać osiągnięcie limitu przydziału zarówno przez liczbę żądań, jak i przez procesor. Przeczytaj treść odpowiedzi, aby zrozumieć, jaki limit został osiągnięty.

6. Maksymalny rozmiar wyników zapytania w jednym żądaniu nie może przekraczać 124 MB. W przypadku przekroczenia tego protokołu http 400 — złe żądanie z komunikatem "Wykonywanie zapytania przekroczyło dozwolony rozmiar wyników. Zostanie wyświetlony temat Optymalizowanie zapytania przez ograniczenie ilości wyników i spróbuj ponownie".

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|AdvancedQuery.Read.All|"Uruchom zapytania zaawansowane"
Delegowane (konto służbowe)|AdvancedQuery.Read|"Uruchom zapytania zaawansowane"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć rolę AD "Wyświetlanie danych"
> - Użytkownik musi mieć dostęp do urządzenia w zależności od ustawień grupy urządzeń (zobacz Tworzenie grup urządzeń i zarządzanie [nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

## <a name="request-headers"></a>Żądaj nagłówków

Nagłówek|Value
:---|:---
Autoryzacja|Użytkownik {token}. **Wymagane**.
Typ zawartości|application/json

## <a name="request-body"></a>Treść wniosku

W treści żądania należy podać obiekt JSON o następujących parametrach:

Parametr|Wpisać|Opis
:---|:---|:---
Zapytanie|Tekst|Kwerenda do uruchomienia. **Wymagane**.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK, a obiekt _QueryResponse_ w treści odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

```json
{
    "Query":"DeviceProcessEvents
|where InitiatingProcessFileName =~ 'powershell.exe'
|where ProcessCommandLine contains 'appdata'
|project Timestamp, FileName, InitiatingProcessFileName, DeviceId
|limit 2"
}
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

> [!NOTE]
> Pokazany tutaj obiekt odpowiedzi może zostać skrócony. Wszystkie właściwości zostaną zwrócone z rzeczywistego wywołania.

```json
{
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
        },
        {
            "Name": "DeviceId",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-02-05T01:10:26.2648757Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        },
        {
            "Timestamp": "2020-02-05T01:10:26.5614772Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        }
    ]
}
```

## <a name="related-topics"></a>Tematy pokrewne

- [Wprowadzenie do interfejsów API programu Microsoft Defender dla punktów końcowych](apis-intro.md)
- [Zaawansowane chyłonie z Portalu](advanced-hunting-query-language.md)
- [Zaawansowane szukanie przy użyciu programu PowerShell](run-advanced-query-sample-powershell.md)
