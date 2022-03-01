---
title: Jak skonfigurować nowoczesne Exchange Server w środowisku lokalnym
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/27/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Dowiedz się, jak skonfigurować Exchange Server w środowisku lokalnym na użytek nowoczesnego uwierzytelniania hybrydowego, co zapewnia większe bezpieczeństwo w uwierzytelnianiu i autoryzacji użytkowników.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d0889008595717308695c1ad9c5d2a9f1766d1ea
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021328"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Jak skonfigurować nowoczesne Exchange Server w środowisku lokalnym

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Nowoczesne uwierzytelnianie hybrydowe (HMA, Hybrid Modern Authentication) jest metodą zarządzania tożsamością, która oferuje bezpieczniejsze uwierzytelnianie i autoryzację użytkowników oraz jest dostępna Exchange lokalnych wdrożeń hybrydowych na serwerze.

## <a name="definitions"></a>Definicje

Przed rozpoczęciem należy zapoznać się z pewnymi definicjami:

- Nowoczesne uwierzytelnianie hybrydowe \> HMA

- Exchange lokalnym \> EXCH

- \> Exchange Online EXO

Ponadto jeśli grafika w tym artykule zawiera obiekt, który jest "wyszarzony" lub "wyszarzony", co oznacza, że element pokazany na szaro nie jest uwzględniony w konfiguracji specyficznej dla usługi *HMA*.

## <a name="enabling-hybrid-modern-authentication"></a>Włączanie nowoczesnego uwierzytelniania hybrydowego

Włączenie oznacza hma:

1. Przed rozpoczęciem upewnij się, że spełniasz wymagania wstępne.

1. Ponieważ wiele **wymagań wstępnych** jest wspólnych zarówno dla usług Skype dla firm, jak i Exchange, omówienie i wymagania wstępne nowoczesnego uwierzytelniania hybrydowego dotyczące używania go z lokalnymi Skype dla firm i Exchange [serwerami](hybrid-modern-auth-overview.md). Zrób to przed rozpoczęciem jakiejkolwiek czynności opisanej w tym artykule.
Wymagania dotyczące wstawianych połączonych skrzynek pocztowych.

1. Dodanie lokalnych adresów URL usług sieci Web jako **głównych nazw usług (SPN) w** usłudze Azure AD. Jeśli usługa EXCH jest w trybie hybrydowym z wieloma dzierżawami **, te** lokalne adresy URL usług sieci Web należy dodać jako adresy SPN w usłudze Azure AD wszystkich dzierżaw, które są w trybie hybrydowym z usługą EXCH.

1. Zapewnianie, że wszystkie katalogi wirtualne są włączone dla hma

1. Checking for theInalSTS Auth Server object

1. Włączanie hma w programie EXCH.

> [!NOTE]
> Czy Twoja wersja programu Office obsługuje mazowieńską? Zobacz [Jak działa nowoczesne uwierzytelnianie w aplikacjach Office 2013 i Office 2016](modern-auth-for-office-2013-and-2016.md).

## <a name="make-sure-you-meet-all-the-prerequisites"></a>Upewnij się, że są spełnione wszystkie wymagania wstępne

Ponieważ wiele wymagań wstępnych jest wspólnych zarówno dla usług Skype dla firm, jak i Exchange, zapoznaj się z omówieniem nowoczesnego uwierzytelniania hybrydowego i z omówieniem jego używania z lokalnymi Skype dla firm i Exchange [serwerami](hybrid-modern-auth-overview.md). Zrób to  *przed*  rozpoczęciem jakiejkolwiek czynności opisanej w tym artykule.

> [!NOTE]
> Outlook Web App i Exchange nie działa z nowoczesnym uwierzytelnianiem hybrydowym.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Dodawanie lokalnych adresów URL usługi sieci Web jako sieci SPN w usłudze Azure AD

Uruchom polecenia, które przypiszą adresy URL lokalnych usług sieci Web jako adresy SPN usługi Azure AD. Sieci SPN są używane przez komputery klienckie i urządzenia podczas uwierzytelniania i autoryzacji. Wszystkie adresy URL, które mogą być używane do łączenia się z lokalnego połączenia z usługą Azure Active Directory (Azure AD) muszą być zarejestrowane w usłudze Azure AD (dotyczy to zarówno wewnętrznych, jak i zewnętrznych przestrzeni nazw).

