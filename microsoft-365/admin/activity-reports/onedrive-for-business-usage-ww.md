---
title: Microsoft 365 OneDrive dla Firm raporty użycia
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Uzyskaj raport użycia OneDrive dla Firm, aby dowiedzieć się więcej o całkowitej liczbie plików i magazynu używanych w całej organizacji.
ms.openlocfilehash: d195a521fba9dc82867821e27414d125dca09c61
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467279"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Microsoft 365 Raporty w centrum administracyjnym — użycie OneDrive dla Firm

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).
  
Na przykład karta OneDrive na pulpicie nawigacyjnym zapewnia ogólny widok wartości uzyskiwanych z usługi OneDrive dla Firm dotyczących łącznej liczby plików i ilości przestrzeni dyskowej używanych w organizacji. Następnie można przejść do szczegółów, aby zrozumieć trendy dotyczące aktywnych kont usługi OneDrive, liczby plików, z którymi pracują użytkownicy oraz użytej przestrzeni dyskowej. Ten widok zawiera również szczegółowe informacje o koncie usługi OneDrive każdego użytkownika.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Jak mogę przejść do raportu użycia OneDrive?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie OneDrive.
  
## <a name="interpret-the-onedrive-usage-report"></a>Interpretowanie raportu użycia usługi OneDrive

Możesz wyświetlić użycie w raporcie OneDrive, wybierając kartę **Użycie**.<br/>![raporty Microsoft 365 — raport użycia Microsoft OneDrive.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![OneDrive raportu użycia — wybierz kolumny.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

Raport **użycia OneDrive dla Firm** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|ADRES URL  <br/> |Adres internetowy OneDrive użytkownika. <br/> |
|Deleted  <br/> |Stan usunięcia OneDrive. Oznaczanie kont jako usunięte trwa co najmniej 7 dni.  <br/> |
|Właściciel  <br/> |Nazwa użytkownika administratora podstawowego OneDrive.   <br/> |
|Główna nazwa właściciela  <br/> |Adres e-mail właściciela OneDrive. <br/> |
|Data ostatniego działania (UTC)  <br/> | Ostatnia data wykonania działania pliku w OneDrive. Jeśli w usłudze OneDrive nie było aktywności dotyczących plików, pole wartości będzie puste.  <br/> |
|Pliki  <br/> |Liczba plików w OneDrive. <br/>|
|Aktywne pliki  <br/> | Liczba aktywnych plików w okresie.<br/> UWAGA: Jeśli pliki zostały usunięte w określonym okresie dla raportu, liczba aktywnych plików wyświetlanych w raporcie może być większa niż bieżąca liczba plików w OneDrive. >  Usunięci użytkownicy będą pokazywani w raportach przez 180 dni.  <br/> |
|Storage używane (MB)  <br/> |Ilość magazynu używanego przez OneDrive w MB. |
|||
   
> [!NOTE]
> Raport zawiera tylko użytkowników, którzy mają ważną licencję OneDrive dla Firm.
