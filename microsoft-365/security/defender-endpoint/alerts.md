---
title: Interfejs API alertów
description: Dowiedz się więcej o metodach i właściwościach typu zasobu Alert w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, alerts, recent
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3344bb13d785739f7957c3b0d000b04ae7fea95b
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62973985"
---
# <a name="alert-resource-type"></a>Typ zasobu alertu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="methods"></a>Metody

<br>

****

|Metoda|Zwracany typ|Opis|
|---|---|---|
|[Otrzymuj alert](get-alert-info-by-id.md)|[Alert](alerts.md)|Uzyskiwanie pojedynczego [obiektu alertu](alerts.md) .|
|[Alerty listy](get-alerts.md)|[Kolekcja alertów](alerts.md)|Zbiór [alertów](alerts.md) listy.|
|[Aktualizowanie alertu](update-alert.md)|[Alert](alerts.md)|Aktualizowanie określonego [alertu](alerts.md).|
|[Alerty aktualizacji wsadowej](batch-update-alerts.md)||Aktualizowanie partii [alertów](alerts.md).|
|[Tworzenie alertu](create-alert-by-reference.md)|[Alert](alerts.md)|Tworzenie alertu na podstawie danych zdarzeń uzyskanych z wyszukiwania [zaawansowanego](run-advanced-query-api.md).|
|[Lista powiązanych domen](get-alert-related-domain-info.md)|Kolekcja domen|Adresy URL listy skojarzone z alertem.|
|[Lista powiązanych plików](get-alert-related-files-info.md)|[Kolekcja](files.md) plików|W tym [celu należy wyświetlić listę](files.md) jednostek plików skojarzonych z [alertem](alerts.md).|
|[Lista powiązanych adresów IP](get-alert-related-ip-info.md)|Kolekcja adresów IP|Lista adresów IP skojarzonych z alertem.|
|[Uzyskiwanie powiązanych komputerów](get-alert-related-machine-info.md)|[Komputer](machine.md)|Komputer [skojarzony](machine.md) z [alertem](alerts.md).|
|[Uzyskiwanie powiązanych użytkowników](get-alert-related-user-info.md)|[Użytkownik](user.md)|Użytkownik [skojarzony](user.md) z [alertem](alerts.md).|
|

## <a name="properties"></a>Właściwości

<br>

****

|Właściwość|Wpisać|Opis|
|---|---|---|
|identyfikator|Ciąg|Identyfikator alertu.|
|tytuł|Ciąg|Tytuł alertu.|
|opis|Ciąg|Opis alertu.|
|alertCreationTime|Nullable DateTimeOffset|Data i godzina utworzenia alertu (w czasie UTC).|
|lastEventTime|Nullable DateTimeOffset|Ostatnie wystąpienie zdarzenia, które wyzwoliło alert na tym samym urządzeniu.|
|firstEventTime|Nullable DateTimeOffset|Pierwsze wystąpienie zdarzenia, które wyzwoliło alert na tym urządzeniu.|
|lastUpdateTime|Nullable DateTimeOffset|Data i godzina ostatniej aktualizacji alertu (w czasie UTC).|
|resolvedTime|Nullable DateTimeOffset|Data i godzina zmiany stanu alertu na "Rozwiązano".|
|incidentId|Nullable Long|Identyfikator [zdarzenia](view-incidents-queue.md) alertu.|
|investigationId|Nullable Long|Identyfikator [badania](automated-investigations.md) związany z alertem.|
|investigationState|Wyliczność z wartością null|Bieżący [stan badania.](automated-investigations.md) Dopuszczalne wartości: "Nieznane", "Zakończone", "PomyślnieRemediated", "Szybki", "Zakończony niepowodzenie", "CzęściowoRemediated", "Uruchomiony", "OczekującyApproval", "OczekiwanieResource", "Częściowo Reinwestowane", "ZakończoneByUser", "TerminatedBySystem", "Queued", 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.|
|assignedTo|Ciąg|Właściciel alertu.|
|rbacGroupName|Ciąg|Nazwa grupy urządzeń RBAC.|
|mitreTechniques|Ciąg|Mitre Enterprise identyfikatora techniki.|
|relatedUser|Ciąg|Szczegóły dotyczące użytkownika związanego z określonym alertem.|
|ważność|Wyli roku|Ważność alertu. Dopuszczalne wartości: "Nieokreślone", "Informacyjne", "Niskie", "Średnie" i "Wysokie".|
|stan|Wyli roku|Określa bieżący stan alertu. Dopuszczalne wartości: "Nieznane", "Nowe", "InProgress" i "Rozpoznane".|
|klasyfikacja|Wyliczność z wartością null|Specyfikacja alertu. Dopuszczalne wartości: "Nieznany", "FałszPozyty", "TruePositive".|
|wyznaczanie|Wyliczność z wartością null|Określa określenie alertu. Dopuszczalne wartości to: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'.|
|kategoria|Ciąg|Kategoria alertu.|
|detectionSource (Źródło wykrywania)|Ciąg|Źródło wykrywania.|
|threatFamilyName|Ciąg|Rodzina zagrożeń.|
|threatName|Ciąg|Nazwa zagrożenia.|
|machineId|Ciąg|Identyfikator [jednostki komputera](machine.md) skojarzonej z alertem.|
|computerDnsName|Ciąg|[w](machine.md) pełni kwalifikowaną nazwę komputera.|
|aadTenantId|Ciąg|Identyfikator Azure Active Directory.|
|2016|Ciąg|Identyfikator użytkownika, który wyzwolił alert.|
|komentarze|Lista komentarzy alertów|Obiekt Komentarz alertu zawiera: ciąg komentarza, utworzonyWłasnyW ciągu i createTime date time.|
|Dowód|Lista dowodów alertu|Dowód związany z alertem. Zobacz przykład poniżej.|
|

