---
title: Windows testowania aplikacji serwera
description: Jak sprawdzić poprawność podczas testowania aplikacji systemu Windows Server
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 99868e53e98bded9139ecedea9c9d62e9d48fd2f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988428"
---
# <a name="windows-server-application-testing"></a>Windows testów aplikacji serwera

Dzięki bazie testowej Microsoft 365 można teraz sprawdzać poprawność aplikacji na Windows Server 2016 i 2019 r., w tym na serwerze Core!

Aby rozpocząć sprawdzania poprawności przekazanych aplikacji pod względem wersji wstępnej aktualizacji dla systemów operacyjnych Windows Server 2016 i 2019 na podstawie bazy testowej dla systemu Microsoft 365, należy wykonać następujące czynności:

1. Zaloguj się do naszego samoobsługowego portalu dołączania. W menu nawigacji po lewej stronie wybierz pozycję `Upload new package` pod `Package catalogue` i wypełnij pole Szczegóły testu.

2. Wybierz `Security updates` jako typ aktualizacji systemu operacyjnego:

   ![Wybierz aktualizacje zabezpieczeń.](Media/selecting-security-updates.png)

3. W obszarze Wersje systemu operacyjnego do przetestowania wybierz odpowiednie wersje systemu operacyjnego. Możesz wybrać Windows serwera operacyjnego lub połączenie wersji serwera i systemu operacyjnego klienta.

   ![Wybierz pozycję Wersja systemu operacyjnego.](Media/selecting-OS-versions.png)

4. Podaj inne wymagane informacje, przejrzyj podane szczegóły i przekaż pakiet aplikacji. Po przesłaniu możesz wyświetlić stan pakietu na karcie menu Zarządzanie pakietami.

5. Aby wyświetlić wyniki testów i szczegółowe informacje dotyczące sprawdzania poprawności aplikacji pod względem wersji wstępnej aktualizacji zabezpieczeń dla wersji Windows Server 2016 i 2019, przejdź do strony Podsumowania testu lub strony wyników aktualizacji zabezpieczeń.

   ![Wyświetl wyniki testów.](Media/access-test-results.png)

Przejść do następnego artykułu, aby rozpocząć testowanie **funkcjonalności**
> [!div class="nextstepaction"]
> [Następny krok](functional.md)
