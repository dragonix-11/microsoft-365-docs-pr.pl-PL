---
title: Centrum administracyjne platformy Microsoft 365 Yammer raporty użycia urządzeń
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
description: Pobierz raport użycia urządzenia Yammer, aby dowiedzieć się więcej o urządzeniach używanych przez użytkowników Yammer, liczbie użytkowników dziennie według typu urządzenia i szczegółach na użytkownika.
ms.openlocfilehash: faf5b364090fe4ed88e0a6dd977238e65f3e6c68
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467191"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-device-usage-report"></a>raporty Microsoft 365 w centrum administracyjnym — raport użycia urządzenia Yammer

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).
  
W raportach użycia urządzeń z usługą Yammer znajdują się informacje o urządzeniach, na których Twoi użytkownicy korzystają z usługi Yammer. Dzienną liczbę użytkowników możesz przeglądać według typu urządzenia oraz liczby użytkowników korzystających z danego typu urządzenia. Obie te wartości możesz wyświetlić dla wybranego okresu. Możesz również zobaczyć szczegółowe informacje dotyczące poszczególnych użytkowników.
 
## <a name="how-do-i-get-to-the-yammer-device-usage-report"></a>Jak uzyskać raport użycia urządzeń z usługą Yammer?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie Yammer.
  
## <a name="interpret-the-yammer-device-usage-report"></a>Interpretowanie raportu użycia urządzenia Yammer

Możesz wyświetlić użycie w raporcie OneDrive, wybierając kartę **Użycie urządzenia**.<br/>![raporty Microsoft 365 — raport użycia urządzenia firmy Microsoft Yammer.](../../media/e21af4c0-0ad2-4485-8ab1-2f82d7dfa90e.png)

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Yammer raport użycia urządzenia — wybierz kolumny.](../../media/fc1fc8db-e197-4878-85c7-7ba0d67b9379.png)

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

Raport **użycia urządzenia Yammer** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Nazwa użytkownika  <br/> |Adres e-mail użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe. Ta siatka przedstawia użytkowników, którzy zalogowali się do Yammer przy użyciu konta Microsoft 365 lub zalogowali się do sieci przy użyciu logowania jednokrotnego. <br/> |
|Nazwa wyświetlana  <br/> |Pełna nazwa użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe.  <br/> |
|Stan użytkownika  <br/> |Jedna z trzech wartości: Aktywne, Usunięte lub Zawieszone. Te raporty zawierają dane dotyczące aktywnych, zawieszonych i usuniętych użytkowników. Nie uwzględniają oczekujących użytkowników, ponieważ oczekujący użytkownicy nie mogą publikować ani odczytywać wiadomości lub oznaczać ich jako lubiane.   <br/> |
|Data zmiany stanu (UTC)  <br/> |Data zmiany stanu użytkownika w Yammer.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Ostatnia data (UTC) udziału użytkownika w Yammer działaniu.  <br/> |
|Web  <br/> |Wskazuje, czy użytkownik użył Yammer w Internecie.  <br/> |
|telefon Windows  <br/> | Wskazuje, czy użytkownik użył Yammer na telefonie Windows.  <br/> |
|Telefon z systemem Android  <br/> |Wskazuje, czy użytkownik użył Yammer na telefonie Android. <br/>|
|Iphone <br/> | Wskazuje, czy użytkownik użył Yammer na iPhone.  <br/> |
|Ipad  <br/> |Wskazuje, czy użytkownik użył Yammer na iPad. <br/>|
|Innych  <br/> |Wskazuje, czy użytkownik użył Yammer na innym urządzeniu, które nie zostało wymienione wcześniej. <br/>|
|||