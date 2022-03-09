---
title: centrum administracyjne platformy Microsoft 365 Teams dotyczące aktywności użytkowników
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
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
description: Dowiedz się, jak uzyskać raport Microsoft Teams aktywności użytkowników i uzyskać szczegółowe informacje na temat Teams aktywności w organizacji.
ms.openlocfilehash: cfb503c09577d4538371ad6a5b35520d8da24bdb
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400842"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Microsoft 365 w centrum administracyjnym — aktywność Microsoft Teams użytkowników

Pulpit Microsoft 365 pulpitu nawigacyjnego Raporty zawiera informacje o aktywności dotyczącej wszystkich produktów w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). Raport dotyczący aktywności użytkowników aplikacji Microsoft Teams pozwala uzyskać szczegółowe informacje o aktywności związanej z aplikacją Microsoft Teams w organizacji.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Jak przejść do raportu aktywności użytkowników aplikacji Microsoft Teams

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na Microsoft Teams karcie aktywność.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpretowanie raportu aktywności użytkowników aplikacji Microsoft Teams

Możesz wyświetlić aktywność użytkowników w raporcie Teams, wybierając **kartę Aktywność** użytkownika. <br/>![Microsoft 365 raporty — Microsoft Teams aktywności użytkowników.](../../media/1011877f-3cf0-4417-9447-91d0b2312aab.png)

Wybierz **pozycję Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Teams aktywności użytkowników — wybierz kolumny.](../../media/6d3c013e-2c5e-4d66-bb41-998aa4bd1c20.png)

Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. Wyeksportowany format czasu **trwania dźwięku**, **czasu wideo** i udostępniania ekranu  jest zgodny z formatem czasu trwania ISO8601.

W raporcie **Aktywność użytkowników aplikacji Microsoft Teams** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).

Aby zapewnić jakość danych, przeprowadzamy codzienne testy sprawdzania poprawności danych z ostatnich trzech dni i zostaną wykryte wszelkie luki. W trakcie tego procesu możesz zauważyć różnice w danych historycznych.

|Element|Opis|
|:-----|:-----|
|**Metryczny**|**Definicja**|
|Nazwa użytkownika  <br/> |Adres e-mail użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe.   <br/> |
|Wiadomości kanałów   <br/> |Liczba unikatowych wiadomości opublikowanych przez użytkownika na czacie zespołu w określonym przedziale czasu.  <br/> |
|Wiadomości czatu   <br/> |Liczba unikatowych wiadomości opublikowanych przez użytkownika w czacie prywatnym w określonym przedziale czasowym.  <br/> |
|Łączna liczba spotkań   <br/> |Liczba spotkań online, w których uczestniczył użytkownik w określonym okresie.  <br/> |
|Rozmowy 1:1   <br/> | Liczba połączeń 1:1, w których uczestniczył użytkownik w określonym okresie.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Ostatnia data, gdy użytkownik uczestniczył w Microsoft Teams aktywności.<br/> |
|Spotkania, w których uczestniczyli ad hoc   <br/> | Liczba spotkań ad hoc, w których uczestniczył użytkownik w określonym przedziale czasu.  <br/> |
|Spotkania zorganizowane ad hoc <br/> |Liczba spotkań ad hoc zorganizowanych przez użytkownika w określonym przedziale czasu. <br/>|
|Łączna liczba zorganizowanych spotkań  <br/> |Suma spotkań zaplanowanych jednorazowo, cyklicznych, ad hoc i niesklasyfikowanych zorganizowanych przez użytkownika w określonym przedziale czasu.  <br/> |
|Łączna liczba spotkań, w których uczestniczyli  <br/> |Suma jednorazowych spotkań zaplanowanych, cyklicznych, ad hoc i niesklasyfikowanych, w których uczestniczył użytkownik w określonym okresie.  <br/> |
|Spotkania zorganizowane raz w harmonogramie  <br/> |Liczba spotkań planowanych jeden raz przez użytkownika w określonym przedziale czasu.  <br/> |
|Spotkania zorganizowane cyklicznie według harmonogramu  <br/> |Liczba spotkań cyklicznych zorganizowanych przez użytkownika w określonym przedziale czasu.  <br/> |
|Spotkania, w których wzięły udział spotkania zaplanowane jeden raz  <br/> |Liczba spotkań planowanych jeden raz, w których uczestniczył użytkownik w określonym okresie.  <br/> |
|Spotkania, w których uczestniczyli cyklicznie  <br/> |Liczba spotkań cyklicznych, w których uczestniczył użytkownik w określonym okresie.  <br/> |
|Ma licencję  <br/> |Zaznaczona, jeśli użytkownik ma licencję na używanie Teams. <br/>|
|Inna aktywność  <br/>|Użytkownik jest aktywny, ale wykonał inne działania niż udostępniane typy akcji oferowane w raporcie (wysyłanie lub odpowiadanie na wiadomości kanałów i wiadomości czatu, planowanie lub uczestniczenie w połączeniach i spotkaniach 1:1). Przykładowe akcje to zmiana statusu Teams lub statusu Teams lub otwarcie wpisu w wiadomości kanału, ale nie odpowiada.  <br/>|
|Niesklasyfikowane spotkania <br/>|Ten, który nie może być klasyfikowany jako harmonogram ani cykliczny ani ad hoc. Są to krótkie liczby, których na ogół nie można zidentyfikować z powodu informacji telemetrii, które zostały naruszone. |
|||
