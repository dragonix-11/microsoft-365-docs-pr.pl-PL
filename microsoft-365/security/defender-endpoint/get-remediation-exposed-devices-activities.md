---
title: Lista dostępnych urządzeń w przypadku jednego działania naprawczego
description: Zwraca informacje o urządzeniach ujawnionych dla określonego zadania naprawczego.
keywords: api, działania naprawcze, interfejs API działań naprawczych, uzyskiwanie, zadania naprawcze, urządzenia udostępniane przez działania naprawcze
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
ms.openlocfilehash: 1a7dffa064b68b2c1ce0296b66eef663eb471496
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996359"
---
# <a name="list-exposed-devices-of-one-remediation-activity"></a>Lista dostępnych urządzeń w przypadku jednego działania naprawczego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Zwraca informacje o urządzeniach ujawnionych dla określonego zadania naprawczego.

[Dowiedz się więcej o działaniach naprawczych](tvm-remediation.md).

## <a name="list-exposed-devices-associated-with-a-remediation-task-id"></a>Lista dostępnych urządzeń skojarzonych z zadaniem rozwiązywania problemów (identyfikator)

**Adres URL:** GET: /api/remediationTasks/\{id\}/machineReferences

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Używanie interfejsów [API punktów końcowych programu Microsoft Defender, aby uzyskać szczegółowe informacje.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|RemediationTasks.Read.All|\'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'
Delegowane (konto służbowe)|RemediationTask.Read.Read|\'Odczytywanie informacji o lukach w zabezpieczeniach przed zagrożeniami i zarządzaniem nimi\'

## <a name="properties-details"></a>Szczegóły właściwości

Właściwość (identyfikator)|Typ danych|Opis|Przykład
:---|:---|:---|:---
identyfikator|Ciąg|Identyfikator urządzenia|w2957837fwda8w9ae7f023dba081059dw8d94503
computerDnsName|Ciąg|Nazwa urządzenia|PC-SRV2012R2Foo.UserNameVldNet.local
osPlatform|Ciąg|System operacyjny urządzenia|WindowsServer2012R2
rbacGroupName|Ciąg|Nazwa grupy urządzeń, z która jest skojarzone to urządzenie|Serwery

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/03942ef5-aecb-4c6e-b555-d6a97013844c/machinereferences
```

### <a name="response-example"></a>Przykład odpowiedzi

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "3cb5df6bb3640a2d37ad09fcd357b182d684fafc",
            "computerDnsName": "ComputerPII_2ea21b2d97c9df23c143ad9e3e454cb674232529.DomainPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3d9b1ca53e8f077199c7dcbfc9dbfa78f9bf1918",
            "computerDnsName": "ComputerPII_001d606fc149567c192747f48fae304b43c0ddba.DomainxPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3db8b27e6172951d7ea2e2d75945abec56feaf82",
            "computerDnsName": "ComputerPII_ce60cfbjj4b82a091deb5eae560332bba99a9bd7.DomainPII_0bc1aee0fa396d175e514bd61a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3bad326dcda5b53fab47408cd4a7080f3f3cc8ab",
            "computerDnsName": "ComputerPII_b6b35960dd6539d1d1cef5ada02e235e7b357408.DomainPII_21eed80b089e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        }
]
}
```

## <a name="see-also"></a>Zobacz też

- [Metody i właściwości środków zaradczych](get-remediation-methods-properties.md)
- [Uzyskiwanie jednego działania naprawczego według identyfikatora](get-remediation-one-activity.md)
- [Lista wszystkich działań naprawczych](get-remediation-all-activities.md)
- [Zagrożenia oparte na czynnikach ryzyka & zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Luki w zabezpieczeniach w organizacji](tvm-weaknesses.md)
