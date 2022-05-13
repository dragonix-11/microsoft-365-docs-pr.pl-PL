---
title: Metody i właściwości punktu odniesienia zabezpieczeń na urządzenie
description: Zawiera informacje o interfejsach API punktów odniesienia zabezpieczeń, które ściągają dane "Zarządzanie zagrożeniami i lukami". Istnieją różne wywołania interfejsu API umożliwiające pobieranie różnych typów danych. Ogólnie rzecz biorąc, każde wywołanie interfejsu API zawiera wymagane dane dla urządzeń w organizacji.
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
ms.openlocfilehash: 730eb90202acff9efad1cc2f01fd60431366e997
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393442"
---
# <a name="export-security-baselines-assessment-per-device"></a>Eksportowanie oceny punktów odniesienia zabezpieczeń na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender — aktualizacja](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.- Update](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Istnieją różne wywołania interfejsu API umożliwiające pobieranie różnych typów danych. Ogólnie rzecz biorąc, każde wywołanie interfejsu API zawiera wymagane dane dla urządzeń w organizacji.

- **Odpowiedź JSON**  Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza w _przypadku małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K_. Odpowiedź jest podzielona na strony, więc możesz użyć \@pola odata.nextLink z odpowiedzi, aby pobrać następne wyniki.

- **za pośrednictwem plików** To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne ściąganie większych ilości danych. Dlatego jest to zalecane w przypadku dużych organizacji z ponad 100-K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL umożliwiające pobranie wszystkich danych z usługi Azure Storage. Dane z usługi Azure Storage można pobrać w następujący sposób:
  - Wywołaj interfejs API, aby uzyskać listę adresów URL pobierania ze wszystkimi danymi organizacji.
  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwórz dane zgodnie z tym, co chcesz.

Dane zbierane przy użyciu "_odpowiedzi JSON_ lub _za pośrednictwem plików_" to bieżąca migawka bieżącego stanu. Nie zawiera danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisywać dane we własnych magazynach danych.

> [!NOTE]
> O ile nie wskazano inaczej, wszystkie wymienione metody oceny punktu odniesienia zabezpieczeń eksportu są **_pełnym eksportem_** i **_urządzeniem_** (nazywanym również **_na urządzeniu_**)

## <a name="1-export-security-baselines-assessment-json-response"></a>1. Eksportowanie oceny punktów odniesienia zabezpieczeń (odpowiedź JSON)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Zwraca wszystkie oceny punktów odniesienia zabezpieczeń dla wszystkich urządzeń na poszczególnych urządzeniach. Zwraca tabelę z oddzielnym wpisem dla każdej unikatowej kombinacji elementów DeviceId, ProfileId i ConfigurationId.

### <a name="12-permissions"></a>1.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md), aby uzyskać szczegółowe informacje.

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|SecurityBaselinesAssessment.Read.All |"Odczytywanie wszystkich informacji o ocenach punktów odniesienia zabezpieczeń"
Delegowane (konto służbowe)|SecurityBaselinesAssessment.Read|"Odczytywanie informacji o ocenach punktów odniesienia zabezpieczeń"

### <a name="13-limitations"></a>1.3 Ograniczenia

- Maksymalny rozmiar strony to 200 000.
- Ograniczenia szybkości dla tego interfejsu API to 30 wywołań na minutę i 1000 wywołań na godzinę.

### <a name="14-parameters"></a>Parametry 1.4

- pageSize (wartość domyślna = 50 000): liczba wyników w odpowiedzi.
- $top: liczba wyników do zwrócenia (nie zwraca @odata.nextLink, więc nie ściąga wszystkich danych).

### <a name="15-http-request"></a>1.5 Żądanie HTTP

```http
GET /api/machines/baselineComplianceAssessmentByMachine
```

### <a name="16-properties-json-response"></a>1.6 Właściwości (odpowiedź JSON)

> [!NOTE]
> Każdy rekord to około 1 KB danych. Należy wziąć to pod uwagę podczas wybierania prawidłowego parametru pageSize.
>
> W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Używaj tylko udokumentowanych kolumn.
>
> Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynikowe dane wyjściowe nie muszą być zwracane w tej samej kolejności wymienionej w tej tabeli.

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
|configurationId|Ciąg|Unikatowy identyfikator określonej konfiguracji w benchmarku odniesienia.
|profileId|Ciąg|Unikatowy identyfikator ocenianego profilu.
|Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
|deviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
|isApplicable|Wartość logiczna|Wskazuje, czy konfiguracja ma zastosowanie do tego urządzenia.
|isCompliant|Wartość logiczna|Wskazuje, czy urządzenie jest zgodne z konfiguracją.
|Identyfikator|Ciąg|Unikatowy identyfikator rekordu, który jest kombinacją elementów DeviceId, ProfileId i ConfigurationId.
|Osversion|Ciąg|Określona wersja systemu operacyjnego działającego na urządzeniu.
|osPlatform|Ciąg|Platforma systemu operacyjnego uruchomiona na urządzeniu. Określone systemy operacyjne z odmianami w tej samej rodzinie, takie jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje [, zobacz Systemy operacyjne i platformy obsługiwane przez program TVM](tvm-supported-os.md) .
|rbacGroupId|Int|Identyfikator grupy kontroli dostępu opartej na rolach (RBAC). Jeśli urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
|rbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".
|DataCollectionTimeOffset|Datetime|Czas zbierania danych z urządzenia. To pole może nie być wyświetlane, jeśli nie zebrano żadnych danych.
|ComplianceCalculationTimeOffset|Datetime|Czas obliczania oceny.
|RecommendedValue|Ciąg|Zestaw oczekiwanych wartości dla bieżącego ustawienia urządzenia, które ma być reklamacji.
|Currentvalue|Ciąg|Zestaw wykrytych wartości znalezionych na urządzeniu.
|Źródło|Ciąg|Ścieżka rejestru lub inna lokalizacja używana do określania bieżącego ustawienia urządzenia.

