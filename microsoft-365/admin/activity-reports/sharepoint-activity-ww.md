---
title: raporty aktywności Centrum administracyjne platformy Microsoft 365 SharePoint
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
description: Uzyskaj raport użycia aktywności SharePoint, aby dowiedzieć się więcej o aktywności każdego użytkownika SharePoint, liczbie udostępnionych plików i wykorzystaniu magazynu.
ms.openlocfilehash: 939dcf5c81d68a7a399c725d44687423670ed65a
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781565"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-activity"></a>Microsoft 365 Raporty w centrum administracyjnym — działanie SharePoint

Jako administrator Microsoft 365 pulpit nawigacyjny Raporty przedstawia omówienie działań w różnych produktach w organizacji. Umożliwia on przejście do bardziej szczegółowych informacji o aktywności specyficznej dla poszczególnych produktów. Zapoznaj się z [raportami aktywności w Centrum administracyjne platformy Microsoft 365](activity-reports.md).
  
Możesz na przykład zrozumieć działanie każdego użytkownika mającego licencję na używanie programu SharePoint poprzez wyświetlenie jego interakcji z plikami. Ułatwia to także zrozumienie poziomu współpracy przez wyświetlanie liczby udostępnionych plików.
  
## <a name="how-do-i-get-to-the-to-the-sharepoint-activity-report"></a>Jak dotrzeć do raportu aktywności programu SharePoint?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie SharePoint.
  
## <a name="interpret-the-sharepoint-activity-report"></a>Interpretowanie raportu aktywności SharePoint

Możesz wyświetlić działania w raporcie SharePoint, wybierając kartę **Działanie**.<br/>![raporty Microsoft 365 — raport aktywności SharePoint firmy Microsoft.](../../media/5a0a96f-0e4f-4fb9-8baa-3262275b3d1f.png)

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![SharePoint raportu aktywności — wybierz kolumny.](../../media/3c396cd1-9701-4712-8eaa-eb7bba702aa8.png)

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

Raport **aktywności SharePoint** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Nazwa użytkownika  <br/> |Adres e-mail użytkownika, który wykonał działanie w witrynie SharePoint.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Ostatnia data wykonania działania pliku lub odwiedzin strony dla wybranego zakresu dat. Aby zobaczyć działanie, które wystąpiło w konkretnym dniu, wybierz datę bezpośrednio na wykresie.  <br/> |
|Pliki wyświetlane lub edytowane  <br/> |Liczba plików przekazanych, pobranych, zmodyfikowanych lub wyświetlonych przez użytkownika.   <br/> |
|Zsynchronizowane pliki  <br/> |Liczba plików, które zostały zsynchronizowane z urządzenia lokalnego użytkownika z witryną SharePoint. <br/> |
|Pliki udostępnione wewnętrznie  <br/> | Liczba plików udostępnionych użytkownikom w organizacji lub użytkownikom w grupach (które mogą obejmować użytkowników zewnętrznych).  <br/> |
|Pliki udostępnione zewnętrznie  <br/> |Liczba plików, które zostały udostępnione użytkownikom spoza organizacji. <br/>|
|Odwiedzone strony  <br/> |Odwiedziny na unikatowych stronach przez użytkownika. <br/>|
|Deleted  <br/> | Oznacza to, że licencja użytkownika została usunięta.  <br/>  **UWAGA:** Aktywność usuniętego użytkownika będzie nadal wyświetlana w raporcie tak długo, jak długo będzie on licencjonowany w wybranym okresie. Kolumna Usunięte pozwala łatwo zauważyć użytkowników, którzy od dłuższego czasu nie byli aktywni, ale jednak ich dane zostały uwzględnione w raporcie.  <br/> |
|Data usunięcia  <br/> |Data usunięcia licencji użytkownika. <br/>|
|Przypisany produkt  <br/> |Microsoft 365 produkty, które są licencjonowane dla użytkownika.|
|||