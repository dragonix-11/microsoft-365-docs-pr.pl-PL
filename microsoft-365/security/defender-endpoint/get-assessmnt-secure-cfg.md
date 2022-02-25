---
title: Eksportowanie bezpiecznego oceny konfiguracji na urządzenie
description: Zwraca pozycję dla każdej unikatowej kombinacji wartości DeviceId, ConfigurationId.
keywords: api, apis, ocena eksportu, ocena na urządzenie, raport oceny luk w zabezpieczeniach, ocena luk w zabezpieczeniach urządzenia, raport na temat luki w zabezpieczeniach urządzenia, bezpieczna ocena konfiguracji, bezpieczny raport konfiguracji, ocena luk w oprogramowaniu, raport z lukami w oprogramowaniu, raport o lukach w zabezpieczeniach komputera,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: ab33db7fb7acf1969973a7af8f80ea97ef3d378f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2021
ms.locfileid: "62959225"
---
# <a name="export-secure-configuration-assessment-per-device"></a>Eksportowanie bezpiecznego oceny konfiguracji na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
Zwraca wszystkie konfiguracje i ich stan na podstawie  per-device.

Istnieją różne wywołania interfejsu API w celu uzyskania różnych typów danych. Ponieważ ilość danych może być duża, można ją pobrać na dwa sposoby:

