---
title: Eksportowanie oceny spisu oprogramowania na urządzenie
description: Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.
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
ms.openlocfilehash: 5663a17de2e601c506b4d1b9ac44eaab6ae6245f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2021
ms.locfileid: "62959224"
---
# <a name="export-software-inventory-assessment-per-device"></a>Eksportowanie oceny spisu oprogramowania na urządzenie

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
Istnieją różne wywołania interfejsu API w celu uzyskania różnych typów danych. Ponieważ ilość danych może być bardzo duża, można ją pobrać na dwa sposoby:

- [Eksportowanie oceny spisu **oprogramowania OData**](#1-export-software-inventory-assessment-odata)  Interfejs API ściąga wszystkie dane w organizacji jako odpowiedzi Json, zgodnie z protokołem OData. Ta metoda jest najlepsza dla _małych organizacji, które mają mniej niż 100 K urządzeń_. Odpowiedź jest podzielony na strony, \@więc można użyć pola odata.nextLink z odpowiedzi w celu pobrania następnych wyników.

- [Eksportowanie oceny spisu oprogramowania **za pośrednictwem plików**](#2-export-software-inventory-assessment-via-files)  To rozwiązanie interfejsu API umożliwia szybsze i bardziej niezawodne wyciąganie większych ilości danych. Dlatego jest zalecane dla dużych organizacji, które mają ponad 100 K urządzeń. Ten interfejs API pobiera wszystkie dane w organizacji jako pliki do pobrania. Odpowiedź zawiera adresy URL służące do pobierania wszystkich danych z usługi Azure Storage. Ten interfejs API umożliwia pobieranie wszystkich danych z usługi Azure Storage w następujący sposób:

  - Wywołaj interfejs API, aby uzyskać listę pobierznych adresów URL wraz ze wszystkimi danymi Twojej organizacji.

  - Pobierz wszystkie pliki przy użyciu adresów URL pobierania i przetwarzaj dane w sposób, który Ci się podoba.

Dane zbierane (przy użyciu źródeł _danych OData_ lub za pośrednictwem _plików) to_ bieżąca migawka stanu bieżącego, która nie zawiera danych historycznych. Aby zbierać dane historyczne, klienci muszą zapisać te dane we własnych magazynach danych.

> [!Note]
>
> O ile nie zaznaczono inaczej, wszystkie wymienione metody **** oceny eksportu są pełne i według **_urządzenia_** (określane również jako **_urządzenia_**).

## <a name="1-export-software-inventory-assessment-odata"></a>1. Eksportowanie oceny spisu oprogramowania (OData)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="limitations"></a>Ograniczenia

- Maksymalny rozmiar strony to 200 000.

- Ograniczenia stawek dla tego interfejsu API to 30 połączeń na minutę i 1000 połączeń na godzinę.

### <a name="12-permissions"></a>1.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
---|---|---
Aplikacja | Software.Read.All | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe) | Software.Read | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

### <a name="13-url"></a>1.3 Adres URL

```http
GET /api/machines/SoftwareInventoryByMachine
```

### <a name="14-parameters"></a>1.4 Parametry

- pageSize (domyślna = 50 000) — liczba wyników w odpowiedzi.

- $top — liczba wyników do zwrócenia (nie zwraca @odata.nextLink, a zatem nie wyciąga wszystkich danych)

### <a name="15-properties"></a>1,5 Właściwości

>[!NOTE]
>
>— Każdy rekord to w przybliżeniu 0,5 KB danych. Należy wziąć to pod uwagę podczas wybierania odpowiedniego parametru pageSize.

>— Właściwości zdefiniowane w poniższej tabeli są uporządkowane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynik nie musi być zwracany w tej samej kolejności, w tej tabeli.
>
>— W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Należy używać tylko kolumn z dokumentami.

Właściwość (identyfikator) | Typ danych | Opis | Przykład zwracanej wartości
:---|:---|:---|:---
DeviceId | ciąg | Unikatowy identyfikator urządzenia w usłudze. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | ciąg | W pełni kwalifikowana nazwa domeny (FQDN) urządzenia. | johnlaptop.europe.contoso.com
DiskPaths | Array[string]  | Dowód dysku, że produkt jest zainstalowany na urządzeniu. | [ "C:\\ Program Files (x86)\\MicrosoftSilverlightApplication\\\\\\silverlight.exe" ]
EndOfSupportDate | ciąg | Data zakończenia obsługi tego oprogramowania. | 2020-12-30
EndOfSupportStatus | ciąg | Stan zakończenia pomocy technicznej. Mogą zawierać następujące możliwe wartości: Brak, Wersja EOS, Nadchodzące wersja systemu EOS, Oprogramowanie EOS, Nadchodzące oprogramowanie EOS. | Nadchodzące urządzenia z systemem EOS
Identyfikator | ciąg | Unikatowy identyfikator rekordu. | 123ABG55_573AG&mnp!
NumberOfWeaknesses | int | Liczba słabego sprzętu w tym oprogramowaniu na tym urządzeniu | 3
OSPlatform | ciąg | Platforma systemu operacyjnego działającego na urządzeniu. To oznacza określone systemy operacyjne, w tym odmiany w obrębie tej samej rodziny, takie jak Windows 10 i Windows 7. Aby uzyskać szczegółowe informacje, zobacz obsługiwane systemy operacyjne i platformy obsługiwane przez program tvm. | Windows10
RbacGroupName | ciąg | Grupa kontroli dostępu opartej na rolach (RBAC, role based access control). Jeśli to urządzenie nie jest przypisane do żadnej grupy RBAC, wartością będzie "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak". | Serwery
RegistryPaths | Array[string] | Dowód rejestru, że produkt jest zainstalowany w urządzeniu. | [ "HKEY_LOCAL_MACHINE\\ SOFTWAREWOW6432NodeMicrosoft\\\\\\ Windows\\ CurrentVersionUninstallMicrosoft\\\\ Silverlight" ]
SoftwareFirstSeenTimestamp | ciąg | To oprogramowanie było widoczne na urządzeniu po raz pierwszy. | 2019-04-07 02:06:47
Nazwa_oprogramowania | ciąg | Nazwa produktu. | Silverlight
SoftwareVendor | ciąg | Nazwa dostawcy oprogramowania. | microsoft
SoftwareVersion | ciąg | Numer wersji produktu oprogramowania. | 81.0.4044.138

### <a name="16-examples"></a>1.6 Przykłady

#### <a name="161-request-example"></a>1.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pageSize=5  &sinceTime=2021-05-19T18%3A35%3A49.924Z 
```

#### <a name="162-response-example"></a>1.6.2 Przykład odpowiedzi

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(contoso.windowsDefenderATP.api.AssetSoftware)",
    "value": [
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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

### <a name="21-api-method-description"></a>Opis metody interfejsu API 2.1

Ta odpowiedź interfejsu API zawiera wszystkie dane zainstalowanego oprogramowania na urządzenie. Zwraca tabelę z wpisem dla każdej unikatowej kombinacji DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="211-limitations"></a>2.1.1 Ograniczenia

Ograniczenia stawek dla tego interfejsu API to 5 połączeń na minutę i 20 połączeń na godzinę.

### <a name="22-permissions"></a>2.2 Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
---|---|---
Aplikacja | Software.Read.All | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe) | Software.Read | \'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

### <a name="23-url"></a>2.3 Adres URL

```http
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>Parametry

- sasValidHours — liczba godzin, przez które będą ważne adresy URL pobierania (maksymalnie 24 godziny)

### <a name="25-properties"></a>2,5 Właściwości

>[!Note]
>
>- Pliki są skompresowane w formacie GZIP & wieloliniowym formacie Json.
>
>- Adresy URL pobierania są ważne tylko przez 3 godziny. W przeciwnym razie możesz użyć parametru.
>
>_ Aby uzyskać maksymalną szybkość pobierania danych, możesz się upewnić, że pobierasz pliki z tego samego regionu platformy Azure, w którym znajdują się Twoje dane.
>
Właściwość (identyfikator) | Typ danych | Opis | Przykład zwracanej wartości
:---|:---|:---|:---
Eksportowanie plików | arraystring\[\] | Lista adresów URL pobierania plików z bieżącą migawką organizacji | [  Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2” ]
GeneratedTime | ciąg | Godzina wygenerowania eksportu. | 2021-05-20T08:00:00Z ]

### <a name="26-examples"></a>2.6 Przykłady

#### <a name="261-request-example"></a>2.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryExport
```

#### <a name="262-response-example"></a>2.6.2 Przykład odpowiedzi

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

- [Eksportowanie metod i właściwości oceny na urządzenie](get-assessmnt-1methods-properties.md)

- [Eksportowanie bezpiecznego oceny konfiguracji na urządzenie](get-assessmnt-secure-cfg.md)

- [Ocena luk w zabezpieczeniach oprogramowania na urządzeniu](get-assessmnt-software-vulnerabilities.md)

Inne powiązane

- [Zagrożenia oparte na czynnikach ryzyka & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)

- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
