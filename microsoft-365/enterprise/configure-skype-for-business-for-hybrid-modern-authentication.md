---
title: Jak skonfigurować Skype dla firm lokalnie do korzystania z nowoczesnego uwierzytelniania hybrydowego
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak skonfigurować Skype dla firm lokalnie do korzystania z nowoczesnego uwierzytelniania hybrydowego (HMA), oferując bezpieczniejsze uwierzytelnianie i autoryzację użytkowników.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7f5e48905416f84ed1a4c48f7e6f1a4b6477f73e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093487"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Jak skonfigurować Skype dla firm lokalnie do korzystania z nowoczesnego uwierzytelniania hybrydowego

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Nowoczesne uwierzytelnianie to metoda zarządzania tożsamościami, która oferuje bezpieczniejsze uwierzytelnianie i autoryzację użytkowników, jest dostępna dla lokalnego serwera Skype dla firm i serwera Exchange lokalnie oraz hybrydowych Skype dla firm domeny podzielonej.

> [!IMPORTANT]
> Czy chcesz dowiedzieć się więcej na temat nowoczesnego uwierzytelniania (MA) i dlaczego warto używać go w swojej firmie lub organizacji? Zapoznaj [się z tym dokumentem](hybrid-modern-auth-overview.md) , aby zapoznać się z omówieniem. Jeśli musisz wiedzieć, jakie topologie Skype dla firm są obsługiwane przez ma, to jest to udokumentowane tutaj!

**Przed rozpoczęciem** używam następujących terminów:

- Nowoczesne uwierzytelnianie (MA)

- Nowoczesne uwierzytelnianie hybrydowe (HMA)

- Exchange lokalnie (EXCH)

- Exchange Online (EXO)

- Skype dla firm lokalnie (SFB)

- Skype dla firm Online (SFBO)

Ponadto jeśli grafika w tym artykule zawiera obiekt, który jest wyszarzony lub wygaszony, oznacza to, że element wyświetlany na szaro **nie jest** uwzględniony w konfiguracji specyficznej dla ma.

## <a name="read-the-summary"></a>Przeczytaj podsumowanie

To podsumowanie dzieli proces na kroki, które w przeciwnym razie mogłyby zostać utracone podczas wykonywania, i jest dobre dla ogólnej listy kontrolnej, aby śledzić, gdzie jesteś w procesie.

1. Najpierw upewnij się, że spełniasz wszystkie wymagania wstępne.

1. Ponieważ wiele **wymagań wstępnych jest typowych** zarówno dla Skype dla firm, jak i Exchange, [zapoznaj się z artykułem przeglądowym listy kontrolnej pre-req](hybrid-modern-auth-overview.md). Należy to zrobić  *przed rozpoczęciem*  wykonywania jakichkolwiek kroków opisanych w tym artykule.

1. Zbierz informacje specyficzne dla hma, które będą potrzebne w pliku lub OneNote.

1. Włącz nowoczesne uwierzytelnianie dla funkcji EXO (jeśli nie zostało jeszcze włączone).

1. Włącz nowoczesne uwierzytelnianie dla SFBO (jeśli nie zostało jeszcze włączone).

1. Włącz nowoczesne uwierzytelnianie hybrydowe dla Exchange lokalnie.

1. Włącz nowoczesne uwierzytelnianie hybrydowe dla Skype dla firm lokalnie.

Te kroki włączają usługę MA dla SFB, SFBO, EXCH i EXO — oznacza to, że wszystkie produkty, które mogą uczestniczyć w konfiguracji HMA SFB i SFBO (w tym zależności od EXCH/EXO). Innymi słowy, jeśli użytkownicy są w domu lub mają skrzynki pocztowe utworzone w dowolnej części hybrydowej (EXO + SFBO, EXO + SFB, EXCH + SFBO lub EXCH + SFB), gotowy produkt będzie wyglądać następująco:

![Topologia HMA mixed 6 Skype dla firm ma uprawnienia do prowadzenia działalności we wszystkich czterech możliwych lokalizacjach.](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)

Jak widać, istnieją cztery różne miejsca, w których można włączyć funkcję MA! Aby uzyskać najlepsze środowisko użytkownika, zalecamy włączenie funkcji ma we wszystkich czterech z tych lokalizacji. Jeśli nie możesz włączyć funkcji MA we wszystkich tych lokalizacjach, dostosuj kroki tak, aby włączyć ma tylko w lokalizacjach, które są niezbędne dla środowiska.

