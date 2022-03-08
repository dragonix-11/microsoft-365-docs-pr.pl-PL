---
title: Omówienie nowoczesnego uwierzytelniania hybrydowego i wymagania wstępne dotyczące używania z lokalnymi Skype dla firm i Exchange lokalnymi
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 12/03/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: W tym artykule dowiesz się więcej o nowoczesnym uwierzytelnianiu hybrydowym i wymaganiach wstępnych dotyczących używania z lokalnymi Skype dla firm i Exchange lokalnymi.
ms.openlocfilehash: efce3b5a04f2e9500330cab87d7ba8e62ca49db0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312869"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Omówienie i wymagania wstępne dotyczące nowoczesnego uwierzytelniania hybrydowego dotyczące używania go z lokalnymi Skype dla firm i Exchange lokalnymi

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

_Nowoczesne uwierzytelnianie_ to metoda zarządzania tożsamością, która zapewnia bezpieczniejsze uwierzytelnianie i autoryzację użytkowników. Jest on dostępny w Office 365 hybrydowych wdrożeń Skype dla firm serwera lokalnego i Exchange lokalnego serwera oraz konfiguracji Skype dla firm hybrydowych. Ten artykuł zawiera linki do powiązanych dokumentów dotyczących wymagań wstępnych, konfigurowania/wyłączania nowoczesnego uwierzytelniania oraz niektórych powiązanych dokumentów (np. Outlook i Skype klientów).

