---
title: Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm
description: Po wykryciu zagrożeń możesz podjąć działania, aby zareagować na te zagrożenia i je zminimalizować.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 50a759c4f84aee72b376ff9126c54d381f4a373f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327787"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Od 1 marca 2022 r. usługa Microsoft Defender dla firm jest wprowadzana u klientów usługi Microsoft 365 Business Premium. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Portal usługi Microsoft 365 Defender umożliwia Twojemu zespołowi zabezpieczeń reagowanie na wykryte zagrożenia i ich ograniczanie. W tym artykule opisano przykłady korzystania z usługi Defender dla firm.

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="view-detected-threats"></a>Wyświetlanie wykrytych zagrożeń

1. Przejdź do portalu usługi Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Karty z powiadomieniami na stronie głównej. Karty informują o tym, ile zagrożeń zostało wykrytych wraz z tym, ile kont użytkowników, punktów końcowych (urządzeń) i innych zasobów wpłynęło na nie. Na poniższej ilustracji przedstawiono przykładowe karty:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Zrzut ekranu przedstawiający karty w portalu usługi Microsoft 365 Defender":::

3. Wybierz przycisk lub link na karcie, aby wyświetlić więcej informacji i podjąć działanie. Na przykład karta Ryzyko w **urządzeniach** zawiera przycisk **Wyświetl szczegóły** . Wybranie tego przycisku powoduje przysłanie na stronę **spisu** urządzeń, jak pokazano na poniższej ilustracji:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Zrzut ekranu przedstawiający spis urządzeń":::

   Na **stronie Spis urządzeń** jest wymieniona urządzenia organizacji wraz z ich poziomem ryzyka i poziomem ekspozycji.

4. Wybierz element, na przykład urządzenie. Zostanie otwarte okienko wysuwu z większej liczby alertów i zdarzeń wygenerowanych dla tego elementu, jak pokazano na poniższej ilustracji:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Zrzut ekranu przedstawiający okienko wysuwu dla wybranego urządzenia":::

5. Wyświetlanie wyświetlanych informacji w wysuwanych informacjach. Wybierz wielokropek (...), aby otworzyć menu z listą dostępnych akcji, jak pokazano na poniższej ilustracji: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Zrzut ekranu przedstawiający dostępne akcje dla wybranego urządzenia":::

6. Wybierz dostępną akcję. Możesz na przykład wybrać pozycję **Uruchom skanowanie antywirusowe**, co spowoduje, że program antywirusowy Microsoft Defender rozpocznie szybkie skanowanie na urządzeniu. Możesz też wybrać pozycję **Zainicjuj automatyczne badanie** , aby uruchomić automatyczne badanie na urządzeniu.

## <a name="next-steps"></a>Następne kroki

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)