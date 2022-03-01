---
title: Zgodność rozwiązania antywirusowego z programem Defender for Endpoint
description: Dowiedz się, jak Windows Defender programem Microsoft Defender dla punktu końcowego. Dowiedz się też, jak działa program Defender for Endpoint, gdy jest używany klient innej firmy chroniącej przed złośliwym oprogramowaniem.
keywords: zgodność z programem windows defender, defender, Microsoft Defender for Endpoint, defender for endpoint, antivirus, mde
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.date: 05/06/2021
ms.technology: mde
ms.openlocfilehash: a8384ed28e8c65871f61241dc522461390106be0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997818"
---
# <a name="antivirus-solution-compatibility-with-microsoft-defender-for-endpoint"></a>Zgodność rozwiązania antywirusowego z programem Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-defendercompat-abovefoldlink)

Agent programu Microsoft Defender for Endpoint zależy Program antywirusowy Microsoft Defender niektórych funkcji, takich jak skanowanie plików.

> [!IMPORTANT]
> Program Defender for Endpoint nie jest zgodny z Program antywirusowy Microsoft Defender wykluczeń.

Musisz skonfigurować aktualizacje analizy zabezpieczeń na urządzeniu z programem Defender dla punktów końcowych, niezależnie od Program antywirusowy Microsoft Defender, czy jest on aktywnym złośliwym oprogramowaniem. Aby uzyskać więcej informacji, zobacz [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md).

Jeśli urządzenie w urządzeniu w urządzeniu jest chronione przez klienta ochrony przed złośliwym oprogramowaniem innej firmy, Program antywirusowy Microsoft Defender na tym punkcie końcowym stanie się ona pasywna.

Program antywirusowy Microsoft Defender będą nadal otrzymywać aktualizacje, a procesmspeng.exezostanie wymieniony ** jako uruchomiona usługa. Nie będzie jednak przeprowadzać skanów i nie zastępuje uruchomionego klienta ochrony przed złośliwym oprogramowaniem innej firmy.

Interfejs Program antywirusowy Microsoft Defender zostanie wyłączony. Użytkownicy urządzenia nie będą mogli przeprowadzać skanów na Program antywirusowy Microsoft Defender ani konfigurować większości opcji za pomocą funkcji skanowania na żądanie.

Aby uzyskać więcej informacji, zobacz temat [Program antywirusowy Microsoft Defender zgodności z programem Defender for Endpoint](microsoft-defender-antivirus-compatibility.md).
