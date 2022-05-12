---
title: Profile oceny punktów odniesienia zabezpieczeń
description: Zawiera informacje o interfejsach API profilów oceny punktów odniesienia zabezpieczeń, które ściągają dane "Zarządzanie zagrożeniami i lukami". Istnieją różne wywołania interfejsu API umożliwiające pobieranie różnych typów danych. Ogólnie rzecz biorąc, każde wywołanie interfejsu API zawiera wymagane dane dla urządzeń w organizacji.
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
ms.openlocfilehash: ca110cfba43b95790114928f1c0d3adcae46f087
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2022
ms.locfileid: "65369623"
---
# <a name="list-all-security-baselines-assessment-profiles"></a>Wyświetlanie listy wszystkich profilów oceny punktów odniesienia zabezpieczeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender — aktualizacja](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.- Update](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="1-get-security-baselines-assessment-profiles"></a>1. Uzyskiwanie profilów oceny punktów odniesienia zabezpieczeń

Ten interfejs API pobiera listę wszystkich profilów oceny punktów odniesienia zabezpieczeń utworzonych przez organizację.  

### <a name="11-parameters"></a>Parametry 1.1

- Obsługuje zapytania OData V4.  
- Obsługiwane operatory OData:  
  - $filter: id,name, operatingSystem, operatingSystemVersion, status, settingsNumber, passedDevices, totalDevices  
  - $top z maksymalną wartością 10 000.  
  - $skip.

### <a name="12-http-request"></a>1.2 Żądanie HTTP

```http
GET:/api/baselineProfiles
```

### <a name="13-request-headers"></a>1.3 Nagłówki żądań

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacji|Ciąg|Element nośny {token}. **Wymagane**.

### <a name="14-properties"></a>1.4 Właściwości

|Właściwość | Wpisać | Opis |
|:---|:---|:---|
|Identyfikator | Ciąg | Unikatowy identyfikator określonego profilu punktu odniesienia.
|Nazwa | Ciąg | Nazwa profilu.
|Opis | Ciąg | Opis profilu.
|Punkt odniesienia | Ciąg | Test porównawczy profilu.
|Wersja | Ciąg | Wersja profilu.
|Operatingsystem|Ciąg|Profil odpowiedniego systemu operacyjnego.
|operatingSystemVersion|Ciąg|Odpowiednia wersja systemu operacyjnego profilu.
|Stan|Wartość logiczna|Wskazuje, czy profil jest aktywny, czy nie
|complianceLevel|Ciąg|Poziom zgodności wybrany dla profilu.
|settingsNumber|Int|Liczba wybranych konfiguracji w profilu.
|Createdby|Ciąg|Użytkownik, który utworzył ten profil.
|lastUpdatedBy|Datetime|Ostatni użytkownik, który zmodyfikował ten profil.
|createdOnTimeOffset|Datetime|Data i godzina utworzenia profilu.
|lastUpdateTimeOffset|Datetime|Data i godzina ostatniej aktualizacji profilu.
|passedDevices|Int|Liczba urządzeń mających zastosowanie do tego profilu, które są zgodne ze wszystkimi konfiguracjami profilu.
|totalDevices|Int|Liczba urządzeń mających zastosowanie do tego profilu.

## <a name="15-example"></a>Przykład 1.5

### <a name="151-request-example"></a>1.5.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/baselineProfiles 
```

### <a name="162-response-example"></a>Przykład odpowiedzi 1.6.2

```json
{  
    "@odata.context": "https:// api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicBaselineProfileDto)",  
    "value": 
    [  
        {  
            "id": "02bcbb9d-d197-479e-811e-1cd5a6f9f8fa",  
            "name": "Windows 10 build 1909 CIS profile",  
            "description": "important",  
            "benchmark": "CIS",  
            "version": "1.0.0",  
            "operatingSystem": "Windows 10",  
            "operatingSystemVersion": "1909",  
            "status": true,  
            "complianceLevel": "Level 1 (L1) - Corporate/Enterprise Environment (general use)",  
            "settingsNumber": 51,  
            "createdBy": "user@org.net",  
            "lastUpdatedBy": null,  
            "createdOnTimestampUTC": "0001-01-01T00:00:00Z",  
            "lastUpdateTimestampUTC": "0001-01-01T00:00:00Z",  
            "passedDevices": 0,  
            "totalDevices": 10  
        }  
     ]  
}  
```

## <a name="see-also"></a>Zobacz też

- [Eksportowanie oceny punktów odniesienia zabezpieczeń](export-security-baseline-assessment.md)
- [Uzyskiwanie konfiguracji oceny punktów odniesienia zabezpieczeń](get-security-baselines-assessment-configurations.md)
