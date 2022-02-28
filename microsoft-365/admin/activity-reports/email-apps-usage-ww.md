---
title: Microsoft 365 w centrum administracyjnym — Użycie aplikacji poczty e-mail
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
description: Dowiedz się, jak uzyskać raport użycia aplikacji poczty e-mail, aby dowiedzieć się więcej o aplikacjach poczty e-mail łączących się Exchange Online siecią Outlook wersji poczty e-mail, z których korzystali użytkownicy.
ms.openlocfilehash: 601258d721f817438f0bd6a08d98d73aa22b7afb
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989653"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Microsoft 365 w centrum administracyjnym — Użycie aplikacji poczty e-mail

Pulpit Microsoft 365 pulpitu nawigacyjnego Raporty zawiera informacje o aktywności dotyczącej wszystkich produktów w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). W raporcie użycie aplikacji poczty e-mail możesz sprawdzić, ile aplikacji poczty e-mail łączy się z Exchange Online. Można też sprawdzić informacje o wersji aplikacji programu Outlook, z których korzystają użytkownicy, co umożliwia skontaktowanie się z tymi, którzy korzystają z nieobsługiwanych wersji, w celu zainstalowania wersji obsługiwanych.
  
## <a name="how-to-get-to-the-email-apps-report"></a>Jak uzyskać dostęp do raportu aplikacji poczty e-mail

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.
2. Wybierz pozycję **Wyświetl więcej w** obszarze **Aktywność poczty e-mail**. 
3. Z listy **rozwijanej** Aktywność poczty e-mail **wybierz pozycję** \> Exchange **użycie aplikacji poczty e-mail**.
  
## <a name="interpret-the-email-apps-report"></a>Interpretowanie raportu aplikacji poczty e-mail

Wykresy Użytkownicy i Klienci mogą chcieć zobaczyć aktywność w aplikacjach poczty **e-mail**. 
  
![U używanych klientów poczty e-mail.](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)
  
|Element|Opis|
|:-----|:-----|
|1.  <br/> |W **raporcie Użycie aplikacji poczty** e-mail można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).  <br/> |
|2.  <br/> |Dane w poszczególnych raportach zazwyczaj obejmują od 24 do 48 godzin.  <br/> |
|3.  <br/> |W widoku **Użytkownicy** można sprawdzić liczbę unikatowych użytkowników, którzy łączyli się z usługą Exchange Online przy użyciu dowolnej aplikacji e-mail.  <br/> |
|4.  <br/> |W widoku **Aplikacje** można sprawdzić liczbę unikatowych użytkowników według aplikacji w wybranym okresie.  <br/> |
|5.  <br/> |W **widoku** Wersje można zobaczyć liczbę unikatowych użytkowników dla każdej wersji pakietu Outlook w Windows.  <br/> |
|6.  <br/> | Oś Y na wykresie na wykresie **Użytkownicy** reprezentuje całkowitą liczbę unikatowych użytkowników, którzy łączyli się z aplikacją dowolnego dnia w okresie raportowania.  <br/>  Oś X na wykresie na wykresie **Użytkownicy** reprezentuje liczbę unikatowych użytkowników, którzy używali aplikacji w okresie raportowania.  <br/>  Oś Y na wykresie **Aplikacje** przedstawia całkowitą liczbę unikatowych użytkowników, którzy używali konkretnej aplikacji w okresie raportowania.  <br/>  Oś X na wykresie **Aplikacje** odpowiada liście aplikacji w organizacji.  <br/>  Oś Y na wykresie na wykresie **Wersje** reprezentuje całkowitą liczbę unikatowych użytkowników korzystających z konkretnej wersji klasycznej programu Outlook. Jeśli nie będzie można rozpoznać numeru wersji Outlook, ta liczba będzie pokazywana jako **Nieustalona**.  <br/>  Oś X na wykresie na wykresie **Wersje** odpowiada liście aplikacji w organizacji.  <br/> |
|7.  <br/> |Serie, które są na wykresie, można filtrować, zaznaczając je w legendzie.  <br/> |
|8.  <br/> | Być może nie wszystkie elementy poniższej listy będą widoczne od razu  musisz wtedy dodać odpowiednie kolumny.<br/> **Nazwa** użytkownika to nazwa właściciela aplikacji poczty e-mail.  <br/> **Data ostatniego działania** to najpóźniejsza data przeczytania lub wysłania wiadomości e-mail przez użytkownika.  <br/> **Poczta na komputerze Mac**, **Outlook dla komputerów Mac**, **Outlook**, **Outlook Mobile** i **Outlook w sieci Web** to przykłady aplikacji e-mail, które mogą być używane w organizacji.  <br/>  Jeśli zasady organizacji nie pozwalają na wyświetlanie raportów zawierających identyfikowalne dane użytkowników, możesz zmienić ustawienie prywatności dla wszystkich tych raportów. Zobacz sekcję **Ukrywanie szczegółów na poziomie użytkownika w** sekcji [Raporty aktywności w centrum administracyjne platformy Microsoft 365](activity-reports.md).  <br/> |
|9.  <br/> |Wybierz **pozycję Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Raport użycia aplikacji poczty e-mail — wybieranie kolumn.](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)|
|10.  <br/> |Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.  <br/> |
|||
   
