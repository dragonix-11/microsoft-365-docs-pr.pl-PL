---
title: Omówienie nowoczesnego uwierzytelniania hybrydowego i wymagania wstępne dotyczące użycia z lokalnymi serwerami Skype dla firm i Exchange
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: scotv
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
description: W tym artykule dowiesz się więcej na temat nowoczesnego uwierzytelniania hybrydowego i wymagań wstępnych dotyczących użycia z lokalnymi serwerami Skype dla firm i Exchange.
ms.openlocfilehash: c161f205aba1222f39811155bef5c6be6da613d0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093399"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Omówienie nowoczesnego uwierzytelniania hybrydowego i wymagania wstępne dotyczące używania go z lokalnymi serwerami Skype dla firm i Exchange

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

_Nowoczesne uwierzytelnianie_ to metoda zarządzania tożsamościami, która oferuje bezpieczniejsze uwierzytelnianie i autoryzację użytkowników. Jest ona dostępna dla Office 365 wdrożeń hybrydowych Skype dla firm serwera lokalnego i lokalnego serwera Exchange oraz hybrydowych Skype dla firm domeny podzielonej. Ten artykuł zawiera linki do powiązanych dokumentów dotyczących wymagań wstępnych, konfiguracji/wyłączania nowoczesnego uwierzytelniania oraz niektórych powiązanych klientów (np. Outlook i Skype klientów).

