---
title: Tabela AADSpnSignInEventsBeta w zaawansowanym schemacie wyszukiwania
description: Dowiedz się więcej o informacjach skojarzonych Azure Active Directory zabezpieczeń usługi i tabeli zdarzeń logowania tożsamości zarządzanej.
keywords: zaawansowane wyszukiwania, chłonianie pod zagrożeniami, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, kolumna, typ danych, opis, AlertInfo, alert, jednostki, dowód, plik, adres IP, urządzenie, komputer, użytkownik, konto, tożsamość, AAD
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 77cf2d7b74dfc4ccea88661642579f5244e14089
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63015813"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**Dotyczy:**
- Microsoft 365 Defender

> [!IMPORTANT]
> Tabela `AADSpnSignInEventsBeta` jest obecnie w wersji beta i będzie oferowana wkrótce, aby umożliwić ci poszukanie zdarzeń logowania w wersji Azure Active Directory (AAD). Klienci muszą mieć licencję Azure Active Directory — wersja Premium P2, aby zbierać i wyświetlać działania dotyczące tej tabeli. Firma Microsoft przeniesie wszystkie informacje schematu logowania do `IdentityLogonEvents` tabeli.

Tabela `AADSpnSignInEventsBeta` w zaawansowanym schemacie chłoń zawiera informacje Azure Active Directory zabezpieczeń usługi i logowania tożsamości zarządzanych. Możesz dowiedzieć się więcej o różnych rodzajach logowania w raportach aktywności [Azure Active Directory — podgląd](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

To odwołanie pozwala konstruować zapytania, które zwracają informacje z tabeli.

Aby uzyskać informacje o innych tabelach w zaawansowanym schemacie łęgowania, zapoznaj się z [zaawansowanymi informacjami na temat wyszukiwania](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Nazwa kolumny|Typ danych|Opis|
|---|---|---|
|`Timestamp`|`datetime`|Data i godzina wygenerowania rekordu|
|`Application`|`string`|Aplikacja, która wykonała nagraną akcję|
|`ApplicationId`|`string`|Unikatowy identyfikator aplikacji|
|`IsManagedIdentity`|`boolean`|Wskazuje, czy logowanie zostało rozpoczęte przez tożsamość zarządzaną.|
|`ErrorCode`|`int`|Zawiera kod błędu, jeśli wystąpi błąd logowania. Aby znaleźć opis określonego kodu błędu, odwiedź stronę <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Unikatowy identyfikator zdarzenia logowania|
|`ServicePrincipalName`|`string`|Nazwa podmiotu zabezpieczeń usługi, który rozpoczął logowanie|
|`ServicePrincipalId`|`string`|Unikatowy identyfikator podmiotu zabezpieczeń usługi, który rozpoczął logowanie|
|`ResourceDisplayName`|`string`|Nazwa wyświetlana zasobu, do którego uzyskano dostęp|
|`ResourceId`|`string`|Unikatowy identyfikator zasobu, do którego uzyskano dostęp|
|`ResourceTenantId`|`string`|Unikatowy identyfikator dzierżawy zasobu, do którego uzyskano dostęp|
|`IPAddress`|`string`|Adres IP przypisany do punktu końcowego i używany podczas powiązanej komunikacji sieciowej|
|`Country`|`string`|Dwuliterowy kod wskazujący kraj, do którego został geolokalizacji adresu IP klienta|
|`State`|`string`|Województwo, w którym wystąpiło logowanie, jeśli jest dostępne|
|`City`|`string`|Miasto, w którym znajduje się użytkownik konta|
|`Latitude`|`string`|Współrzędna od północ do południe lokalizacji logowania|
|`Longitude`|`string`|Współrzędna regionu wschodniego do zachodniego lokalizacji logowania|
|`RequestId`|`string`|Unikatowy identyfikator wniosku|
|`ReportId`|`string`|Unikatowy identyfikator zdarzenia|
||||

## <a name="related-articles"></a>Artykuły pokrewne

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [Omówienie zaawansowanego wyszukiwania](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Poznaw język zapytań](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Opis schematu](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
