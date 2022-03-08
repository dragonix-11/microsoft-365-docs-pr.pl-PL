---
title: Nazwy urządzeń
description: Jak Microsoft Managed Desktop nazwami urządzeń
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: fe29027dab3b3395c14729ee7e04cbe7cebf7261
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317167"
---
# <a name="device-names"></a>Nazwy urządzeń

Microsoft Managed Desktop rozwiązania Windows rozwiązania Azure Active Directory, Azure Active Directory i Microsoft Intune.

Aby te usługi bezproblemowo ze sobą współpracowały, urządzenia muszą mieć spójne, standardowe nazwy. Microsoft Managed Desktop przypadku zarejestrowania urządzeń powoduje zastosowanie standardowego formatu nazwy (`MMD-%RAND11`formularza). Windows te nazwy przypisuje funkcja Autopilot. Aby uzyskać więcej informacji na temat rozwiązania Autopilot, zobacz Środowisko pierwszego uruchomienia z programem [Autopilot i strona Stan rejestracji](../get-started/esp-first-run.md).

## <a name="automated-name-changes"></a>Automatyczne zmiany nazw

Jeśli nazwa urządzenia zostanie zmieniona później, Microsoft Managed Desktop zostanie automatycznie zmieniona jego nazwa na nową w formacie standardowym. Ten proces odbywa się co cztery godziny. Zmiana nazwy ma miejsce po następnym ponownym uruchomieniu urządzenia przez użytkownika.

> [!IMPORTANT]
> Jeśli twoje środowisko zależy od określonych nazw urządzeń (na przykład w celu obsługi konkretnej konfiguracji sieci), przed zarejestrowaniem się w programie należy zbadać opcje usunięcia tej zależności Microsoft Managed Desktop.<br><br>Jeśli musisz zachować zależność nazw, możesz przesłać za pośrednictwem portalu administracyjnego żądanie [](../working-with-managed-desktop/admin-support.md) wyłączenia funkcji zmiany nazwy i użycia odpowiedniego formatu nazwy.
