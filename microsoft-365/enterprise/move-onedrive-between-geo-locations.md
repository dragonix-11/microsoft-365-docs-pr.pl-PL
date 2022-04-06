---
title: Przenoszenie OneDrive lokalizacji geograficznej
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Znajdź informacje na temat przenoszenia OneDrive do innej lokalizacji geograficznej, w tym informacje o planowaniu przenoszenia witryny i komunikowaniu oczekiwań użytkownikom.
ms.openlocfilehash: f0a9e319d20c7b56701d776e85a0618ed30e5f78
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569606"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Przenoszenie OneDrive lokalizacji geograficznej

Przenoszenie OneDrive geolokalizacji umożliwia przenoszenie skrzynek OneDrive do innej lokalizacji geograficznej. OneDrive przenoszenia geolokalizacji wykonuje administrator usługi SharePoint Online lub administrator Microsoft 365 globalnego. Przed rozpoczęciem przenoszenia OneDrive geolokalizacji należy powiadomić użytkownika, OneDrive o przenoszeniu, i polecić zamknięcie wszystkich plików na czas przenoszenia. Jeśli podczas przenoszenia użytkownik ma otwarty dokument przy użyciu Office klienta, po wykonaniu przeniesienia musi zostać zapisany w nowej lokalizacji. W razie potrzeby przeniesienie można zaplanować na przyszłą godzinę.

Ta OneDrive używa Azure Blob Storage do przechowywania zawartości. Obiekt blob Storage skojarzony z obiektem OneDrive użytkownika zostanie przeniesiony z źródłowej do docelowej lokalizacji geograficznej w ciągu 40 dni od OneDrive dostępnego dla użytkownika. Dostęp do plików użytkownika zostanie OneDrive zaraz po tym, jak będzie OneDrive miejsce docelowe.

W OneDrive przenoszenia geolokalizacji (około 2–6 godzin) okienko przenoszenia OneDrive jest ustawione jako tylko do odczytu. Użytkownik nadal może uzyskać dostęp do swoich plików za pośrednictwem aplikacji synchronizacja usługi OneDrive lub swojej witryny OneDrive sieci SharePoint Online. Po OneDrive przenoszenia geolokalizacji użytkownik zostanie automatycznie połączony ze swoim OneDrive lokalizacją geograficzną miejsca docelowego podczas przechodzenia do aplikacji OneDrive w Microsoft 365 Uruchamianie aplikacji. Aplikacja do synchronizacji zacznie automatycznie synchronizować się z nowej lokalizacji.

