---
title: Określanie dodatkowych zestawów definicji dla inspekcji ruchu sieciowego dla Program antywirusowy Microsoft Defender
description: Określ dodatkowe zestawy definicji dla inspekcji ruchu sieciowego dla Program antywirusowy Microsoft Defender.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, defender, inspekcja ruchu sieciowego
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
ms.collection: M365-security-compliance
ms.openlocfilehash: f7b940604272035dc37b170eb759fa0ec45582b6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997887"
---
# <a name="specify-additional-definition-sets-for-network-traffic-inspection"></a>Określanie dodatkowych zestawów definicji dla inspekcji ruchu sieciowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Możesz określić dodatkowe zestawy definicji dla inspekcji ruchu sieciowego przy użyciu zasady grupy.

## <a name="use-group-policy-to-specify-additional-definition-sets-for-network-traffic-inspection"></a>Używanie zasady grupy do określania dodatkowych zestawów definicji dla inspekcji ruchu sieciowego

1. Na swoim zasady grupy zarządzania kontami otwórz [konsolę zasady grupy zarządzania](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Przejdź do **Windows składników Program antywirusowy Microsoft Defender** \>  \> **inspekcji sieci**.

3. Wybierz **pozycję Określ dodatkowe zestawy definicji dla inspekcji ruchu sieciowego**. Domyślnie te zasady są ustawione na **Nieskonfigurowane**.

4. Aby edytować zasady, wybierz link **edytuj ustawienia zasad** .

5. Wybierz **pozycję** Włączone, a następnie w **sekcji Opcje** wybierz pozycję **Pokaż....**

6. Dodaj wpisy do listy, a następnie wybierz przycisk **OK**.

   Każdy wpis musi być podany jako para wartość nazwy, gdzie nazwa jest reprezentacją ciągu identyfikatora GUID zestawu definicji. Jako przykład zestawu definicji Identyfikator GUID umożliwiający analizę zabezpieczeń testowych jest zdefiniowany jako: `{b54b6ac9-a737-498e-9120-6616ad3bf590}`. Ta wartość nie jest używana, dlatego zalecamy ustawienie jej na `0`.

7. Wybierz **przycisk OK**, a następnie wdaj zaktualizowany obiekt zasady grupy obiekt. Zobacz [zasady grupy zarządzania](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Czy używasz lokalnego zasady grupy? Zobacz, jak tłumaczą się w chmurze. [Analizuj lokalne obiekty zasad grupy przy użyciu analizy zasady grupy w aplikacji Microsoft Endpoint Manager Podgląd](/mem/intune/configuration/group-policy-analytics).

## <a name="related-articles"></a>Artykuły pokrewne

- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Jak tworzyć i wdrażać zasady ochrony przed złośliwym oprogramowaniem: usługa ochrony przed chmurą](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)