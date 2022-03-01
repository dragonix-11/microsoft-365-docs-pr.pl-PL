---
title: Wyizoluj interfejs API komputera
description: Dowiedz się, jak za pomocą izolować interfejs API komputera w celu odizolowania urządzenia od uzyskiwania dostępu do sieci zewnętrznej w programie Microsoft Defender for Endpoint.
keywords: apis, graph api, supported apis, isolate device
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
ms.openlocfilehash: 52063135280d9e91ca531546b4ae03cf5b42ccbf
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996274"
---
# <a name="isolate-machine-api"></a>Wyizoluj interfejs API komputera

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Umożliwia odizolowanie urządzenia od uzyskiwania dostępu do sieci zewnętrznej.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Pełna izolacji jest dostępna dla urządzeń Windows 10 wersji 1703 i w Windows 11.
> - Izolacji selektywnej jest dostępna dla urządzeń Windows 10 urządzeniach w wersji 1709 lub nowszej oraz na Windows 11.
> - W przypadku odizolowania urządzenia dozwolone są tylko niektóre procesy i miejsca docelowe. Dlatego urządzenia, które znajdują się za pełnym szyfrowaniem VPN, nie będą mogły uzyskać dostępu do usługi Microsoft Defender for Endpoint w chmurze, gdy urządzenie jest odizolowane. Zalecamy korzystanie z sieci VPN rozdzielaowej dla programu Microsoft Defender dla punktu końcowego i Program antywirusowy Microsoft Defender opartego na chmurze ruchu związanego z ochroną.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Machine.Isolate|"Odizoluj komputer"
Delegowane (konto służbowe)|Machine.Isolate|"Odizoluj komputer"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienia roli: "Aktywne akcje naprawcze" [(zobacz Tworzenie](user-roles.md) ról i zarządzanie nimi, aby uzyskać więcej informacji)
> - Użytkownik musi mieć dostęp do urządzenia w zależności od ustawień grupy urządzeń (zobacz Tworzenie grup urządzeń i zarządzanie [nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/isolate
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.
Typ zawartości|ciąg|application/json. **Wymagane**.

## <a name="request-body"></a>Treść wniosku

W treści żądania należy podać obiekt JSON o następujących parametrach:

Parametr|Wpisać|Opis
:---|:---|:---
Komentowanie|Ciąg|Komentarz do skojarzenia z akcją. **Wymagane**.
IsolationType|Ciąg|Typ izolacji. Dozwolone wartości to: "Pełne" lub "Selektywne".

**IsolationType** określa typ izolacji do wykonania i może być jedną z następujących czynności:

- Pełne: pełna izolacji
- Selektywne: Ograniczanie dostępu do sieci tylko ograniczonego zestawu aplikacji (aby uzyskać więcej szczegółowych informacji, zobacz Wyodrębnianie urządzeń [z](respond-machine-alerts.md#isolate-devices-from-the-network) sieci)

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 201 — utworzono kod odpowiedzi i [akcję maszynową](machineaction.md) w treści odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/isolate
```

```json
{
  "Comment": "Isolate machine due to alert 1234",
  "IsolationType": "Full" 
}
```

- Aby zwolnić urządzenie z izolacji, zobacz [Zwalnianie urządzenia z izolacji](unisolate-machine.md).
