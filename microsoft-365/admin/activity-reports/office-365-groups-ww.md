---
title: Raporty grup centrum administracyjnego platformy Microsoft 365
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
- MET150
- MOE150
- GEA150
ms.assetid: a27f1a99-3557-4f85-9560-a28e3d822a40
description: Pobierz raport Grupy platformy Microsoft 365, aby uzyskać wgląd w aktywność grup w organizacji i zobaczyć, ile grup jest tworzonych i używanych.
ms.openlocfilehash: dc3d05fdad68f18b24dae06021b0cb15306b4338
ms.sourcegitcommit: e6443eb3a4c826792806873428c0c17b59f4fde5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2022
ms.locfileid: "65889241"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Raporty platformy Microsoft 365 w centrum administracyjnym — grupy platformy Microsoft 365

Na pulpicie nawigacyjnym Raporty platformy Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). W raporcie grupy platformy Microsoft 365 możesz uzyskać wgląd w aktywność grup w organizacji i zobaczyć, ile grup jest tworzonych i używanych.
  
## <a name="how-to-get-to-the-groups-report"></a>Jak przejść do raportu grup

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.

2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie Aktywni użytkownicy — Aplikacje platformy Microsoft 365 lub Aktywni użytkownicy — Usługi Microsoft 365, aby przejść do strony raportu usługi Office 365.
  
## <a name="interpret-the-groups-report"></a>Interpretowanie raportu grup

Aktywacje można wyświetlić w raporcie usługi Office 365, wybierając kartę **Działania grupy** .

:::image type="content" alt-text="Raporty platformy Microsoft 365 — działanie grup usługi Microsoft Office 365." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

Wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.

:::image type="content" alt-text="Raport aktywności grup usługi Office 365 — wybierz kolumny." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Możesz również wyeksportować dane raportu do pliku programu Excel .csv, wybierając link **Eksportuj** . Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, aby filtrować i sortować, musisz wyeksportować dane. 

Raport **grup** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).

|Metrycznych|Definicja|
|:-----|:-----|
|Nazwa grupy |Nazwa grupy. |
|Deleted |Liczba usuniętych grup. Jeśli grupa została usunięta, ale w okresie raportowania nastąpiła w niej aktywność, grupa ta pojawi się na siatce z flagą ustawioną na wartość Prawda. |
|Właściciel grupy |Nazwa właściciela grupy. |
|Data ostatniego działania (UTC) |Ostatnia data odebrania komunikatu przez grupę. Jest to najpóźniejsza data jakiegokolwiek działania w konwersacji e-mail, usłudze Yammer lub witrynie. |
|Wpisać |Typ grupy. Grupa może być publiczna lub prywatna. |
|Wiadomości e-mail odebrane w programie Exchange |Liczba komunikatów odebranych przez grupę.|
|Wiadomości e-mail w programie Exchange (łącznie) |Całkowita liczba elementów w skrzynce pocztowej grupy. |
|Magazyn skrzynki pocztowej używany na potrzeby programu Exchange (MB) |Magazyn używany przez skrzynkę pocztową grupy. |
|Pliki programu SharePoint (łącznie) |Liczba plików przechowywanych w witrynach grupy programu SharePoint. |
|Pliki programu SharePoint (aktywne) |Liczba plików w witrynie grupy programu SharePoint, które zostały użyte (wyświetlone lub zmodyfikowane, zsynchronizowane, udostępnione wewnętrznie lub zewnętrznie) w okresie raportowania. |
|Łączny magazyn lokacji używany dla programu SharePoint (MB) |Ilość magazynu w MB używanego w okresie raportowania. |
|Komunikaty w usłudze Yammer (opublikowane) |Liczba komunikatów opublikowanych w grupie usługi Yammer w okresie raportowania. |
|Komunikaty w usłudze Yammer (odczyt) |Liczba konwersacji odczytanych w grupie usługi Yammer w okresie raportowania. |
|Komunikaty w usłudze Yammer (lubię to) |Liczba komunikatów lubianych w grupie usługi Yammer w okresie raportowania. |
|Członków |Liczba członków w grupie. |
|Członkowie zewnętrzni |Liczba użytkowników zewnętrznych w grupie.|
|Łączna liczba zorganizowanych spotkań  |Suma jednorazowych zaplanowanych i cyklicznych spotkań zorganizowanych przez użytkownika w określonym okresie.|
|Komunikaty kanału  |Liczba unikatowych komunikatów, które użytkownik zamieścił na czacie zespołowym w określonym okresie. Obejmuje to oryginalne wpisy i odpowiedzi. |


## <a name="related-content"></a>Zawartość pokrewna

[Raporty platformy Microsoft 365 w centrum administracyjnym](activity-reports.md) (artykuł)\
[Inteligentne raporty i szczegółowe informacje w Centrum zgodności & zabezpieczeń](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance) (artykuł)\
[Raporty platformy Microsoft 365 w centrum administracyjnym — aktywni użytkownicy](../../admin/activity-reports/active-users-ww.md) (artykuł)

