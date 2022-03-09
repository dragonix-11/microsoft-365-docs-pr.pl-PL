---
title: centrum administracyjne platformy Microsoft 365 Yammer dotyczące użycia urządzeń
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
description: Uzyskaj raport Yammer użycia urządzeń, aby dowiedzieć się, z jakich urządzeń korzysta Yammer urządzenia.
ms.openlocfilehash: fc59060cc4ec0ad3d34aae2b165bcb36ee1aee89
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400423"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-device-usage-report"></a>Microsoft 365 raporty w centrum administracyjnym — raport Yammer użycia urządzeń

Pulpit Microsoft 365 pulpitu nawigacyjnego Raporty zawiera informacje o aktywności dotyczącej wszystkich produktów w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).
  
W raportach użycia urządzeń z usługą Yammer znajdują się informacje o urządzeniach, na których Twoi użytkownicy korzystają z usługi Yammer. Dzienną liczbę użytkowników możesz przeglądać według typu urządzenia oraz liczby użytkowników korzystających z danego typu urządzenia. Obie te wartości możesz wyświetlić dla wybranego okresu. Możesz również zobaczyć szczegółowe informacje dotyczące poszczególnych użytkowników.
 
## <a name="how-do-i-get-to-the-yammer-device-usage-report"></a>Jak uzyskać raport użycia urządzeń z usługą Yammer?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie Yammer głównej.
  
## <a name="interpret-the-yammer-device-usage-report"></a>Interpretowanie raportu Yammer użycia urządzeń

Użycie możesz wyświetlić w raporcie OneDrive, wybierając **kartę Użycie** urządzenia.<br/>![Microsoft 365 raporty — Raport Yammer użycia urządzeń przez firmę Microsoft.](../../media/e21af4c0-0ad2-4485-8ab1-2f82d7dfa90e.png)

Wybierz **pozycję Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Yammer użycia urządzeń — wybierz kolumny.](../../media/fc1fc8db-e197-4878-85c7-7ba0d67b9379.png)

Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

W **Yammer użycia** urządzeń można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metryczny**|**Definicja**|
|Nazwa użytkownika  <br/> |Adres e-mail użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe. Ta siatka przedstawia użytkowników, którzy zalogowali się do Yammer przy użyciu konta Microsoft 365 lub zalogowali się do sieci przy użyciu logowania pojedynczego. <br/> |
|Nazwa wyświetlana  <br/> |Pełna nazwa użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe.  <br/> |
|Stan użytkownika  <br/> |Jedna z trzech wartości: Aktywna, Usunięta lub Zawieszona. Te raporty zawierają dane dotyczące aktywnych, zawieszonych i usuniętych użytkowników. Nie uwzględniają oczekujących użytkowników, ponieważ oczekujący użytkownicy nie mogą publikować ani odczytywać wiadomości lub oznaczać ich jako lubiane.   <br/> |
|Data zmiany stanu (UTC)  <br/> |Data zmiany stanu użytkownika w programie Yammer.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Ostatnia data (UTC), w przypadku których użytkownik uczestniczył w Yammer danych.  <br/> |
|Web  <br/> |Wskazuje, czy użytkownik użył już Yammer sieci Web.  <br/> |
|Windows telefonu  <br/> | Wskazuje, czy użytkownik używał Yammer telefonu Windows telefonu.  <br/> |
|Telefon z systemem Android  <br/> |Wskazuje, czy użytkownik używał aplikacji Yammer na telefonie z systemem Android. <br/>|
|iphone <br/> | Wskazuje, czy użytkownik użył już Yammer do iPhone.  <br/> |
|ipad  <br/> |Wskazuje, czy użytkownik użył już Yammer danych w iPad. <br/>|
|inne  <br/> |Wskazuje, czy użytkownik użył wcześniej Yammer urządzenia, które nie zostało wymienione wcześniej. <br/>|
|||