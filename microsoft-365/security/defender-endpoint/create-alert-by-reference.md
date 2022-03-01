---
title: Tworzenie alertów przy użyciu interfejsu API zdarzeń
description: Dowiedz się, jak za pomocą interfejsu API utwórz alert w celu utworzenia nowego alertu na podstawie zdarzenia w programie Microsoft Defender for Endpoint.
keywords: apis, api Graph, obsługiwane api, get, alert, information, id
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
ms.openlocfilehash: cc28ea9082e7afbb6f623e325a48119de393f075
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996418"
---
# <a name="create-alert-api"></a>Tworzenie interfejsu API alertów

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Opis interfejsu API

Powoduje utworzenie [nowego alertu](alerts.md) u góry **zdarzenia**.

- **Do utworzenia alertu jest wymagany program Microsoft Defender for Endpoint** Event.
- Musisz podać trzy parametry z zdarzenia w żądaniu **: Czas** zdarzenia, **Identyfikator komputera** **i Identyfikator raportu**. Zobacz przykład poniżej.
- Możesz użyć zdarzenia znalezionego w interfejsie Advanced Hunting API lub Portal.
- Jeśli na tym samym urządzeniu istnieje otwarty alert o tym samym tytule, nowy utworzony alert zostanie scalony z tym alertem.
- Automatyczne badanie jest rozpoczynane automatycznie w przypadku alertów utworzonych za pomocą interfejsu API.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 15 połączeń na minutę.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień | Uprawnienie | Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja | Alert.ReadWrite.All | "Czytanie i pisanie wszystkich alertów"
Delegowane (konto służbowe) | Alert.ReadWrite | "Alerty dotyczące czytania i pisania"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienia ról: "Badanie alertów" (Aby uzyskać więcej informacji, zobacz Tworzenie ról [i zarządzanie nimi](user-roles.md) )
> - Zależnie od ustawień grupy urządzeń użytkownik musi mieć dostęp do urządzenia skojarzonego z alertem (aby uzyskać więcej informacji, zobacz Tworzenie [grup urządzeń i zarządzanie nimi).](machine-groups.md)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja | Ciąg | Użytkownik {token}. **Wymagane**.
Typ zawartości | Ciąg | application/json. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

W treści żądania podać następujące wartości (wymagane są wszystkie):

Właściwość | Wpisać | Opis
:---|:---|:---
eventTime | DateTime(UTC) | Dokładny czas zdarzenia w postaci ciągu, uzyskany z czasu zaawansowanego szukania. np. **Wymagane**```2018-08-03T16:45:21.7115183Z```.
reportId | Ciąg | The reportId of the event, as obtained from advanced hunting. **Wymagane**.
machineId | Ciąg | Identyfikator urządzenia, na którym określono zdarzenie. **Wymagane**.
ważność | Ciąg | Ważność alertu. Wartości właściwości to: "Niskie", "Średnie" i "Wysokie". **Wymagane**.
tytuł | Ciąg | Tytuł alertu. **Wymagane**.
opis | Ciąg | Opis alertu. **Wymagane**.
recommendedAction| Ciąg | Podczas analizowania alertu musi to zrobić inspektor zabezpieczeń. **Wymagane**.
kategoria| Ciąg | Kategoria alertu. Wartości właściwości to: "Ogólne", "CommandAndControl", "Kolekcja", "CredentialAccess", "ObronaA", "Odnajdowanie", "Ex ex zamszły", "Exploit", "Execution", "InitialAccess", "LateralMovement", "Malware", "Persistence", "PrivilegeEscalation", "Ransomware", "SuspiciousActivity" **Required**.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 200 OK i nowy [obiekt alertu](alerts.md) w treści odpowiedzi. Jeśli nie znaleziono zdarzenia o określonych właściwościach (_reportId_, _eventTime_ i _machineId_) — 404 Nie znaleziono.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład prośby.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

```json
{
    "machineId": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
    "severity": "Low",
    "title": "example",
    "description": "example alert",
    "recommendedAction": "nothing",
    "eventTime": "2018-08-03T16:45:21.7115183Z",
    "reportId": "20776",
    "category": "Exploit"
}
```
