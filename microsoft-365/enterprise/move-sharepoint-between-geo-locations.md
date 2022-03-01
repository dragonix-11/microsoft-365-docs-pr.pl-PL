---
title: Przenoszenie witryny SharePoint do innej lokalizacji geograficznej
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
description: Dowiedz się, jak przenieść witrynę SharePoint do innej lokalizacji geograficznej w środowisku wielolokalowym i jak przekazywać użytkownikom oczekiwania na wprowadzone zmiany.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9e4132b8399cc69067d24af6c3c9ec8e3baf52bd
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019380"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>Przenoszenie witryny SharePoint do innej lokalizacji geograficznej

Dzięki SharePoint geolokalizacji witryny można przenosić SharePoint do innych lokalizacji geograficznych w środowisku wielolokalowym.

Między lokalizacjami geograficznymi można przenosić następujące typy witryn:

- Microsoft 365 połączonych z grupą witryn, w tym witryn skojarzonych z witrynami Microsoft Teams
- Nowoczesne witryny bez skojarzenia Microsoft 365 grupy
- Witryny SharePoint klasyczne
- Witryny do komunikacji

Musisz być administratorem globalnym lub administratorem SharePoint, aby przenosić witrynę między lokalizacjami geograficznymi.

W czasie przesuwania geolokalizacji SharePoint w czasie około 4–6 godzin jest dostępne okno tylko do odczytu, w zależności od zawartości witryny.

## <a name="best-practices"></a>Najważniejsze wskazówki

- Spróbuj wykonać SharePoint w witrynie testowej, aby zapoznać się z procedurą.
- Sprawdź, czy witrynę można przenieść przed zaplanowaniem lub wykonaniem przeniesienia.
- Jeśli jest to możliwe, zaplanuj przesuwanie witryn między lokalizacjami geograficznymi poza godzinami pracy, aby zmniejszyć wpływ na użytkowników.
- Przed przeniesieniem witryn komunikuj się z użytkownikami, których to wpływa.

## <a name="communicating-to-your-users"></a>Komunikowanie się z użytkownikami

Podczas przenoszenia SharePoint między lokalizacjami geograficznymi należy zakomunikować użytkownikom tych witryn (ogólnie wszystkim osobom, które mają możliwość edytowania witryny), czego mogą oczekiwać. Może to zmniejszyć liczbę nieporozumień wśród użytkowników i ograniczyć liczbę telefonów do pomocy technicznej. Przed przeniesieniem użytkowników witryn wyślij im pocztą e-mail następujące informacje:

- Kiedy ma się rozpocząć przenoszenie i jak długo będzie trwać
- Do jakiej lokalizacji geograficznej jest przenosząca się witryna, oraz adres URL, aby uzyskać dostęp do nowej lokalizacji
- Należy zamknąć pliki i nie edytować ich podczas przenoszenia.
- Uprawnienia do plików i udostępnianie nie zmieniają się z powodu przeniesienia.
- Czego można oczekiwać w środowisku użytkownika z wieloma lokalizacjami geograficznymi

Po pomyślnym ukończeniu procesu przenoszenia wyślij użytkownikom witryn wiadomość e-mail z powiadomieniem, że mogą wznowić pracę w swoich witrynach.

## <a name="scheduling-sharepoint-site-moves"></a>Planowanie SharePoint przeniesień witryn

Możesz zaplanować SharePoint witryny (opisano to w dalszej części tego artykułu). Możesz zaplanować przeniesienie w następujący sposób:

- Możesz zaplanować maksymalnie 4000 przejść jednocześnie.
- Po rozpoczęciu przesuń możesz zaplanować więcej, przy maksymalnie 4000 oczekujących przesunięciach w kolejce i o dowolnej porze.
- Maksymalny rozmiar przenoszonej SharePoint to 1 terabajt (1 TB).

Aby zaplanować SharePoint geolokalizacji witryny na później, podczas rozpoczynania przenoszenia uwzględnij jeden z następujących parametrów:

- `PreferredMoveBeginDate` — Przeniesienie rozpocznie się prawdopodobnie o tej określonej godzinie.
- `PreferredMoveEndDate` — Przeniesienie zostanie prawdopodobnie ukończone w tym czasie przy najlepszych starań, ale bez nakładu pracy.

Czas dla obu parametrów musi być określony w uniwersalnym czasie koordynowanej (UTC).

## <a name="moving-the-site"></a>Przenoszenie witryny

SharePoint przenoszenia geolokalizacji witryny wymaga połączenia i przeprowadzenia przenoszenia z adresu URL SharePoint w lokalizacji geograficznej, w której witryna się znajduje.

Jeśli na przykład adres URL witryny to , połącz się z adresem URL <https://contosohealthcare.sharepoint.com/sites/Turbines>administratora SharePoint adres URL<https://contosohealthcare-admin.sharepoint.com>:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

