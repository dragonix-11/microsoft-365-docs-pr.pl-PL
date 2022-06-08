---
title: Przenoszenie witryny programu SharePoint do innej lokalizacji geograficznej
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Dowiedz się, jak przenieść witrynę programu SharePoint do innej lokalizacji geograficznej w środowisku z wieloma lokalizacjami geograficznymi i przekazać użytkownikom oczekiwania dotyczące zmian.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0b388b3fa869e6207c72f62aa2f50b832acab43a
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940827"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>Przenoszenie witryny programu SharePoint do innej lokalizacji geograficznej

Przenoszenie geograficzne witryny programu SharePoint umożliwia przenoszenie witryn programu SharePoint do innych lokalizacji geograficznych w środowisku z wieloma lokalizacjami geograficznymi.

Następujące typy lokacji można przenosić między lokalizacjami geograficznymi:

- Witryny połączone z grupą platformy Microsoft 365, w tym witryny skojarzone z usługą Microsoft Teams
- Nowoczesne witryny bez skojarzenia grupy platformy Microsoft 365
- Klasyczne witryny programu SharePoint
- Witryny komunikacyjne

Aby przenieść witrynę między lokalizacjami geograficznymi, musisz być administratorem globalnym lub administratorem programu SharePoint.

Okno tylko do odczytu podczas przenoszenia geograficznego witryny programu SharePoint trwa około 4–6 godzin, w zależności od zawartości witryny.

## <a name="best-practices"></a>Najważniejsze wskazówki

- Spróbuj przenieść witrynę programu SharePoint w witrynie testowej, aby zapoznać się z procedurą.
- Sprawdź, czy lokację można przenieść przed zaplanowaniem lub wykonaniem przeniesienia.
- Jeśli jest to możliwe, zaplanuj przenoszenie lokacji między lokalizacjami geograficznymi poza godzinami pracy, aby zmniejszyć wpływ użytkowników.
- Komunikuj się z użytkownikami, których dotyczy problem przed przeniesieniem witryn.

## <a name="communicating-to-your-users"></a>Komunikacja z użytkownikami

Podczas przenoszenia witryn programu SharePoint między lokalizacjami geograficznymi ważne jest, aby komunikować się z użytkownikami witryn (zazwyczaj każdy, kto ma możliwość edytowania witryny), czego można oczekiwać. Może to pomóc w ograniczeniu pomyłek użytkowników i wywołań do działu pomocy technicznej. Przed przeniesieniem wyślij wiadomość e-mail do użytkowników witryn i poinformuj ich o następujących informacjach:

- Kiedy ma się rozpocząć przenoszenie i jak długo ma trwać
- Do której lokalizacji geograficznej jest przenoszona witryna, oraz adres URL dostępu do nowej lokalizacji
- Należy zamknąć pliki i nie wprowadzać zmian podczas przenoszenia.
- Uprawnienia i udostępnianie plików nie ulegnie zmianie z powodu przeniesienia.
- Czego można oczekiwać od środowiska użytkownika w środowisku z wieloma lokalizacjami geograficznymi

Pamiętaj, aby po pomyślnym zakończeniu przenoszenia wysłać użytkownikom witryn wiadomość e-mail z informacją, że mogą wznowić pracę w swoich witrynach.

## <a name="scheduling-sharepoint-site-moves"></a>Planowanie przenoszenia witryny programu SharePoint

Możesz zaplanować przenoszenie witryny programu SharePoint z wyprzedzeniem (opisane w dalszej części tego artykułu). Przenoszenie można zaplanować w następujący sposób:

- Możesz zaplanować maksymalnie 4000 ruchów naraz.
- Po rozpoczęciu przenoszenia możesz zaplanować więcej, maksymalnie 4000 oczekujących ruchów w kolejce i w dowolnym momencie.
- Maksymalny rozmiar witryny programu SharePoint, którą można przenieść, wynosi 1 terabajt (1 TB).

Aby zaplanować przeniesienie geograficzne witryny programu SharePoint na później, dołącz jeden z następujących parametrów podczas uruchamiania przenoszenia:

- `PreferredMoveBeginDate` — Przeniesienie prawdopodobnie rozpocznie się o tej określonej godzinie.
- `PreferredMoveEndDate` – Przeniesienie zostanie prawdopodobnie ukończone do tego określonego czasu, na zasadzie najlepszego wysiłku.

Czas musi być określony w uniwersalnym czasie koordynowanym (UTC) dla obu parametrów.

## <a name="moving-the-site"></a>Przenoszenie witryny

Przenoszenie geograficzne witryny programu SharePoint wymaga nawiązania połączenia i wykonania przeniesienia z adresu URL administratora programu SharePoint w lokalizacji geograficznej, w której znajduje się witryna.

Jeśli na przykład adres URL witryny to `https://contosohealthcare.sharepoint.com/sites/Turbines`, połącz się z adresem URL administratora programu SharePoint pod adresem `https://contosohealthcare-admin.sharepoint.com`:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

