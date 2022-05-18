---
title: Centrum administracyjne platformy Microsoft 365 raporty aktywności poczty e-mail
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
ms.assetid: 1cbe2c00-ca65-4fb9-9663-1bbfa58ebe44
description: Dowiedz się, jak uzyskać raport aktywności poczty e-mail i zrozumieć trendy dotyczące poczty e-mail użytkowników, korzystając z pulpitu nawigacyjnego Microsoft 365 Raporty w Centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: b84d8c3e6e85ab64b1ec70379e7c016374f28e78
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467673"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Microsoft 365 Raporty w centrum administracyjnym — działanie poczty e-mail

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).
  
Na przykład możesz uzyskać ogólne informacje dotyczące ruchu związanego z pocztą e-mail w organizacji, korzystając ze strony Raporty, a następnie przejść do szczegółów w widżecie Aktywność poczty e-mail, aby zrozumieć trendy i aktywność poszczególnych użytkowników związaną z pocztą e-mail w organizacji.

## <a name="how-to-get-to-the-email-activity-report"></a>Jak przejść do raportu dotyczącego aktywności poczty e-mail

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.
2. Wybierz pozycję **Wyświetl więcej** w obszarze **Aktywność poczty e-mail**. 
3. Z listy rozwijanej **Aktywność poczty e-mail** wybierz pozycję **Exchange** \> **Działanie poczty e-mail**.
  
## <a name="interpret-the-email-activity-report"></a>Interpretacja raportu dotyczącego aktywności poczty e-mail

Wykresy **Aktywność** i **Użytkownicy** umożliwiają zapoznanie się z aktywnością użytkowników związaną z pocztą e-mail. 
  
![Raport aktywności poczty e-mail.](../../media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png)
  
|Element|Opis|
|:-----|:-----|
|1.  <br/> |W raporcie **Aktywność poczty e-mail** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).  <br/> |
|2.  <br/> |Dane w każdym raporcie zwykle obejmują do ostatnich 24 do 48 godzin.  <br/> |
|3.  <br/> |Wykres **Aktywność** umożliwia zrozumienie trendu intensywności aktywności poczty e-mail w organizacji. Możesz zrozumieć podział działań związanych z wysyłaniem wiadomości e-mail, odczytem wiadomości e-mail, odebraniem wiadomości e-mail, utworzonym spotkaniem lub interakcjami ze spotkaniami.  <br/> |
|4.  <br/> |Wykres **Użytkownicy** umożliwia zrozumienie trendu liczby unikatowych użytkowników generujących aktywność poczty e-mail. Możesz przyjrzeć się trendowi, w który użytkownicy wykonują wysyłanie wiadomości e-mail, odczytywanie wiadomości e-mail, odbieranie wiadomości e-mail, tworzenie spotkań lub interakcje na spotkaniach.  <br/> |
|5.  <br/> | Na wykresie **Działania** oś Y to liczba działań typu wysłana wiadomość e-mail, odebrana wiadomość e-mail, odczyt wiadomości e-mail, utworzone spotkanie i spotkanie.  <br/>  Na wykresie aktywności **Użytkownicy** oś Y jest działaniem użytkownika wykonującym działanie typu wysłana wiadomość e-mail, odebrana wiadomość e-mail, odczyt wiadomości e-mail, utworzone spotkanie lub spotkanie.  <br/>  Oś X na obu wykresach przedstawia wybrany w raporcie przedział czasu.  <br/> |
|6.  <br/> |Możesz filtrować serie widoczne na wykresie, wybierając element w legendzie.  <br/> |
|7.  <br/> | W tabeli przedstawiono zestawienie aktywności poczty e-mail na poziomie poszczególnych użytkowników. Jest to lista wszystkich użytkowników, do których przypisano produkt Exchange, i wykonywanych przez nich operacji związanych z pocztą e-mail. <br/> <br/> **Nazwa użytkownika** to adres e-mail użytkownika.  <br/> **Nazwa wyświetlana** jest pełną nazwą użytkownika.  <br/> Stan **Usunięte** oznacza użytkownika, który został usunięty, ale był aktywny przez pewną część okresu raportowania dla tego raportu.  <br/> **Data usunięcia** to data usunięcia użytkownika.  <br/> **Data ostatniego działania** to data ostatniego odczytania lub wysłania wiadomości e-mail przez użytkownika.  <br/> **Akcje wysłania** to liczba zarejestrowanych akcji wysyłania wiadomości e-mail przez użytkownika.  <br/> **Akcje odebrania** to liczba zarejestrowanych akcji odbierania wiadomości e-mail przez użytkownika.  <br/> **Akcje przeczytania** to liczba zarejestrowanych akcji czytania wiadomości e-mail przez użytkownika.  <br/> **Akcje utworzone na spotkaniu** to liczba akcji wysyłania żądania spotkania zarejestrowanej dla użytkownika.  <br/> **Akcje interakcji ze spotkaniem** to liczba akcji akceptowania, wstępnego, odrzucania lub anulowania żądania spotkania dla użytkownika.  <br/> **Przypisany produkt** to produkty przypisane do tego użytkownika.  <br/>  Jeśli zasady organizacji nie pozwalają na wyświetlanie raportów zawierających identyfikowalne dane użytkowników, możesz zmienić ustawienie prywatności dla wszystkich tych raportów. Zapoznaj się z **sekcją Jak mogę ukrywania szczegółów na poziomie użytkownika?** w sekcji [Raporty aktywności w Centrum administracyjne platformy Microsoft 365](activity-reports.md).  <br/> |
|8.  <br/> |Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Raport aktywności poczty e-mail — wybierz kolumny.](../../media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png)|
|9.  <br/> |Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.  <br/> |
|||
   
> [!NOTE]
> Raport aktywności poczty e-mail jest dostępny tylko dla skrzynek pocztowych skojarzonych z użytkownikami, którzy mają licencje.
