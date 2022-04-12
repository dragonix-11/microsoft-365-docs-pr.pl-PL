---
title: Centrum administracyjne platformy Microsoft 365 Teams raporty aktywności użytkowników
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
description: Dowiedz się, jak uzyskać raport aktywności Microsoft Teams użytkownika i uzyskać wgląd w działania Teams w organizacji.
ms.openlocfilehash: a5261261a1a1cb7b2039b646c3dbbd92c5f43688
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781660"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Microsoft 365 Raporty w centrum administracyjnym — działanie Microsoft Teams użytkownika

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). Raport dotyczący aktywności użytkowników aplikacji Microsoft Teams pozwala uzyskać szczegółowe informacje o aktywności związanej z aplikacją Microsoft Teams w organizacji.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Jak przejść do raportu aktywności użytkowników aplikacji Microsoft Teams

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie aktywności Microsoft Teams.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpretowanie raportu aktywności użytkowników aplikacji Microsoft Teams

Możesz wyświetlić działanie użytkownika w raporcie Teams, wybierając kartę **Aktywność użytkownika**. <br/>![Microsoft 365 raporty — Microsoft Teams aktywności użytkowników.](../../media/user-activity-charts.png)

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Teams raport aktywności użytkownika — wybierz kolumny.](../../media/user-activity-columns.png)

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. Wyeksportowany format **czasu audio**, **czasu wideo** i **czasu udostępniania ekranu** jest zgodny z formatem czasu trwania ISO8601.

W raporcie **Aktywność użytkowników aplikacji Microsoft Teams** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).

Aby zapewnić jakość danych, przeprowadzamy codzienne sprawdzanie poprawności danych w ciągu ostatnich trzech dni i będziemy wypełniać wszelkie wykryte luki. Podczas tego procesu można zauważyć różnice w danych historycznych.

|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Nazwa użytkownika  <br/> |Adres e-mail użytkownika. W tym polu może być wyświetlany rzeczywisty adres e-mail lub można ustawić je jako anonimowe.   <br/> |
|Nazwa dzierżawy  <br/> |Nazwa dzierżawy wewnętrznej lub zewnętrznej, do której należy użytkownik.   <br/> <br/> Jeśli użytkownik należy do dzierżawy zewnętrznej, odpowiednie metryki danych (na przykład komunikaty, wiadomości odpowiedzi itp.) są obliczane na podstawie interakcji w udostępnionych kanałach dzierżawy administratora. Interakcje wykonywane przez użytkownika we własnej dzierżawie (poza kanałami udostępnionymi danej dzierżawy) nie są uwzględniane w raporcie użycia administratora danej dzierżawy.  |
|Nazwy dzierżawy kanału udostępnionego   <br/> |Nazwy wewnętrznych lub zewnętrznych dzierżaw udostępnionych kanałów, w których uczestniczył użytkownik.   <br/> |
|Komunikaty kanału   <br/> |Liczba unikatowych komunikatów, które użytkownik zamieścił na czacie zespołowym w określonym okresie.  <br/> |
|Posty   <br/> |Liczba komunikatów pocztowych we wszystkich kanałach w określonym okresie <br/> |
|Odpowiedzi   <br/> |Liczba odpowiedzi we wszystkich kanałach w określonym okresie. <br/> |
|Pilne komunikaty    <br/> |Liczba pilnych komunikatów w określonym okresie. <br/> |
|Wiadomości na czacie   <br/> |Liczba unikatowych komunikatów, które użytkownik zamieścił na prywatnej czacie w określonym okresie.  <br/> |
|Łączna liczba spotkań   <br/> |Liczba spotkań online, w których użytkownik uczestniczył w określonym okresie.  <br/> |
|Połączenia 1:1   <br/> | Liczba wywołań 1:1, w których użytkownik uczestniczył w określonym okresie.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Ostatnia data udziału użytkownika w Microsoft Teams działaniu.<br/> |
|Spotkania uczestniczyły ad hoc   <br/> | Liczba spotkań ad hoc, w których uczestniczył użytkownik w określonym okresie.  <br/> |
|Spotkania zorganizowane ad hoc <br/> |Liczba spotkań ad hoc zorganizowanych przez użytkownika w określonym okresie. <br/>|
|Łączna liczba zorganizowanych spotkań  <br/> |Suma jednorazowych zaplanowanych, cyklicznych, ad hoc i niesklasyfikowanych spotkań zorganizowanych przez użytkownika w określonym okresie.  <br/> |
|Łączna liczba uczestników spotkań  <br/> |Suma jednorazowych zaplanowanych, cyklicznych, ad hoc i niesklasyfikowanych spotkań, w które uczestniczył użytkownik w określonym okresie.  <br/> |
|Spotkania zorganizowane jednorazowo  <br/> |Liczba zaplanowanych spotkań jednorazowych zorganizowanych przez użytkownika w określonym okresie.  <br/> |
|Zaplanowane spotkania zorganizowane cyklicznie  <br/> |Liczba cyklicznych spotkań zorganizowanych przez użytkownika w określonym okresie.  <br/> |
|Spotkania uczestniczyły w zaplanowanych jednorazowo spotkaniach  <br/> |Liczba zaplanowanych spotkań jednorazowych, w których uczestniczył użytkownik w określonym okresie.  <br/> |
|Spotkania uczestniczyły w zaplanowanych cyklicznych spotkaniach  <br/> |Liczba spotkań cyklicznych, w których uczestniczył użytkownik w określonym okresie.  <br/> |
|Licencja  <br/> |Wybrane, jeśli użytkownik ma licencję na korzystanie z Teams. <br/>|
|Inne działanie  <br/>|Użytkownik jest aktywny, ale wykonał inne działania niż uwidocznione typy akcji oferowane w raporcie (wysyłanie lub odpowiadanie na wiadomości kanałowe i wiadomości czatu, planowanie lub uczestnictwo w połączeniach i spotkaniach 1:1). Przykładowe akcje są następujące, gdy użytkownik zmienia stan Teams lub komunikat o stanie Teams lub otwiera wpis wiadomości kanału, ale nie odpowiada.  <br/>|
|Spotkania niesklasyfikowane <br/>|Ten, którego nie można sklasyfikować jako harmonogramu, cyklicznego lub ad hoc. Są one krótkie i w większości nie można ich zidentyfikować z powodu naruszonych informacji telemetrycznych. |

## <a name="make-the-user-specific-data-anonymous"></a>Anonimowość danych specyficznych dla użytkownika

Aby dane w Teams raport aktywności użytkownika były anonimowe, musisz być administratorem globalnym. Spowoduje to ukrycie możliwych do zidentyfikowania informacji (przy użyciu skrótów MD5), takich jak nazwa wyświetlana, adres e-mail i identyfikator obiektu Azure Active Directory w raporcie i ich eksport.

1. W Centrum administracyjne platformy Microsoft 365 przejdź do **Ustawienia Ustawienia** >  **Org**, a następnie w obszarze **Usługi** wybierz pozycję **Raporty**.

2. Wybierz pozycję **Raporty**, a następnie wybierz pozycję **Wyświetl identyfikatory anonimowe**. To ustawienie jest stosowane zarówno do raportów użycia w Centrum administracyjne platformy Microsoft 365, jak i w centrum administracyjnym Teams.

3. Wybierz pozycję **Zapisz zmiany**.


## <a name="see-also"></a>Zobacz też
[Microsoft Teams raport użycia urządzenia](../activity-reports/microsoft-teams-device-usage-preview.md)

[Microsoft Teams raport aktywności użycia](../activity-reports/microsoft-teams-usage-activity.md) 
