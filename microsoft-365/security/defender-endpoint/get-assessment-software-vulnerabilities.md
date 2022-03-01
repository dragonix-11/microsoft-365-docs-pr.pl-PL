---
title: Ocena luk w zabezpieczeniach oprogramowania na urządzeniu
description: Odpowiedź interfejsu API jest na urządzenie i zawiera narażone na oprogramowanie zainstalowane na twoich urządzeniach, które są dostępne, oraz wszelkie znane luki w zabezpieczeniach tych produktów. Ta tabela zawiera również informacje o systemie operacyjnym, identyfikatory CVE oraz informacje o ważności luk w zabezpieczeniach.
keywords: api, apis, ocena eksportu, ocena na urządzenie, raport oceny luk w zabezpieczeniach, ocena luk w zabezpieczeniach urządzenia, raport na temat luki w zabezpieczeniach urządzenia, bezpieczna ocena konfiguracji, bezpieczny raport konfiguracji, ocena luk w oprogramowaniu, raport z lukami w oprogramowaniu, raport o lukach w zabezpieczeniach komputera,
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
ms.openlocfilehash: 5d10b96e1d5abfe1c9e9a87b9800dafba081c961
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013271"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Ocena luk w zabezpieczeniach oprogramowania na urządzeniu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Wszystkie znane luki w zabezpieczeniach oprogramowania i ich szczegóły dotyczące wszystkich urządzeń są zwracane na podstawie danych urządzenia.

Różne wywołania interfejsu API mają różne typy danych. Ponieważ ilość danych może być duża, można ją pobrać na dwa sposoby:

