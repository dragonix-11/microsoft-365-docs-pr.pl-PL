---
title: Microsoft 365 w centrum administracyjnym — aktywność OneDrive dla Firm użytkowników
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
description: Uzyskaj OneDrive użycia dla organizacji i poznaj aktywność każdego użytkownika OneDrive, liczbę udostępnionych plików i użycie magazynu.
ms.openlocfilehash: 8cfd6dfbcff15c118f9ad54ef29e5cec6cf4d6bf
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989638"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Microsoft 365 w centrum administracyjnym — aktywność OneDrive dla Firm użytkowników

Pulpit Microsoft 365 pulpitu nawigacyjnego Raporty zawiera informacje o aktywności dotyczącej wszystkich produktów w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).
  
Możesz na przykład zrozumieć działania wszystkich użytkowników z licencjami na używanie usługi OneDrive przez wyświetlanie ich interakcji z plikami w usłudze OneDrive. Ułatwia to także zrozumienie poziomu współpracy dzięki wyświetlaniu liczby udostępnionych plików.

## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Jak przejść do raportu aktywności usługi OneDrive?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie OneDrive głównej.
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>Interpretowanie raportu aktywności usługi OneDrive dla Firm

Możesz wyświetlić działania w raporcie OneDrive, wybierając **kartę** Działanie.<br/>![Microsoft 365 raporty — Microsoft OneDrive aktywności.](../../media/c89df0b0-2611-4acf-9ef7-17cedf7977be.png)

Wybierz **pozycję Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![OneDrive aktywności — wybierz kolumny.](../../media/252f311f-ffde-4e5a-9158-2b822bf86964.png)

Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.

W raporcie **Aktywność usługi OneDrive dla Firm** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metryczny**|**Definicja**|
|Nazwa użytkownika  <br/> |Nazwa użytkownika właściciela konta OneDrive konta.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Najpóźniejsza data aktywności dotyczącej plików na OneDrive w wybranym zakresie dat. . Aby zobaczyć działanie, które wystąpiło w konkretnym dniu, wybierz datę bezpośrednio na wykresie.  <br/> |
|Pliki przeglądane lub edytowane  <br/> |Liczba plików, które zostały przekazane, pobrane, zmodyfikowane lub wyświetlone.   <br/> |
|Pliki zsynchronizowane  <br/> |Liczba plików, które zostały zsynchronizowane z lokalnym urządzeniem użytkownika z kontem OneDrive konta. <br/> |
|Pliki udostępnione wewnętrznie  <br/> | Liczba plików, które zostały udostępnione użytkownikom w organizacji lub użytkownikom w grupach (mogą to być użytkownicy zewnętrzni).  <br/> |
|Pliki udostępniane zewnętrznie  <br/> |Liczba plików, które zostały udostępnione użytkownikom spoza organizacji. <br/>|
|Deleted  <br/> | Oznacza to, że licencja użytkownika została usunięta.  <br/> UWAGA: Działania usuniętego użytkownika nadal będą wyświetlane w raporcie, o ile usunięty użytkownik był licencjonowany w pewnym momencie w wybranym okresie. Kolumna **Usunięte** pozwala łatwo zauważyć użytkowników, którzy od dłuższego czasu nie byli aktywni, ale jednak ich dane zostały uwzględnione w raporcie.  <br/> |
|Data usunięcia  <br/> |Data usunięcia licencji użytkownika. <br/>|
|Przypisany produkt  <br/> |Użytkownik Microsoft 365 produktów licencjonowanych na użytkownika.|
|||