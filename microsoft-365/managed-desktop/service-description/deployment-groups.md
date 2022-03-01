---
title: Grupy wdrażania urządzeń
description: Grupy wdrażania używane do zarządzania aktualizacjami i innymi zmianami
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 59f5cd1606c6d0b48bfbc22513790a185dd5f1b1
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009704"
---
# <a name="device-deployment-groups"></a>Grupy wdrażania urządzeń

Microsoft Managed Desktop grupy wdrażania do zarządzania wydaniami aktualizacji i zmian w konfiguracji na urządzeniach. Urządzenia są automatycznie dodawane do grup wdrażania ("pierścienie" lub "grupy aktualizacji") podczas ich zarejestrowania w Microsoft Managed Desktop. Grupy wdrażania umożliwiają urządzeniam otrzymywanie zmian na osi czasu etapowej.

Być może chcesz przypisać określone urządzenia tylko do celów testowych lub wyznaczyć konkretnych wczesnych użytkowników, którzy będą otrzymywać zmiany w pierwszej kolejności. Jeśli masz krytyczne urządzenia, takie jak urządzenia używane przez kadrę kierowniczej lub służące do kluczowych funkcji biznesowych, warto utrzymać je w grupie, która będzie pobierać aktualizacje najwolniejszego tempa. Microsoft Managed Desktop umożliwia określenie, że urządzenie ma pozostać w jednej z następujących grup.

- **Test**: najlepsza w przypadku urządzeń używanych do testowania lub użytkowników, którzy mogą często korzystać z nowych funkcji i dostęp do nowych funkcji, a także na ich wczesne opinie. Ta grupa często otrzymuje zmiany, a jej środowisko ma duży wpływ na jej działanie. Grupa testowa jest wykluczona ze wszystkich ustalonych umów dotyczących poziomu usług i obsługi użytkowników. Najlepiej jest najpierw przenieść tylko kilka urządzeń, a następnie sprawdzić środowisko użytkownika. Microsoft Managed Desktop do tej grupy nie będą automatycznie przypisywane urządzenia; będą do niego trafiać tylko te urządzenia, które określisz.
- **Po** pierwsze: idealne rozwiązanie dla wczesnych użytkowników, ochotników lub wyznaczonych specjalistów IT lub przedstawicieli funkcji biznesowych, czyli osób, które mogą weryfikować zmiany i rezygnować z tych funkcji.
- **Szybkie** zmiany: idealne dla przedstawicieli funkcji biznesowych, osób, które mogą weryfikować zmiany przed szerokiego wdrożenia.
- **Szerokie** grono osób otrzymuje zmiany na końcu. Większość organizacji zazwyczaj znajduje się w tej grupie. Możesz także określić urządzenia, które muszą należeć do tej grupy, i powinny otrzymywać zmiany tylko na końcu, ponieważ pełnią one krytyczne funkcje biznesowe lub należą do użytkowników w krytycznych rolach. 
- **Automatyczne**: zaznacz tę opcję, jeśli chcesz, Microsoft Managed Desktop automatycznie przypisywać urządzenia do jednej z innych grup. (Nie będziemy automatycznie przypisywać urządzeń do testowania). Jeśli chcesz zwolnić urządzenie określone wcześniej i przypisać je ponownie automatycznie, wybierz tę opcję. 

Aby uzyskać więcej informacji o tym, Windows zarządza się w grupach, zobacz Jak są [obsługiwane aktualizacje w Microsoft Managed Desktop](updates.md).

Jeśli urządzenie znajduje się w określonej przez Ciebie grupie, będzie to temat Grupa **przypisana przez**: **Administrator**. Jeśli Microsoft Managed Desktop przypisano grupę, będzie to przycisk **Automatycznie**. Gdy urządzenie jest w trakcie przechodzenia do grupy, będzie ono mieć grupę **Oczekiwanie**. Pole **Grupa** zawsze pokazuje grupę, w których obecnie się znajduje urządzenie, i jest aktualizowana tylko po zakończeniu przenoszenia.

> [!IMPORTANT]
> Nie próbuj bezpośrednio modyfikować członkostwa w tych grupach. Zawsze postępuj zgodnie z instrukcjami [opisanymi w tece Przypisywanie urządzeń do grupy wdrażania](../working-with-managed-desktop/assign-deployment-group.md).