## <a name="17-example"></a>Przykład 1.7

### <a name="171-request-example"></a>1.7.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="172-response-example"></a>Przykład odpowiedzi 1.7.2

```json
{ 
"@odata.context": " https://api.securitycenter.microsoft.com /api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetBaselineAssessment)", 
"value": [
{ 
    "id": "0000682575d5d473e82ed4d8680425d152411251_9e1b90be-e83e-485b-a5ec-4a429412e734_1.1.1", 
    "configurationId": "1.1.1", 
    "deviceId": "0000682575d5d473242222425d152411251", 
    "deviceName": " ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596 ", 
    "profileId": "9e1b90be-e83e-485b-a5ec-4a429412e734", 
    "osPlatform": "WindowsServer2019", 
    "osVersion": "10.0.17763.2330", 
    "rbacGroupId": 86, 
    "rbacGroupName": "UnassignedGroup", 
    "isApplicable": true, 
    "isCompliant": false, 
    "dataCollectionTimeOffset": "2021-12-22T00:08:02.478Z", 
    "recommendedValue": [ 
                    "Greater than or equal '24'" 
                ], 
                "currentValue": [ 
                    "24" 
                ], 
                "source": [ 
                    "password_hist_len"
                ], 
}
```

## <a name="2-export-security-baselines-assessment-via-files"></a>2. Eksportowanie oceny punktów odniesienia zabezpieczeń (za pośrednictwem plików)

### <a name="21-api-method-description"></a>Opis metody interfejsu API w wersji 2.1

Zwraca wszystkie oceny punktów odniesienia zabezpieczeń dla wszystkich urządzeń na poszczególnych urządzeniach. Zwraca tabelę z oddzielnym wpisem dla każdej unikatowej kombinacji elementów DeviceId, ProfileId i ConfigurationId.

### <a name="22-limitations"></a>2.2 Ograniczenia

- Ograniczenia szybkości dla tego interfejsu API to 5 wywołań na minutę i 20 wywołań na godzinę.

### <a name="23-url"></a>Adres URL 2.3

```http
GET /api/machines/BaselineComplianceAssessmentExport
```

### <a name="24-parameters"></a>Parametry 2.4

- sasValidHours: liczba godzin, przez które adresy URL pobierania będą ważne (maksymalnie 24 godziny). 

### <a name="25-properties-via-files"></a>2.5 Właściwości (za pośrednictwem plików)

> [!NOTE]
> Pliki są skompresowane gzip & w wielowierszowym formacie JSON.
>
>Adresy URL pobierania są ważne tylko przez 3 godziny; W przeciwnym razie można użyć parametru .
>
>Aby zmaksymalizować szybkość pobierania, upewnij się, że pobierasz dane z tego samego regionu świadczenia usługi Azure, w którym znajdują się twoje dane.
>
>Każdy rekord to około 1 KB danych. Należy wziąć to pod uwagę podczas wybierania parametru pageSize, który działa dla Ciebie.
>
>W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Używaj tylko udokumentowanych kolumn.

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
|Eksportowanie plików|array[string]|Lista adresów URL pobierania plików przechowujących bieżącą migawkę organizacji.
|GeneratedTime|Ciąg|Czas wygenerowania eksportu.

## <a name="26-example"></a>Przykład 2.6

### <a name="261-request-example"></a>2.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentExport
```

### <a name="262-response-example"></a>Przykład odpowiedzi 2.6.2

```json
{ 
    "@odata.context": "https://api.securitycenter. contoso.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse", 
    "exportFiles": 
    [ 
    "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId= OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00000-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv=ABCD", 
   "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00001-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv= ABCD", 
    ], 
    "generatedTime": "2021-01-11T11:01:00Z" 
}
```

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie profilów oceny punktów odniesienia zabezpieczeń](get-security-baselines-assessment-profiles.md)
- [Uzyskiwanie konfiguracji oceny punktów odniesienia zabezpieczeń](get-security-baselines-assessment-configurations.md)
