---
title: Pobierz zainstalowane oprogramowanie
description: Pobiera kolekcję zainstalowanego oprogramowania związanego z danym identyfikatorem urządzenia.
keywords: apis, graph api, supported apis, get, list, file, information, software inventory, installed software per device, threat & zarządzanie lukami w zabezpieczeniach api, Ochrona punktu końcowego w usłudze Microsoft Defender tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 97aa4a668306c4790dcd42c046ba4bf3a04bcf51
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840414"
---
# <a name="get-installed-software"></a>Pobierz zainstalowane oprogramowanie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Pobiera kolekcję zainstalowanego oprogramowania związanego z danym identyfikatorem urządzenia.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Korzystanie z interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja |Software.Read.All|"Odczytywanie informacji o oprogramowaniu do zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|Software.Read|"Odczytywanie informacji o oprogramowaniu do zarządzania zagrożeniami i lukami w zabezpieczeniach"

## <a name="http-request"></a>Żądanie HTTP

```http
GET /api/machines/{machineId}/software
```

## <a name="request-headers"></a>Nagłówki żądań

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacji|Ciąg|Element nośny {token}. **Wymagane**.

## <a name="request-body"></a>Treść żądania

Pusty

## <a name="response"></a>Odpowiedzi

W przypadku powodzenia ta metoda zwraca wartość 200 OK z zainstalowanymi informacjami o oprogramowaniu w treści.

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

Oto przykład żądania.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/software
```

### <a name="response-example"></a>Przykład odpowiedzi

Oto przykład odpowiedzi.

```json
{
"@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Software",
"value": [
        {
"id": "microsoft-_-internet_explorer",
"name": "internet_explorer",
"vendor": "microsoft",
"weaknesses": 67,
"publicExploit": true,
"activeAlert": false,
"exposedMachines": 42115,
"impactScore": 46.2037163
        }
    ]
}
```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie lukami w zabezpieczeniach opartymi na ryzyku & zagrożeń](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Spis oprogramowania z lukami w zabezpieczeniach & zagrożeń](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
