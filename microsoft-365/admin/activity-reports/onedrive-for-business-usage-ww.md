---
title: Microsoft 365 OneDrive dla Firm użycia
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
description: 'Uzyskaj raport OneDrive dla Firm użycia, aby uzyskać informacje o całkowitej liczbie plików i przestrzeni dyskowej używanych w organizacji. '
ms.openlocfilehash: d3b884f374cf3dde572bd67ad905fc308a1701d1
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400785"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Microsoft 365 raporty w centrum administracyjnym — informacje OneDrive dla Firm użycia

Pulpit Microsoft 365 pulpitu nawigacyjnego Raporty zawiera informacje o aktywności dotyczącej wszystkich produktów w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).
  
Na przykład karta OneDrive na pulpicie nawigacyjnym zapewnia ogólny widok wartości uzyskiwanych z usługi OneDrive dla Firm dotyczących łącznej liczby plików i ilości przestrzeni dyskowej używanych w organizacji. Następnie można przejść do szczegółów, aby zrozumieć trendy dotyczące aktywnych kont usługi OneDrive, liczby plików, z którymi pracują użytkownicy oraz użytej przestrzeni dyskowej. Ten widok zawiera również szczegółowe informacje o koncie usługi OneDrive każdego użytkownika.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Jak uzyskać dostęp do raportu OneDrive użycia?

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie OneDrive głównej.
  
## <a name="interpret-the-onedrive-usage-report"></a>Interpretowanie raportu użycia usługi OneDrive

Użycie możesz wyświetlić w raporcie OneDrive, wybierając **kartę** Użycie.<br/>![Microsoft 365 raporty — Microsoft OneDrive użycia.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

Wybierz **pozycję Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![OneDrive użycia — wybierz kolumny.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

W **OneDrive dla Firm użycia** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metryczny**|**Definicja**|
|ADRES URL  <br/> |Adres internetowy strony OneDrive. <br/> |
|Deleted  <br/> |Stan usunięcia OneDrive. Oznaczanie kont jako usunięte trwa co najmniej 7 dni.  <br/> |
|Właściciel  <br/> |Nazwa użytkownika administratora podstawowego OneDrive.   <br/> |
|Główna nazwa właściciela  <br/> |Adres e-mail właściciela OneDrive. <br/> |
|Data ostatniego działania (UTC)  <br/> | Najpóźniejsza data aktywności dotyczącej plików w OneDrive. Jeśli w usłudze OneDrive nie było aktywności dotyczących plików, pole wartości będzie puste.  <br/> |
|Pliki  <br/> |Liczba plików w OneDrive. <br/>|
|Aktywne pliki  <br/> | Liczba aktywnych plików w tym okresie.<br/> UWAGA: Jeśli pliki zostały usunięte w przedziale czasu określonym dla raportu, liczba aktywnych plików wyświetlana w raporcie może być większa niż bieżąca liczba plików w OneDrive. >  Usunięci użytkownicy będą pokazywani w raportach przez 180 dni.  <br/> |
|Storage (MB)  <br/> |Ilość miejsca do magazynowania używanego OneDrive MB. |
|||
   
> [!NOTE]
> Raport obejmuje tylko użytkowników, którzy mają ważne OneDrive dla Firm licencji.
