---
title: raporty aktywności Microsoft 365 OneDrive dla Firm
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
description: Pobierz raport użycia OneDrive dla organizacji i poznaj aktywność każdego użytkownika OneDrive, liczbę udostępnionych plików i wykorzystanie magazynu.
ms.openlocfilehash: 48edb30eae60f6e7dcac5bc63dc9676dc27e0a90
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781594"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Microsoft 365 Raporty w centrum administracyjnym — działanie OneDrive dla Firm

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).
  
Możesz na przykład zrozumieć działania wszystkich użytkowników z licencjami na używanie usługi OneDrive przez wyświetlanie ich interakcji z plikami w usłudze OneDrive. Ułatwia to także zrozumienie poziomu współpracy dzięki wyświetlaniu liczby udostępnionych plików.

## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Jak przejść do raportu aktywności usługi OneDrive?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie OneDrive.
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>Interpretowanie raportu aktywności usługi OneDrive dla Firm

Możesz wyświetlić działania w raporcie OneDrive, wybierając kartę **Działanie**.<br/>![raporty Microsoft 365 — raport aktywności Microsoft OneDrive.](../../media/c89df0b0-2611-4acf-9ef7-17cedf7977be.png)

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![OneDrive raport aktywności — wybierz kolumny.](../../media/252f311f-ffde-4e5a-9158-2b822bf86964.png)

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.

W raporcie **Aktywność usługi OneDrive dla Firm** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Nazwa użytkownika  <br/> |Nazwa użytkownika właściciela konta OneDrive.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Ostatnia data wykonania działania pliku na koncie OneDrive dla wybranego zakresu dat. . Aby zobaczyć działanie, które wystąpiło w konkretnym dniu, wybierz datę bezpośrednio na wykresie.  <br/> |
|Pliki wyświetlane lub edytowane  <br/> |Liczba plików przekazanych, pobranych, zmodyfikowanych lub wyświetlonych przez użytkownika.   <br/> |
|Zsynchronizowane pliki  <br/> |Liczba plików, które zostały zsynchronizowane z urządzenia lokalnego użytkownika z kontem OneDrive. <br/> |
|Pliki udostępnione wewnętrznie  <br/> | Liczba plików, które zostały udostępnione użytkownikom w organizacji lub użytkownikom w grupach (które mogą obejmować użytkowników zewnętrznych).  <br/> |
|Pliki udostępnione zewnętrznie  <br/> |Liczba plików, które zostały udostępnione użytkownikom spoza organizacji. <br/>|
|Deleted  <br/> | Oznacza to, że licencja użytkownika została usunięta.  <br/> UWAGA: Działanie dla usuniętego użytkownika będzie nadal wyświetlane w raporcie, o ile w wybranym okresie licencja została licencjonowana. Kolumna **Usunięte** pozwala łatwo zauważyć użytkowników, którzy od dłuższego czasu nie byli aktywni, ale jednak ich dane zostały uwzględnione w raporcie.  <br/> |
|Data usunięcia  <br/> |Data usunięcia licencji użytkownika. <br/>|
|Przypisany produkt  <br/> |Microsoft 365 produkty, które są licencjonowane dla użytkownika.|
|||