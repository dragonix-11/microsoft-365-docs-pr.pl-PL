---
title: Szczegółowe informacje o baterii
description: Raport, który przedstawia dane dotyczące przewidywanego czasu pracy baterii i najgorętszych odbiorców energii
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 32ab3a984d5ab46aac26989518cd3e570082d688
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2021
ms.locfileid: "62959215"
---
# <a name="battery-insights"></a>Szczegółowe informacje o baterii
Ten widok udostępnia metryk użycia baterii, baterii i aplikacji dla Twoich Microsoft Managed Desktop urządzeniach. W tych celach aplikacja jest uznawana za "używaną", jeśli jest uruchomiona i ma fokus.

Aby wyświetlić dane dotyczące użycia, wybierz **kartę Bateria** .

![Okienko baterii: prognozowany czas pracy baterii na model urządzenia w lewym górnym rogu, górny odbiorcy energii (według aplikacji) w prawym górnym rogu, tabela Szczegółowe informacje w dolnej części. Link Do dokumentacji w prawym górnym rogu](../../media/insights_battery.png)

## <a name="predicted-battery-life"></a>Przewidywany czas pracy baterii

W obszarze **Prognozowany czas pracy** baterii posuniemy prognozy oczekiwanego czasu pracy baterii dla Twoich urządzeń zorganizowane według modelu urządzenia.

> [!NOTE]
> Te dane pochodzą z próbkowania zużycia energii, czasu użytkowania i pojemności baterii z losowego wyboru urządzeń <em></em> we wdrożeniu pakietu Microsoft Managed Desktop, które również zgłaszają dane.

Ta tabela przewiduje czas pracy baterii (w godzinach), średni czas pracy baterii dla tych samych modeli w innych wdrożeniach firmy Microsoft Managed Desktop oraz liczbę urządzeń raportowania tych danych w Twoim środowisku. Posortuj dane, zaznaczając nagłówki kolumn.



## <a name="top-energy-consumers"></a>Najgorętsi odbiorcy energii

W obszarze **Najważniejsze odbiorcy energii** znajdziesz aplikacje w Twoim środowisku, które zużywa najwięcej energii w miliwatach (mWh). Pokazane aplikacje są dla określonego urządzenia wybrane w sekcji **Prognozowany czas pracy** baterii po lewej stronie. Aby na przykład sprawdzić zużycie przez aplikację urządzeń z systemem Microsoft Surface Book 2, wybierz ten wiersz w obszarze czasu pracy baterii. Jeśli nie wybierzesz żadnego modelu, wyświetlone dane użycia aplikacji będą dla wszystkich aplikacji, dla których mamy dane zbiorczo.

 Dla każdej aplikacji kolorowe segmenty pokazują rozkład zużycia energii w aplikacji w tych kategoriach:

- Procesor CPU
- Wyświetl
- Sieć
- Inne

"Inne" może obejmować zużycie energii przez różne źródła, takie jak aktywność dyskowa, komórkowe połączenie szerokopasmowe oraz zużycie energii utracone na odporność wewnętrzną. 

Możesz filtrować ten widok, aby wyświetlać tylko aplikacje pierwszego planu, aplikacje tła lub obie te aplikacje przy użyciu menu w prawym górnym rogu. Aplikacje pierwszego planu to te, które w ostatnich 28 dniach miały interakcje z użytkownikiem, na przykład wybieranie czegoś za pomocą myszy.

## <a name="insights"></a>Szczegółowe informacje

Obszar **Szczegółowe informacje** przedstawia trzech głównych odbiorców energii w kategoriach procesora i sieci. Te elementy zużywają więcej niż średnia energię w porównaniu z Microsoft Managed Desktop wdrożeniami. Nie pokazujemy zasobu wyświetlania, ponieważ zależy on w dużej mierze od czasu użytkowania urządzenia i ustawień jasności ekranu. 

Wybierz listy w kolumnie **Szczegóły, aby** uzyskać więcej informacji.

## <a name="battery-optimization"></a>Optymalizacja baterii

Windows 10 oferuje wiele [ustawień urządzenia,](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips) aby poprawić zużycie energii i zwiększyć czas pracy baterii Microsoft Managed Desktop urządzenia. Niektóre z tych ustawień mogą zmniejszyć Windows funkcjonalności, dlatego musisz także wziąć pod uwagę inne czynniki, takie jak rola urządzenia w organizacji. Windows obsługuje zapisywanie listy tych porad [dotyczących oszczędzania baterii](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips).

Użytkownicy mogą samodzielnie dostosować niektóre ustawienia bez potrzeby podwyższenia lub obsługi administracyjnej. Inne ustawienia wymagają pomocy ze strony administratora IT Twojej organizacji.
