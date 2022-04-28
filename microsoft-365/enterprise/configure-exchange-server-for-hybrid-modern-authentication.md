---
title: Jak skonfigurować Exchange Server lokalnie do korzystania z nowoczesnego uwierzytelniania hybrydowego
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak skonfigurować Exchange Server lokalnie do korzystania z nowoczesnego uwierzytelniania hybrydowego (HMA), oferując bezpieczniejsze uwierzytelnianie i autoryzację użytkowników.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2ee190a541fdf3e4e77a251e040f2cb69416088c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095757"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Jak skonfigurować Exchange Server lokalnie do korzystania z nowoczesnego uwierzytelniania hybrydowego

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Nowoczesne uwierzytelnianie hybrydowe (HMA) to metoda zarządzania tożsamościami, która oferuje bezpieczniejsze uwierzytelnianie i autoryzację użytkowników i jest dostępna w przypadku wdrożeń hybrydowych serwera Exchange.

## <a name="definitions"></a>Definicje

Przed rozpoczęciem należy zapoznać się z niektórymi definicjami:

- Hybrydowe nowoczesne uwierzytelnianie \> HMA

- Exchange lokalnie \> EXCH

- \> Exchange Online EXO

Ponadto *jeśli grafika w tym artykule zawiera obiekt "wyszarzony" lub "wygaszony", oznacza to, że element wyświetlany w kolorze szarym nie jest uwzględniony w konfiguracji specyficznej dla hma*.

## <a name="enabling-hybrid-modern-authentication"></a>Włączanie nowoczesnego uwierzytelniania hybrydowego

Włączenie hma oznacza:

1. Przed rozpoczęciem upewnij się, że spełniasz wymagania wstępne.

1. Ponieważ wiele **wymagań wstępnych jest typowych** zarówno dla Skype dla firm, jak i Exchange, [omówienie nowoczesnego uwierzytelniania hybrydowego i wymagania wstępne dotyczące korzystania z niego z serwerami lokalnymi Skype dla firm i serwerami Exchange](hybrid-modern-auth-overview.md). Należy to zrobić przed rozpoczęciem wykonywania jakichkolwiek kroków opisanych w tym artykule.
Wymagania dotyczące połączonych skrzynek pocztowych do wstawienia.

1. Dodawanie lokalnych adresów URL usługi internetowej jako **nazw głównych usług (SPN)** w usłudze Azure AD. Jeśli środowisko EXCH jest **hybrydowe z wieloma dzierżawami**, te lokalne adresy URL usługi internetowej muszą zostać dodane jako nazwy SPN w usłudze Azure AD wszystkich dzierżaw, które są w środowisku hybrydowym z usługą EXCH.

1. Zapewnianie, że wszystkie katalogi wirtualne są włączone dla usługi HMA

1. Sprawdzanie obiektu EvoSTS Auth Server

1. Włączanie usługi HMA w programie EXCH.

> [!NOTE]
> Czy twoja wersja Office obsługuje ma? Zobacz [Jak działa nowoczesne uwierzytelnianie dla aplikacji klienckich Office 2013 i Office 2016](modern-auth-for-office-2013-and-2016.md).

## <a name="make-sure-you-meet-all-the-prerequisites"></a>Upewnij się, że spełniasz wszystkie wymagania wstępne

Ponieważ wiele wymagań wstępnych jest typowych zarówno dla Skype dla firm, jak i Exchange, zapoznaj się [z omówieniem nowoczesnego uwierzytelniania hybrydowego i wymaganiami wstępnymi dotyczącymi używania go z lokalnymi serwerami Skype dla firm i Exchange](hybrid-modern-auth-overview.md). Należy to zrobić  *przed rozpoczęciem*  wykonywania jakichkolwiek kroków opisanych w tym artykule.

> [!NOTE]
> Outlook Web App i Exchange Panel sterowania nie współdziała z nowoczesnym uwierzytelnianiem hybrydowym.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Dodawanie lokalnych adresów URL usługi internetowej jako nazw SPN w usłudze Azure AD

