---
title: Włącz rozpoznawanie protokołów dla Program antywirusowy Microsoft Defender
description: Włącz rozpoznawanie protokołów dla Program antywirusowy Microsoft Defender.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, defender, rozpoznawanie protokołów
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 05/07/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: cbb9b50714d252d86fcbaed9b43684351f903251
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997264"
---
# <a name="turn-on-protocol-recognition"></a>Włączanie rozpoznawania protokołów

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

To ustawienie zasad umożliwia skonfigurowanie rozpoznawania protokołów w celu ochrony sieci przed wykorzystywaniem luk w zabezpieczeniach, które są znane. Włączenie lub nieskonfigurowane tego ustawienia spowoduje włączenie rozpoznawania protokołów. Wyłączenie tego ustawienia spowoduje wyłączenie rozpoznawania protokołów.

## <a name="use-group-policy-to-configure-protocol-recognition"></a>Konfigurowanie rozpoznawania zasady grupy przy użyciu protokołu

1. Na swoim zasady grupy zarządzania kontami otwórz [konsolę zasady grupy zarządzania](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Przejdź do **szablonu administracyjnego konfiguracji** \> **komputera i** \> **Windows składników Program antywirusowy Microsoft Defender** \>  \> **inspekcji sieciowej**.

3. Wybierz **pozycję Rozpoznawanie protokołu**. Domyślnie te zasady są włączone. Jeśli ustawiono **ustawienie Nieskonfigurowane**, wycofanie definicji jest włączone.

4. Aby edytować zasady, wybierz link **edytuj ustawienia zasad** .

5. Wybierz **pozycję Włączone**, a następnie wybierz przycisk **OK**.

6. Wdeksuj zaktualizowany obiekt zasady grupy obiekt. Zobacz [zasady grupy zarządzania](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Czy używasz lokalnego zasady grupy? Zobacz, jak tłumaczą się w chmurze. [Analizuj lokalne obiekty zasad grupy przy użyciu analizy zasady grupy w aplikacji Microsoft Endpoint Manager Podgląd](/mem/intune/configuration/group-policy-analytics).

## <a name="related-articles"></a>Artykuły pokrewne

- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Jak tworzyć i wdrażać zasady ochrony przed złośliwym oprogramowaniem: usługa ochrony przed chmurą](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)