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
ms.openlocfilehash: 624bde84da9a0c35f5814e3b6c67c2d190683fc6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330303"
---
# <a name="device-deployment-groups"></a>Grupy wdrażania urządzeń

Microsoft Managed Desktop grupy wdrażania do zarządzania wydaniami aktualizacji i zmian w konfiguracji na urządzeniach. Urządzenia są automatycznie dodawane do grup wdrażania ("pierścienie" lub "grupy aktualizacji") podczas ich zarejestrowania w Microsoft Managed Desktop. Grupy wdrażania umożliwiają urządzeniam otrzymywanie zmian na osi czasu etapowej.

Być może chcesz przypisać określone urządzenia tylko do celów testowych lub wyznaczyć konkretnych wczesnych użytkowników, którzy będą otrzymywać zmiany w pierwszej kolejności. W przypadku urządzeń krytycznych, takich jak urządzenia używane przez kadrę kierowniczej lub funkcje o krytycznym znaczeniu dla firmy, warto utrzymać je w grupie, która będzie pobierać aktualizacje najwolniej. Microsoft Managed Desktop umożliwia określenie, że urządzenie ma pozostać w jednej z następujących grup.

| Grupa | Opis |
| ----- | ----- |
| Test | Grupa Test jest najlepsza dla urządzeń używanych do testów lub użytkowników, którzy mogą często chcieć wprowadzać częste zmiany, korzystać z nowych funkcji i mogą wcześnie dostarczać opinie.<br><br>Ta grupa często otrzymuje zmiany, a jej środowisko ma duży wpływ na jej działanie. Grupa testowa jest wykluczona ze wszystkich ustalonych umów dotyczących poziomu usług i obsługi użytkowników. Najlepiej jest najpierw przenieść tylko kilka urządzeń, a następnie sprawdzić środowisko użytkownika. Microsoft Managed Desktop nie przypisze automatycznie urządzeń do tej grupy. Ta grupa będzie zawierać tylko urządzenia określone przez Ciebie.
| Pierwszy | Grupa Pierwszy jest idealnym rozwiązaniem dla wczesnych użytkowników, ochotników, wyznaczonych specjalistów DS, informatyków lub przedstawicieli funkcji biznesowych. Oznacza to, że osoby, które mogą weryfikować zmiany i udzielać opinii na temat tego doświadczenia.
| Szybkie | Grupa Szybkie działania doskonale nadaje się dla przedstawicieli funkcji biznesowych. Te osoby mogą sprawdzać poprawność zmian przed szerokiego wdrożenia.
| Broad | W ostatniej grupie Ogólne są odbierane zmiany.<br><br>Większość organizacji zazwyczaj znajduje się w tej grupie. Możesz określić urządzenia, które muszą znajdować się w tej grupie. Te urządzenia powinny w ostatnim ciągu otrzymywać zmiany, ponieważ pełnią krytyczne funkcje biznesowe lub należą do użytkowników o krytycznych rolach.
| Automatyczne | Wybierz pozycję Automatycznie, jeśli Microsoft Managed Desktop automatycznie przypisać urządzenia do jednej z innych grup.<br><br>Nie będziemy automatycznie przypisywać urządzeń do testowania. Jeśli chcesz zwolnić urządzenie określone wcześniej i przypisać je ponownie automatycznie, wybierz tę opcję.

Aby uzyskać więcej informacji o tym, Windows zarządza się w grupach, zobacz Jak są [obsługiwane aktualizacje w Microsoft Managed Desktop](updates.md).

## <a name="labels"></a>Etykiety

Kolumna Grupa przypisana przez zawiera następujące etykiety:

| Etykieta | Opis |
| ----- | ----- |
| Administrator | Urządzenie należy do określonej grupy. |
| Automatycznie | Microsoft Managed Desktop przypisano grupę. |
| Oczekiwanie | Urządzenie jest w trakcie przechodzenia do grupy. |

Kolumna **Grupa** zawsze pokazuje grupę, w których obecnie się znajduje urządzenie, i jest aktualizowana tylko po zakończeniu przenoszenia.

> [!IMPORTANT]
> Nie próbuj bezpośrednio modyfikować członkostwa w tych grupach. Zawsze postępuj zgodnie z instrukcjami [opisanymi w tece Przypisywanie urządzeń do grupy wdrażania](../working-with-managed-desktop/assign-deployment-group.md).
