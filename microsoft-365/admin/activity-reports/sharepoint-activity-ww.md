---
title: Microsoft 365 raporty w centrum administracyjnym — aktywność SharePoint administracyjnej
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
description: Uzyskaj raport SharePoint aktywności, aby dowiedzieć się więcej o aktywności każdego SharePoint użytkownika, liczbie udostępnionych plików i użyciu magazynu.
ms.openlocfilehash: b130ad1cca6e25a939b942ed98910ba10150ab40
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989513"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-activity"></a>Microsoft 365 raporty w centrum administracyjnym — aktywność SharePoint administracyjnej

Jako administrator Microsoft 365 nawigacyjny Raporty możesz wyświetlać informacje o aktywności dotyczące różnych produktów w organizacji. Umożliwia on przejście do bardziej szczegółowych informacji o aktywności specyficznej dla poszczególnych produktów. Zapoznaj się z [raportami aktywności w centrum administracyjne platformy Microsoft 365](activity-reports.md).
  
Możesz na przykład zrozumieć działanie każdego użytkownika mającego licencję na używanie programu SharePoint poprzez wyświetlenie jego interakcji z plikami. Ułatwia to także zrozumienie poziomu współpracy przez wyświetlanie liczby udostępnionych plików.
  
## <a name="how-do-i-get-to-the-to-the-sharepoint-activity-report"></a>Jak dotrzeć do raportu aktywności programu SharePoint?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na SharePoint głównej.
  
## <a name="interpret-the-sharepoint-activity-report"></a>Interpretowanie SharePoint aktywności

Możesz wyświetlić działania w raporcie SharePoint, wybierając **kartę** Działanie.<br/>![Microsoft 365 raporty — raport aktywności SharePoint firmy Microsoft.](../../media/5a0a96f-0e4f-4fb9-8baa-3262275b3d1f.png)

Wybierz **pozycję Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![SharePoint aktywności — wybierz kolumny.](../../media/3c396cd1-9701-4712-8eaa-eb7bba702aa8.png)

Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

W **SharePoint aktywności** możesz przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metryczny**|**Definicja**|
|Nazwa użytkownika  <br/> |Adres e-mail użytkownika, który wykonał działanie w SharePoint sieci Web.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Najpóźniejsza data wykonania działania na plikach lub odwiedzono stronę w wybranym zakresie dat. Aby zobaczyć działanie, które wystąpiło w konkretnym dniu, wybierz datę bezpośrednio na wykresie.  <br/> |
|Pliki przeglądane lub edytowane  <br/> |Liczba plików, które zostały przekazane, pobrane, zmodyfikowane lub wyświetlone.   <br/> |
|Pliki zsynchronizowane  <br/> |Liczba plików, które zostały zsynchronizowane z lokalnym urządzeniem użytkownika z witryną SharePoint sieci Web. <br/> |
|Pliki udostępnione wewnętrznie  <br/> | Liczba plików, które zostały udostępnione użytkownikom w organizacji lub użytkownikom w grupach (mogą to być użytkownicy zewnętrzni).  <br/> |
|Pliki udostępniane zewnętrznie  <br/> |Liczba plików, które zostały udostępnione użytkownikom spoza organizacji. <br/>|
|Odwiedzone strony  <br/> |Odwiedziny unikatowych stron przez użytkownika. <br/>|
|Deleted  <br/> | Oznacza to, że licencja użytkownika została usunięta.  <br/>  **UWAGA:** Działania usuniętego użytkownika nadal będą wyświetlane w raporcie, jeśli usunięty użytkownik był licencjonowany w pewnym momencie w wybranym okresie. Kolumna Usunięte pozwala łatwo zauważyć użytkowników, którzy od dłuższego czasu nie byli aktywni, ale jednak ich dane zostały uwzględnione w raporcie.  <br/> |
|Data usunięcia  <br/> |Data usunięcia licencji użytkownika. <br/>|
|Przypisany produkt  <br/> |Użytkownik Microsoft 365 produktów licencjonowanych na użytkownika.|
|||