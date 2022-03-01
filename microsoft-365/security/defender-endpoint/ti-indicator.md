---
title: Typ zasobu wskaźników
description: Określ szczegóły jednostki i zdefiniuj wygaśnięcie wskaźnika przy użyciu programu Microsoft Defender dla punktu końcowego.
keywords: api, obsługiwane api, get, TiIndicator, Indicator, recent
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
ms.openlocfilehash: 8e8660574f65d614bacfe705d7fad19e39d501a6
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996862"
---
# <a name="indicator-resource-type"></a>Typ zasobu wskaźników

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

- Zobacz [odpowiadającą jej stronę Wskaźniki](https://securitycenter.windows.com/preferences2/custom_ti_indicators/files) w portalu.

Metoda|Zwracany typ|Opis
:---|:---|:---
[Wskaźniki listy](get-ti-indicators-collection.md)|[Wskaźnik](ti-indicator.md) Kolekcja|[Jednostki](ti-indicator.md) wskaźnika listy.
[Wskaźnik przesyłania](post-ti-indicator.md)|[Wskaźnik](ti-indicator.md)|Prześlij lub zaktualizuj [encję Wskaźnik](ti-indicator.md) .
[Wskaźniki importu](import-ti-indicators.md)|[Wskaźnik](ti-indicator.md) Kolekcja|Przesyłanie lub [aktualizowanie jednostek](ti-indicator.md) wskaźników.
[Wskaźnik usuwania](delete-ti-indicator-by-id.md)|Brak zawartości|Usuwa [encję Wskaźnik](ti-indicator.md) .

## <a name="properties"></a>Właściwości

Właściwość|Wpisać|Opis
:---|:---|:---
identyfikator|Ciąg|Tożsamość [encji Wskaźnik](ti-indicator.md) .
indicatorValue|Ciąg|Wartość [wskaźnika.](ti-indicator.md)
indicatorType (Typ wskaźnika)|Wyli roku|Typ wskaźnika. Dopuszczalne wartości to: "FileSha1", "FileSha256", "FileMd5", "CertificateThumbprint", "IpAddress", "DomainName" i "Url".
aplikacja|Ciąg|Aplikacja skojarzona ze wskaźnikiem.
akcja|Wyli roku|Akcja, która zostanie podjęta, jeśli wskaźnik zostanie wykryty w organizacji. Dopuszczalne wartości: "Ostrzegaj", "Blok", "Inspekcja", "Alert", "AlertAndBlock", "BlokujAndRemediate" i "Dozwolone".
|externalID|Ciąg|Identyfikator, który klient może przesłać w żądaniu korelacji niestandardowej.|
sourceType (Typ źródła)|Wyli roku|"Użytkownik" na wypadek, gdy wskaźnik utworzony przez użytkownika (na przykład z portalu), "AadApp" na wypadek, gdy został przesłany przy użyciu zautomatyzowanej aplikacji za pośrednictwem interfejsu API.
createdBySource|ciąg|Nazwa użytkownika/aplikacji, która przesłała wskaźnik.
createdBy|Ciąg|Unikatowa tożsamość użytkownika/aplikacji, która przesłała wskaźnik.
lastUpdatedBy|Ciąg|Tożsamość użytkownika/aplikacji, która ostatnio zaktualizowała wskaźnik.
creationTimeDateTimeUtc|DateTimeOffset|Data i godzina utworzenia wskaźnika.
expirationTime|DateTimeOffset|Czas wygaśnięcia wskaźnika.
lastUpdateTime|DateTimeOffset|Godzina ostatniej aktualizacji wskaźnika.
ważność|Wyli roku|Ważność wskaźnika. Możliwe wartości to: "Informacyjne", "Niskie", "Średnie" i "Wysokie".
tytuł|Ciąg|Tytuł wskaźnika.
opis|Ciąg|Opis wskaźnika.
zalecaneActions|Ciąg|Zalecane akcje dotyczące wskaźnika.
rbacGroupNames|Lista ciągów|Nazwy grup urządzeń RBAC, w których wskaźnik jest ujawniony i aktywny. Pusta lista na wypadek, gdy zostanie ona ujawniona na wszystkich urządzeniach.
rbacGroupIds|Lista ciągów|Identyfikator grupy urządzeń RBAC, gdzie wskaźnik jest ujawniony i aktywny. Pusta lista na wypadek, gdy zostanie ona ujawniona na wszystkich urządzeniach.
generateAlert|Wyli roku|**Ma wartość True** (Prawda), jeśli wymagane jest generowanie alertu, **fałsz** , jeśli ten wskaźnik nie powinien generować alertu.

## <a name="indicator-types"></a>Typy wskaźników

Typy akcji wskaźników obsługiwane przez interfejs API to:

- Dozwolone
- Inspekcja
- Blokuj
- BlockAndRemediate
- Ostrzegaj (tylko usługa Defender dla aplikacji w chmurze)

Aby uzyskać więcej informacji na temat opisów typów akcji odpowiedzi, zobacz [Tworzenie wskaźników](manage-indicators.md).

> [!Note]
>
> Wcześniejsze akcje odpowiedzi (AlertAndBlock i Alert) będą obsługiwane do stycznia 2022 r. Po tej dacie wszyscy klienci muszą korzystać z jednego z wymienionych powyżej typów akcji.

## <a name="json-representation"></a>Reprezentacja Jsona

```json
{
    "id": "994",
    "indicatorValue": "881c0f10c75e64ec39d257a131fcd531f47dd2cff2070ae94baa347d375126fd",
    "indicatorType": "FileSha256",
    "action": "AlertAndBlock",
    "application": null,
    "source": "user@contoso.onmicrosoft.com",
    "sourceType": "User",
    "createdBy": "user@contoso.onmicrosoft.com",
    "severity": "Informational",
    "title": "Michael test",
    "description": "test",
    "recommendedActions": "nothing",
    "creationTimeDateTimeUtc": "2019-12-19T09:09:46.9139216Z",
    "expirationTime": null,
    "lastUpdateTime": "2019-12-19T09:09:47.3358111Z",
    "lastUpdatedBy": null,
    "rbacGroupNames": ["team1"]
}
```