Uruchom polecenia, które przypisują adresy URL lokalnej usługi internetowej jako nazwy SPN usługi Azure AD. Nazwy SPN są używane przez maszyny klienckie i urządzenia podczas uwierzytelniania i autoryzacji. Wszystkie adresy URL, które mogą służyć do nawiązywania połączenia ze środowiska lokalnego z usługą Azure Active Directory (Azure AD), muszą być zarejestrowane w usłudze Azure AD (obejmuje to zarówno wewnętrzne, jak i zewnętrzne przestrzenie nazw).

Najpierw zbierz wszystkie adresy URL, które należy dodać w AAD. Uruchom następujące polecenia lokalnie:

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

Upewnij się, że adresy URL, z którymi klienci mogą się łączyć, są wyświetlane jako nazwy główne usługi HTTPS w AAD. Jeśli exch jest w środowisku hybrydowym z **wieloma dzierżawami, te nazwy** SPN https powinny być dodawane w AAD wszystkich dzierżaw w środowisku hybrydowym z exch.

1. Najpierw połącz się z AAD, korzystając z [tych instrukcji](connect-to-microsoft-365-powershell.md).

    > [!NOTE]
    > Aby móc korzystać z poniższego polecenia, należy użyć opcji _Połączenie-MsolService_ na tej stronie.

2. W przypadku adresów URL związanych z Exchange wpisz następujące polecenie:

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   Zanotuj (i zrzut ekranu do późniejszego porównania) dane wyjściowe tego polecenia, które powinny zawierać `https://*autodiscover.yourdomain.com*` adres URL i `https://*mail.yourdomain.com*` , ale składają się głównie z `00000002-0000-0ff1-ce00-000000000000/`nazw SPN rozpoczynających się od . `https://` Jeśli brakuje adresów URL lokalnych, te konkretne rekordy powinny zostać dodane do tej listy.

3. Jeśli nie widzisz wewnętrznych i zewnętrznych rekordów MAPI/HTTP, EWS, ActiveSync, OAB i Autodiscover na tej liście, musisz dodać je przy użyciu poniższego polecenia (przykładowe adresy URL to `mail.corp.contoso.com` i `owa.contoso.com`, ale chcesz **zastąpić przykładowe adresy URL własnymi**):

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. Sprawdź, czy nowe rekordy zostały dodane, uruchamiając `Get-MsolServicePrincipal` ponownie polecenie z kroku 2 i przeglądając dane wyjściowe. Porównaj listę /zrzut ekranu z poprzedniego z nową listą nazw SPN. Możesz również wykonać zrzut ekranu przedstawiający nową listę rekordów. Jeśli pomyślnie się powiodło, na liście zostaną wyświetlone dwa nowe adresy URL. W naszym przykładzie lista nazw SPN będzie teraz zawierać określone adresy `https://mail.corp.contoso.com` URL i `https://owa.contoso.com`.

## <a name="verify-virtual-directories-are-properly-configured"></a>Sprawdź, czy katalogi wirtualne są prawidłowo skonfigurowane

Teraz sprawdź, czy uwierzytelnianie OAuth jest prawidłowo włączone w Exchange we wszystkich katalogach wirtualnych, Outlook mogą być używane, uruchamiając następujące polecenia:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Sprawdź dane wyjściowe, aby upewnić się, że **protokół OAuth** jest włączony dla każdego z tych katalogów VDir, będzie on wyglądać mniej więcej tak (a kluczową kwestią, na którą należy zwrócić uwagę, jest "OAuth"):

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

