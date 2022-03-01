---
title: Program Microsoft Defender dla punktu końcowego dla klientów z rządem Stanów Zjednoczonych
description: Dowiedz się więcej o dostępnych wymaganiach i możliwościach programu Microsoft Defender for Endpoint dla klientów z usa government
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft Defender for Endpoint, endpoint, dod
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
ms.openlocfilehash: 24158e4a9da9ce48382f08b6dbe701c5640972d4
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009819"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Program Microsoft Defender dla punktu końcowego dla klientów z rządem Stanów Zjednoczonych

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Program Microsoft Defender for Endpoint dla klientów z instytucji rządowych Stanów Zjednoczonych, wbudowany w środowisko Azure US Government, używa tych samych podstawowych technologii co program Defender for Endpoint w usłudze Azure Commercial.

Ta oferta jest dostępna dla GCC, użytkowników GCC High i DoD, a także jest oparta na tym samym zapobieganiu, wykrywaniu, śledztwu i rozwiązywaniu problemów co wersja komercyjna. Istnieją jednak pewne różnice w dostępności możliwości tej oferty.

> [!NOTE]
> Jeśli jesteś klientem korzystającym z GCC Endpoint w celach komercyjnych, zapoznaj się z publicznymi stronami dokumentacji.

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Program Microsoft Defender for Endpoint dla klientów z instytucji rządowych Stanów Zjednoczonych wymaga jednej z następujących ofert licencjonowania zbiorowego firmy Microsoft:

### <a name="desktop-licensing"></a>Licencjonowanie pulpitu

<br />

****

|GCC|GCC wysoki|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 dla GCC Wysoka|Microsoft 365 G5 dla dod|
|Microsoft 365 zabezpieczeń G5 GCC|Microsoft 365 G5 dla GCC High|Microsoft 365 G5 security for DOD|
|Program Microsoft Defender dla punktu końcowego — GCC|Program Microsoft Defender for Endpoint for GCC High|Program Microsoft Defender dla punktu końcowego dod|
|Windows 10 Enterprise E5 GCC|Windows 10 Enterprise E5 dla GCC Wysoka|Windows 10 Enterprise E5 dla dod|
|

### <a name="server-licensing"></a>Licencjonowanie serwera

<br />

****

|GCC|GCC wysoki|DoD|
|---|---|---|
|Program Microsoft Defender for Endpoint Server GCC|Program Microsoft Defender for Endpoint Server for GCC High|Microsoft Defender for Endpoint Server for DOD|
|Usługa Microsoft Defender dla serwerów|Usługa Microsoft Defender dla serwerów — dla instytucji rządowych|Usługa Microsoft Defender dla serwerów — dla instytucji rządowych|
|

## <a name="portal-urls"></a>Adresy URL portalu

Poniżej przedstawiono adresy URL portalu programu Microsoft Defender for Endpoint dla klientów z instytucji rządowych Stanów Zjednoczonych:

<br />

****

|Typ klienta|Adres URL portalu|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC wysoki|<https://securitycenter.microsoft.us>|
|DoD|<https://securitycenter.microsoft.us>|
|
> [!NOTE]
> Jeśli jesteś klientem usługi GCC i w trakcie przechodzenia z usługi Microsoft Defender for Endpoint do programu GCC, https://transition.security.microsoft.com użyj go do uzyskania dostępu do danych komercyjnych programu Microsoft Defender for Endpoint.

## <a name="endpoint-versions"></a>Wersje punktów końcowych

### <a name="standalone-os-versions"></a>Autonomiczne wersje systemu operacyjnego

Obsługiwane są następujące wersje systemu operacyjnego:

<br />

****

