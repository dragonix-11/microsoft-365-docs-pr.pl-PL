---
title: Centrum administracyjne platformy Microsoft 365 SharePoint raporty użycia witryny
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
description: Pobierz raport użycia witryny SharePoint, aby dowiedzieć się, ile plików użytkownicy przechowują w witrynach SharePoint, ile z nich jest aktywnie używanych, oraz ile z nich jest używanych.
ms.openlocfilehash: a99884863db3ffc1f2577358abef6d287d01e2d1
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2022
ms.locfileid: "64846998"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Microsoft 365 raporty w centrum administracyjnym — użycie witryny SharePoint

Jako administrator Microsoft 365 pulpit nawigacyjny Raporty przedstawia omówienie działań w różnych produktach w organizacji. Umożliwia on przejście do bardziej szczegółowych informacji o aktywności specyficznej dla poszczególnych produktów. Można na przykład uzyskać ogólny widok wartości uzyskiwanej z SharePoint pod względem całkowitej liczby plików przechowywanych przez użytkowników w witrynach SharePoint, liczby aktywnie używanych plików i magazynu używanego we wszystkich tych witrynach. Następnie możesz przejść do szczegółowego raportu dotyczącego użycia witryny programu SharePoint, aby zrozumieć trendy i szczegóły na poziomie witryny dla wszystkich witryn. 

## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Jak wyświetlić raport dotyczący użycia witryny programu SharePoint

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie SharePoint.

## <a name="show-user-details-in-the-reports"></a>Pokazywanie szczegółów użytkowników w raportach

Raporty zawierają informacje o danych użycia organizacji. Domyślnie raporty wyświetlają informacje o identyfikowalnych nazwach użytkowników, grup i witryn. Od 1 września 2021 r. domyślnie ukrywamy informacje o użytkownikach dla wszystkich raportów w ramach naszego stałego zobowiązania, aby pomóc firmom w obsłudze lokalnych przepisów dotyczących prywatności.
  
Lista użytkowników będzie wyglądać tak:
  
![Raporty — lista zanonimizowanych użytkowników.](../../media/2ed99bce-4978-4ee3-9ea2-4a8db26eef02.png)
  
Administratorzy globalni mogą cofnąć tę zmianę dla swojej dzierżawy i wyświetlać identyfikowalne informacje o użytkownikach, jeśli zezwalają na to ich praktyki ochrony prywatności w organizacji. Można to osiągnąć w centrum administracyjnym platformy Microsoft 365, wykonując następujące kroki:
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> **Ustawienia organizacji** \> **Usługi**.

2. Wybierz pozycję **Raporty**. 
  
3. Usuń zaznaczenie instrukcji **We wszystkich raportach wyświetl zdeidentyfikowane nazwy użytkowników, grup i witryn,** a następnie zapisz zmiany. 
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Interpretowanie raportu użycia witryny SharePoint

Użycie witryny można wyświetlić w raporcie SharePoint, wybierając kartę **Użycie witryny**.

:::image type="content" alt-text="raporty Microsoft 365 — raport użycia witryny firmy Microsoft SharePoint." source="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png" lightbox="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png":::

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.

:::image type="content" alt-text="SharePoint raport użycia witryny — wybierz kolumny." source="../../media/71ac3195-c494-40c1-9346-a858125ef6df.png":::

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

Raport **użycia witryny SharePoint** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).
  
|Metrycznych|Opis|
|:-----|:-----|
|Adres URL witryny  |Pełny adres URL witryny. |
|Deleted  |Stan usunięcia witryny. Oznaczanie witryn jako usunięte trwa co najmniej 7 dni.  |
|Właściciel witryny  |Nazwa użytkownika głównego właściciela witryny.   |
|Główna nazwa właściciela witryny  |Adres e-mail właściciela witryny. |
|Data ostatniego działania (UTC)  | Data ostatniego wykrycia działania pliku lub wyświetlenia strony w witrynie.  |
|Identyfikator etykiety poufności witryny  | Etykieta poufności w witrynie.  |
|Udostępnianie zewnętrzne  | Wartość ustawienia udostępniania zewnętrznego dla witryny. Ta wartość nie odzwierciedla zmian w skutecznym ustawieniu wprowadzonym przez etykiety poufności witryny. Jeśli używasz etykiet poufności, użyj [raportów ładu dostępu do danych](/sharepoint/data-access-governance-reports) , aby uzyskać prawidłowe wartości.|
|Zasady urządzeń niezarządzanych  | Zasady dostępu do witryny dla urządzeń niezarządzanych.  |
|Lokalizacja geograficzna  | Lokalizacja geograficzna lokacji.  |
|Pliki  |Liczba plików w witrynie. |
|Aktywne pliki  | Liczba aktywnych plików w witrynie. Plik jest uznawany za aktywny, jeśli został zapisany, zsynchronizowany, zmodyfikowany lub udostępniony w określonym przedziale czasu.<br/> UWAGA: Jeśli pliki zostały usunięte w określonym okresie dla raportu, liczba aktywnych plików wyświetlanych w raporcie może być większa niż bieżąca liczba plików w witrynie.  |
|Storage używane (MB)  |Ilość magazynu aktualnie używanego w lokacji.  |
|Storage przydzielone (MB)  |Maksymalna ilość miejsca do magazynowania przydzielonego dla lokacji.  |
|Widoki strony  |Liczba wyświetleń stron w witrynie.  |
|Odwiedzone strony  |Liczba unikatowych stron, które zostały odwiedzone w witrynie.  |
|Liczba łączy anonimowych  |Ile razy dokumenty lub foldery są udostępniane przy użyciu opcji "Każdy, kto ma link" w witrynie.  |
|Liczba linków firmowych  |Ile razy dokumenty lub foldery są udostępniane przy użyciu "Osoby w organizacji z linkiem" w witrynie.  |
|Bezpieczny link dla liczby gości  |Ile razy dokumenty lub foldery są udostępniane przy użyciu "określonych osób" w witrynie.  |
|Bezpieczny link dla liczby elementów członkowskich  |Ile razy dokumenty lub foldery są udostępniane przy użyciu "określonych osób" w witrynie.  |
|Główny szablon sieci Web  |Szablon używany do tworzenia witryny.  <br/> UWAGA: Jeśli chcesz filtrować dane według różnych typów witryn, wyeksportuj dane i użyj kolumny Główny szablon sieci Web. |

