---
title: Typ zasobu pliku
description: Pobieranie ostatnich alertów programu Microsoft Defender dla punktu końcowego dotyczących plików.
keywords: apis, api Graph, obsługiwane api, get, alerts, recent
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
ms.openlocfilehash: 7fef64136e27b8b9a85163fe9e25fdf59ab6d2aa
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996886"
---
# <a name="file-resource-type"></a>Typ zasobu pliku

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Reprezentuje jednostkę pliku w uchcie Defender for Endpoint.

## <a name="methods"></a>Metody

Metoda|Zwracany typ |Opis
:---|:---|:---
[Pobierz plik](get-file-information.md) | [plik](files.md) | Pobierz jeden plik 
[Alerty dotyczące plików list](get-file-related-alerts.md) | [kolekcja alertów](alerts.md) | Pobierz [encje alertu](alerts.md) skojarzone z plikiem.
[Komputery powiązane z plikiem listy](get-file-related-machines.md) | [kolekcja maszyn](machine.md) | Pobierz [jednostki maszynowe](machine.md) skojarzone z alertem.
[statystyka plików](get-file-statistics.md) | Podsumowanie statystyki | Pobiera informacje odzyskane dla danego pliku.


## <a name="properties"></a>Właściwości

|Właściwość | Wpisać | Opis |
|:---|:---|:---|
|sha1 | Ciąg | Skrót sha1 zawartości pliku |
|sha256 | Ciąg | Skrót sha256 zawartości pliku |
|globalPrevalence | Nullable long | Plik w organizacji |
|globalFirstObserved | DateTimeOffset | Po raz pierwszy obserwowany plik został obserwowany |
|globalLastObserved | DateTimeOffset | Ostatnia obserwowana godzina obserwowania pliku |
|rozmiar | Nullable long | Rozmiar pliku |
|fileType (Typ pliku) | Ciąg | Typ pliku |
|isPeFile | Wartość logiczna | true, jeśli plik jest przenośnym plikiem wykonywalnym (np. "DLL", "EXE" itd.). |
|filePublisher | Ciąg | Wydawca pliku |
|nazwa_plikuProduktu | Ciąg | Nazwa produktu |
|podpis | Ciąg | File signer |
|wystawca | Ciąg | Wystawca plików |
|signerHash | Ciąg | Skrót certyfikatu podpisywania |
|isValidCertificate | Wartość logiczna | Certyfikat podpisywania został pomyślnie zweryfikowany przez program Microsoft Defender dla agenta punktu końcowego |
|determinationType | Ciąg | Typ wyznaczania pliku |
|określenieWartość | Ciąg | Wartość określania |

## <a name="json-representation"></a>Reprezentacja Jsona

```json
{
    "sha1": "4388963aaa83afe2042a46a3c017ad50bdcdafb3",
    "sha256": "413c58c8267d2c8648d8f6384bacc2ae9c929b2b96578b6860b5087cd1bd6462",
    "globalPrevalence": 180022,
    "globalFirstObserved": "2017-09-19T03:51:27.6785431Z",
    "globalLastObserved": "2020-01-06T03:59:21.3229314Z",
    "size": 22139496,
    "fileType": "APP",
    "isPeFile": true,
    "filePublisher": "CHENGDU YIWO Tech Development Co., Ltd.",
    "fileProductName": "EaseUS MobiSaver for Android",
    "signer": "CHENGDU YIWO Tech Development Co., Ltd.",
    "issuer": "VeriSign Class 3 Code Signing 2010 CA",
    "signerHash": "6c3245d4a9bc0244d99dff27af259cbbae2e2d16",
    "isValidCertificate": false,
    "determinationType": "Pua",
    "determinationValue": "PUA:Win32/FusionCore"
}
```
