---
title: Interfejs API maszyny odłączaowej
description: Dowiedz się, jak używać interfejsu API do odłączenia urządzenia od Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: apis, graph api, obsługiwane interfejsy API, zbieranie pakietu badania
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
ms.openlocfilehash: ebfcfe21070656d71c50429cd4653d0e14f7724d
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493236"
---
# <a name="offboard-machine-api"></a>Interfejs API maszyny odłączaowej

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Opis interfejsu API

Odłącz urządzenie od usługi Defender for Endpoint.

## <a name="limitations"></a>Ograniczenia

- Ograniczenia szybkości dla tego interfejsu API to 100 wywołań na minutę i 1500 wywołań na godzinę.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> Ten interfejs API jest obsługiwany w systemie Windows 11, Windows 10, wersji 1703 lub nowszej albo w systemie Windows Server 2019 lub nowszym.
>
> Ten interfejs API nie jest obsługiwany na urządzeniach z systemem MacOS lub Linux.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz [Korzystanie z usługi Defender dla interfejsów API punktu końcowego](apis-intro.md)

Typ uprawnień|Uprawnienia|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Machine.Offboard|"Maszyna odłączona"
Delegowane (konto służbowe)|Machine.Offboard|"Maszyna odłączona"

> [!NOTE]
> Podczas uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć rolę usługi AD "Global Administracja"
> - Użytkownik musi mieć dostęp do urządzenia na podstawie ustawień grupy urządzeń (zobacz [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md) , aby uzyskać więcej informacji)

## <a name="http-request"></a>Żądanie HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

Identyfikator komputera można znaleźć w adresie URL po wybraniu urządzenia. Ogólnie rzecz biorąc, jest to 40-cyfrowy numer alfanumeryczny, który można znaleźć w adresie URL.

## <a name="request-headers"></a>Nagłówki żądań

Name (Nazwa)|Wpisać|Opis
---|---|---
Autoryzacji|Ciąg|Element nośny {token}. **Wymagane**.
Typ zawartości|Ciąg|application/json. **Wymagane**.

## <a name="request-body"></a>Treść żądania

W treści żądania podaj obiekt JSON z następującymi parametrami:

Parametr|Wpisać|Opis
---|---|---
Komentowanie|Ciąg|Komentarz do skojarzenia z akcją. **Wymagane**.

## <a name="response"></a>Odpowiedzi

W przypadku powodzenia ta metoda zwraca wartość 200 — utworzony kod odpowiedzi i [akcję maszyny](machineaction.md) w treści odpowiedzi.

## <a name="example"></a>Przykład

### <a name="request"></a>Żądanie

Oto przykład żądania. Jeśli nie dodano komentarza JSON, zostanie wyświetlony błąd z kodem **400**.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