![Okno powłoki zarządzania usługi SharePoint Online z wyświetlonym poleceniem Connect-SPOService.](../media/move-onedrive-between-geo-locations-image1.png)

### <a name="validating-the-environment"></a>Weryfikowanie środowiska

Przed zaplanowaniem przenoszenia lokacji zalecamy przeprowadzenie walidacji w celu upewnienia się, że lokacja może zostać przeniesiona.

Nie obsługujemy przenoszenia witryn z:

- Usługi łączności biznesowej
- Formularze programu InfoPath
- Zastosowane szablony usługi Information Rights Management (IRM)

Aby upewnić się, że wszystkie lokalizacje geograficzne są zgodne, uruchom polecenie `Get-SPOGeoMoveCrossCompatibilityStatus`. Spowoduje to wyświetlenie wszystkich lokalizacji geograficznych oraz tego, czy środowisko jest zgodne z docelową lokalizacją geograficzną.

Aby przeprowadzić sprawdzanie tylko walidacji w witrynie, użyj parametru `Start-SPOSiteContentMove` z parametrem `-ValidationOnly` , aby sprawdzić, czy lokacja może zostać przeniesiona. Przykład:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

Spowoduje to *powodzenie* , jeśli witryna jest gotowa do przeniesienia lub *kończy się niepowodzeniem* , jeśli istnieją jakiekolwiek zablokowane warunki.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a>Uruchamianie przenoszenia geograficznego witryny programu SharePoint dla witryny bez skojarzonej grupy platformy Microsoft 365

Domyślnie początkowy adres URL witryny zmieni się na adres URL docelowej lokalizacji geograficznej. Przykład:

`https://Contoso.sharepoint.com/sites/projectx` do `https://ContosoEUR.sharepoint.com/sites/projectx`

W przypadku witryn bez skojarzenia grupy platformy Microsoft 365 można również zmienić nazwę witryny przy użyciu parametru `-DestinationUrl` . Przykład:

<https://Contoso.sharepoint.com/sites/projectx> do `https://ContosoEUR.sharepoint.com/sites/projecty`

Aby rozpocząć przenoszenie witryny, uruchom polecenie:

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

