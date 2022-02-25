---
title: Ocena luk w zabezpieczeniach oprogramowania na urządzeniu
description: Odpowiedź interfejsu API jest na urządzenie i zawiera narażone na oprogramowanie zainstalowane na twoich urządzeniach, a także wszelkie znane luki w zabezpieczeniach w tych produktach oprogramowania. Ta tabela zawiera również informacje o systemie operacyjnym, identyfikatory CVE oraz informacje o ważności luk w zabezpieczeniach.
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
ms.openlocfilehash: 951f78ba361a12e404a5cce2071f931eab30c43f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2021
ms.locfileid: "62959223"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Ocena luk w zabezpieczeniach oprogramowania na urządzeniu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
Wszystkie znane luki w zabezpieczeniach oprogramowania i ich szczegóły dotyczące wszystkich urządzeń są zwracane na podstawie danych urządzenia.

Istnieją różne wywołania interfejsu API w celu uzyskania różnych typów danych. Ponieważ ilość danych może być bardzo duża, można ją pobrać na dwa sposoby:

- [Ocena luk w zabezpieczeniach oprogramowania OData](#1-export-software-vulnerabilities-assessment-odata)  Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi Json, zgodnie z protokołem OData. Ta metoda jest najlepsza dla _małych organizacji, które mają mniej niż 100 K urządzeń_. Odpowiedź jest podzielony na strony, \@więc można użyć pola odata.nextLink z odpowiedzi w celu pobrania następnych wyników.

- [Ocena luk w zabezpieczeniach oprogramowania za pośrednictwem plików](#2-export-software-vulnerabilities-assessment-via-files) To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Dlatego jest zalecane dla dużych organizacji, które mają ponad 100 K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób:

  - Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji.

  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

Dane zbierane (przy użyciu źródeł _danych OData_ lub za pośrednictwem _plików) to_ bieżąca migawka stanu bieżącego, która nie zawiera danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisać te dane we własnych magazynach danych.

> [!Note]
>
> O ile nie zaznaczono inaczej, wszystkie wymienione metody **** oceny eksportu są pełne i według **_urządzenia_** (określane również jako **_urządzenia_**).

## <a name="1-export-software-vulnerabilities-assessment-odata"></a>1. Ocena luk w zabezpieczeniach oprogramowania (OData)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji deviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="limitations"></a>Ograniczenia

>- Maksymalny rozmiar strony to 200 000.
>
>- Ograniczenia stawek dla tego interfejsu API to 30 połączeń na minutę i 1000 połączeń na godzinę.

### <a name="12-permissions"></a>1.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
---|---|---
Aplikacja | Vulnerability.Read.All | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe) | Vulnerability.Read | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

### <a name="13-url"></a>1.3 Adres URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Parametry

- pageSize (domyślna = 50 000) — liczba wyników w odpowiedzi
- $top — liczba wyników do zwrócenia (nie zwraca @odata.nextLink i dlatego nie wyciąga wszystkich danych)

### <a name="15-properties"></a>1,5 Właściwości
>
>[!Note]
>
>- Każdy rekord to w przybliżeniu 1 KB danych. Należy wziąć to pod uwagę podczas wybierania odpowiedniego parametru pageSize.
>
>- Niektóre dodatkowe kolumny mogą być zwracane w odpowiedzi. Te kolumny są tymczasowe i mogą zostać usunięte. Należy używać tylko kolumn z dokumentami.
>
>- Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości.  Podczas uruchamiania tego interfejsu API wynik nie musi być zwracany w tej samej kolejności, w tej tabeli.
>

Właściwość (identyfikator) | Typ danych | Opis | Przykład zwracanej wartości
:---|:---|:---|:---
CveId | ciąg | Unikatowy identyfikator przypisany do luki w zabezpieczeniach systemu cve (Common Vulnerabilities and Exposures). | CVE-2020-15992
CvssScore | ciąg | Wynik CVSS dla CVE. | 6.2
DeviceId | ciąg | Unikatowy identyfikator urządzenia w usłudze. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | ciąg | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia. | johnlaptop.europe.contoso.com
DiskPaths  | Arraystring\[\] | Dowód dysku, że produkt jest zainstalowany na urządzeniu. | [ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
ExploitabilityLevel | ciąg | Poziom wykorzystania tej luki (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit) | ExploitIsInKit
FirstSeenTimestamp | ciąg | Po raz pierwszy cvE tego produktu zostało widziane na urządzeniu. | 2020-11-03 10:13:34.8476880
Identyfikator | ciąg | Unikatowy identyfikator rekordu. | 123ABG55_573AG&mnp!
LastSeenTimestamp | ciąg | Ostatni czas, gdy cvE było widoczne na urządzeniu. | 2020-11-03 10:13:34.8476880
OSPlatform | ciąg | Platforma systemu operacyjnego działającego na urządzeniu. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 10 i Windows 7. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm. | Windows10
RbacGroupName  | ciąg | Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak". | Serwery
ZalecenieReference | ciąg | Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem. | va-_-microsoft-_-silverlight
RecommendedSecurityUpdate (opcjonalnie) | ciąg | Nazwa lub opis aktualizacji zabezpieczeń udostępnianej przez dostawcę oprogramowania w celu rozwiązania problemu. | Aktualizacje zabezpieczeń z kwietnia 2020 r.
RecommendedSecurityUpdateId (opcjonalnie) | ciąg | Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikator odpowiednich wytycznych lub artykułów z bazy wiedzy (KB) | 4550961
RegistryPaths  | Arraystring\[\] | Dowód rejestru, że produkt jest zainstalowany w urządzeniu. | [ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
Nazwa_oprogramowania | ciąg | Nazwa produktu. | chrome
SoftwareVendor | ciąg | Nazwa dostawcy oprogramowania. | google
SoftwareVersion | ciąg | Numer wersji produktu oprogramowania. | 81.0.4044.138
VulnerabilitySeverityLevel  | ciąg | Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i dynamicznych czynników, na które wpływa poziom zagrożeń. | Średni

### <a name="16-examples"></a>1.6 Przykłady

#### <a name="161-request-example"></a>1.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a>1.6.2 Przykład odpowiedzi

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetVulnerability)",
    "value": [
        {
            "id": "00044f612345baf759462dbe6db733b6a9c59ab4_edge_10.0.17763.1637__",
            "deviceId": "00044f612345daf756462bde6bd733b9a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d089e79bdfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "edge",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-edge"
        },
        {
            "id": "00044f912345baf756462bde6db733b9a9c56ad4_.net_framework_4.0.0.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e79bdfa178eabfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-.net_framework"
        },
        {
            "id": "00044f912345baf756462dbe6db733d6a9c59ab4_system_center_2012_endpoint_protection_4.10.209.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eed80b089e79bdfa178eadfa25e8be6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-system_center_2012_endpoint_protection"
        },
        {
            "id": "00044f612345bdaf759462dbe6bd733b6a9c59ab4_onedrive_20.245.1206.2__",
            "deviceId": "00044f91234daf759492dbe6bd733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_189663d45612eed224b2be2f5ea3142729e63f16a.DomainPII_21eed80b086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.245.1206.2",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2944539346-1310925172-2349113062-1001\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive"
        },
        {
            "id": "00044f912345daf759462bde6db733b6a9c56ab4_windows_10_10.0.17763.1637__",
            "deviceId": "00044f912345daf756462dbe6db733d6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eeb224d2be2f5ea3142729e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-windows_10"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. Ocena luk w zabezpieczeniach oprogramowania (za pośrednictwem plików)

### <a name="21-api-method-description"></a>Opis metody interfejsu API 2.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji deviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="212-limitations"></a>2.1.2 Ograniczenia

Ograniczenia stawek dla tego interfejsu API to 5 połączeń na minutę i 20 połączeń na godzinę.

### <a name="22-permissions"></a>2.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje](apis-intro.md).

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
---|---|---
Aplikacja | Vulnerability.Read.All | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe) | Vulnerability.Read | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

### <a name="23-url"></a>2.3 Adres URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Parametry

- sasValidHours — liczba godzin, przez które będą ważne adresy URL pobierania (maksymalnie 24 godziny)

### <a name="25-properties"></a>2,5 Właściwości

>[!Note]
>
>- Pliki są skompresowane w formacie & wieloliniowym Json.
>
>- Adresy URL pobierania są ważne tylko przez 3 godziny. w przeciwnym razie możesz użyć parametru.
>
>- Aby uzyskać maksymalną szybkość pobierania danych, możesz się upewnić, że pobierasz pliki z tego samego regionu platformy Azure, w którym znajdują się Twoje dane.
>

>[!Note]
>
>- Każdy rekord to w przybliżeniu 1 KB danych. Należy wziąć to pod uwagę podczas wybierania odpowiedniego parametru pageSize.
>
>- Niektóre dodatkowe kolumny mogą być zwracane w odpowiedzi. Te kolumny są tymczasowe i mogą zostać usunięte. Należy używać tylko kolumn z dokumentami.
>

Właściwość (identyfikator) | Typ danych | Opis | Przykład zwracanej wartości
:---|:---|:---|:---
Eksportowanie plików | arraystring\[\]  | Lista adresów URL pobierania plików z bieżącą migawką organizacji. | [  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]
GeneratedTime | ciąg | Godzina wygenerowania eksportu. | 2021-05-20T08:00:00Z

### <a name="26-examples"></a>2.6 Przykłady

#### <a name="261-request-example"></a>2.6.1 Przykład żądania

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a>2.6.2 Przykład odpowiedzi

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c002.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Zobacz też

- [Eksportowanie metod i właściwości oceny na urządzenie](get-assessmnt-1methods-properties.md)

- [Eksportowanie bezpiecznego oceny konfiguracji na urządzenie](get-assessmnt-secure-cfg.md)

- [Eksportowanie oceny spisu oprogramowania na urządzenie](get-assessmnt-software-inventory.md)

Inne powiązane

- [Zagrożenia oparte na & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)

- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
