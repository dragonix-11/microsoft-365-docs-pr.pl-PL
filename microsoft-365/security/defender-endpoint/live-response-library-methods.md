---
title: Metody i właściwości biblioteki odpowiedzi na żywo
description: Dowiedz się, jak używać metod i właściwości biblioteki odpowiedzi na żywo.
keywords: apis, graph api, obsługiwane api, get, devices
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
ms.technology: m365d
ms.openlocfilehash: c9eb1de08be8905a41b172a19a33db58dbdc19b9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705500"
---
#  <a name="live-response-library-methods-and-properties"></a>Metody i właściwości biblioteki odpowiedzi na żywo

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy: Program** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="methods"></a>Metody

| **Metoda**          | **Zwracany typ**         | **Opis**                         |
|---------------------|-------------------------|-----------------------------------------|
| Pliki biblioteki list  | Biblioteka zbierania plików | Jednostki plików biblioteki listy              |
| Upload do biblioteki   | Encję pliku biblioteki     | Upload pliku w bibliotece odpowiedzi na żywo |
| Usuwanie z biblioteki | Brak zawartości              | Usuwanie encji pliku biblioteki              |

## <a name="properties"></a>Właściwości

| **Właściwość** | **Type**                         | **Opis**                                        |
|--------------|----------------------------------|--------------------------------------------------------|
| Polecenia     | Kolekcja poleceń Live Response | Tablica obiektów Command. Wyświetl [polecenia odpowiedzi na żywo](live-response.md#live-response-commands). |

