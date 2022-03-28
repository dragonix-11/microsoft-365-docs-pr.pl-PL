---
title: Tworzenie środowiska Microsoft 365 Defender oceny w celu zwiększenia bezpieczeństwa cyberzabłędu i XDR
description: Dowiedz się, co zawiera kod XDR pakietu Microsoft 365 Defender, który ocenisz, i aktywuj środowisko Microsoft 365 Defender próbnego lub pilotażowego, aktywując licencje wersji próbnej. Rozpocznij tutaj podróż z cyberzabłędem w kodach XDR i dowiedz się, jak rozpocząć ten test do produkcji.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/19/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 5b684a1ead5638a787413d7470cb103cbe55e7df
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775527"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>Krok nr 1. Tworzenie środowiska oceny Microsoft 365 Defender w celu większej ochrony przed cyberzabłędem

Możesz dowiedzieć się więcej na temat tego Microsoft Defender XDR i utworzyć je w krokach, które są rozłożone w pozostałej części tej serii:

- [Jak utworzyć środowisko](eval-create-eval-environment.md)
- Konfigurowanie i poznanie poszczególnych technologii tego xdr firmy Microsoft
    - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
    - [Program Microsoft Defender dla Office](eval-defender-office-365-overview.md)
    - [Ochrona punktu końcowego w usłudze Microsoft Defender](eval-defender-endpoint-overview.md)
    - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Jak zbadać i odpowiedzieć przy użyciu tego xdr](eval-defender-investigate-respond.md)
- [Promowanie środowiska próbnego do produkcji](eval-defender-promote-to-production.md)
- [Powrót do przeglądu](eval-overview.md)

Kroki w tej serii są uruchamiane od końca, od nauki pojęć związanych z Microsoft 365 Defender XDR do tworzenia tego środowiska oceny i tworzenia środowiska oceny na żywo.

Istnieją dwa typowe sposoby następnego kroku oceny. W tej serii przyjęto założenie, że masz już dzierżawę produkcyjną Microsoft 365 i aktywujesz licencje wersji próbnej E5, aby ocenić Microsoft 365 Defender *w bieżącym środowisku*. Ocena w miejscu pozwoli zachować wszystkie metody zabezpieczeń przy zakupie licencji po okresie oceny.

Drugie to konfigurowanie [środowiska laboratorium Microsoft 365 Defender na](setup-m365deval.md) potrzeby oceny. Pamiętaj, że podczas testowania może nie mieć wielu rzeczywistych sygnałów od firmy.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Konieczne będzie aktywowanie licencji wersji próbnej E5, aby ocenić Microsoft 365 Defender

1. Zaloguj się do istniejącego Microsoft 365 administracyjnego dzierżawy.
2. Wybierz **pozycję Zakup usług** z menu nawigacji.
3. Przewiń w dół do Office 365 sekcji i wybierz **przycisk Szczegóły** w obszarze Office 365 E5 licencji.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="The Details button in the Microsoft 365 Defender portal" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

4. Wybierz **pozycję Rozpocznij bezpłatny link do wersji próbnej** .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Przycisk Rozpocznij bezpłatną wersję próbną w Microsoft 365 Defender wersji próbnej" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

5. Potwierdź swoją prośbę i kliknij **przycisk Wypróbuj** teraz.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Przycisk Wypróbuj teraz w Microsoft 365 Defender portalu" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="go-to-the-next-step"></a>Przejdź do następnego kroku

[Dowiedz się, jak włączyć Microsoft 365 tożsamości](eval-defender-identity-overview.md)

Lub wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