Najpierw zbierz wszystkie adresy URL, które chcesz dodać w AAD. Uruchom te polecenia lokalnie:

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

Upewnij się, że klienci z adresami URL mogą się łączyć, są wymienione jako nazwy główne usługi HTTPS w AAD. Jeśli program EXCH jest w trybie hybrydowym z wieloma dzierżawami **, te** sieci SPN https powinny zostać dodane AAD we wszystkich dzierżawach we współpracy hybrydowej z usługą EXCH.

1. Najpierw połącz się z AAD, instrukcji[.](connect-to-microsoft-365-powershell.md)

    > [!NOTE]
    > Aby użyć poniższego polecenia, należy użyć opcji _Połączenie-MsolService_ z tej strony.

2. W Exchange URL powiązanych ze swoimi adresami URL wpisz następujące polecenie:

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   Zanotuj (i zanotuj zrzut ekranu w celu późniejszego porównania) danych wyjściowych tego polecenia, `https://*autodiscover.yourdomain.com*` `https://*mail.yourdomain.com*` które powinno zawierać adres URL i ale głównie zawierają spN, które zaczynają się od `00000002-0000-0ff1-ce00-000000000000/`. Jeśli brakuje `https://` adresów URL w środowisku lokalnym, należy dodać te konkretne rekordy do tej listy.

3. Jeśli na tej liście nie widzisz wewnętrznych i zewnętrznych rekordów MAPI/HTTP, EWS, ActiveSync, OAB i wykrywania automatycznego, musisz je dodać za pomocą poniższego polecenia (przykładowe adresy URL `mail.corp.contoso.com` `owa.contoso.com`to i , ale zamienisz przykładowe adresy **URL** na własne):

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. Sprawdź, czy nowe rekordy zostały dodane, uruchamiając `Get-MsolServicePrincipal` ponownie polecenie z kroku 2 i patrząc na wyniki. Porównaj listę /zrzut ekranu z listy "przedtem" z nową listą sieci SPN. Możesz również zrobić zrzut ekranu nowej listy rekordów. Jeśli udało Ci się to zrobić, zostaną one zobaczyć na liście dwa nowe adresy URL. W naszym przykładzie lista sieci SPN będzie teraz zawierać określone adresy URL `https://mail.corp.contoso.com` i `https://owa.contoso.com`.

## <a name="verify-virtual-directories-are-properly-configured"></a>Sprawdzanie, czy katalogi wirtualne są poprawnie skonfigurowane

Teraz sprawdź, czy funkcja OAuth jest poprawnie włączona Exchange we wszystkich wirtualnych katalogach, Outlook użyć, uruchamiając następujące polecenia:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Sprawdź dane wyjściowe, aby upewnić się, że funkcja **OAuth** jest włączona w każdej z tych katalogów VDirs. Będzie ona wyglądać podobnie do następującego (a kluczową rzeczą, którą należy sprawdzić, jest "OAuth").):

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

