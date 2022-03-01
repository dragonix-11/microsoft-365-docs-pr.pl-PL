---
title: Interfejs API ograniczania wykonywania aplikacji
description: Ten interfejs API umożliwia tworzenie wywołań związanych z ograniczaniem wykonywania przez aplikację.
keywords: apis, api Graph, obsługiwane api, zbieranie pakietu badania
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
ms.openlocfilehash: dee5ad9466793892d09af2f85faa9f3fd2348ca6
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996380"
---
# <a name="restrict-app-execution-api"></a>Interfejs API ograniczania wykonywania aplikacji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Ograniczanie wykonywania wszystkich aplikacji na urządzeniu z wyjątkiem wstępnie zdefiniowanego zestawu.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

[!include[Device actions note](../../includes/machineactionsnote.md)]


> [!IMPORTANT]
>
> - Ta akcja jest dostępna dla urządzeń na Windows 10, w wersji 1709 lub nowszej oraz na Windows 11.
> - Ta funkcja jest dostępna, jeśli Twoja organizacja używa Program antywirusowy Microsoft Defender.
> - Ta akcja musi spełniać wymagania dotyczące Windows Defender zasad integralności kontroli aplikacji i podpisywania. Aby uzyskać więcej informacji, zobacz [Formaty zasad integralności kodu i podpisywanie](/windows/device-security/device-guard/requirements-and-deployment-planning-guidelines-for-device-guard#code-integrity-policy-formats-and-signing).

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Machine.RestrictExecution|"Ogranicz wykonywanie kodu"
Delegowane (konto służbowe)|Machine.RestrictExecution|"Ogranicz wykonywanie kodu"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienia roli: "Aktywne akcje naprawcze" [(zobacz Tworzenie](user-roles.md) ról i zarządzanie nimi, aby uzyskać więcej informacji)
> - Użytkownik musi mieć dostęp do urządzenia w zależności od ustawień grupy urządzeń (zobacz Tworzenie grup urządzeń i zarządzanie [nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/restrictCodeExecution
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

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 201 — utworzono kod odpowiedzi i [akcję maszynową](machineaction.md) w treści odpowiedzi.

W przypadku wysłania wielu wywołań interfejsu API w celu ograniczenia wykonywania aplikacji dla tego samego urządzenia zwracana jest "oczekująca akcja maszynowa" lub HTTP 400 z komunikatem "Akcja jest już w toku".

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/restrictCodeExecution 
```

```json
{
  "Comment": "Restrict code execution due to alert 1234"
}
```

- Aby usunąć ograniczenie wykonywania kodu z urządzenia, zobacz [Usuwanie ograniczenia aplikacji](unrestrict-code-execution.md).