![Zrzut ekranu okna programu PowerShell przedstawiający polecenie cmdlet Start-SPOSiteContentMove.](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a>Uruchamianie przenoszenia geograficznego witryny programu SharePoint dla witryny połączonej z grupą platformy Microsoft 365

Aby przenieść witrynę połączoną z grupą platformy Microsoft 365, administrator globalny lub administrator programu SharePoint musi najpierw zmienić atrybut Preferowana lokalizacja danych (PDL) dla grupy platformy Microsoft 365.

Aby ustawić bibliotekę PDL dla grupy platformy Microsoft 365:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

Po zaktualizowaniu biblioteki PDL możesz rozpocząć przenoszenie witryny:

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>Anulowanie przenoszenia geograficznego witryny programu SharePoint

Możesz zatrzymać przenoszenie geograficzne witryny programu SharePoint pod warunkiem, że przenoszenie nie jest w toku lub ukończone przy użyciu `Stop-SPOSiteContentMove` polecenia cmdlet.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>Określanie stanu przenoszenia geograficznego witryny programu SharePoint

Stan przeniesienia lokacji z obszaru geograficznego, z którą masz połączenie, można określić przy użyciu następujących poleceń cmdlet:

- [Get-SPOSiteContentMoveState (lokacje](/powershell/module/sharepoint-online/get-spositecontentmovestate) bez połączenia z grupą)
- [Get-SPOUnifiedGroupMoveState (lokacje](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) połączone z grupą)

Użyj parametru , `-SourceSiteUrl` aby określić lokację, dla której ma zostać wyświetlony stan przenoszenia.

Stan przenoszenia opisano w poniższej tabeli.

****

|Stan|Opis|
|---|---|
|Gotowe do wyzwolenia|Przenoszenie nie zostało rozpoczęte.|
|Zaplanowane|Przenoszenie jest w kolejce, ale nie zostało jeszcze uruchomione.|
|InProgress (n/4)|Przenoszenie jest w toku w jednym z następujących stanów: walidacja (1/4), tworzenie kopii zapasowej (2/4), przywracanie (3/4), oczyszczanie (4/4).|
|Sukces|Przenoszenie zostało pomyślnie zakończone.|
|Zakończone niepowodzeniem|Przenoszenie nie powiodło się.|
|

Możesz również zastosować tę opcję, `-Verbose` aby wyświetlić dodatkowe informacje o przeniesieniu.

## <a name="user-experience"></a>Środowisko użytkownika

Użytkownicy witryny powinni zauważyć minimalne zakłócenia, gdy ich witryna zostanie przeniesiona do innej lokalizacji geograficznej. Oprócz krótkiego stanu tylko do odczytu podczas przenoszenia istniejące linki i uprawnienia będą nadal działać zgodnie z oczekiwaniami po zakończeniu przenoszenia.

### <a name="site"></a>Witryny

Gdy przenoszenie jest w toku, witryna jest ustawiona na tylko do odczytu. Po zakończeniu przenoszenia użytkownik jest kierowany do nowej witryny w nowej lokalizacji geograficznej po kliknięciu zakładek lub innych linków do witryny.

### <a name="permissions"></a>Uprawnienia

Użytkownicy z uprawnieniami do witryny będą nadal mieć dostęp do witryny podczas przenoszenia i po jej zakończeniu.

### <a name="sync-app"></a>Synchronizuj aplikację

Aplikacja synchronizacji automatycznie wykrywa i bezproblemowo przesyła synchronizację do nowej lokalizacji lokacji po zakończeniu przenoszenia lokacji. Użytkownik nie musi logować się ponownie ani podejmować żadnych innych działań. (Wersja 17.3.6943.0625 lub nowsza wymagana aplikacja synchronizacji).

Jeśli użytkownik zaktualizuje plik w trakcie przenoszenia, aplikacja synchronizacji powiadomi go, że przekazywanie plików jest w toku.

### <a name="sharing-links"></a>Udostępnianie linków

Po zakończeniu przenoszenia geograficznego witryny programu SharePoint istniejące łącza udostępnione dla plików, które zostały przeniesione, zostaną automatycznie przekierowane do nowej lokalizacji geograficznej.

### <a name="most-recently-used-files-in-office-mru"></a>Ostatnio używane pliki w pakiecie Office (MRU)

Usługa MRU jest aktualizowana przy użyciu adresu URL witryny i jej adresów URL zawartości po zakończeniu przenoszenia. Dotyczy to programów Word, Excel i PowerPoint.

### <a name="onenote-experience"></a>Środowisko programu OneNote

Klient programu OneNote win32 i aplikacja uniwersalna systemu windows automatycznie wykrywają i bezproblemowo synchronizują notesy z nową lokalizacją lokacji po zakończeniu przenoszenia lokacji. Użytkownik nie musi logować się ponownie ani podejmować żadnych innych działań. Jedynym widocznym wskaźnikiem dla użytkownika jest niepowodzenie synchronizacji notesu, gdy przenoszenie witryny jest w toku. To środowisko jest dostępne w następujących wersjach klienta programu OneNote:

- OneNote win32 — wersja 16.0.8326.2096 (i nowsze)
- OneNote UWP — wersja 16.0.8431.1006 (i nowsze)
- Aplikacja mobilna OneNote — wersja 16.0.8431.1011 (i nowsze)

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>Teams (dotyczy połączonych witryn grupy platformy Microsoft 365)

Po zakończeniu przenoszenia geograficznego witryny programu SharePoint użytkownicy będą mieli dostęp do plików witryny grupy platformy Microsoft 365 w aplikacji Teams. Ponadto pliki udostępnione za pośrednictwem czatu usługi Teams z witryny przed przeniesieniem geograficznym będą nadal działać po zakończeniu przenoszenia.

Przenoszenie geograficzne witryny programu SharePoint nie obsługuje przenoszenia kanałów prywatnych z jednego obszaru geograficznego do innego. Kanały prywatne pozostają w oryginalnym obszarze geograficznym.
  

### <a name="sharepoint-mobile-app-iosandroid"></a>Aplikacja mobilna programu SharePoint (iOS/Android)

Aplikacja mobilna programu SharePoint jest zgodna z wieloma obszarami geograficznymi i może wykrywać nową lokalizację geograficzną witryny.

### <a name="sharepoint-workflows"></a>Przepływy pracy programu SharePoint

Przepływy pracy programu SharePoint 2013 muszą zostać ponownie opublikowane po przeniesieniu witryny. Przepływy pracy programu SharePoint 2010 powinny nadal działać normalnie.

### <a name="apps"></a>Aplikacje

Jeśli przenosisz witrynę z aplikacjami, musisz ponownie uzasadnić aplikację w nowej lokalizacji geograficznej witryny, ponieważ aplikacja i jej połączenia mogą nie być dostępne w docelowej lokalizacji geograficznej.

### <a name="flow"></a>Przepływu

W większości przypadków przepływy będą nadal działać po przeniesieniu geograficznym witryny programu SharePoint. Zalecamy przetestowanie ich po zakończeniu przenoszenia.

### <a name="power-apps"></a>Power Apps

Usługa Power Apps musi zostać ponownie utworzona w lokalizacji docelowej.

### <a name="data-movement-between-geo-locations"></a>Przenoszenie danych między lokalizacjami geograficznymi

Program SharePoint używa usługi Azure Blob Storage do swojej zawartości, podczas gdy metadane skojarzone z witrynami i jego plikami są przechowywane w programie SharePoint. Po przeniesieniu lokacji ze źródłowej lokalizacji geograficznej do docelowej lokalizacji geograficznej usługa przeniesie również skojarzony magazyn obiektów blob. Usługa Blob Storage jest przenoszona w ciągu około 40 dni.
