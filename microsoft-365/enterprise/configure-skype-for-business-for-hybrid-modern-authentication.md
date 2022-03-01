---
title: Jak skonfigurować nowoczesne Skype dla firm w środowisku lokalnym
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Dowiedz się, jak skonfigurować Skype dla firm w środowisku lokalnym na użytek nowoczesnego uwierzytelniania hybrydowego, co zapewnia większe bezpieczeństwo w uwierzytelnianiu i autoryzacji użytkowników.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dd42aa6befdbb646217a9829dd59c0821fbd29d3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996298"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Jak skonfigurować nowoczesne Skype dla firm w środowisku lokalnym

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Nowoczesne uwierzytelnianie to metoda zarządzania tożsamościami, która zapewnia bezpieczniejsze uwierzytelnianie i autoryzację użytkowników, która jest dostępna dla lokalnego serwera Skype dla firm i lokalnego serwera Exchange oraz konfiguracji hybrydowych Skype dla firm dzielonych domen.

> [!IMPORTANT]
> Chcesz dowiedzieć się więcej o nowoczesnym uwierzytelnianiu i dlaczego warto używać go w swojej firmie lub organizacji? Aby [uzyskać omówienie,](hybrid-modern-auth-overview.md) zapoznaj się z tym dokumentem. Jeśli chcesz się dowiedzieć, Skype dla firm które topologii są obsługiwane przez mazowieńską, o tym tutaj po dokumentacji!

**Zanim zaczniemy**, używam tych postanowień:

- Nowoczesne uwierzytelnianie

- Nowoczesne uwierzytelnianie hybrydowe (HMA)

- Exchange lokalnym (EXCH)

- Exchange Online (EXO)

- Skype dla firm lokalne (RZB)

- Skype dla firm online (SFBO)

Ponadto jeśli grafika w tym artykule zawiera obiekt wyszarzony lub wyszarzony, co oznacza, że element pokazany na szaro nie jest uwzględniony w konfiguracji specyficznej dla funkcji ma.

## <a name="read-the-summary"></a>Odczytywanie podsumowania

To podsumowanie dzieli proces na etapy, które w przeciwnym razie zostaną utracone podczas wykonywania, i stanowi ogólną listę kontrolną do śledzenia tego, w którym miejscu procesu się znajdujesz.

1. Najpierw upewnij się, że są spełnione wszystkie wymagania wstępne.

1. Ponieważ wiele **wymagań wstępnych** jest wspólnych zarówno Skype dla firm, jak i Exchange, zobacz artykuł z omówieniem wstępnej listy [kontrolnej](hybrid-modern-auth-overview.md). Zrób to  *przed*  rozpoczęciem jakiejkolwiek czynności opisanej w tym artykule.

1. Zbierz informacje dotyczące programu HMA, których będziesz potrzebować, w pliku lub OneNote.

1. Włącz nowoczesne uwierzytelnianie dla exo (jeśli nie jest jeszcze włączone).

1. Włącz nowoczesne uwierzytelnianie dla serwisu SFBO (jeśli nie zostało jeszcze włączone).

1. Włącz nowoczesne uwierzytelnianie hybrydowe dla Exchange lokalnego.

1. Włącz nowoczesne uwierzytelnianie hybrydowe dla Skype dla firm lokalnego.

Ta procedura włączy mazowieńską usługę SFB, SFBO, EXCH i EXO, czyli wszystkie produkty, które mogą uczestniczyć w konfiguracji HMA sfb i SFBO (w tym zależności od exch/EXO). Innymi słowy, jeśli użytkownicy znajdują się w skrzynkach pocztowych utworzonych w dowolnej części środowiska hybrydowego (EXO + SFBO, EXO + SFB, EXCH + SFBO lub EXCH + SFB), gotowy produkt będzie wyglądał tak:

![W topologii mieszanej 6 Skype hma dla firm jest wł. maj we wszystkich czterech możliwych lokalizacjach.](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)

Jak widać, są cztery różne miejsca, w których można włączyć włączyną mazowieńską. Aby uzyskać najlepsze środowisko użytkownika, zalecamy włączenie obsługi makra we wszystkich czterech z tych lokalizacji. Jeśli nie można włączyć makra ma być w tych wszystkich lokalizacjach, dostosuj kroki tak, aby włączyć ma być tylko w tych lokalizacjach, które są niezbędne dla Twojego środowiska.

