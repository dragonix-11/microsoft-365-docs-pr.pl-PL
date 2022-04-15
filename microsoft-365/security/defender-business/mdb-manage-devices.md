---
title: Zarządzanie urządzeniami w Microsoft Defender dla Firm
description: Dowiedz się, jak zarządzać urządzeniami w Microsoft Defender dla Firm
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
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 453cce2c52902116bc3eaa71f5e6c998ab4164a1
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862835"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Zarządzanie urządzeniami w Microsoft Defender dla Firm

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

W Microsoft Defender dla Firm można zarządzać urządzeniami w następujący sposób:

- [Wyświetl listę dołączonych urządzeń](#view-the-list-of-onboarded-devices) , aby zobaczyć ich poziom ryzyka, poziom narażenia i stan kondycji
- [Podjęcie akcji na urządzeniu z wykrywaniem](#take-action-on-a-device-that-has-threat-detections) zagrożeń
- [Dołączanie urządzenia do usługi Defender dla Firm](#onboard-a-device)  
- [Odłączanie urządzenia od usługi Defender dla Firm](#offboard-a-device)

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="view-the-list-of-onboarded-devices"></a>Wyświetlanie listy dołączonych urządzeń

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Zrzut ekranu przedstawiający spis urządzeń":::

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Spis urządzeń**.

3. Wybierz urządzenie, aby otworzyć jego panel wysuwany, gdzie możesz dowiedzieć się więcej o jego stanie i podjąć działania. 

   Jeśli nie masz jeszcze żadnych urządzeń na liście, [dołącz urządzenia do Microsoft Defender dla Firm](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Podjęcie akcji na urządzeniu z wykrywaniem zagrożeń

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Zrzut ekranu przedstawiający wybrane urządzenie ze szczegółami i dostępnymi akcjami":::

1. W portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w okienku nawigacji wybierz pozycję **Spis urządzeń**. 

2. Wybierz urządzenie, aby otworzyć panel wysuwany, i przejrzyj wyświetlane informacje.

3. Wybierz wielokropek (**...**), aby otworzyć menu akcji. 

4. Wybierz akcję, taką jak **Uruchamianie skanowania antywirusowego** lub **Inicjowanie zautomatyzowanego badania**. 

## <a name="onboard-a-device"></a>Dołączanie urządzenia

Zobacz [Dołączanie urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Odłączanie urządzenia

Zobacz [Odłączanie urządzenia](mdb-offboard-devices.md).

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)
- [Tworzenie lub edytowanie grup urządzeń](mdb-create-edit-device-groups.md)