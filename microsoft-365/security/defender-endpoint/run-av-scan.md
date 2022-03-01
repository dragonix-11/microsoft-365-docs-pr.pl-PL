---
title: Uruchom interfejs API skanowania antywirusowego
description: Ten interfejs API umożliwia tworzenie połączeń związanych z uruchamianiem skanowania antywirusowego na urządzeniu.
keywords: apis, api Graph, obsługiwane api, usuń urządzenie z izolacji
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
ms.openlocfilehash: 3208ff32c2adda051b79fea684af915a909dd062
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016002"
---
# <a name="run-antivirus-scan-api"></a>Uruchom interfejs API skanowania antywirusowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Zainicjuj Program antywirusowy Microsoft Defender skanowanie na urządzeniu.

## <a name="limitations"></a>Ograniczenia

1. Ograniczenia stawek dla tego interfejsu API to 100 połączeń na minutę i 1500 połączeń na godzinę.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Ta akcja jest dostępna dla urządzeń na Windows 10, w wersji 1709 lub nowszej oraz na Windows 11.
> - Skanowanie Program antywirusowy Microsoft Defender (Microsoft Defender AV) może być uruchamiane razem z innymi rozwiązaniami antywirusowymi, niezależnie od tego, Program antywirusowy Microsoft Defender jest aktywnym rozwiązaniem antywirusowym. Program antywirusowy Microsoft Defender być w trybie pasywnym. Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender zgodności](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility).

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Używanie programu Microsoft Defender dla interfejsów API punktów końcowych.](apis-intro.md)

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
:---|:---|:---
Aplikacja|Machine.Scan|"Skanuj komputer"
Delegowane (konto służbowe)|Machine.Scan|"Skanuj komputer"

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć co najmniej następujące uprawnienia roli: "Aktywne akcje naprawcze" [(zobacz Tworzenie](user-roles.md) ról i zarządzanie nimi, aby uzyskać więcej informacji)
> - Użytkownik musi mieć dostęp do urządzenia w zależności od ustawień grupy urządzeń (zobacz Tworzenie grup urządzeń i zarządzanie [nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/runAntiVirusScan
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
:---|:---|:---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**.
Typ zawartości|ciąg|application/json

## <a name="request-body"></a>Treść wniosku

W treści żądania należy podać obiekt JSON o następujących parametrach:

Parametr|Wpisać|Opis
:---|:---|:---
Komentowanie|Ciąg|Komentarz do skojarzenia z akcją. **Wymagane**.
ScanType|Ciąg|Definiuje typ skanowania. **Wymagane**.

**Typ Skanowania** określa typ skanowania do wykonania. Może to być jedna z następujących czynności:

- **Szybkie**: wykonywanie szybkiego skanowania na urządzeniu
- **Pełne**: wykonaj pełne skanowanie na urządzeniu

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie, ta metoda zwróci wartość 201, Utworzono kod odpowiedzi i _obiekt MachineAction_ w treści odpowiedzi.

Jeśli wysyłasz wiele wywołań interfejsu API w celu uruchomienia skanowania antywirusowego dla tego samego urządzenia, zwraca on "oczekujące działanie maszynowe" lub HTTP 400 z komunikatem "Akcja jest już w toku".

## <a name="example"></a>Przykład

### <a name="request"></a>Zażądaj

Oto przykład wniosku.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runAntiVirusScan 
```

```json
{
  "Comment": "Check machine for viruses due to alert 3212",
  "ScanType": "Full"
}
```