Wersja systemu operacyjnego|GCC|GCC wysoki|DoD
:---|:---:|:---:|:---:
Windows 11|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 21H1 i wyżej|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 20H2 (z [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 2004 (z [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1909 (z [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1903 (z [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1809 (z [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1803 (z [KB4598245](https://support.microsoft.com/help/4598245) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 10, wersja 1709|![L.p.](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwane|![Tak](images/svg/check-yes.svg) w [przypadku aktualizacji KB4499147](https://support.microsoft.com/help/4499147) <sup>1</sup> <br /> Uwaga: [Przestarzałe](/lifecycle/announcements/revised-end-of-service-windows-10-1709), uaktualnij|![Nie](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwane
Windows 10, wersja 1703 i wcześniejsze|![L.p.](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwane|![Nie](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwane|![Nie](images/svg/check-no.svg) <br /> Uwaga: nie będzie obsługiwane
Windows Server 2022|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2019 (z [kb4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2016 (nowoczesny) <sup>2</sup>|![Tak.](images/svg/check-yes.svg) <br /> Podgląd publiczny|![Tak](images/svg/check-yes.svg) <br /> Podgląd publiczny|![Tak](images/svg/check-yes.svg) <br /> Podgląd publiczny
Windows Server 2012 R2 (nowoczesny) <sup>2</sup>|![Tak.](images/svg/check-yes.svg) <br /> Podgląd publiczny|![Tak](images/svg/check-yes.svg) <br /> Podgląd publiczny|![Tak](images/svg/check-yes.svg) <br /> Podgląd publiczny
Windows Server 2016 (Starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2012 R2 (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2008 R2 z dodatkiem SP1 (starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 8.1 Enterprise (Starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 8 Pro (Starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 7 z dodatkiem SP1 Enterprise (Starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows 7 z dodatkiem SP1 Pro (Starsza wersja) <sup>3</sup>|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Linux|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
macOS|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Android|![L.p.](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju
iOS|![L.p.](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju
|

> [!NOTE]
> <sup>1</sup> Poprawka musi zostać wdrożona przed dodaniem urządzenia w celu skonfigurowania usługi Defender dla punktu końcowego we właściwym środowisku.
>
> <sup>2</sup> Dowiedz się więcej o [ujednoliconym nowoczesnym rozwiązaniu dla Windows 2016 i 2012 R2](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview). Jeśli serwery były wcześniej wnoszone za pomocą usługi MMA, postępuj zgodnie ze wskazówkami w tece Migracja serwera, aby przeprowadzić migrację do nowego rozwiązania.[](server-migration.md)
>
> <sup>3</sup> W przypadku korzystania z usługi [Microsoft Monitoring Agent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) musisz wybrać pozycję "Azure US Government" w obszarze "Azure Cloud", jeśli korzystasz z kreatora [konfiguracji, albo](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard) użyć wiersza polecenia lub [](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) [skryptu — ustawić](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) parametr "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" na 1. <br /> Minimalna obsługiwana wersja w programie MMA to 10.20.18029 (marzec 2020 r.).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>Wersje systemu operacyjnego podczas korzystania z programu Microsoft Defender dla serwerów

W przypadku korzystania z programu Microsoft Defender dla serwerów są obsługiwane następujące [wersje systemu operacyjnego](/azure/security-center/security-center-wdatp):

<br />

****

Wersja systemu operacyjnego|GCC|GCC wysoki|DoD
:---|:---:|:---:|:---:
Windows Server 2022|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2019|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
System Windows Server 2016|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2012 R2|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
Windows Server 2008 R2 z dodatkiem SP1|![Tak.](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)|![Tak](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>Wymagane ustawienia łączności

Jeśli serwer proxy lub zapora domyślnie blokuje cały ruch i zezwala na dostęp tylko do określonych domen, dodaj domeny wymienione w arkuszu do pobrania do listy dozwolonych domen.

Poniższy arkusz kalkulacyjny zawiera listę usług i skojarzonych z nimi adresów URL, z których sieć musi być w stanie nawiązać połączenie. Sprawdź, czy nie ma żadnych reguł zapory lub filtrowania sieci, które odmawiałyby dostępu do tych adresów URL, lub utwórz regułę zezwalania *specjalnie* dla nich.

|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
| Lista adresów URL programu Microsoft Defender dla punktów końcowych dla klientów GCC/DoD | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień serwera proxy urządzenia i łączności internetowej](configure-proxy-internet.md).

> [!NOTE]
> Arkusz kalkulacyjny zawiera również komercyjne adresy URL, sprawdź, czy są dostępne karty "Rząd Stanów Zjednoczonych".
>
> Podczas filtrowania poszukaj rekordów oznaczonych jako "Rząd Stanów Zjednoczonych" i konkretnej chmury w kolumnie geografii.

## <a name="api"></a>API

Zamiast publicznych URI wymienionych w dokumentacji [interfejsu API](apis-intro.md) należy użyć następujących URI:

<br />

****

|Typ punktu końcowego|GCC|GCC do & DoD|
|---|---|---|
|Zaloguj się|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Defender for Endpoint API|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SIEM|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>Parowalność funkcji z komercyjnymi

Program Defender for Endpoint dla klientów z instytucji rządowych Stanów Zjednoczonych nie ma pełnej podobieństwa z ofertą komercyjną. Chociaż naszym celem jest dostarczenie wszystkich funkcji komercyjnych klientom z rządem Stanów Zjednoczonych, jeszcze nie mamy do dyspozycji niektórych funkcji, które chcemy wyróżnić.

Są to znane odstępy:

<br />

****

|Nazwa funkcji|GCC|GCC wysoki|DoD|
|---|:---:|:---:|:---:|
|Testy sieci|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|
|Odnajdowanie sieci|![Tak](images/svg/check-yes.svg)|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|
|Raporty: Zmniejszenie powierzchni ataków, Sterowanie urządzeniami, Kondycja urządzenia, Zapora|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|
|Filtrowanie zawartości sieci Web|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|![Nie](images/svg/check-no.svg) W rozwoju|
