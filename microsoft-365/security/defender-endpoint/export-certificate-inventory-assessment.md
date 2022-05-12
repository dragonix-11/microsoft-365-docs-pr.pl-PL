---
title: Metody i właściwości oceny certyfikatów na urządzenie
description: Zawiera informacje o interfejsach API certyfikatów, które ściągają dane "Zarządzanie zagrożeniami i lukami". Istnieją różne wywołania interfejsu API umożliwiające pobieranie różnych typów danych. Ogólnie rzecz biorąc, każde wywołanie interfejsu API zawiera wymagane dane dla urządzeń w organizacji.
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
ms.openlocfilehash: c7718175789755a711a0dd43dce041f125d18972
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2022
ms.locfileid: "65369707"
---
# <a name="export-certificate-inventory-per-device"></a>Eksportowanie spisu certyfikatów na urządzenie

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

## <a name="1-export-certificate-assessment-json-response"></a>1. Eksportowanie oceny certyfikatu (odpowiedź JSON)

### <a name="11-api-method-description"></a>Opis metody interfejsu API 1.1

Zwraca wszystkie oceny certyfikatów dla wszystkich urządzeń na poszczególnych urządzeniach. Zwraca tabelę z oddzielnym wpisem dla każdej unikatowej kombinacji elementów DeviceId, Thumbprint i Path.

#### <a name="12-limitations"></a>1.2 Ograniczenia

- Maksymalny rozmiar strony to 200 000.
- Ograniczenia szybkości dla tego interfejsu API to 30 wywołań na minutę i 1000 wywołań na godzinę.

### <a name="13-parameters"></a>Parametry 1.3

- pageSize (wartość domyślna = 50 000): liczba wyników w odpowiedzi.
- $top: liczba wyników do zwrócenia (nie zwraca @odata.nextLink, więc nie ściąga wszystkich danych).

### <a name="14-http-request"></a>1.4 Żądanie HTTP

```http
GET /api/machines/certificateAssessmentByMachine
```

### <a name="15-properties-json-response"></a>1.5 Właściwości (odpowiedź JSON)

> [!NOTE]
> Każdy rekord to około 1 KB danych. Należy wziąć to pod uwagę podczas wybierania prawidłowego parametru pageSize.
>
> W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Używaj tylko udokumentowanych kolumn.
>
> Właściwości zdefiniowane w poniższej tabeli są wyświetlane alfabetycznie według identyfikatora właściwości. Podczas uruchamiania tego interfejsu API wynikowe dane wyjściowe nie muszą być zwracane w tej samej kolejności wymienionej w tej tabeli.

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
|Deviceid|Ciąg|Unikatowy identyfikator urządzenia w usłudze.
|DeviceName|Ciąg|W pełni kwalifikowana nazwa domeny (FQDN) urządzenia.
|Odcisk palca|Wartość logiczna|Unikatowy identyfikator certyfikatu.
|Ścieżka|Ciąg|Lokalizacja certyfikatu.
|SignatureAlgorithm|Ciąg|Użyto algorytmu wyznaczania wartości skrótu i algorytmu szyfrowania.
|Keysize|Ciąg|Rozmiar klucza używanego w algorytmie podpisu.
|Data wygaśnięcia|Ciąg|Data i godzina, po upływie których certyfikat nie jest już ważny.
|Issuedate|Ciąg|Najwcześniejsza data i godzina ważności certyfikatu.
|SubjectType|Ciąg|Wskazuje, czy właścicielem certyfikatu jest urząd certyfikacji, czy jednostka końcowa.
|Numer seryjny|Ciąg|Unikatowy identyfikator certyfikatu w systemach urzędu certyfikacji.
|IssuedTo|Obiektu|Jednostka, do której należy certyfikat; może być urządzeniem, osobą fizyczną lub organizacją.
|Wystawione Przez|Obiektu|Jednostka, która zweryfikowała informacje i podpisała certyfikat.
|KeyUsage|Ciąg|Prawidłowe zastosowania kryptograficzne klucza publicznego certyfikatu.
|ExtendedKeyUsage|Ciąg|Inne prawidłowe zastosowania certyfikatu.
|RbacGroupId|Ciąg|Identyfikator grupy kontroli dostępu opartej na rolach (RBAC).
|RbacGroupName|Ciąg|Grupa kontroli dostępu opartej na rolach (RBAC). Jeśli to urządzenie nie jest przypisane do żadnych grup RBAC, wartość będzie mieć wartość "Nieprzypisane". Jeśli organizacja nie zawiera żadnych grup RBAC, wartość będzie mieć wartość "Brak".