1. [Eksportowanie odpowiedzi **JSON oceny luk w oprogramowaniu**](#1-export-software-vulnerabilities-assessment-json-response)  Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi Json. Ta metoda jest najlepsza dla _małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K_. Odpowiedź jest podzielony na strony, \@więc można użyć pola odata.nextLink z odpowiedzi w celu pobrania następnych wyników.

2. [Ocena luk w zabezpieczeniach oprogramowania za **pośrednictwem plików**](#2-export-software-vulnerabilities-assessment-via-files) To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Pliki za pośrednictwem są zalecane dla dużych organizacji, które mają ponad 100 urządzeń o przekierowywce. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób:
   - Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji.
   - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

3. [Odpowiedź JSON oceny luk w **zabezpieczeniach oprogramowania eksportu różnicowego**](#3-delta-export-software-vulnerabilities-assessment-json-response)  Zwraca tabelę z wpisem dla każdej unikatowej kombinacji: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId i EventTimestamp.
Interfejs API wyciąga dane z Twojej organizacji jako odpowiedzi Json. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników.

   Pełna "ocena luk w oprogramowaniu (odpowiedź JSON)" służy do uzyskania pełnej migawki oceny luk w oprogramowaniu organizacji za pomocą urządzenia. Jednak wywołanie interfejsu API eksportu różnicowego jest używane do pobierania tylko zmian, które miały miejsce między wybraną datą a bieżącą datą (wywołaniem interfejsu API różnicy). Zamiast pełnego eksportu z dużą ilością danych za każdym razem będziesz otrzymywać tylko określone informacje dotyczące nowych, stałych i zaktualizowanych luk w zabezpieczeniach. Za pomocą wywołania interfejsu API odpowiedzi JSON eksportu różnicowego można również obliczać różne wskaźniki KPI, na przykład "ile luk usunięto?". lub "ile nowych luk w zabezpieczeniach dodano do mojej organizacji?".

   Ponieważ wywołanie interfejsu API odpowiedzi JSON Delta w celu wykorzystania luk w oprogramowaniu zwraca dane tylko dla docelowego zakresu dat, nie jest uznawane za pełne _wyeksportowanie_.

Dane zbierane (za pomocą odpowiedzi _Jsona_ lub za pośrednictwem _plików) to_ bieżąca migawka bieżącego stanu. Nie zawiera ona danych historycznych. Aby zbierać dane historyczne, klienci muszą je zapisywać we własnych magazynach danych.

> [!NOTE]
> O ile nie zaznaczono inaczej, wszystkie wymienione metody **** oceny eksportu są pełne i według **_urządzenia_** (określane również jako **_urządzenia_**).

## <a name="1-export-software-vulnerabilities-assessment-json-response"></a>1. Ocena luk w zabezpieczeniach oprogramowania (odpowiedź JSON)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji deviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="111-limitations"></a>1.1.1 Ograniczenia

- Maksymalny rozmiar strony to 200 000.
- Ograniczenia stawek dla tego interfejsu API to 30 połączeń na minutę i 1000 połączeń na godzinę.

### <a name="12-permissions"></a>1.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Vulnerability.Read.All|\'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe)|Vulnerability.Read|\'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

### <a name="13-url"></a>1.3 Adres URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Parametry

- pageSize (wartość domyślna = 50 000): Liczba wyników w odpowiedzi.
- $top: Liczba wyników do zwrócenia (nie zwraca @odata.nextLink, a więc nie powoduje zwrócenia wszystkich danych).

### <a name="15-properties"></a>1,5 Właściwości

> [!NOTE]
>
> - Każdy rekord to około 1 KB danych. Należy wziąć to pod uwagę podczas wybierania odpowiedniego parametru pageSize.
> - Niektóre dodatkowe kolumny mogą być zwracane w odpowiedzi. Te kolumny są tymczasowe i mogą zostać usunięte. Należy używać tylko kolumn z dokumentami.
> - Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynik nie musi być zwracany w tej samej kolejności, w tej tabeli.

<br>

****

Właściwość (identyfikator)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
CveId|Ciąg|Unikatowy identyfikator przypisany do luki w zabezpieczeniach systemu cve (Common Vulnerabilities and Exposures).|CVE-2020-15992
CvssScore|Ciąg|Wynik CVSS dla CVE.|6.2
DeviceId|Ciąg|Unikatowy identyfikator urządzenia w usłudze.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.|johnlaptop.europe.contoso.com
DiskPaths|Arraystring\[\]|Dowód dysku, że produkt jest zainstalowany na urządzeniu.|[ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
ExploitabilityLevel|Ciąg|Poziom wykorzystania tej luki (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit
FirstSeenTimestamp|Ciąg|Po raz pierwszy cvE tego produktu zostało widziane na urządzeniu.|2020-11-03 10:13:34.8476880
Identyfikator|Ciąg|Unikatowy identyfikator rekordu.|123ABG55_573AG&mnp!
LastSeenTimestamp|Ciąg|Ostatni czas, gdy cvE było widoczne na urządzeniu.|2020-11-03 10:13:34.8476880
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu. Ta właściwość wskazuje określone systemy operacyjne z odmianami tej samej rodziny, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm.|Windows 10 i Windows 11
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".|Serwery
ZalecenieReference|Ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.|va-_-microsoft-_-silverlight
RecommendedSecurityUpdate (opcjonalnie)|Ciąg|Nazwa lub opis aktualizacji zabezpieczeń udostępnianej przez dostawcę oprogramowania w celu rozwiązania problemu.|Aktualizacje zabezpieczeń z kwietnia 2020 r.
RecommendedSecurityUpdateId (opcjonalnie)|Ciąg|Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikator odpowiednich wytycznych lub artykułów z bazy wiedzy (KB)|4550961
RegistryPaths|Arraystring\[\]|Dowód rejestru, że produkt jest zainstalowany w urządzeniu.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
Nazwa_oprogramowania|Ciąg|Nazwa produktu.|Chrome
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.|Google
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.|81.0.4044.138
VulnerabilitySeverityLevel|Ciąg|Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i dynamicznych czynników, na które wpływa poziom zagrożeń.|Średni
|

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
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
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
            "recommendationReference": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11"
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

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Vulnerability.Read.All|\'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe)|Vulnerability.Read|\'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

### <a name="23-url"></a>2.3 Adres URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Parametry

- sasValidHours: liczba godzin, przez które mają być ważne adresy URL pobierania (maksymalnie 24 godziny).

### <a name="25-properties"></a>2,5 Właściwości

> [!NOTE]
>
> - Pliki są skompresowane w formacie GZIP & wieloliniowym formacie Json.
> - Adresy URL pobierania są ważne tylko przez 3 godziny. w przeciwnym razie możesz użyć parametru.
> - Aby uzyskać maksymalną szybkość pobierania danych, możesz się upewnić, że pobierasz pliki z tego samego regionu platformy Azure, w którym znajdują się Twoje dane.
>
> - Każdy rekord to w przybliżeniu 1 KB danych. Należy wziąć to pod uwagę podczas wybierania odpowiedniego parametru pageSize.
> - Niektóre dodatkowe kolumny mogą być zwracane w odpowiedzi. Te kolumny są tymczasowe i mogą zostać usunięte. Należy używać tylko kolumn z dokumentami.

<br>

****

Właściwość (identyfikator)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
Eksportowanie plików|arraystring\[\]|Lista adresów URL pobierania plików z bieżącą migawką organizacji.|["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Ciąg|Godzina wygenerowania eksportu.|2021-05-20T08:00:00Z
|

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

## <a name="3-delta-export-software-vulnerabilities-assessment-json-response"></a>3. Ocena luk w oprogramowaniu eksportu różnicowego (odpowiedź JSON)

### <a name="31-api-method-description"></a>Opis metody interfejsu API 3.1

Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Interfejs API wyciąga dane z Twojej organizacji jako odpowiedzi Json. Odpowiedź jest podzielony na strony, więc można użyć pola @odata.nextLink z odpowiedzi w celu pobrania następnych wyników. W przeciwieństwie do pełnej oceny luk w oprogramowaniu (odpowiedź JSON) (która jest używana do uzyskania pełnej migawki oceny luk w oprogramowaniu organizacji według urządzenia), wywołanie interfejsu API odpowiedzi JSON (delta export JSON) jest używane do uzyskiwania zdalnego dostępu tylko do zmian, które miały miejsce między wybraną datą a bieżącą datą (wywołaniem interfejsu API zmiany). Zamiast pełnego eksportu z dużą ilością danych za każdym razem będziesz otrzymywać tylko określone informacje dotyczące nowych, stałych i zaktualizowanych luk w zabezpieczeniach. Za pomocą wywołania interfejsu API odpowiedzi JSON eksportu różnicowego można również obliczać różne wskaźniki KPI, na przykład "ile luk usunięto?". lub "ile nowych luk w zabezpieczeniach dodano do mojej organizacji?".

> [!NOTE]
> Zdecydowanie zalecane jest użycie pełnej oceny luk w oprogramowaniu eksportu przez wywołanie interfejsu API urządzenia co najmniej raz w tygodniu, a te dodatkowe zmiany luk w oprogramowaniu eksportu w interfejsie API urządzenia (delta) wywołują wszystkie pozostałe dni tygodnia. W przeciwieństwie do innych interfejsów API odpowiedzi JSON assessments, eksport różnicowy nie jest pełnym eksportem. Eksport różnicowy obejmuje tylko zmiany, które miały miejsce między wybraną datą a bieżącą datą (wywołanie interfejsu API zmiany).

#### <a name="311-limitations"></a>3.1.1 Ograniczenia

- Maksymalny rozmiar strony to 200 000.
- Parametr sinceTime ma maksymalnie 14 dni.
- Ograniczenia stawek dla tego interfejsu API to 30 połączeń na minutę i 1000 połączeń na godzinę.

### <a name="32-permissions"></a>3.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Vulnerability.Read.All|"Odczyt informacji o lukach w zabezpieczeniach i zarządzaniu zagrożeniami"
Delegowane (konto służbowe)|Vulnerability.Read|"Odczyt informacji o lukach w zabezpieczeniach i zarządzaniu zagrożeniami"

### <a name="33-url"></a>3.3 Adres URL

```http
GET /api/machines/SoftwareVulnerabilityChangesByMachine
```

### <a name="34-parameters"></a>3.4 Parametry

- sinceTime (wymagane): Dane między wybraną godziną a dniem dzisiejszym.
- pageSize (wartość domyślna = 50 000): liczba wyników w odpowiedzi.
- $top: liczba wyników do zwrócenia (nie zwraca ciągu @odata.nextLink, a więc nie powoduje zwrócenia wszystkich danych).

### <a name="35-properties"></a>3.5 Właściwości

Każdy zwrócony rekord zawiera wszystkie dane z pełnego oceny luk w oprogramowaniu eksportu według interfejsu API urządzenia oraz jeszcze dwa pola:  _**EventTimestamp**_ i _**Status**_.

> [!NOTE]
>
> - Niektóre dodatkowe kolumny mogą być zwracane w odpowiedzi. Te kolumny są tymczasowe i mogą zostać usunięte, dlatego należy używać tylko kolumn z dokumentami.
> - Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynik nie musi być zwracany w tej samej kolejności, w tej tabeli.

<br>

****

Właściwość (identyfikator)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
CveId |Ciąg|Unikatowy identyfikator przypisany do luki w zabezpieczeniach systemu cve (Common Vulnerabilities and Exposures).|CVE-2020-15992  
CvssScore|Ciąg|Wynik CVSS dla CVE.|6.2  
DeviceId|Ciąg|Unikatowy identyfikator urządzenia w usłudze.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1  
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.|johnlaptop.europe.contoso.com  
DiskPaths|Array[string]|Dowód dysku, że produkt jest zainstalowany na urządzeniu.|["C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe"]  
EventTimestamp|Ciąg|Czas znalezionego zdarzenia różnicowego.|2021-01-11T11:06:08.291Z
ExploitabilityLevel|Ciąg|Poziom wykorzystania tej luki (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit  
FirstSeenTimestamp|Ciąg|Po raz pierwszy cvE tego produktu zostało widziane na urządzeniu.|2020-11-03 10:13:34.8476880  
Identyfikator|Ciąg|Unikatowy identyfikator rekordu.|123ABG55_573AG&mnp!  
LastSeenTimestamp|Ciąg|Ostatni czas, gdy cvE było widoczne na urządzeniu.|2020-11-03 10:13:34.8476880  
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu; poszczególnych systemów operacyjnych z odmianami tej samej rodziny, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm.|Windows 10 i Windows 11 
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".|Serwery  
ZalecenieReference|ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.|va--microsoft--silverlight  
RecommendedSecurityUpdate |Ciąg|Nazwa lub opis aktualizacji zabezpieczeń udostępnianej przez dostawcę oprogramowania w celu rozwiązania problemu.|Aktualizacje zabezpieczeń z kwietnia 2020 r.  
RecommendedSecurityUpdateId |Ciąg|Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikator odpowiednich wytycznych lub artykułów z bazy wiedzy (KB)|4550961  
RegistryPaths |Array[string]|Dowód rejestru, że produkt jest zainstalowany w urządzeniu.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\Google Chrome" ]  
Nazwa_oprogramowania|Ciąg|Nazwa produktu.|Chrome  
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.|Google  
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.|81.0.4044.138  
Stan|Ciąg|**Nowa** (w przypadku nowej luki w zabezpieczeniach wprowadzona na urządzeniu) ( **1)** Naprawiona (jeśli ta luka nie będzie już istnieć na urządzeniu, co oznacza, że została usunięta). (2) **Zaktualizowano** (jeśli zmieniono lukę w zabezpieczeniach na urządzeniu. Możliwe zmiany to: wynik CVSS, poziom wykorzystania, poziom ważności, DiskPaths, RegistryPaths, RecommendedSecurityUpdate). |Naprawione
VulnerabilitySeverityLevel|Ciąg|Poziom ważności przypisany do luki w zabezpieczeniach. Jest on oparty na wynikach CVSS i dynamicznych czynnikach, na które wpływa poziom zagrożeń.|Średni
|

#### <a name="clarifications"></a>Objaśnienia

- Jeśli oprogramowanie zostało zaktualizowane z wersji 1.0 do wersji 2.0 i obie wersje są dostępne dla CVE-A, otrzymasz dwa oddzielne zdarzenia:
   1. Rozwiązano: Poprawiono CVE-A w wersji 1.0.
   1. Nowy: dodano CVE-A w wersji 2.0.

- Jeśli w oprogramowaniu z wersją 1.0 dosłyszono określoną lukę (na przykład CVE-A) w oprogramowaniu z wersją 1.0, a kilka dni później to oprogramowanie zostało zaktualizowane do wersji 2.0, która zawierała również tę samą cvE-A, otrzymasz następujące dwa rozdzielone zdarzenia:
   1. Rozwiązano: CVE-X, FirstSeenTimestamp 10 stycznia, wersja 1,0.
   1. Nowy: CVE-X, FirstSeenTimestamp 10 stycznia, wersja 2.0.

### <a name="36-examples"></a>3.6 Przykłady

#### <a name="361-request-example"></a>3.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilityChangesByMachine?pageSize=5&sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="362-response-example"></a>3.6.2 Przykład odpowiedzi

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.DeltaAssetVulnerability)",
    "value": [
        {
            "id": "008198251234544f7dfa715e278d4cec0c16c171_chrome_87.0.4280.88__",
            "deviceId": "008198251234544f7dfa715e278b4cec0c19c171",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_1c8fee370690ca24b6a0d3f34d193b0424943a8b8.DomainPII_0dc1aee0fa366d175e514bd91a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "87.0.4280.88",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Google Chrome"
            ],
            "lastSeenTimestamp": "2021-01-04 00:29:42",
            "firstSeenTimestamp": "2020-11-06 03:12:44",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "00e59c61234533860738ecf488eec8abf296e41e_onedrive_20.64.329.3__",
            "deviceId": "00e56c91234533860738ecf488eec8abf296e41e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_82c13a8ad8cf3dbaf7bf34fada9fa3aebc124116.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.64.329.3",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2127521184-1604012920-1887927527-24918864\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-11 19:49:48",
            "firstSeenTimestamp": "2020-12-07 18:25:47",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "01aa8c73095bb12345918663f3f94ce322107d24_firefox_83.0.0.0_CVE-2020-26971_",
            "deviceId": "01aa8c73065bb12345918693f3f94ce322107d24",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_42684eb981bea2d670027e7ad2caafd3f2b381a3.DomainPII_21eed80b086e76dbfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "mozilla",
            "softwareName": "firefox",
            "softwareVersion": "83.0.0.0",
            "cveId": "CVE-2020-26971",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "193220",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Mozilla Firefox\\firefox.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Mozilla Firefox 83.0 (x86 en-US)"
            ],
            "lastSeenTimestamp": "2021-01-05 17:04:30",
            "firstSeenTimestamp": "2020-05-06 12:42:19",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-mozilla-_-firefox",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "026f0fcb12345fbd2decd1a339702131422d362e_project_16.0.13701.20000__",
            "deviceId": "029f0fcb13245fbd2decd1a336702131422d392e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_a5706750acba75f15d69cd17f4a7fcd268d6422c.DomainPII_f290e982685f7e8eee168b4332e0ae5d2a069cd6.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "project",
            "softwareVersion": "16.0.13701.20000",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\ProjectProRetail - en-us"
            ],
            "lastSeenTimestamp": "2021-01-03 23:38:03",
            "firstSeenTimestamp": "2019-08-01 22:56:12",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-project",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "038df381234510b357ac19d0113ef622e4e212b3_chrome_81.0.4044.138_CVE-2020-16011_",
            "deviceId": "038df381234510d357ac19b0113ef922e4e212b3",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596a43a2ef2bbfa00f6a16c0cb1d108bc63e32.DomainPII_3c5fefd2e6fda2f36257359404f6c1092aa6d4b8.net",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "81.0.4044.138",
            "cveId": "CVE-2020-16011",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "ADV 200002",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{C4EBFDFD-0C55-3E5F-A919-E3C54949024A}"
            ],
            "lastSeenTimestamp": "2020-12-10 22:45:41",
            "firstSeenTimestamp": "2020-07-26 02:13:43",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        }
    ],
    "@odata.nextLink": "https://wpatdadi-eus-stg.cloudapp.net/api/machines/SoftwareVulnerabilitiesTimeline?sincetime=2021-01-11&pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="see-also"></a>Zobacz też

- [Eksportowanie metod i właściwości oceny na urządzenie](get-assessment-methods-properties.md)
- [Eksportowanie bezpiecznego oceny konfiguracji na urządzenie](get-assessment-secure-config.md)
- [Eksportowanie oceny spisu oprogramowania na urządzenie](get-assessment-software-inventory.md)

Inne powiązane

- [Zagrożenia oparte na czynnikach ryzyka & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