- [Co to jest nowoczesne uwierzytelnianie?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Jakie zmiany korzystania z nowoczesnego uwierzytelniania?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Sprawdzanie stanu nowoczesnego uwierzytelniania środowiska lokalnego](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Czy spełniasz wymagania wstępne dotyczące nowoczesnego uwierzytelniania?](#do-you-meet-modern-authentication-prerequisites)
- [Co jeszcze muszę wiedzieć przed rozpoczęciem?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Co to jest nowoczesne uwierzytelnianie?
<a name="BKMK_WhatisModAuth"> </a>

Nowoczesne uwierzytelnianie jest terminem parasolowym dla kombinacji metod uwierzytelniania i autoryzacji między klientem (na przykład laptopem lub telefonem) a serwerem, a także niektórych środków bezpieczeństwa, które opierają się na zasadach dostępu, które mogą już być znane. Oto co obejmuje:

- **Metody uwierzytelniania**: uwierzytelnianie wieloskładnikowe (MFA); uwierzytelnianie za pomocą karty inteligentnej; uwierzytelnianie oparte na certyfikatach klienta
- **Metody autoryzacji**: implementacja otwartej autoryzacji (OAuth) firmy Microsoft
- **Zasady dostępu warunkowego: dostęp warunkowy** do zarządzania aplikacjami mobilnymi (MAM) i Azure Active Directory (Azure AD)

Zarządzanie tożsamościami użytkowników przy użyciu nowoczesnego uwierzytelniania zapewnia administratorom wiele różnych narzędzi do użycia w przypadku zabezpieczania zasobów i oferuje bezpieczniejsze metody zarządzania tożsamościami zarówno w środowisku lokalnym (Exchange, jak i Skype dla firm), Exchange hybrydowych i Skype dla firm scenariuszy hybrydowych/podzielonych domen.

Ponieważ Skype dla firm ściśle współpracuje z Exchange, na zachowanie logowania Skype dla firm użytkowników klienckich będzie mieć wpływ nowoczesny stan uwierzytelniania Exchange. Ma to również zastosowanie, jeśli masz Skype dla firm architekturę hybrydową _z podziałem domeny_, w której masz zarówno Skype dla firm Online, jak i Skype dla firm lokalnie, a użytkownicy znajdują się w obu lokalizacjach.

Aby uzyskać więcej informacji na temat nowoczesnego uwierzytelniania w Office 365, zobacz [Office 365 Obsługa aplikacji klienckich — uwierzytelnianie wieloskładnikowe](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> Od sierpnia 2017 r. wszystkie nowe dzierżawy Office 365, które obejmują Skype dla firm online i Exchange online, będą domyślnie włączone nowoczesne uwierzytelnianie. Istniejące dzierżawy nie będą miały zmiany w domyślnym stanie MA, ale wszystkie nowe dzierżawy automatycznie obsługują rozszerzony zestaw funkcji tożsamości widocznych powyżej. Aby sprawdzić stan ma, zobacz [sprawdzanie stanu nowoczesnego uwierzytelniania środowiska lokalnego](hybrid-modern-auth-overview.md#BKMK_CheckStatus) .

## <a name="what-changes-when-i-use-modern-authentication"></a>Jakie zmiany korzystania z nowoczesnego uwierzytelniania?
<a name="BKMK_WhatChanges"> </a>

W przypadku korzystania z nowoczesnego uwierzytelniania z lokalnym serwerem Skype dla firm lub Exchange nadal *uwierzytelniasz* użytkowników lokalnie, ale historia *autoryzacji* ich dostępu do zasobów (takich jak pliki lub wiadomości e-mail) zmienia się. Dlatego mimo że nowoczesne uwierzytelnianie dotyczy komunikacji z klientem i serwerem, kroki wykonywane podczas konfigurowania ma skutkują ustawieniem evoSTS (usługi tokenu zabezpieczającego używanej przez usługę Azure AD) jako serwera uwierzytelniania dla serwera Skype dla firm i serwera Exchange lokalnie.

Zmiana na evoSTS umożliwia lokalnym serwerom korzystanie z uwierzytelniania OAuth (wystawiania tokenów) w celu autoryzowania klientów, a także umożliwia lokalne korzystanie z metod zabezpieczeń typowych w chmurze (takich jak uwierzytelnianie wieloskładnikowe). Ponadto evoSTS wystawia tokeny, które umożliwiają użytkownikom żądanie dostępu do zasobów bez podawania hasła w ramach żądania. Niezależnie od tego, gdzie znajdują się użytkownicy (online lub lokalnie) i niezależnie od tego, która lokalizacja hostuje potrzebny zasób, platforma EvoSTS stanie się rdzeniem autoryzacji użytkowników i klientów po skonfigurowaniu nowoczesnego uwierzytelniania.

Jeśli na przykład klient Skype dla firm musi uzyskać dostęp do serwera Exchange, aby uzyskać informacje o kalendarzu w imieniu użytkownika, używa do tego biblioteki microsoft authentication library (MSAL). BIBLIOTEKA MSAL to biblioteka kodu przeznaczona do udostępniania zabezpieczonych zasobów w katalogu aplikacjom klienckim przy użyciu tokenów zabezpieczających protokołu OAuth. Biblioteka MSAL współpracuje z usługą OAuth w celu weryfikacji oświadczeń i wymiany tokenów (zamiast haseł), aby udzielić użytkownikowi dostępu do zasobu. W przeszłości urząd w transakcji takiej jak ta — serwer, który wie, jak weryfikować oświadczenia użytkowników i wystawiać wymagane tokeny — mógł być lokalną usługą tokenu zabezpieczającego, a nawet Active Directory Federation Services. Jednak nowoczesne uwierzytelnianie scentralizuje ten urząd przy użyciu usługi Azure AD.

Oznacza to również, że nawet jeśli serwer Exchange i środowiska Skype dla firm mogą być całkowicie lokalne, serwer autoryzacji będzie w trybie online, a środowisko lokalne musi mieć możliwość tworzenia i utrzymywania połączenia z subskrypcją Office 365 w chmurze (oraz wystąpieniem usługi Azure AD używanym przez subskrypcję jako jej katalog).

Co się nie zmienia? Niezależnie od tego, czy korzystasz z hybrydowej domeny podzielonej, czy używasz lokalnego serwera Skype dla firm i Exchange, wszyscy użytkownicy muszą najpierw uwierzytelnić się *lokalnie*. W przypadku hybrydowej implementacji nowoczesnego uwierzytelniania wykrywanie programu _Lyncdiscovery_ i _wykrywanie_ automatyczne wskazują serwer lokalny.

> [!IMPORTANT]
> Jeśli musisz znać konkretne topologie Skype dla firm obsługiwane przez ma, jest to [udokumentowane tutaj](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported).

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Sprawdzanie stanu nowoczesnego uwierzytelniania środowiska lokalnego
<a name="BKMK_CheckStatus"> </a>

Ponieważ nowoczesne uwierzytelnianie zmienia serwer autoryzacji używany podczas stosowania usług OAuth/S2S, musisz wiedzieć, czy nowoczesne uwierzytelnianie jest włączone lub wyłączone dla lokalnych środowisk Skype dla firm i Exchange. Stan na serwerach Exchange można sprawdzić, uruchamiając następujące polecenie programu PowerShell:

```powershell
Get-OrganizationConfig | ft OAuth*
```

Jeśli wartość właściwości _OAuth2ClientProfileEnabled_ to **False**, nowoczesne uwierzytelnianie jest wyłączone.

Aby uzyskać więcej informacji na temat polecenia cmdlet Get-OrganizationConfig, zobacz [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

Serwery Skype dla firm można sprawdzić, uruchamiając następujące polecenie programu PowerShell:

```powershell
Get-CSOAuthConfiguration
```

Jeśli polecenie zwraca pustą właściwość _OAuthServers_ lub jeśli wartość właściwości _ClientADALAuthOverride_ nie jest **dozwolona**, nowoczesne uwierzytelnianie jest wyłączone.

Aby uzyskać więcej informacji na temat polecenia cmdlet Get-CsOAuthConfiguration, zobacz [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>Czy spełniasz wymagania wstępne dotyczące nowoczesnego uwierzytelniania?

Przed kontynuowaniem sprawdź i sprawdź te elementy z listy:

- **Skype dla firm specyficzne**
  - Wszystkie serwery muszą mieć aktualizację zbiorczą (CU5) z maja 2017 r. dla Skype dla firm Server 2015 r. lub nowszej
    - **Wyjątek** — urządzenie survivability Branch (SBA) może być w bieżącej wersji (na podstawie programu Lync 2013)
  - Domena SIP jest dodawana jako domena federacyjna w Office 365
  - Wszystkie frontony SFB muszą mieć połączenia wychodzące z Internetem, aby Office 365 adresów URL uwierzytelniania (TCP 443) i dobrze znanych głównych list CRL certyfikatów (TCP 80) wymienionych w wierszach 56 i 125 sekcji "Microsoft 365 Common and Office" [Office 365 adresów URL i zakresów adresów IP](urls-and-ip-address-ranges.md).

- **Skype dla firm lokalnie w środowisku Office 365 hybrydowej**
  - Wdrożenie Skype dla firm Server 2019 r. ze wszystkimi serwerami z systemem Skype dla firm Server 2019 r.
  - Wdrożenie Skype dla firm Server 2015 r. ze wszystkimi serwerami z systemem Skype dla firm Server 2015 r.
  - Wdrożenie z maksymalnie dwiema różnymi wersjami serwera, jak pokazano poniżej:
    - Skype dla firm serwer 2015
    - Skype dla firm serwer 2019
  - Wszystkie serwery Skype dla firm muszą mieć zainstalowane najnowsze aktualizacje zbiorcze, zobacz [Skype dla firm Server aktualizacje](/skypeforbusiness/sfb-server-updates), aby znaleźć wszystkie dostępne aktualizacje i zarządzać nimi.
  - W środowisku hybrydowym nie ma programu Lync Server 2010 ani 2013.

>[!NOTE]
>Jeśli serwery frontonu Skype dla firm używają serwera proxy na potrzeby dostępu do Internetu, adres IP serwera proxy i numer portu muszą zostać wprowadzone w sekcji konfiguracji pliku web.config dla każdego frontonu.

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
> Pamiętaj, aby subskrybować kanał informacyjny RSS dla [Office 365 adresów URL i zakresów adresów IP](urls-and-ip-address-ranges.md), aby być na bieżąco z najnowszymi listami wymaganych adresów URL.

- **Exchange Server specyficzne**
  - Używasz serwera Exchange 2013 CU19 lub nowszego, serwera Exchange 2016 CU8 lub nowszego lub Exchange Server 2019 CU1 i nowszego.
  - W środowisku nie ma Exchange serwera 2010.
  - Odciążanie protokołu SSL nie jest skonfigurowane. Obsługiwane jest kończenie I ponowne szyfrowanie protokołu SSL.
  - W przypadku, gdy środowisko korzysta z infrastruktury serwera proxy, aby umożliwić serwerom łączenie się z Internetem, upewnij się, że wszystkie serwery Exchange mają serwer proxy [zdefiniowany we właściwości InternetWebProxy](/powershell/module/exchange/set-exchangeserver).

- **Exchange Server lokalnie w środowisku Office 365 hybrydowej**

  - Jeśli używasz Exchange Server 2013 r., co najmniej jeden serwer musi mieć zainstalowane role skrzynki pocztowej i serwera dostępu klienta. Chociaż można zainstalować role Skrzynka pocztowa i Dostęp klienta na oddzielnych serwerach, zdecydowanie zalecamy zainstalowanie obu ról na tym samym serwerze, aby zapewnić większą niezawodność i lepszą wydajność.
  - Jeśli używasz serwera Exchange wersji 2016 lub nowszej, co najmniej jeden serwer musi mieć zainstalowaną rolę serwera skrzynki pocztowej.
  - W środowisku hybrydowym nie ma Exchange serwera 2007 lub 2010.
  - Wszystkie serwery Exchange muszą mieć zainstalowane najnowsze aktualizacje zbiorcze. Zobacz [Uaktualnianie Exchange do najnowszych aktualizacji zbiorczych](/exchange/plan-and-deploy/install-cumulative-updates), aby znaleźć wszystkie dostępne aktualizacje i zarządzać nimi.

- **Exchange wymagania dotyczące klienta i protokołu**

    Dostępność nowoczesnego uwierzytelniania zależy od kombinacji klienta, protokołu i konfiguracji. Jeśli nowoczesne uwierzytelnianie nie jest obsługiwane przez klienta, protokół i/lub konfigurację, klient będzie nadal używać starszego uwierzytelniania.
  
    Następujący klienci i protokoły obsługują nowoczesne uwierzytelnianie przy użyciu lokalnego Exchange po włączeniu nowoczesnego uwierzytelniania w środowisku:

  |**Klientów**|**Protokół podstawowy**|**Uwagi**|
  |:-----|:-----|:-----|
  |Outlook 2013 r. i nowsze  <br/> |MAPI za pośrednictwem protokołu HTTP  <br/> |Interfejs MAPI za pośrednictwem protokołu HTTP musi być włączony w ramach Exchange w celu korzystania z nowoczesnego uwierzytelniania z tymi klientami (włączone lub true dla nowych instalacji dodatku Service Pack 1 Exchange 2013 lub nowszych); aby uzyskać więcej informacji, zobacz [Jak działa nowoczesne uwierzytelnianie dla aplikacji klienckich Office 2013 i Office 2016](modern-auth-for-office-2013-and-2016.md).  <br/> Upewnij się, że używasz minimalnej wymaganej kompilacji Outlook. Zobacz [Najnowsze aktualizacje wersji Outlook korzystających z instalatora Windows (MSI).](/officeupdates/outlook-updates-msi)  <br/> |
  |Outlook 2016 dla komputerów Mac i nowsze  <br/> |Usługi sieci Web programu Exchange  <br/> |  <br/> |
  |Outlook dla systemów iOS i Android  <br/> | Technologia synchronizacji firmy Microsoft <br/> |Aby uzyskać więcej informacji, zobacz [Using hybrid Modern Authentication with Outlook for iOS and Android (Używanie nowoczesnego uwierzytelniania hybrydowego z Outlook dla systemów iOS i Android](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)).  <br/> |
  |Exchange ActiveSync klientów (na przykład poczta systemu iOS11)  <br/> |Exchange ActiveSync  <br/> |W przypadku Exchange ActiveSync klientów, którzy obsługują nowoczesne uwierzytelnianie, należy ponownie utworzyć profil, aby przełączyć się z uwierzytelniania podstawowego na nowoczesne uwierzytelnianie.  <br/> |

    Klienci i/lub protokoły, które nie są wymienione (na przykład POP3) nie obsługują nowoczesnego uwierzytelniania przy użyciu lokalnych Exchange i nadal używają starszych mechanizmów uwierzytelniania nawet po włączeniu nowoczesnego uwierzytelniania w środowisku.

- **Ogólne wymagania wstępne**
  - Scenariusze lasu zasobów będą wymagały dwukierunkowego zaufania z lasem konta, aby zapewnić, że podczas żądań nowoczesnego uwierzytelniania hybrydowego są wykonywane odpowiednie wyszukiwania identyfikatorów SID. 
  - Jeśli używasz usług AD FS, należy mieć Windows 2012 R2 AD FS 3.0 i nowsze dla federacji.
  - Konfiguracje tożsamości to dowolne typy obsługiwane przez Połączenie usługi Azure AD, takie jak synchronizacja skrótów haseł, uwierzytelnianie przekazywane i lokalny usługa STS obsługiwana przez Office 365.
  - Usługa Azure AD Połączenie skonfigurowana i działa na potrzeby replikacji i synchronizacji użytkowników.
  - Sprawdzono, że konfiguracja hybrydowa jest skonfigurowana przy użyciu Exchange klasycznego trybu topologii hybrydowej między środowiskiem lokalnym i Office 365. Oficjalne oświadczenie o wsparciu dla hybrydowej Exchange mówi, że musisz mieć obecną cu lub obecną CU - 1.
    > [!NOTE]
    > Nowoczesne uwierzytelnianie hybrydowe nie jest obsługiwane w przypadku [agenta hybrydowego](/exchange/hybrid-deployment/hybrid-agent).

  - Upewnij się, że zarówno lokalny użytkownik testowy, jak i użytkownik testowy hybrydowy hostowane w Office 365, może zalogować się do klienta klasycznego Skype dla firm (jeśli chcesz używać nowoczesnego uwierzytelniania z Skype) i microsoft Outlook (jeśli chcesz używać nowoczesnego uwierzytelniania z Exchange).
  - Upewnij się, że ustawienie SignInOptions w Microsoft Office nie jest skonfigurowane do najbardziej restrykcyjnego ustawienia. Aby uzyskać więcej informacji, zobacz [Jak zezwolić Office na łączenie się z Internetem](/office365/troubleshoot/access-management/office-feature-disabled).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Co jeszcze muszę wiedzieć przed rozpoczęciem?
<a name="BKMK_Whatelse"> </a>

- Wszystkie scenariusze dotyczące serwerów lokalnych obejmują skonfigurowanie nowoczesnego uwierzytelniania lokalnego (w rzeczywistości dla Skype dla firm istnieje lista obsługiwanych topologii), tak aby serwer odpowiedzialny za uwierzytelnianie i autoryzację był w chmurze firmy Microsoft (usługa tokenu zabezpieczającego usługi Azure AD o nazwie "evoSTS") i aktualizował usługę Azure AD o adresy URL lub przestrzenie nazw używane przez lokalną instalację albo Skype dla firm lub Exchange. W związku z tym serwery lokalne przyjmują zależność chmury firmy Microsoft. Wykonanie tej akcji można rozważyć skonfigurowanie "uwierzytelniania hybrydowego".
- Ten artykuł zawiera linki do innych osób, które pomogą Ci wybrać obsługiwane topologie nowoczesnego uwierzytelniania (niezbędne tylko dla Skype dla firm) oraz artykuły z instrukcjami, które przedstawiają kroki konfiguracji lub kroki wyłączania nowoczesnego uwierzytelniania dla Exchange lokalnych i Skype dla firm lokalnych. Wybierz tę stronę jako ulubioną w przeglądarce, jeśli potrzebujesz bazy głównej do korzystania z nowoczesnego uwierzytelniania w środowisku serwera.

## <a name="related-topics"></a>Tematy pokrewne
<a name="BKMK_URLListforMA"> </a>

- [Jak skonfigurować Exchange Server lokalnie do korzystania z nowoczesnego uwierzytelniania](configure-exchange-server-for-hybrid-modern-authentication.md)
- [topologie Skype dla firm obsługiwane przy użyciu nowoczesnego uwierzytelniania](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [Jak skonfigurować Skype dla firm lokalnie do korzystania z nowoczesnego uwierzytelniania](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Usuwanie lub wyłączanie nowoczesnego uwierzytelniania hybrydowego z Skype dla firm i Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
