---
title: Windows informacji o aktualizacjach zabezpieczeń
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: b3b1f43217b3be285f20925065bf9710a38f9606
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2021
ms.locfileid: "62959216"
---
# <a name="windows-security-update-insights"></a>Windows informacji o aktualizacjach zabezpieczeń
Ten widok zawiera omówienie stanu aktualizacji zabezpieczeń dla Twoich Microsoft Managed Desktop urządzeniach. 

Aby wyświetlić dane dotyczące użycia, wybierz <strong>kartę Windows aktualizacji zabezpieczeń</strong>.

![Windows aktualizacji zabezpieczeń: wykresy słupkowe stanu urządzenia i aktualizowanie wersji w lewej kolumnie, aktualizowanie postępu wdrażania w czasie w kolumnie środkowej, procent aktywnych urządzeń według grupy wdrażania, a także liczba dni zajęte do osiągnięcia wartości docelowej wdrożenia na poziomie 95% w prawej kolumnie.](../../media/update-insights.jpg)

## <a name="device-status"></a>Stan urządzenia

Aby urządzenia były aktualizowane przy Windows Update, muszą być połączone z Internetem i nie muszą być w stanie hibernacji przez co najmniej sześć godzin, z których dwie muszą być ciągłe. Chociaż możliwe jest, że urządzenie, które nie spełnia tych wymagań, zostanie zaktualizowane, urządzenia spełniające te wymagania mają największe prawdopodobieństwo aktualizacji. 

Aktywność na urządzeniu kategoryzuje się w kontekście aktualizacji Windows terminami:

- <strong>Aktywny:</strong> Urządzenia, które spełniają minimalne kryteria aktywności (sześć godzin, dwie ciągłe) najnowszej aktualizacji zabezpieczeń i zaewidencjonowane za pomocą Microsoft Intune co najmniej co pięć dni
- <strong>Zsynchronizowano:</strong> Urządzenia, które zaewidencjonowały się w usłudze Intune w ciągu ostatnich 28 dni
- <strong>Nie można zsynchronizować:</strong> Urządzenia, które <i>nie zostały</i> zaewidencjonowane za pomocą usługi Intune w ciągu ostatnich 28 dni




## <a name="update-version-status"></a>Aktualizowanie stanu wersji

Firma Microsoft wydaje aktualizacje zabezpieczeń w drugi wtorek miesiąca. Każde wydanie dodaje ważne aktualizacje dotyczące znanych luk w zabezpieczeniach. Microsoft Managed Desktop zapewnia, że 95% jego urządzeń zarządzanych jest aktualizowanych za pomocą najnowszej dostępnej aktualizacji zabezpieczeń co miesiąc. Aktualizacje zabezpieczeń są czasami wydane w innym czasie w celu pilnego rozwiązania nowych zagrożeń. Microsoft Managed Desktop wdraża te aktualizacje w podobny sposób.

Informacje o stanie wersji aktualizacji zabezpieczeń są kategoryzowane przy użyciu tych warunków:

- <strong>Bieżąca:</strong> Urządzenia z aktualizacją wydaną w bieżącym miesiącu
- <strong>Poprzedni:</strong> Urządzenia z aktualizacją opublikowaną w poprzednim miesiącu
- <strong>Starsze:</strong> Urządzenia z dowolną aktualizacją zabezpieczeń wydaną przed poprzednim miesiącem

W kategorii Starsze powinno być widać niewiele <strong></strong> urządzeń — duża lub rosnąca populacja prawdopodobnie wskazuje problem, który należy zgłosić do firmy Microsoft Managed Desktop aby można było go zbadać.


## <a name="deployment-progress"></a>Postęp wdrażania

Na początku każdego cyklu aktualizacji zabezpieczeń program Microsoft Managed Desktop migawkę populacji urządzeń i ustawia wartość docelową wdrożenia na poziomie 95% tej populacji. W <strong>obszarze Postęp wdrażania</strong> jest przedstawiany trend historyczny, aktualizowany codziennie, w celu śledzenia, jak blisko wdrożenie aktualizacji spełnia ten cel w poszczególnych wersjach. Na tym wykresie są tylko urządzenia ze stanem Aktywne.

Te dane można wyświetlić dla poprzednich cyklów aktualizacji przy użyciu menu rozwijanego w prawym górnym rogu. Okres, który wybierzesz w tym menu, dotyczy wszystkich informacji na całej stronie.

Obszar <strong>Zaktualizowano aktywne urządzenia według grupy</strong> wdrożenia udostępnia inny widok, pokazując postęp instalacji aktualizacji dla poszczególnych Microsoft Managed Desktop wdrażania.

W <strong>obszarze Dni do osiągnięcia wartości docelowej</strong> jest wyświetlany czas, jaki trwało zaktualizowanie przez 95% całkowitej liczby urządzeń przy użyciu bieżącej aktualizacji zabezpieczeń. W trakcie wdrażania w tym obszarze jest wyświetlany <strong></strong> obszar Nadal aktualizowane do momentu osiągnięciu wartości docelowej 95% dla wybranej aktualizacji.

## <a name="device-details-area"></a>Obszar szczegółów urządzenia

U dołu pulpitu nawigacyjnego znajduje się tabela ze szczegółowymi informacjami dla Twoich [](#device-status) urządzeń, w tym stanem urządzenia i [stanem Aktualizacji wersji](#update-version-status). Możesz przeszukać tę listę lub przefiltrować ją według dowolnej wartości z listy.


![Tabela szczegółów urządzenia z kolumnami z nazwą urządzenia, przypisanym użytkownikiem, stanem urządzenia, wersją aktualizacji, wersją systemu operacyjnego i datą ostatniej synchronizacji urządzenia.](../../media/security-update-insights-device-table-sterile.png)
