---
title: Wdrażanie ustawień konfigurowalnych w programie Microsoft Managed Desktop
description: Wdrażaj i śledź zmiany ustawień konfigurowalnych w programie Microsoft Managed Desktop.
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja, wdrażanie, wdrażanie etapowe, konfigurowanie ustawień
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a52995ff9ab2f946ca11417d4ed7bfa13825353f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326785"
---
# <a name="deploy-and-track-configurable-settings---microsoft-managed-desktop"></a>Wdrażanie i śledzenie ustawień konfigurowalnych — Microsoft Managed Desktop

Po wymuszeniu zmian w kategoriach ustawień i rozmieszczeniu wdrożenia na stronie Stan wdrożenia możesz rozpocząć wdrażanie ustawień w grupach. Na tej stronie przedstawiono podsumowanie poszczególnych ustawień, które można skonfigurować. Podczas otwierania kategorii ustawień możesz wdrożyć ustawienia w grupach i śledzić postęp tych wdrożeń.

## <a name="deployment-statuses"></a>Stan wdrożenia

Poniżej przedstawiono stan poszczególnych wdrożeń.

Stan | Objaśnienie
--- | ---
Wdrażanie | Zmiana oczekuje na wdrożenie w tej grupie.
W toku | Zmiana zostanie zastosowana do aktywnych urządzeń w tej grupie.
Ukończ | Zmiana została wyliczana na wszystkich aktywnych urządzeniach w tej grupie.
Zakończone niepowodzeniem | Zmiana nie powiodła się na 10 procent aktywnych urządzeniach w grupie. Wdrażanie zostało zatrzymane.<br><br> Automatycznie zostanie otwarty wniosek o pomoc techniczną z Microsoft Managed Desktop rozwiązywania problemów z wdrożeniem.
Przywrócono | Zmiana została przywrócona do ostatniej zmiany, która została pomyślnie wdrożona we wszystkich grupach wdrożenia.

## <a name="deploy-changes"></a>Wdrażanie zmian

Jako przykładu użyjemy obrazu tła pulpitu w tych instrukcjach. Po etapowym wdrożeniu zmiany są wdrażane na stronie Stan wdrożenia.

**Aby wdrożyć zmiany:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Ustawienia**.
3. W obszarze **roboczym Stan** wdrożenia wybierz ustawienie, które chcesz wdrożyć. Następnie wybierz wdrożenie etapowe, które chcesz wdrożyć.
4. Wybierz **pozycję** Wdeksuj, aby wdrożyć zmianę w jednej z grup wdrażania.

> [!NOTE]
> Pomarańczowa ikona przestrogi wskazuje, że do wdrożenia jest dostępna wcześniejsza grupa, ponieważ zaleca się wdrożenie w tej kolejności.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Trusted sites pane on the right. In the Deployment groups section are three columns: deployment groups, devices, and status. In the status column, "deploy" is highlighted.](../../media/1deployedit.png) -->

Zalecamy wdrożenie grup wdrożeniowych w tej kolejności: Test, Pierwsze, Szybkie, a następnie Ogólne.

Gdy w każdej grupie zostaną wprowadzone zmiany, stan zmieni się na **Ukończone**.

<!-- Needs picture updated to show MEM ![Deployment status workspace with columns for date updated, version, test, first, fast, and broad. The Proxy row is expanded, showing a dated setting flagged as "complete" in each of the four deployment groups.](../../media/2completeedit.png) -->

## <a name="revert-deployment"></a>Przywróć wdrożenie

Po wdrożeniu zmiany możesz przywrócić stan **wdrożenia**. Gdy przywrócisz zmianę w toku lub  **Ukończono**, bieżące wdrożenie zostanie zatrzymane. Ustawienie zostanie przywrócone do ostatniej wersji, która została wdrożona we wszystkich grupach.

Jako przykład przywrócimy obraz tła pulpitu.

**Aby przywrócić zmianę:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Ustawienia**.
3. W obszarze **roboczym Stan wdrożenia** wybierz ustawienie, które chcesz przywrócić. Następnie wybierz wdrożenie etapowe, które chcesz przywrócić.
4. W **obszarze Czy chcesz przywrócić tę zmianę?** wybierz pozycję **Przywróć wdrożenie**.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Browser start pages is selected, opening a pane on the right side with data about the submitted change and its status. At the bottom is the "need to revert this change" area where you can select "Revert deployment."](../../media/3revert.png) -->

## <a name="additional-resources"></a>Dodatkowe materiały

- [Omówienie ustawień konfigurowalnych](config-setting-overview.md)
- [Informacje dotyczące ustawień konfigurowalnych](config-setting-ref.md)
