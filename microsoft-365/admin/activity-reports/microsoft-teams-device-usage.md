---
title: Użycie urządzeń z aplikacją Microsoft Teams
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
ms.assetid: 917b3e1d-203e-4439-8539-634e80196687
description: Uzyskaj szczegółowe informacje na temat Microsoft Teams używanych w organizacji, korzystając z raportu Microsoft Teams użycia aplikacji z raportów Microsoft 365.
ms.openlocfilehash: c1c1440b1dfca30cddea0dea44e82a9e86b0d622
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989641"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-device-usage"></a>Microsoft 365 w centrum administracyjnym — informacje o Microsoft Teams urządzeniach

Pulpit Microsoft 365 pulpitu nawigacyjnego Raporty zawiera informacje o aktywności dotyczącej wszystkich produktów w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). Raport dotyczący użycia aplikacji Microsoft Teams pozwala uzyskać szczegółowe informacje o aplikacjach Microsoft Teams używanych w organizacji.
 
## <a name="how-to-get-to-the-microsoft-teams-app-usage-report"></a>Jak przejść do raportu użycia aplikacji Microsoft Teams

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.

    
2. Z listy **rozwijanej Wybierz raport** **wybierz pozycję** \> Microsoft Teams **Użycie urządzenia**.
  
## <a name="interpret-the-microsoft-teams-app-usage-report"></a>Interpretowanie raportu użycia aplikacji Microsoft Teams

Wgląd w użycie aplikacji Microsoft Teams możesz uzyskać, patrząc na wykresy **Użytkownicy** i **Dystrybucja**. 
  
![Microsoft 365 raporty — Microsoft Teams użycia aplikacji.](../../media/de35c4de-76b4-4109-a806-66774665499b.png)
  
|Element|Opis|
|:-----|:-----|
|1.  <br/> |W raporcie **Użycie urządzeń z aplikacją Microsoft Teams** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela (7) będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).  <br/> |
|2.  <br/> |Dane w poszczególnych raportach zazwyczaj obejmują od 24 do 48 godzin.  <br/> |
|3.  <br/> |W widoku **Użytkownicy** można sprawdzić dzienną liczbę unikatowych użytkowników według aplikacji.  <br/> |
|4.  <br/> |W widoku **Rozkład** można sprawdzić liczbę unikatowych użytkowników według aplikacji w wybranym okresie.  <br/> |
|5.  <br/> | Na wykresie **Użytkownicy** oś Y przedstawia liczbę użytkowników według aplikacji.  <br/>  Na wykresie **Rozkład** oś Y przedstawia liczbę użytkowników korzystających z określonej aplikacji.  <br/>  Oś X na wykresach przedstawia wybrany w danym raporcie przedział czasu.  <br/> |
|6.  <br/> |Serie, które są na wykresie, można filtrować, zaznaczając je w legendzie. Na przykład na wykresie Użytkownicy  wybierz pozycję **Windows,** **Mac****, Połączenia**, **Sieć Web**, Telefon **z systemem Android** lub telefon Windows, aby wyświetlić tylko informacje dotyczące poszczególnych z nich. Zmiana ta nie ma wpływu na informacje w siatce tabeli.  <br/> ![Wykresy użycia Microsoft Teams aplikacji można filtrować, wybierając typ aplikacji.](../../media/64ee1cb1-ca80-4964-8234-7fc671135c3d.png)|
|7.  <br/> | Lista wyświetlanych grup jest ustalana na podstawie zbioru wszystkich grup, które istniały (nie zostały usunięte) w najdłuższym (180-dniowym) przedziale czasu raportowania. Liczba działań zależy od wybranego przedziału dat.  <br/> UWAGA: Możesz nie widzieć wszystkich elementów na poniższej liście w kolumnach, dopóki ich nie dodasz.<br/> **Nazwa użytkownika** to adres e-mail użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe.  <br/> **Data ostatniego działania (UTC)** odwołuje się do ostatniej daty, kiedy użytkownik uczestniczył w działaniu w aplikacji Microsoft Teams.  <br/> **Usunięte** wskazuje, czy zespół został usunięty. Jeśli zespół został usunięty, ale w okresie raportowania nastąpiła w nim aktywność, grupa ta pojawi się na siatce z parametrem Usunięte ustawionym na wartość Prawda.  <br/> **Data usunięcia** to data usunięcia zespołu.  <br/> Pole wyboru **Windows** jest zaznaczone, jeśli w danym okresie użytkownik korzystał z aplikacji dla systemu Windows.  <br/> Pole wyboru **Mac** jest zaznaczone, jeśli w danym okresie użytkownik korzystał z aplikacji dla komputerów Mac.  <br/> Pole wyboru **Sieć Web** jest zaznaczone, jeśli w danym okresie użytkownik korzystał z aplikacji sieci Web.  <br/> Pole wyboru **iOS** jest zaznaczone, jeśli w danym okresie użytkownik korzystał z aplikacji dla systemu iOS.  <br/> Pole wyboru **Telefon z systemem Android** jest zaznaczone, jeśli w danym okresie użytkownik korzystał z aplikacji dla telefonu z systemem Android.  <br/> Pole wyboru **Telefon z systemem Windows** jest zaznaczone, jeśli w danym okresie użytkownik korzystał z aplikacji dla telefonu z systemem Windows.  <br/>  Jeśli zasady organizacji nie pozwalają na wyświetlanie raportów zawierających identyfikowalne dane użytkowników, możesz zmienić ustawienie prywatności dla wszystkich tych raportów. Zobacz sekcję **Ukrywanie szczegółów na poziomie użytkownika w** sekcji [Raporty aktywności w centrum administracyjne platformy Microsoft 365](activity-reports.md).  <br/> |
|8.  <br/> |Wybierz **pozycję** Kolumny, aby dodać lub usunąć kolumny z raportu.  <br/> ![Teams raportu użycia aplikacji uapp — wybierz kolumny.](../../media/333f3077-696d-4829-b0a7-1046b3822222.png)|
|9.  <br/> |Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.  <br/> |
|||
   
  

