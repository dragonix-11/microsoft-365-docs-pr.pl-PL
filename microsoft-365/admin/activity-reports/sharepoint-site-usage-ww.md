---
title: Microsoft 365 raporty w centrum administracyjnym — informacje SharePoint użycia witryny
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
description: Pobierz raport SharePoint witryny, aby dowiedzieć się, ile plików użytkowników przechowuje w witrynach SharePoint, ile jest aktywnie używanych i ile miejsca do magazynowania jest używane.
ms.openlocfilehash: 2c29234df1076fa31ea836b7ead51234e121004e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989512"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Microsoft 365 raporty w centrum administracyjnym — informacje SharePoint użycia witryny

Jako administrator Microsoft 365 nawigacyjny Raporty możesz wyświetlać informacje o aktywności dotyczące różnych produktów w organizacji. Umożliwia on przejście do bardziej szczegółowych informacji o aktywności specyficznej dla poszczególnych produktów. Możesz na przykład uzyskać widok wysokiego poziomu wartości z usługi SharePoint, czyli łącznej liczby plików, które użytkownicy przechowują w witrynach programu SharePoint, liczby aktywnie używanych plików i ilości miejsca do magazynowania używanego we wszystkich tych witrynach. Następnie możesz przejść do szczegółowego raportu dotyczącego użycia witryny programu SharePoint, aby zrozumieć trendy i szczegóły na poziomie witryny dla wszystkich witryn. 

## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Jak wyświetlić raport dotyczący użycia witryny programu SharePoint

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na SharePoint głównej.

## <a name="show-user-details-in-the-reports"></a>Pokazywanie szczegółów użytkowników w raportach

Raporty zawierają informacje na temat danych dotyczących użycia w organizacji. Domyślnie w raportach są wyświetlane informacje umożliwiające identyfikację nazw użytkowników, grup i witryn. Począwszy od 1 września 2021 r., wszystkie raporty domyślnie ukrywają informacje o użytkownikach w ramach naszego bieżącego zobowiązania do pomagania firmom w ochronie prywatności w ich lokalnych działaniach.
  
Lista użytkowników będzie wyglądać tak:
  
![Raporty — lista zanonimizowanych użytkowników.](../../media/2ed99bce-4978-4ee3-9ea2-4a8db26eef02.png)
  
Administratorzy globalni mogą przywrócić tę zmianę w dzierżawie i pokazać identyfikowalne dane użytkowników, jeśli pozwalają na to zasady zachowania poufności informacji ich organizacji. Można to osiągnąć w centrum administracyjne platformy Microsoft 365, korzystając z następujących kroków:
  
1. W centrum administracyjnym przejdź do strony centrum **Ustawienia** \> **organizacji Ustawienia** \> **usługi.**

2. Wybierz pozycję **Raporty**. 
  
3. Usuń zaznaczenie instrukcji **We wszystkich raportach wyświetl odznaczone nazwy użytkowników, grup** i witryn, a następnie zapisz zmiany. 
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Interpretowanie raportu SharePoint użycia witryny

Użycie witryny możesz wyświetlić w raporcie SharePoint, wybierając **kartę Użycie** witryny.

:::image type="content" alt-text="Microsoft 365 raporty — Raport SharePoint użycia witryny firmy Microsoft." source="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png" lightbox="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png":::

Wybierz **pozycję Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.

:::image type="content" alt-text="SharePoint użycia witryny — wybierz kolumny." source="../../media/71ac3195-c494-40c1-9346-a858125ef6df.png":::

Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

W **SharePoint użycia** witryny można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu).
  
|Metryczny|Opis|
|:-----|:-----|
|Adres URL witryny  |Pełny adres URL witryny. |
|Deleted  |Stan usunięcia witryny. Oznaczanie witryn jako usunięte trwa co najmniej 7 dni.  |
|Właściciel witryny  |Nazwa użytkownika podstawowego właściciela witryny.   |
|Główna nazwa właściciela witryny  |Adres e-mail właściciela witryny. |
|Data ostatniego działania (UTC)  | Data wykrycia ostatniego działania na plikach lub wyświetlenia strony w witrynie.  |
|Identyfikator etykiety wrażliwości witryny  | Etykieta wrażliwości w witrynie.  |
|Udostępnianie zewnętrzne  | Ustawienia zewnętrzne służące do współuzywniania w witrynie.  |
|Zasady dotyczące urządzeń niezamanektowych  | Zasady dostępu do witryny dla urządzeń niezawiązyanych.  |
|Lokalizacja geograficzna  | Lokalizacja geograficzna witryny.  |
|Pliki  |Liczba plików w witrynie. |
|Aktywne pliki  | Liczba aktywnych plików w witrynie.<br/> UWAGA: Jeśli pliki zostały usunięte w przedziale czasu określonym dla raportu, liczba aktywnych plików wyświetlana w raporcie może być większa niż bieżąca liczba plików w witrynie.  |
|Storage (MB)  |Ilość miejsca do magazynowania używanego w witrynie.  |
|Storage przydzielone (MB)  |Maksymalna ilość miejsca do magazynowania przydzielonego dla witryny.  |
|Widoki stron  |Liczba wyświetlń stron w witrynie.  |
|Odwiedzone strony  |Liczba unikatowych stron odwiedzone w witrynie.  |
|Liczba linków anonimowych  |Liczba współużytkowanych dokumentów lub folderów za pomocą funkcji "Każda osoba z linkiem" w witrynie.  |
|Liczba łączy firmy  |Liczba współużytkowanych dokumentów lub folderów za pomocą linku "Osoby z organizacji z linkiem" w witrynie.  |
|Bezpieczny link do licznika gości  |Liczba współużytkowanych dokumentów lub folderów przy użyciu "określonych osób" w witrynie.  |
|Bezpieczny link do liczby członków  |Liczba współużytkowanych dokumentów lub folderów przy użyciu "określonych osób" w witrynie.  |
|Główny szablon sieci Web  |Szablon użyty do utworzenia witryny.  <br/> UWAGA: Jeśli chcesz filtrować dane według różnych typów witryn, wyeksportuj dane i użyj kolumny Główny szablon sieci Web. |

