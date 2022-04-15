---
title: Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich
description: W miarę wykrywania zagrożeń można podjąć działania w celu reagowania na te zagrożenia i ich eliminowania.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 730dc448eb360528a0c45da70f6da6ce32ab5ef4
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862241"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

Portal Microsoft 365 Defender umożliwia zespołowi ds. zabezpieczeń reagowanie na wykryte zagrożenia i ich eliminowanie. W tym artykule przedstawiono przykład korzystania z usługi Defender dla Firm.

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

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