![SharePoint Powłoki zarządzania online z Connect-SPOService zarządzaniem.](../media/move-onedrive-between-geo-locations-image1.png)

### <a name="validating-the-environment"></a>Sprawdzania poprawności środowiska

Przed zaplanowanym przeniesieniem witryny zalecamy przeprowadzenie sprawdzania poprawności w celu upewniania się, że można przenieść witrynę.

Nie obsługujemy przenoszenia witryn za pomocą:

- Usługi łączności biznesowej
- Formularze programu InfoPath
- Zastosowane szablony zarządzania prawami do informacji (IRM)

Aby zapewnić zgodność wszystkich lokalizacji geograficznych, uruchom .`Get-SPOGeoMoveCrossCompatibilityStatus` Spowoduje to wyświetlenie wszystkich lokalizacji geograficznych oraz tego, czy środowisko jest zgodne z lokalizacją geograficzną miejsca docelowego.

Aby przeprowadzić w witrynie sprawdzanie tylko przez sprawdzanie poprawności, `Start-SPOSiteContentMove` `-ValidationOnly` użyj z parametrem w celu sprawdzenia, czy można przenieść witrynę. Przykład:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

Spowoduje to *zwrócenie informacji o* sukcesie, jeśli witryna jest gotowa do *przenieść, lub* Niepowodzenie, jeśli istnieje którykolwiek z zablokowanych warunków.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a>Rozpoczynanie SharePoint geolokalizacji witryny dla witryny bez skojarzonej Microsoft 365 grupy

Domyślnie początkowy adres URL witryny zmieni się na adres URL lokalizacji geograficznej miejsca docelowego. Przykład:

<https://Contoso.sharepoint.com/sites/projectx> na <https://ContosoEUR.sharepoint.com/sites/projectx>

W przypadku witryn bez Microsoft 365 skojarzenia grupy możesz również zmienić nazwę witryny za pomocą parametru`-DestinationUrl`. Przykład:

<https://Contoso.sharepoint.com/sites/projectx> na <https://ContosoEUR.sharepoint.com/sites/projecty>

Aby rozpocząć przenoszenie witryny, uruchom:

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

