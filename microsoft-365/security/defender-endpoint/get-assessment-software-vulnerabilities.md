---
title: Eksportowanie oceny luk w zabezpieczeniach oprogramowania na urządzenie
description: Odpowiedź interfejsu API dotyczy poszczególnych urządzeń i zawiera oprogramowanie podatne na zagrożenia zainstalowane na uwidocznionych urządzeniach oraz wszelkie znane luki w zabezpieczeniach tych produktów. Ta tabela zawiera również informacje o systemie operacyjnym, identyfikatory CVE i informacje o ważności luk w zabezpieczeniach.
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
ms.openlocfilehash: 52dc38d3675ffe15bd781aefaecede9d1783bac3
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487175"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Eksportowanie oceny luk w zabezpieczeniach oprogramowania na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Zwraca wszystkie znane luki w zabezpieczeniach oprogramowania i ich szczegóły dotyczące wszystkich urządzeń na poszczególnych urządzeniach.

Różne wywołania interfejsu API pobierają różne typy danych. Ponieważ ilość danych może być duża, można pobrać je na dwa sposoby:

1. [Eksportowanie **odpowiedzi JSON** oceny luk w zabezpieczeniach oprogramowania](#1-export-software-vulnerabilities-assessment-json-response)  Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza w _przypadku małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K_. Odpowiedź jest podzielona na strony, więc możesz użyć \@pola odata.nextLink z odpowiedzi, aby pobrać następne wyniki.

2. [Eksportowanie oceny luk w zabezpieczeniach oprogramowania **za pośrednictwem plików**](#2-export-software-vulnerabilities-assessment-via-files) To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne ściąganie większych ilości danych. Usługa Via-files jest zalecana dla dużych organizacji z ponad 100-K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL umożliwiające pobranie wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobranie wszystkich danych z usługi Azure Storage w następujący sposób:
   - Wywołaj interfejs API, aby uzyskać listę adresów URL pobierania ze wszystkimi danymi organizacji.
   - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwórz dane zgodnie z tym, co chcesz.

3. [**Odpowiedź JSON** dotycząca oceny luk w zabezpieczeniach oprogramowania eksportowania różnic](#3-delta-export-software-vulnerabilities-assessment-json-response)  Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId i EventTimestamp.
Interfejs API pobiera dane w organizacji jako odpowiedzi JSON. Odpowiedź jest podzielona na strony, więc możesz użyć pola @odata.nextLink z odpowiedzi, aby pobrać następne wyniki.

   Pełna "ocena luk w zabezpieczeniach oprogramowania (odpowiedź JSON)" służy do uzyskania całej migawki oceny luk w zabezpieczeniach oprogramowania organizacji według urządzenia. Jednak wywołanie interfejsu API eksportu różnicowego służy do pobierania tylko zmian, które wystąpiły między wybraną datą a bieżącą datą (wywołanie interfejsu API "delta"). Zamiast za każdym razem uzyskiwać pełny eksport z dużą ilością danych, uzyskasz tylko konkretne informacje o nowych, stałych i zaktualizowanych lukach w zabezpieczeniach. Wywołanie interfejsu API odpowiedzi JSON eksportu różnicy może być również używane do obliczania różnych wskaźników KPI, takich jak "ile luk w zabezpieczeniach zostało naprawionych?" lub "ile nowych luk w zabezpieczeniach dodano do mojej organizacji?"

   Ponieważ wywołanie interfejsu API odpowiedzi JSON eksportu delty dla luk w zabezpieczeniach oprogramowania zwraca dane tylko dla docelowego zakresu dat, nie jest uważane za _pełny eksport_.

Zbierane dane (przy użyciu _odpowiedzi JSON_ lub _za pośrednictwem plików_) są bieżącą migawką bieżącego stanu. Nie zawiera danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisywać dane we własnych magazynach danych.

> [!NOTE]
> O ile nie wskazano inaczej, wszystkie wymienione metody oceny eksportu to **_pełny eksport_** i **_urządzenie_** (określane również jako **_dla każdego urządzenia_**).

## <a name="1-export-software-vulnerabilities-assessment-json-response"></a>1. Eksportowanie oceny luk w zabezpieczeniach oprogramowania (odpowiedź JSON)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="111-limitations"></a>Ograniczenia 1.1.1

- Maksymalny rozmiar strony to 200 000.
- Ograniczenia szybkości dla tego interfejsu API to 30 wywołań na minutę i 1000 wywołań na godzinę.

### <a name="12-permissions"></a>1.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Vulnerability.Read.All|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'
Delegowane (konto służbowe)|Luka w zabezpieczeniach.Odczyt|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'

### <a name="13-url"></a>Adres URL 1.3

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>Parametry 1.4

- pageSize (wartość domyślna = 50 000): liczba wyników w odpowiedzi.
- $top: liczba wyników do zwrócenia (nie zwraca @odata.nextLink, więc nie ściąga wszystkich danych).

### <a name="15-properties"></a>1.5 Właściwości

> [!NOTE]
>
> - Każdy rekord to około 1 KB danych. Należy wziąć to pod uwagę podczas wybierania prawidłowego parametru pageSize.
> - W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Użyj tylko udokumentowanych kolumn.
> - Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynikowe dane wyjściowe nie muszą być zwracane w tej samej kolejności wymienionej w tej tabeli.

<br>

****

Właściwość (ID)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
CveId|Ciąg|Unikatowy identyfikator przypisany do luki w zabezpieczeniach w systemie Common Vulnerabilities and Exposures (CVE).|CVE-2020-15992
CvssScore|Ciąg|Wynik CVSS CVE.|6.2
Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.|johnlaptop.europe.contoso.com
DiskPaths|Ciąg tablicy\[\]|Dysk wskazuje, że produkt jest zainstalowany na urządzeniu.|[ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
ExploitabilityLevel|Ciąg|Poziom wykorzystania tej luki w zabezpieczeniach (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit
FirstSeenTimestamp|Ciąg|Po raz pierwszy cve tego produktu był widoczny na urządzeniu.|2020-11-03 10:13:34.8476880
Id|Ciąg|Unikatowy identyfikator rekordu.|123ABG55_573AG&mnp!
LastSeenTimestamp|Ciąg|Ostatni raz cve był widoczny na urządzeniu.|2020-11-03 10:13:34.8476880
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu. Ta właściwość wskazuje określone systemy operacyjne z odmianami w tej samej rodzinie, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy tvm.|Windows10 i Windows 11
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".|Serwery
ZalecenieReferencja|Ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.|_va-microsoft-silverlight_
RecommendedSecurityUpdate (opcjonalnie)|Ciąg|Nazwa lub opis aktualizacji zabezpieczeń udostępnionej przez dostawcę oprogramowania w celu rozwiązania problemu z luką w zabezpieczeniach.|Aktualizacje zabezpieczeń z kwietnia 2020 r.
RecommendedSecurityUpdateId (opcjonalnie)|Ciąg|Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikatora odpowiednich wskazówek lub artykułów baza wiedzy (KB)|4550961
RegistryPaths|Ciąg tablicy\[\]|Rejestr wskazuje, że produkt jest zainstalowany na urządzeniu.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
SecurityUpdateAvailable|Wartość logiczna|Wskazuje, czy aktualizacja zabezpieczeń jest dostępna dla oprogramowania.| Możliwe wartości to true lub false.
SoftwareName|Ciąg|Nazwa produktu programowego.|Chrome
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.|Google
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.|81.0.4044.138
VulnerabilitySeverityLevel|Ciąg|Poziom ważności przypisany do luki w zabezpieczeniach na podstawie wyniku CVSS i czynników dynamicznych, na które wpływa poziom zagrożenia.|Średni
|

### <a name="16-examples"></a>1.6 Przykłady

#### <a name="161-request-example"></a>1.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a>Przykład odpowiedzi 1.6.2

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
            "recommendationReference": "va-_-microsoft-_-edge",
            "securityUpdateAvailable": true
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
            "recommendationReference": "va-_-microsoft-_-.net_framework",
            "securityUpdateAvailable": true
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
            "recommendationReference": "va-_-microsoft-_-system_center_2012_endpoint_protection",
            "securityUpdateAvailable": true
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
            "recommendationReference": "va-_-microsoft-_-onedrive",
            "securityUpdateAvailable": true
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
            "recommendationReference": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11",
            "securityUpdateAvailable": true
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. Eksportowanie oceny luk w zabezpieczeniach oprogramowania (za pośrednictwem plików)

### <a name="21-api-method-description"></a>Opis metody interfejsu API w wersji 2.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="212-limitations"></a>2.1.2 Ograniczenia

Ograniczenia szybkości dla tego interfejsu API to 5 wywołań na minutę i 20 wywołań na godzinę.

### <a name="22-permissions"></a>2.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać szczegółowe informacje](apis-intro.md).

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Vulnerability.Read.All|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'
Delegowane (konto służbowe)|Luka w zabezpieczeniach.Odczyt|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'

### <a name="23-url"></a>Adres URL 2.3

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>Parametry 2.4

- sasValidHours: liczba godzin, przez które adresy URL pobierania będą ważne (maksymalnie 24 godziny).

### <a name="25-properties"></a>2.5 Właściwości

> [!NOTE]
>
> - Pliki są skompresowane gzip & w wielowierszowym formacie JSON.
> - Adresy URL pobierania są ważne tylko przez 3 godziny; W przeciwnym razie można użyć parametru .
> - Aby uzyskać maksymalną szybkość pobierania danych, możesz upewnić się, że pobierasz dane z tego samego regionu świadczenia usługi Azure, w którym znajdują się twoje dane.
>
> - Każdy rekord to około 1 KB danych. Należy wziąć to pod uwagę podczas wybierania prawidłowego parametru pageSize.
> - W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Użyj tylko udokumentowanych kolumn.

<br>

****

Właściwość (ID)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
Eksportowanie plików|ciąg tablicy\[\]|Lista adresów URL pobierania plików przechowujących bieżącą migawkę organizacji.|["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Ciąg|Czas wygenerowania eksportu.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Przykłady

#### <a name="261-request-example"></a>2.6.1 Przykład żądania

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a>Przykład odpowiedzi 2.6.2

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

## <a name="3-delta-export-software-vulnerabilities-assessment-json-response"></a>3. Ocena luk w zabezpieczeniach oprogramowania eksportowania różnicowego (odpowiedź JSON)

### <a name="31-api-method-description"></a>Opis metody interfejsu API 3.1

Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Interfejs API pobiera dane w organizacji jako odpowiedzi JSON. Odpowiedź jest podzielona na strony, więc możesz użyć pola @odata.nextLink z odpowiedzi, aby pobrać następne wyniki. W przeciwieństwie do pełnej oceny luk w zabezpieczeniach oprogramowania (odpowiedź JSON) (która służy do uzyskania całej migawki oceny luk w zabezpieczeniach oprogramowania organizacji według urządzenia) wywołanie interfejsu API odpowiedzi JSON eksportu różnicowego służy do pobierania tylko zmian, które wystąpiły między wybraną datą a bieżącą datą (wywołanie interfejsu API "delta"). Zamiast za każdym razem uzyskiwać pełny eksport z dużą ilością danych, uzyskasz tylko konkretne informacje o nowych, stałych i zaktualizowanych lukach w zabezpieczeniach. Wywołanie interfejsu API odpowiedzi JSON eksportu różnicy może być również używane do obliczania różnych wskaźników KPI, takich jak "ile luk w zabezpieczeniach zostało naprawionych?" lub "ile nowych luk w zabezpieczeniach dodano do mojej organizacji?"

> [!NOTE]
> Zdecydowanie zaleca się używanie pełnej oceny luk w zabezpieczeniach oprogramowania eksportu przez wywołanie interfejsu API urządzenia co najmniej raz w tygodniu, a te dodatkowe zmiany luk w zabezpieczeniach oprogramowania eksportu według interfejsu API urządzenia (delta) wywołają wszystkie pozostałe dni tygodnia. W przeciwieństwie do innych interfejsów API odpowiedzi JSON ocen "eksport różnicowy" nie jest pełnym eksportem. Eksport różnicowy obejmuje tylko zmiany, które wystąpiły między wybraną datą a bieżącą datą (wywołanie interfejsu API "delta").

#### <a name="311-limitations"></a>3.1.1 Ograniczenia

- Maksymalny rozmiar strony to 200 000.
- Parametr sinceTime ma maksymalnie 14 dni.
- Ograniczenia szybkości dla tego interfejsu API to 30 wywołań na minutę i 1000 wywołań na godzinę.

### <a name="32-permissions"></a>3.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Vulnerability.Read.All|"Odczytywanie informacji o lukach w zabezpieczeniach dotyczących zarządzania zagrożeniami i lukami w zabezpieczeniach"
Delegowane (konto służbowe)|Luka w zabezpieczeniach.Odczyt|"Odczytywanie informacji o lukach w zabezpieczeniach dotyczących zarządzania zagrożeniami i lukami w zabezpieczeniach"

### <a name="33-url"></a>Adres URL 3.3

```http
GET /api/machines/SoftwareVulnerabilityChangesByMachine
```

### <a name="34-parameters"></a>3.4 Parametry

- sinceTime (wymagane): dane między wybranym czasem a dniem dzisiejszym.
- pageSize (wartość domyślna = 50 000): liczba wyników w odpowiedzi.
- $top: liczba wyników do zwrócenia (nie zwraca @odata.nextLink, więc nie ściąga wszystkich danych).

### <a name="35-properties"></a>3.5 Właściwości

Każdy zwrócony rekord zawiera wszystkie dane z pełnej oceny luk w zabezpieczeniach oprogramowania eksportu według interfejsu API urządzenia oraz dwa kolejne pola:  _**EventTimestamp**_ i _**Status**_.

> [!NOTE]
>
> - W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte, więc użyj tylko udokumentowanych kolumn.
> - Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynikowe dane wyjściowe nie muszą być zwracane w tej samej kolejności wymienionej w tej tabeli.

<br>

****

Właściwość (ID)|Typ danych|Opis|Przykład zwróconej wartości
:---|:---|:---|:---
CveId |Ciąg|Unikatowy identyfikator przypisany do luki w zabezpieczeniach w systemie Common Vulnerabilities and Exposures (CVE).|CVE-2020-15992  
CvssScore|Ciąg|Wynik CVSS CVE.|6.2  
Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1  
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.|johnlaptop.europe.contoso.com  
DiskPaths|Tablica[ciąg]|Dysk wskazuje, że produkt jest zainstalowany na urządzeniu.|["C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe"]  
EventTimestamp|Ciąg|Czas znalezienia tego zdarzenia różnicowego.|2021-01-11T11:06:08.291Z
ExploitabilityLevel|Ciąg|Poziom wykorzystania tej luki w zabezpieczeniach (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit  
FirstSeenTimestamp|Ciąg|Po raz pierwszy cve tego produktu był widoczny na urządzeniu.|2020-11-03 10:13:34.8476880  
Id|Ciąg|Unikatowy identyfikator rekordu.|123ABG55_573AG&mnp!  
LastSeenTimestamp|Ciąg|Ostatni raz cve był widoczny na urządzeniu.|2020-11-03 10:13:34.8476880  
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu; specyficznych systemów operacyjnych z odmianami w tej samej rodzinie, takimi jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy tvm.|Windows10 i Windows 11 
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".|Serwery  
ZalecenieReferencja|Ciąg|Odwołanie do identyfikatora zalecenia związanego z tym oprogramowaniem.|va--microsoft--silverlight  
RecommendedSecurityUpdate |Ciąg|Nazwa lub opis aktualizacji zabezpieczeń udostępnionej przez dostawcę oprogramowania w celu rozwiązania problemu z luką w zabezpieczeniach.|Aktualizacje zabezpieczeń z kwietnia 2020 r.  
RecommendedSecurityUpdateId |Ciąg|Identyfikator odpowiednich aktualizacji zabezpieczeń lub identyfikatora odpowiednich wskazówek lub artykułów baza wiedzy (KB)|4550961  
RegistryPaths |Tablica[ciąg]|Rejestr wskazuje, że produkt jest zainstalowany na urządzeniu.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\Google Chrome" ]  
SoftwareName|Ciąg|Nazwa produktu programowego.|Chrome  
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.|Google  
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.|81.0.4044.138  
Stan|Ciąg|**Nowe** (dla nowej luki w zabezpieczeniach wprowadzonej na urządzeniu) (1) **Naprawiono** (jeśli ta luka w zabezpieczeniach nie istnieje już na urządzeniu, co oznacza, że została skorygowana). (2) **Zaktualizowano** (jeśli luka w zabezpieczeniach na urządzeniu uległa zmianie. Możliwe zmiany to: wynik CVSS, poziom możliwości wykorzystania, poziom ważności, DiskPaths, RegistryPaths, RecommendedSecurityUpdate). |Stałe
VulnerabilitySeverityLevel|Ciąg|Poziom ważności przypisany do luki w zabezpieczeniach. Jest ona oparta na wyniku CVSS i czynnikach dynamicznych, na które wpływa poziom zagrożenia.|Średni
|

#### <a name="clarifications"></a>Wyjaśnienia

- Jeśli oprogramowanie zostało zaktualizowane z wersji 1.0 do wersji 2.0, a obie wersje są udostępniane CVE-A, otrzymasz dwa oddzielne zdarzenia:
   1. Naprawiono: naprawiono cve-a w wersji 1.0.
   1. Nowość: dodano cve-a w wersji 2.0.

- Jeśli określona luka w zabezpieczeniach (na przykład CVE-A) została po raz pierwszy wyświetlona w określonym czasie (na przykład 10 stycznia) w oprogramowaniu w wersji 1.0, a kilka dni później oprogramowanie zostało zaktualizowane do wersji 2.0, która również została uwidoczniona dla tego samego CVE-A, otrzymasz te dwa oddzielone zdarzenia:
   1. Naprawiono: CVE-X, FirstSeenTimestamp 10 stycznia, wersja 1,0.
   1. Nowość: CVE-X, FirstSeenTimestamp 10 stycznia, wersja 2.0.

### <a name="36-examples"></a>3.6 Przykłady

#### <a name="361-request-example"></a>3.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilityChangesByMachine?pageSize=5&sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="362-response-example"></a>Przykład odpowiedzi 3.6.2

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

- [Eksportowanie metod oceny i właściwości na urządzenie](get-assessment-methods-properties.md)
- [Eksportowanie oceny bezpiecznej konfiguracji na urządzenie](get-assessment-secure-config.md)
- [Eksportowanie oceny spisu oprogramowania na urządzenie](get-assessment-software-inventory.md)

Inne powiązane

- [Zarządzanie lukami w zabezpieczeniach & zagrożeń opartych na ryzyku](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