Aby uzyskać informacje na temat obsługiwanych topologii, zobacz [temat Supportability for Skype dla firm with MA (Obsługa funkcji Skype dla firm z](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) ma).

> [!IMPORTANT]
> Przed rozpoczęciem sprawdź, czy zostały spełnione wszystkie wymagania wstępne. Informacje te znajdują się w [temacie Omówienie nowoczesnego uwierzytelniania hybrydowego i wymagania wstępne](hybrid-modern-auth-overview.md).

## <a name="collect-all-hma-specific-info-youll-need"></a>Zbierz wszystkie potrzebne informacje specyficzne dla hma

Po dwukrotnym sprawdzeniu, czy spełniono [wymagania wstępne](hybrid-modern-auth-overview.md) dotyczące korzystania z nowoczesnego uwierzytelniania (zobacz powyższą notatkę), należy utworzyć plik do przechowywania informacji potrzebnych do skonfigurowania usługi HMA w ramach kroków opisanych wcześniej. Przykłady używane w tym artykule:

- **Domena SIP/SMTP**

  - Na przykład contoso.com (jest federowana z Office 365)

- **Identyfikator dzierżawy**

  - Identyfikator GUID reprezentujący dzierżawę Office 365 (przy logowaniu contoso.onmicrosoft.com).

- **Adresy URL usługi sieci Web SFB 2015 CU5**

Dla wszystkich wdrożonych pul SfB 2015 potrzebne będą wewnętrzne i zewnętrzne adresy URL usługi internetowej. Aby je uzyskać, uruchom następujące polecenie w usłudze Skype dla firm Management Shell:

```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Na przykład Wewnętrznego: https://lyncwebint01.contoso.com

- Na przykład Zewnętrznych: https://lyncwebext01.contoso.com

Jeśli używasz serwera Standard Edition, wewnętrzny adres URL będzie pusty. W takim przypadku użyj nazwy fqdn puli dla wewnętrznego adresu URL.

## <a name="turn-on-modern-authentication-for-exo"></a>Włączanie nowoczesnego uwierzytelniania dla funkcji EXO

Postępuj zgodnie z instrukcjami w tym miejscu: [Exchange Online: Jak włączyć dzierżawę na potrzeby nowoczesnego uwierzytelniania.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)

## <a name="turn-on-modern-authentication-for-sfbo"></a>Włączanie nowoczesnego uwierzytelniania dla SFBO

Postępuj zgodnie z instrukcjami w tym miejscu: [Skype dla firm Online: Włączanie dzierżawy na potrzeby nowoczesnego uwierzytelniania](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Włączanie nowoczesnego uwierzytelniania hybrydowego dla Exchange lokalnie

Postępuj zgodnie z instrukcjami w tym miejscu: [Jak skonfigurować Exchange Server lokalnie do korzystania z nowoczesnego uwierzytelniania hybrydowego](configure-exchange-server-for-hybrid-modern-authentication.md).

## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Włączanie nowoczesnego uwierzytelniania hybrydowego dla Skype dla firm lokalnego

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>Dodawanie lokalnych adresów URL usługi internetowej jako nazw SPN w Azure Active Directory

Teraz musisz uruchomić polecenia, aby dodać adresy URL (zebrane wcześniej) jako jednostki usługi w SFBO.

> [!NOTE]
> Nazwy główne usługi (SPN) identyfikują usługi sieci Web i kojarzą je z podmiotem zabezpieczeń (takim jak nazwa konta lub grupa), aby usługa mogła działać w imieniu autoryzowanego użytkownika. Klienci uwierzytelniający się na serwerze korzystają z informacji zawartych w sieciACH SPN.

1. Najpierw połącz się z usługą Azure Active Directory (Azure AD) za pomocą [tych instrukcji](/powershell/azure/active-directory/overview).

2. Uruchom to polecenie lokalnie, aby uzyskać listę adresów URL usługi internetowej SFB.

   Pamiętaj, że identyfikator AppPrincipalId zaczyna się od `00000004`. Odpowiada to Skype dla firm Online.

   Zanotuj (i zrzut ekranu do późniejszego porównania) dane wyjściowe tego polecenia, które będą zawierać adresy URL SE i WS, ale składają się głównie z `00000004-0000-0ff1-ce00-000000000000/`nazw SPN rozpoczynających się od .

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
   ```

