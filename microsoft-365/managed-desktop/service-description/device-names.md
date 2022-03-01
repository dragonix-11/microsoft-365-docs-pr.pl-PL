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
ms.openlocfilehash: 2ba44974fa2181ccf0b1d4ef0a5705d630aff0d3
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2022
ms.locfileid: "63015749"
---
# <a name="device-names"></a>Nazwy urządzeń

Microsoft Managed Desktop rozwiązania Windows rozwiązania Azure Active Directory, Azure Active Directory i Microsoft Intune. Aby te usługi bezproblemowo ze sobą współpracowały, urządzenia muszą mieć spójne, standardowe nazwy. Microsoft Managed Desktop przypadku zarejestrowania urządzeń stosuje standardowy format nazwy (z formularza *MMD-%RAND11*). Windows te nazwy przypisuje funkcja Autopilot. Aby uzyskać więcej informacji na temat rozwiązania Autopilot, zobacz Środowisko pierwszego uruchomienia z programem [Autopilot i strona Stan rejestracji](../get-started/esp-first-run.md).

## <a name="automated-name-changes"></a>Automatyczne zmiany nazw

Jeśli nazwa urządzenia zostanie zmieniona później, Microsoft Managed Desktop automatycznie zmieni jego nazwę na nową w formacie standardowym. Ten proces odbywa się co cztery godziny. Zmiana nazwy ma miejsce po następnym ponownym uruchomieniu urządzenia przez użytkownika.

> [!IMPORTANT]
> Jeśli twoje środowisko zależy od określonych nazw urządzeń (na przykład w celu obsługi konkretnej konfiguracji sieci), przed zarejestrowaniem się w programie należy zbadać opcje usunięcia tej zależności Microsoft Managed Desktop. Jeśli musisz zachować zależność nazw, możesz przesłać za pośrednictwem portalu administracyjnego żądanie [](../working-with-managed-desktop/admin-support.md) wyłączenia funkcji zmiany nazwy i użycia odpowiedniego formatu nazwy.