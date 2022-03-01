---
title: typ zasobu akcji komputera
description: Informacje o metodach i właściwościach typu zasobu MachineAction w programie Microsoft Defender for Endpoint.
keywords: api, obsługiwane api, get, machineaction, recent
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
ms.technology: mde
ms.openlocfilehash: 625170f0e589ece6f6277dc8445f3af7bef11837
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996349"
---
# <a name="machineaction-resource-type"></a>Typ zasobu Akcji Maszynowej

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


- Aby uzyskać więcej informacji, zobacz [Akcje odpowiedzi](respond-machine-alerts.md).

|Metoda|Zwracany typ|Opis|
|---|---|---|
|[Lista akcji maszynowych](get-machineactions-collection.md)|[Akcja maszynowa](machineaction.md)|Lista [jednostek akcji](machineaction.md) maszynowych.|
|[Get MachineAction](get-machineaction-object.md)|[Akcja maszynowa](machineaction.md)|Pobierz pojedynczą [jednostkę akcja komputera](machineaction.md) .|
|[Zbierz pakiet badania](collect-investigation-package.md)|[Akcja maszynowa](machineaction.md)|Zbierz pakiet badania z [komputera](machine.md).|
|[Uzyskiwanie pakietu badania, URI SAS](get-package-sas-uri.md)|[Akcja maszynowa](machineaction.md)|Uzyskaj URI do pobrania pakietu badania.|
|[Wyizoluj komputer](isolate-machine.md)|[Akcja maszynowa](machineaction.md)|[Wyizoluj komputer](machine.md) z sieci.|
|[Zwolnij komputer z izolacji](unisolate-machine.md)|[Akcja maszynowa](machineaction.md)|Zwolnij [komputer](machine.md) z izolacji.|
|[Ograniczanie wykonywania aplikacji](restrict-code-execution.md)|[Akcja maszynowa](machineaction.md)|Ogranicz wykonywanie aplikacji.|
|[Usuwanie ograniczeń aplikacji](unrestrict-code-execution.md)|[Akcja maszynowa](machineaction.md)|Usuwanie ograniczeń wykonywania aplikacji.|
|[Uruchom skanowanie antywirusowe](run-av-scan.md)|[Akcja maszynowa](machineaction.md)|Uruchom skanowanie wideo przy użyciu Windows Defender (jeśli ma zastosowanie).|
|[Urządzenie wye startowe](offboard-machine-api.md)|[Akcja maszynowa](machineaction.md)|Komputer [wye webboard z](machine.md) usługi Microsoft Defender for Endpoint.|
|[Zatrzymywanie i poddaj kwarantannie plik](stop-and-quarantine-file.md)|[Akcja maszynowa](machineaction.md)|Zatrzymaj wykonywanie pliku na komputerze i usuń go.|
|[Uruchom odpowiedź na żywo](run-live-response.md)|[Akcja maszynowa](machineaction.md)|Uruchamia sekwencję poleceń odpowiedzi na żywo na urządzeniu.|
|[Uzyskiwanie odpowiedzi na żywo](get-live-response-result.md)|Jednostka adresu URL|Pobiera określony link pobierania wyników polecenia na żywo odpowiedzi na jego indeks.|
|[Anuluj akcję komputera](cancel-machine-action.md)|[Akcja maszynowa](machineaction.md)|Anulowanie aktywnej akcji komputera.|

<br>

## <a name="properties"></a>Właściwości

|Właściwość|Wpisać|Opis|
|---|---|---|
|Identyfikator|Guid|Tożsamość [jednostki Akcja komputera](machineaction.md) .|
|wpisz tekst|Wyli roku|Typ akcji. Dopuszczalne wartości to: "RunAntiVirusFile", "Offboard", "Live Response", "CollectInvestigationPackage", "Isolate", "Unisolate", "StopAndQuarantineFile", "RestrictCodeExecution" i "UnrestrictCodeExecution".|
|zakres|ciąg|Zakres akcji. "Full" lub "Selective" for Isolation, "Quick" lub "Full" for Anti-Virus scan.|
|żąda który żąda|Ciąg|Tożsamość osoby, która wykonała akcję.|
|externalID|Ciąg|Identyfikator, który klient może przesłać w żądaniu korelacji niestandardowej.|
|requestSource (źródło żądania)|ciąg|Nazwa użytkownika/aplikacji, która przesłała akcję.|
|polecenia|tablica|Polecenia do uruchomienia. Dozwolone wartości to PutFile, RunScript, GetFile.|
|cancellationRequestor|Ciąg|Tożsamość osoby, która anulowała akcję.|
|requestorComment|Ciąg|Komentarz napisany podczas wydawania akcji.|
|cancellationComment|Ciąg|Komentarz napisany podczas anulowania akcji.|
|stan|Wyli roku|Bieżący stan polecenia. Dopuszczalne wartości: "Oczekiwanie", "Ruch wychodzący", "Pomyślnie", "Niepowodzenie", "Limit czasu" i "Anulowane".|
|machineId|Ciąg|Identyfikator komputera [,](machine.md) na którym wykonano akcję.|
|computerDnsName|Ciąg|Nazwa komputera [,](machine.md) na którym wykonano akcję.|
|creationDateTimeUtc|DateTimeOffset|Data i godzina utworzenia akcji.|
|cancellationDateTimeUtc|DateTimeOffset|Data i godzina anulowania akcji.|
|lastUpdateDateTimeUtc|DateTimeOffset|Data i godzina ostatniej aktualizacji stanu akcji.|
|tytuł|Ciąg|Tytuł akcji komputera.|
|relatedFileInfo|Zajęcia|Zawiera dwie właściwości. ciąg `fileIdentifier`, wylimij `fileIdentifierType` z możliwymi wartościami: "Sha1", "Sha256" i "Md5".|

## <a name="json-representation"></a>Reprezentacja Jsona

```json
{
        "id": "5382f7ea-7557-4ab7-9782-d50480024a4e",
        "type": "Isolate",
        "scope": "Selective",
        "requestor": "Analyst@TestPrd.onmicrosoft.com",
        "requestorComment": "test for docs",
        "status": "Succeeded",
        "machineId": "7b1f4967d9728e5aa3c06a9e617a22a4a5a17378",
        "computerDnsName": "desktop-test",
        "creationDateTimeUtc": "2019-01-02T14:39:38.2262283Z",
        "lastUpdateDateTimeUtc": "2019-01-02T14:40:44.6596267Z",
        "relatedFileInfo": null
}
```
