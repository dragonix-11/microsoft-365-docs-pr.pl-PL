---
title: Uzyskiwanie jednego działania naprawczego według identyfikatora
description: Zwraca informacje dotyczące określonego działania naprawczego.
keywords: api, działania naprawcze, api działań naprawczych, uzyskiwanie, zadania naprawcze, działania naprawcze według identyfikatorów,
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6ea413621ad9d2e3b99fc5abdafd843705e7dc87
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63015806"
---
# <a name="get-one-remediation-activity-by-id"></a>Uzyskiwanie jednego działania naprawczego według identyfikatora

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Zwraca informacje dotyczące określonego działania naprawczego. Przedstawia te same kolumny, co kolumna Pobierz [wszystkie](get-remediation-all-activities.md) działania naprawcze", ale zwraca wyniki tylko dla _jednego określonego działania naprawczego_.

[Dowiedz się więcej o działaniach naprawczych](tvm-remediation.md).

## <a name="list-a-specified-remediation-activity-for-id"></a>Lista określonego działania naprawczego dla (ID)

**Adres URL:** GET: /api/remediationTasks/\{id\}

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|RemediationTasks.Read.All|\'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe)|RemediationTask.Read.Read|\'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

## <a name="properties"></a>Właściwości

Właściwość (identyfikator)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
Kategoria|Ciąg|Kategoria działań naprawczych (konfiguracja oprogramowania/zabezpieczeń)|Oprogramowanie
completerEmail|Ciąg|Jeśli działania naprawcze zostały wykonane ręcznie przez inną osobę, ta kolumna zawiera adres e-mail tej osoby|Null
completerId|Ciąg|Jeśli działania naprawcze zostały wykonane ręcznie przez inną osobę, ta kolumna zawiera identyfikator obiektu|Null
completionMethod|Ciąg|Działania naprawcze mogą być wykonywane "automatycznie" (jeśli wszystkie urządzenia zostały naprawone) lub "ręcznie" przez osobę, która wybierze pozycję "Oznacz jako ukończone".|Automatyczne
createdOn|DateTime|Godzina utworzenia tego działania naprawczego|2021-01-12T18:54:11.5499478Z
Opis|Ciąg|Opis tego działania naprawczego|Zaktualizuj program Microsoft Silverlight do nowszej wersji, aby zminimalizować znane luki w zabezpieczeniach wpływających na urządzenia.
dueOn|DateTime|Termin realizacji tego działania naprawczego ustawiony przez twórcę|2021-01-13T00:00:00Z
fixedDevices||Liczba urządzeń, które zostały naprawione|2
Identyfikator|Ciąg|Identyfikator tego działania naprawczego|097d9735-5479-4899-b1b7-77398899df92
nameId|Ciąg|Powiązana nazwa produktu|Microsoft Silverlight
Priority (Priorytet)|Ciąg|Priorytet zestawu twórców dla tego działania naprawczego (Wysoki\Średni\Niski)|High (Wysoki)
productId|Ciąg|Identyfikator produktu pokrewnego|microsoft-_-silverlight
productivityImpactRemediationType|Ciąg|O kilka zmian w konfiguracji można zażądać tylko w przypadku urządzeń, które nie wpływają na użytkowników. Ta wartość wskazuje wybór między "wszystkimi ujawnione urządzeniami" lub "tylko urządzeniami bez wpływu na użytkownika".|AllExposedAssets
rbacGroupNames|Ciąg|Nazwy grup urządzeń pokrewnych|[ "Windows Servers", "Windows 11", "Windows 10" ]
recommendedProgram|Ciąg|Zalecany program do uaktualnienia do wersji|Null
zalecana firmaVendor|Ciąg|Zaleca się uaktualnienie do wersji zalecanej przez dostawcę|Null
recommendedVersion|Ciąg|Zalecana wersja do aktualizacji/uaktualnienia do|Null
relatedComponent|Ciąg|Powiązany składnik tego działania naprawczego (podobny do składnika pokrewnego w przypadku zalecenia zabezpieczeń)|Microsoft Silverlight
requesterEmail|Ciąg|Adres e-mail twórcy|globaladmin@UserName.contoso.com
requesterId|Ciąg|Identyfikator obiektu Kreatora|r647211f-2e16-43f2-a480-16ar3a2a796r
requesterNotes|Ciąg|Uwagi (bezpłatny tekst) dodane przez autora w celu działania naprawczego|Null
Scid|Ciąg|SCID pokrewnego zalecenia zabezpieczeń|Null
Stan|Ciąg|Stan działań naprawczych (Aktywne/Ukończone)|Aktywny
statusLastModifiedOn|DateTime|Data zaktualizowania pola stanu|2021-01-12T18:54:11.5499487Z
targetDevices|Długa|Liczba ujawnionych urządzeń, których działania naprawcze mają zastosowanie|43
Tytuł|Ciąg|Tytuł tego działania naprawczego|Microsoft Silverlight
Wpisać|Ciąg|Typ działań naprawczych|Aktualizacja
vendorId|Ciąg|Nazwa dostawcy pokrewnego|Microsoft

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/03942ef5-aecb-4c6e-b555-d6a97013844c
```

### <a name="response-example"></a>Przykład odpowiedzi

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#RemediationTasks/$entity",
    "id": "03942ef5-aecb-4c6e-b555-d6a97013844c",
    "title": "Update Microsoft Silverlight",
    "createdOn": "2021-02-10T13:20:36.4718166Z",
    "requesterId": "65548a1d-efo0-4a7a-8d19-1b967b5c36f4",
    "requesterEmail": "user1@contoso.com",
    "status": "Active",
    "statusLastModifiedOn": "2021-02-10T13:20:36.4719698Z",
    "description": "Update Silverlight to a later version to mitigate 55 known vulnerabilities affecting your devices. Doing so can help lessen the security risk to your organization due to versions which have reached their end-of-support.",
    "relatedComponent": "Microsoft Silverlight",
    "targetDevices": 18511,
    "rbacGroupNames": [
        "UnassignedGroup",
        "hhh"
    ],
    "fixedDevices": 2866,
    "requesterNotes": "test",
    "dueOn": "2021-02-11T00:00:00Z",
    "category": "Software",
    "productivityImpactRemediationType": null,
    "priority": "Medium",
    "completionMethod": null,
    "completerId": null,
    "completerEmail": null,
    "scid": null,
    "type": "Update",
    "productId": "microsoft-_-silverlight",
    "vendorId": "microsoft",
    "nameId": "silverlight",
    "recommendedVersion": null,
    "recommendedVendor": null,
    "recommendedProgram": null
}
```

## <a name="see-also"></a>Zobacz też

- [Metody i właściwości środków zaradczych](get-remediation-methods-properties.md)
- [Lista wszystkich działań naprawczych](get-remediation-all-activities.md)
- [Lista dostępnych urządzeń w przypadku jednego działania naprawczego](get-remediation-exposed-devices-activities.md)
- [Zagrożenia oparte na czynnikach ryzyka & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
