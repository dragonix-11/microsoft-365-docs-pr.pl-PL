---
title: Eksportowanie oceny bezpiecznej konfiguracji na urządzenie
description: Zwraca wpis dla każdej unikatowej kombinacji identyfikatora DeviceId, ConfigurationId.
keywords: api, apis, export assessment, per device assessment, vulnerability assessment report, device vulnerability assessment, device vulnerability report, secure configuration assessment, secure configuration report, secure configuration report, software vulnerabilities assessment, software vulnerability report, vulnerability report, vulnerability report by machine,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6d706dc8552490b7705cc23fca4751f810211d47
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839303"
---
# <a name="export-secure-configuration-assessment-per-device"></a>Eksportowanie oceny bezpiecznej konfiguracji na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Zwraca wszystkie konfiguracje i ich stan na poszczególnych urządzeniach.

Istnieją różne wywołania interfejsu API umożliwiające pobieranie różnych typów danych. Ponieważ ilość danych może być duża, można pobrać je na dwa sposoby:

- [Eksportuj **odpowiedź JSON** oceny bezpiecznej konfiguracji](#1-export-secure-configuration-assessment-json-response): interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi w formacie JSON. Ta metoda jest najlepsza w _przypadku małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K_. Odpowiedź jest podzielona na strony, więc możesz użyć \@pola odata.nextLink z odpowiedzi, aby pobrać następne wyniki.

- [Eksportowanie bezpiecznej oceny konfiguracji **za pośrednictwem plików**](#2-export-secure-configuration-assessment-via-files): to rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne ściąganie większych ilości danych. W związku z tym jest zalecane w przypadku dużych organizacji z ponad 100-K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL umożliwiające pobranie wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobranie wszystkich danych z usługi Azure Storage w następujący sposób:

  - Wywołaj interfejs API, aby uzyskać listę adresów URL pobierania ze wszystkimi danymi organizacji.

  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwórz dane zgodnie z tym, co chcesz.

Zbierane dane (przy użyciu _odpowiedzi JSON_ lub _za pośrednictwem plików_) są bieżącą migawką bieżącego stanu i nie zawierają danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisywać dane we własnych magazynach danych.

> [!NOTE]
> O ile nie wskazano inaczej, wszystkie wymienione metody oceny eksportu to **_pełny eksport_** i **_urządzenie_** (określane również jako **_dla każdego urządzenia_**).

## <a name="1-export-secure-configuration-assessment-json-response"></a>1. Eksportowanie oceny bezpiecznej konfiguracji (odpowiedź JSON)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Ta odpowiedź interfejsu API zawiera ocenę bezpiecznej konfiguracji na uwidocznionych urządzeniach i zwraca wpis dla każdej unikatowej kombinacji identyfikatora DeviceId, ConfigurationId.

#### <a name="111-limitations"></a>Ograniczenia 1.1.1

- Maksymalny rozmiar strony to 200 000.

- Ograniczenia szybkości dla tego interfejsu API to 30 wywołań na minutę i 1000 wywołań na godzinę.

### <a name="12-permissions"></a>1.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](apis-intro.md), aby uzyskać szczegółowe informacje.

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Vulnerability.Read.All|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'
Delegowane (konto służbowe)|Luka w zabezpieczeniach.Odczyt|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'

### <a name="13-url"></a>Adres URL 1.3

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>Parametry 1.4

- pageSize \(default = 50 000\): liczba wyników w odpowiedzi.
- \$top: Liczba wyników do zwrócenia \(nie zwraca \@wartości odata.nextLink i dlatego nie ściąga wszystkich danych\).

### <a name="15-properties"></a>1.5 Właściwości

> [!NOTE]
>
> - Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynikowe dane wyjściowe nie muszą być zwracane w tej samej kolejności wymienionej w tej tabeli.
> - W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Użyj tylko udokumentowanych kolumn.

<br>

****

Właściwość (ID)|Typ danych|Opis|Przykład zwracanej wartości
---|---|---|---
ConfigurationCategory|Ciąg|Kategoria lub grupowanie, do których należy konfiguracja: aplikacja, system operacyjny, sieć, konta, mechanizmy kontroli zabezpieczeń|Mechanizmy kontroli zabezpieczeń
ConfigurationId|Ciąg|Unikatowy identyfikator określonej konfiguracji|scid-10000
ConfigurationImpact|Ciąg|Oceniany wpływ konfiguracji na ogólny wynik konfiguracji (1–10)|9
Configurationname|Ciąg|Nazwa wyświetlana konfiguracji|Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender
KonfiguracjaSubcategory|Ciąg|Podkategoria lub podgrupa, do której należy konfiguracja. W wielu przypadkach opisano określone możliwości lub funkcje.|Dołączanie urządzeń
Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.|johnlaptop.europe.contoso.com
IsApplicable|Bool|Wskazuje, czy konfiguracja lub zasady mają zastosowanie|True
IsCompliant|Bool|Wskazuje, czy konfiguracja lub zasady są prawidłowo skonfigurowane|False
IsExpectedUserImpact|Bool|Wskazuje, czy będzie to miało wpływ na użytkownika, jeśli konfiguracja zostanie zastosowana|True
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu. Wskazuje to określone systemy operacyjne, w tym odmiany w tej samej rodzinie, takie jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy tvm.|Windows10 i Windows 11
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".|Serwery
ZalecenieReferencja|Ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.|sca-_-scid-20000
Sygnatury czasowej|Ciąg|Ostatni raz konfiguracja była widoczna na urządzeniu|2020-11-03 10:13:34.8476880
|

### <a name="16-examples"></a>1.6 Przykłady

#### <a name="161-request-example"></a>1.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pageSize=5
```

#### <a name="162-response-example"></a>Przykład odpowiedzi 1.6.2

```json
{
    "@odata.context": "api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetConfiguration)",
    "value": [
        {
            "deviceId": "00013ee62c6b12345b10214e1801b217b50ab455c293d",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_5d96860d69c73fdd06fc8d1679e1eb73eceb8330",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
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

## <a name="2-export-secure-configuration-assessment-via-files"></a>2. Eksportowanie oceny bezpiecznej konfiguracji (za pośrednictwem plików)

### <a name="21-api-method-description"></a>Opis metody interfejsu API w wersji 2.1

Ta odpowiedź interfejsu API zawiera ocenę bezpiecznej konfiguracji na uwidocznionych urządzeniach i zwraca wpis dla każdej unikatowej kombinacji identyfikatora DeviceId, ConfigurationId.

#### <a name="212-limitations"></a>2.1.2 Ograniczenia

Ograniczenia szybkości dla tego interfejsu API to 5 wywołań na minutę i 20 wywołań na godzinę.

### <a name="22-permissions"></a>2.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Vulnerability.Read.All|\'Przeczytaj informacje o lukach w zabezpieczeniach "Zarządzanie zagrożeniami i lukami"\'
Delegowane (konto służbowe)|Luka w zabezpieczeniach.Odczyt|\'Przeczytaj informacje o lukach w zabezpieczeniach "Zarządzanie zagrożeniami i lukami"\'

### <a name="23-url"></a>Adres URL 2.3

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>Parametry

- sasValidHours: liczba godzin, przez które adresy URL pobierania będą ważne (maksymalnie 24 godziny).

### <a name="25-properties"></a>2.5 Właściwości

> [!NOTE]
>
> - Pliki są skompresowane gzip & w wielowierszowym formacie JSON.
> - Adresy URL pobierania są ważne tylko przez 3 godziny; W przeciwnym razie można użyć parametru .
> - Aby uzyskać maksymalną szybkość pobierania danych, możesz upewnić się, że pobierasz dane z tego samego regionu świadczenia usługi Azure, w którym znajdują się twoje dane.

<br>

****

Właściwość (ID)|Typ danych|Opis|Przykład zwracanej wartości
---|---|---|---
Eksportowanie plików|ciąg tablicy\[\]|Lista adresów URL pobierania plików przechowujących bieżącą migawkę organizacji|["Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Ciąg|Czas wygenerowania eksportu.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Przykłady

#### <a name="261-request-example"></a>2.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentExport
```

#### <a name="262-response-example"></a>Przykład odpowiedzi 2.6.2

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

- [Eksportowanie metod oceny i właściwości na urządzenie](get-assessment-methods-properties.md)
- [Eksportowanie oceny spisu oprogramowania na urządzenie](get-assessment-software-inventory.md)
- [Eksportowanie oceny luk w zabezpieczeniach oprogramowania na urządzenie](get-assessment-software-vulnerabilities.md)

Inne powiązane

- [& zarządzanie lukami w zabezpieczeniach zagrożeń opartych na ryzyku](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
