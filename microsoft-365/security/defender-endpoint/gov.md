---
title: Usługa ochrony punktu końcowego w usłudze Microsoft Defender dla klientów z instytucji rządowych Stanów Zjednoczonych
description: Dowiedz się więcej o dostępnych wymaganiach i możliwościach Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów rządowych USA
keywords: government, gcc, high, requirements, capabilities, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, endpoint, dod
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ce42709349e5d7464e1809df248c8055bdfaab30
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810993"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Usługa ochrony punktu końcowego w usłudze Microsoft Defender dla klientów z instytucji rządowych Stanów Zjednoczonych

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów rządowych USA, zbudowanych w środowisku azure us government, korzysta z tych samych technologii, co usługa Defender for Endpoint w usłudze Azure Commercial.

Ta oferta jest dostępna dla klientów GCC, GCC High i DoD i jest oparta na tej samej profilaktyce, wykrywaniu, badaniu i korygowaniu co wersja komercyjna. Istnieją jednak pewne różnice w dostępności możliwości tej oferty.

> [!NOTE]
> Jeśli jesteś klientem GCC korzystającym z usługi Defender for Endpoint w wersji komercyjnej, zapoznaj się ze stronami dokumentacji publicznej.

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów rządowych USA wymaga jednej z następujących ofert licencjonowania zbiorowego firmy Microsoft:

### <a name="desktop-licensing"></a>Licencjonowanie pulpitu

<br />

****

|GCC|GCC wysoki|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 dla GCC High|Microsoft 365 G5 dla dod|
|GCC zabezpieczeń Microsoft 365 G5|Microsoft 365 G5 Security for GCC High|Microsoft 365 G5 Security for DOD|
|Ochrona punktu końcowego w usłudze Microsoft Defender — GCC|Ochrona punktu końcowego w usłudze Microsoft Defender dla GCC High|Ochrona punktu końcowego w usłudze Microsoft Defender dla usługi DOD|
|Windows 10 Enterprise E5 GCC|Windows 10 Enterprise E5 dla GCC High|Windows 10 Enterprise E5 for DOD|
|

### <a name="server-licensing"></a>Licencjonowanie serwera

<br />

****

|GCC|GCC wysoki|DoD|
|---|---|---|
|GCC serwera Ochrona punktu końcowego w usłudze Microsoft Defender|Ochrona punktu końcowego w usłudze Microsoft Defender Server for GCC High|Ochrona punktu końcowego w usłudze Microsoft Defender Server for DOD|
|Microsoft Defender dla serwerów|Microsoft Defender dla serwerów — instytucje rządowe|Microsoft Defender dla serwerów — instytucje rządowe|
|

## <a name="portal-urls"></a>Adresy URL portalu

Poniżej przedstawiono adresy URL portalu Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów rządowych USA:

<br />

****

|Typ klienta|Adres URL portalu|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC wysoki|<https://security.microsoft.us>|
|DoD|<https://security.apps.mil>|
|
> [!NOTE]
> Jeśli jesteś klientem GCC i w trakcie przechodzenia z Ochrona punktu końcowego w usłudze Microsoft Defender komercyjnego do GCC, użyj polecenia https://transition.security.microsoft.com , aby uzyskać dostęp do Ochrona punktu końcowego w usłudze Microsoft Defender komercyjnych Danych.

## <a name="endpoint-versions"></a>Wersje punktów końcowych

### <a name="standalone-os-versions"></a>Autonomiczne wersje systemu operacyjnego

Obsługiwane są następujące wersje systemu operacyjnego:

<br />

****

