---
title: Zarządzanie urządzeniami w Microsoft Defender dla Firm
description: Dowiedz się, jak dodawać i usuwać urządzenia oraz zarządzać nimi w usłudze Defender dla firm, ochrona punktów końcowych dla małych i średnich firm.
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
ms.openlocfilehash: 099cddf662b58f918af5aa3b8cc2cb1fea26b0f8
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090019"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Zarządzanie urządzeniami w Microsoft Defender dla Firm

W Microsoft Defender dla Firm można zarządzać urządzeniami w następujący sposób:

- [Wyświetl listę dołączonych urządzeń](#view-the-list-of-onboarded-devices) , aby zobaczyć ich poziom ryzyka, poziom narażenia i stan kondycji
- [Podjęcie akcji na urządzeniu z wykrywaniem](#take-action-on-a-device-that-has-threat-detections) zagrożeń
- [Dołączanie urządzenia do usługi Defender dla Firm](#onboard-a-device)  
- [Odłączanie urządzenia od usługi Defender dla Firm](#offboard-a-device)


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