- [Eksportowanie bezpiecznej oceny konfiguracji **OData**](#1-export-secure-configuration-assessment-odata): Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi Json, zgodnie z protokołem OData. Ta metoda jest najlepsza dla _małych organizacji, które mają mniej niż 100 K urządzeń_. Odpowiedź jest podzielony na strony, \@więc można użyć pola odata.nextLink z odpowiedzi w celu pobrania następnych wyników.

- [Eksportowanie bezpiecznego **oceny konfiguracji za pośrednictwem**](#2-export-secure-configuration-assessment-via-files) plików: To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Dlatego jest zalecane dla dużych organizacji, które mają ponad 100 K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób:

  - Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji.

  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

Dane zbierane (przy użyciu źródeł _danych OData_ lub za pośrednictwem _plików) to_ bieżąca migawka stanu bieżącego, która nie zawiera danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisać te dane we własnych magazynach danych.

> [!Note]
>
> O ile nie zaznaczono inaczej, wszystkie wymienione metody **** oceny eksportu są pełne i według **_urządzenia_** (określane również jako **_urządzenia_**).

## <a name="1-export-secure-configuration-assessment-odata"></a>1. Eksportowanie bezpiecznej oceny konfiguracji (OData)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Ta odpowiedź interfejsu API zawiera ocenę bezpiecznej konfiguracji na twoich ujawnionych urządzeniach i zwraca wpis dla każdej unikatowej kombinacji deviceId, ConfigurationId.

#### <a name="111-limitations"></a>1.1.1 Ograniczenia

- Maksymalny rozmiar strony to 200 000.

- Ograniczenia stawek dla tego interfejsu API to 30 połączeń na minutę i 1000 połączeń na godzinę.

### <a name="12-permissions"></a>1.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender](apis-intro.md) , aby uzyskać szczegółowe informacje.

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
---|---|---
Aplikacja | Vulnerability.Read.All | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe) | Vulnerability.Read | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

### <a name="13-url"></a>1.3 Adres URL

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 Parametry

- wartość domyślna \(rozmiar strony = 50 000\) — liczba wyników w odpowiedzi

- \$top — liczba zwracanych wyników \(nie powoduje \@zwrócenia ciągu odata.nextLink i dlatego nie powoduje zwrócenia wszystkich danych\)

### <a name="15-properties"></a>1,5 Właściwości

>[!Note]
>
>- Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości.  Podczas uruchamiania tego interfejsu API wynik nie musi być zwracany w tej samej kolejności, w tej tabeli.
>
>- Niektóre dodatkowe kolumny mogą być zwracane w odpowiedzi. Te kolumny są tymczasowe i mogą zostać usunięte. Należy używać tylko kolumn z dokumentami.
>

Właściwość (identyfikator) | Typ danych | Opis | Przykład zwracanej wartości
:---|:---|:---|:---
ConfigurationCategory | ciąg | Kategoria lub grupowanie, do których należy konfiguracja: Aplikacja, system operacyjny, sieć, konta, kontrolki zabezpieczeń | Mechanizmy kontroli zabezpieczeń
ConfigurationId | ciąg | Unikatowy identyfikator określonej konfiguracji | scid-10000
ConfigurationImpact | ciąg | Wpływ oceny konfiguracji na ogólny wynik konfiguracji (1–10) | 9
ConfigurationName | ciąg | Nazwa wyświetlana konfiguracji | Urządzenia w programie Microsoft Defender dla punktu końcowego
ConfigurationSubcategory | ciąg | Podkategoria lub podgrupowanie, do którego należy konfiguracja. W wielu przypadkach opisano konkretne funkcje. | Urządzenia wyniesne
DeviceId | ciąg | Unikatowy identyfikator urządzenia w usłudze. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | ciąg | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia. | johnlaptop.europe.contoso.com
IsApplicable | bool | Wskazuje, czy konfiguracja lub zasady mają zastosowanie. | true
IsCompliant | bool | Wskazuje, czy konfiguracja lub zasady są poprawnie skonfigurowane. | fałsz
IsExpectedUserImpact | bool | Wskazuje, czy jeśli konfiguracja zostanie zastosowana, będzie mieć wpływ na użytkowników | true
OSPlatform | ciąg | Platforma systemu operacyjnego działającego na urządzeniu. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 10 i Windows 7. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm. | Windows10
RbacGroupName | ciąg | Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak". | Serwery
ZalecenieReference | ciąg | Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem. | sca-_-scid-20000
Timestamp | ciąg | Ostatni czas, gdy konfiguracja była widziana na urządzeniu | 2020-11-03 10:13:34.8476880

### <a name="16-examples"></a>1.6 Przykłady

#### <a name="161-request-example"></a>1.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pageSize=5 
```

#### <a name="162-response-example"></a>1.6.2 Przykład odpowiedzi

```json
{
    "@odata.context": "api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetConfiguration)",
    "value": [
        {
            "deviceId": "00013ee62c6b12345b10214e1801b217b50ab455c293d",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_5d96860d69c73fdd06fc8d1679e1eb73eceb8330",
            "osPlatform": "Windows10",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol – Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-20000",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Onboard Devices",
            "configurationImpact": 9,
            "isCompliant": false,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Onboard devices to Microsoft Defender for Endpoint",
            "recommendationReference": "sca-_-scid-20000"
        },
        {
            "deviceId": "0002a1de123456a8c06de736785395d4ce7610",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol – Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-39",
            "configurationCategory": "OS",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Enable 'Domain member: Digitally sign secure channel data (when possible)'",
            "recommendationReference": "sca-_-scid-39"
        },
        {
            "deviceId": "00044f912345daf759462bde6bd733d6a9c56ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45612eeb224d2de2f5ea3142726e63f16a.DomainPII_21eed80d086e76dbfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-6093",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Antivirus",
            "configurationImpact": 5,
            "isCompliant": false,
            "isApplicable": false,
            "isExpectedUserImpact": false,
            "configurationName": "Enable Microsoft Defender Antivirus real-time behavior monitoring for Linux",
            "recommendationReference": "sca-_-scid-6093"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-secure-configuration-assessment-via-files"></a>2. Eksportowanie bezpiecznego oceniania konfiguracji (za pośrednictwem plików)

### <a name="21-api-method-description"></a>Opis metody interfejsu API 2.1

Ta odpowiedź interfejsu API zawiera ocenę bezpiecznej konfiguracji na twoich ujawnionych urządzeniach i zwraca wpis dla każdej unikatowej kombinacji deviceId, ConfigurationId.

#### <a name="212-limitations"></a>2.1.2 Ograniczenia

Ograniczenia stawek dla tego interfejsu API to 5 połączeń na minutę i 20 połączeń na godzinę.

### <a name="22-permissions"></a>2.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
---|---|---
Aplikacja | Vulnerability.Read.All | \'Czytanie informacji o Zarządzanie zagrożeniami i lukami luk w zabezpieczeniach\'
Delegowane (konto służbowe) | Vulnerability.Read | \'Czytanie informacji o Zarządzanie zagrożeniami i lukami luk w zabezpieczeniach\'

### <a name="23-url"></a>2.3 Adres URL

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>Parametry

- sasValidHours — liczba godzin, przez które będą ważne adresy URL pobierania (maksymalnie 24 godziny).

### <a name="25-properties"></a>2,5 Właściwości

>[!Note]
>
>- Pliki są skompresowane w formacie & wieloliniowym Json.
>
>- Adresy URL pobierania są ważne tylko przez 3 godziny. w przeciwnym razie możesz użyć parametru.
>
>- Aby uzyskać maksymalną szybkość pobierania danych, możesz się upewnić, że pobierasz pliki z tego samego regionu platformy Azure, w którym znajdują się Twoje dane.
>
Właściwość (identyfikator) | Typ danych | Opis | Przykład zwracanej wartości
:---|:---|:---|:---
Eksportowanie plików | arraystring\[\] | Lista adresów URL pobierania plików z bieżącą migawką organizacji | [  Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2” ]
GeneratedTime | ciąg | Godzina wygenerowania eksportu. | 2021-05-20T08:00:00Z ]

### <a name="26-examples"></a>2.6 Przykłady

#### <a name="261-request-example"></a>2.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentExport
```

#### <a name="262-response-example"></a>2.6.2 Przykład odpowiedzi

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#contoso.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Zobacz też

- [Eksportowanie metod i właściwości oceny na urządzenie](get-assessmnt-1methods-properties.md)

- [Eksportowanie oceny spisu oprogramowania na urządzenie](get-assessmnt-software-inventory.md)

- [Ocena luk w zabezpieczeniach oprogramowania na urządzeniu](get-assessmnt-software-vulnerabilities.md)

Inne powiązane

- [Zagrożenia oparte na & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)

- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
