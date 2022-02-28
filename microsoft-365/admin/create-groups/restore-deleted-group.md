---
title: Przywracanie usuniętej Microsoft 365 grupy
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: Usunięta grupa jest zachowywana przez 30 dni i nadal można ją przywrócić. Po 30 dniach grupa i jej zawartość zostaną trwale usunięte.
ms.openlocfilehash: 926cfa18972a7ca72009258b02b565bd28a183be
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983916"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>Przywracanie usuniętej Microsoft 365 grupy

Usunięte grupy są domyślnie przechowywane przez 30 dni. Ten 30-dniowy okres jest uznawany za "miękkie usunięcie", ponieważ nadal można przywrócić grupę. Po 30 dniach grupa i skojarzona z nią zawartość zostaną trwale usunięte i nie będzie można ich przywrócić.

Przywrócenie grupy powoduje przywrócenie następującej zawartości:
  
- Azure Active Directory (AD) Microsoft 365, właściwości i elementy członkowskie grupy.
    
- Adresy e-mail grupy.
    
- Exchange Online udostępnionej skrzynki odbiorczej i kalendarza.
    
- SharePoint zespołu w trybie online.
    
- Notes programu OneNote
    
- Planner
    
- Teams

- Yammer zawartości grupy i grupy (jeśli grupa Microsoft 365 została utworzona na podstawie Yammer)

- Power BI [klasyczny obszar roboczy](/power-bi/collaborate-share/service-create-workspaces)

> [!NOTE]
> W tym artykule opisano przywracanie tylko Microsoft 365 grup. Wszystkich pozostałych grup nie można przywrócić po usunięciu.

## <a name="restore-a-group"></a>Przywracanie grupy

# <a name="outlook"></a>[Outlook](#tab/outlook)

Jeśli jesteś właścicielem grupy grupy Microsoft 365, możesz ją przywrócić samodzielnie w programie Outlook w sieci Web następujących czynności:

1. Na stronie [Usunięte grupy wybierz](https://outlook.office.com/people/group/deleted) opcję **Zarządzaj grupami** w węźle **Grupy** , a następnie wybierz pozycję **Usunięte**.

2. Kliknij **kartę Przywróć** obok grupy, którą chcesz przywrócić.

Jeśli usunięta grupa nie jest tutaj wyświetlana, skontaktuj się z administratorem.

# <a name="admin-center"></a>[Centrum administracyjne](#tab/admin-center)

Jeśli jesteś administratorem globalnym lub administratorem grup, możesz przywrócić usuniętą grupę w centrum administracyjne platformy Microsoft 365:

1. Przejdź do [centrum administracyjnego](https://admin.microsoft.com).
2. **Rozwiń pozycję Grupy**, a następnie kliknij pozycję **Usunięte grupy**.
3. Zaznacz grupę, którą chcesz przywrócić, a następnie kliknij pozycję **Przywróć grupę**.

> [!NOTE]
> W niektórych przypadkach przywrócenie grupy i wszystkich jej danych może potrwać nawet 24 godziny. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>Masz pytania dotyczące grup Microsoft 365?

Odwiedź [witrynę Microsoft Tech Community](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups), aby publikować pytania i uczestniczyć w konwersacjach dotyczących Microsoft 365 grup. 
  
## <a name="related-content"></a>Zawartość pokrewna

[Zarządzanie Microsoft 365 grup za pomocą programu PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (artykuł)\
[Usuwanie grup za pomocą Remove-UnifiedGroup cmdlet](/powershell/module/exchange/remove-unifiedgroup) (artykuł)\
[Zarządzanie ustawieniami witryny zespołu połączonej z grupą](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) (artykuł)\
[Usuwanie grupy z Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f) (artykuł)