Jeśli brakuje protokołu OAuth na dowolnym serwerze i w dowolnym z czterech katalogów wirtualnych, należy dodać go przy użyciu odpowiednich poleceń przed kontynuowaniem ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory), [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory), [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) i [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Potwierdzanie obecności obiektu serwera uwierzytelniania EvoSTS

Wróć do lokalnej powłoki zarządzania Exchange dla tego ostatniego polecenia. Teraz możesz sprawdzić, czy w środowisku lokalnym jest dostępny wpis dla dostawcy uwierzytelniania evoSTS:

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

Dane wyjściowe powinny zawierać AuthServer nazwy EvoSts z identyfikatorem GUID, a stan "Włączone" powinien mieć wartość True. Jeśli tego nie widzisz, pobierz i uruchom najnowszą wersję Kreatora konfiguracji hybrydowej.

> [!NOTE]
> Jeśli środowisko EXCH jest w środowisku hybrydowym z **wieloma dzierżawami, dane wyjściowe** powinny zawierać jeden serwer AuthServer nazwy `EvoSts - {GUID}` dla każdej dzierżawy w środowisku hybrydowym z użyciem środowiska EXCH, a stan **Włączony** powinien mieć wartość True dla wszystkich tych obiektów AuthServer.

> [!IMPORTANT]
> Jeśli używasz programu Exchange 2010 w swoim środowisku, dostawca uwierzytelniania EvoSTS nie zostanie utworzony.

## <a name="enable-hma"></a>Włączanie usługi HMA

Uruchom następujące polecenie w lokalnej powłoce zarządzania Exchange, zastępując \<GUID\> w wierszu polecenia ciągiem w środowisku:

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> W starszych wersjach Kreatora konfiguracji hybrydowej evosts AuthServer został po prostu nazwany EvoSTS bez dołączonego identyfikatora GUID. Nie ma żadnej akcji, którą należy wykonać, po prostu zmodyfikuj powyższy wiersz polecenia, aby to odzwierciedlić, usuwając część identyfikatora GUID polecenia:
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

Jeśli wersja exch jest Exchange 2016 (CU18 lub nowsza) lub Exchange 2019 r. (CU7 lub nowsza) i została skonfigurowana hybrydowo z HCW pobranym po wrześniu 2020 r., uruchom następujące polecenie w lokalnej powłoki zarządzania Exchange:

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> Jeśli środowisko EXCH jest w środowisku hybrydowym z **wieloma dzierżawami**, w środowisku EXCH znajduje się wiele obiektów AuthServer z domenami odpowiadającymi każdej dzierżawie.  Flagę **IsDefaultAuthorizationEndpoint** należy ustawić na wartość true (przy użyciu polecenia cmdlet **IsDefaultAuthorizationEndpoint** ) dla dowolnego z tych obiektów AuthServer. Tej flagi nie można ustawić na wartość true dla wszystkich obiektów Authserver i hma zostanie włączona, nawet jeśli jeden z tych obiektów AuthServer **isdefaultAuthorizationEndpoint** flaga jest ustawiona na wartość true.
> 
> W przypadku parametru **DomainName** użyj wartości domeny dzierżawy, która zwykle ma postać `contoso.onmicrosoft.com`.

## <a name="verify"></a>Sprawdź

Po włączeniu usługi HMA podczas następnego logowania klienta zostanie użyty nowy przepływ uwierzytelniania. Pamiętaj, że samo włączenie usługi HMA nie spowoduje wyzwolenia ponownego uwierzytelniania dla żadnego klienta i może upłynąć trochę czasu, gdy Exchange odbierze nowe ustawienia.

Należy również przytrzymać klawisz CTRL w tym samym czasie, klikając prawym przyciskiem myszy ikonę klienta Outlook (również w obszarze powiadomień Windows) i kliknij pozycję Stan połączenia. Wyszukaj adres SMTP klienta względem typu `Bearer\*`**uwierzytelniania** , który reprezentuje token elementu nośnego używany w usłudze OAuth.

> [!NOTE]
> Chcesz skonfigurować Skype dla firm z usługą HMA? Potrzebne będą dwa artykuły: jeden zawierający [listę obsługiwanych topologii](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) i jeden, który pokazuje [, jak wykonać konfigurację](configure-skype-for-business-for-hybrid-modern-authentication.md).

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>Używanie nowoczesnego uwierzytelniania hybrydowego z Outlook dla systemów iOS i Android

Jeśli jesteś klientem lokalnym korzystającym z serwera Exchange na serwerze TCP 443, zezwalaj na ruch sieciowy z następujących zakresów adresów IP:

```console
52.125.128.0/20
52.127.96.0/23
```

Te zakresy adresów IP są również udokumentowane w [temacie Dodatkowe punkty końcowe, które nie są uwzględnione w usłudze sieci Web Office 365 adresów IP i adresów URL](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

## <a name="related-topics"></a>Tematy pokrewne

[Wymagania dotyczące konfiguracji nowoczesnego uwierzytelniania na potrzeby przejścia z Office 365 dedykowanego/ITAR do wersji vNext](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