Wersja systemu operacyjnego|GCC|GCC wysoki|DoD
:---|:---:|:---:|:---:
Windows 11|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 21H1 i nowsze|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 20H2 (z [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 2004 (z [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1909 (z [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1903 (z [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1809 (z [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1803 (z [KB4598245](https://support.microsoft.com/help/4598245) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1709|![Nie.](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwana|![Tak](images/svg/check-yes.svg) z [KB4499147](https://support.microsoft.com/help/4499147) <sup>1</sup> <br /> Uwaga: [Przestarzałe](/lifecycle/announcements/revised-end-of-service-windows-10-1709), uaktualnij|![Nie](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwana
Windows 10, wersja 1703 lub starsza|![Nie.](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwana|![Nie](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwana|![Nie](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwana
Windows Server 2022|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2019 (z [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2016 (nowoczesne) <sup>2</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2012 R2 (nowoczesne) <sup>2</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2016 (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2012 R2 (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 8.1 Enterprise (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 8 Pro (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 7 SP1 Enterprise (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 7 SP1 Pro (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Linux|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
macOS|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Android|![Tak.](images/svg/check-yes.svg) <br /> Publiczna wersja zapoznawcza|![Tak](images/svg/check-yes.svg) <br /> Publiczna wersja zapoznawcza|![Tak](images/svg/check-yes.svg) <br /> Publiczna wersja zapoznawcza
iOS|![Tak.](images/svg/check-yes.svg) <br /> Publiczna wersja zapoznawcza|![Tak](images/svg/check-yes.svg) <br /> Publiczna wersja zapoznawcza|![Tak](images/svg/check-yes.svg) <br /> Publiczna wersja zapoznawcza
|

> [!NOTE]
> <sup>1</sup> Poprawka musi zostać wdrożona przed dołączeniem urządzenia w celu skonfigurowania usługi Defender dla punktu końcowego w odpowiednim środowisku.
>
> <sup>2</sup> Poznaj [ujednolicone nowoczesne rozwiązanie dla Windows 2016 i 2012 R2](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution). Jeśli serwery zostały wcześniej dołączone przy użyciu programu MMA, postępuj zgodnie ze wskazówkami podanymi w temacie [Migracja serwera](server-migration.md) , aby przeprowadzić migrację do nowego rozwiązania.
>
> <sup>3</sup> Podczas korzystania z [Microsoft Monitoring Agent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) należy wybrać pozycję "Azure US Government" w obszarze "Azure Cloud" w przypadku korzystania z [kreatora konfiguracji](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard) lub jeśli używasz [wiersza polecenia](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) lub [skryptu](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) — ustaw parametr "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" na 1. <br /> Minimalna obsługiwana wersja mma to 10.20.18029 (marzec 2020).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>Wersje systemu operacyjnego w przypadku korzystania z usługi Microsoft Defender dla serwerów

Następujące wersje systemu operacyjnego są obsługiwane podczas korzystania z [usługi Microsoft Defender dla serwerów](/azure/security-center/security-center-wdatp):

<br />

****

Wersja systemu operacyjnego|GCC|GCC wysoki|DoD
:---|:---:|:---:|:---:
Windows Server 2022|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2019|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2016|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2012 R2|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2008 R2 z dodatkiem SP1|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>Wymagane ustawienia łączności

Jeśli serwer proxy lub zapora domyślnie blokują cały ruch i zezwalają tylko na określone domeny, dodaj domeny wymienione w arkuszu do pobrania do listy dozwolonych domen.

Poniższy arkusz kalkulacyjny do pobrania zawiera listę usług i skojarzonych z nimi adresów URL, z którymi sieć musi mieć możliwość nawiązania połączenia. Sprawdź, czy nie ma reguły zapory ani filtrowania sieci, które odmawiałyby dostępu do tych adresów URL, lub utwórz regułę *zezwalania* specjalnie dla nich.

|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów komercyjnych| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender gov/GCC/doD | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów Gov/GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień serwera proxy urządzenia i łączności z Internetem](configure-proxy-internet.md).

> [!NOTE]
> Arkusz kalkulacyjny zawiera również komercyjne adresy URL. Sprawdź karty "US Gov".
>
> Podczas filtrowania poszukaj rekordów oznaczonych jako "US Gov" i konkretnej chmury w kolumnie geografii.

## <a name="api"></a>API

Zamiast publicznych identyfikatorów URI wymienionych w naszej [dokumentacji interfejsu API](apis-intro.md) należy użyć następujących identyfikatorów URI:

<br />

****

|Typ punktu końcowego|GCC|GCC High & DoD|
|---|---|---|
|Logowanie|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Defender for Endpoint API|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SIEM|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>Parzność funkcji z komercyjną

Usługa Defender for Endpoint dla klientów rządowych USA nie ma pełnej równoważności z ofertą komercyjną. Chociaż naszym celem jest dostarczenie wszystkich komercyjnych funkcji i funkcji naszym klientom rządowym w Stanach Zjednoczonych, istnieją pewne możliwości, które nie są jeszcze dostępne, które chcemy podkreślić.

Są to znane luki:

<br />

****

|Nazwa funkcji|GCC|GCC wysoki|DoD|
|---|:---:|:---:|:---:|
|Oceny sieci|![Nie](images/svg/check-no.svg) W programie|![Nie](images/svg/check-no.svg) W programie|![Nie](images/svg/check-no.svg) W programie|
|Odnajdywanie sieci|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|
|Raporty: Kontrola urządzenia, kondycja urządzenia, zapora|![Nie](images/svg/check-no.svg) W programie|![Nie](images/svg/check-no.svg) W programie|![Nie](images/svg/check-no.svg) W programie|
|Filtrowanie zawartości sieci Web|![Nie](images/svg/check-no.svg) W programie|![Nie](images/svg/check-no.svg) W programie|![Nie](images/svg/check-no.svg) W programie|
|Wskaźnik bezpieczeństwa Microsoft|![Tak](images/svg/check-yes.svg) <sup>1</sup>|![Nie](images/svg/check-no.svg) Nieobsługiwane|![Nie](images/svg/check-no.svg) Nieobsługiwane|  

> [!NOTE]
> <sup>1</sup> Chociaż wskaźnik bezpieczeństwa firmy Microsoft jest dostępny dla GCC klientów, istnieją pewne zalecenia dotyczące zabezpieczeń, które nie są dostępne.


Są to funkcje i znane luki w usłudze [Mobile Threat Defense (Ochrona punktu końcowego w usłudze Microsoft Defender na Android & iOS)](mtd.md):

<br />

****

|Nazwa funkcji|GCC|GCC wysoki|DoD|
|---|:---:|:---:|:---:|
|Ochrona sieci Web (wskaźniki chroniące przed wyłudzaniem informacji i niestandardowe)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|
|Ochrona przed złośliwym oprogramowaniem (tylko Android)|![Nie](images/svg/check-no.svg) W programie|![Nie](images/svg/check-no.svg) W programie|![Nie](images/svg/check-no.svg) W programie|
|Wykrywanie jailbreaka (tylko iOS)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|
|Dostęp warunkowy/uruchamianie warunkowe|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|
|Obsługa zarządzania aplikacjami mobilnymi|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|
|Mechanizmy kontroli prywatności|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|
|Zarządzanie zagrożeniami i lukami w zabezpieczeniach (TVM)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|
