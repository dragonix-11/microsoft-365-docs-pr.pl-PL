---
title: Przypisywanie urządzeń do grupy wdrażania
description: Jak określić grupę wdrożenia, w której mają się znaleźć urządzenia
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 6f3d2c79c23a37e1e1a965f9a3f416052a49fa76
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2022
ms.locfileid: "63009731"
---
# <a name="assign-devices-to-a-deployment-group"></a>Przypisywanie urządzeń do grupy wdrażania

Microsoft Managed Desktop urządzenia do różnych grup wdrożeniowych. Za pomocą portalu administracyjnego możesz określić lub zmienić grupę, do których przypisano urządzenie. Zadanie można zmienić po zarejestrowaniu urządzenia lub zarejestrowaniu użytkownika.

> [!IMPORTANT]
> Jeśli zmienisz zadanie, zasady specyficzne dla tej grupy zostaną zastosowane do urządzenia. Zmiana może spowodować zainstalowanie najnowszej wersji pakietu Windows 10 (w tym wszelkich nowych funkcji i aktualizacji jakości). Najlepiej jest najpierw przenieść tylko kilka urządzeń, a następnie sprawdzić wynikowe środowisko użytkownika. Niektóre aktualizacje spowoduje ponowne uruchomienie urządzenia. Upewnij się, że wybrano odpowiednie urządzenia do przypisania. Może upłynieć do 24 godzin, aż zadanie stanie się skuteczne.

**Aby przypisać urządzenia do grupy wdrożenia:**

Jeśli chcesz przenieść oddzielne urządzenia do różnych grup, powtórz te kroki dla każdej grupy.

1. W Microsoft Endpoint Manager wybierz **pozycję Urządzenia** w okienku po lewej stronie.
1. W sekcji **Microsoft Managed Desktop** wybierz pozycję **Urządzenia**.
1. Wybierz urządzenia, które chcesz przypisać. Wszystkie wybrane urządzenia zostaną przypisane do  specify przez Ciebie grupy.
1. Z menu **wybierz** pozycję Akcje urządzenia.
1. Wybierz **pozycję Przypisz urządzenie do grupy**. Zostanie otwarta ulotka.
1. Z menu rozwijanego wybierz grupę, do która ma być przesunana urządzenia, a następnie wybierz pozycję **Zapisz**. Grupa **przypisana według kolumny** zmieni się na **Oczekujące**.

Po ukończeniu zadania pole Grupa  przypisana według kolumny zmieni się na **Administrator** (wskazano, że wdano zmianę), a  w kolumnie Grupa będzie wyświetlane nowe przypisanie do grupy.

> [!NOTE]
> Urządzeń nie można przenosić do innych grup, jeśli są one w stanie rejestracji "błąd" lub "oczekujący".
>
>Jeśli urządzenie nie zostało poprawnie usunięte, może być na nim pokazywany stan "gotowe". Jeśli przeniesiesz takie urządzenie, możliwe, że przeniesienie nie zostanie ukończone. Jeśli w kroku 5 nie widzisz  kolumny Grupa przypisana według zmiany  na Oczekuje w kroku 5, sprawdź, czy urządzenie jest dostępne, wyszukując je w usłudze Intune. Aby uzyskać więcej informacji, [zobacz Wyświetlanie szczegółów urządzenia w usłudze Intune](/mem/intune/remote-actions/device-inventory).
