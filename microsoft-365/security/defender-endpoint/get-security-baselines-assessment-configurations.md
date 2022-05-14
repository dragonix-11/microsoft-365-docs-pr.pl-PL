---
title: Konfiguracje oceny punktów odniesienia zabezpieczeń
description: Zawiera informacje o konfiguracjach oceny punktów odniesienia zabezpieczeń, które ściągają dane "Zarządzanie zagrożeniami i lukami". Istnieją różne wywołania interfejsu API umożliwiające pobieranie różnych typów danych. Ogólnie rzecz biorąc, każde wywołanie interfejsu API zawiera wymagane dane dla urządzeń w organizacji.
keywords: api, apis, export assessment, per device assessment, per machine assessment, vulnerability assessment report, device vulnerability assessment, device vulnerability report, secure configuration assessment, secure configuration report, software vulnerabilities assessment, software vulnerability report, vulnerability report, vulnerability report by machine,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 4a9b75698227c86c58255bad4e3336157c179c4a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419052"
---
# <a name="list-security-baselines-assessment-configurations"></a>Wyświetl listę konfiguracji oceny punktów odniesienia zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender — aktualizacja](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.- Update](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="1-get-all-security-baselines-assessment-configurations"></a>1. Uzyskiwanie wszystkich konfiguracji oceny punktów odniesienia zabezpieczeń

Ten interfejs API pobiera listę wszystkich możliwych konfiguracji i ustawień oceny punktów odniesienia zabezpieczeń dla wszystkich dostępnych testów porównawczych.

### <a name="11-parameters"></a>Parametry 1.1

- Obsługuje zapytania OData V4
- Obsługiwane operatory OData:
  - `$filter` on: `id`, , `category`, `name`, `CCE`
  - `$top` z maksymalną wartością 10 000
  - `$skip`

### <a name="12-http-request"></a>1.2 Żądanie HTTP

```http
GET /api/baselineConfigurations 
```

### <a name="13-request-headers"></a>1.3 Nagłówki żądań

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacji|Ciąg|Element nośny {token}. **Wymagane**.

### <a name="14-response"></a>Odpowiedź 1.4

W przypadku powodzenia ta metoda zwraca wartość 200 OK z listą konfiguracji punktu odniesienia w treści.

### <a name="15-properties"></a>1.5 Właściwości

|Właściwość | Wpisać | Opis |
|:---|:---|:---|
|Identyfikator | Ciąg | Unikatowy identyfikator określonej konfiguracji w benchmarku odniesienia.
|Nazwa | Ciąg | Nazwa konfiguracji wyświetlana w testach porównawczych.
|Opis | Ciąg | Opis konfiguracji wyświetlany w testach porównawczych.
|Kategorii | Ciąg | Kategoria konfiguracji wyświetlana w testach porównawczych.
|complianceLevel|Ciąg|Poziom zgodności testu porównawczego, na którym jest wyświetlana ta konfiguracja.
|`cce`|Int|CCE dla tej konfiguracji, jak to jest wyświetlane w testach porównawczych.
|Uzasadnienie |Ciąg|Uzasadnienie dla tej konfiguracji, które pojawia się w benchmarku. W przypadku testu porównawczego STIG nie jest on dostarczany dla tej konfiguracji.

## <a name="16-example"></a>Przykład 1.6

### <a name="151-request-example"></a>1.5.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/baselineConfigurations
```

### <a name="162-response-example"></a>Przykład odpowiedzi 1.6.2

```json
{
    "@odata.context": " https://api-df.securitycenter.microsoft.com/api/$metadata#BaselineConfigurations ", 
    "value": [
        {
            "id": "1.1.8", 
            "name": "(L1) Ensure 'Allow importing of payment info' is set to 'Disabled'",
            "description": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">This policy setting controls whether users are able to import payment information from another browser into Microsoft Edge as well as whether payment information is imported on first use.</p>",
            "category": "Microsoft Edge",
            "complianceLevels": [
                "Level 1 (L1) - Corporate/Enterprise Environment (general use)",
                "Level 2 (L2) - High Security/Sensitive Data Environment (limited functionality)"
            ],
            "cce": "",
            "rationale": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">Having payment information automatically imported or allowing users to import payment data from another browser into Microsoft Edge could allow for sensitive data to be imported into Edge.</p>",
            "remediation": "<div xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">\r\n  <p>\r\n    <p>\r\nTo establish the recommended configuration via GP, set the following UI path to                 <span class=\"inline_block\">Disabled</span></p>\r\n    <code class=\"code_block\">Computer Configuration\\Policies\\Administrative Templates\\Microsoft Edge\\Allow importing of payment info\r\n</code>\r\n    <p>\r\n      <strong>Note:</strong>\r\n This Group Policy path may not exist by default. It is provided by the Group Policy template                 <span class=\"inline_block\">MSEdge.admx/adml</span>\r\n that can be downloaded from Microsoft                 <a href=\"https://www.microsoft.com/en-us/edge/business/download\">here</a>\r\n.              </p>\r\n    <p class=\"bold\">Impact:</p>\r\n    <p>\r\n      <p>Users will be unable to perform a payment information import from other browsers into Microsoft Edge.</p>\r\n    </p>\r\n  </p>\r\n</div>",
            "benchmarkName": "CIS"
"recommendedValue": [ 
                "Equals '0'" 
            ], 
            "source": [ 
                "hkey_local_machine\\software\\policies\\microsoft\\windows\\eventlog\\security\\retention" 
            ]
        }, 
    ] 
} 
```

## <a name="see-also"></a>Zobacz też

- [Eksportuj ocenę punktów odniesienia zabezpieczeń](export-security-baseline-assessment.md)
- [Uzyskiwanie profilów oceny punktów odniesienia zabezpieczeń](get-security-baselines-assessment-profiles.md)