![Zrzut ekranu przedstawiający okno programu PowerShell Start-SPOSiteContentMove polecenie cmdlet.](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a>Rozpoczynanie SharePoint geolokalizacji witryny dla Microsoft 365 witryny połączonej z grupą

Aby przenieść Microsoft 365 połączonej z grupą witryny, administrator globalny lub administrator usługi SharePoint musi najpierw zmienić atrybut Preferred Data Location (PDL) dla grupy Microsoft 365 danych.

Aby ustawić plik PDL dla Microsoft 365 grupy:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

Po zaktualizowania pliku PDL możesz rozpocząć przenoszenie witryny:

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>Anulowanie przenoszenia geolokalizacji SharePoint witryny

Przenoszenie geolokalizacji SharePoint można zatrzymać, o ile nie jest on w toku ani nie jest ukończony przy użyciu `Stop-SPOSiteContentMove` polecenia cmdlet.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>Określanie stanu przenoszenia geolokalizacji SharePoint witryny

Możesz ustalić stan przenoszenia witryny poza lokalizację geograficzną, z która jest połączona, przy użyciu następujących polecenia cmdlet:

- [Get-SPOSiteContentMoveState](/powershell/module/sharepoint-online/get-spositecontentmovestate) (witryny nie połączone z grupą)
- [Get-SPOUnifiedGroupMoveState](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) (witryny połączone z grupą)

Użyj parametru `-SourceSiteUrl` , aby określić witrynę, dla której ma być wyświetlony stan przenoszenia.

Stan przenoszenia został opisany w poniższej tabeli.

****

|Stan|Opis|
|---|---|
|Ready to Trigger|Przenoszenie nie zostało rozpoczęte.|
|Zaplanowane|Przeniesienie jest w kolejce, ale jeszcze się nie rozpoczęło.|
|Ruch wychodzący (n/4)|Proces przenoszenia jest w toku w jednym z następujących stanów: Sprawdzanie poprawności (04-01), Kopii zapasowej (04-02), Przywracanie (04-03), Oczyszczanie (4/4).|
|Sukces|Przeniesienie zostało ukończone pomyślnie.|
|Zakończone niepowodzeniem|Przeniesienie nie powiodło się.|
|

Możesz również zastosować tę opcję `-Verbose` , aby wyświetlić dodatkowe informacje o przenoszeniu.

## <a name="user-experience"></a>Środowisko użytkownika

Użytkownicy witryn powinni zauważyć minimalne zakłócenia w pracy, gdy ich witryna jest przenoszony do innej lokalizacji geograficznej. Poza krótkim stanem tylko do odczytu podczas przenoszenia istniejące linki i uprawnienia będą nadal działać zgodnie z oczekiwaniami po zakończeniu przenoszenia.

### <a name="site"></a>Witryna

Podczas przenoszenia witryna jest ustawiona na tylko do odczytu. Po zakończeniu przenoszenia użytkownik jest przekierowywowany do nowej witryny w nowej lokalizacji geograficznej po kliknięciu zakładek lub innych linków do witryny.

### <a name="permissions"></a>Uprawnienia

Użytkownicy z uprawnieniami do witryny nadal będą mieli dostęp do witryny podczas przenoszenia i po zakończeniu procesu przenoszenia.

### <a name="sync-app"></a>Aplikacja do synchronizacji

Aplikacja do synchronizacji automatycznie wykryje synchronizację i bezproblemowo przeniesie synchronizację do nowej lokalizacji witryny po zakończeniu przenoszenia witryny. Użytkownik nie musi logować się ponownie ani nic innego. (Wersja 17.3.6943.0625 lub nowsza z wymaganej aplikacji do synchronizacji).

Jeśli użytkownik aktualizuje plik w trakcie przenoszenia, aplikacja do synchronizacji powiadomi go, że przekazywanie pliku ma stan oczekiwania, gdy proces przenoszenia jest w toku.

### <a name="sharing-links"></a>Udostępnianie linków

Po zakończeniu SharePoint geolokalizacji witryny istniejące udostępnione linki dla przeniesionych plików zostaną automatycznie przekierowane do nowej lokalizacji geograficznej.

### <a name="most-recently-used-files-in-office-mru"></a>Ostatnio używane pliki w Office (MRU)

Po zakończeniu przenoszenia usługa MRU zostanie zaktualizowana o adres URL witryny i jej adresy URL zawartości. Dotyczy to programu Word, Excel i PowerPoint.

### <a name="onenote-experience"></a>OneNote środowisko użytkownika

OneNote klienta win32 i aplikacji UWP (uniwersalnej) automatycznie wykryje notesy w nowej lokalizacji witryny i bezproblemowo je zsynchronizuj po zakończeniu przenoszenia witryny. Użytkownik nie musi logować się ponownie ani nic innego. Jedynym widocznym wskaźnikiem dla użytkownika jest niepowodzenie synchronizacji notesu w trakcie przenoszenia witryny. To środowisko jest dostępne w następujących OneNote klientach:

- OneNote win32 — wersja 16.0.8326.2096 (lub nowsza)
- OneNote UWP — wersja 16.0.8431.1006 (lub nowsza)
- OneNote dla urządzeń przenośnych — wersja 16.0.8431.1011 (lub nowsza)

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>Teams (dotyczy witryn Microsoft 365 połączonych grup)

Po zakończeniu SharePoint geolokalizacji witryny użytkownicy będą mieli dostęp do swoich plików witryny Microsoft 365 grupy w aplikacji Teams sieci Web. Ponadto pliki udostępniane za pośrednictwem Teams z ich witryny przed przeniesieniem geolokalizacji będą nadal działać po zakończeniu przenoszenia.

SharePoint geolokalizacji witryny nie obsługuje przenoszenia kanałów prywatnych z jednego miejsca do drugiego. Kanały prywatne pozostają w pierwotnym geolokalizacji.
  

### <a name="sharepoint-mobile-app-iosandroid"></a>SharePoint dla urządzeń przenośnych (iOS/Android)

Aplikacja SharePoint mobilna jest zgodna między lokalizacjami geograficznymi i może wykrywać nową lokalizację geograficzną witryny.

### <a name="sharepoint-workflows"></a>SharePoint przepływy pracy

SharePoint 2013 muszą zostać ponownie opublikowane po przeniesienie witryny. SharePoint 2010 powinny działać normalnie.

### <a name="apps"></a>Aplikacje

W przypadku przenoszenia witryny za pomocą aplikacji należy ponownie omówić aplikację w nowej lokalizacji geograficznej witryny, ponieważ aplikacja i jej połączenia mogą być niedostępne w docelowej lokalizacji geograficznej.

### <a name="flow"></a>Flow

W większości przypadków przepływy będą nadal działać po SharePoint geolokalizacji witryny. Zalecamy przetestowanie ich po zakończeniu przenoszenia.

### <a name="power-apps"></a>Power Apps

Power Apps utworzyć go ponownie w lokalizacji docelowej.

### <a name="data-movement-between-geo-locations"></a>Ruch danych między lokalizacjami geograficznymi

SharePoint zawartości korzysta z magazynu obiektów blob platformy Azure, a metadane skojarzone z witrynami i ich plikami są przechowywane w SharePoint. Gdy witryna zostanie przeniesiona z jej źródłowej lokalizacji geograficznej do lokalizacji geograficznej jej miejsca docelowego, usługa również przeniesie skojarzoną z nią witrynę blob Storage. Obiekty blob Storage są ukończone w ciągu około 40 dni.
