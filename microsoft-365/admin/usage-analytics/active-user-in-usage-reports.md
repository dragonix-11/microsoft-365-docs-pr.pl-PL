---
title: Aktywny użytkownik w raportach Microsoft 365 użycia
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 093a6d0d-890b-489e-9f46-b15687d3fe4f
description: Dowiedz się więcej o aktywnym użytkowniku, który Microsoft 365 analizy użycia, raportów aktywności i metryk przyjęcia.
ms.openlocfilehash: 748bd08e08cc5e8243c3733c4b3f8448e15ab050
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "62973887"
---
# <a name="active-user-in-microsoft-365-usage-reports"></a>Aktywny użytkownik w raportach Microsoft 365 użycia

## <a name="active-user-in-usage-reports"></a>Aktywny użytkownik w raportach użycia

Aktywny użytkownik może Microsoft 365 [do analizy Microsoft 365](usage-analytics.md) użycia [oraz raportów aktywności](../activity-reports/activity-reports.md) w centrum administracyjnym w następujący sposób. 
  
|**Produkt**|**Definicja aktywnego użytkownika**|**Uwagi**|
|:-----|:-----|:-----|
|Exchange Online  <br/> |Każdy użytkownik, który wykonał dowolną z następujących czynności: Oznaczanie jako przeczytane, wysyłanie wiadomości, tworzenie terminów, wysyłanie próśb o spotkanie, akceptowanie (wstępnie) lub odrzucanie próśb o spotkanie, anulowanie spotkań.  <br/> |Nie są odzwierciedlane żadne informacje kalendarza. Zostaną one dodane w przyszłej aktualizacji.  <br/> |
|SharePoint Online  <br/> |Każdy użytkownik, który wchodził w interakcję z plikiem przez tworzenie, modyfikowanie, wyświetlanie, usuwanie, udostępnianie wewnętrznie lub zewnętrznie albo synchronizowanie z klientami w dowolnej witrynie lub wyświetlanie strony w dowolnej witrynie.  <br/> |Metryki aktywnego użytkownika dla usługi SharePoint Online w aplikacji szablonu analizy użycia usługi Microsoft 365 odzwierciedlają tylko użytkowników, którzy wywniosli aktywność na plikach w SharePoint witrynie zespołu lub witrynie grupy. Aplikacja szablonów zostanie zaktualizowana w celu zsynchronizowania definicji do takiej samej jak w raportach użycia w centrum administracyjnym.  <br/> |
|OneDrive dla Firm  <br/> |Każdy użytkownik, który wchodził w interakcję z plikiem przez tworzenie, modyfikowanie, wyświetlanie, usuwanie, udostępnianie wewnętrznie lub zewnętrznie albo synchronizowanie z klientami.  <br/> ||
|Yammer  <br/> |Każdy użytkownik, który odczytał, opublikował lub polubił wiadomość w usłudze Yammer.  <br/> ||
|Skype dla firm  <br/> |Każdy użytkownik, który uczestniczył w sesji równorzędnej (obejmującej wiadomości błyskawiczne, połączenia audio i wideo, udostępnianie aplikacji i transfery plików) lub zorganizował konferencję bądź uczestniczył w niej.  <br/> ||
|Office  <br/> |Każdy użytkownik, który aktywował swoją subskrypcję usługi Microsoft 365 Pro Plus, Visio Pro lub Project Pro na co najmniej jednym urządzeniu.  <br/> ||
|Microsoft 365 grupy  <br/> |Każdy członek grupy, dla którego wykryto aktywność skrzynki pocztowej (jeśli do grupy została wysłana wiadomość)  <br/> |Ta definicja zostanie rozszerzona o aktywność związaną z plikami witryny grupy i Yammer grupy (aktywność związana z plikami w witrynie grupy i wiadomość opublikowana w Yammer skojarzonej z grupą). Te dane nie są obecnie dostępne w aplikacji szablonów analizy Microsoft 365 użycia  <br/> |
|Microsoft Teams  <br/> |Każdy użytkownik, który uczestniczył w wiadomościach czatu, prywatnych wiadomościach czatu, połączeniach, spotkaniach lub innej aktywności. Inne działania są definiowane jako liczba innych działań zespołu przez użytkownika, z których niektóre to, a nie wyłącznie: oznaczanie wiadomości, aplikacji, praca nad plikami, wyszukiwanie, following teams and channel i przysyłanie ich.  <br/> ||
   
## <a name="adoption-metrics"></a>Metryki przyjęcia

[Microsoft 365 użycia zawierają](usage-analytics.md) więcej metryk przyjęcia związanych z aktywnymi użytkownikami w celu pokazania wdrożenia produktów z czasem. Te metryki są prawidłowe dla wybranego miesiąca, roku i wybranego produktu oraz są definiowane w następujący sposób. 
  
|**Metryczny**|**Opis**|
|:-----|:-----|
|EnabledUsers  <br/> |Liczba użytkowników, którzy mogą korzystać z produktu w miesiącu.  <br/> |
|ActiveUsers  <br/> |Liczba użytkowników aktywnych w miesiącu.  <br/> |
|MoMReturningUsers  <br/> |Liczba użytkowników aktywnych w miesiącu, którzy byli także aktywni w poprzednim miesiącu.  <br/> |
|FirstTimeUsers  <br/> |Liczba użytkowników aktywnych w miesiącu, którzy nigdy wcześniej nie używali usługi.  <br/> |
|CumulativeActiveUsers  <br/> |Liczba użytkowników aktywnych w miesiącu oraz dowolny poprzedni miesiąc.  <br/> |
|ActiveUsers(%)  <br/> |Procent użytkowników, zaokrąglony do najbliższej dziesiątej liczby aktywnych użytkowników w miesiącu w porównaniu z liczbą użytkowników włączonych w tym miesiącu.  <br/> |
|MoMReturningUsers(%)  <br/> |Procent użytkowników, zaokrąglony do najbliższej dziesiątej liczby aktywnych w miesiącu, którzy też byli aktywni w poprzednim miesiącu, w porównaniu z liczbą aktywnych użytkowników.  <br/> |
   
Ustawienia MoMReturningUsers, FirstTimeUsers, &amp; CumulativeActiveUsers zostały zresetowane począwszy od 1 stycznia 2018 r. z uwzględnieniem Microsoft Teams.
  