Procedury w tym artykule wymagają modułu [Microsoft Office SharePoint Online PowerShell](https://www.microsoft.com/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>Komunikowanie się z użytkownikami

Podczas przenoszenia OneDrive między lokalizacjami geograficznymi należy przekazywać użytkownikom informacje o tym, czego mogą się spodziewać. Może to zmniejszyć liczbę nieporozumień wśród użytkowników i ograniczyć liczbę telefonów do pomocy technicznej. Wyślij do użytkowników pocztą e-mail przed przeniesieniem i poukaj im następujące informacje:

- Kiedy ma się rozpocząć przenoszenie i jak długo będzie trwać
- Do której lokalizacji geograficznej OneDrive jest przenosząca się lokalizacja, oraz adres URL, aby uzyskać dostęp do nowej lokalizacji
- Należy zamknąć pliki i nie edytować ich podczas przenoszenia.
- Uprawnienia do plików i udostępnianie nie zmieniają się w wyniku przeniesienia.
- Czego można oczekiwać w [środowisku użytkownika z wieloma lokalizacjami geograficznymi](multi-geo-user-experience.md)

Po pomyślnym ukończeniu procesu przenoszenia wyślij użytkownikom wiadomość e-mail z powiadomieniem, że mogą wznowić pracę w OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>Planowanie OneDrive przeniesień witryn

Możesz zaplanować OneDrive witryny (opisano to w dalszej części tego artykułu). Zalecamy, aby zacząć od niewielkiej liczby użytkowników, aby zweryfikować przepływy pracy i strategie komunikacyjne. Po zasypcie tego procesu możesz zaplanować przeniesienie w następujący sposób:

- Możesz zaplanować maksymalnie 4000 przejść jednocześnie.
- Po rozpoczęciu przesuń możesz zaplanować więcej, przy maksymalnie 4000 oczekujących przesunięciach w kolejce i o dowolnej porze.
- Maksymalny rozmiar przenoszonej OneDrive to 1 terabajt (1 TB).

## <a name="moving-a-onedrive-site"></a>Przenoszenie witryny OneDrive sieci Web

Aby wykonać OneDrive lokalizacji geograficznej, administrator dzierżawy musi najpierw ustawić preferowaną lokalizację danych (PDL) użytkownika na odpowiednią lokalizację geograficzną. Po skonfigurowaniu pliku PDL poczekaj co najmniej 24 godziny na zsynchronizowanie aktualizacji PDL przez lokalizacje geograficzne przed rozpoczęciem OneDrive geolokalizacji.

Podczas korzystania z funkcji cmdlet przenoszenia geolokalizacji połącz się z usługą SPO w bieżącej OneDrive lokalizacji geograficznej użytkownika, używając następującej składni:

```powershell
Connect-SPOService -url https://<tenantName>-admin.sharepoint.com
```

Na przykład: Aby przenieść OneDrive użytkownika "Matt@contosoenergy.onmicrosoft.com", połącz się z centrum administracyjnym usługi EUR SharePoint, gdy OneDrive użytkownika znajduje się w lokalizacji geograficznej EUR:

```powershell
Connect-SPOService -url https://contosoenergyeur-admin.sharepoint.com
```

![Zrzut ekranu przedstawiający okno programu PowerShell z poleceniem cmdlet connect-sposervice.](../media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Sprawdzania poprawności środowiska

Przed rozpoczęciem przenoszenia OneDrive geolokalizacji zalecamy sprawdzenie poprawności środowiska.

Aby zapewnić zgodność wszystkich lokalizacji geograficznych, uruchom:

```powershell
Get-SPOGeoMoveCrossCompatibilityStatus
```

Zostanie wyświetlona lista lokalizacji geograficznych oraz informacje o tym, czy zawartość może być przenoszony między zostanie oznaczona jako "Zgodna". Jeśli polecenie zwróci wartość "Niezgodne", sprawdź po raz kolejny stan w późniejszym terminie.

Jeśli OneDrive zawiera na przykład podwiterę, nie można jej przenieść. Za pomocą polecenia cmdlet Start-SPOUserAndContentMove z parametrem -ValidationOnly możesz sprawdzić, czy OneDrive można przenieść:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly
```

Spowoduje to zwrot sukcesu, jeśli OneDrive będzie gotowy do przeniesienia, lub Niepowodzenie, jeśli istnieje zawiązek ze względu na prawo lub podwitwitę, która uniemożliwia przeniesienie. Po walidacji, czy OneDrive można przenieść, możesz rozpocząć przenoszenie.

## <a name="start-a-onedrive-geo-move"></a>Rozpoczynanie OneDrive geolokalizacji

Aby rozpocząć przenoszenie, uruchom:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>
```

Używanie tych parametrów:

- _UserPrincipalName (_ Głównej nazwy użytkownika), OneDrive do którego jest przenoszony adres.
- _DestinationDataLocation_ — Geo-Location do OneDrive musi zostać przeniesiona lokalizacja docelowa. Powinna być taka sama jak preferowana lokalizacja danych użytkownika.

Aby na przykład przenieść OneDrive kwoty matt@contosoenergy.onmicrosoft.com EUR na AUS, uruchom:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS
```

![Zrzut ekranu przedstawiający okno programu PowerShell Start-SPOUserAndContentMove polecenie cmdlet.](../media/move-onedrive-between-geo-locations-image2.png)

Aby zaplanować przenoszenie geolokalizacji na później, użyj jednego z następujących parametrów:

- _PreferredMoveBeginDate_ — przeniesienie prawdopodobnie rozpocznie się o tej określonej godzinie. Czas musi być określony w uniwersalnym czasie koordynowany (UTC).
- _PreferredMoveEndDate_ — przeniesienie zostanie prawdopodobnie ukończone w tym czasie przy najlepszym na mocy nakładu pracy. Czas musi być określony w uniwersalnym czasie koordynowany (UTC).

## <a name="cancel-a-onedrive-geo-move"></a>Anulowanie przenoszenia OneDrive lokalizacji geograficznej

Możesz zatrzymać przenoszenie geolokalizacji lokalizacji OneDrive pod warunkiem, że przenoszenie nie jest w toku ani nie zakończyło się przy użyciu polecenia cmdlet:

```powershell
Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>
```

Wartość _UserPrincipalName_ (Głównej nazwy użytkownika) to głównej nazwy użytkownika OneDrive którego przenoszenie ma zostać zatrzymane.

## <a name="determining-current-status"></a>Określanie bieżącego stanu

Stan geolokalizacji możesz sprawdzić OneDrive geolokalizacji do lub z lokalizacji geograficznej, z Get-SPOUserAndContentMoveState polecenie cmdlet.

Stan przenoszenia został opisany w poniższej tabeli.

|Stan|Opis|
|---|---|
|NotStarted|Przenoszenie nie zostało rozpoczęte|
|Ruch wychodzący (*n*/4)|Przenoszenie jest w toku w jednym z następujących stanów: <ul><li>Sprawdzanie poprawności (04-01)</li><li>Kopia zapasowa (04-02)</li><li>Przywracanie (04-03)</li><li>Oczyszczanie (4/4)</li></ul>|
|Sukces|Przeniesienie zostało ukończone pomyślnie.|
|Zakończone niepowodzeniem|Przeniesienie nie powiodło się.|

Aby znaleźć stan przenoszenia określonego użytkownika, użyj *parametru UserPrincipalName* :

```powershell
Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>
```

Aby znaleźć stan wszystkich ruchu do lub z lokalizacji geograficznej, z którym masz połączenie, użyj parametru *MoveState* z jedną z następujących wartości: NotStarted, InProgress, Success, Failed, All.

```powershell
Get-SPOUserAndContentMoveState -MoveState <value>
```

Możesz również dodać parametr *Verbose* , aby uzyskać bardziej szczegółowe opisy stanu przenoszenia.

## <a name="user-experience"></a>Środowisko użytkownika

Użytkownicy OneDrive powinni zauważyć minimalne zakłócenia, jeśli ich OneDrive zostaną przeniesione do innej lokalizacji geograficznej. Poza krótkim stanem tylko do odczytu podczas przenoszenia istniejące linki i uprawnienia będą nadal działać zgodnie z oczekiwaniami po zakończeniu przenoszenia.

### <a name="users-onedrive"></a>Ustawienia OneDrive

Gdy przenoszenie jest w toku, ustawienie dla użytkownika OneDrive tylko do odczytu. Po zakończeniu przenoszenia użytkownik jest przekierowywowyny do swojego OneDrive w nowej lokalizacji geograficznej, gdy przechodzi do OneDrive do ikony uruchamianie aplikacji Microsoft 365 lub przeglądarki internetowej.

### <a name="permissions-on-onedrive-content"></a>Uprawnienia dotyczące OneDrive zawartości

Użytkownicy z uprawnieniami OneDrive będą nadal mieli dostęp do zawartości podczas przenoszenia i po zakończeniu jej przenoszenia.

### <a name="onedrive-sync-app"></a>synchronizacja usługi OneDrive aplikacji

Aplikacja synchronizacja usługi OneDrive automatycznie wykryje i bezproblemowo przeniesie synchronizację do nowej OneDrive OneDrive lokalizacji po zakończeniu przenoszenia geolokalizacji. Użytkownik nie musi logować się ponownie ani nic innego.  (Wersja 17.3.6943.0625 lub nowsza z wymaganej aplikacji do synchronizacji).

Jeśli użytkownik aktualizuje plik w trakcie przenoszenia OneDrive geolokalizacji, aplikacja do synchronizacji powiadomi go, że przekazywanie plików oczekuje na przekazanie w trakcie przenoszenia.

### <a name="sharing-links"></a>Udostępnianie linków

Po OneDrive przenoszenia geolokalizacji istniejące udostępnione linki dla plików, które zostały przeniesione, automatycznie przekierowują do nowej lokalizacji geograficznej.

### <a name="onenote-experience"></a>OneNote obsługi

OneNote klienta win32 i aplikacji UWP (uniwersalnej) automatycznie wykryją i bezproblemowo zsynchronizują notesy z nową lokalizacją OneDrive po zakończeniu przenoszenia geolokalizacji OneDrive. Użytkownik nie musi logować się ponownie ani nic innego. Jedynym widocznym wskaźnikiem dla użytkownika jest niepowodzenie synchronizacji notesu w OneDrive przenoszenia geolokalizacji. To środowisko jest dostępne w następujących OneNote klientach:

- OneNote win32 — wersja 16.0.8326.2096 (lub nowsza)
- OneNote UWP — wersja 16.0.8431.1006 (lub nowsza)
- OneNote dla urządzeń przenośnych — wersja 16.0.8431.1011 (lub nowsza)

### <a name="teams-app"></a>Teams aplikacji

Po OneDrive przenoszenia geolokalizacji użytkownicy będą mieli dostęp do swoich OneDrive plików w Teams lokalizacji geograficznej. Ponadto pliki udostępniane za pośrednictwem Teams na czacie z ich OneDrive przed przeniesieniem geograficznym będą nadal działać po zakończeniu przenoszenia.

### <a name="onedrive-mobile-app-ios"></a>OneDrive dla urządzeń przenośnych (iOS)

Po OneDrive przenoszenia geolokalizacji użytkownik musiałby się wylogować i zalogować ponownie w aplikacji mobilnej dla systemu iOS, aby zsynchronizować się z nową OneDrive lokalizacji.

### <a name="existing-followed-groups-and-sites"></a>Istniejące obserwowane grupy i witryny

Obserwowane witryny i grupy będą wyświetlane w wynikach OneDrive niezależnie od ich lokalizacji geograficznej. Witryny i grupy hostowane w innej lokalizacji geograficznej zostaną otwarte na osobnej karcie.

### <a name="delve-geo-url-updates"></a>aktualizacje Delve adresu URL lokalizacji geograficznej

Użytkownicy będą wysyłani do lokalizacji geograficznej Delve odpowiadającej ich plikom PDL dopiero po OneDrive ich lokalizacji geograficznej.
