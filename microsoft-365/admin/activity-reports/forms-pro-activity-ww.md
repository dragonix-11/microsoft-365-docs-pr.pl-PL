---
title: Raporty dotyczące aktywności głosowej klientów w usłudze Microsoft Dynamics 365
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
description: Dowiedz się, jak uzyskać raport aktywności usługi Microsoft Dynamics 365 Customer Voice przy użyciu pulpitu nawigacyjnego Raporty i dowiedzieć się, jak licencjonowani użytkownicy współpracują.
ms.openlocfilehash: c8c7678991635139f2bdfb97a8baf7ccc2c667aa
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467607"
---
# <a name="microsoft-365-reports-in-the-admin-center---dynamics-365-customer-voice-activity"></a>Microsoft 365 Raporty w centrum administracyjnym — działanie usługi Dynamics 365 Customer Voice

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).
  
Na przykład możesz zrozumieć aktywność każdego użytkownika licencjonowanego do korzystania z usługi Microsoft Dynamics 365 Customer Voice, przeglądając ich interakcje z usługą Dynamics 365 Customer Voice. Pomaga to również zrozumieć poziom współpracy, analizując liczbę Pro ankiet utworzonych i Pro ankiet, na które użytkownicy odpowiedzieli. 
  
## <a name="how-to-get-to-the-dynamics-365-customer-voice-activity-report"></a>Jak uzyskać dostęp do raportu aktywności usługi Dynamics 365 Customer Voice

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>. 
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie Głos klienta usługi Dynamics 365.
  
## <a name="interpret-the-dynamics-365-customer-voice-activity-report"></a>Interpretowanie raportu aktywności usługi Dynamics 365 Customer Voice

Możesz wyświetlić działania w raporcie Dynamics 365 Customer Voice, wybierając kartę **Działanie** .<br/>![Microsoft 365 raporty — raport aktywności usługi Microsoft Dynamics 365 Customer Voice.](../../media/a7e57d18-1ac8-4d4b-bd70-83361505dc3e.png)

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> ![Raport aktywności Dynamics 365 Customer Voice — wybierz kolumny.](../../media/5ab66f4b-32eb-4c9b-9683-1157ae9e2c0a.png)

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. 

Raport **aktywności Dynamics 365 Customer Voice** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).
  
|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Nazwa użytkownika  <br/> |Adres e-mail użytkownika, który wykonał działanie na Microsoft Forms.  <br/> |
|Data ostatniego działania (UTC)  <br/> |Ostatnia data wykonania działania formularza przez użytkownika dla wybranego zakresu dat. Aby zobaczyć działanie, które wystąpiło w konkretnym dniu, wybierz datę bezpośrednio na wykresie.<br/>Spowoduje to przefiltrowanie tabeli w celu wyświetlenia danych aktywności pliku tylko dla użytkowników, którzy wykonali działanie w danym dniu.  <br/> |
|Liczba utworzonych ankiet  <br/> |Liczba ankiet utworzonych przez użytkownika.   <br/> |
|Liczba odpowiedzi na ankietę  <br/> |Liczba odpowiedzi od osób odpowiadających, do których przeprowadzono ankietę.|
|||