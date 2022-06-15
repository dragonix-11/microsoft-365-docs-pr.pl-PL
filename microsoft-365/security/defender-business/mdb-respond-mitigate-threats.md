---
title: Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich
description: W miarę wykrywania zagrożeń w usłudze Defender dla Firm możesz podjąć działania w celu reagowania na te zagrożenia. Zobacz, jak używać widoku spisu urządzeń.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b7a911991935407f9d512213c9d76c92106b74c8
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089567"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich

Portal Microsoft 365 Defender umożliwia zespołowi ds. zabezpieczeń reagowanie na wykryte zagrożenia i ich eliminowanie. W tym artykule przedstawiono przykład korzystania z usługi Defender dla Firm.


## <a name="view-detected-threats"></a>Wyświetlanie wykrytych zagrożeń

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Karty powiadomień na stronie głównej. Karty informują o liczbie wykrytych zagrożeń wraz z liczbą kont użytkowników, punktów końcowych (urządzeń) i innych zasobów. Poniższy obraz jest przykładem kart, które mogą być widoczne:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Zrzut ekranu przedstawiający karty w portalu Microsoft 365 Defender":::

3. Wybierz przycisk lub link na karcie, aby wyświetlić więcej informacji i podjąć działania. Na przykład nasza karta **Urządzenia zagrożone** zawiera przycisk **Wyświetl szczegóły** . Wybranie tego przycisku spowoduje przejście na stronę **Spis urządzeń** , jak pokazano na poniższej ilustracji:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Zrzut ekranu przedstawiający spis urządzeń":::

   Na stronie **Spis urządzeń** wymieniono urządzenia firmowe wraz z poziomem ryzyka i poziomem narażenia.

4. Wybierz element, taki jak urządzenie. Zostanie otwarte okienko wysuwane i zostanie wyświetlone więcej informacji o alertach i zdarzeniach wygenerowanych dla tego elementu, jak pokazano na poniższej ilustracji:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Zrzut ekranu przedstawiający okienko wysuwane dla wybranego urządzenia":::

5. Na wysuwu wyświetl wyświetlane informacje. Wybierz wielokropek (...), aby otworzyć menu z listą dostępnych akcji, jak pokazano na poniższej ilustracji: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Zrzut ekranu przedstawiający dostępne akcje dla wybranego urządzenia":::

6. Wybierz dostępną akcję. Możesz na przykład wybrać pozycję **Uruchom skanowanie antywirusowe**, co spowoduje, że Program antywirusowy Microsoft Defender rozpocznie szybkie skanowanie na urządzeniu. Możesz też wybrać pozycję **Inicjuj automatyczne badanie** , aby wyzwolić automatyczne badanie na urządzeniu.

## <a name="next-steps"></a>Następne kroki

- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)
- [Zarządzanie urządzeniami w Microsoft Defender dla Firm](mdb-manage-devices.md)
- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