## <a name="16-example"></a>Przykład 1.6

### <a name="161-request-example"></a>1.6.1 Przykład żądania

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="162-response-example"></a>Przykład odpowiedzi 1.6.2

```json

  {
     "@odata.context":"https://127.0.0.1/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetCertificateAssessment)",
      "value":[
        {
        "deviceId":"49126b9e4a5473b5229c73799e9e55c48668101b",
        "deviceName":"testmachine5",
        "thumbprint":"A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "path":"LocalMachine\\TestSignRoot\\A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "signatureAlgorithm":"sha384ECDSA",
        "keyLength":0,"notAfter":"0001-01-01T00:00:00Z",
        "notBefore":"0001-01-01T00:00:00Z",
        "subjectType":"CA",
        "serialNumber":"6086A185EAFA2B9943B4671603F40323",
        "subjectObject":null,
        "issuerObject":null,
        "keyUsageArray":null,
        "extendedKeyUsageArray":null,
        "isSelfSigned":false,
        "rbacGroupId":4226,
        "rbacGroupName":"testO6343398Gq31"}],
        "@odata.nextLink":"https://127.0.0.1/api/machines/CertificateAssessmentByMachine?pagesize=1&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMi0wMy0yMS8wNTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjF9"
  }
```

## <a name="2-export-certificate-assessment-via-files"></a>2. Eksportowanie oceny certyfikatów (za pośrednictwem plików)

### <a name="21-api-method-description"></a>Opis metody interfejsu API w wersji 2.1

Zwraca wszystkie oceny certyfikatów dla wszystkich urządzeń na poszczególnych urządzeniach. Zwraca tabelę z oddzielnym wpisem dla każdej unikatowej kombinacji elementów DeviceId, Thumbprint i Path.

#### <a name="22-limitations"></a>2.2 Ograniczenia

- Ograniczenia szybkości dla tego interfejsu API to 5 wywołań na minutę i 20 wywołań na godzinę. 

### <a name="23-parameters"></a>Parametry 2.3

- sasValidHours: liczba godzin, przez które adresy URL pobierania będą ważne (maksymalnie 24 godziny).

### <a name="24-http-request"></a>2.4 Żądanie HTTP

```http
GET /api/machines/certificateAssessmentExport
```

### <a name="25-properties-json-response"></a>2.5 Właściwości (odpowiedź JSON)

> [!NOTE]
> Pliki są skompresowane gzip & w wielowierszowym formacie JSON.
>
> Adresy URL pobierania są ważne tylko przez 3 godziny; W przeciwnym razie można użyć parametru .
>
> Aby zmaksymalizować szybkość pobierania, upewnij się, że pobierasz dane z tego samego regionu świadczenia usługi Azure, w którym znajdują się twoje dane.
>
> Każdy rekord to około 1 KB danych. Należy wziąć to pod uwagę podczas wybierania parametru pageSize, który działa dla Ciebie.
>
> W odpowiedzi mogą zostać zwrócone dodatkowe kolumny. Te kolumny są tymczasowe i mogą zostać usunięte. Używaj tylko udokumentowanych kolumn.

Właściwość (ID)|Typ danych|Opis
:---|:---|:---
|Eksportowanie plików|Ciąg[tablica]|Lista adresów URL pobierania plików przechowujących bieżącą migawkę organizacji.
|GeneratedTime|Datetime|Czas wygenerowania eksportu.


## <a name="26-example"></a>Przykład 2.6

### <a name="261-request-example"></a>2.6.1 Przykład żądania

```http
GET https://api.securitycenter.contoso.com/api/machines/certificateAssessmentExport
```

### <a name="262-response-example"></a>Przykład odpowiedzi 2.6.2

```json
    {
        "@odata.context":"https://127.0.0.1/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
        "exportFiles":["https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4226/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=IMmwTOYmGvU0ei5AHLNAxnFCmZkE2jvBHzRmuAu9xaA%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4414/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=2r0y74WZsATa0DjQTwfBxNqL5vN2Wl0AZKHMNrxuJ30%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=75/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=uVdY4%2BBpMdPMwaD3G0RJTZkS4R9J8oN8I3tu%2FOcG35c%3D"],
        "generatedTime":"2022-03-20T13:18:00Z"
   }
```
