---
title: Włączanie wycofania definicji dla Program antywirusowy Microsoft Defender
description: Włącz wycofanie definicji dla Program antywirusowy Microsoft Defender.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, defender, wycofanie definicji
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 06/10/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: dd9cd313dec962547acef85c6da326d3b6e5c58f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997265"
---
# <a name="turn-on-definition-retirement"></a>Włączanie wycofania definicji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Wycofanie definicji można skonfigurować przy użyciu funkcji zasady grupy. Wycofanie definicji sprawdza, czy komputer ma wymagane aktualizacje zabezpieczeń niezbędne do ochrony przed określoną luką w zabezpieczeniach. Jeśli system nie jest narażony na wykorzystywanie wykorzystywania w definicji, oznacza to, że ta definicja jest "wycofana". Jeśli wszystkie analizy zabezpieczeń dla danego protokołu zostaną wycofane, ten protokół nie będzie już analizowany. Włączenie tej funkcji zwiększa wydajność. Na komputerze, na który są aktualne wszystkie najnowsze aktualizacje zabezpieczeń, ochrona sieci nie ma wpływu na wydajność sieci.

## <a name="use-group-policy-to-configure-definition-retirement"></a>Konfigurowanie zasady grupy definiowania przy użyciu funkcji

1. Na swoim zasady grupy zarządzania kontami otwórz [konsolę zasady grupy zarządzania](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Przejdź do **szablonu administracyjnego konfiguracji** \> **komputera i** \> **Windows składników Program antywirusowy Microsoft Defender** \>  \> **inspekcji sieciowej**.

3. Wybierz **pozycję Włącz wycofanie definicji**. Domyślnie te zasady są włączone. Jeśli ustawiono **ustawienie Nieskonfigurowane**, wycofanie definicji jest włączone.

4. Aby edytować zasady, wybierz link **edytuj ustawienia zasad** .

5. Wybierz **pozycję Włączone**, a następnie wybierz przycisk **OK**.

6. Wdeksuj zaktualizowany obiekt zasady grupy obiekt. Zobacz [zasady grupy zarządzania](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Czy używasz lokalnego zasady grupy? Zobacz, jak tłumaczą się w chmurze. [Analizuj lokalne obiekty zasad grupy przy użyciu analizy zasady grupy w aplikacji Microsoft Endpoint Manager Podgląd](/mem/intune/configuration/group-policy-analytics).
