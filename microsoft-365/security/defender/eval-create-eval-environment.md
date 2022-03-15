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
ms.openlocfilehash: d81d33a01802ebdf8ef0ea67a9ee74fc69b79384
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504741"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>Krok nr 1. Tworzenie środowiska oceny Microsoft 365 Defender w celu większej ochrony przed cyberzabłędem

LMożesz dowiedzieć się więcej na temat tego Microsoft Defender XDR i utworzyć je w krokach rozmieszczonych w pozostałej części tej serii:

- [Jak utworzyć środowisko](eval-create-eval-environment.md)
- Konfigurowanie i poznanie poszczególnych technologii tego xdr firmy Microsoft
    - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
    - [Program Microsoft Defender dla Office](eval-defender-office-365-overview.md)
    - [Ochrona punktu końcowego w usłudze Microsoft Defender](eval-defender-endpoint-overview.md)
    - [Usługa Microsoft Defender dla aplikacji w chmurze](eval-defender-mcas-overview.md)
- [Jak zbadać i odpowiedzieć przy użyciu tego xdr](eval-defender-investigate-respond.md)
- [Promowanie środowiska próbnego do produkcji](eval-defender-promote-to-production.md)
- [Powrót do przeglądu](eval-overview.md)

Kroki w tej serii są uruchamiane od końca, od nauki pojęć związanych z Microsoft 365 Defender XDR do tworzenia tego środowiska oceny i tworzenia środowiska oceny na żywo.

Istnieją dwa typowe sposoby następnego kroku oceny. W tej serii założono, że masz już dzierżawę produkcyjną Microsoft 365 i aktywujesz licencje wersji próbnej E5, aby ocenić Microsoft 365 Defender *w bieżącym środowisku*. Ocena w miejscu pozwoli zachować wszystkie metody zabezpieczeń przy zakupie licencji po okresie oceny.

Drugie to konfigurowanie [środowiska laboratorium Microsoft 365 Defender na](setup-m365deval.md) potrzeby oceny. Pamiętaj, że podczas testowania może nie mieć wielu rzeczywistych sygnałów od firmy.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Konieczne będzie aktywowanie licencji wersji próbnej E5, aby ocenić Microsoft 365 Defender

1. Zaloguj się do istniejącego Microsoft 365 administracyjnego dzierżawy.
2. Wybierz **pozycję Zakup usług** z menu nawigacji.
3. Przewiń w dół do Office 365 sekcji i wybierz **przycisk Szczegóły** w obszarze Office 365 E5 licencji.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Sekcja Office 365 ma przycisk Szczegóły do kliknięcia.":::

4. Wybierz **pozycję Rozpocznij bezpłatny link do wersji próbnej** .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Kliknij pozycję Rozpocznij bezpłatny okres próbny (opłata wynosi 35 USD).":::

5. Potwierdź swoją prośbę i kliknij **przycisk Wypróbuj** teraz.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Na panelu &quot;Sprawdź, potwierdź swoje zamówienie&quot; znajduje się przycisk &quot;Wypróbuj teraz&quot; (w przypadku miesięcznej wersji Office 365 E5 próbnej dla 25 użytkowników).":::

## <a name="go-to-the-next-step"></a>Przejdź do następnego kroku

[Dowiedz się, jak włączyć Microsoft 365 tożsamości](eval-defender-identity-overview.md)

Lub wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)