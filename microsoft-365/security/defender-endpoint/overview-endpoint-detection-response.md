---
title: Omówienie możliwości wykrywanie i reagowanie w punktach końcowych
ms.reviewer: ''
description: Dowiedz się więcej o możliwościach wykrywanie i reagowanie w punktach końcowych w Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: Ochrona punktu końcowego w usłudze Microsoft Defender, wykrywanie i reagowanie w punktach końcowych, reagowanie, wykrywanie, cyberbezpieczeństwo, ochrona
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
ms.openlocfilehash: 78f05c9e366d2f8b4d5b4d7697961f0d702581f8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438533"
---
# <a name="overview-of-endpoint-detection-and-response"></a>Omówienie wykrywanie i reagowanie w punktach końcowych

**Dotyczy:**
- [plany Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](defender-endpoint-plan-1-2.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Funkcje usługi Defender for Endpoint wykrywanie i reagowanie w punktach końcowych zapewniają zaawansowane wykrywanie ataków, które są niemal w czasie rzeczywistym i umożliwiają podjęcie działań. Analitycy zabezpieczeń mogą efektywnie ustalać priorytety alertów, uzyskiwać wgląd w pełny zakres naruszenia i podejmować działania reagowania w celu skorygowania zagrożeń.

Po wykryciu zagrożenia w systemie są tworzone alerty umożliwiające analitykowi badanie. Alerty z tymi samymi technikami ataku lub przypisywane tej samej atakującej są agregowane w jednostkę o nazwie _zdarzenie_. Agregowanie alertów w ten sposób ułatwia analitykom zbiorcze badanie zagrożeń i reagowanie na nie.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4o1j5]

> [!IMPORTANT]
> [Usługa Defender for Endpoint Plan 1](defender-endpoint-plan-1.md) i [Microsoft Defender dla Firm](../defender-business/mdb-overview.md) obejmują tylko następujące ręczne akcje odpowiedzi:
> - Uruchomiono skanowanie antywirusowe
> - Izolowanie urządzenia
> - Zatrzymywanie i kwarantanna pliku
> - Dodawanie wskaźnika w celu zablokowania lub zezwolenia na plik

Zainspirowany nastawieniem "przyjmij naruszenie", usługa Defender for Endpoint stale zbiera behawioralne dane telemetryczne. Obejmuje to informacje o procesach, działania sieciowe, głęboką optykę w jądrze i menedżerze pamięci, działania logowania użytkowników, zmiany rejestru i systemu plików oraz inne. Informacje są przechowywane przez sześć miesięcy, dzięki czemu analityk może cofnąć się w czasie do początku ataku. Analityk może następnie przestawić się w różnych widokach i podejść do badania za pośrednictwem wielu wektorów.

Możliwości reagowania umożliwiają szybkie korygowanie zagrożeń przez działanie na jednostkach, których dotyczy problem.

## <a name="related-topics"></a>Tematy pokrewne

- [Pulpit nawigacyjny operacji zabezpieczeń](security-operations-dashboard.md)
- [Kolejka zdarzeń](view-incidents-queue.md)
- [Kolejka alertów](alerts-queue.md)
- [Lista urządzeń](machines-view-overview.md)