- [Co to jest nowoczesne uwierzytelnianie?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Jakie zmiany wprowadzam, gdy używam nowoczesnego uwierzytelniania?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Sprawdzanie stanu nowoczesnego uwierzytelniania w środowisku lokalnym](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Czy spełniasz wymagania wstępne dotyczące nowoczesnego uwierzytelniania?](#do-you-meet-modern-authentication-prerequisites)
- [Co jeszcze należy wiedzieć przed rozpoczęciem?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Co to jest nowoczesne uwierzytelnianie?
<a name="BKMK_WhatisModAuth"> </a>

Nowoczesne uwierzytelnianie to termin parasolowy, który zapewnia połączenie metod uwierzytelniania i autoryzacji między klientem (na przykład laptopem lub telefonem) a serwerem, a także niektóre zabezpieczenia oparte na zasadach dostępu, które być może znasz. Oto co obejmuje:

- **Metody uwierzytelniania**: uwierzytelnianie wieloskładnikowe (MFA); uwierzytelnianie karty inteligentnej; uwierzytelnianie klienta oparte na certyfikatach
- **Metody autoryzacji**: Implementacja open authorization (OAuth) firmy Microsoft
- **Zasady dostępu warunkowego**: Dostęp warunkowy zarządzanie aplikacjami mobilnymi (MAM) i Azure Active Directory (Azure AD)

Zarządzanie tożsamościami użytkowników za pomocą nowoczesnego uwierzytelniania zapewnia administratorom wiele różnych narzędzi do wykorzystania w zakresie zabezpieczania zasobów i oferuje bezpieczniejsze metody zarządzania tożsamością zarówno w scenariuszach lokalnych (Exchange i Skype dla firm Exchange), hybrydowych oraz Skype dla firm hybrydowych/podzielonych domenach.

Ponieważ Skype dla firm ściśle współpracuje z usługą Exchange, na zachowanie logowania Skype dla firm klientów będzie miał wpływ stan nowoczesnego uwierzytelniania usługi Exchange. Ma to również zastosowanie, jeśli masz architekturę hybrydową Skype dla firm, w której masz zarówno usługę Skype dla firm Online, jak i Skype dla firm lokalną, z użytkownikami w obu tych lokalizacjach.

Aby uzyskać więcej informacji na temat nowoczesnego uwierzytelniania Office 365, zobacz pomoc [Office 365 aplikacji klienckiej — uwierzytelnianie wieloskładnikowe](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> Od sierpnia 2017 r. wszystkie nowe dzierżawy usług Office 365, które zawierają usługę Skype dla firm Online i Exchange online, będą domyślnie włączone nowoczesne uwierzytelnianie. Istniejące już dzierżawy nie będą mieć zmiany w ich domyślnym stanie zarządzania tożsamościami, ale wszystkie nowe dzierżawy automatycznie obsługują rozwinięty zestaw funkcji tożsamości, które są wyświetlane powyżej. Aby sprawdzić stan usługi uwierzytelniania lokalnego, zobacz sekcję Sprawdzanie stanu nowoczesnego uwierzytelniania [w środowisku lokalnym](hybrid-modern-auth-overview.md#BKMK_CheckStatus) .

## <a name="what-changes-when-i-use-modern-authentication"></a>Jakie zmiany wprowadzam, gdy używam nowoczesnego uwierzytelniania?
<a name="BKMK_WhatChanges"> </a>

Podczas korzystania z nowoczesnego uwierzytelniania z lokalnym serwerem Skype dla firm lub Exchange nadal uwierzytelnianie użytkowników lokalnych jest procesem uwierzytelniania, ale  proces tworzenia ich dostępu do zasobów (takich jak pliki lub  wiadomości e-mail) zmienia się. Dlatego, chociaż nowoczesne uwierzytelnianie dotyczy komunikacji z klientem i serwerem, czynności wykonane podczas konfigurowania usługi MA spowodują ustawienie usługi tokenu zabezpieczającego używanej przez usługę Azure AD jako serwera uwierzytelniania dla lokalnego serwera Skype dla firm i Exchange.

Zmiana na usługę tokenS umożliwia Twoim serwerom lokalnym korzystanie z protokołu OAuth (wydawanie tokenów) w celu autoryzacji Twoich klientów, a także umożliwia Twoim lokalnym metodom zabezpieczeń najczęściej występującym w chmurze (na przykład uwierzytelnianie wieloskładnikowe). Ponadto użytkownicy mogą zażądać dostępu do zasobów bez podaniem hasła w ramach żądania przez użytkownika. Niezależnie od miejsca zamieszkania użytkowników (w trybie online lub lokalnym) i niezależnie od tego, która lokalizacja hostuje potrzebny zasób, podstawową zasadą autoryzowania użytkowników i klientów po skonfigurowaniu nowoczesnego uwierzytelniania stanie się ich podstawowa metoda.

Jeśli na przykład klient usługi Skype dla firm musi uzyskać dostęp do serwera Exchange w celu uzyskania informacji kalendarza w imieniu użytkownika, korzysta z biblioteki uwierzytelniania firmy Microsoft (MSAL, Microsoft Authentication Library). MSAL to biblioteka kodów zaprojektowana w celu udostępnienia zabezpieczonych zasobów w katalogu aplikacjom klienckim przy użyciu tokenów zabezpieczeń OAuth. Program MSAL współpracuje z protokołu OAuth w celu weryfikowania roszczeń i wymiany tokenów (a nie haseł) w celu udzielenia użytkownikowi dostępu do zasobu. W przeszłości urząd w transakcji takiej jak ta — serwer, który potrafi weryfikować roszczenia użytkowników i wydawać wymagane tokeny — mógł to być lokalnie usługa tokenu zabezpieczeń, a nawet usługi federacyjnych Active Directory. Nowoczesne uwierzytelnianie scentralizować jednak to właściwe uprawnienia przy użyciu usługi Azure AD.

Oznacza to również, że nawet jeśli środowiska serwera Exchange i programu Skype dla firm mogą być całkowicie lokalne, serwer autoryzowania będzie w trybie online, a środowisko lokalne musi mieć możliwość tworzenia i utrzymywania połączenia z subskrypcją usługi Office 365 w chmurze (i wystąpieniu usługi Azure AD, które używa twojej subskrypcji jako katalogu).

Co się nie zmienia? Niezależnie od tego, czy korzystasz z konfiguracji hybrydowej podzielonej domeny, czy używasz lokalnego Skype dla firm i Exchange, wszyscy użytkownicy muszą najpierw uwierzytelnić *się lokalnie*. W hybrydowej implementacji nowoczesnego uwierzytelniania usługi _lyncdiscovery_ i _wykrywania automatycznego_ wskazują zarówno Twój serwer lokalnym, jak i usługę wykrywania automatycznego.

> [!IMPORTANT]
> Jeśli chcesz poznać konkretne topologii Skype dla firm obsługiwane przez mazowieńską, o czym tutaj [o tym chodzi.](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Sprawdzanie stanu nowoczesnego uwierzytelniania w środowisku lokalnym
<a name="BKMK_CheckStatus"> </a>

Ponieważ nowoczesne uwierzytelnianie zmienia serwer autoryzacji używany w przypadku stosowania przez usługi protokołu OAuth/S2S, musisz wiedzieć, czy nowoczesne uwierzytelnianie zostało włączone lub wyłączone w lokalnych środowiskach Skype dla firm i Exchange sieci. Możesz sprawdzić stan na swoich serwerach Exchange, uruchamiając następujące polecenie programu PowerShell:

```powershell
Get-OrganizationConfig | ft OAuth*
```

Jeśli właściwość _OAuth2ClientProfileEnabled_ ma wartość **False**, nowoczesne uwierzytelnianie jest wyłączone.

Aby uzyskać więcej informacji o tym Get-OrganizationConfig cmdlet, zobacz [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

Możesz sprawdzić swoje serwery Skype dla firm, uruchamiając następujące polecenie programu PowerShell:

```powershell
Get-CSOAuthConfiguration
```

Jeśli polecenie zwraca pustą właściwość _OAuthServers_ lub jeśli wartość właściwości _ClientADALAuthOverride_ nie jest dozwolona **, nowoczesne** uwierzytelnianie jest wyłączone.

Aby uzyskać więcej informacji na Get-CsOAuthConfiguration cmdlet, zobacz [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>Czy spełniasz wymagania wstępne dotyczące nowoczesnego uwierzytelniania?

Przed kontynuowaniem zweryfikuj i zaznacz te elementy na liście:

- **Skype dla firm specyficznych**
  - Wszystkie serwery muszą mieć aktualizację skumulowaną z maja 2017 r. (CU5) dla systemu Skype dla firm Server 2015 lub nowszego
    - **Wyjątek** — urządzenie Nagałęźność (SBA) może mieć bieżącą wersję (opartą na programie Lync 2013)
  - Domena SIP jest dodawana jako domena federacyjna w Office 365
  - Wszystkie fronty uwierzytelniania SFB muszą mieć połączenia wychodzące z Internetem do adresów URL uwierzytelniania usługi Office 365 (TCP 443) i znanych głównych crl certyfikatów (TCP 80) wymienionych w wierszach 56 i 125 sekcji "Typowe i Office" sekcji Microsoft 365 "Typowe i Office" adresów URL i zakresów adresów [IP programu Office 365](urls-and-ip-address-ranges.md).

- **Skype dla firm lokalnym w środowisku hybrydowym Office 365 lokalnym**
  - Wdrożenie Skype dla firm Server 2019 r. ze wszystkimi serwerami z Skype dla firm Server 2019 r.
  - Wdrożenie Skype dla firm Server 2015 ze wszystkimi serwerami z Skype dla firm Server 2015.
  - Wdrożenie z maksymalnie dwiema różnymi wersjami serwera, jak podano poniżej:
    - Skype dla firm serwer 2015
    - Skype dla firm serwer 2019
  - Wszystkie Skype dla firm muszą mieć zainstalowane najnowsze aktualizacje skumulowane. Zobacz Skype dla firm Server, aby znaleźć [](/skypeforbusiness/sfb-server-updates) wszystkie dostępne aktualizacje i zarządzać nimi.
  - W środowisku hybrydowym nie ma programu Lync Server 2010 ani 2013.

>[!NOTE]
>Jeśli serwery Skype dla firm frontonie korzystają z serwera proxy do uzyskiwania dostępu do Internetu, należy wprowadzić adres IP serwera proxy i numer portu w sekcji konfiguracji pliku web.config dla każdego frontu.

- C:\Program Files\Skype dla firm Server 2015\Web Components\Web ticket\int\web.config
- C:\Program Files\Skype dla firm Server 2015\Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> Zasubskrybuj kanał informacyjny RSS dla Office 365 URL i zakresów adresów [IP](urls-and-ip-address-ranges.md), aby być na żywo z najnowszymi listami wymaganych adresów URL.

- **Exchange Server specyficznych**
  - Używasz albo serwera Exchange 2013 CU19, albo Exchange server 2016 CU8 lub Exchange Server 2019 CU1 lub więcej.
  - W środowisku Exchange server 2010.
  - Ładowanie SSL nie jest skonfigurowane. Obsługiwane jest zakończenie ssl i ponowne szyfrowanie.
  - Jeśli twoje środowisko korzysta z infrastruktury serwera proxy w celu umożliwienia serwerom łączenia się z Internetem, upewnij się, że wszystkie serwery Exchange mają serwer proxy zdefiniowany we właściwości [InternetWebProxy](/powershell/module/exchange/set-exchangeserver).

- **Exchange Server lokalnym w środowisku hybrydowym Office 365 lokalnym**

  - Jeśli używasz programu Exchange Server 2013, co najmniej jeden serwer musi mieć zainstalowane role serwera skrzynki pocztowej i dostępu klienta. Role skrzynek pocztowych i dostępu klienta można zainstalować na oddzielnych serwerach, jednak zdecydowanie zalecamy zainstalowanie obu ról na tym samym serwerze w celu zapewnienia większej niezawodności i lepszej wydajności.
  - Jeśli używasz programu Exchange w wersji 2016 lub nowszej, co najmniej jeden serwer musi mieć zainstalowaną rolę serwera Skrzynka pocztowa.
  - W środowisku Exchange hybrydowym nie ma serwera 2007 ani 2010.
  - Wszystkie Exchange skumulowane muszą mieć zainstalowane najnowsze aktualizacje skumulowane. Aby znaleźć wszystkie [](/exchange/plan-and-deploy/install-cumulative-updates) dostępne aktualizacje i zarządzać nimi, zobacz Uaktualnianie Exchange do najnowszych aktualizacji skumulowanych.

- **Exchange klienta i protokołu**

    Dostępność nowoczesnego uwierzytelniania zależy od połączenia klienta, protokołu i konfiguracji. Jeśli nowoczesne uwierzytelnianie nie jest obsługiwane przez klienta, protokół i/lub konfigurację, klient nadal będzie używać starszego uwierzytelniania.
  
    Następujący klienci i protokoły obsługują nowoczesne uwierzytelnianie za pomocą Exchange lokalnych, gdy nowoczesne uwierzytelnianie jest włączone w środowisku:

  |**Klienci**|**Primary Protocol**|**Uwagi**|
  |:-----|:-----|:-----|
  |Outlook 2013 i nowszych  <br/> |MAPI przez HTTP  <br/> |Aby można było korzystać z nowoczesnego uwierzytelniania przy użyciu tych klientów (włączony lub prawda w przypadku nowych instalacji dodatku Service Pack 1 dla programu Exchange 2013 lub nowszego), należy włączyć funkcję MAPI przez protokół HTTP w programie Exchange). Aby uzyskać więcej informacji, zobacz Jak działa nowoczesne uwierzytelnianie w aplikacjach klienckich programów [Office 2013 i Office 2016](modern-auth-for-office-2013-and-2016.md).  <br/> Upewnij się, że korzystasz z minimalnej wymaganej kompilacji pakietu Outlook. Zobacz Najnowsze aktualizacje dla wersji programu Outlook, które korzystają z Instalatora Windows [(MSI).](/officeupdates/outlook-updates-msi)  <br/> |
  |Outlook 2016 dla komputerów Mac i nowsze  <br/> |Usługi sieci Web programu Exchange  <br/> |  <br/> |
  |Outlook dla systemów iOS i Android  <br/> | Technologia synchronizacji firmy Microsoft <br/> |Aby [uzyskać więcej informacji, zobacz Używanie hybrydowego nowoczesnego uwierzytelniania Outlook dla systemów iOS i Android](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).  <br/> |
  |Exchange ActiveSync klientach (na przykład Poczta systemu iOS11)  <br/> |Exchange ActiveSync  <br/> |W Exchange ActiveSync klientów, którzy obsługują nowoczesne uwierzytelnianie, musisz ponownie utworzyć profil, aby przełączyć się z uwierzytelniania podstawowego na nowoczesne.  <br/> |

    Klienci i/lub protokoły, których nie ma na liście (na przykład POP3), nie obsługują nowoczesnego uwierzytelniania za pomocą lokalnego systemu Exchange i nadal korzystają ze starszych mechanizmów uwierzytelniania nawet po włączeniu nowoczesnego uwierzytelniania w środowisku.

- **Wymagania wstępne ogólne**
  - Scenariusze lasu zasobów będą wymagały zaufania dwukierunkowego z lasem konta w celu zapewnienia, że podczas hybrydowych żądań nowoczesnego uwierzytelniania są wykonywane odpowiednie wyszukiwania identyfikatora SID. 
  - Jeśli korzystasz z usług AD FS, musisz mieć Windows USŁUG AD FS 2012 R2 3.0 lub więcej dla federacji.
  - Konfiguracje tożsamości są dowolnymi typami obsługiwanymi przez usługę Azure AD Połączenie, takimi jak synchronizacja skrótów haseł, uwierzytelnianie pass-through i lokalna usługa STS obsługiwana przez usługę Office 365.
  - Masz usługę Azure AD, Połączenie i działa na replikację i synchronizację użytkowników.
  - Po sprawdzeniu, że środowisko hybrydowe zostało skonfigurowane przy Exchange klasycznej topologii hybrydowej między środowiskiem lokalnym a środowiskiem Office 365 hybrydowym. Oficjalne oświadczenie o zapewniania obsługi dla Exchange hybrydowej informuje, że musisz mieć bieżącą cu lub bieżącą cu - 1.
    > [!NOTE]
    > Nowoczesne uwierzytelnianie hybrydowe nie jest obsługiwane przez agenta [hybrydowego](/exchange/hybrid-deployment/hybrid-agent).

  - Upewnij się, że zarówno użytkownik testowy w środowisku lokalnym, jak i użytkownik testowy hybrydowy z systemem Office 365, może zalogować się do klienta klasycznego programu Skype dla firm (jeśli chcesz używać nowoczesnego uwierzytelniania z usługą Skype) i usługi Microsoft Outlook (jeśli chcesz używać nowoczesnego uwierzytelniania z usługą Exchange).
  - Upewnij się, że ustawienie SignInOptions w programie Microsoft Office nie jest skonfigurowane do najbardziej restrykcyjnego ustawienia. Aby uzyskać więcej informacji, [zobacz Jak zezwolić Office na łączenie się z Internetem](/office365/troubleshoot/access-management/office-feature-disabled).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Co jeszcze należy wiedzieć przed rozpoczęciem?
<a name="BKMK_Whatelse"> </a>

- Wszystkie scenariusze dla serwerów lokalnych wymagają skonfigurowania nowoczesnego uwierzytelniania lokalnie (w rzeczywistości dla systemu Skype dla firm jest lista obsługiwanych topologii), tak aby serwer odpowiedzialny za uwierzytelnianie i autoryzację był w chmurze firmy Microsoft (usłudze tokenu zabezpieczeń usługi Azure AD, o nazwie "googleSTS") i zaktualizował usługę Azure AD o adresach URL lub przestrzeniach nazw używanych przez lokalną instalację jednej z tych usług Skype dla firm lub Exchange. Dlatego serwery lokalne biorą udział w zależności od chmury firmy Microsoft. Aby to zrobić, można rozważyć skonfigurowanie "uwierzytelniania hybrydowego".
- Ten artykuł zawiera linki do innych osób, które pomogą Ci wybrać obsługiwane topologii nowoczesnego uwierzytelniania (wymagane tylko w przypadku usługi Skype dla firm) oraz artykuły z instrukcjami, w których opisano kroki konfiguracji, lub procedury wyłączania nowoczesnego uwierzytelniania w przypadku lokalnego Exchange i Skype dla firm lokalnego. Jeśli chcesz korzystać z nowoczesnego uwierzytelniania w środowisku serwera, możesz do ulubionych tę stronę w przeglądarce.

## <a name="related-topics"></a>Tematy pokrewne
<a name="BKMK_URLListforMA"> </a>

- [Jak skonfigurować Exchange Server w celu używania nowoczesnego uwierzytelniania](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Skype dla firm topologii obsługiwane przez nowoczesne uwierzytelnianie](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [Jak skonfigurować Skype dla firm lokalnej do używania nowoczesnego uwierzytelniania](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Usuwanie lub wyłączanie nowoczesnego uwierzytelniania hybrydowego Skype dla firm i Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
