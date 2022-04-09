---
title: Rozwiązywanie problemów z usługą Microsoft 365 Defender
description: Znajdowanie rozwiązań i obejść znanych problemów z Microsoft 365 Defender
keywords: rozwiązywanie problemów z Microsoft 365 Defender, rozwiązywanie problemów, Microsoft Defender for Identity, problemy, dodatek, strona ustawień
search.product: eADQiWindows 10XVcnh
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 656599cf9ec66987119819b2f28f9a8eff1d4e77
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731675"
---
# <a name="troubleshoot-microsoft-365-defender-service-issues"></a>Rozwiązywanie problemów z usługą Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

W tej sekcji rozwiązano problemy, które mogą wystąpić podczas korzystania z usługi Microsoft 365 Defender.

## <a name="i-dont-see-microsoft-365-defender-content"></a>Nie widzę zawartości Microsoft 365 Defender

Jeśli nie widzisz możliwości w okienku nawigacji, takich jak Zdarzenia, Centrum akcji lub Wyszukiwanie zagrożeń w portalu, musisz sprawdzić, czy dzierżawa ma odpowiednie licencje.

Aby uzyskać więcej informacji, zobacz [Wymagania wstępne](prerequisites.md).

## <a name="microsoft-defender-for-identity-alerts-are-not-showing-up-in-the-microsoft-365-defender-incidents"></a>Microsoft Defender for Identity alerty nie są wyświetlane w zdarzeniach Microsoft 365 Defender

Jeśli masz Microsoft Defender for Identity wdrożone w środowisku, ale nie widzisz alertów usługi Defender for Identity w ramach zdarzeń Microsoft 365 Defender, musisz upewnić się, że Microsoft Defender for Cloud Apps  i integracja usługi Defender for Identity jest włączona.

Aby uzyskać więcej informacji, zobacz [integrację Microsoft Defender for Identity](/cloud-app-security/mdi-integration).

## <a name="where-is-the-settings-page-for-turning-on-the-service"></a>Gdzie znajduje się strona ustawień włączania usługi?

Aby włączyć Microsoft 365 Defender, uzyskaj dostęp do **Ustawienia** z okienka nawigacji w portalu Microsoft 365 Defender. Ten element nawigacji jest widoczny tylko wtedy, gdy masz [uprawnienia i licencje wymagań wstępnych](m365d-enable.md#check-license-eligibility-and-required-permissions).

## <a name="how-do-i-create-an-exception-for-my-fileurl"></a>Jak mogę utworzyć wyjątek dla mojego pliku/adresu URL?

Wynik fałszywie dodatni to plik lub adres URL, który jest wykrywany jako złośliwy, ale nie stanowi zagrożenia. Możesz tworzyć wskaźniki i definiować wykluczenia, aby odblokować i zezwolić na niektóre pliki/adresy URL. Zobacz [Address false positives/negatives in Defender for Endpoint (Adresowanie wyników fałszywie dodatnich/ujemnych w usłudze Defender for Endpoint](/microsoft-365/security/defender-endpoint/defender-endpoint-false-positives-negatives)).