Aby uzyskać [informacje o obsługiwanych topologii, Skype dla firm temat](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) Możliwości obsługi.

> [!IMPORTANT]
> Przed rozpoczęciem upewnij się, że zostały spełnione wszystkie wymagania wstępne. Aby uzyskać te informacje, zobacz Omówienie i wymagania wstępne [nowoczesnego uwierzytelniania hybrydowego](hybrid-modern-auth-overview.md).

## <a name="collect-all-hma-specific-info-youll-need"></a>Zbierz wszystkie potrzebne informacje dotyczące hma

Po dwukrotnym sprawdzeniu, czy są spełnione wymagania wstępne [](hybrid-modern-auth-overview.md) dotyczące używania nowoczesnego uwierzytelniania (patrz uwaga powyżej), należy utworzyć plik, w celu przechowywania informacji potrzebnych do skonfigurowania usługi HMA w instrukcje z instrukcjami. Przykłady użyte w tym artykule:

- **Domena SIP/SMTP**

  - Na przykład contoso.com (jest w federacji z Office 365)

- **Identyfikator dzierżawy**

  - Identyfikator GUID reprezentujący Twoją dzierżawę Office 365 (podczas logowania contoso.onmicrosoft.com).

- **Adresy URL usługi sieci Web SFB 2015 CU5**

Potrzebne są wewnętrzne i zewnętrzne adresy URL usług sieci Web dla wszystkich wdrożonych pul sfB 2015. Aby je uzyskać, uruchom następujące elementy z Skype dla firm zarządzania:

```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Na przykład Wewnętrzna: https://lyncwebint01.contoso.com

- Na przykład Zewnętrzne: https://lyncwebext01.contoso.com

Jeśli korzystasz z serwera Standard Edition, wewnętrzny adres URL będzie pusty. W tym przypadku użyj głównej domeny puli dla wewnętrznego adresu URL.

## <a name="turn-on-modern-authentication-for-exo"></a>Włączanie nowoczesnego uwierzytelniania dla usługi EXO

Wykonaj instrukcje tutaj: [Exchange Online: Jak włączyć nowoczesne uwierzytelnianie dla dzierżawy.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)

## <a name="turn-on-modern-authentication-for-sfbo"></a>Włączanie nowoczesnego uwierzytelniania dla usługi SFBO

Postępuj zgodnie z instrukcjami tutaj: [Skype dla firm Online: Włączanie nowoczesnego uwierzytelniania dla dzierżawy](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Włączanie nowoczesnego uwierzytelniania hybrydowego Exchange lokalnego

Wykonaj instrukcje tutaj: [Jak skonfigurować lokalne Exchange Server na używanie nowoczesnego uwierzytelniania hybrydowego](configure-exchange-server-for-hybrid-modern-authentication.md).

## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Włączanie nowoczesnego uwierzytelniania hybrydowego Skype dla firm lokalnego

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>Dodawanie lokalnych adresów URL usług sieci Web jako sieci SPN w Azure Active Directory

Teraz musisz uruchomić polecenia, aby dodać adresy URL (zgromadzone wcześniej) jako podmioty zabezpieczeń usługi w serwisie SFBO.

> [!NOTE]
> Nazwy główne usług (nazwy SPN) identyfikują usługi sieci Web i kojarzą je z podmiotem zabezpieczeń (takim jak nazwa konta lub grupa), aby usługa działała w imieniu upoważnionego użytkownika. Klienci uwierzytelniający się na serwerze używają informacji zawartych w nazwach SPN.

1. Najpierw połącz się z usługą Azure Active Directory (Azure AD) za pomocą [tych instrukcji](/powershell/azure/active-directory/overview).

2. Uruchom to polecenie (lokalnie), aby uzyskać listę adresów URL usługi sieci Web SFB.

   Zwróć uwagę, że appPrincipalId zaczyna się od `00000004`. Odpowiada to ujm Skype dla firm online.

   Zanotuj (i zanotuj zrzut ekranu w celu późniejszego porównania) danych wyjściowych tego polecenia, które będą zawierać adresy URL SE i WS, ale głównie będą zawierać spN, które zaczynają się od `00000004-0000-0ff1-ce00-000000000000/`.

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
   ```

