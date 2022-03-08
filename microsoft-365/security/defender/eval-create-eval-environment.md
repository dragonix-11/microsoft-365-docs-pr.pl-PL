---
title: Krok nr 1. Tworzenie środowiska Microsoft 365 Defender oceny
description: Skonfiguruj laboratorium Microsoft 365 Defender lub środowisko pilotażowe, aktywując licencje wersji próbnej. Następnie skonfiguruj usługę Microsoft Defender for Identity (MDI) i wszystkie inne oceny M365D.
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
ms.openlocfilehash: 17751cf5f71d9754ad8d5c0c913ee3438b49b399
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311623"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment"></a>Krok nr 1. Tworzenie środowiska Microsoft 365 Defender oceny

Istnieją dwa typowe sposoby następnego kroku oceny. Ten dokument zakłada, że masz już dzierżawę produkcyjną Microsoft 365 i aktywuje licencje wersji próbnej E5, aby ocenić Microsoft 365 Defender *w bieżącym środowisku*. Ocena w miejscu pozwoli zachować wszystkie metody zabezpieczeń przy zakupie licencji po okresie oceny.

Drugie to konfigurowanie [środowiska laboratorium Microsoft 365 Defender na](setup-m365deval.md) potrzeby oceny. Pamiętaj, że może ona nie mieć wielu rzeczywistych sygnałów od firmy.

## <a name="to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Aby aktywować licencje wersji próbnej E5 w celu oceny Microsoft 365 Defender 

1. Zaloguj się do istniejącego Microsoft 365 administracyjnego dzierżawy.
2. Wybierz **pozycję Zakup usług** z menu nawigacji.
3. Przewiń w dół do Office 365 sekcji i wybierz **przycisk Szczegóły** w obszarze Office 365 E5 licencji.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Sekcja Office 365 ma przycisk Szczegóły do kliknięcia.":::

4. Wybierz **pozycję Rozpocznij bezpłatny link do wersji próbnej** .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Kliknij pozycję Rozpocznij bezpłatny okres próbny (opłata wynosi 35 USD).":::

5. Potwierdź swoją prośbę i kliknij **przycisk Wypróbuj** teraz.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Na panelu &quot;Sprawdź, potwierdź swoje zamówienie&quot; znajduje się przycisk &quot;Wypróbuj teraz&quot; (w przypadku miesięcznej wersji Office 365 E5 próbnej dla 25 użytkowników).":::

## <a name="next-steps"></a>Następne kroki

[Włączanie Microsoft 365 tożsamości](eval-defender-identity-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)