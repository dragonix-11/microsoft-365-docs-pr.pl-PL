---
title: Usługa Microsoft 365 Defender dla klientów z instytucji rządowych Stanów Zjednoczonych
description: Dowiedz się więcej o dostępnych wymaganiach i możliwościach Microsoft 365 Defender dla klientów rządowych USA
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
ms.openlocfilehash: 53fc78159580a27a8af04009f4e5ecd5b18bc4e8
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057588"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>Usługa Microsoft 365 Defender dla klientów z instytucji rządowych Stanów Zjednoczonych

**Dotyczy:**
- Microsoft 365 Defender

Microsoft 365 Defender dla klientów rządowych USA, zbudowanych w środowisku azure us government, korzysta z tych samych technologii bazowych, co Microsoft 365 Defender w usłudze Azure Commercial.

Ta oferta jest dostępna dla klientów GCC, GCC High i DoD i jest oparta na tej samej profilaktyce, wykrywaniu, badaniu i korygowaniu co wersja komercyjna. Istnieją jednak pewne różnice w dostępności możliwości tej oferty.

> [!NOTE]
> Jeśli jesteś klientem GCC korzystającym z usług Defender dla Chmury Apps, Defender for Endpoint lub Defender for Identity w wersji komercyjnej, musisz przenieść te usługi do wersji GCC, aby kwalifikować się do Microsoft 365 Defender GCC.

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Microsoft 365 Defender dla klientów rządowych USA wymaga jednej z następujących ofert licencjonowania zbiorowego firmy Microsoft:

### <a name="desktop-licensing"></a>Licencjonowanie pulpitu

<br />

****

|GCC|GCC wysoki|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 dla GCC High|Microsoft 365 G5 dla dod|
|GCC zabezpieczeń Microsoft 365 G5|Microsoft 365 G5 Security for GCC High|Microsoft 365 G5 Security for DOD|
|Enterprise Mobility + Security G5 GCC|Enterprise Mobility + Security E5 dla GCC High|Enterprise Mobility + Security E5 dla dod|
|Office 365 G5 GCC|Office 365 E5 dla GCC High|Office 365 E5 do dod|
|Microsoft Defender for Cloud Apps GCC|Microsoft Defender for Cloud Apps dla GCC High|Microsoft Defender for Cloud Apps dla usługi DOD|
|Ochrona punktu końcowego w usłudze Microsoft Defender — GCC|Ochrona punktu końcowego w usłudze Microsoft Defender dla GCC High|Ochrona punktu końcowego w usłudze Microsoft Defender dla usługi DOD|
|Microsoft Defender for Identity — GCC|Microsoft Defender for Identity dla GCC High|Microsoft Defender for Identity do dod|
|Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2) GCC|Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2) dla GCC High|Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2) dla dod|
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

Poniżej przedstawiono adresy URL portalu Microsoft 365 Defender dla klientów rządowych USA:

<br />

****

|Typ klienta|Adres URL portalu|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC wysoki|Wdrażanie|
|DoD|Wdrażanie|
|
> [!NOTE]
> Jeśli jesteś klientem GCC i w trakcie przechodzenia z Ochrona punktu końcowego w usłudze Microsoft Defender komercyjnego do GCC, użyj polecenia https://transition.security.microsoft.com , aby uzyskać dostęp do Ochrona punktu końcowego w usłudze Microsoft Defender komercyjnych Danych.

## <a name="api"></a>API

Zamiast publicznych identyfikatorów URI wymienionych w naszej [dokumentacji interfejsu API](api-overview.md) należy użyć następujących identyfikatorów URI:

<br />

****

|Typ punktu końcowego|GCC|GCC High & DoD|
|---|---|---|
|Logowanie|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|interfejs API Microsoft 365 Defender|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>Parzność funkcji z komercyjną

Microsoft 365 Defender dla klientów rządowych USA nie ma pełnej równoważności z ofertą komercyjną. Chociaż naszym celem jest dostarczenie wszystkich komercyjnych funkcji i funkcji naszym klientom rządowym w Stanach Zjednoczonych, istnieją pewne możliwości, które nie są jeszcze dostępne, które chcemy podkreślić.

Są to znane luki:

<br />

****

|Nazwa funkcji|GCC|GCC wysoki|DoD|
|---|:---:|:---:|:---:|
|Integracje: Microsoft Sentinel (zdarzenia & nieprzetworzone dane)|![Tak](../defender-endpoint/images/svg/check-yes.svg) W publicznej wersji zapoznawczej|![Tak](../defender-endpoint/images/svg/check-yes.svg) W publicznej wersji zapoznawczej|![Tak](../defender-endpoint/images/svg/check-yes.svg) W publicznej wersji zapoznawczej|
|Microsoft Threat Experts|![Nie](../defender-endpoint/images/svg/check-no.svg) Na liście prac inżynierów|![Nie](../defender-endpoint/images/svg/check-no.svg) Na liście prac inżynierów|![Nie](../defender-endpoint/images/svg/check-no.svg) Na liście prac inżynierów|

Aby uzyskać szczegółową listę tabel interfejsu API przesyłania strumieniowego zdarzeń, zobacz [Microsoft 365 Defender typy zdarzeń przesyłania strumieniowego obsługiwane w interfejsie API przesyłania strumieniowego zdarzeń](supported-event-types.md).

## <a name="more-details"></a>Więcej szczegółów

Aby uzyskać więcej informacji, zobacz strony usługi US Gov poszczególnych obciążeń:

- [Microsoft Defender for Cloud Apps](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description).
- [Microsoft Defender for Identity](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/gov).
