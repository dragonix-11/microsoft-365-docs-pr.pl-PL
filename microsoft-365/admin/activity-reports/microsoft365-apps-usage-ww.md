---
title: centrum administracyjne platformy Microsoft 365 użycia aplikacji
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
- MET150
- MOE150
- GEA150
description: Dowiedz się, jak uzyskać raport Aplikacje Microsoft 365 użycia przy użyciu pulpitu nawigacyjnego Raporty Microsoft 365 w centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: c7a8e5bbf2fec8450b52b3cbe52e110d97061ed3
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400827"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-apps-usage"></a>Microsoft 365 raporty w centrum administracyjnym — informacje Aplikacje Microsoft 365 użycia

Pulpit Microsoft 365 pulpitu nawigacyjnego Raporty zawiera informacje o aktywności dotyczącej wszystkich produktów w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).

 Możesz na przykład zrozumieć działanie każdego użytkownika z licencją na używanie aplikacji Aplikacje Microsoft 365, patrząc na ich działanie w aplikacjach i sposób ich używania na różnych platformach.
 
 > [!NOTE]
 > Aktywacje na komputerze udostępnionym nie są uwzględniane w tym raporcie.

## <a name="how-to-get-to-the-microsoft-365-apps-usage-report"></a>Jak uzyskać dostęp do raportu Aplikacje Microsoft 365 użycia

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie Aktywni użytkownicy — Aplikacje Microsoft 365 stronie.

## <a name="interpret-the-microsoft-365-apps-usage-report"></a>Interpretowanie raportu Aplikacje Microsoft 365 użycia

Wykresy Użytkownicy i Platforma Aplikacje Microsoft 365 wyświetlić aktywność użytkowników **i platform.** 

> [!div class="mx-imgBorder"]
> ![Aplikacje Microsoft 365 raportu użycia.](../../media/0bcf67e6-a6e4-4109-a215-369f9f20ad84.png)

|Element|Opis|
 |:-----|:-----|
 |1. <br/> |W **Aplikacje Microsoft 365 użycia** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu). <br/> |
 |2. <br/> |Dane w poszczególnych raportach zazwyczaj obejmują okres ostatnich dwóch dni. Co sześć dni będziemy odświeżać raport drobnymi aktualizacjami, aby zapewnić jakość danych. <br/> |
 |3. <br/> |Widok **Użytkownicy** przedstawia trend liczby aktywnych użytkowników w poszczególnych aplikacjach — w usługach Outlook, Word, Excel, PowerPoint, OneNote i Teams. "Aktywni użytkownicy" to osoby, które wykonują jakiekolwiek celowe działania w tych aplikacjach. <br/> |
 |4. <br/> |Widok **Platformy** przedstawia trend aktywnych użytkowników na wszystkich platformach — na komputerach Windows, Mac, w sieci Web i na urządzeniach przenośnych. <br/> |
 |5.<br/>|Na wykresie **Użytkownicy** oś Y przedstawia liczbę unikatowych aktywnych użytkowników dla poszczególnych aplikacji. Na osi Y  **na platformiePlatformschart**  znajduje się liczba unikatowych użytkowników dla poszczególnych platform. Oś X na obu wykresach jest datą, w której aplikacja została użyta na danej platformie.<br/>|
 6.<br/>|Serie, które są na wykresie, można filtrować, zaznaczając je w legendzie. Na przykład na wykresie Użytkownicy  wybierz pozycję Outlook, Word, Excel, PowerPoint, OneDrive lub Teams, aby wyświetlić tylko informacje dotyczące każdego z nich. Zmiana tego wyboru nie spowoduje zmiany informacji w siatce tabeli poniżej.|
 |7.<br/>|W tabeli przedstawiono zestawienie danych na poziomie poszczególnych użytkowników. Możesz dodać lub usunąć kolumny z tabeli.  <br/><br/>**Nazwa** użytkownika to adres e-mail użytkownika, który wykonał działanie na Microsoft Apps.<br><br/>**Data ostatniej aktywacji (UTC)** to najpóźniejsza data aktywowania subskrypcji usługi Aplikacje Microsoft 365 na komputerze udostępnionym lub uruchomienia aplikacji przy użyciu swojego konta. <br/><br/>**Data ostatniego działania (UTC) to** najpóźniejsza data celowego działania użytkownika. Aby zobaczyć działanie, które wystąpiło w konkretnym dniu, wybierz datę bezpośrednio na wykresie.<br/><br/>Pozostałe kolumny identyfikują, czy użytkownik był aktywny na tej platformie dla tej aplikacji (w Aplikacje Microsoft 365) w wybranym okresie. |
 |8.<br/>|Wybierz **ikonę Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.|
 |9.<br/>|Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Umożliwia to wyeksportowanie danych wszystkich użytkowników oraz umożliwia proste agregacje, sortowanie i filtrowanie w celu dalszej analizy. Jeśli masz mniej niż 100 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 100 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.|
