---
title: Microsoft 365 Defender dla klientów z instytucji rządowych Stanów Zjednoczonych
description: Poznaj wymagania i możliwości Microsoft 365 Defender dla instytucji rządowych Stanów Zjednoczonych
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft 365 Defender, xdr, dod
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
ms.technology: m365d
ms.openlocfilehash: 3e8f6e523a5483de99beb0af7d01ab96951b7a3e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62995837"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>Microsoft 365 Defender dla klientów z instytucji rządowych Stanów Zjednoczonych

**Dotyczy:**
- Microsoft 365 Defender

Microsoft 365 Defender dla klientów z instytucji rządowych w USA, wbudowanych w środowisko Azure US Government, używa tych samych technologii źródłowych, co technologie Microsoft 365 Defender usłudze Azure Commercial.

Ta oferta jest dostępna dla GCC, użytkowników GCC High i DoD, a także jest oparta na tym samym zapobieganiu, wykrywaniu, śledztwu i rozwiązywaniu problemów co wersja komercyjna. Istnieją jednak pewne różnice w dostępności możliwości tej oferty.

> [!NOTE]
> Jeśli jesteś klientem usługi GCC korzystającym z usługi Defender for Cloud Apps, Defender for Endpoint lub Defender for Identity w wersji komercyjnej, musisz przejść do wersji programu GCC tych usług, aby kwalifikowały się do korzystania z usługi Microsoft 365 Defender GCC.

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Microsoft 365 Defender dla klientów z instytucji rządowych w Usa wymaga jednej z następujących ofert licencjonowania zbiorowego firmy Microsoft:

### <a name="desktop-licensing"></a>Licencjonowanie pulpitu

<br />

****

|GCC|GCC wysoki|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 dla GCC Wysoka|Microsoft 365 G5 dla dod|
|Microsoft 365 zabezpieczeń G5 GCC|Microsoft 365 G5 dla GCC High|Microsoft 365 G5 security for DOD|
|Enterprise Mobility + Security G5 GCC|Enterprise Mobility + Security E5 dla GCC Wysoka|Enterprise Mobility + Security E5 dla dod|
|Office 365 G5 GCC|Office 365 E5 dla GCC Wysoki|Office 365 E5 dla doD|
|Program Microsoft Defender dla aplikacji w chmurze GCC|Program Microsoft Defender for Cloud Apps for GCC High|Microsoft Defender for Cloud Apps for DOD|
|Program Microsoft Defender dla punktu końcowego — GCC|Program Microsoft Defender for Endpoint for GCC High|Program Microsoft Defender dla punktu końcowego dod|
|Usługa Microsoft Defender dla tożsamości — GCC|Usługa Microsoft Defender for Identity dla GCC High|Microsoft Defender for Identity for DOD|
|Program Microsoft Defender Office 365 (plan 2) GCC|Microsoft Defender for Office 365 (Plan 2) for GCC High|Microsoft Defender for Office 365 (Plan 2) for DOD|
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

Poniżej przedstawiono adresy URL Microsoft 365 Defender dla klientów z instytucji rządowych Stanów Zjednoczonych:

<br />

****

|Typ klienta|Adres URL portalu|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC wysoki|Wyedytowanie|
|DoD|Wyedytowanie|
|
> [!NOTE]
> Jeśli jesteś klientem usługi GCC i w trakcie przechodzenia z usługi Microsoft Defender for Endpoint do programu GCC, https://transition.security.microsoft.com użyj go do uzyskania dostępu do danych komercyjnych programu Microsoft Defender for Endpoint.

## <a name="api"></a>API

Zamiast publicznych URI wymienionych w dokumentacji [interfejsu API](api-overview.md) należy użyć następujących URI:

<br />

****

|Typ punktu końcowego|GCC|GCC do & DoD|
|---|---|---|
|Zaloguj się|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Microsoft 365 Defender API|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>Parowalność funkcji z komercyjnymi

Microsoft 365 Defender dla klientów z instytucji rządowych w USA nie zapewnia pełnej podobieństwa do oferty komercyjnej. Chociaż naszym celem jest dostarczenie wszystkich funkcji komercyjnych klientom z rządem Stanów Zjednoczonych, jeszcze nie mamy do dyspozycji niektórych funkcji, które chcemy wyróżnić.

Są to znane odstępy:

<br />

****

|Nazwa funkcji|GCC|GCC wysoki|DoD|
|---|:---:|:---:|:---:|
|Integracje: Microsoft Sentinel (zdarzenia i & nieprzetworzone dane)|![Tak](../defender-endpoint/images/svg/check-yes.svg)|![Tak](../defender-endpoint/images/svg/check-yes.svg) W podglądzie prywatnym|![Tak](../defender-endpoint/images/svg/check-yes.svg) W podglądzie prywatnym|
|Microsoft Threat Experts|![Nie](../defender-endpoint/images/svg/check-no.svg) Na stronie prac inżynierskich|![Nie](../defender-endpoint/images/svg/check-no.svg) Na stronie prac inżynierskich|![Nie](../defender-endpoint/images/svg/check-no.svg) Na stronie prac inżynierskich|

## <a name="more-details"></a>Więcej szczegółów

Aby uzyskać więcej informacji, zobacz poszczególne strony z informacjami o obciążeniach pracą w Usa:
- [Program Microsoft Defender dla aplikacji w chmurze](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description).
- [Program Microsoft Defender dla tożsamości](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Program Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/gov).
