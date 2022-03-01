---
title: Omówienie wykrywanie i reagowanie w punktach końcowych funkcji
ms.reviewer: ''
description: Dowiedz się więcej o wykrywanie i reagowanie w punktach końcowych programu Microsoft Defender dla punktu końcowego
keywords: Program Microsoft Defender dla punktu końcowego, wykrywanie i reagowanie w punktach końcowych, odpowiedzi, wykrywania,ity, ochrony
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: cf09e20b0f11713152070b12c30efc4820d6678c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997275"
---
# <a name="overview-of-endpoint-detection-and-response"></a>Omówienie wykrywanie i reagowanie w punktach końcowych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Program Defender for Endpoint wykrywanie i reagowanie w punktach końcowych funkcje zaawansowane wykrywania ataków, które są blisko czasu rzeczywistego i które oferują akcję. Analitycy zabezpieczeń mogą efektywnie określać priorytety alertów, zyskać wgląd w pełny zakres naruszenia zabezpieczeń oraz podjąć działania w celu reagowania na zagrożenia.

Po wykryciu zagrożenia w systemie są tworzone alerty dla analityka w celu jego zbadania. Alerty z takich samych technik ataków lub przypisane do tego samego atakującego są agregowane w jednostkę nazywaną _zdarzeniem_. Agregowanie alertów w ten sposób ułatwia analitykom zbiorcze badanie zagrożeń i reagowanie na nie.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4o1j5]

Program Defender for Endpoint, który jest inspirowany myślą "założono naruszenie", stale zbiera dane telemetrii cyberprzestępczych. Proces ten obejmuje informacje o procesach, działania sieciowe, szczegółowe informacje do menedżera kernela i pamięci, działania związane z logowaniem użytkownika, zmiany rejestru i systemu plików oraz inne. Informacje są przechowywane przez sześć miesięcy, co pozwala analitykowi na powrót do chwili rozpoczęcia ataków. Analityk może następnie przechodzić w różne widoki i podchodzić do badania na wiele wektorów.

Funkcje reakcji dają Ci możliwości szybkiego korygowania zagrożeń, działając w podmiotach, których to dotyczy.

## <a name="related-topics"></a>Tematy pokrewne

- [Pulpit nawigacyjny operacji zabezpieczeń](security-operations-dashboard.md)
- [Kolejka zdarzeń](view-incidents-queue.md)
- [Kolejka alertów](alerts-queue.md)
- [Lista Urządzeń](machines-view-overview.md)
