---
title: raporty aktywności Centrum administracyjne platformy Microsoft 365 Yammer
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Pobierz raport aktywności Yammer i dowiedz się więcej o liczbie użytkowników korzystających z Yammer do publikowania lub odczytywania wiadomości.
ms.openlocfilehash: 3ab1f13ec9b7b86bb1a7d858b849f22e687ae8aa
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781298"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-activity-report"></a>raporty Microsoft 365 w centrum administracyjnym — raport aktywności Yammer

Jako administrator Microsoft 365 pulpit nawigacyjny Raporty przedstawia dane dotyczące użycia produktów w organizacji. Zapoznaj się z [raportami aktywności w centrum administracyjnym](activity-reports.md). **Raport aktywności usługi Yammer** umożliwia zrozumienie poziomu zaangażowania organizacji w usłudze Yammer na podstawie liczby unikatowych użytkowników publikujących i odczytujących wiadomości w usłudze Yammer oraz oznaczających je jako lubiane, jak również liczby aktywności wygenerowanych w organizacji. 
 
## <a name="how-do-i-get-to-the-yammer-activity-report"></a>Jak mogę przejść do raportu aktywności Yammer?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie Yammer.

  
## <a name="interpret-the-yammer-activity-report"></a>Interpretowanie raportu dotyczącego aktywności usługi Yammer

Możesz wyświetlić działania w raporcie Yammer, wybierając kartę **Działanie**.<br/>![raporty Microsoft 365 — raport aktywności Yammer firmy Microsoft.](../../media/9b251183-c2b3-430c-ab2d-58bf11e7e3ae.png)

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Yammer raport aktywności — wybierz kolumny.](../../media/7ef6351d-f7e9-4504-913d-2c2df9062bf6.png)

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

Raport **aktywności Yammer** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Nazwa użytkownika  <br/> |Adres e-mail użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe. Ta siatka przedstawia użytkowników, którzy zalogowali się do Yammer przy użyciu konta Microsoft 365 lub zalogowali się do sieci przy użyciu logowania jednokrotnego. <br/> |
|Nazwa wyświetlana  <br/> |Pełna nazwa użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe.  <br/> |
|Stan użytkownika  <br/> |Jedna z trzech wartości: Aktywowane, Usunięte lub Zawieszone. Te raporty zawierają dane dotyczące aktywnych, zawieszonych i usuniętych użytkowników. Nie uwzględniają oczekujących użytkowników, ponieważ oczekujący użytkownicy nie mogą publikować ani odczytywać wiadomości lub oznaczać ich jako lubiane.  <br/> |
|Data zmiany stanu (UTC)  <br/> |Data zmiany stanu użytkownika w Yammer.  <br/> |
|Data ostatniego działania (UTC)  <br/> | Ostatnia data opublikowania, przeczytania lub polubiania wiadomości przez użytkownika.  <br/> |
|Wysłany  <br/> |Liczba komunikatów publikowanych przez użytkownika w określonym okresie. <br/>|
|Odczytu  <br/> |Liczba konwersacji odczytanych przez użytkownika w określonym okresie.  <br/> |
|Lubi  <br/> |Liczba komunikatów, które użytkownik lubił w określonym okresie.  <br/>|
|Przypisany produkt  <br/> |Produkty przypisane do tego użytkownika.|
|||