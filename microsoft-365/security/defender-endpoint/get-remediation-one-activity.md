---
title: Pobierz jedną akcję korygującą według identyfikatora
description: Zwraca informacje dotyczące określonego działania korygowania.
keywords: apis, korygowanie, interfejs API korygowania, pobieranie, zadania korygowania, korygowanie według identyfikatora,
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
ms.openlocfilehash: cac976b7c189a44ff206b64bb9fe0f1a5d8c5d4a
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839010"
---
# <a name="get-one-remediation-activity-by-id"></a>Pobierz jedną akcję korygującą według identyfikatora

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Zarządzanie lukami w zabezpieczeniach w usłudze Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Zwraca informacje dotyczące określonego działania korygowania. Przedstawia te same kolumny co [działanie Pobierz wszystkie korygowanie](get-remediation-all-activities.md)", ale zwraca wyniki _tylko dla jednego określonego działania korygowania_.

[Dowiedz się więcej o działaniach korygowania](tvm-remediation.md).

## <a name="list-a-specified-remediation-activity-for-id"></a>Wyświetl listę określonego działania korygowania (ID)

**ADRES URL:** GET: /api/remediationTasks/\{id\}

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|RemediationTasks.Read.All|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'
Delegowane (konto służbowe)|RemediationTask.Read.Read|\'Przeczytaj informacje o lukach w zabezpieczeniach dotyczące zarządzania zagrożeniami i lukami w zabezpieczeniach\'

## <a name="properties"></a>Właściwości

Właściwość (ID)|Typ danych|Opis|Przykład zwracanej wartości
:---|:---|:---|:---
Kategoria|Ciąg|Kategoria działania korygowania (konfiguracja oprogramowania/zabezpieczeń)|Oprogramowanie
completerEmail|Ciąg|Jeśli działanie korygujące zostało wykonane ręcznie przez kogoś, ta kolumna zawiera adres e-mail|Null
completerId|Ciąg|Jeśli działanie korygowania zostało wykonane ręcznie przez kogoś, ta kolumna zawiera identyfikator obiektu|Null
completionMethod|Ciąg|Działanie korygowania może zostać wykonane "automatycznie" (jeśli wszystkie urządzenia zostaną poprawione) lub "ręcznie" przez osobę, która wybierze pozycję "oznacz jako ukończone"|Automatyczne
createdOn|Datetime|Czas utworzenia tego działania korygowania|2021-01-12T18:54:11.5499478Z
Opis|Ciąg|Opis tego działania korygowania|Zaktualizuj program Microsoft Silverlight do nowszej wersji, aby ograniczyć znane luki w zabezpieczeniach wpływające na urządzenia.
dueOn|Datetime|Data ukończenia ustawiona przez twórcę dla tego działania korygowania|2021-01-13T00:00:00Z
fixedDevices||Liczba urządzeń, które zostały naprawione|2
ID|Ciąg|Identyfikator tego działania korygowania|097d9735-5479-4899-b1b7-77398899df92
nameId|Ciąg|Pokrewna nazwa produktu|Microsoft Silverlight
Priority (Priorytet)|Ciąg|Priorytet dla tego działania korygowania ustawionego przez twórcę (High\Medium\Low)|High (Wysoki)
Productid|Ciąg|Identyfikator produktu pokrewne|microsoft-_-silverlight
productivityImpactRemediationType|Ciąg|Można zażądać kilku zmian konfiguracji tylko w przypadku urządzeń, które nie mają wpływu na użytkowników. Ta wartość wskazuje wybór między "wszystkimi uwidocznionymi urządzeniami" lub "tylko urządzeniami bez wpływu na użytkownika".|AllExposedAssets
rbacGroupNames|Ciąg|Nazwy powiązanych grup urządzeń|[ "serwery Windows", "Windows 11", "Windows 10" ]
recommendedProgram|Ciąg|Zalecany program do uaktualnienia do|Null
recommendedVendor|Ciąg|Zalecany dostawca do uaktualnienia do|Null
recommendedVersion|Ciąg|Zalecana wersja do aktualizacji/uaktualnienia do|Null
Relatedcomponent|Ciąg|Powiązany składnik tego działania korygowania (podobny do powiązanego składnika zalecenia dotyczącego zabezpieczeń)|Microsoft Silverlight
requesterEmail|Ciąg|Adres e-mail twórcy|globaladmin@UserName.contoso.com
requesterId|Ciąg|Identyfikator obiektu twórcy|r647211f-2e16-43f2-a480-16ar3a2a796r
requesterNotes|Ciąg|Notatki (bezpłatny tekst) dodane przez twórcę dla tego działania korygowania|Null
Scid|Ciąg|SCID powiązanego zalecenia dotyczącego zabezpieczeń|Null
Stan|Ciąg|Stan działania korygowania (aktywny/ukończony)|Aktywny
statusLastModifiedOn|Datetime|Data aktualizacji pola stanu|2021-01-12T18:54:11.5499487Z
targetDevices|Długi|Liczba uwidocznionych urządzeń, których dotyczy to korygowanie|43
Tytuł|Ciąg|Tytuł tego działania korygowania|Microsoft Silverlight
Wpisać|Ciąg|Typ korygowania|Aktualizacja
Vendorid|Ciąg|Nazwa powiązanego dostawcy|Microsoft

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

- [Metody i właściwości korygowania](get-remediation-methods-properties.md)
- [Wylistuj wszystkie działania korygujące](get-remediation-all-activities.md)
- [Wylistuj narażone urządzenia z jednym działaniem korygowania](get-remediation-exposed-devices-activities.md)
- [& zarządzanie lukami w zabezpieczeniach zagrożeń opartych na ryzyku](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
