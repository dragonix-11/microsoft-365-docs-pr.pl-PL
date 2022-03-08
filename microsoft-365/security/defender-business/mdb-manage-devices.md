---
title: Zarządzanie urządzeniami w programie Microsoft Defender dla firm
description: Dowiedz się, jak zarządzać urządzeniami w programie Microsoft Defender dla firm
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
ms.openlocfilehash: e0c564fda55393d9f60bd79081a309bde1e87f02
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329351"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Zarządzanie urządzeniami w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W programie Microsoft Defender dla Firm możesz zarządzać urządzeniami w następujący sposób:

- [Wyświetl listę urządzeń na urządzeniach, aby](#view-the-list-of-onboarded-devices) zobaczyć ich poziom ryzyka, poziom ekspozycji i stan zdrowia

- [Podjąć działania na urządzeniu, które](#take-action-on-a-device-that-has-threat-detections) wykrywa zagrożenia

- [Dołączanie urządzenia do usługi Defender dla firm](#onboard-a-device)  

- [Wyłączanie urządzenia z usługi Defender dla firm](#offboard-a-device)

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="view-the-list-of-onboarded-devices"></a>Wyświetlanie listy urządzeń podłączonych do urządzenia

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Zrzut ekranu przedstawiający spis urządzeń":::

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Spis urządzeń**.

3. Wybierz urządzenie, aby otworzyć jego panel wysuwu, w którym możesz dowiedzieć się więcej o jego stanie i podjąć działanie. 

   Jeśli nie masz jeszcze żadnych urządzeń na liście, na urządzeniach w [programie Microsoft Defender dla Firm](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Podjąć działania na urządzeniu, które wykrywa zagrożenia

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Zrzut ekranu przedstawiający wybrane urządzenie z dostępnymi szczegółami i akcjami":::

1. W portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w okienku nawigacji wybierz pozycję **Spis urządzeń**. 

2. Wybierz urządzenie, aby otworzyć jego panel wysuwu i przejrzeć wyświetlane informacje.

3. Wybierz wielokropek (**...**), aby otworzyć menu akcje. 

4. Wybierz akcję, na przykład Uruchom **skanowanie antywirusowe lub** **Inicjuj automatyczne badanie**. 

## <a name="onboard-a-device"></a>Wniesienie urządzenia

Zobacz [: Na urządzeniach w programie Microsoft Defender dla firm](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Odłożanie urządzenia

Zobacz [Wyniesanie urządzenia](mdb-onboard-devices.md#offboarding-a-device).

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)

- [Tworzenie lub edytowanie grup urządzeń](mdb-create-edit-device-groups.md)