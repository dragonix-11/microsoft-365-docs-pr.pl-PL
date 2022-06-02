---
title: Eksportowanie oceny spisu oprogramowania na urządzenie
description: Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName i SoftwareVersion.
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
ms.openlocfilehash: 296b977452802d8e1ed8949cf6a8871cac171f3a
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839999"
---
# <a name="export-software-inventory-assessment-per-device"></a>Eksportowanie oceny spisu oprogramowania na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Różne wywołania interfejsu API pobierają różne typy danych. Ponieważ ilość danych może być duża, można pobrać je na dwa sposoby:

- [Eksportowanie **odpowiedzi JSON** oceny spisu oprogramowania](#1-export-software-inventory-assessment-json-response) Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi JSON. Ta metoda jest najlepsza w _przypadku małych organizacji z urządzeniami o rozmiarze mniejszym niż 100 K_. Odpowiedź jest podzielona na strony, więc możesz użyć \@pola odata.nextLink z odpowiedzi, aby pobrać następne wyniki.

- [Eksportowanie oceny spisu oprogramowania **za pośrednictwem plików**](#2-export-software-inventory-assessment-via-files)  To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne ściąganie większych ilości danych. Dlatego jest to zalecane w przypadku dużych organizacji z ponad 100-K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL umożliwiające pobranie wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobranie wszystkich danych z usługi Azure Storage w następujący sposób:
  - Wywołaj interfejs API, aby uzyskać listę adresów URL pobierania ze wszystkimi danymi organizacji.
  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwórz dane zgodnie z tym, co chcesz.

Zbierane dane (przy użyciu _odpowiedzi JSON_ lub _za pośrednictwem plików_) są bieżącą migawką bieżącego stanu. Nie zawiera danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisywać dane we własnych magazynach danych.

> [!NOTE]
> O ile nie wskazano inaczej, wszystkie wymienione metody oceny eksportu to **_pełny eksport_** i **_urządzenie_** (określane również jako **_dla każdego urządzenia_**).

## <a name="1-export-software-inventory-assessment-json-response"></a>1. Eksportowanie oceny spisu oprogramowania (odpowiedź JSON)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName i SoftwareVersion.

#### <a name="limitations"></a>Ograniczenia

- Maksymalny rozmiar strony to 200 000.
- Ograniczenia szybkości dla tego interfejsu API to 30 wywołań na minutę i 1000 wywołań na godzinę.

### <a name="12-permissions"></a>1.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Software.Read.All|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'
Delegowane (konto służbowe)|Software.Read|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'

### <a name="13-url"></a>Adres URL 1.3

```http
GET /api/machines/SoftwareInventoryByMachine
```

### <a name="14-parameters"></a>Parametry 1.4

- pageSize (wartość domyślna = 50 000): liczba wyników w odpowiedzi.
- $top: liczba wyników do zwrócenia (nie zwraca @odata.nextLink i w związku z tym nie ściąga wszystkich danych)

### <a name="15-properties"></a>1.5 Właściwości

> [!NOTE]
>
> - Każdy rekord to około 0,5 KB danych. Należy wziąć to pod uwagę podczas wybierania prawidłowego parametru pageSize.
> - Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynikowe dane wyjściowe nie muszą być zwracane w tej samej kolejności wymienionej w tej tabeli.
> - W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Użyj tylko udokumentowanych kolumn.

<br>

****

Właściwość (ID)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.|johnlaptop.europe.contoso.com
DiskPaths|Tablica[ciąg]|Dysk wskazuje, że produkt jest zainstalowany na urządzeniu.|[ "C:\\ Program Files (x86)\\Microsoft\\Silverlight\\Application\\silverlight.exe" ]
EndOfSupportDate|Ciąg|Data zakończenia pomocy technicznej dla tego oprogramowania.|2020-12-30
EndOfSupportStatus|Ciąg|Stan zakończenia pomocy technicznej. Mogą zawierać następujące możliwe wartości: Brak, wersja systemu EOS, nadchodząca wersja systemu EOS, oprogramowanie EOS, nadchodzące oprogramowanie EOS.|Nadchodzący EOS
Id|Ciąg|Unikatowy identyfikator rekordu.|123ABG55_573AG&mnp!
LiczbaOfWeaknesses|Int|Liczba słabych stron tego oprogramowania na tym urządzeniu|3
OSPlatform|Ciąg|Platforma systemu operacyjnego działającego na urządzeniu. Są to specyficzne systemy operacyjne z odmianami w tej samej rodzinie, takie jak Windows 10 i Windows 11. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy tvm.|Windows10 i Windows 11
RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".|Serwery
RegistryPaths|Tablica[ciąg]|Rejestr wskazuje, że produkt jest zainstalowany na urządzeniu.|[ "HKEY_LOCAL_MACHINE\\ SOFTWARE\\WOW6432Node\\Microsoft\\ Windows\\ CurrentVersion\\Uninstall\\Microsoft Silverlight" ]
SoftwareFirstSeenTimestamp|Ciąg|Po raz pierwszy to oprogramowanie było widoczne na urządzeniu.|2019-04-07 02:06:47
SoftwareName|Ciąg|Nazwa produktu programowego.|Silverlight
SoftwareVendor|Ciąg|Nazwa dostawcy oprogramowania.|Microsoft
SoftwareVersion|Ciąg|Numer wersji produktu oprogramowania.|81.0.4044.138
|

### <a name="16-examples"></a>1.6 Przykłady

#### <a name="161-request-example"></a>1.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pageSize=5  &sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="162-response-example"></a>Przykład odpowiedzi 1.6.2

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(contoso.windowsDefenderATP.api.AssetSoftware)",
    "value": [
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
            "softwareVersion": "10.0.17763.1637",
            "numberOfWeaknesses": 58,
            "diskPaths": [],
            "registryPaths": [],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "Upcoming EOS Version",
            "endOfSupportDate": "2021-05-11T00:00:00+00:00"
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eed80d086e79bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.7.214.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765ddaf71234bde6bd733d6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178aedfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "configuration_manager",
            "softwareVersion": "5.0.8634.1000",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{B7D3A842-E826-4542-B39B-1D883264B279}"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f38765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0yNS8wMjAwLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-inventory-assessment-via-files"></a>2. Eksportowanie oceny spisu oprogramowania (za pośrednictwem plików)

### <a name="21-api-method-description"></a>Opis metody interfejsu API w wersji 2.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji elementów DeviceId, SoftwareVendor, SoftwareName i SoftwareVersion.

#### <a name="211-limitations"></a>Ograniczenia 2.1.1

Ograniczenia szybkości dla tego interfejsu API to 5 wywołań na minutę i 20 wywołań na godzinę.

### <a name="22-permissions"></a>2.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Software.Read.All|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'
Delegowane (konto służbowe)|Software.Read|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'

### <a name="23-url"></a>Adres URL 2.3

```http
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>Parametry

- sasValidHours: liczba godzin, przez które adresy URL pobierania będą ważne (maksymalnie 24 godziny)

### <a name="25-properties"></a>2.5 Właściwości

> [!NOTE]
>
> - Pliki są skompresowane gzip & w wielowierszowym formacie JSON.
> - Adresy URL pobierania są ważne tylko przez 3 godziny. W przeciwnym razie można użyć parametru .
> - Aby uzyskać maksymalną szybkość pobierania danych, możesz upewnić się, że pobierasz dane z tego samego regionu świadczenia usługi Azure, w którym znajdują się twoje dane.

<br>

****

Właściwość (ID)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
Eksportowanie plików|ciąg tablicy\[\]|Lista adresów URL pobierania plików przechowujących bieżącą migawkę organizacji|"[Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Ciąg|Czas wygenerowania eksportu.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Przykłady

#### <a name="261-request-example"></a>2.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryExport
```

#### <a name="262-response-example"></a>Przykład odpowiedzi 2.6.2

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Zobacz też

- [Eksportowanie metod oceny i właściwości na urządzenie](get-assessment-methods-properties.md)
- [Eksportowanie oceny bezpiecznej konfiguracji na urządzenie](get-assessment-secure-config.md)
- [Eksportowanie oceny luk w zabezpieczeniach oprogramowania na urządzenie](get-assessment-software-vulnerabilities.md)

Inne powiązane

- [& zarządzanie lukami w zabezpieczeniach zagrożeń opartych na ryzyku](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
