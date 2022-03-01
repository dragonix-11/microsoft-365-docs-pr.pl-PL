---
title: Zarządzanie regułami obsługi punktów końcowych programu Microsoft Defender
description: Może być konieczne uniemożliwienie pojawiania się alertów w portalu przy użyciu reguł obowiązujących w witrynie. Dowiedz się, jak zarządzać regułami swojej reprezentacji w programie Microsoft Defender for Endpoint.
keywords: zarządzanie regułami, regułami, nazwami reguł, zakresem, akcjami, alertami, włączaniem i wyłączaniem
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
ms.technology: mde
ms.openlocfilehash: ee488256363cbb008f670bb8c88d3fb88d7c4090
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998117"
---
# <a name="manage-suppression-rules"></a>Zarządzanie regułami zarządzania regułami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Mogą się okazać sytuacje, w których trzeba pominąć pojawianie się alertów w portalu. Dla określonych alertów, o których wiadomo, że są one niezabłędne, takie jak znane narzędzia lub procesy w organizacji, można utworzyć reguły reguł. Aby uzyskać więcej informacji na temat pomiń alerty, zobacz [Pomijanie alertów](manage-alerts.md).

W jednym miejscu możesz wyświetlić listę wszystkich reguł dotyczących konta i zarządzać nimi. Można również włączyć lub wyłączyć regułę alertów.


1. W okienku nawigacji wybierz **pozycję Ustawienia** \> **punktami końcowymi** \> **Alert** \> **.** Zostanie wyświetlona lista reguł utworzonych przez użytkowników w Twojej organizacji.

2. Wybierz regułę, klikając pole wyboru obok nazwy reguły.

3. Kliknij **pozycję Włącz regułę**, **Edytuj regułę** lub  **Usuń regułę**. W przypadku zmiany reguły można wybrać opcję zwolnienia alertów, które zostały już pominięte, niezależnie od tego, czy alerty te spełniają nowe kryteria. 


## <a name="view-details-of-a-suppression-rule"></a>Wyświetlanie szczegółów reguły reguły

1. W okienku nawigacji wybierz **pozycję Ustawienia** \> **punktami końcowymi** \> **Alert** \> **.** Zostanie wyświetlona lista reguł utworzonych przez użytkowników w Twojej organizacji.

2. Kliknij nazwę reguły. Zostaną wyświetlone szczegóły reguły. Zobaczysz szczegóły reguły, takie jak stan, zakres, akcja, liczba zgodnych alertów, utworzony przez i data utworzenia reguły. Można także wyświetlać skojarzone alerty i warunki reguły.

## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie alertami](manage-alerts.md)