3. Jeśli brakuje wewnętrznych **lub** zewnętrznych adresów URL SFB ze środowiska lokalnego (na przykład https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) należy dodać te określone rekordy do tej listy.

    Pamiętaj, aby zastąpić  *poniższe przykładowe adresy URL* rzeczywistymi adresami URL w poleceniach Dodaj!

    ```powershell
    $x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    $x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
    $x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
    Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
    ```

4. Sprawdź, czy nowe rekordy zostały dodane, uruchamiając ponownie polecenie **Get-MsolServicePrincipal** z kroku 2 i przeglądając dane wyjściowe. Porównaj listę lub zrzut ekranu z poprzedniego elementu z nową listą nazw SPN. Możesz również zrzut ekranu przedstawiający nową listę rekordów. Jeśli to się powiedzie, na liście zostaną wyświetlone dwa nowe adresy URL. W naszym przykładzie lista nazw SPN będzie teraz zawierać określone adresy https://lyncwebint01.contoso.com URL i https://lyncwebext01.contoso.com/.

### <a name="create-the-evosts-auth-server-object"></a>Tworzenie obiektu serwera uwierzytelniania EvoSTS

Uruchom następujące polecenie w powłoce zarządzania Skype dla firm.

```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>Włączanie nowoczesnego uwierzytelniania hybrydowego

Jest to krok, który faktycznie włącza ma. Wszystkie poprzednie kroki można wykonać z wyprzedzeniem bez zmiany przepływu uwierzytelniania klienta. Gdy wszystko będzie gotowe do zmiany przepływu uwierzytelniania, uruchom to polecenie w powłoce zarządzania Skype dla firm.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>Sprawdź

Po włączeniu usługi HMA podczas następnego logowania klienta zostanie użyty nowy przepływ uwierzytelniania. Pamiętaj, że samo włączenie usługi HMA nie spowoduje ponownego uwierzytelnienia dla żadnego klienta. Klienci ponownie uwierzytelniają się na podstawie okresu istnienia tokenów uwierzytelniania i/lub certyfikatów, które mają.

Aby sprawdzić, czy usługa HMA działa po włączeniu tej funkcji, wyloguj się z testowego klienta Windows SFB i kliknij pozycję "Usuń moje poświadczenia". Zaloguj się ponownie. Klient powinien teraz korzystać z przepływu nowoczesnego uwierzytelniania, a logowanie będzie teraz zawierać **Office 365** monit o konto służbowe widoczne tuż przed kontaktem klienta z serwerem i zalogowaniem się.

Należy również sprawdzić "Informacje o konfiguracji" dla klientów Skype dla firm dla "Urzędu OAuth". Aby to zrobić na komputerze klienckim, przytrzymaj wciśnięty klawisz CTRL jednocześnie, klikając prawym przyciskiem myszy ikonę Skype dla firm w zasobniku powiadomień Windows. Kliknij pozycję **Informacje o konfiguracji** w wyświetlonym menu. W oknie "informacje o konfiguracji Skype dla firm", które pojawią się na pulpicie, poszukaj następujących elementów:

:::image type="content" alt-text="Informacje o konfiguracji klienta Skype dla firm przy użyciu nowoczesnego uwierzytelniania pokazują adres URL urzędu OAUTH programu Lync i EWS o wartości https://login.windows.net/common/oauth2/authorize." source="../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png":::

Należy również przytrzymać klawisz CTRL w tym samym czasie, klikając prawym przyciskiem myszy ikonę klienta Outlook (również w obszarze powiadomień Windows) i kliknij pozycję Stan połączenia. Wyszukaj adres SMTP klienta względem typu AuthN "Bearer\*", który reprezentuje token elementu nośnego używany w usłudze OAuth.

## <a name="related-articles"></a>Artykuły pokrewne

[Link z powrotem do przeglądu nowoczesnego uwierzytelniania](hybrid-modern-auth-overview.md).

Czy musisz wiedzieć, jak używać nowoczesnego uwierzytelniania dla klientów Skype dla firm? Poniżej przedstawiono kroki: [omówienie nowoczesnego uwierzytelniania hybrydowego i wymagania wstępne dotyczące używania go z lokalnymi serwerami Skype dla firm i Exchange](./hybrid-modern-auth-overview.md).
