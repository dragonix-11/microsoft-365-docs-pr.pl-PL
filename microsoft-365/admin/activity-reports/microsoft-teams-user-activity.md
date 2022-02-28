---
title: centrum administracyjne platformy Microsoft 365 — aktywność Microsoft Teams użytkowników
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
ms.assetid: 07f67fc4-c0a4-4d3f-ad20-f40c7f6db524
description: Dowiedz się, jak uzyskać raport Microsoft Teams aktywności użytkowników i uzyskać szczegółowe informacje na temat Teams aktywności w organizacji.
ms.openlocfilehash: ec5e6d2aa17fb3e58136a61336f06f6d41f3162f
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989639"
---
# <a name="microsoft-365-admin-center-reports---microsoft-teams-user-activity"></a>centrum administracyjne platformy Microsoft 365 — aktywność Microsoft Teams użytkowników

Pulpit Microsoft 365 pulpitu nawigacyjnego Raporty zawiera informacje o aktywności dotyczącej wszystkich produktów w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). Raport dotyczący aktywności użytkowników aplikacji Microsoft Teams pozwala uzyskać szczegółowe informacje o aktywności związanej z aplikacją Microsoft Teams w organizacji.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Jak przejść do raportu aktywności użytkowników aplikacji Microsoft Teams

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.

    
2. Z listy **rozwijanej Wybierz** raport wybierz pozycję Aktywność **Microsoft Teams** \> **użytkowników**.
  
## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpretowanie raportu aktywności użytkowników aplikacji Microsoft Teams

Wykresy **Aktywność** i **Użytkownicy** umożliwiają zapoznanie się z aktywnością użytkowników związaną z aplikacją Microsoft Teams.<br/>![Microsoft 365 raporty — Microsoft Teams aktywności użytkowników.](../../media/40359f81-25f7-416d-bb1e-37289133ef6b.png)
  
|Element|Opis|
|:-----|:-----|
|1.  <br/> |W raporcie **Aktywność użytkowników aplikacji Microsoft Teams** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).  <br/> |
|2.  <br/> |Dane w poszczególnych raportach zazwyczaj obejmują od 24 do 48 godzin.  <br/> |
|3.  <br/> |Aby zapewnić jakość danych, przeprowadzamy codzienne testy sprawdzania poprawności danych z ostatnich pięciu dni i będziemy wypełniać wszelkie wykryte luki. W trakcie tego procesu możesz zauważyć różnice w danych historycznych.  <br/> |
|4.  <br/> |W widoku **Aktywność** można sprawdzić liczbę działań w aplikacji Microsoft Teams według typu aktywności. Typy aktywności to liczba wiadomości czatu zespołu, wiadomości czatu prywatnego, połączeń lub spotkań.  <br/> |
|5.  <br/> |W widoku **Użytkownicy** można sprawdzić liczbę użytkowników według typu aktywności. Typy aktywności to liczba wiadomości czatu zespołu, wiadomości czatu prywatnego, połączeń lub spotkań.  <br/> |
|6.  <br/> | Oś Y **na wykresie Aktywność** przedstawia liczbę określonych działań.  <br/>  Oś Y na **wykresie Pliki przedstawia** liczbę użytkowników uczestniczących w czatach zespołów, czatach prywatnych, połączeniach lub spotkaniach.  <br/>  Oś X na wykresach to wybrany w raporcie przedział czasu.  <br/> |
|7.  <br/> |Serie, które są na wykresie, można filtrować, zaznaczając je w legendzie. Na  przykład na wykresie Aktywność wybierz **pozycję** Wiadomości kanałów **, Wiadomości** **czatu, Połączenia** lub **Spotkania, aby** wyświetlić tylko informacje dotyczące poszczególnych kanałów. Zmiana ta nie ma wpływu na informacje w siatce tabeli.  <br/> ![Filtrowanie Microsoft Teams aktywności.](../../media/c819c4ea-6e9a-4411-a0dd-9f800d64ce38.png)|
|8.  <br/> | Lista wyświetlanych grup jest ustalana na podstawie zbioru wszystkich grup, które istniały (nie zostały usunięte) w najdłuższym (180-dniowym) przedziale czasu raportowania. Liczba działań zależy od wybranego przedziału dat.  <br/> UWAGA: Możesz nie widzieć wszystkich elementów na poniższej liście w kolumnach, dopóki ich nie dodasz.<br/>**Nazwa użytkownika** to adres e-mail użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe.  <br/> **Data ostatniego działania (UTC)** odwołuje się do ostatniej daty, kiedy użytkownik uczestniczył w działaniu w aplikacji Microsoft Teams.  <br/> **Wiadomości kanałów** to liczba unikatowych wiadomości opublikowanych przez użytkownika w czacie zespołu w danym okresie.  <br/> **Wiadomości czatu** to liczba unikatowych wiadomości opublikowanych przez użytkownika w czacie prywatnym w danym okresie.  <br/> **Połączenia** to liczba połączeń, w których uczestniczył użytkownik w danym okresie.  <br/> **Spotkania** to liczba spotkań online, w których uczestniczył użytkownik w danym okresie.  <br/> **Inne działania** to liczba innych działań w zespole wykonanych przez użytkownika.  <br/> **Usunięte** wskazuje, czy zespół został usunięty. Jeśli zespół został usunięty, ale w okresie raportowania nastąpiła w nim aktywność, grupa ta pojawi się na siatce z parametrem Usunięte ustawionym na wartość Prawda.  <br/> **Data usunięcia** to data usunięcia zespołu.  <br/> **Przypisany produkt** to lista produktów przypisanych do użytkownika.  <br/>  Jeśli zasady organizacji nie pozwalają na wyświetlanie raportów zawierających identyfikowalne dane użytkowników, możesz zmienić ustawienie prywatności dla wszystkich tych raportów. Zobacz sekcję **Ukrywanie szczegółów na poziomie użytkownika w** sekcji [Raporty aktywności w centrum administracyjne platformy Microsoft 365](activity-reports.md).  <br/> |
|9.  <br/> |Wybierz **pozycję** Kolumny, aby dodać lub usunąć kolumny z raportu.  <br/> ![Teams aktywności użytkowników — wybierz kolumny.](../../media/eb5fbcee-e371-4d36-a0c6-fa54732311ec.png)|
|10.  <br/> |Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.  <br/> |
|||
   