Jeśli brakuje protokołu OAuth na dowolnym serwerze i w dowolnym z czterech katalogów wirtualnych, przed rozpoczęciem należy go dodać przy użyciu odpowiednich poleceń ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory), [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory), [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) i [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Sprawdzanie, czy obiekt Serwer AuthSTS jest obecny

Wróć do lokalnej powłoki zarządzania Exchange zarządzanie dla tego ostatniego polecenia. Teraz możesz sprawdzić, czy twój dostawca uwierzytelniania lokalnego ma wpis:

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

W wynikach powinien być pokazywany serwer uwierzytelniania nazw z identyfikatorem GUID, a stan "Włączony" powinien mieć wartość True. Jeśli nie widzisz tej informacji, pobierz i uruchom najnowszą wersję Kreatora konfiguracji hybrydowej.

> [!NOTE]
> Jeśli program EXCH jest w trybie hybrydowym z wieloma dzierżawami **,**`EvoSts - {GUID}` w wynikach powinien być pokazywany jeden serwer uwierzytelniania Name (Nazwa) dla każdej dzierżawy we współpracy hybrydowej z usługą EXCH, a stan **Enabled** (Włączone) powinien mieć wartość True (Prawda) dla wszystkich tych obiektów AuthServer (Serwer uwierzytelniania).

> [!IMPORTANT]
> Jeśli używasz w swoim środowisku Exchange 2010, dostawca uwierzytelniania OsóbStS nie zostanie utworzony.

## <a name="enable-hma"></a>Włączanie HMA

Uruchom następujące polecenie w lokalnej Exchange zarządzania, \<GUID\> zastępując w wierszu polecenia ciągiem w środowisku:

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> W starszych wersjach Kreatora konfiguracji hybrydowej serwer AuthServers został po prostu nazwany NastS bez dołączonego identyfikatora GUID. Nie trzeba nic zrobić. Wystarczy zmodyfikować wiersz polecenia powyżej, aby odzwierciedlał ten przykład, usuwając część identyfikatora GUID polecenia:
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

Jeśli wersja EXCH to Exchange 2016 (CU18 lub nowsza wersja) albo Exchange 2019 (CU7 lub nowsza wersja), a w środowisku hybrydowym skonfigurowano usługę hcw pobraną po wrześniu 2020 r., uruchom następujące polecenie w lokalnej powłoki zarządzania programu Exchange:

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> W przypadku, gdy program EXCH jest w trybie hybrydowym z wieloma dzierżawami **, istnieje** wiele obiektów AuthServer w programie EXCH z domenami odpowiadającymi każdej dzierżawie.  **Flaga IsDefaultAuthorizationEndpoint** powinna mieć wartość true (przy użyciu polecenia cmdlet **IsDefaultAuthorizationEndpoint**) dla dowolnego z tych obiektów AuthServer. Dla wszystkich obiektów serwera uwierzytelniania nie można ustawić wartości true, a funkcja HMA zostanie włączona, nawet jeśli dla flagi **IsDefaultAuthorizationEndpoint** obiektu AuthServer jest ustawiona wartość true.
> 
> W **parametrze DomainName** użyj wartości domeny dzierżawy, która zwykle znajduje się w formularzu `contoso.onmicrosoft.com`.

## <a name="verify"></a>Weryfikuj

Po włączeniu usługi HMA następny identyfikator logowania klienta będzie używać nowego przepływu uwierzytelniania. Pamiętaj, że włączenie usługi HMA nie spowoduje wyzwolenia ponownego uwierzytelniania dla żadnego klienta, a może upłynie trochę czasu, Exchange nowe ustawienia.

Należy również przytrzymać naciśnięty klawisz CTRL w tym samym czasie, gdy klikniesz prawym przyciskiem myszy ikonę klienta usługi Outlook (również w pasku powiadomień systemu Windows) i kliknij pozycję "Stan połączenia". Odszukaj adres SMTP klienta dla **typu Uwierzytelniania** `Bearer\*`, który reprezentuje token użytkownika używany w uwierzytelniania OAuth.

> [!NOTE]
> Musisz skonfigurować Skype dla firm HMA? Potrzebne są dwa artykuły: jeden z listą obsługiwanych [topologii](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) i jeden, w których pokazano, [jak wykonać konfigurację](configure-skype-for-business-for-hybrid-modern-authentication.md).

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>Używanie hybrydowego nowoczesnego uwierzytelniania z Outlook dla systemów iOS i Android

Jeśli jesteś klientem lokalnym korzystającym z serwera Exchange tcp 443, zezwalaj na ruch sieciowy z następujących zakresów adresów IP:

```console
52.125.128.0/20
52.127.96.0/23
```

Te zakresy adresów IP również o dokumencie Dodatkowe punkty końcowe nie są dostępne w usłudze sieci [Office 365 adres IP i usługa sieci Web adresów URL](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

## <a name="related-topics"></a>Tematy pokrewne

[Wymagania dotyczące konfiguracji nowoczesnego uwierzytelniania dotyczące przechodzenia z Office 365/ITAR na vNext](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