### <a name="response-example-for-getting-single-alert"></a>Przykład odpowiedzi na pojedyncze alerty:

```http
GET https://api.securitycenter.microsoft.com/api/alerts/da637472900382838869_1364969609
```

```json
{
    "id": "da637472900382838869_1364969609",
    "incidentId": 1126093,
    "investigationId": null,
    "assignedTo": null,
    "severity": "Low",
    "status": "New",
    "classification": null,
    "determination": null,
    "investigationState": "Queued",
    "detectionSource": "WindowsDefenderAtp",
    "detectorId": "17e10bbc-3a68-474a-8aad-faef14d43952",
    "category": "Execution",
    "threatFamilyName": null,
    "title": "Low-reputation arbitrary code executed by signed executable",
    "description": "Binaries signed by Microsoft can be used to run low-reputation arbitrary code. This technique hides the execution of malicious code within a trusted process. As a result, the trusted process might exhibit suspicious behaviors, such as opening a listening port or connecting to a command-and-control (C&C) server.",
    "alertCreationTime": "2021-01-26T20:33:57.7220239Z",
    "firstEventTime": "2021-01-26T20:31:32.9562661Z",
    "lastEventTime": "2021-01-26T20:31:33.0577322Z",
    "lastUpdateTime": "2021-01-26T20:33:59.2Z",
    "resolvedTime": null,
    "machineId": "111e6dd8c833c8a052ea231ec1b19adaf497b625",
    "computerDnsName": "temp123.middleeast.corp.microsoft.com",
    "rbacGroupName": "A",
    "aadTenantId": "a839b112-1253-6432-9bf6-94542403f21c",
    "threatName": null,
    "mitreTechniques": [
        "T1064",
        "T1085",
        "T1220"
    ],
    "relatedUser": {
        "userName": "temp123",
        "domainName": "DOMAIN"
    },
    "comments": [
        {
            "comment": "test comment for docs",
            "createdBy": "secop123@contoso.com",
            "createdTime": "2021-01-26T01:00:37.8404534Z"
        }
    ],
    "evidence": [
        {
            "entityType": "User",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": null,
            "sha256": null,
            "fileName": null,
            "filePath": null,
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": "name",
            "domainName": "DOMAIN",
            "userSid": "S-1-5-21-11111607-1111760036-109187956-75141",
            "aadUserId": "11118379-2a59-1111-ac3c-a51eb4a3c627",
            "userPrincipalName": "temp123@microsoft.com",
            "detectionStatus": null
        },
        {
            "entityType": "Process",
            "evidenceCreationTime": "2021-01-26T20:33:58.6133333Z",
            "sha1": "ff836cfb1af40252bd2a2ea843032e99a5b262ed",
            "sha256": "a4752c71d81afd3d5865d24ddb11a6b0c615062fcc448d24050c2172d2cbccd6",
            "fileName": "rundll32.exe",
            "filePath": "C:\\Windows\\SysWOW64",
            "processId": 3276,
            "processCommandLine": "rundll32.exe  c:\\temp\\suspicious.dll,RepeatAfterMe",
            "processCreationTime": "2021-01-26T20:31:32.9581596Z",
            "parentProcessId": 8420,
            "parentProcessCreationTime": "2021-01-26T20:31:32.9004163Z",
            "parentProcessFileName": "rundll32.exe",
            "parentProcessFilePath": "C:\\Windows\\System32",
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        },
        {
            "entityType": "File",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": "8563f95b2f8a284fc99da44500cd51a77c1ff36c",
            "sha256": "dc0ade0c95d6db98882bc8fa6707e64353cd6f7767ff48d6a81a6c2aef21c608",
            "fileName": "suspicious.dll",
            "filePath": "c:\\temp",
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        }
    ]
}
```