3. W przypadku braku **wewnętrznych lub** zewnętrznych adresów URL SFB ze źródeł lokalnych ( https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) na przykład trzeba dodać te konkretne rekordy do tej listy).

    Pamiętaj, aby zastąpić poniższe  *przykładowe adresy URL* rzeczywistymi adresami URL w poleceniach Dodaj.

    ```powershell
    $x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    $x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
    $x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
    Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
    ```

4. Sprawdź, czy nowe rekordy zostały dodane, uruchamiając ponownie polecenie **Get-MsolServicePrincipal** z kroku 2 i patrząc na wyniki. Porównaj listę lub zrzut ekranu z nową listą sieci SPN. Możesz również zrzuć zrzut ekranu nowej listy rekordów. Jeśli udało Ci się, zobaczysz na liście dwa nowe adresy URL. W naszym przykładzie lista sieci SPN będzie teraz zawierać określone adresy URL https://lyncwebint01.contoso.com i https://lyncwebext01.contoso.com/.

### <a name="create-the-evosts-auth-server-object"></a>Tworzenie obiektu serwera authsts

Uruchom następujące polecenie w Skype dla firm zarządzania danymi.

```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>Włączanie nowoczesnego uwierzytelniania hybrydowego

Jest to krok, który w rzeczywistości włącza się w programie MI. Wszystkie poprzednie kroki można uruchomić z wyprzedzeniem bez zmieniania przepływu uwierzytelniania klienta. Gdy wszystko będzie gotowe do zmiany przepływu uwierzytelniania, uruchom to polecenie w Skype dla firm zarządzania danymi.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>Weryfikuj

Po włączeniu usługi HMA następny identyfikator logowania klienta będzie używać nowego przepływu uwierzytelniania. Pamiętaj, że włączenie usługi HMA nie spowoduje wyzwolenia ponownego uwierzytelniania dla żadnego klienta. Klienci ponownie uwierzytelniają się na podstawie okresu istnienia posiadanych tokenów uwierzytelniania i/lub certyfikatów.

Aby sprawdzić, czy funkcja HMA działa po jej włączeniu, wyloguj się z testowego klienta Windows SFB i kliknij pozycję Usuń moje poświadczenia. Zaloguj się ponownie. Klient powinien teraz korzystać z przepływu nowoczesnego uwierzytelniania, **Office 365** logowanie będzie zawierać monit o "konto służbowe" wyświetlany bezpośrednio przed kontaktem klienta z serwerem i zalogowaniem.

Należy również sprawdzić informacje o konfiguracji dla klientów Skype dla firm OAuth Authority. Aby to zrobić na komputerze klienckim, przytrzymaj naciśnięty klawisz CTRL i kliknij prawym przyciskiem myszy ikonę Skype dla firm w pasku Windows powiadomień. W **wyświetlonym** menu kliknij pozycję Informacje o konfiguracji. W oknie Skype dla firm konfiguracji komputera, które pojawi się na pulpicie, poszukaj następujących informacji:

:::image type="content" alt-text="Informacje o konfiguracji klienta programu Skype dla firm korzystającym z nowoczesnego uwierzytelniania pokazują adres URL programu Lync i urzędu OAUTH ews oauth o adresie URL .https://login.windows.net/common/oauth2/authorize" source="../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png":::

Należy również przytrzymać naciśnięty klawisz CTRL w tym samym czasie, gdy klikniesz prawym przyciskiem myszy ikonę klienta usługi Outlook (również w pasku powiadomień systemu Windows) i kliknij pozycję "Stan połączenia". Odszukaj adres SMTP klienta dla typu AuthN użytkownika "Bearer\*", który reprezentuje token użytkownika używanego w uwierzytelniania OAuth.

## <a name="related-articles"></a>Artykuły pokrewne

[Wróć do przeglądu nowoczesnego uwierzytelniania](hybrid-modern-auth-overview.md).

Chcesz się dowiedzieć, jak używać nowoczesnego uwierzytelniania dla swoich klientów Skype dla firm klientów? Poniżej przedstawiono kroki: Omówienie nowoczesnego uwierzytelniania hybrydowego i wymagania wstępne dotyczące używania go z lokalnymi Skype dla firm i [Exchange lokalnymi](./hybrid-modern-auth-overview.md).
