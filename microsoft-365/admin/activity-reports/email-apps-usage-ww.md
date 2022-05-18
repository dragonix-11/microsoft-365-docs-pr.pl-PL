---
title: Centrum administracyjne platformy Microsoft 365 raporty użycia aplikacji poczty e-mail
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
- MET150
- MOE150
- GEA150
ms.assetid: c2ce12a2-934f-4dd4-ba65-49b02be4703d
description: Dowiedz się, jak uzyskać raport użycia aplikacji poczty e-mail, aby dowiedzieć się, ile aplikacji poczty e-mail łączy się z Exchange Online i której wersji Outlook użytkownicy używają.
ms.openlocfilehash: 8a9a416e533bd1e8b30f385ec8b15db182e593c6
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467695"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Microsoft 365 Raporty w centrum administracyjnym — użycie aplikacji poczty e-mail

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). W raporcie użycia aplikacji poczty e-mail możesz zobaczyć, ile aplikacji poczty e-mail łączy się z Exchange Online. Można też sprawdzić informacje o wersji aplikacji programu Outlook, z których korzystają użytkownicy, co umożliwia skontaktowanie się z tymi, którzy korzystają z nieobsługiwanych wersji, w celu zainstalowania wersji obsługiwanych.
  
## <a name="how-to-get-to-the-email-apps-report"></a>Jak uzyskać dostęp do raportu aplikacji poczty e-mail

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.
2. Wybierz pozycję **Wyświetl więcej** w obszarze **Aktywność poczty e-mail**. 
3. Z listy rozwijanej **Aktywność poczty e-mail** wybierz pozycję **Exchange** \> **Użycie aplikacji poczty e-mail**.
  
## <a name="interpret-the-email-apps-report"></a>Interpretowanie raportu aplikacji poczty e-mail

Widok aktywności aplikacji poczty e-mail można uzyskać, przeglądając **wykresy Użytkownicy** i **Klienci** . 
  
![Użyto klientów poczty e-mail.](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)
  
|Element|Opis|
|:-----|:-----|
|1.  <br/> |Raport **użycia aplikacji poczty e-mail** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).  <br/> |
|2.  <br/> |Dane w każdym raporcie zwykle obejmują do ostatnich 24 do 48 godzin.  <br/> |
|3.  <br/> |W widoku **Użytkownicy** można sprawdzić liczbę unikatowych użytkowników, którzy łączyli się z usługą Exchange Online przy użyciu dowolnej aplikacji e-mail.  <br/> |
|4.  <br/> |W widoku **Aplikacje** można sprawdzić liczbę unikatowych użytkowników według aplikacji w wybranym okresie.  <br/> |
|5.  <br/> |W widoku **Wersje** jest wyświetlana liczba unikatowych użytkowników dla każdej wersji Outlook w Windows.  <br/> |
|6.  <br/> | Oś Y na wykresie na wykresie **Użytkownicy** reprezentuje całkowitą liczbę unikatowych użytkowników, którzy łączyli się z aplikacją dowolnego dnia w okresie raportowania.  <br/>  Oś X na wykresie na wykresie **Użytkownicy** reprezentuje liczbę unikatowych użytkowników, którzy używali aplikacji w okresie raportowania.  <br/>  Oś Y na wykresie **Aplikacje** przedstawia całkowitą liczbę unikatowych użytkowników, którzy używali konkretnej aplikacji w okresie raportowania.  <br/>  Oś X na wykresie **Aplikacje** odpowiada liście aplikacji w organizacji.  <br/>  Oś Y na wykresie na wykresie **Wersje** reprezentuje całkowitą liczbę unikatowych użytkowników korzystających z konkretnej wersji klasycznej programu Outlook. Jeśli raport nie może rozpoznać numeru wersji Outlook, ilość będzie wyświetlana jako **Nieokreślona**.  <br/>  Oś X na wykresie na wykresie **Wersje** odpowiada liście aplikacji w organizacji.  <br/> |
|7.  <br/> |Możesz filtrować serie widoczne na wykresie, wybierając element w legendzie.  <br/> |
|8.  <br/> | Być może nie wszystkie elementy poniższej listy będą widoczne od razu  musisz wtedy dodać odpowiednie kolumny.<br/> **Nazwa użytkownika** to nazwa właściciela aplikacji poczty e-mail.  <br/> **Data ostatniego działania** to najnowsza data odczytu lub wysłania wiadomości e-mail przez użytkownika.  <br/> **Poczta na komputerze Mac**, **Outlook dla komputerów Mac**, **Outlook**, **Outlook Mobile** i **Outlook w sieci Web** to przykłady aplikacji e-mail, które mogą być używane w organizacji.  <br/>  Jeśli zasady organizacji nie pozwalają na wyświetlanie raportów zawierających identyfikowalne dane użytkowników, możesz zmienić ustawienie prywatności dla wszystkich tych raportów. Zapoznaj się z **sekcją Jak mogę ukrywania szczegółów na poziomie użytkownika?** w sekcji [Raporty aktywności w Centrum administracyjne platformy Microsoft 365](activity-reports.md).  <br/> |
|9.  <br/> |Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Raport użycia aplikacji poczty e-mail — wybierz kolumny.](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)|
|10.  <br/> |Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.  <br/> |
|||
   
